# How to use dogebuild-tex

Dogebuild-tex is tex/latex plugin for [dogebuild](https://github.com/dogebuild/dogebuild).

## Simple project

To start simple project create `dogefile.py` and fill it with following code:

```python
from dogebuild_tex import Tex

Tex()
```

Create your latex document in `main.tex` file.

## Parameters

To modify behaviour if plugin you can pass following parameters:

- `tex_binary` - define binary to build .tex file, can be instance of `SystemTexBinary` or `DockerTexBinary`.
- `main_file` - file to build, `main.tex` by default.
- `build_dir` - output directory.
- `out_file_name` - output file name, `main` by default.

## Change binary to build

Usually `.tex` files are built to `.pdf` with `pdflatex` binary.
If you want to use different binary, e.g. `pdftex` you should set up binary as parameter of `SystemTexBinary` or `DockerTexBinary`.

Example of `dogefile.py` with `pdftex` as binary:

```python
from dogebuild_tex import Tex, SystemTexBinary

Tex(tex_binary=SystemTexBinary(pdf_binary="pdftex"))
```

Example of `dogefile.py` with `pdftex` as binary in docker container:

```python
from dogebuild_tex import Tex, DockerTexBinary

Tex(tex_binary=DockerTexBinary(
    "vipintm/xelatex",
    version="latest",
    pdf_binary="pdftex",
))
```
