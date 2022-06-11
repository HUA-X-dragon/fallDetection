# fallDetection
本次实验为基于猎豹平台的跌倒检测实验，内容为对测试图像中内容进行分类检测，共3个类别:'stand',  'sit',  'fall'。

训练步骤：

1 修改data文件夹里面的fall.yaml文件，设置好自己的训练集、验证集和测试集路径，同时修改类别数量和每一个类别的名称。修改models文件夹里的yolov5l.yaml文件，将识别类别改为3

2 当前项目路径下，新建pretrained文件夹，其中放入yolov5预训练权重yolov5l6文件

3 输入命令运行train.py文件，命令如下：

python train.py --data fall.yaml --cfg yolov5l.yaml --weights pretrained/yolov5l6.pt --epoch 100 --batch-size 6

4 训练完成后找到best.pt文件，运行export.py文件，将best.pt导出为onnx文件，命令如下：

python export.py --weights best.pt --include onnx --img 640 --batch 1

识别：

运行onnxTest.py文件，将模型路径换成转换好的onnx模型路径，即可完成识别
