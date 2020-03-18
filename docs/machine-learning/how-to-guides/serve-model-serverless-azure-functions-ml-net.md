---
title: 將模型部署到 Azure Functions
description: 使用 Azure Functions 在網際網路上提供 ML.NET 情感分析機器學習模型以進行預測
ms.date: 02/21/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 33afd568bb12b855a3888bec31f2e9bbc3c720da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "77628666"
---
# <a name="deploy-a-model-to-azure-functions"></a>將模型部署到 Azure Functions

了解如何部署預先定型的 ML.NET 機器學習模型，以使用 Azure Functions 無伺服器環境透過 HTTP 進行預測。

> [!NOTE]
> 此示例運行`PredictionEnginePool`服務的預覽版本。

## <a name="prerequisites"></a>必要條件

- [Visual Studio 2017 版本 15.6 或更高版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)，安裝了".NET 核心跨平臺開發"工作負載和"Azure 開發"。
- [Azure 函數工具](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- Powershell
- 預先定型的模型。 使用 [ML.NET 情感分析教學課程](../tutorials/sentiment-analysis.md)來建置您自己的模型，或是下載這個[預先定型的情感分析機器學習模型](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)

## <a name="azure-functions-sample-overview"></a>Azure 函數示例概述

此示例是**C# HTTP 觸發器 Azure 函數應用程式**，該應用程式使用預先訓練的二進位分類模型將文本的情緒分類為正或負。 Azure 函數提供了一種在雲中的託管無伺服器環境中大規模運行小段代碼的簡單方法。 此示例的代碼可以在 GitHub 上的[dotnet/機器學習示例](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction)存儲庫中找到。

## <a name="create-azure-functions-project"></a>建立 Azure Functions 專案

1. 開啟 Visual Studio 2017。 **從功能表**欄中選擇 **"檔** > **新專案** > "。 在 [新增專案]**** 對話方塊中，選取 [Visual C#]**** 節點，然後選取 [雲端]**** 節點。 然後選取 [Azure Functions]**** 專案範本。 在 [名稱]**** 文字方塊中，輸入 "SentimentAnalysisFunctionsApp"，然後選取 [確定]**** 按鈕。
1. 在 [新增專案]**** 對話方塊中，開啟專案選項上方的下拉式清單，然後選取 [Azure Functions v2 (.NET Core)]****。 然後，選取 [Http 觸發程序]**** 專案，然後選取 [確定]**** 按鈕。
1. 在您的專案中建立名為 *MLModels* 的目錄，以儲存您的模型：

    在 [方案總管]**** 中，於您的專案上按一下滑鼠右鍵，然後選取 [新增]**** > [新增資料夾]****。 輸入 "MLModels"，然後按 Enter。

1. 安裝**Microsoft.ML NuGet 包**版本**1.3.1**：

    在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]****。 選擇 "nuget.org" 作為 [套件來源]，選取 [瀏覽] 索引標籤、搜尋 **Microsoft.ML**、從清單中選取該套件，然後選取 [安裝]**** 按鈕。 在 [預覽變更]**** 對話方塊上，選取 [確定]**** 按鈕，然後在 [授權接受]**** 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]****。

1. 安裝 **Microsoft.Azure.Functions.Extensions NuGet 套件**：

    在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]****。 選擇 "nuget.org" 作為 [套件來源]、選取 [瀏覽] 索引標籤、搜尋 **Microsoft.Azure.Functions.Extensions**、從清單中選取該套件，然後選取 [安裝]**** 按鈕。 在 [預覽變更]**** 對話方塊上，選取 [確定]**** 按鈕，然後在 [授權接受]**** 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]****。

1. 安裝**Microsoft.Extensions.ML NuGet 包**版本**0.15.1**：

    在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]****。 選擇 "nuget.org" 作為 [套件來源]、選取 [瀏覽] 索引標籤、搜尋 **Microsoft.Extensions.ML**、從清單中選取該套件，然後選取 [安裝]**** 按鈕。 在 [預覽變更]**** 對話方塊上，選取 [確定]**** 按鈕，然後在 [授權接受]**** 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]****。

