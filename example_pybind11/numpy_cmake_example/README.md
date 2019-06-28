
## pre install 
```
pip install pybind11
git clone https://github.com/pybind/pybind11.git 
```

## compile & install
```
# compile
python setup.py build
# install
python setup.py install

```

## test code
```
import numpy_example
numpy_example.add(1,2)
import numpy as np
a = np.arange(3)
b = np.arange(3) * 2
c = numpy_example.add_arrays_1d(a,b)
print c
```

## reference 
* An example project built with [pybind11](https://github.com/pybind/pybind11).
