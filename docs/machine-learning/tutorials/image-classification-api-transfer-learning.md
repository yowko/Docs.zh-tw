---
title: 教學:使用轉移學習進行自動目檢視
description: 本教程演示了如何使用傳輸學習在ML.NET使用圖像檢測 API 訓練 TensorFlow 深度學習模型,將混凝土表面的圖像分類為破裂或未破裂。
author: luisquintanilla
ms.author: luquinta
ms.date: 12/12/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: a050d7673f7ef00cf11d959d04e709222cb2be8f
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607554"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a><span data-ttu-id="4deed-103">教學:使用ML.NET影像類別 API 使用傳輸學習進行自動目視檢查</span><span class="sxs-lookup"><span data-stu-id="4deed-103">Tutorial: Automated visual inspection using transfer learning with the ML.NET Image Classification API</span></span>

<span data-ttu-id="4deed-104">瞭解如何使用轉移學習、預先訓練的 TensorFlow 模型和ML.NET圖像分類 API 來訓練自定義深度學習模型,將混凝土表面的圖像分類為破裂或未開裂。</span><span class="sxs-lookup"><span data-stu-id="4deed-104">Learn how to train a custom deep learning model using transfer learning, a pretrained TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="4deed-105">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="4deed-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="4deed-106">了解問題</span><span class="sxs-lookup"><span data-stu-id="4deed-106">Understand the problem</span></span>
> - <span data-ttu-id="4deed-107">瞭解ML.NET映像類別 API</span><span class="sxs-lookup"><span data-stu-id="4deed-107">Learn about ML.NET Image Classification API</span></span>
> - <span data-ttu-id="4deed-108">瞭解預先訓練的模型</span><span class="sxs-lookup"><span data-stu-id="4deed-108">Understand the pretrained model</span></span>
> - <span data-ttu-id="4deed-109">使用轉移學習訓練自訂 TensorFlow 影像分類模型</span><span class="sxs-lookup"><span data-stu-id="4deed-109">Use transfer learning to train a custom TensorFlow image classification model</span></span>
> - <span data-ttu-id="4deed-110">使用自訂模型對影像進行類別</span><span class="sxs-lookup"><span data-stu-id="4deed-110">Classify images with the custom model</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4deed-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="4deed-111">Prerequisites</span></span>

- <span data-ttu-id="4deed-112">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)或更高版本或 Visual Studio 2017 版本 15.6 或更高版本,安裝了".NET 核心跨平臺開發「工作負載。</span><span class="sxs-lookup"><span data-stu-id="4deed-112">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="image-classification-transfer-learning-sample-overview"></a><span data-ttu-id="4deed-113">影像分類傳輸學習範例概述</span><span class="sxs-lookup"><span data-stu-id="4deed-113">Image classification transfer learning sample overview</span></span>

<span data-ttu-id="4deed-114">此示例是 C# .NET 核心主控台應用程式,該應用程式使用預先訓練的深入學習 TensorFlow 模型對圖像進行分類。</span><span class="sxs-lookup"><span data-stu-id="4deed-114">This sample is a C# .NET Core console application that classifies images using a pretrained deep learning TensorFlow model.</span></span> <span data-ttu-id="4deed-115">您可以在 GitHub 的 [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) 找到此範例的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4deed-115">The code for this sample can be found on the [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="4deed-116">了解問題</span><span class="sxs-lookup"><span data-stu-id="4deed-116">Understand the problem</span></span>

<span data-ttu-id="4deed-117">圖像分類是計算機視覺問題。</span><span class="sxs-lookup"><span data-stu-id="4deed-117">Image classification is a computer vision problem.</span></span> <span data-ttu-id="4deed-118">圖像分類將圖像作為輸入,並將其分類為指定的類。</span><span class="sxs-lookup"><span data-stu-id="4deed-118">Image classification takes an image as input and categorizes it into a prescribed class.</span></span> <span data-ttu-id="4deed-119">影像分類有用的一些方案包括:</span><span class="sxs-lookup"><span data-stu-id="4deed-119">Some scenarios where image classification is useful include:</span></span>

- <span data-ttu-id="4deed-120">臉部辨識</span><span class="sxs-lookup"><span data-stu-id="4deed-120">Facial recognition</span></span>
- <span data-ttu-id="4deed-121">情緒偵測</span><span class="sxs-lookup"><span data-stu-id="4deed-121">Emotion detection</span></span>
- <span data-ttu-id="4deed-122">醫療診斷</span><span class="sxs-lookup"><span data-stu-id="4deed-122">Medical diagnosis</span></span>
- <span data-ttu-id="4deed-123">地標檢測</span><span class="sxs-lookup"><span data-stu-id="4deed-123">Landmark detection</span></span>

<span data-ttu-id="4deed-124">本教程將訓練自定義圖像分類模型,以對橋面進行自動目視檢查,以識別被裂縫損壞的結構。</span><span class="sxs-lookup"><span data-stu-id="4deed-124">This tutorial trains a custom image classification model to perform automated visual inspection of bridge decks to identify structures that are damaged by cracks.</span></span>

## <a name="mlnet-image-classification-api"></a><span data-ttu-id="4deed-125">ML.NET影像類別 API</span><span class="sxs-lookup"><span data-stu-id="4deed-125">ML.NET Image Classification API</span></span>

