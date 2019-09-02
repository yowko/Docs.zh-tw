---
title: 什麼是模型建立器且其如何運作？
description: 如何使用 ML.NET 模型建立器來自動定型機器學習服務模型
author: natke
ms.date: 08/07/2019
ms.custom: overview
ms.openlocfilehash: 715c9f5854d9691fd9fc2cd771d38456405836ec
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70104872"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a><span data-ttu-id="6bc47-103">什麼是模型建立器且其如何運作？</span><span class="sxs-lookup"><span data-stu-id="6bc47-103">What is Model Builder and how does it work?</span></span>

<span data-ttu-id="6bc47-104">ML.NET 模型建立器是直覺式圖形化 Visual Studio 延伸模組，其用於建置、定型和部署自訂機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="6bc47-104">ML.NET Model Builder is an intuitive graphical Visual Studio extension to build, train, and deploy custom machine learning models.</span></span>

<span data-ttu-id="6bc47-105">模型建立器會使用自動化的機器學習服務 (AutoML) 來探索不同機器學習服務演算法和設定，協助您找出最適合您案例的組合。</span><span class="sxs-lookup"><span data-stu-id="6bc47-105">Model Builder uses automated machine learning (AutoML) to explore different machine learning algorithms and settings to help you find the one that best suits your scenario.</span></span>

<span data-ttu-id="6bc47-106">您不需要有機器學習專業知識也能使用模型建立器。</span><span class="sxs-lookup"><span data-stu-id="6bc47-106">You don't need machine learning expertise to use Model Builder.</span></span> <span data-ttu-id="6bc47-107">您只需要一些資料和待解決的問題。</span><span class="sxs-lookup"><span data-stu-id="6bc47-107">All you need is some data, and a problem to solve.</span></span> <span data-ttu-id="6bc47-108">模型建立器會產生程式碼，將模型新增至您的 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="6bc47-108">Model Builder generates the code to add the model to your .NET application.</span></span>

