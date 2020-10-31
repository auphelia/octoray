## Build instructions
Note: For this demo, we are using the branch `2019.2` of https://github.com/Xilinx/Vitis_Libraries



1. For this example, we use the `libz.so` shared library object. First, append a thin C wrapper to the source file `zlib.cpp`:
```cat wrapper.c >> Vitis_Libraries/data_compression/L3/src/zlib.cpp```

2. Generate the `xclbin` and `libz.so` file
```cd Vitis_Libraries/data_compression/L3/demos/gzip_hbm && make lib xclbin TARGET=hw DEVICE=xilinx_u50_gen3x16_xdma_201920_3```

Copy them here:

```cp Vitis_Libraries/data_compression/L3/demos/gzip_hbm/build . ```

3. This assumes a Python version > 3.6. Install dependencies using:
```pip3 install jupyter "dask[complete]" bokeh```

4. Run the dask scheduler using:

```dask-scheduler```

Note the IP address of the scheduler (of the form tcp://x.x.x.x:8786)

5. Run the dask worker (using the IP above).

```dask-worker tcp://x.x.x.x:8786 --nthreads 1 --memory-limit 0 --no-nanny```

6. Run the `dask.ipynb` notebook using jupyter (```$ jupyter notebook```)