<span data-ttu-id="4deed-126">ML.NET提供了執行圖像分類的各種方法。</span><span class="sxs-lookup"><span data-stu-id="4deed-126">ML.NET provides various ways of performing image classification.</span></span> <span data-ttu-id="4deed-127">本教學使用圖像分類 API 應用傳輸學習。</span><span class="sxs-lookup"><span data-stu-id="4deed-127">This tutorial applies transfer learning using the Image Classification API.</span></span> <span data-ttu-id="4deed-128">圖像分類 API 使用[TensorFlow.NET,](https://github.com/SciSharp/TensorFlow.NET)這是一個為 TensorFlow C++ API 提供 C# 綁定的低級庫。</span><span class="sxs-lookup"><span data-stu-id="4deed-128">The Image Classification API makes use of [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), a low-level library that provides C# bindings for the TensorFlow C++ API.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="4deed-129">什麼是傳輸學習？</span><span class="sxs-lookup"><span data-stu-id="4deed-129">What is transfer learning?</span></span>

<span data-ttu-id="4deed-130">轉移學習將從解決一個問題中獲得的知識應用於另一個相關問題。</span><span class="sxs-lookup"><span data-stu-id="4deed-130">Transfer learning applies knowledge gained from solving one problem to another related problem.</span></span>

<span data-ttu-id="4deed-131">從頭開始訓練深度學習模型需要設置多個參數、大量標記的訓練數據以及大量的計算資源(數百個 GPU 小時)。</span><span class="sxs-lookup"><span data-stu-id="4deed-131">Training a deep learning model from scratch requires setting several parameters, a large amount of labeled training data, and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="4deed-132">使用預訓練的模型以及轉移學習允許您縮短培訓過程。</span><span class="sxs-lookup"><span data-stu-id="4deed-132">Using a pretrained model along with transfer learning allows you to shortcut the training process.</span></span>

## <a name="training-process"></a><span data-ttu-id="4deed-133">培訓流程</span><span class="sxs-lookup"><span data-stu-id="4deed-133">Training process</span></span>

<span data-ttu-id="4deed-134">圖像分類 API 透過載入預先訓練的 TensorFlow 模型來啟動培訓過程。</span><span class="sxs-lookup"><span data-stu-id="4deed-134">The Image Classification API starts the training process by loading a pretrained TensorFlow model.</span></span> <span data-ttu-id="4deed-135">培訓過程包括兩個步驟:</span><span class="sxs-lookup"><span data-stu-id="4deed-135">The training process consists of two steps:</span></span>

1. <span data-ttu-id="4deed-136">瓶頸階段</span><span class="sxs-lookup"><span data-stu-id="4deed-136">Bottleneck phase</span></span>
2. <span data-ttu-id="4deed-137">培訓階段</span><span class="sxs-lookup"><span data-stu-id="4deed-137">Training phase</span></span>

![培訓步驟](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a><span data-ttu-id="4deed-139">瓶頸階段</span><span class="sxs-lookup"><span data-stu-id="4deed-139">Bottleneck phase</span></span>

<span data-ttu-id="4deed-140">在瓶頸階段,將載入訓練圖像集,並將圖元值用作預訓練模型的凍結圖層的輸入或要素。</span><span class="sxs-lookup"><span data-stu-id="4deed-140">During the bottleneck phase, the set of training images is loaded and the pixel values are used as input, or features, for the frozen layers of the pretrained model.</span></span> <span data-ttu-id="4deed-141">凍結層包括神經網路中的所有圖層,直達倒數第二層,非正式地稱為瓶頸層。</span><span class="sxs-lookup"><span data-stu-id="4deed-141">The frozen layers include all of the layers in the neural network up to the penultimate layer, informally known as the bottleneck layer.</span></span> <span data-ttu-id="4deed-142">這些層稱為凍結層,因為這些層上不會發生任何訓練,並且操作是傳遞的。</span><span class="sxs-lookup"><span data-stu-id="4deed-142">These layers are referred to as frozen because no training will occur on these layers and operations are pass-through.</span></span> <span data-ttu-id="4deed-143">在這些凍結層中,計算有助於模型區分不同類的較低級別的模式。</span><span class="sxs-lookup"><span data-stu-id="4deed-143">It's at these frozen layers where the lower-level patterns that help a model differentiate between the different classes are computed.</span></span> <span data-ttu-id="4deed-144">圖層數越大,此步驟的計算密集程度就越高。</span><span class="sxs-lookup"><span data-stu-id="4deed-144">The larger the number of layers, the more computationally intensive this step is.</span></span> <span data-ttu-id="4deed-145">幸運的是,由於這是一次性計算,因此在試驗不同參數時,可以緩存結果並在以後的運行中使用。</span><span class="sxs-lookup"><span data-stu-id="4deed-145">Fortunately, since this is a one-time calculation, the results can be cached and used in later runs when experimenting with different parameters.</span></span>

### <a name="training-phase"></a><span data-ttu-id="4deed-146">培訓階段</span><span class="sxs-lookup"><span data-stu-id="4deed-146">Training phase</span></span>

<span data-ttu-id="4deed-147">計算瓶頸階段的輸出值后,它們將用作輸入來重新訓練模型的最終層。</span><span class="sxs-lookup"><span data-stu-id="4deed-147">Once the output values from the bottleneck phase are computed, they are used as input to retrain the final layer of the model.</span></span> <span data-ttu-id="4deed-148">此過程是反覆運算的,並且運行模型參數指定的次數。</span><span class="sxs-lookup"><span data-stu-id="4deed-148">This process is iterative and runs for the number of times specified by model parameters.</span></span> <span data-ttu-id="4deed-149">每次運行期間,都會評估損耗和準確性。</span><span class="sxs-lookup"><span data-stu-id="4deed-149">During each run, the loss and accuracy are evaluated.</span></span> <span data-ttu-id="4deed-150">然後,進行適當的調整,以改進模型,以最小化損失和最大化精度。</span><span class="sxs-lookup"><span data-stu-id="4deed-150">Then, the appropriate adjustments are made to improve the model with the goal of minimizing the loss and maximizing the accuracy.</span></span> <span data-ttu-id="4deed-151">培訓完成後,將輸出兩種模型格式。</span><span class="sxs-lookup"><span data-stu-id="4deed-151">Once training is finished, two model formats are output.</span></span> <span data-ttu-id="4deed-152">其中之一是`.pb`模型的版本,另一個是模型的`.zip`ML.NET 序列化版本。</span><span class="sxs-lookup"><span data-stu-id="4deed-152">One of them is the `.pb` version of the model and the other is the `.zip` ML.NET serialized version of the model.</span></span> <span data-ttu-id="4deed-153">在ML.NET支援的環境中工作時,建議使用模型`.zip`的版本。</span><span class="sxs-lookup"><span data-stu-id="4deed-153">When working in environments supported by ML.NET, it is recommended to use the `.zip` version of the model.</span></span> <span data-ttu-id="4deed-154">但是,在不支援ML.NET的環境中,您可以選擇使用`.pb`版本。</span><span class="sxs-lookup"><span data-stu-id="4deed-154">However, in environments where ML.NET is not supported, you have the option of using the `.pb` version.</span></span>

## <a name="understand-the-pretrained-model"></a><span data-ttu-id="4deed-155">瞭解預先訓練的模型</span><span class="sxs-lookup"><span data-stu-id="4deed-155">Understand the pretrained model</span></span>

<span data-ttu-id="4deed-156">本教學中使用的預訓練模型是剩餘網路 (ResNet) v2 模型的 101 層變體。</span><span class="sxs-lookup"><span data-stu-id="4deed-156">The pretrained model used in this tutorial is the 101-layer variant of the Residual Network (ResNet) v2 model.</span></span> <span data-ttu-id="4deed-157">原始模型經過培訓,將圖像分類為一千個類別。</span><span class="sxs-lookup"><span data-stu-id="4deed-157">The original model is trained to classify images into a thousand categories.</span></span> <span data-ttu-id="4deed-158">該模型以大小 224 x 224 的圖像為輸入,並輸出所訓練的每個類的類概率。</span><span class="sxs-lookup"><span data-stu-id="4deed-158">The model takes as input an image of size 224 x 224 and outputs the class probabilities for each of the classes it's trained on.</span></span> <span data-ttu-id="4deed-159">此模型的一部分用於使用自定義圖像在兩個類之間進行預測來訓練新模型。</span><span class="sxs-lookup"><span data-stu-id="4deed-159">Part of this model is used to train a new model using custom images to make predictions between two classes.</span></span>

## <a name="create-console-application"></a><span data-ttu-id="4deed-160">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="4deed-160">Create console application</span></span>

<span data-ttu-id="4deed-161">現在,您已經瞭解了傳輸學習和圖像分類 API,是時候構建應用程式了。</span><span class="sxs-lookup"><span data-stu-id="4deed-161">Now that you have a general understanding of transfer learning and the Image Classification API, it's time to build the application.</span></span>

1. <span data-ttu-id="4deed-162">創建**C# .NET 核心控制台應用程式**,稱為"DeepLearning_ImageClassification_Binary"。</span><span class="sxs-lookup"><span data-stu-id="4deed-162">Create a **C# .NET Core Console Application** called "DeepLearning_ImageClassification_Binary".</span></span>
1. <span data-ttu-id="4deed-163">安裝**Microsoft.ML**Microsoft.ML**版本 1.4.0** NuGet 套件:</span><span class="sxs-lookup"><span data-stu-id="4deed-163">Install the **Microsoft.ML** version **1.4.0** NuGet Package:</span></span>
    1. <span data-ttu-id="4deed-164">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4deed-164">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="4deed-165">選擇「nuget.org」作為包源。</span><span class="sxs-lookup"><span data-stu-id="4deed-165">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="4deed-166">選取 [瀏覽]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="4deed-166">Select the **Browse** tab.</span></span>
    1. <span data-ttu-id="4deed-167">選中包含**預先發佈**「複選框」。</span><span class="sxs-lookup"><span data-stu-id="4deed-167">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="4deed-168">搜尋**Microsoft.ML**。</span><span class="sxs-lookup"><span data-stu-id="4deed-168">Search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="4deed-169">選取 [安裝]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4deed-169">Select the **Install** button.</span></span>
    1. <span data-ttu-id="4deed-170">在 [預覽變更]\*\*\*\* 對話方塊上，選取 [確定]\*\*\*\* 按鈕，然後在 [授權接受]\*\*\*\* 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4deed-170">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="4deed-171">對**Microsoft.ML.Vision**版本 1.4.0、SciSharp.TensorFlow.Redist 版本**1.15.0**和**Microsoft.ML.ImageAnalytics**版本**1.4.0** NuGet 包重複這些步驟。 **1.4.0** **SciSharp.TensorFlow.Redist**</span><span class="sxs-lookup"><span data-stu-id="4deed-171">Repeat these steps for the **Microsoft.ML.Vision** version **1.4.0**, **SciSharp.TensorFlow.Redist** version **1.15.0**, and **Microsoft.ML.ImageAnalytics** version **1.4.0** NuGet packages.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="4deed-172">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="4deed-172">Prepare and understand the data</span></span>

> [!NOTE]
> <span data-ttu-id="4deed-173">本教程的數據集來自馬奎爾,馬克;多拉夫山,薩塔爾;和湯瑪斯,羅伯特J.,"SDNET2018:機器學習應用的具體裂紋圖像數據集"(2018年)。</span><span class="sxs-lookup"><span data-stu-id="4deed-173">The datasets for this tutorial are from Maguire, Marc; Dorafshan, Sattar; and Thomas, Robert J., "SDNET2018: A concrete crack image dataset for machine learning applications" (2018).</span></span> <span data-ttu-id="4deed-174">瀏覽所有數據集。</span><span class="sxs-lookup"><span data-stu-id="4deed-174">Browse all Datasets.</span></span> <span data-ttu-id="4deed-175">紙 48.</span><span class="sxs-lookup"><span data-stu-id="4deed-175">Paper 48.</span></span> <span data-ttu-id="4deed-176">https://digitalcommons.usu.edu/all_datasets/48</span><span class="sxs-lookup"><span data-stu-id="4deed-176">https://digitalcommons.usu.edu/all_datasets/48</span></span>

<span data-ttu-id="4deed-177">SDNET2018 是一個圖像數據集,包含開裂和非開裂混凝土結構(橋面、牆壁和路面)的註釋。</span><span class="sxs-lookup"><span data-stu-id="4deed-177">SDNET2018 is an image dataset that contains annotations for cracked and non-cracked concrete structures (bridge decks, walls, and pavement).</span></span>

![SDNET2018 資料集橋面範例](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

<span data-ttu-id="4deed-179">資料分為三個子目錄:</span><span class="sxs-lookup"><span data-stu-id="4deed-179">The data is organized in three subdirectories:</span></span>

- <span data-ttu-id="4deed-180">D 包含橋面影像</span><span class="sxs-lookup"><span data-stu-id="4deed-180">D contains bridge deck images</span></span>
- <span data-ttu-id="4deed-181">P 包含路面影像</span><span class="sxs-lookup"><span data-stu-id="4deed-181">P contains pavement images</span></span>
- <span data-ttu-id="4deed-182">W 包含牆影像</span><span class="sxs-lookup"><span data-stu-id="4deed-182">W contains wall images</span></span>

<span data-ttu-id="4deed-183">每個子目錄包含兩個額外的預固定子目錄:</span><span class="sxs-lookup"><span data-stu-id="4deed-183">Each of these subdirectories contains two additional prefixed subdirectories:</span></span>

- <span data-ttu-id="4deed-184">C 是用於破裂曲面的前置字串</span><span class="sxs-lookup"><span data-stu-id="4deed-184">C is the prefix used for cracked surfaces</span></span>
- <span data-ttu-id="4deed-185">U 是用於未開裂曲面的前置字串</span><span class="sxs-lookup"><span data-stu-id="4deed-185">U is the prefix used for uncracked surfaces</span></span>

<span data-ttu-id="4deed-186">在本教程中,僅使用橋面圖像。</span><span class="sxs-lookup"><span data-stu-id="4deed-186">In this tutorial, only bridge deck images are used.</span></span>

1. <span data-ttu-id="4deed-187">下載[數據集](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip)並解壓縮。</span><span class="sxs-lookup"><span data-stu-id="4deed-187">Download the [dataset](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) and unzip.</span></span>
1. <span data-ttu-id="4deed-188">在專案中創建名為「資產」的目錄以保存數據集檔。</span><span class="sxs-lookup"><span data-stu-id="4deed-188">Create a directory named "assets" in your project to save your dataset files.</span></span>
1. <span data-ttu-id="4deed-189">將*CD*和*UD*子目錄從最近解壓縮的目錄複製到*資產*目錄。</span><span class="sxs-lookup"><span data-stu-id="4deed-189">Copy the *CD* and *UD* subdirectories from the recently unzipped directory to the *assets* directory.</span></span>

### <a name="create-input-and-output-classes"></a><span data-ttu-id="4deed-190">建立輸入與輸出類別</span><span class="sxs-lookup"><span data-stu-id="4deed-190">Create input and output classes</span></span>

1. <span data-ttu-id="4deed-191">開啟*Program.cs*檔案,並將檔案頂部的`using`現有 語句取代為以下內容:</span><span class="sxs-lookup"><span data-stu-id="4deed-191">Open the *Program.cs* file and replace the existing `using` statements at the top of the file with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L1-L7)]

1. <span data-ttu-id="4deed-192">在Program.cs`Program`的*Program.cs*類 下面,創建一`ImageData`個名為的類。</span><span class="sxs-lookup"><span data-stu-id="4deed-192">Below the `Program` class in *Program.cs*, create a class called `ImageData`.</span></span> <span data-ttu-id="4deed-193">此類用於表示最初載入的數據。</span><span class="sxs-lookup"><span data-stu-id="4deed-193">This class is used to represent the initially loaded data.</span></span>

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L137-L142)]

    <span data-ttu-id="4deed-194">`ImageData`引入以下屬性:</span><span class="sxs-lookup"><span data-stu-id="4deed-194">`ImageData` contains the following properties:</span></span>

    - <span data-ttu-id="4deed-195">`ImagePath`是存儲映射的完全限定路徑。</span><span class="sxs-lookup"><span data-stu-id="4deed-195">`ImagePath` is the fully qualified path where the image is stored.</span></span>
    - <span data-ttu-id="4deed-196">`Label`是圖像所屬的類別。</span><span class="sxs-lookup"><span data-stu-id="4deed-196">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="4deed-197">這是要預測的值。</span><span class="sxs-lookup"><span data-stu-id="4deed-197">This is the value to predict.</span></span>

