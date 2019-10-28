---
title: 教學課程：使用傳輸學習的自動化視覺效果檢查
description: 本教學課程說明如何使用「傳輸學習」來定型 ML.NET 中的 TensorFlow 深度學習模型，其方式是使用影像偵測 API，將具體介面的影像分類為破裂或未破解。
author: luisquintanilla
ms.author: luquinta
ms.date: 10/25/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: b8aec80134188811eb80ad1394e5a64d65a3c6f0
ms.sourcegitcommit: 9b2ef64c4fc10a4a10f28a223d60d17d7d249ee8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/26/2019
ms.locfileid: "72961984"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a><span data-ttu-id="91652-103">教學課程：搭配 ML.NET 影像分類 API 使用傳輸學習的自動化視覺效果檢查</span><span class="sxs-lookup"><span data-stu-id="91652-103">Tutorial: Automated visual inspection using transfer learning with the ML.NET Image Classification API</span></span>

<span data-ttu-id="91652-104">瞭解如何使用「傳輸學習」（預先定型 TensorFlow 模型）和「ML.NET 影像分類 API」來定型自訂深度學習模型，以將具體表面的影像分類為破裂或 uncracked。</span><span class="sxs-lookup"><span data-stu-id="91652-104">Learn how to train a custom deep learning model using transfer learning, a pretrained TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

> [!NOTE]
> <span data-ttu-id="91652-105">本教學課程使用 ML.NET 影像分類 API 的預覽版本。</span><span class="sxs-lookup"><span data-stu-id="91652-105">This tutorial uses a preview version of the ML.NET Image Classification API.</span></span>

<span data-ttu-id="91652-106">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="91652-106">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="91652-107">了解問題</span><span class="sxs-lookup"><span data-stu-id="91652-107">Understand the problem</span></span>
> - <span data-ttu-id="91652-108">瞭解 ML.NET 影像分類 API</span><span class="sxs-lookup"><span data-stu-id="91652-108">Learn about ML.NET Image Classification API</span></span>
> - <span data-ttu-id="91652-109">瞭解預先定型模型</span><span class="sxs-lookup"><span data-stu-id="91652-109">Understand the pretrained model</span></span>
> - <span data-ttu-id="91652-110">使用傳輸學習來定型自訂 TensorFlow 影像分類模型</span><span class="sxs-lookup"><span data-stu-id="91652-110">Use transfer learning to train a custom TensorFlow image classification model</span></span>
> - <span data-ttu-id="91652-111">使用自訂模型分類影像</span><span class="sxs-lookup"><span data-stu-id="91652-111">Classify images with the custom model</span></span>

## <a name="prerequisites"></a><span data-ttu-id="91652-112">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="91652-112">Prerequisites</span></span>

- <span data-ttu-id="91652-113">已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)。</span><span class="sxs-lookup"><span data-stu-id="91652-113">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="image-classification-transfer-learning-sample-overview"></a><span data-ttu-id="91652-114">影像分類傳輸學習範例總覽</span><span class="sxs-lookup"><span data-stu-id="91652-114">Image classification transfer learning sample overview</span></span>

<span data-ttu-id="91652-115">此範例是C# .net Core 主控台應用程式，可使用預先定型深度學習 TensorFlow 模型來分類影像。</span><span class="sxs-lookup"><span data-stu-id="91652-115">This sample is a C# .NET Core console application that classifies images using a pretrained deep learning TensorFlow model.</span></span> <span data-ttu-id="91652-116">您可以在 GitHub 的 [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) 找到此範例的程式碼。</span><span class="sxs-lookup"><span data-stu-id="91652-116">The code for this sample can be found on the [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="91652-117">了解問題</span><span class="sxs-lookup"><span data-stu-id="91652-117">Understand the problem</span></span>

<span data-ttu-id="91652-118">影像分類是電腦視覺問題。</span><span class="sxs-lookup"><span data-stu-id="91652-118">Image classification is a computer vision problem.</span></span> <span data-ttu-id="91652-119">影像分類會將影像做為輸入，並將其分類為指定的類別。</span><span class="sxs-lookup"><span data-stu-id="91652-119">Image classification takes an image as input and categorizes it into a prescribed class.</span></span> <span data-ttu-id="91652-120">影像分類非常有用的部分案例包括：</span><span class="sxs-lookup"><span data-stu-id="91652-120">Some scenarios where image classification is useful include:</span></span>

- <span data-ttu-id="91652-121">臉部辨識</span><span class="sxs-lookup"><span data-stu-id="91652-121">Facial recognition</span></span>
- <span data-ttu-id="91652-122">表情偵測</span><span class="sxs-lookup"><span data-stu-id="91652-122">Emotion detection</span></span>
- <span data-ttu-id="91652-123">醫療診斷</span><span class="sxs-lookup"><span data-stu-id="91652-123">Medical diagnosis</span></span>
- <span data-ttu-id="91652-124">地標偵測</span><span class="sxs-lookup"><span data-stu-id="91652-124">Landmark detection</span></span>

<span data-ttu-id="91652-125">本教學課程會將自訂影像分類模型定型，以執行橋接器投影片的自動化視覺效果檢查，以識別破裂所損毀的結構。</span><span class="sxs-lookup"><span data-stu-id="91652-125">This tutorial trains a custom image classification model to perform automated visual inspection of bridge decks to identify structures that are damaged by cracks.</span></span>

## <a name="mlnet-image-classification-api"></a><span data-ttu-id="91652-126">ML.NET 影像分類 API</span><span class="sxs-lookup"><span data-stu-id="91652-126">ML.NET Image Classification API</span></span>

<span data-ttu-id="91652-127">ML.NET 提供各種執行影像分類的方式。</span><span class="sxs-lookup"><span data-stu-id="91652-127">ML.NET provides various ways of performing image classification.</span></span> <span data-ttu-id="91652-128">本教學課程會使用影像分類 API 來套用傳輸學習。</span><span class="sxs-lookup"><span data-stu-id="91652-128">This tutorial applies transfer learning using the Image Classification API.</span></span> <span data-ttu-id="91652-129">影像分類 API 會使用[TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET)，這是為 TensorFlow C# C++ API 提供系結的低層級程式庫。</span><span class="sxs-lookup"><span data-stu-id="91652-129">The Image Classification API makes use of [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), a low-level library that provides C# bindings for the TensorFlow C++ API.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="91652-130">什麼是傳輸學習？</span><span class="sxs-lookup"><span data-stu-id="91652-130">What is transfer learning?</span></span>

<span data-ttu-id="91652-131">轉移學習會將解決一個問題所獲得的知識套用至另一個相關問題。</span><span class="sxs-lookup"><span data-stu-id="91652-131">Transfer learning applies knowledge gained from solving one problem to another related problem.</span></span>

<span data-ttu-id="91652-132">從頭開始訓練深度學習模型，需要設定數個參數、大量標記的定型資料，以及大量的計算資源（數百個 GPU 小時）。</span><span class="sxs-lookup"><span data-stu-id="91652-132">Training a deep learning model from scratch requires setting several parameters, a large amount of labeled training data, and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="91652-133">搭配使用預先定型模型與轉移學習，可讓您將定型程式的快捷方式。</span><span class="sxs-lookup"><span data-stu-id="91652-133">Using a pretrained model along with transfer learning allows you to shortcut the training process.</span></span> 

