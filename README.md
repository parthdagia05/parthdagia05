<!--markdownlint-disable-->

<div align="center">

<img width="78%" src="https://raw.githubusercontent.com/parthdagia05/parthdagia05/main/assets/devil.svg" alt="devil" />

<br><br>

# `man parth`

<sub>SYSTEMS PROGRAMMING MANUAL &nbsp;·&nbsp; SECTION 1 &nbsp;·&nbsp; LAST UPDATED: WHENEVER THE BUILD FINISHED</sub>

<br>

<a href="https://www.linkedin.com/in/parthdagia/" target="_blank">
  <img src="https://img.shields.io/badge/LinkedIn-0d1117?style=for-the-badge&logo=linkedin&logoColor=ff2200" alt="LinkedIn" />
</a>
<a href="https://x.com/parthdagia" target="_blank">
  <img src="https://img.shields.io/badge/X-0d1117?style=for-the-badge&logo=x&logoColor=white" alt="X" />
</a>
<a href="mailto:work.parthdagia@gmail.com" target="_blank">
  <img src="https://img.shields.io/badge/Gmail-0d1117?style=for-the-badge&logo=gmail&logoColor=ff2200" alt="Gmail" />
</a>
<a href="https://github.com/WasmEdge/WasmEdge/pulls?q=author%3Aparthdagia05" target="_blank">
  <img src="https://img.shields.io/badge/WasmEdge_PRs-0d1117?style=for-the-badge&logo=webassembly&logoColor=ff2200" alt="WasmEdge" />
</a>

<img src="https://komarev.com/ghpvc/?username=parthdagia05&abbreviated=true&style=for-the-badge&color=ff0000&label=MANPAGE+OPENED" alt="views" />

</div>

<br>

```console
$ man parth
```

```
NAME
     parth - systems programmer; runs WebAssembly, occasionally runs out of memory

SYNOPSIS
     parth [-j$(nproc)] [-O2] [--no-sleep] [--enable-component] < coffee

DESCRIPTION
     Contributes to WasmEdge, a CNCF WebAssembly runtime. Spends most cycles in
     lib/validator/ losing arguments to the Component Model specification, and
     the remainder waiting for LLVM to finish linking.

     Implemented ML-KEM, so your keys will survive a quantum computer. Has not
     yet implemented anything that survives a Monday.

OPTIONS
     -j N        Parallelism. Accepted and ignored; parth is single-threaded
                 and blocks on I/O (email).

     -O2         Optimize. Increases confidence. Does not increase correctness.

     -g          Emit debug symbols. Redundant. The debug symbols are already
                 visible, directly beneath the eyes.

     -Wall       Enable all warnings. Not recommended. Output exceeds the
                 terminal scrollback buffer on every known platform.

     --fast      Not implemented. See BUGS.

     --enable-component
                 Enables experimental behavior with no stability guarantees.
                 Identical semantics to the upstream flag of the same name.

EXIT STATUS
     0     All tests passed. Never observed in the wild; believed theoretical.
     1     All tests passed locally.
     101   CI is green everywhere except Windows.
     134   Assertion failed, core dumped. parth also dumped.
     139   Segmentation fault. Dereferenced a pointer he was explicitly told
           not to dereference, in a comment, that he wrote.
     143   Terminated during code review by a maintainer named hydai.

ENVIRONMENT
     CXX                     Must be clang. gcc is tolerated, never respected.

     WASMEDGE_PLUGIN_PATH    Set incorrectly. Always. By everyone. Including,
                             on at least four documented occasions, by parth.

     TZ                      Asia/Kolkata. This explains the commit timestamps
                             and should not be raised in conversation.

FILES
     ~/.gitconfig            Contained the wrong email for an embarrassing
                             number of months. Resolved. Probably.

     ~/WasmEdge/build/       47 GB. Do not open. Do not `du -sh`. Do not think
                             about it.

     ~/projects/             Contains 33 repositories, of which 1 is finished.

BUGS
     -  Cannot be interrupted while a build is running. Maintainers have
        classified this as WONTFIX, working as intended.
     -  Announces "one sec, just rebasing", then is unreachable for 40 minutes.
     -  Writes a commit message, discovers the header limit is 100 characters,
        writes it again, discovers it is still 100 characters.
     -  Undefined behavior when handed a merge conflict after 02:00 local time.
     -  Known memory leak. Will not fix. The memory was allocated for a Java
        assignment and is not coming back regardless.

SEE ALSO
     git-blame(1), valgrind(1), cmake(1), touch-grass(1) [not installed]

AUTHOR
     Written by Parth Dagia.
     Reviewed, at considerable length, by strangers on the internet.
```

<br>

<div align="center">

### `$ parth --version`

</div>

```console
parth 2.4.0 (build 24bcs10414, +wasm +llvm +postquantum -sleep)
Copyright (C) 2026. License: WTFPL-adjacent.
This is free software; you are welcome to fork it, as 29 people have.
There is NO WARRANTY, to the extent permitted by law, and to the extent
permitted by my own test coverage, which is a separate and lesser extent.
```

<br>

<div align="center">

### `$ cat /proc/parth/stack`

</div>

```
#0  0x00007f  __wasmedge_validator_component_lift ()   at lib/validator/
#1  0x00007f  llvm::LinkAllPassesLikeItIs3AM ()        at lib/llvm/
#2  0x00007f  resolve_review_thread (hydai)            at github.com/
#3  0x00007f  rebase_onto_master (conflicts=17)        at ~/WasmEdge/
#4  0x00007f  "it worked on my machine"                at src/excuses.cpp:1
#5  0x00007f  main ()                                  at ~/life.cpp:∞
```

<br>

<div align="center">

<img src="https://skillicons.dev/icons?i=cpp,c,java,go,python,llvm,cmake,wasm,linux,docker,git&theme=dark" alt="stack" />

<br><br>

<sub><b>WARNING:</b> the contribution graph below is generated by GitHub and cannot be
disabled. It reflects days on which I pushed to a non-fork repository, which is
a strictly smaller set than days on which I did work, which is in turn a
strictly smaller set than days on which I suffered.</sub>

</div>
