Step2: edit compile option
===============================

open the ``CMakeLists.txt`` file in ``ascend-quadruped-cpp`` folder, check the compile options so as to match the hardware and applications. In particular, when compiling unitree_legged_skd, the binary ``.so`` file should be ``*amd64.so`` in ``./lib/`` subdirectory, according to current X86/AMD64 platform. If you do not want to compile test examples, please disable ``ENABLE_TEST``.