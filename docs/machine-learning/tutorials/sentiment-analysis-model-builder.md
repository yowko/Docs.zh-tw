---
title: 教程:分析情緒 - 二進位分類
description: 本教程演示如何創建 Razor Pages 應用程式,該應用程式從網站評論中對情緒進行分類並採取適當的操作。 二進位情緒分類器在可視化工作室中使用模型生成器。
ms.date: 11/21/2019
author: luisquintanilla
ms.author: luquinta
ms.topic: tutorial
ms.custom: mvc,mlnet-tooling
ms.openlocfilehash: 7761240055c90ae9c713b1c460e9e83316d256f9
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278947"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-in-a-web-application-using-mlnet-model-builder"></a>教學:使用模型產生器分析 Web 應用程式中網站評論的情緒ML.NET

瞭解如何在 Web 應用程式內即時分析來自評論的情緒。

本教程介紹如何創建一個ASP.NET核心剃刀頁面應用程式,該應用程式即時從網站評論中對情緒進行分類。

在本教學課程中，您會了解如何：

> [!div class="checklist"]
>
> - 建立ASP.NET核心剃鬚刀頁面應用程式
> - 準備並了解資料
> - 選擇案例
> - 載入資料
> - 將模型定型
> - 評估模型
> - 使用模型來進行預測

> [!NOTE]
> 模型產生器目前為預覽版。

