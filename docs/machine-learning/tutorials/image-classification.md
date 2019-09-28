---
title: 教學課程：從預先定型的 TensorFlow 模型產生 ML.NET 影像分類模型
description: 瞭解如何將現有 TensorFlow 模型的知識，轉移到新的 ML.NET 影像分類模型。 TensorFlow 模型已定型，可將影像分類為一千個類別。 ML.NET 模型利用轉移學習，將影像分類成較少的類別。
ms.date: 09/26/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
author: natke
ms.author: nakersha
ms.openlocfilehash: 28d8c18721bd353e961284935758a87679c8c8e0
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353691"
---
# <a name="tutorial-generate-an-mlnet-image-classification-model-from-a-pre-trained-tensorflow-model"></a><span data-ttu-id="5d8a9-105">教學課程：從預先定型的 TensorFlow 模型產生 ML.NET 影像分類模型</span><span class="sxs-lookup"><span data-stu-id="5d8a9-105">Tutorial: Generate an ML.NET image classification model from a pre-trained TensorFlow model</span></span>

<span data-ttu-id="5d8a9-106">瞭解如何將現有 TensorFlow 模型的知識，轉移到新的 ML.NET 影像分類模型。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-106">Learn how to transfer the knowledge from an existing TensorFlow model into a new ML.NET image classification model.</span></span>

<span data-ttu-id="5d8a9-107">TensorFlow 模型已定型，可將影像分類為一千個類別。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-107">The TensorFlow model was trained to classify images into a thousand categories.</span></span> <span data-ttu-id="5d8a9-108">ML.NET 模型會在其管線中使用部分的 TensorFlow 模型來定型模型，以將影像分類成3個類別。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-108">The ML.NET model makes use of part of the TensorFlow model in its pipeline to train a model to classify images into 3 categories.</span></span>

