---
title: 使用 .NET 進行 Apache Spark 和 ML.NET 教學課程的情感分析
description: 在本教學課程中，您將瞭解如何使用 ML.NET 搭配 .NET 以進行情感分析的 Apache Spark。
author: mamccrea
ms.author: mamccrea
ms.date: 10/09/2020
ms.topic: tutorial
ms.openlocfilehash: 16b4d34e4c581da2cd0ba798d87e53ccfc49f0e9
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2020
ms.locfileid: "91954889"
---
# <a name="tutorial-sentiment-analysis-with-net-for-apache-spark-and-mlnet"></a>教學課程：使用 .NET 進行 Apache Spark 和 ML.NET 的情感分析

本教學課程會教您如何使用 ML.NET 和 .NET 進行 Apache Spark 的線上審核情感分析。 [ML.NET](http://dot.net/ml) 是免費的跨平臺開放原始碼機器學習架構。 您可以使用 ML.NET 搭配 .NET 進行 Apache Spark，以調整機器學習演算法的定型和預測。

在本教學課程中，您會了解如何：

> [!div class="checklist"]
>
> * 在 Visual Studio 中使用 ML.NET 模型產生器建立情感分析模型。
> * 為 Apache Spark 主控台應用程式建立 .NET。
> * 撰寫和執行使用者定義函數。
> * 針對 Apache Spark 主控台應用程式執行 .NET。

## <a name="prerequisites"></a>必要條件

* 如果您之前尚未開發 Apache Spark 應用程式的 .NET，請從 [消費者入門教學](get-started.md) 課程開始，以熟悉基本概念。 繼續進行本教學課程之前，請先完成消費者入門教學課程的所有必要條件。

* 本教學課程使用 ML.NET 模型產生器 (預覽) ，Visual Studio 提供視覺化介面。 如果您還沒有 Visual Studio，可以免費 [下載 Visual Studio](https://visualstudio.microsoft.com/downloads/) 的免費版。

* [下載並安裝](https://marketplace.visualstudio.com/items?itemName=MLNET.07) ML.NET 模型產生器 (預覽) 。

* 下載 [yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) 並 [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) Yelp 評論資料集。

## <a name="review-the-data"></a>檢閱資料

Yelp 評論資料集包含有關各種服務的線上 Yelp 評論。 開啟 [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) 並注意資料的結構。 第一個資料行包含審核文字，而第二個數據行包含情感分數。 如果情感分數是1，則審核是正面的，且如果情感分數為0，則審核為負數。

下表包含範例資料：

|ReviewText|情感|
|-|-|
|哇。。。喜歡這個位置。|    1|
|不夠酥脆。|    0|

## <a name="build-your-machine-learning-model"></a>建立您的機器學習模型

1. 開啟 Visual Studio，並 ( .NET Core) 建立新的 c # 主控台應用程式。 將專案命名為 *MLSparkModel*。

1. 在 **方案總管**中，以滑鼠右鍵按一下 [ *MLSparkModel* ] 專案。 然後選取 [ **新增 > Machine Learning**。

1. 從 [ML.NET 模型產生器] 中，選取 [ **情感分析** 案例] 磚。

1. 在 [ **加入資料** ] 頁面上，上傳 *yelptrain.csv* 資料集。

1. 從 [**要預測**的資料行] 下拉式清單中選擇 [*情感*]。

1. 在 [ **定型** ] 頁面上，將 [定型時間] 設定為 *60 秒* ，然後選取 [ **開始訓練**]。 請注意訓練的**狀態。**

1. 模型產生器完成定型之後，請 **評估** 定型結果。 您可以 **在下方的** 文字方塊中輸入片語，然後選取 [ **預測** ] 以查看輸出。

1. 選取 [程式 **代碼** ]，然後選取 [ **新增專案** ]，將 ML 模型新增至方案。

1. 請注意，您的方案中加入了兩個專案： **MLSparkModelML. consoleapp.exe**和**MLSparkModelML。**

1. 按兩下 *MLSpark* c # 專案，並注意已加入下列專案參考。

   ```xml
   <ItemGroup>
       <ProjectReference Include="..\MLSparkModelML.Model\MLSparkModelML.Model.csproj" />
   </ItemGroup>
   ```

## <a name="create-a-console-app"></a>建立主控台應用程式

模型產生器會為您建立主控台應用程式。

1. 以滑鼠右鍵按一下方案總管中的 [ **MLSparkModelML** ]，然後選取 [ **管理 NuGet 套件**]。

1. 搜尋 **Microsoft Spark** 並安裝套件。 模型產生器會為您自動安裝**Microsoft.ML** 。

### <a name="create-a-sparksession"></a>建立 SparkSession

1. 開啟**MLSparkModelML. consoleapp.exe**的*Program.cs*檔案。 此檔案是由模型產生器自動產生的。 刪除 `using` 語句、主要 ( # A1 方法的內容，以及 `CreateSingleDataSample` 區域。

1. 將下列其他 `using` 語句新增至 *Program.cs*頂端：

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.ML;
   using Microsoft.ML.Data;
   using Microsoft.Spark.Sql;
   using MLSparkModelML.Model;
   ```

1. 將變更 `DATA_FILEPATH` 為您 *yelptest.csv*的路徑。

1. 將下列程式碼新增至您 `Main` 的方法，以建立新的 `SparkSession` 。 Spark 會話是使用資料集和資料框架 API 對 Spark 進行程式設計的進入點。

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName(".NET for Apache Spark Sentiment Analysis")
        .GetOrCreate();
   ```

   呼叫上面建立的 *spark* 物件，可讓您存取整個程式中的 Spark 和資料框架功能。

### <a name="create-a-dataframe-and-print-to-console"></a>建立資料框架並列印到主控台

從 *yelptest.csv* 檔案讀取 Yelp 審核資料 `DataFrame` 。 包含 `header` 和 `inferSchema` 選項。 選項會將 `header` *yelptest.csv* 的第一行讀取為數據行名稱，而不是資料。 `inferSchema`選項會根據資料推斷資料行類型。

```csharp
DataFrame df = spark
    .ReadStream()
    .Option("header", true)
    .Option("inferSchema", true)
    .Csv(DATA_FILEPATH);

df.Show();
```

### <a name="register-a-user-defined-function"></a>註冊使用者定義函數

您可以在 Spark 應用程式中使用 Udf （ *使用者定義函式*）來執行資料的計算和分析。 在本教學課程中，您會使用 ML.NET 搭配 UDF 來評估每個 Yelp 評論。

將下列程式碼新增至您 `Main` 的方法，以註冊名為的 UDF `MLudf` 。

```csharp
spark.Udf()
    .Register<string, bool>("MLudf", predict);
```

此 UDF 會採用 Yelp 審核字串做為輸入，並分別針對正面或負面情緒輸出 true 或 false。 它會使用您在稍後的步驟中定義的 *predict ( # B1 * 方法。

### <a name="use-spark-sql-to-call-the-udf"></a>使用 Spark SQL 來呼叫 UDF

既然您已讀取資料並納入 ML，請使用 Spark SQL 來呼叫將在資料框架的每個資料列上執行情感分析的 UDF。 將下列程式碼新增至 `Main` 方法：

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

### <a name="create-predict-method"></a>建立 predict ( # A1 方法

在您的方法之前加入下列程式碼 `Main()` 。 此程式碼類似于 *ConsumeModel.cs*中的模型產生器所產生的程式碼。 將此方法移至主控台會在您每次執行應用程式時載入模型載入。

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

## <a name="add-the-model-to-your-console-app"></a>將模型新增至您的主控台應用程式

在方案總管中，從**MLSparkModelML**專案複製*MLModel.zip*檔案，然後將它貼入**MLSparkModelML. consoleapp.exe**專案中。 參考會自動加入至 *MLSparkModelML. consoleapp.exe*。

## <a name="run-your-code"></a>執行您的程式碼

使用 `spark-submit` 來執行您的程式碼。 使用命令提示字元流覽至您的主控台應用程式根資料夾，然後執行下列命令。

首先，請清除併發布您的應用程式。

```dotnetcli
dotnet clean
dotnet publish
```

然後，流覽至主控台應用程式的 [發佈] 資料夾，然後執行下列 `spark-submit` 命令。 請記得使用您的 Microsoft Spark jar 檔案的實際路徑來更新命令。

```dotnetcli
%SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local microsoft-spark-2.4.x-0.10.0.jar dotnet MLSparkModelML.ConsoleApp.dll
```

## <a name="get-the-code"></a>取得程式碼

本教學課程類似于 [情感分析具有 Big Data](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment) 範例的程式碼。

## <a name="next-steps"></a>後續步驟

前進到下一篇文章，以瞭解如何使用 .NET 進行結構化串流以進行 Apache Spark。
> [!div class="nextstepaction"]
> [教學課程：使用 .NET 進行 Apache Spark 的結構化串流](streaming.md)
