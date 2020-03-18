---
title: 使用 ML.NET CLI 自動化模型定型
description: 探索如何使用 ML.NET CLI 工具，從命令列自動定型最佳模型。
ms.date: 12/17/2019
ms.custom: how-to, mlnet-tooling
ms.openlocfilehash: 3344ed15266503d4d5c7cd9db0a0596f58a904fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185888"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a><span data-ttu-id="d7f5c-103">使用 ML.NET CLI 自動化模型定型</span><span class="sxs-lookup"><span data-stu-id="d7f5c-103">Automate model training with the ML.NET CLI</span></span>

<span data-ttu-id="d7f5c-104">ML.NET CLI 可自動為 .NET 開發人員生成模型。</span><span class="sxs-lookup"><span data-stu-id="d7f5c-104">The ML.NET CLI automates model generation for .NET developers.</span></span>

<span data-ttu-id="d7f5c-105">若要使用 ML.NET API 本身 (不利用 ML.NET AutoML CLI)，您需要選擇定型器 (實作特定工作的機器學習演算法) 以及要套用至資料的一組資料轉換 (特徵工程)。</span><span class="sxs-lookup"><span data-stu-id="d7f5c-105">To use the ML.NET API by itself, (without the ML.NET AutoML CLI) you need to choose a trainer (implementation of a machine learning algorithm for a particular task), and the set of data transformations (feature engineering) to apply to your data.</span></span> <span data-ttu-id="d7f5c-106">每個資料集的最佳管道各有不同，而從所有的選項中選取最佳演算法會增加複雜性。</span><span class="sxs-lookup"><span data-stu-id="d7f5c-106">The optimal pipeline will vary for each dataset and selecting the optimal algorithm from all the choices adds to the complexity.</span></span> <span data-ttu-id="d7f5c-107">更進一步，每個演算法都有一組要微調的超參數。</span><span class="sxs-lookup"><span data-stu-id="d7f5c-107">Even further, each algorithm has a set of hyperparameters to be tuned.</span></span> <span data-ttu-id="d7f5c-108">因此，您可以花費數週或數月來最佳化機器學習模型，嘗試尋找特徵工程、學習演算法和超參數的最佳組合。</span><span class="sxs-lookup"><span data-stu-id="d7f5c-108">Hence, you can spend weeks and sometimes months on machine learning model optimization trying to find the best combinations of feature engineering, learning algorithms, and hyperparameters.</span></span>

<span data-ttu-id="d7f5c-109">ML.NET CLI 使用自動機器學習 （AutoML） 簡化了此過程。</span><span class="sxs-lookup"><span data-stu-id="d7f5c-109">The ML.NET CLI simplifies this process using automated machine learning (AutoML).</span></span>

> [!NOTE]
> <span data-ttu-id="d7f5c-110">本主題是指當前處於預覽版中的ML.NET **CLI**和 ML.NET **AutoML，** 材料可能會有所更改。</span><span class="sxs-lookup"><span data-stu-id="d7f5c-110">This topic refers to ML.NET **CLI** and ML.NET **AutoML**, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="what-is-the-mlnet-command-line-interface-cli"></a><span data-ttu-id="d7f5c-111">什麼是ML.NET命令列介面 （CLI）？</span><span class="sxs-lookup"><span data-stu-id="d7f5c-111">What is the ML.NET command-line interface (CLI)?</span></span>