1. 安裝**Microsoft.NET.Sdk.函數 NuGet 包**版本**1.0.31**：

    在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]****。 選擇"nuget.org"作為包源，選擇"已安裝"選項卡，搜索**Microsoft.NET.Sdk.功能**，在清單中選擇該包，從"版本"下拉清單中選擇**1.0.31，** 然後選擇 **"更新**"按鈕。 在 [預覽變更]**** 對話方塊上，選取 [確定]**** 按鈕，然後在 [授權接受]**** 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]****。

## <a name="add-pre-trained-model-to-project"></a>將預先定型的模型新增到專案

1. 將預先建置的模型複製到 *MLModels* 目錄。
1. 在 [方案總管] 中，以滑鼠右鍵按一下您預先建置的模型檔案，並選取 [內容]****。 在 **"高級"** 下，將 **"複製到輸出目錄**"的值更改為 **"如果更新"，則將其更改為"複製**"。

## <a name="create-azure-function-to-analyze-sentiment"></a>建立 Azure Function 來分析情感

建立用來預測情緒的類別。 將新類別新增至專案：

1. 在 [方案總管]**** 中，以滑鼠右鍵按一下專案，然後選取 [新增]**** > [新項目]****。

1. 在 [新增項目]**** 對話方塊中，選取 [Azure Function]****，然後將 [名稱]**** 欄位變更為 *AnalyzeSentiment.cs*。 接著，選取 [新增]**** 按鈕。

1. 在 [新增 Azure 函式]**** 對話方塊中，選取 [Http 觸發程序]****。 然後，選取 [確定]**** 按鈕。

    *AnalyzeSentiment.cs* 檔案隨即在程式碼編輯器中開啟。 將下列 `using` 陳述式新增到 *AnalyzeSentiment.cs* 的頂端：

    [!code-csharp [AnalyzeUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L1-L11)]

    根據預設，`AnalyzeSentiment` 類別為 `static`。 請務必從類別定義移除 `static` 關鍵字。

    ```csharp
    public class AnalyzeSentiment
    {

    }
    ```

## <a name="create-data-models"></a>建立資料模型

您必須為輸入資料和預測建立一些類別。 將新類別新增至專案：

1. 在專案中創建名為*DataModel*的目錄以保存資料模型：在解決方案資源管理器中，按右鍵專案並選擇"**添加>新資料夾**"。 輸入 "DataModels"，然後按 Enter。
2. 在解決方案資源管理器中，按右鍵 *"資料模型"* 目錄，然後選擇"**添加>新專案**。
3. 在 [新增項目]**** 對話方塊中，選取 [類別]****，然後將 [名稱]**** 欄位變更為 *SentimentData.cs*。 接著，選取 [新增]**** 按鈕。

    *SentimentData.cs* 檔案隨即在程式碼編輯器中開啟。 將下列 using 陳述式新增至 *SentimentData.cs* 頂端：

    [!code-csharp [SentimentDataUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L1)]

    刪除現有類定義並將以下代碼添加到*SentimentData.cs*檔中：

    [!code-csharp [SentimentData](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L5-L13)]

4. 在解決方案資源管理器中，按右鍵 *"資料模型"* 目錄，然後選擇"**添加>新專案**。
5. 在 [加入新項目]**** 對話方塊中，選取 [類別]****，然後將 [名稱]**** 欄位變更為 *SentimentPrediction.cs*。 接著，選取 [新增]**** 按鈕。 *SentimentPrediction.cs* 檔案隨即在程式碼編輯器中開啟。 將下列 using 陳述式新增至 *SentimentPrediction.cs* 頂端：

    [!code-csharp [SentimentPredictionUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L1)]

    移除現有的類別定義，然後將下列程式碼新增至 *SentimentPrediction.cs* 檔案：

    [!code-csharp [SentimentPrediction](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L5-L14)]

    `SentimentPrediction` 會從 `SentimentData` 繼承，後者會在 `SentimentText` 屬性中提供原始資料的存取，以及由模型產生的輸出。

## <a name="register-predictionenginepool-service"></a>登錄 PredictionEnginePool 服務