## <a name="training-process"></a><span data-ttu-id="91652-134">訓練流程</span><span class="sxs-lookup"><span data-stu-id="91652-134">Training process</span></span>

<span data-ttu-id="91652-135">影像分類 API 會藉由載入預先定型 TensorFlow 模型來啟動定型程式。</span><span class="sxs-lookup"><span data-stu-id="91652-135">The Image Classification API starts the training process by loading a pretrained TensorFlow model.</span></span> <span data-ttu-id="91652-136">定型套裝程式含兩個步驟：</span><span class="sxs-lookup"><span data-stu-id="91652-136">The training process consists of two steps:</span></span>

1. <span data-ttu-id="91652-137">瓶頸階段</span><span class="sxs-lookup"><span data-stu-id="91652-137">Bottleneck phase</span></span>
2. <span data-ttu-id="91652-138">訓練階段</span><span class="sxs-lookup"><span data-stu-id="91652-138">Training phase</span></span>

![訓練步驟](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a><span data-ttu-id="91652-140">瓶頸階段</span><span class="sxs-lookup"><span data-stu-id="91652-140">Bottleneck phase</span></span>

<span data-ttu-id="91652-141">在瓶頸階段，會載入定型影像集，並使用圖元值做為預先定型模型之凍結層的輸入或特徵。</span><span class="sxs-lookup"><span data-stu-id="91652-141">During the bottleneck phase, the set of training images is loaded and the pixel values are used as input, or features, for the frozen layers of the pretrained model.</span></span> <span data-ttu-id="91652-142">凍結層包含類神經網路中的所有圖層，最多倒數第二層，非正式稱為瓶頸層。</span><span class="sxs-lookup"><span data-stu-id="91652-142">The frozen layers include all of the layers in the neural network up to the penultimate layer, informally known as the bottleneck layer.</span></span> <span data-ttu-id="91652-143">這些層級稱為「已凍結」，因為這些層上不會進行定型，而且作業會通過傳遞。</span><span class="sxs-lookup"><span data-stu-id="91652-143">These layers are referred to as frozen because no training will occur on these layers and operations are pass-through.</span></span> <span data-ttu-id="91652-144">這是在這些凍結層級，可協助模型區別不同類別的較低等級模式會進行計算。</span><span class="sxs-lookup"><span data-stu-id="91652-144">It's at these frozen layers where the lower-level patterns that help a model differentiate between the different classes are computed.</span></span> <span data-ttu-id="91652-145">層的數目越大，此步驟所需的計算密集型就愈多。</span><span class="sxs-lookup"><span data-stu-id="91652-145">The larger the number of layers, the more computationally intensive this step is.</span></span> <span data-ttu-id="91652-146">幸好，由於這是一次性的計算，因此可以快取結果，並在使用不同的參數進行實驗時，于稍後執行。</span><span class="sxs-lookup"><span data-stu-id="91652-146">Fortunately, since this is a one-time calculation, the results can be cached and used in later runs when experimenting with different parameters.</span></span>

### <a name="training-phase"></a><span data-ttu-id="91652-147">訓練階段</span><span class="sxs-lookup"><span data-stu-id="91652-147">Training phase</span></span>

<span data-ttu-id="91652-148">一旦計算出瓶頸階段的輸出值，就會使用它們做為輸入，以重新定型模型的最後一層。</span><span class="sxs-lookup"><span data-stu-id="91652-148">Once the output values from the bottleneck phase are computed, they are used as input to retrain the final layer of the model.</span></span> <span data-ttu-id="91652-149">此程式會反復執行，並針對模型參數所指定的次數執行。</span><span class="sxs-lookup"><span data-stu-id="91652-149">This process is iterative and runs for the number of times specified by model parameters.</span></span> <span data-ttu-id="91652-150">在每次執行期間，會評估遺失和精確度。</span><span class="sxs-lookup"><span data-stu-id="91652-150">During each run, the loss and accuracy are evaluated.</span></span> <span data-ttu-id="91652-151">然後，會進行適當的調整來改善模型，其目標是將遺失降至最低，並將精確度最大化。</span><span class="sxs-lookup"><span data-stu-id="91652-151">Then, the appropriate adjustments are made to improve the model with the goal of minimizing the loss and maximizing the accuracy.</span></span> <span data-ttu-id="91652-152">定型完成後，會輸出兩種模型格式。</span><span class="sxs-lookup"><span data-stu-id="91652-152">Once training is finished, two model formats are output.</span></span> <span data-ttu-id="91652-153">其中一個是模型的 `.pb` 版本，另一個是模型的 `.zip` ML.NET 序列化版本。</span><span class="sxs-lookup"><span data-stu-id="91652-153">One of them is the `.pb` version of the model and the other is the `.zip` ML.NET serialized version of the model.</span></span> <span data-ttu-id="91652-154">在 ML.NET 所支援的環境中工作時，建議使用模型的 `.zip` 版本。</span><span class="sxs-lookup"><span data-stu-id="91652-154">When working in environments supported by ML.NET, it is recommended to use the `.zip` version of the model.</span></span> <span data-ttu-id="91652-155">不過，在不支援 ML.NET 的環境中，您可以選擇使用 `.pb` 版本。</span><span class="sxs-lookup"><span data-stu-id="91652-155">However, in environments where ML.NET is not supported, you have the option of using the `.pb` version.</span></span>

## <a name="understand-the-pretrained-model"></a><span data-ttu-id="91652-156">瞭解預先定型模型</span><span class="sxs-lookup"><span data-stu-id="91652-156">Understand the pretrained model</span></span>

<span data-ttu-id="91652-157">本教學課程中使用的預先定型模型是「剩餘網路（ResNet） v2」模型的101層變體。</span><span class="sxs-lookup"><span data-stu-id="91652-157">The pretrained model used in this tutorial is the 101-layer variant of the Residual Network (ResNet) v2 model.</span></span> <span data-ttu-id="91652-158">原始模型已定型，可將影像分類為一千個類別。</span><span class="sxs-lookup"><span data-stu-id="91652-158">The original model is trained to classify images into a thousand categories.</span></span> <span data-ttu-id="91652-159">此模型會使用大小為 224 x 224 的影像做為輸入，並針對其定型的每個類別輸出類別機率。</span><span class="sxs-lookup"><span data-stu-id="91652-159">The model takes as input an image of size 224 x 224 and outputs the class probabilities for each of the classes it's trained on.</span></span> <span data-ttu-id="91652-160">此模型的一部分是用來使用自訂影像來定型新模型，以便在兩個類別之間進行預測。</span><span class="sxs-lookup"><span data-stu-id="91652-160">Part of this model is used to train a new model using custom images to make predictions between two classes.</span></span> 

## <a name="create-console-application"></a><span data-ttu-id="91652-161">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="91652-161">Create console application</span></span>

<span data-ttu-id="91652-162">既然您已大致瞭解轉移學習和影像分類 API，現在正是建立應用程式的時候了。</span><span class="sxs-lookup"><span data-stu-id="91652-162">Now that you have a general understanding of transfer learning and the Image Classification API, it's time to build the application.</span></span>

1. <span data-ttu-id="91652-163">建立名為 "DeepLearning_ImageClassification_Binary" 的 **C# .net Core 主控台應用程式**。</span><span class="sxs-lookup"><span data-stu-id="91652-163">Create a **C# .NET Core Console Application** called "DeepLearning_ImageClassification_Binary".</span></span>
1. <span data-ttu-id="91652-164">安裝**Microsoft.ML 1.4.0-preview2** NuGet 套件：</span><span class="sxs-lookup"><span data-stu-id="91652-164">Install the **Microsoft.ML 1.4.0-preview2** NuGet Package:</span></span>
    1. <span data-ttu-id="91652-165">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="91652-165">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="91652-166">選擇 "nuget.org" 作為套件來源。</span><span class="sxs-lookup"><span data-stu-id="91652-166">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="91652-167">選取 [瀏覽] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="91652-167">Select the **Browse** tab.</span></span>
    1. <span data-ttu-id="91652-168">勾選 [**包含發行**前版本] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="91652-168">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="91652-169">搜尋**Microsoft.ML**。</span><span class="sxs-lookup"><span data-stu-id="91652-169">Search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="91652-170">選取 [安裝] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="91652-170">Select the **Install** button.</span></span>
    1. <span data-ttu-id="91652-171">在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。</span><span class="sxs-lookup"><span data-stu-id="91652-171">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="91652-172">針對**Dnn 0.16.0-preview2**和**ImageAnalytics 1.4.0-preview2**重複這些步驟。</span><span class="sxs-lookup"><span data-stu-id="91652-172">Repeat these steps for **Microsoft.ML.Dnn 0.16.0-preview2** and **Microsoft.ML.ImageAnalytics 1.4.0-preview2**.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="91652-173">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="91652-173">Prepare and understand the data</span></span>

> [!NOTE]
> <span data-ttu-id="91652-174">本教學課程的資料集來自 Maguire、Marc、Dorafshan, Sattar;和 Thomas，Robert J.，"SDNET2018：機器學習應用程式的具體破解影像資料集" （2018）。</span><span class="sxs-lookup"><span data-stu-id="91652-174">The datasets for this tutorial are from Maguire, Marc; Dorafshan, Sattar; and Thomas, Robert J., "SDNET2018: A concrete crack image dataset for machine learning applications" (2018).</span></span> <span data-ttu-id="91652-175">流覽所有資料集。</span><span class="sxs-lookup"><span data-stu-id="91652-175">Browse all Datasets.</span></span> <span data-ttu-id="91652-176">紙張48。</span><span class="sxs-lookup"><span data-stu-id="91652-176">Paper 48.</span></span> <span data-ttu-id="91652-177">https://digitalcommons.usu.edu/all_datasets/48</span><span class="sxs-lookup"><span data-stu-id="91652-177">https://digitalcommons.usu.edu/all_datasets/48</span></span>

<span data-ttu-id="91652-178">SDNET2018 是影像資料集，其中包含已破裂和未破裂之實體結構（bridge 圖、牆和 pavement）的注釋。</span><span class="sxs-lookup"><span data-stu-id="91652-178">SDNET2018 is an image dataset that contains annotations for cracked and non-cracked concrete structures (bridge decks, walls, and pavement).</span></span> 

![SDNET2018 資料集橋接器範例](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

<span data-ttu-id="91652-180">資料會組織成三個子目錄：</span><span class="sxs-lookup"><span data-stu-id="91652-180">The data is organized in three subdirectories:</span></span>

- <span data-ttu-id="91652-181">D 包含橋接器影像</span><span class="sxs-lookup"><span data-stu-id="91652-181">D contains bridge deck images</span></span>
- <span data-ttu-id="91652-182">P 包含 pavement 映射</span><span class="sxs-lookup"><span data-stu-id="91652-182">P contains pavement images</span></span>
- <span data-ttu-id="91652-183">W 包含牆影像</span><span class="sxs-lookup"><span data-stu-id="91652-183">W contains wall images</span></span>

<span data-ttu-id="91652-184">這些子目錄中的每一個都包含兩個額外的首碼子目錄：</span><span class="sxs-lookup"><span data-stu-id="91652-184">Each of these subdirectories contains two additional prefixed subdirectories:</span></span>

- <span data-ttu-id="91652-185">C 是用於破裂表面的前置詞</span><span class="sxs-lookup"><span data-stu-id="91652-185">C is the prefix used for cracked surfaces</span></span>
- <span data-ttu-id="91652-186">U 是用於 uncracked 表面的前置詞</span><span class="sxs-lookup"><span data-stu-id="91652-186">U is the prefix used for uncracked surfaces</span></span>

<span data-ttu-id="91652-187">在本教學課程中，只會使用橋接器的影像。</span><span class="sxs-lookup"><span data-stu-id="91652-187">In this tutorial, only bridge deck images are used.</span></span>

1. <span data-ttu-id="91652-188">下載[資料集](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip)並解壓縮。</span><span class="sxs-lookup"><span data-stu-id="91652-188">Download the [dataset](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) and unzip.</span></span>
1. <span data-ttu-id="91652-189">在您的專案中建立名為「資產」的目錄，以儲存您的資料集檔案。</span><span class="sxs-lookup"><span data-stu-id="91652-189">Create a directory named "assets" in your project to save your dataset files.</span></span>
1. <span data-ttu-id="91652-190">將*CD*和*UD*子目錄從最近解壓縮的目錄複寫到*資產*目錄。</span><span class="sxs-lookup"><span data-stu-id="91652-190">Copy the *CD* and *UD* subdirectories from the recently unzipped directory to the *assets* directory.</span></span>

### <a name="create-input-and-output-classes"></a><span data-ttu-id="91652-191">建立輸入和輸出類別</span><span class="sxs-lookup"><span data-stu-id="91652-191">Create input and output classes</span></span>

1. <span data-ttu-id="91652-192">開啟*Program.cs*檔案，並將檔案頂端的現有 `using` 語句取代為下列內容：</span><span class="sxs-lookup"><span data-stu-id="91652-192">Open the *Program.cs* file and replace the existing `using` statements at the top of the file with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L1-L7)]

