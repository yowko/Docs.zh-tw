---
title: 在 ASP.NET Core Web API 中提供機器學習模型
description: 使用 ASP.NET Core Web API 在網際網路上提供 ML.NET 情感分析機器學習模型
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 0cc13ec22b3a8805ec4aa17bf10560b2564ccd63
ms.sourcegitcommit: 77854e8704b9689b73103d691db34d71c2bf1dad
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2019
ms.locfileid: "58307911"
---
# <a name="how-to-serve-machine-learning-model-through-aspnet-core-web-api"></a>操作說明：透過 ASP.NET Core Web API 提供機器學習模型

此操作說明會顯示如何使用 ASP.NET Core Web API 將預先建置的 ML.NET 機器學習模型提供給 Web。 透過這種方式，它可讓使用者透過標準 HTTP 方法，針對預測目的存取 API。

> [!NOTE]
> 本主題涉及 ML.NET，此功能目前為公開預覽版，因此内容可能會有變更。 如需詳細資訊，請瀏覽 [ML.NET 簡介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet) (英文)。

本操作說明與關聯的範例目前是使用 **ML.NET 0.10 版**。 如需詳細資訊，請參閱 [dotnet/machinelearning GitHub 存放庫](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes) \(英文\) 中的版本資訊。

## <a name="prerequisites"></a>必要條件

- 已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)。
- PowerShell。
- 預先定型的模型。
    - 使用 [ ML.NET 情感分析教學課程](../tutorials/sentiment-analysis.md)建置您自己的模型。
    - 下載此[預先定型的情感分析機器學習模型](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)

## <a name="create-aspnet-core-web-api-project"></a>建立 ASP.NET Core Web API 專案

