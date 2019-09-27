---
title: 在 ASP.NET Core Web API 中部署模型
description: 使用 ASP.NET Core Web API 在網際網路上提供 ML.NET 情感分析機器學習模型
ms.date: 09/11/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: 1173315bbc88797ce0c6d0fcc9597896f14889ac
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332695"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a>在 ASP.NET Core Web API 中部署模型

了解如何使用 ASP.NET Core Web API，在 Web 上提供預先定型的 ML.NET 機器學習模型。 透過 Web API 提供模型可讓您透過標準 HTTP 方法進行預測。

> [!NOTE]
> `PredictionEnginePool` 服務延伸模組目前處於預覽狀態。

## <a name="prerequisites"></a>必要條件

- 已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)。
- PowerShell。
- 預先定型的模型。 使用 [ML.NET 情感分析教學課程](../tutorials/sentiment-analysis.md)來建置您自己的模型，或是下載這個[預先定型的情感分析機器學習模型](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)

## <a name="create-aspnet-core-web-api-project"></a>建立 ASP.NET Core Web API 專案

1. 開啟 Visual Studio 2017。 從功能表列中選取 [檔案] > [新增] > [專案]。 在 [新增專案] 對話方塊中，選取 [Visual C#] 節點，然後選取 [Web] 節點。 然後，選取 [ASP.NET Core Web 應用程式] 專案範本。 在 [名稱] 文字方塊中，輸入 "SentimentAnalysisWebAPI"，然後選取 [確定] 按鈕。

1. 在顯示不同類型的 ASP.NET Core 專案的視窗中，選取 [API]，然後選取 [確定] 按鈕。

1. 在專案中建立名為 *MLModels* 的目錄，以儲存您預先建置的機器學習模型檔案：

    在 [方案總管] 中，以滑鼠右鍵按一下您的專案，然後選取 [新增] > [新增資料夾]。 輸入 "MLModels"，然後按 Enter。

1. 安裝「Microsoft.ML NuGet 套件」：

    在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。 選擇 "nuget.org" 作為 [套件來源]、選取 [瀏覽] 索引標籤、搜尋 **Microsoft.ML**、從清單中選取該套件，然後選取 [安裝] 按鈕。 在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。

1. 安裝 **Microsoft.Extensions.ML Nuget 套件**：

    在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。 選擇 "nuget.org" 作為 [套件來源]、選取 [瀏覽] 索引標籤、搜尋 **Microsoft.Extensions.ML**、從清單中選取該套件，然後選取 [安裝] 按鈕。 在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。

### <a name="add-model-to-aspnet-core-web-api-project"></a>將模型新增至 ASP.NET Core Web API 專案

1. 將預先建置的模型複製到 *MLModels* 目錄
1. 在 [方案總管] 中，以滑鼠右鍵按一下模型 zip 檔案，並選取 [內容]。 在 [進階] 下，將 [複製到輸出目錄] 的值變更為 [有更新才複製]。

## <a name="create-data-models"></a>建立資料模型

您必須為輸入資料和預測建立一些類別。 將新類別新增至專案：

1. 在您的專案中建立名為 *DataModels* 的目錄以儲存資料模型：

    在 [方案總管] 中，以滑鼠右鍵按一下您的專案，然後選取 [新增] > [新增資料夾]。 輸入 "DataModels"，然後按 **Enter**。

2. 在 [方案總管] 中，以滑鼠右鍵按一下 *DataModels* 目錄，然後選取 [新增] > [新增項目]。
3. 在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *SentimentData.cs*。 接著，選取 [新增] 按鈕。 *SentimentData.cs* 檔案隨即在程式碼編輯器中開啟。 將下列 using 陳述式新增至 *SentimentData.cs* 頂端：

    ```csharp
    using Microsoft.ML.Data;
    ```
    
    移除現有的類別定義，然後將下列程式碼新增至 **SentimentData.cs** 檔案：
    
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

4. 在 [方案總管] 中，以滑鼠右鍵按一下 *DataModels* 目錄，然後選取 [新增] > [新增項目]。
5. 在 [加入新項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *SentimentPrediction.cs*。 接著，選取 [新增] 按鈕。 *SentimentPrediction.cs* 檔案隨即在程式碼編輯器中開啟。 將下列 using 陳述式新增至 *SentimentPrediction.cs* 頂端：

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

若要進行單一預測，您必須建立[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)。 [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) 不是安全執行緒。 此外，您必須在應用程式內需要的任何地方建立它的實例。 當您的應用程式成長時，此進程可能會變得難以管理。 為了改善效能和執行緒安全性，請使用相依性插入和 `PredictionEnginePool` 服務的組合，這會建立[@no__t 4](xref:Microsoft.ML.PredictionEngine%602)物件的[@no__t 2](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) ，以便在整個應用程式中使用。

如果您想要深入瞭解[ASP.NET Core 中的](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1)相依性插入，下列連結提供詳細資訊。

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
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_1);
        services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
            .FromFile(modelName: "SentimentAnalysisModel", filePath:"MLModels/sentiment_model.zip", watchForChanges: true);
    }
    ```

概括而言，此程式碼會自動初始化物件和服務，以供稍後在應用程式要求時使用，而不需要手動執行。 

機器學習模型不是靜態的。 當有新的定型資料可供使用時，就會重新訓練並重新部署模型。 將模型的最新版本取得至應用程式的方法之一，就是重新部署整個應用程式。 不過，這會引進應用程式停機時間。 @No__t-0 服務提供一種機制，可重載已更新的模型，而不需要讓應用程式關閉。 

將 `watchForChanges` 參數設定為 `true`，而 `PredictionEnginePool` 啟動一個[`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) ，接聽檔案系統變更通知，並在檔案變更時引發事件。 這會提示 `PredictionEnginePool` 會自動重載模型。

此模型是由 `modelName` 參數所識別，因此，每個應用程式可以在變更時重載一個以上的模型。 

或者，當您使用遠端儲存的模型時，可以使用 `FromUri` 方法。 @No__t-0 會輪詢遠端位置以進行變更，而不是監看檔案已變更的事件。 輪詢間隔預設為5分鐘。 您可以根據應用程式的需求來增加或減少輪詢間隔。

## <a name="create-predict-controller"></a>建立預測控制器

若要處理傳入的 HTTP 要求，請建立一個控制器。

1. 在 [方案總管] 中，以滑鼠右鍵按一下 *Controllers* 目錄，然後選取 [新增] > [控制器]。
1. 在 [加入新項目] 對話方塊中，選取 [API 控制器 - 空白]，然後選取 [新增]。
1. 在提示中，將 [控制器名稱] 欄位變更為 *PredictController.cs*。 接著，選取 [新增] 按鈕。 *PredictController.cs* 檔案隨即在程式碼編輯器中開啟。 將下列 using 陳述式新增至 *PredictController.cs* 頂端：

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

此程式碼會透過將預測服務傳遞至控制器的建構函式 (透過相依性插入取得) 來指派 `PredictionEnginePool`。 然後，`Predict` 控制器的 @no__t 1 方法會使用 `PredictionEnginePool`，利用在 `Startup` 類別中註冊的 `SentimentAnalysisModel` 進行預測，並在成功時將結果傳回給使用者。

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

恭喜您！ 您已成功提供您的模型，使用 ASP.NET Core Web API 在網際網路上進行預測。

## <a name="next-steps"></a>後續步驟

- [部署到 Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs#deploy-the-app-to-azure)
