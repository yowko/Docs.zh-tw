---
title: 教學課程：分析情感-二進位分類
description: 本教學課程會示範如何建立 Razor Pages 應用程式，以將情感從網站批註中分類，並採取適當的動作。 二元情感分類器會在 Visual Studio 中使用模型產生器。
ms.date: 09/30/2019
author: luisquintanilla
ms.author: luquinta
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: ce64f0d11b1da65e460235fdabc2b07e05ffcbe4
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700904"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-in-a-web-application-using-mlnet-model-builder"></a>教學課程：在 web 應用程式中使用 ML.NET 模型產生器來分析網站批註的情感

瞭解如何在 web 應用程式內即時分析批註中的情感。

本教學課程會示範如何建立 ASP.NET Core Razor Pages 應用程式，以即時將情感的網站批註分類。

在本教學課程中，您將了解如何：

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

您可以在[dotnet/machinelearning 範例](https://github.com/dotnet/machinelearning-samples)存放庫中找到本教學課程的原始程式碼。

## <a name="pre-requisites"></a>先決條件

如需必要條件和安裝指示清單，請瀏覽[模型產生器安裝指南](../how-to-guides/install-model-builder.md)。

## <a name="create-a-razor-pages-application"></a>建立 Razor Pages 應用程式

1. 建立**ASP.NET Core Razor Pages 應用程式**。

    1. 開啟 Visual Studio，然後從功能表列選取 [檔案] **> [新增 > 專案**]。
    1. 在 [新增專案] 對話方塊中，選取 [Visual C#] 節點，然後選取 [Web] 節點。
    1. 然後，選取 [ASP.NET Core Web 應用程式] 專案範本。
    1. 在 [**名稱**] 文字方塊中，輸入 "SentimentRazor"。
    1. 預設應該會核取 [**為方案建立目錄**] 核取方塊。 如果不是這種情況，請檢查它。
    1. 選取 [確定] 按鈕。
    1. 在顯示不同類型 ASP.NET Core 專案的視窗中，選擇 [ **Web 應用程式**]，然後選取 [**確定]** 按鈕。

## <a name="prepare-and-understand-the-data"></a>準備並了解資料

下載[維琪百科 detox 資料集](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)。 當網頁開啟時，以滑鼠右鍵按一下頁面，選取 [**另存**新檔]，然後將檔案儲存在您電腦上的任何位置。

*維琪百科-detox-250-line-data.tsv*中的每個資料列都代表使用者在維琪百科上留下的不同評論。 第一個資料行代表文字的情感（0是非有毒，1是有毒），而第二個數據行代表使用者所留下的批註。 資料行是以 tab 鍵分隔。 資料看起來如下所示：

| 情感 | SentimentText |
| :---: | :---: |
1 | = = 「強制」 = = Dude，您可以將 carl 的上傳放回，或其他。
1 | = = OK！ = = IM 即將 VANDALIZE 萬用字元 WIKI 然後!!!
0 | 我希望這有説明。

## <a name="choose-a-scenario"></a>選擇案例

![Visual Studio 中的模型產生器 wizard](./media/sentiment-analysis-model-builder/model-builder-screen.png)

若要定型您的模型，您需要從模型產生器所提供的可用機器學習服務案例清單中選取。

1. 在**方案總管**中，以滑鼠右鍵按一下*SentimentRazor*專案，然後選取 [**新增** >  **Machine Learning**]。
1. 在此範例中，案例是情感分析。 在模型產生器工具的*情節*步驟中，選取 [**情感分析**] 案例。

## <a name="load-the-data"></a>載入資料

模型產生器會接受來自兩個來源、SQL Server 資料庫或本機`csv`檔案或`tsv`格式的資料。

1. 在模型產生器工具的資料步驟中，從資料來源下拉式清單中選取 [檔案]。
1. 選取 [**選取**檔案] 文字方塊旁的按鈕，然後使用 [檔案瀏覽器] 流覽並選取 [*維琪百科-detox-250-line-data.tsv* ] 檔案。
1. 在 [**要預測的資料行（標籤）** ] 下拉式清單中選擇 [**情感**]。
1. 保留 [**輸入資料行（功能）** ] 下拉式清單的預設值。
1. 選取 [**定型**] 連結，以移至模型產生器工具中的下一個步驟。

## <a name="train-the-model"></a>將模型定型

在本教學課程中用來定型價格預測模型的機器學習工作是二元分類。 在模型定型程式期間，模型產生器會使用不同的二進位分類演算法和設定來訓練不同的模型，以尋找資料集最佳的執行模型。

定型模型所需要的時間會與資料量成比例。 「模型產生器」會根據您的資料來源大小，自動選取要定型的預設值 **（秒）** 。

1. 雖然模型產生器會將 [**要定型的時間] 值（秒）** 設定為10秒，但將它增加為30秒。 定型一段較長的時間，可讓模型產生器在搜尋最佳模型時，探索更多的演算法和參數組合。
1. 選取 [開始定型]。

    在整個定型程序期間，進度資料會顯示在定型步驟的 `Progress` 區段中。

    - [狀態] 會顯示定型程序的完成狀態。
    - [最佳正確性] 會顯示模型產生器到目前為止所找到執行效能最佳模型的正確性。 正確性越高，表示模型針對測試資料的預測越正確。
    - [最佳演算法] 會顯示模型產生器到目前為止所執行演算法中效能最佳的演算法名稱。
    - [上一個演算法] 會顯示模型產生器最近一次用來定型模型的演算法名稱。

1. 定型完成後，請選取 [**評估**] 連結以移至下一個步驟。

## <a name="evaluate-the-model"></a>評估模型

定型步驟之結果將會是具備最佳效能的單一模型。 在模型產生器工具的評估步驟中，[輸出] 區段會包含最佳**模型**專案中最佳執行模型所使用的演算法，以及最佳**模型精確度**中的計量。 此外，還會具備一個摘要表，其中包含前五個模型及其計量。

若您不滿意您的正確性計量，可嘗試及改善模型正確性的一些簡單方法為增加定型模型的時間，或是使用更多資料。 否則，請選取 [程式**代碼**] 連結，以移至模型產生器工具中的最後一個步驟。

## <a name="add-the-code-to-make-predictions"></a>新增程式碼來進行預測

定型程序的結果會建立兩個專案。

### <a name="reference-the-trained-model"></a>參考定型的模型

1. 在模型產生器工具的程式*代碼*步驟中，選取 [**加入專案**]，將自動產生的專案加入至方案。

    下列專案應該會出現在**方案總管**中：

    - *SentimentRazorML. consoleapp.exe*：包含模型定型和預測程式碼的 .NET Core 主控台應用程式。
    - *SentimentRazorML。模型*：.NET Standard 類別庫，其中包含定義輸入和輸出模型資料之架構的資料模型，以及定型期間所儲存的最佳執行模型版本。

    在本教學課程中，只會使用*SentimentRazorML 模型*專案，因為會在*SentimentRazor* web 應用程式中，而不是在主控台中進行預測。 雖然*SentimentRazorML*不會用於計分，但它可以用來在稍後使用新資料重新定型模型。 不過，重新定型已超出本教學課程的範圍。

### <a name="configure-the-predictionengine-pool"></a>設定 PredictionEngine 集區

若要進行單一預測，您必須建立[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)。 [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) 不是安全執行緒。 此外，您必須在應用程式內需要的任何地方建立它的實例。 當您的應用程式成長時，此進程可能會變得難以管理。 為了改善效能和執行緒安全性，請使用相依性插入和 `PredictionEnginePool` 服務的組合，這會建立[@no__t 4](xref:Microsoft.ML.PredictionEngine%602)物件的[@no__t 2](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) ，以便在整個應用程式中使用。

1. 安裝*Microsoft.Extensions.ML* NuGet 套件：

    1. 在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選取 [管理 NuGet 套件]。
    1. 選擇 "nuget.org" 作為套件來源。
    1. 選取 [**流覽**] 索引標籤，並搜尋**Microsoft.Extensions.ML**。
    1. 在清單中選取套件，然後選取 [**安裝**] 按鈕。
    1. 選取 [**預覽變更**] 對話方塊上的 [**確定]** 按鈕
    1. 如果您同意所列套件的授權條款，請選取 [**授權接受**] 對話方塊上的 [**我接受**] 按鈕。

1. 開啟*SentimentRazor*專案中的*Startup.cs*檔案。
1. 新增下列 using 語句，以參考*Microsoft.Extensions.ML* NuGet 封裝和*SentimentRazorML*專案：

    ```csharp
    using System.IO;
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

1. 建立全域變數來儲存定型模型檔案的位置。

    ```csharp
    private readonly string _modelPath;
    ```

1. 模型檔案會連同應用程式的元件檔案一起儲存在組建目錄中。 若要讓它更容易存取，請建立一個在`GetAbsolutePath` `Configure`方法之後呼叫的 helper 方法

    ```csharp
    public static string GetAbsolutePath(string relativePath)
    {
        FileInfo _dataRoot = new FileInfo(typeof(Program).Assembly.Location);
        string assemblyFolderPath = _dataRoot.Directory.FullName;

        string fullPath = Path.Combine(assemblyFolderPath, relativePath);
        return fullPath;
    }    
    ```

1. 在類別的函式中使用`GetAbsolutePath`方法，以`_modelPath`設定 `Startup` 。

    ```csharp
    _modelPath = GetAbsolutePath("MLModel.zip");
    ```

1. 在方法中，為您的應用程式設定： `PredictionEnginePool` `ConfigureServices`

    ```csharp
    services.AddPredictionEnginePool<ModelInput, ModelOutput>()
            .FromFile(_modelPath);
    ```

### <a name="create-sentiment-analysis-handler"></a>建立情感分析處理常式

預測將會在應用程式的主頁面中進行。 因此，接受使用者輸入並使用`PredictionEnginePool`傳回預測的方法必須加入。

1. 開啟位於*Pages*目錄中的*Index.cshtml.cs*檔案，並新增下列 using 語句：

    ```csharp
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

    若要使用在`PredictionEnginePool` `Startup`類別中設定的，您必須將它插入您想要使用它的模型的函式中。

1. 新增變數以參考`PredictionEnginePool` `IndexModel`類別內的。

    ```csharp
    private readonly PredictionEnginePool<ModelInput, ModelOutput> _predictionEnginePool;
    ```

1. 在`IndexModel`類別中建立一個函式，並`PredictionEnginePool`將服務插入其中。

    ```csharp
    public IndexModel(PredictionEnginePool<ModelInput, ModelOutput> predictionEnginePool)
    {
        _predictionEnginePool = predictionEnginePool;
    }    
    ```

1. 建立方法處理常式， `PredictionEnginePool`以使用從網頁接收的使用者輸入進行預測。

    1. 在`OnGet`方法下方，建立名為的新方法`OnGetAnalyzeSentiment`

        ```csharp
        public IActionResult OnGetAnalyzeSentiment([FromQuery] string text)
        {

        }
        ```

    1. 在方法內，如果使用者輸入空白或為 null，則傳回中性情感。 `OnGetAnalyzeSentiment`

        ```csharp
        if (String.IsNullOrEmpty(text)) return Content("Neutral");
        ```

    1. 指定有效的輸入，建立的新實例`ModelInput`。

        ```csharp
        var input = new ModelInput { SentimentText = text };
        ```

    1. `PredictionEnginePool`使用來預測情感。

        ```csharp
        var prediction = _predictionEnginePool.Predict(input);
        ```

    1. 使用下列程式`bool`代碼，將預測值轉換成有毒或 not 有毒。

        ```csharp
        var sentiment = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";
        ```

    1. 最後，將情感回到網頁。

        ```csharp
        return Content(sentiment);
        ```

### <a name="configure-the-web-page"></a>設定網頁

所傳回`OnGetAnalyzeSentiment`的結果會動態顯示`Index`在網頁上。

1. 開啟*Pages*目錄中的*Index. cshtml*檔案，並以下列程式碼取代其內容：

    [!code-cshtml [IndexPage](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml)]

1. 接下來，將 css 樣式程式碼新增至*wwwroot\css*目錄中的*網站 .css*頁面結尾：

    [!code-css [CssStyling](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/css/site.css#L61-L105)]

1. 之後，請新增`OnGetAnalyzeSentiment`程式碼，以將網頁的輸入傳送至處理常式。

    1. 在位於*wwwroot\js*目錄中的`getSentiment` *網站 .js*檔案中，建立名為的函式，以向`OnGetAnalyzeSentiment`處理常式的使用者輸入提出 GET HTTP 要求。

        [!code-javascript [GetSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L5-L10)]

    1. 如下所示，新增另一個`updateMarker`名為的函式，以動態方式在情感預測時更新網頁上標記的位置。

        [!code-javascript [UpdateMarkerMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L12-L15)]

    1. 建立名`updateSentiment`為的事件處理常式函式，以取得使用者的輸入、使用`getSentiment`函`OnGetAnalyzeSentiment`式將它傳送至函式，並使用`updateMarker`函數更新標記。

        [!code-javascript [UpdateSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L17-L34)]

    1. 最後，註冊事件處理常式，並`textarea` `id=Message`使用屬性將它系結至元素。

        [!code-javascript [UpdateSentimentEvtHandler](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L36)]

## <a name="run-the-application"></a>執行應用程式

現在您已設定好應用程式，請執行應用程式，以在瀏覽器中啟動。

當應用程式啟動時，進入「模型產生器」*是很酷的！* 在文字區域中。 所顯示的預測情感應該*不會有毒*。

![使用預測的情感視窗執行視窗](./media/sentiment-analysis-model-builder/web-app.png)

如果您稍後需要參考模型產生器的專案，您可以在`C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools`目錄中找到它們。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您將了解如何：
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

- [模型建立器案例](../automate-training-with-model-builder.md#scenarios)
- [二元分類](../resources/glossary.md#binary-classification)
- [二元分類模型計量](../resources/metrics.md#metrics-for-binary-classification)