1. <span data-ttu-id="4deed-198">為輸入與輸出資料建立類別</span><span class="sxs-lookup"><span data-stu-id="4deed-198">Create classes for your input and output data</span></span>

    1. <span data-ttu-id="4deed-199">在類`ImageData`下面,在`ModelInput`稱為的新類中定義輸入數據的架構。</span><span class="sxs-lookup"><span data-stu-id="4deed-199">Below the `ImageData` class, define the schema of your input data in a new class called `ModelInput`.</span></span>

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L144-L153)]

        <span data-ttu-id="4deed-200">`ModelInput`引入以下屬性:</span><span class="sxs-lookup"><span data-stu-id="4deed-200">`ModelInput` contains the following properties:</span></span>

        - <span data-ttu-id="4deed-201">`Image`是`byte[]`圖像的表示形式。</span><span class="sxs-lookup"><span data-stu-id="4deed-201">`Image` is the `byte[]` representation of the image.</span></span> <span data-ttu-id="4deed-202">模型希望圖像數據為此類訓練。</span><span class="sxs-lookup"><span data-stu-id="4deed-202">The model expects image data to be of this type for training.</span></span>
        - <span data-ttu-id="4deed-203">`LabelAsKey`是的數位`Label`表示形式。</span><span class="sxs-lookup"><span data-stu-id="4deed-203">`LabelAsKey` is the numerical representation of the `Label`.</span></span>
        - <span data-ttu-id="4deed-204">`ImagePath`是存儲映射的完全限定路徑。</span><span class="sxs-lookup"><span data-stu-id="4deed-204">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="4deed-205">`Label`是圖像所屬的類別。</span><span class="sxs-lookup"><span data-stu-id="4deed-205">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="4deed-206">這是要預測的值。</span><span class="sxs-lookup"><span data-stu-id="4deed-206">This is the value to predict.</span></span>

        <span data-ttu-id="4deed-207">僅用於`Image`和`LabelAsKey`用於訓練模型和進行預測。</span><span class="sxs-lookup"><span data-stu-id="4deed-207">Only `Image` and `LabelAsKey` are used to train the model and make predictions.</span></span> <span data-ttu-id="4deed-208">保留`ImagePath``Label`和 屬性是為了方便存取原始影像檔名和類別。</span><span class="sxs-lookup"><span data-stu-id="4deed-208">The `ImagePath` and `Label` properties are kept for convenience to access the original image file name and category.</span></span>

    1. <span data-ttu-id="4deed-209">然後,在類`ModelInput`下方,在名為`ModelOutput`的新類中定義輸出數據的架構。</span><span class="sxs-lookup"><span data-stu-id="4deed-209">Then, below the `ModelInput` class, define the schema of your output data in a new class called `ModelOutput`.</span></span>

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L155-L162)]

        <span data-ttu-id="4deed-210">`ModelOutput`引入以下屬性:</span><span class="sxs-lookup"><span data-stu-id="4deed-210">`ModelOutput` contains the following properties:</span></span>

        - <span data-ttu-id="4deed-211">`ImagePath`是存儲映射的完全限定路徑。</span><span class="sxs-lookup"><span data-stu-id="4deed-211">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="4deed-212">`Label`是圖像所屬的原始類別。</span><span class="sxs-lookup"><span data-stu-id="4deed-212">`Label` is the original category the image belongs to.</span></span> <span data-ttu-id="4deed-213">這是要預測的值。</span><span class="sxs-lookup"><span data-stu-id="4deed-213">This is the value to predict.</span></span>
        - <span data-ttu-id="4deed-214">`PredictedLabel`是模型預測的值。</span><span class="sxs-lookup"><span data-stu-id="4deed-214">`PredictedLabel` is the value predicted by the model.</span></span>

        <span data-ttu-id="4deed-215">與`ModelInput`類似`PredictedLabel`, 只有 進行預測所需的 ,因為它包含模型所做的預測。</span><span class="sxs-lookup"><span data-stu-id="4deed-215">Similar to `ModelInput`, only the `PredictedLabel` is required to make predictions since it contains the prediction made by the model.</span></span> <span data-ttu-id="4deed-216">保留`ImagePath``Label`和 屬性是為了方便存取原始映像檔名和類別。</span><span class="sxs-lookup"><span data-stu-id="4deed-216">The `ImagePath` and `Label` properties are retained for convenience to access the original image file name and category.</span></span>

