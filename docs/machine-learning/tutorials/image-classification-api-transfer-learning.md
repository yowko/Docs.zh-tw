---
title: 教學課程：使用傳輸學習的自動化視覺效果檢查
description: 本教學課程說明如何使用「傳輸學習」來定型 ML.NET 中的 TensorFlow 深度學習模型，其方式是使用影像偵測 API，將具體介面的影像分類為破裂或未破解。
author: luisquintanilla
ms.author: luquinta
ms.date: 12/12/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 2915259d7c7031b9e699c7fd0cf65cf723c41680
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144418"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a><span data-ttu-id="b2d91-103">教學課程：搭配 ML.NET 影像分類 API 使用傳輸學習的自動化視覺效果檢查</span><span class="sxs-lookup"><span data-stu-id="b2d91-103">Tutorial: Automated visual inspection using transfer learning with the ML.NET Image Classification API</span></span>

<span data-ttu-id="b2d91-104">瞭解如何使用「傳輸學習」（預先定型 TensorFlow 模型）和「ML.NET 影像分類 API」來定型自訂深度學習模型，以將具體表面的影像分類為破裂或 uncracked。</span><span class="sxs-lookup"><span data-stu-id="b2d91-104">Learn how to train a custom deep learning model using transfer learning, a pretrained TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="b2d91-105">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="b2d91-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="b2d91-106">了解問題</span><span class="sxs-lookup"><span data-stu-id="b2d91-106">Understand the problem</span></span>
> - <span data-ttu-id="b2d91-107">瞭解 ML.NET 影像分類 API</span><span class="sxs-lookup"><span data-stu-id="b2d91-107">Learn about ML.NET Image Classification API</span></span>
> - <span data-ttu-id="b2d91-108">瞭解預先定型模型</span><span class="sxs-lookup"><span data-stu-id="b2d91-108">Understand the pretrained model</span></span>
> - <span data-ttu-id="b2d91-109">使用傳輸學習來定型自訂 TensorFlow 影像分類模型</span><span class="sxs-lookup"><span data-stu-id="b2d91-109">Use transfer learning to train a custom TensorFlow image classification model</span></span>
> - <span data-ttu-id="b2d91-110">使用自訂模型分類影像</span><span class="sxs-lookup"><span data-stu-id="b2d91-110">Classify images with the custom model</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b2d91-111">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="b2d91-111">Prerequisites</span></span>

- <span data-ttu-id="b2d91-112">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)或更新版本，或是已安裝「.net Core 跨平臺開發」工作負載的 Visual Studio 2017 15.6 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="b2d91-112">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="image-classification-transfer-learning-sample-overview"></a><span data-ttu-id="b2d91-113">影像分類傳輸學習範例總覽</span><span class="sxs-lookup"><span data-stu-id="b2d91-113">Image classification transfer learning sample overview</span></span>

<span data-ttu-id="b2d91-114">此範例是 c # .NET Core 主控台應用程式，可使用預先定型深度學習 TensorFlow 模型來分類影像。</span><span class="sxs-lookup"><span data-stu-id="b2d91-114">This sample is a C# .NET Core console application that classifies images using a pretrained deep learning TensorFlow model.</span></span> <span data-ttu-id="b2d91-115">您可以在 GitHub 的 [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) 找到此範例的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b2d91-115">The code for this sample can be found on the [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="b2d91-116">了解問題</span><span class="sxs-lookup"><span data-stu-id="b2d91-116">Understand the problem</span></span>

<span data-ttu-id="b2d91-117">影像分類是電腦視覺問題。</span><span class="sxs-lookup"><span data-stu-id="b2d91-117">Image classification is a computer vision problem.</span></span> <span data-ttu-id="b2d91-118">影像分類會將影像做為輸入，並將其分類為指定的類別。</span><span class="sxs-lookup"><span data-stu-id="b2d91-118">Image classification takes an image as input and categorizes it into a prescribed class.</span></span> <span data-ttu-id="b2d91-119">影像分類非常有用的部分案例包括：</span><span class="sxs-lookup"><span data-stu-id="b2d91-119">Some scenarios where image classification is useful include:</span></span>

- <span data-ttu-id="b2d91-120">臉部辨識</span><span class="sxs-lookup"><span data-stu-id="b2d91-120">Facial recognition</span></span>
- <span data-ttu-id="b2d91-121">情緒偵測</span><span class="sxs-lookup"><span data-stu-id="b2d91-121">Emotion detection</span></span>
- <span data-ttu-id="b2d91-122">醫療診斷</span><span class="sxs-lookup"><span data-stu-id="b2d91-122">Medical diagnosis</span></span>
- <span data-ttu-id="b2d91-123">地標偵測</span><span class="sxs-lookup"><span data-stu-id="b2d91-123">Landmark detection</span></span>

<span data-ttu-id="b2d91-124">本教學課程會將自訂影像分類模型定型，以執行橋接器投影片的自動化視覺效果檢查，以識別破裂所損毀的結構。</span><span class="sxs-lookup"><span data-stu-id="b2d91-124">This tutorial trains a custom image classification model to perform automated visual inspection of bridge decks to identify structures that are damaged by cracks.</span></span>

## <a name="mlnet-image-classification-api"></a><span data-ttu-id="b2d91-125">ML.NET 影像分類 API</span><span class="sxs-lookup"><span data-stu-id="b2d91-125">ML.NET Image Classification API</span></span>

<span data-ttu-id="b2d91-126">ML.NET 提供各種執行影像分類的方式。</span><span class="sxs-lookup"><span data-stu-id="b2d91-126">ML.NET provides various ways of performing image classification.</span></span> <span data-ttu-id="b2d91-127">本教學課程會使用影像分類 API 來套用傳輸學習。</span><span class="sxs-lookup"><span data-stu-id="b2d91-127">This tutorial applies transfer learning using the Image Classification API.</span></span> <span data-ttu-id="b2d91-128">影像分類 API 會使用[TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET)，這是為 TensorFlow c + + API 提供 c # 系結的低層級程式庫。</span><span class="sxs-lookup"><span data-stu-id="b2d91-128">The Image Classification API makes use of [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), a low-level library that provides C# bindings for the TensorFlow C++ API.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="b2d91-129">什麼是傳輸學習？</span><span class="sxs-lookup"><span data-stu-id="b2d91-129">What is transfer learning?</span></span>

<span data-ttu-id="b2d91-130">轉移學習會將解決一個問題所獲得的知識套用至另一個相關問題。</span><span class="sxs-lookup"><span data-stu-id="b2d91-130">Transfer learning applies knowledge gained from solving one problem to another related problem.</span></span>

<span data-ttu-id="b2d91-131">從頭開始訓練深度學習模型，需要設定數個參數、大量標記的定型資料，以及大量的計算資源（數百個 GPU 小時）。</span><span class="sxs-lookup"><span data-stu-id="b2d91-131">Training a deep learning model from scratch requires setting several parameters, a large amount of labeled training data, and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="b2d91-132">搭配使用預先定型模型與轉移學習，可讓您將定型程式的快捷方式。</span><span class="sxs-lookup"><span data-stu-id="b2d91-132">Using a pretrained model along with transfer learning allows you to shortcut the training process.</span></span>

## <a name="training-process"></a><span data-ttu-id="b2d91-133">訓練流程</span><span class="sxs-lookup"><span data-stu-id="b2d91-133">Training process</span></span>