1. <span data-ttu-id="91652-193">在*Program.cs*的 `Program` 類別底下，建立名為 `ImageData`的類別。</span><span class="sxs-lookup"><span data-stu-id="91652-193">Below the `Program` class in *Program.cs*, create a class called `ImageData`.</span></span> <span data-ttu-id="91652-194">這個類別是用來代表一開始載入的資料。</span><span class="sxs-lookup"><span data-stu-id="91652-194">This class is used to represent the initially loaded data.</span></span> 

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L135-L140)]

    <span data-ttu-id="91652-195">`ImageData` 包含下列屬性：</span><span class="sxs-lookup"><span data-stu-id="91652-195">`ImageData` contains the following properties:</span></span>

    - <span data-ttu-id="91652-196">`ImagePath` 是儲存映射的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="91652-196">`ImagePath` is the fully qualified path where the image is stored.</span></span>
    - <span data-ttu-id="91652-197">`Label` 是影像所屬的類別目錄。</span><span class="sxs-lookup"><span data-stu-id="91652-197">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="91652-198">這是要預測的值。</span><span class="sxs-lookup"><span data-stu-id="91652-198">This is the value to predict.</span></span>

1. <span data-ttu-id="91652-199">建立輸入和輸出資料的類別</span><span class="sxs-lookup"><span data-stu-id="91652-199">Create classes for your input and output data</span></span>

    1. <span data-ttu-id="91652-200">在 `ImageData` 類別底下，于名為 `ModelInput`的新類別中定義輸入資料的架構。</span><span class="sxs-lookup"><span data-stu-id="91652-200">Below the `ImageData` class, define the schema of your input data in a new class called `ModelInput`.</span></span>

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L142-L151)]

        <span data-ttu-id="91652-201">`ModelInput` 包含下列屬性：</span><span class="sxs-lookup"><span data-stu-id="91652-201">`ModelInput` contains the following properties:</span></span>

        - <span data-ttu-id="91652-202">`ImagePath` 是儲存映射的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="91652-202">`ImagePath` is the fully qualified path where the image is stored.</span></span> 
        - <span data-ttu-id="91652-203">`Label` 是影像所屬的類別目錄。</span><span class="sxs-lookup"><span data-stu-id="91652-203">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="91652-204">這是要預測的值。</span><span class="sxs-lookup"><span data-stu-id="91652-204">This is the value to predict.</span></span>
        - <span data-ttu-id="91652-205">`Image` 是影像的 `byte[]` 標記法。</span><span class="sxs-lookup"><span data-stu-id="91652-205">`Image` is the `byte[]` representation of the image.</span></span> <span data-ttu-id="91652-206">此模型預期影像資料屬於這種定型類型。</span><span class="sxs-lookup"><span data-stu-id="91652-206">The model expects image data to be of this type for training.</span></span>
        - <span data-ttu-id="91652-207">`LabelAsKey` 是 `Label`的數值標記法。</span><span class="sxs-lookup"><span data-stu-id="91652-207">`LabelAsKey` is the numerical representation of the `Label`.</span></span> 

        <span data-ttu-id="91652-208">只有 `Image` 和 `LabelAsKey` 會用來定型模型並進行預測。</span><span class="sxs-lookup"><span data-stu-id="91652-208">Only `Image` and `LabelAsKey` are used to train the model and make predictions.</span></span> <span data-ttu-id="91652-209">為了方便存取原始的影像檔案名稱和類別，會保留 [`ImagePath`] 和 [`Label`] 屬性。</span><span class="sxs-lookup"><span data-stu-id="91652-209">The `ImagePath` and `Label` properties are kept for convenience to access the original image file name and category.</span></span>

    1. <span data-ttu-id="91652-210">然後，在 `ModelInput` 類別底下，在名為 `ModelOutput`的新類別中定義輸出資料的架構。</span><span class="sxs-lookup"><span data-stu-id="91652-210">Then, below the `ModelInput` class, define the schema of your output data in a new class called `ModelOutput`.</span></span> 

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L153-L160)]

        <span data-ttu-id="91652-211">`ModelOutput` 包含下列屬性：</span><span class="sxs-lookup"><span data-stu-id="91652-211">`ModelOutput` contains the following properties:</span></span>

        - <span data-ttu-id="91652-212">`ImagePath` 是儲存映射的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="91652-212">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="91652-213">`Label` 是影像所屬的原始類別目錄。</span><span class="sxs-lookup"><span data-stu-id="91652-213">`Label` is the original category the image belongs to.</span></span> <span data-ttu-id="91652-214">這是要預測的值。</span><span class="sxs-lookup"><span data-stu-id="91652-214">This is the value to predict.</span></span> 
        - <span data-ttu-id="91652-215">`PredictedLabel` 是模型所預測的值。</span><span class="sxs-lookup"><span data-stu-id="91652-215">`PredictedLabel` is the value predicted by the model.</span></span>

        <span data-ttu-id="91652-216">類似于 `ModelInput`，只有 `PredictedLabel` 才需要進行預測，因為它包含模型所做的預測。</span><span class="sxs-lookup"><span data-stu-id="91652-216">Similar to `ModelInput`, only the `PredictedLabel` is required to make predictions since it contains the prediction made by the model.</span></span> <span data-ttu-id="91652-217">為了方便存取原始的影像檔案名稱和類別，會保留 [`ImagePath`] 和 [`Label`] 屬性。</span><span class="sxs-lookup"><span data-stu-id="91652-217">The `ImagePath` and `Label` properties are retained for convenience to access the original image file name and category.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="91652-218">定義路徑和初始化變數</span><span class="sxs-lookup"><span data-stu-id="91652-218">Define paths and initialize variables</span></span>

