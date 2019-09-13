---
title: 什麼是 ML.NET，它如何運作？
description: 不論是在線上或是離線，ML.NET 都能讓您將機器學習新增至 .NET 應用程式。 使用此功能，您可以使用應用程式可用的資料來建立自動預測，而不需要連線至網路來使用 ML.NET。 本文說明 ML.NET 的機器學習基本概念。
ms.date: 08/26/2019
ms.topic: overview
ms.custom: mvc
ms.author: nakersha
author: natke
ms.openlocfilehash: d49a4bdfec133fe805bc9d534e04edf2f9ca5726
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929404"
---
# <a name="what-is-mlnet-and-how-does-it-work"></a>什麼是 ML.NET，它如何運作？

不論是在線上或是離線，ML.NET 都能讓您將機器學習新增至 .NET 應用程式。 使用此功能，您可以使用應用程式可用的資料來建立自動預測，而不需要連線至網路。 本文說明 ML.NET 的機器學習基本概念。 

您可使用 ML.NET 建立的預測類型範例包括：

|||
|-|-|
|分類/分類|自動將客戶的意見反應分成正負類別|
|迴歸/預測連續值|根據大小和位置預測房價|
|異常偵測|偵測詐騙的銀行交易 |
|建議|根據線上購物者之前的購買記錄，建議他們可能想要購買的產品|

## <a name="hello-mlnet-world"></a>Hello ML.NET World

下列程式碼片段中程式碼會示範最簡單的 ML.NET 應用程式。 此範例會建構線性迴歸模型，使用房子大小及價格資料來預測房價。 在實際的應用程式中，您的資料和模型會更複雜。

 ```csharp
    using System;
    using Microsoft.ML;
    using Microsoft.ML.Data;
    
    class Program
    {
        public class HouseData
        {
            public float Size { get; set; }
            public float Price { get; set; }
        }
    
        public class Prediction
        {
            [ColumnName("Score")]
            public float Price { get; set; }
        }
    
        static void Main(string[] args)
        {
            MLContext mlContext = new MLContext();
    
            // 1. Import or create training data
            HouseData[] houseData = {
                new HouseData() { Size = 1.1F, Price = 1.2F },
                new HouseData() { Size = 1.9F, Price = 2.3F },
                new HouseData() { Size = 2.8F, Price = 3.0F },
                new HouseData() { Size = 3.4F, Price = 3.7F } };
            IDataView trainingData = mlContext.Data.LoadFromEnumerable(houseData);

            // 2. Specify data preparation and model training pipeline
            var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
                .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));
    
            // 3. Train model
            var model = pipeline.Fit(trainingData);
    
            // 4. Make a prediction
            var size = new HouseData() { Size = 2.5F };
            var price = mlContext.Model.CreatePredictionEngine<HouseData, Prediction>(model).Predict(size);

            Console.WriteLine($"Predicted price for size: {size.Size*1000} sq ft= {price.Price*100:C}k");

            // Predicted price for size: 2500 sq ft= $261.98k
        }
    } 
```

## <a name="code-workflow"></a>程式碼工作流程

下圖代表應用程式程式碼結構，以及模型開發的反覆程序：

- 收集定型資料，並將其載入 **IDataView** 物件
- 指定擷取特性的作業管線並套用機器學習演算法
- 對管線呼叫 **Fit()** 以定型模型
- 評估模型並反覆運算來加以改善
- 將模型儲存成二進位格式，供應用程式使用
- 將模型載回至 **ITransformer** 物件
- 呼叫 **CreatePredictionEngine.Predict()** 以建立預測

![ML.NET 應用程式開發流程包括產生資料、開發管線、定型模型、評估模型和使用模型的元件](./media/mldotnet-annotated-workflow.png) 

讓我們稍微深入探討這些概念。

## <a name="machine-learning-model"></a>機器學習模型

ML.NET 模型是一個物件，包含要對輸入資料執行的轉換，以達成預測的輸出。

### <a name="basic"></a>基本

最基本的模型是二維線性迴歸，其中一個持續數量和另一個成正比，如上述的房價範例所示。 

![使用偏差和加權參數的線性迴歸模型](./media/linear-regression-model.svg)

此模型就只是：$Price = b + Size * w$。 參數 $b$ 和 $w$ 的評估方式是根據一組 (大小、價格) 對組來調整線條。 用來尋找模型參數的資料稱為**定型資料**。 機器學習模型的輸入稱為**特性**。 在本例中，$Size$ 是唯一的特性。 用來定型機器學習模型的實況資料稱為**標籤**。 在這裡，定型資料集的 $Price$ 值是標籤。

### <a name="more-complex"></a>更複雜

更複雜模型會使用交易的文字描述將財務交易分類成類別。

