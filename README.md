<!--markdownlint-disable-->

<div align="center">

<img width="46%" src="https://raw.githubusercontent.com/parthdagia05/parthdagia05/main/assets/devil.svg" alt="" />

# Parth Dagia

**I build the layer underneath an agent —**
**the part that has to be fast, cheap and correct when nobody is watching.**

<sub>CNCF · Hyperledger · Sugar Labs &nbsp;|&nbsp; Go · C++17 · Java · Python · TypeScript &nbsp;|&nbsp; BITS Pilani '27 · Bengaluru</sub>

<br>

<a href="https://www.linkedin.com/in/parthdagia/"><img src="https://img.shields.io/badge/LinkedIn-0d1117?style=for-the-badge&logo=linkedin&logoColor=ff2200" /></a>
<a href="https://x.com/parthdagia"><img src="https://img.shields.io/badge/X-0d1117?style=for-the-badge&logo=x&logoColor=white" /></a>
<a href="mailto:work.parthdagia@gmail.com"><img src="https://img.shields.io/badge/Email-0d1117?style=for-the-badge&logo=gmail&logoColor=ff2200" /></a>
<img src="https://img.shields.io/badge/MERGED_UPSTREAM-140_PRs-ff2200?style=for-the-badge&labelColor=0d1117" />

</div>

<br>

## `$ parth --bench`

I don't have a portfolio. I have a changelog of things that got measurably better.

```
BENCHMARK                              BEFORE              AFTER                  DELTA
────────────────────────────────────────────────────────────────────────────────────────
besu · uint256 mul (EVM hot path)      ████████████████    ████                   3.9x faster
besu · div / addMod / mulMod           ████████████████    ████████               28-78% faster
musicblocks · total blocking time      ████████████████    █████                  66% lower
musicblocks · bundle size              ████████████████    ███████████            3.8 MB lighter
musicblocks · startup delay            █████               ·                      5.0s -> 0s
mandate · agent attack success         ████████████████    ·                      80% -> 0%
deception-gym · detection accuracy     █████               ████████████████       32.7% -> 96.7%
deception-gym · sycophancy             ████████████████    █                      17x lower
────────────────────────────────────────────────────────────────────────────────────────
                                       all numbers reproducible from the linked repos
```

<br>

## `$ parth --upstream`

Production codebases, no onboarding, every change fenced by a test that fails on `master` first.

