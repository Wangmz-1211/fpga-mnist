# FPGA-MNIST
this is a repo for the fpga course.

## Environment Installation
```shell
conda env create -f ./env/env-wangmz.yaml
```



## Project Structure

| FILE                        | EXPLAINATION                                                 |
| --------------------------- | ------------------------------------------------------------ |
| ./best.pt                   | ./resources/LeNet5_Pytorch/train.py训练出的模型              |
| ./env/                      | conda环境信息                                                |
| ./figure/                   | 图像                                                         |
| ./param_text/               | ./resources/LeNet5_Pytorch/param_extraction.py 提取的模型参数 |
| ./intermediate_layer_param/ | 模型推理过程产生的中间变量                                   |



## Run (Linux)

**clear.sh**

~~~ shell
#!/bin/zsh

rm ./mnistTest.json
rm ./pix_norm.txt
rm ./best.pt
rm -rf ./param_text
rm ./weights_and_bias_bin.txt
rm ./img_pix_bin.txt 
rm ./img_5_norm.txt
~~~

**run.sh**

~~~shell
#!/bin/zsh

python -m visdom.server &

sleep 3

open http://localhost:8097 ;

sleep 3

# this will create 
# ./mnistTest.json
python ./convert_mnist_to_json.py

# this will create 
# ./pix_norm.txt
python ./MINIST_json_to_txt.py

# this will create 
# ./best.pt
python ./train.py

# this will create
# ./param_text/
python ./param_extraction.py

# this will create 
# ./intermediate_layer_param/
python ./LeNet5.py

# this will create 
# ./weights_and_bias_bin.txt
# ./img_pix_bin.txt 
python ./float2fixed.py
~~~

then, run

~~~shell
chmod +x ./clear.sh
chmod +x ./run.sh
./clear.sh
./run.sh
~~~