### <a name="create-workspace-directory"></a><span data-ttu-id="4deed-217">建立工作區目錄</span><span class="sxs-lookup"><span data-stu-id="4deed-217">Create workspace directory</span></span>

<span data-ttu-id="4deed-218">當訓練和驗證數據不經常更改時,最好緩存計算的瓶頸值以進行進一步運行。</span><span class="sxs-lookup"><span data-stu-id="4deed-218">When training and validation data do not change often, it is good practice to cache the computed bottleneck values for further runs.</span></span>

1. <span data-ttu-id="4deed-219">在專案中,創建一個名為*工作區*的新目錄來存儲計算的瓶頸`.pb`值和模型版本。</span><span class="sxs-lookup"><span data-stu-id="4deed-219">In your project, create a new directory called *workspace* to store the computed bottleneck values and `.pb` version of the model.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="4deed-220">定義路徑並初始化變數</span><span class="sxs-lookup"><span data-stu-id="4deed-220">Define paths and initialize variables</span></span>

1. <span data-ttu-id="4deed-221">在方法`Main`內,定義資產的位置、計算的瓶頸值`.pb`和模型的版本。</span><span class="sxs-lookup"><span data-stu-id="4deed-221">Inside the `Main` method, define the location of your assets, computed bottleneck values and `.pb` version of the model.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L15-L17)]

1. <span data-ttu-id="4deed-222">使用`mlContext`[MLContext](xref:Microsoft.ML.MLContext)的新實例初始化變數。</span><span class="sxs-lookup"><span data-stu-id="4deed-222">Initialize the `mlContext` variable with a new instance of [MLContext](xref:Microsoft.ML.MLContext).</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L19)]

    <span data-ttu-id="4deed-223">[MLContext](xref:Microsoft.ML.MLContext)類別是所有ML.NET操作的起點,初始化 mlContext可建立可在模型建立工作流對象之間共用的新ML.NET環境。</span><span class="sxs-lookup"><span data-stu-id="4deed-223">The [MLContext](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="4deed-224">就概念而言，類似於 Entity Framework 中的 `DBContext`。</span><span class="sxs-lookup"><span data-stu-id="4deed-224">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="4deed-225">載入資料</span><span class="sxs-lookup"><span data-stu-id="4deed-225">Load the data</span></span>

### <a name="create-data-loading-utility-method"></a><span data-ttu-id="4deed-226">建立資料載入實用程式方法</span><span class="sxs-lookup"><span data-stu-id="4deed-226">Create data loading utility method</span></span>

<span data-ttu-id="4deed-227">圖像存儲在兩個子目錄中。</span><span class="sxs-lookup"><span data-stu-id="4deed-227">The images are stored in two subdirectories.</span></span> <span data-ttu-id="4deed-228">在載入資料之前,需要將其格式化為`ImageData`物件清單。</span><span class="sxs-lookup"><span data-stu-id="4deed-228">Before loading the data, it needs to be formatted into a list of `ImageData` objects.</span></span> <span data-ttu-id="4deed-229">為此,請建立`LoadImagesFromDirectory``Main`方法下方的方法。</span><span class="sxs-lookup"><span data-stu-id="4deed-229">To do so, create the `LoadImagesFromDirectory` method below the `Main` method.</span></span>

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. <span data-ttu-id="4deed-230">新增`LoadImagesDirectory`以下代碼以從子目錄取得所有檔案路徑:</span><span class="sxs-lookup"><span data-stu-id="4deed-230">Inside the `LoadImagesDirectory` add the following code to get all of the file paths from the subdirectories:</span></span>

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L104-L105)]