1. <span data-ttu-id="91652-219">在 `Main` 方法中，定義資產的位置。</span><span class="sxs-lookup"><span data-stu-id="91652-219">Inside the `Main` method, define the location of your assets.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L15-L16)]

1. <span data-ttu-id="91652-220">然後，使用[MLCoNtext](xref:Microsoft.ML.MLContext)的新實例來初始化 `mlContext` 變數。</span><span class="sxs-lookup"><span data-stu-id="91652-220">Then, initialize the `mlContext` variable with a new instance of [MLContext](xref:Microsoft.ML.MLContext).</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L18)]

<span data-ttu-id="91652-221">[MLCoNtext](xref:Microsoft.ML.MLContext)類別是所有 ML.NET 作業的起點，而初始化 MLCoNtext 會建立可在模型建立工作流程物件之間共用的新 ML.NET 環境。</span><span class="sxs-lookup"><span data-stu-id="91652-221">The [MLContext](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="91652-222">就概念而言，類似於 Entity Framework 中的 `DBContext`。</span><span class="sxs-lookup"><span data-stu-id="91652-222">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="91652-223">載入資料</span><span class="sxs-lookup"><span data-stu-id="91652-223">Load the data</span></span>

### <a name="create-data-loading-utility-method"></a><span data-ttu-id="91652-224">建立資料載入公用程式方法</span><span class="sxs-lookup"><span data-stu-id="91652-224">Create data loading utility method</span></span>

<span data-ttu-id="91652-225">映射會儲存在兩個子目錄中。</span><span class="sxs-lookup"><span data-stu-id="91652-225">The images are stored in two subdirectories.</span></span> <span data-ttu-id="91652-226">載入資料之前，必須先將它格式化為 `ImageData` 物件的清單。</span><span class="sxs-lookup"><span data-stu-id="91652-226">Before loading the data, it needs to be formatted into a list of `ImageData` objects.</span></span> <span data-ttu-id="91652-227">若要這麼做，請在 `Main` 方法底下建立 `LoadImagesFromDirectory` 方法。</span><span class="sxs-lookup"><span data-stu-id="91652-227">To do so, create the `LoadImagesFromDirectory` method below the `Main` method.</span></span>

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. <span data-ttu-id="91652-228">在 `LoadImagesDirectory` 內新增下列程式碼，以從子目錄取得所有檔案路徑：</span><span class="sxs-lookup"><span data-stu-id="91652-228">Inside the `LoadImagesDirectory` add the following code to get all of the file paths from the subdirectories:</span></span>

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L102-L103)]

1. <span data-ttu-id="91652-229">然後，使用 `foreach` 語句逐一查看每個檔案。</span><span class="sxs-lookup"><span data-stu-id="91652-229">Then, iterate through each of the files using a `foreach` statement.</span></span>

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. <span data-ttu-id="91652-230">在 `foreach` 語句中，檢查是否支援副檔名。</span><span class="sxs-lookup"><span data-stu-id="91652-230">Inside the `foreach` statement, check that the file extensions are supported.</span></span> <span data-ttu-id="91652-231">影像分類 API 支援 JPEG 和 PNG 格式。</span><span class="sxs-lookup"><span data-stu-id="91652-231">The Image Classification API supports JPEG and PNG formats.</span></span>

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L107-L108)]

