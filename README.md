<p align="center">
  <a title="'doc' workflow Status" href="https://github.com/hdl/containers/actions?query=workflow%3Adoc"><img alt="'doc' workflow Status" src="https://img.shields.io/github/workflow/status/hdl/containers/doc?longCache=true&style=flat-square&label=doc&logo=GitHub%20Actions&logoColor=fff"></a><!--
  -->
  <a title="'base' workflow Status" href="https://github.com/hdl/containers/actions?query=workflow%3Abase"><img alt="'base' workflow Status" src="https://img.shields.io/github/workflow/status/hdl/containers/base?longCache=true&style=flat-square&label=base&logo=GitHub%20Actions&logoColor=fff"></a><!--
  -->
</p>
<p align="center">
  <a title="'ghdl' workflow Status" href="https://github.com/hdl/containers/actions?query=workflow%3Aghdl"><img alt="'ghdl' workflow Status" src="https://img.shields.io/github/workflow/status/hdl/containers/ghdl?longCache=true&style=flat-square&label=ghdl&logo=GitHub%20Actions&logoColor=fff"></a><!--
  -->
  <a title="'gtkwave' workflow Status" href="https://github.com/hdl/containers/actions?query=workflow%3Agtkwave"><img alt="'gtkwave' workflow Status" src="https://img.shields.io/github/workflow/status/hdl/containers/gtkwave?longCache=true&style=flat-square&label=gtkwave&logo=GitHub%20Actions&logoColor=fff"></a><!--
  -->
  <a title="'icestorm' workflow Status" href="https://github.com/hdl/containers/actions?query=workflow%3Aicestorm"><img alt="'icestorm' workflow Status" src="https://img.shields.io/github/workflow/status/hdl/containers/icestorm?longCache=true&style=flat-square&label=icestorm&logo=GitHub%20Actions&logoColor=fff"></a><!--
  -->
  <a title="'nextpnr' workflow Status" href="https://github.com/hdl/containers/actions?query=workflow%3Anextpnr"><img alt="'nextpnr' workflow Status" src="https://img.shields.io/github/workflow/status/hdl/containers/nextpnr?longCache=true&style=flat-square&label=nextpnr&logo=GitHub%20Actions&logoColor=fff"></a><!--
  -->
  <a title="'prjtrellis' workflow Status" href="https://github.com/hdl/containers/actions?query=workflow%3Aprjtrellis"><img alt="'prjtrellis' workflow Status" src="https://img.shields.io/github/workflow/status/hdl/containers/prjtrellis?longCache=true&style=flat-square&label=prjtrellis&logo=GitHub%20Actions&logoColor=fff"></a><!--
  -->
</p>
<p align="center">
  <a title="'symbiyosys' workflow Status" href="https://github.com/hdl/containers/actions?query=workflow%3Asymbiyosys"><img alt="'symbiyosys' workflow Status" src="https://img.shields.io/github/workflow/status/hdl/containers/symbiyosys?longCache=true&style=flat-square&label=symbiyosys&logo=GitHub%20Actions&logoColor=fff"></a><!--
  -->
  <a title="'yosys' workflow Status" href="https://github.com/hdl/containers/actions?query=workflow%3Ayosys"><img alt="'yosys' workflow Status" src="https://img.shields.io/github/workflow/status/hdl/containers/yosys?longCache=true&style=flat-square&label=yosys&logo=GitHub%20Actions&logoColor=fff"></a><!--
  -->
  <a title="'z3' workflow Status" href="https://github.com/hdl/containers/actions?query=workflow%3Az3"><img alt="'z3' workflow Status" src="https://img.shields.io/github/workflow/status/hdl/containers/z3?longCache=true&style=flat-square&label=z3&logo=GitHub%20Actions&logoColor=fff"></a>
</p>
<p align="center">
  <a title="'formal' workflow Status" href="https://github.com/hdl/containers/actions?query=workflow%3Aformal"><img alt="'formal' workflow Status" src="https://img.shields.io/github/workflow/status/hdl/containers/formal?longCache=true&style=flat-square&label=formal&logo=GitHub%20Actions&logoColor=fff"></a><!--
  -->
  <a title="'prog' workflow Status" href="https://github.com/hdl/containers/actions?query=workflow%3Aprog"><img alt="'prog' workflow Status" src="https://img.shields.io/github/workflow/status/hdl/containers/prog?longCache=true&style=flat-square&label=prog&logo=GitHub%20Actions&logoColor=fff"></a><!--
  -->
</p>

