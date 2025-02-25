# pandas-mlir

# Requirements

Requires Python 3.9+. Install python requirements using pip.
```
pip install -r requirements.txt
```

# Build

```
cmake -GNinja -Bbuild \
  -DCMAKE_C_COMPILER=clang \
  -DCMAKE_CXX_COMPILER=clang++ \
  -DLLVM_ENABLE_PROJECTS=mlir \
  -DLLVM_EXTERNAL_PROJECTS=pandas-mlir \
  -DLLVM_EXTERNAL_PANDAS_MLIR_SOURCE_DIR=`pwd` \
  -DMLIR_ENABLE_BINDINGS_PYTHON=OFF \
  -DLLVM_TARGETS_TO_BUILD=host \
  external/llvm-project/llvm

# Build pandas-mlir
cmake --build build --target tools/pandas-mlir/all

# Build everything
cmake --build build

# Run unit tests
cmake --build build --target check-pandas-mlir

# Convert Pandas Python -> Pandas MLIR
cd python/test; pytest -s

```
