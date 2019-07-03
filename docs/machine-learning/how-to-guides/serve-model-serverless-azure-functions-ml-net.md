---
title: 將模型部署到 Azure Functions
description: 使用 Azure Functions 在網際網路上提供 ML.NET 情感分析機器學習模型以進行預測
ms.date: 06/11/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 7df7a6f9fcc5a4702171e1aac4b6b67e0c343748
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025987"
---
# <a name="deploy-a-model-to-azure-functions"></a><span data-ttu-id="ad2ae-103">將模型部署到 Azure Functions</span><span class="sxs-lookup"><span data-stu-id="ad2ae-103">Deploy a model to Azure Functions</span></span>

<span data-ttu-id="ad2ae-104">了解如何部署預先定型的 ML.NET 機器學習模型，以使用 Azure Functions 無伺服器環境透過 HTTP 進行預測。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-104">Learn how to deploy a pre-trained ML.NET machine learning model for predictions over HTTP through an Azure Functions serverless environment.</span></span>

> [!NOTE]
> <span data-ttu-id="ad2ae-105">`PredictionEnginePool` 服務延伸模組目前處於預覽狀態。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-105">`PredictionEnginePool` service extension is currently in preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ad2ae-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="ad2ae-106">Prerequisites</span></span>

- <span data-ttu-id="ad2ae-107">已安裝「.NET Core 跨平台開發」工作負載和「Azure 開發」的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-107">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload and "Azure development" installed.</span></span>
- <span data-ttu-id="ad2ae-108">Microsoft.NET.Sdk.Functions NuGet 套件版本 1.0.28+。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-108">Microsoft.NET.Sdk.Functions NuGet Package version 1.0.28+.</span></span>
- [<span data-ttu-id="ad2ae-109">Azure Functions Tools</span><span class="sxs-lookup"><span data-stu-id="ad2ae-109">Azure Functions Tools</span></span>](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- <span data-ttu-id="ad2ae-110">Powershell</span><span class="sxs-lookup"><span data-stu-id="ad2ae-110">Powershell</span></span>
- <span data-ttu-id="ad2ae-111">預先定型的模型。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-111">Pre-trained model.</span></span> <span data-ttu-id="ad2ae-112">使用 [ML.NET 情感分析教學課程](../tutorials/sentiment-analysis.md)來建置您自己的模型，或是下載這個[預先定型的情感分析機器學習模型](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="ad2ae-112">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-azure-functions-project"></a><span data-ttu-id="ad2ae-113">建立 Azure Functions 專案</span><span class="sxs-lookup"><span data-stu-id="ad2ae-113">Create Azure Functions project</span></span>

1. <span data-ttu-id="ad2ae-114">開啟 Visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-114">Open Visual Studio 2017.</span></span> <span data-ttu-id="ad2ae-115">從功能表列中選取 [檔案]   >  [新增]   >  [專案]  。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-115">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="ad2ae-116">在 [新增專案]  對話方塊中，選取 [Visual C#]  節點，然後選取 [雲端]  節點。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-116">In the **New Project** dialog, select the **Visual C#** node followed by the **Cloud** node.</span></span> <span data-ttu-id="ad2ae-117">然後選取 [Azure Functions]  專案範本。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-117">Then select the **Azure Functions** project template.</span></span> <span data-ttu-id="ad2ae-118">在 [名稱]  文字方塊中，輸入 "SentimentAnalysisFunctionsApp"，然後選取 [確定]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-118">In the **Name** text box, type "SentimentAnalysisFunctionsApp" and then select the **OK** button.</span></span>
1. <span data-ttu-id="ad2ae-119">在 [新增專案]  對話方塊中，開啟專案選項上方的下拉式清單，然後選取 [Azure Functions v2 (.NET Core)]  。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-119">In the **New Project** dialog, open the dropdown above the project options and select **Azure Functions v2 (.NET Core)**.</span></span> <span data-ttu-id="ad2ae-120">然後，選取 [Http 觸發程序]  專案，然後選取 [確定]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-120">Then, select the **Http trigger** project and then select the **OK** button.</span></span>
1. <span data-ttu-id="ad2ae-121">在您的專案中建立名為 *MLModels* 的目錄，以儲存您的模型：</span><span class="sxs-lookup"><span data-stu-id="ad2ae-121">Create a directory named *MLModels* in your project to save your model:</span></span>

    <span data-ttu-id="ad2ae-122">在 [方案總管]  中，於您的專案上按一下滑鼠右鍵，然後選取 [新增]   > [新增資料夾]  。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-122">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="ad2ae-123">輸入 "MLModels"，然後按 Enter。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-123">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="ad2ae-124">安裝「Microsoft.ML NuGet 套件」  ：</span><span class="sxs-lookup"><span data-stu-id="ad2ae-124">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="ad2ae-125">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]  。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-125">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="ad2ae-126">選擇 "nuget.org" 作為 [套件來源]，選取 [瀏覽] 索引標籤、搜尋 **Microsoft.ML**、從清單中選取該套件，然後選取 [安裝]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-126">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="ad2ae-127">在 [預覽變更]  對話方塊上，選取 [確定]  按鈕，然後在 [授權接受]  對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]  。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-127">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="ad2ae-128">安裝 **Microsoft.Azure.Functions.Extensions NuGet 套件**：</span><span class="sxs-lookup"><span data-stu-id="ad2ae-128">Install the **Microsoft.Azure.Functions.Extensions NuGet Package**:</span></span>

    <span data-ttu-id="ad2ae-129">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]  。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-129">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="ad2ae-130">選擇 "nuget.org" 作為 [套件來源]、選取 [瀏覽] 索引標籤、搜尋 **Microsoft.Azure.Functions.Extensions**、從清單中選取該套件，然後選取 [安裝]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-130">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Azure.Functions.Extensions**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="ad2ae-131">在 [預覽變更]  對話方塊上，選取 [確定]  按鈕，然後在 [授權接受]  對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]  。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-131">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="ad2ae-132">安裝 **Microsoft.Extensions.ML NuGet 套件**：</span><span class="sxs-lookup"><span data-stu-id="ad2ae-132">Install the **Microsoft.Extensions.ML NuGet Package**:</span></span>

    <span data-ttu-id="ad2ae-133">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]  。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-133">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="ad2ae-134">選擇 "nuget.org" 作為 [套件來源]、選取 [瀏覽] 索引標籤、搜尋 **Microsoft.Extensions.ML**、從清單中選取該套件，然後選取 [安裝]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-134">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="ad2ae-135">在 [預覽變更]  對話方塊上，選取 [確定]  按鈕，然後在 [授權接受]  對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]  。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-135">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="ad2ae-136">將 **Microsoft.NET.Sdk.Functions NuGet 套件**版本更新至 1.0.28：</span><span class="sxs-lookup"><span data-stu-id="ad2ae-136">Update the **Microsoft.NET.Sdk.Functions NuGet Package** to version 1.0.28:</span></span>

    <span data-ttu-id="ad2ae-137">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]  。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-137">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="ad2ae-138">選擇 "nuget.org" 作為套件來源、選取 [安裝] 索引標籤、搜尋 **Microsoft.NET.Sdk.Functions**、從 [版本] 下拉式清單選取 1.0.28 或更新版本，然後選取 [更新]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-138">Choose "nuget.org" as the Package source, select the Installed tab, search for **Microsoft.NET.Sdk.Functions**, select that package in the list, select 1.0.28 or later from the Version dropdown, and select the **Update** button.</span></span> <span data-ttu-id="ad2ae-139">在 [預覽變更]  對話方塊上，選取 [確定]  按鈕，然後在 [授權接受]  對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]  。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-139">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="add-pre-trained-model-to-project"></a><span data-ttu-id="ad2ae-140">將預先定型的模型新增到專案</span><span class="sxs-lookup"><span data-stu-id="ad2ae-140">Add pre-trained model to project</span></span>

