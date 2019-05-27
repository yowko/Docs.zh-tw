---
title: 將模型部署到 Azure Functions
description: 使用 Azure Functions 在網際網路上提供 ML.NET 情感分析機器學習模型以進行預測
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 9e62d8826227aed07451387cc733d27094327f99
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645100"
---
# <a name="deploy-a-model-to-azure-functions"></a>將模型部署到 Azure Functions

了解如何部署預先定型的 ML.NET 機器學習模型，以使用 Azure Functions 無伺服器環境透過 HTTP 進行預測。

> [!NOTE]
> `PredictionEnginePool` 服務延伸模組目前處於預覽狀態。

## <a name="prerequisites"></a>必要條件

- 已安裝「.NET Core 跨平台開發」工作負載和「Azure 開發」的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)。
- [Azure Functions Tools](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- Powershell
- 預先定型的模型。 使用 [ML.NET 情感分析教學課程](../tutorials/sentiment-analysis.md)來建置您自己的模型，或是下載這個[預先定型的情感分析機器學習模型](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)

## <a name="create-azure-functions-project"></a>建立 Azure Functions 專案

1. 開啟 Visual Studio 2017。 從功能表列中選取 [檔案]  >  [新增]  >  [專案]。 在 [新增專案] 對話方塊中，選取 [Visual C#] 節點，然後選取 [雲端] 節點。 然後選取 [Azure Functions] 專案範本。 在 [名稱] 文字方塊中，輸入 "SentimentAnalysisFunctionsApp"，然後選取 [確定] 按鈕。
1. 在 [新增專案] 對話方塊中，開啟專案選項上方的下拉式清單，然後選取 [Azure Functions v2 (.NET Core)]。 然後，選取 [Http 觸發程序] 專案，然後選取 [確定] 按鈕。
1. 在您的專案中建立名為 *MLModels* 的目錄，以儲存您的模型：

    在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [新增] > [新增資料夾]。 輸入 "MLModels"，然後按 Enter。

1. 安裝「Microsoft.ML NuGet 套件」：

    在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。 選擇 "nuget.org" 作為 [套件來源]，選取 [瀏覽] 索引標籤、搜尋 **Microsoft.ML**、從清單中選取該套件，然後選取 [安裝] 按鈕。 在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。

1. 安裝 **Microsoft.Extensions.ML NuGet 套件**：

    在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。 選擇 "nuget.org" 作為 [套件來源]、選取 [瀏覽] 索引標籤、搜尋 **Microsoft.Extensions.ML**、從清單中選取該套件，然後選取 [安裝] 按鈕。 在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。

## <a name="add-pre-trained-model-to-project"></a>將預先定型的模型新增到專案

1. 將預先建置的模型複製到 *MLModels* 目錄。
1. 在 [方案總管] 中，以滑鼠右鍵按一下您預先建置的模型檔案，並選取 [內容]。 在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。

## <a name="create-azure-function-to-analyze-sentiment"></a>建立 Azure Function 來分析情感

建立用來預測情緒的類別。 將新類別新增至專案：

1. 在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。

1. 在 [新增項目] 對話方塊中，選取 [Azure Function]，然後將 [名稱] 欄位變更為 *AnalyzeSentiment.cs*。 接著，選取 [新增] 按鈕。

1. 在 [新增 Azure 函式] 對話方塊中，選取 [Http 觸發程序]。 然後，選取 [確定] 按鈕。

    *AnalyzeSentiment.cs* 檔案隨即在程式碼編輯器中開啟。 將下列 `using` 陳述式新增到 *AnalyzeSentiment.cs* 的頂端：

    ```csharp
    using System;
    using System.IO;
    using System.Threading.Tasks;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Azure.WebJobs;
    using Microsoft.Azure.WebJobs.Extensions.Http;
    using Microsoft.AspNetCore.Http;
    using Microsoft.Extensions.Logging;
    using Newtonsoft.Json;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisFunctionsApp.DataModels;
    ```

    根據預設，`AnalyzeSentiment` 類別為 `static`。 請務必從類別定義移除 `static` 關鍵字。

    ```csharp
    public class AnalyzeSentiment
    {
    
    }
    ```

## <a name="create-data-models"></a>建立資料模型

您必須為輸入資料和預測建立一些類別。 將新類別新增至專案：

1. 在您的專案中建立名為 *DataModels* 的目錄以儲存資料模型：在 [方案總管] 中，以滑鼠右鍵按一下您的專案，然後選取 [新增] > [新增資料夾]。 輸入 "DataModels"，然後按 Enter。
2. 在 [方案總管] 中，以滑鼠右鍵按一下 *DataModels* 目錄，然後選取 [新增] > [新增項目]。
3. 在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *SentimentData.cs*。 接著，選取 [新增] 按鈕。 

    *SentimentData.cs* 檔案隨即在程式碼編輯器中開啟。 將下列 using 陳述式新增至 *SentimentData.cs* 頂端：

    ```csharp
    using Microsoft.ML.Data;
    ```

    移除現有的類別定義，然後將下列程式碼新增至 *SentimentData.cs* 檔案：
    
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

    `SentimentPrediction` 會從 `SentimentData` 繼承，後者會在 `SentimentText` 屬性中提供原始資料的存取，以及由模型產生的輸出。

## <a name="register-predictionenginepool-service"></a>登錄 PredictionEnginePool 服務

若要進行單一預測，請使用 [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)。 為了在您的應用程式中使用 [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)，您必須在需要的時候建立它。 在此情況下，要考慮的最佳做法是相依性插入。

如果您想要深入了解[相依性插入](https://en.wikipedia.org/wiki/Dependency_injection)，下列連結提供詳細資訊。

1. 在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。
1. 在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *Startup.cs*。 接著，選取 [新增] 按鈕。 

    *Startup.cs* 檔案隨即在程式碼編輯器中開啟。 將下列的 using 陳述式新增到 *Startup.cs* 的頂端：

    ```csharp
    using Microsoft.Azure.WebJobs;
    using Microsoft.Azure.WebJobs.Hosting;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisFunctionsApp;
    using SentimentAnalysisFunctionsApp.DataModels;
    ```

    移除 using 陳述式下方的現有程式碼，並將下列程式碼新增到 *Startup.cs* 檔案：

    ```csharp
    [assembly: WebJobsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        class Startup : IWebJobsStartup
        {
            public void Configure(IWebJobsBuilder builder)
            {
                builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
                    .FromFile("MLModels/sentiment_model.zip");
            }
        }
    }
    ```

概括而言，此程式碼會在應用程式要求時自動初始化物件和服務，不必手動執行。

> [!WARNING]
> [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) 不是安全執行緒。 為了改善效能及執行緒安全性，請使用 `PredictionEnginePool` 服務，該服務會建立 `PredictionEngine` 物件的 [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601)以供應用程式使用。 

## <a name="register-startup-as-an-azure-functions-extension"></a>將 Startup 登錄為 Azure Functions 延伸模組

為了在您的應用程式中使用 `Startup`，您需要將它登錄為 Azure Functions 延伸模組。 在您專案中建立稱為 *extensions.json* 的新檔案 (若尚未存在的話)。

1. 在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。
1. 在 [新增項目] 對話方塊中，選取 **Visual C#** 節點，然後選取 **Web** 節點。 然後選取 [JSON 檔案] 選項。 在 [名稱] 文字方塊中，輸入 "extensions.json"，然後選取 [確定] 按鈕。

    *extensions.json* 檔案隨即在程式碼編輯器中開啟。 將下列內容新增至 *extensions.json*：
    
    ```json
    {
      "extensions": [
        {
          "name": "Startup",
          "typename": "SentimentAnalysisFunctionsApp.Startup, SentimentAnalysisFunctionsApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"
        }
      ]
    }
    ```

1. 在 [方案總管] 中，以滑鼠右鍵按一下您的 *extensions.json* 檔案，然後選取 [屬性]。 在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。

## <a name="load-the-model-into-the-function"></a>將模型載入函式

將下列程式碼插入 *AnalyzeSentiment* 類別：

```csharp
private readonly PredictionEnginePool<SentimentData, SentimentPrediction> _predictionEnginePool;

// AnalyzeSentiment class constructor
public AnalyzeSentiment(PredictionEnginePool<SentimentData, SentimentPrediction> predictionEnginePool)
{
    _predictionEnginePool = predictionEnginePool;
}
```

此程式碼會透過將 `PredictionEnginePool` 傳遞到您透過相依性插入所取得的函式建構函式來指派它。

## <a name="use-the-model-to-make-predictions"></a>使用模型進行預測

使用下列程式碼取代 *AnalyzeSentiment* 類別中 *Run* 方法的現有實作：

```csharp
[FunctionName("AnalyzeSentiment")]
public async Task<IActionResult> Run(
[HttpTrigger(AuthorizationLevel.Function, "post", Route = null)] HttpRequest req,
ILogger log)
{
    log.LogInformation("C# HTTP trigger function processed a request.");

    //Parse HTTP Request Body
    string requestBody = await new StreamReader(req.Body).ReadToEndAsync();
    SentimentData data = JsonConvert.DeserializeObject<SentimentData>(requestBody);
    
    //Make Prediction
    SentimentPrediction prediction = _predictionEnginePool.Predict(data);

    //Convert prediction to string
    string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

    //Return Prediction
    return (ActionResult)new OkObjectResult(sentiment);
}
```

`Run` 方法執行時，來自 HTTP 請求的傳入資料會還原序列化，並用來作為 `PredictionEnginePool` 的輸入。 接著會呼叫 `Predict` 方法來產生預測，並將結果傳回使用者。 

## <a name="test-locally"></a>在本機進行測試

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

恭喜您！ 您已成功提供您的模型，以使用 Azure Function 在網際網路上進行預測。

## <a name="next-steps"></a>後續步驟

- [部署到 Azure](/azure/azure-functions/functions-develop-vs#publish-to-azure)