1. <span data-ttu-id="91652-232">然後，取得檔案的標籤。</span><span class="sxs-lookup"><span data-stu-id="91652-232">Then, get the label for the file.</span></span> <span data-ttu-id="91652-233">如果 `useFolderNameAsLabel` 參數設定為 `true`，則會使用儲存檔案的上層目錄做為標籤。</span><span class="sxs-lookup"><span data-stu-id="91652-233">If the `useFolderNameAsLabel` parameter is set to `true`, then the parent directory where the file is saved is used as the label.</span></span> <span data-ttu-id="91652-234">否則，它會預期標籤必須是檔案名或檔案名本身的前置詞。</span><span class="sxs-lookup"><span data-stu-id="91652-234">Otherwise, it expects the label to be a prefix of the file name or the file name itself.</span></span>

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L110-L124)]

1. <span data-ttu-id="91652-235">最後，建立 `ModelInput`的新實例。</span><span class="sxs-lookup"><span data-stu-id="91652-235">Finally, create a new instance of `ModelInput`.</span></span>

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L126-L130)]

### <a name="prepare-the-data"></a><span data-ttu-id="91652-236">準備資料</span><span class="sxs-lookup"><span data-stu-id="91652-236">Prepare the data</span></span>

1. <span data-ttu-id="91652-237">回到 `Main` 方法中，使用 `LoadFromDirectory` 公用程式方法來取得用於定型的影像清單。</span><span class="sxs-lookup"><span data-stu-id="91652-237">Back in the `Main` method, use the `LoadFromDirectory` utility method to get the list of images used for training.</span></span>

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L20)]

1. <span data-ttu-id="91652-238">然後，使用[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*)方法，將影像載入[`IDataView`](xref:Microsoft.ML.IDataView) 。</span><span class="sxs-lookup"><span data-stu-id="91652-238">Then, load the images into an [`IDataView`](xref:Microsoft.ML.IDataView) using the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method.</span></span>

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L22)]    