1. <span data-ttu-id="4deed-231">然後,使用`foreach`語句反覆運算每個檔。</span><span class="sxs-lookup"><span data-stu-id="4deed-231">Then, iterate through each of the files using a `foreach` statement.</span></span>

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. <span data-ttu-id="4deed-232">在`foreach`語句中,檢查檔副檔名受支援。</span><span class="sxs-lookup"><span data-stu-id="4deed-232">Inside the `foreach` statement, check that the file extensions are supported.</span></span> <span data-ttu-id="4deed-233">圖像分類 API 支援 JPEG 和 PNG 格式。</span><span class="sxs-lookup"><span data-stu-id="4deed-233">The Image Classification API supports JPEG and PNG formats.</span></span>

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L109-L110)]

1. <span data-ttu-id="4deed-234">然後,獲取文件的標籤。</span><span class="sxs-lookup"><span data-stu-id="4deed-234">Then, get the label for the file.</span></span> <span data-ttu-id="4deed-235">如果參數`useFolderNameAsLabel`設定`true`為 ,則保存檔的父目錄將用作標籤。</span><span class="sxs-lookup"><span data-stu-id="4deed-235">If the `useFolderNameAsLabel` parameter is set to `true`, then the parent directory where the file is saved is used as the label.</span></span> <span data-ttu-id="4deed-236">否則,它期望標籤是檔名或檔名本身的首碼。</span><span class="sxs-lookup"><span data-stu-id="4deed-236">Otherwise, it expects the label to be a prefix of the file name or the file name itself.</span></span>

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L112-L126)]

1. <span data-ttu-id="4deed-237">最後,創建`ModelInput`的新實例。</span><span class="sxs-lookup"><span data-stu-id="4deed-237">Finally, create a new instance of `ModelInput`.</span></span>

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L128-L132)]

### <a name="prepare-the-data"></a><span data-ttu-id="4deed-238">準備資料</span><span class="sxs-lookup"><span data-stu-id="4deed-238">Prepare the data</span></span>

1. <span data-ttu-id="4deed-239">回到方法中`Main`,`LoadFromDirectory`使用實用程式方法獲取用於訓練的圖像清單。</span><span class="sxs-lookup"><span data-stu-id="4deed-239">Back in the `Main` method, use the `LoadFromDirectory` utility method to get the list of images used for training.</span></span>

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L21)]

1. <span data-ttu-id="4deed-240">然後,使用方法將影像[`IDataView`](xref:Microsoft.ML.IDataView)載入[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*)。</span><span class="sxs-lookup"><span data-stu-id="4deed-240">Then, load the images into an [`IDataView`](xref:Microsoft.ML.IDataView) using the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method.</span></span>

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L23)]

