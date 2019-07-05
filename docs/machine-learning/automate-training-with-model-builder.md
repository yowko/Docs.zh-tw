---
title: 什麼是模型建立器且其如何運作？
description: 如何使用 ML.NET 模型建立器來自動定型機器學習服務模型
author: natke
ms.date: 06/26/2019
ms.custom: overview
ms.openlocfilehash: 6f5bbe3c389e3ca42550a48ef3e6edbc963ac2e9
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410586"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a><span data-ttu-id="e0427-103">什麼是模型建立器且其如何運作？</span><span class="sxs-lookup"><span data-stu-id="e0427-103">What is Model Builder and how does it work?</span></span>

<span data-ttu-id="e0427-104">ML.NET 模型建立器是易於了解的圖形化 Visual Studio 延伸模組，其用於建置、定型和部署自訂機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="e0427-104">ML.NET Model Builder is an easy-to-understand graphical Visual Studio extension to build, train, and deploy custom machine learning models.</span></span> 

<span data-ttu-id="e0427-105">模型建立器會使用自動化的機器學習服務 (AutoML) 來探索不同機器學習服務演算法和設定，協助您找出最適合您案例的組合。</span><span class="sxs-lookup"><span data-stu-id="e0427-105">Model Builder uses automated machine learning (AutoML) to explore different machine learning algorithms and settings to help you find the one that best suits your scenario.</span></span>

<span data-ttu-id="e0427-106">您不需要有機器學習專業知識也能使用模型建立器。</span><span class="sxs-lookup"><span data-stu-id="e0427-106">You don't need machine learning expertise to use Model Builder.</span></span> <span data-ttu-id="e0427-107">您只需要一些資料和待解決的問題。</span><span class="sxs-lookup"><span data-stu-id="e0427-107">All you need is some data, and a problem to solve.</span></span> <span data-ttu-id="e0427-108">模型建立器會產生程式碼，將模型新增至您的 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e0427-108">Model Builder generates the code to add the model to your .NET application.</span></span>

