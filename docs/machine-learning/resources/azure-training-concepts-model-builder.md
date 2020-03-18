---
title: 模型產生器 Azure 訓練資源
description: Azure 機器學習資源指南
ms.topic: reference
ms.date: 02/27/2020
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: a19e13955d0eaea344109eb817f3a3959c3dd883
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185827"
---
# <a name="model-builder-azure-training-resources"></a><span data-ttu-id="34e84-103">模型產生器 Azure 訓練資源</span><span class="sxs-lookup"><span data-stu-id="34e84-103">Model Builder Azure Training Resources</span></span>

<span data-ttu-id="34e84-104">以下是説明您瞭解有關使用模型產生器在 Azure 中訓練模型的資源的指南。</span><span class="sxs-lookup"><span data-stu-id="34e84-104">The following is a guide to help you learn more about resources used to train models in Azure with Model Builder.</span></span>

## <a name="what-is-an-azure-machine-learning-experiment"></a><span data-ttu-id="34e84-105">什麼是 Azure 機器學習實驗？</span><span class="sxs-lookup"><span data-stu-id="34e84-105">What is an Azure Machine Learning experiment?</span></span>

<span data-ttu-id="34e84-106">Azure 機器學習實驗是在 Azure 上運行模型產生器培訓之前需要創建的資源。</span><span class="sxs-lookup"><span data-stu-id="34e84-106">An Azure Machine Learning experiment is a resource that needs to be created before running Model Builder training on Azure.</span></span>

<span data-ttu-id="34e84-107">該實驗封裝了一個或多個機器學習培訓運行的配置和結果。</span><span class="sxs-lookup"><span data-stu-id="34e84-107">The experiment encapsulates the configuration and results for one or more machine learning training runs.</span></span> <span data-ttu-id="34e84-108">實驗屬於特定的工作區。</span><span class="sxs-lookup"><span data-stu-id="34e84-108">Experiments belong to a specific workspace.</span></span> <span data-ttu-id="34e84-109">首次創建實驗時，其名稱在工作區中註冊。</span><span class="sxs-lookup"><span data-stu-id="34e84-109">The first time an experiment is created, its name is registered in the workspace.</span></span> <span data-ttu-id="34e84-110">任何後續運行（如果使用相同的實驗名稱）將作為同一實驗的一部分進行記錄。</span><span class="sxs-lookup"><span data-stu-id="34e84-110">Any subsequent runs - if the same experiment name is used - are logged as part of the same experiment.</span></span> <span data-ttu-id="34e84-111">否則，將創建新實驗。</span><span class="sxs-lookup"><span data-stu-id="34e84-111">Otherwise, a new experiment is created.</span></span>

## <a name="what-is-an-azure-machine-learning-workspace"></a><span data-ttu-id="34e84-112">什麼是 Azure 機器學習工作區？</span><span class="sxs-lookup"><span data-stu-id="34e84-112">What is an Azure Machine Learning workspace?</span></span>

<span data-ttu-id="34e84-113">工作區是 Azure 機器學習資源，它為作為訓練運行的一部分創建的所有 Azure 機器學習資源和專案提供中心位置。</span><span class="sxs-lookup"><span data-stu-id="34e84-113">A workspace is an Azure Machine Learning resource that provides a central place for all Azure Machine Learning resources and artifacts created as part of training run.</span></span>

<span data-ttu-id="34e84-114">要創建 Azure 機器學習工作區，需要執行以下操作：</span><span class="sxs-lookup"><span data-stu-id="34e84-114">To create an Azure Machine Learning workspace, the following are required:</span></span>

- <span data-ttu-id="34e84-115">名稱：工作區的名稱介於 3-33 個字元之間。</span><span class="sxs-lookup"><span data-stu-id="34e84-115">Name: A name for your workspace between 3-33 characters.</span></span> <span data-ttu-id="34e84-116">名稱可能僅包含字母數位字元和連字號。</span><span class="sxs-lookup"><span data-stu-id="34e84-116">Names may only contain alphanumeric characters and hyphens.</span></span>
- <span data-ttu-id="34e84-117">區域：工作區和資源部署到的資料中心的地理位置。</span><span class="sxs-lookup"><span data-stu-id="34e84-117">Region: The geographic location of the data center where your workspace and resources are deployed to.</span></span> <span data-ttu-id="34e84-118">建議您選擇靠近您或您的客戶的位置。</span><span class="sxs-lookup"><span data-stu-id="34e84-118">It is recommended that you choose a location close to where you or your customers are.</span></span>
- <span data-ttu-id="34e84-119">資源組：包含 Azure 解決方案所有相關資源的容器。</span><span class="sxs-lookup"><span data-stu-id="34e84-119">Resource group: A container that contains all related resources for an Azure solution.</span></span>