<span data-ttu-id="b2d91-134">影像分類 API 會藉由載入預先定型 TensorFlow 模型來啟動定型程式。</span><span class="sxs-lookup"><span data-stu-id="b2d91-134">The Image Classification API starts the training process by loading a pretrained TensorFlow model.</span></span> <span data-ttu-id="b2d91-135">定型套裝程式含兩個步驟：</span><span class="sxs-lookup"><span data-stu-id="b2d91-135">The training process consists of two steps:</span></span>

1. <span data-ttu-id="b2d91-136">瓶頸階段</span><span class="sxs-lookup"><span data-stu-id="b2d91-136">Bottleneck phase</span></span>
2. <span data-ttu-id="b2d91-137">訓練階段</span><span class="sxs-lookup"><span data-stu-id="b2d91-137">Training phase</span></span>

![訓練步驟](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a><span data-ttu-id="b2d91-139">瓶頸階段</span><span class="sxs-lookup"><span data-stu-id="b2d91-139">Bottleneck phase</span></span>

<span data-ttu-id="b2d91-140">在瓶頸階段，會載入定型影像集，並使用圖元值做為預先定型模型之凍結層的輸入或特徵。</span><span class="sxs-lookup"><span data-stu-id="b2d91-140">During the bottleneck phase, the set of training images is loaded and the pixel values are used as input, or features, for the frozen layers of the pretrained model.</span></span> <span data-ttu-id="b2d91-141">凍結層包含類神經網路中的所有圖層，最多倒數第二層，非正式稱為瓶頸層。</span><span class="sxs-lookup"><span data-stu-id="b2d91-141">The frozen layers include all of the layers in the neural network up to the penultimate layer, informally known as the bottleneck layer.</span></span> <span data-ttu-id="b2d91-142">這些層級稱為「已凍結」，因為這些層上不會進行定型，而且作業會通過傳遞。</span><span class="sxs-lookup"><span data-stu-id="b2d91-142">These layers are referred to as frozen because no training will occur on these layers and operations are pass-through.</span></span> <span data-ttu-id="b2d91-143">這是在這些凍結層級，可協助模型區別不同類別的較低等級模式會進行計算。</span><span class="sxs-lookup"><span data-stu-id="b2d91-143">It's at these frozen layers where the lower-level patterns that help a model differentiate between the different classes are computed.</span></span> <span data-ttu-id="b2d91-144">層的數目越大，此步驟所需的計算密集型就愈多。</span><span class="sxs-lookup"><span data-stu-id="b2d91-144">The larger the number of layers, the more computationally intensive this step is.</span></span> <span data-ttu-id="b2d91-145">幸好，由於這是一次性的計算，因此可以快取結果，並在使用不同的參數進行實驗時，于稍後執行。</span><span class="sxs-lookup"><span data-stu-id="b2d91-145">Fortunately, since this is a one-time calculation, the results can be cached and used in later runs when experimenting with different parameters.</span></span>

### <a name="training-phase"></a><span data-ttu-id="b2d91-146">訓練階段</span><span class="sxs-lookup"><span data-stu-id="b2d91-146">Training phase</span></span>

<span data-ttu-id="b2d91-147">一旦計算出瓶頸階段的輸出值，就會使用它們做為輸入，以重新定型模型的最後一層。</span><span class="sxs-lookup"><span data-stu-id="b2d91-147">Once the output values from the bottleneck phase are computed, they are used as input to retrain the final layer of the model.</span></span> <span data-ttu-id="b2d91-148">此程式會反復執行，並針對模型參數所指定的次數執行。</span><span class="sxs-lookup"><span data-stu-id="b2d91-148">This process is iterative and runs for the number of times specified by model parameters.</span></span> <span data-ttu-id="b2d91-149">在每次執行期間，會評估遺失和精確度。</span><span class="sxs-lookup"><span data-stu-id="b2d91-149">During each run, the loss and accuracy are evaluated.</span></span> <span data-ttu-id="b2d91-150">然後，會進行適當的調整來改善模型，其目標是將遺失降至最低，並將精確度最大化。</span><span class="sxs-lookup"><span data-stu-id="b2d91-150">Then, the appropriate adjustments are made to improve the model with the goal of minimizing the loss and maximizing the accuracy.</span></span> <span data-ttu-id="b2d91-151">定型完成後，會輸出兩種模型格式。</span><span class="sxs-lookup"><span data-stu-id="b2d91-151">Once training is finished, two model formats are output.</span></span> <span data-ttu-id="b2d91-152">其中一個是模型的 `.pb` 版本，另一個則是 `.zip` 模型的 ML.NET 序列化版本。</span><span class="sxs-lookup"><span data-stu-id="b2d91-152">One of them is the `.pb` version of the model and the other is the `.zip` ML.NET serialized version of the model.</span></span> <span data-ttu-id="b2d91-153">在 ML.NET 所支援的環境中工作時，建議使用模型的 `.zip` 版本。</span><span class="sxs-lookup"><span data-stu-id="b2d91-153">When working in environments supported by ML.NET, it is recommended to use the `.zip` version of the model.</span></span> <span data-ttu-id="b2d91-154">不過，在不支援 ML.NET 的環境中，您可以選擇使用 `.pb` 版本。</span><span class="sxs-lookup"><span data-stu-id="b2d91-154">However, in environments where ML.NET is not supported, you have the option of using the `.pb` version.</span></span>

## <a name="understand-the-pretrained-model"></a><span data-ttu-id="b2d91-155">瞭解預先定型模型</span><span class="sxs-lookup"><span data-stu-id="b2d91-155">Understand the pretrained model</span></span>

<span data-ttu-id="b2d91-156">本教學課程中使用的預先定型模型是「剩餘網路（ResNet） v2」模型的101層變體。</span><span class="sxs-lookup"><span data-stu-id="b2d91-156">The pretrained model used in this tutorial is the 101-layer variant of the Residual Network (ResNet) v2 model.</span></span> <span data-ttu-id="b2d91-157">原始模型已定型，可將影像分類為一千個類別。</span><span class="sxs-lookup"><span data-stu-id="b2d91-157">The original model is trained to classify images into a thousand categories.</span></span> <span data-ttu-id="b2d91-158">此模型會使用大小為 224 x 224 的影像做為輸入，並針對其定型的每個類別輸出類別機率。</span><span class="sxs-lookup"><span data-stu-id="b2d91-158">The model takes as input an image of size 224 x 224 and outputs the class probabilities for each of the classes it's trained on.</span></span> <span data-ttu-id="b2d91-159">此模型的一部分是用來使用自訂影像來定型新模型，以便在兩個類別之間進行預測。</span><span class="sxs-lookup"><span data-stu-id="b2d91-159">Part of this model is used to train a new model using custom images to make predictions between two classes.</span></span>

## <a name="create-console-application"></a><span data-ttu-id="b2d91-160">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="b2d91-160">Create console application</span></span>

<span data-ttu-id="b2d91-161">既然您已大致瞭解轉移學習和影像分類 API，現在正是建立應用程式的時候了。</span><span class="sxs-lookup"><span data-stu-id="b2d91-161">Now that you have a general understanding of transfer learning and the Image Classification API, it's time to build the application.</span></span>

1. <span data-ttu-id="b2d91-162">建立名為 "DeepLearning_ImageClassification_Binary" 的**c # .Net Core 主控台應用程式**。</span><span class="sxs-lookup"><span data-stu-id="b2d91-162">Create a **C# .NET Core Console Application** called "DeepLearning_ImageClassification_Binary".</span></span>
1. <span data-ttu-id="b2d91-163">安裝**Microsoft.ML**版本**1.4.0** NuGet 套件：</span><span class="sxs-lookup"><span data-stu-id="b2d91-163">Install the **Microsoft.ML** version **1.4.0** NuGet Package:</span></span>
    1. <span data-ttu-id="b2d91-164">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b2d91-164">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="b2d91-165">選擇 "nuget.org" 作為套件來源。</span><span class="sxs-lookup"><span data-stu-id="b2d91-165">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="b2d91-166">選取 [瀏覽]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b2d91-166">Select the **Browse** tab.</span></span>
    1. <span data-ttu-id="b2d91-167">勾選 [**包含發行**前版本] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="b2d91-167">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="b2d91-168">搜尋**Microsoft.ML**。</span><span class="sxs-lookup"><span data-stu-id="b2d91-168">Search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="b2d91-169">選取 [安裝]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="b2d91-169">Select the **Install** button.</span></span>
    1. <span data-ttu-id="b2d91-170">在 [預覽變更]\*\*\*\* 對話方塊上，選取 [確定]\*\*\*\* 按鈕，然後在 [授權接受]\*\*\*\* 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b2d91-170">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="b2d91-171">針對**1.4.0**、SciSharp**版本** **1.15.0**和**TensorFlow**版本**ImageAnalytics** NuGet 套件，重複上述步驟。（適用于**microsoft ml** ）。</span><span class="sxs-lookup"><span data-stu-id="b2d91-171">Repeat these steps for the **Microsoft.ML.Vision** version **1.4.0**, **SciSharp.TensorFlow.Redist** version **1.15.0**, and **Microsoft.ML.ImageAnalytics** version **1.4.0** NuGet packages.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="b2d91-172">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="b2d91-172">Prepare and understand the data</span></span>

> [!NOTE]
> <span data-ttu-id="b2d91-173">本教學課程的資料集來自 Maguire、Marc、Dorafshan, Sattar;和 Thomas，Robert J.，"SDNET2018：機器學習應用程式的具體破解影像資料集" （2018）。</span><span class="sxs-lookup"><span data-stu-id="b2d91-173">The datasets for this tutorial are from Maguire, Marc; Dorafshan, Sattar; and Thomas, Robert J., "SDNET2018: A concrete crack image dataset for machine learning applications" (2018).</span></span> <span data-ttu-id="b2d91-174">流覽所有資料集。</span><span class="sxs-lookup"><span data-stu-id="b2d91-174">Browse all Datasets.</span></span> <span data-ttu-id="b2d91-175">紙張48。</span><span class="sxs-lookup"><span data-stu-id="b2d91-175">Paper 48.</span></span> <https://digitalcommons.usu.edu/all_datasets/48>

<span data-ttu-id="b2d91-176">SDNET2018 是影像資料集，其中包含已破裂和未破裂之實體結構（bridge 圖、牆和 pavement）的注釋。</span><span class="sxs-lookup"><span data-stu-id="b2d91-176">SDNET2018 is an image dataset that contains annotations for cracked and non-cracked concrete structures (bridge decks, walls, and pavement).</span></span>

![SDNET2018 資料集橋接器範例](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

<span data-ttu-id="b2d91-178">資料會組織成三個子目錄：</span><span class="sxs-lookup"><span data-stu-id="b2d91-178">The data is organized in three subdirectories:</span></span>

- <span data-ttu-id="b2d91-179">D 包含橋接器影像</span><span class="sxs-lookup"><span data-stu-id="b2d91-179">D contains bridge deck images</span></span>
- <span data-ttu-id="b2d91-180">P 包含 pavement 映射</span><span class="sxs-lookup"><span data-stu-id="b2d91-180">P contains pavement images</span></span>
- <span data-ttu-id="b2d91-181">W 包含牆影像</span><span class="sxs-lookup"><span data-stu-id="b2d91-181">W contains wall images</span></span>

<span data-ttu-id="b2d91-182">這些子目錄中的每一個都包含兩個額外的首碼子目錄：</span><span class="sxs-lookup"><span data-stu-id="b2d91-182">Each of these subdirectories contains two additional prefixed subdirectories:</span></span>

- <span data-ttu-id="b2d91-183">C 是用於破裂表面的前置詞</span><span class="sxs-lookup"><span data-stu-id="b2d91-183">C is the prefix used for cracked surfaces</span></span>
- <span data-ttu-id="b2d91-184">U 是用於 uncracked 表面的前置詞</span><span class="sxs-lookup"><span data-stu-id="b2d91-184">U is the prefix used for uncracked surfaces</span></span>

<span data-ttu-id="b2d91-185">在本教學課程中，只會使用橋接器的影像。</span><span class="sxs-lookup"><span data-stu-id="b2d91-185">In this tutorial, only bridge deck images are used.</span></span>

1. <span data-ttu-id="b2d91-186">下載[資料集](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip)並解壓縮。</span><span class="sxs-lookup"><span data-stu-id="b2d91-186">Download the [dataset](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) and unzip.</span></span>
1. <span data-ttu-id="b2d91-187">在您的專案中建立名為「資產」的目錄，以儲存您的資料集檔案。</span><span class="sxs-lookup"><span data-stu-id="b2d91-187">Create a directory named "assets" in your project to save your dataset files.</span></span>
1. <span data-ttu-id="b2d91-188">將*CD*和*UD*子目錄從最近解壓縮的目錄複寫到*資產*目錄。</span><span class="sxs-lookup"><span data-stu-id="b2d91-188">Copy the *CD* and *UD* subdirectories from the recently unzipped directory to the *assets* directory.</span></span>

### <a name="create-input-and-output-classes"></a><span data-ttu-id="b2d91-189">建立輸入和輸出類別</span><span class="sxs-lookup"><span data-stu-id="b2d91-189">Create input and output classes</span></span>

1. <span data-ttu-id="b2d91-190">開啟*Program.cs*檔案，並將檔案頂端的現有語句取代為 `using` 下列內容：</span><span class="sxs-lookup"><span data-stu-id="b2d91-190">Open the *Program.cs* file and replace the existing `using` statements at the top of the file with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L1-L7)]

