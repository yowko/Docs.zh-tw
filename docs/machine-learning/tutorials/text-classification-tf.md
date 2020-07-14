---
title: 教學課程：使用 TensorFlow 模型分析審核情感
description: '本教學課程說明如何使用預先定型的 TensorFlow 模型，將網站批註中的情感分類。 Binary 情感分類器是使用 Visual Studio 開發的 c # 主控台應用程式。'
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 9a2e7f72d59e31cfd7db5b89bfad55bccb063cea
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281403"
---
# <a name="tutorial-analyze-sentiment-of-movie-reviews-using-a-pre-trained-tensorflow-model-in-mlnet"></a>教學課程：在 ML.NET 中使用預先定型的 TensorFlow 模型來分析電影評論的情感

本教學課程說明如何使用預先定型的 TensorFlow 模型，將網站批註中的情感分類。 Binary 情感分類器是使用 Visual Studio 開發的 c # 主控台應用程式。

本教學課程中使用的 TensorFlow 模型已使用 IMDB 資料庫中的電影評論進行定型。 完成應用程式開發之後，您將能夠提供電影評論文字，而應用程式會告訴您此評論是否有正面或負面的情感。

在本教學課程中，您會了解如何：
> [!div class="checklist"]
>
> * 載入預先定型的 TensorFlow 模型
> * 將網站註解文字轉換成適用于模型的功能
> * 使用模型來進行預測

您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) 存放庫中找到本教學課程的原始程式碼。

## <a name="prerequisites"></a>必要條件

* 已安裝「.NET Core 跨平臺開發」工作負載的[Visual Studio 2017 15.6 版或更新](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)版本。

## <a name="setup"></a>設定

### <a name="create-the-application"></a>建立應用程式

1. 建立名為 "TextClassificationTF" 的 **.Net Core 主控台應用程式**。

2. 在專案中建立名為*Data*的目錄，以儲存您的資料集檔案。

3. 安裝「Microsoft.ML NuGet 套件」****：

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]****。 選擇 "nuget.org" 作為套件來源，然後選取 [**流覽**] 索引標籤。搜尋**Microsoft.ML**，選取您想要的套件，然後選取 [**安裝**] 按鈕。 同意您所選套件的授權條款，以繼續進行安裝。 針對**TensorFlow**、 **SampleUtils**和**SciSharp**重複這些步驟。（可轉散發套件）。

### <a name="add-the-tensorflow-model-to-the-project"></a>將 TensorFlow 模型加入至專案

> [!NOTE]
> 本教學課程的模型來自[dotnet/machinelearning-testdata](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) GitHub 存放庫。 模型為 TensorFlow SavedModel 格式。

1. 下載[sentiment_model zip](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true)檔案，然後解壓縮。

    Zip 檔案包含：

    * `saved_model.pb`： TensorFlow 模型本身。 此模型會採用固定長度 (大小 600) 整數陣列，這是代表 IMDB 審核字串中之文字的特徵，並輸出兩個加總為1的機率：輸入審核的機率為正情感，以及輸入評論具有負面情感的可能性。
    * `imdb_word_index.csv`：從個別單字到整數值的對應。 對應是用來產生 TensorFlow 模型的輸入特徵。

2. 將最內層目錄的內容複寫 `sentiment_model` 到您的*TextClassificationTF*專案 `sentiment_model` 目錄。 此目錄包含本教學課程所需的模型和其他支援檔案，如下圖所示：

   ![sentiment_model 目錄內容](./media/text-classification-tf/sentiment-model-files.png)

3. 在方案總管中，以滑鼠右鍵按一下目錄和子目錄中的每個檔案， `sentiment_model` 然後選取 [**屬性**]。 在 [ **Advanced**] 底下，將 [**複製到輸出目錄**] 的值變更為 [**更新時複製**]。

### <a name="add-using-statements-and-global-variables"></a>加入 using 語句和全域變數

