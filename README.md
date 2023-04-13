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

