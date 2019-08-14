---
title: 教學課程：搭配 ONNX 和 ML.NET 使用深度學習偵測物件
description: 本教學課程會示範如何使用 ML.NET 中預先定型的 ONNX 深度學習模型來偵測影像中物件。
author: luisquintanilla
ms.author: luquinta
ms.date: 08/01/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 3e5b6b482dfbd1ff06347883a93a561944200a9f
ms.sourcegitcommit: 8c6426a3d2adff5fbcbe1fed0f28eda718c15351
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2019
ms.locfileid: "68733404"
---
# <a name="tutorial-detect-objects-using-onnx-in-mlnet"></a><span data-ttu-id="ce007-103">教學課程：使用 ML.NET 中的 ONNX 來偵測物件</span><span class="sxs-lookup"><span data-stu-id="ce007-103">Tutorial: Detect objects using ONNX in ML.NET</span></span>

<span data-ttu-id="ce007-104">了解如何使用 ML.NET 中預先定型的 ONNX 模型來偵測影像中物件。</span><span class="sxs-lookup"><span data-stu-id="ce007-104">Learn how to use a pre-trained ONNX model in ML.NET to detect objects in images.</span></span>

<span data-ttu-id="ce007-105">若要從頭開始定型物件偵測模型，將會需要設定數以百萬計的參數、大量的標籤定型資料，以及大量的計算資源 (數以百計的 GPU 小時)。</span><span class="sxs-lookup"><span data-stu-id="ce007-105">Training an object detection model from scratch requires setting millions of parameters, a large amount of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="ce007-106">使用預先定型的模型可讓您快速地進行定型過程。</span><span class="sxs-lookup"><span data-stu-id="ce007-106">Using a pre-trained model allows you to shortcut the training process.</span></span>

<span data-ttu-id="ce007-107">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="ce007-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="ce007-108">了解問題</span><span class="sxs-lookup"><span data-stu-id="ce007-108">Understand the problem</span></span>
> * <span data-ttu-id="ce007-109">了解 ONNX 是什麼，以及它和 ML.NET 搭配運作的方式</span><span class="sxs-lookup"><span data-stu-id="ce007-109">Learn what ONNX is and how it works with ML.NET</span></span>
> * <span data-ttu-id="ce007-110">了解模型</span><span class="sxs-lookup"><span data-stu-id="ce007-110">Understand the model</span></span>
> * <span data-ttu-id="ce007-111">重複使用預先定型的模型</span><span class="sxs-lookup"><span data-stu-id="ce007-111">Reuse the pre-trained model</span></span>
> * <span data-ttu-id="ce007-112">使用載入的模型偵測物件</span><span class="sxs-lookup"><span data-stu-id="ce007-112">Detect objects with a loaded model</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="ce007-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="ce007-113">Pre-requisites</span></span>

