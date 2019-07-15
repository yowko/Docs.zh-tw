---
title: 使用 ML.NET CLI 自動化模型定型
description: 探索如何使用 ML.NET CLI 工具，從命令列自動定型最佳模型。
author: CESARDELATORRE
ms.date: 04/17/2019
ms.custom: how-to
ms.openlocfilehash: e5f75dc70ea5a76951d8698ea9c0d07cb2d4ddec
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663930"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a><span data-ttu-id="8afe9-103">使用 ML.NET CLI 自動化模型定型</span><span class="sxs-lookup"><span data-stu-id="8afe9-103">Automate model training with the ML.NET CLI</span></span>

<span data-ttu-id="8afe9-104">ML.NET CLI 在學習 ML.NET 時，向 .NET 開發人員「推廣」ML.NET。</span><span class="sxs-lookup"><span data-stu-id="8afe9-104">The ML.NET CLI "democratizes" ML.NET for .NET developers when learning ML.NET.</span></span>

<span data-ttu-id="8afe9-105">若要使用 ML.NET API 本身 (不利用 ML.NET AutoML CLI)，您需要選擇定型器 (實作特定工作的機器學習演算法) 以及要套用至資料的一組資料轉換 (特徵工程)。</span><span class="sxs-lookup"><span data-stu-id="8afe9-105">To use the ML.NET API by itself, (without the ML.NET AutoML CLI) you need to choose a trainer (implementation of a machine learning algorithm for a particular task), and the set of data transformations (feature engineering) to apply to your data.</span></span> <span data-ttu-id="8afe9-106">每個資料集的最佳管道各有不同，而從所有的選項中選取最佳演算法會增加複雜性。</span><span class="sxs-lookup"><span data-stu-id="8afe9-106">The optimal pipeline will vary for each dataset and selecting the optimal algorithm from all the choices adds to the complexity.</span></span> <span data-ttu-id="8afe9-107">更進一步，每個演算法都有一組要微調的超參數。</span><span class="sxs-lookup"><span data-stu-id="8afe9-107">Even further, each algorithm has a set of hyperparameters to be tuned.</span></span> <span data-ttu-id="8afe9-108">因此，您可以花費數週或數月來最佳化機器學習模型，嘗試尋找特徵工程、學習演算法和超參數的最佳組合。</span><span class="sxs-lookup"><span data-stu-id="8afe9-108">Hence, you can spend weeks and sometimes months on machine learning model optimization trying to find the best combinations of feature engineering, learning algorithms, and hyperparameters.</span></span>

<span data-ttu-id="8afe9-109">此程序可使用 ML.NET CLI 自動化，這會實作 ML.NET AutoML 的智慧引擎。</span><span class="sxs-lookup"><span data-stu-id="8afe9-109">This process can be automated with the ML.NET CLI, which implements the ML.NET AutoML intelligent engine.</span></span>

> [!NOTE]
> <span data-ttu-id="8afe9-110">本主題參考 ML.NET **CLI** 和 ML.NET **AutoML**，它們目前為公開預覽版，因此内容可能會有變更。</span><span class="sxs-lookup"><span data-stu-id="8afe9-110">This topic refers to ML.NET **CLI** and ML.NET **AutoML**, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="what-is-the-mlnet-command-line-interface-cli"></a><span data-ttu-id="8afe9-111">什麼是 ML.NET 命令列介面 (CLI)？</span><span class="sxs-lookup"><span data-stu-id="8afe9-111">What is the ML.NET Command-line Interface (CLI)?</span></span>

<span data-ttu-id="8afe9-112">您可以在任何命令提示字元 (Windows、Mac 或 Linux) 中執行 ML.NET CLI，根據您的定型資料集產生高品質的 ML.NET 模型和原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="8afe9-112">You can run the ML.NET CLI on any command-prompt (Windows, Mac, or Linux) for generating good quality ML.NET models and source code based on your training dataset.</span></span>