1. <span data-ttu-id="4deed-241">數據按從目錄中讀取的順序載入。</span><span class="sxs-lookup"><span data-stu-id="4deed-241">The data is loaded in the order it was read from the directories.</span></span> <span data-ttu-id="4deed-242">要平衡數據,請使用方法[`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*)隨機排列數據。</span><span class="sxs-lookup"><span data-stu-id="4deed-242">To balance the data, shuffle it using the [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) method.</span></span>

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L25)]

1. <span data-ttu-id="4deed-243">機器學習模型期望輸入以數位格式。</span><span class="sxs-lookup"><span data-stu-id="4deed-243">Machine learning models expect input to be in numerical format.</span></span> <span data-ttu-id="4deed-244">因此,在培訓之前,需要對數據進行一些預處理。</span><span class="sxs-lookup"><span data-stu-id="4deed-244">Therefore, some preprocessing needs to be done on the data prior to training.</span></span> <span data-ttu-id="4deed-245">創建由[`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601)和[`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*)`LoadRawImageBytes`轉換組成的一個組成。</span><span class="sxs-lookup"><span data-stu-id="4deed-245">Create an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) made up of the [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) and `LoadRawImageBytes` transforms.</span></span> <span data-ttu-id="4deed-246">轉換`MapValueToKey``Label`採用 列中的分類值,將其轉換為`KeyType`數值 並將其`LabelAsKey`存儲在稱為 的新列中。</span><span class="sxs-lookup"><span data-stu-id="4deed-246">The `MapValueToKey` transform takes the categorical value in the `Label` column, converts it to a numerical `KeyType` value and stores it in a new column called `LabelAsKey`.</span></span> <span data-ttu-id="4deed-247">從列獲取值以及參數以`imageFolder`載入用於定型的圖像。 `ImagePath` `LoadImages`</span><span class="sxs-lookup"><span data-stu-id="4deed-247">The `LoadImages` takes the values from the `ImagePath` column along with the `imageFolder` parameter to load images for training.</span></span>

    [!code-csharp [PreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L27-L33)]

1. <span data-ttu-id="4deed-248">使用[`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*)方法將資料應用`preprocessingPipeline`[`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601)於 後[`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*)跟的方法 ,該方法傳回包含[`IDataView`](xref:Microsoft.ML.IDataView)預處理資料的 。</span><span class="sxs-lookup"><span data-stu-id="4deed-248">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to apply the data to the `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) followed by the [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) method, which returns an [`IDataView`](xref:Microsoft.ML.IDataView) containing the pre-processed data.</span></span>

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L35-L37)]

1. <span data-ttu-id="4deed-249">要訓練模型,必須擁有訓練數據集和驗證數據集。</span><span class="sxs-lookup"><span data-stu-id="4deed-249">To train a model, it's important to have a training dataset as well as a validation dataset.</span></span> <span data-ttu-id="4deed-250">模型在培訓集上進行了培訓。</span><span class="sxs-lookup"><span data-stu-id="4deed-250">The model is trained on the training set.</span></span> <span data-ttu-id="4deed-251">對看不見的數據進行預測的績效由根據驗證集的性能來衡量。</span><span class="sxs-lookup"><span data-stu-id="4deed-251">How well it makes predictions on unseen data is measured by the performance against the validation set.</span></span> <span data-ttu-id="4deed-252">根據該性能的結果,模型會根據所學知識進行調整,以努力改進。</span><span class="sxs-lookup"><span data-stu-id="4deed-252">Based on the results of that performance, the model makes adjustments to what it has learned in an effort to improve.</span></span> <span data-ttu-id="4deed-253">驗證集可能來自拆分原始數據集或已為此預留的另一個源。</span><span class="sxs-lookup"><span data-stu-id="4deed-253">The validation set can come from either splitting your original dataset or from another source that has already been set aside for this purpose.</span></span> <span data-ttu-id="4deed-254">在這種情況下,預處理的數據集將拆分為訓練、驗證和測試集。</span><span class="sxs-lookup"><span data-stu-id="4deed-254">In this case, the pre-processed dataset is split into training, validation and test sets.</span></span>

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L39-L40)]

    <span data-ttu-id="4deed-255">上面的代碼示例執行兩個拆分。</span><span class="sxs-lookup"><span data-stu-id="4deed-255">The code sample above performs two splits.</span></span> <span data-ttu-id="4deed-256">首先,預處理的數據被拆分,70% 用於培訓,其餘 30% 用於驗證。</span><span class="sxs-lookup"><span data-stu-id="4deed-256">First, the pre-processed data is split and 70% is used for training while the remaining 30% is used for validation.</span></span> <span data-ttu-id="4deed-257">然後,30% 驗證集進一步拆分為驗證和測試集,其中 90% 用於驗證,10% 用於測試。</span><span class="sxs-lookup"><span data-stu-id="4deed-257">Then, the 30% validation set is further split into validation and test sets where 90% is used for validation and 10% is used for testing.</span></span>

    <span data-ttu-id="4deed-258">考慮這些數據分區用途的一種方法是參加考試。</span><span class="sxs-lookup"><span data-stu-id="4deed-258">A way to think about the purpose of these data partitions is taking an exam.</span></span> <span data-ttu-id="4deed-259">在學習考試時,您可以複習筆記、書籍或其他資源,以便了解考試中的概念。</span><span class="sxs-lookup"><span data-stu-id="4deed-259">When studying for an exam, you review your notes, books, or other resources to get a grasp on the concepts that are on the exam.</span></span> <span data-ttu-id="4deed-260">這就是火車的用點。</span><span class="sxs-lookup"><span data-stu-id="4deed-260">This is what the train set is for.</span></span> <span data-ttu-id="4deed-261">然後,您可以參加模擬考試來驗證您的知識。</span><span class="sxs-lookup"><span data-stu-id="4deed-261">Then, you might take a mock exam to validate your knowledge.</span></span> <span data-ttu-id="4deed-262">這是驗證集派上用場的地方。</span><span class="sxs-lookup"><span data-stu-id="4deed-262">This is where the validation set comes in handy.</span></span> <span data-ttu-id="4deed-263">在參加實際考試之前,您要檢查您是否很好地理解了這些概念。</span><span class="sxs-lookup"><span data-stu-id="4deed-263">You want to check whether you have a good grasp of the concepts before taking the actual exam.</span></span> <span data-ttu-id="4deed-264">根據這些結果,您會注意到自己出錯或不太瞭解的內容,並在複習真實考試時合併您的更改。</span><span class="sxs-lookup"><span data-stu-id="4deed-264">Based on those results, you take note of what you got wrong or didn't understand well and incorporate your changes as you review for the real exam.</span></span> <span data-ttu-id="4deed-265">最後,你參加考試。</span><span class="sxs-lookup"><span data-stu-id="4deed-265">Finally, you take the exam.</span></span> <span data-ttu-id="4deed-266">這就是測試集的用途。</span><span class="sxs-lookup"><span data-stu-id="4deed-266">This is what the test set is used for.</span></span> <span data-ttu-id="4deed-267">您從未見過考試中的問題,現在使用從培訓和驗證中學到的知識將您的知識應用於手頭的任務。</span><span class="sxs-lookup"><span data-stu-id="4deed-267">You've never seen the questions that are on the exam and now use what you learned from training and validation to apply your knowledge to the task at hand.</span></span>

1. <span data-ttu-id="4deed-268">為訓練、驗證和測試數據分配各自的分區各自的值。</span><span class="sxs-lookup"><span data-stu-id="4deed-268">Assign the partitions their respective values for the train, validation and test data.</span></span>

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L42-L44)]

## <a name="define-the-training-pipeline"></a><span data-ttu-id="4deed-269">定義訓練管道</span><span class="sxs-lookup"><span data-stu-id="4deed-269">Define the training pipeline</span></span>

<span data-ttu-id="4deed-270">模型培訓包括幾個步驟。</span><span class="sxs-lookup"><span data-stu-id="4deed-270">Model training consists of a couple of steps.</span></span> <span data-ttu-id="4deed-271">首先,圖像分類 API 用於訓練模型。</span><span class="sxs-lookup"><span data-stu-id="4deed-271">First, Image Classification API is used to train the model.</span></span> <span data-ttu-id="4deed-272">然後,使用`PredictedLabel``MapKeyToValue`轉換將列中的編碼標籤轉換回其原始分類值。</span><span class="sxs-lookup"><span data-stu-id="4deed-272">Then, the encoded labels in the `PredictedLabel` column are converted back to their original categorical value using the `MapKeyToValue` transform.</span></span>

1. <span data-ttu-id="4deed-273">建立新變數以儲存 的`ImageClassificationTrainer`一組必需和可選參數。</span><span class="sxs-lookup"><span data-stu-id="4deed-273">Create a new variable to store a set of required and optional parameters for an `ImageClassificationTrainer`.</span></span>

    [!code-csharp [ClassifierOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L46-L57)]

    <span data-ttu-id="4deed-274">A`ImageClassificationTrainer`需要幾個可選參數:</span><span class="sxs-lookup"><span data-stu-id="4deed-274">An `ImageClassificationTrainer` takes several optional parameters:</span></span>

    - <span data-ttu-id="4deed-275">`FeatureColumnName`是用作模型輸入的列。</span><span class="sxs-lookup"><span data-stu-id="4deed-275">`FeatureColumnName` is the column that is used as input for the model.</span></span>
    - <span data-ttu-id="4deed-276">`LabelColumnName`是要預測的值的列。</span><span class="sxs-lookup"><span data-stu-id="4deed-276">`LabelColumnName` is the column for the value to predict.</span></span>
    - <span data-ttu-id="4deed-277">`ValidationSet`是[`IDataView`](xref:Microsoft.ML.IDataView)包含驗證數據的。</span><span class="sxs-lookup"><span data-stu-id="4deed-277">`ValidationSet` is the [`IDataView`](xref:Microsoft.ML.IDataView) containing the validation data.</span></span>
    - <span data-ttu-id="4deed-278">`Arch`定義要使用的預訓練的模型體系結構。</span><span class="sxs-lookup"><span data-stu-id="4deed-278">`Arch` defines which of the pretrained model architectures to use.</span></span> <span data-ttu-id="4deed-279">本教學使用 ResNetv2 模型的 101 層變體。</span><span class="sxs-lookup"><span data-stu-id="4deed-279">This tutorial uses the 101-layer variant of the ResNetv2 model.</span></span>
    - <span data-ttu-id="4deed-280">`MetricsCallback`綁定函數以跟蹤訓練期間的進度。</span><span class="sxs-lookup"><span data-stu-id="4deed-280">`MetricsCallback` binds a function to track the progress during training.</span></span>
    - <span data-ttu-id="4deed-281">`TestOnTrainSet`告訴模型在不存在驗證集時根據訓練集測量性能。</span><span class="sxs-lookup"><span data-stu-id="4deed-281">`TestOnTrainSet` tells the model to measure performance against the training set when no validation set is present.</span></span>
    - <span data-ttu-id="4deed-282">`ReuseTrainSetBottleneckCachedValues`告訴模型在後續運行中是否使用瓶頸階段的緩存值。</span><span class="sxs-lookup"><span data-stu-id="4deed-282">`ReuseTrainSetBottleneckCachedValues` tells the model whether to use the cached values from the bottleneck phase in subsequent runs.</span></span> <span data-ttu-id="4deed-283">瓶頸階段是一次性傳遞計算,在首次執行時計算密集型計算。</span><span class="sxs-lookup"><span data-stu-id="4deed-283">The bottleneck phase is a one-time pass-through computation that is computationally intensive the first time it is performed.</span></span> <span data-ttu-id="4deed-284">如果訓練數據沒有變化,並且希望使用不同的紀元或批處理大小進行試驗,則使用緩存值可顯著減少定型模型所需的時間。</span><span class="sxs-lookup"><span data-stu-id="4deed-284">If the training data does not change and you want to experiment using a different number of epochs or batch size, using the cached values significantly reduces the amount of time required to train a model.</span></span>
    - <span data-ttu-id="4deed-285">`ReuseValidationSetBottleneckCachedValues``ReuseTrainSetBottleneckCachedValues`與僅與在這種情況下用於驗證數據集的情況類似。</span><span class="sxs-lookup"><span data-stu-id="4deed-285">`ReuseValidationSetBottleneckCachedValues` is similar to `ReuseTrainSetBottleneckCachedValues` only that in this case it's for the validation dataset.</span></span>
    - <span data-ttu-id="4deed-286">`WorkspacePath`定義存儲計算瓶頸值和`.pb`模型版本的目錄。</span><span class="sxs-lookup"><span data-stu-id="4deed-286">`WorkspacePath` defines the directory where to store the computed bottleneck values and `.pb` version of the model.</span></span>

1. <span data-ttu-id="4deed-287">定義[`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601)`mapLabelEstimator`由和組成的訓練管道`ImageClassificationTrainer`。</span><span class="sxs-lookup"><span data-stu-id="4deed-287">Define the [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) training pipeline that consists of both the `mapLabelEstimator` and the `ImageClassificationTrainer`.</span></span>

    [!code-csharp [TrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L59-L60)]

