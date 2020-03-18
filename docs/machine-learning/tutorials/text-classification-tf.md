---
title: 教程：使用 TensorFlow 模型分析審核情緒
description: 本教程介紹如何使用預先訓練的 TensorFlow 模型對網站評論中的情緒進行分類。 二進位情緒分類器是使用 Visual Studio 開發的 C# 主控台應用程式。
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 688c5b83cef8f21eef8fa24521a85449a9cfbd48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "78241113"
---
# <a name="tutorial-analyze-sentiment-of-movie-reviews-using-a-pre-trained-tensorflow-model-in-mlnet"></a>教程：在ML.NET中使用預先訓練的 TensorFlow 模型分析電影評論的情緒

本教程介紹如何使用預先訓練的 TensorFlow 模型對網站評論中的情緒進行分類。 二進位情緒分類器是使用 Visual Studio 開發的 C# 主控台應用程式。

本教程中使用的 TensorFlow 模型使用 IMDB 資料庫中的電影評論進行了訓練。 一旦你完成了應用程式的發展，你將能夠提供電影評論文本，應用程式會告訴你，審查是正面的還是負面的情緒。

在本教學課程中，您會了解如何：
> [!div class="checklist"]
>
> * 載入預先訓練的 TensorFlow 模型
> * 將網站評論文本轉換為適合模型的功能
> * 使用模型來進行預測

您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) 存放庫中找到本教學課程的原始程式碼。

## <a name="prerequisites"></a>必要條件

* [Visual Studio 2017 版本 15.6 或更高版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)安裝了".NET 核心跨平臺開發"工作負載。

## <a name="setup"></a>安裝程式

### <a name="create-the-application"></a>建立應用程式

1. 創建一個稱為"文本分類TF"**的 .NET 核心主控台應用程式**。

2. 在專案中創建名為*Data*的目錄以保存資料集檔。

3. 安裝「Microsoft.ML NuGet 套件」****：

    在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]****。 選擇"nuget.org"作為包源，然後選擇 **"流覽**"選項卡。搜索**Microsoft.ML，** 選擇所需的包，然後選擇"**安裝**"按鈕。 同意您所選套件的授權條款，以繼續進行安裝。 重複這些步驟的**微軟.ML.TensorFlow**和**SciSharp.TensorFlow.Redist**.

### <a name="add-the-tensorflow-model-to-the-project"></a>將 TensorFlow 模型添加到專案中

> [!NOTE]
> 本教程的模型來自[dotnet/機器學習測試資料](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model)GitHub 存儲庫。 該模型採用 TensorFlow 保存模型格式。

1. 下載[sentiment_model壓縮檔](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true)，並解壓縮。

    ZIP 檔案包含：

    * `saved_model.pb`：TensorFlow 模型本身。 模型採用表示 IMDB 審核字串中文本的固定長度（大小 600）整數陣列，並輸出兩個概率，總和為 1：輸入審核具有正情緒的概率，以及輸入評審具有的概率負面情緒。
    * `imdb_word_index.csv`：從單個單詞到整數值的映射。 映射用於生成 TensorFlow 模型的輸入要素。

2. 將最`sentiment_model`內側目錄的內容複寫到*文本分類TF*專案`sentiment_model`目錄中。 此目錄包含本教學課程所需的模型和其他支援檔案，如下圖所示：

   ![sentiment_model目錄內容](./media/text-classification-tf/sentiment-model-files.png)

3. 在解決方案資源管理器中，按右鍵`sentiment_model`目錄和子目錄中的每個檔，然後選擇**屬性**。 在 **"高級"** 下，將 **"複製到輸出目錄**"的值更改為 **"如果更新"，則將其更改為"複製**"。

### <a name="add-using-statements-and-global-variables"></a>使用語句和全域變數添加

