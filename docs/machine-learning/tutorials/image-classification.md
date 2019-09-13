---
title: 教學課程：重新定型 TensorFlow 影像分類器 - 傳輸學習
description: 了解如何使用傳輸學習和 ML.NET 重新定型影像分類 TensorFlow 模型。 原始模型已經定型，以將個別影像分類。 重新定型之後，新模型會將影像組織為各種不同類別。
ms.date: 07/09/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: eb6e3d3f3a33aa7360802ce1bc6c16532539c828
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929244"
---
# <a name="tutorial-retrain-a-tensorflow-image-classifier-with-transfer-learning-and-mlnet"></a><span data-ttu-id="f52b0-105">教學課程：運用傳輸學習與 ML.NET 重新定型 TensorFlow 影像分類器</span><span class="sxs-lookup"><span data-stu-id="f52b0-105">Tutorial: Retrain a TensorFlow image classifier with transfer learning and ML.NET</span></span>

<span data-ttu-id="f52b0-106">了解如何使用傳輸學習和 ML.NET 重新定型影像分類 TensorFlow 模型。</span><span class="sxs-lookup"><span data-stu-id="f52b0-106">Learn how to retrain an image classification TensorFlow model with transfer learning and ML.NET.</span></span> <span data-ttu-id="f52b0-107">原始模型已經定型，以將個別影像分類。</span><span class="sxs-lookup"><span data-stu-id="f52b0-107">The original model was trained to classify individual images.</span></span> <span data-ttu-id="f52b0-108">重新定型之後，新模型會將影像組織為各種不同類別。</span><span class="sxs-lookup"><span data-stu-id="f52b0-108">After retraining, the new model organizes the images into broad categories.</span></span> 

<span data-ttu-id="f52b0-109">若要從頭對[影像分類](https://en.wikipedia.org/wiki/Outline_of_object_recognition) \(英文\) 模型進行定型，將會需要設定數以百萬計的參數、眾多已標籤的定型資料，以及大量的計算資源 (數以百計的 GPU 小時)。</span><span class="sxs-lookup"><span data-stu-id="f52b0-109">Training an [Image Classification](https://en.wikipedia.org/wiki/Outline_of_object_recognition) model from scratch requires setting millions of parameters, a ton of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="f52b0-110">遷移學習的效能雖然不如從頭對自訂模型進行定型來得有效，但它能讓您透過僅需處理數以千計的影像 (而非數以百萬計的已標籤影像) 來縮短此程序，並以較為快速的方式建置自訂模型 (在不具備 GPU 的電腦上於一小時內便能完成)。</span><span class="sxs-lookup"><span data-stu-id="f52b0-110">While not as effective as training a custom model from scratch, transfer learning allows you to shortcut this process by working with thousands of images vs. millions of labeled images and build a customized model fairly quickly (within an hour on a machine without a GPU).</span></span>

<span data-ttu-id="f52b0-111">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="f52b0-111">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="f52b0-112">了解問題</span><span class="sxs-lookup"><span data-stu-id="f52b0-112">Understand the problem</span></span>
> * <span data-ttu-id="f52b0-113">重複使用並調整預先定型的模型</span><span class="sxs-lookup"><span data-stu-id="f52b0-113">Reuse and tune the pre-trained model</span></span>
> * <span data-ttu-id="f52b0-114">分類影像</span><span class="sxs-lookup"><span data-stu-id="f52b0-114">Classify Images</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="f52b0-115">什麼是傳輸學習？</span><span class="sxs-lookup"><span data-stu-id="f52b0-115">What is transfer learning?</span></span>

<span data-ttu-id="f52b0-116">想想看，如果您可以重複使用已預先定型的模型來解決類似問題，並重新對該模型的所有或部分層面進行定型來使它可以解決您的問題，會有多方便？</span><span class="sxs-lookup"><span data-stu-id="f52b0-116">What if you could reuse a model that's already been pre trained to solve a similar problem and retrain either all or some of the layers of that model to make it solve your problem?</span></span> <span data-ttu-id="f52b0-117">這種重新使用部分已定型模型來建置新模型的技巧，稱為[遷移學習](https://en.wikipedia.org/wiki/Transfer_learning)。</span><span class="sxs-lookup"><span data-stu-id="f52b0-117">This technique of reusing part of an already trained model to build a new model is known as [transfer learning](https://en.wikipedia.org/wiki/Transfer_learning).</span></span>

## <a name="image-classification-sample-overview"></a><span data-ttu-id="f52b0-118">影像分類範例概觀</span><span class="sxs-lookup"><span data-stu-id="f52b0-118">Image classification sample overview</span></span>

<span data-ttu-id="f52b0-119">範例為使用 ML.NET 來建置影像分類器的主控台應用程式，其會重複使用已預先定型的模型搭配少量的定型資料來分類影像。</span><span class="sxs-lookup"><span data-stu-id="f52b0-119">The sample is a console application that uses ML.NET to build an image classifier by reusing a pre-trained model to classify images with a small amount of training data.</span></span>

<span data-ttu-id="f52b0-120">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="f52b0-120">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span> <span data-ttu-id="f52b0-121">請注意，根據預設，本教學課程的 .NET 專案組態以 .NET Core 2.2 為目標。</span><span class="sxs-lookup"><span data-stu-id="f52b0-121">Note that by default, the .NET project configuration for this tutorial targets .NET core 2.2.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f52b0-122">必要條件</span><span class="sxs-lookup"><span data-stu-id="f52b0-122">Prerequisites</span></span>

* <span data-ttu-id="f52b0-123">已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)。</span><span class="sxs-lookup"><span data-stu-id="f52b0-123">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span> 

* <span data-ttu-id="f52b0-124">Microsoft.ML 1.0.0 Nuget 套件</span><span class="sxs-lookup"><span data-stu-id="f52b0-124">Microsoft.ML 1.0.0 Nuget package</span></span>
* <span data-ttu-id="f52b0-125">Microsoft.ML.ImageAnalytics 1.0.0 Nuget 套件</span><span class="sxs-lookup"><span data-stu-id="f52b0-125">Microsoft.ML.ImageAnalytics 1.0.0 Nuget package</span></span>
* <span data-ttu-id="f52b0-126">Microsoft.ML.TensorFlow 0.12.0 Nuget 套件</span><span class="sxs-lookup"><span data-stu-id="f52b0-126">Microsoft.ML.TensorFlow 0.12.0 Nuget package</span></span>

* [<span data-ttu-id="f52b0-127">教學課程資產目錄 .ZIP 檔案</span><span class="sxs-lookup"><span data-stu-id="f52b0-127">The tutorial assets directory .ZIP file</span></span>](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)

