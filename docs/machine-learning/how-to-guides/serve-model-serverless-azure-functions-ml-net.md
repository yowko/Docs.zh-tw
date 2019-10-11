---
title: 將模型部署到 Azure Functions
description: 使用 Azure Functions 在網際網路上提供 ML.NET 情感分析機器學習模型以進行預測
ms.date: 09/12/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 2abd8588aa314b630c995e0c78b5869ec00a89df
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179367"
---
# <a name="deploy-a-model-to-azure-functions"></a><span data-ttu-id="928af-103">將模型部署到 Azure Functions</span><span class="sxs-lookup"><span data-stu-id="928af-103">Deploy a model to Azure Functions</span></span>

<span data-ttu-id="928af-104">了解如何部署預先定型的 ML.NET 機器學習模型，以使用 Azure Functions 無伺服器環境透過 HTTP 進行預測。</span><span class="sxs-lookup"><span data-stu-id="928af-104">Learn how to deploy a pre-trained ML.NET machine learning model for predictions over HTTP through an Azure Functions serverless environment.</span></span>

> [!NOTE]
> <span data-ttu-id="928af-105">`PredictionEnginePool` 服務延伸模組目前處於預覽狀態。</span><span class="sxs-lookup"><span data-stu-id="928af-105">`PredictionEnginePool` service extension is currently in preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="928af-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="928af-106">Prerequisites</span></span>

