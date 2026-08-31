# Module proposals

## CRS jit compiler fuzzer

A CRS that generates adversarial JavaScript/WebAssembly or JVM bytecode specifically designed to trigger JIT compiler bugs (incorrect deoptimization, type confusion in speculative execution, bounds check elimination bypasses) in V8, SpiderMonkey, HotSpot, and Graal.

## CRS static analysis

A CRS running static analyzers (Semgrep, CodeQL, Flawfinder, cppcheck) in batch mode against source code (C/C++ or other languages), producing structured vulnerability reports mapped to CWE categories.

## CRS patch gen

An LLM-based patch generation CRS that takes a crash plus root cause analysis (can be chained with the CRS static analysis), creates patches then verifies them using a sanitizier in a closed loop.

## CRS CVE correlator

A module that takes a found vulnerability's characteristics (type, affected function, crash pattern) and queries NVD/CVE databases plus embedding search over known CVEs to find related past vulnerabilities and existing PoCs.

## Module Multilang Support (AI orchestrator)

An extension of the dataset and CRS modules to support source-available targets in Python (via atheris), Go (go-fuzz), Rust (cargo-fuzz), and Java (via JQF/Zest), broadening OpenCRS beyond C/C++ binaries.

## CRS Adversarial ML

A CRS that generates adversarial examples against ML models deployed in security tools (malware classifiers, IDS models, spam filters) using gradient-based and black-box attacks (FGSM, PGD, square attack), measuring how much perturbation is needed to flip a classification.

## CRS dependency confusion

A CRS that scans package manifests across ecosystems (npm, PyPI, Maven, RubyGems, crates.io) for dependency confusion vulnerability patterns: internal package names that could be squatted on public registries, version pinning gaps, and typosquatting candidates.

## Cross-Architecture Binary Lifting and Normalisation

A vulnerability found in an ARM Cortex-M firmware may also exist in the same library compiled for
x86_64 or RISC-V. Binary lifting, translating machine code to an intermediate representation (LLVM IR, VEX, ESIL), enables cross-architecture comparison.
<br>ML applied here: learning architecture-agnostic embeddings of basic blocks (similar to asm2vec and Trex) that map semantically equivalent code to
nearby points in embedding space regardless of ISA. The practical goal is one model that can match a CVE-affected function across all architectures in a firmware corpus without recompiling.

## Microarchitectural Attack Surface Mapping

CPU microarchitectural features (speculative execution, branch
predictors, cache hierarchies, TLBs) can be exploited without any software bug. Systematically discovering new microarchitectural vulnerabilities requires reasoning about CPU internal state that is not documented and not directly observable. <br>ML approaches: training fuzzing feedback signals on micro-benchmark timing measurements to discover new cache-timing oracles; using LLMs to reason over CPU microarchitecture documentation and generate hypotheses about novel transient execution paths; and building ML models of branch predictor behaviour to identify new Spectre gadget patterns automatically.

## Control Flow Integrity Violation Detection

CFI (Control Flow Integrity) defences (clang CFI, Microsoft CFG, grsecurity RAP) restrict indirect branches to a set of valid targets. Attackers bypass CFI by reusing valid targets in unexpected sequences (COOP - Counterfeit Object-Oriented Programming). <br>ML can model the expected distribution of call sequences at runtime and flag deviations even when each individual transfer is CFI-compliant. LSTM/Transformer models trained on normal execution traces of a target application can detect COOP-style attacks with low false-positive rates on synthetic benchmarks; generalisation to production workloads is still an open problem.

#### Other ideas can be found here:

- https://docs-website-2qbb.vercel.app/view/AI_Cybersec_Overview_2026.pdf
- https://docs-website-2qbb.vercel.app/view/Project_Ideas.pdf
