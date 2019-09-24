---
title: 在 ASP.NET Core Web API 中部署模型
description: 使用 ASP.NET Core Web API 在網際網路上提供 ML.NET 情感分析機器學習模型
ms.date: 08/20/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: 8d21ae5ae3aa4701ddd7d042d5069351c22864bb
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182545"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a><span data-ttu-id="87814-103">在 ASP.NET Core Web API 中部署模型</span><span class="sxs-lookup"><span data-stu-id="87814-103">Deploy a model in an ASP.NET Core Web API</span></span>

<span data-ttu-id="87814-104">了解如何使用 ASP.NET Core Web API，在 Web 上提供預先定型的 ML.NET 機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="87814-104">Learn how to serve a pre-trained ML.NET machine learning model on the web using an ASP.NET Core Web API.</span></span> <span data-ttu-id="87814-105">透過 Web API 提供模型可讓您透過標準 HTTP 方法進行預測。</span><span class="sxs-lookup"><span data-stu-id="87814-105">Serving a model over a web API enables predictions via standard HTTP methods.</span></span>

> [!NOTE]
> <span data-ttu-id="87814-106">`PredictionEnginePool` 服務延伸模組目前處於預覽狀態。</span><span class="sxs-lookup"><span data-stu-id="87814-106">`PredictionEnginePool` service extension is currently in preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="87814-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="87814-107">Prerequisites</span></span>