<span data-ttu-id="8afe9-113">如下圖所示，產生高品質的 ML.NET 模型 (序列化模型 .zip 檔案) 加上執行/評分數模型的範例 C# 程式碼很容易。</span><span class="sxs-lookup"><span data-stu-id="8afe9-113">As shown in the figure below, it is simple to generate a high quality ML.NET model (serialized model .zip file) plus the sample C# code to run/score that model.</span></span> <span data-ttu-id="8afe9-114">此外，也產生建立/定型模型的 C# 程式碼，以便您可以研究並重覆所產生「最佳模型」使用的演算法和設定。</span><span class="sxs-lookup"><span data-stu-id="8afe9-114">In addition, the C# code to create/train that model is also generated, so that you can research and iterate on the algorithm and settings used for that generated "best model".</span></span>

<span data-ttu-id="8afe9-115">![圖](media/automate-training-with-cli/cli-high-level-process.png "在 ML.NET CLI 內工作的 AutoML 引擎")</span><span class="sxs-lookup"><span data-stu-id="8afe9-115">![image](media/automate-training-with-cli/cli-high-level-process.png "AutoML engine working inside the ML.NET CLI")</span></span>

<span data-ttu-id="8afe9-116">您可以從自己的資料集產生這些資產，不用自行撰寫程式碼，因此即使您已熟悉 ML.NET，也能提升生產力。</span><span class="sxs-lookup"><span data-stu-id="8afe9-116">You can generate those assets from your own datasets without coding by yourself, so it also improves your productivity even if you already know ML.NET.</span></span>

<span data-ttu-id="8afe9-117">ML.NET CLI 目前支援的 ML 工作如下：</span><span class="sxs-lookup"><span data-stu-id="8afe9-117">Currently, the ML Tasks supported by the ML.NET CLI are:</span></span>

- `binary-classification`
- `multiclass-classification`
- `regression`
- <span data-ttu-id="8afe9-118">未來：其他機器學習工作，例如 `recommendation`、`ranking`、`anomaly-detection`、`clustering`</span><span class="sxs-lookup"><span data-stu-id="8afe9-118">Future: other machine learning tasks such as `recommendation`, `ranking`, `anomaly-detection`, `clustering`</span></span>

<span data-ttu-id="8afe9-119">使用範例：</span><span class="sxs-lookup"><span data-stu-id="8afe9-119">Example of usage:</span></span>