1. <span data-ttu-id="b2d91-191">`Program`在*Program.cs*中的類別底下，建立名為的類別 `ImageData` 。</span><span class="sxs-lookup"><span data-stu-id="b2d91-191">Below the `Program` class in *Program.cs*, create a class called `ImageData`.</span></span> <span data-ttu-id="b2d91-192">這個類別是用來代表一開始載入的資料。</span><span class="sxs-lookup"><span data-stu-id="b2d91-192">This class is used to represent the initially loaded data.</span></span>

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L137-L142)]

    <span data-ttu-id="b2d91-193">`ImageData`包含下列屬性：</span><span class="sxs-lookup"><span data-stu-id="b2d91-193">`ImageData` contains the following properties:</span></span>

    - <span data-ttu-id="b2d91-194">`ImagePath`這是儲存影像的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="b2d91-194">`ImagePath` is the fully qualified path where the image is stored.</span></span>
    - <span data-ttu-id="b2d91-195">`Label`這是影像所屬的類別目錄。</span><span class="sxs-lookup"><span data-stu-id="b2d91-195">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="b2d91-196">這是要預測的值。</span><span class="sxs-lookup"><span data-stu-id="b2d91-196">This is the value to predict.</span></span>

1. <span data-ttu-id="b2d91-197">建立輸入和輸出資料的類別</span><span class="sxs-lookup"><span data-stu-id="b2d91-197">Create classes for your input and output data</span></span>

    1. <span data-ttu-id="b2d91-198">在 `ImageData` 類別底下，于名為的新類別中定義輸入資料的架構 `ModelInput` 。</span><span class="sxs-lookup"><span data-stu-id="b2d91-198">Below the `ImageData` class, define the schema of your input data in a new class called `ModelInput`.</span></span>

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L144-L153)]

        <span data-ttu-id="b2d91-199">`ModelInput`包含下列屬性：</span><span class="sxs-lookup"><span data-stu-id="b2d91-199">`ModelInput` contains the following properties:</span></span>

        - <span data-ttu-id="b2d91-200">`Image`這是 `byte[]` 影像的標記法。</span><span class="sxs-lookup"><span data-stu-id="b2d91-200">`Image` is the `byte[]` representation of the image.</span></span> <span data-ttu-id="b2d91-201">此模型預期影像資料屬於這種定型類型。</span><span class="sxs-lookup"><span data-stu-id="b2d91-201">The model expects image data to be of this type for training.</span></span>
        - <span data-ttu-id="b2d91-202">`LabelAsKey`這是的數值表示 `Label` 。</span><span class="sxs-lookup"><span data-stu-id="b2d91-202">`LabelAsKey` is the numerical representation of the `Label`.</span></span>
        - <span data-ttu-id="b2d91-203">`ImagePath`這是儲存影像的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="b2d91-203">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="b2d91-204">`Label`這是影像所屬的類別目錄。</span><span class="sxs-lookup"><span data-stu-id="b2d91-204">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="b2d91-205">這是要預測的值。</span><span class="sxs-lookup"><span data-stu-id="b2d91-205">This is the value to predict.</span></span>

        <span data-ttu-id="b2d91-206">只有 `Image` 和 `LabelAsKey` 可用來定型模型並進行預測。</span><span class="sxs-lookup"><span data-stu-id="b2d91-206">Only `Image` and `LabelAsKey` are used to train the model and make predictions.</span></span> <span data-ttu-id="b2d91-207">為了 `ImagePath` `Label` 方便存取原始的影像檔案名稱和類別，會保留和屬性。</span><span class="sxs-lookup"><span data-stu-id="b2d91-207">The `ImagePath` and `Label` properties are kept for convenience to access the original image file name and category.</span></span>

    1. <span data-ttu-id="b2d91-208">然後，在 `ModelInput` 類別底下，在名為的新類別中定義輸出資料的架構 `ModelOutput` 。</span><span class="sxs-lookup"><span data-stu-id="b2d91-208">Then, below the `ModelInput` class, define the schema of your output data in a new class called `ModelOutput`.</span></span>

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L155-L162)]

        <span data-ttu-id="b2d91-209">`ModelOutput`包含下列屬性：</span><span class="sxs-lookup"><span data-stu-id="b2d91-209">`ModelOutput` contains the following properties:</span></span>

        - <span data-ttu-id="b2d91-210">`ImagePath`這是儲存影像的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="b2d91-210">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="b2d91-211">`Label`是影像所屬的原始類別目錄。</span><span class="sxs-lookup"><span data-stu-id="b2d91-211">`Label` is the original category the image belongs to.</span></span> <span data-ttu-id="b2d91-212">這是要預測的值。</span><span class="sxs-lookup"><span data-stu-id="b2d91-212">This is the value to predict.</span></span>
        - <span data-ttu-id="b2d91-213">`PredictedLabel`這是模型所預測的值。</span><span class="sxs-lookup"><span data-stu-id="b2d91-213">`PredictedLabel` is the value predicted by the model.</span></span>

        <span data-ttu-id="b2d91-214">與類似 `ModelInput` ，只 `PredictedLabel` 需要進行預測，因為它包含模型所做的預測。</span><span class="sxs-lookup"><span data-stu-id="b2d91-214">Similar to `ModelInput`, only the `PredictedLabel` is required to make predictions since it contains the prediction made by the model.</span></span> <span data-ttu-id="b2d91-215">為了 `ImagePath` `Label` 方便存取原始的影像檔案名稱和類別，會保留和屬性。</span><span class="sxs-lookup"><span data-stu-id="b2d91-215">The `ImagePath` and `Label` properties are retained for convenience to access the original image file name and category.</span></span>

