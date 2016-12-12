# AZPlugins

AZPlugins is a component (plugin) for [HOOMD-blue](http://glotzerlab.engin.umich.edu/hoomd-blue)
which expands its functionality for tackling a variety of problems in soft matter physics.
See [ChangeLog.md](ChangeLog.md) for recent development.

## Compiling AZPlugins

AZPlugins can be built using either of the standard [plugin build methods](http://hoomd-blue.readthedocs.io/en/stable/developer.html).
To build AZPlugins **internally** to HOOMD-blue, add a symlink to the code into the `hoomd-blue/hoomd`:

```bash
cd hoomd-blue/hoomd
ln -s /path/to/azplugins/azplugins azplugins
cd ../build && make install
```

AZPlugins is now available as a component of HOOMD-blue:

```python
import hoomd
from hoomd import azplugins
```

To build AZPlugins **externally** to HOOMD-blue, ensure that the `hoomd` module is on your Python path
(or hint to its location using `HOOMD_ROOT`), and install to an appropriate location:

```bash
cd /path/to/azplugins
mkdir build && cd build
cmake ..
make install
```

You must make sure that your installation location is on your `PYTHONPATH`, and then `azplugins` can
be imported as usual

```python
import hoomd
import azplugins
```

### Prerequisites

 * Required:
     * Python >= 2.7
     * numpy >= 1.7
     * CMake >= 2.8.0
     * C++ 11 capable compiler (tested with gcc >= 4.8.5, clang 3.5)
 * Optional:
     * NVIDIA CUDA Toolkit >= 7.0
     * MPI (tested with OpenMPI, MVAPICH)

### Testing

All code is unittested at the Python level. If AZPlugins has been built as a HOOMD-blue component,
it is automatically included into the testing tree. To run only the `azplugins` tests out of your build
directory, use ctest:

```bash
ctest -R azplugins-*
```
