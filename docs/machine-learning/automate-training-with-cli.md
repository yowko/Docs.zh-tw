---
title: 使用 ML.NET CLI 自動化模型定型
description: 探索如何使用 ML.NET CLI 工具，從命令列自動定型最佳模型。
ms.date: 06/03/2020
ms.custom: how-to, mlnet-tooling
ms.openlocfilehash: d7c6102c2257be1daa613fde0edabce83d04b414
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589654"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a><span data-ttu-id="0154b-103">使用 ML.NET CLI 自動化模型定型</span><span class="sxs-lookup"><span data-stu-id="0154b-103">Automate model training with the ML.NET CLI</span></span>

<span data-ttu-id="0154b-104">ML.NET CLI 會自動產生適用于 .NET 開發人員的模型。</span><span class="sxs-lookup"><span data-stu-id="0154b-104">The ML.NET CLI automates model generation for .NET developers.</span></span>

<span data-ttu-id="0154b-105">若要使用 ML.NET API 本身 (不利用 ML.NET AutoML CLI)，您需要選擇定型器 (實作特定工作的機器學習演算法) 以及要套用至資料的一組資料轉換 (特徵工程)。</span><span class="sxs-lookup"><span data-stu-id="0154b-105">To use the ML.NET API by itself, (without the ML.NET AutoML CLI) you need to choose a trainer (implementation of a machine learning algorithm for a particular task), and the set of data transformations (feature engineering) to apply to your data.</span></span> <span data-ttu-id="0154b-106">每個資料集的最佳管道各有不同，而從所有的選項中選取最佳演算法會增加複雜性。</span><span class="sxs-lookup"><span data-stu-id="0154b-106">The optimal pipeline will vary for each dataset and selecting the optimal algorithm from all the choices adds to the complexity.</span></span> <span data-ttu-id="0154b-107">更進一步，每個演算法都有一組要微調的超參數。</span><span class="sxs-lookup"><span data-stu-id="0154b-107">Even further, each algorithm has a set of hyperparameters to be tuned.</span></span> <span data-ttu-id="0154b-108">因此，您可以花費數週或數月來最佳化機器學習模型，嘗試尋找特徵工程、學習演算法和超參數的最佳組合。</span><span class="sxs-lookup"><span data-stu-id="0154b-108">Hence, you can spend weeks and sometimes months on machine learning model optimization trying to find the best combinations of feature engineering, learning algorithms, and hyperparameters.</span></span>

<span data-ttu-id="0154b-109">ML.NET CLI 會使用自動化機器學習（AutoML）來簡化此程式。</span><span class="sxs-lookup"><span data-stu-id="0154b-109">The ML.NET CLI simplifies this process using automated machine learning (AutoML).</span></span>

> [!NOTE]
> <span data-ttu-id="0154b-110">本主題是指 ML.NET **CLI**和 ML.NET **AutoML**（目前為預覽狀態），而材質可能會有所變更。</span><span class="sxs-lookup"><span data-stu-id="0154b-110">This topic refers to ML.NET **CLI** and ML.NET **AutoML**, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="what-is-the-mlnet-command-line-interface-cli"></a><span data-ttu-id="0154b-111">什麼是 ML.NET 命令列介面（CLI）？</span><span class="sxs-lookup"><span data-stu-id="0154b-111">What is the ML.NET command-line interface (CLI)?</span></span>