1. <span data-ttu-id="4deed-288">使用[`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*)方法訓練模型。</span><span class="sxs-lookup"><span data-stu-id="4deed-288">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to train your model.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L62)]

## <a name="use-the-model"></a><span data-ttu-id="4deed-289">使用模型</span><span class="sxs-lookup"><span data-stu-id="4deed-289">Use the model</span></span>

<span data-ttu-id="4deed-290">現在,您已經訓練了模型,是時候使用它來對圖像進行分類了。</span><span class="sxs-lookup"><span data-stu-id="4deed-290">Now that you have trained your model, it's time to use it to classify images.</span></span>

<span data-ttu-id="4deed-291">在方法`Main`下方,創建一種新的實用程式方法`OutputPrediction`, 用於在控制台中顯示預測資訊。</span><span class="sxs-lookup"><span data-stu-id="4deed-291">Below the `Main` method, create a new utility method called `OutputPrediction` to display prediction information in the console.</span></span>

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L96-L100)]

### <a name="classify-a-single-image"></a><span data-ttu-id="4deed-292">對單一個影像進行類別</span><span class="sxs-lookup"><span data-stu-id="4deed-292">Classify a single image</span></span>

1. <span data-ttu-id="4deed-293">在`Main`方法下方添加一`ClassifySingleImage`個新方法,以製作和輸出單個圖像預測。</span><span class="sxs-lookup"><span data-stu-id="4deed-293">Add a new method called `ClassifySingleImage` below the `Main` method to make and output a single image prediction.</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="4deed-294">在`ClassifySingleImage`方法[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)內創建一個。</span><span class="sxs-lookup"><span data-stu-id="4deed-294">Create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) inside the `ClassifySingleImage` method.</span></span> <span data-ttu-id="4deed-295">是[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)一個方便的 API,它允許您傳遞,然後對單個數據實例執行預測。</span><span class="sxs-lookup"><span data-stu-id="4deed-295">The [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span>

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L73)]

1. <span data-ttu-id="4deed-296">`ModelInput`要存取單一個實體,請`data`[`IDataView`](xref:Microsoft.ML.IDataView)[`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)[`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*)使用方法將轉換為, 然後取得第一個觀察值。</span><span class="sxs-lookup"><span data-stu-id="4deed-296">To access a single `ModelInput` instance, convert the `data` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first observation.</span></span>

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L75)]

1. <span data-ttu-id="4deed-297">使用[`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*)方法對圖像進行分類。</span><span class="sxs-lookup"><span data-stu-id="4deed-297">Use the [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) method to classify the image.</span></span>

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L77)]

1. <span data-ttu-id="4deed-298">使用`OutputPrediction`方法將預測輸出到主控台。</span><span class="sxs-lookup"><span data-stu-id="4deed-298">Output the prediction to the console with the `OutputPrediction` method.</span></span>

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L79-L80)]

1. <span data-ttu-id="4deed-299">在方法`Main`內,`ClassifySingleImage`使用映射的測試集調用。</span><span class="sxs-lookup"><span data-stu-id="4deed-299">Inside the `Main` method, call `ClassifySingleImage` using the test set of images.</span></span>

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L64)]

### <a name="classify-multiple-images"></a><span data-ttu-id="4deed-300">對多個影像進行類別</span><span class="sxs-lookup"><span data-stu-id="4deed-300">Classify multiple images</span></span>

1. <span data-ttu-id="4deed-301">在`ClassifySingleImage`方法下方添加一`ClassifyImages`個新方法,用於創建和輸出多個圖像預測。</span><span class="sxs-lookup"><span data-stu-id="4deed-301">Add a new method called `ClassifyImages` below the `ClassifySingleImage` method to make and output multiple image predictions.</span></span>

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="4deed-302">使用[`IDataView`](xref:Microsoft.ML.IDataView)方法建立包含預測的方法[`Transform`](xref:Microsoft.ML.ITransformer.Transform*)。</span><span class="sxs-lookup"><span data-stu-id="4deed-302">Create an [`IDataView`](xref:Microsoft.ML.IDataView) containing the predictions by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method.</span></span> <span data-ttu-id="4deed-303">將下列程式碼新增至 `ClassifyImages` 方法內。</span><span class="sxs-lookup"><span data-stu-id="4deed-303">Add the following code inside the `ClassifyImages` method.</span></span>

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L85)]

