# YOLOv8 OpenVINO Inference in C++ using Windows

## Environment Setup

1. Download [Visual Studio 2022 Community Edition](https://visualstudio.microsoft.com/downloads).

2. Install Visual Studio with "Desktop development with C++" and keep the default packages (here `cmake` is already included).

![](https://github.com/lakshanthad/assets/releases/download/v0.1/pic1.jpg)

3. Open Visual Studio and select "Continue without code"

![](https://github.com/lakshanthad/assets/releases/download/v0.1/pic2.jpg)

4. Navigate to `View > Terminal`

![](https://github.com/lakshanthad/assets/releases/download/v0.1/pic3.jpg)

5. Make sure `cmake` is already installed

```sh
**********************************************************************
** Visual Studio 2022 Developer PowerShell v17.14.4
** Copyright (c) 2025 Microsoft Corporation
**********************************************************************
PS C:\Users\laksh\source\repos> cmake --version
cmake version 3.31.6-msvc6

CMake suite maintained and supported by Kitware (kitware.com/cmake).
```

6. Install OpenCV and OpenVINO using `vcpkg`

```sh
git clone https://github.com/microsoft/vcpkg.git
cd vcpkg
.\bootstrap-vcpkg.bat
.\vcpkg install opencv4
.\vcpkg install openvino
```

Note: OpenCV and OpenVINO compilation will take around 2hr+ depending on your hardware configuration. Also it will take around 70GB+ of storage space.

7. Clone the below repository and navigate to `YOLOv8-OpenVINO-CPP-Inference-Windows`

```sh
git clone https://github.com/lakshanthad/YOLOv8-OpenVINO-CPP-Inference-Windows
cd YOLOv8-OpenVINO-CPP-Inference-Windows
```

Note: The above repository is a fork of `https://github.com/ultralytics/ultralytics/examples/YOLOv8-OpenVINO-CPP-Inference` with minor changes to `CMakeLists.txt` to make the example work on Windows systems

8. Create a build directory and compile the project using CMake

```sh
mkdir build
cd build
cmake .. -DCMAKE_TOOLCHAIN_FILE="[path_to_vcpkg]/scripts/buildsystems/vcpkg.cmake"
"C:\Program Files\Microsoft Visual Studio\2022\Community\MSBuild\Current\Bin\MSBuild.exe" YOLOv8-OpenVINO-CPP-Inference.sln /p:Configuration=Release
```

9. Inference using the compiled `detect.exe`executable

```sh
cd Release
detect.exe path/to/your/model.xml path/to/your/image.jpg
```

Note: Here `model.xml` is obtained via exporting an Ultralytics YOLOv8 model to OpenVINO using `yolo export model=yolov8n.pt format=openvino`

