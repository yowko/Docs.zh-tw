---
title: ML.NET 模型定型的基本概念
description: 本文章說明的基本概念涵蓋 ML.NET 中的*模型定型*情節。 並非所有概念都與*使用現有模型進行預測*的更簡單情節相關。
ms.date: 02/13/2019
ms.topic: overview
ms.custom: mvc
ms.openlocfilehash: c47d5832527dca1416abfc55756dca48f1daf493
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2019
ms.locfileid: "56303656"
---
# <a name="basic-concepts-for-model-training-in-mlnet"></a>ML.NET 模型定型的基本概念

本文章說明的基本概念涵蓋 ML.NET 中的*模型定型*情節。 並非所有概念都與「使用現有模型進行預測」的更簡單案例相關。

## <a name="model-training-concepts"></a>模型定型概念

本文件涵蓋下列與 ML.NET 模型定型相關的概念：

- [*資料*](#data)，以 `IDataView` 介面表示。
  - 在 ML.NET 中，資料相當於 SQL 檢視：它是延遲評估、不可變、可支援資料指標、異質性、結構描述化的資料集。 
  - 有關資料介面的絕佳文件是 [IDataView 設計原則](https://github.com/dotnet/machinelearning/blob/master/docs/code/IDataViewDesignPrinciples.md)。
- [*轉換器* ](#transformer)，以 `ITransformer` 介面表示。
  - 轉換器是一種元件，其會取得資料、對其執行一些運作，並傳回新的轉換資料。
  - 例如，您可以將機器學習模型視為取得功能並傳回預測的轉換器。
  - 另一個範例是文字權杖化工具，其會取得單一文字資料行，並輸出向量資料行，其中具有從文字中擷取的個別文字。
- [*資料讀取器*](#data-reader)，以 `IDataReader<T>` 介面表示。
  - 資料讀取器是用來建立資料的 ML.NET 元件。 它會取得 `T` 的執行個體，並傳回其中資料。 
  - 例如，*TextLoader* 是 `IDataReader<IMultiStreamSource>`。 它會取得來源並產生資料。 
- [*評估工具*](#estimator)，以 `IEstimator<T>` 介面表示。
  - 這是從資料學習的物件。 學習的結果是*轉換器*。
  - 您可以將機器學習*演算法*視為評估工具，其會根據資料學習，並產生機器學習*模型*。
- [*預測函數*](#prediction-function)，以 `PredictionEngine<TSrc, TDst>` 類別表示。
  - 預測函數可以視為將轉換器套用至某個資料列 (例如預測時間) 的機器。

## <a name="data"></a>資料

在 ML.NET 中，資料相當於 SQL 檢視：它是延遲評估、可支援資料指標、異質性、結構描述化的資料集。

- 它具有*結構描述* (`ISchema` 介面的執行個體)，其中包含資料檢視資料行的相關資訊。
  - 每個資料行都有*名稱*、*類型*，以及任意一組與其相關聯的*中繼資料*。
  - 資料行的*中繼資料*包含像是向量資料行的插槽名稱這類資訊。 中繼資料本身是以另一個一列*資料*表示，此資料對於每個資料行都是唯一的。
  - 資料檢視是*資料指標*的來源。 想想 SQL 資料指標：資料指標是一種物件，其會逐一查看資料，一次一個資料列，並呈現可用資料。
  - 當然，資料可以視需要具有多個作用中的資料指標。 由於資料本身不可變，因此資料指標是真正獨立的。
  - 資料指標通常只會存取資料行子集：為了提高效率，ML.NET 只會計算資料指標所需的資料行值。

## <a name="transformer"></a>轉換器

轉換器是一種元件，其會取得資料、對其執行一些運作，並傳回新的轉換資料。

ML.NET 中大部分的轉換器傾向於一次操作一個*輸入資料行*，以及產生*輸出資料行*。 例如，`new HashTransformer("bar", "foo")` 會從資料行 "foo" 取得值、將其雜湊，並將它們放入資料行 "bar" 中。 

輸入和輸出資料行名稱相同也是很常見的。 在此情況下，舊資料行會取代為新資料行。 例如，`new HashTransformer("foo")` 會從資料行 "foo" 取得值、將其雜湊，並將它們放回資料行 "foo" 中。 

在呼叫 `Transform` 時，任何轉換器都會產生新的資料檢視。 請記住，資料檢視是不可變的。

另一個重要考量是，因為資料會延遲評估，所以*轉換器也會延遲執行*。 基本上，在您呼叫之後

```csharp
var newData = transformer.Transform(oldData)
```

沒有實際計算發生。 只有在您從 `newData` 取得資料指標，並開始使用值之後，`newData` 才會叫用 `transformer` 轉換邏輯 (即使如此，只會在需要問題中的 `transformer` 時，才會發生此情況，以產生所要求的資料行)。

### <a name="transformer-chains"></a>轉換器鏈結

轉換器有個很有用的屬性，「您可以將轉換器的循序應用程式建置為另一個轉換器」：

```csharp
var fullTransformer = transformer1.Append(transformer2).Append(transformer3);
```

此屬性常用於 ML.NET：通常，定型的 ML.NET 模型是轉換器的鏈結，亦即，基於所有意圖和目的，視為一個*轉換器*。

## <a name="data-reader"></a>資料讀取器

資料讀取器是用來「建立」資料的 ML.NET 元件：它會取得 `T` 的執行個體，並傳回其中資料。

需要注意的有趣屬性是，您可以將轉換器附加至現有的資料讀取器來建立資料讀取器。 如此一來，您可以具有轉換行為加入其中的讀取器：

```csharp
var newReader = reader.Append(transformer1).Append(transformer2)
```

轉換器的另一個類似之處是，因為資料會延遲評估，所以*讀取器會延遲執行*：呼叫 `reader.Read()` 時，沒有 (或最少) 實際「讀取」發生：僅在產生的資料要求資料指標時，讀取器才會開始運作。

## <a name="estimator"></a>評估工具

*評估工具*是從資料學習的物件。 學習的結果是*轉換器*。

在 ML.NET 中，使用此屬性來建立學習管線，將不同的評估工具鏈結在一起：

```csharp
MLContext mlContext = new MLContext(seed: 0);

var pipeline = mlContext.Transforms.CopyColumns("Label","FareAmount")
    .Append(mlContext.Transforms.Categorical.OneHotEncoding("VendorId"))
    .Append(mlContext.Transforms.Categorical.OneHotEncoding("RateCode"))
    .Append(mlContext.Transforms.Categorical.OneHotEncoding("PaymentType"))
    .Append(mlContext.Transforms.Concatenate("Features","VendorId","RateCode","PassengerCount","TripTime","TripDistance","PaymentType"))
    .Append(mlContext.Regression.Trainers.FastTree("Label","Features"));

var model = pipeline.Fit(dataView);
```

評估工具的一個重要屬性是，*評估工具是積極的，而不會延遲*：每次呼叫 `Fit` 都會導致學習發生，這可能是耗時作業。

## <a name="prediction-function"></a>預測函數

預測函式可以視為將轉換器套用至某個資料列的元件。

一旦您取得模型 (透過 `Fit()` 定型或從某處載入的 *轉換器*)，就可以使用它，正常呼叫 `model.Transform(data)` 來進行預測。 不過，當您在真實情節中使用此模型時，通常沒有很多範例做為預測依據。 反之，您一次有一個範例，因此您需要立即對它們做出及時預測。

當然，您可以將此縮小為批次預測：

- 建立只有一個資料列的資料檢視。
- 呼叫 `model.Transform(data)` 來取得預測的資料檢視。
- 透過產生的資料取得資料指標。
- 將資料指標前進一步，以到達第一個 (且唯一的) 資料列。
- 從中擷取預測值。

實作上述演算法的方法為，使用[結構描述理解](https://github.com/dotnet/machinelearning/blob/master/docs/code/SchemaComprehension.md)與兩個使用者定義的物件 `InputExample` 和 `OutputPrediction` 搭配，如下所示：

```csharp
var inputData = mlContext.Data.ReadFromEnumerable(new InputExample[] { example });
var outputData = model.Transform(inputData);
var output = mlContext.CreateEnumerable<OutputPrediction>(outputData,reuseRowObject:false).First();
```

但這樣做很麻煩，且會產生效能成本。 反之，預測函數物件可透過擴充方法 `CreatePredictionEngine` 執行相同工作，但更快速且更方便：

```csharp
var predictionEngine = model.CreatePredictionEngine<InputExample,OutputPrediction>(mlContext);
var prediction = predictionEngine.Predict(example);
```

預測函數是*不可重入的/安全執行緒*。 如果您想要同時使用多個執行緒進行預測，則需要每個執行緒具有一個預測函數。