1. <span data-ttu-id="4deed-304">為了反覆運算預測,請使用`predictionData`[`IDataView`](xref:Microsoft.ML.IDataView)[`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)[`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*)方法將轉換為, 然後獲取前 10 個觀測值。</span><span class="sxs-lookup"><span data-stu-id="4deed-304">In order to iterate over the predictions, convert the `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first 10 observations.</span></span>

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L87)]

1. <span data-ttu-id="4deed-305">反覆運算並輸出預測的原始和預測標籤。</span><span class="sxs-lookup"><span data-stu-id="4deed-305">Iterate and output the original and predicted labels for the predictions.</span></span>

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L89-L93)]

1. <span data-ttu-id="4deed-306">最後,在方法`Main`內,使用`ClassifyImages`測試圖像集調用。</span><span class="sxs-lookup"><span data-stu-id="4deed-306">Finally, inside the `Main` method, call `ClassifyImages` using the test set of images.</span></span>

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L66)]

## <a name="run-the-application"></a><span data-ttu-id="4deed-307">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="4deed-307">Run the application</span></span>

<span data-ttu-id="4deed-308">運行控制台應用。</span><span class="sxs-lookup"><span data-stu-id="4deed-308">Run your console app.</span></span> <span data-ttu-id="4deed-309">輸出應類似於下面的輸出。</span><span class="sxs-lookup"><span data-stu-id="4deed-309">The output should be similar to that below.</span></span> <span data-ttu-id="4deed-310">您可能會看到警告或處理中訊息，但為了讓結果變得清楚，這些訊息已從下列結果中移除。</span><span class="sxs-lookup"><span data-stu-id="4deed-310">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span> <span data-ttu-id="4deed-311">為簡潔起見,輸出已壓縮。</span><span class="sxs-lookup"><span data-stu-id="4deed-311">For brevity, the output has been condensed.</span></span>

<span data-ttu-id="4deed-312">**瓶頸階段**</span><span class="sxs-lookup"><span data-stu-id="4deed-312">**Bottleneck phase**</span></span>

<span data-ttu-id="4deed-313">不會列印影像名稱的值,因為影像載入為,`byte[]`因此沒有要顯示的影像名稱。</span><span class="sxs-lookup"><span data-stu-id="4deed-313">No value is printed for the image name because the images are loaded as a `byte[]` therefore there is no image name to display.</span></span>

```test
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 279
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 280
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   1
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   2
```

<span data-ttu-id="4deed-314">**培訓階段**</span><span class="sxs-lookup"><span data-stu-id="4deed-314">**Training phase**</span></span>

```text
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  21, Accuracy:  0.6797619
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  22, Accuracy:  0.7642857
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  23, Accuracy:  0.7916667
```

<span data-ttu-id="4deed-315">**影像輸出進行類別**</span><span class="sxs-lookup"><span data-stu-id="4deed-315">**Classify images output**</span></span>

```text
Classifying single image
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD

Classifying multiple images
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-163.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-210.jpg | Actual Value: UD | Predicted Value: UD
```

<span data-ttu-id="4deed-316">在檢查*7001-220.jpg*圖像時,您可以看到它實際上沒有破裂。</span><span class="sxs-lookup"><span data-stu-id="4deed-316">Upon inspection of the *7001-220.jpg* image, you can see that it in fact is not cracked.</span></span>

![預測的 SDNET2018 資料集影像](./media/image-classification-api-transfer-learning/predictedimage.jpg)

<span data-ttu-id="4deed-318">恭喜！</span><span class="sxs-lookup"><span data-stu-id="4deed-318">Congratulations!</span></span> <span data-ttu-id="4deed-319">現在,您已成功構建了用於對圖像進行分類的深層學習模型。</span><span class="sxs-lookup"><span data-stu-id="4deed-319">You've now successfully built a deep learning model for classifying images.</span></span>

### <a name="improve-the-model"></a><span data-ttu-id="4deed-320">改進模型</span><span class="sxs-lookup"><span data-stu-id="4deed-320">Improve the model</span></span>

<span data-ttu-id="4deed-321">如果您對模型的結果不滿意,則可以嘗試嘗試以下一些方法來提高模型的性能:</span><span class="sxs-lookup"><span data-stu-id="4deed-321">If you're not satisfied with the results of your model, you can try to improve its performance by trying some of the following approaches:</span></span>

- <span data-ttu-id="4deed-322">**數據越多**:模型從中學習的實例越多,效果越好。</span><span class="sxs-lookup"><span data-stu-id="4deed-322">**More Data**: The more examples a model learns from, the better it performs.</span></span> <span data-ttu-id="4deed-323">下載完整的[SDNET2018 數據集](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional),並將其用於培訓。</span><span class="sxs-lookup"><span data-stu-id="4deed-323">Download the full [SDNET2018 dataset](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) and use it to train.</span></span>
- <span data-ttu-id="4deed-324">**增強數據**:向數據添加多樣性的一種常見方法是通過拍攝圖像並應用不同的變換(旋轉、翻轉、移位、裁剪)來增強數據。</span><span class="sxs-lookup"><span data-stu-id="4deed-324">**Augment the data**: A common technique to add variety to the data is to augment the data by taking an image and applying different transforms (rotate, flip, shift, crop).</span></span> <span data-ttu-id="4deed-325">這為模型添加了更多要學習的範例。</span><span class="sxs-lookup"><span data-stu-id="4deed-325">This adds more varied examples for the model to learn from.</span></span>
- <span data-ttu-id="4deed-326">**訓練時間更長**:訓練時間越長,模型就越調整。</span><span class="sxs-lookup"><span data-stu-id="4deed-326">**Train for a longer time**: The longer you train, the more tuned the model will be.</span></span> <span data-ttu-id="4deed-327">增加紀元數可能會提高模型的性能。</span><span class="sxs-lookup"><span data-stu-id="4deed-327">Increasing the number of epochs may improve the performance of your model.</span></span>
- <span data-ttu-id="4deed-328">**試驗超參數**:除了本教程中使用的參數外,還可以調整其他參數,以可能提高性能。</span><span class="sxs-lookup"><span data-stu-id="4deed-328">**Experiment with the hyper-parameters**: In addition to the parameters used in this tutorial, other parameters can be tuned to potentially improve performance.</span></span> <span data-ttu-id="4deed-329">更改學習速率,這將確定每個時代之後對模型所做的更新量可能會提高性能。</span><span class="sxs-lookup"><span data-stu-id="4deed-329">Changing the learning rate, which determines the magnitude of updates made to the model after each epoch may improve performance.</span></span>
- <span data-ttu-id="4deed-330">**使用不同的模型體系結構**:根據數據的外觀,最能瞭解其功能的模型可能有所不同。</span><span class="sxs-lookup"><span data-stu-id="4deed-330">**Use a different model architecture**: Depending on what your data looks like, the model that can best learn its features may differ.</span></span> <span data-ttu-id="4deed-331">如果您對模型的性能不滿意,請嘗試更改體系結構。</span><span class="sxs-lookup"><span data-stu-id="4deed-331">If you're not satisfied with the performance of your model, try changing the architecture.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="4deed-332">其他資源</span><span class="sxs-lookup"><span data-stu-id="4deed-332">Additional Resources</span></span>

- <span data-ttu-id="4deed-333">[深度學習與機器學習](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning)。</span><span class="sxs-lookup"><span data-stu-id="4deed-333">[Deep Learning vs Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span></span>

## <a name="next-steps"></a><span data-ttu-id="4deed-334">後續步驟</span><span class="sxs-lookup"><span data-stu-id="4deed-334">Next steps</span></span>

<span data-ttu-id="4deed-335">在本教學中,您學習了如何使用傳輸學習、預先訓練的圖像分類 TensorFlow 模型和ML.NET圖像分類 API 構建自訂深度學習模型,將混凝土表面的圖像分類為破裂或未開裂。</span><span class="sxs-lookup"><span data-stu-id="4deed-335">In this tutorial, you learned how to build a custom deep learning model using transfer learning, a pretrained image classification TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="4deed-336">前進到下一個教學課程來深入了解。</span><span class="sxs-lookup"><span data-stu-id="4deed-336">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4deed-337">物件偵測</span><span class="sxs-lookup"><span data-stu-id="4deed-337">Object Detection</span></span>](object-detection-onnx.md)