- <span data-ttu-id="ce007-114">已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)。</span><span class="sxs-lookup"><span data-stu-id="ce007-114">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
- [<span data-ttu-id="ce007-115">Microsoft.ML NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="ce007-115">Microsoft.ML NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML/)
- [<span data-ttu-id="ce007-116">Microsoft.ML.ImageAnalytics NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="ce007-116">Microsoft.ML.ImageAnalytics NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML.ImageAnalytics/)
- [<span data-ttu-id="ce007-117">Microsoft.ML.OnnxTransformer NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="ce007-117">Microsoft.ML.OnnxTransformer NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML.OnnxTransformer/)
- [<span data-ttu-id="ce007-118">Tiny YOLOv2 預先定型模型</span><span class="sxs-lookup"><span data-stu-id="ce007-118">Tiny YOLOv2 pre-trained model</span></span>](https://github.com/onnx/models/tree/master/tiny_yolov2)
- <span data-ttu-id="ce007-119">[Netron](https://github.com/lutzroeder/netron) (選擇性)</span><span class="sxs-lookup"><span data-stu-id="ce007-119">[Netron](https://github.com/lutzroeder/netron) (optional)</span></span>

## <a name="onnx-object-detection-sample-overview"></a><span data-ttu-id="ce007-120">ONNX 物件偵測範例概觀</span><span class="sxs-lookup"><span data-stu-id="ce007-120">ONNX object detection sample overview</span></span>

<span data-ttu-id="ce007-121">此範例會建立 .NET Core 主控台應用程式，使用預先定型的深度學習 ONNX 模型偵測影像內的物件。</span><span class="sxs-lookup"><span data-stu-id="ce007-121">This sample creates a .NET core console application that detects objects within an image using a pre-trained deep learning ONNX model.</span></span> <span data-ttu-id="ce007-122">您可以在 GitHub 的 [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) 找到此範例的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ce007-122">The code for this sample can be found on the [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) on GitHub.</span></span>

## <a name="what-is-object-detection"></a><span data-ttu-id="ce007-123">什麼是物件偵測？</span><span class="sxs-lookup"><span data-stu-id="ce007-123">What is object detection?</span></span>

<span data-ttu-id="ce007-124">物件偵測是一種電腦視覺問題。</span><span class="sxs-lookup"><span data-stu-id="ce007-124">Object detection is a computer vision problem.</span></span> <span data-ttu-id="ce007-125">雖然與影像分類密切相關，但物件偵測會更仔細的執行影像分類。</span><span class="sxs-lookup"><span data-stu-id="ce007-125">While closely related to image classification, object detection performs image classification at a more granular scale.</span></span> <span data-ttu-id="ce007-126">物件偵測會尋找影像中實體的位置「並」  進行分類。</span><span class="sxs-lookup"><span data-stu-id="ce007-126">Object detection both locates _and_ categorizes entities within images.</span></span> <span data-ttu-id="ce007-127">當影像包含不同類型的多個物件時，請使用物件偵測。</span><span class="sxs-lookup"><span data-stu-id="ce007-127">Use object detection when images contain multiple objects of different types.</span></span>

![](./media/object-detection-onnx/img-classification-obj-detection.PNG)

<span data-ttu-id="ce007-128">物件偵測的一些使用案例包括：</span><span class="sxs-lookup"><span data-stu-id="ce007-128">Some use cases for object detection include:</span></span>

- <span data-ttu-id="ce007-129">自動駕駛車輛</span><span class="sxs-lookup"><span data-stu-id="ce007-129">Self-Driving Cars</span></span>
- <span data-ttu-id="ce007-130">機器人</span><span class="sxs-lookup"><span data-stu-id="ce007-130">Robotics</span></span>
- <span data-ttu-id="ce007-131">臉部偵測</span><span class="sxs-lookup"><span data-stu-id="ce007-131">Face Detection</span></span>
- <span data-ttu-id="ce007-132">工作場所安全</span><span class="sxs-lookup"><span data-stu-id="ce007-132">Workplace Safety</span></span>
- <span data-ttu-id="ce007-133">物件計數</span><span class="sxs-lookup"><span data-stu-id="ce007-133">Object Counting</span></span>
- <span data-ttu-id="ce007-134">活動辨識</span><span class="sxs-lookup"><span data-stu-id="ce007-134">Activity Recognition</span></span>

## <a name="select-a-deep-learning-model"></a><span data-ttu-id="ce007-135">選取深度學習模型</span><span class="sxs-lookup"><span data-stu-id="ce007-135">Select a deep learning model</span></span>

<span data-ttu-id="ce007-136">深度學習是機器學習的子集。</span><span class="sxs-lookup"><span data-stu-id="ce007-136">Deep learning is a subset of machine learning.</span></span> <span data-ttu-id="ce007-137">若要定型機器學習模型，將需要大量的資料。</span><span class="sxs-lookup"><span data-stu-id="ce007-137">To train deep learning models, large quantities of data are required.</span></span> <span data-ttu-id="ce007-138">資料中的模式會以一系列層來表示。</span><span class="sxs-lookup"><span data-stu-id="ce007-138">Patterns in the data are represented by a series of layers.</span></span> <span data-ttu-id="ce007-139">資料中關聯性會編碼成層之間的連線，其中每個層都會包含權數。</span><span class="sxs-lookup"><span data-stu-id="ce007-139">The relationships in the data are encoded as connections between the layers containing weights.</span></span> <span data-ttu-id="ce007-140">權數越高，關聯性越強。</span><span class="sxs-lookup"><span data-stu-id="ce007-140">The higher the weight, the stronger the relationship.</span></span> <span data-ttu-id="ce007-141">這一系列的層和連線統稱為人工神經網路。</span><span class="sxs-lookup"><span data-stu-id="ce007-141">Collectively, this series of layers and connections are known as artificial neural networks.</span></span> <span data-ttu-id="ce007-142">網路中的層越多，其「深度」也越高，使其形成深度神經網路。</span><span class="sxs-lookup"><span data-stu-id="ce007-142">The more layers in a network, the "deeper" it is, making it a deep neural network.</span></span> 

<span data-ttu-id="ce007-143">目前有許多不同的神經網路類型，其中最常見的便是多層感知器 (MLP)、卷積神經網路 (CNN) 及遞歸神經網路 (RNN)。</span><span class="sxs-lookup"><span data-stu-id="ce007-143">There are different types of neural networks, the most common being Multi-Layered Perceptron (MLP), Convolutional Neural Network (CNN) and Recurrent Neural Network (RNN).</span></span> <span data-ttu-id="ce007-144">其中最基本的為 MLP，它會將一組輸入對應到一組輸出。</span><span class="sxs-lookup"><span data-stu-id="ce007-144">The most basic is the MLP, which maps a set of inputs to a set of outputs.</span></span> <span data-ttu-id="ce007-145">這種神經網路在資料不包含空間或時間元件時非常實用。</span><span class="sxs-lookup"><span data-stu-id="ce007-145">This neural network is good when the data does not have a spatial or time component.</span></span> <span data-ttu-id="ce007-146">CNN 則會利用卷積層來處理資料中包含的空間資訊。</span><span class="sxs-lookup"><span data-stu-id="ce007-146">The CNN makes use of convolutional layers to process spatial information contained in the data.</span></span> <span data-ttu-id="ce007-147">CNN 的良好使用範例便是影像處理，用來偵測影像中特定區域內是否存在某一特徵 (例如影像的中央是否有鼻子？)。</span><span class="sxs-lookup"><span data-stu-id="ce007-147">A good use case for CNNs is image processing to detect the presence of a feature in a region of an image (for example, is there a nose in the center of an image?).</span></span> <span data-ttu-id="ce007-148">最後，RNN 則可以保存狀態或記憶體，並用作為輸入。</span><span class="sxs-lookup"><span data-stu-id="ce007-148">Finally, RNNs allow for the persistence of state or memory to be used as input.</span></span> <span data-ttu-id="ce007-149">RNN 會用在時間序列分析，在進行這種分析時事件的循序順序和內容非常重要。</span><span class="sxs-lookup"><span data-stu-id="ce007-149">RNNs are used for time-series analysis, where the sequential ordering and context of events is important.</span></span> 

### <a name="understand-the-model"></a><span data-ttu-id="ce007-150">了解模型</span><span class="sxs-lookup"><span data-stu-id="ce007-150">Understand the model</span></span>

<span data-ttu-id="ce007-151">物件偵測是一種影像處理工作。</span><span class="sxs-lookup"><span data-stu-id="ce007-151">Object detection is an image processing task.</span></span> <span data-ttu-id="ce007-152">因此，大多數定型並用來解決此問題的深度學習模型都是 CNN。</span><span class="sxs-lookup"><span data-stu-id="ce007-152">Therefore, most deep learning models trained to solve this problem are CNNs.</span></span> <span data-ttu-id="ce007-153">本教學課程中所使用的模型是 Tiny YOLOv2 模型，它是一種以下文件中所述 YOLOv2 模型的壓縮版本：["YOLO9000:Better, Faster, Stronger" by Redmon and Fadhari](https://arxiv.org/pdf/1612.08242.pdf) (YOLO9000：更好、更快、更強，作者：Redmon 及 Fadhari)。</span><span class="sxs-lookup"><span data-stu-id="ce007-153">The model used in this tutorial is the Tiny YOLOv2 model, a more compact version of the YOLOv2 model described in the paper: ["YOLO9000: Better, Faster, Stronger" by Redmon and Fadhari](https://arxiv.org/pdf/1612.08242.pdf).</span></span> <span data-ttu-id="ce007-154">Tiny YOLOv2 是使用 Pascal VOC 資料集所定型，由 15 個層組成，可預測 20 種不同的物件類別。</span><span class="sxs-lookup"><span data-stu-id="ce007-154">Tiny YOLOv2 is trained on the Pascal VOC dataset and is made up of 15 layers that can predict 20 different classes of objects.</span></span> <span data-ttu-id="ce007-155">因為 Tiny YOLOv2 是一種原始 YOLOv2 模型的壓縮版本，所以它在速度和正確性間進行了取捨。</span><span class="sxs-lookup"><span data-stu-id="ce007-155">Because Tiny YOLOv2 is a condensed version of the original YOLOv2 model, a tradeoff is made between speed and accuracy.</span></span> <span data-ttu-id="ce007-156">組成模型的不同層可使用如 Netron 等工具進行視覺化。</span><span class="sxs-lookup"><span data-stu-id="ce007-156">The different layers that make up the model can be visualized using tools like Netron.</span></span> <span data-ttu-id="ce007-157">檢查模型之後，您可以觀察到所有組成神經網路層之間的連線對應，其中每個層將包含層名稱及個別輸入/輸出的維度。</span><span class="sxs-lookup"><span data-stu-id="ce007-157">Inspecting the model would yield a mapping of the connections between all the layers that make up the neural network, where each layer would contain the name of the layer along with the dimensions of the respective input / output.</span></span> <span data-ttu-id="ce007-158">用來描述模型輸入和輸出的資料結構則稱為 Tensor。</span><span class="sxs-lookup"><span data-stu-id="ce007-158">The data structures used to describe the inputs and outputs of the model are known as tensors.</span></span> <span data-ttu-id="ce007-159">您可以把 Tensor 想成是將資料儲存在 N 個維度中的容器。</span><span class="sxs-lookup"><span data-stu-id="ce007-159">Tensors can be thought of as containers that store data in N-dimensions.</span></span> <span data-ttu-id="ce007-160">以 Tiny YOLOv2 為例，輸入層的名稱為 `image`，且它會預期維度為 `3 x 416 x 416` 的 Tensor。</span><span class="sxs-lookup"><span data-stu-id="ce007-160">In the case of Tiny YOLOv2, the name of the input layer is `image` and it expects a tensor of dimensions `3 x 416 x 416`.</span></span> <span data-ttu-id="ce007-161">輸出層的名稱則為 `grid`，它會產生維度為 `125 x 13 x 13` 的輸出 Tensor。</span><span class="sxs-lookup"><span data-stu-id="ce007-161">The name of the output layer is `grid` and generates an output tensor of dimensions `125 x 13 x 13`.</span></span>  

![](./media/object-detection-onnx/netron-model-map.png)

<span data-ttu-id="ce007-162">YOLO 模型接受 `3(RGB) x 416px x 416px` 的影像。</span><span class="sxs-lookup"><span data-stu-id="ce007-162">The YOLO model takes an image `3(RGB) x 416px x 416px`.</span></span> <span data-ttu-id="ce007-163">模型會接受此輸入，並透過不同的層傳遞它來產生輸出。</span><span class="sxs-lookup"><span data-stu-id="ce007-163">The model takes this input and passes it through the different layers to produce an output.</span></span> <span data-ttu-id="ce007-164">輸出會將輸入影像分成 `13 x 13` 的格線，格線中的每個儲存格都由 `125` 個值組成。</span><span class="sxs-lookup"><span data-stu-id="ce007-164">The output divides the input image into a `13 x 13` grid, with each cell in the grid consisting of `125` values.</span></span> 

### <a name="what-is-an-onnx-model"></a><span data-ttu-id="ce007-165">什麼是 ONNX 模型？</span><span class="sxs-lookup"><span data-stu-id="ce007-165">What is an ONNX model?</span></span>

<span data-ttu-id="ce007-166">Open Neural Network Exchange (ONNX) 是一種 AI 型的開放原始碼格式。</span><span class="sxs-lookup"><span data-stu-id="ce007-166">The Open Neural Network Exchange (ONNX) is an open source format for AI models.</span></span> <span data-ttu-id="ce007-167">ONNX 支援架構間的互通性。</span><span class="sxs-lookup"><span data-stu-id="ce007-167">ONNX supports interoperability between frameworks.</span></span> <span data-ttu-id="ce007-168">這表示您可以在其中一個熱門的機器學習架構 (例如 PyTorch) 中定型模型、將它轉換成 ONNX 格式，然後在 ML.NET 等不同的架構中取用 ONNX 模型。</span><span class="sxs-lookup"><span data-stu-id="ce007-168">This means you can train a model in one of the many popular machine learning frameworks like PyTorch, convert it into ONNX format and consume the ONNX model in a different framework like ML.NET.</span></span> <span data-ttu-id="ce007-169">若要深入了解，請前往 [ONNX 網站](https://onnx.ai/)。</span><span class="sxs-lookup"><span data-stu-id="ce007-169">To learn more, visit the [ONNX website](https://onnx.ai/).</span></span> 

![](./media/object-detection-onnx/onnx-frameworks.png)

<span data-ttu-id="ce007-170">預先定型的 Tiny YOLOv2 模型是以 ONNX 格式儲存，它是一種層的序列化表示和從這些層中所學習到模式。</span><span class="sxs-lookup"><span data-stu-id="ce007-170">The pre-trained Tiny YOLOv2 model is stored in ONNX format, a serialized representation of the layers and learned patterns of those layers.</span></span> <span data-ttu-id="ce007-171">在 ML.NET 中，與 ONNX 的互通性是透過 [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) 和 [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) NuGet 套件來達成。</span><span class="sxs-lookup"><span data-stu-id="ce007-171">In ML.NET, interoperability with ONNX is achieved with the [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) and [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) NuGet packages.</span></span> <span data-ttu-id="ce007-172">[`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) 套件包含一系列的轉換，這些轉換會接受影像，並將影像編碼成可用來作為輸入以進行預測或定型管線的數值。</span><span class="sxs-lookup"><span data-stu-id="ce007-172">The [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) package contains a series of transforms that take an image and encode it into numerical values that can be used as input into a prediction or training pipeline.</span></span> <span data-ttu-id="ce007-173">[`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) 套件會利用 ONNX 執行階段載入 ONNX 模型，並用它來根據所提供的輸入進行預測。</span><span class="sxs-lookup"><span data-stu-id="ce007-173">The [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) package leverages the ONNX Runtime to load an ONNX model and use it to make predictions based on input provided.</span></span> 

![](./media/object-detection-onnx/onnx-ml-net-integration.png)

## <a name="set-up-the-net-core-project"></a><span data-ttu-id="ce007-174">設定 .NET Core 專案</span><span class="sxs-lookup"><span data-stu-id="ce007-174">Set up the .NET Core project</span></span>

<span data-ttu-id="ce007-175">現在您已對 ONNX 以及 Tiny YOLOv2 的運作方式有了一般程度的了解，是時候建置應用程式了。</span><span class="sxs-lookup"><span data-stu-id="ce007-175">Now that you have a general understanding of what ONNX is and how Tiny YOLOv2 works, it's time to build the application.</span></span>

### <a name="create-a-console-application"></a><span data-ttu-id="ce007-176">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="ce007-176">Create a console application</span></span>

1. <span data-ttu-id="ce007-177">建立稱為 "ObjectDetection" 的 **.NET Core 主控台應用程式**。</span><span class="sxs-lookup"><span data-stu-id="ce007-177">Create a **.NET Core Console Application** called "ObjectDetection".</span></span>

1. <span data-ttu-id="ce007-178">安裝「Microsoft.ML NuGet 套件」  ：</span><span class="sxs-lookup"><span data-stu-id="ce007-178">Install the **Microsoft.ML NuGet Package**:</span></span>

    - <span data-ttu-id="ce007-179">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]  。</span><span class="sxs-lookup"><span data-stu-id="ce007-179">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> 
    - <span data-ttu-id="ce007-180">選擇 [nuget.org] 作為 [套件來源]，選取 [瀏覽] 索引標籤，搜尋 **Microsoft.ML**。</span><span class="sxs-lookup"><span data-stu-id="ce007-180">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span> 
    - <span data-ttu-id="ce007-181">選取 [安裝]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="ce007-181">Select the **Install** button.</span></span> 
    - <span data-ttu-id="ce007-182">在 [預覽變更]  對話方塊上，選取 [確定]  按鈕，然後在 [授權接受]  對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]  。</span><span class="sxs-lookup"><span data-stu-id="ce007-182">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> 
    - <span data-ttu-id="ce007-183">針對 **Microsoft.ML.ImageAnalytics** 和 **Microsoft.ML.OnnxTransformer** 重複這些步驟。</span><span class="sxs-lookup"><span data-stu-id="ce007-183">Repeat these steps for **Microsoft.ML.ImageAnalytics** and **Microsoft.ML.OnnxTransformer**.</span></span>

### <a name="prepare-your-data-and-pre-trained-model"></a><span data-ttu-id="ce007-184">準備您的資料及預先定型模型</span><span class="sxs-lookup"><span data-stu-id="ce007-184">Prepare your data and pre-trained model</span></span>

1. <span data-ttu-id="ce007-185">下載[專案資產目錄 ZIP 檔案](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip)並將它解壓縮。</span><span class="sxs-lookup"><span data-stu-id="ce007-185">Download [The project assets directory zip file](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip) and unzip.</span></span>

1. <span data-ttu-id="ce007-186">將 `assets` 目錄複製到您的 *ObjectDetection* 專案目錄。</span><span class="sxs-lookup"><span data-stu-id="ce007-186">Copy the `assets` directory into your *ObjectDetection* project directory.</span></span> <span data-ttu-id="ce007-187">此目錄及其子目錄包含本教學課程所需的影像檔案 (Tiny YOLOv2 模型除外，您將會在下個步驟中下載並新增它)。</span><span class="sxs-lookup"><span data-stu-id="ce007-187">This directory and its subdirectories contain the image files (except for the Tiny YOLOv2 model, which you'll download and add in the next step) needed for this tutorial.</span></span>

1. <span data-ttu-id="ce007-188">從 [ONNX Model Zoo](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2) (ONNX 模型動物園) 下載 [Tiny YOLOv2 模型](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz)並將它解壓縮。</span><span class="sxs-lookup"><span data-stu-id="ce007-188">Download the [Tiny YOLOv2 model](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz) from the [ONNX Model Zoo](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2), and unzip.</span></span>

    <span data-ttu-id="ce007-189">開啟命令提示字元，然後輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="ce007-189">Open the command prompt and enter the following command:</span></span>

    ```shell
    tar -xvzf tiny_yolov2.tar.gz 
    ```

1. <span data-ttu-id="ce007-190">將解壓縮後目錄中解壓縮後的 `model.onnx` 檔案複製到您 *ObjectDetection* 專案的 `assets\Model` 目錄，然後將它重新命名為 `TinyYolo2_model.onnx`。</span><span class="sxs-lookup"><span data-stu-id="ce007-190">Copy the extracted `model.onnx` file from the directory just unzipped into your *ObjectDetection* project `assets\Model` directory and rename it to `TinyYolo2_model.onnx`.</span></span> <span data-ttu-id="ce007-191">此目錄包含本教學課程需要的模型。</span><span class="sxs-lookup"><span data-stu-id="ce007-191">This directory contains the model needed for this tutorial.</span></span>

1. <span data-ttu-id="ce007-192">在 [方案總管] 中，以滑鼠右鍵按一下資產目錄及子目錄中的每個檔案，然後選取 [內容]  。</span><span class="sxs-lookup"><span data-stu-id="ce007-192">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="ce007-193">在 [進階]  底下，將 [複製到輸出目錄]  的值變更為 [有更新時才複製]  。</span><span class="sxs-lookup"><span data-stu-id="ce007-193">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="ce007-194">建立類別及定義路徑</span><span class="sxs-lookup"><span data-stu-id="ce007-194">Create classes and define paths</span></span>

<span data-ttu-id="ce007-195">開啟 *Program.cs* 檔案，然後將下列額外的 `using` 陳述式新增到檔案頂端：</span><span class="sxs-lookup"><span data-stu-id="ce007-195">Open the *Program.cs* file and add the following additional `using` statements to the top of the file:</span></span>

[!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L1-L9)]

<span data-ttu-id="ce007-196">接下來，請定義各種資產的路徑。</span><span class="sxs-lookup"><span data-stu-id="ce007-196">Next, define the paths of the various assets.</span></span> 

1. <span data-ttu-id="ce007-197">首先，請在 `Program` 類別的 `Main` 方法下新增 `GetAbsolutePath` 方法。</span><span class="sxs-lookup"><span data-stu-id="ce007-197">First, add the `GetAbsolutePath` method below the `Main` method in the `Program` class.</span></span> 

    [!code-csharp [GetAbsolutePath](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L66-L74)]

1. <span data-ttu-id="ce007-198">接著，在 `Main` 方法中，建立儲存您資產位置的欄位：</span><span class="sxs-lookup"><span data-stu-id="ce007-198">Then, inside the `Main` method, create fields to store the location of your assets:</span></span>

    [!code-csharp [AssetDefinition](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L17-L21)]

<span data-ttu-id="ce007-199">將新目錄新增到專案來儲存您的輸入資料和預測類別。</span><span class="sxs-lookup"><span data-stu-id="ce007-199">Add a new directory to your project to store your input data and prediction classes.</span></span>

<span data-ttu-id="ce007-200">在 [方案總管]  中，以滑鼠右鍵按一下專案，然後選取 [新增]   > [新增資料夾]  。</span><span class="sxs-lookup"><span data-stu-id="ce007-200">In **Solution Explorer**, right-click the project, and then select **Add** > **New Folder**.</span></span> <span data-ttu-id="ce007-201">當新的資料夾出現在 [方案總管中] 時，請將它命名為 "DataStructures"。</span><span class="sxs-lookup"><span data-stu-id="ce007-201">When the new folder appears in the Solution Explorer, name it "DataStructures".</span></span>

<span data-ttu-id="ce007-202">在新建立的 *DataStructures* 目錄中建立輸入資料類別。</span><span class="sxs-lookup"><span data-stu-id="ce007-202">Create your input data class in the newly created *DataStructures* directory.</span></span>

1. <span data-ttu-id="ce007-203">在 [方案總管]  中，以滑鼠右鍵按一下 *DataStructures* 目錄，然後選取 [新增]   > [新增項目]  。</span><span class="sxs-lookup"><span data-stu-id="ce007-203">In **Solution Explorer**, right-click the *DataStructures* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="ce007-204">在 [新增項目]  對話方塊中，選取 [類別]  ，然後將 [名稱]  欄位變更為 *ImageNetData.cs*。</span><span class="sxs-lookup"><span data-stu-id="ce007-204">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageNetData.cs*.</span></span> <span data-ttu-id="ce007-205">接著，選取 [新增]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="ce007-205">Then, select the **Add** button.</span></span>
     
    <span data-ttu-id="ce007-206">隨即在程式碼編輯器中開啟 *ImageNetData.cs* 檔案。</span><span class="sxs-lookup"><span data-stu-id="ce007-206">The *ImageNetData.cs* file opens in the code editor.</span></span> <span data-ttu-id="ce007-207">將下列 `using` 陳述式新增到 *ImageNetData.cs* 的頂端：</span><span class="sxs-lookup"><span data-stu-id="ce007-207">Add the following `using` statement to the top of *ImageNetData.cs*:</span></span>

    [!code-csharp [ImageNetDataUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L1-L4)]

    <span data-ttu-id="ce007-208">移除現有的類別定義，然後將下列 `ImageNetData` 類別的程式碼新增到 *ImageNetData.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="ce007-208">Remove the existing class definition and add the following code for the `ImageNetData` class to the *ImageNetData.cs* file:</span></span>
    
    [!code-csharp [ImageNetDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L8-L23)]

    <span data-ttu-id="ce007-209">`ImageNetData` 是輸入資料集類別，並具有下列 <xref:System.String> 欄位：</span><span class="sxs-lookup"><span data-stu-id="ce007-209">`ImageNetData` is the input image data class and has the following <xref:System.String> fields:</span></span>

    - <span data-ttu-id="ce007-210">`ImagePath` 包含儲存影像的路徑。</span><span class="sxs-lookup"><span data-stu-id="ce007-210">`ImagePath` contains the path where the image is stored.</span></span>
    - <span data-ttu-id="ce007-211">`Label` 包含檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="ce007-211">`Label` contains the name of the file.</span></span>

    <span data-ttu-id="ce007-212">此外，`ImageNetData` 還包含 `ReadFromFile` 方法，此方法會載入所指定 `imageFolder` 路徑中儲存的多個影像檔案，並將它們作為 `ImageNetData` 物件的集合傳回。</span><span class="sxs-lookup"><span data-stu-id="ce007-212">Additionally, `ImageNetData` contains a method `ReadFromFile` which loads multiple image files stored in the `imageFolder` path specified and returns them as a collection of `ImageNetData` objects.</span></span>

<span data-ttu-id="ce007-213">在 *DataStructures* 目錄中建立您的預測類別。</span><span class="sxs-lookup"><span data-stu-id="ce007-213">Create your prediction class in the *DataStructures* directory.</span></span>

1. <span data-ttu-id="ce007-214">在 [方案總管]  中，以滑鼠右鍵按一下 *DataStructures* 目錄，然後選取 [新增]   > [新增項目]  。</span><span class="sxs-lookup"><span data-stu-id="ce007-214">In **Solution Explorer**, right-click the *DataStructures* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="ce007-215">在 [新增項目]  對話方塊中，選取 [類別]  ，然後將 [名稱]  欄位變更為 *ImageNetPrediction.cs*。</span><span class="sxs-lookup"><span data-stu-id="ce007-215">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageNetPrediction.cs*.</span></span> <span data-ttu-id="ce007-216">接著，選取 [新增]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="ce007-216">Then, select the **Add** button.</span></span>

    <span data-ttu-id="ce007-217">隨即在程式碼編輯器中開啟 *ImageNetPrediction.cs* 檔案。</span><span class="sxs-lookup"><span data-stu-id="ce007-217">The *ImageNetPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="ce007-218">將下列 `using` 陳述式新增到 *ImageNetPrediction.cs* 的頂端：</span><span class="sxs-lookup"><span data-stu-id="ce007-218">Add the following `using` statement to the top of *ImageNetPrediction.cs*:</span></span>

    [!code-csharp [ImageNetPredictionUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L1)]

    <span data-ttu-id="ce007-219">移除現有的類別定義，然後將下列 `ImageNetPrediction` 類別的程式碼新增到 *ImageNetPrediction.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="ce007-219">Remove the existing class definition and add the following code for the `ImageNetPrediction` class to the *ImageNetPrediction.cs* file:</span></span>

    [!code-csharp [ImageNetPredictionClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L5-L9)]

    <span data-ttu-id="ce007-220">`ImageNetPrediction` 是預測資料類別，並具有下列 `float[]` 欄位：</span><span class="sxs-lookup"><span data-stu-id="ce007-220">`ImageNetPrediction` is the prediction data class and has the following `float[]` field:</span></span>

    - <span data-ttu-id="ce007-221">`PredictedLabel` 包含影像中所偵測到每個週框方塊的維度、物件性分數及類別機率。</span><span class="sxs-lookup"><span data-stu-id="ce007-221">`PredictedLabel` contains the dimensions, objectness score and class probabilities for each of the bounding boxes detected in an image.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="ce007-222">在 Main 中初始化變數</span><span class="sxs-lookup"><span data-stu-id="ce007-222">Initialize variables in Main</span></span>

<span data-ttu-id="ce007-223">[MLContext 類別](xref:Microsoft.ML.MLContext)是所有 ML.NET 作業的起點，且初始化 `mlContext` 會建立新的 ML.NET 環境，其可在模型建立工作流程物件之間共用。</span><span class="sxs-lookup"><span data-stu-id="ce007-223">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="ce007-224">就概念而言，類似於 Entity Framework 中的 `DBContext`。</span><span class="sxs-lookup"><span data-stu-id="ce007-224">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="ce007-225">將下列程式碼新增到 *Program.cs* 中 `outputFolder` 欄位下方的 `Main` 方法，使用 `MLContext` 的新執行個體初始化 `mlContext` 變數。</span><span class="sxs-lookup"><span data-stu-id="ce007-225">Initialize the `mlContext` variable with a new instance of `MLContext` by adding the following line to the `Main` method of *Program.cs* below the `outputFolder` field.</span></span>

[!code-csharp [InitMLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L24)]

### <a name="add-helper-methods"></a><span data-ttu-id="ce007-226">新增協助程式方法</span><span class="sxs-lookup"><span data-stu-id="ce007-226">Add Helper Methods</span></span>

<span data-ttu-id="ce007-227">在模型進行預測 (通常稱為評分) 且輸出處理完畢後，必須在影像上繪製週框方塊。</span><span class="sxs-lookup"><span data-stu-id="ce007-227">After the model has made a prediction, commonly referred to as scoring, and the outputs have been processed, the bounding boxes have to be drawn on the image.</span></span> <span data-ttu-id="ce007-228">若要執行此操作，請在 *Program.cs* 內 `GetAbsolutePath` 方法的下方新增稱為 `DrawBoundingBox` 的方法。</span><span class="sxs-lookup"><span data-stu-id="ce007-228">To do so, add a method called `DrawBoundingBox` below the `GetAbsolutePath` method insode of *Program.cs*.</span></span>

```csharp
private static void DrawBoundingBox(string inputImageLocation, string outputImageLocation, string imageName, IList<YoloBoundingBox> filteredBoundingBoxes)
{

}
```

<span data-ttu-id="ce007-229">首先，請先在 `DrawBoundingBox` 方法中載入影像並取得高度及寬度維度。</span><span class="sxs-lookup"><span data-stu-id="ce007-229">First, load the image and get the height and width dimensions in the `DrawBoundingBox` method.</span></span>

[!code-csharp [LoadImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L78-L81)]

<span data-ttu-id="ce007-230">接著，請建立 for-each 迴圈逐一查看模型偵測到的每個週框方塊。</span><span class="sxs-lookup"><span data-stu-id="ce007-230">Then, create a for-each loop to iterate over each of the bounding boxes detected by the model.</span></span>

```csharp
foreach (var box in filteredBoundingBoxes)
{

}
```

<span data-ttu-id="ce007-231">在 for-each 迴圈內，取得週框方塊的維度。</span><span class="sxs-lookup"><span data-stu-id="ce007-231">Inside of the for-each loop, get the dimensions of the bounding box.</span></span>

[!code-csharp [GetBBoxDimensions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L86-L89)]

<span data-ttu-id="ce007-232">因為週框方塊維度會對應到 `416 x 416` 的模型輸出，請調整週框方塊的維度，使其與影像的實際大小相符。</span><span class="sxs-lookup"><span data-stu-id="ce007-232">Because the dimensions of the bounding box correspond to the model input of `416 x 416`, scale the bounding box dimensions to match the actual size of the image.</span></span>

[!code-csharp [ScaleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L92-L95)]

<span data-ttu-id="ce007-233">接著，請定義將出現在每個週框方塊上方的文字範本。</span><span class="sxs-lookup"><span data-stu-id="ce007-233">Then, define a template for text that will apear above each bounding box.</span></span> <span data-ttu-id="ce007-234">文字會包含個別週框方塊內部物件的類別，以及其信賴度。</span><span class="sxs-lookup"><span data-stu-id="ce007-234">The text will contain the class of the object inside of the respective bounding box as well as the confidence.</span></span>

[!code-csharp [DefineBBoxText](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L98)]

<span data-ttu-id="ce007-235">為了在影像上進行繪製，請將它轉換成 [`Graphics`](xref:System.Drawing.Graphics) 物件。</span><span class="sxs-lookup"><span data-stu-id="ce007-235">In order to draw on the image, convert it to a [`Graphics`](xref:System.Drawing.Graphics) object.</span></span>

```csharp
using (Graphics thumbnailGraphic = Graphics.FromImage(image))
{
    
}
```

<span data-ttu-id="ce007-236">在 `using` 程式碼區塊內，調整圖形的 [`Graphics`](xref:System.Drawing.Graphics) 物件設定。</span><span class="sxs-lookup"><span data-stu-id="ce007-236">Inside the `using` code block, tune the graphic's [`Graphics`](xref:System.Drawing.Graphics) object settings.</span></span>

[!code-csharp [TuneGraphicSettings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L102-L104)]

<span data-ttu-id="ce007-237">在其下方，設定文字及週框方塊的字體和色彩選項。</span><span class="sxs-lookup"><span data-stu-id="ce007-237">Below that, set the font and color options for the text and bounding box.</span></span>

[!code-csharp [SetColorOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L106-L114)]

<span data-ttu-id="ce007-238">使用 [`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle*) 方法建立並填滿週框方塊上方的矩形，以包含文字。</span><span class="sxs-lookup"><span data-stu-id="ce007-238">Create and fill a rectangle above the bounding box to contain the text using the [`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle*) method.</span></span> <span data-ttu-id="ce007-239">這可協助提高文字的對比並改善可讀性。</span><span class="sxs-lookup"><span data-stu-id="ce007-239">This will help contrast the text and improve readability.</span></span>

[!code-csharp [DrawTextBackground](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L117)]

<span data-ttu-id="ce007-240">接著，使用 [`DrawString`](xref:System.Drawing.Graphics.DrawString*) 和 [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle*) 方法在影像中繪製文字和週框方塊。</span><span class="sxs-lookup"><span data-stu-id="ce007-240">Then, Draw the text and bounding box on the image using the [`DrawString`](xref:System.Drawing.Graphics.DrawString*) and [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle*) methods.</span></span>

[!code-csharp [DrawClassAndBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L118-L121)]

<span data-ttu-id="ce007-241">在 for-each 迴圈的外部，新增程式碼來在 `outputDirectory` 中儲存影像。</span><span class="sxs-lookup"><span data-stu-id="ce007-241">Outside of the for-each loop, add code to save the images in the `outputDirectory`.</span></span>

[!code-csharp [SaveImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L125-L130)]

<span data-ttu-id="ce007-242">若要取得額外的意見反應，了解應用程式確實在執行階段期間進行預測，請在 *Program.cs* 檔案的 `DrawBoundingBox` 方法下方新增稱為 `LogDetectedObjects` 的方法，將偵測到的物件輸出到主控台。</span><span class="sxs-lookup"><span data-stu-id="ce007-242">To get additional feedback that the application is making predictions as expected at runtime, add a method called `LogDetectedObjects` below the `DrawBoundingBox` method in the *Program.cs* file to output the detected objects to the console.</span></span>

[!code-csharp [LogOuptuts](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L133-L143)]

<span data-ttu-id="ce007-243">這兩種方法在模型已產生輸出，且也已經處理這些輸出時非常實用。</span><span class="sxs-lookup"><span data-stu-id="ce007-243">Both of these methods will be useful when the model has produced outputs and those have been processed.</span></span> <span data-ttu-id="ce007-244">但首先，請先建立處理模型輸出的功能。</span><span class="sxs-lookup"><span data-stu-id="ce007-244">First though, create the functionality to process the model outputs.</span></span>

## <a name="create-a-parser-to-post-process-model-outputs"></a><span data-ttu-id="ce007-245">建立剖析器來針對模型輸出進行後續處理</span><span class="sxs-lookup"><span data-stu-id="ce007-245">Create a parser to post-process model outputs</span></span>

<span data-ttu-id="ce007-246">模型會將影像分成 `13 x 13` 的格線，其中每個格線儲存格都是 `32px x 32px`。</span><span class="sxs-lookup"><span data-stu-id="ce007-246">The model segments an image into a `13 x 13` grid, where each grid cell is `32px x 32px`.</span></span> <span data-ttu-id="ce007-247">每個格線儲存格都包含 5 個可能的物件週框方塊。</span><span class="sxs-lookup"><span data-stu-id="ce007-247">Each grid cell contains 5 potential object bounding boxes.</span></span> <span data-ttu-id="ce007-248">週框方塊包含 25 個項目：</span><span class="sxs-lookup"><span data-stu-id="ce007-248">A bounding box has  25 elements:</span></span>

![](./media/object-detection-onnx/model-output-description.png)

- <span data-ttu-id="ce007-249">`x` 週框方塊中心的 X 位置，相對於與其建立關聯的格線儲存格。</span><span class="sxs-lookup"><span data-stu-id="ce007-249">`x` the x position of the bounding box center relative to the grid cell it's associated with.</span></span>
- <span data-ttu-id="ce007-250">`y` 週框方塊中心的 Y 位置，相對於與其建立關聯的格線儲存格。</span><span class="sxs-lookup"><span data-stu-id="ce007-250">`y` the y position of the bounding box center relative to the grid cell it's associated with.</span></span>
- <span data-ttu-id="ce007-251">`w` 週框方塊的寬度。</span><span class="sxs-lookup"><span data-stu-id="ce007-251">`w` the width of the bounding box.</span></span>
- <span data-ttu-id="ce007-252">`h` 週框方塊的高度。</span><span class="sxs-lookup"><span data-stu-id="ce007-252">`h` the height of the bounding box.</span></span> 
- <span data-ttu-id="ce007-253">`o` 物件存在於週框方塊內部的信賴度，也稱為物件性分數。</span><span class="sxs-lookup"><span data-stu-id="ce007-253">`o` the confidence value that an object exists within the bounding box, also known as objectness score.</span></span>
- <span data-ttu-id="ce007-254">`p1-p20` 為模型所預測 20 個類別各自的類別機率。</span><span class="sxs-lookup"><span data-stu-id="ce007-254">`p1-p20` class probabilities for each of the 20 classes predicted by the model.</span></span>

<span data-ttu-id="ce007-255">25 個描述 5 個週框方塊的項目會構成每個格線儲存格中所包含 125 個項目。</span><span class="sxs-lookup"><span data-stu-id="ce007-255">In total, the 25 elements describing each of the 5 bounding boxes make up the 125 elements contained in each grid cell.</span></span>

<span data-ttu-id="ce007-256">預先定型 ONNX 模型所產生輸出是長度為 `21125` 的 float 陣列，代表維度為 `125 x 13 x 13` Tensor 的項目。</span><span class="sxs-lookup"><span data-stu-id="ce007-256">The output generated by the pre-trained ONNX model is a float array of length `21125`, representing the elements of a tensor with dimensions `125 x 13 x 13`.</span></span> <span data-ttu-id="ce007-257">為了將模型所產生的預測轉換成 Tensor，將需要進行一些後續處理工作。</span><span class="sxs-lookup"><span data-stu-id="ce007-257">In order to transform the predictions generated by the model into a tensor, some post-processing work is required.</span></span> <span data-ttu-id="ce007-258">若要執行此操作，請建立一組類別來協助剖析輸出。</span><span class="sxs-lookup"><span data-stu-id="ce007-258">To do so, create a set of classes to help parse the output.</span></span>

<span data-ttu-id="ce007-259">將新目錄新增到您的專案來整理剖析器類別組。</span><span class="sxs-lookup"><span data-stu-id="ce007-259">Add a new directory to your project to organize the set of parser classes.</span></span>

1. <span data-ttu-id="ce007-260">在 [方案總管]  中，以滑鼠右鍵按一下專案，然後選取 [新增]   > [新增資料夾]  。</span><span class="sxs-lookup"><span data-stu-id="ce007-260">In **Solution Explorer**, right-click the project, and then select **Add** > **New Folder**.</span></span> <span data-ttu-id="ce007-261">當新的資料夾出現在 [方案總管] 中時，請將它命名為 "YoloParser"。</span><span class="sxs-lookup"><span data-stu-id="ce007-261">When the new folder appears in the Solution Explorer, name it "YoloParser".</span></span>

### <a name="create-bounding-boxes-and-dimensions"></a><span data-ttu-id="ce007-262">建立週框方塊和維度</span><span class="sxs-lookup"><span data-stu-id="ce007-262">Create bounding boxes and dimensions</span></span>

<span data-ttu-id="ce007-263">模型所輸出資料包含影像中物件的週框方塊座標及維度。</span><span class="sxs-lookup"><span data-stu-id="ce007-263">The data output by the model contains coordinates and dimensions of the bounding boxes of objects within the image.</span></span> <span data-ttu-id="ce007-264">建立維度的基底類別。</span><span class="sxs-lookup"><span data-stu-id="ce007-264">Create a base class for dimensions.</span></span>

1. <span data-ttu-id="ce007-265">在 [方案總管]  中，以滑鼠右鍵按一下 *YoloParser* 目錄，然後選取 [新增]   > [新增項目]  。</span><span class="sxs-lookup"><span data-stu-id="ce007-265">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="ce007-266">在 [新增項目]  對話方塊中，選取 [類別]  ，然後將 [名稱]  欄位變更為 *DimensionsBase.cs*。</span><span class="sxs-lookup"><span data-stu-id="ce007-266">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *DimensionsBase.cs*.</span></span> <span data-ttu-id="ce007-267">接著，選取 [新增]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="ce007-267">Then, select the **Add** button.</span></span>

    <span data-ttu-id="ce007-268">隨即在程式碼編輯器中開啟 *DimensionsBase.cs* 檔案。</span><span class="sxs-lookup"><span data-stu-id="ce007-268">The *DimensionsBase.cs* file opens in the code editor.</span></span> <span data-ttu-id="ce007-269">移除所有 `using` 陳述式及現有的類別定義。</span><span class="sxs-lookup"><span data-stu-id="ce007-269">Remove all `using` statements and existing class definition.</span></span> 

    <span data-ttu-id="ce007-270">將下列 `DimensionsBase` 類別的程式碼新增到 *DimensionsBase.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="ce007-270">Add the following code for the `DimensionsBase` class to the *DimensionsBase.cs* file:</span></span>

    [!code-csharp [DimensionsBaseClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/DimensionsBase.cs#L3-L9)]

    <span data-ttu-id="ce007-271">`DimensionsBase` 具備下列 `float` 欄位：</span><span class="sxs-lookup"><span data-stu-id="ce007-271">`DimensionsBase` has the following `float` fields:</span></span>

    - <span data-ttu-id="ce007-272">`X` 包含物件的 X 軸位置。</span><span class="sxs-lookup"><span data-stu-id="ce007-272">`X` contains the position of the object along the x-axis.</span></span>
    - <span data-ttu-id="ce007-273">`Y` 包含物件的 Y 軸位置。</span><span class="sxs-lookup"><span data-stu-id="ce007-273">`Y` contains the position of the object along the y-axis.</span></span>
    - <span data-ttu-id="ce007-274">`Height` 包含物件的高度。</span><span class="sxs-lookup"><span data-stu-id="ce007-274">`Height` contains the height of the object.</span></span>
    - <span data-ttu-id="ce007-275">`Width` 包含物件的寬度。</span><span class="sxs-lookup"><span data-stu-id="ce007-275">`Width` contains the width of the object.</span></span>

<span data-ttu-id="ce007-276">接下來，請建立週框方塊的類別。</span><span class="sxs-lookup"><span data-stu-id="ce007-276">Next, create a class for your bounding boxes.</span></span>

1. <span data-ttu-id="ce007-277">在 [方案總管]  中，以滑鼠右鍵按一下 *YoloParser* 目錄，然後選取 [新增]   > [新增項目]  。</span><span class="sxs-lookup"><span data-stu-id="ce007-277">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="ce007-278">在 [新增項目]  對話方塊中，選取 [類別]  ，然後將 [名稱]  欄位變更為 *YoloBoundingBox.cs*。</span><span class="sxs-lookup"><span data-stu-id="ce007-278">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *YoloBoundingBox.cs*.</span></span> <span data-ttu-id="ce007-279">接著，選取 [新增]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="ce007-279">Then, select the **Add** button.</span></span>

    <span data-ttu-id="ce007-280">隨即在程式碼編輯器中開啟 *YoloBoundingBox.cs* 檔案。</span><span class="sxs-lookup"><span data-stu-id="ce007-280">The *YoloBoundingBox.cs* file opens in the code editor.</span></span> <span data-ttu-id="ce007-281">將下列 `using` 陳述式新增到 *YoloBoundingBox.cs* 的頂端：</span><span class="sxs-lookup"><span data-stu-id="ce007-281">Add the following `using` statement to the top of *YoloBoundingBox.cs*:</span></span>

    [!code-csharp [YoloBoundingBoxUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L1)]

    <span data-ttu-id="ce007-282">在現有類別定義的上方，新增稱為 `BoundingBoxDimensions` 的新類別定義，並繼承 `DimensionsBase` 類別以包含個別週框方塊的維度。</span><span class="sxs-lookup"><span data-stu-id="ce007-282">Just above the existing class definition, add a new class definition called `BoundingBoxDimensions` which inherits from the `DimensionsBase` class to contain the dimensions of the respective bounding box.</span></span>

    [!code-csharp [BoundingBoxDimClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L5)]

    <span data-ttu-id="ce007-283">移除現有的 `YoloBoundingBox` 類別定義，然後將下列 `YoloBoundingBox` 類別的程式碼新增到 *YoloBoundingBox.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="ce007-283">Remove the existing `YoloBoundingBox` class definition and add the following code for the `YoloBoundingBox` class to the *YoloBoundingBox.cs* file:</span></span>

    [!code-csharp [YoloBoundingBoxClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L7-L21)]
    
    <span data-ttu-id="ce007-284">`YoloBoundingBox` 具備下列欄位：</span><span class="sxs-lookup"><span data-stu-id="ce007-284">`YoloBoundingBox` has the following fields:</span></span>

    - <span data-ttu-id="ce007-285">`Dimensions` 包含週框方塊的維度。</span><span class="sxs-lookup"><span data-stu-id="ce007-285">`Dimensions` contains dimensions of the bounding box.</span></span>
    - <span data-ttu-id="ce007-286">`Label` 包含在週框方塊內部所偵測到物件的類別。</span><span class="sxs-lookup"><span data-stu-id="ce007-286">`Label` contains the class of object detected within the bounding box.</span></span>
    - <span data-ttu-id="ce007-287">`Confidence` 包含類別的信賴度。</span><span class="sxs-lookup"><span data-stu-id="ce007-287">`Confidence` contains the confidence of the class.</span></span>
    - <span data-ttu-id="ce007-288">`Rect` 包含週框方塊維度的矩形表示法。</span><span class="sxs-lookup"><span data-stu-id="ce007-288">`Rect` contains the rectangle representation of the bounding box's dimensions.</span></span>
    - <span data-ttu-id="ce007-289">`BoxColor` 包含與個別類別建立關聯的色彩，用來在影像上進行繪製。</span><span class="sxs-lookup"><span data-stu-id="ce007-289">`BoxColor` contains the color associated with the respective class used to draw on the image.</span></span>

### <a name="create-the-parser"></a><span data-ttu-id="ce007-290">建立剖析器</span><span class="sxs-lookup"><span data-stu-id="ce007-290">Create the parser</span></span>

<span data-ttu-id="ce007-291">現在您已建立了維度和週框方塊的類別，是時候建立剖析器了。</span><span class="sxs-lookup"><span data-stu-id="ce007-291">Now that the classes for dimensions and bounding boxes are created, it's time to create the parser.</span></span>

1. <span data-ttu-id="ce007-292">在 [方案總管]  中，以滑鼠右鍵按一下 *YoloParser* 目錄，然後選取 [新增]   > [新增項目]  。</span><span class="sxs-lookup"><span data-stu-id="ce007-292">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="ce007-293">在 [新增項目]  對話方塊中，選取 [類別]  ，然後將 [名稱]  欄位變更為 *YoloOutputParser.cs*。</span><span class="sxs-lookup"><span data-stu-id="ce007-293">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *YoloOutputParser.cs*.</span></span> <span data-ttu-id="ce007-294">接著，選取 [新增]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="ce007-294">Then, select the **Add** button.</span></span>

    <span data-ttu-id="ce007-295">隨即在程式碼編輯器中開啟 *YoloOutputParser.cs* 檔案。</span><span class="sxs-lookup"><span data-stu-id="ce007-295">The *YoloOutputParser.cs* file opens in the code editor.</span></span> <span data-ttu-id="ce007-296">將下列 `using` 陳述式新增到 *YoloOutputParser.cs* 的頂端：</span><span class="sxs-lookup"><span data-stu-id="ce007-296">Add the following `using` statement to the top of *YoloOutputParser.cs*:</span></span>

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L1-L4)]

    <span data-ttu-id="ce007-297">在現有的 `YoloOutputParser` 類別定義中，新增包含影像中每個儲存格維度的巢狀類別。</span><span class="sxs-lookup"><span data-stu-id="ce007-297">Inside the existing `YoloOutputParser` class definition, add a nested class that contains the dimensions of each of the cells in the image.</span></span> <span data-ttu-id="ce007-298">將下列 `CellDimensions` 類別的程式碼新增到 `YoloOutputParser` 類別定義頂端，並繼承 `DimensionsBase` 類別。</span><span class="sxs-lookup"><span data-stu-id="ce007-298">Add the following code for the `CellDimensions` class which inherits from the `DimensionsBase` class at the top of the `YoloOutputParser` class definition.</span></span>

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L10)]

