---
title: 將 ML.NET 模型部署至 Azure Functions
description: 使用 Azure Functions 在網際網路上提供 ML.NET 情感分析機器學習模型以進行預測
ms.date: 03/08/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 4681b37da64097dd8e537b4c956917277ecff96b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59330632"
---
# <a name="how-to-use-mlnet-model-in-azure-functions"></a><span data-ttu-id="0c4bd-103">操作說明：在 Azure Functions 中使用 ML.NET 模型</span><span class="sxs-lookup"><span data-stu-id="0c4bd-103">How-To: Use ML.NET Model in Azure Functions</span></span>

<span data-ttu-id="0c4bd-104">此操作說明顯示如何在無伺服器環境 (例如 Azure Functions) 中透過網際網路使用預先建置的 ML.NET 機器學習模型進行個別預測。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-104">This how-to shows how individual predictions can be made using a pre-built ML.NET machine learning model through the internet in a serverless environment such as Azure Functions.</span></span>

> [!NOTE]
> <span data-ttu-id="0c4bd-105">本主題涉及 ML.NET，此功能目前為公開預覽版，因此内容可能會有變更。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-105">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="0c4bd-106">如需詳細資訊，請瀏覽 [ML.NET 簡介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet) (英文)。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-106">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="0c4bd-107">本操作說明與關聯的範例目前是使用 **ML.NET 0.10 版**。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-107">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="0c4bd-108">如需詳細資訊，請參閱 [dotnet/machinelearning GitHub 存放庫](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes) \(英文\) 中的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-108">For more information, see the release notes at the [dotnet/machinelearning github repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0c4bd-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="0c4bd-109">Prerequisites</span></span>

- <span data-ttu-id="0c4bd-110">已安裝「.NET Core 跨平台開發」工作負載和「Azure 開發」的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-110">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload and "Azure development" installed.</span></span> 
- [<span data-ttu-id="0c4bd-111">Azure Functions Tools</span><span class="sxs-lookup"><span data-stu-id="0c4bd-111">Azure Functions Tools</span></span>](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- <span data-ttu-id="0c4bd-112">Powershell</span><span class="sxs-lookup"><span data-stu-id="0c4bd-112">Powershell</span></span>
- <span data-ttu-id="0c4bd-113">預先定型的模型。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-113">Pre-trained model.</span></span> 
    - <span data-ttu-id="0c4bd-114">使用 [ ML.NET 情感分析教學課程](../tutorials/sentiment-analysis.md)建置您自己的模型。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-114">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model.</span></span>
    - <span data-ttu-id="0c4bd-115">下載此[預先定型的情感分析機器學習模型](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="0c4bd-115">Download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-azure-functions-project"></a><span data-ttu-id="0c4bd-116">建立 Azure Functions 專案</span><span class="sxs-lookup"><span data-stu-id="0c4bd-116">Create Azure Functions Project</span></span>

1. <span data-ttu-id="0c4bd-117">開啟 Visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-117">Open Visual Studio 2017.</span></span> <span data-ttu-id="0c4bd-118">從功能表列中選取 [檔案]  >  [新增]  >  [專案]。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-118">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="0c4bd-119">在 [新增專案] 對話方塊中，選取 [Visual C#] 節點，然後選取 [雲端] 節點。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-119">In the **New Project** dialog, select the **Visual C#** node followed by the **Cloud** node.</span></span> <span data-ttu-id="0c4bd-120">然後選取 [Azure Functions] 專案範本。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-120">Then select the **Azure Functions** project template.</span></span> <span data-ttu-id="0c4bd-121">在 [名稱] 文字方塊中，輸入 "SentimentAnalysisFunctionsApp"，然後選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-121">In the **Name** text box, type "SentimentAnalysisFunctionsApp" and then select the **OK** button.</span></span>
1. <span data-ttu-id="0c4bd-122">在 [新增專案] 對話方塊中，開啟專案選項上方的下拉式清單，然後選取 [Azure Functions v2 (.NET Core)]。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-122">In the **New Project** dialog, open the dropdown above the project options and select **Azure Functions v2 (.NET Core)**.</span></span> <span data-ttu-id="0c4bd-123">然後，選取 [Http 觸發程序] 專案，然後選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-123">Then, select the **Http trigger** project and then select the **OK** button.</span></span>
1. <span data-ttu-id="0c4bd-124">在您的專案中建立名為 *MLModels* 的目錄，以儲存您的模型：</span><span class="sxs-lookup"><span data-stu-id="0c4bd-124">Create a directory named *MLModels* in your project to save your model:</span></span>

    <span data-ttu-id="0c4bd-125">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [新增] > [新增資料夾]。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-125">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="0c4bd-126">輸入 "MLModels"，然後按 Enter。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-126">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="0c4bd-127">安裝「Microsoft.ML NuGet 套件」：</span><span class="sxs-lookup"><span data-stu-id="0c4bd-127">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="0c4bd-128">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-128">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="0c4bd-129">選擇 "nuget.org" 作為 [套件來源]，選取 [瀏覽] 索引標籤、搜尋 **Microsoft.ML**、從清單中選取該套件，然後選取 [安裝] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-129">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="0c4bd-130">在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-130">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="add-pre-built-model-to-project"></a><span data-ttu-id="0c4bd-131">將預先建置的模型加入至專案</span><span class="sxs-lookup"><span data-stu-id="0c4bd-131">Add Pre-built Model To Project</span></span>

1. <span data-ttu-id="0c4bd-132">將預先建置的模型複製到 *MLModels* 目錄。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-132">Copy your pre-built model to the *MLModels* folder.</span></span>
1. <span data-ttu-id="0c4bd-133">在 [方案總管] 中，以滑鼠右鍵按一下您預先建置的模型檔案，並選取 [內容]。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-133">In Solution Explorer, right-click your pre-built model file and select **Properties**.</span></span> <span data-ttu-id="0c4bd-134">在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-134">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

## <a name="create-function-to-analyze-sentiment"></a><span data-ttu-id="0c4bd-135">建立用來分析情感的函式</span><span class="sxs-lookup"><span data-stu-id="0c4bd-135">Create Function to Analyze Sentiment</span></span>

<span data-ttu-id="0c4bd-136">建立用來預測情緒的類別。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-136">Create a class to predict sentiment.</span></span> <span data-ttu-id="0c4bd-137">將新類別新增至專案：</span><span class="sxs-lookup"><span data-stu-id="0c4bd-137">Add a new class to your project:</span></span>

1. <span data-ttu-id="0c4bd-138">在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-138">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="0c4bd-139">在 [新增項目] 對話方塊中，選取 [Azure Function]，然後將 [名稱] 欄位變更為 *AnalyzeSentiment.cs*。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-139">In the **Add New Item** dialog box, select **Azure Function** and change the **Name** field to *AnalyzeSentiment.cs*.</span></span> <span data-ttu-id="0c4bd-140">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-140">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="0c4bd-141">在 [新增 Azure 函式] 對話方塊中，選取 [Http 觸發程序]。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-141">In the **New Azure Function** dialog box, select **Http Trigger**.</span></span> <span data-ttu-id="0c4bd-142">然後，選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-142">Then, select the **OK** button.</span></span>

    <span data-ttu-id="0c4bd-143">*AnalyzeSentiment.cs* 檔案隨即在程式碼編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-143">The *AnalyzeSentiment.cs* file opens in the code editor.</span></span> <span data-ttu-id="0c4bd-144">將下列 `using` 陳述式新增至 *GitHubIssueData.cs* 最上方：</span><span class="sxs-lookup"><span data-stu-id="0c4bd-144">Add the following `using` statement to the top of *GitHubIssueData.cs*:</span></span>

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
using Microsoft.ML;
using Microsoft.ML.Core.Data;
using Microsoft.ML.Data;
using MLNETServerless.DataModels;
```

### <a name="create-data-models"></a><span data-ttu-id="0c4bd-145">建立資料模型</span><span class="sxs-lookup"><span data-stu-id="0c4bd-145">Create Data Models</span></span>

<span data-ttu-id="0c4bd-146">您必須為輸入資料和預測建立一些類別。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-146">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="0c4bd-147">將新類別新增至專案：</span><span class="sxs-lookup"><span data-stu-id="0c4bd-147">Add a new class to your project:</span></span>

1. <span data-ttu-id="0c4bd-148">在您的專案中建立名為 *DataModels* 的目錄以儲存資料模型：在 [方案總管] 中，以滑鼠右鍵按一下您的專案，然後選取 [新增] > [新增資料夾]。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-148">Create a directory named *DataModels* in your project to save your data models: In Solution Explorer, right-click on your project and select **Add > New Folder**.</span></span> <span data-ttu-id="0c4bd-149">輸入 "DataModels"，然後按 Enter。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-149">Type "DataModels" and hit Enter.</span></span>
2. <span data-ttu-id="0c4bd-150">在 [方案總管] 中，以滑鼠右鍵按一下 *DataModels* 目錄，然後選取 [新增] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-150">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
3. <span data-ttu-id="0c4bd-151">在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *SentimentData.cs*。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-151">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="0c4bd-152">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-152">Then, select the **Add** button.</span></span> <span data-ttu-id="0c4bd-153">*SentimentData.cs* 檔案隨即在程式碼編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-153">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="0c4bd-154">將下列 using 陳述式新增至 *SentimentData.cs* 頂端：</span><span class="sxs-lookup"><span data-stu-id="0c4bd-154">Add the following using statement to the top of *SentimentData.cs*:</span></span>

```csharp
using Microsoft.ML.Data;
```

<span data-ttu-id="0c4bd-155">移除現有的類別定義，然後將下列程式碼新增至 SentimentData.cs 檔案：</span><span class="sxs-lookup"><span data-stu-id="0c4bd-155">Remove the existing class definition and add the following code to the SentimentData.cs file:</span></span>

```csharp
public class SentimentData
{
    [LoadColumn(0)]
    public bool Label { get; set; }
    [LoadColumn(1)]
    public string Text { get; set; }
}
```

4. <span data-ttu-id="0c4bd-156">在 [方案總管] 中，以滑鼠右鍵按一下 *DataModels* 目錄，然後選取 [新增] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-156">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="0c4bd-157">在 [加入新項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *SentimentPrediction.cs*。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-157">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="0c4bd-158">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-158">Then, select the **Add** button.</span></span> <span data-ttu-id="0c4bd-159">*SentimentPrediction.cs* 檔案隨即在程式碼編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-159">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="0c4bd-160">將下列 using 陳述式新增至 *SentimentPrediction.cs* 頂端：</span><span class="sxs-lookup"><span data-stu-id="0c4bd-160">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

```csharp
using Microsoft.ML.Data;
```

<span data-ttu-id="0c4bd-161">移除現有的類別定義，然後將下列程式碼新增至 *SentimentPrediction.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="0c4bd-161">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

```csharp
public class SentimentPrediction
{
    [ColumnName("PredictedLabel")]
    public bool Prediction { get; set; }
}
```

### <a name="add-prediction-logic"></a><span data-ttu-id="0c4bd-162">加入預測邏輯</span><span class="sxs-lookup"><span data-stu-id="0c4bd-162">Add Prediction Logic</span></span>

<span data-ttu-id="0c4bd-163">使用下列程式碼取代 *AnalyzeSentiment* 類別中 *Run* 方法的現有實作：</span><span class="sxs-lookup"><span data-stu-id="0c4bd-163">Replace the existing implementation of *Run* method in *AnalyzeSentiment* class with the following code:</span></span>

```csharp
    public static async Task<IActionResult> Run(
        [HttpTrigger(AuthorizationLevel.Function,"post", Route = null)] HttpRequest req,
        ILogger log)
    {
        log.LogInformation("C# HTTP trigger function processed a request.");

        //Create Context
        MLContext mlContext = new MLContext();

        //Load Model
        using (var fs = File.OpenRead("MLModels/sentiment_model.zip"))
        {
            model = mlContext.Model.Load(fs);
        }

        //Parse HTTP Request Body
        string requestBody = await new StreamReader(req.Body).ReadToEndAsync();
        SentimentData data = JsonConvert.DeserializeObject<SentimentData>(requestBody);

        //Create Prediction Engine
        PredictionEngine<SentimentData, SentimentPrediction> predictionEngine = model.CreatePredictionEngine<SentimentData, SentimentPrediction>(mlContext);

        //Make Prediction
        SentimentPrediction prediction = predictionEngine.Predict(data);

        //Convert prediction to string
        string isToxic = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";

        //Return Prediction
        return (ActionResult)new OkObjectResult(isToxic);
    }
}
```

## <a name="test-locally"></a><span data-ttu-id="0c4bd-164">在本機進行測試</span><span class="sxs-lookup"><span data-stu-id="0c4bd-164">Test Locally</span></span>

<span data-ttu-id="0c4bd-165">一切都設定好後，就可以開始測試應用程式：</span><span class="sxs-lookup"><span data-stu-id="0c4bd-165">Now that everything is set up, it's time to test the application:</span></span>

1. <span data-ttu-id="0c4bd-166">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="0c4bd-166">Run the application</span></span>
1. <span data-ttu-id="0c4bd-167">開啟 Powershell 並在提示字元中輸入下列程式碼，其中 PORT 是正在執行您應用程式的連接埠。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-167">Open PowerShell and enter the code into the prompt where PORT is the port your application is running on.</span></span> <span data-ttu-id="0c4bd-168">一般來說，連接埠是 7071。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-168">Typically the port is 7071.</span></span> 

```powershell
Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{Text="This is a very rude movie"} | ConvertTo-Json) -ContentType "application/json"
```

<span data-ttu-id="0c4bd-169">如果成功，輸出看起來應該類似下列文字：</span><span class="sxs-lookup"><span data-stu-id="0c4bd-169">If successful, the output should look similar to the text below:</span></span>

```powershell
Toxic
```

<span data-ttu-id="0c4bd-170">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="0c4bd-170">Congratulations!</span></span> <span data-ttu-id="0c4bd-171">您已成功提供您的模型，以使用 Azure Function 在網際網路上進行預測。</span><span class="sxs-lookup"><span data-stu-id="0c4bd-171">You have successfully served your model to make predictions over the internet using an Azure Function.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0c4bd-172">後續步驟</span><span class="sxs-lookup"><span data-stu-id="0c4bd-172">Next Steps</span></span>

- [<span data-ttu-id="0c4bd-173">部署到 Azure</span><span class="sxs-lookup"><span data-stu-id="0c4bd-173">Deploy to Azure</span></span>](/azure/azure-functions/functions-develop-vs#publish-to-azure)