This repository contains scripts and GitHub Actions (GHA) YAML workflows for building and deploying OCI images (aka Docker images) including open source EDA tooling. All of them are pushed to [hub.docker.com/u/hdlc](https://hub.docker.com/u/hdlc).

----

## Proposed collaboration flow

This repository provides base images for building and for runtime:

- [![hdlc/build:base Docker image size](https://img.shields.io/docker/image-size/hdlc/build/base?longCache=true&style=flat-square&label=hdlc%2Fbuild:base&logo=Docker&logoColor=fff)](https://hub.docker.com/r/hdlc/build/tags) Debian Buster with updated `ca-certificates`, `curl` and Python 3.
- [![hdlc/build:build Docker image size](https://img.shields.io/docker/image-size/hdlc/build/build?longCache=true&style=flat-square&label=hdlc%2Fbuild:build&logo=Docker&logoColor=fff)](https://hub.docker.com/r/hdlc/build/tags) based on `base`, includes `clang` and `make`.
- [![hdlc/build:dev Docker image size](https://img.shields.io/docker/image-size/hdlc/build/dev?longCache=true&style=flat-square&label=hdlc%2Fbuild:dev&logo=Docker&logoColor=fff)](https://hub.docker.com/r/hdlc/build/tags) based on `build`, includes `cmake`, `libboost-all-dev` and `python3-dev`.

Then, each project:

- Uses base building images for building their own tools.
- Produces cache images based on `scratch`, and/or other reusable packages.
- Produces ready-to-use images based on the runtime base image.

Last, this repository merges multiple tools into ready-to-use images for specific use cases.

Finally, users consume the ready-to-use images that include a single tool, or the ones including many of them.

Some projects don't use containers at all. In some of those cases, all images are generated in this repository. However, the workload is expected to be distributed between multiple projects in the ecosystem.

## Tools/projects

The following is a non-exhaustive list of projects that we'd like to support in this repository:

- [ ] [bitman](https://github.com/khoapham/bitman)
- [ ] [cocotb](https://github.com/cocotb/cocotb)
- [ ] [fujprog](https://github.com/kost/fujprog)
- [x] [ghdl](https://github.com/ghdl/ghdl)
  - [![hdlc/ghdl:latest Docker image size](https://img.shields.io/docker/image-size/hdlc/ghdl/latest?longCache=true&style=flat-square&label=hdlc%2Fghdl&logo=Docker&logoColor=fff)](https://hub.docker.com/r/hdlc/ghdl/tags)
  - [![hdlc/ghdl:yosys Docker image size](https://img.shields.io/docker/image-size/hdlc/ghdl/yosys?longCache=true&style=flat-square&label=hdlc%2Fghdl:yosys&logo=Docker&logoColor=fff)](https://hub.docker.com/r/hdlc/ghdl/tags)
  - In `hdlc/formal`.
- [x] [ghdl-yosys-plugin](https://github.com/ghdl/ghdl-yosys-plugin)
  - In `hdlc/ghdl:yosys` and `hdlc/formal`.
- [x] [graphviz](https://graphviz.org/)
  - In `hdlc/yosys`, `hdlc/ghdl:yosys` and `hdlc/formal`.
- [x] [gtkwave](https://github.com/gtkwave/gtkwave)
  - [![hdlc/pkg:gtkwave Docker image size](https://img.shields.io/docker/image-size/hdlc/pkg/gtkwave?longCache=true&style=flat-square&label=hdlc%2Fpkg:gtkwave&logo=Docker&logoColor=fff)](https://hub.docker.com/r/hdlc/pkg/tags)
- [x] [icestorm](https://github.com/cliffordwolf/icestorm)
  - [![hdlc/icestorm:latest Docker image size](https://img.shields.io/docker/image-size/hdlc/icestorm/latest?longCache=true&style=flat-square&label=hdlc%2Ficestorm&logo=Docker&logoColor=fff)](https://hub.docker.com/r/hdlc/icestorm/tags)
  - [![hdlc/pkg:icestorm Docker image size](https://img.shields.io/docker/image-size/hdlc/pkg/icestorm?longCache=true&style=flat-square&label=hdlc%2Fpkg:icestorm&logo=Docker&logoColor=fff)](https://hub.docker.com/r/hdlc/pkg/tags)
- [ ] [iverilog](https://github.com/steveicarus/iverilog)
- [ ] [netlistsvg](https://github.com/nturley/netlistsvg)
- [x] [nextpnr](https://github.com/YosysHQ/nextpnr)
  - [![hdlc/nextpnr:latest Docker image size](https://img.shields.io/docker/image-size/hdlc/nextpnr/latest?longCache=true&style=flat-square&label=hdlc%2Fnextpnr&logo=Docker&logoColor=fff)](https://hub.docker.com/r/hdlc/nextpnr/tags)
  - [![hdlc/nextpnr:ice40 Docker image size](https://img.shields.io/docker/image-size/hdlc/nextpnr/ice40?longCache=true&style=flat-square&label=hdlc%2Fnextpnr:ice40&logo=Docker&logoColor=fff)](https://hub.docker.com/r/hdlc/nextpnr/tags)
  - [![hdlc/nextpnr:ecp5 Docker image size](https://img.shields.io/docker/image-size/hdlc/nextpnr/ecp5?longCache=true&style=flat-square&label=hdlc%2Fnextpnr:ecp5&logo=Docker&logoColor=fff)](https://hub.docker.com/r/hdlc/nextpnr/tags)
- [ ] [openFPGALoader](https://github.com/trabucayre/openFPGALoader)
- [x] [openocd](http://openocd.org/)
  - In `hdlc/prog`.
- [x] [prjtrellis](https://github.com/hdlc/prjtrellis)
  - [![hdlc/prjtrellis:latest Docker image size](https://img.shields.io/docker/image-size/hdlc/prjtrellis/latest?longCache=true&style=flat-square&label=hdlc%2Fprjtrellis&logo=Docker&logoColor=fff)](https://hub.docker.com/r/hdlc/prjtrellis/tags)
  - [![hdlc/pkg:prjtrellis Docker image size](https://img.shields.io/docker/image-size/hdlc/pkg/prjtrellis?longCache=true&style=flat-square&label=hdlc%2Fpkg:prjtrellis&logo=Docker&logoColor=fff)](https://hub.docker.com/r/hdlc/pkg/tags)
- [x] [symbiyosys](https://github.com/YosysHQ/SymbiYosys)
  - [![hdlc/pkg:symbiyosys Docker image size](https://img.shields.io/docker/image-size/hdlc/pkg/symbiyosys?longCache=true&style=flat-square&label=hdlc%2Fpkg:symbiyosys&logo=Docker&logoColor=fff)](https://hub.docker.com/r/hdlc/pkg/tags)
  - In `hdlc/formal`.
- [ ] [verilator](https://github.com/verilator/verilator)
- [ ] [vunit](https://github.com/VUnit/vunit)
- [ ] [Yices 2](https://github.com/SRI-CSL/yices2)
- [x] [yosys](https://github.com/YosysHQ/yosys)
  - [![hdlc/yosys:latest Docker image size](https://img.shields.io/docker/image-size/hdlc/yosys/latest?longCache=true&style=flat-square&label=hdlc%2Fyosys&logo=Docker&logoColor=fff)](https://hub.docker.com/r/hdlc/yosys/tags)
  - [![hdlc/pkg:yosys Docker image size](https://img.shields.io/docker/image-size/hdlc/pkg/yosys?longCache=true&style=flat-square&label=hdlc%2Fpkg:yosys&logo=Docker&logoColor=fff)](https://hub.docker.com/r/hdlc/pkg/tags)
  - In `hdlc/ghdl:yosys` and `hdlc/formal`.
- [x] [z3](https://github.com/Z3Prover/z3)
  - [![hdlc/pkg:z3 Docker image size](https://img.shields.io/docker/image-size/hdlc/pkg/z3?longCache=true&style=flat-square&label=hdlc%2Fpkg:z3&logo=Docker&logoColor=fff)](https://hub.docker.com/r/hdlc/pkg/tags)
  - In `hdlc/formal`.

## Images including multiple tools

- [![hdlc/prog:latest Docker image size](https://img.shields.io/docker/image-size/hdlc/prog/latest?longCache=true&style=flat-square&label=hdlc%2Fprog&logo=Docker&logoColor=fff)](https://hub.docker.com/r/hdlc/prog/tags)
  - iceprog
  - openocd

- [![hdlc/formal Docker image size](https://img.shields.io/docker/image-size/hdlc/formal/latest?longCache=true&style=flat-square&label=hdlc%2Fformal&logo=Docker&logoColor=fff)](https://hub.docker.com/r/hdlc/formal/tags)
  - GHDL
  - ghdl-yosys-plugin
  - graphviz
  - Symbiyosys
  - Yosys
  - z3

## Development

*NOTE: Currently, there is no triggering mechanism set up between different GitHub repositories. All the workflows in this repo are triggered by CRON jobs.*

## References

- SymbiFlow:
  - [SymbiFlow/symbiflow-examples](https://github.com/SymbiFlow/symbiflow-examples)
  - [SymbiFlow/make-env](https://github.com/SymbiFlow/make-env)
    - [bit.ly/edda-conda-eda-spec](http://bit.ly/edda-conda-eda-spec): Conda based system for FPGA and ASIC Dev
    - [Support providing the environment using docker rather than conda #15](https://github.com/SymbiFlow/make-env/issues/15)
- GHDL:
  - [ghdl/docker](https://github.com/ghdl/docker)
  - [ghdl/setup-ghdl-ci](https://github.com/ghdl/setup-ghdl-ci)
- DBHI:
  - [dbhi/qus](https://github.com/dbhi/qus)
  - [dbhi/docker](https://github.com/dbhi/docker)
- [open-tool-forge/fpga-toolchain](https://github.com/open-tool-forge/fpga-toolchain)
- [im-tomu/fomu-toolchain](https://github.com/im-tomu/fomu-toolchain)
- [alpin3/ulx3s](https://github.com/alpin3/ulx3s)
- [eine/elide](https://github.com/eine/elide/tree/master/elide/docker)
- [hackfin/ghdl-cross.mk](https://github.com/hackfin/ghdl-cross.mk)