1. <span data-ttu-id="ce007-299">在 `YoloOutputParser` 類別定義內，新增下列常數及欄位。</span><span class="sxs-lookup"><span data-stu-id="ce007-299">Inside the `YoloOutputParser` class definition, add the following constant and fields.</span></span>

    [!code-csharp [ParserVarDefinitions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L12-L21)]    

    - <span data-ttu-id="ce007-300">`ROW_COUNT` 是影像所分割成格線中的資料列數。</span><span class="sxs-lookup"><span data-stu-id="ce007-300">`ROW_COUNT` is the number of rows in the grid the image is divided into.</span></span>
    - <span data-ttu-id="ce007-301">`COL_COUNT` 是影像所分割成格線中的資料行數。</span><span class="sxs-lookup"><span data-stu-id="ce007-301">`COL_COUNT` is the number of columns in the grid the image is divided into.</span></span>
    - <span data-ttu-id="ce007-302">`CHANNEL_COUNT` 是包含在格線單一儲存格中值的總數。</span><span class="sxs-lookup"><span data-stu-id="ce007-302">`CHANNEL_COUNT` is the total number of values contained in one cell of the grid.</span></span>
    - <span data-ttu-id="ce007-303">`BOXES_PER_CELL` 是儲存格中週框方塊的數量，</span><span class="sxs-lookup"><span data-stu-id="ce007-303">`BOXES_PER_CELL` is the number of bounding boxes in a cell,</span></span>
    - <span data-ttu-id="ce007-304">`BOX_INFO_FEATURE_COUNT` 是包含在方塊 (X、Y、高度、寬度及信賴度) 內的特徵數。</span><span class="sxs-lookup"><span data-stu-id="ce007-304">`BOX_INFO_FEATURE_COUNT` is the number of features contained within a box (x,y,height,width,confidence).</span></span>
    - <span data-ttu-id="ce007-305">`CLASS_COUNT` 是包含在每個週框方塊內的類別預測數。</span><span class="sxs-lookup"><span data-stu-id="ce007-305">`CLASS_COUNT` is the number of class predictions contained in each bounding box.</span></span>
    - <span data-ttu-id="ce007-306">`CELL_WIDTH` 是影像格線中單一儲存格的寬度。</span><span class="sxs-lookup"><span data-stu-id="ce007-306">`CELL_WIDTH` is the width of one cell in the image grid.</span></span>
    - <span data-ttu-id="ce007-307">`CELL_HEIGHT` 是影像格線中單一儲存格的高度。</span><span class="sxs-lookup"><span data-stu-id="ce007-307">`CELL_HEIGHT` is the height of one cell in the image grid.</span></span>
    - <span data-ttu-id="ce007-308">`channelStride` 是格線中目前儲存格的開始位置。</span><span class="sxs-lookup"><span data-stu-id="ce007-308">`channelStride` is the starting position of the current cell in the grid.</span></span>


    <span data-ttu-id="ce007-309">當模型對影像進行評分時，它會將 `416px x 416px` 輸入分成大小為 `13 x 13` 的儲存格格線。</span><span class="sxs-lookup"><span data-stu-id="ce007-309">When the model scores an image, it divides the `416px x 416px`input into a grid of cells the size of `13 x 13`.</span></span> <span data-ttu-id="ce007-310">每個儲存格都包含 `32px x 32px`。</span><span class="sxs-lookup"><span data-stu-id="ce007-310">Each cell contains is `32px x 32px`.</span></span> <span data-ttu-id="ce007-311">在每個儲存格中都有 5 個週框方塊，每個週框方塊都包含了 5 個特徵 (X、Y、高度、寬度、信賴度)。</span><span class="sxs-lookup"><span data-stu-id="ce007-311">Within each cell, there are 5 bounding boxes each containing 5 features (x, y, width, height, confidence).</span></span> <span data-ttu-id="ce007-312">此外，每個週框方塊都包含每個類別的機率 (在此案例中為 20)。</span><span class="sxs-lookup"><span data-stu-id="ce007-312">In addition, each bounding box contains the probability of each of the classes which in this case is 20.</span></span> <span data-ttu-id="ce007-313">因此，每個儲存格都包含 125 個資訊 (5 個特徵 + 20 個類別機率)。</span><span class="sxs-lookup"><span data-stu-id="ce007-313">Therefore, each cell contains 125 pieces of information (5 features + 20 class probabilities).</span></span> 

