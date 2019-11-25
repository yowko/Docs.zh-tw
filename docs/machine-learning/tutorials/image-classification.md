---
title: 'Tutorial: Generate an ML.NET image classification model from a pre-trained TensorFlow model'
description: Learn how to transfer the knowledge from an existing TensorFlow model into a new ML.NET image classification model. The TensorFlow model was trained to classify images into a thousand categories. The ML.NET model makes use of transfer learning to classify images into fewer broader categories.
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
author: natke
ms.author: nakersha
ms.openlocfilehash: 952ce5c52bcd09b8c4e4e40d5ddf85835a26478d
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204992"
---
# <a name="tutorial-generate-an-mlnet-image-classification-model-from-a-pre-trained-tensorflow-model"></a><span data-ttu-id="7f5fe-105">Tutorial: Generate an ML.NET image classification model from a pre-trained TensorFlow model</span><span class="sxs-lookup"><span data-stu-id="7f5fe-105">Tutorial: Generate an ML.NET image classification model from a pre-trained TensorFlow model</span></span>

<span data-ttu-id="7f5fe-106">Learn how to transfer the knowledge from an existing TensorFlow model into a new ML.NET image classification model.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-106">Learn how to transfer the knowledge from an existing TensorFlow model into a new ML.NET image classification model.</span></span>

<span data-ttu-id="7f5fe-107">The TensorFlow model was trained to classify images into a thousand categories.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-107">The TensorFlow model was trained to classify images into a thousand categories.</span></span> <span data-ttu-id="7f5fe-108">The ML.NET model makes use of part of the TensorFlow model in its pipeline to train a model to classify images into 3 categories.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-108">The ML.NET model makes use of part of the TensorFlow model in its pipeline to train a model to classify images into 3 categories.</span></span>

