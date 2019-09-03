---
title: 定型和評估模型
description: 了解如何建置機器學習模型、收集計量，以及使用 ML.NET 測量效能。 機器學習模型會識別定型資料中的模式，以使用新資料進行預測。
ms.date: 08/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 3fb586b218f1769949efc362cacc3957623dd43b
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169039"
---
# <a name="train-and-evaluate-a-model"></a><span data-ttu-id="0b335-104">定型和評估模型</span><span class="sxs-lookup"><span data-stu-id="0b335-104">Train and evaluate a model</span></span>

<span data-ttu-id="0b335-105">了解如何建置機器學習模型、收集計量，以及使用 ML.NET 測量效能。</span><span class="sxs-lookup"><span data-stu-id="0b335-105">Learn how to build machine learning models, collect metrics, and measure performance with ML.NET.</span></span> <span data-ttu-id="0b335-106">雖然此範例訓練的是迴歸模型，但概念可適用於大多數的其他演算法。</span><span class="sxs-lookup"><span data-stu-id="0b335-106">Although this sample trains a regression model, the concepts are applicable throughout a majority of the other algorithms.</span></span>

## <a name="split-data-for-training-and-testing"></a><span data-ttu-id="0b335-107">分割資料以進行定型和測試</span><span class="sxs-lookup"><span data-stu-id="0b335-107">Split data for training and testing</span></span>

<span data-ttu-id="0b335-108">機器學習模型的目標是識別定型資料中模式。</span><span class="sxs-lookup"><span data-stu-id="0b335-108">The goal of a machine learning model is to identify patterns within training data.</span></span> <span data-ttu-id="0b335-109">這些模式會用來使用新資料進行預測。</span><span class="sxs-lookup"><span data-stu-id="0b335-109">These patterns are used to make predictions using new data.</span></span>

<span data-ttu-id="0b335-110">資料可由 `HousingData` 等類別建立模型。</span><span class="sxs-lookup"><span data-stu-id="0b335-110">The data can be modeled by a class like `HousingData`.</span></span>

```csharp
public class HousingData
{
    [LoadColumn(0)]
    public float Size { get; set; }

    [LoadColumn(1, 3)]
    [VectorType(3)]
    public float[] HistoricalPrices { get; set; }

    [LoadColumn(4)]
    [ColumnName("Label")]
    public float CurrentPrice { get; set; }
}
```

<span data-ttu-id="0b335-111">假設下列資料已載入至 [`IDataView`](xref:Microsoft.ML.IDataView)。</span><span class="sxs-lookup"><span data-stu-id="0b335-111">Given the following data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

```csharp
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 600f,
        HistoricalPrices = new float[] { 100000f ,125000f ,122000f },
        CurrentPrice = 170000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 200000f, 250000f, 230000f },
        CurrentPrice = 225000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 126000f, 130000f, 200000f },
        CurrentPrice = 195000f
    },
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f,175000f,210000f },
        CurrentPrice = 205000f
    },
    new HousingData
    {
        Size = 900f,
        HistoricalPrices = new float[] { 155000f, 190000f, 220000f },
        CurrentPrice = 210000f
    },
    new HousingData
    {
        Size = 550f,
        HistoricalPrices = new float[] { 99000f, 98000f, 130000f },
        CurrentPrice = 180000f
    }
};
```

<span data-ttu-id="0b335-112">使用 [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*) 方法將資料分割成定型及測試集。</span><span class="sxs-lookup"><span data-stu-id="0b335-112">Use the [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*) method to split the data into train and test sets.</span></span> <span data-ttu-id="0b335-113">其結果將會是一個 [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) 物件，其中包含兩個 [`IDataView`](xref:Microsoft.ML.IDataView) 成員，一個用於定型集，一個用於測試集。</span><span class="sxs-lookup"><span data-stu-id="0b335-113">The result will be a [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) object which contains two [`IDataView`](xref:Microsoft.ML.IDataView) members, one for the train set and the other for the test set.</span></span> <span data-ttu-id="0b335-114">資料分割百分比是由 `testFraction` 參數所決定。</span><span class="sxs-lookup"><span data-stu-id="0b335-114">The data split percentage is determined by the `testFraction` parameter.</span></span> <span data-ttu-id="0b335-115">以下程式碼片段會保留原始資料的 20% 作為測試集。</span><span class="sxs-lookup"><span data-stu-id="0b335-115">The snippet below is holding out 20 percent of the original data for the test set.</span></span>