<span data-ttu-id="ce007-314">在 `channelStride` 的下方為 5 個週框方塊建立錨點清單：</span><span class="sxs-lookup"><span data-stu-id="ce007-314">Create a list of anchors below `channelStride` for all 5 bounding boxes:</span></span>

[!code-csharp [ParserAnchors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L23-L26)]   

<span data-ttu-id="ce007-315">錨點是週框方塊的預先定義高度及寬度比例。</span><span class="sxs-lookup"><span data-stu-id="ce007-315">Anchors are pre-defined height and width ratios of bounding boxes.</span></span> <span data-ttu-id="ce007-316">模型所偵測到的大多數物件或類別都具有類似比例。</span><span class="sxs-lookup"><span data-stu-id="ce007-316">Most object or classes detected by a model have similar ratios.</span></span> <span data-ttu-id="ce007-317">這在建立週框方塊時會非常實用。</span><span class="sxs-lookup"><span data-stu-id="ce007-317">This is valuable when it comes to creating bounding boxes.</span></span> <span data-ttu-id="ce007-318">相較於預測週框方塊，預先定義維度的位移會藉由計算取得，因此可減少預測週框方塊時所需的計算。</span><span class="sxs-lookup"><span data-stu-id="ce007-318">Instead of predicting the bounding boxes, the offset from the pre-defined dimensions is calculated therefore reducing the computation required to predict the bounding box.</span></span> <span data-ttu-id="ce007-319">通常這些錨點比例都會根據所使用的資料集進行計算。</span><span class="sxs-lookup"><span data-stu-id="ce007-319">Typically these anchor ratios are calculated based on the dataset used.</span></span> <span data-ttu-id="ce007-320">在此案例中，因為資料集已知且值都已經預先進行計算，因此我們可以針對錨點直接進行硬式編碼。</span><span class="sxs-lookup"><span data-stu-id="ce007-320">In this case because the dataset is known and the values have been pre-computed, the anchors can be hard-coded.</span></span>