1. <span data-ttu-id="91652-239">資料會以從目錄中讀取的順序載入。</span><span class="sxs-lookup"><span data-stu-id="91652-239">The data is loaded in the order it was read from the directories.</span></span> <span data-ttu-id="91652-240">若要平衡資料，請使用[`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*)方法將其隨機播放。</span><span class="sxs-lookup"><span data-stu-id="91652-240">To balance the data, shuffle it using the [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) method.</span></span>

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L24)]

1. <span data-ttu-id="91652-241">機器學習模型預期輸入為數值格式。</span><span class="sxs-lookup"><span data-stu-id="91652-241">Machine learning models expect input to be in numerical format.</span></span> <span data-ttu-id="91652-242">因此，必須在定型之前對資料進行一些前置處理。</span><span class="sxs-lookup"><span data-stu-id="91652-242">Therefore, some preprocessing needs to be done on the data prior to training.</span></span> <span data-ttu-id="91652-243">建立由[`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*)和[`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*)轉換所組成的[`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) 。</span><span class="sxs-lookup"><span data-stu-id="91652-243">Create an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) made up of the [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) and [`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*) transforms.</span></span> <span data-ttu-id="91652-244">`MapValueToKey` 轉換會採用 `Label` 資料行中的類別值，將它轉換成數值 `KeyType` 值，並將它儲存在名為 `LabelAsKey`的新資料行中。</span><span class="sxs-lookup"><span data-stu-id="91652-244">The `MapValueToKey` transform takes the categorical value in the `Label` column, converts it to a numerical `KeyType` value and stores it in a new column called `LabelAsKey`.</span></span> <span data-ttu-id="91652-245">`LoadImages` 會從 `ImagePath` 資料行中取得值，並使用 `imageFolder` 參數來載入要定型的影像。</span><span class="sxs-lookup"><span data-stu-id="91652-245">The `LoadImages` takes the values from the `ImagePath` column along with the `imageFolder` parameter to load images for training.</span></span> <span data-ttu-id="91652-246">將 `useImageType` 設定為 `false` 會將影像轉換成 `byte[]`。</span><span class="sxs-lookup"><span data-stu-id="91652-246">Setting the `useImageType` to `false` converts the images into a `byte[]`.</span></span> 

    [!code-csharp [DefinePreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L26-L33)]

1. <span data-ttu-id="91652-247">使用[`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*)方法，將資料套用至 `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601)後面接著[`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*)方法，這會傳回包含預先處理資料的[`IDataView`](xref:Microsoft.ML.IDataView) 。</span><span class="sxs-lookup"><span data-stu-id="91652-247">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to apply the data to the `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) followed by the [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) method, which returns an [`IDataView`](xref:Microsoft.ML.IDataView) containing the pre-processed data.</span></span>

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L35-L37)]

1. <span data-ttu-id="91652-248">若要定型模型，請務必具有訓練資料集和驗證資料集。</span><span class="sxs-lookup"><span data-stu-id="91652-248">To train a model, it's important to have a training dataset as well as a validation dataset.</span></span> <span data-ttu-id="91652-249">此模型會在定型集上定型。</span><span class="sxs-lookup"><span data-stu-id="91652-249">The model is trained on the training set.</span></span> <span data-ttu-id="91652-250">其對未看到資料進行預測的程度，是根據驗證集的效能來測量。</span><span class="sxs-lookup"><span data-stu-id="91652-250">How well it makes predictions on unseen data is measured by the performance against the validation set.</span></span> <span data-ttu-id="91652-251">根據該效能的結果，此模型會調整其所學習到的成果以改善。</span><span class="sxs-lookup"><span data-stu-id="91652-251">Based on the results of that performance, the model makes adjustments to what it has learned in an effort to improve.</span></span> <span data-ttu-id="91652-252">驗證集可能來自于分割您的原始資料集，或來自已針對此用途設定的另一個來源。</span><span class="sxs-lookup"><span data-stu-id="91652-252">The validation set can come from either splitting your original dataset or from another source that has already been set aside for this purpose.</span></span> <span data-ttu-id="91652-253">在此情況下，預先處理的資料集會分割成定型、驗證和測試集。</span><span class="sxs-lookup"><span data-stu-id="91652-253">In this case, the pre-processed dataset is split into training, validation and test sets.</span></span>

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L39-L40)]

    <span data-ttu-id="91652-254">上述程式碼範例會執行兩個分割。</span><span class="sxs-lookup"><span data-stu-id="91652-254">The code sample above performs two splits.</span></span> <span data-ttu-id="91652-255">首先，預先處理的資料會被分割，而70% 用於定型，而剩餘的30% 則用於驗證。</span><span class="sxs-lookup"><span data-stu-id="91652-255">First, the pre-processed data is split and 70% is used for training while the remaining 30% is used for validation.</span></span> <span data-ttu-id="91652-256">然後，30% 的驗證集會進一步分割成驗證和測試集，其中90% 用於驗證，而10% 用於測試。</span><span class="sxs-lookup"><span data-stu-id="91652-256">Then, the 30% validation set is further split into validation and test sets where 90% is used for validation and 10% is used for testing.</span></span> 

    <span data-ttu-id="91652-257">有一種方法可以思考這些資料分割的用途，這是一項測驗。</span><span class="sxs-lookup"><span data-stu-id="91652-257">A way to think about the purpose of these data partitions is taking an exam.</span></span> <span data-ttu-id="91652-258">在研究測驗時，您會複習您的記事、書籍或其他資源，以瞭解測驗上的概念。</span><span class="sxs-lookup"><span data-stu-id="91652-258">When studying for an exam, you review your notes, books, or other resources to get a grasp on the concepts that are on the exam.</span></span> <span data-ttu-id="91652-259">這就是定型集的用途。</span><span class="sxs-lookup"><span data-stu-id="91652-259">This is what the train set is for.</span></span> <span data-ttu-id="91652-260">然後，您可能會進行模擬測驗來驗證您的知識。</span><span class="sxs-lookup"><span data-stu-id="91652-260">Then, you might take a mock exam to validate your knowledge.</span></span> <span data-ttu-id="91652-261">這就是驗證集派上用場的地方。</span><span class="sxs-lookup"><span data-stu-id="91652-261">This is where the validation set comes in handy.</span></span> <span data-ttu-id="91652-262">在進行實際測驗之前，您想要先檢查是否有良好的概念。</span><span class="sxs-lookup"><span data-stu-id="91652-262">You want to check whether you have a good grasp of the concepts before taking the actual exam.</span></span> <span data-ttu-id="91652-263">根據這些結果，您可以記下錯誤或不了解的內容，並在您查看實際測驗時納入變更。</span><span class="sxs-lookup"><span data-stu-id="91652-263">Based on those results, you take note of what you got wrong or didn't understand well and incorporate your changes as you review for the real exam.</span></span> <span data-ttu-id="91652-264">最後，您要進行測驗。</span><span class="sxs-lookup"><span data-stu-id="91652-264">Finally, you take the exam.</span></span> <span data-ttu-id="91652-265">這就是測試集的用途。</span><span class="sxs-lookup"><span data-stu-id="91652-265">This is what the test set is used for.</span></span> <span data-ttu-id="91652-266">您從未見過測驗中的問題，現在使用您從訓練和驗證中學到的內容，將您的知識套用至手邊的工作。</span><span class="sxs-lookup"><span data-stu-id="91652-266">You've never seen the questions that are on the exam and now use what you learned from training and validation to apply your knowledge to the task at hand.</span></span> 

1. <span data-ttu-id="91652-267">針對定型、驗證和測試資料，將分割區的個別值指派給分割區。</span><span class="sxs-lookup"><span data-stu-id="91652-267">Assign the partitions their respective values for the train, validation and test data.</span></span>

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L42-L44)]

## <a name="define-the-training-pipeline"></a><span data-ttu-id="91652-268">定義定型管線</span><span class="sxs-lookup"><span data-stu-id="91652-268">Define the training pipeline</span></span>

<span data-ttu-id="91652-269">模型訓練包含幾個步驟。</span><span class="sxs-lookup"><span data-stu-id="91652-269">Model training consists of a couple of steps.</span></span> <span data-ttu-id="91652-270">首先，使用影像分類 API 來定型模型。</span><span class="sxs-lookup"><span data-stu-id="91652-270">First, Image Classification API is used to train the model.</span></span> <span data-ttu-id="91652-271">然後，`PredictedLabel` 資料行中的編碼標籤會使用 `MapKeyToValue` 轉換，轉換回其原始類別值。</span><span class="sxs-lookup"><span data-stu-id="91652-271">Then, the encoded labels in the `PredictedLabel` column are converted back to their original categorical value using the `MapKeyToValue` transform.</span></span> 

1. <span data-ttu-id="91652-272">定義包含 `mapLabelEstimator` 和 `ImageClassification` 轉換的定型[`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601)管線。</span><span class="sxs-lookup"><span data-stu-id="91652-272">Define the training [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) pipeline that consists of both the `mapLabelEstimator` and the `ImageClassification` transforms.</span></span>

    [!code-csharp [DefineTrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L46-L58)]    

    <span data-ttu-id="91652-273">`ImageClassification` 估計工具接受數個參數：</span><span class="sxs-lookup"><span data-stu-id="91652-273">The `ImageClassification` estimator takes in several parameters:</span></span>

    - <span data-ttu-id="91652-274">`featuresColumnName` 是用來做為模型輸入的資料行。</span><span class="sxs-lookup"><span data-stu-id="91652-274">`featuresColumnName` is the column that is used as input for the model.</span></span>
    - <span data-ttu-id="91652-275">`labelColumnName` 是要預測之值的資料行。</span><span class="sxs-lookup"><span data-stu-id="91652-275">`labelColumnName` is the column for the value to predict.</span></span>
    - <span data-ttu-id="91652-276">`arch` 定義要使用的預先定型模型架構。</span><span class="sxs-lookup"><span data-stu-id="91652-276">`arch` defines which of the pretrained model architectures to use.</span></span> <span data-ttu-id="91652-277">本教學課程使用 ResNetv2 模型的101層變體。</span><span class="sxs-lookup"><span data-stu-id="91652-277">This tutorial uses the 101-layer variant of the ResNetv2 model.</span></span>
    - <span data-ttu-id="91652-278">`epoch` 在整個定型程式中，指定整個資料集的反覆運算次數上限。</span><span class="sxs-lookup"><span data-stu-id="91652-278">`epoch` specifies the maximum number of iterations over the entire dataset throughout the training process.</span></span> <span data-ttu-id="91652-279">數位愈大，模型所定型的時間愈長，而且可能會產生較佳的模型。</span><span class="sxs-lookup"><span data-stu-id="91652-279">The higher the number, the longer the model trains for and potentially the better model that is produced.</span></span>
    - <span data-ttu-id="91652-280">`batchSize` 是一次用於定型的樣本數。</span><span class="sxs-lookup"><span data-stu-id="91652-280">`batchSize` is the number of samples to use at a time for training.</span></span> <span data-ttu-id="91652-281">在一個 epoch 期間，會使用多個與 batchSize 相等的批次來定型及更新模型。</span><span class="sxs-lookup"><span data-stu-id="91652-281">During one epoch, multiple batches equal to the batchSize are used to train and update the model.</span></span> <span data-ttu-id="91652-282">數位越低，處理每個批次時所需的記憶體就越少。</span><span class="sxs-lookup"><span data-stu-id="91652-282">The lower the number, the less memory required when each batch is processed.</span></span>
    - <span data-ttu-id="91652-283">`testOnTrainSet` 會告知模型在沒有驗證集時，測量定型集的效能。</span><span class="sxs-lookup"><span data-stu-id="91652-283">`testOnTrainSet` tells the model to measure performance against the training set when no validation set is present.</span></span>
    - <span data-ttu-id="91652-284">`metricsCallback` 系結函式來追蹤定型期間的進度。</span><span class="sxs-lookup"><span data-stu-id="91652-284">`metricsCallback` binds a function to track the progress during training.</span></span>
    - <span data-ttu-id="91652-285">`validationSet` 是包含驗證資料的[`IDataView`](xref:Microsoft.ML.IDataView) 。</span><span class="sxs-lookup"><span data-stu-id="91652-285">`validationSet` is the [`IDataView`](xref:Microsoft.ML.IDataView) containing the validation data.</span></span>
    - <span data-ttu-id="91652-286">`reuseTrainSetBottleneckCachedValues` 會告訴模型，是否要在後續執行的瓶頸階段中使用快取的值。</span><span class="sxs-lookup"><span data-stu-id="91652-286">`reuseTrainSetBottleneckCachedValues` tells the model whether to use the cached values from the bottleneck phase in subsequent runs.</span></span> <span data-ttu-id="91652-287">瓶頸階段是單次傳遞計算，在第一次執行時需要大量計算。</span><span class="sxs-lookup"><span data-stu-id="91652-287">The bottleneck phase is a one-time pass-through computation that is computationally intensive the first time it is performed.</span></span> <span data-ttu-id="91652-288">如果定型資料不會變更，而您想要使用不同數目的 epoch 或批次大小進行實驗，則使用快取的值會大幅減少定型模型所需的時間量。</span><span class="sxs-lookup"><span data-stu-id="91652-288">If the training data does not change and you want to experiment using a different number of epochs or batch size, using the cached values significantly reduces the amount of time required to train a model.</span></span>
    - <span data-ttu-id="91652-289">`reuseValidationSetBottleneckCachedValues` 類似 `reuseTrainSetBottleneckCachedValues` 只有在此情況下，它是用於驗證資料集。</span><span class="sxs-lookup"><span data-stu-id="91652-289">`reuseValidationSetBottleneckCachedValues` is similar to `reuseTrainSetBottleneckCachedValues` only that in this case it's for the validation dataset.</span></span>
    - <span data-ttu-id="91652-290">`disableEarlyStopping` 會告訴 ImageClassification 估計工具是否要採用早期停止策略。</span><span class="sxs-lookup"><span data-stu-id="91652-290">`disableEarlyStopping` tells the ImageClassification estimator whether to employ an early stopping strategy.</span></span> <span data-ttu-id="91652-291">當此模型搜尋可協助它在定型期間做出精確預測的最佳值時，效能可能會增加或減少。</span><span class="sxs-lookup"><span data-stu-id="91652-291">As the model searches for the optimal values that will help it make accurate predictions during training, performance may increase or decrease.</span></span> <span data-ttu-id="91652-292">最後，如果模型達到上一個 epoch，則從定型學習到的模式可能會是不佳的情況。</span><span class="sxs-lookup"><span data-stu-id="91652-292">Ultimately, if the model reaches the last epoch, it may be the case that the patterns it learned from training are suboptimal.</span></span> <span data-ttu-id="91652-293">及早停止監視這些效能下降的訓練，並停止定型程式以保留模型的最佳版本。</span><span class="sxs-lookup"><span data-stu-id="91652-293">Early stopping monitors training for these drops in performance and stops the training process in an effort to preserve an optimal version of the model.</span></span>

