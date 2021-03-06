TVM Documentations
==================
This folder contains the source of TVM documents

- A hosted version of doc is at https://tvm.apache.org/docs
- pip install sphinx>=1.5.5 sphinx-gallery sphinx_rtd_theme matplotlib Image recommonmark "Pillow<7"
- Build tvm first in the root folder.
- To build locally, you need to enable USE_CUDA, USE_OPENCL, LLVM_CONFIG in config.cmake and then type "make html" in this folder.

Only Execute Specified Tutorials
--------------------------------
The document build process will execute all the tutorials in the sphinx gallery.
This will cause failure in some cases when certain machines do not have necessary
environment. You can set ```TVM_TUTORIAL_EXEC_PATTERN``` to only execute
the path that matches the regular expression pattern.

For example, to only build tutorials under /vta/tutorials, run

```bash
TVM_TUTORIAL_EXEC_PATTERN=/vta/tutorials make html
```

To only build one specific file, do

```bash
# The slash \ is used to get . in regular expression
TVM_TUTORIAL_EXEC_PATTERN=file_name\.py make html
```

Helper Scripts
--------------

You can run the following script to reproduce the CI sphinx pre-check stage.
This script skips the tutorial executions and is useful for quickly check the content.

```bash
./tests/scrpts/task_sphinx_precheck.sh
```

The following script runs the full build which includes tutorial executions.
You will need a gpu CI environment.

```bash
./tests/scrpts/task_python_docs.sh
```