1. <span data-ttu-id="ad2ae-141">將預先建置的模型複製到 *MLModels* 目錄。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-141">Copy your pre-built model to the *MLModels* folder.</span></span>
1. <span data-ttu-id="ad2ae-142">在 [方案總管] 中，以滑鼠右鍵按一下您預先建置的模型檔案，並選取 [內容]  。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-142">In Solution Explorer, right-click your pre-built model file and select **Properties**.</span></span> <span data-ttu-id="ad2ae-143">在 [進階]  底下，將 [複製到輸出目錄]  的值變更為 [有更新時才複製]  。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-143">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

## <a name="create-azure-function-to-analyze-sentiment"></a><span data-ttu-id="ad2ae-144">建立 Azure Function 來分析情感</span><span class="sxs-lookup"><span data-stu-id="ad2ae-144">Create Azure Function to analyze sentiment</span></span>

<span data-ttu-id="ad2ae-145">建立用來預測情緒的類別。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-145">Create a class to predict sentiment.</span></span> <span data-ttu-id="ad2ae-146">將新類別新增至專案：</span><span class="sxs-lookup"><span data-stu-id="ad2ae-146">Add a new class to your project:</span></span>

1. <span data-ttu-id="ad2ae-147">在 [方案總管]  中，於專案上按一下滑鼠右鍵，然後選取 [新增]   > [新增項目]  。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-147">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="ad2ae-148">在 [新增項目]  對話方塊中，選取 [Azure Function]  ，然後將 [名稱]  欄位變更為 *AnalyzeSentiment.cs*。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-148">In the **Add New Item** dialog box, select **Azure Function** and change the **Name** field to *AnalyzeSentiment.cs*.</span></span> <span data-ttu-id="ad2ae-149">接著，選取 [新增]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-149">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="ad2ae-150">在 [新增 Azure 函式]  對話方塊中，選取 [Http 觸發程序]  。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-150">In the **New Azure Function** dialog box, select **Http Trigger**.</span></span> <span data-ttu-id="ad2ae-151">然後，選取 [確定]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-151">Then, select the **OK** button.</span></span>

    <span data-ttu-id="ad2ae-152">*AnalyzeSentiment.cs* 檔案隨即在程式碼編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-152">The *AnalyzeSentiment.cs* file opens in the code editor.</span></span> <span data-ttu-id="ad2ae-153">將下列 `using` 陳述式新增到 *AnalyzeSentiment.cs* 的頂端：</span><span class="sxs-lookup"><span data-stu-id="ad2ae-153">Add the following `using` statement to the top of *AnalyzeSentiment.cs*:</span></span>

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

    <span data-ttu-id="ad2ae-154">根據預設，`AnalyzeSentiment` 類別為 `static`。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-154">By default, the `AnalyzeSentiment` class is `static`.</span></span> <span data-ttu-id="ad2ae-155">請務必從類別定義移除 `static` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-155">Make sure to remove the `static` keyword from the class definition.</span></span>

    ```csharp
    public class AnalyzeSentiment
    {
    
    }
    ```