1. <span data-ttu-id="91652-294">使用[`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*)方法來定型您的模型。</span><span class="sxs-lookup"><span data-stu-id="91652-294">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to train your model.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L60)]

## <a name="use-the-model"></a><span data-ttu-id="91652-295">使用模型</span><span class="sxs-lookup"><span data-stu-id="91652-295">Use the model</span></span>

<span data-ttu-id="91652-296">既然您已定型模型，現在可以用它來分類影像。</span><span class="sxs-lookup"><span data-stu-id="91652-296">Now that you have trained your model, it's time to use it to classify images.</span></span>

<span data-ttu-id="91652-297">在 `Main` 方法底下，建立稱為 `OutputPrediction` 的新公用程式方法，以在主控台中顯示預測資訊。</span><span class="sxs-lookup"><span data-stu-id="91652-297">Below the `Main` method, create a new utility method called `OutputPrediction` to display prediction information in the console.</span></span>

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L94-L98)]

### <a name="classify-a-single-image"></a><span data-ttu-id="91652-298">分類單一影像</span><span class="sxs-lookup"><span data-stu-id="91652-298">Classify a single image</span></span>

1. <span data-ttu-id="91652-299">將名為 `ClassifySingleImage` 的新方法新增至 `Main` 方法下方，以讓和輸出單一影像預測。</span><span class="sxs-lookup"><span data-stu-id="91652-299">Add a new method called `ClassifySingleImage` below the `Main` method to make and output a single image prediction.</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="91652-300">在 `ClassifySingleImage` 方法中建立[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) 。</span><span class="sxs-lookup"><span data-stu-id="91652-300">Create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) inside the `ClassifySingleImage` method.</span></span> <span data-ttu-id="91652-301">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)是一個方便的 API，可讓您傳入，然後在單一資料實例上執行預測。</span><span class="sxs-lookup"><span data-stu-id="91652-301">The [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span>

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L71)]    

1. <span data-ttu-id="91652-302">若要存取單一 `ModelInput` 實例，請使用[`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*)方法將 `data` [`IDataView`](xref:Microsoft.ML.IDataView)轉換成[`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) ，然後取得第一個觀察。</span><span class="sxs-lookup"><span data-stu-id="91652-302">To access a single `ModelInput` instance, convert the `data` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first observation.</span></span> 

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L73)]

1. <span data-ttu-id="91652-303">使用[`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*)方法來分類映射。</span><span class="sxs-lookup"><span data-stu-id="91652-303">Use the [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) method to classify the image.</span></span>

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L75)]

1. <span data-ttu-id="91652-304">使用 `OutputPrediction` 方法，將預測輸出至主控台。</span><span class="sxs-lookup"><span data-stu-id="91652-304">Output the prediction to the console with the `OutputPrediction` method.</span></span>

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L77-L78)]

1. <span data-ttu-id="91652-305">在 `Main` 方法中，使用影像的測試集來呼叫 `ClassifySingleImage`。</span><span class="sxs-lookup"><span data-stu-id="91652-305">Inside the `Main` method, call `ClassifySingleImage` using the test set of images.</span></span>

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L62)]

### <a name="classify-multiple-images"></a><span data-ttu-id="91652-306">分類多個映射</span><span class="sxs-lookup"><span data-stu-id="91652-306">Classify multiple images</span></span>

1. <span data-ttu-id="91652-307">將名為 `ClassifyImages` 的新方法新增至 `ClassifySingleImage` 方法下方，以進行和輸出多個影像預測。</span><span class="sxs-lookup"><span data-stu-id="91652-307">Add a new method called `ClassifyImages` below the `ClassifySingleImage` method to make and output multiple image predictions.</span></span>

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="91652-308">使用[`Transform`](xref:Microsoft.ML.ITransformer.Transform*)方法，建立包含預測的[`IDataView`](xref:Microsoft.ML.IDataView) 。</span><span class="sxs-lookup"><span data-stu-id="91652-308">Create an [`IDataView`](xref:Microsoft.ML.IDataView) containing the predictions by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method.</span></span> <span data-ttu-id="91652-309">將下列程式碼新增至 `ClassifyImages` 方法內。</span><span class="sxs-lookup"><span data-stu-id="91652-309">Add the following code inside the `ClassifyImages` method.</span></span>

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L83)]

1. <span data-ttu-id="91652-310">若要反復執行預測，請使用[`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*)方法，將 `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView)轉換成[`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) ，然後取得前10個觀察。</span><span class="sxs-lookup"><span data-stu-id="91652-310">In order to iterate over the predictions, convert the `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first 10 observations.</span></span>

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L85)]

1. <span data-ttu-id="91652-311">反覆運算和輸出預測的原始和預測標籤。</span><span class="sxs-lookup"><span data-stu-id="91652-311">Iterate and output the original and predicted labels for the predictions.</span></span>

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L87-L91)]

1. <span data-ttu-id="91652-312">最後，在 `Main` 方法中，使用影像的測試集呼叫 `ClassifyImages`。</span><span class="sxs-lookup"><span data-stu-id="91652-312">Finally, inside the `Main` method, call `ClassifyImages` using the test set of images.</span></span>

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L64)]