```console
> mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

![影像](media/automate-training-with-cli/cli-model-generation.gif)

<span data-ttu-id="8afe9-121">您可以用在 *Windows PowerShell*、\*macOS/Linux bash 或 *Windows CMD* 執行的方式執行它。</span><span class="sxs-lookup"><span data-stu-id="8afe9-121">You can run it the same way on *Windows PowerShell*, \*macOS/Linux bash, or *Windows CMD*.</span></span> <span data-ttu-id="8afe9-122">不過，表格式自動完成 (參數建議) 不適用於 *Windows CMD*。</span><span class="sxs-lookup"><span data-stu-id="8afe9-122">However, tabular auto-completion (parameter suggestions) won't work on *Windows CMD*.</span></span>

## <a name="output-assets-generated"></a><span data-ttu-id="8afe9-123">產生的輸出資產</span><span class="sxs-lookup"><span data-stu-id="8afe9-123">Output assets generated</span></span>

<span data-ttu-id="8afe9-124">CLI `auto-train` 命令會在輸出資料夾中產生下列資產：</span><span class="sxs-lookup"><span data-stu-id="8afe9-124">The CLI `auto-train` command generates the following assets in the output folder:</span></span>

- <span data-ttu-id="8afe9-125">序列化模型 .zip (「最佳模型」) 準備好用於執行預測。</span><span class="sxs-lookup"><span data-stu-id="8afe9-125">A serialized model .zip ("best model") ready to use for running predictions.</span></span>
- <span data-ttu-id="8afe9-126">C# 解決方案具有：</span><span class="sxs-lookup"><span data-stu-id="8afe9-126">C# solution with:</span></span>
  - <span data-ttu-id="8afe9-127">C# 程式碼，執行/評分產生的模型 (使用該模型以您的終端使用者應用程式建立預測)。</span><span class="sxs-lookup"><span data-stu-id="8afe9-127">C# code to run/score that generated model (to make predictions in your end-user apps with that model).</span></span>
  - <span data-ttu-id="8afe9-128">C# 程式碼和定型程式碼，用來產生該模型 (適用於學習目的或重新定型模型)。</span><span class="sxs-lookup"><span data-stu-id="8afe9-128">C# code with the training code used to generate that model (for learning purposes or model retraining).</span></span>
- <span data-ttu-id="8afe9-129">記錄檔，具有多個已評估之演算法所有反覆項目/清除的資訊，包括其詳細的組態/管線。</span><span class="sxs-lookup"><span data-stu-id="8afe9-129">Log file with information of all iterations/sweeps across the multiple algorithms evaluated, including their detailed configuration/pipeline.</span></span>

<span data-ttu-id="8afe9-130">前兩項資產可以直接用於終端使用者應用程式 (ASP.NET Core Web 應用程式、服務、桌面應用程式等)，使用已產生的 ML 模型建立預測。</span><span class="sxs-lookup"><span data-stu-id="8afe9-130">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

<span data-ttu-id="8afe9-131">第三項資產，即定型程式碼，會向您顯示 CLI 已使用哪些 ML.NET API 程式碼來定型產生的模型，讓您可以重新定型模型，以及調查和逐一查看 CLI 和 AutoML 在幕後選取了哪些特定的定型器/演算法和超參數。</span><span class="sxs-lookup"><span data-stu-id="8afe9-131">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can retrain your model and investigate and iterate on which specific trainer/algorithm and hyperparameters were selected by the CLI and AutoML under the covers.</span></span>

## <a name="understanding-the-quality-of-the-model"></a><span data-ttu-id="8afe9-132">了解模型的品質</span><span class="sxs-lookup"><span data-stu-id="8afe9-132">Understanding the quality of the model</span></span>

<span data-ttu-id="8afe9-133">當您使用 CLI 工具產生「最佳模型」後，您會看到適合您目標 ML 工作的品質計量 (例如精確度和 R 平方)。</span><span class="sxs-lookup"><span data-stu-id="8afe9-133">When you generate a 'best model' with the CLI tool, you see quality metrics (such as accuracy, and R-Squared) as appropriate for the ML task you are targeting.</span></span>

<span data-ttu-id="8afe9-134">在此摘要依 ML 工作分組的計量，以便您了解自動產生的「最佳模型」品質。</span><span class="sxs-lookup"><span data-stu-id="8afe9-134">Here we summarize those metrics grouped by ML task so you can understand the quality of your auto-generated 'best model'.</span></span>

### <a name="metrics-for-binary-classification-models"></a><span data-ttu-id="8afe9-135">二元分類模型的計量</span><span class="sxs-lookup"><span data-stu-id="8afe9-135">Metrics for Binary Classification models</span></span>

<span data-ttu-id="8afe9-136">下列顯示 CLI 找到之前五個模型的二元分類 ML 工作計量清單：</span><span class="sxs-lookup"><span data-stu-id="8afe9-136">The following displays the binary classification ML task metrics list for the top five models found by the CLI:</span></span>

![影像](media/automate-training-with-cli/cli-binary-classification-metrics.png)

<span data-ttu-id="8afe9-138">精確度是分類問題的最熱門計量，但如以下參考所述，精確度不一定一律是選取最佳模型的最佳計量。</span><span class="sxs-lookup"><span data-stu-id="8afe9-138">Accuracy is a popular metric for classification problems, however accuracy is not always the best metric to select the best model from as explained in the references below.</span></span> <span data-ttu-id="8afe9-139">在某些情況下，您需要評估模型品質和其他計量。</span><span class="sxs-lookup"><span data-stu-id="8afe9-139">There are cases where you need to evaluate the quality of your model with additional metrics.</span></span>

<span data-ttu-id="8afe9-140">若要探索及了解 CLI 輸出的計量，請參閱[二元分類計量](resources/metrics.md#metrics-for-binary-classification)。</span><span class="sxs-lookup"><span data-stu-id="8afe9-140">To explore and understand the metrics that are output by the CLI, see [Metrics for binary classification](resources/metrics.md#metrics-for-binary-classification).</span></span>

### <a name="metrics-for-multi-class-classification-models"></a><span data-ttu-id="8afe9-141">多元分類模型的計量</span><span class="sxs-lookup"><span data-stu-id="8afe9-141">Metrics for Multi-class Classification models</span></span>

<span data-ttu-id="8afe9-142">下列顯示 CLI 找到之前五個模型的多元分類 ML 工作計量清單：</span><span class="sxs-lookup"><span data-stu-id="8afe9-142">The following displays the multi-class classification ML task metrics list for the top five models found by the CLI:</span></span>

![影像](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

<span data-ttu-id="8afe9-144">若要探索及了解 CLI 輸出的計量，請參閱[多元分類計量](resources/metrics.md#metrics-for-multi-class-classification)。</span><span class="sxs-lookup"><span data-stu-id="8afe9-144">To explore and understand the metrics that are output by the CLI, see [Metrics for multiclass classification](resources/metrics.md#metrics-for-multi-class-classification).</span></span>

### <a name="metrics-for-regression-models"></a><span data-ttu-id="8afe9-145">迴歸模型的計量</span><span class="sxs-lookup"><span data-stu-id="8afe9-145">Metrics for Regression models</span></span>

<span data-ttu-id="8afe9-146">如果觀察到的值和模型預測值之間差異很小且非偏誤，則迴歸模型非常適合這種資料。</span><span class="sxs-lookup"><span data-stu-id="8afe9-146">A regression model fits the data well if the differences between the observed values and the model's predicted values are small and unbiased.</span></span> <span data-ttu-id="8afe9-147">可以使用特定計量評估迴歸。</span><span class="sxs-lookup"><span data-stu-id="8afe9-147">Regression can be evaluated with certain metrics.</span></span>

<span data-ttu-id="8afe9-148">您會看到類似最佳 CLI 找到之前五個品質最佳模型的計量清單。</span><span class="sxs-lookup"><span data-stu-id="8afe9-148">You will see a similar list of metrics for the best top five quality models found by the CLI.</span></span> <span data-ttu-id="8afe9-149">在這個特例中與迴歸 ML 工作相關：</span><span class="sxs-lookup"><span data-stu-id="8afe9-149">In this particular case related to a regression ML task:</span></span>

![影像](media/automate-training-with-cli/cli-regression-metrics.png)

<span data-ttu-id="8afe9-151">若要探索及了解 CLI 輸出的計量，請參閱[廻歸計量](resources/metrics.md#metrics-for-regression)。</span><span class="sxs-lookup"><span data-stu-id="8afe9-151">To explore and understand the metrics that are output by the CLI, see [Metrics for regression](resources/metrics.md#metrics-for-regression).</span></span>

## <a name="see-also"></a><span data-ttu-id="8afe9-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8afe9-152">See also</span></span>

- [<span data-ttu-id="8afe9-153">如何安裝 ML.NET CLI 工具</span><span class="sxs-lookup"><span data-stu-id="8afe9-153">How to install the ML.NET CLI tool</span></span>](how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="8afe9-154">教學課程：使用 ML.NET CLI 自動產生二元分類器</span><span class="sxs-lookup"><span data-stu-id="8afe9-154">Tutorial: Auto generate a binary classifier using the ML.NET CLI</span></span>](tutorials/mlnet-cli.md)
- [<span data-ttu-id="8afe9-155">ML.NET CLI 命令參考</span><span class="sxs-lookup"><span data-stu-id="8afe9-155">ML.NET CLI command reference</span></span>](reference/ml-net-cli-reference.md)
- [<span data-ttu-id="8afe9-156">ML.NET CLI 中的遙測</span><span class="sxs-lookup"><span data-stu-id="8afe9-156">Telemetry in ML.NET CLI</span></span>](resources/ml-net-cli-telemetry.md)
