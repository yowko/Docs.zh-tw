---
title: 在 ASP.NET Core Web API 中部署模型
description: 使用 ASP.NET Core Web API 在網際網路上提供 ML.NET 情感分析機器學習模型
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: b6801b7de5a17257be706f77a7a67aa87df96524
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79398927"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a>在 ASP.NET Core Web API 中部署模型

了解如何使用 ASP.NET Core Web API，在 Web 上提供預先定型的 ML.NET 機器學習模型。 透過 Web API 提供模型可讓您透過標準 HTTP 方法進行預測。

## <a name="prerequisites"></a>必要條件

- [Visual Studio 2017 版本 15.6 或更高版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)安裝了".NET 核心跨平臺開發"工作負載。
- PowerShell。
- 預先定型的模型。 使用 [ML.NET 情感分析教學課程](../tutorials/sentiment-analysis.md)來建置您自己的模型，或是下載這個[預先定型的情感分析機器學習模型](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)

## <a name="create-aspnet-core-web-api-project"></a>建立 ASP.NET Core Web API 專案

1. 開啟 Visual Studio 2017。 從功能表列中選取 [檔案] > [新增] > [專案]****。 在 [新增專案] 對話方塊中，選取 [Visual C#]**** 節點，然後選取 [Web]**** 節點。 然後，選取 [ASP.NET Core Web 應用程式]**** 專案範本。 在 [名稱]**** 文字方塊中，輸入 "SentimentAnalysisWebAPI"，然後選取 [確定]**** 按鈕。

1. 在顯示不同類型的 ASP.NET Core 專案的視窗中，選取 [API]****，然後選取 [確定]**** 按鈕。

1. 在專案中建立名為 *MLModels* 的目錄，以儲存您預先建置的機器學習模型檔案：

    在 [方案總管] 中，以滑鼠右鍵按一下您的專案，然後選取 [新增] > [新增資料夾]。 輸入 "MLModels"，然後按 Enter。

1. 安裝「Microsoft.ML NuGet 套件」****：

    在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]****。 選擇 "nuget.org" 作為 [套件來源]，選取 [瀏覽] 索引標籤、搜尋 **Microsoft.ML**、從清單中選取該套件，然後選取 [安裝] 按鈕。 在 [預覽變更]**** 對話方塊上，選取 [確定]**** 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]****。

1. 安裝**Microsoft.Extensions.ML Nuget 套裝軟體**：

    在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]****。 選擇 "nuget.org" 作為 [套件來源]、選取 [瀏覽] 索引標籤、搜尋 **Microsoft.Extensions.ML**、從清單中選取該套件，然後選取 [安裝] 按鈕。 在 [預覽變更]**** 對話方塊上，選取 [確定]**** 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]****。

### <a name="add-model-to-aspnet-core-web-api-project"></a>將模型新增至 ASP.NET Core Web API 專案

1. 將預先建置的模型複製到 *MLModels* 目錄
1. 在 [方案總管] 中，以滑鼠右鍵按一下模型 zip 檔案，並選取 [內容]。 在 [進階] 下，將 [複製到輸出目錄] 的值變更為 [有更新才複製]。

## <a name="create-data-models"></a>建立資料模型

您必須為輸入資料和預測建立一些類別。 將新類別新增至專案：

1. 在您的專案中建立名為 *DataModels* 的目錄以儲存資料模型：

    在 [方案總管] 中，以滑鼠右鍵按一下您的專案，然後選取 [新增] > [新增資料夾]。 鍵入"資料模型"並點擊**Enter**。

2. 在 [方案總管] 中，以滑鼠右鍵按一下 *DataModels* 目錄，然後選取 [新增] > [新增項目]。
3. 在 [新增項目]**** 對話方塊中，選取 [類別]****，然後將 [名稱]**** 欄位變更為 *SentimentData.cs*。 接著，選取 [新增]**** 按鈕。 *SentimentData.cs* 檔案隨即在程式碼編輯器中開啟。 將下列 using 陳述式新增至 *SentimentData.cs* 頂端：

    ```csharp
    using Microsoft.ML.Data;
    ```

    刪除現有類定義並將以下代碼添加到**SentimentData.cs**檔中：

    ```csharp
    public class SentimentData
    {
        [LoadColumn(0)]
        public string SentimentText;

        [LoadColumn(1)]
        [ColumnName("Label")]
        public bool Sentiment;
    }
    ```

4. 在解決方案資源管理器中，按右鍵 *"資料模型"* 目錄，然後選擇"**添加>新專案**。
5. 在 [加入新項目]**** 對話方塊中，選取 [類別]****，然後將 [名稱]**** 欄位變更為 *SentimentPrediction.cs*。 接著，選取 [新增] 按鈕。 *SentimentPrediction.cs* 檔案隨即在程式碼編輯器中開啟。 將下列 using 陳述式新增至 *SentimentPrediction.cs* 頂端：

    ```csharp
    using Microsoft.ML.Data;
    ```

    移除現有的類別定義，然後將下列程式碼新增至 *SentimentPrediction.cs* 檔案：

    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    `SentimentPrediction` 繼承自 `SentimentData`。 這可讓您更輕易地看到 `SentimentText` 屬性中的原始資料，以及模型所產生的輸出。

