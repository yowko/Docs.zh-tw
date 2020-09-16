---
title: 如何使用 ML.NET 自動化的 ML API
description: ML.NET 自動化的 ML API 會自動化模型建置程序，並產生隨時可供部署的模型。 了解您可用來設定自動化機器學習工作的選項。
ms.date: 12/18/2019
ms.custom: mvc,how-to
ms.openlocfilehash: b1ef526301e01e1e75e71e0646f4d11e68215d69
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540728"
---
# <a name="how-to-use-the-mlnet-automated-machine-learning-api"></a><span data-ttu-id="fdc36-104">如何使用 ML.NET 自動化的機器學習 API</span><span class="sxs-lookup"><span data-stu-id="fdc36-104">How to use the ML.NET automated machine learning API</span></span>

<span data-ttu-id="fdc36-105">自動化的機器學習 (AutoML) 會自動化將機器學習套用至資料的程序。</span><span class="sxs-lookup"><span data-stu-id="fdc36-105">Automated machine learning (AutoML) automates the process of applying machine learning to data.</span></span> <span data-ttu-id="fdc36-106">指定資料集，您可以執行 AutoML **實驗**來逐一查看不同的資料特徵化、機器學習演算法和超參數，以選取最佳的模型。</span><span class="sxs-lookup"><span data-stu-id="fdc36-106">Given a dataset, you can run an AutoML **experiment** to iterate over different data featurizations, machine learning algorithms, and hyperparameters to select the best model.</span></span>

> [!NOTE]
> <span data-ttu-id="fdc36-107">本主題是指 ML.NET 的自動化機器學習 API，目前為預覽版。</span><span class="sxs-lookup"><span data-stu-id="fdc36-107">This topic refers to the automated machine learning API for ML.NET, which is currently in preview.</span></span> <span data-ttu-id="fdc36-108">資料可能會有變更。</span><span class="sxs-lookup"><span data-stu-id="fdc36-108">Material may be subject to change.</span></span>

## <a name="load-data"></a><span data-ttu-id="fdc36-109">載入資料</span><span class="sxs-lookup"><span data-stu-id="fdc36-109">Load data</span></span>

