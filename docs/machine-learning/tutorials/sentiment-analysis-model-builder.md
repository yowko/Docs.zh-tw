---
title: 教學課程：分析情感-二元分類
description: 本教學課程說明如何建立 Razor Pages 應用程式，以從網站批註分類情感並採取適當的動作。 二元情感分類器使用 Visual Studio 中的模型產生器。
ms.date: 11/21/2019
author: luisquintanilla
ms.author: luquinta
ms.topic: tutorial
ms.custom: mvc,mlnet-tooling
ms.openlocfilehash: 7761240055c90ae9c713b1c460e9e83316d256f9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/29/2020
ms.locfileid: "81278947"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-in-a-web-application-using-mlnet-model-builder"></a>教學課程：使用 ML.NET 模型產生器來分析 web 應用程式中的網站批註情感

瞭解如何在 web 應用程式內即時分析批註中的情感。

本教學課程會示範如何建立 ASP.NET Core Razor Pages 應用程式，以即時分類情感的網站批註。

在本教學課程中，您會了解如何：

> [!div class="checklist"]
>
> - 建立 ASP.NET Core Razor Pages 應用程式
> - 準備並了解資料
> - 選擇案例
> - 載入資料
> - 將模型定型
> - 評估模型
> - 使用模型來進行預測

> [!NOTE]
> 模型產生器目前為預覽版。

