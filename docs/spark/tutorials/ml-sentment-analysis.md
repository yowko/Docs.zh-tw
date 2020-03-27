---
title: 情緒分析與 .NET 的 Apache Spark 和ML.NET教程
description: 在本教程中，您將學習如何將 ML.NET與 .NET 一起用於 Apache Spark 進行情緒分析。
author: mamccrea
ms.author: mamccrea
ms.date: 03/25/2019
ms.topic: tutorial
ms.openlocfilehash: cdd1214c26a5d5a4b159df3a396ec6f36b9fc0dd
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345338"
---
# <a name="tutorial-sentiment-analysis-with-net-for-apache-spark-and-mlnet"></a>教程：使用 .NET 進行情緒分析，用於 Apache Spark 和ML.NET

本教程教您如何使用ML.NET和 .NET 進行 Apache Spark 的線上評論情緒分析。 [ML.NET](http://dot.net/ml)是一個免費的跨平臺、開源機器學習框架。 您可以使用 ML.NET 與 .NET 的 Apache Spark 一起擴展機器學習演算法的訓練和預測。

在本教學課程中，您會了解如何：

> [!div class="checklist"]
>
> * 在視覺化工作室中使用ML.NET模型產生器創建情緒分析模型。
> * 為 Apache Spark 主控台應用創建 .NET。
> * 編寫並實現使用者定義的函數。
> * 為 Apache Spark 主控台應用運行 .NET。

## <a name="prerequisites"></a>Prerequisites

* 如果您以前沒有為 Apache Spark 應用程式開發 .NET，請從[入門教程](get-started.md)開始熟悉基礎知識。 在繼續本教程之前，請完成入門教程的所有先決條件。

* 本教程使用ML.NET模型產生器（預覽），視覺化工作室中提供的視覺介面。 如果您還沒有 Visual Studio，您可以免費[下載視覺工作室的社區版本](https://visualstudio.microsoft.com/downloads/)。

* [下載並安裝](https://marketplace.visualstudio.com/items?itemName=MLNET.07)ML.NET模型產生器（預覽）。

* 下載[yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv)和[yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) Yelp 審核資料集。

## <a name="review-the-data"></a>檢閱資料

Yelp 評論資料集包含有關各種服務的線上 Yelp 評論。 打開[yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv)並注意資料的結構。 第一列包含審閱文本，第二列包含情緒分數。 如果情緒評分為 1，則審核為正值，如果情緒評分為 0，則審核為負數。

下表包含示例資料：

|評論文本|情感|
|-|-|
|哇。。。喜歡這個地方|    1|
|不夠酥脆。|    0|

## <a name="build-your-machine-learning-model"></a>構建機器學習模型

1. 打開視覺化工作室並創建新的 C# 主控台應用程式 （.NET 核心）。 命名專案*MLSparkModel。*

1. 在**解決方案資源管理器中**，按右鍵*MLSparkModel*專案。 然後選擇 **"添加>機器學習**"。

1. 在模型產生器ML.NET，選擇**情緒分析**方案磁貼。

1. 在 **"添加資料"** 頁上，上載*yelptrain.csv*資料集。

1. 從"列 *"中選擇"情緒"***以預測**下拉清單。

1. 在 **"火車"** 頁上，將訓練時間設置為*60 秒*，然後選擇 **"開始訓練**"。 請注意"**進度**"下的培訓狀態。

1. 模型產生器完成培訓後，**評估**培訓結果。 您可以在下面的文字方塊中鍵入短語 **"嘗試模型****"，然後選擇"預測"** 以查看輸出。

1. 選擇 **"代碼"，** 然後選擇 **"添加專案**"以將 ML 模型添加到解決方案。

1. 請注意，您的解決方案中添加了兩個專案 **：MLSparkModelML.ConsoleApp**和**MLSparkModelML.Model.Model.Model.**

1. 按兩下*您的 MLSpark* C++ 專案，並注意到添加了以下專案參考。

   ```xml
   <ItemGroup>
       <ProjectReference Include="..\MLSparkModelML.Model\MLSparkModelML.Model.csproj" />
   </ItemGroup>
   ```

## <a name="create-a-console-app"></a>建立主控台應用程式

模型產生器為您創建一個主控台應用。

1. 按右鍵解決方案資源管理器中的**MLSparkModelML.主控台**，然後選擇 **"管理 NuGet 包**"。

1. 搜索**Microsoft.Spark**並安裝套裝軟體。 模型產生器會自動為您安裝**Microsoft.ML。**

### <a name="create-a-sparksession"></a>創建火花會話

1. 打開**MLSparkModelML.ConsoleApp**的*Program.cs*檔。 此檔由模型產生器自動生成。 刪除語句`using`、Main（） 方法的內容以及`CreateSingleDataSample`區域。

1. 將以下附加`using`語句添加到*Program.cs*的頂部：

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.ML;
   using Microsoft.ML.Data;
   using Microsoft.Spark.Sql;
   using MLSparkModelML.Model;
   ```

1. 將`DATA_FILEPATH`更改為*yelptest.csv*的路徑。

1. 將以下代碼添加到方法`Main`以創建新的`SparkSession`。 Spark 會話是使用資料集和資料幀 API 程式設計 Spark 的進入點。

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName(".NET for Apache Spark Sentiment Analysis")
        .GetOrCreate();
   ```

   調用上面創建的*火花*物件允許您在整個程式中訪問 Spark 和 DataFrame 功能。

### <a name="create-a-dataframe-and-print-to-console"></a>創建資料幀並列印到主控台

在 Yelp 審查資料中從*yelptest.csv*檔中`DataFrame`讀取為 。 包括`header`和`inferSchema`選項。 該`header`選項將*yelptest.csv*的第一行顯示為列名稱而不是資料。 選項`inferSchema`根據資料推斷列類型。

```csharp
DataFrame df = spark
    .ReadStream()
    .Option("header", true)
    .Option("inferSchema", true)
    .Csv(DATA_FILEPATH);

df.Show();
```

### <a name="register-a-user-defined-function"></a>註冊使用者定義的函數

您可以在 Spark 應用程式中使用*使用者定義的函數*UdF 對資料進行計算和分析。 在本教程中，您將ML.NET與 UDF 一起評估每個 Yelp 審核。

將以下代碼添加到方法`Main`以註冊稱為`MLudf`的 UDF。

```csharp
spark.Udf()
    .Register<string, bool>("MLudf", predict);
```

此 UDF 將 Yelp 審核字串作為輸入，並分別輸出正或負情緒的真或假。 它使用在後面的步驟中定義的*預測（）方法*。

### <a name="use-spark-sql-to-call-the-udf"></a>使用 Spark SQL 調用 UDF

現在，您已讀取資料併合並 ML，請使用 Spark SQL 調用 UDF，該 UDF 將在 DataFrame 的每一行上運行情緒分析。 將下列程式碼新增至 `Main` 方法：

```csharp
// Use Spark SQL to call ML.NET UDF
// Display results of sentiment analysis on reviews
df.CreateOrReplaceTempView("Reviews");
DataFrame sqlDf = spark.Sql("SELECT ReviewText, MLudf(ReviewText) FROM Reviews");
sqlDf.Show();

// Print out first 20 rows of data
// Prevent data getting cut off by setting truncate = 0
sqlDf.Show(20, 0, false);

spark.Stop();
```

### <a name="create-predict-method"></a>創建預測（）方法

在方法`Main()`之前添加以下代碼。 此代碼類似于模型產生器在*ConsumeModel.cs*中生成的代碼。 將此方法移動到主控台會載入每次運行應用時載入模型。

```csharp
private static readonly PredictionEngine<ModelInput, ModelOutput> _predictionEngine;

static Program()
{
    MLContext mlContext = new MLContext();
    ITransformer model = mlContext.Model.Load("MLModel.zip", out DataViewSchema schema);
    _predictionEngine = mlContext.Model.CreatePredictionEngine<ModelInput, ModelOutput>(model);
}

static bool predict(string text)
{
    ModelInput input = new ModelInput
    {
        ReviewText = text
    };

    return _predictionEngine.Predict(input).Prediction;
}
```

## <a name="add-the-model-to-your-console-app"></a>將模型添加到主控台應用

在解決方案資源管理器中，從**MLSparkModelML.Model.Model**專案複製*MLModel.zip*檔，並將其粘貼到**MLSparkModelML.ConsoleApp**專案中。 引用將自動添加到*MLSparkModelML.ConsoleApp.csproj*中。

## <a name="run-your-code"></a>運行代碼

用於`spark-submit`運行代碼。 使用命令提示導航到主控台應用的根資料夾並運行以下命令。

首先，清理併發布應用。

```dotnetcli
dotnet clean
dotnet publish
```

然後導航到主控台應用的發佈資料夾並運行以下`spark-submit`命令。 請記住使用 Microsoft Spark jar 檔的實際路徑更新該命令。

```dotnetcli
%SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local microsoft-spark-2.4.x-0.10.0.jar dotnet MLSparkModelML.ConsoleApp.dll
```

## <a name="get-the-code"></a>取得程式碼

本教程類似于["使用大資料進行情緒分析"](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment)示例中的代碼。

## <a name="next-steps"></a>後續步驟

前進到下一篇文章，瞭解如何使用 .NET 為 Apache Spark 進行結構化流式處理。
> [!div class="nextstepaction"]
> [教程：結構化流與 .NET 的 Apache Spark](streaming.md)