<span data-ttu-id="0154b-112">ML.NET CLI 是一種[.Net Core 工具](../core/tools/global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="0154b-112">The ML.NET CLI is a [.NET Core tool](../core/tools/global-tools.md).</span></span> <span data-ttu-id="0154b-113">安裝之後，您會提供機器學習工作和訓練資料集，並產生 ML.NET 模型，以及要在應用程式中執行以使用模型的 c # 程式碼。</span><span class="sxs-lookup"><span data-stu-id="0154b-113">Once installed, you give it a machine learning task and a training dataset, and it generates an ML.NET model, as well as the C# code to run to use the model in your application.</span></span>

<span data-ttu-id="0154b-114">如下圖所示，您可以輕鬆地產生高品質的 ML.NET 模型（序列化模型 .zip 檔案），再加上用來執行/評分該模型的範例 c # 程式碼。</span><span class="sxs-lookup"><span data-stu-id="0154b-114">As shown in the following figure, it is simple to generate a high quality ML.NET model (serialized model .zip file) plus the sample C# code to run/score that model.</span></span> <span data-ttu-id="0154b-115">此外，也產生建立/定型模型的 C# 程式碼，以便您可以研究並重覆所產生「最佳模型」使用的演算法和設定。</span><span class="sxs-lookup"><span data-stu-id="0154b-115">In addition, the C# code to create/train that model is also generated, so that you can research and iterate on the algorithm and settings used for that generated "best model".</span></span>

<span data-ttu-id="0154b-116">![image](media/automate-training-with-cli/cli-high-level-process.png "在 ML.NET CLI 內運作的 AutoML 引擎")</span><span class="sxs-lookup"><span data-stu-id="0154b-116">![image](media/automate-training-with-cli/cli-high-level-process.png "AutoML engine working inside the ML.NET CLI")</span></span>

<span data-ttu-id="0154b-117">您可以從自己的資料集產生這些資產，不用自行撰寫程式碼，因此即使您已熟悉 ML.NET，也能提升生產力。</span><span class="sxs-lookup"><span data-stu-id="0154b-117">You can generate those assets from your own datasets without coding by yourself, so it also improves your productivity even if you already know ML.NET.</span></span>

<span data-ttu-id="0154b-118">ML.NET CLI 目前支援的 ML 工作如下：</span><span class="sxs-lookup"><span data-stu-id="0154b-118">Currently, the ML Tasks supported by the ML.NET CLI are:</span></span>

- <span data-ttu-id="0154b-119">分類（二進位和多類別）</span><span class="sxs-lookup"><span data-stu-id="0154b-119">classification (binary and multi-class)</span></span>
- <span data-ttu-id="0154b-120">迴歸</span><span class="sxs-lookup"><span data-stu-id="0154b-120">regression</span></span>
- <span data-ttu-id="0154b-121">建議</span><span class="sxs-lookup"><span data-stu-id="0154b-121">recommendation</span></span>
- <span data-ttu-id="0154b-122">未來：其他機器學習工作，例如影像分類、排名、異常偵測、叢集</span><span class="sxs-lookup"><span data-stu-id="0154b-122">Future: other machine learning tasks such as image-classification, ranking, anomaly-detection, clustering</span></span>

<span data-ttu-id="0154b-123">使用方式範例（分類案例）：</span><span class="sxs-lookup"><span data-stu-id="0154b-123">Example of usage (classification scenario):</span></span>

```console
mlnet classification --dataset "yelp_labelled.txt" --label-col 1 --has-header false --train-time 10
```

![image](media/automate-training-with-cli/mlnet-classification-powershell.gif)

<span data-ttu-id="0154b-125">您可以在*Windows PowerShell*、 *macOS/Linux BASH*或*windows CMD*上以相同的方式執行它。</span><span class="sxs-lookup"><span data-stu-id="0154b-125">You can run it the same way on *Windows PowerShell*, *macOS/Linux bash*, or *Windows CMD*.</span></span> <span data-ttu-id="0154b-126">不過，表格式自動完成 (參數建議) 不適用於 *Windows CMD*。</span><span class="sxs-lookup"><span data-stu-id="0154b-126">However, tabular auto-completion (parameter suggestions) won't work on *Windows CMD*.</span></span>

## <a name="output-assets-generated"></a><span data-ttu-id="0154b-127">產生的輸出資產</span><span class="sxs-lookup"><span data-stu-id="0154b-127">Output assets generated</span></span>

<span data-ttu-id="0154b-128">CLI 中的 ML 工作命令會在輸出檔案夾中產生下列資產：</span><span class="sxs-lookup"><span data-stu-id="0154b-128">The ML task commands in the CLI generate the following assets in the output folder:</span></span>

- <span data-ttu-id="0154b-129">序列化模型 .zip (「最佳模型」) 準備好用於執行預測。</span><span class="sxs-lookup"><span data-stu-id="0154b-129">A serialized model .zip ("best model") ready to use for running predictions.</span></span>
- <span data-ttu-id="0154b-130">C# 解決方案具有：</span><span class="sxs-lookup"><span data-stu-id="0154b-130">C# solution with:</span></span>
  - <span data-ttu-id="0154b-131">C# 程式碼，執行/評分產生的模型 (使用該模型以您的終端使用者應用程式建立預測)。</span><span class="sxs-lookup"><span data-stu-id="0154b-131">C# code to run/score that generated model (to make predictions in your end-user apps with that model).</span></span>
  - <span data-ttu-id="0154b-132">C# 程式碼和定型程式碼，用來產生該模型 (適用於學習目的或重新定型模型)。</span><span class="sxs-lookup"><span data-stu-id="0154b-132">C# code with the training code used to generate that model (for learning purposes or model retraining).</span></span>
- <span data-ttu-id="0154b-133">記錄檔，具有多個已評估之演算法所有反覆項目/清除的資訊，包括其詳細的組態/管線。</span><span class="sxs-lookup"><span data-stu-id="0154b-133">Log file with information of all iterations/sweeps across the multiple algorithms evaluated, including their detailed configuration/pipeline.</span></span>

<span data-ttu-id="0154b-134">前兩項資產可以直接用於終端使用者應用程式 (ASP.NET Core Web 應用程式、服務、桌面應用程式等)，使用已產生的 ML 模型建立預測。</span><span class="sxs-lookup"><span data-stu-id="0154b-134">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

<span data-ttu-id="0154b-135">第三項資產，即定型程式碼，會向您顯示 CLI 已使用哪些 ML.NET API 程式碼來定型產生的模型，讓您可以重新定型模型，以及調查和逐一查看 CLI 和 AutoML 在幕後選取了哪些特定的定型器/演算法和超參數。</span><span class="sxs-lookup"><span data-stu-id="0154b-135">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can retrain your model and investigate and iterate on which specific trainer/algorithm and hyperparameters were selected by the CLI and AutoML under the covers.</span></span>

## <a name="understanding-the-quality-of-the-model"></a><span data-ttu-id="0154b-136">了解模型的品質</span><span class="sxs-lookup"><span data-stu-id="0154b-136">Understanding the quality of the model</span></span>

<span data-ttu-id="0154b-137">當您使用 CLI 工具產生「最佳模型」時，您會看到適用于您的目標 ML 工作的品質度量（例如精確度和右平方）。</span><span class="sxs-lookup"><span data-stu-id="0154b-137">When you generate a 'best model' with the CLI tool, you see quality metrics (such as accuracy and R-Squared) as appropriate for the ML task you're targeting.</span></span>

<span data-ttu-id="0154b-138">這裡的計量是依 ML 工作分組，因此您可以瞭解自動產生的「最佳模型」的品質。</span><span class="sxs-lookup"><span data-stu-id="0154b-138">Here those metrics are summarized grouped by ML task so you can understand the quality of your auto-generated 'best model'.</span></span>

### <a name="metrics-for-classification-models"></a><span data-ttu-id="0154b-139">分類模型的計量</span><span class="sxs-lookup"><span data-stu-id="0154b-139">Metrics for Classification models</span></span>

<span data-ttu-id="0154b-140">以下顯示 CLI 找到的前五個模型的分類計量清單：</span><span class="sxs-lookup"><span data-stu-id="0154b-140">The following displays the classification metrics list for the top five models found by the CLI:</span></span>

![image](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

 <span data-ttu-id="0154b-142">精確度是分類問題的熱門計量，不過，精確度不一定是最佳的計量，可以從中選取最佳的模型，如下列參考中所述。</span><span class="sxs-lookup"><span data-stu-id="0154b-142">Accuracy is a popular metric for classification problems, however accuracy isn't always the best metric to select the best model from as explained in the following references.</span></span> <span data-ttu-id="0154b-143">在某些情況下，您需要評估模型品質和其他計量。</span><span class="sxs-lookup"><span data-stu-id="0154b-143">There are cases where you need to evaluate the quality of your model with additional metrics.</span></span>

<span data-ttu-id="0154b-144">若要探索及瞭解 CLI 所輸出的計量，請參閱[分類的評估度量](resources/metrics.md#evaluation-metrics-for-multi-class-classification)。</span><span class="sxs-lookup"><span data-stu-id="0154b-144">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for classification](resources/metrics.md#evaluation-metrics-for-multi-class-classification).</span></span>

### <a name="metrics-for-regression-and-recommendation-models"></a><span data-ttu-id="0154b-145">回歸和建議模型的計量</span><span class="sxs-lookup"><span data-stu-id="0154b-145">Metrics for Regression and Recommendation models</span></span>

<span data-ttu-id="0154b-146">如果觀察到的值和模型預測值之間差異很小且非偏誤，則迴歸模型非常適合這種資料。</span><span class="sxs-lookup"><span data-stu-id="0154b-146">A regression model fits the data well if the differences between the observed values and the model's predicted values are small and unbiased.</span></span> <span data-ttu-id="0154b-147">可以使用特定計量評估迴歸。</span><span class="sxs-lookup"><span data-stu-id="0154b-147">Regression can be evaluated with certain metrics.</span></span>

<span data-ttu-id="0154b-148">您會看到一份類似的計量清單，適用于 CLI 找到的最佳前五個品質模型。</span><span class="sxs-lookup"><span data-stu-id="0154b-148">You'll see a similar list of metrics for the best top five quality models found by the CLI.</span></span> <span data-ttu-id="0154b-149">在這個特例中與迴歸 ML 工作相關：</span><span class="sxs-lookup"><span data-stu-id="0154b-149">In this particular case related to a regression ML task:</span></span>

![image](media/automate-training-with-cli/cli-regression-metrics.png)

<span data-ttu-id="0154b-151">若要探索及瞭解 CLI 所輸出的計量，請參閱[回歸的評估計量](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation)。</span><span class="sxs-lookup"><span data-stu-id="0154b-151">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for regression](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation).</span></span>

## <a name="see-also"></a><span data-ttu-id="0154b-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0154b-152">See also</span></span>

- [<span data-ttu-id="0154b-153">如何安裝 ML.NET CLI 工具</span><span class="sxs-lookup"><span data-stu-id="0154b-153">How to install the ML.NET CLI tool</span></span>](how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="0154b-154">教學課程：使用 ML.NET CLI 來分析情感</span><span class="sxs-lookup"><span data-stu-id="0154b-154">Tutorial: Analyze sentiment using the ML.NET CLI</span></span>](tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="0154b-155">ML.NET CLI 命令參考</span><span class="sxs-lookup"><span data-stu-id="0154b-155">ML.NET CLI command reference</span></span>](reference/ml-net-cli-reference.md)
- [<span data-ttu-id="0154b-156">ML.NET CLI 中的遙測</span><span class="sxs-lookup"><span data-stu-id="0154b-156">Telemetry in ML.NET CLI</span></span>](resources/ml-net-cli-telemetry.md)