### <a name="create-workspace-directory"></a><span data-ttu-id="b2d91-216">建立工作區目錄</span><span class="sxs-lookup"><span data-stu-id="b2d91-216">Create workspace directory</span></span>

<span data-ttu-id="b2d91-217">當定型和驗證資料不常變更時，快取計算的瓶頸值以進行進一步的執行是很好的作法。</span><span class="sxs-lookup"><span data-stu-id="b2d91-217">When training and validation data do not change often, it is good practice to cache the computed bottleneck values for further runs.</span></span>

1. <span data-ttu-id="b2d91-218">在您的專案中，建立名為*workspace*的新目錄，以儲存計算的瓶頸值和 `.pb` 模型的版本。</span><span class="sxs-lookup"><span data-stu-id="b2d91-218">In your project, create a new directory called *workspace* to store the computed bottleneck values and `.pb` version of the model.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="b2d91-219">定義路徑和初始化變數</span><span class="sxs-lookup"><span data-stu-id="b2d91-219">Define paths and initialize variables</span></span>

1. <span data-ttu-id="b2d91-220">在 `Main` 方法內，定義資產的位置、計算的瓶頸值和 `.pb` 模型的版本。</span><span class="sxs-lookup"><span data-stu-id="b2d91-220">Inside the `Main` method, define the location of your assets, computed bottleneck values and `.pb` version of the model.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L15-L17)]

1. <span data-ttu-id="b2d91-221">`mlContext`以[MLCoNtext](xref:Microsoft.ML.MLContext)的新實例初始化變數。</span><span class="sxs-lookup"><span data-stu-id="b2d91-221">Initialize the `mlContext` variable with a new instance of [MLContext](xref:Microsoft.ML.MLContext).</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L19)]

    <span data-ttu-id="b2d91-222">[MLCoNtext](xref:Microsoft.ML.MLContext)類別是所有 ML.NET 作業的起點，而初始化 MLCoNtext 會建立可在模型建立工作流程物件之間共用的新 ML.NET 環境。</span><span class="sxs-lookup"><span data-stu-id="b2d91-222">The [MLContext](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="b2d91-223">就概念而言，類似於 Entity Framework 中的 `DBContext`。</span><span class="sxs-lookup"><span data-stu-id="b2d91-223">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="b2d91-224">載入資料</span><span class="sxs-lookup"><span data-stu-id="b2d91-224">Load the data</span></span>

### <a name="create-data-loading-utility-method"></a><span data-ttu-id="b2d91-225">建立資料載入公用程式方法</span><span class="sxs-lookup"><span data-stu-id="b2d91-225">Create data loading utility method</span></span>

<span data-ttu-id="b2d91-226">映射會儲存在兩個子目錄中。</span><span class="sxs-lookup"><span data-stu-id="b2d91-226">The images are stored in two subdirectories.</span></span> <span data-ttu-id="b2d91-227">載入資料之前，必須先將它格式化成 `ImageData` 物件清單。</span><span class="sxs-lookup"><span data-stu-id="b2d91-227">Before loading the data, it needs to be formatted into a list of `ImageData` objects.</span></span> <span data-ttu-id="b2d91-228">若要這麼做，請 `LoadImagesFromDirectory` 在方法下方建立方法 `Main` 。</span><span class="sxs-lookup"><span data-stu-id="b2d91-228">To do so, create the `LoadImagesFromDirectory` method below the `Main` method.</span></span>

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. <span data-ttu-id="b2d91-229">在中， `LoadImagesDirectory` 新增下列程式碼，以從子目錄取得所有檔案路徑：</span><span class="sxs-lookup"><span data-stu-id="b2d91-229">Inside the `LoadImagesDirectory` add the following code to get all of the file paths from the subdirectories:</span></span>

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L104-L105)]

