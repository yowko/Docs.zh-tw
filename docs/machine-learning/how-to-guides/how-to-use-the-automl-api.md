---
title: 如何使用 ML.NET 自動化的 ML API
description: ML.NET 自動化的 ML API 會自動化模型建置程序，並產生隨時可供部署的模型。 了解您可用來設定自動化機器學習工作的選項。
ms.date: 04/24/2019
ms.custom: mvc,how-to
ms.openlocfilehash: bb1cd66e7341f2ada57d533d8b2dcbb48f08f726
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774557"
---
# <a name="how-to-use-the-mlnet-automated-machine-learning-api"></a><span data-ttu-id="01d56-104">如何使用 ML.NET 自動化的機器學習 API</span><span class="sxs-lookup"><span data-stu-id="01d56-104">How to use the ML.NET automated machine learning API</span></span>

<span data-ttu-id="01d56-105">自動化的機器學習 (AutoML) 會自動化將機器學習套用至資料的程序。</span><span class="sxs-lookup"><span data-stu-id="01d56-105">Automated machine learning (AutoML) automates the process of applying machine learning to data.</span></span> <span data-ttu-id="01d56-106">指定資料集，您可以執行 AutoML **實驗**來逐一查看不同的資料特徵化、機器學習演算法和超參數，以選取最佳的模型。</span><span class="sxs-lookup"><span data-stu-id="01d56-106">Given a dataset, you can run an AutoML **experiment** to iterate over different data featurizations, machine learning algorithms, and hyperparameters to select the best model.</span></span>

> [!NOTE]
> <span data-ttu-id="01d56-107">本主題是指 ML.NET 的自動化機器學習 API，目前為預覽版。</span><span class="sxs-lookup"><span data-stu-id="01d56-107">This topic refers to the automated machine learning API for ML.NET, which is currently in preview.</span></span> <span data-ttu-id="01d56-108">資料可能會有變更。</span><span class="sxs-lookup"><span data-stu-id="01d56-108">Material may be subject to change.</span></span>

## <a name="load-data"></a><span data-ttu-id="01d56-109">載入資料</span><span class="sxs-lookup"><span data-stu-id="01d56-109">Load data</span></span>