## <a name="create-data-models"></a><span data-ttu-id="ad2ae-156">建立資料模型</span><span class="sxs-lookup"><span data-stu-id="ad2ae-156">Create data models</span></span>

<span data-ttu-id="ad2ae-157">您必須為輸入資料和預測建立一些類別。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-157">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="ad2ae-158">將新類別新增至專案：</span><span class="sxs-lookup"><span data-stu-id="ad2ae-158">Add a new class to your project:</span></span>

1. <span data-ttu-id="ad2ae-159">在您的專案中建立名為 *DataModels* 的目錄以儲存資料模型：在 [方案總管] 中，以滑鼠右鍵按一下您的專案，然後選取 [新增] > [新增資料夾]  。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-159">Create a directory named *DataModels* in your project to save your data models: In Solution Explorer, right-click on your project and select **Add > New Folder**.</span></span> <span data-ttu-id="ad2ae-160">輸入 "DataModels"，然後按 Enter。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-160">Type "DataModels" and hit Enter.</span></span>
2. <span data-ttu-id="ad2ae-161">在 [方案總管] 中，以滑鼠右鍵按一下 *DataModels* 目錄，然後選取 [新增] > [新增項目]  。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-161">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
3. <span data-ttu-id="ad2ae-162">在 [新增項目]  對話方塊中，選取 [類別]  ，然後將 [名稱]  欄位變更為 *SentimentData.cs*。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-162">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="ad2ae-163">接著，選取 [新增]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-163">Then, select the **Add** button.</span></span> 

    <span data-ttu-id="ad2ae-164">*SentimentData.cs* 檔案隨即在程式碼編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-164">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="ad2ae-165">將下列 using 陳述式新增至 *SentimentData.cs* 頂端：</span><span class="sxs-lookup"><span data-stu-id="ad2ae-165">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="ad2ae-166">移除現有的類別定義，然後將下列程式碼新增至 *SentimentData.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="ad2ae-166">Remove the existing class definition and add the following code to the *SentimentData.cs* file:</span></span>
    
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