1. 開啟 Visual Studio 2017。 從功能表列中選取 [檔案] > [新增] > [專案]。 在 [新增專案] 對話方塊中，選取 [Visual C#] 節點，然後選取 [Web] 節點。 然後，選取 [ASP.NET Core Web 應用程式] 專案範本。 在 [名稱] 文字方塊中，輸入 "SentimentAnalysisWebAPI"，然後選取 [確定] 按鈕。
1. 在顯示不同類型的 ASP.NET Core 專案的視窗中，選取 [API]，然後選取 [確定] 按鈕。
1. 在專案中建立名為 *MLModels* 的目錄，以儲存您預先建置的機器學習模型檔案：

    在 [方案總管] 中，以滑鼠右鍵按一下您的專案，然後選取 [新增] > [新增資料夾]。 輸入 "MLModels"，然後按 Enter。

1. 安裝「Microsoft.ML NuGet 套件」：

    在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。 選擇 "nuget.org" 作為 [套件來源]、選取 [瀏覽] 索引標籤、搜尋 **Microsoft.ML**、從清單中選取該套件，然後選取 [安裝] 按鈕。 在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。

### <a name="add-model-to-aspnet-core-web-api-project"></a>將模型新增至 ASP.NET Core Web API 專案

1. 將預先建置的模型複製到 *MLModels* 目錄
1. 在 [方案總管] 中，以滑鼠右鍵按一下模型 zip 檔案，並選取 [內容]。 在 [進階] 下，將 [複製到輸出目錄] 的值變更為 [有更新才複製]。

## <a name="build-data-models"></a>建置資料模型

您必須為輸入資料和預測建立一些類別。 將新類別新增至專案：

1. 在您的專案中建立名為 *DataModels* 的目錄以儲存資料模型：

    在 [方案總管] 中，以滑鼠右鍵按一下您的專案，然後選取 [新增] > [新增資料夾]。 輸入 "DataModels"，然後按 **Enter**。

2. 在 [方案總管] 中，以滑鼠右鍵按一下 *DataModels* 目錄，然後選取 [新增] > [新增項目]。
3. 在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *SentimentData.cs*。 接著，選取 [新增] 按鈕。 *SentimentData.cs* 檔案隨即在程式碼編輯器中開啟。 將下列 using 陳述式新增至 *SentimentData.cs* 頂端：

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.ML.Data;
```

移除現有的類別定義，然後將下列程式碼新增至 **SentimentData.cs** 檔案：

```csharp
public class SentimentData
{
    [LoadColumn(0)]
    public bool Label { get; set; }
    [LoadColumn(1)]
    public string Text { get; set; }   
}
```

4. 在 [方案總管] 中，以滑鼠右鍵按一下 *DataModels* 目錄，然後選取 [新增] > [新增項目]。
5. 在 [加入新項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *SentimentPrediction.cs*。 接著，選取 [新增] 按鈕。 *SentimentPrediction.cs* 檔案隨即在程式碼編輯器中開啟。 將下列 using 陳述式新增至 *SentimentPrediction.cs* 頂端：

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.ML.Data;
```

移除現有的類別定義，然後將下列程式碼新增至 *SentimentPrediction.cs* 檔案：

```csharp
public class SentimentPrediction
{
    [ColumnName("PredictedLabel")]
    public bool Prediction { get; set; }
}
```

## <a name="register-predictionengine-for-use-in-application"></a>註冊 PredictionEngine 以便在應用程式中使用

若要進行單一預測，您可以使用 `PredictionEngine`。 若要在您的應用程式中使用 `PredictionEngine`，必須在每次需要時建立。 在此情況下，要考慮的最佳做法是 ASP.NET Core 的相依性插入。

如果您想要深入了解[相依性插入](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1)，下列連結提供詳細資訊。

1. 開啟 *Startup.cs* 類別，並將下列 using 陳述式新增至檔案頂端：

```csharp
using System.IO;
using Microsoft.AspNetCore.Builder;
using Microsoft.AspNetCore.Hosting;
using Microsoft.AspNetCore.Mvc;
using Microsoft.Extensions.Configuration;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.ML;
using Microsoft.ML.Core.Data;
using SentimentAnalysisWebAPI.DataModels;
```

2. 將下列程式碼加入 *ConfigureServices* 類別：

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_1);

    services.AddScoped<MLContext>();
    services.AddScoped<PredictionEngine<SentimentData, SentimentPrediction>>((ctx) =>
    {
        MLContext mlContext = ctx.GetRequiredService<MLContext>();
        string modelFilePathName = "MLModels/sentiment_model.zip";

        //Load model from file
        ITransformer model;
        using (var stream = File.OpenRead(modelFilePathName))
        {
            model = mlContext.Model.Load(stream);
        }

        // Return prediction engine
        return model.CreatePredictionEngine<SentimentData, SentimentPrediction>(mlContext);
    });
}
```

> [!WARNING]
> `PredictionEngine` 不是安全執行緒。 您可以用來限制建立物件成本的方式為使其服務存留期「具範圍」。 「具範圍」物件在要求內相同，但在不同的要求之間會不同。 請前往下列連結以深入了解[服務存留期](/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1#service-lifetimes)。

概括而言，此程式碼會在應用程式要求時自動初始化物件和服務，不必手動執行。

## <a name="create-predict-controller"></a>建立預測控制器

若要處理傳入的 HTTP 要求，您需要建立一個控制器。

1. 在 [方案總管] 中，以滑鼠右鍵按一下 *Controllers* 目錄，然後選取 [新增] > [控制器]。
1. 在 [加入新項目] 對話方塊中，選取 [API 控制器 - 空白]，然後選取 [新增]。
1. 在提示中，將 [控制器名稱] 欄位變更為 *PredictController.cs*。 接著，選取 [新增] 按鈕。 *PredictController.cs* 檔案隨即在程式碼編輯器中開啟。 將下列 using 陳述式新增至 *PredictController.cs* 頂端：

```csharp
using System;
using Microsoft.AspNetCore.Mvc;
using SentimentAnalysisWebAPI.DataModels;
using Microsoft.ML;
```

移除現有的類別定義，然後將下列程式碼新增至 *PredictController.cs* 檔案：

```csharp
public class PredictController : ControllerBase
{
    
    private readonly PredictionEngine<SentimentData,SentimentPrediction> _predictionEngine;

    public PredictController(PredictionEngine<SentimentData, SentimentPrediction> predictionEngine)
    {
        _predictionEngine = predictionEngine; //Define prediction engine
    }

    [HttpPost]
    public ActionResult<string> Post([FromBody]SentimentData input)
    {
        if(!ModelState.IsValid)
        {
            return BadRequest();
        }

        // Make a prediction
        SentimentPrediction prediction = _predictionEngine.Predict(input);

        //If prediction is true then it is toxic. If it is false, the it is not.
        string isToxic = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";

        return Ok(isToxic);
    }
    
}
```

這是透過將預測服務傳遞至控制器的建構函式 (透過相依性插入取得) 來指派 `PredictionEngine`。 然後，在此控制器的 POST 方法中，`PredictionEngine` 會用來進行預測，並在成功時將結果傳回給使用者。

## <a name="test-web-api-locally"></a>在本機測試 Web API

一切都設定好後，就可以開始測試應用程式。

1. 執行應用程式。
1. 開啟 Powershell 並輸入下列程式碼，其中 PORT 是應用程式正在接聽的連接埠。

```powershell
Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{Text="This is a very rude movie"} | ConvertTo-Json) -ContentType "application/json"
```

如果成功，輸出看起來應該類似下列文字：

```powershell
Toxic
```

恭喜您！ 您已成功提供您的模型，以使用 ASP.NET Core API 在網際網路上進行預測。

## <a name="next-steps"></a>後續步驟

- [部署到 Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.1#deploy-the-app-to-azure)