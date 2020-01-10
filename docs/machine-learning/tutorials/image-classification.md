---
title: 教學課程：從預先定型的 TensorFlow 模型產生 ML.NET 影像分類模型
description: 瞭解如何將現有 TensorFlow 模型的知識，轉移到新的 ML.NET 影像分類模型。 TensorFlow 模型已定型，可將影像分類為一千個類別。 ML.NET 模型利用轉移學習，將影像分類成較少的類別。
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: 5fe47c42d0cf24ebfdc33a937e1afbd11a976680
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2020
ms.locfileid: "75738960"
---
# <a name="tutorial-generate-an-mlnet-image-classification-model-from-a-pre-trained-tensorflow-model"></a><span data-ttu-id="9431c-105">教學課程：從預先定型的 TensorFlow 模型產生 ML.NET 影像分類模型</span><span class="sxs-lookup"><span data-stu-id="9431c-105">Tutorial: Generate an ML.NET image classification model from a pre-trained TensorFlow model</span></span>

<span data-ttu-id="9431c-106">瞭解如何將現有 TensorFlow 模型的知識，轉移到新的 ML.NET 影像分類模型。</span><span class="sxs-lookup"><span data-stu-id="9431c-106">Learn how to transfer the knowledge from an existing TensorFlow model into a new ML.NET image classification model.</span></span>

<span data-ttu-id="9431c-107">TensorFlow 模型已定型，可將影像分類為一千個類別。</span><span class="sxs-lookup"><span data-stu-id="9431c-107">The TensorFlow model was trained to classify images into a thousand categories.</span></span> <span data-ttu-id="9431c-108">ML.NET 模型會在其管線中使用部分的 TensorFlow 模型來定型模型，以將影像分類成3個類別。</span><span class="sxs-lookup"><span data-stu-id="9431c-108">The ML.NET model makes use of part of the TensorFlow model in its pipeline to train a model to classify images into 3 categories.</span></span>

