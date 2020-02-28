---
title: 模型產生器 Azure 訓練資源
description: Azure Machine Learning 的資源指南
ms.topic: reference
ms.date: 02/25/2020
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: a0a75283cdc7402c67b6bfb0799189fa34cd39a7
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "77675202"
---
# <a name="model-builder-azure-training-resources"></a><span data-ttu-id="cf563-103">模型產生器 Azure 訓練資源</span><span class="sxs-lookup"><span data-stu-id="cf563-103">Model Builder Azure Training Resources</span></span>

<span data-ttu-id="cf563-104">下列指南可協助您深入瞭解在 Azure 中使用模型產生器來定型模型所用的資源。</span><span class="sxs-lookup"><span data-stu-id="cf563-104">The following is a guide to help you learn more about resources used to train models in Azure with Model Builder.</span></span>

## <a name="what-is-an-azure-machine-learning-experiment"></a><span data-ttu-id="cf563-105">什麼是 Azure Machine Learning 實驗？</span><span class="sxs-lookup"><span data-stu-id="cf563-105">What is an Azure Machine Learning experiment?</span></span>

<span data-ttu-id="cf563-106">Azure Machine Learning 實驗是在 Azure 上執行模型產生器訓練之前必須建立的資源。</span><span class="sxs-lookup"><span data-stu-id="cf563-106">An Azure Machine Learning experiment is a resource that needs to be created before running Model Builder training on Azure.</span></span>

<span data-ttu-id="cf563-107">實驗會針對一或多個機器學習訓練執行封裝設定和結果。</span><span class="sxs-lookup"><span data-stu-id="cf563-107">The experiment encapsulates the configuration and results for one or more machine learning training runs.</span></span> <span data-ttu-id="cf563-108">實驗屬於特定的工作區。</span><span class="sxs-lookup"><span data-stu-id="cf563-108">Experiments belong to a specific workspace.</span></span> <span data-ttu-id="cf563-109">第一次建立實驗時，其名稱會在工作區中註冊。</span><span class="sxs-lookup"><span data-stu-id="cf563-109">The first time an experiment is created, its name is registered in the workspace.</span></span> <span data-ttu-id="cf563-110">任何後續的執行-如果使用相同的實驗名稱，則會記錄為相同實驗的一部分。</span><span class="sxs-lookup"><span data-stu-id="cf563-110">Any subsequent runs - if the same experiment name is used - are logged as part of the same experiment.</span></span> <span data-ttu-id="cf563-111">否則，會建立新的實驗。</span><span class="sxs-lookup"><span data-stu-id="cf563-111">Otherwise, a new experiment is created.</span></span>

## <a name="what-is-an-azure-machine-learning-workspace"></a><span data-ttu-id="cf563-112">什麼是 Azure Machine Learning 工作區？</span><span class="sxs-lookup"><span data-stu-id="cf563-112">What is an Azure Machine Learning workspace?</span></span>

<span data-ttu-id="cf563-113">工作區是一種 Azure Machine Learning 資源，可針對在定型執行過程中建立的所有 Azure Machine Learning 資源和成品提供集中位置。</span><span class="sxs-lookup"><span data-stu-id="cf563-113">A workspace is an Azure Machine Learning resource that provides a central place for all Azure Machine Learning resources and artifacts created as part of training run.</span></span>

<span data-ttu-id="cf563-114">若要建立 Azure Machine Learning 工作區，需要下列各項：</span><span class="sxs-lookup"><span data-stu-id="cf563-114">To create an Azure Machine Learning workspace, the following are required:</span></span>

- <span data-ttu-id="cf563-115">名稱：您的工作區名稱，介於3-33 個字元之間。</span><span class="sxs-lookup"><span data-stu-id="cf563-115">Name: A name for your workspace between 3-33 characters.</span></span> <span data-ttu-id="cf563-116">名稱只可包含英數位元和連字號。</span><span class="sxs-lookup"><span data-stu-id="cf563-116">Names may only contain alphanumeric characters and hyphens.</span></span> 
- <span data-ttu-id="cf563-117">區域：您的工作區和資源部署所在之資料中心的地理位置。</span><span class="sxs-lookup"><span data-stu-id="cf563-117">Region: The geographic location of the data center where your workspace and resources are deployed to.</span></span> <span data-ttu-id="cf563-118">建議您選擇靠近您或客戶的位置。</span><span class="sxs-lookup"><span data-stu-id="cf563-118">It is recommended that you choose a location close to where you or your customers are.</span></span>
- <span data-ttu-id="cf563-119">資源群組：容器，其中包含 Azure 解決方案的所有相關資源。</span><span class="sxs-lookup"><span data-stu-id="cf563-119">Resource group: A container that contains all related resources for an Azure solution.</span></span>