| Project | What it is | Lang | Merged |
|---|---|---|:--:|
| **[Music Blocks](https://github.com/sugarlabs/musicblocks)** + **[v4](https://github.com/sugarlabs/musicblocks-v4)** | Sugar Labs · nonprofit education software — **maintainer, GSoC '26** | TypeScript | **86** |
| **[Kubescape](https://github.com/kubescape/kubescape)** | CNCF · Kubernetes security & admission control | Go | **39** |
| **[WasmEdge](https://github.com/WasmEdge/WasmEdge)** | CNCF · WebAssembly runtime, loader/validator/executor | C++17 | **9** |
| **[Besu](https://github.com/besu-eth/besu)** | Hyperledger · Ethereum execution client & EVM | Java | **6** |

<details>
<summary><b>Kubescape</b> — 39 PRs in three weeks, mostly by deleting things &nbsp;<code>Go</code></summary>

<br>

- **Found a scan that passed by scanning nothing.** Resource plurals were guessed by appending `s`, so a policy scoped to `sandboxes` never matched a `Sandbox` and the run reported a clean pass over zero resources. ([#3355](https://github.com/kubescape/kubescape/pull/3355), [#3177](https://github.com/kubescape/kubescape/pull/3177))
- **Per-resource scoping and multi-action support** for generated `ValidatingAdmissionPolicy` bindings, which previously matched every resource the bound policy did and could not target a CRD at all. ([#3283](https://github.com/kubescape/kubescape/pull/3283), [#3295](https://github.com/kubescape/kubescape/pull/3295))
- **Speed came from caching the right things and deleting the wrong ones:** cached per-file work in the SARIF writer, indexed a scope's resources once instead of once per rule, replaced a full directory walk with an ancestor lookup.
- Hardened live-cluster discovery: kind filtering before collection, dedup when several API versions serve one resource, correct handling of an undecided access review. ([#3411](https://github.com/kubescape/kubescape/pull/3411), [#3297](https://github.com/kubescape/kubescape/pull/3297), [#3446](https://github.com/kubescape/kubescape/pull/3446))

</details>

<details>
<summary><b>Hyperledger Besu</b> — made the EVM stop allocating &nbsp;<code>Java · JMH</code></summary>

<br>

- **256-bit opcodes on a flat `long[]` operand stack, zero heap allocation.** `ADD` with carry propagation across four 64-bit limbs, `SUB` with borrow, plus `MUL`, `DIV` and bitwise ops — **~3.9x faster** than the boxed path. This is the arithmetic under *every* EVM opcode.
- **Power-of-two fast paths** for `UInt256.div`, `addMod`, `mulMod`: Knuth Algorithm D replaced with a shift or a mask, **28–78% faster**, verified under JMH with property-based differential tests against `BigInteger`.
- Enabled NullAway null-safety analysis across `datatypes` and `ethereum:rlp`.

</details>

<details>
<summary><b>WasmEdge</b> — post-quantum crypto and the Component Model &nbsp;<code>C++17 · CMake</code></summary>

<br>

- **ML-KEM post-quantum key encapsulation** merged into the `wasi_crypto` plugin with FIPS 203 known-answer tests. Plus ECDSA and EdDSA public-key verification.
- **Component Model value-section loader**, value-linearity enforcement, and core global/table type checks at instantiation — rejecting malformed components before they execute.
- Enabled three official spec suites in CI: naming, invalid, memory64.

</details>

<details>
<summary><b>Music Blocks</b> — maintainer, and the reason it loads now &nbsp;<code>TypeScript · React</code></summary>

<br>

- **Total Blocking Time down ~66%** and a **five-second startup delay deleted**, by lazy-loading 17 modules — **3.8 MB** off the bundle — held in place with Lighthouse CI budgets.
- **Designed the brick-rendering engine:** stroke-width-aware SVG outline paths with rounded corners and connector notches, so bricks snap together at any scale. Path geometry is unit-tested.
- Rebuilt the Brick Palette as a declarative system where one schema object determines what renders and how it groups.
- Review and merge community pull requests as a maintainer.

</details>

<br>

## `$ parth --own-work`

<table>
<tr>
<td width="50%" valign="top">

### [mandate](https://github.com/parthdagia05/mandate)
**A deterministic enforcement kernel for agent actions**
`Python` `SQLite`

Keeps the model **off the safety path** — the check costs zero tokens and returns the same answer every time. Nine deterministic checks, fail-closed on any store failure, and a CI test that fails the build if the kernel ever imports the model client.

Two-phase idempotency with a recovery scan, so a crash mid-capture and a duplicate webhook each leave **exactly one debit**.

Content-addressed cache over every model call — a whole eval run replays byte-identically **with no API key**.

> Attack success **80% → 0%** across seven attack classes, scored by programmatic oracles, no judge model. The 12% false-block rate is published beside it, not buried.

</td>
<td width="50%" valign="top">

### [among-us-deception-gym](https://github.com/parthdagia05/among-us-deception-gym)
**An OpenEnv-spec RL environment for deception detection**
`Python` `GRPO`

Trained a model to stop believing confident liars, on a single A10G.

> Detection **32.7% → 96.7%**, sycophancy **17x lower**, held on an unseen harder distribution.

### [exlang-jit](https://github.com/parthdagia05/exlang-jit)
**A JIT compiler for integer expressions**
`C++17` `LLVM` `ORC JIT`

lexer → recursive-descent parser → AST → IR gen → O2 pass pipeline → ORC JIT. Variables resolve to array slots up front, giving one `i64 @expr(ptr)` signature.

### [schemago](https://github.com/parthdagia05/schemago)
**A PostgreSQL schema migration runner**
`Go` `PostgreSQL` `Docker`

Per-migration transactional apply with rollback, advisory locking so concurrent deploys cannot race, dry-run and plan previews, one static binary per platform.

</td>
</tr>
</table>

<br>

## `$ parth --stack`

<div align="center">

<img src="https://skillicons.dev/icons?i=go,cpp,java,python,ts,react,llvm,kubernetes,docker,postgres,cmake,githubactions&theme=dark" />

</div>

```
performance    hot-path profiling, allocation-free data paths, caching strategy,
               cold-start and bundle reduction, JMH / Lighthouse CI
ai systems     Anthropic API, structured output, response caching, deterministic
               replay, RL fine-tuning (GRPO), programmatic eval oracles
cloud native   Kubernetes API discovery, CRDs, RBAC, ValidatingAdmissionPolicy,
               CEL, OPA, client-go
compilers      LLVM IR generation, pass pipelines, ORC JIT, AOT/JIT, WebAssembly
```

<br>

<div align="center">

<sub><b>note:</b> the contribution graph below is generated by GitHub and cannot be disabled.
It counts days I pushed to a non-fork repository — a strictly smaller set than days I did work,
which is a strictly smaller set than days I suffered. The table above is the honest one.</sub>

</div>