<span data-ttu-id="5d8a9-109">若要從頭對[影像分類](https://en.wikipedia.org/wiki/Outline_of_object_recognition) \(英文\) 模型進行定型，將會需要設定數以百萬計的參數、眾多已標籤的定型資料，以及大量的計算資源 (數以百計的 GPU 小時)。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-109">Training an [Image Classification](https://en.wikipedia.org/wiki/Outline_of_object_recognition) model from scratch requires setting millions of parameters, a ton of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="5d8a9-110">遷移學習的效能雖然不如從頭對自訂模型進行定型來得有效，但它能讓您透過僅需處理數以千計的影像 (而非數以百萬計的已標籤影像) 來縮短此程序，並以較為快速的方式建置自訂模型 (在不具備 GPU 的電腦上於一小時內便能完成)。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-110">While not as effective as training a custom model from scratch, transfer learning allows you to shortcut this process by working with thousands of images vs. millions of labeled images and build a customized model fairly quickly (within an hour on a machine without a GPU).</span></span> <span data-ttu-id="5d8a9-111">本教學課程會更進一步調整該程式，只使用數十個訓練影像。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-111">This tutorial scales that process down even further, using only a dozen training images.</span></span>

<span data-ttu-id="5d8a9-112">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-112">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="5d8a9-113">了解問題</span><span class="sxs-lookup"><span data-stu-id="5d8a9-113">Understand the problem</span></span>
> * <span data-ttu-id="5d8a9-114">將預先定型的 TensorFlow 模型納入 ML.NET 管線中</span><span class="sxs-lookup"><span data-stu-id="5d8a9-114">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span></span>
> * <span data-ttu-id="5d8a9-115">定型和評估 ML.NET 模型</span><span class="sxs-lookup"><span data-stu-id="5d8a9-115">Train and evaluate the ML.NET model</span></span>
> * <span data-ttu-id="5d8a9-116">分類測試影像</span><span class="sxs-lookup"><span data-stu-id="5d8a9-116">Classify a test image</span></span>

<span data-ttu-id="5d8a9-117">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-117">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span> <span data-ttu-id="5d8a9-118">請注意，根據預設，本教學課程的 .NET 專案組態以 .NET Core 2.2 為目標。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-118">Note that by default, the .NET project configuration for this tutorial targets .NET core 2.2.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="5d8a9-119">什麼是傳輸學習？</span><span class="sxs-lookup"><span data-stu-id="5d8a9-119">What is transfer learning?</span></span>

<span data-ttu-id="5d8a9-120">轉移學習是在解決一個問題，並將其套用至不同但相關的問題時，使用所獲得知識的過程。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-120">Transfer learning is the process of using knowledge gained while solving one problem and applying it to a different but related problem.</span></span>

<span data-ttu-id="5d8a9-121">在本教學課程中，您會使用已定型的部分 TensorFlow 模型，將影像分類成一千個類別-在 ML.NET 模型中，將影像分類成3個類別。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-121">For this tutorial, you use part of a TensorFlow model - trained to classify images into a thousand categories - in an ML.NET model that classifies images into 3 categories.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5d8a9-122">必要條件</span><span class="sxs-lookup"><span data-stu-id="5d8a9-122">Prerequisites</span></span>

* <span data-ttu-id="5d8a9-123">已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-123">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="5d8a9-124">Microsoft.ML 1.3.1 Nuget 套件</span><span class="sxs-lookup"><span data-stu-id="5d8a9-124">Microsoft.ML 1.3.1 Nuget package</span></span>
* <span data-ttu-id="5d8a9-125">ImageAnalytics 1.3.1 Nuget 套件</span><span class="sxs-lookup"><span data-stu-id="5d8a9-125">Microsoft.ML.ImageAnalytics 1.3.1 Nuget package</span></span>
* <span data-ttu-id="5d8a9-126">TensorFlow 1.3.1 Nuget 套件</span><span class="sxs-lookup"><span data-stu-id="5d8a9-126">Microsoft.ML.TensorFlow 1.3.1 Nuget package</span></span>

* [<span data-ttu-id="5d8a9-127">教學課程資產目錄 .ZIP 檔案</span><span class="sxs-lookup"><span data-stu-id="5d8a9-127">The tutorial assets directory .ZIP file</span></span>](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)

* [<span data-ttu-id="5d8a9-128">InceptionV1 機器學習模型</span><span class="sxs-lookup"><span data-stu-id="5d8a9-128">The InceptionV1 machine learning model</span></span>](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-right-machine-learning-task"></a><span data-ttu-id="5d8a9-129">選取適當的機器學習工作</span><span class="sxs-lookup"><span data-stu-id="5d8a9-129">Select the right machine learning task</span></span>

### <a name="deep-learning"></a><span data-ttu-id="5d8a9-130">深度學習</span><span class="sxs-lookup"><span data-stu-id="5d8a9-130">Deep learning</span></span>

<span data-ttu-id="5d8a9-131">[深度學習](https://en.wikipedia.org/wiki/Deep_learning)是機器學習的子集，其正為電腦視覺及語音辨識等領域帶來革命性的影響。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-131">[Deep learning](https://en.wikipedia.org/wiki/Deep_learning) is a subset of Machine Learning, which is revolutionizing areas like Computer Vision and Speech Recognition.</span></span>

<span data-ttu-id="5d8a9-132">深度學習模型是使用包含多個學習層級的大量[已標籤資料](https://en.wikipedia.org/wiki/Labeled_data) \(英文\) 及[神經網路](https://en.wikipedia.org/wiki/Artificial_neural_network)來定型的。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-132">Deep learning models are trained by using large sets of [labeled data](https://en.wikipedia.org/wiki/Labeled_data) and [neural networks](https://en.wikipedia.org/wiki/Artificial_neural_network) that contain multiple learning layers.</span></span> <span data-ttu-id="5d8a9-133">深度學習：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-133">Deep learning:</span></span>

* <span data-ttu-id="5d8a9-134">能在某些工作上產生較好的效能，例如電腦視覺。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-134">Performs better on some tasks like Computer Vision.</span></span>
* <span data-ttu-id="5d8a9-135">需要大量的定型資料。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-135">Requires huge amounts of training data.</span></span>

<span data-ttu-id="5d8a9-136">影像分類是常見的 Machine Learning 工作，可讓我們自動將影像分類為下列類別：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-136">Image Classification is a common Machine Learning task that allows us to automatically classify images into categories such as:</span></span>

* <span data-ttu-id="5d8a9-137">是否能在影像中偵測到人類面孔。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-137">Detecting a human face in an image or not.</span></span>
* <span data-ttu-id="5d8a9-138">偵測貓與狗。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-138">Detecting cats vs. dogs.</span></span>

 <span data-ttu-id="5d8a9-139">或如下列影像所示，判斷影像是否為（n）食物、玩具或設備：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-139">Or as in the following images, determining if an image is a(n)  food, toy, or appliance:</span></span>

<span data-ttu-id="5d8a9-140">![披薩影像](./media/image-classification/220px-Pepperoni_pizza.jpg)
![玩具熊影像](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![烤麵包機影像](./media/image-classification/193px-Broodrooster.jpg)</span><span class="sxs-lookup"><span data-stu-id="5d8a9-140">![pizza image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![teddy bear image](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toaster image](./media/image-classification/193px-Broodrooster.jpg)</span></span>

>[!Note]
> <span data-ttu-id="5d8a9-141">上述影像為 Wikimedia Commons 所有，並具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-141">The preceding images belong to Wikimedia Commons and are attributed as follows:</span></span>
>
> * <span data-ttu-id="5d8a9-142">"220px-Pepperoni_pizza.jpg" 公眾領域， https://commons.wikimedia.org/w/index.php?curid=79505 \(英文\)，</span><span class="sxs-lookup"><span data-stu-id="5d8a9-142">"220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,</span></span>
> * <span data-ttu-id="5d8a9-143">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" 攝影者：[Jonik](https://commons.wikimedia.org/wiki/User:Jonik) \(英文\) - 自行拍攝，CC BY-SA 2.0， https://commons.wikimedia.org/w/index.php?curid=48166 \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-143">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.</span></span>
> * <span data-ttu-id="5d8a9-144">"193px-Broodrooster.jpg" 攝影者：[M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) \(英文\) - 自行創作，CC BY-SA 3.0， https://commons.wikimedia.org/w/index.php?curid=27403 \(英文\)</span><span class="sxs-lookup"><span data-stu-id="5d8a9-144">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403</span></span>

<span data-ttu-id="5d8a9-145">@No__t-0 經過訓練，可將影像分類為一千個類別，但在本教學課程中，您需要將影像分類為較小的類別集，而僅限於那些類別。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-145">The `Inception model` is trained to classify images into a thousand categories, but for this tutorial, you need to classify images in a smaller category set, and only those categories.</span></span> <span data-ttu-id="5d8a9-146">這就是 `transfer learning` (遷移學習) 名稱中 `transfer` (遷移) 這部分派上用場的時候。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-146">Enter the `transfer` part of `transfer learning`.</span></span> <span data-ttu-id="5d8a9-147">您可以將 `Inception model` 辨識及分類影像的能力遷移至您自訂影像分類器新的受限類別之中。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-147">You can transfer the `Inception model`'s ability to recognize and classify images to the new limited categories of your custom image classifier.</span></span>

* <span data-ttu-id="5d8a9-148">Food (食物)</span><span class="sxs-lookup"><span data-stu-id="5d8a9-148">Food</span></span>
* <span data-ttu-id="5d8a9-149">Toy (玩具)</span><span class="sxs-lookup"><span data-stu-id="5d8a9-149">Toy</span></span>
* <span data-ttu-id="5d8a9-150">Appliance (設備)</span><span class="sxs-lookup"><span data-stu-id="5d8a9-150">Appliance</span></span>

<span data-ttu-id="5d8a9-151">本教學課程使用 TensorFlow[開始模型](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)深度學習模型，這是在 @no__t 1 資料集上定型的熱門影像辨識模型。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-151">This tutorial uses the TensorFlow [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) deep learning model, a popular image recognition model trained on the `ImageNet` dataset.</span></span> <span data-ttu-id="5d8a9-152">TensorFlow 模型會將整個影像分類為一千個類別，例如 "傘"、"Jersey" 和 "洗碗機"。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-152">The TensorFlow model classifies entire images into a thousand classes, such as “Umbrella”, “Jersey”, and “Dishwasher”.</span></span>

<span data-ttu-id="5d8a9-153">因為 `Inception model` 已在數千個不同的映射上預先定型，所以內部會包含影像識別所需的[影像功能](https://en.wikipedia.org/wiki/Feature_(computer_vision))。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-153">Because the `Inception model` has already been pre trained on thousands of different images, internally it contains the [image features](https://en.wikipedia.org/wiki/Feature_(computer_vision)) needed for image identification.</span></span> <span data-ttu-id="5d8a9-154">我們可以利用模型中的這些內部影像功能，以更少的類別來定型新模型。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-154">We can make use of these internal image features in the model to train a new model with far fewer classes.</span></span>

<span data-ttu-id="5d8a9-155">如下圖所示，您會在 .NET Core 或 .NET Framework 應用程式中新增對 ML.NET NuGet 套件的參考。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-155">As shown in the following diagram, you add a reference to the ML.NET NuGet packages in your .NET Core or .NET Framework applications.</span></span> <span data-ttu-id="5d8a9-156">實際上，ML.NET 包含並參考原生 @no__t 0 程式庫，可讓您撰寫程式碼來載入現有已定型的 @no__t 1 模型檔案。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-156">Under the covers, ML.NET includes and references the native `TensorFlow` library that allows you to write code that loads an existing trained `TensorFlow` model file.</span></span>

![TensorFlow 轉換 ML.NET 架構圖表](./media/image-classification/tensorflow-mlnet.png)

### <a name="multiclass-classification"></a><span data-ttu-id="5d8a9-158">多元分類</span><span class="sxs-lookup"><span data-stu-id="5d8a9-158">Multiclass classification</span></span>

<span data-ttu-id="5d8a9-159">在使用 TensorFlow 起始模型來解壓縮適用于傳統機器學習演算法輸入的功能之後，我們會新增一個 ML.NET 的[多類別分類器](../resources/tasks.md#multiclass-classification)。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-159">After using the TensorFlow inception model to extract features suitable as input for a classical machine learning algorithm, we add an ML.NET [multi-class classifier](../resources/tasks.md#multiclass-classification).</span></span>

<span data-ttu-id="5d8a9-160">在此案例中使用的特定訓練員是[多維度羅吉斯回歸演算法](https://en.wikipedia.org/wiki/Multinomial_logistic_regression)。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-160">The specific trainer used in this case is the [multinomial logistic regression algorithm](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).</span></span>

<span data-ttu-id="5d8a9-161">這個定型者所實行的演算法會在大量功能的問題上順利執行，這是在影像資料上操作的深度學習模型的情況。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-161">The algorithm implemented by this trainer performs well on problems with a large number of features, which is the case for a deep learning model operating on image data.</span></span>

### <a name="data"></a><span data-ttu-id="5d8a9-162">Data</span><span class="sxs-lookup"><span data-stu-id="5d8a9-162">Data</span></span>

<span data-ttu-id="5d8a9-163">有兩個資料來源：`.tsv` 檔案，以及影像檔案。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-163">There are two data sources: the `.tsv` file, and the image files.</span></span>  <span data-ttu-id="5d8a9-164">`tags.tsv` 檔案包含兩個資料行：第一個會被定義為 `ImagePath`，而第二個則是對應至影像的 `Label`。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-164">The `tags.tsv` file contains two columns: the first one is defined as `ImagePath` and the second one is the `Label` corresponding to the image.</span></span> <span data-ttu-id="5d8a9-165">下列範例檔案沒有標頭資料列，且看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-165">The following example file doesn't have a header row, and looks like this:</span></span>

<!-- markdownlint-disable MD010 -->
```tsv
broccoli.jpg    food
pizza.jpg   food
pizza2.jpg  food
teddy2.jpg  toy
teddy3.jpg  toy
teddy4.jpg  toy
toaster.jpg appliance
toaster2.png    appliance
```
<!-- markdownlint-enable MD010 -->

<span data-ttu-id="5d8a9-166">定型及測試影像都位於您將以 zip 檔案下載的資產資料夾中。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-166">The training and testing images are located in the assets folders that you'll download in a zip file.</span></span> <span data-ttu-id="5d8a9-167">這些影像皆由 Wikimedia Commons 所有。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-167">These images belong to Wikimedia Commons.</span></span>
> <span data-ttu-id="5d8a9-168">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208) \(英文\), the free media repository*。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-168">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), the free media repository.*</span></span> <span data-ttu-id="5d8a9-169">已從下列來源取出10:48，2018年10月17日： https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toaster https://commons.wikimedia.org/wiki/Teddy_bear</span><span class="sxs-lookup"><span data-stu-id="5d8a9-169">Retrieved 10:48, October 17, 2018 from: https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toaster https://commons.wikimedia.org/wiki/Teddy_bear</span></span>

## <a name="setup"></a><span data-ttu-id="5d8a9-170">安裝程式</span><span class="sxs-lookup"><span data-stu-id="5d8a9-170">Setup</span></span>

### <a name="create-a-project"></a><span data-ttu-id="5d8a9-171">建立專案</span><span class="sxs-lookup"><span data-stu-id="5d8a9-171">Create a project</span></span>

1. <span data-ttu-id="5d8a9-172">建立稱為 "TransferLearningTF" 的 **.NET Core 主控台應用程式**。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-172">Create a **.NET Core Console Application** called "TransferLearningTF".</span></span>

1. <span data-ttu-id="5d8a9-173">安裝「Microsoft.ML NuGet 套件」：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-173">Install the **Microsoft.ML NuGet Package**:</span></span>

    * <span data-ttu-id="5d8a9-174">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-174">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    * <span data-ttu-id="5d8a9-175">選擇 [nuget.org] 作為 [套件來源]，選取 [瀏覽] 索引標籤，搜尋 **Microsoft.ML**。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-175">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span>
    * <span data-ttu-id="5d8a9-176">按一下 [**版本**] 下拉式清單，選取清單中的 [ **1.3.1** ] 套件，然後選取 [**安裝**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-176">Click on the **Version** drop-down, select the **1.3.1** package in the list, and select the **Install** button.</span></span>
    * <span data-ttu-id="5d8a9-177">選取 [**預覽變更**] 對話方塊上的 [**確定]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-177">Select the **OK** button on the **Preview Changes** dialog.</span></span>
    * <span data-ttu-id="5d8a9-178">如果您同意所列套件的授權條款，請選取 [**授權接受**] 對話方塊上的 [**我接受**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-178">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    * <span data-ttu-id="5d8a9-179">針對**ImageAnalytics v 1.3.1**和**TensorFlow v 1.3.1**重複這些步驟。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-179">Repeat these steps for **Microsoft.ML.ImageAnalytics v1.3.1** and **Microsoft.ML.TensorFlow v1.3.1**.</span></span>

### <a name="download-assets"></a><span data-ttu-id="5d8a9-180">下載資產</span><span class="sxs-lookup"><span data-stu-id="5d8a9-180">Download assets</span></span>

1. <span data-ttu-id="5d8a9-181">下載[專案資產目錄 zip 檔案](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)，然後將它解壓縮。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-181">Download [The project assets directory zip file](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip), and unzip.</span></span>

1. <span data-ttu-id="5d8a9-182">將 `assets` 目錄複製到您的 *TransferLearningTF* 專案目錄中。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-182">Copy the `assets` directory into your *TransferLearningTF* project directory.</span></span> <span data-ttu-id="5d8a9-183">此目錄及其子目錄包含本教學課程所需的資料和支援檔案 (Inception model 除外，您將會在下個步驟中下載並新增它)。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-183">This directory and its subdirectories contain the data and support files (except for the Inception model, which you'll download and add in the next step) needed for this tutorial.</span></span>

1. <span data-ttu-id="5d8a9-184">下載 [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)，然後將它解壓縮。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-184">Download the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), and unzip.</span></span>

1. <span data-ttu-id="5d8a9-185">將剛才解壓縮的 `inception5h` 目錄的內容複製到您 *TransferLearningTF* 專案的 `assets/inputs-train/inception` 目錄中。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-185">Copy the contents of the `inception5h` directory just unzipped into your *TransferLearningTF* project `assets/inputs-train/inception` directory.</span></span> <span data-ttu-id="5d8a9-186">此目錄包含本教學課程所需的模型和其他支援檔案，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-186">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![Inception 目錄內容](./media/image-classification/inception-files.png)

1. <span data-ttu-id="5d8a9-188">在 [方案總管] 中，以滑鼠右鍵按一下資產目錄及子目錄中的每個檔案，然後選取 [內容]。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-188">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="5d8a9-189">在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-189">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="5d8a9-190">建立類別及定義路徑</span><span class="sxs-lookup"><span data-stu-id="5d8a9-190">Create classes and define paths</span></span>

1. <span data-ttu-id="5d8a9-191">在 *Program.cs* 檔案頂端新增下列額外的 `using` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-191">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

1. <span data-ttu-id="5d8a9-192">將下列程式碼新增至 `Main` 方法上方的一行，以指定資產路徑：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-192">Add the following code to the line right above the `Main` method to specify the asset paths:</span></span>

    [!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

1. <span data-ttu-id="5d8a9-193">為輸入資料和預測建立類別。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-193">Create classes for your input data, and predictions.</span></span>

    [!code-csharp[DeclareImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareImageData)]

    <span data-ttu-id="5d8a9-194">`ImageData` 是輸入資料集類別，並具有下列 <xref:System.String> 欄位：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-194">`ImageData` is the input image data class and has the following <xref:System.String> fields:</span></span>

    * <span data-ttu-id="5d8a9-195">`ImagePath` 包含影像檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-195">`ImagePath` contains the image file name.</span></span>
    * <span data-ttu-id="5d8a9-196">`Label` 包含影像標籤的值。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-196">`Label` contains a value for the image label.</span></span>

1. <span data-ttu-id="5d8a9-197">將新類別新增至 `ImagePrediction` 的專案：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-197">Add a new class to your project for `ImagePrediction`:</span></span>

    [!code-csharp[DeclareImagePrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareImagePrediction)]

    <span data-ttu-id="5d8a9-198">`ImagePrediction` 是影像預測類別，並具有下列欄位：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-198">`ImagePrediction` is the image prediction class and has the following fields:</span></span>

    * <span data-ttu-id="5d8a9-199">`Score` 包含指定影像分類的信賴百分比。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-199">`Score` contains the confidence percentage for a given image classification.</span></span>
    * <span data-ttu-id="5d8a9-200">`PredictedLabelValue` 包含已預測影像分類標籤的值。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-200">`PredictedLabelValue` contains a value for the predicted image classification label.</span></span>

    <span data-ttu-id="5d8a9-201">`ImagePrediction` 是在模型定型後，用來進行預測的類別。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-201">`ImagePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="5d8a9-202">它具有影像路徑的 `string` (`ImagePath`)。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-202">It has a `string` (`ImagePath`) for the image path.</span></span> <span data-ttu-id="5d8a9-203">@No__t-0 是用來重複使用和定型模型。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-203">The `Label` is used to reuse and train the model.</span></span> <span data-ttu-id="5d8a9-204">`PredictedLabelValue` 的使用時機是在進行預測和評估的期間。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-204">The `PredictedLabelValue` is used during prediction and evaluation.</span></span> <span data-ttu-id="5d8a9-205">就評估而言，會使用含有定型資料、預設值及模型的輸入。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-205">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="5d8a9-206">在 Main 中初始化變數</span><span class="sxs-lookup"><span data-stu-id="5d8a9-206">Initialize variables in Main</span></span>

1. <span data-ttu-id="5d8a9-207">搭配 `MLContext` 的新執行個體來初始化 `mlContext` 變數。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-207">Initialize the `mlContext` variable with a new instance of `MLContext`.</span></span>  <span data-ttu-id="5d8a9-208">在 `Main` 方法中，以下列程式碼取代 `Console.WriteLine("Hello World!")`：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-208">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

    [!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

    <span data-ttu-id="5d8a9-209">[MLContext 類別](xref:Microsoft.ML.MLContext)是所有 ML.NET 作業的起點，且初始化 `mlContext` 會建立新的 ML.NET 環境，其可在模型建立工作流程物件之間共用。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-209">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="5d8a9-210">就概念而言，類似於 Entity Framework 中的 `DBContext`。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-210">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="create-a-struct-for-inception-model-parameters"></a><span data-ttu-id="5d8a9-211">建立用於開始模型參數的結構</span><span class="sxs-lookup"><span data-stu-id="5d8a9-211">Create a struct for Inception model parameters</span></span>

1. <span data-ttu-id="5d8a9-212">開始模型有數個您需要傳入的參數。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-212">The Inception model has several parameters you need to pass in.</span></span> <span data-ttu-id="5d8a9-213">使用下列程式碼，在 `Main()` 方法之後，建立結構來將參數值對應至易記名稱：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-213">Create a struct to map the parameter values to friendly names with the following code, just after the `Main()` method:</span></span>

    [!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a><span data-ttu-id="5d8a9-214">建立顯示公用程式方法</span><span class="sxs-lookup"><span data-stu-id="5d8a9-214">Create a display utility method</span></span>

<span data-ttu-id="5d8a9-215">因為您將會不只一次顯示影像資料和相關預測，所以請建立顯示公用程式方法來處理顯示影像和預測結果。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-215">Since you'll display the image data and the related predictions more than once, create a display utility method to handle displaying the image and prediction results.</span></span>

1. <span data-ttu-id="5d8a9-216">使用下列程式碼，在緊接著 `InceptionSettings` 結構之後，建立 `DisplayResults()` 方法：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-216">Create the `DisplayResults()` method, just after the `InceptionSettings` struct, using the following code:</span></span>

    ```csharp
    private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
    {

    }
    ```

1. <span data-ttu-id="5d8a9-217">填入 `DisplayResults` 方法的主體：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-217">Fill in the body of the `DisplayResults` method:</span></span>

    [!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

### <a name="create-a-tsv-file-utility-method"></a><span data-ttu-id="5d8a9-218">建立 .tsv 檔案公用程式方法</span><span class="sxs-lookup"><span data-stu-id="5d8a9-218">Create a .tsv file utility method</span></span>

1. <span data-ttu-id="5d8a9-219">請使用下列程式碼，在緊接著 `DisplayResults()` 方法之後，建立 `ReadFromTsv()` 方法：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-219">Create the `ReadFromTsv()` method, just after the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
    {

    }
    ```

1. <span data-ttu-id="5d8a9-220">填入 `ReadFromTsv` 方法的主體：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-220">Fill in the body of the `ReadFromTsv` method:</span></span>

    [!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]

    <span data-ttu-id="5d8a9-221">程式碼會剖析 `tags.tsv` 檔案，將檔案路徑新增至 @no__t 1 屬性的影像檔案名稱，並將其載入至 @no__t 3 物件，並將 `Label`。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-221">The code parses through the `tags.tsv` file to add the file path to the image file name for the `ImagePath` property and load it and the `Label` into an `ImageData` object.</span></span>

### <a name="create-a-method-to-make-a-prediction"></a><span data-ttu-id="5d8a9-222">建立方法以進行預測</span><span class="sxs-lookup"><span data-stu-id="5d8a9-222">Create a method to make a prediction</span></span>

1. <span data-ttu-id="5d8a9-223">請使用下列程式碼，緊接在 `DisplayResults()` 方法之前，建立 `ClassifySingleImage()` 方法：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-223">Create the `ClassifySingleImage()` method, just before the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. <span data-ttu-id="5d8a9-224">建立 `ImageData` 物件，其中包含單一 `ImagePath` 的完整路徑和影像檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-224">Create an `ImageData` object that contains the fully qualified path and image file name for the single `ImagePath`.</span></span> <span data-ttu-id="5d8a9-225">將下列程式碼新增為 `ClassifySingleImage()` 方法中的下一行：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-225">Add the following code as the next  lines in the `ClassifySingleImage()` method:</span></span>

    [!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

1. <span data-ttu-id="5d8a9-226">藉由將下列程式碼新增為 `ClassifySingleImage` 方法中的下一行來進行單一預測：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-226">Make a single prediction, by adding the following code as the next line in the `ClassifySingleImage` method:</span></span>

    [!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

    <span data-ttu-id="5d8a9-227">[PredictionEngine 類別](xref:Microsoft.ML.PredictionEngine%602)是一個方便的 API，可在單一資料實例上執行預測。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-227">The [PredictionEngine class](xref:Microsoft.ML.PredictionEngine%602) class is a convenience API that performs a prediction on a single instance of data.</span></span> <span data-ttu-id="5d8a9-228">若要取得預測，請使用[Predict （）](xref:Microsoft.ML.PredictionEngine%602.Predict%2A)方法。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-228">To get the prediction, use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) method.</span></span>

1. <span data-ttu-id="5d8a9-229">將預測結果顯示為 `ClassifySingleImage()` 方法中的下一行程式碼：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-229">Display the prediction result as the next line of code in the `ClassifySingleImage()` method:</span></span>

   [!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="construct-the-mlnet-model-pipeline"></a><span data-ttu-id="5d8a9-230">建立 ML.NET 模型管線</span><span class="sxs-lookup"><span data-stu-id="5d8a9-230">Construct the ML.NET model pipeline</span></span>

<span data-ttu-id="5d8a9-231">ML.NET 模型管線是一鏈估算器。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-231">An ML.NET model pipeline is a chain of estimators.</span></span> <span data-ttu-id="5d8a9-232">請注意，管線結構中不會執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-232">Note that no execution happens during pipeline construction.</span></span> <span data-ttu-id="5d8a9-233">系統會建立估計工具物件，但不會執行。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-233">The estimator objects are created but not executed.</span></span>

1. <span data-ttu-id="5d8a9-234">新增方法以產生模型</span><span class="sxs-lookup"><span data-stu-id="5d8a9-234">Add a method to generate the model</span></span>

    <span data-ttu-id="5d8a9-235">這個方法是教學課程的核心。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-235">This method is the heart of the tutorial.</span></span> <span data-ttu-id="5d8a9-236">它會建立模型的管線，並訓練管線以產生 ML.NET 模型。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-236">It creates a pipeline for the model, and trains the pipeline to produce the ML.NET model.</span></span> <span data-ttu-id="5d8a9-237">它也會針對某些先前看不見的測試資料評估模型。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-237">It also evaluates the model against some previously unseen test data.</span></span>

    <span data-ttu-id="5d8a9-238">使用下列程式碼，緊接在 `InceptionSettings` 結構之後及 `DisplayResults()` 方法之前，建立 `GenerateModel()` 方法：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-238">Create the `GenerateModel()` method, just after the `InceptionSettings` struct and just before the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer GenerateModel(MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="5d8a9-239">新增估算器以載入、調整大小，並從影像資料中將圖元解壓縮：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-239">Add the estimators to load, resize and extract the pixels from the image data:</span></span>

    [!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

    <span data-ttu-id="5d8a9-240">影像資料必須處理成 TensorFlow 模型所預期的格式。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-240">The image data needs to be processed into the format that the TensorFlow model expects.</span></span> <span data-ttu-id="5d8a9-241">在此情況下，影像會載入記憶體中，並調整為一致大小，而圖元會解壓縮為數值向量。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-241">In this case, the images are loaded into memory, resized to a consistent size, and the pixels are extracted into a numeric vector.</span></span>

1. <span data-ttu-id="5d8a9-242">新增估計工具以載入 TensorFlow 模型，並對它進行評分：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-242">Add the estimator to load the TensorFlow model, and score it:</span></span>

    [!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

    <span data-ttu-id="5d8a9-243">管線中的這個階段會將 TensorFlow 模型載入記憶體中，然後透過 TensorFlow 模型網路處理圖元值的向量。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-243">This stage in the pipeline loads the TensorFlow model into memory, then processes the vector of pixel values through the TensorFlow model network.</span></span> <span data-ttu-id="5d8a9-244">將輸入套用至深度學習模型，並使用模型產生輸出，稱為**計分**。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-244">Applying inputs to a deep learning model, and generating an output using the model, is referred to as **Scoring**.</span></span> <span data-ttu-id="5d8a9-245">整體使用模型時，計分會進行推斷或預測。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-245">When using the model in its entirety, scoring makes an inference, or prediction.</span></span> 

    <span data-ttu-id="5d8a9-246">在此情況下，您會使用最後一層以外的所有 TensorFlow 模型，這是進行推斷的層。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-246">In this case, you use all of the TensorFlow model except the last layer, which is the layer that makes the inference.</span></span> <span data-ttu-id="5d8a9-247">倒數第二圖層的輸出會標示 `softmax_2_preactivation`。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-247">The output of the penultimate layer is labeled `softmax_2_preactivation`.</span></span> <span data-ttu-id="5d8a9-248">此圖層的輸出實際上是特徵的向量，可描述原始輸入影像。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-248">The output of this layer is effectively a vector of features that characterize the original input images.</span></span>

    <span data-ttu-id="5d8a9-249">TensorFlow 模型所產生的此功能向量將用來做為 ML.NET 定型演算法的輸入。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-249">This feature vector generated by the TensorFlow model will be used as input to an ML.NET training algorithm.</span></span>

1. <span data-ttu-id="5d8a9-250">新增估計工具，以將定型資料中的字串標籤對應到整數索引鍵值：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-250">Add the estimator to map the string labels in the training data to integer key values:</span></span>

    [!code-csharp[MapValueToKey](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey)]

    <span data-ttu-id="5d8a9-251">接下來附加的 ML.NET 訓練員需要其標籤為 `key` 格式，而不是任一字元串。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-251">The ML.NET trainer that is appended next requires its labels to be in `key` format rather than arbitrary strings.</span></span> <span data-ttu-id="5d8a9-252">「索引鍵」是一個數位，其中包含一個與字串值的對應。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-252">A key is a number that has a one to one mapping to a string value.</span></span>

1. <span data-ttu-id="5d8a9-253">新增 ML.NET 訓練演算法：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-253">Add the ML.NET training algorithm:</span></span>

    [!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

1. <span data-ttu-id="5d8a9-254">新增估計工具以將預測的索引鍵值對應回字串：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-254">Add the estimator to map the predicted key value back into a string:</span></span>

    [!code-csharp[MapKeyToValue](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapKeyToValue)]

## <a name="train-the-model"></a><span data-ttu-id="5d8a9-255">將模型定型</span><span class="sxs-lookup"><span data-stu-id="5d8a9-255">Train the model</span></span>

1. <span data-ttu-id="5d8a9-256">使用[LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options))包裝函式載入定型資料。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-256">Load the training data using the [LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) wrapper.</span></span> <span data-ttu-id="5d8a9-257">將下列程式碼加入為 `GenerateModel()` 方法中的下一行：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-257">Add the following code as the next line in the `GenerateModel()` method:</span></span>

    [!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

    <span data-ttu-id="5d8a9-258">ML.NET 中的資料以 [IDataView 類別](xref:Microsoft.ML.IDataView) 表示。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-258">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="5d8a9-259">`IDataView` 是彈性且有效率的表格式資料描述方式 (數值和文字)。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-259">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="5d8a9-260">資料可以從文字或即時 (例如 SQL 資料庫或記錄檔) 載入至 `IDataView` 物件。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-260">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

1. <span data-ttu-id="5d8a9-261">使用上述載入的資料來定型模型：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-261">Train the model with the data loaded above:</span></span>

    [!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

    <span data-ttu-id="5d8a9-262">@No__t-0 方法會將訓練資料集套用至管線，以訓練您的模型。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-262">The `Fit()` method trains your model by applying the training dataset to the pipeline.</span></span>

## <a name="evaluate-the-accuracy-of-the-model"></a><span data-ttu-id="5d8a9-263">評估模型的精確度</span><span class="sxs-lookup"><span data-stu-id="5d8a9-263">Evaluate the accuracy of the model</span></span>

1. <span data-ttu-id="5d8a9-264">將下列程式碼新增至 `GenerateModel` 方法的下一行，以載入並轉換測試資料：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-264">Load and transform the test data, by adding the following code to the next line of the `GenerateModel` method:</span></span>

    [!code-csharp[LoadAndTransformTestData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadAndTransformTestData "Load and transform test data")]

    <span data-ttu-id="5d8a9-265">您可以使用幾個範例影像來評估模型。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-265">There are a few sample images that you can use to evaluate the model.</span></span> <span data-ttu-id="5d8a9-266">就像定型資料一樣，這些都必須載入至 `IDataView`，才能由模型進行轉換。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-266">Like the training data, these need to be loaded into an `IDataView`, so that they can be transformed by the model.</span></span>
   
1. <span data-ttu-id="5d8a9-267">將下列程式碼新增至 `GenerateModel()` 方法以評估模型：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-267">Add the following code to the `GenerateModel()` method to evaluate the model:</span></span>

    [!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

    <span data-ttu-id="5d8a9-268">當您具有預測之後，請設定 [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) 方法：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-268">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method:</span></span>

    * <span data-ttu-id="5d8a9-269">評估模型（比較預測值與測試資料集 `labels`）。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-269">Assesses the model (compares the predicted values with the test dataset `labels`).</span></span>
    * <span data-ttu-id="5d8a9-270">傳回模型效能計量。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-270">Returns the model performance metrics.</span></span>

1. <span data-ttu-id="5d8a9-271">顯示模型精確度計量</span><span class="sxs-lookup"><span data-stu-id="5d8a9-271">Display the model accuracy metrics</span></span>

    <span data-ttu-id="5d8a9-272">使用下列程式碼來顯示計量、共用結果，然後依結果採取動作：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-272">Use the following code to display the metrics, share the results, and then act on them:</span></span>

    [!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

    <span data-ttu-id="5d8a9-273">下列計量會針對影像分類進行評估：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-273">The following metrics are evaluated for image classification:</span></span>

    * <span data-ttu-id="5d8a9-274">`Log-loss`：請參閱[記錄檔遺失](../resources/glossary.md#log-loss)。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-274">`Log-loss` - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="5d8a9-275">建議讓記錄檔遺失盡量接近零。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-275">You want Log-loss to be as close to zero as possible.</span></span>
    * <span data-ttu-id="5d8a9-276">`Per class Log-loss`.</span><span class="sxs-lookup"><span data-stu-id="5d8a9-276">`Per class Log-loss`.</span></span> <span data-ttu-id="5d8a9-277">建議讓每個類別的記錄檔遺失盡量接近零。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-277">You want per class Log-loss to be as close to zero as possible.</span></span>

1. <span data-ttu-id="5d8a9-278">新增下列程式碼來將定型後的模型作為下一行傳回：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-278">Add the following code to return the trained model as the next line:</span></span>

    [!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReturnModel)]

## <a name="run-the-application"></a><span data-ttu-id="5d8a9-279">執行應用程式！</span><span class="sxs-lookup"><span data-stu-id="5d8a9-279">Run the application!</span></span>

1. <span data-ttu-id="5d8a9-280">建立 MLCoNtext 類別之後，在 `Main` 方法中，將 `GenerateModel` 的呼叫加入：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-280">Add the call to `GenerateModel` in the `Main` method after the creation of the MLContext class:</span></span>

    [!code-csharp[CallGenerateModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallGenerateModel)]

1. <span data-ttu-id="5d8a9-281">將 `ClassifySingleImage()` 方法的呼叫加入 `Main` 方法中的下一行程式碼：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-281">Add the call to the `ClassifySingleImage()` method as the next line of code in the `Main` method:</span></span>

    [!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

1. <span data-ttu-id="5d8a9-282">執行主控台應用程式（Ctrl + F5）。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-282">Run your console app (Ctrl + F5).</span></span> <span data-ttu-id="5d8a9-283">您的結果應該與下列輸出類似。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-283">Your results should be similar to the following output.</span></span>  <span data-ttu-id="5d8a9-284">您可能會看到警告或處理中訊息，但為了讓結果變得清楚，這些訊息已從下列結果中移除。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-284">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

    ```console
    =============== Training classification model ===============
    Image: broccoli.jpg predicted as: food with score: 0.976743
    Image: pizza.jpg predicted as: food with score: 0.9751652
    Image: pizza2.jpg predicted as: food with score: 0.9660203
    Image: teddy2.jpg predicted as: toy with score: 0.9748783
    Image: teddy3.jpg predicted as: toy with score: 0.9829691
    Image: teddy4.jpg predicted as: toy with score: 0.9868168
    Image: toaster.jpg predicted as: appliance with score: 0.9769174
    Image: toaster2.png predicted as: appliance with score: 0.9800823
    =============== Classification metrics ===============
    LogLoss is: 0.0228266745633507
    PerClassLogLoss is: 0.0277501705149937 , 0.0186303530571291 , 0.0217359128952187
    =============== Making single image classification ===============
    Image: toaster3.jpg predicted as: appliance with score: 0.9625379

    C:\Program Files\dotnet\dotnet.exe (process 4304) exited with code 0.
    Press any key to close this window . . .
    ```

<span data-ttu-id="5d8a9-285">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="5d8a9-285">Congratulations!</span></span> <span data-ttu-id="5d8a9-286">您現在已成功建立影像分類的機器學習模型，其方式是在 ML.NET 中將轉移學習套用至 @no__t 0 模型。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-286">You've now successfully built a machine learning model for image classification by applying transfer learning to a `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="5d8a9-287">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-287">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span>

<span data-ttu-id="5d8a9-288">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-288">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="5d8a9-289">了解問題</span><span class="sxs-lookup"><span data-stu-id="5d8a9-289">Understand the problem</span></span>
> * <span data-ttu-id="5d8a9-290">將預先定型的 TensorFlow 模型納入 ML.NET 管線中</span><span class="sxs-lookup"><span data-stu-id="5d8a9-290">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span></span>
> * <span data-ttu-id="5d8a9-291">定型和評估 ML.NET 模型</span><span class="sxs-lookup"><span data-stu-id="5d8a9-291">Train and evaluate the ML.NET model</span></span>
> * <span data-ttu-id="5d8a9-292">分類測試影像</span><span class="sxs-lookup"><span data-stu-id="5d8a9-292">Classify a test image</span></span>

<span data-ttu-id="5d8a9-293">請查看機器學習範例 GitHub 存放庫，以探索更複雜的影像分類範例。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-293">Check out the Machine Learning samples GitHub repository to explore an expanded image classification sample.</span></span>
> [!div class="nextstepaction"]
> <span data-ttu-id="5d8a9-294">[dotnet/machinelearning-samples GitHub 存放庫](https://github.com/dotnet/machinelearning-samples/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="5d8a9-294">[dotnet/machinelearning-samples GitHub repository](https://github.com/dotnet/machinelearning-samples/)</span></span>