4. <span data-ttu-id="ad2ae-167">在 [方案總管] 中，以滑鼠右鍵按一下 *DataModels* 目錄，然後選取 [新增] > [新增項目]  。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-167">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="ad2ae-168">在 [加入新項目]  對話方塊中，選取 [類別]  ，然後將 [名稱]  欄位變更為 *SentimentPrediction.cs*。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-168">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="ad2ae-169">接著，選取 [新增]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-169">Then, select the **Add** button.</span></span> <span data-ttu-id="ad2ae-170">*SentimentPrediction.cs* 檔案隨即在程式碼編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-170">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="ad2ae-171">將下列 using 陳述式新增至 *SentimentPrediction.cs* 頂端：</span><span class="sxs-lookup"><span data-stu-id="ad2ae-171">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="ad2ae-172">移除現有的類別定義，然後將下列程式碼新增至 *SentimentPrediction.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="ad2ae-172">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    <span data-ttu-id="ad2ae-173">`SentimentPrediction` 會從 `SentimentData` 繼承，後者會在 `SentimentText` 屬性中提供原始資料的存取，以及由模型產生的輸出。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-173">`SentimentPrediction` inherits from `SentimentData` which provides access to the original data in the `SentimentText` property as well as the output generated by the model.</span></span>

## <a name="register-predictionenginepool-service"></a><span data-ttu-id="ad2ae-174">登錄 PredictionEnginePool 服務</span><span class="sxs-lookup"><span data-stu-id="ad2ae-174">Register PredictionEnginePool service</span></span>

<span data-ttu-id="ad2ae-175">若要進行單一預測，請使用 [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-175">To make a single prediction, use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="ad2ae-176">為了在您的應用程式中使用 [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)，您必須在需要的時候建立它。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-176">In order to use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) in your application you must create it when it's needed.</span></span> <span data-ttu-id="ad2ae-177">在此情況下，要考慮的最佳做法是相依性插入。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-177">In that case, a best practice to consider is dependency injection.</span></span>

<span data-ttu-id="ad2ae-178">如果您想要深入了解[相依性插入](https://en.wikipedia.org/wiki/Dependency_injection)，下列連結提供詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-178">The following link provides more information if you want to learn about [dependency injection](https://en.wikipedia.org/wiki/Dependency_injection).</span></span>

1. <span data-ttu-id="ad2ae-179">在 [方案總管]  中，於專案上按一下滑鼠右鍵，然後選取 [新增]   > [新增項目]  。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-179">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="ad2ae-180">在 [新增項目]  對話方塊中，選取 [類別]  ，然後將 [名稱]  欄位變更為 *Startup.cs*。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-180">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *Startup.cs*.</span></span> <span data-ttu-id="ad2ae-181">接著，選取 [新增]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-181">Then, select the **Add** button.</span></span> 

    <span data-ttu-id="ad2ae-182">*Startup.cs* 檔案隨即在程式碼編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-182">The *Startup.cs* file opens in the code editor.</span></span> <span data-ttu-id="ad2ae-183">將下列的 using 陳述式新增到 *Startup.cs* 的頂端：</span><span class="sxs-lookup"><span data-stu-id="ad2ae-183">Add the following using statement to the top of *Startup.cs*:</span></span>

    ```csharp
    using Microsoft.Azure.WebJobs;
    using Microsoft.Azure.WebJobs.Hosting;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisFunctionsApp;
    using SentimentAnalysisFunctionsApp.DataModels;
    ```

    <span data-ttu-id="ad2ae-184">移除 using 陳述式下方的現有程式碼，並將下列程式碼新增到 *Startup.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="ad2ae-184">Remove the existing code below the using statements and add the following code to the *Startup.cs* file:</span></span>

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

<span data-ttu-id="ad2ae-185">概括而言，此程式碼會在應用程式要求時自動初始化物件和服務，不必手動執行。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-185">At a high level, this code initializes the objects and services automatically when requested by the application instead of having to manually do it.</span></span>

> [!WARNING]
> <span data-ttu-id="ad2ae-186">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) 不是安全執行緒。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-186">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="ad2ae-187">為了改善效能及執行緒安全性，請使用 `PredictionEnginePool` 服務，該服務會建立 `PredictionEngine` 物件的 [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) 以供應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-187">For improved performance and thread safety, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of `PredictionEngine` objects for application use.</span></span> 

