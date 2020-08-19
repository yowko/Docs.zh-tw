---
title: 如何在模型產生器中安裝 GPU 支援
description: 瞭解如何在模型產生器中安裝 GPU 支援
ms.date: 08/18/2020
author: luisquintanilla
ms.author: luquinta
ms.topic: how-to
ms.openlocfilehash: ce629efa4c12a69f87196de35ebfe4331dc0800f
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608563"
---
# <a name="how-to-install-gpu-support-in-model-builder"></a>如何在模型產生器中安裝 GPU 支援

瞭解如何安裝 GPU 驅動程式，以搭配使用您的 GPU 與模型產生器。

## <a name="prerequisites"></a>先決條件

- 模型產生器 Visual Studio 延伸模組。 擴充功能內建于16.6.1 版本的 Visual Studio。
- [模型產生器 VISUAL STUDIO GPU 支援延伸模組](https://marketplace.visualstudio.com/items?itemName=MLNET.ModelBuilderGPU)。
- 至少一個 CUDA 相容的 GPU。 如需相容的 Gpu 清單，請參閱 [NVIDIA 指南](https://developer.nvidia.com/cuda-gpus)。
- NVIDIA 開發人員帳戶。 如果您沒有訂用帳戶，請[建立免費帳戶](https://developer.nvidia.com/developer-program)。

## <a name="install-dependencies"></a>安裝相依性

1. 安裝 [CUDA 10.0](https://developer.nvidia.com/cuda-10.0-download-archive)。 請確定您安裝的是 CUDA 10.0，而不是任何其他較新的版本。 您不能安裝多個版本的 CUDA。
1. 安裝 [cuDNN v 7.6.4 FOR CUDA 10.0](https://developer.nvidia.com/rdp/cudnn-download)。 您不能安裝多個版本的 cuDNN。 下載 cuDNN v 7.6.4 zip 檔案並將它解壓縮之後，請複製 `<CUDNN_zip_files_path>\cuda\bin\cudnn64_7.dll` 到 `<YOUR_DRIVE>\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.0\bin` 。

## <a name="troubleshooting"></a>疑難排解

**如何? 知道我有什麼 GPU？**

遵循提供的指示：

1. 以滑鼠右鍵按一下桌面
1. 如果您在快顯視窗中看到「NVIDIA 主控台」或「NVIDIA 顯示器」，則會有 NVIDIA GPU
1. 按一下快顯視窗中的 [NVIDIA 主控台] 或 [NVIDIA Display]
1. 查看「圖形配接器資訊」
1. 您會看到 NVIDIA GPU 的名稱

**我看不到 NVIDIA 主控台 (或無法開啟) 但我知道有 NVIDIA GPU。**

1. 開啟 [裝置管理員]
1. 查看顯示配接器
1. 為您的 GPU 安裝適當的 [驅動程式](https://www.nvidia.com/drivers) 。