- <span data-ttu-id="87814-108">已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)。</span><span class="sxs-lookup"><span data-stu-id="87814-108">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
- <span data-ttu-id="87814-109">PowerShell。</span><span class="sxs-lookup"><span data-stu-id="87814-109">Powershell.</span></span>
- <span data-ttu-id="87814-110">預先定型的模型。</span><span class="sxs-lookup"><span data-stu-id="87814-110">Pre-trained model.</span></span> <span data-ttu-id="87814-111">使用 [ML.NET 情感分析教學課程](../tutorials/sentiment-analysis.md)來建置您自己的模型，或是下載這個[預先定型的情感分析機器學習模型](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="87814-111">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-aspnet-core-web-api-project"></a><span data-ttu-id="87814-112">建立 ASP.NET Core Web API 專案</span><span class="sxs-lookup"><span data-stu-id="87814-112">Create ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="87814-113">開啟 Visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="87814-113">Open Visual Studio 2017.</span></span> <span data-ttu-id="87814-114">從功能表列中選取 [檔案] > [新增] > [專案]。</span><span class="sxs-lookup"><span data-stu-id="87814-114">Select **File > New > Project** from the menu bar.</span></span> <span data-ttu-id="87814-115">在 [新增專案] 對話方塊中，選取 [Visual C#] 節點，然後選取 [Web] 節點。</span><span class="sxs-lookup"><span data-stu-id="87814-115">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span> <span data-ttu-id="87814-116">然後，選取 [ASP.NET Core Web 應用程式] 專案範本。</span><span class="sxs-lookup"><span data-stu-id="87814-116">Then select the **ASP.NET Core Web Application** project template.</span></span> <span data-ttu-id="87814-117">在 [名稱] 文字方塊中，輸入 "SentimentAnalysisWebAPI"，然後選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="87814-117">In the **Name** text box, type "SentimentAnalysisWebAPI" and then select the **OK** button.</span></span>

1. <span data-ttu-id="87814-118">在顯示不同類型的 ASP.NET Core 專案的視窗中，選取 [API]，然後選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="87814-118">In the window that displays the different types of ASP.NET Core Projects, select **API** and the select the **OK** button.</span></span>

1. <span data-ttu-id="87814-119">在專案中建立名為 *MLModels* 的目錄，以儲存您預先建置的機器學習模型檔案：</span><span class="sxs-lookup"><span data-stu-id="87814-119">Create a directory named *MLModels* in your project to save your pre-built machine learning model files:</span></span>

    <span data-ttu-id="87814-120">在 [方案總管] 中，以滑鼠右鍵按一下您的專案，然後選取 [新增] > [新增資料夾]。</span><span class="sxs-lookup"><span data-stu-id="87814-120">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="87814-121">輸入 "MLModels"，然後按 Enter。</span><span class="sxs-lookup"><span data-stu-id="87814-121">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="87814-122">安裝「Microsoft.ML NuGet 套件」：</span><span class="sxs-lookup"><span data-stu-id="87814-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="87814-123">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="87814-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="87814-124">選擇 "nuget.org" 作為 [套件來源]、選取 [瀏覽] 索引標籤、搜尋 **Microsoft.ML**、從清單中選取該套件，然後選取 [安裝] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="87814-124">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="87814-125">在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。</span><span class="sxs-lookup"><span data-stu-id="87814-125">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="87814-126">安裝 **Microsoft.Extensions.ML Nuget 套件**：</span><span class="sxs-lookup"><span data-stu-id="87814-126">Install the **Microsoft.Extensions.ML Nuget Package**:</span></span>

    <span data-ttu-id="87814-127">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="87814-127">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="87814-128">選擇 "nuget.org" 作為 [套件來源]、選取 [瀏覽] 索引標籤、搜尋 **Microsoft.Extensions.ML**、從清單中選取該套件，然後選取 [安裝] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="87814-128">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="87814-129">在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。</span><span class="sxs-lookup"><span data-stu-id="87814-129">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="add-model-to-aspnet-core-web-api-project"></a><span data-ttu-id="87814-130">將模型新增至 ASP.NET Core Web API 專案</span><span class="sxs-lookup"><span data-stu-id="87814-130">Add model to ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="87814-131">將預先建置的模型複製到 *MLModels* 目錄</span><span class="sxs-lookup"><span data-stu-id="87814-131">Copy your pre-built model to the *MLModels* directory</span></span>
1. <span data-ttu-id="87814-132">在 [方案總管] 中，以滑鼠右鍵按一下模型 zip 檔案，並選取 [內容]。</span><span class="sxs-lookup"><span data-stu-id="87814-132">In Solution Explorer, right-click the model zip file and select Properties.</span></span> <span data-ttu-id="87814-133">在 [進階] 下，將 [複製到輸出目錄] 的值變更為 [有更新才複製]。</span><span class="sxs-lookup"><span data-stu-id="87814-133">Under Advanced, change the value of Copy to Output Directory to Copy if newer.</span></span>

## <a name="create-data-models"></a><span data-ttu-id="87814-134">建立資料模型</span><span class="sxs-lookup"><span data-stu-id="87814-134">Create data models</span></span>

<span data-ttu-id="87814-135">您必須為輸入資料和預測建立一些類別。</span><span class="sxs-lookup"><span data-stu-id="87814-135">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="87814-136">將新類別新增至專案：</span><span class="sxs-lookup"><span data-stu-id="87814-136">Add a new class to your project:</span></span>

1. <span data-ttu-id="87814-137">在您的專案中建立名為 *DataModels* 的目錄以儲存資料模型：</span><span class="sxs-lookup"><span data-stu-id="87814-137">Create a directory named *DataModels* in your project to save your data models:</span></span>

    <span data-ttu-id="87814-138">在 [方案總管] 中，以滑鼠右鍵按一下您的專案，然後選取 [新增] > [新增資料夾]。</span><span class="sxs-lookup"><span data-stu-id="87814-138">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="87814-139">輸入 "DataModels"，然後按 **Enter**。</span><span class="sxs-lookup"><span data-stu-id="87814-139">Type "DataModels" and hit **Enter**.</span></span>

2. <span data-ttu-id="87814-140">在 [方案總管] 中，以滑鼠右鍵按一下 *DataModels* 目錄，然後選取 [新增] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="87814-140">In Solution Explorer, right-click the *DataModels* directory, and then select Add > New Item.</span></span>
3. <span data-ttu-id="87814-141">在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *SentimentData.cs*。</span><span class="sxs-lookup"><span data-stu-id="87814-141">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="87814-142">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="87814-142">Then, select the **Add** button.</span></span> <span data-ttu-id="87814-143">*SentimentData.cs* 檔案隨即在程式碼編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="87814-143">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="87814-144">將下列 using 陳述式新增至 *SentimentData.cs* 頂端：</span><span class="sxs-lookup"><span data-stu-id="87814-144">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```
    
    <span data-ttu-id="87814-145">移除現有的類別定義，然後將下列程式碼新增至 **SentimentData.cs** 檔案：</span><span class="sxs-lookup"><span data-stu-id="87814-145">Remove the existing class definition and add the following code to the **SentimentData.cs** file:</span></span>
    
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

4. <span data-ttu-id="87814-146">在 [方案總管] 中，以滑鼠右鍵按一下 *DataModels* 目錄，然後選取 [新增] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="87814-146">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="87814-147">在 [加入新項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *SentimentPrediction.cs*。</span><span class="sxs-lookup"><span data-stu-id="87814-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="87814-148">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="87814-148">Then, select the Add button.</span></span> <span data-ttu-id="87814-149">*SentimentPrediction.cs* 檔案隨即在程式碼編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="87814-149">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="87814-150">將下列 using 陳述式新增至 *SentimentPrediction.cs* 頂端：</span><span class="sxs-lookup"><span data-stu-id="87814-150">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```
    
    <span data-ttu-id="87814-151">移除現有的類別定義，然後將下列程式碼新增至 *SentimentPrediction.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="87814-151">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>
    
    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    <span data-ttu-id="87814-152">`SentimentPrediction` 繼承自 `SentimentData`。</span><span class="sxs-lookup"><span data-stu-id="87814-152">`SentimentPrediction` inherits from `SentimentData`.</span></span> <span data-ttu-id="87814-153">這可讓您更輕易地看到 `SentimentText` 屬性中的原始資料，以及模型所產生的輸出。</span><span class="sxs-lookup"><span data-stu-id="87814-153">This makes it easier to see the original data in the `SentimentText` property along with the output generated by the model.</span></span> 

## <a name="register-predictionenginepool-for-use-in-the-application"></a><span data-ttu-id="87814-154">登錄 PredictionEnginePool 以在應用程式中使用</span><span class="sxs-lookup"><span data-stu-id="87814-154">Register PredictionEnginePool for use in the application</span></span>

<span data-ttu-id="87814-155">若要進行單一預測，請使用 [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)。</span><span class="sxs-lookup"><span data-stu-id="87814-155">To make a single prediction, use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="87814-156">為了在您的應用程式中使用 [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)，您必須在需要的時候建立它。</span><span class="sxs-lookup"><span data-stu-id="87814-156">In order to use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) in your application you must create it when it's needed.</span></span> <span data-ttu-id="87814-157">在此情況下，要考慮的最佳做法是相依性插入。</span><span class="sxs-lookup"><span data-stu-id="87814-157">In that case, a best practice to consider is dependency injection.</span></span>