## <a name="what-is-an-azure-machine-learning-compute"></a><span data-ttu-id="34e84-120">什麼是 Azure 機器學習計算？</span><span class="sxs-lookup"><span data-stu-id="34e84-120">What is an Azure Machine Learning compute?</span></span>

<span data-ttu-id="34e84-121">Azure 機器學習計算是一種基於雲的 Linux VM，用於培訓。</span><span class="sxs-lookup"><span data-stu-id="34e84-121">An Azure Machine Learning compute is a cloud-based Linux VM used for training.</span></span>

<span data-ttu-id="34e84-122">要創建 Azure 機器學習工作區，需要執行以下操作：</span><span class="sxs-lookup"><span data-stu-id="34e84-122">To create an Azure Machine Learning workspace, the following are required:</span></span>

- <span data-ttu-id="34e84-123">名稱：工作區的名稱介於 2-16 個字元之間。</span><span class="sxs-lookup"><span data-stu-id="34e84-123">Name: A name for your workspace between 2-16 characters.</span></span> <span data-ttu-id="34e84-124">名稱可能僅包含字母數位字元和連字號。</span><span class="sxs-lookup"><span data-stu-id="34e84-124">Names may only contain alphanumeric characters and hyphens.</span></span>
- <span data-ttu-id="34e84-125">計算大小</span><span class="sxs-lookup"><span data-stu-id="34e84-125">Compute size</span></span>

    <span data-ttu-id="34e84-126">模型產生器可以使用以下 GPU 優化的計算類型之一：</span><span class="sxs-lookup"><span data-stu-id="34e84-126">Model Builder can use one of the following GPU-optimized compute types:</span></span>

    | <span data-ttu-id="34e84-127">大小</span><span class="sxs-lookup"><span data-stu-id="34e84-127">Size</span></span> | <span data-ttu-id="34e84-128">vCPU</span><span class="sxs-lookup"><span data-stu-id="34e84-128">vCPU</span></span> | <span data-ttu-id="34e84-129">記憶體：GiB</span><span class="sxs-lookup"><span data-stu-id="34e84-129">Memory: GiB</span></span> | <span data-ttu-id="34e84-130">暫存儲存體 (SSD) GiB</span><span class="sxs-lookup"><span data-stu-id="34e84-130">Temp storage (SSD) GiB</span></span> | <span data-ttu-id="34e84-131">GPU</span><span class="sxs-lookup"><span data-stu-id="34e84-131">GPU</span></span> | <span data-ttu-id="34e84-132">GPU 記憶體：GiB</span><span class="sxs-lookup"><span data-stu-id="34e84-132">GPU memory: GiB</span></span> | <span data-ttu-id="34e84-133">最大資料磁碟</span><span class="sxs-lookup"><span data-stu-id="34e84-133">Max data disks</span></span> | <span data-ttu-id="34e84-134">最大 NIC</span><span class="sxs-lookup"><span data-stu-id="34e84-134">Max NICs</span></span> |
    |---|---|---|---|---|---|---|---|
    | <span data-ttu-id="34e84-135">Standard_NC12</span><span class="sxs-lookup"><span data-stu-id="34e84-135">Standard_NC12</span></span>   | <span data-ttu-id="34e84-136">12</span><span class="sxs-lookup"><span data-stu-id="34e84-136">12</span></span> | <span data-ttu-id="34e84-137">112</span><span class="sxs-lookup"><span data-stu-id="34e84-137">112</span></span> | <span data-ttu-id="34e84-138">680</span><span class="sxs-lookup"><span data-stu-id="34e84-138">680</span></span>  | <span data-ttu-id="34e84-139">2</span><span class="sxs-lookup"><span data-stu-id="34e84-139">2</span></span> | <span data-ttu-id="34e84-140">24</span><span class="sxs-lookup"><span data-stu-id="34e84-140">24</span></span> | <span data-ttu-id="34e84-141">48</span><span class="sxs-lookup"><span data-stu-id="34e84-141">48</span></span> | <span data-ttu-id="34e84-142">2</span><span class="sxs-lookup"><span data-stu-id="34e84-142">2</span></span> |
    | <span data-ttu-id="34e84-143">Standard_NC24</span><span class="sxs-lookup"><span data-stu-id="34e84-143">Standard_NC24</span></span>   | <span data-ttu-id="34e84-144">24</span><span class="sxs-lookup"><span data-stu-id="34e84-144">24</span></span> | <span data-ttu-id="34e84-145">224</span><span class="sxs-lookup"><span data-stu-id="34e84-145">224</span></span> | <span data-ttu-id="34e84-146">1440</span><span class="sxs-lookup"><span data-stu-id="34e84-146">1440</span></span> | <span data-ttu-id="34e84-147">4</span><span class="sxs-lookup"><span data-stu-id="34e84-147">4</span></span> | <span data-ttu-id="34e84-148">48</span><span class="sxs-lookup"><span data-stu-id="34e84-148">48</span></span> | <span data-ttu-id="34e84-149">64</span><span class="sxs-lookup"><span data-stu-id="34e84-149">64</span></span> | <span data-ttu-id="34e84-150">4</span><span class="sxs-lookup"><span data-stu-id="34e84-150">4</span></span> |

    <span data-ttu-id="34e84-151">有關 GPU 優化計算類型的更多詳細資訊，請訪問[NC 系列 Linux VM 文檔](https://docs.microsoft.com/azure/virtual-machines/nc-series?toc=/azure/virtual-machines/linux/toc.json&bc=/azure/virtual-machines/linux/breadcrumb/toc.json)。</span><span class="sxs-lookup"><span data-stu-id="34e84-151">Visit the [NC-series Linux VM documentation](https://docs.microsoft.com/azure/virtual-machines/nc-series?toc=/azure/virtual-machines/linux/toc.json&bc=/azure/virtual-machines/linux/breadcrumb/toc.json) for more details on GPU optimized compute types.</span></span>

## <a name="training"></a><span data-ttu-id="34e84-152">訓練</span><span class="sxs-lookup"><span data-stu-id="34e84-152">Training</span></span>

<span data-ttu-id="34e84-153">Azure 上的培訓僅適用于模型產生器映射分類方案。</span><span class="sxs-lookup"><span data-stu-id="34e84-153">Training on Azure is only available for the Model Builder image classification scenario.</span></span> <span data-ttu-id="34e84-154">用於訓練這些模型的演算法是基於 ResNet50 體系結構的深層神經網路。</span><span class="sxs-lookup"><span data-stu-id="34e84-154">The algorithm used to train these models is a Deep Neural Network based on the ResNet50 architecture.</span></span> <span data-ttu-id="34e84-155">培訓過程需要一些時間，時間量可能因所選計算的大小和資料量而異。</span><span class="sxs-lookup"><span data-stu-id="34e84-155">The training process takes some time and the amount of time may vary depending on the size of compute selected as well as amount of data.</span></span> <span data-ttu-id="34e84-156">第一次訓練模型時，由於必須預配資源，因此培訓時間會稍長。</span><span class="sxs-lookup"><span data-stu-id="34e84-156">The first time a model is trained, you can expect a slightly longer training time because resources have to be provisioned.</span></span> <span data-ttu-id="34e84-157">通過在 Visual Studio 中選擇"Azure 門戶中的監視器當前運行"連結，可以跟蹤運行進度。</span><span class="sxs-lookup"><span data-stu-id="34e84-157">You can track the progress of your runs by selecting the "Monitor current run in Azure portal" link in Visual Studio.</span></span>

## <a name="results"></a><span data-ttu-id="34e84-158">結果</span><span class="sxs-lookup"><span data-stu-id="34e84-158">Results</span></span>

<span data-ttu-id="34e84-159">培訓完成後，使用以下尾碼將兩個專案添加到解決方案中：</span><span class="sxs-lookup"><span data-stu-id="34e84-159">Once training is complete, two projects are added to your solution with the following suffixes:</span></span>

- <span data-ttu-id="34e84-160">*主控台應用程式*：一個 C# .NET 核心主控台應用程式，提供啟動代碼來構建預測管道並做出預測。</span><span class="sxs-lookup"><span data-stu-id="34e84-160">*ConsoleApp*: A C# .NET Core console application that provides starter code to build the prediction pipeline and make predictions.</span></span>
- <span data-ttu-id="34e84-161">*模型*： 包含定義輸入和輸出模型資料架構以及以下資產的資料模型的 C# .NET 標準應用程式：</span><span class="sxs-lookup"><span data-stu-id="34e84-161">*Model*: A C# .NET Standard application that contains the data models that define the schema of input and output model data as well as the following assets:</span></span>

  - <span data-ttu-id="34e84-162">bestModel.onnx：以開放神經網路交換 （ONNX） 格式的模型序列化版本。</span><span class="sxs-lookup"><span data-stu-id="34e84-162">bestModel.onnx: A serialized version of the model in Open Neural Network Exchange (ONNX) format.</span></span> <span data-ttu-id="34e84-163">ONNX 是 AI 模型的開源格式，支援ML.NET、PyTorch 和 TensorFlow 等框架之間的互通性。</span><span class="sxs-lookup"><span data-stu-id="34e84-163">ONNX is an open source format for AI models that supports interoperability between frameworks like ML.NET, PyTorch and TensorFlow.</span></span>
  - <span data-ttu-id="34e84-164">最佳模型Map.json：在進行預測時用於將模型輸出映射到文本類別時使用的類別清單。</span><span class="sxs-lookup"><span data-stu-id="34e84-164">bestModelMap.json: A list of categories used when making predictions to map the model output to a text category.</span></span>
  - <span data-ttu-id="34e84-165">MLModel.zip：ML.NET預測管道的序列化版本，它使用模型*bestModel.onnx*的序列化版本來使用`bestModelMap.json`該檔進行預測和映射輸出。</span><span class="sxs-lookup"><span data-stu-id="34e84-165">MLModel.zip: A serialized version of the ML.NET prediction pipeline that uses the serialized version of the model *bestModel.onnx* to make predictions and maps outputs using the `bestModelMap.json` file.</span></span>

## <a name="use-the-machine-learning-model"></a><span data-ttu-id="34e84-166">使用機器學習模型</span><span class="sxs-lookup"><span data-stu-id="34e84-166">Use the machine learning model</span></span>

<span data-ttu-id="34e84-167">模型`ModelInput`專案中`ModelOutput`的*Model*和 類分別定義模型的預期輸入和輸出的架構。</span><span class="sxs-lookup"><span data-stu-id="34e84-167">The `ModelInput` and `ModelOutput` classes in the *Model* project define the schema of the model's expected input and output respectively.</span></span>

<span data-ttu-id="34e84-168">在圖像分類方案中，`ModelInput`包含兩列：</span><span class="sxs-lookup"><span data-stu-id="34e84-168">In an image classification scenario, the `ModelInput` contains two columns:</span></span>

- <span data-ttu-id="34e84-169">`ImageSource`：圖像位置的字串路徑。</span><span class="sxs-lookup"><span data-stu-id="34e84-169">`ImageSource`: The string path of the image location.</span></span>
- <span data-ttu-id="34e84-170">`Label`：圖像所屬的實體類別。</span><span class="sxs-lookup"><span data-stu-id="34e84-170">`Label`: The actual category the image belongs to.</span></span> <span data-ttu-id="34e84-171">`Label`僅在訓練時用作輸入，在進行預測時不需要提供。</span><span class="sxs-lookup"><span data-stu-id="34e84-171">`Label` is only used as an input when training and does not need to be provided when making predictions.</span></span>

<span data-ttu-id="34e84-172">包含`ModelOutput`兩列：</span><span class="sxs-lookup"><span data-stu-id="34e84-172">The `ModelOutput` contains two columns:</span></span>

- <span data-ttu-id="34e84-173">`Prediction`：圖像的預測類別。</span><span class="sxs-lookup"><span data-stu-id="34e84-173">`Prediction`: The image's predicted category.</span></span>
- <span data-ttu-id="34e84-174">`Score`： 所有類別的概率清單（最高屬於`Prediction`）。</span><span class="sxs-lookup"><span data-stu-id="34e84-174">`Score`: The list of probabilities for all categories (the highest belongs to the `Prediction`).</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="34e84-175">疑難排解</span><span class="sxs-lookup"><span data-stu-id="34e84-175">Troubleshooting</span></span>

### <a name="cannot-create-compute"></a><span data-ttu-id="34e84-176">無法創建計算</span><span class="sxs-lookup"><span data-stu-id="34e84-176">Cannot create compute</span></span>

<span data-ttu-id="34e84-177">如果在 Azure 機器學習計算創建過程中發生錯誤，則計算資源可能仍然存在，處於錯誤狀態。</span><span class="sxs-lookup"><span data-stu-id="34e84-177">If an error occurs during Azure Machine Learning compute creation, the compute resource may still exist, in an errored state.</span></span> <span data-ttu-id="34e84-178">如果嘗試使用同名重新創建計算資源，則操作將失敗。</span><span class="sxs-lookup"><span data-stu-id="34e84-178">If you try to re-create the compute resource with the same name, the operation fails.</span></span> <span data-ttu-id="34e84-179">若要修正此錯誤，請使用以下其中一種方法：</span><span class="sxs-lookup"><span data-stu-id="34e84-179">To fix this error, either:</span></span>

- <span data-ttu-id="34e84-180">使用其他名稱創建新計算</span><span class="sxs-lookup"><span data-stu-id="34e84-180">Create the new compute with a different name</span></span>
- <span data-ttu-id="34e84-181">轉到 Azure 門戶，然後刪除原始計算資源</span><span class="sxs-lookup"><span data-stu-id="34e84-181">Go to the Azure portal, and remove the original compute resource</span></span>