![模型建立器 Visual Studio 延伸模組使用者介面動畫](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> <span data-ttu-id="6bc47-110">模型建立器目前為預覽版。</span><span class="sxs-lookup"><span data-stu-id="6bc47-110">Model Builder is currently in Preview.</span></span>

## <a name="scenarios"></a><span data-ttu-id="6bc47-111">案例</span><span class="sxs-lookup"><span data-stu-id="6bc47-111">Scenarios</span></span>

<span data-ttu-id="6bc47-112">您可以在模型建立器中放入許多不同的案例，以產生應用程式的機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="6bc47-112">You can bring many different scenarios to Model Builder, to generate a machine learning model for your application.</span></span>

<span data-ttu-id="6bc47-113">案例是您想要使用資料進行的預測類型描述。</span><span class="sxs-lookup"><span data-stu-id="6bc47-113">A scenario is a description of the type of prediction you want to make using your data.</span></span> <span data-ttu-id="6bc47-114">例如：</span><span class="sxs-lookup"><span data-stu-id="6bc47-114">For example:</span></span>
- <span data-ttu-id="6bc47-115">根據歷史銷售資料預測未來的產品銷售量</span><span class="sxs-lookup"><span data-stu-id="6bc47-115">predict future product sales volume based on historical sales data</span></span>
- <span data-ttu-id="6bc47-116">根據客戶評論將人氣分類為正面或負面</span><span class="sxs-lookup"><span data-stu-id="6bc47-116">classify sentiments as positive or negative based on customer reviews</span></span>
- <span data-ttu-id="6bc47-117">偵測銀行交易是否為詐騙</span><span class="sxs-lookup"><span data-stu-id="6bc47-117">detect whether a banking transaction is fraudulent</span></span>
- <span data-ttu-id="6bc47-118">將客戶意見反應問題路由至公司的正確小組</span><span class="sxs-lookup"><span data-stu-id="6bc47-118">route customer feedback issues to the correct team in your company</span></span>

## <a name="choose-a-model-type"></a><span data-ttu-id="6bc47-119">選擇模型類型</span><span class="sxs-lookup"><span data-stu-id="6bc47-119">Choose a model type</span></span>

<span data-ttu-id="6bc47-120">在模型建立器中，您需要選取機器學習模型類型。</span><span class="sxs-lookup"><span data-stu-id="6bc47-120">In Model Builder, you need to select a machine learning model type.</span></span> <span data-ttu-id="6bc47-121">模型類型取決於您嘗試進行的預測類型。</span><span class="sxs-lookup"><span data-stu-id="6bc47-121">The type of model depends on what sort of prediction you are trying to make.</span></span>

<span data-ttu-id="6bc47-122">在預測數字的案例中，機器學習模型類型稱為`regression`。</span><span class="sxs-lookup"><span data-stu-id="6bc47-122">For scenarios that predict a number, the machine learning model type is called `regression`.</span></span>

<span data-ttu-id="6bc47-123">在預測類別的案例中，模型類型為 `classification`。</span><span class="sxs-lookup"><span data-stu-id="6bc47-123">For scenarios that predict a category, the model type is `classification`.</span></span> <span data-ttu-id="6bc47-124">分類有兩種類型：</span><span class="sxs-lookup"><span data-stu-id="6bc47-124">There are two types of classification:</span></span>
- <span data-ttu-id="6bc47-125">其中只有 2 個類別：`binary classification`。</span><span class="sxs-lookup"><span data-stu-id="6bc47-125">where there are only 2 categories: `binary classification`.</span></span>
- <span data-ttu-id="6bc47-126">其中有三個或多個類別：`multiclass classification`。</span><span class="sxs-lookup"><span data-stu-id="6bc47-126">where there are three or more categories: `multiclass classification`.</span></span>

### <a name="which-model-type-is-right-for-me"></a><span data-ttu-id="6bc47-127">哪一種模型類型適合我？</span><span class="sxs-lookup"><span data-stu-id="6bc47-127">Which model type is right for me?</span></span>

#### <a name="predict-a-category-when-there-are-only-two-categories"></a><span data-ttu-id="6bc47-128">預測類別 (當只有兩個類別時)</span><span class="sxs-lookup"><span data-stu-id="6bc47-128">Predict a category (when there are only two categories)</span></span>

<span data-ttu-id="6bc47-129">二元分類用來將資料分類為兩個類別 (是/否、通過/失敗、true/false、正/負)。</span><span class="sxs-lookup"><span data-stu-id="6bc47-129">Binary classification is used to categorize data into two categories (yes/no; pass/fail; true/false; positive/negative).</span></span>

![顯示二元分類範例的圖表，包括詐騙偵測、風險降低和應用程式檢測](media/binary-classification-examples.png)

<span data-ttu-id="6bc47-131">情感分析可用來預測客戶意見反應的正面或負面人氣。</span><span class="sxs-lookup"><span data-stu-id="6bc47-131">Sentiment analysis can be used to predict positive or negative sentiment of customer feedback.</span></span> <span data-ttu-id="6bc47-132">這是二元分類模型類型的範例。</span><span class="sxs-lookup"><span data-stu-id="6bc47-132">It is an example of a binary classification model type.</span></span>

<span data-ttu-id="6bc47-133">如果您的案例需要分類成兩種類別，您可以使用此範本處理您的資料集。</span><span class="sxs-lookup"><span data-stu-id="6bc47-133">If your scenario requires classification into two categories, you can use this template with your own dataset.</span></span>

#### <a name="predict-a-category-when-there-are-three-or-more-categories"></a><span data-ttu-id="6bc47-134">預測類別 (當有三個或多個類別時)</span><span class="sxs-lookup"><span data-stu-id="6bc47-134">Predict a category (when there are three or more categories)</span></span>

<span data-ttu-id="6bc47-135">多元分類可用來將資料分類為三或多個類別。</span><span class="sxs-lookup"><span data-stu-id="6bc47-135">Multiclass classification can be used to categorize data into three or more classes.</span></span> 

![多元分類的範例，包括文件和產品分類、支援票證路由，以及客戶問題優先順序](media/multiclass-classification-examples.png)

<span data-ttu-id="6bc47-137">問題分類可使用問題標題和描述來分類客戶意見反應問題 (例如，針對 GitHub)。</span><span class="sxs-lookup"><span data-stu-id="6bc47-137">Issue classification can be used to categorize customer feedback (for example, on GitHub) issues using the issue title and description.</span></span> <span data-ttu-id="6bc47-138">這是多元分類模型類型的範例。</span><span class="sxs-lookup"><span data-stu-id="6bc47-138">It is an example of the multi-class classification model type.</span></span>

<span data-ttu-id="6bc47-139">如果您想要將資料分類為三或多個類別，您可以使用問題分類範本處理您的案例。</span><span class="sxs-lookup"><span data-stu-id="6bc47-139">You can use the issue classification template for your scenario if you want to categorize data into three or more categories.</span></span>

#### <a name="predict-a-number"></a><span data-ttu-id="6bc47-140">預測數字</span><span class="sxs-lookup"><span data-stu-id="6bc47-140">Predict a number</span></span>

<span data-ttu-id="6bc47-141">迴歸用來預測數字。</span><span class="sxs-lookup"><span data-stu-id="6bc47-141">Regression is used to predict numbers.</span></span>

![顯示迴歸範例的圖表，例如價格預測、銷售預測和預測性維護](media/regression-examples.png)

<span data-ttu-id="6bc47-143">價格預測可使用位置、大小和其他房屋特性來預測房價。</span><span class="sxs-lookup"><span data-stu-id="6bc47-143">Price prediction can be used to predict house prices using location, size, and other characteristics of the house.</span></span> <span data-ttu-id="6bc47-144">這是迴歸模型類型的範例。</span><span class="sxs-lookup"><span data-stu-id="6bc47-144">It is an example of a regression model type.</span></span>

<span data-ttu-id="6bc47-145">如果您想要使用自己的資料集來預測數值，針對您的案例您可以使用價格預測範本。</span><span class="sxs-lookup"><span data-stu-id="6bc47-145">You can use the price prediction template for your scenario if you want to predict a numerical value with your own dataset.</span></span>

#### <a name="custom-scenario-choose-your-model-type"></a><span data-ttu-id="6bc47-146">自訂案例 (選擇您的模型類型)</span><span class="sxs-lookup"><span data-stu-id="6bc47-146">Custom scenario (choose your model type)</span></span>

<span data-ttu-id="6bc47-147">自訂案例可讓您手動選擇模型類型。</span><span class="sxs-lookup"><span data-stu-id="6bc47-147">The custom scenario allows you to manually choose your model type.</span></span>

## <a name="data"></a><span data-ttu-id="6bc47-148">資料</span><span class="sxs-lookup"><span data-stu-id="6bc47-148">Data</span></span>

<span data-ttu-id="6bc47-149">一旦選擇了模型類型，模型建立器就會要求您提供資料集。</span><span class="sxs-lookup"><span data-stu-id="6bc47-149">Once you have chosen your model type, Model Builder asks you to provide a dataset.</span></span> <span data-ttu-id="6bc47-150">資料用來定型、評估及選擇最適合您案例的模型。</span><span class="sxs-lookup"><span data-stu-id="6bc47-150">The data is used to train, evaluate, and choose the best model for your scenario.</span></span>

![顯示模型建立器步驟的圖表](media/model-builder-steps.png)

### <a name="choose-the-output-to-predict-label"></a><span data-ttu-id="6bc47-152">選擇要預測的輸出 (標籤)</span><span class="sxs-lookup"><span data-stu-id="6bc47-152">Choose the output to predict (label)</span></span>

<span data-ttu-id="6bc47-153">資料集是定型範例資料列和屬性資料行的資料表。</span><span class="sxs-lookup"><span data-stu-id="6bc47-153">A dataset is a table of rows of training examples, and columns of attributes.</span></span> <span data-ttu-id="6bc47-154">每個資料列都有：</span><span class="sxs-lookup"><span data-stu-id="6bc47-154">Each row has:</span></span>
- <span data-ttu-id="6bc47-155">**標籤** (您想要預測的屬性)</span><span class="sxs-lookup"><span data-stu-id="6bc47-155">a **label** (the attribute that you want to predict)</span></span>
- <span data-ttu-id="6bc47-156">**特性** (作為輸入用來預測標籤的屬性)。</span><span class="sxs-lookup"><span data-stu-id="6bc47-156">**features** (attributes that are used as inputs to predict the label).</span></span>

<span data-ttu-id="6bc47-157">針對房價預測案例，可能的特性為：</span><span class="sxs-lookup"><span data-stu-id="6bc47-157">For the house-price prediction scenario, the features could be:</span></span>
- <span data-ttu-id="6bc47-158">房屋的坪數</span><span class="sxs-lookup"><span data-stu-id="6bc47-158">the square footage of the house</span></span>
- <span data-ttu-id="6bc47-159">房間和衛浴數量</span><span class="sxs-lookup"><span data-stu-id="6bc47-159">the number of bedrooms and bathrooms</span></span>
- <span data-ttu-id="6bc47-160">郵遞區號</span><span class="sxs-lookup"><span data-stu-id="6bc47-160">the zip code</span></span>

<span data-ttu-id="6bc47-161">標籤是坪數列、房間和衛浴值，以及郵遞區號資料列的歷史房價。</span><span class="sxs-lookup"><span data-stu-id="6bc47-161">The label is the historical house price for that row of square footage, bedroom, and bathroom values and zip code.</span></span>

![資料表顯示房價資料的資料列和資料行，具有大小、房間數、郵遞區號和價格標籤組成的特性](media/model-builder-data.png)

### <a name="example-datasets"></a><span data-ttu-id="6bc47-163">範例資料集</span><span class="sxs-lookup"><span data-stu-id="6bc47-163">Example datasets</span></span>

<span data-ttu-id="6bc47-164">如果您還沒有自己的資料，請嘗試下列資料集之一：</span><span class="sxs-lookup"><span data-stu-id="6bc47-164">If you don't have your own data yet, try out one of these datasets:</span></span>

|<span data-ttu-id="6bc47-165">情節</span><span class="sxs-lookup"><span data-stu-id="6bc47-165">Scenario</span></span>|<span data-ttu-id="6bc47-166">模型類型</span><span class="sxs-lookup"><span data-stu-id="6bc47-166">Model Type</span></span>|<span data-ttu-id="6bc47-167">資料</span><span class="sxs-lookup"><span data-stu-id="6bc47-167">Data</span></span>|<span data-ttu-id="6bc47-168">標籤</span><span class="sxs-lookup"><span data-stu-id="6bc47-168">Label</span></span>|<span data-ttu-id="6bc47-169">功能</span><span class="sxs-lookup"><span data-stu-id="6bc47-169">Features</span></span>|
|-|-|-|-|-|
|<span data-ttu-id="6bc47-170">價格預測</span><span class="sxs-lookup"><span data-stu-id="6bc47-170">Price prediction</span></span>|<span data-ttu-id="6bc47-171">迴歸</span><span class="sxs-lookup"><span data-stu-id="6bc47-171">regression</span></span>|[<span data-ttu-id="6bc47-172">計程車費用資料</span><span class="sxs-lookup"><span data-stu-id="6bc47-172">taxi fare data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|<span data-ttu-id="6bc47-173">費用</span><span class="sxs-lookup"><span data-stu-id="6bc47-173">Fare</span></span>|<span data-ttu-id="6bc47-174">行車時間、距離</span><span class="sxs-lookup"><span data-stu-id="6bc47-174">Trip time, distance</span></span>|
|<span data-ttu-id="6bc47-175">異常偵測</span><span class="sxs-lookup"><span data-stu-id="6bc47-175">Anomaly detection</span></span>|<span data-ttu-id="6bc47-176">二進位分類</span><span class="sxs-lookup"><span data-stu-id="6bc47-176">binary classification</span></span>|[<span data-ttu-id="6bc47-177">產品銷售資料</span><span class="sxs-lookup"><span data-stu-id="6bc47-177">product sales data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|<span data-ttu-id="6bc47-178">產品銷售</span><span class="sxs-lookup"><span data-stu-id="6bc47-178">Product Sales</span></span>|<span data-ttu-id="6bc47-179">月份</span><span class="sxs-lookup"><span data-stu-id="6bc47-179">Month</span></span>|
|<span data-ttu-id="6bc47-180">情感分析</span><span class="sxs-lookup"><span data-stu-id="6bc47-180">Sentiment analysis</span></span>|<span data-ttu-id="6bc47-181">二進位分類</span><span class="sxs-lookup"><span data-stu-id="6bc47-181">binary classification</span></span>|[<span data-ttu-id="6bc47-182">網站留言資料</span><span class="sxs-lookup"><span data-stu-id="6bc47-182">website comment data</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|<span data-ttu-id="6bc47-183">標籤 (負面人氣時為 0，正面人氣時為 1)</span><span class="sxs-lookup"><span data-stu-id="6bc47-183">Label (0 when negative sentiment, 1 when positive)</span></span>|<span data-ttu-id="6bc47-184">留言、年度</span><span class="sxs-lookup"><span data-stu-id="6bc47-184">Comment, Year</span></span>|
|<span data-ttu-id="6bc47-185">詐騙偵測</span><span class="sxs-lookup"><span data-stu-id="6bc47-185">Fraud detection</span></span>|<span data-ttu-id="6bc47-186">二進位分類</span><span class="sxs-lookup"><span data-stu-id="6bc47-186">binary classification</span></span>|[<span data-ttu-id="6bc47-187">信用卡資料</span><span class="sxs-lookup"><span data-stu-id="6bc47-187">credit card data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|<span data-ttu-id="6bc47-188">類別 (詐騙時為 1，否則為 0)</span><span class="sxs-lookup"><span data-stu-id="6bc47-188">Class (1 when fraudulent, 0 otherwise)</span></span>|<span data-ttu-id="6bc47-189">數量、V1-V28 (匿名特性)</span><span class="sxs-lookup"><span data-stu-id="6bc47-189">Amount, V1-V28 (anonymized features)</span></span>|
|<span data-ttu-id="6bc47-190">文字分類</span><span class="sxs-lookup"><span data-stu-id="6bc47-190">Text classification</span></span>|<span data-ttu-id="6bc47-191">多元分類</span><span class="sxs-lookup"><span data-stu-id="6bc47-191">multiclass classification</span></span>|[<span data-ttu-id="6bc47-192">GitHub 問題資料</span><span class="sxs-lookup"><span data-stu-id="6bc47-192">GitHub issue data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|<span data-ttu-id="6bc47-193">區域圖</span><span class="sxs-lookup"><span data-stu-id="6bc47-193">Area</span></span>|<span data-ttu-id="6bc47-194">標題、描述</span><span class="sxs-lookup"><span data-stu-id="6bc47-194">Title, Description</span></span>|

## <a name="train"></a><span data-ttu-id="6bc47-195">定型</span><span class="sxs-lookup"><span data-stu-id="6bc47-195">Train</span></span>

<span data-ttu-id="6bc47-196">一旦選取案例、資料和標籤，模型建立器就會定型模型。</span><span class="sxs-lookup"><span data-stu-id="6bc47-196">Once you select your scenario, data, and label, Model Builder trains the model.</span></span>

### <a name="what-is-training"></a><span data-ttu-id="6bc47-197">什麼是定型？</span><span class="sxs-lookup"><span data-stu-id="6bc47-197">What is training?</span></span>

<span data-ttu-id="6bc47-198">定型模型建立器用來教導模型如何回答案例問題的自動化程序。</span><span class="sxs-lookup"><span data-stu-id="6bc47-198">Training is an automatic process by which Model Builder teaches your model how to answer questions for your scenario.</span></span> <span data-ttu-id="6bc47-199">一旦定型，模型就可以使用之前未見過的輸入資料來建立預測。</span><span class="sxs-lookup"><span data-stu-id="6bc47-199">Once trained, your model can make predictions with input data that it has not seen before.</span></span> <span data-ttu-id="6bc47-200">例如，如果您要預測房價且有新屋上市，您就可以預測其銷售價格。</span><span class="sxs-lookup"><span data-stu-id="6bc47-200">For example, if you are predicting house prices and a new house comes on the market, you can predict its sale price.</span></span>

<span data-ttu-id="6bc47-201">因為模型建立器使用自動化的機器學習服務 (AutoML)，所以它不需要任何輸入，也不需要您在定型期間調整。</span><span class="sxs-lookup"><span data-stu-id="6bc47-201">Because Model Builder uses automated machine learning (AutoML), it does not require any input or tuning from you during training.</span></span>

## <a name="evaluate"></a><span data-ttu-id="6bc47-202">評估</span><span class="sxs-lookup"><span data-stu-id="6bc47-202">Evaluate</span></span>

<span data-ttu-id="6bc47-203">評估是使用定型模型以新測試資料來建立預測，然後測量預測有多準確的程序。</span><span class="sxs-lookup"><span data-stu-id="6bc47-203">Evaluation is the process of using the trained model to make predictions with new test data, and then measuring how good the predictions are.</span></span>

<span data-ttu-id="6bc47-204">模型建立器會將定型資料分割為定型集和測試集。</span><span class="sxs-lookup"><span data-stu-id="6bc47-204">Model Builder splits the training data into a training set and a test set.</span></span> <span data-ttu-id="6bc47-205">定型資料 (80%) 用來定型模型，而測試資料 (20%) 則保留用於評估模型。</span><span class="sxs-lookup"><span data-stu-id="6bc47-205">The training data (80%) is used to train your model and the test data (20%) is held back to evaluate your model.</span></span> <span data-ttu-id="6bc47-206">模型建立器使用計量來測量模型的完善程度。</span><span class="sxs-lookup"><span data-stu-id="6bc47-206">Model Builder uses metrics to measure how good the model is.</span></span> <span data-ttu-id="6bc47-207">所使用的特定計量會視模型類型而定。</span><span class="sxs-lookup"><span data-stu-id="6bc47-207">The specific metrics used are dependent on the type of model.</span></span> <span data-ttu-id="6bc47-208">如需詳細資訊，請參閱[模型評估計量](resources/metrics.md)。</span><span class="sxs-lookup"><span data-stu-id="6bc47-208">For more information, see [model evaluation metrics](resources/metrics.md).</span></span>

## <a name="improve"></a><span data-ttu-id="6bc47-209">改善</span><span class="sxs-lookup"><span data-stu-id="6bc47-209">Improve</span></span>

<span data-ttu-id="6bc47-210">如果您的模型效能分數不如預期，您可以：</span><span class="sxs-lookup"><span data-stu-id="6bc47-210">If your model performance score is not as good as you want it to be, you can:</span></span>

- <span data-ttu-id="6bc47-211">延長定型時間。</span><span class="sxs-lookup"><span data-stu-id="6bc47-211">Train for a longer period of time.</span></span> <span data-ttu-id="6bc47-212">時間較長，自動化的機器學習引擎就會嘗試更多演算法及設定。</span><span class="sxs-lookup"><span data-stu-id="6bc47-212">With more time, the automated machine learning engine to try more algorithms and settings.</span></span>

- <span data-ttu-id="6bc47-213">新增更多資料。</span><span class="sxs-lookup"><span data-stu-id="6bc47-213">Add more data.</span></span> <span data-ttu-id="6bc47-214">有時資料數量不足，無法定型高品質的機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="6bc47-214">Sometimes the amount of data is not sufficient to train a high-quality machine learning model.</span></span>

- <span data-ttu-id="6bc47-215">平衡資料。</span><span class="sxs-lookup"><span data-stu-id="6bc47-215">Balance your data.</span></span> <span data-ttu-id="6bc47-216">針對分類工作，請務必平衡所有類別的定型集。</span><span class="sxs-lookup"><span data-stu-id="6bc47-216">For classification tasks, make sure that the training set is balanced across the categories.</span></span> <span data-ttu-id="6bc47-217">例如，如果您有四個類別的 100 個定型範例，有 90 筆記錄使用前兩個類別 (tag1 和 tag2)，只有剩餘的 10 筆記錄使用其他兩個類別 (tag3 和 tag4)，則資料失衡可能會導致模型難以正確預測 tag3 或 tag4。</span><span class="sxs-lookup"><span data-stu-id="6bc47-217">For example, if you have four classes for 100 training examples, and the two first classes (tag1 and tag2) are used for 90 records, but the other two (tag3 and tag4) are only used on the remaining 10 records, the lack of balanced data may cause your model to struggle to correctly predict tag3 or tag4.</span></span>

## <a name="code"></a><span data-ttu-id="6bc47-218">程式碼</span><span class="sxs-lookup"><span data-stu-id="6bc47-218">Code</span></span>

<span data-ttu-id="6bc47-219">在評估階段後，模型建立器會輸出模型檔案，以及可用來將模型新增至應用程式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="6bc47-219">After the evaluation phase, Model Builder outputs a model file, and code that you can use to add the model to your application.</span></span> <span data-ttu-id="6bc47-220">ML.NET 模型會儲存為 ZIP 檔案。</span><span class="sxs-lookup"><span data-stu-id="6bc47-220">ML.NET models are saved as a zip file.</span></span> <span data-ttu-id="6bc47-221">載入並使用模型的程式碼會新增為解決方案中新專案。</span><span class="sxs-lookup"><span data-stu-id="6bc47-221">The code to load and use your model is added as a new project in your solution.</span></span> <span data-ttu-id="6bc47-222">模型建立器也會新增範例主控台應用程式，您可以執行它以查看運行的模型。</span><span class="sxs-lookup"><span data-stu-id="6bc47-222">Model Builder also adds a sample console app that you can run to see your model in action.</span></span>

<span data-ttu-id="6bc47-223">此外，模型建立器會輸出產生模型的程式碼，以便您可以了解產生模型所用的步驟。</span><span class="sxs-lookup"><span data-stu-id="6bc47-223">In addition, Model Builder outputs the code that generated the model, so that you can understand the steps used to generate the model.</span></span> <span data-ttu-id="6bc47-224">您也可以使用模型定型程式碼以新資料重新定型模型。</span><span class="sxs-lookup"><span data-stu-id="6bc47-224">You can also use the model training code to retrain your model with new data.</span></span>

## <a name="whats-next"></a><span data-ttu-id="6bc47-225">後續步驟</span><span class="sxs-lookup"><span data-stu-id="6bc47-225">What's next?</span></span>

<span data-ttu-id="6bc47-226">[安裝](how-to-guides/install-model-builder.md)模型建立器 Visual Studio 延伸模組</span><span class="sxs-lookup"><span data-stu-id="6bc47-226">[Install](how-to-guides/install-model-builder.md) the Model Builder Visual Studio extension</span></span>

<span data-ttu-id="6bc47-227">請嘗試[價格預測或任何迴歸案例](tutorials/predict-prices-with-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="6bc47-227">Try [price prediction or any regression scenario](tutorials/predict-prices-with-model-builder.md)</span></span>