1. <span data-ttu-id="b2d91-230">然後，使用語句逐一查看每個檔案 `foreach` 。</span><span class="sxs-lookup"><span data-stu-id="b2d91-230">Then, iterate through each of the files using a `foreach` statement.</span></span>

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. <span data-ttu-id="b2d91-231">在 `foreach` 語句內，檢查是否支援副檔名。</span><span class="sxs-lookup"><span data-stu-id="b2d91-231">Inside the `foreach` statement, check that the file extensions are supported.</span></span> <span data-ttu-id="b2d91-232">影像分類 API 支援 JPEG 和 PNG 格式。</span><span class="sxs-lookup"><span data-stu-id="b2d91-232">The Image Classification API supports JPEG and PNG formats.</span></span>

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L109-L110)]

1. <span data-ttu-id="b2d91-233">然後，取得檔案的標籤。</span><span class="sxs-lookup"><span data-stu-id="b2d91-233">Then, get the label for the file.</span></span> <span data-ttu-id="b2d91-234">如果 `useFolderNameAsLabel` 參數設定為，則會 `true` 使用儲存檔案的上層目錄做為標籤。</span><span class="sxs-lookup"><span data-stu-id="b2d91-234">If the `useFolderNameAsLabel` parameter is set to `true`, then the parent directory where the file is saved is used as the label.</span></span> <span data-ttu-id="b2d91-235">否則，它會預期標籤必須是檔案名或檔案名本身的前置詞。</span><span class="sxs-lookup"><span data-stu-id="b2d91-235">Otherwise, it expects the label to be a prefix of the file name or the file name itself.</span></span>

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L112-L126)]

1. <span data-ttu-id="b2d91-236">最後，建立的新實例 `ModelInput` 。</span><span class="sxs-lookup"><span data-stu-id="b2d91-236">Finally, create a new instance of `ModelInput`.</span></span>

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L128-L132)]

### <a name="prepare-the-data"></a><span data-ttu-id="b2d91-237">準備資料</span><span class="sxs-lookup"><span data-stu-id="b2d91-237">Prepare the data</span></span>

1. <span data-ttu-id="b2d91-238">回到方法中 `Main` ，使用 `LoadFromDirectory` 公用程式方法來取得用於定型的影像清單。</span><span class="sxs-lookup"><span data-stu-id="b2d91-238">Back in the `Main` method, use the `LoadFromDirectory` utility method to get the list of images used for training.</span></span>

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L21)]

1. <span data-ttu-id="b2d91-239">然後， [`IDataView`](xref:Microsoft.ML.IDataView) 使用方法將影像載入中 [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) 。</span><span class="sxs-lookup"><span data-stu-id="b2d91-239">Then, load the images into an [`IDataView`](xref:Microsoft.ML.IDataView) using the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method.</span></span>

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L23)]

1. <span data-ttu-id="b2d91-240">資料會以從目錄中讀取的順序載入。</span><span class="sxs-lookup"><span data-stu-id="b2d91-240">The data is loaded in the order it was read from the directories.</span></span> <span data-ttu-id="b2d91-241">若要平衡資料，請使用方法將其隨機播放 [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) 。</span><span class="sxs-lookup"><span data-stu-id="b2d91-241">To balance the data, shuffle it using the [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) method.</span></span>

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L25)]

1. <span data-ttu-id="b2d91-242">機器學習模型預期輸入為數值格式。</span><span class="sxs-lookup"><span data-stu-id="b2d91-242">Machine learning models expect input to be in numerical format.</span></span> <span data-ttu-id="b2d91-243">因此，必須在定型之前對資料進行一些前置處理。</span><span class="sxs-lookup"><span data-stu-id="b2d91-243">Therefore, some preprocessing needs to be done on the data prior to training.</span></span> <span data-ttu-id="b2d91-244">建立 [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) 由和轉換組成的 [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) `LoadRawImageBytes` 。</span><span class="sxs-lookup"><span data-stu-id="b2d91-244">Create an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) made up of the [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) and `LoadRawImageBytes` transforms.</span></span> <span data-ttu-id="b2d91-245">`MapValueToKey`轉換會採用資料行中的類別值 `Label` ，將它轉換成數值， `KeyType` 並將它儲存在名為的新資料行中 `LabelAsKey` 。</span><span class="sxs-lookup"><span data-stu-id="b2d91-245">The `MapValueToKey` transform takes the categorical value in the `Label` column, converts it to a numerical `KeyType` value and stores it in a new column called `LabelAsKey`.</span></span> <span data-ttu-id="b2d91-246">`LoadImages`會採用資料行中的值 `ImagePath` 以及 `imageFolder` 參數來載入要定型的影像。</span><span class="sxs-lookup"><span data-stu-id="b2d91-246">The `LoadImages` takes the values from the `ImagePath` column along with the `imageFolder` parameter to load images for training.</span></span>

    [!code-csharp [PreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L27-L33)]

1. <span data-ttu-id="b2d91-247">使用 [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) 方法，將資料套用至 `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) 後面接著 [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) 方法的，其會傳回 [`IDataView`](xref:Microsoft.ML.IDataView) 包含預先處理資料的。</span><span class="sxs-lookup"><span data-stu-id="b2d91-247">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to apply the data to the `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) followed by the [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) method, which returns an [`IDataView`](xref:Microsoft.ML.IDataView) containing the pre-processed data.</span></span>

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L35-L37)]