您可以在 [dotnet/machinelearning 範例](https://github.com/dotnet/machinelearning-samples) 存放庫中找到本教學課程的原始程式碼。

## <a name="pre-requisites"></a>必要條件

如需必要條件和安裝指示清單，請瀏覽[模型產生器安裝指南](../how-to-guides/install-model-builder.md)。

## <a name="create-a-razor-pages-application"></a>建立 Razor Pages 應用程式

1. 建立 **ASP.NET Core Razor Pages 應用程式**。

    1. 開啟 Visual Studio，然後從功能表列選取 [檔案] **> 新的 > 專案** 。
    1. 在 [新增專案] 對話方塊中，選取 [Visual C#] 節點，然後選取 [Web] 節點。
    1. 然後，選取 [ASP.NET Core Web 應用程式] 專案範本。
    1. 在 [ **名稱** ] 文字方塊中，輸入 "SentimentRazor"。
    1. 請確定未 **核** 取 **[將方案和專案放置在相同的目錄中** **] (vs** 2019) ，或 [**為方案建立目錄**] (與 2017) 。
    1. 選取 [ **確定]** 按鈕。
    1. 在顯示不同類型 ASP.NET Core 專案的視窗中選擇 [ **Web 應用程式** ]，然後選取 [ **確定]** 按鈕。

## <a name="prepare-and-understand-the-data"></a>準備並了解資料

下載 [維琪百科 detox 資料集](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)。 當網頁開啟時，在頁面上按一下滑鼠右鍵，選取 [ **另存** 新檔]，並將檔案儲存在您電腦上的任何位置。

*維琪百科-detox-250-line-data tsv* 資料集中的每個資料列，代表使用者在維琪百科所留下的不同評論。 第一個資料行代表文字 (0 為非有毒，1是有毒) ，而第二個數據行代表使用者所留下的批註。 這些資料行會以定位字元分隔。 資料看起來如下所示：

| 情感 | SentimentText |
| :---: | :---: |
1 | = = 強制 = = Dude，您會在上傳至您的上傳。
1 | = = 確定！ = = IM 會 VANDALIZE 萬用字元，然後再!!!
0 | 我希望這有説明。

## <a name="choose-a-scenario"></a>選擇案例

![Visual Studio 中的模型產生器 wizard](./media/sentiment-analysis-model-builder/model-builder-screen.png)

若要定型您的模型，您需要從模型產生器所提供的可用機器學習服務案例清單中選取。

1. 在 **方案總管** 中，以滑鼠右鍵按一下 *SentimentRazor* 專案，然後選取 [**加入**  >  **Machine Learning**。
1. 針對此範例，案例為情感分析。 在模型產生器工具的 *案例* 步驟中，選取 **情感分析** 案例。

## <a name="load-the-data"></a>載入資料

模型產生器會接受來自兩個來源的資料，SQL Server 資料庫或或格式的本機檔案 `csv` `tsv` 。

1. 在模型產生器工具的資料步驟中，從資料來源下拉式清單中選取 [檔案]。
1. 選取 [ **選取** 檔案] 文字方塊旁的按鈕，然後使用檔案總管流覽並選取 [ *維琪百科-detox-250-line-data tsv* ] 檔案。
1. 選擇資料行中的 [ **情感** ] **來預測 (標籤)** 下拉式清單。
1. 保留 [輸入資料行的預設值 **(功能])** 下拉式清單。
1. 選取 [ **定型** ] 連結，移至 [模型產生器] 工具中的下一個步驟。

## <a name="train-the-model"></a>將模型定型

在本教學課程中用來定型情感分析模型的機器學習服務工作是二元分類。 在模型定型程式期間，模型建立器會使用不同的二進位分類演算法和設定來訓練個別的模型，以找出最適合您資料集的模型。

定型模型所需要的時間會與資料量成比例。 模型產生器會根據資料來源的大小，自動選取預設值以根據您的資料來源大小 **(秒) 定型** 。

1. 雖然模型產生器會將 **時間值定型 (秒)** 為10秒，但請將其增加為30秒。 訓練較長的時間可讓模型產生器探索更大量的演算法和參數的組合，以搜尋最佳模型。
1. 選取 [開始定型]。

    在整個定型程序期間，進度資料會顯示在定型步驟的 `Progress` 區段中。

    - [狀態] 會顯示定型程序的完成狀態。
    - [最佳正確性] 會顯示模型產生器到目前為止所找到執行效能最佳模型的正確性。 正確性越高，表示模型針對測試資料的預測越正確。
    - [最佳演算法] 會顯示模型產生器到目前為止所執行演算法中效能最佳的演算法名稱。
    - [上一個演算法] 會顯示模型產生器最近一次用來定型模型的演算法名稱。

1. 定型完成後，請選取 [ **評估** ] 連結，以移至下一個步驟。

## <a name="evaluate-the-model"></a>評估模型

定型步驟的結果會是一個具有最佳效能的模型。 在模型產生器工具的評估步驟中，[輸出] 區段會包含最佳 **模型** 專案中最佳執行模型所使用的演算法，以及 **最佳模型精確度** 的度量。 此外，也會顯示包含前五個模型及其度量的摘要資料表。

如果您對精確度度量感到不滿意，可以透過一些簡單的方法來改善模型的精確度，以增加定型模型或使用更多資料的時間量。 否則，請選取 [程式 **代碼** ] 連結，以移至模型產生器工具中的最後一個步驟。

## <a name="add-the-code-to-make-predictions"></a>新增程式碼來進行預測

定型程序的結果會建立兩個專案。

### <a name="reference-the-trained-model"></a>參考定型的模型

1. 在模型產生器工具的程式 *代碼* 步驟中，選取 [ **加入專案** ]，將自動產生的專案加入至方案。

    下列專案應該會出現在 **方案總管** 中：

    - *SentimentRazorML. consoleapp.exe*： .Net Core 主控台應用程式，其中包含模型定型和預測程式碼。
    - *SentimentRazorML*： .NET Standard 類別庫，其中包含的資料模型會定義輸入和輸出模型資料的架構，以及定型期間最佳執行模型的儲存版本。

    在本教學課程中，只會使用 *SentimentRazorML 模型* 專案，因為會在 *SentimentRazor* web 應用程式中進行預測，而不是在主控台中進行預測。 雖然 *SentimentRazorML* 不會用於計分，但是可以用來在稍後使用新的資料重新定型模型。 不過，重新定型已超出本教學課程的範圍。

### <a name="configure-the-predictionengine-pool"></a>設定 PredictionEngine 集區

若要進行單一預測，您必須建立 <xref:Microsoft.ML.PredictionEngine%602> 。 <xref:Microsoft.ML.PredictionEngine%602> 不是安全執行緒。 此外，您必須在應用程式中的任何位置建立其實例。 當您的應用程式成長時，此程式可能會變得難以管理。 為了改善效能和執行緒安全性，請使用相依性插入和服務的組合 `PredictionEnginePool` ，以建立可 <xref:Microsoft.Extensions.ObjectPool.ObjectPool%601> <xref:Microsoft.ML.PredictionEngine%602> 在整個應用程式中使用的物件。

1. 安裝 *Microsoft.Extensions.ML* NuGet 套件：

    1. 在 **方案總管** 中，以滑鼠右鍵按一下專案，然後選取 [ **管理 NuGet 套件**]。
    1. 選擇 [nuget.org] 作為 [套件來源]。
    1. 選取 [ **流覽** ] 索引標籤，並搜尋 **Microsoft.Extensions.ML**。
    1. 選取清單中的套件，然後選取 [ **安裝** ] 按鈕。
    1. 在 [**預覽變更**] 對話方塊中選取 [**確定]** 按鈕
    1. 如果您同意所列套件的授權條款，請在 [**接受授權**] 對話方塊上選取 [**我接受**] 按鈕。

1. 開啟 *SentimentRazor* 專案中的 *Startup.cs* 檔案。
1. 新增下列 using 語句，以參考 *Microsoft.Extensions.ML* NuGet 封裝和 *SentimentRazorML 模型* 專案：

    ```csharp
    using System.IO;
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

1. 建立全域變數，以儲存定型模型檔案的位置。

    ```csharp
    private readonly string _modelPath;
    ```

1. 模型檔案會與應用程式的元件檔案一起儲存在組建目錄中。 為了讓存取更容易，請建立在 `GetAbsolutePath` 方法之後呼叫的 helper `Configure` 方法

    ```csharp
    public static string GetAbsolutePath(string relativePath)
    {
        FileInfo _dataRoot = new FileInfo(typeof(Program).Assembly.Location);
        string assemblyFolderPath = _dataRoot.Directory.FullName;

        string fullPath = Path.Combine(assemblyFolderPath, relativePath);
        return fullPath;
    }
    ```

1. 在類別的函式 `GetAbsolutePath` 中使用方法 `Startup` 來設定 `_modelPath` 。

    ```csharp
    _modelPath = GetAbsolutePath("MLModel.zip");
    ```

1. `PredictionEnginePool`在方法中為您的應用程式設定 `ConfigureServices` ：

    ```csharp
    services.AddPredictionEnginePool<ModelInput, ModelOutput>()
            .FromFile(_modelPath);
    ```

### <a name="create-sentiment-analysis-handler"></a>建立情感分析處理常式

系統會在應用程式的主頁面內進行預測。 因此，接受使用者輸入並使用來傳回預測的方法 `PredictionEnginePool` 需要加入。

1. 開啟位於 *Pages* 目錄中的 *Index.cshtml.cs* 檔案，然後新增下列 using 語句：

    ```csharp
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

    若要使用在 `PredictionEnginePool` 類別中設定的 `Startup` ，您必須將它插入您想要使用之模型的函式。

1. 加入變數以參考 `PredictionEnginePool` 類別內部的 `IndexModel` 。

    ```csharp
    private readonly PredictionEnginePool<ModelInput, ModelOutput> _predictionEnginePool;
    ```

1. 在類別中建立函式 `IndexModel` ，並將 `PredictionEnginePool` 服務插入其中。

    ```csharp
    public IndexModel(PredictionEnginePool<ModelInput, ModelOutput> predictionEnginePool)
    {
        _predictionEnginePool = predictionEnginePool;
    }
    ```

1. 建立方法處理常式，該處理常式會使用 `PredictionEnginePool` 從網頁收到的使用者輸入進行預測。

    1. 在 `OnGet` 方法底下，建立名為的新方法 `OnGetAnalyzeSentiment`

        ```csharp
        public IActionResult OnGetAnalyzeSentiment([FromQuery] string text)
        {

        }
        ```

    1. 在 `OnGetAnalyzeSentiment` 方法中，如果使用者的輸入是空白或 null，則傳回 *中性* 情感。

        ```csharp
        if (String.IsNullOrEmpty(text)) return Content("Neutral");
        ```

    1. 指定有效的輸入，建立的新實例 `ModelInput` 。

        ```csharp
        var input = new ModelInput { SentimentText = text };
        ```

    1. 使用 `PredictionEnginePool` 來預測情感。

        ```csharp
        var prediction = _predictionEnginePool.Predict(input);
        ```

    1. 使用下列程式碼，將預測 `bool` 值轉換為有毒或 not 有毒。

        ```csharp
        var sentiment = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";
        ```

    1. 最後，將情感回到網頁。

        ```csharp
        return Content(sentiment);
        ```

### <a name="configure-the-web-page"></a>設定網頁

所傳回的結果 `OnGetAnalyzeSentiment` 會動態顯示在 `Index` 網頁上。

1. 開啟 *Pages* 目錄中的 *Index* ，然後將其內容取代為下列程式碼：

    [!code-cshtml [IndexPage](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml)]

1. 接下來，將 css 樣式程式碼新增至 *wwwroot\css* 目錄中的 *網站 .css* 頁面結尾：

    [!code-css [CssStyling](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/css/site.css#L61-L105)]

1. 之後，請新增程式碼，以將 web 網頁的輸入傳送至 `OnGetAnalyzeSentiment` 處理常式。

    1. 在位於 *wwwroot\js* 目錄中的 *site.js* 檔案中，建立一個名為的函式， `getSentiment` 以對處理常式的使用者輸入提出 GET HTTP 要求 `OnGetAnalyzeSentiment` 。

        [!code-javascript [GetSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L5-L10)]

    1. 在下方，加入另一個函式， `updateMarker` 以在預測情感時動態更新網頁上標記的位置。

        [!code-javascript [UpdateMarkerMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L12-L15)]

    1. 建立呼叫的事件處理常式函式 `updateSentiment` ，以取得使用者的輸入、使用函式將其傳送至函式，並使用函式 `OnGetAnalyzeSentiment` `getSentiment` 更新標記 `updateMarker` 。

        [!code-javascript [UpdateSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L17-L34)]

    1. 最後，註冊事件處理常式，並將它系結至 `textarea` 具有 `id=Message` 屬性的元素。

        [!code-javascript [UpdateSentimentEvtHandler](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L36)]

## <a name="run-the-application"></a>執行應用程式

現在您的應用程式已設定完成，請執行應用程式，該應用程式應該會在您的瀏覽器中啟動。

當應用程式啟動時，輸入模型產生器 *是很酷的！* 在文字區域中。 所顯示的預測情感應該 *不會有毒*。

![使用預測的情感視窗執行視窗](./media/sentiment-analysis-model-builder/web-app.png)

如果您需要稍後再參考模型產生器所產生的專案，您可以在目錄中找到它們 `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` 。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已了解如何：
> [!div class="checklist"]
>
> - 建立 ASP.NET Core Razor Pages 應用程式
> - 準備並了解資料
> - 選擇案例
> - 載入資料
> - 將模型定型
> - 評估模型
> - 使用模型來進行預測

### <a name="additional-resources"></a>其他資源

若要深入了解此教學課程中提及的主題，請瀏覽下列資源：

- [模型建立器案例](../automate-training-with-model-builder.md#scenario)
- [二元分類](../resources/glossary.md#binary-classification)
- [二元分類模型計量](../resources/metrics.md#evaluation-metrics-for-binary-classification)
