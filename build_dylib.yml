name: Build Dylib

on:
  workflow_dispatch: # Cho phép bạn bấm nút chạy thủ công

jobs:
  build:
    runs-on: macos-latest # Bắt buộc phải chạy trên máy Mac của GitHub

    steps:
    - name: Checkout code
      uses: actions/checkout@v4

    - name: Build Dylib
      run: |
        # Chạy lệnh make trực tiếp, bỏ qua lỗi makefile bằng cách gọi clang++ thủ công
        clang++ -std=c++17 -fPIC -shared -I./include -I./src \
        -framework Foundation -framework UIKit -framework Metal -framework MetalKit \
        src/main.cpp src/ui.mm src/luau_bridge.cpp -o RobloxExecutor.dylib

    - name: Upload Dylib Artifact
      uses: actions/upload-artifact@v4
      with:
        name: Roblox-Executor-Dylib
        path: RobloxExecutor.dylib