您可以在[dotnet/機器學習範例](https://github.com/dotnet/machinelearning-samples)儲存庫中找到本教程的原始程式碼。

## <a name="pre-requisites"></a>必要條件

如需必要條件和安裝指示清單，請瀏覽[模型產生器安裝指南](../how-to-guides/install-model-builder.md)。

## <a name="create-a-razor-pages-application"></a>建立剃刀頁面應用程式

1. 建立**ASP.NET 核心剃刀頁應用程式**。

    1. 打開視覺化工作室,並從菜單欄中選擇**檔>"新>專案**"。
    1. 在 [新增專案] 對話方塊中，選取 [Visual C#]**** 節點，然後選取 [Web]**** 節點。
    1. 然後，選取 [ASP.NET Core Web 應用程式]**** 專案範本。
    1. 在 **「名稱**」文本框中,鍵入"情緒剃鬚刀"。
    1. 確保**未選取****同一目錄中的放置解決方案和專案**(VS 2019),或**選中****「創建解決方案目錄**」(VS 2017)。
    1. 選擇「**確定」** 按鈕。
    1. 在視窗中選擇**顯示**不同類型的ASP.NET核心項目,然後選擇 **「確定**」按鈕。

## <a name="prepare-and-understand-the-data"></a>準備並了解資料

下載[維琪百科排毒資料集](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)。 打開網頁時,右鍵單擊頁面,選擇 **「保存為」,** 並將檔保存在電腦上的任意位置。

*維琪百科-排毒-250行數據.tsv*數據集中的每一行代表使用者在維琪百科上留下的不同評論。 第一列表示文本的情緒(0 無毒,1 是有毒的),第二列表示使用者留下的註釋。 列由選項卡分隔。 資料如下所示:

| 情感 | SentimentText |
| :---: | :---: |
1 | [RUDE] 杜德,你粗魯地把卡爾的照片上傳回來,否則。
1 | • 正常! •我要破壞野生維琪然後!!!
0 | 我希望這會有所説明。

## <a name="choose-a-scenario"></a>選擇案例

![視覺化工作室中的模型產生器精靈](./media/sentiment-analysis-model-builder/model-builder-screen.png)

若要定型您的模型，您需要從模型產生器所提供的可用機器學習服務案例清單中選取。

1. 在**解決方案資源管理器**中,右鍵按*下 「情緒剃鬚刀*」專案,然後選擇「**添加** > **機器學習**」。
1. 對於此示例,方案是情緒分析。 在模型生成器工具*的方案*步驟中,選擇**情緒分析**方案。

## <a name="load-the-data"></a>載入資料

模型生成器接受來自兩個源的數據:SQL Server 資料庫或`csv`本地`tsv`檔案( 或格式)。

1. 在模型產生器工具的資料步驟中，從資料來源下拉式清單中選取 [檔案]****。
1. 選擇「**選擇檔案**文字框」 旁邊的按鈕,並使用檔案資源管理器瀏覽並選擇*wikipedia-detox-250 行資料.tsv*檔。
1. 在 **「要預測(標籤)** 下拉清單的列中選擇 **「情緒**」。
1. 保留**輸入列(要素)** 下拉的預設值。
1. 選擇 **「訓練」** 連結以移動到模型生成器工具中的下一步。

## <a name="train-the-model"></a>將模型定型

本教程中用於訓練情緒分析模型的機器學習任務是二進位製分類。 在模型培訓過程中,模型生成器使用不同的二進位分類演演演算法和設置訓練單獨的模型,以查找數據集的最佳模型。

定型模型所需要的時間會與資料量成比例。 模型生成器根據資料來源的大小自動選擇**時間訓練時間(秒)** 的預設值。

1. 儘管模型生成器將**訓練時間(秒)** 的值設置為 10 秒,但將其增加到 30 秒。 經過更長時間的培訓,模型構建器可以探索更多演演演算法和參數組合,以查找最佳模型。
1. 選取 [開始定型]****。

    在整個定型程序期間，進度資料會顯示在定型步驟的 `Progress` 區段中。

    - [狀態] 會顯示定型程序的完成狀態。
    - [最佳正確性] 會顯示模型產生器到目前為止所找到執行效能最佳模型的正確性。 正確性越高，表示模型針對測試資料的預測越正確。
    - [最佳演算法] 會顯示模型產生器到目前為止所執行演算法中效能最佳的演算法名稱。
    - [上一個演算法] 會顯示模型產生器最近一次用來定型模型的演算法名稱。

1. 培訓完成後,選擇**評估**鏈接以移動到下一步。

## <a name="evaluate-the-model"></a>評估模型

訓練步驟的結果將是一個性能最好的模型。 在模型生成器工具的計算步驟中,輸出部分將包含**最佳模型**條目中性能最佳的模型使用的演演演算法以及**最佳模型精度**中的指標。 此外,還顯示了包含前五個模型及其指標的匯總表。

如果您對準確性指標不滿意,則嘗試提高模型準確性的一些簡單方法是增加訓練模型或使用更多數據的時間。 否則,選擇**代碼**連結以移動到模型生成器工具中的最後一步。

## <a name="add-the-code-to-make-predictions"></a>新增程式碼來進行預測

定型程序的結果會建立兩個專案。

### <a name="reference-the-trained-model"></a>參考經過培訓的模型

1. 在模型生成器工具*的代碼*步驟中,選擇 **「添加專案」** 以將自動生成的專案添加到解決方案。

    以下項目應出現在**解決方案資源管理員**中:

    - *情緒剃鬚刀.控制台應用程式*:一個 .NET 核心控制台應用程式,其中包含模型訓練和預測代碼。
    - *情緒剃鬚刀ML.模型*:.NET 標準類庫,其中包含定義輸入和輸出模型數據的架構的數據模型,以及在培訓期間保存的保存版本最佳性能模型。

    在本教程中,僅使用*情緒RazorML.Model*項目,因為預測將在*情緒剃鬚刀*Web 應用程式中而不是在控制台中進行。 儘管*情緒剃鬚刀ML.ConsoleApp*不會用於評分,但它可用於在以後使用新數據重新訓練模型。 不過,再培訓不在本教程的範圍之內。

### <a name="configure-the-predictionengine-pool"></a>設定預測引擎池

要進行單一預測,必須建立一個<xref:Microsoft.ML.PredictionEngine%602>。 <xref:Microsoft.ML.PredictionEngine%602> 不是安全執行緒。 此外,您必須在應用程式中需要它的地方創建它的實例。 隨著應用程式的增長,此過程可能會變得難以管理。 為提高性能和線程安全性,請使用依賴項注入和服務`PredictionEnginePool`的組合,該服務將創建一個<xref:Microsoft.Extensions.ObjectPool.ObjectPool%601><xref:Microsoft.ML.PredictionEngine%602>物件,供整個應用程式使用。

1. 安裝*Microsoft.Extensions.ML* NuGet 套件:

    1. 在**解決方案資源管理員**中,右鍵單擊專案並選擇 **「管理 NuGet 包**」 。。
    1. 選擇「nuget.org」作為包源。
    1. 選擇「**瀏覽**」選項卡並搜尋**Microsoft.Extensions.ML**。
    1. 選擇清單中的套件,然後選擇 **「安裝**」按鈕。
    1. 選擇 **「預覽變更**」 對話框上的 **「 確定**」 按鈕
    1. 如果您同意列出的套件的許可證條款,請選擇 **「許可證接受」** 對話方塊上的 **「接受」** 按鈕。

1. 打開 *「情緒剃鬚刀*」專案中*的Startup.cs*檔。
1. 新增以下使用敘述以引用nuGet 包和*情緒RazorML.model*專案*Microsoft.Extensions.ML:*

    ```csharp
    using System.IO;
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

1. 建立全域變數以存儲已訓練的模型檔的位置。

    ```csharp
    private readonly string _modelPath;
    ```

1. 模型檔與應用程式的程式集檔一起存儲在生成目錄中。 為了便於存取,請建立一個`GetAbsolutePath``Configure`在 方法之後呼叫的說明器方法

    ```csharp
    public static string GetAbsolutePath(string relativePath)
    {
        FileInfo _dataRoot = new FileInfo(typeof(Program).Assembly.Location);
        string assemblyFolderPath = _dataRoot.Directory.FullName;

        string fullPath = Path.Combine(assemblyFolderPath, relativePath);
        return fullPath;
    }
    ```

1. 使用`GetAbsolutePath`類別建構函`Startup`式中的方法`_modelPath`設定 。

    ```csharp
    _modelPath = GetAbsolutePath("MLModel.zip");
    ```

1. 在`PredictionEnginePool`方法中為應用程式設定`ConfigureServices`的 。

    ```csharp
    services.AddPredictionEnginePool<ModelInput, ModelOutput>()
            .FromFile(_modelPath);
    ```

### <a name="create-sentiment-analysis-handler"></a>建立情緒分析處理程式

將在應用程式的主頁內進行預測。 因此,需要添加一個獲取使用者輸入並使用`PredictionEnginePool`返回預測的方法。

1. 開啟*頁面'* 目錄中*的Index.cshtml.cs*檔,並使用敘述加入以下內容:

    ```csharp
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

    為了在類別使用配置`PredictionEnginePool`,`Startup`必須將其注入到要使用它的模型的建構函數中。

1. 添加變數以引用類`PredictionEnginePool`內部。 `IndexModel`

    ```csharp
    private readonly PredictionEnginePool<ModelInput, ModelOutput> _predictionEnginePool;
    ```

1. 在`IndexModel`類中創建一個構造函數`PredictionEnginePool`, 並將服務注入其中。

    ```csharp
    public IndexModel(PredictionEnginePool<ModelInput, ModelOutput> predictionEnginePool)
    {
        _predictionEnginePool = predictionEnginePool;
    }
    ```

1. 創建一個方法處理程式,使用`PredictionEnginePool`從從網頁收到的使用者輸入進行預測。

    1. 在方法`OnGet`下方,創建一個稱為`OnGetAnalyzeSentiment`

        ```csharp
        public IActionResult OnGetAnalyzeSentiment([FromQuery] string text)
        {

        }
        ```

    1. 在`OnGetAnalyzeSentiment`方法內,如果來自用戶的輸入為空或為空,則返回*中性*情緒。

        ```csharp
        if (String.IsNullOrEmpty(text)) return Content("Neutral");
        ```

    1. 給定有效的輸入,請建立新實體 。`ModelInput`

        ```csharp
        var input = new ModelInput { SentimentText = text };
        ```

    1. 使用`PredictionEnginePool`預測情緒。

        ```csharp
        var prediction = _predictionEnginePool.Predict(input);
        ```

    1. 使用以下代碼`bool`將預測值轉換為有毒或無毒值。

        ```csharp
        var sentiment = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";
        ```

    1. 最後,將情緒返回到網頁。

        ```csharp
        return Content(sentiment);
        ```

### <a name="configure-the-web-page"></a>設定網頁

返回的結果`OnGetAnalyzeSentiment`將動態顯示`Index`在網頁上。

1. 開啟*Pages*目錄中的*Index.cshtml*檔案,並將其內容取代為以下代碼:

    [!code-cshtml [IndexPage](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml)]

1. 接下來,在*wwwroot_css*目錄中將 css 樣式代碼添加到*site.css*頁面的末尾:

    [!code-css [CssStyling](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/css/site.css#L61-L105)]

1. 之後,添加代碼以將網頁中的輸入發送到`OnGetAnalyzeSentiment`處理程式。

    1. 在位於*wwwroot_js*目錄中的*site.js*檔`getSentiment`中,創建一個調用函數,`OnGetAnalyzeSentiment`以便使用使用者輸入 處理程式發出 GET HTTP 請求。

        [!code-javascript [GetSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L5-L10)]

    1. 在此下方,添加另一個`updateMarker`調用函數,以動態更新標記在網頁上的位置,因為情緒預測。

        [!code-javascript [UpdateMarkerMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L12-L15)]

    1. 創建一個事件處理程式函數`updateSentiment`,用於從使用者獲取輸入,`OnGetAnalyzeSentiment``getSentiment`使用 函數將其發送到函數,`updateMarker`並使用函數更新標記。

        [!code-javascript [UpdateSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L17-L34)]

    1. 最後,註冊事件處理程式並將其綁定到具有`textarea``id=Message`屬性的元素。

        [!code-javascript [UpdateSentimentEvtHandler](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L36)]

## <a name="run-the-application"></a>執行應用程式

現在,您的應用程式已設置,請運行應用程式,該應用程式應在瀏覽器中啟動。

當應用程式啟動時,輸入*模型生成器是很酷的!* 到文本區域。 顯示的預測情緒應該*不是有毒的*。

![使用預測情緒視窗執行視窗](./media/sentiment-analysis-model-builder/web-app.png)

如果需要在以後引用模型產生器產生的項目,可以在其他解決方案中找到這些專案`C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools`。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已了解如何：
> [!div class="checklist"]
>
> - 建立ASP.NET核心剃鬚刀頁面應用程式
> - 準備並了解資料
> - 選擇案例
> - 載入資料
> - 將模型定型
> - 評估模型
> - 使用模型來進行預測

### <a name="additional-resources"></a>其他資源

若要深入了解此教學課程中提及的主題，請瀏覽下列資源：

- [模型建立器案例](../automate-training-with-model-builder.md#scenario)
- [二進位類別](../resources/glossary.md#binary-classification)
- [二進位類別模型指標](../resources/metrics.md#evaluation-metrics-for-binary-classification)