<span data-ttu-id="01d56-110">自動化的機器學習支援將資料集載入至 [IDataView](xref:Microsoft.ML.IDataView)。</span><span class="sxs-lookup"><span data-stu-id="01d56-110">Automated machine learning supports loading a dataset into an [IDataView](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="01d56-111">資料的格式可以是定位字元分隔值 (TSV) 檔案和逗號分隔值 (CSV) 檔案。</span><span class="sxs-lookup"><span data-stu-id="01d56-111">Data can be in the form of tab-separated value (TSV) files and comma separated value (CSV) files.</span></span>

<span data-ttu-id="01d56-112">範例：</span><span class="sxs-lookup"><span data-stu-id="01d56-112">Example:</span></span>

```csharp
using Microsoft.ML;
using Microsoft.ML.AutoML;
    // ...
    MLContext mlContext = new MLContext();
    IDataView trainDataView = mlContext.Data.LoadFromTextFile<SentimentIssue>("my-data-file.csv", hasHeader: true);
```

## <a name="select-the-machine-learning-task-type"></a><span data-ttu-id="01d56-113">選取機器學習工作類型</span><span class="sxs-lookup"><span data-stu-id="01d56-113">Select the machine learning task type</span></span>
<span data-ttu-id="01d56-114">建立實驗之前，請先決定您想要解決的機器學習問題種類。</span><span class="sxs-lookup"><span data-stu-id="01d56-114">Before creating an experiment, determine the kind of machine learning problem you want to solve.</span></span> <span data-ttu-id="01d56-115">自動化的機器學習支援下列 ML 工作：</span><span class="sxs-lookup"><span data-stu-id="01d56-115">Automated machine learning supports the following ML tasks:</span></span>

* <span data-ttu-id="01d56-116">二元分類</span><span class="sxs-lookup"><span data-stu-id="01d56-116">Binary Classification</span></span>
* <span data-ttu-id="01d56-117">多元分類</span><span class="sxs-lookup"><span data-stu-id="01d56-117">Multiclass Classification</span></span>
* <span data-ttu-id="01d56-118">回復</span><span class="sxs-lookup"><span data-stu-id="01d56-118">Regression</span></span>

## <a name="create-experiment-settings"></a><span data-ttu-id="01d56-119">建立實驗設定</span><span class="sxs-lookup"><span data-stu-id="01d56-119">Create experiment settings</span></span>

<span data-ttu-id="01d56-120">建立已決定 ML 工作類型的實驗設定：</span><span class="sxs-lookup"><span data-stu-id="01d56-120">Create experiment settings for the determined ML task type:</span></span>

* <span data-ttu-id="01d56-121">二元分類</span><span class="sxs-lookup"><span data-stu-id="01d56-121">Binary Classification</span></span>

  ```csharp
  var experimentSettings = new BinaryExperimentSettings();
  ```

* <span data-ttu-id="01d56-122">多元分類</span><span class="sxs-lookup"><span data-stu-id="01d56-122">Multiclass Classification</span></span>

  ```csharp
  var experimentSettings = new MulticlassExperimentSettings();
  ```

* <span data-ttu-id="01d56-123">回復</span><span class="sxs-lookup"><span data-stu-id="01d56-123">Regression</span></span>

  ```csharp
  var experimentSettings = new RegressionExperimentSettings();
  ```

## <a name="configure-experiment-settings"></a><span data-ttu-id="01d56-124">設定實驗設定</span><span class="sxs-lookup"><span data-stu-id="01d56-124">Configure experiment settings</span></span>

<span data-ttu-id="01d56-125">實驗的可設定程度很高。</span><span class="sxs-lookup"><span data-stu-id="01d56-125">Experiments are highly configurable.</span></span> <span data-ttu-id="01d56-126">如需組態設定的完整清單，請參閱 [AutoML API 文件](https://docs.microsoft.com/dotnet/api/?view=automl-dotnet)。</span><span class="sxs-lookup"><span data-stu-id="01d56-126">See the [AutoML API docs](https://docs.microsoft.com/dotnet/api/?view=automl-dotnet) for a full list of configuration settings.</span></span>

<span data-ttu-id="01d56-127">其中某些範例包括：</span><span class="sxs-lookup"><span data-stu-id="01d56-127">Some examples include:</span></span>

1. <span data-ttu-id="01d56-128">指定允許執行實驗的時間上限。</span><span class="sxs-lookup"><span data-stu-id="01d56-128">Specify the maximum time that the experiment is allowed to run.</span></span>

    ```csharp
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    ```

1. <span data-ttu-id="01d56-129">在排程完成前先使用取消權杖取消實驗。</span><span class="sxs-lookup"><span data-stu-id="01d56-129">Use a cancellation token to cancel the experiment before it is scheduled to finish.</span></span>

    ```csharp
    experimentSettings.CancellationToken = cts.Token;

    // Cancel experiment after the user presses any key
    CancelExperimentAfterAnyKeyPress(cts);
    ```

1. <span data-ttu-id="01d56-130">指定不同的最佳化計量。</span><span class="sxs-lookup"><span data-stu-id="01d56-130">Specify a different optimizing metric.</span></span>

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.OptimizingMetric = RegressionMetric.MeanSquaredError;
    ```

1. <span data-ttu-id="01d56-131">`CacheDirectory` 設定是目錄的指標，所有在 AutoML 工作期間定型的模型都儲存在此目錄。</span><span class="sxs-lookup"><span data-stu-id="01d56-131">The `CacheDirectory` setting is a pointer to a directory where all models trained during the AutoML task will be saved.</span></span> <span data-ttu-id="01d56-132">如果 `CacheDirectory` 設為 null，則模型會保留在記憶體中，而不是寫入磁碟。</span><span class="sxs-lookup"><span data-stu-id="01d56-132">If `CacheDirectory` is set to null, models will be kept in memory instead of written to disk.</span></span>

    ```csharp
    experimentSettings.CacheDirectory = null;
    ```

1. <span data-ttu-id="01d56-133">指示自動化的 ML 不要使用某些定型器。</span><span class="sxs-lookup"><span data-stu-id="01d56-133">Instruct automated ML not to use certain trainers.</span></span>

    <span data-ttu-id="01d56-134">依工作探索要最佳化之定型器的預設清單。</span><span class="sxs-lookup"><span data-stu-id="01d56-134">A default list of trainers to optimize are explored per task.</span></span> <span data-ttu-id="01d56-135">這份清單可針對每個實驗修改。</span><span class="sxs-lookup"><span data-stu-id="01d56-135">This list can be modified for each experiment.</span></span> <span data-ttu-id="01d56-136">例如，您可從清單移除對資料集執行緩慢的定型器。</span><span class="sxs-lookup"><span data-stu-id="01d56-136">For instance, trainers that run slowly on your dataset can be removed from the list.</span></span> <span data-ttu-id="01d56-137">若要最佳化一個特定的定型器，請呼叫 `experimentSettings.Trainers.Clear()`，然後新增您想要使用的定型器。</span><span class="sxs-lookup"><span data-stu-id="01d56-137">To optimize on one specific trainer call `experimentSettings.Trainers.Clear()`, then add the trainer that you want to use.</span></span>

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.Trainers.Remove(RegressionTrainer.LbfgsPoissonRegression);
    experimentSettings.Trainers.Remove(RegressionTrainer.OnlineGradientDescent);
    ```

<span data-ttu-id="01d56-138">依 ML 工作支援的定型器清單位在對應連結中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="01d56-138">The list of supported trainers per ML task can be found at the corresponding link below:</span></span>

* [<span data-ttu-id="01d56-139">支援的二元分類演算法</span><span class="sxs-lookup"><span data-stu-id="01d56-139">Supported Binary Classification Algorithms</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationTrainer)
* [<span data-ttu-id="01d56-140">支援的多元分類演算法</span><span class="sxs-lookup"><span data-stu-id="01d56-140">Supported Multiclass Classification Algorithms</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationTrainer)
* [<span data-ttu-id="01d56-141">支援的迴歸演算法</span><span class="sxs-lookup"><span data-stu-id="01d56-141">Supported Regression Algorithms</span></span>](xref:Microsoft.ML.AutoML.RegressionTrainer)

## <a name="optimizing-metric"></a><span data-ttu-id="01d56-142">最佳化計量</span><span class="sxs-lookup"><span data-stu-id="01d56-142">Optimizing metric</span></span>

<span data-ttu-id="01d56-143">最佳化度量，如上例所示，決定要在模型定型期間最佳化的計量。</span><span class="sxs-lookup"><span data-stu-id="01d56-143">The optimizing metric, as shown in the example above, determines the metric to be optimized during model training.</span></span> <span data-ttu-id="01d56-144">您可以選取的最佳化計量由您所選工作類型決定。</span><span class="sxs-lookup"><span data-stu-id="01d56-144">The optimizing metric you can select is determined by the task type you choose.</span></span> <span data-ttu-id="01d56-145">以下為可用計量的清單。</span><span class="sxs-lookup"><span data-stu-id="01d56-145">Below is a list of available metrics.</span></span>

|[<span data-ttu-id="01d56-146">二元分類</span><span class="sxs-lookup"><span data-stu-id="01d56-146">Binary Classification</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationMetric) | [<span data-ttu-id="01d56-147">多元分類</span><span class="sxs-lookup"><span data-stu-id="01d56-147">Multiclass Classification</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric) |[<span data-ttu-id="01d56-148">迴歸</span><span class="sxs-lookup"><span data-stu-id="01d56-148">Regression</span></span>](xref:Microsoft.ML.AutoML.RegressionMetric)
|-- |-- |--
|<span data-ttu-id="01d56-149">準確率</span><span class="sxs-lookup"><span data-stu-id="01d56-149">Accuracy</span></span>| <span data-ttu-id="01d56-150">LogLoss</span><span class="sxs-lookup"><span data-stu-id="01d56-150">LogLoss</span></span> | <span data-ttu-id="01d56-151">RSquared</span><span class="sxs-lookup"><span data-stu-id="01d56-151">RSquared</span></span>
|<span data-ttu-id="01d56-152">AreaUnderPrecisionRecallCurve</span><span class="sxs-lookup"><span data-stu-id="01d56-152">AreaUnderPrecisionRecallCurve</span></span> | <span data-ttu-id="01d56-153">LogLossReduction</span><span class="sxs-lookup"><span data-stu-id="01d56-153">LogLossReduction</span></span> | <span data-ttu-id="01d56-154">MeanAbsoluteError</span><span class="sxs-lookup"><span data-stu-id="01d56-154">MeanAbsoluteError</span></span>
|<span data-ttu-id="01d56-155">AreaUnderRocCurve</span><span class="sxs-lookup"><span data-stu-id="01d56-155">AreaUnderRocCurve</span></span> | <span data-ttu-id="01d56-156">MacroAccuracy</span><span class="sxs-lookup"><span data-stu-id="01d56-156">MacroAccuracy</span></span> | <span data-ttu-id="01d56-157">MeanSquaredError</span><span class="sxs-lookup"><span data-stu-id="01d56-157">MeanSquaredError</span></span>
|<span data-ttu-id="01d56-158">F1Score</span><span class="sxs-lookup"><span data-stu-id="01d56-158">F1Score</span></span> | <span data-ttu-id="01d56-159">MicroAccuracy</span><span class="sxs-lookup"><span data-stu-id="01d56-159">MicroAccuracy</span></span> | <span data-ttu-id="01d56-160">RootMeanSquaredError</span><span class="sxs-lookup"><span data-stu-id="01d56-160">RootMeanSquaredError</span></span>
|<span data-ttu-id="01d56-161">NegativePrecision</span><span class="sxs-lookup"><span data-stu-id="01d56-161">NegativePrecision</span></span> | <span data-ttu-id="01d56-162">TopKAccuracy</span><span class="sxs-lookup"><span data-stu-id="01d56-162">TopKAccuracy</span></span>
|<span data-ttu-id="01d56-163">NegativeRecall</span><span class="sxs-lookup"><span data-stu-id="01d56-163">NegativeRecall</span></span> |
|<span data-ttu-id="01d56-164">PositivePrecision</span><span class="sxs-lookup"><span data-stu-id="01d56-164">PositivePrecision</span></span>
|<span data-ttu-id="01d56-165">PositiveRecall</span><span class="sxs-lookup"><span data-stu-id="01d56-165">PositiveRecall</span></span>

## <a name="data-pre-processing-and-featurization"></a><span data-ttu-id="01d56-166">資料前置處理與特徵化</span><span class="sxs-lookup"><span data-stu-id="01d56-166">Data pre-processing and featurization</span></span>

> [!NOTE]
> <span data-ttu-id="01d56-167">[功能] 資料行僅支援 <xref:System.Boolean>、<xref:System.Single> 和 <xref:System.String> 的類型。</span><span class="sxs-lookup"><span data-stu-id="01d56-167">The feature column only supported types of <xref:System.Boolean>, <xref:System.Single>, and <xref:System.String>.</span></span>

<span data-ttu-id="01d56-168">根據預設，資料予以前置處理，並為您自動執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="01d56-168">Data pre-processing happens by default and the following steps are performed automatically for you:</span></span>

1. <span data-ttu-id="01d56-169">卸除無有用資訊的特性</span><span class="sxs-lookup"><span data-stu-id="01d56-169">Drop features with no useful information</span></span>

    <span data-ttu-id="01d56-170">從定型和驗證的集合中卸除無有用資訊的特性。</span><span class="sxs-lookup"><span data-stu-id="01d56-170">Drop features with no useful information from training and validation sets.</span></span> <span data-ttu-id="01d56-171">其中包括遺漏所有值、所有資料列值相同，或基數 (例如雜湊、識別碼或 GUID) 極高的特性。</span><span class="sxs-lookup"><span data-stu-id="01d56-171">These include features with all values missing, same value across all rows or with extremely high cardinality (e.g., hashes, IDs or GUIDs).</span></span>

1. <span data-ttu-id="01d56-172">遺漏值表示和插補</span><span class="sxs-lookup"><span data-stu-id="01d56-172">Missing value indication and imputation</span></span>

    <span data-ttu-id="01d56-173">以資料類型的預設值填入遺漏值資料格。</span><span class="sxs-lookup"><span data-stu-id="01d56-173">Fill missing value cells with the default value for the datatype.</span></span> <span data-ttu-id="01d56-174">以和輸入資料行相同的插槽數附加指標特性。</span><span class="sxs-lookup"><span data-stu-id="01d56-174">Append indicator features with the same number of slots as the input column.</span></span> <span data-ttu-id="01d56-175">如果輸入資料行中的值遺漏，則附加指標特性中的值是 `1`；否則為 `0`。</span><span class="sxs-lookup"><span data-stu-id="01d56-175">The value in the appended indicator features is `1` if the value in the input column is missing and `0` otherwise.</span></span>

1. <span data-ttu-id="01d56-176">產生其他特性</span><span class="sxs-lookup"><span data-stu-id="01d56-176">Generate additional features</span></span>

    <span data-ttu-id="01d56-177">針對文字功能：使用 unigrams 和三字元-克的字組功能。</span><span class="sxs-lookup"><span data-stu-id="01d56-177">For text features: Bag-of-word features using unigrams and tri-character-grams.</span></span>

    <span data-ttu-id="01d56-178">針對分類功能：適用于低基數功能的一種經常性編碼，以及高基數類別功能的一種熱雜湊編碼。</span><span class="sxs-lookup"><span data-stu-id="01d56-178">For categorical features: One-hot encoding for low cardinality features, and one-hot-hash encoding for high cardinality categorical features.</span></span>

1. <span data-ttu-id="01d56-179">轉換和編碼</span><span class="sxs-lookup"><span data-stu-id="01d56-179">Transformations and encodings</span></span>

    <span data-ttu-id="01d56-180">極少數唯一值轉換成類別特性的文字特性。</span><span class="sxs-lookup"><span data-stu-id="01d56-180">Text features with very few unique values transformed into categorical features.</span></span> <span data-ttu-id="01d56-181">視類別特性的基數而定，執行 One-Hot 編碼或 One-Hot 雜湊編碼。</span><span class="sxs-lookup"><span data-stu-id="01d56-181">Depending on cardinality of categorical features, perform one-hot encoding or one-hot hash encoding.</span></span>

## <a name="exit-criteria"></a><span data-ttu-id="01d56-182">允出準則</span><span class="sxs-lookup"><span data-stu-id="01d56-182">Exit criteria</span></span>

<span data-ttu-id="01d56-183">定義完成工作的準則：</span><span class="sxs-lookup"><span data-stu-id="01d56-183">Define the criteria to complete your task:</span></span>

1. <span data-ttu-id="01d56-184">在一段時間後結束 - 在您的實驗設定中使用 `MaxExperimentTimeInSeconds`，您可以定義工作應該繼續執行的秒數。</span><span class="sxs-lookup"><span data-stu-id="01d56-184">Exit after a length of time - Using `MaxExperimentTimeInSeconds` in your experiment settings you can define how long in seconds that an task should continue to run.</span></span>

1. <span data-ttu-id="01d56-185">於取消權杖處結束 - 您可以使用取消權杖，讓您在排程完成前取消工作。</span><span class="sxs-lookup"><span data-stu-id="01d56-185">Exit on a cancellation token -  You can use a cancellation token that lets you cancel the task before it is scheduled to finish.</span></span>

    ```csharp
    var cts = new CancellationTokenSource();
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    experimentSettings.CancellationToken = cts.Token;
    ```

## <a name="create-an-experiment"></a><span data-ttu-id="01d56-186">建立實驗</span><span class="sxs-lookup"><span data-stu-id="01d56-186">Create an experiment</span></span>

<span data-ttu-id="01d56-187">一旦設定了實驗設定，您就隨時可以建立實驗。</span><span class="sxs-lookup"><span data-stu-id="01d56-187">Once you have configured the experiment settings, you are ready to create the experiment.</span></span>

```csharp
RegressionExperiment experiment = mlContext.Auto().CreateRegressionExperiment(experimentSettings);
```

## <a name="run-the-experiment"></a><span data-ttu-id="01d56-188">執行實驗</span><span class="sxs-lookup"><span data-stu-id="01d56-188">Run the experiment</span></span>

<span data-ttu-id="01d56-189">執行實驗會觸發前置處理資料、選取學習演算法，以及微調超參數。</span><span class="sxs-lookup"><span data-stu-id="01d56-189">Running the experiment triggers data pre-processing, learning algorithm selection, and hyperparameter tuning.</span></span> <span data-ttu-id="01d56-190">AutoML 會繼續產生特徵化、學習演算法和超參數的組合，直到達到 `MaxExperimentTimeInSeconds` 或實驗終止。</span><span class="sxs-lookup"><span data-stu-id="01d56-190">AutoML will continue to generate combinations of featurization, learning algorithms, and hyperparameters until the `MaxExperimentTimeInSeconds` is reached or the experiment is terminated.</span></span>

```csharp
ExperimentResult<RegressionMetrics> experimentResult = experiment
    .Execute(trainingDataView, LabelColumnName, progressHandler: progressHandler);
```

<span data-ttu-id="01d56-191">如果您想要傳入驗證資料、指出資料行目的的資料行資訊或前置特徵化工具，請探索 `Execute()` 的其他多載。</span><span class="sxs-lookup"><span data-stu-id="01d56-191">Explore other overloads for `Execute()` if you want to pass in validation data, column information indicating the column purpose, or prefeaturizers.</span></span>

## <a name="training-modes"></a><span data-ttu-id="01d56-192">定型模式</span><span class="sxs-lookup"><span data-stu-id="01d56-192">Training modes</span></span>

### <a name="training-dataset"></a><span data-ttu-id="01d56-193">定型資料集</span><span class="sxs-lookup"><span data-stu-id="01d56-193">Training dataset</span></span>

<span data-ttu-id="01d56-194">AutoML 提供多載的實驗執行方法，讓您提供定型資料。</span><span class="sxs-lookup"><span data-stu-id="01d56-194">AutoML provides an overloaded experiment execute method which allows you to provide training data.</span></span> <span data-ttu-id="01d56-195">就內部而言，自動化的 ML 會將資料分成定型驗證分割。</span><span class="sxs-lookup"><span data-stu-id="01d56-195">Internally, automated ML divides the data into train-validate splits.</span></span>

```csharp
experiment.Execute(trainDataView);
```

### <a name="custom-validation-dataset"></a><span data-ttu-id="01d56-196">自訂的驗證資料集</span><span class="sxs-lookup"><span data-stu-id="01d56-196">Custom validation dataset</span></span>

<span data-ttu-id="01d56-197">如不接受隨機分割，請使用自訂的驗證資料集，時間序列資料通常是這種情況。</span><span class="sxs-lookup"><span data-stu-id="01d56-197">Use custom validation dataset if random split is not acceptable, as is usually the case with time series data.</span></span> <span data-ttu-id="01d56-198">您可以指定自己的驗證資料集。</span><span class="sxs-lookup"><span data-stu-id="01d56-198">You can specify your own validation dataset.</span></span> <span data-ttu-id="01d56-199">針對指定的驗證資料集評估模型，而不是一或多個隨機資料集。</span><span class="sxs-lookup"><span data-stu-id="01d56-199">The model will be evaluated against the validation dataset specified instead of one or more random datasets.</span></span>

```csharp
experiment.Execute(trainDataView, validationDataView);
```

## <a name="explore-model-metrics"></a><span data-ttu-id="01d56-200">探索模型計量</span><span class="sxs-lookup"><span data-stu-id="01d56-200">Explore model metrics</span></span>

<span data-ttu-id="01d56-201">每次反覆運算 ML 實驗之後，會儲存與該工作相關的計量。</span><span class="sxs-lookup"><span data-stu-id="01d56-201">After each iteration of an ML experiment, metrics relating to that task are stored.</span></span>

<span data-ttu-id="01d56-202">例如，我們可以存取最佳回合的驗證計量：</span><span class="sxs-lookup"><span data-stu-id="01d56-202">For example, we can access validation metrics from the best run:</span></span>

```csharp
RegressionMetrics metrics = experimentResult.BestRun.ValidationMetrics;
Console.WriteLine($"R-Squared: {metrics.RSquared:0.##}");
Console.WriteLine($"Root Mean Squared Error: {metrics.RootMeanSquaredError:0.##}");
```

<span data-ttu-id="01d56-203">下列是每項 ML 工作的所有可用計量：</span><span class="sxs-lookup"><span data-stu-id="01d56-203">The following are all the available metrics per ML task:</span></span>

* [<span data-ttu-id="01d56-204">二元分類計量</span><span class="sxs-lookup"><span data-stu-id="01d56-204">Binary classification metrics</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationMetric)
* [<span data-ttu-id="01d56-205">多元分類計量</span><span class="sxs-lookup"><span data-stu-id="01d56-205">Multiclass classification metrics</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric)
* [<span data-ttu-id="01d56-206">迴歸計量</span><span class="sxs-lookup"><span data-stu-id="01d56-206">Regression metrics</span></span>](xref:Microsoft.ML.AutoML.RegressionMetric)

## <a name="see-also"></a><span data-ttu-id="01d56-207">請參閱</span><span class="sxs-lookup"><span data-stu-id="01d56-207">See also</span></span>

<span data-ttu-id="01d56-208">如需完整的程式碼範例和更多範例，請瀏覽 GitHub 存放庫的 [ 範例](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state)。</span><span class="sxs-lookup"><span data-stu-id="01d56-208">For full code samples and more visit the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) GitHub repository.</span></span>