## <a name="run-the-application"></a><span data-ttu-id="91652-313">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="91652-313">Run the application</span></span>

<span data-ttu-id="91652-314">執行您的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="91652-314">Run your console app.</span></span> <span data-ttu-id="91652-315">輸出應該如下所示。</span><span class="sxs-lookup"><span data-stu-id="91652-315">The output should be similar to that below.</span></span> <span data-ttu-id="91652-316">您可能會看到警告或處理中訊息，但為了讓結果變得清楚，這些訊息已從下列結果中移除。</span><span class="sxs-lookup"><span data-stu-id="91652-316">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span> <span data-ttu-id="91652-317">為求簡潔，輸出已壓縮。</span><span class="sxs-lookup"><span data-stu-id="91652-317">For brevity, the output has been condensed.</span></span>

<span data-ttu-id="91652-318">**瓶頸階段**</span><span class="sxs-lookup"><span data-stu-id="91652-318">**Bottleneck phase**</span></span>

<span data-ttu-id="91652-319">影像名稱不會列印任何值，因為影像會載入為 `byte[]` 因此沒有可顯示的影像名稱。</span><span class="sxs-lookup"><span data-stu-id="91652-319">No value is printed for the image name because the images are loaded as a `byte[]` therefore there is no image name to display.</span></span>

```test
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 279, Image Name:
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 280, Image Name:
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   1, Image Name:
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   2, Image Name:
```

<span data-ttu-id="91652-320">**訓練階段**</span><span class="sxs-lookup"><span data-stu-id="91652-320">**Training phase**</span></span>

```text
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  21, Accuracy:  0.6797619
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  22, Accuracy:  0.7642857
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  23, Accuracy:  0.7916667
```

<span data-ttu-id="91652-321">**分類影像輸出**</span><span class="sxs-lookup"><span data-stu-id="91652-321">**Classify images output**</span></span>

```text
Classifying single image
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD

Classifying multiple images
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-163.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-210.jpg | Actual Value: UD | Predicted Value: UD
```

<span data-ttu-id="91652-322">在檢查*7001-220 .jpg*影像之後，您可以看到它實際上不會被破解。</span><span class="sxs-lookup"><span data-stu-id="91652-322">Upon inspection of the *7001-220.jpg* image, you can see that it in fact is not cracked.</span></span> 

![用於預測的 SDNET2018 資料集影像](./media/image-classification-api-transfer-learning/predictedimage.jpg)

<span data-ttu-id="91652-324">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="91652-324">Congratulations!</span></span> <span data-ttu-id="91652-325">您現在已成功建立用於分類影像的深度學習模型。</span><span class="sxs-lookup"><span data-stu-id="91652-325">You've now successfully built a deep learning model for classifying images.</span></span>

### <a name="improve-the-model"></a><span data-ttu-id="91652-326">改善模型</span><span class="sxs-lookup"><span data-stu-id="91652-326">Improve the model</span></span>

<span data-ttu-id="91652-327">如果您不滿意模型的結果，您可以嘗試下列一些方法來提升其效能：</span><span class="sxs-lookup"><span data-stu-id="91652-327">If you're not satisfied with the results of your model, you can try to improve its performance by trying some of the following approaches:</span></span>

- <span data-ttu-id="91652-328">**更多資料**：模型從中學習的範例越多，執行的效能就愈好。</span><span class="sxs-lookup"><span data-stu-id="91652-328">**More Data**: The more examples a model learns from, the better it performs.</span></span> <span data-ttu-id="91652-329">下載完整的[SDNET2018 資料集](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional)，並使用它來進行定型。</span><span class="sxs-lookup"><span data-stu-id="91652-329">Download the full [SDNET2018 dataset](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) and use it to train.</span></span> 
- <span data-ttu-id="91652-330">**增強資料**：將各種資料新增至資料的常見技術是藉由取得影像並套用不同的轉換（旋轉、翻轉、shift、裁剪）來擴大資料。</span><span class="sxs-lookup"><span data-stu-id="91652-330">**Augment the data**: A common technique to add variety to the data is to augment the data by taking an image and applying different transforms (rotate, flip, shift, crop).</span></span> <span data-ttu-id="91652-331">這會為要從中學習的模型加入更多不同的範例。</span><span class="sxs-lookup"><span data-stu-id="91652-331">This adds more varied examples for the model to learn from.</span></span> 
- <span data-ttu-id="91652-332">**訓練較長的時間**：您所定型的時間愈久，模型的微調就愈多。</span><span class="sxs-lookup"><span data-stu-id="91652-332">**Train for a longer time**: The longer you train, the more tuned the model will be.</span></span> <span data-ttu-id="91652-333">增加 epoch 數目可能會改善模型的效能。</span><span class="sxs-lookup"><span data-stu-id="91652-333">Increasing the number of epochs may improve the performance of your model.</span></span>
- <span data-ttu-id="91652-334">**使用超參數進行實驗**：除了本教學課程中使用的參數之外，其他參數也可以調整，以改善效能。</span><span class="sxs-lookup"><span data-stu-id="91652-334">**Experiment with the hyper-parameters**: In addition to the parameters used in this tutorial, other parameters can be tuned to potentially improve performance.</span></span> <span data-ttu-id="91652-335">變更學習速率，以決定在每個 epoch 之後對模型所做的更新大小，可能會改善效能。</span><span class="sxs-lookup"><span data-stu-id="91652-335">Changing the learning rate, which determines the magnitude of updates made to the model after each epoch may improve performance.</span></span>
- <span data-ttu-id="91652-336">**使用不同的模型架構**：根據您的資料看起來的樣子，可以充分瞭解其功能的模型可能會有所不同。</span><span class="sxs-lookup"><span data-stu-id="91652-336">**Use a different model architecture**: Depending on what your data looks like, the model that can best learn its features may differ.</span></span> <span data-ttu-id="91652-337">如果您不滿意模型的效能，請嘗試變更架構。</span><span class="sxs-lookup"><span data-stu-id="91652-337">If you're not satisfied with the performance of your model, try changing the architecture.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="91652-338">其他資源</span><span class="sxs-lookup"><span data-stu-id="91652-338">Additional Resources</span></span>

- <span data-ttu-id="91652-339">[深度學習與 Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning)。</span><span class="sxs-lookup"><span data-stu-id="91652-339">[Deep Learning vs Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span></span>

## <a name="next-steps"></a><span data-ttu-id="91652-340">後續步驟</span><span class="sxs-lookup"><span data-stu-id="91652-340">Next steps</span></span>

<span data-ttu-id="91652-341">在本教學課程中，您已瞭解如何使用「傳輸學習」（預先定型影像分類 TensorFlow 模型和 ML.NET 影像分類 API）來建立自訂深度學習模型，以將具體表面的影像分類為破裂或 uncracked。</span><span class="sxs-lookup"><span data-stu-id="91652-341">In this tutorial, you learned how to build a custom deep learning model using transfer learning, a pretrained image classification TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="91652-342">前進到下一個教學課程來深入了解。</span><span class="sxs-lookup"><span data-stu-id="91652-342">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="91652-343">物件偵測</span><span class="sxs-lookup"><span data-stu-id="91652-343">Object Detection</span></span>](object-detection-onnx.md)
