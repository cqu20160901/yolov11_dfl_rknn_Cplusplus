# yolov11_dfl_rknn_Cplusplus
yolov11 rk3588 部署版本，将DFL放在后处理中，转换工具版本 rknn_toolkit2-2.2.0-cp38-cp38-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.


导出onnx、转rknn流程说明[【yolov11 部署瑞芯微rk3588、RKNN部署工程难度小、模型推理速度快】](https://blog.csdn.net/zhangqian_1/article/details/142722526)

## 编译和运行

1）编译

```
cd examples/rknn_yolov11_demo_dfl_open

bash build-linux_RK3588.sh

```

2）运行

```
cd install/rknn_yolo_demo_Linux

./rknn_yolo_demo 

```

注意：修改模型、测试图像、保存图像的路径，修改文件为src下的main.cc

```

int main(int argc, char **argv)
{
    char model_path[256] = "/home/zhangqian/rknn/examples/rknn_yolov11_demo_dfl_open/model/RK3588/yolov11n_80class_ZQ.rknn";
    char image_path[256] = "/home/zhangqian/rknn/examples/rknn_yolov11_demo_dfl_open/test.jpg";
    char save_image_path[256] = "/home/zhangqian/rknn/examples/rknn_yolov11_demo_dfl_open/test_result.jpg";

    detect(model_path, image_path, save_image_path);
    return 0;
}
```


# 测试效果

## onnx 测试效果

![image](https://github.com/cqu20160901/yolov11_onnx_rknn/blob/main/yolov11n_onnx/test_onnx_result.jpg)


## rk3588上测试效果

![images](https://github.com/cqu20160901/yolov11_dfl_rknn_Cplusplus/blob/main/examples/rknn_yolov11_demo_dfl_open/test_result.jpg)

把板端模型推理和后处理时耗也附上，供参考，使用的芯片rk3588，模型输入640x640。

![image](https://github.com/cqu20160901/yolov11_dfl_rknn_Cplusplus/blob/main/examples/rknn_yolov11_demo_dfl_open/yolov11_rk3588_costtime.png)


# tenorRT cuda 版本参考(cuda 实现后处理中部分最耗时处理)
[yolov11_tensorRT_postprocess_cuda](https://github.com/cqu20160901/yolov11_tensorRT_postprocess_cuda)