<span data-ttu-id="9431c-109">若要從頭對[影像分類](https://en.wikipedia.org/wiki/Outline_of_object_recognition) \(英文\) 模型進行定型，將會需要設定數以百萬計的參數、眾多已標籤的定型資料，以及大量的計算資源 (數以百計的 GPU 小時)。</span><span class="sxs-lookup"><span data-stu-id="9431c-109">Training an [Image Classification](https://en.wikipedia.org/wiki/Outline_of_object_recognition) model from scratch requires setting millions of parameters, a ton of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="9431c-110">遷移學習的效能雖然不如從頭對自訂模型進行定型來得有效，但它能讓您透過僅需處理數以千計的影像 (而非數以百萬計的已標籤影像) 來縮短此程序，並以較為快速的方式建置自訂模型 (在不具備 GPU 的電腦上於一小時內便能完成)。</span><span class="sxs-lookup"><span data-stu-id="9431c-110">While not as effective as training a custom model from scratch, transfer learning allows you to shortcut this process by working with thousands of images vs. millions of labeled images and build a customized model fairly quickly (within an hour on a machine without a GPU).</span></span> <span data-ttu-id="9431c-111">本教學課程會更進一步調整該程式，只使用數十個訓練影像。</span><span class="sxs-lookup"><span data-stu-id="9431c-111">This tutorial scales that process down even further, using only a dozen training images.</span></span>

<span data-ttu-id="9431c-112">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="9431c-112">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="9431c-113">了解問題</span><span class="sxs-lookup"><span data-stu-id="9431c-113">Understand the problem</span></span>
> * <span data-ttu-id="9431c-114">將預先定型的 TensorFlow 模型納入 ML.NET 管線中</span><span class="sxs-lookup"><span data-stu-id="9431c-114">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span></span>
> * <span data-ttu-id="9431c-115">定型和評估 ML.NET 模型</span><span class="sxs-lookup"><span data-stu-id="9431c-115">Train and evaluate the ML.NET model</span></span>
> * <span data-ttu-id="9431c-116">分類測試影像</span><span class="sxs-lookup"><span data-stu-id="9431c-116">Classify a test image</span></span>

<span data-ttu-id="9431c-117">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="9431c-117">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span> <span data-ttu-id="9431c-118">請注意，根據預設，本教學課程的 .NET 專案組態以 .NET Core 2.2 為目標。</span><span class="sxs-lookup"><span data-stu-id="9431c-118">Note that by default, the .NET project configuration for this tutorial targets .NET core 2.2.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="9431c-119">什麼是傳輸學習？</span><span class="sxs-lookup"><span data-stu-id="9431c-119">What is transfer learning?</span></span>

<span data-ttu-id="9431c-120">轉移學習是在解決一個問題，並將其套用至不同但相關的問題時，使用所獲得知識的過程。</span><span class="sxs-lookup"><span data-stu-id="9431c-120">Transfer learning is the process of using knowledge gained while solving one problem and applying it to a different but related problem.</span></span>

<span data-ttu-id="9431c-121">在本教學課程中，您會使用已定型的部分 TensorFlow 模型，將影像分類成一千個類別-在 ML.NET 模型中，將影像分類成3個類別。</span><span class="sxs-lookup"><span data-stu-id="9431c-121">For this tutorial, you use part of a TensorFlow model - trained to classify images into a thousand categories - in an ML.NET model that classifies images into 3 categories.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9431c-122">必要條件：</span><span class="sxs-lookup"><span data-stu-id="9431c-122">Prerequisites</span></span>

* <span data-ttu-id="9431c-123">已安裝「.NET Core 跨平臺開發」工作負載的[Visual Studio 2017 15.6 版或更新](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)版本。</span><span class="sxs-lookup"><span data-stu-id="9431c-123">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
* [<span data-ttu-id="9431c-124">教學課程資產目錄 .ZIP 檔案</span><span class="sxs-lookup"><span data-stu-id="9431c-124">The tutorial assets directory .ZIP file</span></span>](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)
* [<span data-ttu-id="9431c-125">InceptionV1 機器學習模型</span><span class="sxs-lookup"><span data-stu-id="9431c-125">The InceptionV1 machine learning model</span></span>](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-right-machine-learning-task"></a><span data-ttu-id="9431c-126">選取適當的機器學習工作</span><span class="sxs-lookup"><span data-stu-id="9431c-126">Select the right machine learning task</span></span>

### <a name="deep-learning"></a><span data-ttu-id="9431c-127">深度學習</span><span class="sxs-lookup"><span data-stu-id="9431c-127">Deep learning</span></span>

<span data-ttu-id="9431c-128">[深度學習](https://en.wikipedia.org/wiki/Deep_learning)是機器學習的子集，其正為電腦視覺及語音辨識等領域帶來革命性的影響。</span><span class="sxs-lookup"><span data-stu-id="9431c-128">[Deep learning](https://en.wikipedia.org/wiki/Deep_learning) is a subset of Machine Learning, which is revolutionizing areas like Computer Vision and Speech Recognition.</span></span>

<span data-ttu-id="9431c-129">深度學習模型是使用包含多個學習層級的大量[已標籤資料](https://en.wikipedia.org/wiki/Labeled_data) \(英文\) 及[神經網路](https://en.wikipedia.org/wiki/Artificial_neural_network)來定型的。</span><span class="sxs-lookup"><span data-stu-id="9431c-129">Deep learning models are trained by using large sets of [labeled data](https://en.wikipedia.org/wiki/Labeled_data) and [neural networks](https://en.wikipedia.org/wiki/Artificial_neural_network) that contain multiple learning layers.</span></span> <span data-ttu-id="9431c-130">深度學習：</span><span class="sxs-lookup"><span data-stu-id="9431c-130">Deep learning:</span></span>

* <span data-ttu-id="9431c-131">能在某些工作上產生較好的效能，例如電腦視覺。</span><span class="sxs-lookup"><span data-stu-id="9431c-131">Performs better on some tasks like Computer Vision.</span></span>
* <span data-ttu-id="9431c-132">需要大量的定型資料。</span><span class="sxs-lookup"><span data-stu-id="9431c-132">Requires huge amounts of training data.</span></span>

<span data-ttu-id="9431c-133">影像分類是常見的 Machine Learning 工作，可讓我們自動將影像分類為下列類別：</span><span class="sxs-lookup"><span data-stu-id="9431c-133">Image Classification is a common Machine Learning task that allows us to automatically classify images into categories such as:</span></span>

* <span data-ttu-id="9431c-134">是否能在影像中偵測到人類面孔。</span><span class="sxs-lookup"><span data-stu-id="9431c-134">Detecting a human face in an image or not.</span></span>
* <span data-ttu-id="9431c-135">偵測貓與狗。</span><span class="sxs-lookup"><span data-stu-id="9431c-135">Detecting cats vs. dogs.</span></span>

 <span data-ttu-id="9431c-136">或如下列影像所示，判斷影像是否為（n）食物、玩具或設備：</span><span class="sxs-lookup"><span data-stu-id="9431c-136">Or as in the following images, determining if an image is a(n)  food, toy, or appliance:</span></span>

<span data-ttu-id="9431c-137">![披薩影像](./media/image-classification/220px-Pepperoni_pizza.jpg)
![玩具熊影像](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![烤麵包機影像](./media/image-classification/193px-Broodrooster.jpg)</span><span class="sxs-lookup"><span data-stu-id="9431c-137">![pizza image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![teddy bear image](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toaster image](./media/image-classification/193px-Broodrooster.jpg)</span></span>

>[!Note]
> <span data-ttu-id="9431c-138">上述影像為 Wikimedia Commons 所有，並具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="9431c-138">The preceding images belong to Wikimedia Commons and are attributed as follows:</span></span>
>
> * <span data-ttu-id="9431c-139">"220px-Pepperoni_pizza.jpg" 公眾領域， https://commons.wikimedia.org/w/index.php?curid=79505 \(英文\)，</span><span class="sxs-lookup"><span data-stu-id="9431c-139">"220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,</span></span>
> * <span data-ttu-id="9431c-140">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" 攝影者：[Jonik](https://commons.wikimedia.org/wiki/User:Jonik) \(英文\) - 自行拍攝，CC BY-SA 2.0， https://commons.wikimedia.org/w/index.php?curid=48166 \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="9431c-140">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.</span></span>
> * <span data-ttu-id="9431c-141">"193px-Broodrooster.jpg" 攝影者：[M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) \(英文\) - 自行創作，CC BY-SA 3.0， https://commons.wikimedia.org/w/index.php?curid=27403 \(英文\)</span><span class="sxs-lookup"><span data-stu-id="9431c-141">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403</span></span>

<span data-ttu-id="9431c-142">`Inception model` 經過訓練，可將影像分類為一千個類別，但在本教學課程中，您需要將影像分類為較小的類別集，而僅限於那些類別。</span><span class="sxs-lookup"><span data-stu-id="9431c-142">The `Inception model` is trained to classify images into a thousand categories, but for this tutorial, you need to classify images in a smaller category set, and only those categories.</span></span> <span data-ttu-id="9431c-143">這就是 `transfer learning` (遷移學習) 名稱中 `transfer` (遷移) 這部分派上用場的時候。</span><span class="sxs-lookup"><span data-stu-id="9431c-143">Enter the `transfer` part of `transfer learning`.</span></span> <span data-ttu-id="9431c-144">您可以將 `Inception model` 辨識及分類影像的能力遷移至您自訂影像分類器新的受限類別之中。</span><span class="sxs-lookup"><span data-stu-id="9431c-144">You can transfer the `Inception model`'s ability to recognize and classify images to the new limited categories of your custom image classifier.</span></span>

* <span data-ttu-id="9431c-145">Food (食物)</span><span class="sxs-lookup"><span data-stu-id="9431c-145">Food</span></span>
* <span data-ttu-id="9431c-146">Toy (玩具)</span><span class="sxs-lookup"><span data-stu-id="9431c-146">Toy</span></span>
* <span data-ttu-id="9431c-147">Appliance (設備)</span><span class="sxs-lookup"><span data-stu-id="9431c-147">Appliance</span></span>

<span data-ttu-id="9431c-148">本教學課程使用 TensorFlow[開始模型](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)深度學習模型，這是在 `ImageNet` 資料集上定型的熱門影像識別模型。</span><span class="sxs-lookup"><span data-stu-id="9431c-148">This tutorial uses the TensorFlow [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) deep learning model, a popular image recognition model trained on the `ImageNet` dataset.</span></span> <span data-ttu-id="9431c-149">TensorFlow 模型會將整個影像分類為一千個類別，例如 "傘"、"Jersey" 和 "洗碗機"。</span><span class="sxs-lookup"><span data-stu-id="9431c-149">The TensorFlow model classifies entire images into a thousand classes, such as “Umbrella”, “Jersey”, and “Dishwasher”.</span></span>

<span data-ttu-id="9431c-150">因為 `Inception model` 已在數千個不同的映射上預先定型，所以內部會包含影像識別所需的[影像功能](https://en.wikipedia.org/wiki/Feature_(computer_vision))。</span><span class="sxs-lookup"><span data-stu-id="9431c-150">Because the `Inception model` has already been pre trained on thousands of different images, internally it contains the [image features](https://en.wikipedia.org/wiki/Feature_(computer_vision)) needed for image identification.</span></span> <span data-ttu-id="9431c-151">我們可以利用模型中的這些內部影像功能，以更少的類別來定型新模型。</span><span class="sxs-lookup"><span data-stu-id="9431c-151">We can make use of these internal image features in the model to train a new model with far fewer classes.</span></span>

<span data-ttu-id="9431c-152">如下圖所示，您會在 .NET Core 或 .NET Framework 應用程式中新增對 ML.NET NuGet 套件的參考。</span><span class="sxs-lookup"><span data-stu-id="9431c-152">As shown in the following diagram, you add a reference to the ML.NET NuGet packages in your .NET Core or .NET Framework applications.</span></span> <span data-ttu-id="9431c-153">實際上，ML.NET 包含並參考原生 `TensorFlow` 程式庫，可讓您撰寫程式碼來載入現有已定型的 `TensorFlow` 模型檔案。</span><span class="sxs-lookup"><span data-stu-id="9431c-153">Under the covers, ML.NET includes and references the native `TensorFlow` library that allows you to write code that loads an existing trained `TensorFlow` model file.</span></span>

![TensorFlow 轉換 ML.NET 架構圖表](./media/image-classification/tensorflow-mlnet.png)

### <a name="multiclass-classification"></a><span data-ttu-id="9431c-155">多元分類</span><span class="sxs-lookup"><span data-stu-id="9431c-155">Multiclass classification</span></span>

<span data-ttu-id="9431c-156">在使用 TensorFlow 起始模型來解壓縮適用于傳統機器學習演算法輸入的功能之後，我們會新增一個 ML.NET 的[多類別分類器](../resources/tasks.md#multiclass-classification)。</span><span class="sxs-lookup"><span data-stu-id="9431c-156">After using the TensorFlow inception model to extract features suitable as input for a classical machine learning algorithm, we add an ML.NET [multi-class classifier](../resources/tasks.md#multiclass-classification).</span></span>

<span data-ttu-id="9431c-157">在此案例中使用的特定訓練員是[多維度羅吉斯回歸演算法](https://en.wikipedia.org/wiki/Multinomial_logistic_regression)。</span><span class="sxs-lookup"><span data-stu-id="9431c-157">The specific trainer used in this case is the [multinomial logistic regression algorithm](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).</span></span>

<span data-ttu-id="9431c-158">這個定型者所實行的演算法會在大量功能的問題上順利執行，這是在影像資料上操作的深度學習模型的情況。</span><span class="sxs-lookup"><span data-stu-id="9431c-158">The algorithm implemented by this trainer performs well on problems with a large number of features, which is the case for a deep learning model operating on image data.</span></span>

### <a name="data"></a><span data-ttu-id="9431c-159">Data</span><span class="sxs-lookup"><span data-stu-id="9431c-159">Data</span></span>

<span data-ttu-id="9431c-160">有兩個資料來源：`.tsv` 檔案，以及影像檔案。</span><span class="sxs-lookup"><span data-stu-id="9431c-160">There are two data sources: the `.tsv` file, and the image files.</span></span>  <span data-ttu-id="9431c-161">`tags.tsv` 檔案包含兩個資料行：第一個會被定義為 `ImagePath`，而第二個則是對應至影像的 `Label`。</span><span class="sxs-lookup"><span data-stu-id="9431c-161">The `tags.tsv` file contains two columns: the first one is defined as `ImagePath` and the second one is the `Label` corresponding to the image.</span></span> <span data-ttu-id="9431c-162">下列範例檔案沒有標頭資料列，且看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="9431c-162">The following example file doesn't have a header row, and looks like this:</span></span>

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

<span data-ttu-id="9431c-163">定型及測試影像都位於您將以 zip 檔案下載的資產資料夾中。</span><span class="sxs-lookup"><span data-stu-id="9431c-163">The training and testing images are located in the assets folders that you'll download in a zip file.</span></span> <span data-ttu-id="9431c-164">這些影像皆由 Wikimedia Commons 所有。</span><span class="sxs-lookup"><span data-stu-id="9431c-164">These images belong to Wikimedia Commons.</span></span>
> <span data-ttu-id="9431c-165">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208) \(英文\), the free media repository*。</span><span class="sxs-lookup"><span data-stu-id="9431c-165">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), the free media repository.*</span></span> <span data-ttu-id="9431c-166">從取得10:48 年10月 17 2018 日： https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toaster https://commons.wikimedia.org/wiki/Teddy_bear</span><span class="sxs-lookup"><span data-stu-id="9431c-166">Retrieved 10:48, October 17, 2018 from: https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toaster https://commons.wikimedia.org/wiki/Teddy_bear</span></span>

## <a name="setup"></a><span data-ttu-id="9431c-167">安裝程式</span><span class="sxs-lookup"><span data-stu-id="9431c-167">Setup</span></span>

### <a name="create-a-project"></a><span data-ttu-id="9431c-168">建立專案</span><span class="sxs-lookup"><span data-stu-id="9431c-168">Create a project</span></span>

1. <span data-ttu-id="9431c-169">建立稱為 "TransferLearningTF" 的 **.NET Core 主控台應用程式**。</span><span class="sxs-lookup"><span data-stu-id="9431c-169">Create a **.NET Core Console Application** called "TransferLearningTF".</span></span>

1. <span data-ttu-id="9431c-170">安裝「Microsoft.ML NuGet 套件」：</span><span class="sxs-lookup"><span data-stu-id="9431c-170">Install the **Microsoft.ML NuGet Package**:</span></span>

    * <span data-ttu-id="9431c-171">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="9431c-171">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    * <span data-ttu-id="9431c-172">選擇 [nuget.org] 作為 [套件來源]，選取 [瀏覽] 索引標籤，搜尋 **Microsoft.ML**。</span><span class="sxs-lookup"><span data-stu-id="9431c-172">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span>
    * <span data-ttu-id="9431c-173">按一下 [**版本**] 下拉式清單，選取清單中的 [ **1.4.0** ] 套件，然後選取 [**安裝**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="9431c-173">Click on the **Version** drop-down, select the **1.4.0** package in the list, and select the **Install** button.</span></span>
    * <span data-ttu-id="9431c-174">選取 [**預覽變更**] 對話方塊上的 [**確定]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="9431c-174">Select the **OK** button on the **Preview Changes** dialog.</span></span>
    * <span data-ttu-id="9431c-175">如果您同意所列套件的授權條款，請選取 [**授權接受**] 對話方塊上的 [**我接受**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="9431c-175">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    * <span data-ttu-id="9431c-176">針對**ImageAnalytics v 1.4.0**、 **SciSharp、TensorFlow**和**1.15.0 v**TensorFlow，重複執行這些步驟。</span><span class="sxs-lookup"><span data-stu-id="9431c-176">Repeat these steps for **Microsoft.ML.ImageAnalytics v1.4.0**, **SciSharp.TensorFlow.Redist v1.15.0** and **Microsoft.ML.TensorFlow v1.4.0**.</span></span>

### <a name="download-assets"></a><span data-ttu-id="9431c-177">下載資產</span><span class="sxs-lookup"><span data-stu-id="9431c-177">Download assets</span></span>

1. <span data-ttu-id="9431c-178">下載[專案資產目錄 zip 檔案](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)，然後將它解壓縮。</span><span class="sxs-lookup"><span data-stu-id="9431c-178">Download [The project assets directory zip file](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip), and unzip.</span></span>

1. <span data-ttu-id="9431c-179">將 `assets` 目錄複製到您的 *TransferLearningTF* 專案目錄中。</span><span class="sxs-lookup"><span data-stu-id="9431c-179">Copy the `assets` directory into your *TransferLearningTF* project directory.</span></span> <span data-ttu-id="9431c-180">此目錄及其子目錄包含本教學課程所需的資料和支援檔案 (Inception model 除外，您將會在下個步驟中下載並新增它)。</span><span class="sxs-lookup"><span data-stu-id="9431c-180">This directory and its subdirectories contain the data and support files (except for the Inception model, which you'll download and add in the next step) needed for this tutorial.</span></span>

1. <span data-ttu-id="9431c-181">下載 [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)，然後將它解壓縮。</span><span class="sxs-lookup"><span data-stu-id="9431c-181">Download the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), and unzip.</span></span>

1. <span data-ttu-id="9431c-182">將剛才解壓縮的 `inception5h` 目錄的內容複製到您 *TransferLearningTF* 專案的 `assets/inception` 目錄中。</span><span class="sxs-lookup"><span data-stu-id="9431c-182">Copy the contents of the `inception5h` directory just unzipped into your *TransferLearningTF* project `assets/inception` directory.</span></span> <span data-ttu-id="9431c-183">此目錄包含本教學課程所需的模型和其他支援檔案，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="9431c-183">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![Inception 目錄內容](./media/image-classification/inception-files.png)

1. <span data-ttu-id="9431c-185">在 [方案總管] 中，以滑鼠右鍵按一下資產目錄及子目錄中的每個檔案，然後選取 [內容]。</span><span class="sxs-lookup"><span data-stu-id="9431c-185">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="9431c-186">在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。</span><span class="sxs-lookup"><span data-stu-id="9431c-186">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="9431c-187">建立類別及定義路徑</span><span class="sxs-lookup"><span data-stu-id="9431c-187">Create classes and define paths</span></span>

1. <span data-ttu-id="9431c-188">在 *Program.cs* 檔案頂端新增下列額外的 `using` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="9431c-188">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

1. <span data-ttu-id="9431c-189">將下列程式碼新增至 `Main` 方法上方的一行，以指定資產路徑：</span><span class="sxs-lookup"><span data-stu-id="9431c-189">Add the following code to the line right above the `Main` method to specify the asset paths:</span></span>

    [!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

1. <span data-ttu-id="9431c-190">為輸入資料和預測建立類別。</span><span class="sxs-lookup"><span data-stu-id="9431c-190">Create classes for your input data, and predictions.</span></span>

    [!code-csharp[DeclareImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareImageData)]

    <span data-ttu-id="9431c-191">`ImageData` 是輸入資料集類別，並具有下列 <xref:System.String> 欄位：</span><span class="sxs-lookup"><span data-stu-id="9431c-191">`ImageData` is the input image data class and has the following <xref:System.String> fields:</span></span>

    * <span data-ttu-id="9431c-192">`ImagePath` 包含影像檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="9431c-192">`ImagePath` contains the image file name.</span></span>
    * <span data-ttu-id="9431c-193">`Label` 包含影像標籤的值。</span><span class="sxs-lookup"><span data-stu-id="9431c-193">`Label` contains a value for the image label.</span></span>

1. <span data-ttu-id="9431c-194">將新類別新增至 `ImagePrediction` 的專案：</span><span class="sxs-lookup"><span data-stu-id="9431c-194">Add a new class to your project for `ImagePrediction`:</span></span>

    [!code-csharp[DeclareImagePrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareImagePrediction)]

    <span data-ttu-id="9431c-195">`ImagePrediction` 是影像預測類別，並具有下列欄位：</span><span class="sxs-lookup"><span data-stu-id="9431c-195">`ImagePrediction` is the image prediction class and has the following fields:</span></span>

    * <span data-ttu-id="9431c-196">`Score` 包含指定影像分類的信賴百分比。</span><span class="sxs-lookup"><span data-stu-id="9431c-196">`Score` contains the confidence percentage for a given image classification.</span></span>
    * <span data-ttu-id="9431c-197">`PredictedLabelValue` 包含已預測影像分類標籤的值。</span><span class="sxs-lookup"><span data-stu-id="9431c-197">`PredictedLabelValue` contains a value for the predicted image classification label.</span></span>

    <span data-ttu-id="9431c-198">`ImagePrediction` 是在模型定型後，用來進行預測的類別。</span><span class="sxs-lookup"><span data-stu-id="9431c-198">`ImagePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="9431c-199">它具有影像路徑的 `string` (`ImagePath`)。</span><span class="sxs-lookup"><span data-stu-id="9431c-199">It has a `string` (`ImagePath`) for the image path.</span></span> <span data-ttu-id="9431c-200">`Label` 可用來重複使用和定型模型。</span><span class="sxs-lookup"><span data-stu-id="9431c-200">The `Label` is used to reuse and train the model.</span></span> <span data-ttu-id="9431c-201">`PredictedLabelValue` 的使用時機是在進行預測和評估的期間。</span><span class="sxs-lookup"><span data-stu-id="9431c-201">The `PredictedLabelValue` is used during prediction and evaluation.</span></span> <span data-ttu-id="9431c-202">就評估而言，會使用含有定型資料、預設值及模型的輸入。</span><span class="sxs-lookup"><span data-stu-id="9431c-202">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="9431c-203">在 Main 中初始化變數</span><span class="sxs-lookup"><span data-stu-id="9431c-203">Initialize variables in Main</span></span>

1. <span data-ttu-id="9431c-204">搭配 `MLContext` 的新執行個體來初始化 `mlContext` 變數。</span><span class="sxs-lookup"><span data-stu-id="9431c-204">Initialize the `mlContext` variable with a new instance of `MLContext`.</span></span>  <span data-ttu-id="9431c-205">在 `Main` 方法中，以下列程式碼取代 `Console.WriteLine("Hello World!")`：</span><span class="sxs-lookup"><span data-stu-id="9431c-205">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

    [!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

    <span data-ttu-id="9431c-206">[MLContext 類別](xref:Microsoft.ML.MLContext)是所有 ML.NET 作業的起點，且初始化 `mlContext` 會建立新的 ML.NET 環境，其可在模型建立工作流程物件之間共用。</span><span class="sxs-lookup"><span data-stu-id="9431c-206">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="9431c-207">就概念而言，類似於 Entity Framework 中的 `DBContext`。</span><span class="sxs-lookup"><span data-stu-id="9431c-207">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="create-a-struct-for-inception-model-parameters"></a><span data-ttu-id="9431c-208">建立用於開始模型參數的結構</span><span class="sxs-lookup"><span data-stu-id="9431c-208">Create a struct for Inception model parameters</span></span>

1. <span data-ttu-id="9431c-209">開始模型有數個您需要傳入的參數。</span><span class="sxs-lookup"><span data-stu-id="9431c-209">The Inception model has several parameters you need to pass in.</span></span> <span data-ttu-id="9431c-210">使用下列程式碼，在 `Main()` 方法後面建立結構，以將參數值對應至易記名稱：</span><span class="sxs-lookup"><span data-stu-id="9431c-210">Create a struct to map the parameter values to friendly names with the following code, just after the `Main()` method:</span></span>

    [!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a><span data-ttu-id="9431c-211">建立顯示公用程式方法</span><span class="sxs-lookup"><span data-stu-id="9431c-211">Create a display utility method</span></span>

<span data-ttu-id="9431c-212">因為您將會不只一次顯示影像資料和相關預測，所以請建立顯示公用程式方法來處理顯示影像和預測結果。</span><span class="sxs-lookup"><span data-stu-id="9431c-212">Since you'll display the image data and the related predictions more than once, create a display utility method to handle displaying the image and prediction results.</span></span>

1. <span data-ttu-id="9431c-213">使用下列程式碼，在緊接著 `InceptionSettings` 結構之後，建立 `DisplayResults()` 方法：</span><span class="sxs-lookup"><span data-stu-id="9431c-213">Create the `DisplayResults()` method, just after the `InceptionSettings` struct, using the following code:</span></span>

    ```csharp
    private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
    {

    }
    ```

1. <span data-ttu-id="9431c-214">填入 `DisplayResults` 方法的主體：</span><span class="sxs-lookup"><span data-stu-id="9431c-214">Fill in the body of the `DisplayResults` method:</span></span>

    [!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

### <a name="create-a-tsv-file-utility-method"></a><span data-ttu-id="9431c-215">建立 .tsv 檔案公用程式方法</span><span class="sxs-lookup"><span data-stu-id="9431c-215">Create a .tsv file utility method</span></span>

1. <span data-ttu-id="9431c-216">請使用下列程式碼，在緊接著 `DisplayResults()` 方法之後，建立 `ReadFromTsv()` 方法：</span><span class="sxs-lookup"><span data-stu-id="9431c-216">Create the `ReadFromTsv()` method, just after the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
    {

    }
    ```

1. <span data-ttu-id="9431c-217">填入 `ReadFromTsv` 方法的主體：</span><span class="sxs-lookup"><span data-stu-id="9431c-217">Fill in the body of the `ReadFromTsv` method:</span></span>

    [!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]

    <span data-ttu-id="9431c-218">程式碼會剖析 `tags.tsv` 檔案，將檔案路徑新增至 `ImagePath` 屬性的影像檔案名稱，並將它和 `Label` 載入 `ImageData` 物件中。</span><span class="sxs-lookup"><span data-stu-id="9431c-218">The code parses through the `tags.tsv` file to add the file path to the image file name for the `ImagePath` property and load it and the `Label` into an `ImageData` object.</span></span>

### <a name="create-a-method-to-make-a-prediction"></a><span data-ttu-id="9431c-219">建立方法以進行預測</span><span class="sxs-lookup"><span data-stu-id="9431c-219">Create a method to make a prediction</span></span>

1. <span data-ttu-id="9431c-220">請使用下列程式碼，緊接在 `DisplayResults()` 方法之前，建立 `ClassifySingleImage()` 方法：</span><span class="sxs-lookup"><span data-stu-id="9431c-220">Create the `ClassifySingleImage()` method, just before the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. <span data-ttu-id="9431c-221">建立 `ImageData` 物件，其中包含單一 `ImagePath`的完整路徑和影像檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="9431c-221">Create an `ImageData` object that contains the fully qualified path and image file name for the single `ImagePath`.</span></span> <span data-ttu-id="9431c-222">將下列程式碼新增為 `ClassifySingleImage()` 方法中的下一行：</span><span class="sxs-lookup"><span data-stu-id="9431c-222">Add the following code as the next  lines in the `ClassifySingleImage()` method:</span></span>

    [!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

1. <span data-ttu-id="9431c-223">藉由新增下列程式碼做為 `ClassifySingleImage` 方法中的下一行，進行單一預測：</span><span class="sxs-lookup"><span data-stu-id="9431c-223">Make a single prediction, by adding the following code as the next line in the `ClassifySingleImage` method:</span></span>

    [!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

    <span data-ttu-id="9431c-224">若要取得預測，請使用[Predict （）](xref:Microsoft.ML.PredictionEngine%602.Predict%2A)方法。</span><span class="sxs-lookup"><span data-stu-id="9431c-224">To get the prediction, use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) method.</span></span> <span data-ttu-id="9431c-225">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602)是一個方便的 API，可讓您在單一資料實例上執行預測。</span><span class="sxs-lookup"><span data-stu-id="9431c-225">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="9431c-226">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) 不是安全執行緒。</span><span class="sxs-lookup"><span data-stu-id="9431c-226">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="9431c-227">可接受在單一執行緒或原型環境中使用。</span><span class="sxs-lookup"><span data-stu-id="9431c-227">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="9431c-228">為了改善生產環境中的效能和執行緒安全，請使用 `PredictionEnginePool` 服務，這會建立[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)物件的[`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) ，以便在整個應用程式中使用。</span><span class="sxs-lookup"><span data-stu-id="9431c-228">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="9431c-229">請參閱本指南，以瞭解如何[在 ASP.NET Core WEB API 中使用 `PredictionEnginePool`](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)。</span><span class="sxs-lookup"><span data-stu-id="9431c-229">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="9431c-230">`PredictionEnginePool` 服務延伸模組目前處於預覽狀態。</span><span class="sxs-lookup"><span data-stu-id="9431c-230">`PredictionEnginePool` service extension is currently in preview.</span></span>

1. <span data-ttu-id="9431c-231">將預測結果顯示為 `ClassifySingleImage()` 方法中的下一行程式碼：</span><span class="sxs-lookup"><span data-stu-id="9431c-231">Display the prediction result as the next line of code in the `ClassifySingleImage()` method:</span></span>

   [!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="construct-the-mlnet-model-pipeline"></a><span data-ttu-id="9431c-232">建立 ML.NET 模型管線</span><span class="sxs-lookup"><span data-stu-id="9431c-232">Construct the ML.NET model pipeline</span></span>

<span data-ttu-id="9431c-233">ML.NET 模型管線是一鏈估算器。</span><span class="sxs-lookup"><span data-stu-id="9431c-233">An ML.NET model pipeline is a chain of estimators.</span></span> <span data-ttu-id="9431c-234">請注意，管線結構中不會執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="9431c-234">Note that no execution happens during pipeline construction.</span></span> <span data-ttu-id="9431c-235">系統會建立估計工具物件，但不會執行。</span><span class="sxs-lookup"><span data-stu-id="9431c-235">The estimator objects are created but not executed.</span></span>

1. <span data-ttu-id="9431c-236">新增方法以產生模型</span><span class="sxs-lookup"><span data-stu-id="9431c-236">Add a method to generate the model</span></span>

    <span data-ttu-id="9431c-237">這個方法是教學課程的核心。</span><span class="sxs-lookup"><span data-stu-id="9431c-237">This method is the heart of the tutorial.</span></span> <span data-ttu-id="9431c-238">它會建立模型的管線，並訓練管線以產生 ML.NET 模型。</span><span class="sxs-lookup"><span data-stu-id="9431c-238">It creates a pipeline for the model, and trains the pipeline to produce the ML.NET model.</span></span> <span data-ttu-id="9431c-239">它也會針對某些先前看不見的測試資料評估模型。</span><span class="sxs-lookup"><span data-stu-id="9431c-239">It also evaluates the model against some previously unseen test data.</span></span>

    <span data-ttu-id="9431c-240">使用下列程式碼，緊接在 `InceptionSettings` 結構之後及 `DisplayResults()` 方法之前，建立 `GenerateModel()` 方法：</span><span class="sxs-lookup"><span data-stu-id="9431c-240">Create the `GenerateModel()` method, just after the `InceptionSettings` struct and just before the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer GenerateModel(MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="9431c-241">新增估算器以載入、調整大小，並從影像資料中將圖元解壓縮：</span><span class="sxs-lookup"><span data-stu-id="9431c-241">Add the estimators to load, resize and extract the pixels from the image data:</span></span>

    [!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

    <span data-ttu-id="9431c-242">影像資料必須處理成 TensorFlow 模型所預期的格式。</span><span class="sxs-lookup"><span data-stu-id="9431c-242">The image data needs to be processed into the format that the TensorFlow model expects.</span></span> <span data-ttu-id="9431c-243">在此情況下，影像會載入記憶體中，並調整為一致大小，而圖元會解壓縮為數值向量。</span><span class="sxs-lookup"><span data-stu-id="9431c-243">In this case, the images are loaded into memory, resized to a consistent size, and the pixels are extracted into a numeric vector.</span></span>

1. <span data-ttu-id="9431c-244">新增估計工具以載入 TensorFlow 模型，並對它進行評分：</span><span class="sxs-lookup"><span data-stu-id="9431c-244">Add the estimator to load the TensorFlow model, and score it:</span></span>

    [!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

    <span data-ttu-id="9431c-245">管線中的這個階段會將 TensorFlow 模型載入記憶體中，然後透過 TensorFlow 模型網路處理圖元值的向量。</span><span class="sxs-lookup"><span data-stu-id="9431c-245">This stage in the pipeline loads the TensorFlow model into memory, then processes the vector of pixel values through the TensorFlow model network.</span></span> <span data-ttu-id="9431c-246">將輸入套用至深度學習模型，並使用模型產生輸出，稱為**計分**。</span><span class="sxs-lookup"><span data-stu-id="9431c-246">Applying inputs to a deep learning model, and generating an output using the model, is referred to as **Scoring**.</span></span> <span data-ttu-id="9431c-247">整體使用模型時，計分會進行推斷或預測。</span><span class="sxs-lookup"><span data-stu-id="9431c-247">When using the model in its entirety, scoring makes an inference, or prediction.</span></span>

    <span data-ttu-id="9431c-248">在此情況下，您會使用最後一層以外的所有 TensorFlow 模型，這是進行推斷的層。</span><span class="sxs-lookup"><span data-stu-id="9431c-248">In this case, you use all of the TensorFlow model except the last layer, which is the layer that makes the inference.</span></span> <span data-ttu-id="9431c-249">倒數第二圖層的輸出會標示為 `softmax_2_preactivation`。</span><span class="sxs-lookup"><span data-stu-id="9431c-249">The output of the penultimate layer is labeled `softmax_2_preactivation`.</span></span> <span data-ttu-id="9431c-250">此圖層的輸出實際上是特徵的向量，可描述原始輸入影像。</span><span class="sxs-lookup"><span data-stu-id="9431c-250">The output of this layer is effectively a vector of features that characterize the original input images.</span></span>

    <span data-ttu-id="9431c-251">TensorFlow 模型所產生的此功能向量將用來做為 ML.NET 定型演算法的輸入。</span><span class="sxs-lookup"><span data-stu-id="9431c-251">This feature vector generated by the TensorFlow model will be used as input to an ML.NET training algorithm.</span></span>

1. <span data-ttu-id="9431c-252">新增估計工具，以將定型資料中的字串標籤對應到整數索引鍵值：</span><span class="sxs-lookup"><span data-stu-id="9431c-252">Add the estimator to map the string labels in the training data to integer key values:</span></span>

    [!code-csharp[MapValueToKey](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey)]

    <span data-ttu-id="9431c-253">接下來附加的 ML.NET 訓練員要求其標籤必須是 `key` 格式，而不是任一字元串。</span><span class="sxs-lookup"><span data-stu-id="9431c-253">The ML.NET trainer that is appended next requires its labels to be in `key` format rather than arbitrary strings.</span></span> <span data-ttu-id="9431c-254">「索引鍵」是一個數位，其中包含一個與字串值的對應。</span><span class="sxs-lookup"><span data-stu-id="9431c-254">A key is a number that has a one to one mapping to a string value.</span></span>

1. <span data-ttu-id="9431c-255">新增 ML.NET 訓練演算法：</span><span class="sxs-lookup"><span data-stu-id="9431c-255">Add the ML.NET training algorithm:</span></span>

    [!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

1. <span data-ttu-id="9431c-256">新增估計工具以將預測的索引鍵值對應回字串：</span><span class="sxs-lookup"><span data-stu-id="9431c-256">Add the estimator to map the predicted key value back into a string:</span></span>

    [!code-csharp[MapKeyToValue](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapKeyToValue)]

## <a name="train-the-model"></a><span data-ttu-id="9431c-257">將模型定型</span><span class="sxs-lookup"><span data-stu-id="9431c-257">Train the model</span></span>

1. <span data-ttu-id="9431c-258">使用[LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options))包裝函式載入定型資料。</span><span class="sxs-lookup"><span data-stu-id="9431c-258">Load the training data using the [LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) wrapper.</span></span> <span data-ttu-id="9431c-259">將下列程式碼加入為 `GenerateModel()` 方法中的下一行：</span><span class="sxs-lookup"><span data-stu-id="9431c-259">Add the following code as the next line in the `GenerateModel()` method:</span></span>

    [!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

    <span data-ttu-id="9431c-260">ML.NET 中的資料以 [IDataView 類別](xref:Microsoft.ML.IDataView) 表示。</span><span class="sxs-lookup"><span data-stu-id="9431c-260">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="9431c-261">`IDataView` 是彈性且有效率的表格式資料描述方式 (數值和文字)。</span><span class="sxs-lookup"><span data-stu-id="9431c-261">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="9431c-262">資料可以從文字或即時 (例如 SQL 資料庫或記錄檔) 載入至 `IDataView` 物件。</span><span class="sxs-lookup"><span data-stu-id="9431c-262">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

1. <span data-ttu-id="9431c-263">使用上述載入的資料來定型模型：</span><span class="sxs-lookup"><span data-stu-id="9431c-263">Train the model with the data loaded above:</span></span>

    [!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

    <span data-ttu-id="9431c-264">`Fit()` 方法會將訓練資料集套用至管線，以訓練您的模型。</span><span class="sxs-lookup"><span data-stu-id="9431c-264">The `Fit()` method trains your model by applying the training dataset to the pipeline.</span></span>

## <a name="evaluate-the-accuracy-of-the-model"></a><span data-ttu-id="9431c-265">評估模型的精確度</span><span class="sxs-lookup"><span data-stu-id="9431c-265">Evaluate the accuracy of the model</span></span>

1. <span data-ttu-id="9431c-266">將下列程式碼新增至 `GenerateModel` 方法的下一行，以載入並轉換測試資料：</span><span class="sxs-lookup"><span data-stu-id="9431c-266">Load and transform the test data, by adding the following code to the next line of the `GenerateModel` method:</span></span>

    [!code-csharp[LoadAndTransformTestData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadAndTransformTestData "Load and transform test data")]

    <span data-ttu-id="9431c-267">您可以使用幾個範例影像來評估模型。</span><span class="sxs-lookup"><span data-stu-id="9431c-267">There are a few sample images that you can use to evaluate the model.</span></span> <span data-ttu-id="9431c-268">就像定型資料一樣，這些都需要載入 `IDataView`，讓模型可以轉換它們。</span><span class="sxs-lookup"><span data-stu-id="9431c-268">Like the training data, these need to be loaded into an `IDataView`, so that they can be transformed by the model.</span></span>

1. <span data-ttu-id="9431c-269">將下列程式碼新增至 `GenerateModel()` 方法，以評估模型：</span><span class="sxs-lookup"><span data-stu-id="9431c-269">Add the following code to the `GenerateModel()` method to evaluate the model:</span></span>

    [!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

    <span data-ttu-id="9431c-270">當您具有預測之後，請設定 [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) 方法：</span><span class="sxs-lookup"><span data-stu-id="9431c-270">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method:</span></span>

    * <span data-ttu-id="9431c-271">評估模型（比較預測值與測試資料集 `labels`）。</span><span class="sxs-lookup"><span data-stu-id="9431c-271">Assesses the model (compares the predicted values with the test dataset `labels`).</span></span>
    * <span data-ttu-id="9431c-272">傳回模型效能計量。</span><span class="sxs-lookup"><span data-stu-id="9431c-272">Returns the model performance metrics.</span></span>

1. <span data-ttu-id="9431c-273">顯示模型精確度計量</span><span class="sxs-lookup"><span data-stu-id="9431c-273">Display the model accuracy metrics</span></span>

    <span data-ttu-id="9431c-274">使用下列程式碼來顯示計量、共用結果，然後依結果採取動作：</span><span class="sxs-lookup"><span data-stu-id="9431c-274">Use the following code to display the metrics, share the results, and then act on them:</span></span>

    [!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

    <span data-ttu-id="9431c-275">下列計量會針對影像分類進行評估：</span><span class="sxs-lookup"><span data-stu-id="9431c-275">The following metrics are evaluated for image classification:</span></span>

    * <span data-ttu-id="9431c-276">`Log-loss`：請參閱[記錄檔遺失](../resources/glossary.md#log-loss)。</span><span class="sxs-lookup"><span data-stu-id="9431c-276">`Log-loss` - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="9431c-277">建議讓記錄檔遺失盡量接近零。</span><span class="sxs-lookup"><span data-stu-id="9431c-277">You want Log-loss to be as close to zero as possible.</span></span>
    * <span data-ttu-id="9431c-278">`Per class Log-loss`。</span><span class="sxs-lookup"><span data-stu-id="9431c-278">`Per class Log-loss`.</span></span> <span data-ttu-id="9431c-279">建議讓每個類別的記錄檔遺失盡量接近零。</span><span class="sxs-lookup"><span data-stu-id="9431c-279">You want per class Log-loss to be as close to zero as possible.</span></span>

1. <span data-ttu-id="9431c-280">新增下列程式碼來將定型後的模型作為下一行傳回：</span><span class="sxs-lookup"><span data-stu-id="9431c-280">Add the following code to return the trained model as the next line:</span></span>

    [!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReturnModel)]

## <a name="run-the-application"></a><span data-ttu-id="9431c-281">執行應用程式！</span><span class="sxs-lookup"><span data-stu-id="9431c-281">Run the application!</span></span>

1. <span data-ttu-id="9431c-282">在建立 MLCoNtext 類別之後，將呼叫新增至 `Main` 方法中的 `GenerateModel`：</span><span class="sxs-lookup"><span data-stu-id="9431c-282">Add the call to `GenerateModel` in the `Main` method after the creation of the MLContext class:</span></span>

    [!code-csharp[CallGenerateModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallGenerateModel)]

1. <span data-ttu-id="9431c-283">將呼叫新增至 `ClassifySingleImage()` 方法，做為 `Main` 方法中的下一行程式碼：</span><span class="sxs-lookup"><span data-stu-id="9431c-283">Add the call to the `ClassifySingleImage()` method as the next line of code in the `Main` method:</span></span>

    [!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

1. <span data-ttu-id="9431c-284">執行主控台應用程式（Ctrl + F5）。</span><span class="sxs-lookup"><span data-stu-id="9431c-284">Run your console app (Ctrl + F5).</span></span> <span data-ttu-id="9431c-285">您的結果應該與下列輸出類似。</span><span class="sxs-lookup"><span data-stu-id="9431c-285">Your results should be similar to the following output.</span></span>  <span data-ttu-id="9431c-286">您可能會看到警告或處理中訊息，但為了讓結果變得清楚，這些訊息已從下列結果中移除。</span><span class="sxs-lookup"><span data-stu-id="9431c-286">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="9431c-287">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="9431c-287">Congratulations!</span></span> <span data-ttu-id="9431c-288">您現在已成功地為影像分類建立機器學習模型，其方式是在 ML.NET 中將轉移學習套用至 `TensorFlow` 模型。</span><span class="sxs-lookup"><span data-stu-id="9431c-288">You've now successfully built a machine learning model for image classification by applying transfer learning to a `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="9431c-289">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="9431c-289">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span>

<span data-ttu-id="9431c-290">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="9431c-290">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="9431c-291">了解問題</span><span class="sxs-lookup"><span data-stu-id="9431c-291">Understand the problem</span></span>
> * <span data-ttu-id="9431c-292">將預先定型的 TensorFlow 模型納入 ML.NET 管線中</span><span class="sxs-lookup"><span data-stu-id="9431c-292">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span></span>
> * <span data-ttu-id="9431c-293">定型和評估 ML.NET 模型</span><span class="sxs-lookup"><span data-stu-id="9431c-293">Train and evaluate the ML.NET model</span></span>
> * <span data-ttu-id="9431c-294">分類測試影像</span><span class="sxs-lookup"><span data-stu-id="9431c-294">Classify a test image</span></span>

<span data-ttu-id="9431c-295">請查看機器學習範例 GitHub 存放庫，以探索更複雜的影像分類範例。</span><span class="sxs-lookup"><span data-stu-id="9431c-295">Check out the Machine Learning samples GitHub repository to explore an expanded image classification sample.</span></span>
> [!div class="nextstepaction"]
> <span data-ttu-id="9431c-296">[dotnet/machinelearning-samples GitHub 存放庫](https://github.com/dotnet/machinelearning-samples/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="9431c-296">[dotnet/machinelearning-samples GitHub repository](https://github.com/dotnet/machinelearning-samples/)</span></span>
