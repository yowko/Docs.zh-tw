---
title: 定型及評估模型
description: 了解如何建置機器學習模型、收集計量，以及使用 ML.NET 測量效能。 機器學習模型會識別定型資料中的模式，以使用新資料進行預測。
ms.date: 08/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 0e0f43225b9bf243c31b3095817bdcbdb3123012
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "73976765"
---
# <a name="train-and-evaluate-a-model"></a>定型及評估模型

了解如何建置機器學習模型、收集計量，以及使用 ML.NET 測量效能。 雖然此範例訓練的是迴歸模型，但概念可適用於大多數的其他演算法。

## <a name="split-data-for-training-and-testing"></a>分割資料以進行定型和測試

機器學習模型的目標是識別定型資料中模式。 這些模式會用來使用新資料進行預測。

資料可由 `HousingData` 等類別建立模型。

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

給定載入到 的[`IDataView`](xref:Microsoft.ML.IDataView)以下資料。

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

使用[`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*)方法將資料拆分為訓練組和測試集。 結果將是一個包含[`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData)兩[`IDataView`](xref:Microsoft.ML.IDataView)個成員的物件，一個用於訓練集，另一個用於測試集。 資料分割百分比是由 `testFraction` 參數所決定。 以下程式碼片段會保留原始資料的 20% 作為測試集。

```csharp
DataOperationsCatalog.TrainTestData dataSplit = mlContext.Data.TrainTestSplit(data, testFraction: 0.2);
IDataView trainData = dataSplit.TrainSet;
IDataView testData = dataSplit.TestSet;
```

## <a name="prepare-the-data"></a>準備資料

資料需要進行預先處理，才能定型機器學習模型。 資料準備的詳細資訊可在[資料準備操作說明文章](prepare-data-ml-net.md)，以及 [`transforms page`](../resources/transforms.md) 中找到。

ML.NET 演算法針對輸入資料行類型具有條件約束。 此外，若沒有指定任何值，則會使用預設值作為輸入和輸出資料行名稱。

### <a name="working-with-expected-column-types"></a>使用預期的資料行類型

ML.NET 中的機器學習演算法預期收到大小已知浮動向量作為輸入。 當所有資料[`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute)都已採用數位格式且打算一起處理（即圖像圖元）時，將該屬性應用於資料模型。

如果資料不是全部數位，並且您希望在每個列上分別應用不同的資料轉換，則在處理了所有列後使用[`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*)方法將所有單個列合併為一個要素向量，該要素向量將輸出到新列。

下列程式碼片段會將 `Size` 和 `HistoricalPrices` 資料行合併成單一特徵向量，輸出到稱為 `Features` 的新資料行。 由於比例存在差異，[`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*)因此將應用於`Features`列以正常化資料。

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

### <a name="working-with-default-column-names"></a>使用預設資料行名稱

ML.NET 演算法會在沒有指定任何項目時使用預設資料行名稱。 所有訓練員都具有一個稱為 `featureColumnName` 的參數作為演算法的輸入，且當適用時，他們也會針對預期值擁有一個稱為 `labelColumnName` 的參數。 根據預設，這些值分別是 `Features` 和 `Label`。

通過在預處理[`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*)期間使用 方法創建稱為`Features`的新列，無需在演算法的參數中指定要素列名稱，因為它已存在於預處理中。 `IDataView` 標籤列`CurrentPrice`為 ，但由於屬性[`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute)在資料模型中使用，ML.NET重命名`CurrentPrice`列`Label`，從而不再需要向機器學習演算法估計器提供`labelColumnName`參數。

若您不想要使用預設資料行名稱，請在定義機器學習服務演算法估算時將特徵和標籤資料行的名稱作為參數傳遞，如接下來的程式碼片段所示：

```csharp
var UserDefinedColumnSdcaEstimator = mlContext.Regression.Trainers.Sdca(labelColumnName: "MyLabelColumnName", featureColumnName: "MyFeatureColumnName");
```

## <a name="train-the-machine-learning-model"></a>定型機器學習模型

預處理資料後，使用 該方法[`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*)使用[`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer)回歸演算法訓練機器學習模型。

```csharp
// Define StochasticDualCoordinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Build machine learning model
var trainedModel = sdcaEstimator.Fit(transformedTrainingData);
```

## <a name="extract-model-parameters"></a>擷取模型參數

模型經過培訓後，提取所學知識[`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601)進行檢查或再培訓。 [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters)提供訓練模型的偏置和學習係數或權重。

```csharp
var trainedModelParameters = trainedModel.Model as LinearRegressionModelParameters;
```

> [!NOTE]
> 其他模型也具有其工作限定的參數。 例如，[K-平均演算法](xref:Microsoft.ML.Trainers.KMeansTrainer)會根據距心將資料放入叢集，[`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) 則包含儲存這些所學習到距心的屬性。 要瞭解更多資訊，[`Microsoft.ML.Trainers`](xref:Microsoft.ML.Trainers)請訪問 API 文檔並查找包含`ModelParameters`其名稱中的類。

## <a name="evaluate-model-quality"></a>評估模型品質

若要協助選擇最佳的執行模型，評估其在測試資料上的效能非常重要。 使用[`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*)方法測量已訓練的模型的各種指標。

> [!NOTE]
> `Evaluate` 方法會根據執行的機器學習服務工作類型，產生不同的計量。 有關詳細資訊，請訪問[`Microsoft.ML.Data`API 文檔](xref:Microsoft.ML.Data)並查找包含`Metrics`其名稱中的類。

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

在先前的程式碼範例中：

1. 測試資料集已使用先前定義的資料準備轉換進行預先處理。
2. 定型後的機器學習模型會用來針對測試資料進行預測。
3. 在 `Evaluate` 方法中，測試資料集 `CurrentPrice` 資料行中的值會和新輸出預測的 `Score` 資料行比較，計算迴歸模型的計量，其中一個的決定係數儲存在 `rSquared` 變數中。

> [!NOTE]
> 在此小型範例中，由於資料的限制大小，決定係數是不介於 0 到 1 範圍內的數字。 在現實世界案例中，您應預期介於 0 和 1 之間的值。