* [<span data-ttu-id="f52b0-128">InceptionV1 機器學習模型</span><span class="sxs-lookup"><span data-stu-id="f52b0-128">The InceptionV1 machine learning model</span></span>](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="f52b0-129">選取適當的機器學習工作</span><span class="sxs-lookup"><span data-stu-id="f52b0-129">Select the appropriate machine learning task</span></span>

<span data-ttu-id="f52b0-130">[深度學習](https://en.wikipedia.org/wiki/Deep_learning)是機器學習的子集，其正為電腦視覺及語音辨識等領域帶來革命性的影響。</span><span class="sxs-lookup"><span data-stu-id="f52b0-130">[Deep learning](https://en.wikipedia.org/wiki/Deep_learning) is a subset of Machine Learning, which is revolutionizing areas like Computer Vision and Speech Recognition.</span></span>

<span data-ttu-id="f52b0-131">深度學習模型是使用包含多個學習層級的大量[已標籤資料](https://en.wikipedia.org/wiki/Labeled_data) \(英文\) 及[神經網路](https://en.wikipedia.org/wiki/Artificial_neural_network)來定型的。</span><span class="sxs-lookup"><span data-stu-id="f52b0-131">Deep learning models are trained by using large sets of [labeled data](https://en.wikipedia.org/wiki/Labeled_data) and [neural networks](https://en.wikipedia.org/wiki/Artificial_neural_network) that contain multiple learning layers.</span></span> <span data-ttu-id="f52b0-132">深度學習：</span><span class="sxs-lookup"><span data-stu-id="f52b0-132">Deep learning:</span></span>

* <span data-ttu-id="f52b0-133">能在某些工作上產生較好的效能，例如電腦視覺。</span><span class="sxs-lookup"><span data-stu-id="f52b0-133">Performs better on some tasks like Computer Vision.</span></span>

* <span data-ttu-id="f52b0-134">能在龐大資料量上產生較好的效能。</span><span class="sxs-lookup"><span data-stu-id="f52b0-134">Performs well on huge data amounts.</span></span>

<span data-ttu-id="f52b0-135">影像分類是常見的機器學習工作，其可讓我們將影像自動分類為多個類別，例如：</span><span class="sxs-lookup"><span data-stu-id="f52b0-135">Image Classification is a common Machine Learning task that allows us to automatically classify images into multiple categories such as:</span></span>

* <span data-ttu-id="f52b0-136">是否能在影像中偵測到人類面孔。</span><span class="sxs-lookup"><span data-stu-id="f52b0-136">Detecting a human face in an image or not.</span></span>
* <span data-ttu-id="f52b0-137">偵測貓與狗。</span><span class="sxs-lookup"><span data-stu-id="f52b0-137">Detecting Cats vs. dogs.</span></span>

 <span data-ttu-id="f52b0-138">或是以下列影像為例，判斷該影像是否為食物、玩具或設備：</span><span class="sxs-lookup"><span data-stu-id="f52b0-138">Or as in the following images determining if an image is a(n)  food, toy, or appliance:</span></span>

<span data-ttu-id="f52b0-139">![披薩影像](./media/image-classification/220px-Pepperoni_pizza.jpg)
![玩具熊影像](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![烤麵包機影像](./media/image-classification/193px-Broodrooster.jpg)</span><span class="sxs-lookup"><span data-stu-id="f52b0-139">![pizza image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![teddy bear image](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toaster image](./media/image-classification/193px-Broodrooster.jpg)</span></span>

>[!Note]
> <span data-ttu-id="f52b0-140">上述影像為 Wikimedia Commons 所有，並具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="f52b0-140">The preceding images belong to Wikimedia Commons and are attributed as follows:</span></span>
>
> * <span data-ttu-id="f52b0-141">"220px-Pepperoni_pizza.jpg" 公眾領域， https://commons.wikimedia.org/w/index.php?curid=79505 \(英文\)，</span><span class="sxs-lookup"><span data-stu-id="f52b0-141">"220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,</span></span>
> * <span data-ttu-id="f52b0-142">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" 攝影者：[Jonik](https://commons.wikimedia.org/wiki/User:Jonik) \(英文\) - 自行拍攝，CC BY-SA 2.0， https://commons.wikimedia.org/w/index.php?curid=48166 \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="f52b0-142">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.</span></span>
> * <span data-ttu-id="f52b0-143">"193px-Broodrooster.jpg" 攝影者：[M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) \(英文\) - 自行創作，CC BY-SA 3.0， https://commons.wikimedia.org/w/index.php?curid=27403 \(英文\)</span><span class="sxs-lookup"><span data-stu-id="f52b0-143">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403</span></span>

<span data-ttu-id="f52b0-144">遷移學習包含幾個策略，例如「重新對所有層級進行定型」和「倒數第二個層級」。</span><span class="sxs-lookup"><span data-stu-id="f52b0-144">Transfer learning includes a few strategies, such as *retrain all layers* and *penultimate layer*.</span></span> <span data-ttu-id="f52b0-145">本教學課程將會說明並示範使用「倒數第二個層級策略」的方式。</span><span class="sxs-lookup"><span data-stu-id="f52b0-145">This tutorial will explain and show how to use the *penultimate layer strategy*.</span></span> <span data-ttu-id="f52b0-146">「倒數第二個層級策略」會重複使用已預先定型來解決某個特定問題的模型。</span><span class="sxs-lookup"><span data-stu-id="f52b0-146">The *penultimate layer strategy* reuses a model that's already been pre-trained to solve a specific problem.</span></span> <span data-ttu-id="f52b0-147">該策略接著會將模型的最終層級重新定型，來使它能解決新的問題。</span><span class="sxs-lookup"><span data-stu-id="f52b0-147">The strategy then retrains the final layer of that model to make it solve a new problem.</span></span> <span data-ttu-id="f52b0-148">重複使用預先定型的模型作為新模型的一部分，能為您省下大量的時間和資源。</span><span class="sxs-lookup"><span data-stu-id="f52b0-148">Reusing the pre-trained model as part of your new model will save significant time and resources.</span></span>

<span data-ttu-id="f52b0-149">您的影像分類模型會重複使用 [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)，這是一個以 `ImageNet` 資料集進行定型的熱門影像辨識模型，其中 TensorFlow 模型會嘗試將影像分類為一千個類別中的其中一個類別，例如「雨傘」、「球衣」和「洗碗機」。</span><span class="sxs-lookup"><span data-stu-id="f52b0-149">Your image classification model reuses the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), a popular image recognition model trained on the `ImageNet` dataset where the TensorFlow model tries to classify entire images into a thousand classes, like “Umbrella”, “Jersey”, and “Dishwasher”.</span></span>

<span data-ttu-id="f52b0-150">`Inception v1 model` 可以被分類為[深度卷積神經網路](https://en.wikipedia.org/wiki/Convolutional_neural_network) \(英文\)，且可以在困難的辨識工作上取得相當合理的效能，並在某些領域上達到與人類相符甚至超越人類的效能。</span><span class="sxs-lookup"><span data-stu-id="f52b0-150">The `Inception v1 model` can be classified as a [deep convolutional neural network](https://en.wikipedia.org/wiki/Convolutional_neural_network) and can achieve reasonable performance on hard visual recognition tasks, matching or exceeding human performance in some domains.</span></span> <span data-ttu-id="f52b0-151">該模型/演算法是由數個研究者根據下列原始論文所開發：["Rethinking the Inception Architecture for Computer Vision” by Szegedy, et. al.](https://arxiv.org/abs/1512.00567) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="f52b0-151">The model/algorithm was developed by multiple researchers and based on the original paper: ["Rethinking the Inception Architecture for Computer Vision” by Szegedy, et. al.](https://arxiv.org/abs/1512.00567)</span></span>

<span data-ttu-id="f52b0-152">由於 `Inception model` 已經搭配數以千計的不同影像預先進行定型，其包含影像識別所需的[影像特徵](https://en.wikipedia.org/wiki/Feature_(computer_vision)) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="f52b0-152">Because the `Inception model` has already been pre trained on thousands of different images, it contains the [image features](https://en.wikipedia.org/wiki/Feature_(computer_vision)) needed for image identification.</span></span> <span data-ttu-id="f52b0-153">較低的影像特徵層能辨識簡單的特徵 (例如邊緣)，而較高的層則能辨識更加複雜的特徵 (例如形狀)。</span><span class="sxs-lookup"><span data-stu-id="f52b0-153">The lower image feature layers recognize simple features (such as edges) and the higher layers recognize more complex features (such as shapes).</span></span> <span data-ttu-id="f52b0-154">最終層會針對較小許多的資料集進行定型，因為您是以已經了解如何分類影像的預先定型模型作為開始。</span><span class="sxs-lookup"><span data-stu-id="f52b0-154">The final layer is trained against a much smaller set of data because you're starting with a pre trained model that already understands how to classify images.</span></span> <span data-ttu-id="f52b0-155">隨著您的模型允許您將影像分類至兩個以上的類別，這將會成為[多類別分類器](../resources/tasks.md#multiclass-classification)的範例。</span><span class="sxs-lookup"><span data-stu-id="f52b0-155">As your model allows you to classify more than two categories, this is an example of a [multi-class classifier](../resources/tasks.md#multiclass-classification).</span></span> 

<span data-ttu-id="f52b0-156">`TensorFlow` 是熱門的深度學習及機器學習工具組，其能讓您對深度神經網路 (及一般的數值計算) 進行定型，並已實作為 ML.NET 中的 `transformer`。</span><span class="sxs-lookup"><span data-stu-id="f52b0-156">`TensorFlow` is a popular deep learning and machine learning toolkit that enables training deep neural networks (and general numeric computations), and is implemented as a `transformer` in ML.NET.</span></span> <span data-ttu-id="f52b0-157">針對本教學課程，我們會使用它來重複使用 `Inception model`。</span><span class="sxs-lookup"><span data-stu-id="f52b0-157">For this tutorial, it's used to reuse the `Inception model`.</span></span>

<span data-ttu-id="f52b0-158">如下圖所示，您會在 .NET Core 或 .NET Framework 應用程式中新增對 ML.NET NuGet 套件的參考。</span><span class="sxs-lookup"><span data-stu-id="f52b0-158">As shown in the following diagram, you add a reference to the ML.NET NuGet packages in your .NET Core or .NET Framework applications.</span></span> <span data-ttu-id="f52b0-159">實際上，ML.NET 會包含並參考原生 `TensorFlow` 程式庫，其能讓您撰寫能載入現有已定型 `TensorFlow` 模型檔案的程式碼以用於評分。</span><span class="sxs-lookup"><span data-stu-id="f52b0-159">Under the covers, ML.NET includes and references the native `TensorFlow` library that allows you to write code that loads an existing trained `TensorFlow` model file for scoring.</span></span>  

![TensorFlow 轉換 ML.NET 架構圖表](./media/image-classification/tensorflow-mlnet.png)

<span data-ttu-id="f52b0-161">`Inception model` 已針對將影像分類至一千個類別進行定型，但您只需要將影像分類至較小的類別集合，且僅分類至那些集合。</span><span class="sxs-lookup"><span data-stu-id="f52b0-161">The `Inception model` is trained to classify images into a thousand categories, but you need to classify images in a smaller category set, and only those categories.</span></span> <span data-ttu-id="f52b0-162">這就是 `transfer learning` (遷移學習) 名稱中 `transfer` (遷移) 這部分派上用場的時候。</span><span class="sxs-lookup"><span data-stu-id="f52b0-162">Enter the `transfer` part of `transfer learning`.</span></span> <span data-ttu-id="f52b0-163">您可以將 `Inception model` 辨識及分類影像的能力遷移至您自訂影像分類器新的受限類別之中。</span><span class="sxs-lookup"><span data-stu-id="f52b0-163">You can transfer the `Inception model`'s ability to recognize and classify images to the new limited categories of your custom image classifier.</span></span>  

 <span data-ttu-id="f52b0-164">您將會使用三個類別集合來對該模型的最終層進行定型：</span><span class="sxs-lookup"><span data-stu-id="f52b0-164">You're going to retrain the final layer of that model using a set of three categories:</span></span>

* <span data-ttu-id="f52b0-165">Food (食物)</span><span class="sxs-lookup"><span data-stu-id="f52b0-165">Food</span></span>
* <span data-ttu-id="f52b0-166">Toy (玩具)</span><span class="sxs-lookup"><span data-stu-id="f52b0-166">Toy</span></span>
* <span data-ttu-id="f52b0-167">Appliance (設備)</span><span class="sxs-lookup"><span data-stu-id="f52b0-167">Appliance</span></span>

<span data-ttu-id="f52b0-168">您的層會使用[多維度羅吉斯迴歸演算法](https://en.wikipedia.org/wiki/Multinomial_logistic_regression) \(英文\) 來以最快的速度找出正確的類別。</span><span class="sxs-lookup"><span data-stu-id="f52b0-168">Your layer uses a [multinomial logistic regression algorithm](https://en.wikipedia.org/wiki/Multinomial_logistic_regression) to find the correct category as quickly as possible.</span></span> <span data-ttu-id="f52b0-169">此演算法在分類時會使用機率來判斷解答，並為正確的類別提供「一」的值，然後為其餘類別提供「零」的值。</span><span class="sxs-lookup"><span data-stu-id="f52b0-169">This algorithm classifies using probabilities to determine the answer, giving a one value to the correct category and a zero value to the others.</span></span>  

### <a name="dataset"></a><span data-ttu-id="f52b0-170">資料集</span><span class="sxs-lookup"><span data-stu-id="f52b0-170">DataSet</span></span>

<span data-ttu-id="f52b0-171">有兩個資料來源：`.tsv` 檔案，以及影像檔案。</span><span class="sxs-lookup"><span data-stu-id="f52b0-171">There are two data sources: the `.tsv` file, and the image files.</span></span>  <span data-ttu-id="f52b0-172">`tags.tsv` 檔案包含兩個資料行：第一個會被定義為 `ImagePath`，而第二個則是對應至影像的 `Label`。</span><span class="sxs-lookup"><span data-stu-id="f52b0-172">The `tags.tsv` file contains two columns: the first one is defined as `ImagePath` and the second one is the `Label` corresponding to the image.</span></span> <span data-ttu-id="f52b0-173">下列範例檔案沒有標頭資料列，且看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="f52b0-173">The following example file doesn't have a header row, and looks like this:</span></span>

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

<span data-ttu-id="f52b0-174">定型及測試影像都位於您將以 zip 檔案下載的資產資料夾中。</span><span class="sxs-lookup"><span data-stu-id="f52b0-174">The training and testing images are located in the assets folders that you'll download in a zip file.</span></span> <span data-ttu-id="f52b0-175">這些影像皆由 Wikimedia Commons 所有。</span><span class="sxs-lookup"><span data-stu-id="f52b0-175">These images belong to Wikimedia Commons.</span></span>
> <span data-ttu-id="f52b0-176">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208) \(英文\), the free media repository*。</span><span class="sxs-lookup"><span data-stu-id="f52b0-176">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), the free media repository.*</span></span> <span data-ttu-id="f52b0-177">於 2018 年 10 月 17 日 10:48 擷取自：</span><span class="sxs-lookup"><span data-stu-id="f52b0-177">Retrieved 10:48, October 17, 2018 from:</span></span>  
> https://commons.wikimedia.org/wiki/Pizza  
> https://commons.wikimedia.org/wiki/Toaster  
> https://commons.wikimedia.org/wiki/Teddy_bear  

## <a name="create-a-console-application"></a><span data-ttu-id="f52b0-178">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="f52b0-178">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="f52b0-179">建立專案</span><span class="sxs-lookup"><span data-stu-id="f52b0-179">Create a project</span></span>

1. <span data-ttu-id="f52b0-180">建立稱為 "TransferLearningTF" 的 **.NET Core 主控台應用程式**。</span><span class="sxs-lookup"><span data-stu-id="f52b0-180">Create a **.NET Core Console Application** called "TransferLearningTF".</span></span>

2. <span data-ttu-id="f52b0-181">安裝「Microsoft.ML NuGet 套件」：</span><span class="sxs-lookup"><span data-stu-id="f52b0-181">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="f52b0-182">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="f52b0-182">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="f52b0-183">選擇 [nuget.org] 作為 [套件來源]，選取 [瀏覽] 索引標籤，搜尋 **Microsoft.ML**。</span><span class="sxs-lookup"><span data-stu-id="f52b0-183">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span> <span data-ttu-id="f52b0-184">按一下 [版本] 下拉式清單，選取清單中的 [1.0.0] 套件，然後選取 [安裝] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f52b0-184">Click on the **Version** drop-down, select the **1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="f52b0-185">在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。</span><span class="sxs-lookup"><span data-stu-id="f52b0-185">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="f52b0-186">針對 **Microsoft.ML.ImageAnalytics v1.0.0** 和 **Microsoft.ML.TensorFlow v0.12.0** 重複這些步驟。</span><span class="sxs-lookup"><span data-stu-id="f52b0-186">Repeat these steps for **Microsoft.ML.ImageAnalytics v1.0.0** and **Microsoft.ML.TensorFlow v0.12.0**.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="f52b0-187">準備您的資料</span><span class="sxs-lookup"><span data-stu-id="f52b0-187">Prepare your data</span></span>

1. <span data-ttu-id="f52b0-188">下載[專案資產目錄 zip 檔案](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)，然後將它解壓縮。</span><span class="sxs-lookup"><span data-stu-id="f52b0-188">Download [The project assets directory zip file](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip), and unzip.</span></span>

2. <span data-ttu-id="f52b0-189">將 `assets` 目錄複製到您的 *TransferLearningTF* 專案目錄中。</span><span class="sxs-lookup"><span data-stu-id="f52b0-189">Copy the `assets` directory into your *TransferLearningTF* project directory.</span></span> <span data-ttu-id="f52b0-190">此目錄及其子目錄包含本教學課程所需的資料和支援檔案 (Inception model 除外，您將會在下個步驟中下載並新增它)。</span><span class="sxs-lookup"><span data-stu-id="f52b0-190">This directory and its subdirectories contain the data and support files (except for the Inception model, which you'll download and add in the next step) needed for this tutorial.</span></span>

3. <span data-ttu-id="f52b0-191">下載 [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)，然後將它解壓縮。</span><span class="sxs-lookup"><span data-stu-id="f52b0-191">Download the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), and unzip.</span></span>

4. <span data-ttu-id="f52b0-192">將剛才解壓縮的 `inception5h` 目錄的內容複製到您 *TransferLearningTF* 專案的 `assets\inputs-train\inception` 目錄中。</span><span class="sxs-lookup"><span data-stu-id="f52b0-192">Copy the contents of the `inception5h` directory just unzipped into your *TransferLearningTF* project `assets\inputs-train\inception` directory.</span></span> <span data-ttu-id="f52b0-193">此目錄包含本教學課程所需的模型和其他支援檔案，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="f52b0-193">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![Inception 目錄內容](./media/image-classification/inception-files.png)

5. <span data-ttu-id="f52b0-195">在 [方案總管] 中，以滑鼠右鍵按一下資產目錄及子目錄中的每個檔案，然後選取 [內容]。</span><span class="sxs-lookup"><span data-stu-id="f52b0-195">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="f52b0-196">在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。</span><span class="sxs-lookup"><span data-stu-id="f52b0-196">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="f52b0-197">建立類別及定義路徑</span><span class="sxs-lookup"><span data-stu-id="f52b0-197">Create classes and define paths</span></span>

<span data-ttu-id="f52b0-198">在 *Program.cs* 檔案頂端新增下列額外的 `using` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="f52b0-198">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

<span data-ttu-id="f52b0-199">建個全域欄位來保留各種資產的路徑，以及 `LabelTokey`、`ImageReal` 及 `PredictedLabelValue` 的全域變數：</span><span class="sxs-lookup"><span data-stu-id="f52b0-199">Create global fields to hold the paths to the various assets, and global variables for the `LabelTokey`,`ImageReal`, and  `PredictedLabelValue`:</span></span>

* <span data-ttu-id="f52b0-200">`_assetsPath` 具有資產的路徑。</span><span class="sxs-lookup"><span data-stu-id="f52b0-200">`_assetsPath` has the path to the assets.</span></span>
* <span data-ttu-id="f52b0-201">`_trainTagsTsv` 具有定型影像資料標記 tsv 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="f52b0-201">`_trainTagsTsv` has the path to the training image data tags tsv file.</span></span>
* <span data-ttu-id="f52b0-202">`_predictTagsTsv` 具有預測影像資料標記 tsv 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="f52b0-202">`_predictTagsTsv` has the path to the prediction image data tags tsv file.</span></span>
* <span data-ttu-id="f52b0-203">`_trainImagesFolder` 具有用來將模型定型之影像的路徑。</span><span class="sxs-lookup"><span data-stu-id="f52b0-203">`_trainImagesFolder` has the path to the images used to train the model.</span></span>
* <span data-ttu-id="f52b0-204">`_predictImagesFolder` 具有要由已定型模型分類之影像的路徑。</span><span class="sxs-lookup"><span data-stu-id="f52b0-204">`_predictImagesFolder` has the path to the images to be classified by the trained model.</span></span>
* <span data-ttu-id="f52b0-205">`_inceptionPb` 具有要重複使用以重新對模型進行定型之預先定型 Inception model 的路徑。</span><span class="sxs-lookup"><span data-stu-id="f52b0-205">`_inceptionPb` has the path to the pre-trained Inception model to be reused to retrain your model.</span></span>
* <span data-ttu-id="f52b0-206">`_inputImageClassifierZip` 具有用來載入已定型模型的路徑。</span><span class="sxs-lookup"><span data-stu-id="f52b0-206">`_inputImageClassifierZip` has the path where the trained model is loaded from.</span></span>
* <span data-ttu-id="f52b0-207">`_outputImageClassifierZip` 包含用來儲存定型模型的路徑。</span><span class="sxs-lookup"><span data-stu-id="f52b0-207">`_outputImageClassifierZip` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="f52b0-208">`LabelTokey` 是對應至索引鍵的 `Label` 值。</span><span class="sxs-lookup"><span data-stu-id="f52b0-208">`LabelTokey` is the `Label` value mapped to a key.</span></span>
* <span data-ttu-id="f52b0-209">`ImageReal` 是包含已預測影像值的資料行。</span><span class="sxs-lookup"><span data-stu-id="f52b0-209">`ImageReal`  is the column containing the predicted image value.</span></span>
* <span data-ttu-id="f52b0-210">`PredictedLabelValue` 是包含已預測標籤值的資料行。</span><span class="sxs-lookup"><span data-stu-id="f52b0-210">`PredictedLabelValue` is the column containing the predicted label value.</span></span>

<span data-ttu-id="f52b0-211">將下列程式碼新增至 `Main` 方法正上方的一行，以指定這些路徑和其他變數：</span><span class="sxs-lookup"><span data-stu-id="f52b0-211">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="f52b0-212">為輸入資料和預測建立一些類別。</span><span class="sxs-lookup"><span data-stu-id="f52b0-212">Create some classes for your input data, and predictions.</span></span> <span data-ttu-id="f52b0-213">將新類別新增至專案：</span><span class="sxs-lookup"><span data-stu-id="f52b0-213">Add a new class to your project:</span></span>

1. <span data-ttu-id="f52b0-214">在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="f52b0-214">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="f52b0-215">在 [加入新項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *ImageData.cs*。</span><span class="sxs-lookup"><span data-stu-id="f52b0-215">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageData.cs*.</span></span> <span data-ttu-id="f52b0-216">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f52b0-216">Then, select the **Add** button.</span></span>

    <span data-ttu-id="f52b0-217">*ImageData.cs* 檔案隨即在程式碼編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="f52b0-217">The *ImageData.cs* file opens in the code editor.</span></span> <span data-ttu-id="f52b0-218">將下列 `using` 陳述式新增至 *ImageData.cs* 最上方：</span><span class="sxs-lookup"><span data-stu-id="f52b0-218">Add the following `using` statement to the top of *ImageData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#AddUsings)]

<span data-ttu-id="f52b0-219">移除現有的類別定義，然後將下列適用於 `ImageData` 類別的程式碼新增至 *ImageData.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="f52b0-219">Remove the existing class definition and add the following code for the `ImageData` class to the *ImageData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#DeclareTypes)]

<span data-ttu-id="f52b0-220">`ImageData` 是輸入資料集類別，並具有下列 <xref:System.String> 欄位：</span><span class="sxs-lookup"><span data-stu-id="f52b0-220">`ImageData` is the input image data class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="f52b0-221">`ImagePath` 包含影像檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="f52b0-221">`ImagePath` contains the image file name.</span></span>
* <span data-ttu-id="f52b0-222">`Label` 包含影像標籤的值。</span><span class="sxs-lookup"><span data-stu-id="f52b0-222">`Label` contains a value for the image label.</span></span>

<span data-ttu-id="f52b0-223">將新類別新增至 `ImagePrediction` 的專案：</span><span class="sxs-lookup"><span data-stu-id="f52b0-223">Add a new class to your project for `ImagePrediction`:</span></span>

1. <span data-ttu-id="f52b0-224">在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="f52b0-224">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="f52b0-225">在 [加入新項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *ImagePrediction.cs*。</span><span class="sxs-lookup"><span data-stu-id="f52b0-225">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImagePrediction.cs*.</span></span> <span data-ttu-id="f52b0-226">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f52b0-226">Then, select the **Add** button.</span></span>

    <span data-ttu-id="f52b0-227">*ImagePrediction.cs* 檔案隨即在程式碼編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="f52b0-227">The *ImagePrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="f52b0-228">移除 *ImagePrediction.cs* 頂端的 `System.Collections.Generic` 和 `System.Text` `using` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="f52b0-228">Remove both the `System.Collections.Generic` and the `System.Text` `using` statements at the top of *ImagePrediction.cs*:</span></span>

<span data-ttu-id="f52b0-229">移除現有的類別定義，然後將下列程式碼 (其具有 `ImagePrediction` 類別) 新增至 *ImagePrediction.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="f52b0-229">Remove the existing class definition and add the following code, which has the `ImagePrediction` class, to the *ImagePrediction.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/ImagePrediction.cs#DeclareTypes)]

<span data-ttu-id="f52b0-230">`ImagePrediction` 是影像預測類別，並具有下列欄位：</span><span class="sxs-lookup"><span data-stu-id="f52b0-230">`ImagePrediction` is the image prediction class and has the following fields:</span></span>

* <span data-ttu-id="f52b0-231">`Score` 包含指定影像分類的信賴百分比。</span><span class="sxs-lookup"><span data-stu-id="f52b0-231">`Score` contains the confidence percentage for a given image classification.</span></span>
* <span data-ttu-id="f52b0-232">`PredictedLabelValue` 包含已預測影像分類標籤的值。</span><span class="sxs-lookup"><span data-stu-id="f52b0-232">`PredictedLabelValue` contains a value for the predicted image classification label.</span></span>

<span data-ttu-id="f52b0-233">`ImagePrediction` 是在模型定型後，用來進行預測的類別。</span><span class="sxs-lookup"><span data-stu-id="f52b0-233">`ImagePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="f52b0-234">它具有影像路徑的 `string` (`ImagePath`)。</span><span class="sxs-lookup"><span data-stu-id="f52b0-234">It has a `string` (`ImagePath`) for the image path.</span></span> <span data-ttu-id="f52b0-235">`Label` 會被用來進行模型的重複使用和重新定型。</span><span class="sxs-lookup"><span data-stu-id="f52b0-235">The `Label` is used to reuse and retrain the model.</span></span> <span data-ttu-id="f52b0-236">`PredictedLabelValue` 的使用時機是在進行預測和評估的期間。</span><span class="sxs-lookup"><span data-stu-id="f52b0-236">The `PredictedLabelValue` is used during prediction and evaluation.</span></span> <span data-ttu-id="f52b0-237">就評估而言，會使用含有定型資料、預設值及模型的輸入。</span><span class="sxs-lookup"><span data-stu-id="f52b0-237">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="f52b0-238">[MLContext 類別](xref:Microsoft.ML.MLContext)是所有 ML.NET 作業的起點，且初始化 `mlContext` 會建立新的 ML.NET 環境，其可在模型建立工作流程物件之間共用。</span><span class="sxs-lookup"><span data-stu-id="f52b0-238">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="f52b0-239">就概念而言，類似於 Entity Framework 中的 `DBContext`。</span><span class="sxs-lookup"><span data-stu-id="f52b0-239">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="f52b0-240">在 Main 中初始化變數</span><span class="sxs-lookup"><span data-stu-id="f52b0-240">Initialize variables in Main</span></span>

<span data-ttu-id="f52b0-241">搭配 `MLContext` 的新執行個體來初始化 `mlContext` 變數。</span><span class="sxs-lookup"><span data-stu-id="f52b0-241">Initialize the `mlContext` variable with a new instance of `MLContext`.</span></span>  <span data-ttu-id="f52b0-242">在 `Main` 方法中，以下列程式碼取代 `Console.WriteLine("Hello World!")`：</span><span class="sxs-lookup"><span data-stu-id="f52b0-242">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

### <a name="create-a-struct-for-default-parameters"></a><span data-ttu-id="f52b0-243">建立適用於預設參數的結構</span><span class="sxs-lookup"><span data-stu-id="f52b0-243">Create a struct for default parameters</span></span>

<span data-ttu-id="f52b0-244">Inception model 具有數個您需要傳遞的預設參數。</span><span class="sxs-lookup"><span data-stu-id="f52b0-244">The Inception model has several default parameters you need to pass in.</span></span> <span data-ttu-id="f52b0-245">在 `Main()` 方法正後方使用下列程式碼來建立結構，以將預設參數值對應至易記名稱：</span><span class="sxs-lookup"><span data-stu-id="f52b0-245">Create a struct to map the default parameter values to friendly names with the following code, just after the `Main()` method:</span></span>

[!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a><span data-ttu-id="f52b0-246">建立顯示公用程式方法</span><span class="sxs-lookup"><span data-stu-id="f52b0-246">Create a display utility method</span></span>

<span data-ttu-id="f52b0-247">因為您將會不只一次顯示影像資料和相關預測，所以請建立顯示公用程式方法來處理顯示影像和預測結果。</span><span class="sxs-lookup"><span data-stu-id="f52b0-247">Since you'll display the image data and the related predictions more than once, create a display utility method to handle displaying the image and prediction results.</span></span>

<span data-ttu-id="f52b0-248">`DisplayResults()` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="f52b0-248">The `DisplayResults()` method executes the following tasks:</span></span>

* <span data-ttu-id="f52b0-249">顯示預測的結果。</span><span class="sxs-lookup"><span data-stu-id="f52b0-249">Displays the predicted results.</span></span>

<span data-ttu-id="f52b0-250">使用下列程式碼，在緊接著 `InceptionSettings` 結構之後，建立 `DisplayResults()` 方法：</span><span class="sxs-lookup"><span data-stu-id="f52b0-250">Create the `DisplayResults()` method, just after the `InceptionSettings` struct, using the following code:</span></span>

```csharp
private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
{

}
```

<span data-ttu-id="f52b0-251">`Transform()` 方法會在 `ImagePrediction` 及預測欄位中填入 `ImagePath`。</span><span class="sxs-lookup"><span data-stu-id="f52b0-251">The `Transform()` method populated `ImagePath` in `ImagePrediction` along with the predicted fields.</span></span> <span data-ttu-id="f52b0-252">隨著 ML.NET 處理的進行，每個元件都會新增資料行，使其易於顯示結果：</span><span class="sxs-lookup"><span data-stu-id="f52b0-252">As the ML.NET process progresses, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

<span data-ttu-id="f52b0-253">您將會在兩個影像分類方法中呼叫 `DisplayResults()` 方法。</span><span class="sxs-lookup"><span data-stu-id="f52b0-253">You'll call the `DisplayResults()` method in the two image classification methods.</span></span>

### <a name="create-a-tsv-file-utility-method"></a><span data-ttu-id="f52b0-254">建立 .tsv 檔案公用程式方法</span><span class="sxs-lookup"><span data-stu-id="f52b0-254">Create a .tsv file utility method</span></span>

<span data-ttu-id="f52b0-255">`ReadFromTsv()` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="f52b0-255">The `ReadFromTsv()` method executes the following tasks:</span></span>

* <span data-ttu-id="f52b0-256">讀取影像資料 `tags.tsv` 檔案。</span><span class="sxs-lookup"><span data-stu-id="f52b0-256">Reads the image data `tags.tsv` file.</span></span>
* <span data-ttu-id="f52b0-257">將檔案路徑新增至影像檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="f52b0-257">Adds the file path to the image file name.</span></span>
* <span data-ttu-id="f52b0-258">將檔案資料載入 IEnumerable`ImageData` 物件。</span><span class="sxs-lookup"><span data-stu-id="f52b0-258">Loads the file data into an IEnumerable`ImageData` object.</span></span>

<span data-ttu-id="f52b0-259">請使用下列程式碼，在緊接著 `PairAndDisplayResults()` 方法之後，建立 `ReadFromTsv()` 方法：</span><span class="sxs-lookup"><span data-stu-id="f52b0-259">Create the `ReadFromTsv()` method, just after the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
{

}
```

<span data-ttu-id="f52b0-260">下列程式碼會剖析 `tags.tsv` 檔案以新增 `ImagePath` 屬性之影像檔案名稱的檔案路徑，然後將它和 `Label` 載入 `ImageData` 物件。</span><span class="sxs-lookup"><span data-stu-id="f52b0-260">The following code parses through the `tags.tsv` file to add the file path to the image file name for the `ImagePath` property and load it and the `Label` into an `ImageData` object.</span></span> <span data-ttu-id="f52b0-261">將它新增為 `ReadFromTsv()` 方法的第一行。</span><span class="sxs-lookup"><span data-stu-id="f52b0-261">Add it as the first line of the `ReadFromTsv()` method.</span></span>  <span data-ttu-id="f52b0-262">您需要完整的檔案路徑以顯示預測結果。</span><span class="sxs-lookup"><span data-stu-id="f52b0-262">You need the fully qualified file path to display the prediction results.</span></span>

[!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]
<span data-ttu-id="f52b0-263">ML.NET 有三個主要概念：[資料](../resources/glossary.md#data)、[轉換器](../resources/glossary.md#transformer)以及[估算工具](../resources/glossary.md#estimator)。</span><span class="sxs-lookup"><span data-stu-id="f52b0-263">There are three major concepts in ML.NET: [Data](../resources/glossary.md#data), [Transformers](../resources/glossary.md#transformer), and [Estimators](../resources/glossary.md#estimator).</span></span>

## <a name="reuse-and-tune-pre-trained-model"></a><span data-ttu-id="f52b0-264">重複使用並調整預先定型的模型</span><span class="sxs-lookup"><span data-stu-id="f52b0-264">Reuse and tune pre-trained model</span></span>

<span data-ttu-id="f52b0-265">將下列呼叫新增至 `ReuseAndTuneInceptionModel()` 方法作為 `Main()` 方法中的下一行程式碼：</span><span class="sxs-lookup"><span data-stu-id="f52b0-265">Add the following call to the `ReuseAndTuneInceptionModel()`method as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallReuseAndTuneInceptionModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReuseAndTuneInceptionModel)]

<span data-ttu-id="f52b0-266">`ReuseAndTuneInceptionModel()` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="f52b0-266">The `ReuseAndTuneInceptionModel()` method executes the following tasks:</span></span>

* <span data-ttu-id="f52b0-267">載入資料</span><span class="sxs-lookup"><span data-stu-id="f52b0-267">Loads the data</span></span>
* <span data-ttu-id="f52b0-268">擷取並轉換資料。</span><span class="sxs-lookup"><span data-stu-id="f52b0-268">Extracts and transforms the data.</span></span>
* <span data-ttu-id="f52b0-269">為 TensorFlow 模型評分。</span><span class="sxs-lookup"><span data-stu-id="f52b0-269">Scores the TensorFlow model.</span></span>
* <span data-ttu-id="f52b0-270">調整 (重新定型) 模型。</span><span class="sxs-lookup"><span data-stu-id="f52b0-270">Tunes (retrains) the model.</span></span>
* <span data-ttu-id="f52b0-271">顯示模型結果。</span><span class="sxs-lookup"><span data-stu-id="f52b0-271">Displays model results.</span></span>
* <span data-ttu-id="f52b0-272">評估模型。</span><span class="sxs-lookup"><span data-stu-id="f52b0-272">Evaluates the model.</span></span>
* <span data-ttu-id="f52b0-273">傳回模型。</span><span class="sxs-lookup"><span data-stu-id="f52b0-273">Returns the model.</span></span>

<span data-ttu-id="f52b0-274">使用下列程式碼，緊接在 `InceptionSettings` 結構之後及 `DisplayResults()` 方法之前，建立 `ReuseAndTuneInceptionModel()` 方法：</span><span class="sxs-lookup"><span data-stu-id="f52b0-274">Create the `ReuseAndTuneInceptionModel()` method, just after the `InceptionSettings` struct and just before the `DisplayResults()` method, using the following code:</span></span>

```csharp
public static ITransformer ReuseAndTuneInceptionModel(MLContext mlContext, string dataLocation, string imagesFolder, string inputModelLocation, string outputModelLocation)
{

}
```

### <a name="load-the-data"></a><span data-ttu-id="f52b0-275">載入資料</span><span class="sxs-lookup"><span data-stu-id="f52b0-275">Load the data</span></span>

<span data-ttu-id="f52b0-276">ML.NET 中的資料以 [IDataView 類別](xref:Microsoft.ML.IDataView) 表示。</span><span class="sxs-lookup"><span data-stu-id="f52b0-276">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="f52b0-277">`IDataView` 是彈性且有效率的表格式資料描述方式 (數值和文字)。</span><span class="sxs-lookup"><span data-stu-id="f52b0-277">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="f52b0-278">資料可以從文字或即時 (例如 SQL 資料庫或記錄檔) 載入至 `IDataView` 物件。</span><span class="sxs-lookup"><span data-stu-id="f52b0-278">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="f52b0-279">使用 `MLContext.Data.LoadFromTextFile` 包裝函式載入資料。</span><span class="sxs-lookup"><span data-stu-id="f52b0-279">Load the data using the `MLContext.Data.LoadFromTextFile` wrapper.</span></span> <span data-ttu-id="f52b0-280">將下列程式碼加入為 `ReuseAndTuneInceptionModel()` 方法中的下一行：</span><span class="sxs-lookup"><span data-stu-id="f52b0-280">Add the following code as the next line in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

### <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="f52b0-281">擷取 Features 並傳輸資料</span><span class="sxs-lookup"><span data-stu-id="f52b0-281">Extract Features and transform the data</span></span>

<span data-ttu-id="f52b0-282">資料前處理和清除是相當重要的工作，發生在有效地使用資料集來進行機器學習之前。</span><span class="sxs-lookup"><span data-stu-id="f52b0-282">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span>  <span data-ttu-id="f52b0-283">使用資料時，如果未進行這些模型化工作，可能會產生誤導的結果。</span><span class="sxs-lookup"><span data-stu-id="f52b0-283">Using data without these modeling tasks can produce misleading results.</span></span>

<span data-ttu-id="f52b0-284">機器學習演算法能了解[特徵化](../resources/glossary.md#feature)的資料，且在處理深度神經網路時，您必須將影像調整為網路所預期的格式。</span><span class="sxs-lookup"><span data-stu-id="f52b0-284">Machine learning algorithms understand [featurized](../resources/glossary.md#feature) data, and when dealing with deep neural networks you must adapt the images to the format expected by the network.</span></span> <span data-ttu-id="f52b0-285">該格式為[數值向量](../resources/glossary.md#numerical-feature-vector)。</span><span class="sxs-lookup"><span data-stu-id="f52b0-285">That format is a [numeric vector](../resources/glossary.md#numerical-feature-vector).</span></span>

<span data-ttu-id="f52b0-286">在定型和評估之後，搭配 [標籤] 資料行值進行預測。</span><span class="sxs-lookup"><span data-stu-id="f52b0-286">After training and evaluation, predict with the **Label** column values.</span></span> <span data-ttu-id="f52b0-287">由於您是使用預先定型的模型，請使用 [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) 方法將藍為對應至新的模型。</span><span class="sxs-lookup"><span data-stu-id="f52b0-287">As you're using a pre-trained model, map fields to the new model with the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method.</span></span> <span data-ttu-id="f52b0-288">此方法會將 `Label` 轉換為數值索引鍵類型 (`LabelTokey`) 的資料行，並將它新增為新的資料集資料行：請為此 `estimator` 命名，因為您也會為它新增定型器。</span><span class="sxs-lookup"><span data-stu-id="f52b0-288">This method transforms the `Label` into a numeric key type (`LabelTokey`) column and add it as new dataset column:  Name this `estimator` as you'll also add the trainer to it.</span></span> <span data-ttu-id="f52b0-289">新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="f52b0-289">Add the next line of code:</span></span>

[!code-csharp[MapValueToKey1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey1)]

<span data-ttu-id="f52b0-290">您的影像處理估算工具會使用預先定型的[深度神經網路 (DNN)](https://en.wikipedia.org/wiki/Deep_learning#Deep_neural_networks) 特徵化工具來擷取特徵。</span><span class="sxs-lookup"><span data-stu-id="f52b0-290">Your image processing estimator uses pre-trained [Deep Neural Network(DNN)](https://en.wikipedia.org/wiki/Deep_learning#Deep_neural_networks) featurizers for feature extraction.</span></span> <span data-ttu-id="f52b0-291">處理深度神經網路時，您必須將影像調整為預期的網路格式。</span><span class="sxs-lookup"><span data-stu-id="f52b0-291">When dealing with deep neural networks, you  adapt the images to the expected network format.</span></span> <span data-ttu-id="f52b0-292">這就是為何您會使用數種影像轉換，來將影像資料轉換為模型預期的形式：</span><span class="sxs-lookup"><span data-stu-id="f52b0-292">This is the reason you use several image transforms to get the image data into the model's expected form:</span></span>

1. <span data-ttu-id="f52b0-293">`LoadImages` 轉換所處理的影像，會以點陣圖類型的形式載入記憶體。</span><span class="sxs-lookup"><span data-stu-id="f52b0-293">The `LoadImages`transform images are loaded in memory as a Bitmap type.</span></span>
2. <span data-ttu-id="f52b0-294">`ResizeImages` 轉換會調整影像大小，因為預先定型的模組具有已定義的輸入影像寬度和高度。</span><span class="sxs-lookup"><span data-stu-id="f52b0-294">The `ResizeImages` transform resizes the images as the pre-trained model has a defined input image width and height.</span></span>
3. <span data-ttu-id="f52b0-295">`ExtractPixels` 轉換會從輸入影像擷取像素，並將它們轉換成數值向量。</span><span class="sxs-lookup"><span data-stu-id="f52b0-295">The `ExtractPixels` transform extracts the pixels from the input images and converts them into a numeric vector.</span></span>

<span data-ttu-id="f52b0-296">將這些影像轉換新增為後續的程式碼行：</span><span class="sxs-lookup"><span data-stu-id="f52b0-296">Add these image transforms as the next lines of code:</span></span>

[!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

<span data-ttu-id="f52b0-297">`LoadTensorFlowModel` 是一種便利方法，允許載入 `TensorFlow` 模型一次，接著便會使用 `ScoreTensorFlowModel` 建立 `TensorFlowEstimator`。</span><span class="sxs-lookup"><span data-stu-id="f52b0-297">The `LoadTensorFlowModel` is a convenience method that allows the `TensorFlow` model to be loaded once and then creates the `TensorFlowEstimator` using `ScoreTensorFlowModel`.</span></span> <span data-ttu-id="f52b0-298">`ScoreTensorFlowModel` 會擷取指定的輸出 (`Inception model` 的影像特徵 `softmax2_pre_activation`)，並使用預先定型的 `TensorFlow` 模型為資料集評分。</span><span class="sxs-lookup"><span data-stu-id="f52b0-298">The `ScoreTensorFlowModel` extracts specified outputs (the `Inception model`'s image features `softmax2_pre_activation`), and scores a dataset using the pre-trained `TensorFlow` model.</span></span>

<span data-ttu-id="f52b0-299">`softmax2_pre_activation` 會透過判斷影像所屬的類別來協助模型。</span><span class="sxs-lookup"><span data-stu-id="f52b0-299">`softmax2_pre_activation` assists the model with determining which class the images belongs to.</span></span> <span data-ttu-id="f52b0-300">`softmax2_pre_activation` 會傳回每個類別適用於某個影像的機率，且那些機率的總和必須為 1。</span><span class="sxs-lookup"><span data-stu-id="f52b0-300">`softmax2_pre_activation` returns a probability for each of the categories for an image, and all of those probabilities must add up to 1.</span></span> <span data-ttu-id="f52b0-301">它假設某個影像將會僅屬於單一類別，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="f52b0-301">It assumes that an image will belong to only one category, as shown in the following example:</span></span>

| <span data-ttu-id="f52b0-302">類別</span><span class="sxs-lookup"><span data-stu-id="f52b0-302">Class</span></span>         | <span data-ttu-id="f52b0-303">機率</span><span class="sxs-lookup"><span data-stu-id="f52b0-303">Probability</span></span>   |
| ------------- | ------------- |
| `Food`        |  <span data-ttu-id="f52b0-304">0.001</span><span class="sxs-lookup"><span data-stu-id="f52b0-304">0.001</span></span>        |
| `Toy`         |  <span data-ttu-id="f52b0-305">0.95</span><span class="sxs-lookup"><span data-stu-id="f52b0-305">0.95</span></span>         |
| `Appliance`   |  <span data-ttu-id="f52b0-306">0.06</span><span class="sxs-lookup"><span data-stu-id="f52b0-306">0.06</span></span>         |

<span data-ttu-id="f52b0-307">搭配下列程式碼將 `TensorFlowTransform` 附加至 `estimator`：</span><span class="sxs-lookup"><span data-stu-id="f52b0-307">Append the `TensorFlowTransform` to the `estimator` with the following line of code:</span></span>

[!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

### <a name="choose-a-training-algorithm"></a><span data-ttu-id="f52b0-308">選擇的定型演算法</span><span class="sxs-lookup"><span data-stu-id="f52b0-308">Choose a training algorithm</span></span>

<span data-ttu-id="f52b0-309">若要新增定型演算法，請呼叫 `mlContext.MulticlassClassification.Trainers.LbfgsMaximumEntropy()` 包裝函式方法。</span><span class="sxs-lookup"><span data-stu-id="f52b0-309">To add the training algorithm, call the `mlContext.MulticlassClassification.Trainers.LbfgsMaximumEntropy()` wrapper method.</span></span>  <span data-ttu-id="f52b0-310">[LbfgsMaximumEntropy](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer) 會附加到 `estimator`，並接受 Inception 影像特徵 (`softmax2_pre_activation`) 及 `Label` 輸入參數來從歷史資料學習。</span><span class="sxs-lookup"><span data-stu-id="f52b0-310">The [LbfgsMaximumEntropy](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer) is appended to the `estimator` and accepts the Inception image features (`softmax2_pre_activation`) and the `Label` input parameters to learn from the historic data.</span></span>  <span data-ttu-id="f52b0-311">使用下列程式碼來新增定型器：</span><span class="sxs-lookup"><span data-stu-id="f52b0-311">Add the trainer with the following code:</span></span>

[!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

<span data-ttu-id="f52b0-312">您也必須將 `predictedlabel` 對應至 `predictedlabelvalue`：</span><span class="sxs-lookup"><span data-stu-id="f52b0-312">You also need to map the `predictedlabel` to the `predictedlabelvalue`:</span></span>

[!code-csharp[MapValueToKey2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey2)]

<span data-ttu-id="f52b0-313">`Fit()` 方法會透過轉換資料集及套用定型，來定型您的模型。</span><span class="sxs-lookup"><span data-stu-id="f52b0-313">The `Fit()` method trains your model by transforming the dataset and applying the training.</span></span> <span data-ttu-id="f52b0-314">將下列內容新增為 `ReuseAndTuneInceptionModel()` 方法中的下一行程式碼，調整模型使其符合定型資料集，並傳回已定型的模型：</span><span class="sxs-lookup"><span data-stu-id="f52b0-314">Fit the model to the training dataset and return the trained model by adding the following as the next line of code in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

<span data-ttu-id="f52b0-315">[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) 方法會對測試資料集之多個提供的輸入資料列進行預測。</span><span class="sxs-lookup"><span data-stu-id="f52b0-315">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for multiple provided input rows of a test dataset.</span></span>  <span data-ttu-id="f52b0-316">將下列程式碼新增至 `ReuseAndTuneInceptionModel()` 以轉換 `Training` 資料：</span><span class="sxs-lookup"><span data-stu-id="f52b0-316">Transform the `Training` data by adding the following code to `ReuseAndTuneInceptionModel()`:</span></span>

[!code-csharp[TransformData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TransformData)]

<span data-ttu-id="f52b0-317">將您的影像資料和預測 `DataViews` 轉換為強類型的 `IEnumerables` 以配對並輕鬆顯示。</span><span class="sxs-lookup"><span data-stu-id="f52b0-317">Convert your image data and prediction `DataViews` into strongly-typed `IEnumerables` to pair for easier display.</span></span> <span data-ttu-id="f52b0-318">若要這麼做，請搭配下列程式碼使用 `MLContext.CreateEnumerable()` 方法：</span><span class="sxs-lookup"><span data-stu-id="f52b0-318">Use the `MLContext.CreateEnumerable()` method to do that, using the following code:</span></span>

[!code-csharp[EnumerateDataViews](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#EnumerateDataViews)]

<span data-ttu-id="f52b0-319">呼叫 `DisplayResults()` 方法來顯示您的資料和預測，作為 `ReuseAndTuneInceptionModel()` 方法中的下一行：</span><span class="sxs-lookup"><span data-stu-id="f52b0-319">Call the `DisplayResults()` method to display your data and predictions as the next line in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[CallDisplayResults1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults1)]

<span data-ttu-id="f52b0-320">當您具有預測之後，請設定 [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) 方法：</span><span class="sxs-lookup"><span data-stu-id="f52b0-320">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method:</span></span>

* <span data-ttu-id="f52b0-321">評估模型 (將預測的值與實際的資料集 `Labels` 比較)。</span><span class="sxs-lookup"><span data-stu-id="f52b0-321">Assesses the model (compares the predicted values with the actual dataset `Labels`).</span></span>

* <span data-ttu-id="f52b0-322">傳回模型效能計量。</span><span class="sxs-lookup"><span data-stu-id="f52b0-322">Returns the model performance metrics.</span></span>

<span data-ttu-id="f52b0-323">將下列程式碼加入 `ReuseAndTuneInceptionModel()` 方法中作為的下一行：</span><span class="sxs-lookup"><span data-stu-id="f52b0-323">Add the following code to the `ReuseAndTuneInceptionModel()` method as the next line:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

<span data-ttu-id="f52b0-324">下列計量會針對影像分類進行評估：</span><span class="sxs-lookup"><span data-stu-id="f52b0-324">The following metrics are evaluated for image classification:</span></span>

* <span data-ttu-id="f52b0-325">`Log-loss`：請參閱[記錄檔遺失](../resources/glossary.md#log-loss)。</span><span class="sxs-lookup"><span data-stu-id="f52b0-325">`Log-loss` - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="f52b0-326">建議讓記錄檔遺失盡量接近零。</span><span class="sxs-lookup"><span data-stu-id="f52b0-326">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="f52b0-327">`Per class Log-loss`.</span><span class="sxs-lookup"><span data-stu-id="f52b0-327">`Per class Log-loss`.</span></span> <span data-ttu-id="f52b0-328">建議讓每個類別的記錄檔遺失盡量接近零。</span><span class="sxs-lookup"><span data-stu-id="f52b0-328">You want per class Log-loss to be as close to zero as possible.</span></span>

<span data-ttu-id="f52b0-329">使用下列程式碼來顯示計量、共用結果，然後依結果採取動作：</span><span class="sxs-lookup"><span data-stu-id="f52b0-329">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

 <span data-ttu-id="f52b0-330">新增下列程式碼來將定型後的模型作為下一行傳回：</span><span class="sxs-lookup"><span data-stu-id="f52b0-330">Add the following code to return the trained model as the next line:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReturnModel)]

## <a name="classify-images-with-a-loaded-model"></a><span data-ttu-id="f52b0-331">搭配已載入的模型分類影像</span><span class="sxs-lookup"><span data-stu-id="f52b0-331">Classify images with a loaded model</span></span>

<span data-ttu-id="f52b0-332">將下列呼叫新增至 `ClassifyImages()` 方法作為 `Main` 方法中的下一行程式碼：</span><span class="sxs-lookup"><span data-stu-id="f52b0-332">Add the following call to the `ClassifyImages()` method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallClassifyImages](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifyImages)]

<span data-ttu-id="f52b0-333">`ClassifyImages()` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="f52b0-333">The `ClassifyImages()` method executes the following tasks:</span></span>

* <span data-ttu-id="f52b0-334">將 .TSV 檔案讀取至 `IEnumerable`。</span><span class="sxs-lookup"><span data-stu-id="f52b0-334">Reads .TSV file into `IEnumerable`.</span></span>
* <span data-ttu-id="f52b0-335">根據測試資料預測影像分類。</span><span class="sxs-lookup"><span data-stu-id="f52b0-335">Predicts image classifications based on test data.</span></span>

<span data-ttu-id="f52b0-336">使用下列程式碼，緊接在 `ReuseAndTuneInceptionModel()` 方法之後及 `PairAndDisplayResults()` 方法之前，建立 `ClassifyImages()` 方法：</span><span class="sxs-lookup"><span data-stu-id="f52b0-336">Create the `ClassifyImages()` method, just after the `ReuseAndTuneInceptionModel()` method and just before the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static void ClassifyImages(MLContext mlContext, string dataLocation, string imagesFolder, string outputModelLocation, ITransformer model)
{

}
```

<span data-ttu-id="f52b0-337">首先，呼叫 `ReadFromTsv()` 方法來建立 `IEnumerable<ImageData>` 類別，其中包含每個 `ImagePath` 的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="f52b0-337">First, call the `ReadFromTsv()` method to create an `IEnumerable<ImageData>` class that contains the fully qualified path for each `ImagePath`.</span></span> <span data-ttu-id="f52b0-338">您需要該檔案路徑來配對資料與預測結果。</span><span class="sxs-lookup"><span data-stu-id="f52b0-338">You need that file path to pair your data and prediction results.</span></span> <span data-ttu-id="f52b0-339">您也需要將 `IEnumerable<ImageData>` 類別轉換為將用來進行預測的 `IDataView`。</span><span class="sxs-lookup"><span data-stu-id="f52b0-339">You also need to convert the `IEnumerable<ImageData>` class to an `IDataView` that you will use to predict.</span></span> <span data-ttu-id="f52b0-340">將下列程式碼新增為 `ClassifyImages()` 方法中的下兩行：</span><span class="sxs-lookup"><span data-stu-id="f52b0-340">Add the following code as the next two lines in the `ClassifyImages()` method:</span></span>

[!code-csharp[CallReadFromTSV](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReadFromTSV)]

<span data-ttu-id="f52b0-341">和您先前針對定型影像資料所做的相同，請使用傳入模型的 [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) 方法來預測測試影像資料的類別。</span><span class="sxs-lookup"><span data-stu-id="f52b0-341">As you did previously with the training image data, predict the category of the test image data using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method of the model passed in.</span></span> <span data-ttu-id="f52b0-342">將下列程式碼新增至 `ClassifyImages()` 方法以取得預測，並將 `predictions` `IDataView` 轉換為 `IEnumerable` 以進行配對及顯示：</span><span class="sxs-lookup"><span data-stu-id="f52b0-342">Add the following code to the `ClassifyImages()` method for the predictions and to convert the `predictions` `IDataView` into an `IEnumerable` for pairing and display:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Predict)]

<span data-ttu-id="f52b0-343">若要配對及顯示您的測試影像資料和預測，請將下列程式碼新增為 `ClassifyImages()` 方法中的下一行，以呼叫先前所建立的 `DisplayResults()` 方法：</span><span class="sxs-lookup"><span data-stu-id="f52b0-343">To pair and display your test image data and predictions, add the following code to call the `DisplayResults()` method previously created as the next line in the `ClassifyImages()` method:</span></span>

[!code-csharp[CallDisplayResults2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults2)]

## <a name="classify-a-single-image-with-a-loaded-model"></a><span data-ttu-id="f52b0-344">搭配已載入的模型分類單一影像</span><span class="sxs-lookup"><span data-stu-id="f52b0-344">Classify a single image with a loaded model</span></span>

<span data-ttu-id="f52b0-345">將下列呼叫新增至 `ClassifySingleImage()` 方法作為 `Main` 方法中的下一行程式碼：</span><span class="sxs-lookup"><span data-stu-id="f52b0-345">Add the following call to the `ClassifySingleImage()` method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

<span data-ttu-id="f52b0-346">`ClassifySingleImage()` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="f52b0-346">The `ClassifySingleImage()` method executes the following tasks:</span></span>

* <span data-ttu-id="f52b0-347">載入 `ImageData` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="f52b0-347">Loads an `ImageData` instance.</span></span>
* <span data-ttu-id="f52b0-348">根據測試資料預測影像分類。</span><span class="sxs-lookup"><span data-stu-id="f52b0-348">Predicts image classification based on test data.</span></span>

<span data-ttu-id="f52b0-349">使用下列程式碼，緊接在 `ClassifyImages()` 方法之後及 `PairAndDisplayResults()` 方法之前，建立 `ClassifySingleImage()` 方法：</span><span class="sxs-lookup"><span data-stu-id="f52b0-349">Create the `ClassifySingleImage()` method, just after the `ClassifyImages()` method and just before the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static void ClassifySingleImage(MLContext mlContext, string imagePath, string outputModelLocation, ITransformer model)
{

}
```

<span data-ttu-id="f52b0-350">首先，建立包含單一 `ImagePath` 完整路徑和影像檔案名稱的 `ImageData` 類別。</span><span class="sxs-lookup"><span data-stu-id="f52b0-350">First, create an `ImageData` class that contains the fully qualified path and image file name for the single `ImagePath`.</span></span> <span data-ttu-id="f52b0-351">將下列程式碼新增為 `ClassifySingleImage()` 方法中的下一行：</span><span class="sxs-lookup"><span data-stu-id="f52b0-351">Add the following code as the next  lines in the `ClassifySingleImage()` method:</span></span>

[!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

<span data-ttu-id="f52b0-352">[PredictionEngine 類別](xref:Microsoft.ML.PredictionEngine%602)是能針對單一資料執行個體執行預測的方便 API。</span><span class="sxs-lookup"><span data-stu-id="f52b0-352">The [PredictionEngine class](xref:Microsoft.ML.PredictionEngine%602) is a convenience API that performs a prediction on a single instance of data.</span></span> <span data-ttu-id="f52b0-353">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) 函式會在資料的單一資料行進行預測。</span><span class="sxs-lookup"><span data-stu-id="f52b0-353">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single column of data.</span></span> <span data-ttu-id="f52b0-354">將下列程式碼新增至 `ClassifySingleImage()` 來將 `imageData` 傳遞至 `PredictionEngine` 以預測影像類別：</span><span class="sxs-lookup"><span data-stu-id="f52b0-354">Pass `imageData` to the `PredictionEngine` to predict the image category by adding the following code to `ClassifySingleImage()`:</span></span>

[!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

<span data-ttu-id="f52b0-355">將預測結果顯示為 `ClassifySingleImage()` 方法中的下一行程式碼：</span><span class="sxs-lookup"><span data-stu-id="f52b0-355">Display the prediction result as the next line of code in the `ClassifySingleImage()` method:</span></span>

[!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="results"></a><span data-ttu-id="f52b0-356">結果</span><span class="sxs-lookup"><span data-stu-id="f52b0-356">Results</span></span>

<span data-ttu-id="f52b0-357">完成上述步驟後，請執行主控台應用程式 (Ctrl + F5)。</span><span class="sxs-lookup"><span data-stu-id="f52b0-357">After following the previous steps, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="f52b0-358">您的結果應該與下列輸出類似。</span><span class="sxs-lookup"><span data-stu-id="f52b0-358">Your results should be similar to the following output.</span></span>  <span data-ttu-id="f52b0-359">您可能會看到警告或處理中訊息，但為了讓結果變得清楚，這些訊息已從下列結果中移除。</span><span class="sxs-lookup"><span data-stu-id="f52b0-359">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

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
=============== Making classifications ===============
Image: broccoli.png predicted as: food with score: 0.905548
Image: pizza3.jpg predicted as: food with score: 0.9709008
Image: teddy6.jpg predicted as: toy with score: 0.9750155
=============== Making single image classification ===============
Image: toaster3.jpg predicted as: appliance with score: 0.9625379

C:\Program Files\dotnet\dotnet.exe (process 4304) exited with code 0.
Press any key to close this window . . .
```

<span data-ttu-id="f52b0-360">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="f52b0-360">Congratulations!</span></span> <span data-ttu-id="f52b0-361">您已透過在 ML.NET 中重複使用已預先定型的 `TensorFlow` 模型，成功建置出可用來分類影像的機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="f52b0-361">You've now successfully built a machine learning model for image classification by reusing a pre-trained `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="f52b0-362">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="f52b0-362">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span>

<span data-ttu-id="f52b0-363">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="f52b0-363">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="f52b0-364">了解問題</span><span class="sxs-lookup"><span data-stu-id="f52b0-364">Understand the problem</span></span>
> * <span data-ttu-id="f52b0-365">重複使用並調整預先定型的模型</span><span class="sxs-lookup"><span data-stu-id="f52b0-365">Reuse and tune the pre-trained model</span></span>
> * <span data-ttu-id="f52b0-366">搭配已載入的模型分類影像</span><span class="sxs-lookup"><span data-stu-id="f52b0-366">Classify images with a loaded model</span></span>

<span data-ttu-id="f52b0-367">請查看機器學習範例 GitHub 存放庫，以探索更複雜的影像分類範例。</span><span class="sxs-lookup"><span data-stu-id="f52b0-367">Check out the Machine Learning samples GitHub repository to explore an expanded image classification sample.</span></span>
> [!div class="nextstepaction"]
> <span data-ttu-id="f52b0-368">[dotnet/machinelearning-samples GitHub 存放庫](https://github.com/dotnet/machinelearning-samples/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="f52b0-368">[dotnet/machinelearning-samples GitHub repository](https://github.com/dotnet/machinelearning-samples/)</span></span>