## <a name="register-predictionenginepool-for-use-in-the-application"></a>登錄 PredictionEnginePool 以在應用程式中使用

要進行單個預測，必須創建 一個[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)。 [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)不是執行緒安全的。 此外，您必須在應用程式中需要它的地方創建它的實例。 隨著應用程式的增長，此過程可能會變得難以管理。 為提高性能和執行緒安全性，請使用依賴項注入和服務`PredictionEnginePool`的組合，該服務將創建一個[`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601)[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)物件，供整個應用程式使用。

如果要瞭解有關[ASP.NET酷中的依賴項注入的詳細資訊，](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1)以下連結提供了更多資訊。

1. 開啟 *Startup.cs* 類別，並將下列 using 陳述式新增至檔案頂端：

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

2. 將下列程式碼新增到 *ConfigureServices* 方法：

    ```csharp
    services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
        .FromFile(modelName: "SentimentAnalysisModel", filePath:"MLModels/sentiment_model.zip", watchForChanges: true);
    ```

在高級別上，此代碼會自動初始化物件和服務，以便以後在應用程式請求時使用，而不必手動執行此操作。

機器學習模型不是靜態的。 隨著新的培訓資料可用，模型將重新訓練和重新部署。 將最新版本的模型引入應用程式的一種方法是重新部署整個應用程式。 但是，這引入了應用程式停機時間。 該服務`PredictionEnginePool`提供了一種機制，用於重新載入更新的模型，而無需關閉應用程式。

將`watchForChanges`參數設置為`true`，並`PredictionEnginePool`啟動[`FileSystemWatcher`](xref:System.IO.FileSystemWatcher)偵聽檔案系統更改通知並在檔發生更改時引發事件。 這提示 自動`PredictionEnginePool`重新載入模型。

參數標識模型，`modelName`以便每個應用程式可以在更改時重新載入多個模型。

> [!TIP]
> 或者，在使用遠端存放`FromUri`的模型時，可以使用 該方法。 不要監視檔更改的事件，而是`FromUri`輪詢遠端位置以進行更改。 輪詢間隔預設為 5 分鐘。 您可以根據應用程式的要求增加或減少輪詢間隔。 在下面的代碼示例中，`PredictionEnginePool`每分鐘輪詢存儲在指定 URI 中的模型。
>
>```csharp
>services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="create-predict-controller"></a>建立預測控制器

若要處理傳入的 HTTP 要求，請建立一個控制器。

1. 在 [方案總管] 中，以滑鼠右鍵按一下 *Controllers* 目錄，然後選取 [新增] > [控制器]****。
1. 在 [加入新項目]**** 對話方塊中，選取 [API 控制器 - 空白]****，然後選取 [新增]****。
1. 在提示中，將 [控制器名稱]**** 欄位變更為 *PredictController.cs*。 接著，選取 [新增] 按鈕。 *PredictController.cs* 檔案隨即在程式碼編輯器中開啟。 將下列 using 陳述式新增至 *PredictController.cs* 頂端：

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

    移除現有的類別定義，然後將下列程式碼新增至 *PredictController.cs* 檔案：

    ```csharp
    public class PredictController : ControllerBase
    {
        private readonly PredictionEnginePool<SentimentData, SentimentPrediction> _predictionEnginePool;

        public PredictController(PredictionEnginePool<SentimentData,SentimentPrediction> predictionEnginePool)
        {
            _predictionEnginePool = predictionEnginePool;
        }

        [HttpPost]
        public ActionResult<string> Post([FromBody] SentimentData input)
        {
            if(!ModelState.IsValid)
            {
                return BadRequest();
            }

            SentimentPrediction prediction = _predictionEnginePool.Predict(modelName: "SentimentAnalysisModel", example: input);

            string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

            return Ok(sentiment);
        }
    }
    ```

此程式碼會透過將預測服務傳遞至控制器的建構函式 (透過相依性插入取得) 來指派 `PredictionEnginePool`。 然後，`Predict`控制器`Post`的方法使用`PredictionEnginePool`使用`SentimentAnalysisModel``Startup`類中的註冊進行預測，如果成功，則返回結果返回給使用者。

## <a name="test-web-api-locally"></a>在本機測試 Web API

一切都設定好後，就可以開始測試應用程式。

1. 執行應用程式。
1. 開啟 Powershell 並輸入下列程式碼，其中 PORT 是應用程式正在接聽的連接埠。

    ```powershell
    Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{SentimentText="This was a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    如果成功，輸出看起來應該類似下列文字：

    ```powershell
    Negative
    ```

恭喜！ 您已成功提供您的模型，使用 ASP.NET Core Web API 在網際網路上進行預測。

## <a name="next-steps"></a>後續步驟

- [部署到 Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs#deploy-the-app-to-azure)