<span data-ttu-id="ce007-321">接下來，請定義模型將預測的標籤或類別。</span><span class="sxs-lookup"><span data-stu-id="ce007-321">Next, define the labels or classes that the model will predict.</span></span> <span data-ttu-id="ce007-322">此模型會預測 20 個類別，這 20 個類別是原始 YOLOv2 模型所預測類別總數的子集。</span><span class="sxs-lookup"><span data-stu-id="ce007-322">This model predicts 20 classes which is a subset of the total number of classes predicted by the original YOLOv2 model.</span></span>

<span data-ttu-id="ce007-323">請在 `anchors` 下方新增標籤清單。</span><span class="sxs-lookup"><span data-stu-id="ce007-323">Add your list of labels below the `anchors`.</span></span> 

[!code-csharp [ParserLabels](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L28-L34)]

<span data-ttu-id="ce007-324">每個類別都有與其建立關聯的色彩。</span><span class="sxs-lookup"><span data-stu-id="ce007-324">There are colors associated with each of the classes.</span></span> <span data-ttu-id="ce007-325">請在 `labels` 下方指派類別色彩：</span><span class="sxs-lookup"><span data-stu-id="ce007-325">Assign your class colors below your `labels`:</span></span>

[!code-csharp [ParserColors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L36-L59)]

