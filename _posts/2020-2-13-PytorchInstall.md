---
title: Pytorch安裝(使用Anaconda 3)
layout: single
category: Pytorch
tag: 環境建置
toc: true
toc_label: "目錄"
toc_icon: "th-list"
header:
  teaser: "/assets/images/PytorchInstall/pytorch.png"
---
>Pytorch很適合想入門深度學習的人使用，官方文檔整理的很清楚，社區雖然還不是很完善，但有很多相關的教程可以幫助學習，之後再開一篇學習資源彙整，這篇先把Pytorch的環境架好，我是使用Windows10 搭配Anaconda3進行安裝

環境 : 
Anaconda 3 、 Sublime Text 、 Pytorch 1.4 (Conda,Python,CUDA 10.1)

確認顯卡有無支援CUDA，沒有則使用CPU [`CUDA支援GPU一覽`](https://developer.nvidia.com/cuda-gpus)


## **安裝Anaconda & Pytorch**

- 安裝[`Anaconda 3`](https://www.anaconda.com/),[`pytorch`](https://pytorch.org/get-started/locally/),[`Sublime Text`](https://www.sublimetext.com/),[`VsCode`](https://code.visualstudio.com/)(後兩者擇一)

- 在Anaconda建立虛擬環境(使用python 3.7.6)

```

conda create -n pytorch_GPU python==3.7

```

- 切換至pytorch虛擬環境

```

activate pytorch_GPU

```

- 安裝pytorch(with CUDA)

```

conda install pytorch torchvision cudatoolkit=10.1 -c pytorch

```

- 安裝pytorch(CPU) <- 顯卡不支援CUDA時用這個

```

conda install pytorch torchvision cpuonly -c pytorch

```

- 進python測試是否安裝成功

```

import torch

torch.cuda.is_available()

```

## **在 VsCode 中用Anaconda建立虛擬環境編譯(推薦)**

- 在左邊的 EXTENSIONS 中搜尋 Pytorch 並安裝
![](/assets/images/PytorchInstall/1.png)
- 打開命令面板（Ctrl / Cmd + Shift + P）

- 輸入"Python : Select Interpreter"

- 選擇 "pytorch_GPU : conda" 進行編譯

>`torch has no member` : setting -> 搜尋python.linting.pylintPath -> 修改為(Anaconda安裝路徑)\pkgs\pylint-1.8.4-py36_0\Scriptspylint


## **在 Sublime Text 中使用Anaconda建立的虛擬環境編譯**

- 選擇 Tools -> Build System -> New Build System

- 將程式碼替換如下(換成自己的Anaconda3虛擬環境路徑)

```

{

  "cmd": ["A:\\Anaconda3\\envs\\pytorch_GPU\\python", "-u", "$file"],

  "file_regex": "^[ ]*File \"(...*?)\", line ([0-9]*)",

  "selector": "source.python"

}

```

- 儲存並命名 pytorch.sublime-build

- 選擇 Tools -> Build System -> pytorch 開始編譯

---

