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
# <a name="deploy-a-model-to-azure-functions"></a><span data-ttu-id="07b15-103">將模型部署到 Azure Functions</span><span class="sxs-lookup"><span data-stu-id="07b15-103">Deploy a model to Azure Functions</span></span>

<span data-ttu-id="07b15-104">了解如何部署預先定型的 ML.NET 機器學習模型，以使用 Azure Functions 無伺服器環境透過 HTTP 進行預測。</span><span class="sxs-lookup"><span data-stu-id="07b15-104">Learn how to deploy a pre-trained ML.NET machine learning model for predictions over HTTP through an Azure Functions serverless environment.</span></span>

> [!NOTE]
> <span data-ttu-id="07b15-105">`PredictionEnginePool` 服務延伸模組目前處於預覽狀態。</span><span class="sxs-lookup"><span data-stu-id="07b15-105">`PredictionEnginePool` service extension is currently in preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="07b15-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="07b15-106">Prerequisites</span></span>

- <span data-ttu-id="07b15-107">已安裝「.NET Core 跨平台開發」工作負載和「Azure 開發」的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)。</span><span class="sxs-lookup"><span data-stu-id="07b15-107">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload and "Azure development" installed.</span></span>
- [<span data-ttu-id="07b15-108">Azure Functions Tools</span><span class="sxs-lookup"><span data-stu-id="07b15-108">Azure Functions Tools</span></span>](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- <span data-ttu-id="07b15-109">Powershell</span><span class="sxs-lookup"><span data-stu-id="07b15-109">Powershell</span></span>
- <span data-ttu-id="07b15-110">預先定型的模型。</span><span class="sxs-lookup"><span data-stu-id="07b15-110">Pre-trained model.</span></span> <span data-ttu-id="07b15-111">使用 [ML.NET 情感分析教學課程](../tutorials/sentiment-analysis.md)來建置您自己的模型，或是下載這個[預先定型的情感分析機器學習模型](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="07b15-111">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-azure-functions-project"></a><span data-ttu-id="07b15-112">建立 Azure Functions 專案</span><span class="sxs-lookup"><span data-stu-id="07b15-112">Create Azure Functions project</span></span>

1. <span data-ttu-id="07b15-113">開啟 Visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="07b15-113">Open Visual Studio 2017.</span></span> <span data-ttu-id="07b15-114">從功能表列中選取 [檔案]  >  [新增]  >  [專案]。</span><span class="sxs-lookup"><span data-stu-id="07b15-114">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="07b15-115">在 [新增專案] 對話方塊中，選取 [Visual C#] 節點，然後選取 [雲端] 節點。</span><span class="sxs-lookup"><span data-stu-id="07b15-115">In the **New Project** dialog, select the **Visual C#** node followed by the **Cloud** node.</span></span> <span data-ttu-id="07b15-116">然後選取 [Azure Functions] 專案範本。</span><span class="sxs-lookup"><span data-stu-id="07b15-116">Then select the **Azure Functions** project template.</span></span> <span data-ttu-id="07b15-117">在 [名稱] 文字方塊中，輸入 "SentimentAnalysisFunctionsApp"，然後選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="07b15-117">In the **Name** text box, type "SentimentAnalysisFunctionsApp" and then select the **OK** button.</span></span>
1. <span data-ttu-id="07b15-118">在 [新增專案] 對話方塊中，開啟專案選項上方的下拉式清單，然後選取 [Azure Functions v2 (.NET Core)]。</span><span class="sxs-lookup"><span data-stu-id="07b15-118">In the **New Project** dialog, open the dropdown above the project options and select **Azure Functions v2 (.NET Core)**.</span></span> <span data-ttu-id="07b15-119">然後，選取 [Http 觸發程序] 專案，然後選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="07b15-119">Then, select the **Http trigger** project and then select the **OK** button.</span></span>
1. <span data-ttu-id="07b15-120">在您的專案中建立名為 *MLModels* 的目錄，以儲存您的模型：</span><span class="sxs-lookup"><span data-stu-id="07b15-120">Create a directory named *MLModels* in your project to save your model:</span></span>

    <span data-ttu-id="07b15-121">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [新增] > [新增資料夾]。</span><span class="sxs-lookup"><span data-stu-id="07b15-121">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="07b15-122">輸入 "MLModels"，然後按 Enter。</span><span class="sxs-lookup"><span data-stu-id="07b15-122">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="07b15-123">安裝「Microsoft.ML NuGet 套件」：</span><span class="sxs-lookup"><span data-stu-id="07b15-123">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="07b15-124">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="07b15-124">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="07b15-125">選擇 "nuget.org" 作為 [套件來源]，選取 [瀏覽] 索引標籤、搜尋 **Microsoft.ML**、從清單中選取該套件，然後選取 [安裝] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="07b15-125">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="07b15-126">在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。</span><span class="sxs-lookup"><span data-stu-id="07b15-126">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="07b15-127">安裝 **Microsoft.Extensions.ML NuGet 套件**：</span><span class="sxs-lookup"><span data-stu-id="07b15-127">Install the **Microsoft.Extensions.ML NuGet Package**:</span></span>

    <span data-ttu-id="07b15-128">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="07b15-128">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="07b15-129">選擇 "nuget.org" 作為 [套件來源]、選取 [瀏覽] 索引標籤、搜尋 **Microsoft.Extensions.ML**、從清單中選取該套件，然後選取 [安裝] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="07b15-129">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="07b15-130">在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。</span><span class="sxs-lookup"><span data-stu-id="07b15-130">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="add-pre-trained-model-to-project"></a><span data-ttu-id="07b15-131">將預先定型的模型新增到專案</span><span class="sxs-lookup"><span data-stu-id="07b15-131">Add pre-trained model to project</span></span>

1. <span data-ttu-id="07b15-132">將預先建置的模型複製到 *MLModels* 目錄。</span><span class="sxs-lookup"><span data-stu-id="07b15-132">Copy your pre-built model to the *MLModels* folder.</span></span>
1. <span data-ttu-id="07b15-133">在 [方案總管] 中，以滑鼠右鍵按一下您預先建置的模型檔案，並選取 [內容]。</span><span class="sxs-lookup"><span data-stu-id="07b15-133">In Solution Explorer, right-click your pre-built model file and select **Properties**.</span></span> <span data-ttu-id="07b15-134">在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。</span><span class="sxs-lookup"><span data-stu-id="07b15-134">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

## <a name="create-azure-function-to-analyze-sentiment"></a><span data-ttu-id="07b15-135">建立 Azure Function 來分析情感</span><span class="sxs-lookup"><span data-stu-id="07b15-135">Create Azure Function to analyze sentiment</span></span>

<span data-ttu-id="07b15-136">建立用來預測情緒的類別。</span><span class="sxs-lookup"><span data-stu-id="07b15-136">Create a class to predict sentiment.</span></span> <span data-ttu-id="07b15-137">將新類別新增至專案：</span><span class="sxs-lookup"><span data-stu-id="07b15-137">Add a new class to your project:</span></span>

1. <span data-ttu-id="07b15-138">在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="07b15-138">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="07b15-139">在 [新增項目] 對話方塊中，選取 [Azure Function]，然後將 [名稱] 欄位變更為 *AnalyzeSentiment.cs*。</span><span class="sxs-lookup"><span data-stu-id="07b15-139">In the **Add New Item** dialog box, select **Azure Function** and change the **Name** field to *AnalyzeSentiment.cs*.</span></span> <span data-ttu-id="07b15-140">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="07b15-140">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="07b15-141">在 [新增 Azure 函式] 對話方塊中，選取 [Http 觸發程序]。</span><span class="sxs-lookup"><span data-stu-id="07b15-141">In the **New Azure Function** dialog box, select **Http Trigger**.</span></span> <span data-ttu-id="07b15-142">然後，選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="07b15-142">Then, select the **OK** button.</span></span>

    <span data-ttu-id="07b15-143">*AnalyzeSentiment.cs* 檔案隨即在程式碼編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="07b15-143">The *AnalyzeSentiment.cs* file opens in the code editor.</span></span> <span data-ttu-id="07b15-144">將下列 `using` 陳述式新增到 *AnalyzeSentiment.cs* 的頂端：</span><span class="sxs-lookup"><span data-stu-id="07b15-144">Add the following `using` statement to the top of *AnalyzeSentiment.cs*:</span></span>

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

    <span data-ttu-id="07b15-145">根據預設，`AnalyzeSentiment` 類別為 `static`。</span><span class="sxs-lookup"><span data-stu-id="07b15-145">By default, the `AnalyzeSentiment` class is `static`.</span></span> <span data-ttu-id="07b15-146">請務必從類別定義移除 `static` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="07b15-146">Make sure to remove the `static` keyword from the class definition.</span></span>

    ```csharp
    public class AnalyzeSentiment
    {
    
    }
    ```

## <a name="create-data-models"></a><span data-ttu-id="07b15-147">建立資料模型</span><span class="sxs-lookup"><span data-stu-id="07b15-147">Create data models</span></span>

<span data-ttu-id="07b15-148">您必須為輸入資料和預測建立一些類別。</span><span class="sxs-lookup"><span data-stu-id="07b15-148">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="07b15-149">將新類別新增至專案：</span><span class="sxs-lookup"><span data-stu-id="07b15-149">Add a new class to your project:</span></span>

1. <span data-ttu-id="07b15-150">在您的專案中建立名為 *DataModels* 的目錄以儲存資料模型：在 [方案總管] 中，以滑鼠右鍵按一下您的專案，然後選取 [新增] > [新增資料夾]。</span><span class="sxs-lookup"><span data-stu-id="07b15-150">Create a directory named *DataModels* in your project to save your data models: In Solution Explorer, right-click on your project and select **Add > New Folder**.</span></span> <span data-ttu-id="07b15-151">輸入 "DataModels"，然後按 Enter。</span><span class="sxs-lookup"><span data-stu-id="07b15-151">Type "DataModels" and hit Enter.</span></span>
2. <span data-ttu-id="07b15-152">在 [方案總管] 中，以滑鼠右鍵按一下 *DataModels* 目錄，然後選取 [新增] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="07b15-152">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
3. <span data-ttu-id="07b15-153">在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *SentimentData.cs*。</span><span class="sxs-lookup"><span data-stu-id="07b15-153">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="07b15-154">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="07b15-154">Then, select the **Add** button.</span></span> 

    <span data-ttu-id="07b15-155">*SentimentData.cs* 檔案隨即在程式碼編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="07b15-155">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="07b15-156">將下列 using 陳述式新增至 *SentimentData.cs* 頂端：</span><span class="sxs-lookup"><span data-stu-id="07b15-156">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="07b15-157">移除現有的類別定義，然後將下列程式碼新增至 *SentimentData.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="07b15-157">Remove the existing class definition and add the following code to the *SentimentData.cs* file:</span></span>
    
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

4. <span data-ttu-id="07b15-158">在 [方案總管] 中，以滑鼠右鍵按一下 *DataModels* 目錄，然後選取 [新增] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="07b15-158">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="07b15-159">在 [加入新項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *SentimentPrediction.cs*。</span><span class="sxs-lookup"><span data-stu-id="07b15-159">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="07b15-160">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="07b15-160">Then, select the **Add** button.</span></span> <span data-ttu-id="07b15-161">*SentimentPrediction.cs* 檔案隨即在程式碼編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="07b15-161">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="07b15-162">將下列 using 陳述式新增至 *SentimentPrediction.cs* 頂端：</span><span class="sxs-lookup"><span data-stu-id="07b15-162">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="07b15-163">移除現有的類別定義，然後將下列程式碼新增至 *SentimentPrediction.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="07b15-163">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    <span data-ttu-id="07b15-164">`SentimentPrediction` 會從 `SentimentData` 繼承，後者會在 `SentimentText` 屬性中提供原始資料的存取，以及由模型產生的輸出。</span><span class="sxs-lookup"><span data-stu-id="07b15-164">`SentimentPrediction` inherits from `SentimentData` which provides access to the original data in the `SentimentText` property as well as the output generated by the model.</span></span>

## <a name="register-predictionenginepool-service"></a><span data-ttu-id="07b15-165">登錄 PredictionEnginePool 服務</span><span class="sxs-lookup"><span data-stu-id="07b15-165">Register PredictionEnginePool service</span></span>

<span data-ttu-id="07b15-166">若要進行單一預測，請使用 [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)。</span><span class="sxs-lookup"><span data-stu-id="07b15-166">To make a single prediction, use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="07b15-167">為了在您的應用程式中使用 [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)，您必須在需要的時候建立它。</span><span class="sxs-lookup"><span data-stu-id="07b15-167">In order to use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) in your application you must create it when it's needed.</span></span> <span data-ttu-id="07b15-168">在此情況下，要考慮的最佳做法是相依性插入。</span><span class="sxs-lookup"><span data-stu-id="07b15-168">In that case, a best practice to consider is dependency injection.</span></span>

<span data-ttu-id="07b15-169">如果您想要深入了解[相依性插入](https://en.wikipedia.org/wiki/Dependency_injection)，下列連結提供詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="07b15-169">The following link provides more information if you want to learn about [dependency injection](https://en.wikipedia.org/wiki/Dependency_injection).</span></span>

1. <span data-ttu-id="07b15-170">在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="07b15-170">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="07b15-171">在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *Startup.cs*。</span><span class="sxs-lookup"><span data-stu-id="07b15-171">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *Startup.cs*.</span></span> <span data-ttu-id="07b15-172">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="07b15-172">Then, select the **Add** button.</span></span> 

    <span data-ttu-id="07b15-173">*Startup.cs* 檔案隨即在程式碼編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="07b15-173">The *Startup.cs* file opens in the code editor.</span></span> <span data-ttu-id="07b15-174">將下列的 using 陳述式新增到 *Startup.cs* 的頂端：</span><span class="sxs-lookup"><span data-stu-id="07b15-174">Add the following using statement to the top of *Startup.cs*:</span></span>

    ```csharp
    using Microsoft.Azure.WebJobs;
    using Microsoft.Azure.WebJobs.Hosting;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisFunctionsApp;
    using SentimentAnalysisFunctionsApp.DataModels;
    ```

    <span data-ttu-id="07b15-175">移除 using 陳述式下方的現有程式碼，並將下列程式碼新增到 *Startup.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="07b15-175">Remove the existing code below the using statements and add the following code to the *Startup.cs* file:</span></span>

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

<span data-ttu-id="07b15-176">概括而言，此程式碼會在應用程式要求時自動初始化物件和服務，不必手動執行。</span><span class="sxs-lookup"><span data-stu-id="07b15-176">At a high level, this code initializes the objects and services automatically when requested by the application instead of having to manually do it.</span></span>

> [!WARNING]
> <span data-ttu-id="07b15-177">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) 不是安全執行緒。</span><span class="sxs-lookup"><span data-stu-id="07b15-177">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="07b15-178">為了改善效能及執行緒安全性，請使用 `PredictionEnginePool` 服務，該服務會建立 `PredictionEngine` 物件的 [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601)以供應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="07b15-178">For improved performance and thread safety, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of `PredictionEngine` objects for application use.</span></span> 

## <a name="register-startup-as-an-azure-functions-extension"></a><span data-ttu-id="07b15-179">將 Startup 登錄為 Azure Functions 延伸模組</span><span class="sxs-lookup"><span data-stu-id="07b15-179">Register Startup as an Azure Functions extension</span></span>

<span data-ttu-id="07b15-180">為了在您的應用程式中使用 `Startup`，您需要將它登錄為 Azure Functions 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="07b15-180">In order to use `Startup` in your application, you need to register it as an Azure Functions extension.</span></span> <span data-ttu-id="07b15-181">在您專案中建立稱為 *extensions.json* 的新檔案 (若尚未存在的話)。</span><span class="sxs-lookup"><span data-stu-id="07b15-181">Create a new file called *extensions.json* in your project if one does not already exist.</span></span>

1. <span data-ttu-id="07b15-182">在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="07b15-182">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="07b15-183">在 [新增項目] 對話方塊中，選取 **Visual C#** 節點，然後選取 **Web** 節點。</span><span class="sxs-lookup"><span data-stu-id="07b15-183">In the **New Item** dialog, select the **Visual C#** node followed by the **Web** node.</span></span> <span data-ttu-id="07b15-184">然後選取 [JSON 檔案] 選項。</span><span class="sxs-lookup"><span data-stu-id="07b15-184">Then select the **Json File** option.</span></span> <span data-ttu-id="07b15-185">在 [名稱] 文字方塊中，輸入 "extensions.json"，然後選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="07b15-185">In the **Name** text box, type "extensions.json" and then select the **OK** button.</span></span>

    <span data-ttu-id="07b15-186">*extensions.json* 檔案隨即在程式碼編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="07b15-186">The *extensions.json* file opens in the code editor.</span></span> <span data-ttu-id="07b15-187">將下列內容新增至 *extensions.json*：</span><span class="sxs-lookup"><span data-stu-id="07b15-187">Add the following content to *extensions.json*:</span></span>
    
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

1. <span data-ttu-id="07b15-188">在 [方案總管] 中，以滑鼠右鍵按一下您的 *extensions.json* 檔案，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="07b15-188">In Solution Explorer, right-click your *extensions.json* file and select **Properties**.</span></span> <span data-ttu-id="07b15-189">在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。</span><span class="sxs-lookup"><span data-stu-id="07b15-189">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

## <a name="load-the-model-into-the-function"></a><span data-ttu-id="07b15-190">將模型載入函式</span><span class="sxs-lookup"><span data-stu-id="07b15-190">Load the model into the function</span></span>

<span data-ttu-id="07b15-191">將下列程式碼插入 *AnalyzeSentiment* 類別：</span><span class="sxs-lookup"><span data-stu-id="07b15-191">Insert the following code inside the *AnalyzeSentiment* class:</span></span>

```csharp
private readonly PredictionEnginePool<SentimentData, SentimentPrediction> _predictionEnginePool;

// AnalyzeSentiment class constructor
public AnalyzeSentiment(PredictionEnginePool<SentimentData, SentimentPrediction> predictionEnginePool)
{
    _predictionEnginePool = predictionEnginePool;
}
```

<span data-ttu-id="07b15-192">此程式碼會透過將 `PredictionEnginePool` 傳遞到您透過相依性插入所取得的函式建構函式來指派它。</span><span class="sxs-lookup"><span data-stu-id="07b15-192">This code assigns the `PredictionEnginePool` by passing it to the function's constructor which you get via dependency injection.</span></span>

## <a name="use-the-model-to-make-predictions"></a><span data-ttu-id="07b15-193">使用模型進行預測</span><span class="sxs-lookup"><span data-stu-id="07b15-193">Use the model to make predictions</span></span>

<span data-ttu-id="07b15-194">使用下列程式碼取代 *AnalyzeSentiment* 類別中 *Run* 方法的現有實作：</span><span class="sxs-lookup"><span data-stu-id="07b15-194">Replace the existing implementation of *Run* method in *AnalyzeSentiment* class with the following code:</span></span>

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

<span data-ttu-id="07b15-195">`Run` 方法執行時，來自 HTTP 請求的傳入資料會還原序列化，並用來作為 `PredictionEnginePool` 的輸入。</span><span class="sxs-lookup"><span data-stu-id="07b15-195">When the `Run` method executes, the incoming data from the HTTP request is deserialized and used as input for the `PredictionEnginePool`.</span></span> <span data-ttu-id="07b15-196">接著會呼叫 `Predict` 方法來產生預測，並將結果傳回使用者。</span><span class="sxs-lookup"><span data-stu-id="07b15-196">The `Predict` method is then called to generate a prediction and return the result to the user.</span></span> 

## <a name="test-locally"></a><span data-ttu-id="07b15-197">在本機進行測試</span><span class="sxs-lookup"><span data-stu-id="07b15-197">Test locally</span></span>

<span data-ttu-id="07b15-198">一切都設定好後，就可以開始測試應用程式：</span><span class="sxs-lookup"><span data-stu-id="07b15-198">Now that everything is set up, it's time to test the application:</span></span>

1. <span data-ttu-id="07b15-199">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="07b15-199">Run the application</span></span>
1. <span data-ttu-id="07b15-200">開啟 Powershell 並在提示字元中輸入下列程式碼，其中 PORT 是正在執行您應用程式的連接埠。</span><span class="sxs-lookup"><span data-stu-id="07b15-200">Open PowerShell and enter the code into the prompt where PORT is the port your application is running on.</span></span> <span data-ttu-id="07b15-201">一般來說，連接埠是 7071。</span><span class="sxs-lookup"><span data-stu-id="07b15-201">Typically the port is 7071.</span></span>

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="07b15-202">如果成功，輸出看起來應該類似下列文字：</span><span class="sxs-lookup"><span data-stu-id="07b15-202">If successful, the output should look similar to the text below:</span></span>
    
    ```powershell
    Negative
    ```

<span data-ttu-id="07b15-203">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="07b15-203">Congratulations!</span></span> <span data-ttu-id="07b15-204">您已成功提供您的模型，以使用 Azure Function 在網際網路上進行預測。</span><span class="sxs-lookup"><span data-stu-id="07b15-204">You have successfully served your model to make predictions over the internet using an Azure Function.</span></span>

## <a name="next-steps"></a><span data-ttu-id="07b15-205">後續步驟</span><span class="sxs-lookup"><span data-stu-id="07b15-205">Next Steps</span></span>

- [<span data-ttu-id="07b15-206">部署到 Azure</span><span class="sxs-lookup"><span data-stu-id="07b15-206">Deploy to Azure</span></span>](/azure/azure-functions/functions-develop-vs#publish-to-azure)