<span data-ttu-id="7f5fe-109">若要從頭對[影像分類](https://en.wikipedia.org/wiki/Outline_of_object_recognition) \(英文\) 模型進行定型，將會需要設定數以百萬計的參數、眾多已標籤的定型資料，以及大量的計算資源 (數以百計的 GPU 小時)。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-109">Training an [Image Classification](https://en.wikipedia.org/wiki/Outline_of_object_recognition) model from scratch requires setting millions of parameters, a ton of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="7f5fe-110">遷移學習的效能雖然不如從頭對自訂模型進行定型來得有效，但它能讓您透過僅需處理數以千計的影像 (而非數以百萬計的已標籤影像) 來縮短此程序，並以較為快速的方式建置自訂模型 (在不具備 GPU 的電腦上於一小時內便能完成)。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-110">While not as effective as training a custom model from scratch, transfer learning allows you to shortcut this process by working with thousands of images vs. millions of labeled images and build a customized model fairly quickly (within an hour on a machine without a GPU).</span></span> <span data-ttu-id="7f5fe-111">This tutorial scales that process down even further, using only a dozen training images.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-111">This tutorial scales that process down even further, using only a dozen training images.</span></span>

<span data-ttu-id="7f5fe-112">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="7f5fe-112">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="7f5fe-113">了解問題</span><span class="sxs-lookup"><span data-stu-id="7f5fe-113">Understand the problem</span></span>
> * <span data-ttu-id="7f5fe-114">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span><span class="sxs-lookup"><span data-stu-id="7f5fe-114">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span></span>
> * <span data-ttu-id="7f5fe-115">Train and evaluate the ML.NET model</span><span class="sxs-lookup"><span data-stu-id="7f5fe-115">Train and evaluate the ML.NET model</span></span>
> * <span data-ttu-id="7f5fe-116">Classify a test image</span><span class="sxs-lookup"><span data-stu-id="7f5fe-116">Classify a test image</span></span>

<span data-ttu-id="7f5fe-117">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-117">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span> <span data-ttu-id="7f5fe-118">請注意，根據預設，本教學課程的 .NET 專案組態以 .NET Core 2.2 為目標。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-118">Note that by default, the .NET project configuration for this tutorial targets .NET core 2.2.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="7f5fe-119">什麼是傳輸學習？</span><span class="sxs-lookup"><span data-stu-id="7f5fe-119">What is transfer learning?</span></span>

<span data-ttu-id="7f5fe-120">Transfer learning is the process of using knowledge gained while solving one problem and applying it to a different but related problem.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-120">Transfer learning is the process of using knowledge gained while solving one problem and applying it to a different but related problem.</span></span>

<span data-ttu-id="7f5fe-121">For this tutorial, you use part of a TensorFlow model - trained to classify images into a thousand categories - in an ML.NET model that classifies images into 3 categories.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-121">For this tutorial, you use part of a TensorFlow model - trained to classify images into a thousand categories - in an ML.NET model that classifies images into 3 categories.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7f5fe-122">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="7f5fe-122">Prerequisites</span></span>

* <span data-ttu-id="7f5fe-123">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-123">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
* [<span data-ttu-id="7f5fe-124">教學課程資產目錄 .ZIP 檔案</span><span class="sxs-lookup"><span data-stu-id="7f5fe-124">The tutorial assets directory .ZIP file</span></span>](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)
* [<span data-ttu-id="7f5fe-125">InceptionV1 機器學習模型</span><span class="sxs-lookup"><span data-stu-id="7f5fe-125">The InceptionV1 machine learning model</span></span>](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-right-machine-learning-task"></a><span data-ttu-id="7f5fe-126">Select the right machine learning task</span><span class="sxs-lookup"><span data-stu-id="7f5fe-126">Select the right machine learning task</span></span>

### <a name="deep-learning"></a><span data-ttu-id="7f5fe-127">深度學習</span><span class="sxs-lookup"><span data-stu-id="7f5fe-127">Deep learning</span></span>

<span data-ttu-id="7f5fe-128">[深度學習](https://en.wikipedia.org/wiki/Deep_learning)是機器學習的子集，其正為電腦視覺及語音辨識等領域帶來革命性的影響。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-128">[Deep learning](https://en.wikipedia.org/wiki/Deep_learning) is a subset of Machine Learning, which is revolutionizing areas like Computer Vision and Speech Recognition.</span></span>

<span data-ttu-id="7f5fe-129">深度學習模型是使用包含多個學習層級的大量[已標籤資料](https://en.wikipedia.org/wiki/Labeled_data) \(英文\) 及[神經網路](https://en.wikipedia.org/wiki/Artificial_neural_network)來定型的。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-129">Deep learning models are trained by using large sets of [labeled data](https://en.wikipedia.org/wiki/Labeled_data) and [neural networks](https://en.wikipedia.org/wiki/Artificial_neural_network) that contain multiple learning layers.</span></span> <span data-ttu-id="7f5fe-130">深度學習：</span><span class="sxs-lookup"><span data-stu-id="7f5fe-130">Deep learning:</span></span>

* <span data-ttu-id="7f5fe-131">能在某些工作上產生較好的效能，例如電腦視覺。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-131">Performs better on some tasks like Computer Vision.</span></span>
* <span data-ttu-id="7f5fe-132">Requires huge amounts of training data.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-132">Requires huge amounts of training data.</span></span>

<span data-ttu-id="7f5fe-133">Image Classification is a common Machine Learning task that allows us to automatically classify images into categories such as:</span><span class="sxs-lookup"><span data-stu-id="7f5fe-133">Image Classification is a common Machine Learning task that allows us to automatically classify images into categories such as:</span></span>

* <span data-ttu-id="7f5fe-134">是否能在影像中偵測到人類面孔。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-134">Detecting a human face in an image or not.</span></span>
* <span data-ttu-id="7f5fe-135">Detecting cats vs. dogs.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-135">Detecting cats vs. dogs.</span></span>

 <span data-ttu-id="7f5fe-136">Or as in the following images, determining if an image is a(n)  food, toy, or appliance:</span><span class="sxs-lookup"><span data-stu-id="7f5fe-136">Or as in the following images, determining if an image is a(n)  food, toy, or appliance:</span></span>

<span data-ttu-id="7f5fe-137">![披薩影像](./media/image-classification/220px-Pepperoni_pizza.jpg)
![玩具熊影像](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![烤麵包機影像](./media/image-classification/193px-Broodrooster.jpg)</span><span class="sxs-lookup"><span data-stu-id="7f5fe-137">![pizza image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![teddy bear image](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toaster image](./media/image-classification/193px-Broodrooster.jpg)</span></span>

>[!Note]
> <span data-ttu-id="7f5fe-138">上述影像為 Wikimedia Commons 所有，並具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="7f5fe-138">The preceding images belong to Wikimedia Commons and are attributed as follows:</span></span>
>
> * <span data-ttu-id="7f5fe-139">"220px-Pepperoni_pizza.jpg" 公眾領域， https://commons.wikimedia.org/w/index.php?curid=79505 \(英文\)，</span><span class="sxs-lookup"><span data-stu-id="7f5fe-139">"220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,</span></span>
> * <span data-ttu-id="7f5fe-140">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" 攝影者：[Jonik](https://commons.wikimedia.org/wiki/User:Jonik) \(英文\) - 自行拍攝，CC BY-SA 2.0， https://commons.wikimedia.org/w/index.php?curid=48166 \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-140">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.</span></span>
> * <span data-ttu-id="7f5fe-141">"193px-Broodrooster.jpg" 攝影者：[M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) \(英文\) - 自行創作，CC BY-SA 3.0， https://commons.wikimedia.org/w/index.php?curid=27403 \(英文\)</span><span class="sxs-lookup"><span data-stu-id="7f5fe-141">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403</span></span>

<span data-ttu-id="7f5fe-142">The `Inception model` is trained to classify images into a thousand categories, but for this tutorial, you need to classify images in a smaller category set, and only those categories.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-142">The `Inception model` is trained to classify images into a thousand categories, but for this tutorial, you need to classify images in a smaller category set, and only those categories.</span></span> <span data-ttu-id="7f5fe-143">這就是 `transfer learning` (遷移學習) 名稱中 `transfer` (遷移) 這部分派上用場的時候。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-143">Enter the `transfer` part of `transfer learning`.</span></span> <span data-ttu-id="7f5fe-144">您可以將 `Inception model` 辨識及分類影像的能力遷移至您自訂影像分類器新的受限類別之中。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-144">You can transfer the `Inception model`'s ability to recognize and classify images to the new limited categories of your custom image classifier.</span></span>

* <span data-ttu-id="7f5fe-145">Food (食物)</span><span class="sxs-lookup"><span data-stu-id="7f5fe-145">Food</span></span>
* <span data-ttu-id="7f5fe-146">Toy (玩具)</span><span class="sxs-lookup"><span data-stu-id="7f5fe-146">Toy</span></span>
* <span data-ttu-id="7f5fe-147">Appliance (設備)</span><span class="sxs-lookup"><span data-stu-id="7f5fe-147">Appliance</span></span>

<span data-ttu-id="7f5fe-148">This tutorial uses the TensorFlow [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) deep learning model, a popular image recognition model trained on the `ImageNet` dataset.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-148">This tutorial uses the TensorFlow [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) deep learning model, a popular image recognition model trained on the `ImageNet` dataset.</span></span> <span data-ttu-id="7f5fe-149">The TensorFlow model classifies entire images into a thousand classes, such as “Umbrella”, “Jersey”, and “Dishwasher”.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-149">The TensorFlow model classifies entire images into a thousand classes, such as “Umbrella”, “Jersey”, and “Dishwasher”.</span></span>

<span data-ttu-id="7f5fe-150">Because the `Inception model` has already been pre trained on thousands of different images, internally it contains the [image features](https://en.wikipedia.org/wiki/Feature_(computer_vision)) needed for image identification.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-150">Because the `Inception model` has already been pre trained on thousands of different images, internally it contains the [image features](https://en.wikipedia.org/wiki/Feature_(computer_vision)) needed for image identification.</span></span> <span data-ttu-id="7f5fe-151">We can make use of these internal image features in the model to train a new model with far fewer classes.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-151">We can make use of these internal image features in the model to train a new model with far fewer classes.</span></span>

<span data-ttu-id="7f5fe-152">如下圖所示，您會在 .NET Core 或 .NET Framework 應用程式中新增對 ML.NET NuGet 套件的參考。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-152">As shown in the following diagram, you add a reference to the ML.NET NuGet packages in your .NET Core or .NET Framework applications.</span></span> <span data-ttu-id="7f5fe-153">Under the covers, ML.NET includes and references the native `TensorFlow` library that allows you to write code that loads an existing trained `TensorFlow` model file.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-153">Under the covers, ML.NET includes and references the native `TensorFlow` library that allows you to write code that loads an existing trained `TensorFlow` model file.</span></span>

![TensorFlow 轉換 ML.NET 架構圖表](./media/image-classification/tensorflow-mlnet.png)

### <a name="multiclass-classification"></a><span data-ttu-id="7f5fe-155">多元分類</span><span class="sxs-lookup"><span data-stu-id="7f5fe-155">Multiclass classification</span></span>

<span data-ttu-id="7f5fe-156">After using the TensorFlow inception model to extract features suitable as input for a classical machine learning algorithm, we add an ML.NET [multi-class classifier](../resources/tasks.md#multiclass-classification).</span><span class="sxs-lookup"><span data-stu-id="7f5fe-156">After using the TensorFlow inception model to extract features suitable as input for a classical machine learning algorithm, we add an ML.NET [multi-class classifier](../resources/tasks.md#multiclass-classification).</span></span>

<span data-ttu-id="7f5fe-157">The specific trainer used in this case is the [multinomial logistic regression algorithm](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).</span><span class="sxs-lookup"><span data-stu-id="7f5fe-157">The specific trainer used in this case is the [multinomial logistic regression algorithm](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).</span></span>

<span data-ttu-id="7f5fe-158">The algorithm implemented by this trainer performs well on problems with a large number of features, which is the case for a deep learning model operating on image data.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-158">The algorithm implemented by this trainer performs well on problems with a large number of features, which is the case for a deep learning model operating on image data.</span></span>

### <a name="data"></a><span data-ttu-id="7f5fe-159">資料</span><span class="sxs-lookup"><span data-stu-id="7f5fe-159">Data</span></span>

<span data-ttu-id="7f5fe-160">有兩個資料來源：`.tsv` 檔案，以及影像檔案。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-160">There are two data sources: the `.tsv` file, and the image files.</span></span>  <span data-ttu-id="7f5fe-161">`tags.tsv` 檔案包含兩個資料行：第一個會被定義為 `ImagePath`，而第二個則是對應至影像的 `Label`。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-161">The `tags.tsv` file contains two columns: the first one is defined as `ImagePath` and the second one is the `Label` corresponding to the image.</span></span> <span data-ttu-id="7f5fe-162">下列範例檔案沒有標頭資料列，且看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="7f5fe-162">The following example file doesn't have a header row, and looks like this:</span></span>

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

<span data-ttu-id="7f5fe-163">定型及測試影像都位於您將以 zip 檔案下載的資產資料夾中。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-163">The training and testing images are located in the assets folders that you'll download in a zip file.</span></span> <span data-ttu-id="7f5fe-164">這些影像皆由 Wikimedia Commons 所有。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-164">These images belong to Wikimedia Commons.</span></span>
> <span data-ttu-id="7f5fe-165">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208) \(英文\), the free media repository*。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-165">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), the free media repository.*</span></span> <span data-ttu-id="7f5fe-166">Retrieved 10:48, October 17, 2018 from: https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toaster https://commons.wikimedia.org/wiki/Teddy_bear</span><span class="sxs-lookup"><span data-stu-id="7f5fe-166">Retrieved 10:48, October 17, 2018 from: https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toaster https://commons.wikimedia.org/wiki/Teddy_bear</span></span>

## <a name="setup"></a><span data-ttu-id="7f5fe-167">安裝程式</span><span class="sxs-lookup"><span data-stu-id="7f5fe-167">Setup</span></span>

### <a name="create-a-project"></a><span data-ttu-id="7f5fe-168">建立專案</span><span class="sxs-lookup"><span data-stu-id="7f5fe-168">Create a project</span></span>

1. <span data-ttu-id="7f5fe-169">建立稱為 "TransferLearningTF" 的 **.NET Core 主控台應用程式**。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-169">Create a **.NET Core Console Application** called "TransferLearningTF".</span></span>

1. <span data-ttu-id="7f5fe-170">安裝「Microsoft.ML NuGet 套件」：</span><span class="sxs-lookup"><span data-stu-id="7f5fe-170">Install the **Microsoft.ML NuGet Package**:</span></span>

    * <span data-ttu-id="7f5fe-171">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-171">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    * <span data-ttu-id="7f5fe-172">選擇 [nuget.org] 作為 [套件來源]，選取 [瀏覽] 索引標籤，搜尋 **Microsoft.ML**。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-172">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span>
    * <span data-ttu-id="7f5fe-173">Click on the **Version** drop-down, select the **1.4.0** package in the list, and select the **Install** button.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-173">Click on the **Version** drop-down, select the **1.4.0** package in the list, and select the **Install** button.</span></span>
    * <span data-ttu-id="7f5fe-174">Select the **OK** button on the **Preview Changes** dialog.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-174">Select the **OK** button on the **Preview Changes** dialog.</span></span>
    * <span data-ttu-id="7f5fe-175">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-175">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    * <span data-ttu-id="7f5fe-176">Repeat these steps for **Microsoft.ML.ImageAnalytics v1.4.0**, **SciSharp.TensorFlow.Redist v1.15.0** and **Microsoft.ML.TensorFlow v1.4.0**.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-176">Repeat these steps for **Microsoft.ML.ImageAnalytics v1.4.0**, **SciSharp.TensorFlow.Redist v1.15.0** and **Microsoft.ML.TensorFlow v1.4.0**.</span></span>

### <a name="download-assets"></a><span data-ttu-id="7f5fe-177">Download assets</span><span class="sxs-lookup"><span data-stu-id="7f5fe-177">Download assets</span></span>

1. <span data-ttu-id="7f5fe-178">下載[專案資產目錄 zip 檔案](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)，然後將它解壓縮。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-178">Download [The project assets directory zip file](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip), and unzip.</span></span>

1. <span data-ttu-id="7f5fe-179">將 `assets` 目錄複製到您的 *TransferLearningTF* 專案目錄中。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-179">Copy the `assets` directory into your *TransferLearningTF* project directory.</span></span> <span data-ttu-id="7f5fe-180">此目錄及其子目錄包含本教學課程所需的資料和支援檔案 (Inception model 除外，您將會在下個步驟中下載並新增它)。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-180">This directory and its subdirectories contain the data and support files (except for the Inception model, which you'll download and add in the next step) needed for this tutorial.</span></span>

1. <span data-ttu-id="7f5fe-181">下載 [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)，然後將它解壓縮。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-181">Download the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), and unzip.</span></span>

1. <span data-ttu-id="7f5fe-182">將剛才解壓縮的 `inception5h` 目錄的內容複製到您 *TransferLearningTF* 專案的 `assets/inception` 目錄中。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-182">Copy the contents of the `inception5h` directory just unzipped into your *TransferLearningTF* project `assets/inception` directory.</span></span> <span data-ttu-id="7f5fe-183">此目錄包含本教學課程所需的模型和其他支援檔案，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="7f5fe-183">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![Inception 目錄內容](./media/image-classification/inception-files.png)

1. <span data-ttu-id="7f5fe-185">在 [方案總管] 中，以滑鼠右鍵按一下資產目錄及子目錄中的每個檔案，然後選取 [內容]。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-185">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="7f5fe-186">在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-186">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="7f5fe-187">建立類別及定義路徑</span><span class="sxs-lookup"><span data-stu-id="7f5fe-187">Create classes and define paths</span></span>

1. <span data-ttu-id="7f5fe-188">在 *Program.cs* 檔案頂端新增下列額外的 `using` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="7f5fe-188">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

1. <span data-ttu-id="7f5fe-189">Add the following code to the line right above the `Main` method to specify the asset paths:</span><span class="sxs-lookup"><span data-stu-id="7f5fe-189">Add the following code to the line right above the `Main` method to specify the asset paths:</span></span>

    [!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

1. <span data-ttu-id="7f5fe-190">Create classes for your input data, and predictions.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-190">Create classes for your input data, and predictions.</span></span>

    [!code-csharp[DeclareImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareImageData)]

    <span data-ttu-id="7f5fe-191">`ImageData` 是輸入資料集類別，並具有下列 <xref:System.String> 欄位：</span><span class="sxs-lookup"><span data-stu-id="7f5fe-191">`ImageData` is the input image data class and has the following <xref:System.String> fields:</span></span>

    * <span data-ttu-id="7f5fe-192">`ImagePath` 包含影像檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-192">`ImagePath` contains the image file name.</span></span>
    * <span data-ttu-id="7f5fe-193">`Label` 包含影像標籤的值。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-193">`Label` contains a value for the image label.</span></span>

1. <span data-ttu-id="7f5fe-194">將新類別新增至 `ImagePrediction` 的專案：</span><span class="sxs-lookup"><span data-stu-id="7f5fe-194">Add a new class to your project for `ImagePrediction`:</span></span>

    [!code-csharp[DeclareImagePrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareImagePrediction)]

    <span data-ttu-id="7f5fe-195">`ImagePrediction` 是影像預測類別，並具有下列欄位：</span><span class="sxs-lookup"><span data-stu-id="7f5fe-195">`ImagePrediction` is the image prediction class and has the following fields:</span></span>

    * <span data-ttu-id="7f5fe-196">`Score` 包含指定影像分類的信賴百分比。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-196">`Score` contains the confidence percentage for a given image classification.</span></span>
    * <span data-ttu-id="7f5fe-197">`PredictedLabelValue` 包含已預測影像分類標籤的值。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-197">`PredictedLabelValue` contains a value for the predicted image classification label.</span></span>

    <span data-ttu-id="7f5fe-198">`ImagePrediction` 是在模型定型後，用來進行預測的類別。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-198">`ImagePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="7f5fe-199">它具有影像路徑的 `string` (`ImagePath`)。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-199">It has a `string` (`ImagePath`) for the image path.</span></span> <span data-ttu-id="7f5fe-200">The `Label` is used to reuse and train the model.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-200">The `Label` is used to reuse and train the model.</span></span> <span data-ttu-id="7f5fe-201">`PredictedLabelValue` 的使用時機是在進行預測和評估的期間。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-201">The `PredictedLabelValue` is used during prediction and evaluation.</span></span> <span data-ttu-id="7f5fe-202">就評估而言，會使用含有定型資料、預設值及模型的輸入。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-202">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="7f5fe-203">在 Main 中初始化變數</span><span class="sxs-lookup"><span data-stu-id="7f5fe-203">Initialize variables in Main</span></span>

1. <span data-ttu-id="7f5fe-204">搭配 `MLContext` 的新執行個體來初始化 `mlContext` 變數。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-204">Initialize the `mlContext` variable with a new instance of `MLContext`.</span></span>  <span data-ttu-id="7f5fe-205">在 `Main` 方法中，以下列程式碼取代 `Console.WriteLine("Hello World!")`：</span><span class="sxs-lookup"><span data-stu-id="7f5fe-205">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

    [!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

    <span data-ttu-id="7f5fe-206">[MLContext 類別](xref:Microsoft.ML.MLContext)是所有 ML.NET 作業的起點，且初始化 `mlContext` 會建立新的 ML.NET 環境，其可在模型建立工作流程物件之間共用。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-206">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="7f5fe-207">就概念而言，類似於 Entity Framework 中的 `DBContext`。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-207">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="create-a-struct-for-inception-model-parameters"></a><span data-ttu-id="7f5fe-208">Create a struct for Inception model parameters</span><span class="sxs-lookup"><span data-stu-id="7f5fe-208">Create a struct for Inception model parameters</span></span>

1. <span data-ttu-id="7f5fe-209">The Inception model has several parameters you need to pass in.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-209">The Inception model has several parameters you need to pass in.</span></span> <span data-ttu-id="7f5fe-210">Create a struct to map the parameter values to friendly names with the following code, just after the `Main()` method:</span><span class="sxs-lookup"><span data-stu-id="7f5fe-210">Create a struct to map the parameter values to friendly names with the following code, just after the `Main()` method:</span></span>

    [!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a><span data-ttu-id="7f5fe-211">建立顯示公用程式方法</span><span class="sxs-lookup"><span data-stu-id="7f5fe-211">Create a display utility method</span></span>

<span data-ttu-id="7f5fe-212">因為您將會不只一次顯示影像資料和相關預測，所以請建立顯示公用程式方法來處理顯示影像和預測結果。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-212">Since you'll display the image data and the related predictions more than once, create a display utility method to handle displaying the image and prediction results.</span></span>

1. <span data-ttu-id="7f5fe-213">使用下列程式碼，在緊接著 `InceptionSettings` 結構之後，建立 `DisplayResults()` 方法：</span><span class="sxs-lookup"><span data-stu-id="7f5fe-213">Create the `DisplayResults()` method, just after the `InceptionSettings` struct, using the following code:</span></span>

    ```csharp
    private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
    {

    }
    ```

1. <span data-ttu-id="7f5fe-214">Fill in the body of the `DisplayResults` method:</span><span class="sxs-lookup"><span data-stu-id="7f5fe-214">Fill in the body of the `DisplayResults` method:</span></span>

    [!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

### <a name="create-a-tsv-file-utility-method"></a><span data-ttu-id="7f5fe-215">建立 .tsv 檔案公用程式方法</span><span class="sxs-lookup"><span data-stu-id="7f5fe-215">Create a .tsv file utility method</span></span>

1. <span data-ttu-id="7f5fe-216">請使用下列程式碼，在緊接著 `DisplayResults()` 方法之後，建立 `ReadFromTsv()` 方法：</span><span class="sxs-lookup"><span data-stu-id="7f5fe-216">Create the `ReadFromTsv()` method, just after the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
    {

    }
    ```

1. <span data-ttu-id="7f5fe-217">Fill in the body of the `ReadFromTsv` method:</span><span class="sxs-lookup"><span data-stu-id="7f5fe-217">Fill in the body of the `ReadFromTsv` method:</span></span>

    [!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]

    <span data-ttu-id="7f5fe-218">The code parses through the `tags.tsv` file to add the file path to the image file name for the `ImagePath` property and load it and the `Label` into an `ImageData` object.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-218">The code parses through the `tags.tsv` file to add the file path to the image file name for the `ImagePath` property and load it and the `Label` into an `ImageData` object.</span></span>

### <a name="create-a-method-to-make-a-prediction"></a><span data-ttu-id="7f5fe-219">Create a method to make a prediction</span><span class="sxs-lookup"><span data-stu-id="7f5fe-219">Create a method to make a prediction</span></span>

1. <span data-ttu-id="7f5fe-220">請使用下列程式碼，緊接在 `DisplayResults()` 方法之前，建立 `ClassifySingleImage()` 方法：</span><span class="sxs-lookup"><span data-stu-id="7f5fe-220">Create the `ClassifySingleImage()` method, just before the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. <span data-ttu-id="7f5fe-221">Create an `ImageData` object that contains the fully qualified path and image file name for the single `ImagePath`.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-221">Create an `ImageData` object that contains the fully qualified path and image file name for the single `ImagePath`.</span></span> <span data-ttu-id="7f5fe-222">將下列程式碼新增為 `ClassifySingleImage()` 方法中的下一行：</span><span class="sxs-lookup"><span data-stu-id="7f5fe-222">Add the following code as the next  lines in the `ClassifySingleImage()` method:</span></span>

    [!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

1. <span data-ttu-id="7f5fe-223">Make a single prediction, by adding the following code as the next line in the `ClassifySingleImage` method:</span><span class="sxs-lookup"><span data-stu-id="7f5fe-223">Make a single prediction, by adding the following code as the next line in the `ClassifySingleImage` method:</span></span>

    [!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

    <span data-ttu-id="7f5fe-224">To get the prediction, use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) method.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-224">To get the prediction, use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) method.</span></span> <span data-ttu-id="7f5fe-225">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-225">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="7f5fe-226">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) 不是安全執行緒。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-226">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="7f5fe-227">It's acceptable to use in single-threaded or prototype environments.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-227">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="7f5fe-228">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-228">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="7f5fe-229">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="7f5fe-229">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="7f5fe-230">`PredictionEnginePool` 服務延伸模組目前處於預覽狀態。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-230">`PredictionEnginePool` service extension is currently in preview.</span></span>

1. <span data-ttu-id="7f5fe-231">將預測結果顯示為 `ClassifySingleImage()` 方法中的下一行程式碼：</span><span class="sxs-lookup"><span data-stu-id="7f5fe-231">Display the prediction result as the next line of code in the `ClassifySingleImage()` method:</span></span>

   [!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="construct-the-mlnet-model-pipeline"></a><span data-ttu-id="7f5fe-232">Construct the ML.NET model pipeline</span><span class="sxs-lookup"><span data-stu-id="7f5fe-232">Construct the ML.NET model pipeline</span></span>

<span data-ttu-id="7f5fe-233">An ML.NET model pipeline is a chain of estimators.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-233">An ML.NET model pipeline is a chain of estimators.</span></span> <span data-ttu-id="7f5fe-234">Note that no execution happens during pipeline construction.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-234">Note that no execution happens during pipeline construction.</span></span> <span data-ttu-id="7f5fe-235">The estimator objects are created but not executed.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-235">The estimator objects are created but not executed.</span></span>

1. <span data-ttu-id="7f5fe-236">Add a method to generate the model</span><span class="sxs-lookup"><span data-stu-id="7f5fe-236">Add a method to generate the model</span></span>

    <span data-ttu-id="7f5fe-237">This method is the heart of the tutorial.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-237">This method is the heart of the tutorial.</span></span> <span data-ttu-id="7f5fe-238">It creates a pipeline for the model, and trains the pipeline to produce the ML.NET model.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-238">It creates a pipeline for the model, and trains the pipeline to produce the ML.NET model.</span></span> <span data-ttu-id="7f5fe-239">It also evaluates the model against some previously unseen test data.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-239">It also evaluates the model against some previously unseen test data.</span></span>

    <span data-ttu-id="7f5fe-240">使用下列程式碼，緊接在 `InceptionSettings` 結構之後及 `DisplayResults()` 方法之前，建立 `GenerateModel()` 方法：</span><span class="sxs-lookup"><span data-stu-id="7f5fe-240">Create the `GenerateModel()` method, just after the `InceptionSettings` struct and just before the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer GenerateModel(MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="7f5fe-241">Add the estimators to load, resize and extract the pixels from the image data:</span><span class="sxs-lookup"><span data-stu-id="7f5fe-241">Add the estimators to load, resize and extract the pixels from the image data:</span></span>

    [!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

    <span data-ttu-id="7f5fe-242">The image data needs to be processed into the format that the TensorFlow model expects.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-242">The image data needs to be processed into the format that the TensorFlow model expects.</span></span> <span data-ttu-id="7f5fe-243">In this case, the images are loaded into memory, resized to a consistent size, and the pixels are extracted into a numeric vector.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-243">In this case, the images are loaded into memory, resized to a consistent size, and the pixels are extracted into a numeric vector.</span></span>

1. <span data-ttu-id="7f5fe-244">Add the estimator to load the TensorFlow model, and score it:</span><span class="sxs-lookup"><span data-stu-id="7f5fe-244">Add the estimator to load the TensorFlow model, and score it:</span></span>

    [!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

    <span data-ttu-id="7f5fe-245">This stage in the pipeline loads the TensorFlow model into memory, then processes the vector of pixel values through the TensorFlow model network.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-245">This stage in the pipeline loads the TensorFlow model into memory, then processes the vector of pixel values through the TensorFlow model network.</span></span> <span data-ttu-id="7f5fe-246">Applying inputs to a deep learning model, and generating an output using the model, is referred to as **Scoring**.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-246">Applying inputs to a deep learning model, and generating an output using the model, is referred to as **Scoring**.</span></span> <span data-ttu-id="7f5fe-247">When using the model in its entirety, scoring makes an inference, or prediction.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-247">When using the model in its entirety, scoring makes an inference, or prediction.</span></span>

    <span data-ttu-id="7f5fe-248">In this case, you use all of the TensorFlow model except the last layer, which is the layer that makes the inference.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-248">In this case, you use all of the TensorFlow model except the last layer, which is the layer that makes the inference.</span></span> <span data-ttu-id="7f5fe-249">The output of the penultimate layer is labeled `softmax_2_preactivation`.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-249">The output of the penultimate layer is labeled `softmax_2_preactivation`.</span></span> <span data-ttu-id="7f5fe-250">The output of this layer is effectively a vector of features that characterize the original input images.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-250">The output of this layer is effectively a vector of features that characterize the original input images.</span></span>

    <span data-ttu-id="7f5fe-251">This feature vector generated by the TensorFlow model will be used as input to an ML.NET training algorithm.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-251">This feature vector generated by the TensorFlow model will be used as input to an ML.NET training algorithm.</span></span>

1. <span data-ttu-id="7f5fe-252">Add the estimator to map the string labels in the training data to integer key values:</span><span class="sxs-lookup"><span data-stu-id="7f5fe-252">Add the estimator to map the string labels in the training data to integer key values:</span></span>

    [!code-csharp[MapValueToKey](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey)]

    <span data-ttu-id="7f5fe-253">The ML.NET trainer that is appended next requires its labels to be in `key` format rather than arbitrary strings.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-253">The ML.NET trainer that is appended next requires its labels to be in `key` format rather than arbitrary strings.</span></span> <span data-ttu-id="7f5fe-254">A key is a number that has a one to one mapping to a string value.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-254">A key is a number that has a one to one mapping to a string value.</span></span>

1. <span data-ttu-id="7f5fe-255">Add the ML.NET training algorithm:</span><span class="sxs-lookup"><span data-stu-id="7f5fe-255">Add the ML.NET training algorithm:</span></span>

    [!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

1. <span data-ttu-id="7f5fe-256">Add the estimator to map the predicted key value back into a string:</span><span class="sxs-lookup"><span data-stu-id="7f5fe-256">Add the estimator to map the predicted key value back into a string:</span></span>

    [!code-csharp[MapKeyToValue](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapKeyToValue)]

## <a name="train-the-model"></a><span data-ttu-id="7f5fe-257">將模型定型</span><span class="sxs-lookup"><span data-stu-id="7f5fe-257">Train the model</span></span>

1. <span data-ttu-id="7f5fe-258">Load the training data using the [LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) wrapper.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-258">Load the training data using the [LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) wrapper.</span></span> <span data-ttu-id="7f5fe-259">將下列程式碼加入為 `GenerateModel()` 方法中的下一行：</span><span class="sxs-lookup"><span data-stu-id="7f5fe-259">Add the following code as the next line in the `GenerateModel()` method:</span></span>

    [!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

    <span data-ttu-id="7f5fe-260">ML.NET 中的資料以 [IDataView 類別](xref:Microsoft.ML.IDataView) 表示。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-260">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="7f5fe-261">`IDataView` 是彈性且有效率的表格式資料描述方式 (數值和文字)。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-261">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="7f5fe-262">資料可以從文字或即時 (例如 SQL 資料庫或記錄檔) 載入至 `IDataView` 物件。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-262">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

1. <span data-ttu-id="7f5fe-263">Train the model with the data loaded above:</span><span class="sxs-lookup"><span data-stu-id="7f5fe-263">Train the model with the data loaded above:</span></span>

    [!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

    <span data-ttu-id="7f5fe-264">The `Fit()` method trains your model by applying the training dataset to the pipeline.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-264">The `Fit()` method trains your model by applying the training dataset to the pipeline.</span></span>

## <a name="evaluate-the-accuracy-of-the-model"></a><span data-ttu-id="7f5fe-265">Evaluate the accuracy of the model</span><span class="sxs-lookup"><span data-stu-id="7f5fe-265">Evaluate the accuracy of the model</span></span>

1. <span data-ttu-id="7f5fe-266">Load and transform the test data, by adding the following code to the next line of the `GenerateModel` method:</span><span class="sxs-lookup"><span data-stu-id="7f5fe-266">Load and transform the test data, by adding the following code to the next line of the `GenerateModel` method:</span></span>

    [!code-csharp[LoadAndTransformTestData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadAndTransformTestData "Load and transform test data")]

    <span data-ttu-id="7f5fe-267">There are a few sample images that you can use to evaluate the model.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-267">There are a few sample images that you can use to evaluate the model.</span></span> <span data-ttu-id="7f5fe-268">Like the training data, these need to be loaded into an `IDataView`, so that they can be transformed by the model.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-268">Like the training data, these need to be loaded into an `IDataView`, so that they can be transformed by the model.</span></span>

1. <span data-ttu-id="7f5fe-269">Add the following code to the `GenerateModel()` method to evaluate the model:</span><span class="sxs-lookup"><span data-stu-id="7f5fe-269">Add the following code to the `GenerateModel()` method to evaluate the model:</span></span>

    [!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

    <span data-ttu-id="7f5fe-270">當您具有預測之後，請設定 [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) 方法：</span><span class="sxs-lookup"><span data-stu-id="7f5fe-270">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method:</span></span>

    * <span data-ttu-id="7f5fe-271">Assesses the model (compares the predicted values with the test dataset `labels`).</span><span class="sxs-lookup"><span data-stu-id="7f5fe-271">Assesses the model (compares the predicted values with the test dataset `labels`).</span></span>
    * <span data-ttu-id="7f5fe-272">傳回模型效能計量。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-272">Returns the model performance metrics.</span></span>

1. <span data-ttu-id="7f5fe-273">Display the model accuracy metrics</span><span class="sxs-lookup"><span data-stu-id="7f5fe-273">Display the model accuracy metrics</span></span>

    <span data-ttu-id="7f5fe-274">使用下列程式碼來顯示計量、共用結果，然後依結果採取動作：</span><span class="sxs-lookup"><span data-stu-id="7f5fe-274">Use the following code to display the metrics, share the results, and then act on them:</span></span>

    [!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

    <span data-ttu-id="7f5fe-275">下列計量會針對影像分類進行評估：</span><span class="sxs-lookup"><span data-stu-id="7f5fe-275">The following metrics are evaluated for image classification:</span></span>

    * <span data-ttu-id="7f5fe-276">`Log-loss`：請參閱[記錄檔遺失](../resources/glossary.md#log-loss)。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-276">`Log-loss` - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="7f5fe-277">建議讓記錄檔遺失盡量接近零。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-277">You want Log-loss to be as close to zero as possible.</span></span>
    * <span data-ttu-id="7f5fe-278">`Per class Log-loss`</span><span class="sxs-lookup"><span data-stu-id="7f5fe-278">`Per class Log-loss`.</span></span> <span data-ttu-id="7f5fe-279">建議讓每個類別的記錄檔遺失盡量接近零。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-279">You want per class Log-loss to be as close to zero as possible.</span></span>

1. <span data-ttu-id="7f5fe-280">新增下列程式碼來將定型後的模型作為下一行傳回：</span><span class="sxs-lookup"><span data-stu-id="7f5fe-280">Add the following code to return the trained model as the next line:</span></span>

    [!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReturnModel)]

## <a name="run-the-application"></a><span data-ttu-id="7f5fe-281">Run the application!</span><span class="sxs-lookup"><span data-stu-id="7f5fe-281">Run the application!</span></span>

1. <span data-ttu-id="7f5fe-282">Add the call to `GenerateModel` in the `Main` method after the creation of the MLContext class:</span><span class="sxs-lookup"><span data-stu-id="7f5fe-282">Add the call to `GenerateModel` in the `Main` method after the creation of the MLContext class:</span></span>

    [!code-csharp[CallGenerateModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallGenerateModel)]

1. <span data-ttu-id="7f5fe-283">Add the call to the `ClassifySingleImage()` method as the next line of code in the `Main` method:</span><span class="sxs-lookup"><span data-stu-id="7f5fe-283">Add the call to the `ClassifySingleImage()` method as the next line of code in the `Main` method:</span></span>

    [!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

1. <span data-ttu-id="7f5fe-284">Run your console app (Ctrl + F5).</span><span class="sxs-lookup"><span data-stu-id="7f5fe-284">Run your console app (Ctrl + F5).</span></span> <span data-ttu-id="7f5fe-285">您的結果應該與下列輸出類似。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-285">Your results should be similar to the following output.</span></span>  <span data-ttu-id="7f5fe-286">您可能會看到警告或處理中訊息，但為了讓結果變得清楚，這些訊息已從下列結果中移除。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-286">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

    ```console
    =============== Training classification model ===============
    Image: broccoli2.jpg predicted as: food with score: 0.8955513
    Image: pizza3.jpg predicted as: food with score: 0.9667718
    Image: teddy6.jpg predicted as: toy with score: 0.9797683
    =============== Classification metrics ===============
    LogLoss is: 0.0653774699265059
    PerClassLogLoss is: 0.110315812569315 , 0.0204391272836966 , 0
    =============== Making single image classification ===============
    Image: toaster3.jpg predicted as: appliance with score: 0.9646884
    ```

<span data-ttu-id="7f5fe-287">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="7f5fe-287">Congratulations!</span></span> <span data-ttu-id="7f5fe-288">You've now successfully built a machine learning model for image classification by applying transfer learning to a `TensorFlow` model in ML.NET.</span><span class="sxs-lookup"><span data-stu-id="7f5fe-288">You've now successfully built a machine learning model for image classification by applying transfer learning to a `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="7f5fe-289">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-289">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span>

<span data-ttu-id="7f5fe-290">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="7f5fe-290">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="7f5fe-291">了解問題</span><span class="sxs-lookup"><span data-stu-id="7f5fe-291">Understand the problem</span></span>
> * <span data-ttu-id="7f5fe-292">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span><span class="sxs-lookup"><span data-stu-id="7f5fe-292">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span></span>
> * <span data-ttu-id="7f5fe-293">Train and evaluate the ML.NET model</span><span class="sxs-lookup"><span data-stu-id="7f5fe-293">Train and evaluate the ML.NET model</span></span>
> * <span data-ttu-id="7f5fe-294">Classify a test image</span><span class="sxs-lookup"><span data-stu-id="7f5fe-294">Classify a test image</span></span>

<span data-ttu-id="7f5fe-295">請查看機器學習範例 GitHub 存放庫，以探索更複雜的影像分類範例。</span><span class="sxs-lookup"><span data-stu-id="7f5fe-295">Check out the Machine Learning samples GitHub repository to explore an expanded image classification sample.</span></span>
> [!div class="nextstepaction"]
> <span data-ttu-id="7f5fe-296">[dotnet/machinelearning-samples GitHub 存放庫](https://github.com/dotnet/machinelearning-samples/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="7f5fe-296">[dotnet/machinelearning-samples GitHub repository](https://github.com/dotnet/machinelearning-samples/)</span></span>