```csharp
DataOperationsCatalog.TrainTestData dataSplit = mlContext.Data.TrainTestSplit(data, testFraction: 0.2);
IDataView trainData = dataSplit.TrainSet;
IDataView testData = dataSplit.TestSet;
```

## <a name="prepare-the-data"></a><span data-ttu-id="0b335-116">準備資料</span><span class="sxs-lookup"><span data-stu-id="0b335-116">Prepare the data</span></span>

<span data-ttu-id="0b335-117">資料需要進行預先處理，才能定型機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="0b335-117">The data needs to be pre-processed before training a machine learning model.</span></span> <span data-ttu-id="0b335-118">資料準備的詳細資訊可在[資料準備操作說明文章](prepare-data-ml-net.md)，以及 [`transforms page`](../resources/transforms.md) 中找到。</span><span class="sxs-lookup"><span data-stu-id="0b335-118">More information on data preparation can be found on the [data prep how-to article](prepare-data-ml-net.md) as well as the [`transforms page`](../resources/transforms.md).</span></span>

<span data-ttu-id="0b335-119">ML.NET 演算法針對輸入資料行類型具有條件約束。</span><span class="sxs-lookup"><span data-stu-id="0b335-119">ML.NET algorithms have constraints on input column types.</span></span> <span data-ttu-id="0b335-120">此外，若沒有指定任何值，則會使用預設值作為輸入和輸出資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="0b335-120">Additionally, default values are used for input and output column names when no values are specified.</span></span>

### <a name="working-with-expected-column-types"></a><span data-ttu-id="0b335-121">使用預期的資料行類型</span><span class="sxs-lookup"><span data-stu-id="0b335-121">Working with expected column types</span></span>

<span data-ttu-id="0b335-122">ML.NET 中的機器學習演算法預期收到大小已知浮動向量作為輸入。</span><span class="sxs-lookup"><span data-stu-id="0b335-122">The machine learning algorithms in ML.NET expect a float vector of known size as input.</span></span> <span data-ttu-id="0b335-123">當所有資料都已是數字格式，且可一起進行處理時 (例如影像像素)，請將 [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) 屬性套用到您的資料模型。</span><span class="sxs-lookup"><span data-stu-id="0b335-123">Apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to your data model when all of the data is already in numerical format and is intended to be processed together (i.e. image pixels).</span></span> 

<span data-ttu-id="0b335-124">若資料並非全部都是數字格式，且您希望為每個資料行個別套用不同的資料轉換時，請在所有資料行都已經過處理後使用 [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) 方法來將所有個別資料行合併成單一特徵向量，輸出到新資料行。</span><span class="sxs-lookup"><span data-stu-id="0b335-124">If data is not all numerical and you want to apply different data transformations on each of the columns individually, use the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) method after all of the columns have been processed to combine all of the individual columns into a single feature vector that is output to a new column.</span></span> 