<span data-ttu-id="87814-158">若您想要深入了解 [ASP.NET Core 中的相依性插入](/aspnet/core/fundamentals/dependency-injection)，下列連結提供詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="87814-158">The following link provides more information if you want to learn about [dependency injection in ASP.NET Core](/aspnet/core/fundamentals/dependency-injection).</span></span>

1. <span data-ttu-id="87814-159">開啟 *Startup.cs* 類別，並將下列 using 陳述式新增至檔案頂端：</span><span class="sxs-lookup"><span data-stu-id="87814-159">Open the *Startup.cs* class and add the following using statement to the top of the file:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

2. <span data-ttu-id="87814-160">將下列程式碼新增到 *ConfigureServices* 方法：</span><span class="sxs-lookup"><span data-stu-id="87814-160">Add the following code to the *ConfigureServices* method:</span></span>

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_1);
        services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
            .FromFile("MLModels/sentiment_model.zip");
    }
    ```

<span data-ttu-id="87814-161">概括而言，此程式碼會在應用程式要求時自動初始化物件和服務，不必手動執行。</span><span class="sxs-lookup"><span data-stu-id="87814-161">At a high level, this code initializes the objects and services automatically when requested by the application instead of having to manually do it.</span></span>

> [!WARNING]
> <span data-ttu-id="87814-162">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) 不是安全執行緒。</span><span class="sxs-lookup"><span data-stu-id="87814-162">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="87814-163">為了改善效能及執行緒安全性，請使用 `PredictionEnginePool` 服務，該服務會建立 `PredictionEngine` 物件的 [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) 以供應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="87814-163">For improved performance and thread safety, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of `PredictionEngine` objects for application use.</span></span> <span data-ttu-id="87814-164">閱讀下列部落格文章來深入了解[建立及使用 ASP.NET Core 中的 `PredictionEngine` 物件集區](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/)。</span><span class="sxs-lookup"><span data-stu-id="87814-164">Read the following blog post to learn more about [creating and using `PredictionEngine` object pools in ASP.NET Core](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span></span>  

## <a name="create-predict-controller"></a><span data-ttu-id="87814-165">建立預測控制器</span><span class="sxs-lookup"><span data-stu-id="87814-165">Create Predict controller</span></span>

<span data-ttu-id="87814-166">若要處理傳入的 HTTP 要求，請建立一個控制器。</span><span class="sxs-lookup"><span data-stu-id="87814-166">To process your incoming HTTP requests, create a controller.</span></span>

1. <span data-ttu-id="87814-167">在 [方案總管] 中，以滑鼠右鍵按一下 *Controllers* 目錄，然後選取 [新增] > [控制器]。</span><span class="sxs-lookup"><span data-stu-id="87814-167">In Solution Explorer, right-click the *Controllers* directory, and then select **Add > Controller**.</span></span>
1. <span data-ttu-id="87814-168">在 [加入新項目] 對話方塊中，選取 [API 控制器 - 空白]，然後選取 [新增]。</span><span class="sxs-lookup"><span data-stu-id="87814-168">In the **Add New Item** dialog box, select **API Controller Empty** and select **Add**.</span></span>
1. <span data-ttu-id="87814-169">在提示中，將 [控制器名稱] 欄位變更為 *PredictController.cs*。</span><span class="sxs-lookup"><span data-stu-id="87814-169">In the prompt change the **Controller Name** field to *PredictController.cs*.</span></span> <span data-ttu-id="87814-170">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="87814-170">Then, select the Add button.</span></span> <span data-ttu-id="87814-171">*PredictController.cs* 檔案隨即在程式碼編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="87814-171">The *PredictController.cs* file opens in the code editor.</span></span> <span data-ttu-id="87814-172">將下列 using 陳述式新增至 *PredictController.cs* 頂端：</span><span class="sxs-lookup"><span data-stu-id="87814-172">Add the following using statement to the top of *PredictController.cs*:</span></span>

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

    <span data-ttu-id="87814-173">移除現有的類別定義，然後將下列程式碼新增至 *PredictController.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="87814-173">Remove the existing class definition and add the following code to the *PredictController.cs* file:</span></span>
    
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

            SentimentPrediction prediction = _predictionEnginePool.Predict(input);

            string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

            return Ok(sentiment);
        }
    }
    ```