要進行單個預測，必須創建 一個[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)。 [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)不是執行緒安全的。 此外，您必須在應用程式中需要它的地方創建它的實例。 隨著應用程式的增長，此過程可能會變得難以管理。 為提高性能和執行緒安全性，請使用依賴項注入和服務`PredictionEnginePool`的組合，該服務將創建一個[`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601)[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)物件，供整個應用程式使用。

如果要瞭解有關[依賴項注入](https://en.wikipedia.org/wiki/Dependency_injection)的詳細資訊，以下連結將提供更多資訊。

1. 在 [方案總管]**** 中，以滑鼠右鍵按一下專案，然後選取 [新增]**** > [新項目]****。
1. 在 [新增項目]**** 對話方塊中，選取 [類別]****，然後將 [名稱]**** 欄位變更為 *Startup.cs*。 接著，選取 [新增]**** 按鈕。
1. 將以下使用語句添加到*Startup.cs*的頂部：

    [!code-csharp [StartupUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L1-L6)]

1. 刪除 using 語句下方的現有代碼，並添加以下代碼：

    ```csharp
    [assembly: FunctionsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        public class Startup : FunctionsStartup
        {

        }
    }
    ```

1. 定義變數以存儲應用正在運行的環境和模型位於`Startup`類內的檔路徑

    [!code-csharp [DefineStartupVars](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L13-L14)]

1. 在下面，創建一個建構函式來設置`_environment`和`_modelPath`變數的值。 當應用程式在本地運行時，預設環境是*開發*。

    [!code-csharp [StartupCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L16-L29)]

1. 然後，添加調用`Configure`的新方法以在建構函式`PredictionEnginePool`下方註冊服務。

    [!code-csharp [ConfigureServices](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L31-L35)]

在高級別上，此代碼會自動初始化物件和服務，以便以後在應用程式請求時使用，而不必手動執行此操作。

機器學習模型不是靜態的。 隨著新的培訓資料可用，模型將重新訓練和重新部署。 將最新版本的模型引入應用程式的一種方法是重新部署整個應用程式。 但是，這引入了應用程式停機時間。 該服務`PredictionEnginePool`提供了一種機制，用於重新載入更新的模型，而無需關閉應用程式。

將`watchForChanges`參數設置為`true`，並`PredictionEnginePool`啟動[`FileSystemWatcher`](xref:System.IO.FileSystemWatcher)偵聽檔案系統更改通知並在檔發生更改時引發事件。 這提示 自動`PredictionEnginePool`重新載入模型。

參數標識模型，`modelName`以便每個應用程式可以在更改時重新載入多個模型。

> [!TIP]
> 或者，在使用遠端存放`FromUri`的模型時，可以使用 該方法。 不要監視檔更改的事件，而是`FromUri`輪詢遠端位置以進行更改。 輪詢間隔預設為 5 分鐘。 您可以根據應用程式的要求增加或減少輪詢間隔。 在下面的代碼示例中，`PredictionEnginePool`每分鐘輪詢存儲在指定 URI 中的模型。
>
>```csharp
>builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="load-the-model-into-the-function"></a>將模型載入函式

將下列程式碼插入 *AnalyzeSentiment* 類別：

[!code-csharp [AnalyzeCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L18-L24)]

此程式碼會透過將 `PredictionEnginePool` 傳遞到您透過相依性插入所取得的函式建構函式來指派它。

## <a name="use-the-model-to-make-predictions"></a>使用模型進行預測

使用下列程式碼取代 *AnalyzeSentiment* 類別中 *Run* 方法的現有實作：

[!code-csharp [AnalyzeRunMethod](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L26-L45)]

`Run` 方法執行時，來自 HTTP 請求的傳入資料會還原序列化，並用來作為 `PredictionEnginePool` 的輸入。 然後`Predict`調用 該方法，使用`SentimentAnalysisModel``Startup`類中的註冊進行預測，如果成功，則返回結果返回給使用者。

## <a name="test-locally"></a>本機測試

一切都設定好後，就可以開始測試應用程式：

1. 執行應用程式
1. 開啟 Powershell 並在提示字元中輸入下列程式碼，其中 PORT 是正在執行您應用程式的連接埠。 一般來說，連接埠是 7071。

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    如果成功，輸出看起來應該類似下列文字：

    ```powershell
    Negative
    ```

恭喜！ 您已成功提供您的模型，以使用 Azure Function 在網際網路上進行預測。

## <a name="next-steps"></a>後續步驟

- [部署到 Azure](/azure/azure-functions/functions-develop-vs#publish-to-azure)