<span data-ttu-id="fdc36-110">自動化的機器學習支援將資料集載入至 [IDataView](xref:Microsoft.ML.IDataView)。</span><span class="sxs-lookup"><span data-stu-id="fdc36-110">Automated machine learning supports loading a dataset into an [IDataView](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="fdc36-111">資料的格式可以是定位字元分隔值 (TSV) 檔案和逗號分隔值 (CSV) 檔案。</span><span class="sxs-lookup"><span data-stu-id="fdc36-111">Data can be in the form of tab-separated value (TSV) files and comma separated value (CSV) files.</span></span>

<span data-ttu-id="fdc36-112">範例：</span><span class="sxs-lookup"><span data-stu-id="fdc36-112">Example:</span></span>

```csharp
using Microsoft.ML;
using Microsoft.ML.AutoML;
    // ...
    MLContext mlContext = new MLContext();
    IDataView trainDataView = mlContext.Data.LoadFromTextFile<SentimentIssue>("my-data-file.csv", hasHeader: true);
```

## <a name="select-the-machine-learning-task-type"></a><span data-ttu-id="fdc36-113">選取機器學習工作類型</span><span class="sxs-lookup"><span data-stu-id="fdc36-113">Select the machine learning task type</span></span>

<span data-ttu-id="fdc36-114">建立實驗之前，請先決定您想要解決的機器學習問題種類。</span><span class="sxs-lookup"><span data-stu-id="fdc36-114">Before creating an experiment, determine the kind of machine learning problem you want to solve.</span></span> <span data-ttu-id="fdc36-115">自動化的機器學習支援下列 ML 工作：</span><span class="sxs-lookup"><span data-stu-id="fdc36-115">Automated machine learning supports the following ML tasks:</span></span>

* <span data-ttu-id="fdc36-116">二元分類</span><span class="sxs-lookup"><span data-stu-id="fdc36-116">Binary Classification</span></span>
* <span data-ttu-id="fdc36-117">多元分類</span><span class="sxs-lookup"><span data-stu-id="fdc36-117">Multiclass Classification</span></span>
* <span data-ttu-id="fdc36-118">迴歸</span><span class="sxs-lookup"><span data-stu-id="fdc36-118">Regression</span></span>
* <span data-ttu-id="fdc36-119">建議</span><span class="sxs-lookup"><span data-stu-id="fdc36-119">Recommendation</span></span>

## <a name="create-experiment-settings"></a><span data-ttu-id="fdc36-120">建立實驗設定</span><span class="sxs-lookup"><span data-stu-id="fdc36-120">Create experiment settings</span></span>

<span data-ttu-id="fdc36-121">建立已決定 ML 工作類型的實驗設定：</span><span class="sxs-lookup"><span data-stu-id="fdc36-121">Create experiment settings for the determined ML task type:</span></span>

* <span data-ttu-id="fdc36-122">二元分類</span><span class="sxs-lookup"><span data-stu-id="fdc36-122">Binary Classification</span></span>

  ```csharp
  var experimentSettings = new BinaryExperimentSettings();
  ```

* <span data-ttu-id="fdc36-123">多元分類</span><span class="sxs-lookup"><span data-stu-id="fdc36-123">Multiclass Classification</span></span>

  ```csharp
  var experimentSettings = new MulticlassExperimentSettings();
  ```

* <span data-ttu-id="fdc36-124">迴歸</span><span class="sxs-lookup"><span data-stu-id="fdc36-124">Regression</span></span>

  ```csharp
  var experimentSettings = new RegressionExperimentSettings();
  ```

* <span data-ttu-id="fdc36-125">建議</span><span class="sxs-lookup"><span data-stu-id="fdc36-125">Recommendation</span></span>

  ```csharp
  var experimentSettings = new RecommendationExperimentSettings();
  ```

## <a name="configure-experiment-settings"></a><span data-ttu-id="fdc36-126">設定實驗設定</span><span class="sxs-lookup"><span data-stu-id="fdc36-126">Configure experiment settings</span></span>

<span data-ttu-id="fdc36-127">實驗的可設定程度很高。</span><span class="sxs-lookup"><span data-stu-id="fdc36-127">Experiments are highly configurable.</span></span> <span data-ttu-id="fdc36-128">如需組態設定的完整清單，請參閱 [AutoML API 文件](/dotnet/api/microsoft.ml.automl?view=ml-dotnet-preview)。</span><span class="sxs-lookup"><span data-stu-id="fdc36-128">See the [AutoML API docs](/dotnet/api/microsoft.ml.automl?view=ml-dotnet-preview) for a full list of configuration settings.</span></span>

<span data-ttu-id="fdc36-129">部分範例包括：</span><span class="sxs-lookup"><span data-stu-id="fdc36-129">Some examples include:</span></span>

1. <span data-ttu-id="fdc36-130">指定允許執行實驗的時間上限。</span><span class="sxs-lookup"><span data-stu-id="fdc36-130">Specify the maximum time that the experiment is allowed to run.</span></span>

    ```csharp
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    ```

1. <span data-ttu-id="fdc36-131">在排程完成前先使用取消權杖取消實驗。</span><span class="sxs-lookup"><span data-stu-id="fdc36-131">Use a cancellation token to cancel the experiment before it is scheduled to finish.</span></span>

    ```csharp
    experimentSettings.CancellationToken = cts.Token;

    // Cancel experiment after the user presses any key
    CancelExperimentAfterAnyKeyPress(cts);
    ```

1. <span data-ttu-id="fdc36-132">指定不同的最佳化計量。</span><span class="sxs-lookup"><span data-stu-id="fdc36-132">Specify a different optimizing metric.</span></span>

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.OptimizingMetric = RegressionMetric.MeanSquaredError;
    ```

1. <span data-ttu-id="fdc36-133">`CacheDirectory` 設定是目錄的指標，所有在 AutoML 工作期間定型的模型都儲存在此目錄。</span><span class="sxs-lookup"><span data-stu-id="fdc36-133">The `CacheDirectory` setting is a pointer to a directory where all models trained during the AutoML task will be saved.</span></span> <span data-ttu-id="fdc36-134">如果 `CacheDirectory` 設為 null，則模型會保留在記憶體中，而不是寫入磁碟。</span><span class="sxs-lookup"><span data-stu-id="fdc36-134">If `CacheDirectory` is set to null, models will be kept in memory instead of written to disk.</span></span>

    ```csharp
    experimentSettings.CacheDirectory = null;
    ```

1. <span data-ttu-id="fdc36-135">指示自動化的 ML 不要使用某些定型器。</span><span class="sxs-lookup"><span data-stu-id="fdc36-135">Instruct automated ML not to use certain trainers.</span></span>

    <span data-ttu-id="fdc36-136">依工作探索要最佳化之定型器的預設清單。</span><span class="sxs-lookup"><span data-stu-id="fdc36-136">A default list of trainers to optimize are explored per task.</span></span> <span data-ttu-id="fdc36-137">這份清單可針對每個實驗修改。</span><span class="sxs-lookup"><span data-stu-id="fdc36-137">This list can be modified for each experiment.</span></span> <span data-ttu-id="fdc36-138">例如，您可從清單移除對資料集執行緩慢的定型器。</span><span class="sxs-lookup"><span data-stu-id="fdc36-138">For instance, trainers that run slowly on your dataset can be removed from the list.</span></span> <span data-ttu-id="fdc36-139">若要最佳化一個特定的定型器，請呼叫 `experimentSettings.Trainers.Clear()`，然後新增您想要使用的定型器。</span><span class="sxs-lookup"><span data-stu-id="fdc36-139">To optimize on one specific trainer call `experimentSettings.Trainers.Clear()`, then add the trainer that you want to use.</span></span>

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.Trainers.Remove(RegressionTrainer.LbfgsPoissonRegression);
    experimentSettings.Trainers.Remove(RegressionTrainer.OnlineGradientDescent);
    ```

<span data-ttu-id="fdc36-140">依 ML 工作支援的定型器清單位在對應連結中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="fdc36-140">The list of supported trainers per ML task can be found at the corresponding link below:</span></span>

* [<span data-ttu-id="fdc36-141">支援的二元分類演算法</span><span class="sxs-lookup"><span data-stu-id="fdc36-141">Supported Binary Classification Algorithms</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationTrainer)
* [<span data-ttu-id="fdc36-142">支援的多元分類演算法</span><span class="sxs-lookup"><span data-stu-id="fdc36-142">Supported Multiclass Classification Algorithms</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationTrainer)
* [<span data-ttu-id="fdc36-143">支援的迴歸演算法</span><span class="sxs-lookup"><span data-stu-id="fdc36-143">Supported Regression Algorithms</span></span>](xref:Microsoft.ML.AutoML.RegressionTrainer)
* [<span data-ttu-id="fdc36-144">支援的建議演算法</span><span class="sxs-lookup"><span data-stu-id="fdc36-144">Supported Recommendation Algorithms</span></span>](xref:Microsoft.ML.AutoML.RecommendationTrainer)

## <a name="optimizing-metric"></a><span data-ttu-id="fdc36-145">最佳化計量</span><span class="sxs-lookup"><span data-stu-id="fdc36-145">Optimizing metric</span></span>

<span data-ttu-id="fdc36-146">最佳化度量，如上例所示，決定要在模型定型期間最佳化的計量。</span><span class="sxs-lookup"><span data-stu-id="fdc36-146">The optimizing metric, as shown in the example above, determines the metric to be optimized during model training.</span></span> <span data-ttu-id="fdc36-147">您可以選取的最佳化計量由您所選工作類型決定。</span><span class="sxs-lookup"><span data-stu-id="fdc36-147">The optimizing metric you can select is determined by the task type you choose.</span></span> <span data-ttu-id="fdc36-148">以下為可用計量的清單。</span><span class="sxs-lookup"><span data-stu-id="fdc36-148">Below is a list of available metrics.</span></span>

|[<span data-ttu-id="fdc36-149">二元分類</span><span class="sxs-lookup"><span data-stu-id="fdc36-149">Binary Classification</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationMetric) | [<span data-ttu-id="fdc36-150">多元分類</span><span class="sxs-lookup"><span data-stu-id="fdc36-150">Multiclass Classification</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric) |[<span data-ttu-id="fdc36-151">回歸 & 建議</span><span class="sxs-lookup"><span data-stu-id="fdc36-151">Regression & Recommendation</span></span>](xref:Microsoft.ML.AutoML.RegressionMetric)
|-- |-- |--
|<span data-ttu-id="fdc36-152">精確度</span><span class="sxs-lookup"><span data-stu-id="fdc36-152">Accuracy</span></span>| <span data-ttu-id="fdc36-153">LogLoss</span><span class="sxs-lookup"><span data-stu-id="fdc36-153">LogLoss</span></span> | <span data-ttu-id="fdc36-154">RSquared</span><span class="sxs-lookup"><span data-stu-id="fdc36-154">RSquared</span></span>
|<span data-ttu-id="fdc36-155">AreaUnderPrecisionRecallCurve</span><span class="sxs-lookup"><span data-stu-id="fdc36-155">AreaUnderPrecisionRecallCurve</span></span> | <span data-ttu-id="fdc36-156">LogLossReduction</span><span class="sxs-lookup"><span data-stu-id="fdc36-156">LogLossReduction</span></span> | <span data-ttu-id="fdc36-157">MeanAbsoluteError</span><span class="sxs-lookup"><span data-stu-id="fdc36-157">MeanAbsoluteError</span></span>
|<span data-ttu-id="fdc36-158">AreaUnderRocCurve</span><span class="sxs-lookup"><span data-stu-id="fdc36-158">AreaUnderRocCurve</span></span> | <span data-ttu-id="fdc36-159">MacroAccuracy</span><span class="sxs-lookup"><span data-stu-id="fdc36-159">MacroAccuracy</span></span> | <span data-ttu-id="fdc36-160">MeanSquaredError</span><span class="sxs-lookup"><span data-stu-id="fdc36-160">MeanSquaredError</span></span>
|<span data-ttu-id="fdc36-161">F1Score</span><span class="sxs-lookup"><span data-stu-id="fdc36-161">F1Score</span></span> | <span data-ttu-id="fdc36-162">MicroAccuracy</span><span class="sxs-lookup"><span data-stu-id="fdc36-162">MicroAccuracy</span></span> | <span data-ttu-id="fdc36-163">RootMeanSquaredError</span><span class="sxs-lookup"><span data-stu-id="fdc36-163">RootMeanSquaredError</span></span>
|<span data-ttu-id="fdc36-164">NegativePrecision</span><span class="sxs-lookup"><span data-stu-id="fdc36-164">NegativePrecision</span></span> | <span data-ttu-id="fdc36-165">TopKAccuracy</span><span class="sxs-lookup"><span data-stu-id="fdc36-165">TopKAccuracy</span></span>
|<span data-ttu-id="fdc36-166">NegativeRecall</span><span class="sxs-lookup"><span data-stu-id="fdc36-166">NegativeRecall</span></span> |
|<span data-ttu-id="fdc36-167">PositivePrecision</span><span class="sxs-lookup"><span data-stu-id="fdc36-167">PositivePrecision</span></span>
|<span data-ttu-id="fdc36-168">PositiveRecall</span><span class="sxs-lookup"><span data-stu-id="fdc36-168">PositiveRecall</span></span>

## <a name="data-pre-processing-and-featurization"></a><span data-ttu-id="fdc36-169">資料預先處理與特徵化</span><span class="sxs-lookup"><span data-stu-id="fdc36-169">Data pre-processing and featurization</span></span>

> [!NOTE]
> <span data-ttu-id="fdc36-170">Feature 資料行僅支援 <xref:System.Boolean> 、和的類型 <xref:System.Single> <xref:System.String> 。</span><span class="sxs-lookup"><span data-stu-id="fdc36-170">The feature column only supported types of <xref:System.Boolean>, <xref:System.Single>, and <xref:System.String>.</span></span>

<span data-ttu-id="fdc36-171">根據預設，資料予以前置處理，並為您自動執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="fdc36-171">Data pre-processing happens by default and the following steps are performed automatically for you:</span></span>

1. <span data-ttu-id="fdc36-172">卸除無有用資訊的特性</span><span class="sxs-lookup"><span data-stu-id="fdc36-172">Drop features with no useful information</span></span>

    <span data-ttu-id="fdc36-173">將無實用資訊的特徵從定型與驗證集合中卸除。</span><span class="sxs-lookup"><span data-stu-id="fdc36-173">Drop features with no useful information from training and validation sets.</span></span> <span data-ttu-id="fdc36-174">其中包括遺漏所有值、所有資料列之間的值相同，或具有極高基數 (例如雜湊、識別碼或 GUID) 的特徵。</span><span class="sxs-lookup"><span data-stu-id="fdc36-174">These include features with all values missing, same value across all rows or with extremely high cardinality (e.g., hashes, IDs or GUIDs).</span></span>

1. <span data-ttu-id="fdc36-175">遺漏值表示和插補</span><span class="sxs-lookup"><span data-stu-id="fdc36-175">Missing value indication and imputation</span></span>

    <span data-ttu-id="fdc36-176">以資料類型的預設值填入遺漏值資料格。</span><span class="sxs-lookup"><span data-stu-id="fdc36-176">Fill missing value cells with the default value for the datatype.</span></span> <span data-ttu-id="fdc36-177">以和輸入資料行相同的插槽數附加指標特性。</span><span class="sxs-lookup"><span data-stu-id="fdc36-177">Append indicator features with the same number of slots as the input column.</span></span> <span data-ttu-id="fdc36-178">如果輸入資料行中的值遺漏，則附加指標特性中的值是 `1`；否則為 `0`。</span><span class="sxs-lookup"><span data-stu-id="fdc36-178">The value in the appended indicator features is `1` if the value in the input column is missing and `0` otherwise.</span></span>

1. <span data-ttu-id="fdc36-179">產生其他特徵</span><span class="sxs-lookup"><span data-stu-id="fdc36-179">Generate additional features</span></span>

    <span data-ttu-id="fdc36-180">針對文字功能：使用 unigrams 和三字元字元的全字組功能。</span><span class="sxs-lookup"><span data-stu-id="fdc36-180">For text features: Bag-of-word features using unigrams and tri-character-grams.</span></span>

    <span data-ttu-id="fdc36-181">針對類別功能：適用于低基數功能的一種經常性編碼，以及高基數類別功能的一次熱雜湊編碼。</span><span class="sxs-lookup"><span data-stu-id="fdc36-181">For categorical features: One-hot encoding for low cardinality features, and one-hot-hash encoding for high cardinality categorical features.</span></span>

1. <span data-ttu-id="fdc36-182">轉換與編碼</span><span class="sxs-lookup"><span data-stu-id="fdc36-182">Transformations and encodings</span></span>

    <span data-ttu-id="fdc36-183">極少數唯一值轉換成類別特性的文字特性。</span><span class="sxs-lookup"><span data-stu-id="fdc36-183">Text features with very few unique values transformed into categorical features.</span></span> <span data-ttu-id="fdc36-184">視類別特性的基數而定，執行 One-Hot 編碼或 One-Hot 雜湊編碼。</span><span class="sxs-lookup"><span data-stu-id="fdc36-184">Depending on cardinality of categorical features, perform one-hot encoding or one-hot hash encoding.</span></span>

## <a name="exit-criteria"></a><span data-ttu-id="fdc36-185">允出準則</span><span class="sxs-lookup"><span data-stu-id="fdc36-185">Exit criteria</span></span>

<span data-ttu-id="fdc36-186">定義完成工作的準則：</span><span class="sxs-lookup"><span data-stu-id="fdc36-186">Define the criteria to complete your task:</span></span>

1. <span data-ttu-id="fdc36-187">在一段時間後結束 - 在您的實驗設定中使用 `MaxExperimentTimeInSeconds`，您可以定義工作應該繼續執行的秒數。</span><span class="sxs-lookup"><span data-stu-id="fdc36-187">Exit after a length of time - Using `MaxExperimentTimeInSeconds` in your experiment settings you can define how long in seconds that an task should continue to run.</span></span>

1. <span data-ttu-id="fdc36-188">於取消權杖處結束 - 您可以使用取消權杖，讓您在排程完成前取消工作。</span><span class="sxs-lookup"><span data-stu-id="fdc36-188">Exit on a cancellation token -  You can use a cancellation token that lets you cancel the task before it is scheduled to finish.</span></span>

    ```csharp
    var cts = new CancellationTokenSource();
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    experimentSettings.CancellationToken = cts.Token;
    ```

## <a name="create-an-experiment"></a><span data-ttu-id="fdc36-189">建立實驗</span><span class="sxs-lookup"><span data-stu-id="fdc36-189">Create an experiment</span></span>

<span data-ttu-id="fdc36-190">一旦設定了實驗設定，您就隨時可以建立實驗。</span><span class="sxs-lookup"><span data-stu-id="fdc36-190">Once you have configured the experiment settings, you are ready to create the experiment.</span></span>

```csharp
RegressionExperiment experiment = mlContext.Auto().CreateRegressionExperiment(experimentSettings);
```

## <a name="run-the-experiment"></a><span data-ttu-id="fdc36-191">執行實驗</span><span class="sxs-lookup"><span data-stu-id="fdc36-191">Run the experiment</span></span>

<span data-ttu-id="fdc36-192">執行實驗會觸發前置處理資料、選取學習演算法，以及微調超參數。</span><span class="sxs-lookup"><span data-stu-id="fdc36-192">Running the experiment triggers data pre-processing, learning algorithm selection, and hyperparameter tuning.</span></span> <span data-ttu-id="fdc36-193">AutoML 會繼續產生特徵化、學習演算法和超參數的組合，直到達到 `MaxExperimentTimeInSeconds` 或實驗終止。</span><span class="sxs-lookup"><span data-stu-id="fdc36-193">AutoML will continue to generate combinations of featurization, learning algorithms, and hyperparameters until the `MaxExperimentTimeInSeconds` is reached or the experiment is terminated.</span></span>

```csharp
ExperimentResult<RegressionMetrics> experimentResult = experiment
    .Execute(trainingDataView, LabelColumnName, progressHandler: progressHandler);
```

<span data-ttu-id="fdc36-194">如果您想要傳入驗證資料、指出資料行目的的資料行資訊或前置特徵化工具，請探索 `Execute()` 的其他多載。</span><span class="sxs-lookup"><span data-stu-id="fdc36-194">Explore other overloads for `Execute()` if you want to pass in validation data, column information indicating the column purpose, or prefeaturizers.</span></span>

## <a name="training-modes"></a><span data-ttu-id="fdc36-195">定型模式</span><span class="sxs-lookup"><span data-stu-id="fdc36-195">Training modes</span></span>

### <a name="training-dataset"></a><span data-ttu-id="fdc36-196">定型資料集</span><span class="sxs-lookup"><span data-stu-id="fdc36-196">Training dataset</span></span>

<span data-ttu-id="fdc36-197">AutoML 提供多載的實驗執行方法，讓您提供定型資料。</span><span class="sxs-lookup"><span data-stu-id="fdc36-197">AutoML provides an overloaded experiment execute method which allows you to provide training data.</span></span> <span data-ttu-id="fdc36-198">就內部而言，自動化的 ML 會將資料分成定型驗證分割。</span><span class="sxs-lookup"><span data-stu-id="fdc36-198">Internally, automated ML divides the data into train-validate splits.</span></span>

```csharp
experiment.Execute(trainDataView);
```

### <a name="custom-validation-dataset"></a><span data-ttu-id="fdc36-199">自訂驗證資料集</span><span class="sxs-lookup"><span data-stu-id="fdc36-199">Custom validation dataset</span></span>

<span data-ttu-id="fdc36-200">如不接受隨機分割，請使用自訂的驗證資料集，時間序列資料通常是這種情況。</span><span class="sxs-lookup"><span data-stu-id="fdc36-200">Use custom validation dataset if random split is not acceptable, as is usually the case with time series data.</span></span> <span data-ttu-id="fdc36-201">您可以指定自己的驗證資料集。</span><span class="sxs-lookup"><span data-stu-id="fdc36-201">You can specify your own validation dataset.</span></span> <span data-ttu-id="fdc36-202">針對指定的驗證資料集評估模型，而不是一或多個隨機資料集。</span><span class="sxs-lookup"><span data-stu-id="fdc36-202">The model will be evaluated against the validation dataset specified instead of one or more random datasets.</span></span>

```csharp
experiment.Execute(trainDataView, validationDataView);
```

## <a name="explore-model-metrics"></a><span data-ttu-id="fdc36-203">探索模型計量</span><span class="sxs-lookup"><span data-stu-id="fdc36-203">Explore model metrics</span></span>

<span data-ttu-id="fdc36-204">每次反覆運算 ML 實驗之後，會儲存與該工作相關的計量。</span><span class="sxs-lookup"><span data-stu-id="fdc36-204">After each iteration of an ML experiment, metrics relating to that task are stored.</span></span>

<span data-ttu-id="fdc36-205">例如，我們可以存取最佳回合的驗證計量：</span><span class="sxs-lookup"><span data-stu-id="fdc36-205">For example, we can access validation metrics from the best run:</span></span>

```csharp
RegressionMetrics metrics = experimentResult.BestRun.ValidationMetrics;
Console.WriteLine($"R-Squared: {metrics.RSquared:0.##}");
Console.WriteLine($"Root Mean Squared Error: {metrics.RootMeanSquaredError:0.##}");
```

<span data-ttu-id="fdc36-206">下列是每項 ML 工作的所有可用計量：</span><span class="sxs-lookup"><span data-stu-id="fdc36-206">The following are all the available metrics per ML task:</span></span>

* [<span data-ttu-id="fdc36-207">二元分類計量</span><span class="sxs-lookup"><span data-stu-id="fdc36-207">Binary classification metrics</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationMetric)
* [<span data-ttu-id="fdc36-208">多元分類計量</span><span class="sxs-lookup"><span data-stu-id="fdc36-208">Multiclass classification metrics</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric)
* [<span data-ttu-id="fdc36-209">回歸 & 建議計量</span><span class="sxs-lookup"><span data-stu-id="fdc36-209">Regression & recommendation metrics</span></span>](xref:Microsoft.ML.AutoML.RegressionMetric)

## <a name="see-also"></a><span data-ttu-id="fdc36-210">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fdc36-210">See also</span></span>

<span data-ttu-id="fdc36-211">如需完整的程式碼範例和更多範例，請瀏覽 GitHub 存放庫的 [ 範例](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state)。</span><span class="sxs-lookup"><span data-stu-id="fdc36-211">For full code samples and more visit the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) GitHub repository.</span></span>