1. 在 *Program.cs* 檔案頂端新增下列額外的 `using` 陳述式：

   [!code-csharp[AddUsings](../../../samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#AddUsings "Add necessary usings")]

1. 在`Main`方法的正上方創建兩個全域變數，以保存保存的模型檔路徑和要素向量長度。

   [!code-csharp[DeclareGlobalVariables](../../../samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

    * `_modelPath`是訓練模型的檔路徑。
    * `FeatureLength`是模型期望的整數要素陣列的長度。

### <a name="model-the-data"></a>將資料模型化

電影評論是免費形式文本。 應用程式將文本轉換為模型在多個離散階段中期望的輸入格式。

第一種是將文本拆分為單獨的單詞，並使用提供的映射檔將每個單詞映射到整數編碼。 此轉換的結果是一個可變長度整數陣列，其長度對應于句子中的單詞數。

|屬性| 值|類型|
|-------------|-----------------------|------|
|評論文本|這部電影真的很好|字串|
|可變長度特徵|14,22,9,66,78,... |int_|

然後，可變長度要素陣列將大小調整為固定長度為 600。 這是 TensorFlow 模型期望的長度。

|屬性| 值|類型|
|-------------|-----------------------|------|
|評論文本|這部電影真的很好|字串|
|可變長度特徵|14,22,9,66,78,... |int_|
|特性|14,22,9,66,78,... |int[600]|

1. 在`Main`方法之後為輸入資料創建類：

    [!code-csharp[MovieReviewClass](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#MovieReviewClass "Declare movie review type")]

    輸入資料類`MovieReview`（ 具有`string`用於使用者注釋的`ReviewText`。

1. 在`Main`方法之後為可變長度要素創建類：

    [!code-csharp[VariableLengthFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#VariableLengthFeatures "Declare variable length features type")]

    屬性`VariableLengthFeatures`具有[向量類型](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A)屬性，用於將其指定為向量。  所有向量元素必須相同類型。 在具有大量列的資料集中，將多個列載入為單個向量會減少應用資料轉換時的資料傳遞次數。

    類用於`ResizeFeatures`操作。 其屬性的名稱（本例中只有一個）用於指示 DataView 中的哪些列可用作自訂映射操作的_輸入_。

1. 在`Main`方法之後為固定長度要素創建類：

    [!code-csharp[FixedLengthFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#FixedLengthFeatures)]

    類用於`ResizeFeatures`操作。 其屬性的名稱（本例中只有一個）用於指示 DataView 中的哪些列可用作自訂映射操作的_輸出_。

    請注意，屬性`Features`的名稱由 TensorFlow 模型確定。 不能更改此屬性名稱。

1. 在`Main`方法之後為預測創建類：

    [!code-csharp[Prediction](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#Prediction "Declare prediction class")]

    `MovieReviewSentimentPrediction` 是在模型定型後所使用的預測類別。 `MovieReviewSentimentPrediction`具有單個`float`陣列 （`Prediction`）`VectorType`和屬性。

### <a name="create-the-mlcontext-lookup-dictionary-and-action-to-resize-features"></a>創建 MLCoNtext、查找字典和調整功能大小的操作

[MLContext 類別](xref:Microsoft.ML.MLContext)是所有 ML.NET 作業的起點。 將 `mlContext` 初始化會建立新的 ML.NET 環境，可在模型建立工作流程物件間共用。 就概念而言，類似於 Entity Framework 中的 `DBContext`。

1. 將 `Main` 方法中的 `Console.WriteLine("Hello World!")` 程式碼行取代為下列程式碼，以宣告 mlContext 變數並將它初始化：

   [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateMLContext "Create the ML Context")]

1. 使用[`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A)方法載入檔中的映射資料，創建字典將單詞編碼為整數，如下表所示：

    |Word     |索引    |
    |---------|---------|
    |孩子     |  362    |
    |want     |  181    |
    |錯    |  355    |
    |effects  |  302    |
    |感覺  |  547    |

    添加以下代碼以創建查找映射：

    [!code-csharp[CreateLookupMap](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateLookupMap)]

1. 添加`Action`用於將可變長度字整數陣列的大小調整到固定大小的整數陣列，並包含下一行代碼：

   [!code-csharp[ResizeFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#ResizeFeatures)]

## <a name="load-the-pre-trained-tensorflow-model"></a>載入預先訓練的 TensorFlow 模型

1. 添加代碼以載入 TensorFlow 模型：

    [!code-csharp[LoadTensorFlowModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#LoadTensorFlowModel)]

    載入模型後，可以提取其輸入和輸出架構。 圖解僅供興趣和學習。 不需要此代碼才能使最終應用程式正常運行：

    [!code-csharp[GetModelSchema](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#GetModelSchema)]

    輸入架構是整數編碼詞的固定長度陣列。 輸出架構是一個浮動概率陣列，指示評論的情緒是負的還是正的。 這些值總和為 1，因為正值的概率是情緒為負的概率的補數。

## <a name="create-the-mlnet-pipeline"></a>創建ML.NET管道

1. 創建管道並使用[TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A)轉換將輸入文本拆分為單詞，將文本拆分為單詞作為下一行代碼：

   [!code-csharp[TokenizeIntoWords](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#TokenizeIntoWords)]

   ["標記到"轉換](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A)使用空格將文本/字串解析為單詞。 它創建一個新列，並根據使用者定義的分隔符號將每個輸入字串拆分為子字串向量。

1. 使用上面聲明的查閱資料表將單詞映射到其整數編碼：

    [!code-csharp[MapValue](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#MapValue)]

1. 將可變長度整數編碼的大小調整到模型所需的固定長度編碼：

    [!code-csharp[CustomMapping](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CustomMapping)]

1. 使用載入的 TensorFlow 模型對輸入進行分類：

    [!code-csharp[ScoreTensorFlowModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#ScoreTensorFlowModel)]

    張力流模型輸出稱為`Prediction/Softmax`。 請注意，名稱`Prediction/Softmax`由 TensorFlow 模型確定。 您不能更改此名稱。

1. 為輸出預測創建新列：

    [!code-csharp[SnippetCopyColumns](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#SnippetCopyColumns)]

    您需要將`Prediction/Softmax`列複製到一個名稱中，該名稱可用作 C# 類中的屬性： `Prediction`。 C# 屬性名稱中不允許該`/`字元。

## <a name="create-the-mlnet-model-from-the-pipeline"></a>從管道創建ML.NET模型

1. 添加代碼以從管道創建模型：

    [!code-csharp[SnippetCreateModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#SnippetCreateModel)]

    通過調用`Fit`方法，從管道中的估計器鏈創建ML.NET模型。 在這種情況下，我們未擬合任何資料來創建模型，因為 TensorFlow 模型以前已經過訓練。 我們提供一個空資料檢視物件，以滿足`Fit`該方法的要求。

## <a name="use-the-model-to-make-a-prediction"></a>使用模型來進行預測

1. 在`PredictSentiment``Main`方法下方添加方法：

    ```csharp
    public static void PredictSentiment(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. 添加以下代碼以創建`PredictionEngine``PredictSentiment()`方法中的第一行：

    [!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreatePredictionEngine)]

    [預測引擎](xref:Microsoft.ML.PredictionEngine%602)是一個方便的 API，它允許您對單個資料實例執行預測。 [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)不是執行緒安全的。 在單線程或原型環境中使用是可以接受的。 為提高生產環境中的性能和執行緒安全性，請使用`PredictionEnginePool`該服務，該服務創建一個[`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601)[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)物件，供整個應用程式使用。 請參閱有關如何[`PredictionEnginePool`在 ASP.NET核心 Web API 中使用](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)的本指南。

    > [!NOTE]
    > `PredictionEnginePool` 服務延伸模組目前處於預覽狀態。

1. 透過建立 `MovieReview` 的執行個體，在 `Predict()` 方法中新增評論，以測試定型模型的預測：

    [!code-csharp[CreateTestData](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateTestData)]

1. `Prediction Engine`通過在`PredictSentiment()`方法中添加下一行代碼，將測試注釋資料傳遞給 ：

    [!code-csharp[Predict](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#Predict)]

1. [預測（）](xref:Microsoft.ML.PredictionEngine%602.Predict%2A)函數對一行資料進行預測：

    |屬性| 值|類型|
    |-------------|-----------------------|------|
    |預測|[0.5459937, 0.454006255]|浮動*|

1. 使用以下代碼顯示情緒預測：

    [!code-csharp[DisplayPredictions](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#DisplayPredictions)]

1. 在`Main`方法末尾添加`PredictSentiment`調用：

    [!code-csharp[CallPredictSentiment](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CallPredictSentiment)]

## <a name="results"></a>結果

建置並執行應用程式。

您的結果應該與以下類似。 處理期間會顯示訊息。 您可能會看到警告或處理訊息。 為了讓結果變得清楚，這些訊息已從下列結果中移除。

```console
Number of classes: 2
Is sentiment/review positive ? Yes
```

恭喜！ 現在，您已經成功地構建了機器學習模型，通過重用ML.NET預先訓練的`TensorFlow`模型來分類和預測消息情緒。

您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) 存放庫中找到本教學課程的原始程式碼。

在本教學課程中，您已了解如何：
> [!div class="checklist"]
>
> * 載入預先訓練的 TensorFlow 模型
> * 將網站評論文本轉換為適合模型的功能
> * 使用模型來進行預測