## <a name="load-the-model-into-the-function"></a><span data-ttu-id="ad2ae-188">將模型載入函式</span><span class="sxs-lookup"><span data-stu-id="ad2ae-188">Load the model into the function</span></span>

<span data-ttu-id="ad2ae-189">將下列程式碼插入 *AnalyzeSentiment* 類別：</span><span class="sxs-lookup"><span data-stu-id="ad2ae-189">Insert the following code inside the *AnalyzeSentiment* class:</span></span>

```csharp
private readonly PredictionEnginePool<SentimentData, SentimentPrediction> _predictionEnginePool;

// AnalyzeSentiment class constructor
public AnalyzeSentiment(PredictionEnginePool<SentimentData, SentimentPrediction> predictionEnginePool)
{
    _predictionEnginePool = predictionEnginePool;
}
```

<span data-ttu-id="ad2ae-190">此程式碼會透過將 `PredictionEnginePool` 傳遞到您透過相依性插入所取得的函式建構函式來指派它。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-190">This code assigns the `PredictionEnginePool` by passing it to the function's constructor which you get via dependency injection.</span></span>

## <a name="use-the-model-to-make-predictions"></a><span data-ttu-id="ad2ae-191">使用模型進行預測</span><span class="sxs-lookup"><span data-stu-id="ad2ae-191">Use the model to make predictions</span></span>

<span data-ttu-id="ad2ae-192">使用下列程式碼取代 *AnalyzeSentiment* 類別中 *Run* 方法的現有實作：</span><span class="sxs-lookup"><span data-stu-id="ad2ae-192">Replace the existing implementation of *Run* method in *AnalyzeSentiment* class with the following code:</span></span>

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

<span data-ttu-id="ad2ae-193">`Run` 方法執行時，來自 HTTP 請求的傳入資料會還原序列化，並用來作為 `PredictionEnginePool` 的輸入。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-193">When the `Run` method executes, the incoming data from the HTTP request is deserialized and used as input for the `PredictionEnginePool`.</span></span> <span data-ttu-id="ad2ae-194">接著會呼叫 `Predict` 方法來產生預測，並將結果傳回使用者。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-194">The `Predict` method is then called to generate a prediction and return the result to the user.</span></span> 

## <a name="test-locally"></a><span data-ttu-id="ad2ae-195">在本機進行測試</span><span class="sxs-lookup"><span data-stu-id="ad2ae-195">Test locally</span></span>

<span data-ttu-id="ad2ae-196">一切都設定好後，就可以開始測試應用程式：</span><span class="sxs-lookup"><span data-stu-id="ad2ae-196">Now that everything is set up, it's time to test the application:</span></span>

1. <span data-ttu-id="ad2ae-197">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="ad2ae-197">Run the application</span></span>
1. <span data-ttu-id="ad2ae-198">開啟 Powershell 並在提示字元中輸入下列程式碼，其中 PORT 是正在執行您應用程式的連接埠。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-198">Open PowerShell and enter the code into the prompt where PORT is the port your application is running on.</span></span> <span data-ttu-id="ad2ae-199">一般來說，連接埠是 7071。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-199">Typically the port is 7071.</span></span>

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="ad2ae-200">如果成功，輸出看起來應該類似下列文字：</span><span class="sxs-lookup"><span data-stu-id="ad2ae-200">If successful, the output should look similar to the text below:</span></span>
    
    ```powershell
    Negative
    ```

<span data-ttu-id="ad2ae-201">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="ad2ae-201">Congratulations!</span></span> <span data-ttu-id="ad2ae-202">您已成功提供您的模型，以使用 Azure Function 在網際網路上進行預測。</span><span class="sxs-lookup"><span data-stu-id="ad2ae-202">You have successfully served your model to make predictions over the internet using an Azure Function.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ad2ae-203">後續步驟</span><span class="sxs-lookup"><span data-stu-id="ad2ae-203">Next Steps</span></span>

- [<span data-ttu-id="ad2ae-204">部署到 Azure</span><span class="sxs-lookup"><span data-stu-id="ad2ae-204">Deploy to Azure</span></span>](/azure/azure-functions/functions-develop-vs#publish-to-azure)