<span data-ttu-id="87814-174">此程式碼會透過將預測服務傳遞至控制器的建構函式 (透過相依性插入取得) 來指派 `PredictionEnginePool`。</span><span class="sxs-lookup"><span data-stu-id="87814-174">This code assigns the `PredictionEnginePool` by passing it to the controller's constructor which you get via dependency injection.</span></span> <span data-ttu-id="87814-175">然後，`Predict` 控制器的 `Post` 方法會使用 `PredictionEnginePool` 來進行預測，並將結果傳回使用者 (若成功的話)。</span><span class="sxs-lookup"><span data-stu-id="87814-175">Then, the `Predict` controller's `Post` method uses the `PredictionEnginePool` to make predictions and return the results back to the user if successful.</span></span>

## <a name="test-web-api-locally"></a><span data-ttu-id="87814-176">在本機測試 Web API</span><span class="sxs-lookup"><span data-stu-id="87814-176">Test web API locally</span></span>

<span data-ttu-id="87814-177">一切都設定好後，就可以開始測試應用程式。</span><span class="sxs-lookup"><span data-stu-id="87814-177">Once everything is set up, it's time to test the application.</span></span>

1. <span data-ttu-id="87814-178">執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="87814-178">Run the application.</span></span>
1. <span data-ttu-id="87814-179">開啟 Powershell 並輸入下列程式碼，其中 PORT 是應用程式正在接聽的連接埠。</span><span class="sxs-lookup"><span data-stu-id="87814-179">Open Powershell and enter the following code where PORT is the port your application is listening on.</span></span>

    ```powershell
    Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{SentimentText="This was a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="87814-180">如果成功，輸出看起來應該類似下列文字：</span><span class="sxs-lookup"><span data-stu-id="87814-180">If successful, the output should look similar to the text below:</span></span>
    
    ```powershell
    Negative
    ```

<span data-ttu-id="87814-181">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="87814-181">Congratulations!</span></span> <span data-ttu-id="87814-182">您已成功提供您的模型，使用 ASP.NET Core Web API 在網際網路上進行預測。</span><span class="sxs-lookup"><span data-stu-id="87814-182">You have successfully served your model to make predictions over the internet using an ASP.NET Core Web API.</span></span>

## <a name="next-steps"></a><span data-ttu-id="87814-183">後續步驟</span><span class="sxs-lookup"><span data-stu-id="87814-183">Next Steps</span></span>

- [<span data-ttu-id="87814-184">部署到 Azure</span><span class="sxs-lookup"><span data-stu-id="87814-184">Deploy to Azure</span></span>](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs#deploy-the-app-to-azure)
