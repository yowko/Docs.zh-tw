---
title: 什麼是模型建立器且其如何運作？
description: 如何使用 ML.NET 模型建立器來自動定型機器學習服務模型
ms.date: 01/07/2020
ms.custom: overview
ms.openlocfilehash: ac704b7961a8442a9174cdef5a4cd2a619236a4e
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777399"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a><span data-ttu-id="ee3f3-103">什麼是模型建立器且其如何運作？</span><span class="sxs-lookup"><span data-stu-id="ee3f3-103">What is Model Builder and how does it work?</span></span>

<span data-ttu-id="ee3f3-104">ML.NET 模型建立器是直覺式圖形化 Visual Studio 延伸模組，其用於建置、定型和部署自訂機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-104">ML.NET Model Builder is an intuitive graphical Visual Studio extension to build, train, and deploy custom machine learning models.</span></span>

<span data-ttu-id="ee3f3-105">模型建立器會使用自動化的機器學習服務 (AutoML) 來探索不同機器學習服務演算法和設定，協助您找出最適合您案例的組合。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-105">Model Builder uses automated machine learning (AutoML) to explore different machine learning algorithms and settings to help you find the one that best suits your scenario.</span></span>

<span data-ttu-id="ee3f3-106">您不需要有機器學習專業知識也能使用模型建立器。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-106">You don't need machine learning expertise to use Model Builder.</span></span> <span data-ttu-id="ee3f3-107">您只需要一些資料和待解決的問題。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-107">All you need is some data, and a problem to solve.</span></span> <span data-ttu-id="ee3f3-108">模型建立器會產生程式碼，將模型新增至您的 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-108">Model Builder generates the code to add the model to your .NET application.</span></span>

