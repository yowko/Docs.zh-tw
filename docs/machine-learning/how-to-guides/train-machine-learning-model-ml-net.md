---
title: 定型和評估模型
description: 了解如何建置機器學習模型、擷取學習到的參數及使用 ML.NET 測量效能。 雖然此範例訓練的是迴歸模型，但概念可適用於大多數的其他演算法。
ms.date: 06/11/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0612
ms.openlocfilehash: d93353a3503ba67bde5fb61dc88f45d26e2f4306
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307449"
---
# <a name="train-and-evaluate-a-model"></a>定型和評估模型

了解如何建置機器學習模型、擷取學習到的參數及使用 ML.NET 測量效能。 雖然此範例訓練的是迴歸模型，但概念可適用於大多數的其他演算法。

## <a name="split-data-for-training-and-testing"></a>分割資料以進行定型和測試

機器學習模型的目標是識別定型資料中模式。 這些模式會用來使用新資料進行預測。

假設下列資料模型：

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

將資料載入 [`IDataView`](xref:Microsoft.ML.IDataView)：

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

使用 [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*) 方法將資料分割成定型及測試集。 其結果將會是一個 [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) 物件，其中包含兩個 [`IDataView`](xref:Microsoft.ML.IDataView) 成員，一個用於定型集，一個用於測試集。 資料分割百分比是由 `testFraction` 參數所決定。 以下程式碼片段會保留原始資料的 20% 作為測試集。

```csharp
DataOperationsCatalog.TrainTestData dataSplit = mlContext.Data.TrainTestSplit(data, testFraction: 0.2);
IDataView trainData = dataSplit.TrainSet;
IDataView testData = dataSplit.TestSet;
```

## <a name="prepare-the-data"></a>準備資料

資料需要進行預先處理，才能定型機器學習模型。 資料準備的詳細資訊可在[資料準備操作說明文章](prepare-data-ml-net.md)，以及 [`transforms page`](../resources/transforms.md) 中找到。

ML.NET 演算法針對輸入資料行類型具有條件約束。 此外，若沒有指定任何值，則會使用預設值作為輸入和輸出資料行名稱。

### <a name="working-with-expected-column-types"></a>使用預期的資料行類型

ML.NET 中的機器學習演算法預期收到大小已知浮動向量作為輸入。 當所有資料都已是數字格式，且可一起進行處理時 (例如影像像素)，請將 [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) 屬性套用到您的資料模型。 

若資料並非全部都是數字格式，且您希望為每個資料行個別套用不同的資料轉換時，請在所有資料行都已經過處理後使用 [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) 方法來將所有個別資料行合併成單一特徵向量，輸出到新資料行。 

下列程式碼片段會將 `Size` 和 `HistoricalPrices` 資料行合併成單一特徵向量，輸出到稱為 `Features` 的新資料行。 因為規模不同，[`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) 會套用到 `Features` 資料行以正常化資料。

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

透過在預先處理期間使用 [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) 方法來建立稱為 `Features` 的新資料行，便不需要在演算法的參數中指定特徵資料行名稱，因為它們已存在於預先處理的 `IDataView` 中。 標籤資料行是 `CurrentPrice`，但因為已在資料模型中使用 [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) 屬性，ML.NET 會將 `CurrentPrice` 資料行重新命名成 `Label`，使其不再需要提供 `labelColumnName` 參數給機器學習服務演算法的估算。 

若您不想要使用預設資料行名稱，請在定義機器學習服務演算法估算時將特徵和標籤資料行的名稱作為參數傳遞，如接下來的程式碼片段所示：

```csharp
var UserDefinedColumnSdcaEstimator = mlContext.Regression.Trainers.Sdca(labelColumnName: "MyLabelColumnName", featureColumnName: "MyFeatureColumnName");
```

## <a name="train-the-machine-learning-model"></a>定型機器學習模型

預先處理資料後，請使用 [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*) 方法來使用 [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) 迴歸演算法定型機器學習模型。

```csharp
// Define StochasticDualCoordinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Build machine learning model
var trainedModel = sdcaEstimator.Fit(transformedTrainingData);
```

## <a name="extract-model-parameters"></a>擷取模型參數

在定型模型後，請擷取學習到的 [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) 以進行檢查或重新定型。 [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) 可提供偏差和學習到的相關係數，或是定型模型的權數。 

```csharp
var trainedModelParameters = trainedModel.Model as LinearRegressionModelParameters;
```

> [!NOTE]
> 其他模型也具有其工作限定的參數。 例如，[K-平均演算法](xref:Microsoft.ML.Trainers.KMeansTrainer)會根據距心將資料放入叢集，[`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) 則包含儲存這些所學習到距心的屬性。 若要深入了解，請前往 [`Microsoft.ML.Trainers` API 文件](xref:Microsoft.ML.Trainers)並尋找其名稱中包含 `ModelParameters` 的類別。 

## <a name="evaluate-model-quality"></a>評估模型品質

若要協助選擇最佳的執行模型，評估其在測試資料上的效能非常重要。 請使用 [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) 方法來針對定型後的模型測量各種計量。

> [!NOTE]
> `Evaluate` 方法會根據執行的機器學習服務工作類型，產生不同的計量。 如需詳細資訊，請前往 [`Microsoft.ML.Data` API 文件](xref:Microsoft.ML.Data)並尋找其名稱中包含 `Metrics` 的類別。 

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