## <a name="what-is-an-azure-machine-learning-compute"></a><span data-ttu-id="cf563-120">什麼是 Azure Machine Learning 計算？</span><span class="sxs-lookup"><span data-stu-id="cf563-120">What is an Azure Machine Learning compute?</span></span>

<span data-ttu-id="cf563-121">Azure Machine Learning 計算是用於定型的雲端式 Linux VM。</span><span class="sxs-lookup"><span data-stu-id="cf563-121">An Azure Machine Learning compute is a cloud-based Linux VM used for training.</span></span>

<span data-ttu-id="cf563-122">若要建立 Azure Machine Learning 工作區，需要下列各項：</span><span class="sxs-lookup"><span data-stu-id="cf563-122">To create an Azure Machine Learning workspace, the following are required:</span></span>

- <span data-ttu-id="cf563-123">名稱：您的工作區名稱，介於2-16 個字元之間。</span><span class="sxs-lookup"><span data-stu-id="cf563-123">Name: A name for your workspace between 2-16 characters.</span></span> <span data-ttu-id="cf563-124">名稱只可包含英數位元和連字號。</span><span class="sxs-lookup"><span data-stu-id="cf563-124">Names may only contain alphanumeric characters and hyphens.</span></span>
- <span data-ttu-id="cf563-125">計算大小</span><span class="sxs-lookup"><span data-stu-id="cf563-125">Compute size</span></span>

    <span data-ttu-id="cf563-126">模型產生器可以使用下列其中一種 GPU 優化計算類型：</span><span class="sxs-lookup"><span data-stu-id="cf563-126">Model Builder can use one of the following GPU-optimized compute types:</span></span>

    | <span data-ttu-id="cf563-127">大小</span><span class="sxs-lookup"><span data-stu-id="cf563-127">Size</span></span> | <span data-ttu-id="cf563-128">vCPU</span><span class="sxs-lookup"><span data-stu-id="cf563-128">vCPU</span></span> | <span data-ttu-id="cf563-129">記憶體：GiB</span><span class="sxs-lookup"><span data-stu-id="cf563-129">Memory: GiB</span></span> | <span data-ttu-id="cf563-130">暫存儲存體 (SSD) GiB</span><span class="sxs-lookup"><span data-stu-id="cf563-130">Temp storage (SSD) GiB</span></span> | <span data-ttu-id="cf563-131">GPU</span><span class="sxs-lookup"><span data-stu-id="cf563-131">GPU</span></span> | <span data-ttu-id="cf563-132">GPU 記憶體：GiB</span><span class="sxs-lookup"><span data-stu-id="cf563-132">GPU memory: GiB</span></span> | <span data-ttu-id="cf563-133">最大資料磁碟</span><span class="sxs-lookup"><span data-stu-id="cf563-133">Max data disks</span></span> | <span data-ttu-id="cf563-134">最大 NIC</span><span class="sxs-lookup"><span data-stu-id="cf563-134">Max NICs</span></span> |
    |---|---|---|---|---|---|---|---|
    | <span data-ttu-id="cf563-135">Standard_NC12</span><span class="sxs-lookup"><span data-stu-id="cf563-135">Standard_NC12</span></span>   | <span data-ttu-id="cf563-136">12</span><span class="sxs-lookup"><span data-stu-id="cf563-136">12</span></span> | <span data-ttu-id="cf563-137">112</span><span class="sxs-lookup"><span data-stu-id="cf563-137">112</span></span> | <span data-ttu-id="cf563-138">680</span><span class="sxs-lookup"><span data-stu-id="cf563-138">680</span></span>  | <span data-ttu-id="cf563-139">2</span><span class="sxs-lookup"><span data-stu-id="cf563-139">2</span></span> | <span data-ttu-id="cf563-140">24</span><span class="sxs-lookup"><span data-stu-id="cf563-140">24</span></span> | <span data-ttu-id="cf563-141">48</span><span class="sxs-lookup"><span data-stu-id="cf563-141">48</span></span> | <span data-ttu-id="cf563-142">2</span><span class="sxs-lookup"><span data-stu-id="cf563-142">2</span></span> |
    | <span data-ttu-id="cf563-143">Standard_NC24</span><span class="sxs-lookup"><span data-stu-id="cf563-143">Standard_NC24</span></span>   | <span data-ttu-id="cf563-144">24</span><span class="sxs-lookup"><span data-stu-id="cf563-144">24</span></span> | <span data-ttu-id="cf563-145">224</span><span class="sxs-lookup"><span data-stu-id="cf563-145">224</span></span> | <span data-ttu-id="cf563-146">1440</span><span class="sxs-lookup"><span data-stu-id="cf563-146">1440</span></span> | <span data-ttu-id="cf563-147">4</span><span class="sxs-lookup"><span data-stu-id="cf563-147">4</span></span> | <span data-ttu-id="cf563-148">48</span><span class="sxs-lookup"><span data-stu-id="cf563-148">48</span></span> | <span data-ttu-id="cf563-149">64</span><span class="sxs-lookup"><span data-stu-id="cf563-149">64</span></span> | <span data-ttu-id="cf563-150">4</span><span class="sxs-lookup"><span data-stu-id="cf563-150">4</span></span> |

    <span data-ttu-id="cf563-151">如需 GPU 優化計算類型的詳細資訊，請流覽[NC 系列 LINUX VM 檔](https://docs.microsoft.com/azure/virtual-machines/nc-series?toc=/azure/virtual-machines/linux/toc.json&bc=/azure/virtual-machines/linux/breadcrumb/toc.json)。</span><span class="sxs-lookup"><span data-stu-id="cf563-151">Visit the [NC-series Linux VM documentation](https://docs.microsoft.com/azure/virtual-machines/nc-series?toc=/azure/virtual-machines/linux/toc.json&bc=/azure/virtual-machines/linux/breadcrumb/toc.json) for more details on GPU optimized compute types.</span></span>

## <a name="training"></a><span data-ttu-id="cf563-152">訓練</span><span class="sxs-lookup"><span data-stu-id="cf563-152">Training</span></span>

<span data-ttu-id="cf563-153">Azure 上的訓練僅適用于模型產生器影像分類案例。</span><span class="sxs-lookup"><span data-stu-id="cf563-153">Training on Azure is only available for the Model Builder image classification scenario.</span></span> <span data-ttu-id="cf563-154">用來定型這些模型的演算法是以 ResNet50 架構為基礎的深度類神經網路。</span><span class="sxs-lookup"><span data-stu-id="cf563-154">The algorithm used to train these models is a Deep Neural Network based on the ResNet50 architecture.</span></span> <span data-ttu-id="cf563-155">定型期間，會布建定型模型所需的資源，並定型模型。</span><span class="sxs-lookup"><span data-stu-id="cf563-155">During training, the resources required to train the model are provisioned and the model is trained.</span></span> <span data-ttu-id="cf563-156">此程式需要幾分鐘的時間，而且可能會根據所選取的計算大小和資料量而有所不同。</span><span class="sxs-lookup"><span data-stu-id="cf563-156">This process takes several minutes and the amount of time may vary depending on the size of compute selected as well as amount of data.</span></span> <span data-ttu-id="cf563-157">您可以藉由選取 Visual Studio 中的 [在 Azure 入口網站中監視目前的執行] 連結來追蹤執行進度。</span><span class="sxs-lookup"><span data-stu-id="cf563-157">You can track the progress of your runs by selecting the "Monitor current run in Azure portal" link in Visual Studio.</span></span>

## <a name="results"></a><span data-ttu-id="cf563-158">結果</span><span class="sxs-lookup"><span data-stu-id="cf563-158">Results</span></span>

<span data-ttu-id="cf563-159">定型完成後，會將兩個專案新增至您的方案，並具有下列尾碼：</span><span class="sxs-lookup"><span data-stu-id="cf563-159">Once training is complete, two projects are added to your solution with the following suffixes:</span></span>

- <span data-ttu-id="cf563-160">*Consoleapp.exe*： C# .net Core 主控台應用程式，可提供起始程式碼來建立預測管線並進行預測。</span><span class="sxs-lookup"><span data-stu-id="cf563-160">*ConsoleApp*: A C# .NET Core console application that provides starter code to build the prediction pipeline and make predictions.</span></span>
- <span data-ttu-id="cf563-161">*Model*： C# .NET Standard 應用程式，其中包含定義輸入和輸出模型資料之架構的資料模型，以及下列資產：</span><span class="sxs-lookup"><span data-stu-id="cf563-161">*Model*: A C# .NET Standard application that contains the data models that define the schema of input and output model data as well as the following assets:</span></span>

  - <span data-ttu-id="cf563-162">bestModel. onnx：以 Open Neural Network Exchange （ONNX）格式的模型序列化版本。</span><span class="sxs-lookup"><span data-stu-id="cf563-162">bestModel.onnx: A serialized version of the model in Open Neural Network Exchange (ONNX) format.</span></span> <span data-ttu-id="cf563-163">ONNX 是 AI 模型的開放原始碼格式，可支援 ML.NET、PyTorch 和 TensorFlow 等架構之間的互通性。</span><span class="sxs-lookup"><span data-stu-id="cf563-163">ONNX is an open source format for AI models that supports interoperability between frameworks like ML.NET, PyTorch and TensorFlow.</span></span>
  - <span data-ttu-id="cf563-164">bestModelMap：進行預測以將模型輸出對應至文字類別目錄時，所使用的類別目錄清單。</span><span class="sxs-lookup"><span data-stu-id="cf563-164">bestModelMap.json: A list of categories used when making predictions to map the model output to a text category.</span></span>
  - <span data-ttu-id="cf563-165">MLModel .zip： ML.NET 預測管線的序列化版本，它會使用模型*bestModel*的序列化版本來進行預測，並使用 `bestModelMap.json` 檔案來對應輸出。</span><span class="sxs-lookup"><span data-stu-id="cf563-165">MLModel.zip: A serialized version of the ML.NET prediction pipeline that uses the serialized version of the model *bestModel.onnx* to make predictions and maps outputs using the `bestModelMap.json` file.</span></span>
  
## <a name="troubleshooting"></a><span data-ttu-id="cf563-166">疑難排解</span><span class="sxs-lookup"><span data-stu-id="cf563-166">Troubleshooting</span></span>

### <a name="cannot-create-compute"></a><span data-ttu-id="cf563-167">無法建立計算</span><span class="sxs-lookup"><span data-stu-id="cf563-167">Cannot create compute</span></span>

<span data-ttu-id="cf563-168">如果在建立 Azure Machine Learning 計算期間發生錯誤，計算資源可能仍存在，錯誤狀態。</span><span class="sxs-lookup"><span data-stu-id="cf563-168">If an error occurs during Azure Machine Learning compute creation, the compute resource may still exist, in an errored state.</span></span> <span data-ttu-id="cf563-169">如果您嘗試以相同的名稱重新建立計算資源，作業會失敗。</span><span class="sxs-lookup"><span data-stu-id="cf563-169">If you try to re-create the compute resource with the same name, the operation fails.</span></span> <span data-ttu-id="cf563-170">若要修正此錯誤，請使用以下其中一種方法：</span><span class="sxs-lookup"><span data-stu-id="cf563-170">To fix this error, either:</span></span>

* <span data-ttu-id="cf563-171">以不同的名稱建立新的計算</span><span class="sxs-lookup"><span data-stu-id="cf563-171">Create the new compute with a different name</span></span>
* <span data-ttu-id="cf563-172">移至 Azure 入口網站，並移除原始的計算資源</span><span class="sxs-lookup"><span data-stu-id="cf563-172">Go to the Azure portal, and remove the original compute resource</span></span>