- <span data-ttu-id="928af-107">已安裝「.NET Core 跨平台開發」工作負載和「Azure 開發」的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)。</span><span class="sxs-lookup"><span data-stu-id="928af-107">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload and "Azure development" installed.</span></span>
- <span data-ttu-id="928af-108">Microsoft.NET.Sdk.Functions NuGet 套件版本 1.0.28+。</span><span class="sxs-lookup"><span data-stu-id="928af-108">Microsoft.NET.Sdk.Functions NuGet Package version 1.0.28+.</span></span>
- [<span data-ttu-id="928af-109">Azure Functions Tools</span><span class="sxs-lookup"><span data-stu-id="928af-109">Azure Functions Tools</span></span>](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- <span data-ttu-id="928af-110">Powershell</span><span class="sxs-lookup"><span data-stu-id="928af-110">Powershell</span></span>
- <span data-ttu-id="928af-111">預先定型的模型。</span><span class="sxs-lookup"><span data-stu-id="928af-111">Pre-trained model.</span></span> <span data-ttu-id="928af-112">使用 [ML.NET 情感分析教學課程](../tutorials/sentiment-analysis.md)來建置您自己的模型，或是下載這個[預先定型的情感分析機器學習模型](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="928af-112">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-azure-functions-project"></a><span data-ttu-id="928af-113">建立 Azure Functions 專案</span><span class="sxs-lookup"><span data-stu-id="928af-113">Create Azure Functions project</span></span>

1. <span data-ttu-id="928af-114">開啟 Visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="928af-114">Open Visual Studio 2017.</span></span> <span data-ttu-id="928af-115">從功能表列中選取 [檔案]  >  [新增]  >  [專案]。</span><span class="sxs-lookup"><span data-stu-id="928af-115">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="928af-116">在 [新增專案] 對話方塊中，選取 [Visual C#] 節點，然後選取 [雲端] 節點。</span><span class="sxs-lookup"><span data-stu-id="928af-116">In the **New Project** dialog, select the **Visual C#** node followed by the **Cloud** node.</span></span> <span data-ttu-id="928af-117">然後選取 [Azure Functions] 專案範本。</span><span class="sxs-lookup"><span data-stu-id="928af-117">Then select the **Azure Functions** project template.</span></span> <span data-ttu-id="928af-118">在 [名稱] 文字方塊中，輸入 "SentimentAnalysisFunctionsApp"，然後選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="928af-118">In the **Name** text box, type "SentimentAnalysisFunctionsApp" and then select the **OK** button.</span></span>
1. <span data-ttu-id="928af-119">在 [新增專案] 對話方塊中，開啟專案選項上方的下拉式清單，然後選取 [Azure Functions v2 (.NET Core)]。</span><span class="sxs-lookup"><span data-stu-id="928af-119">In the **New Project** dialog, open the dropdown above the project options and select **Azure Functions v2 (.NET Core)**.</span></span> <span data-ttu-id="928af-120">然後，選取 [Http 觸發程序] 專案，然後選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="928af-120">Then, select the **Http trigger** project and then select the **OK** button.</span></span>
1. <span data-ttu-id="928af-121">在您的專案中建立名為 *MLModels* 的目錄，以儲存您的模型：</span><span class="sxs-lookup"><span data-stu-id="928af-121">Create a directory named *MLModels* in your project to save your model:</span></span>

    <span data-ttu-id="928af-122">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [新增] > [新增資料夾]。</span><span class="sxs-lookup"><span data-stu-id="928af-122">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="928af-123">輸入 "MLModels"，然後按 Enter。</span><span class="sxs-lookup"><span data-stu-id="928af-123">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="928af-124">安裝「Microsoft.ML NuGet 套件」：</span><span class="sxs-lookup"><span data-stu-id="928af-124">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="928af-125">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="928af-125">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="928af-126">選擇 "nuget.org" 作為 [套件來源]，選取 [瀏覽] 索引標籤、搜尋 **Microsoft.ML**、從清單中選取該套件，然後選取 [安裝] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="928af-126">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="928af-127">在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。</span><span class="sxs-lookup"><span data-stu-id="928af-127">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="928af-128">安裝 **Microsoft.Azure.Functions.Extensions NuGet 套件**：</span><span class="sxs-lookup"><span data-stu-id="928af-128">Install the **Microsoft.Azure.Functions.Extensions NuGet Package**:</span></span>

    <span data-ttu-id="928af-129">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="928af-129">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="928af-130">選擇 "nuget.org" 作為 [套件來源]、選取 [瀏覽] 索引標籤、搜尋 **Microsoft.Azure.Functions.Extensions**、從清單中選取該套件，然後選取 [安裝] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="928af-130">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Azure.Functions.Extensions**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="928af-131">在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。</span><span class="sxs-lookup"><span data-stu-id="928af-131">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="928af-132">安裝 **Microsoft.Extensions.ML NuGet 套件**：</span><span class="sxs-lookup"><span data-stu-id="928af-132">Install the **Microsoft.Extensions.ML NuGet Package**:</span></span>

    <span data-ttu-id="928af-133">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="928af-133">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="928af-134">選擇 "nuget.org" 作為 [套件來源]、選取 [瀏覽] 索引標籤、搜尋 **Microsoft.Extensions.ML**、從清單中選取該套件，然後選取 [安裝] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="928af-134">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="928af-135">在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。</span><span class="sxs-lookup"><span data-stu-id="928af-135">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="928af-136">將 **Microsoft.NET.Sdk.Functions NuGet 套件**更新至 1.0.28 (含) 以後版本：</span><span class="sxs-lookup"><span data-stu-id="928af-136">Update the **Microsoft.NET.Sdk.Functions NuGet Package** to version 1.0.28+:</span></span>

    <span data-ttu-id="928af-137">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="928af-137">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="928af-138">選擇 "nuget.org" 作為套件來源、選取 [安裝] 索引標籤、搜尋 **Microsoft.NET.Sdk.Functions**、從 [版本] 下拉式清單選取 1.0.28 或更新版本，然後選取 [更新] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="928af-138">Choose "nuget.org" as the Package source, select the Installed tab, search for **Microsoft.NET.Sdk.Functions**, select that package in the list, select 1.0.28 or later from the Version dropdown, and select the **Update** button.</span></span> <span data-ttu-id="928af-139">在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。</span><span class="sxs-lookup"><span data-stu-id="928af-139">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="add-pre-trained-model-to-project"></a><span data-ttu-id="928af-140">將預先定型的模型新增到專案</span><span class="sxs-lookup"><span data-stu-id="928af-140">Add pre-trained model to project</span></span>

1. <span data-ttu-id="928af-141">將預先建置的模型複製到 *MLModels* 目錄。</span><span class="sxs-lookup"><span data-stu-id="928af-141">Copy your pre-built model to the *MLModels* folder.</span></span>
1. <span data-ttu-id="928af-142">在 [方案總管] 中，以滑鼠右鍵按一下您預先建置的模型檔案，並選取 [內容]。</span><span class="sxs-lookup"><span data-stu-id="928af-142">In Solution Explorer, right-click your pre-built model file and select **Properties**.</span></span> <span data-ttu-id="928af-143">在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。</span><span class="sxs-lookup"><span data-stu-id="928af-143">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

## <a name="create-azure-function-to-analyze-sentiment"></a><span data-ttu-id="928af-144">建立 Azure Function 來分析情感</span><span class="sxs-lookup"><span data-stu-id="928af-144">Create Azure Function to analyze sentiment</span></span>

<span data-ttu-id="928af-145">建立用來預測情緒的類別。</span><span class="sxs-lookup"><span data-stu-id="928af-145">Create a class to predict sentiment.</span></span> <span data-ttu-id="928af-146">將新類別新增至專案：</span><span class="sxs-lookup"><span data-stu-id="928af-146">Add a new class to your project:</span></span>

1. <span data-ttu-id="928af-147">在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="928af-147">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="928af-148">在 [新增項目] 對話方塊中，選取 [Azure Function]，然後將 [名稱] 欄位變更為 *AnalyzeSentiment.cs*。</span><span class="sxs-lookup"><span data-stu-id="928af-148">In the **Add New Item** dialog box, select **Azure Function** and change the **Name** field to *AnalyzeSentiment.cs*.</span></span> <span data-ttu-id="928af-149">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="928af-149">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="928af-150">在 [新增 Azure 函式] 對話方塊中，選取 [Http 觸發程序]。</span><span class="sxs-lookup"><span data-stu-id="928af-150">In the **New Azure Function** dialog box, select **Http Trigger**.</span></span> <span data-ttu-id="928af-151">然後，選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="928af-151">Then, select the **OK** button.</span></span>

    <span data-ttu-id="928af-152">*AnalyzeSentiment.cs* 檔案隨即在程式碼編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="928af-152">The *AnalyzeSentiment.cs* file opens in the code editor.</span></span> <span data-ttu-id="928af-153">將下列 `using` 陳述式新增到 *AnalyzeSentiment.cs* 的頂端：</span><span class="sxs-lookup"><span data-stu-id="928af-153">Add the following `using` statement to the top of *AnalyzeSentiment.cs*:</span></span>

    [!code-csharp [AnalyzeUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L1-L11)]

    <span data-ttu-id="928af-154">根據預設，`AnalyzeSentiment` 類別為 `static`。</span><span class="sxs-lookup"><span data-stu-id="928af-154">By default, the `AnalyzeSentiment` class is `static`.</span></span> <span data-ttu-id="928af-155">請務必從類別定義移除 `static` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="928af-155">Make sure to remove the `static` keyword from the class definition.</span></span>

    ```csharp
    public class AnalyzeSentiment
    {
    
    }
    ```

## <a name="create-data-models"></a><span data-ttu-id="928af-156">建立資料模型</span><span class="sxs-lookup"><span data-stu-id="928af-156">Create data models</span></span>

<span data-ttu-id="928af-157">您必須為輸入資料和預測建立一些類別。</span><span class="sxs-lookup"><span data-stu-id="928af-157">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="928af-158">將新類別新增至專案：</span><span class="sxs-lookup"><span data-stu-id="928af-158">Add a new class to your project:</span></span>

1. <span data-ttu-id="928af-159">在您的專案中建立名為 *DataModels* 的目錄以儲存資料模型：在 [方案總管] 中，以滑鼠右鍵按一下您的專案，然後選取 [新增] > [新增資料夾]。</span><span class="sxs-lookup"><span data-stu-id="928af-159">Create a directory named *DataModels* in your project to save your data models: In Solution Explorer, right-click on your project and select **Add > New Folder**.</span></span> <span data-ttu-id="928af-160">輸入 "DataModels"，然後按 Enter。</span><span class="sxs-lookup"><span data-stu-id="928af-160">Type "DataModels" and hit Enter.</span></span>
2. <span data-ttu-id="928af-161">在 [方案總管] 中，以滑鼠右鍵按一下 *DataModels* 目錄，然後選取 [新增] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="928af-161">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
3. <span data-ttu-id="928af-162">在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *SentimentData.cs*。</span><span class="sxs-lookup"><span data-stu-id="928af-162">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="928af-163">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="928af-163">Then, select the **Add** button.</span></span> 

    <span data-ttu-id="928af-164">*SentimentData.cs* 檔案隨即在程式碼編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="928af-164">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="928af-165">將下列 using 陳述式新增至 *SentimentData.cs* 頂端：</span><span class="sxs-lookup"><span data-stu-id="928af-165">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp [SentimentDataUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L1)]

    <span data-ttu-id="928af-166">移除現有的類別定義，然後將下列程式碼新增至 *SentimentData.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="928af-166">Remove the existing class definition and add the following code to the *SentimentData.cs* file:</span></span>

    [!code-csharp [SentimentData](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L5-L13)]

4. <span data-ttu-id="928af-167">在 [方案總管] 中，以滑鼠右鍵按一下 *DataModels* 目錄，然後選取 [新增] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="928af-167">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="928af-168">在 [加入新項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *SentimentPrediction.cs*。</span><span class="sxs-lookup"><span data-stu-id="928af-168">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="928af-169">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="928af-169">Then, select the **Add** button.</span></span> <span data-ttu-id="928af-170">*SentimentPrediction.cs* 檔案隨即在程式碼編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="928af-170">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="928af-171">將下列 using 陳述式新增至 *SentimentPrediction.cs* 頂端：</span><span class="sxs-lookup"><span data-stu-id="928af-171">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    [!code-csharp [SentimentPredictionUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L1)]

    <span data-ttu-id="928af-172">移除現有的類別定義，然後將下列程式碼新增至 *SentimentPrediction.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="928af-172">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

    [!code-csharp [SentimentPrediction](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L5-L14)]

    <span data-ttu-id="928af-173">`SentimentPrediction` 會從 `SentimentData` 繼承，後者會在 `SentimentText` 屬性中提供原始資料的存取，以及由模型產生的輸出。</span><span class="sxs-lookup"><span data-stu-id="928af-173">`SentimentPrediction` inherits from `SentimentData` which provides access to the original data in the `SentimentText` property as well as the output generated by the model.</span></span>

## <a name="register-predictionenginepool-service"></a><span data-ttu-id="928af-174">登錄 PredictionEnginePool 服務</span><span class="sxs-lookup"><span data-stu-id="928af-174">Register PredictionEnginePool service</span></span>

<span data-ttu-id="928af-175">若要進行單一預測，您必須建立[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)。</span><span class="sxs-lookup"><span data-stu-id="928af-175">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="928af-176">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) 不是安全執行緒。</span><span class="sxs-lookup"><span data-stu-id="928af-176">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="928af-177">此外，您必須在應用程式內需要的任何地方建立它的實例。</span><span class="sxs-lookup"><span data-stu-id="928af-177">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="928af-178">當您的應用程式成長時，此進程可能會變得難以管理。</span><span class="sxs-lookup"><span data-stu-id="928af-178">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="928af-179">為了改善效能和執行緒安全性，請使用相依性插入和 `PredictionEnginePool` 服務的組合，這會建立[@no__t 4](xref:Microsoft.ML.PredictionEngine%602)物件的[@no__t 2](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) ，以便在整個應用程式中使用。</span><span class="sxs-lookup"><span data-stu-id="928af-179">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

<span data-ttu-id="928af-180">如果您想要深入瞭解相依性[插入](https://en.wikipedia.org/wiki/Dependency_injection)，下列連結提供詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="928af-180">The following link provides more information if you want to learn more about [dependency injection](https://en.wikipedia.org/wiki/Dependency_injection).</span></span>

1. <span data-ttu-id="928af-181">在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="928af-181">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="928af-182">在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *Startup.cs*。</span><span class="sxs-lookup"><span data-stu-id="928af-182">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *Startup.cs*.</span></span> <span data-ttu-id="928af-183">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="928af-183">Then, select the **Add** button.</span></span> 

    <span data-ttu-id="928af-184">*Startup.cs* 檔案隨即在程式碼編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="928af-184">The *Startup.cs* file opens in the code editor.</span></span> <span data-ttu-id="928af-185">將下列的 using 陳述式新增到 *Startup.cs* 的頂端：</span><span class="sxs-lookup"><span data-stu-id="928af-185">Add the following using statement to the top of *Startup.cs*:</span></span>

    ```csharp
    using Microsoft.Azure.Functions.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisFunctionsApp;
    using SentimentAnalysisFunctionsApp.DataModels;
    ```

    <span data-ttu-id="928af-186">移除 using 陳述式下方的現有程式碼，並將下列程式碼新增到 *Startup.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="928af-186">Remove the existing code below the using statements and add the following code to the *Startup.cs* file:</span></span>

    ```csharp
    [assembly: FunctionsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        public class Startup : FunctionsStartup
        {
            public override void Configure(IFunctionsHostBuilder builder)
            {
                builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
                    .FromFile(modelName: "SentimentAnalysisModel", filePath:"MLModels/sentiment_model.zip", watchForChanges: true);
            }
        }
    }
    ```

<span data-ttu-id="928af-187">概括而言，此程式碼會自動初始化物件和服務，以供稍後在應用程式要求時使用，而不需要手動執行。</span><span class="sxs-lookup"><span data-stu-id="928af-187">At a high level, this code initializes the objects and services automatically for later use when requested by the application instead of having to manually do it.</span></span> 

<span data-ttu-id="928af-188">機器學習模型不是靜態的。</span><span class="sxs-lookup"><span data-stu-id="928af-188">Machine learning models are not static.</span></span> <span data-ttu-id="928af-189">當有新的定型資料可供使用時，就會重新訓練並重新部署模型。</span><span class="sxs-lookup"><span data-stu-id="928af-189">As new training data becomes available, the model is retrained and redeployed.</span></span> <span data-ttu-id="928af-190">將模型的最新版本取得至應用程式的方法之一，就是重新部署整個應用程式。</span><span class="sxs-lookup"><span data-stu-id="928af-190">One way to get the latest version of the model into your application is to redeploy the entire application.</span></span> <span data-ttu-id="928af-191">不過，這會引進應用程式停機時間。</span><span class="sxs-lookup"><span data-stu-id="928af-191">However, this introduces application downtime.</span></span> <span data-ttu-id="928af-192">@No__t-0 服務提供一種機制，可重載已更新的模型，而不需要讓應用程式關閉。</span><span class="sxs-lookup"><span data-stu-id="928af-192">The `PredictionEnginePool` service provides a mechanism to reload an updated model without taking your application down.</span></span> 

<span data-ttu-id="928af-193">將 `watchForChanges` 參數設定為 `true`，而 `PredictionEnginePool` 啟動一個[`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) ，接聽檔案系統變更通知，並在檔案變更時引發事件。</span><span class="sxs-lookup"><span data-stu-id="928af-193">Set the `watchForChanges` parameter to `true`, and the `PredictionEnginePool` starts a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) that listens to the file system change notifications and raises events when there is a change to the file.</span></span> <span data-ttu-id="928af-194">這會提示 `PredictionEnginePool` 會自動重載模型。</span><span class="sxs-lookup"><span data-stu-id="928af-194">This prompts the `PredictionEnginePool` to automatically reload the model.</span></span>

<span data-ttu-id="928af-195">此模型是由 `modelName` 參數所識別，因此，每個應用程式可以在變更時重載一個以上的模型。</span><span class="sxs-lookup"><span data-stu-id="928af-195">The model is identified by the `modelName` parameter so that more than one model per application can be reloaded upon change.</span></span> 

> [!TIP]
> <span data-ttu-id="928af-196">或者，當您使用遠端儲存的模型時，可以使用 `FromUri` 方法。</span><span class="sxs-lookup"><span data-stu-id="928af-196">Alternatively, you can use the `FromUri` method when working with models stored remotely.</span></span> <span data-ttu-id="928af-197">@No__t-0 會輪詢遠端位置以進行變更，而不是監看檔案已變更的事件。</span><span class="sxs-lookup"><span data-stu-id="928af-197">Rather than watching for file changed events, `FromUri` polls the remote location for changes.</span></span> <span data-ttu-id="928af-198">輪詢間隔預設為5分鐘。</span><span class="sxs-lookup"><span data-stu-id="928af-198">The polling interval defaults to 5 minutes.</span></span> <span data-ttu-id="928af-199">您可以根據應用程式的需求來增加或減少輪詢間隔。</span><span class="sxs-lookup"><span data-stu-id="928af-199">You can increase or decrease the polling interval based on your application's requirements.</span></span> <span data-ttu-id="928af-200">在下面的程式碼範例中，`PredictionEnginePool` 會每分鐘輪詢儲存在指定 URI 的模型。</span><span class="sxs-lookup"><span data-stu-id="928af-200">In the code sample below, the `PredictionEnginePool` polls the model stored at the specified URI every minute.</span></span>
>    
>```csharp
>builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel", 
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip", 
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="load-the-model-into-the-function"></a><span data-ttu-id="928af-201">將模型載入函式</span><span class="sxs-lookup"><span data-stu-id="928af-201">Load the model into the function</span></span>

<span data-ttu-id="928af-202">將下列程式碼插入 *AnalyzeSentiment* 類別：</span><span class="sxs-lookup"><span data-stu-id="928af-202">Insert the following code inside the *AnalyzeSentiment* class:</span></span>

[!code-csharp [AnalyzeCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L18-L24)]

<span data-ttu-id="928af-203">此程式碼會透過將 `PredictionEnginePool` 傳遞到您透過相依性插入所取得的函式建構函式來指派它。</span><span class="sxs-lookup"><span data-stu-id="928af-203">This code assigns the `PredictionEnginePool` by passing it to the function's constructor which you get via dependency injection.</span></span>

## <a name="use-the-model-to-make-predictions"></a><span data-ttu-id="928af-204">使用模型進行預測</span><span class="sxs-lookup"><span data-stu-id="928af-204">Use the model to make predictions</span></span>

<span data-ttu-id="928af-205">使用下列程式碼取代 *AnalyzeSentiment* 類別中 *Run* 方法的現有實作：</span><span class="sxs-lookup"><span data-stu-id="928af-205">Replace the existing implementation of *Run* method in *AnalyzeSentiment* class with the following code:</span></span>

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
    SentimentPrediction prediction = _predictionEnginePool.Predict(modelName: "SentimentAnalysisModel", example: data);

    //Convert prediction to string
    string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

    //Return Prediction
    return (ActionResult)new OkObjectResult(sentiment);
}
```

<span data-ttu-id="928af-206">`Run` 方法執行時，來自 HTTP 請求的傳入資料會還原序列化，並用來作為 `PredictionEnginePool` 的輸入。</span><span class="sxs-lookup"><span data-stu-id="928af-206">When the `Run` method executes, the incoming data from the HTTP request is deserialized and used as input for the `PredictionEnginePool`.</span></span> <span data-ttu-id="928af-207">然後會呼叫 `Predict` 方法，以使用在 `Startup` 類別中註冊的 `SentimentAnalysisModel` 進行預測，並在成功時將結果傳回給使用者。</span><span class="sxs-lookup"><span data-stu-id="928af-207">The `Predict` method is then called to to make predictions using the `SentimentAnalysisModel` registered in the `Startup` class and returns the results back to the user if successful.</span></span>

## <a name="test-locally"></a><span data-ttu-id="928af-208">在本機進行測試</span><span class="sxs-lookup"><span data-stu-id="928af-208">Test locally</span></span>

<span data-ttu-id="928af-209">一切都設定好後，就可以開始測試應用程式：</span><span class="sxs-lookup"><span data-stu-id="928af-209">Now that everything is set up, it's time to test the application:</span></span>

1. <span data-ttu-id="928af-210">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="928af-210">Run the application</span></span>
1. <span data-ttu-id="928af-211">開啟 Powershell 並在提示字元中輸入下列程式碼，其中 PORT 是正在執行您應用程式的連接埠。</span><span class="sxs-lookup"><span data-stu-id="928af-211">Open PowerShell and enter the code into the prompt where PORT is the port your application is running on.</span></span> <span data-ttu-id="928af-212">一般來說，連接埠是 7071。</span><span class="sxs-lookup"><span data-stu-id="928af-212">Typically the port is 7071.</span></span>

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="928af-213">如果成功，輸出看起來應該類似下列文字：</span><span class="sxs-lookup"><span data-stu-id="928af-213">If successful, the output should look similar to the text below:</span></span>
    
    ```powershell
    Negative
    ```

<span data-ttu-id="928af-214">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="928af-214">Congratulations!</span></span> <span data-ttu-id="928af-215">您已成功提供您的模型，以使用 Azure Function 在網際網路上進行預測。</span><span class="sxs-lookup"><span data-stu-id="928af-215">You have successfully served your model to make predictions over the internet using an Azure Function.</span></span>

## <a name="next-steps"></a><span data-ttu-id="928af-216">後續步驟</span><span class="sxs-lookup"><span data-stu-id="928af-216">Next Steps</span></span>

- [<span data-ttu-id="928af-217">部署到 Azure</span><span class="sxs-lookup"><span data-stu-id="928af-217">Deploy to Azure</span></span>](/azure/azure-functions/functions-develop-vs#publish-to-azure)