每條交易描述會移除多餘的字詞和字元，並計算字詞和字元組合，細分成一組特性。 以定型資料中的類別集為基礎，用特性集定型線性模型。 新描述與定型集中的描述愈相似，愈可能指派給同一分類。 

![文字分類模型](./media/text-classification-model.svg)

房價模型和文字分類模型都是**線性**模型。 根據資料本質以及要解決的問題本質，您也可以使用**決策樹**模型、**一般化累加**模型和其他模型。 您可以在[任務](./resources/tasks.md)中深入了解模型。

## <a name="data-preparation"></a>資料準備

在大部分的情況下，您所用的資料不適合直接用來定型機器學習模型。 未經處理資料需要經過準備或前置處理，才能用來尋找您模型的參數。 您的資料可能需要從字串值轉換成數值表示。 您的輸入資料中可能有多餘資訊。 您可能需要縮小或擴充您輸入資料的維度。 您的資料可能需要標準化或調整。

[ML.NET 教學課程](./tutorials/index.md)會教導您用於特定機器學習工作之文字、影像、數值和時間序列資料的不同資料處理管線。

[如何準備您的資料](./how-to-guides/prepare-data-ml-net.md)會示範如何更全面地套用資料準備。

您可以在＜資源＞一節中找到所有[可用轉換](./resources/transforms.md)的附錄。

## <a name="model-evaluation"></a>模型評估

定型模型之後，您怎麼知道它對未來的預測有多準？ 使用 ML.NET，您可以利用某些新的測試資料來評估模型。 

每種機器學習工作都有針對測試資料集，用來評估模型正確性和精確度的計量。

在房價範例中，我們使用了**迴歸**工作。 若要評估模型，請將下列程式碼新增至原始範例。

```csharp
        HouseData[] testHouseData =
        {
            new HouseData() { Size = 1.1F, Price = 0.98F },
            new HouseData() { Size = 1.9F, Price = 2.1F },
            new HouseData() { Size = 2.8F, Price = 2.9F },
            new HouseData() { Size = 3.4F, Price = 3.6F }
        };

        var testHouseDataView = mlContext.Data.LoadFromEnumerable(testHouseData);
        var testPriceDataView = model.Transform(testHouseDataView);
                
        var metrics = mlContext.Regression.Evaluate(testPriceDataView, labelColumnName: "Price");

        Console.WriteLine($"R^2: {metrics.RSquared:0.##}");
        Console.WriteLine($"RMS error: {metrics.RootMeanSquaredError:0.##}");

        // R^2: 0.96
        // RMS error: 0.19
```

評估計量會告訴您錯誤有點低，且預測輸出和測試輸出之間的關聯性很高。 很簡單！ 在實際範例中，需要更多微調才能達到良好的模型計量。

## <a name="mlnet-architecture"></a>ML.NET 架構

在本節中，我們要探討 ML.NET 的架構模式。 如果您是有經驗的 .NET 開發人員，對這些模式有些很熟悉，有些則較不熟悉。 跟上來一探究竟吧！

ML.NET 應用程式以 <xref:Microsoft.ML.MLContext> 物件開始。 此單一物件包含**目錄**。 目錄是資料載入儲存、轉換、定型器和模型作業元件的處理站。 每個目錄物件都有建立不同類型元件的方法：

|||||
|-|-|-|-|
|資料載入及儲存||<xref:Microsoft.ML.DataOperationsCatalog>||
|資料準備||<xref:Microsoft.ML.TransformsCatalog>||
|定型演算法|二元分類|<xref:Microsoft.ML.BinaryClassificationCatalog>||
||多元分類|<xref:Microsoft.ML.MulticlassClassificationCatalog>||
||異常偵測|<xref:Microsoft.ML.AnomalyDetectionCatalog>||
||群集|<xref:Microsoft.ML.ClusteringCatalog>||
||針對|<xref:Microsoft.ML.ForecastingCatalog>||
||排名|<xref:Microsoft.ML.RankingCatalog>||
||回復|<xref:Microsoft.ML.RegressionCatalog>||
||建議|<xref:Microsoft.ML.RecommendationCatalog>|新增 `Microsoft.ML.Recommender` NuGet 套件|
||TimeSeries|<xref:Microsoft.ML.TimeSeriesCatalog>|新增 `Microsoft.ML.TimeSeries` NuGet 套件|
|模型使用方式 ||<xref:Microsoft.ML.ModelOperationsCatalog>||

您可以巡覽至上述每個類別的建立方法。 使用 Visual Studio，會透過 IntelliSense 顯示目錄。

   ![適用於迴歸定型器的 Intellisense](./media/catalog-intellisense.png)

### <a name="build-the-pipeline"></a>建置管線

每個目錄中都是一組擴充方法。 讓我們看看如何使用擴充方法建立定型管線。

```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
        .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));
```