1. <span data-ttu-id="b2d91-248">若要定型模型，請務必具有訓練資料集和驗證資料集。</span><span class="sxs-lookup"><span data-stu-id="b2d91-248">To train a model, it's important to have a training dataset as well as a validation dataset.</span></span> <span data-ttu-id="b2d91-249">此模型會在定型集上定型。</span><span class="sxs-lookup"><span data-stu-id="b2d91-249">The model is trained on the training set.</span></span> <span data-ttu-id="b2d91-250">其對未看到資料進行預測的程度，是根據驗證集的效能來測量。</span><span class="sxs-lookup"><span data-stu-id="b2d91-250">How well it makes predictions on unseen data is measured by the performance against the validation set.</span></span> <span data-ttu-id="b2d91-251">根據該效能的結果，此模型會調整其所學習到的成果以改善。</span><span class="sxs-lookup"><span data-stu-id="b2d91-251">Based on the results of that performance, the model makes adjustments to what it has learned in an effort to improve.</span></span> <span data-ttu-id="b2d91-252">驗證集可能來自于分割您的原始資料集，或來自已針對此用途設定的另一個來源。</span><span class="sxs-lookup"><span data-stu-id="b2d91-252">The validation set can come from either splitting your original dataset or from another source that has already been set aside for this purpose.</span></span> <span data-ttu-id="b2d91-253">在此情況下，預先處理的資料集會分割成定型、驗證和測試集。</span><span class="sxs-lookup"><span data-stu-id="b2d91-253">In this case, the pre-processed dataset is split into training, validation and test sets.</span></span>

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L39-L40)]

    <span data-ttu-id="b2d91-254">上述程式碼範例會執行兩個分割。</span><span class="sxs-lookup"><span data-stu-id="b2d91-254">The code sample above performs two splits.</span></span> <span data-ttu-id="b2d91-255">首先，預先處理的資料會被分割，而70% 用於定型，而剩餘的30% 則用於驗證。</span><span class="sxs-lookup"><span data-stu-id="b2d91-255">First, the pre-processed data is split and 70% is used for training while the remaining 30% is used for validation.</span></span> <span data-ttu-id="b2d91-256">然後，30% 的驗證集會進一步分割成驗證和測試集，其中90% 用於驗證，而10% 用於測試。</span><span class="sxs-lookup"><span data-stu-id="b2d91-256">Then, the 30% validation set is further split into validation and test sets where 90% is used for validation and 10% is used for testing.</span></span>

    <span data-ttu-id="b2d91-257">有一種方法可以思考這些資料分割的用途，這是一項測驗。</span><span class="sxs-lookup"><span data-stu-id="b2d91-257">A way to think about the purpose of these data partitions is taking an exam.</span></span> <span data-ttu-id="b2d91-258">在研究測驗時，您會複習您的記事、書籍或其他資源，以瞭解測驗上的概念。</span><span class="sxs-lookup"><span data-stu-id="b2d91-258">When studying for an exam, you review your notes, books, or other resources to get a grasp on the concepts that are on the exam.</span></span> <span data-ttu-id="b2d91-259">這就是定型集的用途。</span><span class="sxs-lookup"><span data-stu-id="b2d91-259">This is what the train set is for.</span></span> <span data-ttu-id="b2d91-260">然後，您可能會進行模擬測驗來驗證您的知識。</span><span class="sxs-lookup"><span data-stu-id="b2d91-260">Then, you might take a mock exam to validate your knowledge.</span></span> <span data-ttu-id="b2d91-261">這就是驗證集派上用場的地方。</span><span class="sxs-lookup"><span data-stu-id="b2d91-261">This is where the validation set comes in handy.</span></span> <span data-ttu-id="b2d91-262">在進行實際測驗之前，您想要先檢查是否有良好的概念。</span><span class="sxs-lookup"><span data-stu-id="b2d91-262">You want to check whether you have a good grasp of the concepts before taking the actual exam.</span></span> <span data-ttu-id="b2d91-263">根據這些結果，您可以記下錯誤或不了解的內容，並在您查看實際測驗時納入變更。</span><span class="sxs-lookup"><span data-stu-id="b2d91-263">Based on those results, you take note of what you got wrong or didn't understand well and incorporate your changes as you review for the real exam.</span></span> <span data-ttu-id="b2d91-264">最後，您要進行測驗。</span><span class="sxs-lookup"><span data-stu-id="b2d91-264">Finally, you take the exam.</span></span> <span data-ttu-id="b2d91-265">這就是測試集的用途。</span><span class="sxs-lookup"><span data-stu-id="b2d91-265">This is what the test set is used for.</span></span> <span data-ttu-id="b2d91-266">您從未見過測驗中的問題，現在使用您從訓練和驗證中學到的內容，將您的知識套用至手邊的工作。</span><span class="sxs-lookup"><span data-stu-id="b2d91-266">You've never seen the questions that are on the exam and now use what you learned from training and validation to apply your knowledge to the task at hand.</span></span>

1. <span data-ttu-id="b2d91-267">針對定型、驗證和測試資料，將分割區的個別值指派給分割區。</span><span class="sxs-lookup"><span data-stu-id="b2d91-267">Assign the partitions their respective values for the train, validation and test data.</span></span>

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L42-L44)]

## <a name="define-the-training-pipeline"></a><span data-ttu-id="b2d91-268">定義定型管線</span><span class="sxs-lookup"><span data-stu-id="b2d91-268">Define the training pipeline</span></span>

<span data-ttu-id="b2d91-269">模型訓練包含幾個步驟。</span><span class="sxs-lookup"><span data-stu-id="b2d91-269">Model training consists of a couple of steps.</span></span> <span data-ttu-id="b2d91-270">首先，使用影像分類 API 來定型模型。</span><span class="sxs-lookup"><span data-stu-id="b2d91-270">First, Image Classification API is used to train the model.</span></span> <span data-ttu-id="b2d91-271">然後，會使用轉換，將資料行中編碼的標籤 `PredictedLabel` 轉換回其原始類別值 `MapKeyToValue` 。</span><span class="sxs-lookup"><span data-stu-id="b2d91-271">Then, the encoded labels in the `PredictedLabel` column are converted back to their original categorical value using the `MapKeyToValue` transform.</span></span>

1. <span data-ttu-id="b2d91-272">建立新變數，以儲存的一組必要和選擇性參數 `ImageClassificationTrainer` 。</span><span class="sxs-lookup"><span data-stu-id="b2d91-272">Create a new variable to store a set of required and optional parameters for an `ImageClassificationTrainer`.</span></span>

    [!code-csharp [ClassifierOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L46-L57)]

    <span data-ttu-id="b2d91-273">`ImageClassificationTrainer`會採用數個選擇性參數：</span><span class="sxs-lookup"><span data-stu-id="b2d91-273">An `ImageClassificationTrainer` takes several optional parameters:</span></span>

    - <span data-ttu-id="b2d91-274">`FeatureColumnName`這是用來做為模型輸入的資料行。</span><span class="sxs-lookup"><span data-stu-id="b2d91-274">`FeatureColumnName` is the column that is used as input for the model.</span></span>
    - <span data-ttu-id="b2d91-275">`LabelColumnName`這是要預測之值的資料行。</span><span class="sxs-lookup"><span data-stu-id="b2d91-275">`LabelColumnName` is the column for the value to predict.</span></span>
    - <span data-ttu-id="b2d91-276">`ValidationSet`是 [`IDataView`](xref:Microsoft.ML.IDataView) 包含驗證資料的。</span><span class="sxs-lookup"><span data-stu-id="b2d91-276">`ValidationSet` is the [`IDataView`](xref:Microsoft.ML.IDataView) containing the validation data.</span></span>
    - <span data-ttu-id="b2d91-277">`Arch`定義要使用的預先定型模型架構。</span><span class="sxs-lookup"><span data-stu-id="b2d91-277">`Arch` defines which of the pretrained model architectures to use.</span></span> <span data-ttu-id="b2d91-278">本教學課程使用 ResNetv2 模型的101層變體。</span><span class="sxs-lookup"><span data-stu-id="b2d91-278">This tutorial uses the 101-layer variant of the ResNetv2 model.</span></span>
    - <span data-ttu-id="b2d91-279">`MetricsCallback`系結函式以追蹤定型期間的進度。</span><span class="sxs-lookup"><span data-stu-id="b2d91-279">`MetricsCallback` binds a function to track the progress during training.</span></span>
    - <span data-ttu-id="b2d91-280">`TestOnTrainSet`告知模型在沒有任何驗證集時，測量定型集的效能。</span><span class="sxs-lookup"><span data-stu-id="b2d91-280">`TestOnTrainSet` tells the model to measure performance against the training set when no validation set is present.</span></span>
    - <span data-ttu-id="b2d91-281">`ReuseTrainSetBottleneckCachedValues`告訴模型，是否要在後續執行的瓶頸階段中使用快取的值。</span><span class="sxs-lookup"><span data-stu-id="b2d91-281">`ReuseTrainSetBottleneckCachedValues` tells the model whether to use the cached values from the bottleneck phase in subsequent runs.</span></span> <span data-ttu-id="b2d91-282">瓶頸階段是單次傳遞計算，在第一次執行時需要大量計算。</span><span class="sxs-lookup"><span data-stu-id="b2d91-282">The bottleneck phase is a one-time pass-through computation that is computationally intensive the first time it is performed.</span></span> <span data-ttu-id="b2d91-283">如果定型資料不會變更，而您想要使用不同數目的 epoch 或批次大小進行實驗，則使用快取的值會大幅減少定型模型所需的時間量。</span><span class="sxs-lookup"><span data-stu-id="b2d91-283">If the training data does not change and you want to experiment using a different number of epochs or batch size, using the cached values significantly reduces the amount of time required to train a model.</span></span>
    - <span data-ttu-id="b2d91-284">`ReuseValidationSetBottleneckCachedValues`類似于 `ReuseTrainSetBottleneckCachedValues` 在此情況下，它是用於驗證資料集。</span><span class="sxs-lookup"><span data-stu-id="b2d91-284">`ReuseValidationSetBottleneckCachedValues` is similar to `ReuseTrainSetBottleneckCachedValues` only that in this case it's for the validation dataset.</span></span>
    - <span data-ttu-id="b2d91-285">`WorkspacePath`定義要儲存計算的瓶頸值和 `.pb` 模型版本的目錄。</span><span class="sxs-lookup"><span data-stu-id="b2d91-285">`WorkspacePath` defines the directory where to store the computed bottleneck values and `.pb` version of the model.</span></span>