![模型建立器 Visual Studio 延伸模組使用者介面動畫](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> <span data-ttu-id="e0427-110">模型建立器目前為預覽版。</span><span class="sxs-lookup"><span data-stu-id="e0427-110">Model Builder is currently in Preview.</span></span>

## <a name="scenarios"></a><span data-ttu-id="e0427-111">案例</span><span class="sxs-lookup"><span data-stu-id="e0427-111">Scenarios</span></span>

<span data-ttu-id="e0427-112">您可以在模型建立器中放入許多不同的案例，以產生應用程式的機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="e0427-112">You can bring many different scenarios to Model Builder, to generate a machine learning model for your application.</span></span>

<span data-ttu-id="e0427-113">案例是您希望用資料建立的預測型別描述。</span><span class="sxs-lookup"><span data-stu-id="e0427-113">A scenario is a description of the type of prediction you want to make on your data.</span></span> <span data-ttu-id="e0427-114">例如：</span><span class="sxs-lookup"><span data-stu-id="e0427-114">For example:</span></span>
- <span data-ttu-id="e0427-115">根據歷史銷售資料預測未來的產品銷售量</span><span class="sxs-lookup"><span data-stu-id="e0427-115">predict future product sales volume based on historical sales data</span></span>
- <span data-ttu-id="e0427-116">根據客戶評論將人氣分類為正面或負面</span><span class="sxs-lookup"><span data-stu-id="e0427-116">classify sentiments as positive or negative based on customer reviews</span></span>
- <span data-ttu-id="e0427-117">偵測銀行交易是否為詐騙</span><span class="sxs-lookup"><span data-stu-id="e0427-117">detect whether a banking transaction is fraudulent</span></span>
- <span data-ttu-id="e0427-118">將客戶意見反應問題路由至公司的正確小組</span><span class="sxs-lookup"><span data-stu-id="e0427-118">route customer feedback issues to the correct team in your company</span></span>

<span data-ttu-id="e0427-119">在模型建立器中，您需要將您的案例對應到 [ML.NET 工作](resources/tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="e0427-119">In Model Builder, you need to map your scenario onto an [ML.NET task](resources/tasks.md).</span></span> <span data-ttu-id="e0427-120">您可以使用模型建立器處理**迴歸** (預測數字) 和**分類** (預測類別)。</span><span class="sxs-lookup"><span data-stu-id="e0427-120">You can use Model Builder for **regression** (predicting numbers) and **classification** (predicting categories).</span></span>

### <a name="which-machine-learning-scenario-is-right-for-me"></a><span data-ttu-id="e0427-121">哪種機器學習服務案例適合我？</span><span class="sxs-lookup"><span data-stu-id="e0427-121">Which machine learning scenario is right for me?</span></span>

<span data-ttu-id="e0427-122">模型建立器附有情感分析、問題分類、價格預測和自訂案例的範本。</span><span class="sxs-lookup"><span data-stu-id="e0427-122">Model Builder comes with templates for sentiment analysis, issue classification, price prediction, and custom scenarios.</span></span> <span data-ttu-id="e0427-123">這些範本可以作為特定 ML.NET 案例的起點使用。</span><span class="sxs-lookup"><span data-stu-id="e0427-123">These templates can be used as a starting point for your specific ML.NET scenario.</span></span>

#### <a name="sentiment-analysis-binary-classification"></a><span data-ttu-id="e0427-124">情感分析 (二元分類)</span><span class="sxs-lookup"><span data-stu-id="e0427-124">Sentiment analysis (binary classification)</span></span>

<span data-ttu-id="e0427-125">情感分析可用來預測客戶意見反應的正面或負面人氣。</span><span class="sxs-lookup"><span data-stu-id="e0427-125">Sentiment analysis can be used to predict positive or negative sentiment of customer feedback.</span></span> <span data-ttu-id="e0427-126">這是二元分類工作的範例。</span><span class="sxs-lookup"><span data-stu-id="e0427-126">It is an example of the binary classification task.</span></span>

<span data-ttu-id="e0427-127">二元分類用來將資料分類為兩種類別 (是/否、通過/失敗、true/false、正/負)。</span><span class="sxs-lookup"><span data-stu-id="e0427-127">Binary classification is used to categorize data into two classes (yes/no; pass/fail; true/false; positive/negative).</span></span> <span data-ttu-id="e0427-128">它可用來回答下列問題：</span><span class="sxs-lookup"><span data-stu-id="e0427-128">It can be used to answer questions such as:</span></span>

- <span data-ttu-id="e0427-129">此電子郵件是垃圾郵件嗎？</span><span class="sxs-lookup"><span data-stu-id="e0427-129">Is this email spam?</span></span> <span data-ttu-id="e0427-130">(垃圾郵件偵測)</span><span class="sxs-lookup"><span data-stu-id="e0427-130">(spam detection)</span></span>
- <span data-ttu-id="e0427-131">哪些申請者符合成員資格？</span><span class="sxs-lookup"><span data-stu-id="e0427-131">Which applicants may be eligible for membership?</span></span> <span data-ttu-id="e0427-132">(申請篩選)</span><span class="sxs-lookup"><span data-stu-id="e0427-132">(application screening)</span></span>
- <span data-ttu-id="e0427-133">哪些帳戶可能不會準時付款？</span><span class="sxs-lookup"><span data-stu-id="e0427-133">Which accounts may not pay their invoices on time?</span></span> <span data-ttu-id="e0427-134">(風險降低)</span><span class="sxs-lookup"><span data-stu-id="e0427-134">(risk mitigation)</span></span>
- <span data-ttu-id="e0427-135">此信用卡交易為詐騙嗎？</span><span class="sxs-lookup"><span data-stu-id="e0427-135">Is this credit card transaction fraudulent?</span></span> <span data-ttu-id="e0427-136">(詐騙偵測)</span><span class="sxs-lookup"><span data-stu-id="e0427-136">(fraud detection)</span></span>

<span data-ttu-id="e0427-137">如果您的案例需要分類成兩種類別，您可以使用此範本處理您的資料集。</span><span class="sxs-lookup"><span data-stu-id="e0427-137">If your scenario requires classification into two categories, you can use this template with your own dataset.</span></span>
 
#### <a name="issue-classification-multiclass-classification"></a><span data-ttu-id="e0427-138">問題分類 (多元分類)</span><span class="sxs-lookup"><span data-stu-id="e0427-138">Issue classification (multiclass classification)</span></span>

<span data-ttu-id="e0427-139">問題分類可使用問題標題和描述來分類客戶意見反應問題 (例如，針對 GitHub)。</span><span class="sxs-lookup"><span data-stu-id="e0427-139">Issue classification can be used to categorize customer feedback (for example, on GitHub) issues using the issue title and description.</span></span> <span data-ttu-id="e0427-140">這是多元分類工作的範例。</span><span class="sxs-lookup"><span data-stu-id="e0427-140">It is an example of the multi-class classification task.</span></span>

<span data-ttu-id="e0427-141">多元分類可用來將資料分類為三或多個類別。</span><span class="sxs-lookup"><span data-stu-id="e0427-141">Multiclass classification can be used to categorize data into three or more classes.</span></span> <span data-ttu-id="e0427-142">它可用來回答下列問題：</span><span class="sxs-lookup"><span data-stu-id="e0427-142">It can be used to answer questions such as:</span></span>

- <span data-ttu-id="e0427-143">我該將支援票證路由到哪個部門？</span><span class="sxs-lookup"><span data-stu-id="e0427-143">To which department should I route a support ticket?</span></span> <span data-ttu-id="e0427-144">(路由支援票證)</span><span class="sxs-lookup"><span data-stu-id="e0427-144">(support ticket routing)</span></span>
- <span data-ttu-id="e0427-145">客戶問題的優先順序為何？</span><span class="sxs-lookup"><span data-stu-id="e0427-145">What is the priority of a customer issue?</span></span> <span data-ttu-id="e0427-146">(客戶問題的優先順序)</span><span class="sxs-lookup"><span data-stu-id="e0427-146">(customer issue prioritization)</span></span>
- <span data-ttu-id="e0427-147">產品屬於哪個類別？</span><span class="sxs-lookup"><span data-stu-id="e0427-147">What category does a product belong to?</span></span> <span data-ttu-id="e0427-148">(產品分類)</span><span class="sxs-lookup"><span data-stu-id="e0427-148">(product classification)</span></span>
- <span data-ttu-id="e0427-149">哪種文件？</span><span class="sxs-lookup"><span data-stu-id="e0427-149">What type of document?</span></span> <span data-ttu-id="e0427-150">(文件/電子郵件分類)</span><span class="sxs-lookup"><span data-stu-id="e0427-150">(document/email classification)</span></span>

<span data-ttu-id="e0427-151">如果您想要將資料分類為三或多個類別，您可以使用問題分類範本處理您的案例。</span><span class="sxs-lookup"><span data-stu-id="e0427-151">You can use the issue classification template for your scenario if you want to categorize data into three or more categories.</span></span>

#### <a name="price-prediction-regression"></a><span data-ttu-id="e0427-152">價格預測 (迴歸)</span><span class="sxs-lookup"><span data-stu-id="e0427-152">Price prediction (regression)</span></span>

<span data-ttu-id="e0427-153">價格預測可使用位置、大小和其他房屋特性來預測房價。</span><span class="sxs-lookup"><span data-stu-id="e0427-153">Price prediction can be used to predict house prices using location, size, and other characteristics of the house.</span></span> <span data-ttu-id="e0427-154">它是迴歸工作的範例。</span><span class="sxs-lookup"><span data-stu-id="e0427-154">It is an example of the regression task.</span></span>

<span data-ttu-id="e0427-155">迴歸用來預測數字。</span><span class="sxs-lookup"><span data-stu-id="e0427-155">Regression is used to predict numbers.</span></span> <span data-ttu-id="e0427-156">它可用來回答下列問題：</span><span class="sxs-lookup"><span data-stu-id="e0427-156">It can be used to answer questions such as:</span></span>

- <span data-ttu-id="e0427-157">房屋的售價為何？</span><span class="sxs-lookup"><span data-stu-id="e0427-157">What price will a house sell for?</span></span> <span data-ttu-id="e0427-158">(價格預測)</span><span class="sxs-lookup"><span data-stu-id="e0427-158">(price prediction)</span></span>
- <span data-ttu-id="e0427-159">機械組件多久之後需要維修？</span><span class="sxs-lookup"><span data-stu-id="e0427-159">After how much time will a mechanical part require maintenance?</span></span> <span data-ttu-id="e0427-160">(預測性維護)</span><span class="sxs-lookup"><span data-stu-id="e0427-160">(predictive maintenance)</span></span>
- <span data-ttu-id="e0427-161">此乾燥機的含水量為何？</span><span class="sxs-lookup"><span data-stu-id="e0427-161">What is the moisture content in this dryer?</span></span> <span data-ttu-id="e0427-162">(機器監視)</span><span class="sxs-lookup"><span data-stu-id="e0427-162">(machine monitoring)</span></span>
- <span data-ttu-id="e0427-163">此區域的年度總銷售額為何？</span><span class="sxs-lookup"><span data-stu-id="e0427-163">What will the total annual sales for this region be?</span></span> <span data-ttu-id="e0427-164">(銷售預測)</span><span class="sxs-lookup"><span data-stu-id="e0427-164">(sales forecasting)</span></span>

<span data-ttu-id="e0427-165">如果您想要使用自己的資料集來預測數值，針對您的案例您可以使用價格預測範本。</span><span class="sxs-lookup"><span data-stu-id="e0427-165">You can use the price prediction template for your scenario if you want to predict a numerical value with your own dataset.</span></span>

#### <a name="custom-scenario-choose-your-task"></a><span data-ttu-id="e0427-166">自訂案例 (選擇您的工作)</span><span class="sxs-lookup"><span data-stu-id="e0427-166">Custom scenario (choose your task)</span></span>

<span data-ttu-id="e0427-167">自訂案例可讓您選擇自己的工作。</span><span class="sxs-lookup"><span data-stu-id="e0427-167">The custom scenario allows you to choose your own task.</span></span> <span data-ttu-id="e0427-168">挑選最能處理問題的案例。</span><span class="sxs-lookup"><span data-stu-id="e0427-168">Pick the scenario that makes the most sense for your problem.</span></span>

<span data-ttu-id="e0427-169">自訂案例可讓您選擇自己的機器學習服務工作。</span><span class="sxs-lookup"><span data-stu-id="e0427-169">The custom scenario allows you to choose your own machine learning task.</span></span> <span data-ttu-id="e0427-170">在前面的範本中，機器學習服務工作已固定為以下案例︰二元分類、多元分類或迴歸。</span><span class="sxs-lookup"><span data-stu-id="e0427-170">In the previous templates, the machine learning task was fixed to the scenario: binary classification, multi-class classification, or regression.</span></span> <span data-ttu-id="e0427-171">在此範本中，您可以選擇您想要用在您資料上的 ML 工作。</span><span class="sxs-lookup"><span data-stu-id="e0427-171">In this template, you can choose the ML task you want to use on your data.</span></span>

## <a name="data"></a><span data-ttu-id="e0427-172">資料</span><span class="sxs-lookup"><span data-stu-id="e0427-172">Data</span></span>

<span data-ttu-id="e0427-173">一旦案例對應到工作，模型建立器就會要求您提供資料集。</span><span class="sxs-lookup"><span data-stu-id="e0427-173">Once you have mapped your scenario onto a task, Model Builder asks you to provide a dataset.</span></span> <span data-ttu-id="e0427-174">資料用來定型、評估及選擇最適合您案例的模型。</span><span class="sxs-lookup"><span data-stu-id="e0427-174">The data is used to train, evaluate, and choose the best model for your scenario.</span></span> <span data-ttu-id="e0427-175">您也需要選擇您想要預測的輸出。</span><span class="sxs-lookup"><span data-stu-id="e0427-175">You also need to choose the output you want to predict.</span></span>

### <a name="choose-the-output-to-predict-label"></a><span data-ttu-id="e0427-176">選擇要預測的輸出 (標籤)</span><span class="sxs-lookup"><span data-stu-id="e0427-176">Choose the output to predict (label)</span></span>

<span data-ttu-id="e0427-177">資料集是定型範例資料列和屬性資料行的資料表。</span><span class="sxs-lookup"><span data-stu-id="e0427-177">A dataset is a table of rows of training examples, and columns of attributes.</span></span> <span data-ttu-id="e0427-178">每個資料列都有：</span><span class="sxs-lookup"><span data-stu-id="e0427-178">Each row has:</span></span>
- <span data-ttu-id="e0427-179">**標籤** (您想要預測的屬性)</span><span class="sxs-lookup"><span data-stu-id="e0427-179">a **label** (the attribute that you want to predict)</span></span>
- <span data-ttu-id="e0427-180">**特性** (作為輸入用來預測標籤的屬性)。</span><span class="sxs-lookup"><span data-stu-id="e0427-180">**features** (attributes that are used as inputs to predict the label).</span></span>

<span data-ttu-id="e0427-181">針對房價預測案例，可能的特性為：</span><span class="sxs-lookup"><span data-stu-id="e0427-181">For the house-price prediction scenario, the features could be:</span></span>
- <span data-ttu-id="e0427-182">房屋的坪數</span><span class="sxs-lookup"><span data-stu-id="e0427-182">the square footage of the house</span></span>
- <span data-ttu-id="e0427-183">房間和衛浴數量</span><span class="sxs-lookup"><span data-stu-id="e0427-183">the number of bedrooms and bathrooms</span></span>
- <span data-ttu-id="e0427-184">郵遞區號</span><span class="sxs-lookup"><span data-stu-id="e0427-184">the zip code</span></span>

<span data-ttu-id="e0427-185">標籤是坪數列、房間和衛浴值，以及郵遞區號資料列的歷史房價。</span><span class="sxs-lookup"><span data-stu-id="e0427-185">The label is the historical house price for that row of square footage, bedroom, and bathroom values and zip code.</span></span>

![資料表顯示房價資料的資料列和資料行，具有大小、房間數、郵遞區號和價格標籤組成的特性](media/model-builder-data.png)

### <a name="data-formats"></a><span data-ttu-id="e0427-187">資料格式</span><span class="sxs-lookup"><span data-stu-id="e0427-187">Data formats</span></span>

<span data-ttu-id="e0427-188">模型建立器對資料有下列限制：</span><span class="sxs-lookup"><span data-stu-id="e0427-188">Model Builder places the following limitations on the data:</span></span>

- <span data-ttu-id="e0427-189">資料必須儲存在檔案 (有標頭資料列的 .csv 或 .tsv) 或 SQL Server 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="e0427-189">Data must be stored in a file (.csv or .tsv with a header row), or in a SQL server database.</span></span>
- <span data-ttu-id="e0427-190">定型資料集的限制為 1 GB</span><span class="sxs-lookup"><span data-stu-id="e0427-190">A limit of 1 GB on the training dataset</span></span>
- <span data-ttu-id="e0427-191">SQL Server 的定型上限為 100,000 筆資料列</span><span class="sxs-lookup"><span data-stu-id="e0427-191">SQL server has a limit of 100,000 rows for training</span></span>
- <span data-ttu-id="e0427-192">SQL Server 資料會在定型前從伺服器複製到您的本機電腦</span><span class="sxs-lookup"><span data-stu-id="e0427-192">Data from SQL server is copied from the server to your local machine before training</span></span>

### <a name="example-datasets"></a><span data-ttu-id="e0427-193">範例資料集</span><span class="sxs-lookup"><span data-stu-id="e0427-193">Example datasets</span></span>

<span data-ttu-id="e0427-194">如果您還沒有自己的資料，請嘗試下列資料集之一：</span><span class="sxs-lookup"><span data-stu-id="e0427-194">If you don't have your own data yet, try out one of these datasets:</span></span>

|<span data-ttu-id="e0427-195">情節</span><span class="sxs-lookup"><span data-stu-id="e0427-195">Scenario</span></span>|<span data-ttu-id="e0427-196">ML 工作</span><span class="sxs-lookup"><span data-stu-id="e0427-196">ML Task</span></span>|<span data-ttu-id="e0427-197">資料</span><span class="sxs-lookup"><span data-stu-id="e0427-197">Data</span></span>|<span data-ttu-id="e0427-198">標籤</span><span class="sxs-lookup"><span data-stu-id="e0427-198">Label</span></span>|<span data-ttu-id="e0427-199">功能</span><span class="sxs-lookup"><span data-stu-id="e0427-199">Features</span></span>|
|-|-|-|-|-|
|<span data-ttu-id="e0427-200">價格預測</span><span class="sxs-lookup"><span data-stu-id="e0427-200">Price prediction</span></span>|<span data-ttu-id="e0427-201">迴歸</span><span class="sxs-lookup"><span data-stu-id="e0427-201">regression</span></span>|[<span data-ttu-id="e0427-202">計程車費用資料</span><span class="sxs-lookup"><span data-stu-id="e0427-202">taxi fare data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|<span data-ttu-id="e0427-203">費用</span><span class="sxs-lookup"><span data-stu-id="e0427-203">Fare</span></span>|<span data-ttu-id="e0427-204">行車時間、距離</span><span class="sxs-lookup"><span data-stu-id="e0427-204">Trip time, distance</span></span>|
|<span data-ttu-id="e0427-205">異常偵測</span><span class="sxs-lookup"><span data-stu-id="e0427-205">Anomaly detection</span></span>|<span data-ttu-id="e0427-206">二進位分類</span><span class="sxs-lookup"><span data-stu-id="e0427-206">binary classification</span></span>|[<span data-ttu-id="e0427-207">產品銷售資料</span><span class="sxs-lookup"><span data-stu-id="e0427-207">product sales data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|<span data-ttu-id="e0427-208">產品銷售</span><span class="sxs-lookup"><span data-stu-id="e0427-208">Product Sales</span></span>|<span data-ttu-id="e0427-209">月份</span><span class="sxs-lookup"><span data-stu-id="e0427-209">Month</span></span>|
|<span data-ttu-id="e0427-210">情感分析</span><span class="sxs-lookup"><span data-stu-id="e0427-210">Sentiment analysis</span></span>|<span data-ttu-id="e0427-211">二進位分類</span><span class="sxs-lookup"><span data-stu-id="e0427-211">binary classification</span></span>|[<span data-ttu-id="e0427-212">網站留言資料</span><span class="sxs-lookup"><span data-stu-id="e0427-212">website comment data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_SentimentAnalysis/SentimentAnalysis/Data/wikiDetoxAnnotated40kRows.tsv)|<span data-ttu-id="e0427-213">標籤 (負面人氣時為 0，正面人氣時為 1)</span><span class="sxs-lookup"><span data-stu-id="e0427-213">Label (0 when negative sentiment, 1 when positive)</span></span>|<span data-ttu-id="e0427-214">留言、年度</span><span class="sxs-lookup"><span data-stu-id="e0427-214">Comment, Year</span></span>|
|<span data-ttu-id="e0427-215">詐騙偵測</span><span class="sxs-lookup"><span data-stu-id="e0427-215">Fraud detection</span></span>|<span data-ttu-id="e0427-216">二進位分類</span><span class="sxs-lookup"><span data-stu-id="e0427-216">binary classification</span></span>|[<span data-ttu-id="e0427-217">信用卡資料</span><span class="sxs-lookup"><span data-stu-id="e0427-217">credit card data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|<span data-ttu-id="e0427-218">類別 (詐騙時為 1，否則為 0)</span><span class="sxs-lookup"><span data-stu-id="e0427-218">Class (1 when fraudulent, 0 otherwise)</span></span>|<span data-ttu-id="e0427-219">數量、V1-V28 (匿名特性)</span><span class="sxs-lookup"><span data-stu-id="e0427-219">Amount, V1-V28 (anonymized features)</span></span>|
|<span data-ttu-id="e0427-220">文字分類</span><span class="sxs-lookup"><span data-stu-id="e0427-220">Text classification</span></span>|<span data-ttu-id="e0427-221">多元分類</span><span class="sxs-lookup"><span data-stu-id="e0427-221">multiclass classification</span></span>|[<span data-ttu-id="e0427-222">GitHub 問題資料</span><span class="sxs-lookup"><span data-stu-id="e0427-222">GitHub issue data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|<span data-ttu-id="e0427-223">區域圖</span><span class="sxs-lookup"><span data-stu-id="e0427-223">Area</span></span>|<span data-ttu-id="e0427-224">標題、描述</span><span class="sxs-lookup"><span data-stu-id="e0427-224">Title, Description</span></span>|

## <a name="train"></a><span data-ttu-id="e0427-225">定型</span><span class="sxs-lookup"><span data-stu-id="e0427-225">Train</span></span>

<span data-ttu-id="e0427-226">一旦選取案例、資料和標籤，模型建立器就會定型模型。</span><span class="sxs-lookup"><span data-stu-id="e0427-226">Once you select your scenario, data, and label, Model Builder trains the model.</span></span>

### <a name="what-is-training"></a><span data-ttu-id="e0427-227">什麼是定型？</span><span class="sxs-lookup"><span data-stu-id="e0427-227">What is training?</span></span>

<span data-ttu-id="e0427-228">定型模型建立器用來教導模型如何回答案例問題的自動化程序。</span><span class="sxs-lookup"><span data-stu-id="e0427-228">Training is an automatic process by which Model Builder teaches your model how to answer questions for your scenario.</span></span> <span data-ttu-id="e0427-229">一旦定型，模型就可以使用之前未見過的輸入資料來建立預測。</span><span class="sxs-lookup"><span data-stu-id="e0427-229">Once trained, your model can make predictions with input data that it has not seen before.</span></span> <span data-ttu-id="e0427-230">例如，如果您要預測房價且有新屋上市，您就可以預測其銷售價格。</span><span class="sxs-lookup"><span data-stu-id="e0427-230">For example, if you are predicting house prices and a new house comes on the market, you can predict its sale price.</span></span>

<span data-ttu-id="e0427-231">因為模型建立器使用自動化的機器學習服務 (AutoML)，所以它不需要任何輸入，也不需要您在定型期間調整。</span><span class="sxs-lookup"><span data-stu-id="e0427-231">Because Model Builder uses automated machine learning (AutoML), it does not require any input or tuning from you during training.</span></span>

### <a name="how-long-should-i-train-for"></a><span data-ttu-id="e0427-232">定型時間應該多長？</span><span class="sxs-lookup"><span data-stu-id="e0427-232">How long should I train for?</span></span>

<span data-ttu-id="e0427-233">您可以提供定型時間。</span><span class="sxs-lookup"><span data-stu-id="e0427-233">You can provide a training time.</span></span> <span data-ttu-id="e0427-234">一般情況下，定型時間愈長，就會產生愈精確的模型。</span><span class="sxs-lookup"><span data-stu-id="e0427-234">In general, training for a longer time produces a more accurate model.</span></span> <span data-ttu-id="e0427-235">當定型資料集的大小增加時，也會需要更長的定型時間。</span><span class="sxs-lookup"><span data-stu-id="e0427-235">More training time is also required as the size of the training dataset increases.</span></span> <span data-ttu-id="e0427-236">下表提供增加資料集大小的一些定型時間指導方針。</span><span class="sxs-lookup"><span data-stu-id="e0427-236">The following table gives some training time guidelines for datasets of increasing size.</span></span>

<span data-ttu-id="e0427-237">資料集大小</span><span class="sxs-lookup"><span data-stu-id="e0427-237">Dataset Size</span></span>  | <span data-ttu-id="e0427-238">資料集型別</span><span class="sxs-lookup"><span data-stu-id="e0427-238">Dataset Type</span></span>       | <span data-ttu-id="e0427-239">Avg.定型時間</span><span class="sxs-lookup"><span data-stu-id="e0427-239">Avg. Time to train</span></span>
------------- | ------------------ | --------------
<span data-ttu-id="e0427-240">0 - 10 MB</span><span class="sxs-lookup"><span data-stu-id="e0427-240">0 - 10 Mb</span></span>     | <span data-ttu-id="e0427-241">數值和文字</span><span class="sxs-lookup"><span data-stu-id="e0427-241">Numeric and Text</span></span>   | <span data-ttu-id="e0427-242">10 秒</span><span class="sxs-lookup"><span data-stu-id="e0427-242">10 sec</span></span>
<span data-ttu-id="e0427-243">10 - 100 MB</span><span class="sxs-lookup"><span data-stu-id="e0427-243">10 - 100 Mb</span></span>   | <span data-ttu-id="e0427-244">數值和文字</span><span class="sxs-lookup"><span data-stu-id="e0427-244">Numeric and Text</span></span>   | <span data-ttu-id="e0427-245">10 分鐘</span><span class="sxs-lookup"><span data-stu-id="e0427-245">10 min</span></span> 
<span data-ttu-id="e0427-246">100 - 500 MB</span><span class="sxs-lookup"><span data-stu-id="e0427-246">100 - 500 Mb</span></span>  | <span data-ttu-id="e0427-247">數值和文字</span><span class="sxs-lookup"><span data-stu-id="e0427-247">Numeric and Text</span></span>   | <span data-ttu-id="e0427-248">30 分鐘</span><span class="sxs-lookup"><span data-stu-id="e0427-248">30 min</span></span> 
<span data-ttu-id="e0427-249">500 - 1 GB</span><span class="sxs-lookup"><span data-stu-id="e0427-249">500 - 1 Gb</span></span>    | <span data-ttu-id="e0427-250">數值和文字</span><span class="sxs-lookup"><span data-stu-id="e0427-250">Numeric and Text</span></span>   | <span data-ttu-id="e0427-251">60 分鐘</span><span class="sxs-lookup"><span data-stu-id="e0427-251">60 min</span></span> 
<span data-ttu-id="e0427-252">1 GB+</span><span class="sxs-lookup"><span data-stu-id="e0427-252">1 Gb+</span></span>         | <span data-ttu-id="e0427-253">數值和文字</span><span class="sxs-lookup"><span data-stu-id="e0427-253">Numeric and Text</span></span>   | <span data-ttu-id="e0427-254">3 小時以上</span><span class="sxs-lookup"><span data-stu-id="e0427-254">3 hour+</span></span> 

<span data-ttu-id="e0427-255">定型的確切時間也取決於：</span><span class="sxs-lookup"><span data-stu-id="e0427-255">The exact time to train also depends on:</span></span>

- <span data-ttu-id="e0427-256">資料行的型別，文字或數值</span><span class="sxs-lookup"><span data-stu-id="e0427-256">the type of columns that is, text vs numeric</span></span>
- <span data-ttu-id="e0427-257">機器學習服務工作的型別 (迴歸或分類)</span><span class="sxs-lookup"><span data-stu-id="e0427-257">the type of machine learning task (regression or classification)</span></span>
- <span data-ttu-id="e0427-258">用於定型的資料列數目</span><span class="sxs-lookup"><span data-stu-id="e0427-258">the number of rows used for training</span></span>
- <span data-ttu-id="e0427-259">用於定型的特性資料行數目</span><span class="sxs-lookup"><span data-stu-id="e0427-259">the number of feature columns used for training</span></span>

<span data-ttu-id="e0427-260">模型建立器已通過 1-TB 資料集的縮放測試，但建置此大小資料集的高品質模型最多可能耗時四天！</span><span class="sxs-lookup"><span data-stu-id="e0427-260">Model Builder has been tested for scale with a 1-TB dataset, but building a high-quality model for that size of dataset can take up to four days!</span></span>

## <a name="evaluate"></a><span data-ttu-id="e0427-261">評估</span><span class="sxs-lookup"><span data-stu-id="e0427-261">Evaluate</span></span>

<span data-ttu-id="e0427-262">評估是使用定型模型以新測試資料來建立預測，然後測量預測有多準確的程序。</span><span class="sxs-lookup"><span data-stu-id="e0427-262">Evaluation is the process of using the trained model to make predictions with new test data, and then measuring how good the predictions are.</span></span>

<span data-ttu-id="e0427-263">模型建立器會將定型資料分割為定型集和測試集。</span><span class="sxs-lookup"><span data-stu-id="e0427-263">Model Builder splits the training data into a training set and a test set.</span></span> <span data-ttu-id="e0427-264">定型資料 (80%) 用來定型模型，而測試資料 (20%) 則保留用於評估模型。</span><span class="sxs-lookup"><span data-stu-id="e0427-264">The training data (80%) is used to train your model and the test data (20%) is held back to evaluate your model.</span></span>  <span data-ttu-id="e0427-265">用於評估的計量取決於 ML 工作。</span><span class="sxs-lookup"><span data-stu-id="e0427-265">The metrics used for evaluation depend on the ML task.</span></span> <span data-ttu-id="e0427-266">如需詳細資訊，請參閱[模型評估計量](resources/metrics.md)。</span><span class="sxs-lookup"><span data-stu-id="e0427-266">For more information, see [model evaluation metrics](resources/metrics.md).</span></span>  

### <a name="sentiment-analysis-binary-classification"></a><span data-ttu-id="e0427-267">情感分析 (二元分類)</span><span class="sxs-lookup"><span data-stu-id="e0427-267">Sentiment analysis (binary classification)</span></span>

<span data-ttu-id="e0427-268">二元分類問題的預設計量為**精確度**。</span><span class="sxs-lookup"><span data-stu-id="e0427-268">The default metric for binary classification problems is **accuracy**.</span></span> <span data-ttu-id="e0427-269">精確度會定義模型對測試資料集建立的正確預測比例。</span><span class="sxs-lookup"><span data-stu-id="e0427-269">Accuracy defines the proportion of correct predictions your model makes over the test dataset.</span></span> <span data-ttu-id="e0427-270">**越接近 100% 越好**。</span><span class="sxs-lookup"><span data-stu-id="e0427-270">The **closer to 100%, the better it is**.</span></span>

<span data-ttu-id="e0427-271">其他回報計量，例如測量真陽性率和偽陽性率的 AUC (曲線下面積) 應大於 0.50 才是可以接受的模型。</span><span class="sxs-lookup"><span data-stu-id="e0427-271">Other metrics reported such as AUC (Area under the curve), which measures the true positive rate vs. the false positive rate, should be greater than 0.50 for models to be acceptable.</span></span> 

<span data-ttu-id="e0427-272">其他計量，例如 F1 分數可用來控制精確度 (該類別總預測數的正確預測率) 與回收 (該類別實際成員總數的正確預測比例) 之間的平衡。</span><span class="sxs-lookup"><span data-stu-id="e0427-272">Additional metrics such as F1 score can be used to control the balance between precision (ratio of correct predictions to the total predictions of that class) and recall (proportion of correct predictions to the total actual members of that class).</span></span>

### <a name="issue-classification-multiclass-classification"></a><span data-ttu-id="e0427-273">問題分類 (多元分類)</span><span class="sxs-lookup"><span data-stu-id="e0427-273">Issue classification (multiclass classification)</span></span>

<span data-ttu-id="e0427-274">多元分類問題的預設計量是**微精確度**。</span><span class="sxs-lookup"><span data-stu-id="e0427-274">The default metric for multiclass classification problems is **micro accuracy**.</span></span> <span data-ttu-id="e0427-275">**越接近 100% 越好**。</span><span class="sxs-lookup"><span data-stu-id="e0427-275">The **closer to 100%, the better it is**.</span></span>

<span data-ttu-id="e0427-276">資料分類成多個類別的問題有兩種精確度：</span><span class="sxs-lookup"><span data-stu-id="e0427-276">For problems where data is categorized into multiple classes there are two types of accuracy:</span></span>

- <span data-ttu-id="e0427-277">微精確度：所有執行個體的正確預測分數。</span><span class="sxs-lookup"><span data-stu-id="e0427-277">Micro-accuracy: the fraction of predictions that are correct across all instances.</span></span> <span data-ttu-id="e0427-278">在問題分類案例中，微精確度是指派給正確類別的發生問題比例。</span><span class="sxs-lookup"><span data-stu-id="e0427-278">In the issue classification scenario, micro-accuracy is the proportion of incoming issues that get assigned to the correct category.</span></span> 
- <span data-ttu-id="e0427-279">宏準確度：類別層級的平均準確度。</span><span class="sxs-lookup"><span data-stu-id="e0427-279">Macro-accuracy: the average accuracy at the class level.</span></span> <span data-ttu-id="e0427-280">在問題分類案例中，會測量每個類別的精確度，然後平均分類的精確度。</span><span class="sxs-lookup"><span data-stu-id="e0427-280">In the issue classification scenario, the accuracy is measured for each category, and then the category accuracies are averaged.</span></span> <span data-ttu-id="e0427-281">針對此計量，所有類別都有相同的權重。</span><span class="sxs-lookup"><span data-stu-id="e0427-281">For this metric, all classes are given equal weight.</span></span> <span data-ttu-id="e0427-282">若為完美平衡的資料集 (即每個類別的範例數都相同)，微精確度和宏精確度相同。</span><span class="sxs-lookup"><span data-stu-id="e0427-282">For perfectly balanced datasets (where there are an equal number of examples of each category), micro-accuracy and macro-accuracy are the same.</span></span>


### <a name="price-prediction-regression"></a><span data-ttu-id="e0427-283">價格預測 (迴歸)</span><span class="sxs-lookup"><span data-stu-id="e0427-283">Price prediction (regression)</span></span>

<span data-ttu-id="e0427-284">迴歸問題的預設計量為 **RSquared**。</span><span class="sxs-lookup"><span data-stu-id="e0427-284">The default metric for regression problems is **RSquared**.</span></span> <span data-ttu-id="e0427-285">1 是最可能的值。</span><span class="sxs-lookup"><span data-stu-id="e0427-285">1 is the best possible value.</span></span> <span data-ttu-id="e0427-286">RSquared 越接近 1，模型就越好。</span><span class="sxs-lookup"><span data-stu-id="e0427-286">The closer RSquared is to 1, the better your model is.</span></span>

<span data-ttu-id="e0427-287">其他回報計量，例如絕對損失、平方損失和 RMS 損失，都可以用來了解您的模型，並和其他迴歸模型比較。</span><span class="sxs-lookup"><span data-stu-id="e0427-287">Other metrics reported, such as absolute-loss, squared-loss, and RMS loss can be used to understand your model, and compare it with other regression models.</span></span> 

## <a name="improve"></a><span data-ttu-id="e0427-288">改善</span><span class="sxs-lookup"><span data-stu-id="e0427-288">Improve</span></span>

<span data-ttu-id="e0427-289">如果您的模型效能分數不如預期，您可以：</span><span class="sxs-lookup"><span data-stu-id="e0427-289">If your model performance score is not as good as you want it to be, you can:</span></span>

* <span data-ttu-id="e0427-290">延長定型時間。</span><span class="sxs-lookup"><span data-stu-id="e0427-290">Train for a longer period of time.</span></span> <span data-ttu-id="e0427-291">時間較長，自動化的機器學習引擎就會嘗試更多演算法及設定。</span><span class="sxs-lookup"><span data-stu-id="e0427-291">With more time, the automated machine learning engine to try more algorithms and settings.</span></span>

* <span data-ttu-id="e0427-292">新增更多資料。</span><span class="sxs-lookup"><span data-stu-id="e0427-292">Add more data.</span></span> <span data-ttu-id="e0427-293">有時資料數量不足，無法定型高品質的機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="e0427-293">Sometimes the amount of data is not sufficient to train a high-quality machine learning model.</span></span> 

* <span data-ttu-id="e0427-294">平衡資料。</span><span class="sxs-lookup"><span data-stu-id="e0427-294">Balance your data.</span></span> <span data-ttu-id="e0427-295">針對分類工作，請務必平衡所有類別的定型集。</span><span class="sxs-lookup"><span data-stu-id="e0427-295">For classification tasks, make sure that the training set is balanced across the categories.</span></span> <span data-ttu-id="e0427-296">例如，如果您有四個類別的 100 個定型範例，有 90 筆記錄使用前兩個類別 (tag1 和 tag2)，只有剩餘的 10 筆記錄使用其他兩個類別 (tag3 和 tag4)，則資料失衡可能會導致模型難以正確預測 tag3 或 tag4。</span><span class="sxs-lookup"><span data-stu-id="e0427-296">For example, if you have four classes for 100 training examples, and the two first classes (tag1 and tag2) are used for 90 records, but the other two (tag3 and tag4) are only used on the remaining 10 records, the lack of balanced data may cause your model to struggle to correctly predict tag3 or tag4.</span></span>

## <a name="code"></a><span data-ttu-id="e0427-297">程式碼</span><span class="sxs-lookup"><span data-stu-id="e0427-297">Code</span></span>

<span data-ttu-id="e0427-298">在評估階段後，模型建立器會輸出模型檔案，以及可用來將模型新增至應用程式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e0427-298">After the evaluation phase, Model Builder outputs a model file, and code that you can use to add the model to your application.</span></span> <span data-ttu-id="e0427-299">ML.NET 模型會儲存為 ZIP 檔案。</span><span class="sxs-lookup"><span data-stu-id="e0427-299">ML.NET models are saved as a zip file.</span></span> <span data-ttu-id="e0427-300">載入並使用模型的程式碼會新增為解決方案中新專案。</span><span class="sxs-lookup"><span data-stu-id="e0427-300">The code to load and use your model is added as a new project in your solution.</span></span> <span data-ttu-id="e0427-301">模型建立器也會新增範例主控台應用程式，您可以執行它以查看運行的模型。</span><span class="sxs-lookup"><span data-stu-id="e0427-301">Model Builder also adds a sample console app that you can run to see your model in action.</span></span>

<span data-ttu-id="e0427-302">此外，模型建立器會輸出產生模型的程式碼，以便您可以了解產生模型所用的步驟。</span><span class="sxs-lookup"><span data-stu-id="e0427-302">In addition, Model Builder outputs the code that generated the model, so that you can understand the steps used to generate the model.</span></span> <span data-ttu-id="e0427-303">您也可以使用模型定型程式碼以新資料重新定型模型。</span><span class="sxs-lookup"><span data-stu-id="e0427-303">You can also use the model training code to retrain your model with new data.</span></span>

## <a name="whats-next"></a><span data-ttu-id="e0427-304">後續步驟</span><span class="sxs-lookup"><span data-stu-id="e0427-304">What's next?</span></span>

<span data-ttu-id="e0427-305">請嘗試[價格預測或任何迴歸案例](tutorials/predict-prices-with-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="e0427-305">Try [price prediction or any regression scenario](tutorials/predict-prices-with-model-builder.md)</span></span>