<span data-ttu-id="0b335-125">下列程式碼片段會將 `Size` 和 `HistoricalPrices` 資料行合併成單一特徵向量，輸出到稱為 `Features` 的新資料行。</span><span class="sxs-lookup"><span data-stu-id="0b335-125">The following snippet combines the `Size` and `HistoricalPrices` columns into a single feature vector that is output to a new column called `Features`.</span></span> <span data-ttu-id="0b335-126">因為規模不同，[`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) 會套用到 `Features` 資料行以正常化資料。</span><span class="sxs-lookup"><span data-stu-id="0b335-126">Because there is a difference in scales, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) is applied to the `Features` column to normalize the data.</span></span>

```csharp
// Define Data Prep Estimator
// 1. Concatenate Size and Historical into a single feature vector output to a new column called Features
// 2. Normalize Features vector
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", "Size", "HistoricalPrices")
        .Append(mlContext.Transforms.NormalizeMinMax("Features"));

// Create data prep transformer
ITransformer dataPrepTransformer = dataPrepEstimator.Fit(trainData);

// Apply transforms to training data
IDataView transformedTrainingData = dataPrepTransformer.Transform(trainData);
```

### <a name="working-with-default-column-names"></a><span data-ttu-id="0b335-127">使用預設資料行名稱</span><span class="sxs-lookup"><span data-stu-id="0b335-127">Working with default column names</span></span>

<span data-ttu-id="0b335-128">ML.NET 演算法會在沒有指定任何項目時使用預設資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="0b335-128">ML.NET algorithms use default column names when none are specified.</span></span> <span data-ttu-id="0b335-129">所有訓練員都具有一個稱為 `featureColumnName` 的參數作為演算法的輸入，且當適用時，他們也會針對預期值擁有一個稱為 `labelColumnName` 的參數。</span><span class="sxs-lookup"><span data-stu-id="0b335-129">All trainers have a parameter called `featureColumnName` for the inputs of the algorithm and when applicable they also have a parameter for the expected value called `labelColumnName`.</span></span> <span data-ttu-id="0b335-130">根據預設，這些值分別是 `Features` 和 `Label`。</span><span class="sxs-lookup"><span data-stu-id="0b335-130">By default those values are `Features` and `Label` respectively.</span></span> 

<span data-ttu-id="0b335-131">透過在預先處理期間使用 [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) 方法來建立稱為 `Features` 的新資料行，便不需要在演算法的參數中指定特徵資料行名稱，因為它們已存在於預先處理的 `IDataView` 中。</span><span class="sxs-lookup"><span data-stu-id="0b335-131">By using the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) method during pre-processing to create a new column called `Features`, there is no need to specify the feature column name in the parameters of the algorithm since it already exists in the pre-processed `IDataView`.</span></span> <span data-ttu-id="0b335-132">標籤資料行是 `CurrentPrice`，但因為已在資料模型中使用 [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) 屬性，ML.NET 會將 `CurrentPrice` 資料行重新命名成 `Label`，使其不再需要提供 `labelColumnName` 參數給機器學習服務演算法的估算。</span><span class="sxs-lookup"><span data-stu-id="0b335-132">The label column is `CurrentPrice`, but since the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute is used in the data model, ML.NET renames the `CurrentPrice` column to `Label` which removes the need to provide the `labelColumnName` parameter to the machine learning algorithm estimator.</span></span> 

<span data-ttu-id="0b335-133">若您不想要使用預設資料行名稱，請在定義機器學習服務演算法估算時將特徵和標籤資料行的名稱作為參數傳遞，如接下來的程式碼片段所示：</span><span class="sxs-lookup"><span data-stu-id="0b335-133">If you don't want to use the default column names, pass in the names of the feature and label columns as parameters when defining the machine learning algorithm estimator as demonstrated by the subsequent snippet:</span></span>

```csharp
var UserDefinedColumnSdcaEstimator = mlContext.Regression.Trainers.Sdca(labelColumnName: "MyLabelColumnName", featureColumnName: "MyFeatureColumnName");
```

## <a name="train-the-machine-learning-model"></a><span data-ttu-id="0b335-134">定型機器學習模型</span><span class="sxs-lookup"><span data-stu-id="0b335-134">Train the machine learning model</span></span>

<span data-ttu-id="0b335-135">預先處理資料後，請使用 [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*) 方法來使用 [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) 迴歸演算法定型機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="0b335-135">Once the data is pre-processed, use the [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*) method to train the machine learning model with the [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) regression algorithm.</span></span>

```csharp
// Define StochasticDualCoordinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Build machine learning model
var trainedModel = sdcaEstimator.Fit(transformedTrainingData);
```

## <a name="extract-model-parameters"></a><span data-ttu-id="0b335-136">擷取模型參數</span><span class="sxs-lookup"><span data-stu-id="0b335-136">Extract model parameters</span></span>

<span data-ttu-id="0b335-137">在定型模型後，請擷取學習到的 [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) 以進行檢查或重新定型。</span><span class="sxs-lookup"><span data-stu-id="0b335-137">After the model has been trained, extract the learned [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) for inspection or re-training.</span></span> <span data-ttu-id="0b335-138">[`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) 可提供偏差和學習到的相關係數，或是定型模型的權數。</span><span class="sxs-lookup"><span data-stu-id="0b335-138">The [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) provide the bias and learned coefficients or weights of the trained model.</span></span> 

```csharp
var trainedModelParameters = trainedModel.Model as LinearRegressionModelParameters;
```