### <a name="create-helper-functions"></a><span data-ttu-id="ce007-326">建立協助程式函式</span><span class="sxs-lookup"><span data-stu-id="ce007-326">Create helper functions</span></span>

<span data-ttu-id="ce007-327">後續處理階段會涉及一系列的步驟。</span><span class="sxs-lookup"><span data-stu-id="ce007-327">There are a series of steps involved in the post-processing phase.</span></span> <span data-ttu-id="ce007-328">為了協助處理，我們可以採用幾個協助程式方法。</span><span class="sxs-lookup"><span data-stu-id="ce007-328">To help with that, several helper methods can be employed.</span></span> 

<span data-ttu-id="ce007-329">剖析器使用的協助程式方法包括：</span><span class="sxs-lookup"><span data-stu-id="ce007-329">The helper methods used in by the parser are:</span></span>

- <span data-ttu-id="ce007-330">`Sigmoid` 會套用 sigmoid 函式，輸出介於 0 和 1 之間的數字。</span><span class="sxs-lookup"><span data-stu-id="ce007-330">`Sigmoid` applies the sigmoid function that outputs a number between 0 and 1.</span></span>
- <span data-ttu-id="ce007-331">`Softmax` 會將輸入向量正常化為機率分佈。</span><span class="sxs-lookup"><span data-stu-id="ce007-331">`Softmax` normalizes an input vector into a probability distribution.</span></span>
- <span data-ttu-id="ce007-332">`GetOffset` 會將單一維度模型輸出中項目對應到 `125 x 13 x 13` Tensor 中相對應的位置。</span><span class="sxs-lookup"><span data-stu-id="ce007-332">`GetOffset` maps elements in the one-dimensional model output to the corresponding position in a `125 x 13 x 13` tensor.</span></span>
- <span data-ttu-id="ce007-333">`ExtractBoundingBoxes` 會使用模型輸出的 `GetOffset` 方法擷取週框方塊維度。</span><span class="sxs-lookup"><span data-stu-id="ce007-333">`ExtractBoundingBoxes` extracts the bounding box dimensions using the `GetOffset` method from the model output.</span></span>
- <span data-ttu-id="ce007-334">`GetConfidence` 會擷取信賴度值，其指出模型針對所偵測到物件的確信度，並使用 `Sigmoid` 函式將它轉換成百分比。</span><span class="sxs-lookup"><span data-stu-id="ce007-334">`GetConfidence` extracts the confidence value which states how sure the model is that it has detected an object and uses the `Sigmoid` function to turn it into a percentage.</span></span>
- <span data-ttu-id="ce007-335">`MapBoundingBoxToCell` 會使用週框方塊維度，並將它們對應到影像內的個別儲存格。</span><span class="sxs-lookup"><span data-stu-id="ce007-335">`MapBoundingBoxToCell` uses the bounding box dimensions and maps them onto its respective cell within the image.</span></span>
- <span data-ttu-id="ce007-336">`ExtractClasses` 會使用 `GetOffset` 方法從模型輸出擷取週框方塊的類別預測，並使用 `Softmax` 方法將它們轉換成機率分佈。</span><span class="sxs-lookup"><span data-stu-id="ce007-336">`ExtractClasses` extracts the class predictions for the bounding box from the model output using the `GetOffset` method and turns them into a probability distribution using the `Softmax` method.</span></span>
- <span data-ttu-id="ce007-337">`GetTopResult` 會從預測類別清單選取機率最高的類別。</span><span class="sxs-lookup"><span data-stu-id="ce007-337">`GetTopResult` selects the class from the list of predicted classes with the highest probability.</span></span>
- <span data-ttu-id="ce007-338">`IntersectionOverUnion` 會篩選機率較低的重疊週框方塊。</span><span class="sxs-lookup"><span data-stu-id="ce007-338">`IntersectionOverUnion` filters overlapping bounding boxes with lower probabilities.</span></span>

<span data-ttu-id="ce007-339">將所有協助程式方法的程式碼新增到 `classColors` 清單下方。</span><span class="sxs-lookup"><span data-stu-id="ce007-339">Add the code for all the helper methods below your list of `classColors`.</span></span>

[!code-csharp [ParserHelperMethods](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L61-L151)]

<span data-ttu-id="ce007-340">在您定義完所有協助程式方法後，是時候使用它們來處理模型輸出了。</span><span class="sxs-lookup"><span data-stu-id="ce007-340">Once you have defined all of the helper methods, it's time to use them to process the model output.</span></span>

<span data-ttu-id="ce007-341">請在 `IntersectionOverUnion` 方法的下方建立 `ParseOutputs` 方法來處理模型所產生輸出。</span><span class="sxs-lookup"><span data-stu-id="ce007-341">Below the `IntersectionOverUnion` method, create the `ParseOutputs` method to process the output generated by the model.</span></span>

```csharp
public IList<YoloBoundingBox> ParseOutputs(float[] yoloModelOutputs, float threshold = .3F)
{

}
```
    
<span data-ttu-id="ce007-342">在 `ParseOutputs` 方法內建立清單來儲存您的週框方塊及定義變數。</span><span class="sxs-lookup"><span data-stu-id="ce007-342">Create a list to store your bounding boxes and define variables inside the `ParseOutputs` method.</span></span>

[!code-csharp [BBoxList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L155)]

<span data-ttu-id="ce007-343">每個影像都會分成 `13 x 13` 個儲存格的格線。</span><span class="sxs-lookup"><span data-stu-id="ce007-343">Each image is divided into a grid of `13 x 13` cells.</span></span> <span data-ttu-id="ce007-344">每個儲存格都包含五個週框方塊。</span><span class="sxs-lookup"><span data-stu-id="ce007-344">Each cell contains five bounding boxes.</span></span> <span data-ttu-id="ce007-345">在 `boxes` 變數的下方，新增程式碼來處理每個儲存格中的所有方塊。</span><span class="sxs-lookup"><span data-stu-id="ce007-345">Below the `boxes` variable, add code to process all of the boxes in each of the cells.</span></span>

```csharp
for (int row = 0; row < ROW_COUNT; row++)
{
    for (int column = 0; column < COL_COUNT; column++)
    {
        for (int box = 0; box < BOXES_PER_CELL; box++)
        {

        }
    }
}
```

<span data-ttu-id="ce007-346">在最內層的迴圈中，計算目前方塊在單一維度模型輸出內的開始位置。</span><span class="sxs-lookup"><span data-stu-id="ce007-346">Inside the inner-most loop, calculate the starting position of the current box within the one-dimensional model output.</span></span>

[!code-csharp [ChannelDef](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L163)]

<span data-ttu-id="ce007-347">在其下方立即使用 `ExtractBoundingBoxDimensions` 方法來取得目前週框方塊的維度。</span><span class="sxs-lookup"><span data-stu-id="ce007-347">Directly below that, use the `ExtractBoundingBoxDimensions` method to get the dimensions of the current bounding box.</span></span>

[!code-csharp [GetBBoxDims](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L165)]

<span data-ttu-id="ce007-348">然後，請使用 `GetConfidence` 方法取得目前週框方塊的信賴度。</span><span class="sxs-lookup"><span data-stu-id="ce007-348">Then, use the `GetConfidence` method to get the confidence for the current bounding box.</span></span>

[!code-csharp [GetConfidence](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L167)]

<span data-ttu-id="ce007-349">之後，請使用 `MapBoundingBoxToCell` 方法將目前週框方塊對應到目前正在處理的儲存格。</span><span class="sxs-lookup"><span data-stu-id="ce007-349">After that, use the `MapBoundingBoxToCell` method to map the current bounding box to the current cell being processed.</span></span>

[!code-csharp [MapBoundingBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L169)]

<span data-ttu-id="ce007-350">在進行任何更進一步的處理前，請先檢查您的信賴度值是否大於所提供閾值。</span><span class="sxs-lookup"><span data-stu-id="ce007-350">Before doing any further processing, check whether your confidence value is greater than the threshold provided.</span></span> <span data-ttu-id="ce007-351">若沒有，請處理下一個週框方塊。</span><span class="sxs-lookup"><span data-stu-id="ce007-351">If not, process the next bounding box.</span></span>

[!code-csharp [CheckThreshold1](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L171-L172)]

<span data-ttu-id="ce007-352">否則，請繼續處理輸出。</span><span class="sxs-lookup"><span data-stu-id="ce007-352">Otherwise, continue processing the output.</span></span> <span data-ttu-id="ce007-353">下一個步驟是使用 `ExtractClasses` 方法取得目前週框方塊預測類別的機率分佈。</span><span class="sxs-lookup"><span data-stu-id="ce007-353">The next step is to get the probability distribution of the predicted classes for the current bounding box using the `ExtractClasses` method.</span></span>

[!code-csharp [ExtractClasses](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L174)]

<span data-ttu-id="ce007-354">然後，使用 `GetTopResult` 方法取得目前週框方塊機率最高的類別值和索引，並計算其分數。</span><span class="sxs-lookup"><span data-stu-id="ce007-354">Then, use the `GetTopResult` method to get the value and index of the class with the highest probability for the current box and compute its score.</span></span>

[!code-csharp [GetTopResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L176-L177)]

<span data-ttu-id="ce007-355">使用 `topScore` 再次並僅保存高於指定閾值的週框方塊。</span><span class="sxs-lookup"><span data-stu-id="ce007-355">Use the `topScore` to once again keep only those bounding boxes that are above the specified threshold.</span></span>

[!code-csharp [CheckThreshold2](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L179-L180)]

<span data-ttu-id="ce007-356">最後，若目前的週框方塊超過閾值，請建立新的 `BoundingBox` 物件並將它新增到 `boxes` 清單。</span><span class="sxs-lookup"><span data-stu-id="ce007-356">Finally, if the current bounding box exceeds the threshold, create a new `BoundingBox` object and add it to the `boxes` list.</span></span>

[!code-csharp [AddBBoxToList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L182-L194)]

<span data-ttu-id="ce007-357">在處理完影像中所有的儲存格後，傳回 `boxes` 清單。</span><span class="sxs-lookup"><span data-stu-id="ce007-357">Once all cells in the image have been processed, return the `boxes` list.</span></span> <span data-ttu-id="ce007-358">將下列 return 陳述式新增到 `ParseOutputs` 方法最外層 for 迴圈的下方。</span><span class="sxs-lookup"><span data-stu-id="ce007-358">Add the following return statement below the outer-most for-loop in the `ParseOutputs` method.</span></span>

[!code-csharp [ReturnBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L198)]

### <a name="filter-overlapping-boxes"></a><span data-ttu-id="ce007-359">篩選重疊方塊</span><span class="sxs-lookup"><span data-stu-id="ce007-359">Filter overlapping boxes</span></span>

<span data-ttu-id="ce007-360">現在您已從模型輸出擷取所有信賴度較高的週框方塊，您仍需要進行額外篩選才能移除重疊的影像。</span><span class="sxs-lookup"><span data-stu-id="ce007-360">Now that all of the highly confident bounding boxes have been extracted from the model output, additional filtering needs to be done to remove overlapping images.</span></span> <span data-ttu-id="ce007-361">在 `ParseOutputs` 方法下方新增稱為 `FilterBoundingBoxes` 的方法：</span><span class="sxs-lookup"><span data-stu-id="ce007-361">Add a method called `FilterBoundingBoxes` below the `ParseOutputs` method:</span></span>

```csharp
public IList<YoloBoundingBox> FilterBoundingBoxes(IList<YoloBoundingBox> boxes, int limit, float threshold)
{

}
```