1. 在 *Program.cs* 檔案頂端新增下列額外的 `using` 陳述式：

   [!code-csharp[AddUsings](./snippets/text-classification-tf/csharp/Program.cs#AddUsings "Add necessary usings")]

1. 在方法上方建立兩個全域變數 `Main` ，以保存已儲存的模型檔案路徑和功能向量長度。

   [!code-csharp[DeclareGlobalVariables](./snippets/text-classification-tf/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

    * `_modelPath`這是定型模型的檔案路徑。
    * `FeatureLength`這是模型所預期的整數功能陣列長度。

### <a name="model-the-data"></a>將資料模型化

電影評論是自由格式的文字。 您的應用程式會將文字轉換成模型所預期的輸入格式，這幾個不同的階段。

第一種方式是將文字分割成不同的字組，然後使用提供的對應檔案，將每個單字對應到整數編碼。 此轉換的結果是可變長度的整數陣列，其長度會對應到句子中的單字數目。

|屬性| 值|類型|
|-------------|-----------------------|------|
|ReviewText|這部電影真的不錯|字串|
|VariableLengthFeatures|14、22、9、66、78,.。。 |int []|

然後，可變長度功能陣列會調整為固定長度的600。 這是 TensorFlow 模型所預期的長度。

|屬性| 值|類型|
|-------------|-----------------------|------|
|ReviewText|這部電影真的不錯|字串|
|VariableLengthFeatures|14、22、9、66、78,.。。 |int []|
|功能|14、22、9、66、78,.。。 |int [600]|

1. 在方法之後，為您的輸入資料建立類別 `Main` ：

    [!code-csharp[MovieReviewClass](./snippets/text-classification-tf/csharp/Program.cs#MovieReviewClass "Declare movie review type")]

    輸入資料類別 `MovieReview` 具有 `string` () 的使用者批註 `ReviewText` 。

1. 在方法之後，建立變數長度功能的類別 `Main` ：

    [!code-csharp[VariableLengthFeatures](./snippets/text-classification-tf/csharp/Program.cs#VariableLengthFeatures "Declare variable length features type")]

    `VariableLengthFeatures`屬性具有[VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A)屬性，可將它指定為向量。  所有向量元素都必須是相同的類型。 在具有大量資料行的資料集內，將多個資料行當做單一向量載入，可減少套用資料轉換時的資料傳遞數目。

    這個類別會用於動作中 `ResizeFeatures` 。 其屬性的名稱 (在此情況下，只會使用一個) 來指示 DataView 中的哪些資料行可以當做自訂對應動作的_輸入_使用。

1. 在方法之後，建立固定長度功能的類別 `Main` ：

    [!code-csharp[FixedLengthFeatures](./snippets/text-classification-tf/csharp/Program.cs#FixedLengthFeatures)]

    這個類別會用於動作中 `ResizeFeatures` 。 其屬性的名稱 (在此情況下，只會使用一個) 來指示 DataView 中的哪些資料行可以當做自訂對應動作的_輸出_使用。

    請注意，屬性的名稱 `Features` 是由 TensorFlow 模型所決定。 您無法變更此屬性名稱。

1. 在方法之後，建立預測的類別 `Main` ：

    [!code-csharp[Prediction](./snippets/text-classification-tf/csharp/Program.cs#Prediction "Declare prediction class")]

    `MovieReviewSentimentPrediction` 是在模型定型後所使用的預測類別。 `MovieReviewSentimentPrediction`具有單一 `float` 陣列 (`Prediction`) 和 `VectorType` 屬性。

### <a name="create-the-mlcontext-lookup-dictionary-and-action-to-resize-features"></a>建立 MLCoNtext、查閱字典，以及調整功能大小的動作

[MLContext 類別](xref:Microsoft.ML.MLContext)是所有 ML.NET 作業的起點。 將 `mlContext` 初始化會建立新的 ML.NET 環境，可在模型建立工作流程物件間共用。 就概念而言，類似於 Entity Framework 中的 `DBContext`。

1. 將 `Main` 方法中的 `Console.WriteLine("Hello World!")` 程式碼行取代為下列程式碼，以宣告 mlContext 變數並將它初始化：

   [!code-csharp[CreateMLContext](./snippets/text-classification-tf/csharp/Program.cs#CreateMLContext "Create the ML Context")]

1. 建立字典，使用方法從檔案載入對應資料，以將單字編碼為整數 [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) ，如下表所示：

    |單字     |索引    |
    |---------|---------|
    |小子     |  362    |
    |want     |  181    |
    |發生    |  355    |
    |effects  |  302    |
    |感受  |  547    |

    新增下列程式碼以建立查找對應：

    [!code-csharp[CreateLookupMap](./snippets/text-classification-tf/csharp/Program.cs#CreateLookupMap)]

1. 加入 `Action` 以將可變長度的文字陣列大小調整為固定大小的整數陣列，並使用下一行程式碼：

   [!code-csharp[ResizeFeatures](./snippets/text-classification-tf/csharp/Program.cs#ResizeFeatures)]

## <a name="load-the-pre-trained-tensorflow-model"></a>載入預先定型的 TensorFlow 模型

1. 新增程式碼以載入 TensorFlow 模型：

    [!code-csharp[LoadTensorFlowModel](./snippets/text-classification-tf/csharp/Program.cs#LoadTensorFlowModel)]

    載入模型之後，您可以將它的輸入和輸出架構解壓縮。 架構會顯示為感興趣並僅供學習之用。 您不需要這段程式碼，最終應用程式就能運作：

    [!code-csharp[GetModelSchema](./snippets/text-classification-tf/csharp/Program.cs#GetModelSchema)]

    輸入架構是整數編碼單字的固定長度陣列。 輸出架構是機率的浮點數組，表示評論的情感是負數或正數。 這些值會加總為1，因為正的機率是情感為負值的機率補數。

## <a name="create-the-mlnet-pipeline"></a>建立 ML.NET 管線

1. 建立管線，並使用[TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A)轉換將輸入文字分割成單字，以將文字分成單字，做為下一行程式碼：

   [!code-csharp[TokenizeIntoWords](./snippets/text-classification-tf/csharp/Program.cs#TokenizeIntoWords)]

   [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A)轉換會使用空格，將文字/字串剖析成單字。 它會建立新的資料行，並根據使用者定義的分隔符號，將每個輸入字串分割成子字串的向量。

1. 使用您在上方宣告的查閱資料表，將單字對應到其整數編碼：

    [!code-csharp[MapValue](./snippets/text-classification-tf/csharp/Program.cs#MapValue)]

1. 將可變長度的整數編碼方式調整為模型所需的固定長度：

    [!code-csharp[CustomMapping](./snippets/text-classification-tf/csharp/Program.cs#CustomMapping)]

1. 使用已載入的 TensorFlow 模型將輸入分類：

    [!code-csharp[ScoreTensorFlowModel](./snippets/text-classification-tf/csharp/Program.cs#ScoreTensorFlowModel)]

    會呼叫 TensorFlow 模型輸出 `Prediction/Softmax` 。 請注意，此名稱 `Prediction/Softmax` 是由 TensorFlow 模型所決定。 您無法變更此名稱。

1. 為輸出預測建立新的資料行：

    [!code-csharp[SnippetCopyColumns](./snippets/text-classification-tf/csharp/Program.cs#SnippetCopyColumns)]

    您必須將資料 `Prediction/Softmax` 行複製到一個，其名稱可以當做 c # 類別中的屬性使用： `Prediction` 。 `/`C # 屬性名稱中不允許字元。

## <a name="create-the-mlnet-model-from-the-pipeline"></a>從管線建立 ML.NET 模型

1. 新增程式碼，以從管線建立模型：

    [!code-csharp[SnippetCreateModel](./snippets/text-classification-tf/csharp/Program.cs#SnippetCreateModel)]

    ML.NET 模型是藉由呼叫方法，從管線中的估算器鏈建立而來 `Fit` 。 在此情況下，我們不會調整任何資料來建立模型，因為 TensorFlow 模型先前已定型。 我們會提供空的資料檢視物件，以滿足方法的需求 `Fit` 。

## <a name="use-the-model-to-make-a-prediction"></a>使用模型來進行預測

1. `PredictSentiment`在方法下方新增方法 `Main` ：

    ```csharp
    public static void PredictSentiment(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. 新增下列程式碼，以建立 `PredictionEngine` 做為方法中的第一行 `PredictSentiment()` ：

    [!code-csharp[CreatePredictionEngine](./snippets/text-classification-tf/csharp/Program.cs#CreatePredictionEngine)]

    [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602)是一個方便的 API，可讓您在單一資料實例上執行預測。 [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)不是安全線程。 可接受在單一執行緒或原型環境中使用。 為了改善生產環境中的效能和執行緒安全，請使用 `PredictionEnginePool` 服務，這會建立物件的， [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) 以便在 [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) 整個應用程式中使用。 請參閱本指南，以瞭解如何[ `PredictionEnginePool` 在 ASP.NET CORE Web API 中使用](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)。

    > [!NOTE]
    > `PredictionEnginePool` 服務延伸模組目前處於預覽狀態。

1. 透過建立 `MovieReview` 的執行個體，在 `Predict()` 方法中新增評論，以測試定型模型的預測：

    [!code-csharp[CreateTestData](./snippets/text-classification-tf/csharp/Program.cs#CreateTestData)]

1. 藉 `Prediction Engine` 由在方法中新增下一行程式碼，將測試批註資料傳遞給 `PredictSentiment()` ：

    [!code-csharp[Predict](./snippets/text-classification-tf/csharp/Program.cs#Predict)]

1. [Predict ( # B1](xref:Microsoft.ML.PredictionEngine%602.Predict%2A)函數會對單一資料列進行預測：

    |屬性| 值|類型|
    |-------------|-----------------------|------|
    |預測|[0.5459937，0.454006255]|float []|

1. 使用下列程式碼來顯示情感預測：

    [!code-csharp[DisplayPredictions](./snippets/text-classification-tf/csharp/Program.cs#DisplayPredictions)]

1. `PredictSentiment`在方法的結尾新增對的呼叫 `Main` ：

    [!code-csharp[CallPredictSentiment](./snippets/text-classification-tf/csharp/Program.cs#CallPredictSentiment)]

## <a name="results"></a>結果

建置並執行應用程式。

您的結果應該與以下類似。 處理期間會顯示訊息。 您可能會看到警告或處理訊息。 為了讓結果變得清楚，這些訊息已從下列結果中移除。

```console
Number of classes: 2
Is sentiment/review positive ? Yes
```

恭喜！ 您現在已成功建立機器學習模型，以在 ML.NET 中重複使用預先定型的模型來分類和預測訊息情感 `TensorFlow` 。

您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) 存放庫中找到本教學課程的原始程式碼。

在本教學課程中，您已了解如何：
> [!div class="checklist"]
>
> * 載入預先定型的 TensorFlow 模型
> * 將網站註解文字轉換成適用于模型的功能
> * 使用模型來進行預測