1. <span data-ttu-id="b2d91-286">定義 [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) 由和組成的定型管線 `mapLabelEstimator` `ImageClassificationTrainer` 。</span><span class="sxs-lookup"><span data-stu-id="b2d91-286">Define the [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) training pipeline that consists of both the `mapLabelEstimator` and the `ImageClassificationTrainer`.</span></span>

    [!code-csharp [TrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L59-L60)]

1. <span data-ttu-id="b2d91-287">使用 [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) 方法來定型您的模型。</span><span class="sxs-lookup"><span data-stu-id="b2d91-287">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to train your model.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L62)]

## <a name="use-the-model"></a><span data-ttu-id="b2d91-288">使用模型</span><span class="sxs-lookup"><span data-stu-id="b2d91-288">Use the model</span></span>

<span data-ttu-id="b2d91-289">既然您已定型模型，現在可以用它來分類影像。</span><span class="sxs-lookup"><span data-stu-id="b2d91-289">Now that you have trained your model, it's time to use it to classify images.</span></span>

<span data-ttu-id="b2d91-290">在 `Main` 方法下方，建立名為的新公用程式方法， `OutputPrediction` 以在主控台中顯示預測資訊。</span><span class="sxs-lookup"><span data-stu-id="b2d91-290">Below the `Main` method, create a new utility method called `OutputPrediction` to display prediction information in the console.</span></span>

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L96-L100)]

### <a name="classify-a-single-image"></a><span data-ttu-id="b2d91-291">分類單一影像</span><span class="sxs-lookup"><span data-stu-id="b2d91-291">Classify a single image</span></span>

1. <span data-ttu-id="b2d91-292">在方法下方新增名為的方法， `ClassifySingleImage` `Main` 以進行單一影像預測並輸出。</span><span class="sxs-lookup"><span data-stu-id="b2d91-292">Add a new method called `ClassifySingleImage` below the `Main` method to make and output a single image prediction.</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="b2d91-293">在 [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) 方法內建立 `ClassifySingleImage` 。</span><span class="sxs-lookup"><span data-stu-id="b2d91-293">Create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) inside the `ClassifySingleImage` method.</span></span> <span data-ttu-id="b2d91-294">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)是一個方便的 API，可讓您傳入，然後在單一資料實例上執行預測。</span><span class="sxs-lookup"><span data-stu-id="b2d91-294">The [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span>

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L73)]

1. <span data-ttu-id="b2d91-295">若要存取單一 `ModelInput` 實例，請 `data` [`IDataView`](xref:Microsoft.ML.IDataView) 使用方法將轉換成， [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) 然後取得第一個觀察。</span><span class="sxs-lookup"><span data-stu-id="b2d91-295">To access a single `ModelInput` instance, convert the `data` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first observation.</span></span>

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L75)]

1. <span data-ttu-id="b2d91-296">使用 [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) 方法來分類映射。</span><span class="sxs-lookup"><span data-stu-id="b2d91-296">Use the [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) method to classify the image.</span></span>

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L77)]

1. <span data-ttu-id="b2d91-297">使用方法將預測輸出至主控台 `OutputPrediction` 。</span><span class="sxs-lookup"><span data-stu-id="b2d91-297">Output the prediction to the console with the `OutputPrediction` method.</span></span>

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L79-L80)]

1. <span data-ttu-id="b2d91-298">在 `Main` 方法內， `ClassifySingleImage` 使用影像的測試集呼叫。</span><span class="sxs-lookup"><span data-stu-id="b2d91-298">Inside the `Main` method, call `ClassifySingleImage` using the test set of images.</span></span>

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L64)]

### <a name="classify-multiple-images"></a><span data-ttu-id="b2d91-299">分類多個映射</span><span class="sxs-lookup"><span data-stu-id="b2d91-299">Classify multiple images</span></span>

1. <span data-ttu-id="b2d91-300">`ClassifyImages`在方法下方新增名為的方法， `ClassifySingleImage` 以建立和輸出多個影像預測。</span><span class="sxs-lookup"><span data-stu-id="b2d91-300">Add a new method called `ClassifyImages` below the `ClassifySingleImage` method to make and output multiple image predictions.</span></span>

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="b2d91-301">[`IDataView`](xref:Microsoft.ML.IDataView)使用方法，建立包含預測的 [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) 。</span><span class="sxs-lookup"><span data-stu-id="b2d91-301">Create an [`IDataView`](xref:Microsoft.ML.IDataView) containing the predictions by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method.</span></span> <span data-ttu-id="b2d91-302">將下列程式碼新增至 `ClassifyImages` 方法內。</span><span class="sxs-lookup"><span data-stu-id="b2d91-302">Add the following code inside the `ClassifyImages` method.</span></span>

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L85)]

1. <span data-ttu-id="b2d91-303">為了反復執行預測，請使用方法將轉換 `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) 成， [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) 然後取得前10個觀察。</span><span class="sxs-lookup"><span data-stu-id="b2d91-303">In order to iterate over the predictions, convert the `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first 10 observations.</span></span>

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L87)]

1. <span data-ttu-id="b2d91-304">反覆運算和輸出預測的原始和預測標籤。</span><span class="sxs-lookup"><span data-stu-id="b2d91-304">Iterate and output the original and predicted labels for the predictions.</span></span>

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L89-L93)]

1. <span data-ttu-id="b2d91-305">最後，在 `Main` 方法中， `ClassifyImages` 使用影像的測試集呼叫。</span><span class="sxs-lookup"><span data-stu-id="b2d91-305">Finally, inside the `Main` method, call `ClassifyImages` using the test set of images.</span></span>

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L66)]

## <a name="run-the-application"></a><span data-ttu-id="b2d91-306">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="b2d91-306">Run the application</span></span>