<span data-ttu-id="ce007-362">在 `FilterBoundingBoxes` 方法中，從建立大小與所偵測方塊相等的陣列，並將所有位置標記為使用中或準備好進行處理。</span><span class="sxs-lookup"><span data-stu-id="ce007-362">Inside the `FilterBoundingBoxes` method, start off by creating an array equal to the size of detected boxes and marking all slots as active or ready for processing.</span></span>

[!code-csharp [InitActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L203-L207)]

<span data-ttu-id="ce007-363">接著，根據信賴度依照遞減排序來排序包含您週框方塊的清單。</span><span class="sxs-lookup"><span data-stu-id="ce007-363">Then, sort the list containing your bounding boxes in descending order based on confidence.</span></span>

[!code-csharp [SortBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L209-L211)]

<span data-ttu-id="ce007-364">之後，建立保存篩選後結果的清單。</span><span class="sxs-lookup"><span data-stu-id="ce007-364">After that, create a list to hold the filtered results.</span></span>

[!code-csharp [InitFilterResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L213)]

<span data-ttu-id="ce007-365">逐一查看每個週框方塊來開始處理每個週框方塊。</span><span class="sxs-lookup"><span data-stu-id="ce007-365">Begin processing each bounding box by iterating over each of the bounding boxes.</span></span>

```csharp
for (int i = 0; i < boxes.Count; i++)
{

}
```

<span data-ttu-id="ce007-366">在此 for 迴圈中，檢查目前的週框方塊是否可以進行處理。</span><span class="sxs-lookup"><span data-stu-id="ce007-366">Inside of this for-loop, check whether the current bounding box can be processed.</span></span>

```csharp
if (isActiveBoxes[i])
{
    
}
```

<span data-ttu-id="ce007-367">若可以進行處理，請將週框方塊新增到結果清單。</span><span class="sxs-lookup"><span data-stu-id="ce007-367">If so, add the bounding box to the list of results.</span></span> <span data-ttu-id="ce007-368">若結果超過指定的擷取方塊數限制，請中斷迴圈。</span><span class="sxs-lookup"><span data-stu-id="ce007-368">If the results exceeds the specified limit of boxes to be extracted, break out of the loop.</span></span> <span data-ttu-id="ce007-369">在 if 陳述式中新增下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="ce007-369">Add the following code inside the if-statement.</span></span>

[!code-csharp [AddFirstBBoxToResults](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L219-L223)]

<span data-ttu-id="ce007-370">否則，請查看相鄰的週框方塊。</span><span class="sxs-lookup"><span data-stu-id="ce007-370">Otherwise, look at the adjacent bounding boxes.</span></span> <span data-ttu-id="ce007-371">在方塊數限制檢查的下方新增下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="ce007-371">Add the following code below the box limit check.</span></span>

```csharp
for (var j = i + 1; j < boxes.Count; j++)
{

}
```

<span data-ttu-id="ce007-372">與第一個方塊相似，若相鄰的方塊已為使用中或是準備好進行處理，請使用 `IntersectionOverUnion` 方法來檢查第一個方塊和第二個方塊是否超過指定的閾值。</span><span class="sxs-lookup"><span data-stu-id="ce007-372">Like the first box, if the adjacent box is active or ready to be processed, use the `IntersectionOverUnion` method to check whether the first box and the second box exceed the specified threshold.</span></span> <span data-ttu-id="ce007-373">將下列程式碼新增到您最內層的 for 迴圈。</span><span class="sxs-lookup"><span data-stu-id="ce007-373">Add the following code to your inner-most for-loop.</span></span>

[!code-csharp [IOUBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L227-L239)]

<span data-ttu-id="ce007-374">在最內層檢查相鄰週框方塊的 for 迴圈外部，查看是否有任何需要處理的剩餘週框方塊。</span><span class="sxs-lookup"><span data-stu-id="ce007-374">Outside of the inner-most for-loop that checks adjacent bounding boxes, see whether there are any remaining bounding boxes to be processed.</span></span> <span data-ttu-id="ce007-375">若沒有的話，請中斷外層的 for 迴圈。</span><span class="sxs-lookup"><span data-stu-id="ce007-375">If not, break out of the outer for-loop.</span></span>

[!code-csharp [CheckActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L242-L243)]

<span data-ttu-id="ce007-376">最後，在 `FilterBoundingBoxes` 方法初始 for 迴圈的外部，傳回結果：</span><span class="sxs-lookup"><span data-stu-id="ce007-376">Finally, outside of the initial for-loop of the `FilterBoundingBoxes` method, return the results:</span></span>

[!code-csharp [ReturnFilteredBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L246)]

<span data-ttu-id="ce007-377">太棒了！</span><span class="sxs-lookup"><span data-stu-id="ce007-377">Great!</span></span> <span data-ttu-id="ce007-378">現在是時候搭配模型使用此程式碼來進行評分了。</span><span class="sxs-lookup"><span data-stu-id="ce007-378">Now it's time to use this code along with the model for scoring.</span></span>

## <a name="use-the-model-for-scoring"></a><span data-ttu-id="ce007-379">使用模型進行評分</span><span class="sxs-lookup"><span data-stu-id="ce007-379">Use the model for scoring</span></span>

<span data-ttu-id="ce007-380">與後續處理相似，評分步驟中也有幾個步驟。</span><span class="sxs-lookup"><span data-stu-id="ce007-380">Just like with post-processing, there are a few steps in the scoring steps.</span></span> <span data-ttu-id="ce007-381">為了協助處理，請將包含評分邏輯的類別新增至專案。</span><span class="sxs-lookup"><span data-stu-id="ce007-381">To help with this, add a class that will contain the scoring logic to your project.</span></span>