> [!NOTE]
> <span data-ttu-id="0b335-139">其他模型也具有其工作限定的參數。</span><span class="sxs-lookup"><span data-stu-id="0b335-139">Other models have parameters that are specific to their tasks.</span></span> <span data-ttu-id="0b335-140">例如，[K-平均演算法](xref:Microsoft.ML.Trainers.KMeansTrainer)會根據距心將資料放入叢集，[`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) 則包含儲存這些所學習到距心的屬性。</span><span class="sxs-lookup"><span data-stu-id="0b335-140">For example, the [K-Means algorithm](xref:Microsoft.ML.Trainers.KMeansTrainer) puts data into cluster based on centroids and the [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) contains a property that stores these learned centroids.</span></span> <span data-ttu-id="0b335-141">若要深入了解，請前往 [`Microsoft.ML.Trainers` API 文件](xref:Microsoft.ML.Trainers)並尋找其名稱中包含 `ModelParameters` 的類別。</span><span class="sxs-lookup"><span data-stu-id="0b335-141">To learn more, visit the [`Microsoft.ML.Trainers` API Documentation](xref:Microsoft.ML.Trainers) and look for classes that contain `ModelParameters` in their name.</span></span> 

## <a name="evaluate-model-quality"></a><span data-ttu-id="0b335-142">評估模型品質</span><span class="sxs-lookup"><span data-stu-id="0b335-142">Evaluate model quality</span></span>

<span data-ttu-id="0b335-143">若要協助選擇最佳的執行模型，評估其在測試資料上的效能非常重要。</span><span class="sxs-lookup"><span data-stu-id="0b335-143">To help choose the best performing model, it is essential to evaluate its performance on test data.</span></span> <span data-ttu-id="0b335-144">請使用 [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) 方法來針對定型後的模型測量各種計量。</span><span class="sxs-lookup"><span data-stu-id="0b335-144">Use the [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) method, to measure various metrics for the trained model.</span></span>

> [!NOTE]
> <span data-ttu-id="0b335-145">`Evaluate` 方法會根據執行的機器學習服務工作類型，產生不同的計量。</span><span class="sxs-lookup"><span data-stu-id="0b335-145">The `Evaluate` method produces different metrics depending on which machine learning task was performed.</span></span> <span data-ttu-id="0b335-146">如需詳細資訊，請前往 [`Microsoft.ML.Data` API 文件](xref:Microsoft.ML.Data)並尋找其名稱中包含 `Metrics` 的類別。</span><span class="sxs-lookup"><span data-stu-id="0b335-146">For more details, visit the [`Microsoft.ML.Data` API Documentation](xref:Microsoft.ML.Data) and look for classes that contain `Metrics` in their name.</span></span> 

```csharp
// Measure trained model performance
// Apply data prep transformer to test data
IDataView transformedTestData = dataPrepTransformer.Transform(testData);

// Use trained model to make inferences on test data
IDataView testDataPredictions = trainedModel.Transform(transformedTestData);

// Extract model metrics and get RSquared
RegressionMetrics trainedModelMetrics = mlContext.Regression.Evaluate(testDataPredictions);
double rSquared = trainedModelMetrics.RSquared;
```

<span data-ttu-id="0b335-147">在先前的程式碼範例中：</span><span class="sxs-lookup"><span data-stu-id="0b335-147">In the previous code sample:</span></span>  
1. <span data-ttu-id="0b335-148">測試資料集已使用先前定義的資料準備轉換進行預先處理。</span><span class="sxs-lookup"><span data-stu-id="0b335-148">Test data set is pre-processed using the data preparation transforms previously defined.</span></span> 
2. <span data-ttu-id="0b335-149">定型後的機器學習模型會用來針對測試資料進行預測。</span><span class="sxs-lookup"><span data-stu-id="0b335-149">The trained machine learning model is used to make predictions on the test data.</span></span>
3. <span data-ttu-id="0b335-150">在 `Evaluate` 方法中，測試資料集 `CurrentPrice` 資料行中的值會和新輸出預測的 `Score` 資料行比較，計算迴歸模型的計量，其中一個的決定係數儲存在 `rSquared` 變數中。</span><span class="sxs-lookup"><span data-stu-id="0b335-150">In the `Evaluate` method, the values in the `CurrentPrice` column of the test data set are compared against the `Score` column of the newly output predictions to calculate the metrics for the regression model, one of which, R-Squared is stored in the `rSquared` variable.</span></span>

> [!NOTE]
> <span data-ttu-id="0b335-151">在此小型範例中，由於資料的限制大小，決定係數是不介於 0 到 1 範圍內的數字。</span><span class="sxs-lookup"><span data-stu-id="0b335-151">In this small example, the R-Squared is a number not in the range of 0-1 because of the limited size of the data.</span></span> <span data-ttu-id="0b335-152">在現實世界案例中，您應預期介於 0 和 1 之間的值。</span><span class="sxs-lookup"><span data-stu-id="0b335-152">In a real-world scenario, you should expect to see a value between 0 and 1.</span></span>