![模型建立器 Visual Studio 延伸模組使用者介面動畫](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> <span data-ttu-id="ee3f3-110">模型產生器目前為預覽版。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-110">Model Builder is currently in Preview.</span></span>

## <a name="scenarios"></a><span data-ttu-id="ee3f3-111">案例</span><span class="sxs-lookup"><span data-stu-id="ee3f3-111">Scenarios</span></span>

<span data-ttu-id="ee3f3-112">您可以在模型建立器中放入許多不同的案例，以產生應用程式的機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-112">You can bring many different scenarios to Model Builder, to generate a machine learning model for your application.</span></span>

<span data-ttu-id="ee3f3-113">案例是您想要使用資料進行的預測類型描述。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-113">A scenario is a description of the type of prediction you want to make using your data.</span></span> <span data-ttu-id="ee3f3-114">例如：</span><span class="sxs-lookup"><span data-stu-id="ee3f3-114">For example:</span></span>

- <span data-ttu-id="ee3f3-115">根據歷史銷售資料預測未來的產品銷售量</span><span class="sxs-lookup"><span data-stu-id="ee3f3-115">predict future product sales volume based on historical sales data</span></span>
- <span data-ttu-id="ee3f3-116">根據客戶評論將人氣分類為正面或負面</span><span class="sxs-lookup"><span data-stu-id="ee3f3-116">classify sentiments as positive or negative based on customer reviews</span></span>
- <span data-ttu-id="ee3f3-117">偵測銀行交易是否為詐騙</span><span class="sxs-lookup"><span data-stu-id="ee3f3-117">detect whether a banking transaction is fraudulent</span></span>
- <span data-ttu-id="ee3f3-118">將客戶意見反應問題路由至公司的正確小組</span><span class="sxs-lookup"><span data-stu-id="ee3f3-118">route customer feedback issues to the correct team in your company</span></span>

### <a name="which-machine-learning-scenario-is-right-for-me"></a><span data-ttu-id="ee3f3-119">哪種機器學習服務案例適合我？</span><span class="sxs-lookup"><span data-stu-id="ee3f3-119">Which machine learning scenario is right for me?</span></span>

<span data-ttu-id="ee3f3-120">在模型產生器中，您必須選取一個案例。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-120">In Model Builder, you need to select a scenario.</span></span> <span data-ttu-id="ee3f3-121">案例的類型取決於您嘗試進行的預測類型。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-121">The type of scenario depends on what type of prediction you are trying to make.</span></span>

#### <a name="predict-a-category-when-there-are-only-two-categories"></a><span data-ttu-id="ee3f3-122">預測類別 (當只有兩個類別時)</span><span class="sxs-lookup"><span data-stu-id="ee3f3-122">Predict a category (when there are only two categories)</span></span>

<span data-ttu-id="ee3f3-123">二元分類用來將資料分類為兩個類別 (是/否、通過/失敗、true/false、正/負)。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-123">Binary classification is used to categorize data into two categories (yes/no; pass/fail; true/false; positive/negative).</span></span>

![顯示二元分類範例的圖表，包括詐騙偵測、風險降低和應用程式檢測](media/binary-classification-examples.png)

<span data-ttu-id="ee3f3-125">情感分析可用來預測客戶意見反應的正面或負面人氣。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-125">Sentiment analysis can be used to predict positive or negative sentiment of customer feedback.</span></span> <span data-ttu-id="ee3f3-126">這是二元分類機器學習工作的範例。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-126">It is an example of the binary classification machine learning task.</span></span>

<span data-ttu-id="ee3f3-127">如果您的案例需要分類成兩種類別，您可以使用此範本處理您的資料集。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-127">If your scenario requires classification into two categories, you can use this template with your own dataset.</span></span>

#### <a name="predict-a-category-when-there-are-three-or-more-categories"></a><span data-ttu-id="ee3f3-128">預測類別 (當有三個或多個類別時)</span><span class="sxs-lookup"><span data-stu-id="ee3f3-128">Predict a category (when there are three or more categories)</span></span>

<span data-ttu-id="ee3f3-129">多元分類可用來將資料分類為三或多個類別。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-129">Multiclass classification can be used to categorize data into three or more classes.</span></span>

![多元分類的範例，包括文件和產品分類、支援票證路由，以及客戶問題優先順序](media/multiclass-classification-examples.png)

<span data-ttu-id="ee3f3-131">問題分類可使用問題標題和描述來分類客戶意見反應問題 (例如，針對 GitHub)。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-131">Issue classification can be used to categorize customer feedback (for example, on GitHub) issues using the issue title and description.</span></span> <span data-ttu-id="ee3f3-132">這是多類別分類機器學習工作的範例。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-132">It is an example of the multi-class classification machine learning task.</span></span>

<span data-ttu-id="ee3f3-133">如果您想要將資料分類為三或多個類別，您可以使用問題分類範本處理您的案例。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-133">You can use the issue classification template for your scenario if you want to categorize data into three or more categories.</span></span>

#### <a name="predict-a-number"></a><span data-ttu-id="ee3f3-134">預測數字</span><span class="sxs-lookup"><span data-stu-id="ee3f3-134">Predict a number</span></span>

<span data-ttu-id="ee3f3-135">迴歸用來預測數字。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-135">Regression is used to predict numbers.</span></span>

![顯示迴歸範例的圖表，例如價格預測、銷售預測和預測性維護](media/regression-examples.png)

<span data-ttu-id="ee3f3-137">價格預測可使用位置、大小和其他房屋特性來預測房價。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-137">Price prediction can be used to predict house prices using location, size, and other characteristics of the house.</span></span> <span data-ttu-id="ee3f3-138">這是回歸機器學習工作的範例。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-138">It is an example of the regression machine learning task.</span></span>

<span data-ttu-id="ee3f3-139">如果您想要使用自己的資料集來預測數值，針對您的案例您可以使用價格預測範本。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-139">You can use the price prediction template for your scenario if you want to predict a numerical value with your own dataset.</span></span>

#### <a name="classify-images-into-categories"></a><span data-ttu-id="ee3f3-140">將影像分類為類別</span><span class="sxs-lookup"><span data-stu-id="ee3f3-140">Classify images into categories</span></span>

<span data-ttu-id="ee3f3-141">這種情況是多元分類的特殊案例，其中要分類的輸入資料是一組影像。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-141">This scenario is a special case of multiclass classification, where the input data to be categorized is a set of images.</span></span>

<span data-ttu-id="ee3f3-142">影像分類可以用來識別不同類別目錄的影像。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-142">Image classification can be used to identify images of different categories.</span></span> <span data-ttu-id="ee3f3-143">例如，不同類型的地形或動物或製造瑕疵。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-143">For example, different types of terrain or animals or manufacturing defects.</span></span>

<span data-ttu-id="ee3f3-144">如果您有一組影像，而且想要將影像分類成不同的類別，您可以將影像分類範本用於您的案例。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-144">You can use the image classification template for your scenario if you have a set of images, and you want to classify the images into different categories.</span></span>

#### <a name="custom-scenario"></a><span data-ttu-id="ee3f3-145">自訂案例</span><span class="sxs-lookup"><span data-stu-id="ee3f3-145">Custom scenario</span></span>

<span data-ttu-id="ee3f3-146">自訂案例可讓您手動選擇您的案例。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-146">The custom scenario allows you to manually choose your scenario.</span></span>

## <a name="data"></a><span data-ttu-id="ee3f3-147">Data</span><span class="sxs-lookup"><span data-stu-id="ee3f3-147">Data</span></span>

<span data-ttu-id="ee3f3-148">一旦您選擇了案例，模型產生器就會要求您提供資料集。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-148">Once you have chosen your scenario, Model Builder asks you to provide a dataset.</span></span> <span data-ttu-id="ee3f3-149">資料用來定型、評估及選擇最適合您案例的模型。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-149">The data is used to train, evaluate, and choose the best model for your scenario.</span></span>

![顯示模型建立器步驟的圖表](media/model-builder-steps.png)

<span data-ttu-id="ee3f3-151">模型產生器支援 tsv、.csv、.txt 格式的資料集，以及 SQL database 格式。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-151">Model Builder supports datasets in .tsv, .csv, .txt formats, as well as SQL database format.</span></span> <span data-ttu-id="ee3f3-152">如果您有 .txt 檔案，則應該以 `,`、`;` 或 `/t` 來分隔資料行，而且該檔案必須有標題列。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-152">If you have a .txt file, columns should be separated with `,`, `;` or `/t` and the file must have a header row.</span></span>

<span data-ttu-id="ee3f3-153">如果資料集是由影像所組成，支援的檔案類型會 `.jpg` 並 `.png`。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-153">If the dataset is made up of images, the supported file types are `.jpg` and `.png`.</span></span>

<span data-ttu-id="ee3f3-154">如需詳細資訊，請參閱將[定型資料載入模型](how-to-guides/load-data-model-builder.md)產生器。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-154">For more information, see [Load training data into Model Builder](how-to-guides/load-data-model-builder.md).</span></span>

### <a name="choose-the-output-to-predict-label"></a><span data-ttu-id="ee3f3-155">選擇要預測的輸出 (標籤)</span><span class="sxs-lookup"><span data-stu-id="ee3f3-155">Choose the output to predict (label)</span></span>

<span data-ttu-id="ee3f3-156">資料集是定型範例資料列和屬性資料行的資料表。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-156">A dataset is a table of rows of training examples, and columns of attributes.</span></span> <span data-ttu-id="ee3f3-157">每個資料列都有：</span><span class="sxs-lookup"><span data-stu-id="ee3f3-157">Each row has:</span></span>

- <span data-ttu-id="ee3f3-158">**標籤** (您想要預測的屬性)</span><span class="sxs-lookup"><span data-stu-id="ee3f3-158">a **label** (the attribute that you want to predict)</span></span>
- <span data-ttu-id="ee3f3-159">**特性** (作為輸入用來預測標籤的屬性)。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-159">**features** (attributes that are used as inputs to predict the label).</span></span>

<span data-ttu-id="ee3f3-160">針對房價預測案例，可能的特性為：</span><span class="sxs-lookup"><span data-stu-id="ee3f3-160">For the house-price prediction scenario, the features could be:</span></span>

- <span data-ttu-id="ee3f3-161">房屋的坪數</span><span class="sxs-lookup"><span data-stu-id="ee3f3-161">the square footage of the house</span></span>
- <span data-ttu-id="ee3f3-162">房間和衛浴數量</span><span class="sxs-lookup"><span data-stu-id="ee3f3-162">the number of bedrooms and bathrooms</span></span>
- <span data-ttu-id="ee3f3-163">郵遞區號</span><span class="sxs-lookup"><span data-stu-id="ee3f3-163">the zip code</span></span>

<span data-ttu-id="ee3f3-164">標籤是坪數列、房間和衛浴值，以及郵遞區號資料列的歷史房價。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-164">The label is the historical house price for that row of square footage, bedroom, and bathroom values and zip code.</span></span>

![資料表顯示房價資料的資料列和資料行，具有大小、房間數、郵遞區號和價格標籤組成的特性](media/model-builder-data.png)

### <a name="example-datasets"></a><span data-ttu-id="ee3f3-166">範例資料集</span><span class="sxs-lookup"><span data-stu-id="ee3f3-166">Example datasets</span></span>

<span data-ttu-id="ee3f3-167">如果您還沒有自己的資料，請嘗試下列資料集之一：</span><span class="sxs-lookup"><span data-stu-id="ee3f3-167">If you don't have your own data yet, try out one of these datasets:</span></span>

|<span data-ttu-id="ee3f3-168">情節</span><span class="sxs-lookup"><span data-stu-id="ee3f3-168">Scenario</span></span>|<span data-ttu-id="ee3f3-169">ML 工作</span><span class="sxs-lookup"><span data-stu-id="ee3f3-169">ML task</span></span>|<span data-ttu-id="ee3f3-170">Data</span><span class="sxs-lookup"><span data-stu-id="ee3f3-170">Data</span></span>|<span data-ttu-id="ee3f3-171">ThisAddIn</span><span class="sxs-lookup"><span data-stu-id="ee3f3-171">Label</span></span>|<span data-ttu-id="ee3f3-172">功能</span><span class="sxs-lookup"><span data-stu-id="ee3f3-172">Features</span></span>|
|-|-|-|-|-|
|<span data-ttu-id="ee3f3-173">價格預測</span><span class="sxs-lookup"><span data-stu-id="ee3f3-173">Price prediction</span></span>|<span data-ttu-id="ee3f3-174">迴歸</span><span class="sxs-lookup"><span data-stu-id="ee3f3-174">regression</span></span>|[<span data-ttu-id="ee3f3-175">計程車費用資料</span><span class="sxs-lookup"><span data-stu-id="ee3f3-175">taxi fare data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|<span data-ttu-id="ee3f3-176">費用</span><span class="sxs-lookup"><span data-stu-id="ee3f3-176">Fare</span></span>|<span data-ttu-id="ee3f3-177">行車時間、距離</span><span class="sxs-lookup"><span data-stu-id="ee3f3-177">Trip time, distance</span></span>|
|<span data-ttu-id="ee3f3-178">異常偵測</span><span class="sxs-lookup"><span data-stu-id="ee3f3-178">Anomaly detection</span></span>|<span data-ttu-id="ee3f3-179">二進位分類</span><span class="sxs-lookup"><span data-stu-id="ee3f3-179">binary classification</span></span>|[<span data-ttu-id="ee3f3-180">產品銷售資料</span><span class="sxs-lookup"><span data-stu-id="ee3f3-180">product sales data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|<span data-ttu-id="ee3f3-181">產品銷售</span><span class="sxs-lookup"><span data-stu-id="ee3f3-181">Product Sales</span></span>|<span data-ttu-id="ee3f3-182">月份</span><span class="sxs-lookup"><span data-stu-id="ee3f3-182">Month</span></span>|
|<span data-ttu-id="ee3f3-183">情緒分析</span><span class="sxs-lookup"><span data-stu-id="ee3f3-183">Sentiment analysis</span></span>|<span data-ttu-id="ee3f3-184">二進位分類</span><span class="sxs-lookup"><span data-stu-id="ee3f3-184">binary classification</span></span>|[<span data-ttu-id="ee3f3-185">網站留言資料</span><span class="sxs-lookup"><span data-stu-id="ee3f3-185">website comment data</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|<span data-ttu-id="ee3f3-186">標籤 (負面人氣時為 0，正面人氣時為 1)</span><span class="sxs-lookup"><span data-stu-id="ee3f3-186">Label (0 when negative sentiment, 1 when positive)</span></span>|<span data-ttu-id="ee3f3-187">留言、年度</span><span class="sxs-lookup"><span data-stu-id="ee3f3-187">Comment, Year</span></span>|
|<span data-ttu-id="ee3f3-188">詐騙偵測</span><span class="sxs-lookup"><span data-stu-id="ee3f3-188">Fraud detection</span></span>|<span data-ttu-id="ee3f3-189">二進位分類</span><span class="sxs-lookup"><span data-stu-id="ee3f3-189">binary classification</span></span>|[<span data-ttu-id="ee3f3-190">信用卡資料</span><span class="sxs-lookup"><span data-stu-id="ee3f3-190">credit card data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|<span data-ttu-id="ee3f3-191">類別 (詐騙時為 1，否則為 0)</span><span class="sxs-lookup"><span data-stu-id="ee3f3-191">Class (1 when fraudulent, 0 otherwise)</span></span>|<span data-ttu-id="ee3f3-192">數量、V1-V28 (匿名特性)</span><span class="sxs-lookup"><span data-stu-id="ee3f3-192">Amount, V1-V28 (anonymized features)</span></span>|
|<span data-ttu-id="ee3f3-193">文字分類</span><span class="sxs-lookup"><span data-stu-id="ee3f3-193">Text classification</span></span>|<span data-ttu-id="ee3f3-194">多元分類</span><span class="sxs-lookup"><span data-stu-id="ee3f3-194">multiclass classification</span></span>|[<span data-ttu-id="ee3f3-195">GitHub 問題資料</span><span class="sxs-lookup"><span data-stu-id="ee3f3-195">GitHub issue data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|<span data-ttu-id="ee3f3-196">區域圖</span><span class="sxs-lookup"><span data-stu-id="ee3f3-196">Area</span></span>|<span data-ttu-id="ee3f3-197">標題、描述</span><span class="sxs-lookup"><span data-stu-id="ee3f3-197">Title, Description</span></span>|
|<span data-ttu-id="ee3f3-198">影像分類</span><span class="sxs-lookup"><span data-stu-id="ee3f3-198">Image classification</span></span>|<span data-ttu-id="ee3f3-199">多元分類</span><span class="sxs-lookup"><span data-stu-id="ee3f3-199">multiclass classification</span></span>|[<span data-ttu-id="ee3f3-200">花卉影像</span><span class="sxs-lookup"><span data-stu-id="ee3f3-200">Flowers images</span></span>](http://download.tensorflow.org/example_images/flower_photos.tgz)|<span data-ttu-id="ee3f3-201">花卉的類型：雛菊、dandelion、玫瑰、sunflowers、tulips</span><span class="sxs-lookup"><span data-stu-id="ee3f3-201">The type of flower: daisy, dandelion, roses, sunflowers, tulips</span></span>|<span data-ttu-id="ee3f3-202">影像資料本身</span><span class="sxs-lookup"><span data-stu-id="ee3f3-202">The image data itself</span></span>|

## <a name="train"></a><span data-ttu-id="ee3f3-203">訓練</span><span class="sxs-lookup"><span data-stu-id="ee3f3-203">Train</span></span>

<span data-ttu-id="ee3f3-204">一旦選取案例、資料和標籤，模型建立器就會定型模型。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-204">Once you select your scenario, data, and label, Model Builder trains the model.</span></span>

### <a name="what-is-training"></a><span data-ttu-id="ee3f3-205">什麼是定型？</span><span class="sxs-lookup"><span data-stu-id="ee3f3-205">What is training?</span></span>

<span data-ttu-id="ee3f3-206">定型模型建立器用來教導模型如何回答案例問題的自動化程序。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-206">Training is an automatic process by which Model Builder teaches your model how to answer questions for your scenario.</span></span> <span data-ttu-id="ee3f3-207">一旦定型，模型就可以使用之前未見過的輸入資料來建立預測。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-207">Once trained, your model can make predictions with input data that it has not seen before.</span></span> <span data-ttu-id="ee3f3-208">例如，如果您要預測房價且有新屋上市，您就可以預測其銷售價格。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-208">For example, if you are predicting house prices and a new house comes on the market, you can predict its sale price.</span></span>

<span data-ttu-id="ee3f3-209">因為模型建立器使用自動化的機器學習服務 (AutoML)，所以它不需要任何輸入，也不需要您在定型期間調整。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-209">Because Model Builder uses automated machine learning (AutoML), it does not require any input or tuning from you during training.</span></span>

### <a name="how-long-should-i-train-for"></a><span data-ttu-id="ee3f3-210">定型時間應該多長？</span><span class="sxs-lookup"><span data-stu-id="ee3f3-210">How long should I train for?</span></span>

<span data-ttu-id="ee3f3-211">模型產生器會使用 AutoML 來探索多個模型，以找出最佳的執行模型。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-211">Model Builder uses AutoML to explore multiple models to find you the best performing model.</span></span>

<span data-ttu-id="ee3f3-212">較長的定型期間可讓 AutoML 探索更多具有更廣泛設定的模型。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-212">Longer training periods allow AutoML to explore more models with a wider range of settings.</span></span>

<span data-ttu-id="ee3f3-213">下表摘要說明在本機電腦上取得一組範例資料集良好效能所花費的平均時間。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-213">The table below summarizes the average time taken to get good performance for a suite of example datasets, on a local machine.</span></span>

|<span data-ttu-id="ee3f3-214">資料集大小</span><span class="sxs-lookup"><span data-stu-id="ee3f3-214">Dataset size</span></span>|<span data-ttu-id="ee3f3-215">定型的平均時間</span><span class="sxs-lookup"><span data-stu-id="ee3f3-215">Average time to train</span></span>|
|------------|---------------------|
|<span data-ttu-id="ee3f3-216">0-10 MB</span><span class="sxs-lookup"><span data-stu-id="ee3f3-216">0 - 10 MB</span></span>|<span data-ttu-id="ee3f3-217">10 秒</span><span class="sxs-lookup"><span data-stu-id="ee3f3-217">10 sec</span></span>|
|<span data-ttu-id="ee3f3-218">10-100 MB</span><span class="sxs-lookup"><span data-stu-id="ee3f3-218">10 - 100 MB</span></span>|<span data-ttu-id="ee3f3-219">10 分鐘</span><span class="sxs-lookup"><span data-stu-id="ee3f3-219">10 min</span></span>|
|<span data-ttu-id="ee3f3-220">100-500 MB</span><span class="sxs-lookup"><span data-stu-id="ee3f3-220">100 - 500 MB</span></span>|<span data-ttu-id="ee3f3-221">30 分鐘</span><span class="sxs-lookup"><span data-stu-id="ee3f3-221">30 min</span></span>|
|<span data-ttu-id="ee3f3-222">500-1 GB</span><span class="sxs-lookup"><span data-stu-id="ee3f3-222">500 - 1 GB</span></span>|<span data-ttu-id="ee3f3-223">60 分鐘</span><span class="sxs-lookup"><span data-stu-id="ee3f3-223">60 min</span></span>|
|<span data-ttu-id="ee3f3-224">1 GB +</span><span class="sxs-lookup"><span data-stu-id="ee3f3-224">1 GB+</span></span>|<span data-ttu-id="ee3f3-225">3 + 小時</span><span class="sxs-lookup"><span data-stu-id="ee3f3-225">3+ hours</span></span>|

<span data-ttu-id="ee3f3-226">這些數位只是指南。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-226">These numbers are a guide only.</span></span> <span data-ttu-id="ee3f3-227">確切的訓練長度取決於：</span><span class="sxs-lookup"><span data-stu-id="ee3f3-227">The exact length of training is dependent on:</span></span>

- <span data-ttu-id="ee3f3-228">當做模型輸入使用的特徵（資料行）數目</span><span class="sxs-lookup"><span data-stu-id="ee3f3-228">the number of features (columns) being used to as input to the model</span></span>
- <span data-ttu-id="ee3f3-229">資料行的類型</span><span class="sxs-lookup"><span data-stu-id="ee3f3-229">the type of columns</span></span>
- <span data-ttu-id="ee3f3-230">ML 工作</span><span class="sxs-lookup"><span data-stu-id="ee3f3-230">the ML task</span></span>
- <span data-ttu-id="ee3f3-231">用於定型之電腦的 CPU、磁片和記憶體效能</span><span class="sxs-lookup"><span data-stu-id="ee3f3-231">the CPU, disk and memory performance of the machine used for training</span></span>

## <a name="evaluate"></a><span data-ttu-id="ee3f3-232">評估</span><span class="sxs-lookup"><span data-stu-id="ee3f3-232">Evaluate</span></span>

<span data-ttu-id="ee3f3-233">評估是測量模型良好程度的程式。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-233">Evaluation is the process of measuring how good your model is.</span></span> <span data-ttu-id="ee3f3-234">「模型產生器」會使用定型的模型，以新的測試資料進行預測，然後測量預測的良好程度。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-234">Model Builder uses the trained model to make predictions with new test data, and then measures how good the predictions are.</span></span>

<span data-ttu-id="ee3f3-235">模型建立器會將定型資料分割為定型集和測試集。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-235">Model Builder splits the training data into a training set and a test set.</span></span> <span data-ttu-id="ee3f3-236">定型資料 (80%) 用來定型模型，而測試資料 (20%) 則保留用於評估模型。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-236">The training data (80%) is used to train your model and the test data (20%) is held back to evaluate your model.</span></span> 

### <a name="how-do-i-understand-my-model-performance"></a><span data-ttu-id="ee3f3-237">如何? 瞭解我的模型效能嗎？</span><span class="sxs-lookup"><span data-stu-id="ee3f3-237">How do I understand my model performance?</span></span>

<span data-ttu-id="ee3f3-238">案例會對應至機器學習工作。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-238">A scenario maps to a machine learning task.</span></span> <span data-ttu-id="ee3f3-239">每個 ML 工作都有自己的一組評估計量。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-239">Each ML task has its own set of evaluation metrics.</span></span>

#### <a name="regression-for-example-price-prediction"></a><span data-ttu-id="ee3f3-240">回歸（例如，價格預測）</span><span class="sxs-lookup"><span data-stu-id="ee3f3-240">Regression (for example, Price Prediction)</span></span>

<span data-ttu-id="ee3f3-241">回歸問題的預設度量是 RSquared，RSquared 的值範圍介於0到1之間。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-241">The default metric for regression problems is RSquared, the value of RSquared ranges between 0 and 1.</span></span> <span data-ttu-id="ee3f3-242">1是最佳的可能值，換句話說，RSquared 到1的值愈接近您的模型所執行的效果。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-242">1 is the best possible value or in other words the closer the value of RSquared to 1 the better your model is performing.</span></span>

<span data-ttu-id="ee3f3-243">其他回報的計量（例如絕對遺失、遺失平方和 RMS 遺失）是額外的計量，可用來瞭解模型的執行方式，並將其與其他回歸模型做比較。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-243">Other metrics reported such as absolute-loss, squared-loss, and RMS loss are additional metrics, which can be used to understand how your model is performing and comparing it against other regression models.</span></span>

#### <a name="binary-classification-for-example-sentiment-analysis"></a><span data-ttu-id="ee3f3-244">二元分類（例如，情感分析）</span><span class="sxs-lookup"><span data-stu-id="ee3f3-244">Binary Classification (for example, Sentiment Analysis)</span></span>

<span data-ttu-id="ee3f3-245">分類問題的預設度量是精確度。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-245">The default metric for classification problems is accuracy.</span></span> <span data-ttu-id="ee3f3-246">精確度會定義您的模型在測試資料集上所進行的正確預測比例。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-246">Accuracy defines the proportion of correct predictions your model is making over the test dataset.</span></span> <span data-ttu-id="ee3f3-247">接近100% 或1.0 的效果愈佳。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-247">The closer to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="ee3f3-248">其他回報的計量，例如 AUC （曲線下的區域），其會測量真肯定的比率與錯誤的正面比率，應大於0.50，才能接受模型。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-248">Other metrics reported such as AUC (Area under the curve), which measures the true positive rate vs. the false positive rate should be greater than 0.50 for models to be acceptable.</span></span>

<span data-ttu-id="ee3f3-249">如 F1 分數等其他計量，可以用來控制精確度和召回率之間的平衡。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-249">Additional metrics like F1 score can be used to control the balance between Precision and Recall.</span></span>

#### <a name="multi-class-classification-for-example-issue-classification-image-classification"></a><span data-ttu-id="ee3f3-250">多類別分類（例如，問題分類、影像分類）</span><span class="sxs-lookup"><span data-stu-id="ee3f3-250">Multi-Class Classification (for example, Issue Classification, Image Classification)</span></span>

<span data-ttu-id="ee3f3-251">多類別分類的預設度量是微精確度。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-251">The default metric for Multi-class classification is Micro Accuracy.</span></span> <span data-ttu-id="ee3f3-252">越接近100% 或1.0 的微準確度越好。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-252">The closer the Micro Accuracy to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="ee3f3-253">多類別分類的另一個重要計量是「宏精確度」，類似于較接近1.0 的微準確度。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-253">Another important metric for Multi-class classification is Macro-accuracy, similar to Micro-accuracy the closer to 1.0 the better it is.</span></span> <span data-ttu-id="ee3f3-254">有一個很好的方法可以考慮這兩種類型的精確度，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ee3f3-254">A good way to think about these two types of accuracy is:</span></span>

- <span data-ttu-id="ee3f3-255">微精確度：傳入票證分類到正確小組的頻率為何？</span><span class="sxs-lookup"><span data-stu-id="ee3f3-255">Micro-accuracy: How often does an incoming ticket get classified to the right team?</span></span>
- <span data-ttu-id="ee3f3-256">宏-精確度：對於平均小組而言，其小組的傳入票證正確的頻率為何？</span><span class="sxs-lookup"><span data-stu-id="ee3f3-256">Macro-accuracy: For an average team, how often is an incoming ticket correct for their team?</span></span>

### <a name="more-information-on-evaluation-metrics"></a><span data-ttu-id="ee3f3-257">評估計量的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="ee3f3-257">More information on evaluation metrics</span></span>

<span data-ttu-id="ee3f3-258">如需詳細資訊，請參閱[模型評估計量](resources/metrics.md)。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-258">For more information, see [model evaluation metrics](resources/metrics.md).</span></span>

## <a name="improve"></a><span data-ttu-id="ee3f3-259">改善</span><span class="sxs-lookup"><span data-stu-id="ee3f3-259">Improve</span></span>

<span data-ttu-id="ee3f3-260">如果您的模型效能分數不如預期，您可以：</span><span class="sxs-lookup"><span data-stu-id="ee3f3-260">If your model performance score is not as good as you want it to be, you can:</span></span>

- <span data-ttu-id="ee3f3-261">延長定型時間。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-261">Train for a longer period of time.</span></span> <span data-ttu-id="ee3f3-262">時間較長，自動化的機器學習引擎就會嘗試更多演算法及設定。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-262">With more time, the automated machine learning engine to try more algorithms and settings.</span></span>

- <span data-ttu-id="ee3f3-263">新增更多資料。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-263">Add more data.</span></span> <span data-ttu-id="ee3f3-264">有時資料數量不足，無法定型高品質的機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-264">Sometimes the amount of data is not sufficient to train a high-quality machine learning model.</span></span>

- <span data-ttu-id="ee3f3-265">平衡資料。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-265">Balance your data.</span></span> <span data-ttu-id="ee3f3-266">針對分類工作，請務必平衡所有類別的定型集。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-266">For classification tasks, make sure that the training set is balanced across the categories.</span></span> <span data-ttu-id="ee3f3-267">例如，如果您有四個類別的 100 個定型範例，有 90 筆記錄使用前兩個類別 (tag1 和 tag2)，只有剩餘的 10 筆記錄使用其他兩個類別 (tag3 和 tag4)，則資料失衡可能會導致模型難以正確預測 tag3 或 tag4。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-267">For example, if you have four classes for 100 training examples, and the two first classes (tag1 and tag2) are used for 90 records, but the other two (tag3 and tag4) are only used on the remaining 10 records, the lack of balanced data may cause your model to struggle to correctly predict tag3 or tag4.</span></span>

## <a name="code"></a><span data-ttu-id="ee3f3-268">程式碼</span><span class="sxs-lookup"><span data-stu-id="ee3f3-268">Code</span></span>

<span data-ttu-id="ee3f3-269">在評估階段後，模型建立器會輸出模型檔案，以及可用來將模型新增至應用程式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-269">After the evaluation phase, Model Builder outputs a model file, and code that you can use to add the model to your application.</span></span> <span data-ttu-id="ee3f3-270">ML.NET 模型會儲存為 ZIP 檔案。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-270">ML.NET models are saved as a zip file.</span></span> <span data-ttu-id="ee3f3-271">載入並使用模型的程式碼會新增為解決方案中新專案。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-271">The code to load and use your model is added as a new project in your solution.</span></span> <span data-ttu-id="ee3f3-272">模型建立器也會新增範例主控台應用程式，您可以執行它以查看運行的模型。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-272">Model Builder also adds a sample console app that you can run to see your model in action.</span></span>

<span data-ttu-id="ee3f3-273">此外，模型建立器會輸出產生模型的程式碼，以便您可以了解產生模型所用的步驟。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-273">In addition, Model Builder outputs the code that generated the model, so that you can understand the steps used to generate the model.</span></span> <span data-ttu-id="ee3f3-274">您也可以使用模型定型程式碼以新資料重新定型模型。</span><span class="sxs-lookup"><span data-stu-id="ee3f3-274">You can also use the model training code to retrain your model with new data.</span></span>

## <a name="whats-next"></a><span data-ttu-id="ee3f3-275">後續步驟</span><span class="sxs-lookup"><span data-stu-id="ee3f3-275">What's next?</span></span>

<span data-ttu-id="ee3f3-276">[安裝](how-to-guides/install-model-builder.md)模型建立器 Visual Studio 延伸模組</span><span class="sxs-lookup"><span data-stu-id="ee3f3-276">[Install](how-to-guides/install-model-builder.md) the Model Builder Visual Studio extension</span></span>

<span data-ttu-id="ee3f3-277">請嘗試[價格預測或任何迴歸案例](tutorials/predict-prices-with-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="ee3f3-277">Try [price prediction or any regression scenario](tutorials/predict-prices-with-model-builder.md)</span></span>