1. <span data-ttu-id="ce007-382">在 [方案總管]  中，於專案上按一下滑鼠右鍵，然後選取 [新增]   > [新增項目]  。</span><span class="sxs-lookup"><span data-stu-id="ce007-382">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="ce007-383">在 [新增項目]  對話方塊中，選取 [類別]  ，然後將 [名稱]  欄位變更為 *OnnxModelScorer.cs*。</span><span class="sxs-lookup"><span data-stu-id="ce007-383">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *OnnxModelScorer.cs*.</span></span> <span data-ttu-id="ce007-384">接著，選取 [新增]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="ce007-384">Then, select the **Add** button.</span></span>

    <span data-ttu-id="ce007-385">隨即在程式碼編輯器中開啟 *OnnxModelScorer.cs* 檔案。</span><span class="sxs-lookup"><span data-stu-id="ce007-385">The *OnnxModelScorer.cs* file opens in the code editor.</span></span> <span data-ttu-id="ce007-386">將下列 `using` 陳述式新增至 *OnnxModelScorer.cs* 的頂端：</span><span class="sxs-lookup"><span data-stu-id="ce007-386">Add the following `using` statement to the top of *OnnxModelScorer.cs*:</span></span>

    [!code-csharp [ScorerUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L1-L7)]

    <span data-ttu-id="ce007-387">在 `OnnxModelScorer` 類別定義的內部，新增下列變數。</span><span class="sxs-lookup"><span data-stu-id="ce007-387">Inside the `OnnxModelScorer` class definition, add the following variables.</span></span>

    [!code-csharp [InitScorerVars](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L13-L17)]

    <span data-ttu-id="ce007-388">在其正下方，建立 `OnnxModelScorer` 類別的建構函式，初始化先前定義的變數。</span><span class="sxs-lookup"><span data-stu-id="ce007-388">Directly below that, create a constructor for the `OnnxModelScorer` class that will initialize the previously defined variables.</span></span>

    [!code-csharp [ScorerCtor](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L19-L24)]

    <span data-ttu-id="ce007-389">在您建立建構函式後，請定義幾個結構，其包含與影像和模型設定相關的變數。</span><span class="sxs-lookup"><span data-stu-id="ce007-389">Once you have created the constructor, define a couple of structs that contain variables related to the image and model settings.</span></span> <span data-ttu-id="ce007-390">建立稱為 `ImageNetSettings` 的結構，來包含預期作為模型輸入的高度和寬度。</span><span class="sxs-lookup"><span data-stu-id="ce007-390">Create a struct called `ImageNetSettings` to contain the height and width expected as input for the model.</span></span>

    [!code-csharp [ImageNetSettingStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L26-L30)]

    <span data-ttu-id="ce007-391">之後，請建立另一個稱為 `TinyYoloModelSettings` 的結構，其包含模型輸入和輸出層的名稱。</span><span class="sxs-lookup"><span data-stu-id="ce007-391">After that, create another struct called `TinyYoloModelSettings` which contains the names of the input and output layers of the model.</span></span> <span data-ttu-id="ce007-392">若要視覺化模型輸入和輸出層的名稱，您可以使用 [Netron](https://github.com/lutzroeder/netron) 等工具。</span><span class="sxs-lookup"><span data-stu-id="ce007-392">To visualize the name of the input and output layers of the model, you can use a tool like [Netron](https://github.com/lutzroeder/netron).</span></span>

    [!code-csharp [YoloSettingsStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L32-L43)]

    <span data-ttu-id="ce007-393">接下來，請建立用來評分的第一組方法。</span><span class="sxs-lookup"><span data-stu-id="ce007-393">Next, create the first set of methods use for scoring.</span></span> <span data-ttu-id="ce007-394">在您的 `OnnxModelScorer` 類別中建立 `LoadModel` 方法。</span><span class="sxs-lookup"><span data-stu-id="ce007-394">Create the `LoadModel` method inside of your `OnnxModelScorer` class.</span></span>

    ```csharp
    private ITransformer LoadModel(string modelLocation)
    {

    }
    ```

    <span data-ttu-id="ce007-395">在 `LoadModel` 方法中，新增下列程式碼來進行記錄。</span><span class="sxs-lookup"><span data-stu-id="ce007-395">Inside the `LoadModel` method, add the following code for logging.</span></span>

    [!code-csharp [LoadModelLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L47-L49)]

    <span data-ttu-id="ce007-396">ML.NET 管線通常會預期資料在呼叫 [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) 方法時運作。</span><span class="sxs-lookup"><span data-stu-id="ce007-396">ML.NET pipelines typically expect data to operate on when the [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) method is called.</span></span> <span data-ttu-id="ce007-397">在此案例中，我們會使用與定型相似的處理過程。</span><span class="sxs-lookup"><span data-stu-id="ce007-397">In this case, a process similar to training will be used.</span></span> <span data-ttu-id="ce007-398">但是，由於實際上不會進行定型，因此我們也可以使用空白的 [`IDataView`](xref:Microsoft.ML.IDataView)。</span><span class="sxs-lookup"><span data-stu-id="ce007-398">However, because no actual training is happening, it is acceptable to use an empty [`IDataView`](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="ce007-399">從空白清單為管線建立新的 [`IDataView`](xref:Microsoft.ML.IDataView)。</span><span class="sxs-lookup"><span data-stu-id="ce007-399">Create a new [`IDataView`](xref:Microsoft.ML.IDataView) for the pipeline from an empty list.</span></span>

    [!code-csharp [LoadEmptyIDV](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L52)]    

    <span data-ttu-id="ce007-400">在其下方定義管線。</span><span class="sxs-lookup"><span data-stu-id="ce007-400">Below that, define the pipeline.</span></span> <span data-ttu-id="ce007-401">管線會由四個轉換組成。</span><span class="sxs-lookup"><span data-stu-id="ce007-401">The pipeline will consist of four transforms.</span></span>

    - <span data-ttu-id="ce007-402">[`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*) 會將影像作為點陣圖載入。</span><span class="sxs-lookup"><span data-stu-id="ce007-402">[`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*) loads the image as a Bitmap.</span></span>
    - <span data-ttu-id="ce007-403">[`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*) 會將影像的大小重新調整為指定大小 (在此案例中為 `416 x 416`)。</span><span class="sxs-lookup"><span data-stu-id="ce007-403">[`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*) rescales the image to the size specified (in this case, `416 x 416`).</span></span>
    - <span data-ttu-id="ce007-404">[`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*) 會將影像的像素表示法從點陣圖變更為數值向量。</span><span class="sxs-lookup"><span data-stu-id="ce007-404">[`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*) changes the pixel representation of the image from a Bitmap to a numerical vector.</span></span>
    - <span data-ttu-id="ce007-405">[`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*) 會載入 ONNX 模型並用它來對提供的資料進行評分。</span><span class="sxs-lookup"><span data-stu-id="ce007-405">[`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*) loads the ONNX model and uses it to score on the data provided.</span></span>

    <span data-ttu-id="ce007-406">在 `data` 變數下方的 `LoadModel` 方法中定義您的管線。</span><span class="sxs-lookup"><span data-stu-id="ce007-406">Define your pipeline in the `LoadModel` method below the `data` variable.</span></span>

    [!code-csharp [ScoringPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L55-L58)]

    <span data-ttu-id="ce007-407">現在是時候具現化模型以進行評分了。</span><span class="sxs-lookup"><span data-stu-id="ce007-407">Now it's time to instantiate the model for scoring.</span></span> <span data-ttu-id="ce007-408">請在管線上呼叫 [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) 方法並傳回它以進行更進一步的處理。</span><span class="sxs-lookup"><span data-stu-id="ce007-408">Call the [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) method on the pipeline and return it for further processing.</span></span>

    [!code-csharp [FitReturnModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L61-L63)]

<span data-ttu-id="ce007-409">載入模型後，便可以用它來進行預測。</span><span class="sxs-lookup"><span data-stu-id="ce007-409">Once the model is loaded, it can then be used to make predictions.</span></span> <span data-ttu-id="ce007-410">若要輔助該程序，請在 `LoadModel` 方法的下方建立稱為 `PredictDataUsingModel` 的方法。</span><span class="sxs-lookup"><span data-stu-id="ce007-410">To facilitate that process, create a method called `PredictDataUsingModel` below the `LoadModel` method.</span></span>

```csharp
private IEnumerable<float[]> PredictDataUsingModel(IDataView testData, ITransformer model)
{

}
```

<span data-ttu-id="ce007-411">在 `PredictDataUsingModel` 中，新增下列程式碼來進行記錄。</span><span class="sxs-lookup"><span data-stu-id="ce007-411">Inside the `PredictDataUsingModel`, add the following code for logging.</span></span>

[!code-csharp [PredictDataLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L68-L71)]

<span data-ttu-id="ce007-412">然後，請使用 [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) 方法來對資料進行評分。</span><span class="sxs-lookup"><span data-stu-id="ce007-412">Then, use the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method to score the data.</span></span>

[!code-csharp [ScoreImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L73)]

<span data-ttu-id="ce007-413">擷取預測的機率並傳回它們以進行進一步處理。</span><span class="sxs-lookup"><span data-stu-id="ce007-413">Extract the predicted probabilities and return them for additional processing.</span></span>

[!code-csharp [ReturnModelOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L75-L77)]

<span data-ttu-id="ce007-414">現在您已設定完這兩個步驟，請將它們合併成單一方法。</span><span class="sxs-lookup"><span data-stu-id="ce007-414">Now that both steps are set up, combine them into a single method.</span></span> <span data-ttu-id="ce007-415">在 `PredictDataUsingModel` 方法的下方，新增稱為 `Score` 的新方法。</span><span class="sxs-lookup"><span data-stu-id="ce007-415">Below the `PredictDataUsingModel` method, add a new method called `Score`.</span></span>

[!code-csharp [ScoreMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L80-L85)]

<span data-ttu-id="ce007-416">即將完成！</span><span class="sxs-lookup"><span data-stu-id="ce007-416">Almost there!</span></span> <span data-ttu-id="ce007-417">現在是時候統整所有項目並加以使用了。</span><span class="sxs-lookup"><span data-stu-id="ce007-417">Now it's time to put it all to use.</span></span>

## <a name="detect-objects"></a><span data-ttu-id="ce007-418">偵測物件</span><span class="sxs-lookup"><span data-stu-id="ce007-418">Detect objects</span></span>

<span data-ttu-id="ce007-419">現在您已完成所有設定，是時候來偵測一些物件了。</span><span class="sxs-lookup"><span data-stu-id="ce007-419">Now that all of the setup is complete, it's time to detect some objects.</span></span> <span data-ttu-id="ce007-420">請在您 *Program.cs* 類別的 `Main` 方法中，新增一個 try-catch 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ce007-420">Inside the `Main` method of your *Program.cs* class, add a try-catch statement.</span></span>

```csharp
try
{

}
catch (Exception ex)
{
    Console.WriteLine(ex.ToString());
}
```

<span data-ttu-id="ce007-421">在 `try` 區塊中，開始實作物件偵測邏輯。</span><span class="sxs-lookup"><span data-stu-id="ce007-421">Inside of the `try` block, start implementing the object detection logic.</span></span> <span data-ttu-id="ce007-422">首先，請將資料載入 [`IDataView`](xref:Microsoft.ML.IDataView)。</span><span class="sxs-lookup"><span data-stu-id="ce007-422">First, load the data into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

[!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L29-L30)]

<span data-ttu-id="ce007-423">然後，請建立 `OnnxModelScorer` 的執行個體，並用它來對載入的資料進行評分。</span><span class="sxs-lookup"><span data-stu-id="ce007-423">Then, create an instance of `OnnxModelScorer` and use it to score the loaded data.</span></span>

[!code-csharp [ScoreData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L33-L36)]

<span data-ttu-id="ce007-424">現在是時候進行後續處理步驟了。</span><span class="sxs-lookup"><span data-stu-id="ce007-424">Now it's time for the post-processing step.</span></span> <span data-ttu-id="ce007-425">建立 `YoloOutputParser` 的執行個體，然後用它來處理模型輸出。</span><span class="sxs-lookup"><span data-stu-id="ce007-425">Create an instance of `YoloOutputParser` and use it to process the model output.</span></span>

[!code-csharp [ParsePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L39-L44)]

<span data-ttu-id="ce007-426">處理完模型輸出後，是時候在影像上繪製週框方塊了。</span><span class="sxs-lookup"><span data-stu-id="ce007-426">Once the model output has been processed, it's time to draw the bounding boxes on the images.</span></span> <span data-ttu-id="ce007-427">請建立 for 迴圈來逐一查看每個經過評分的影像。</span><span class="sxs-lookup"><span data-stu-id="ce007-427">Create a for-loop to iterate over each of the scored images.</span></span>

```csharp
for (var i = 0; i < images.Count(); i++)
{

}
```

<span data-ttu-id="ce007-428">在 for 迴圈內，取得影像檔案名稱及與其建立關聯的週框方塊。</span><span class="sxs-lookup"><span data-stu-id="ce007-428">Inside of the for-loop, get the name of the image file and the bounding boxes associated with it.</span></span>

[!code-csharp [GetImageFileName](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L49-L50)]

<span data-ttu-id="ce007-429">在其下方，使用 `DrawBoundingBox` 方法來在影像上繪製週框方塊。</span><span class="sxs-lookup"><span data-stu-id="ce007-429">Below that, use the `DrawBoundingBox` method to draw the bounding boxes on the image.</span></span>

[!code-csharp [DrawBBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L52)]

<span data-ttu-id="ce007-430">最後，使用 `LogDetectedObjects` 方法來新增一些記錄邏輯。</span><span class="sxs-lookup"><span data-stu-id="ce007-430">Lastly, add some logging logic with the `LogDetectedObjects` method.</span></span>

[!code-csharp [LogPredictionsOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L54)]


<span data-ttu-id="ce007-431">在 try-catch 陳述式後，新增其他邏輯來指出程序已執行完成。</span><span class="sxs-lookup"><span data-stu-id="ce007-431">After the try-catch statement, add additional logic to indicate the process is done running.</span></span>

[!code-csharp [EndProcessLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L62-L63)]

<span data-ttu-id="ce007-432">就這麼容易！</span><span class="sxs-lookup"><span data-stu-id="ce007-432">That's it!</span></span> 

## <a name="results"></a><span data-ttu-id="ce007-433">結果</span><span class="sxs-lookup"><span data-stu-id="ce007-433">Results</span></span> 

<span data-ttu-id="ce007-434">完成上述步驟後，請執行主控台應用程式 (Ctrl + F5)。</span><span class="sxs-lookup"><span data-stu-id="ce007-434">After following the previous steps, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="ce007-435">您的結果應該與下列輸出類似。</span><span class="sxs-lookup"><span data-stu-id="ce007-435">Your results should be similar to the following output.</span></span> <span data-ttu-id="ce007-436">您可能會看到警告或處理中訊息，但為了讓結果變得清楚，這些訊息已從下列結果中移除。</span><span class="sxs-lookup"><span data-stu-id="ce007-436">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

```console
=====Identify the objects in the images=====

.....The objects in the image image1.jpg are detected as below....
car and its Confidence score: 0.9697262
car and its Confidence score: 0.6674225
person and its Confidence score: 0.5226039
car and its Confidence score: 0.5224892
car and its Confidence score: 0.4675332

.....The objects in the image image2.jpg are detected as below....
cat and its Confidence score: 0.6461141
cat and its Confidence score: 0.6400049

.....The objects in the image image3.jpg are detected as below....
chair and its Confidence score: 0.840578
chair and its Confidence score: 0.796363
diningtable and its Confidence score: 0.6056048
diningtable and its Confidence score: 0.3737402

.....The objects in the image image4.jpg are detected as below....
dog and its Confidence score: 0.7608147
person and its Confidence score: 0.6321323
dog and its Confidence score: 0.5967442
person and its Confidence score: 0.5730394
person and its Confidence score: 0.5551759

========= End of Process..Hit any Key ========
```

<span data-ttu-id="ce007-437">若要查看包含週框方塊的影像，請巡覽至 `assets/images/output/` 目錄。</span><span class="sxs-lookup"><span data-stu-id="ce007-437">To see the images with bounding boxes, navigate to the `assets/images/output/` directory.</span></span> <span data-ttu-id="ce007-438">以下是其中一個經處理影像的範例。</span><span class="sxs-lookup"><span data-stu-id="ce007-438">Below is a sample from one of the processed images.</span></span> 

![](./media/object-detection-onnx/image3.jpg)

<span data-ttu-id="ce007-439">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="ce007-439">Congratulations!</span></span> <span data-ttu-id="ce007-440">您已透過在 ML.NET 中重複使用已預先定型的 `ONNX` 模型，成功建置出可用來偵測物件的機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="ce007-440">You've now successfully built a machine learning model for object detection by reusing a pre-trained `ONNX` model in ML.NET.</span></span>

<span data-ttu-id="ce007-441">您可以在 [dotnet/samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="ce007-441">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) repository.</span></span>

<span data-ttu-id="ce007-442">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="ce007-442">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="ce007-443">了解問題</span><span class="sxs-lookup"><span data-stu-id="ce007-443">Understand the problem</span></span>
> * <span data-ttu-id="ce007-444">了解 ONNX 是什麼，以及它和 ML.NET 搭配運作的方式</span><span class="sxs-lookup"><span data-stu-id="ce007-444">Learn what ONNX is and how it works with ML.NET</span></span>
> * <span data-ttu-id="ce007-445">了解模型</span><span class="sxs-lookup"><span data-stu-id="ce007-445">Understand the model</span></span>
> * <span data-ttu-id="ce007-446">重複使用預先定型的模型</span><span class="sxs-lookup"><span data-stu-id="ce007-446">Reuse the pre-trained model</span></span>
> * <span data-ttu-id="ce007-447">使用載入的模型偵測物件</span><span class="sxs-lookup"><span data-stu-id="ce007-447">Detect objects with a loaded model</span></span>

<span data-ttu-id="ce007-448">查看機器學習範例 GitHub 存放庫，探索更複雜的物件偵測範例。</span><span class="sxs-lookup"><span data-stu-id="ce007-448">Check out the Machine Learning samples GitHub repository to explore an expanded object detection sample.</span></span>
> [!div class="nextstepaction"]
> <span data-ttu-id="ce007-449">[dotnet/machinelearning-samples GitHub 存放庫](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/DeepLearning_ObjectDetection_Onnx) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="ce007-449">[dotnet/machinelearning-samples GitHub repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/DeepLearning_ObjectDetection_Onnx)</span></span>