<span data-ttu-id="b2d91-307">執行您的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2d91-307">Run your console app.</span></span> <span data-ttu-id="b2d91-308">輸出應該如下所示。</span><span class="sxs-lookup"><span data-stu-id="b2d91-308">The output should be similar to that below.</span></span> <span data-ttu-id="b2d91-309">您可能會看到警告或處理中訊息，但為了讓結果變得清楚，這些訊息已從下列結果中移除。</span><span class="sxs-lookup"><span data-stu-id="b2d91-309">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span> <span data-ttu-id="b2d91-310">為求簡潔，輸出已壓縮。</span><span class="sxs-lookup"><span data-stu-id="b2d91-310">For brevity, the output has been condensed.</span></span>

<span data-ttu-id="b2d91-311">**瓶頸階段**</span><span class="sxs-lookup"><span data-stu-id="b2d91-311">**Bottleneck phase**</span></span>

<span data-ttu-id="b2d91-312">影像名稱不會列印任何值，因為影像會載入為， `byte[]` 因此不會顯示任何影像名稱。</span><span class="sxs-lookup"><span data-stu-id="b2d91-312">No value is printed for the image name because the images are loaded as a `byte[]` therefore there is no image name to display.</span></span>

```test
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 279
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 280
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   1
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   2
```

<span data-ttu-id="b2d91-313">**訓練階段**</span><span class="sxs-lookup"><span data-stu-id="b2d91-313">**Training phase**</span></span>

```text
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  21, Accuracy:  0.6797619
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  22, Accuracy:  0.7642857
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  23, Accuracy:  0.7916667
```

<span data-ttu-id="b2d91-314">**分類影像輸出**</span><span class="sxs-lookup"><span data-stu-id="b2d91-314">**Classify images output**</span></span>

```text
Classifying single image
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD

Classifying multiple images
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-163.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-210.jpg | Actual Value: UD | Predicted Value: UD
```

<span data-ttu-id="b2d91-315">在檢查*7001-220 .jpg*影像之後，您可以看到它實際上不會被破解。</span><span class="sxs-lookup"><span data-stu-id="b2d91-315">Upon inspection of the *7001-220.jpg* image, you can see that it in fact is not cracked.</span></span>

![用於預測的 SDNET2018 資料集影像](./media/image-classification-api-transfer-learning/predictedimage.jpg)

<span data-ttu-id="b2d91-317">恭喜！</span><span class="sxs-lookup"><span data-stu-id="b2d91-317">Congratulations!</span></span> <span data-ttu-id="b2d91-318">您現在已成功建立用於分類影像的深度學習模型。</span><span class="sxs-lookup"><span data-stu-id="b2d91-318">You've now successfully built a deep learning model for classifying images.</span></span>

### <a name="improve-the-model"></a><span data-ttu-id="b2d91-319">改善模型</span><span class="sxs-lookup"><span data-stu-id="b2d91-319">Improve the model</span></span>

<span data-ttu-id="b2d91-320">如果您不滿意模型的結果，您可以嘗試下列一些方法來提升其效能：</span><span class="sxs-lookup"><span data-stu-id="b2d91-320">If you're not satisfied with the results of your model, you can try to improve its performance by trying some of the following approaches:</span></span>

- <span data-ttu-id="b2d91-321">**更多資料**：模型從中學習的範例越多，執行的效能就愈好。</span><span class="sxs-lookup"><span data-stu-id="b2d91-321">**More Data**: The more examples a model learns from, the better it performs.</span></span> <span data-ttu-id="b2d91-322">下載完整的[SDNET2018 資料集](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional)，並使用它來進行定型。</span><span class="sxs-lookup"><span data-stu-id="b2d91-322">Download the full [SDNET2018 dataset](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) and use it to train.</span></span>
- <span data-ttu-id="b2d91-323">**增強資料**：將各種資料新增至資料的常見技術是藉由取得影像並套用不同的轉換（旋轉、翻轉、shift、裁剪）來擴大資料。</span><span class="sxs-lookup"><span data-stu-id="b2d91-323">**Augment the data**: A common technique to add variety to the data is to augment the data by taking an image and applying different transforms (rotate, flip, shift, crop).</span></span> <span data-ttu-id="b2d91-324">這會為要從中學習的模型加入更多不同的範例。</span><span class="sxs-lookup"><span data-stu-id="b2d91-324">This adds more varied examples for the model to learn from.</span></span>
- <span data-ttu-id="b2d91-325">**訓練較長的時間**：您所定型的時間愈久，模型的微調就愈多。</span><span class="sxs-lookup"><span data-stu-id="b2d91-325">**Train for a longer time**: The longer you train, the more tuned the model will be.</span></span> <span data-ttu-id="b2d91-326">增加 epoch 數目可能會改善模型的效能。</span><span class="sxs-lookup"><span data-stu-id="b2d91-326">Increasing the number of epochs may improve the performance of your model.</span></span>
- <span data-ttu-id="b2d91-327">**使用超參數進行實驗**：除了本教學課程中使用的參數之外，其他參數也可以調整，以改善效能。</span><span class="sxs-lookup"><span data-stu-id="b2d91-327">**Experiment with the hyper-parameters**: In addition to the parameters used in this tutorial, other parameters can be tuned to potentially improve performance.</span></span> <span data-ttu-id="b2d91-328">變更學習速率，以決定在每個 epoch 之後對模型所做的更新大小，可能會改善效能。</span><span class="sxs-lookup"><span data-stu-id="b2d91-328">Changing the learning rate, which determines the magnitude of updates made to the model after each epoch may improve performance.</span></span>
- <span data-ttu-id="b2d91-329">**使用不同的模型架構**：根據您的資料看起來的樣子，可以充分瞭解其功能的模型可能會有所不同。</span><span class="sxs-lookup"><span data-stu-id="b2d91-329">**Use a different model architecture**: Depending on what your data looks like, the model that can best learn its features may differ.</span></span> <span data-ttu-id="b2d91-330">如果您不滿意模型的效能，請嘗試變更架構。</span><span class="sxs-lookup"><span data-stu-id="b2d91-330">If you're not satisfied with the performance of your model, try changing the architecture.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="b2d91-331">其他資源</span><span class="sxs-lookup"><span data-stu-id="b2d91-331">Additional Resources</span></span>

- <span data-ttu-id="b2d91-332">[深度學習與 Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning)。</span><span class="sxs-lookup"><span data-stu-id="b2d91-332">[Deep Learning vs Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span></span>

## <a name="next-steps"></a><span data-ttu-id="b2d91-333">後續步驟</span><span class="sxs-lookup"><span data-stu-id="b2d91-333">Next steps</span></span>

<span data-ttu-id="b2d91-334">在本教學課程中，您已瞭解如何使用「傳輸學習」（預先定型影像分類 TensorFlow 模型和 ML.NET 影像分類 API）來建立自訂深度學習模型，以將具體表面的影像分類為破裂或 uncracked。</span><span class="sxs-lookup"><span data-stu-id="b2d91-334">In this tutorial, you learned how to build a custom deep learning model using transfer learning, a pretrained image classification TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="b2d91-335">前進到下一個教學課程來深入了解。</span><span class="sxs-lookup"><span data-stu-id="b2d91-335">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b2d91-336">物件偵測</span><span class="sxs-lookup"><span data-stu-id="b2d91-336">Object Detection</span></span>](object-detection-onnx.md)