<span data-ttu-id="d7f5c-112">cLIML.NET是[.NET 核心工具](../core/tools/global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="d7f5c-112">The ML.NET CLI is a [.NET Core tool](../core/tools/global-tools.md).</span></span> <span data-ttu-id="d7f5c-113">安裝後，您將給它一個機器學習任務和培訓資料集，並生成一個ML.NET模型，以及運行以在應用程式中使用模型的 C# 代碼。</span><span class="sxs-lookup"><span data-stu-id="d7f5c-113">Once installed, you give it a machine learning task and a training dataset, and it generates an ML.NET model, as well as the C# code to run to use the model in your application.</span></span>

<span data-ttu-id="d7f5c-114">如下圖所示，生成高品質ML.NET模型（序列化模型 .ZIP 檔案）加上示例 C# 代碼以運行/評分該模型非常簡單。</span><span class="sxs-lookup"><span data-stu-id="d7f5c-114">As shown in the following figure, it is simple to generate a high quality ML.NET model (serialized model .zip file) plus the sample C# code to run/score that model.</span></span> <span data-ttu-id="d7f5c-115">此外，也產生建立/定型模型的 C# 程式碼，以便您可以研究並重覆所產生「最佳模型」使用的演算法和設定。</span><span class="sxs-lookup"><span data-stu-id="d7f5c-115">In addition, the C# code to create/train that model is also generated, so that you can research and iterate on the algorithm and settings used for that generated "best model".</span></span>

<span data-ttu-id="d7f5c-116">![圖像](media/automate-training-with-cli/cli-high-level-process.png "自動ML發動機在ML.NET CLI 內工作")</span><span class="sxs-lookup"><span data-stu-id="d7f5c-116">![image](media/automate-training-with-cli/cli-high-level-process.png "AutoML engine working inside the ML.NET CLI")</span></span>

<span data-ttu-id="d7f5c-117">您可以從自己的資料集產生這些資產，不用自行撰寫程式碼，因此即使您已熟悉 ML.NET，也能提升生產力。</span><span class="sxs-lookup"><span data-stu-id="d7f5c-117">You can generate those assets from your own datasets without coding by yourself, so it also improves your productivity even if you already know ML.NET.</span></span>

<span data-ttu-id="d7f5c-118">ML.NET CLI 目前支援的 ML 工作如下：</span><span class="sxs-lookup"><span data-stu-id="d7f5c-118">Currently, the ML Tasks supported by the ML.NET CLI are:</span></span>

- `binary-classification`
- `multiclass-classification`
- `regression`
- <span data-ttu-id="d7f5c-119">未來：其他機器學習工作，例如 `recommendation`、`ranking`、`anomaly-detection`、`clustering`</span><span class="sxs-lookup"><span data-stu-id="d7f5c-119">Future: other machine learning tasks such as `recommendation`, `ranking`, `anomaly-detection`, `clustering`</span></span>

<span data-ttu-id="d7f5c-120">使用範例：</span><span class="sxs-lookup"><span data-stu-id="d7f5c-120">Example of usage:</span></span>

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

![image](media/automate-training-with-cli/cli-model-generation.gif)

<span data-ttu-id="d7f5c-122">您可以用在 *Windows PowerShell*、\*macOS/Linux bash 或 *Windows CMD* 執行的方式執行它。</span><span class="sxs-lookup"><span data-stu-id="d7f5c-122">You can run it the same way on *Windows PowerShell*, \*macOS/Linux bash, or *Windows CMD*.</span></span> <span data-ttu-id="d7f5c-123">不過，表格式自動完成 (參數建議) 不適用於 *Windows CMD*。</span><span class="sxs-lookup"><span data-stu-id="d7f5c-123">However, tabular auto-completion (parameter suggestions) won't work on *Windows CMD*.</span></span>

## <a name="output-assets-generated"></a><span data-ttu-id="d7f5c-124">產生的輸出資產</span><span class="sxs-lookup"><span data-stu-id="d7f5c-124">Output assets generated</span></span>

<span data-ttu-id="d7f5c-125">CLI `auto-train` 命令會在輸出資料夾中產生下列資產：</span><span class="sxs-lookup"><span data-stu-id="d7f5c-125">The CLI `auto-train` command generates the following assets in the output folder:</span></span>

- <span data-ttu-id="d7f5c-126">序列化模型 .zip (「最佳模型」) 準備好用於執行預測。</span><span class="sxs-lookup"><span data-stu-id="d7f5c-126">A serialized model .zip ("best model") ready to use for running predictions.</span></span>
- <span data-ttu-id="d7f5c-127">C# 解決方案具有：</span><span class="sxs-lookup"><span data-stu-id="d7f5c-127">C# solution with:</span></span>
  - <span data-ttu-id="d7f5c-128">C# 程式碼，執行/評分產生的模型 (使用該模型以您的終端使用者應用程式建立預測)。</span><span class="sxs-lookup"><span data-stu-id="d7f5c-128">C# code to run/score that generated model (to make predictions in your end-user apps with that model).</span></span>
  - <span data-ttu-id="d7f5c-129">C# 程式碼和定型程式碼，用來產生該模型 (適用於學習目的或重新定型模型)。</span><span class="sxs-lookup"><span data-stu-id="d7f5c-129">C# code with the training code used to generate that model (for learning purposes or model retraining).</span></span>
- <span data-ttu-id="d7f5c-130">記錄檔，具有多個已評估之演算法所有反覆項目/清除的資訊，包括其詳細的組態/管線。</span><span class="sxs-lookup"><span data-stu-id="d7f5c-130">Log file with information of all iterations/sweeps across the multiple algorithms evaluated, including their detailed configuration/pipeline.</span></span>

<span data-ttu-id="d7f5c-131">前兩項資產可以直接用於終端使用者應用程式 (ASP.NET Core Web 應用程式、服務、桌面應用程式等)，使用已產生的 ML 模型建立預測。</span><span class="sxs-lookup"><span data-stu-id="d7f5c-131">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

<span data-ttu-id="d7f5c-132">第三項資產，即定型程式碼，會向您顯示 CLI 已使用哪些 ML.NET API 程式碼來定型產生的模型，讓您可以重新定型模型，以及調查和逐一查看 CLI 和 AutoML 在幕後選取了哪些特定的定型器/演算法和超參數。</span><span class="sxs-lookup"><span data-stu-id="d7f5c-132">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can retrain your model and investigate and iterate on which specific trainer/algorithm and hyperparameters were selected by the CLI and AutoML under the covers.</span></span>

## <a name="understanding-the-quality-of-the-model"></a><span data-ttu-id="d7f5c-133">了解模型的品質</span><span class="sxs-lookup"><span data-stu-id="d7f5c-133">Understanding the quality of the model</span></span>

<span data-ttu-id="d7f5c-134">當您使用 CLI 工具生成"最佳模型"時，您將看到針對要定位的 ML 任務所需的品質指標（如準確性和 R-平方度）。</span><span class="sxs-lookup"><span data-stu-id="d7f5c-134">When you generate a 'best model' with the CLI tool, you see quality metrics (such as accuracy and R-Squared) as appropriate for the ML task you're targeting.</span></span>

<span data-ttu-id="d7f5c-135">在這裡，這些指標按 ML 任務進行分組，以便您可以瞭解自動生成的"最佳模型"的品質。</span><span class="sxs-lookup"><span data-stu-id="d7f5c-135">Here those metrics are summarized grouped by ML task so you can understand the quality of your auto-generated 'best model'.</span></span>

### <a name="metrics-for-binary-classification-models"></a><span data-ttu-id="d7f5c-136">二元分類模型的計量</span><span class="sxs-lookup"><span data-stu-id="d7f5c-136">Metrics for Binary Classification models</span></span>

<span data-ttu-id="d7f5c-137">下列顯示 CLI 找到之前五個模型的二元分類 ML 工作計量清單：</span><span class="sxs-lookup"><span data-stu-id="d7f5c-137">The following displays the binary classification ML task metrics list for the top five models found by the CLI:</span></span>

![image](media/automate-training-with-cli/cli-binary-classification-metrics.png)

<span data-ttu-id="d7f5c-139">準確性是分類問題的熱門指標，但準確性並不總是從以下引用中解釋的最佳指標來選擇最佳模型。</span><span class="sxs-lookup"><span data-stu-id="d7f5c-139">Accuracy is a popular metric for classification problems, however accuracy isn't always the best metric to select the best model from as explained in the following references.</span></span> <span data-ttu-id="d7f5c-140">在某些情況下，您需要評估模型品質和其他計量。</span><span class="sxs-lookup"><span data-stu-id="d7f5c-140">There are cases where you need to evaluate the quality of your model with additional metrics.</span></span>

<span data-ttu-id="d7f5c-141">要探索和瞭解由 CLI 輸出的指標，請參閱[二進位分類的評估指標](resources/metrics.md#evaluation-metrics-for-binary-classification)。</span><span class="sxs-lookup"><span data-stu-id="d7f5c-141">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for binary classification](resources/metrics.md#evaluation-metrics-for-binary-classification).</span></span>

### <a name="metrics-for-multi-class-classification-models"></a><span data-ttu-id="d7f5c-142">多元分類模型的計量</span><span class="sxs-lookup"><span data-stu-id="d7f5c-142">Metrics for Multi-class Classification models</span></span>

<span data-ttu-id="d7f5c-143">下列顯示 CLI 找到之前五個模型的多元分類 ML 工作計量清單：</span><span class="sxs-lookup"><span data-stu-id="d7f5c-143">The following displays the multi-class classification ML task metrics list for the top five models found by the CLI:</span></span>

![image](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

<span data-ttu-id="d7f5c-145">要流覽和瞭解由 CLI 輸出的指標，請參閱[多類分類的評估指標](resources/metrics.md#evaluation-metrics-for-multi-class-classification)。</span><span class="sxs-lookup"><span data-stu-id="d7f5c-145">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for multiclass classification](resources/metrics.md#evaluation-metrics-for-multi-class-classification).</span></span>

### <a name="metrics-for-regression-and-recommendation-models"></a><span data-ttu-id="d7f5c-146">回歸和推薦模型的指標</span><span class="sxs-lookup"><span data-stu-id="d7f5c-146">Metrics for Regression and Recommendation models</span></span>

<span data-ttu-id="d7f5c-147">如果觀察到的值和模型預測值之間差異很小且非偏誤，則迴歸模型非常適合這種資料。</span><span class="sxs-lookup"><span data-stu-id="d7f5c-147">A regression model fits the data well if the differences between the observed values and the model's predicted values are small and unbiased.</span></span> <span data-ttu-id="d7f5c-148">可以使用特定計量評估迴歸。</span><span class="sxs-lookup"><span data-stu-id="d7f5c-148">Regression can be evaluated with certain metrics.</span></span>

<span data-ttu-id="d7f5c-149">您將看到 CLI 找到的最佳五大品質模型的類似指標清單。</span><span class="sxs-lookup"><span data-stu-id="d7f5c-149">You'll see a similar list of metrics for the best top five quality models found by the CLI.</span></span> <span data-ttu-id="d7f5c-150">在這個特例中與迴歸 ML 工作相關：</span><span class="sxs-lookup"><span data-stu-id="d7f5c-150">In this particular case related to a regression ML task:</span></span>

![image](media/automate-training-with-cli/cli-regression-metrics.png)

<span data-ttu-id="d7f5c-152">要流覽和瞭解 CLI 輸出的指標，請參閱[回歸的評估指標](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation)。</span><span class="sxs-lookup"><span data-stu-id="d7f5c-152">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for regression](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation).</span></span>

## <a name="see-also"></a><span data-ttu-id="d7f5c-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7f5c-153">See also</span></span>

- [<span data-ttu-id="d7f5c-154">如何安裝 ML.NET CLI 工具</span><span class="sxs-lookup"><span data-stu-id="d7f5c-154">How to install the ML.NET CLI tool</span></span>](how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="d7f5c-155">教程：使用 cLI ML.NET分析情緒</span><span class="sxs-lookup"><span data-stu-id="d7f5c-155">Tutorial: Analyze sentiment using the ML.NET CLI</span></span>](tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="d7f5c-156">ML.NET CLI 命令參考</span><span class="sxs-lookup"><span data-stu-id="d7f5c-156">ML.NET CLI command reference</span></span>](reference/ml-net-cli-reference.md)
- [<span data-ttu-id="d7f5c-157">ML.NET CLI 中的遙測</span><span class="sxs-lookup"><span data-stu-id="d7f5c-157">Telemetry in ML.NET CLI</span></span>](resources/ml-net-cli-telemetry.md)
