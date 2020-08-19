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
# <a name="how-to-install-gpu-support-in-model-builder"></a><span data-ttu-id="e6d9f-103">如何在模型產生器中安裝 GPU 支援</span><span class="sxs-lookup"><span data-stu-id="e6d9f-103">How to install GPU support in Model Builder</span></span>

<span data-ttu-id="e6d9f-104">瞭解如何安裝 GPU 驅動程式，以搭配使用您的 GPU 與模型產生器。</span><span class="sxs-lookup"><span data-stu-id="e6d9f-104">Learn how to install the GPU drivers to use your GPU with Model Builder.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e6d9f-105">先決條件</span><span class="sxs-lookup"><span data-stu-id="e6d9f-105">Prerequisites</span></span>

- <span data-ttu-id="e6d9f-106">模型產生器 Visual Studio 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="e6d9f-106">Model Builder Visual Studio extension.</span></span> <span data-ttu-id="e6d9f-107">擴充功能內建于16.6.1 版本的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="e6d9f-107">The extension is built into Visual Studio as of version 16.6.1.</span></span>
- <span data-ttu-id="e6d9f-108">[模型產生器 VISUAL STUDIO GPU 支援延伸模組](https://marketplace.visualstudio.com/items?itemName=MLNET.ModelBuilderGPU)。</span><span class="sxs-lookup"><span data-stu-id="e6d9f-108">[Model Builder Visual Studio GPU support extension](https://marketplace.visualstudio.com/items?itemName=MLNET.ModelBuilderGPU).</span></span>
- <span data-ttu-id="e6d9f-109">至少一個 CUDA 相容的 GPU。</span><span class="sxs-lookup"><span data-stu-id="e6d9f-109">At least one CUDA compatible GPU.</span></span> <span data-ttu-id="e6d9f-110">如需相容的 Gpu 清單，請參閱 [NVIDIA 指南](https://developer.nvidia.com/cuda-gpus)。</span><span class="sxs-lookup"><span data-stu-id="e6d9f-110">For a list of compatible GPUs, see [NVIDIA's guide](https://developer.nvidia.com/cuda-gpus).</span></span>
- <span data-ttu-id="e6d9f-111">NVIDIA 開發人員帳戶。</span><span class="sxs-lookup"><span data-stu-id="e6d9f-111">NVIDIA developer account.</span></span> <span data-ttu-id="e6d9f-112">如果您沒有訂用帳戶，請[建立免費帳戶](https://developer.nvidia.com/developer-program)。</span><span class="sxs-lookup"><span data-stu-id="e6d9f-112">If you don't have one, [create a free account](https://developer.nvidia.com/developer-program).</span></span>

## <a name="install-dependencies"></a><span data-ttu-id="e6d9f-113">安裝相依性</span><span class="sxs-lookup"><span data-stu-id="e6d9f-113">Install dependencies</span></span>

1. <span data-ttu-id="e6d9f-114">安裝 [CUDA 10.0](https://developer.nvidia.com/cuda-10.0-download-archive)。</span><span class="sxs-lookup"><span data-stu-id="e6d9f-114">Install [CUDA v10.0](https://developer.nvidia.com/cuda-10.0-download-archive).</span></span> <span data-ttu-id="e6d9f-115">請確定您安裝的是 CUDA 10.0，而不是任何其他較新的版本。</span><span class="sxs-lookup"><span data-stu-id="e6d9f-115">Make sure you install CUDA v10.0, not any other newer version.</span></span> <span data-ttu-id="e6d9f-116">您不能安裝多個版本的 CUDA。</span><span class="sxs-lookup"><span data-stu-id="e6d9f-116">You cannot have multiple versions of CUDA installed.</span></span>
1. <span data-ttu-id="e6d9f-117">安裝 [cuDNN v 7.6.4 FOR CUDA 10.0](https://developer.nvidia.com/rdp/cudnn-download)。</span><span class="sxs-lookup"><span data-stu-id="e6d9f-117">Install [cuDNN v7.6.4 for CUDA 10.0](https://developer.nvidia.com/rdp/cudnn-download).</span></span> <span data-ttu-id="e6d9f-118">您不能安裝多個版本的 cuDNN。</span><span class="sxs-lookup"><span data-stu-id="e6d9f-118">You cannot have multiple versions of cuDNN installed.</span></span> <span data-ttu-id="e6d9f-119">下載 cuDNN v 7.6.4 zip 檔案並將它解壓縮之後，請複製 `<CUDNN_zip_files_path>\cuda\bin\cudnn64_7.dll` 到 `<YOUR_DRIVE>\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.0\bin` 。</span><span class="sxs-lookup"><span data-stu-id="e6d9f-119">After downloading cuDNN v7.6.4 zip file and unpacking it, copy `<CUDNN_zip_files_path>\cuda\bin\cudnn64_7.dll` to `<YOUR_DRIVE>\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.0\bin`.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="e6d9f-120">疑難排解</span><span class="sxs-lookup"><span data-stu-id="e6d9f-120">Troubleshooting</span></span>

<span data-ttu-id="e6d9f-121">**如何? 知道我有什麼 GPU？**</span><span class="sxs-lookup"><span data-stu-id="e6d9f-121">**How do I know what GPU I have?**</span></span>

<span data-ttu-id="e6d9f-122">遵循提供的指示：</span><span class="sxs-lookup"><span data-stu-id="e6d9f-122">Follow instructions provided:</span></span>

1. <span data-ttu-id="e6d9f-123">以滑鼠右鍵按一下桌面</span><span class="sxs-lookup"><span data-stu-id="e6d9f-123">Right-click on desktop</span></span>
1. <span data-ttu-id="e6d9f-124">如果您在快顯視窗中看到「NVIDIA 主控台」或「NVIDIA 顯示器」，則會有 NVIDIA GPU</span><span class="sxs-lookup"><span data-stu-id="e6d9f-124">If you see "NVIDIA Control Panel" or "NVIDIA Display" in the pop-up window, you have an NVIDIA GPU</span></span>
1. <span data-ttu-id="e6d9f-125">按一下快顯視窗中的 [NVIDIA 主控台] 或 [NVIDIA Display]</span><span class="sxs-lookup"><span data-stu-id="e6d9f-125">Click on "NVIDIA Control Panel" or "NVIDIA Display" in the pop-up window</span></span>
1. <span data-ttu-id="e6d9f-126">查看「圖形配接器資訊」</span><span class="sxs-lookup"><span data-stu-id="e6d9f-126">Look at "Graphics Card Information"</span></span>
1. <span data-ttu-id="e6d9f-127">您會看到 NVIDIA GPU 的名稱</span><span class="sxs-lookup"><span data-stu-id="e6d9f-127">You will see the name of your NVIDIA GPU</span></span>

<span data-ttu-id="e6d9f-128">**我看不到 NVIDIA 主控台 (或無法開啟) 但我知道有 NVIDIA GPU。**</span><span class="sxs-lookup"><span data-stu-id="e6d9f-128">**I don't see NVIDIA Control Panel (or it fails to open) but I know I have an NVIDIA GPU.**</span></span>

1. <span data-ttu-id="e6d9f-129">開啟 [裝置管理員]</span><span class="sxs-lookup"><span data-stu-id="e6d9f-129">Open Device Manager</span></span>
1. <span data-ttu-id="e6d9f-130">查看顯示配接器</span><span class="sxs-lookup"><span data-stu-id="e6d9f-130">Look at Display adapters</span></span>
1. <span data-ttu-id="e6d9f-131">為您的 GPU 安裝適當的 [驅動程式](https://www.nvidia.com/drivers) 。</span><span class="sxs-lookup"><span data-stu-id="e6d9f-131">Install appropriate [driver](https://www.nvidia.com/drivers) for your GPU.</span></span>