在程式碼片段中，`Concatenate` 和 `Sdca` 都是目錄中的方法。 它們會各自建立附加至管線的 [IEstimator](xref:Microsoft.ML.IEstimator%601) 物件。

此時，只會建立物件。 尚未開始執行。

### <a name="train-the-model"></a>將模型定型

管線中一旦建立物件，資料就可用來定型模型。

```csharp
    var model = pipeline.Fit(trainingData);
```

呼叫 `Fit()` 會使用輸入定型資料來評估模型的參數。 這就是定型模型。 請記住，上述的線性迴歸模型有兩個模型參數：**偏差**和**權數**。 呼叫 `Fit()` 之後，即已知參數值。 大部分模型的參數都比這個模型多。

您可以在[如何定型模型](./how-to-guides/train-machine-learning-model-ml-net.md)中深入了解模型定型

產生的模型物件會實作 <xref:Microsoft.ML.ITransformer> 介面。 亦即，模型會將輸入資料轉換成預測。

```csharp
   IDataView predictions = model.Transform(inputData);
```

### <a name="use-the-model"></a>使用模型

您可以將大量輸入資料或一次一筆輸入資料轉換成預測。 在房價範例中，我們兩種都做了：大量資料是用於評估模型，一次一筆資料則是為了建立新的預測。 讓我們看看建立單一預測。

```csharp
    var size = new HouseData() { Size = 2.5F };
    var predEngine = mlContext.CreatePredictionEngine<HouseData, Prediction>(model);
    var price = predEngine.Predict(size);
```
 
`CreatePredictionEngine()` 方法接受輸入類別和輸出類別。 欄位名稱及/或程式碼屬性決定模型定型和預測期間所用的資料行名稱。 您可以閱讀＜做法＞一節中的[如何建立單一預測](./how-to-guides/single-predict-model-ml-net.md)。

### <a name="data-models-and-schema"></a>資料模型和結構描述

ML.NET 機器學習管線的核心是 [DataView](xref:Microsoft.ML.IDataView) 物件。

管線中的每個轉換都有輸入結構描述 (轉換預期在其輸入中看到的資料名稱、類型和大小) 以及輸出結構描述 (轉換在轉換後產生的資料名稱、類型和大小)。 下列文件提供 [IDataView 介面及其型別系統](https://xadupre.github.io/machinelearningext/mlnetdocs/idataviewtypesystem.html)的深入說明。

如果管線中來自轉換之輸出結構描述不符合下一個轉換的輸入結構描述，則 ML.NET 會擲回例外狀況。

資料檢視物件具有資料行和資料列。 每個資料行都有名稱和類型以及長度。 例如：房價範例的輸入資料行為**大小**和**價格**。 它們都是類型，其數量為純量而非向量。

   ![具有房價預測資料的 ML.NET 資料檢視範例](./media/ml-net-dataview.png)

所有 ML.NET 演算法都在尋找向量的輸入資料行。 根據預設，此向量資料行稱為**特性**。 這就是為什麼我們要在房價範例中，把 [大小] 資料行串連到稱為 [特性]的新資料行。

 ```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
 ```

所有演算法也都會在執行預測之後，建立新的資料行。 這些新資料行的固定名稱取決於機器學習演算法類型。 若為迴歸工作，其中一個新資料行稱為 [分數]。 這就是為什麼我們要使用這個名稱作為價格資料的屬性。

```csharp
    public class Prediction
    {
        [ColumnName("Score")]
        public float Price { get; set; }
    }
```    

您可以在[機器學習工作](resources/tasks.md)指南中深入了解不同機器學習工作的輸出資料行。

DataView 物件的重要屬性是它們都**延遲**評估。 資料檢視只會在模型定型和評估期間以及資料預測期間載入及操作。 當您撰寫和測試 ML.NET 應用程式時，您可以呼叫 [Preview](xref:Microsoft.ML.DebuggerExtensions.Preview*) 方法，使用 Visual Studio 偵錯工具看一下任何資料檢視物件。

```csharp
    var debug = testPriceDataView.Preview();
```

您可以在偵錯工具中觀看 `debug` 變數，並檢查其內容。 請勿在實際程式碼中使用 Preview 方法，因為它會大幅降低效能。

### <a name="model-deployment"></a>模型部署

在實際的應用程式中，您的模型定型和評估程式碼與預測無關。 事實上，這兩項活動通常是由不同的小組執行。 您的模型開發小組可以儲存模型，供預測應用程式使用。

```csharp   
   mlContext.Model.Save(model, trainingData.Schema,"model.zip");
```

## <a name="where-to-now"></a>接下來去哪？

您可以在[教學課程](./tutorials/index.md)中了解如何使用不同機器學習工作搭配更實際的資料集來建置應用程式。

或者您可以在[操作指南](./how-to-guides/index.md)中深入了解特定的主題。

如果您很急切，您可以直接深入 [API 參考文件](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet)！
