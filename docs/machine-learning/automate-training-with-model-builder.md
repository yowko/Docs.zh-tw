---
title: 什麼是模型建立器且其如何運作？
description: 如何使用 ML.NET 模型建立器來自動定型機器學習服務模型
ms.date: 06/01/2020
ms.custom: overview, mlnet-tooling
ms.openlocfilehash: 80f5f5d064c4e0c4097dacc6022d4624c1516ab9
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679673"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a><span data-ttu-id="bb21a-103">什麼是模型建立器且其如何運作？</span><span class="sxs-lookup"><span data-stu-id="bb21a-103">What is Model Builder and how does it work?</span></span>

<span data-ttu-id="bb21a-104">ML.NET 模型建立器是直覺式圖形化 Visual Studio 延伸模組，其用於建置、定型和部署自訂機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="bb21a-104">ML.NET Model Builder is an intuitive graphical Visual Studio extension to build, train, and deploy custom machine learning models.</span></span>

<span data-ttu-id="bb21a-105">模型建立器會使用自動化的機器學習服務 (AutoML) 來探索不同機器學習服務演算法和設定，協助您找出最適合您案例的組合。</span><span class="sxs-lookup"><span data-stu-id="bb21a-105">Model Builder uses automated machine learning (AutoML) to explore different machine learning algorithms and settings to help you find the one that best suits your scenario.</span></span>

<span data-ttu-id="bb21a-106">您不需要有機器學習專業知識也能使用模型建立器。</span><span class="sxs-lookup"><span data-stu-id="bb21a-106">You don't need machine learning expertise to use Model Builder.</span></span> <span data-ttu-id="bb21a-107">您只需要一些資料和待解決的問題。</span><span class="sxs-lookup"><span data-stu-id="bb21a-107">All you need is some data, and a problem to solve.</span></span> <span data-ttu-id="bb21a-108">模型建立器會產生程式碼，將模型新增至您的 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="bb21a-108">Model Builder generates the code to add the model to your .NET application.</span></span>

![模型建立器 Visual Studio 延伸模組使用者介面動畫](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> <span data-ttu-id="bb21a-110">模型產生器目前為預覽版。</span><span class="sxs-lookup"><span data-stu-id="bb21a-110">Model Builder is currently in Preview.</span></span>

## <a name="scenario"></a><span data-ttu-id="bb21a-111">狀況</span><span class="sxs-lookup"><span data-stu-id="bb21a-111">Scenario</span></span>

<span data-ttu-id="bb21a-112">您可以在模型建立器中放入許多不同的案例，以產生應用程式的機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="bb21a-112">You can bring many different scenarios to Model Builder, to generate a machine learning model for your application.</span></span>

<span data-ttu-id="bb21a-113">案例是您想要使用資料進行的預測類型描述。</span><span class="sxs-lookup"><span data-stu-id="bb21a-113">A scenario is a description of the type of prediction you want to make using your data.</span></span> <span data-ttu-id="bb21a-114">例如：</span><span class="sxs-lookup"><span data-stu-id="bb21a-114">For example:</span></span>

- <span data-ttu-id="bb21a-115">根據歷史銷售資料預測未來的產品銷售量</span><span class="sxs-lookup"><span data-stu-id="bb21a-115">predict future product sales volume based on historical sales data</span></span>
- <span data-ttu-id="bb21a-116">根據客戶評論將人氣分類為正面或負面</span><span class="sxs-lookup"><span data-stu-id="bb21a-116">classify sentiments as positive or negative based on customer reviews</span></span>
- <span data-ttu-id="bb21a-117">偵測銀行交易是否為詐騙</span><span class="sxs-lookup"><span data-stu-id="bb21a-117">detect whether a banking transaction is fraudulent</span></span>
- <span data-ttu-id="bb21a-118">將客戶意見反應問題路由至公司的正確小組</span><span class="sxs-lookup"><span data-stu-id="bb21a-118">route customer feedback issues to the correct team in your company</span></span>

### <a name="which-machine-learning-scenario-is-right-for-me"></a><span data-ttu-id="bb21a-119">哪種機器學習服務案例適合我？</span><span class="sxs-lookup"><span data-stu-id="bb21a-119">Which machine learning scenario is right for me?</span></span>

<span data-ttu-id="bb21a-120">在模型產生器中，您需要選取案例。</span><span class="sxs-lookup"><span data-stu-id="bb21a-120">In Model Builder, you need to select a scenario.</span></span> <span data-ttu-id="bb21a-121">案例的類型取決於您嘗試進行的預測類型。</span><span class="sxs-lookup"><span data-stu-id="bb21a-121">The type of scenario depends on what type of prediction you are trying to make.</span></span>

#### <a name="text-classification"></a><span data-ttu-id="bb21a-122">文字分類</span><span class="sxs-lookup"><span data-stu-id="bb21a-122">Text classification</span></span>

<span data-ttu-id="bb21a-123">分類是用來將資料分類為類別。</span><span class="sxs-lookup"><span data-stu-id="bb21a-123">Classification is used to categorize data into categories.</span></span>

![顯示二元分類範例的圖表，包括詐騙偵測、風險降低和應用程式檢測](media/binary-classification-examples.png)

![多元分類的範例，包括文件和產品分類、支援票證路由，以及客戶問題優先順序](media/multiclass-classification-examples.png)

#### <a name="value-prediction"></a><span data-ttu-id="bb21a-126">值預測</span><span class="sxs-lookup"><span data-stu-id="bb21a-126">Value prediction</span></span>

<span data-ttu-id="bb21a-127">迴歸用來預測數字。</span><span class="sxs-lookup"><span data-stu-id="bb21a-127">Regression is used to predict numbers.</span></span>

![顯示迴歸範例的圖表，例如價格預測、銷售預測和預測性維護](media/regression-examples.png)

#### <a name="image-classification"></a><span data-ttu-id="bb21a-129">影像分類</span><span class="sxs-lookup"><span data-stu-id="bb21a-129">Image classification</span></span>

<span data-ttu-id="bb21a-130">影像分類可以用來識別不同類別的影像。</span><span class="sxs-lookup"><span data-stu-id="bb21a-130">Image classification can be used to identify images of different categories.</span></span> <span data-ttu-id="bb21a-131">例如，不同類型的地形或動物或製造瑕疵。</span><span class="sxs-lookup"><span data-stu-id="bb21a-131">For example, different types of terrain or animals or manufacturing defects.</span></span>

<span data-ttu-id="bb21a-132">如果您有一組影像，而且想要將影像分類成不同的類別，您可以使用影像分類案例。</span><span class="sxs-lookup"><span data-stu-id="bb21a-132">You can use the image classification scenario if you have a set of images, and you want to classify the images into different categories.</span></span>

#### <a name="recommendation"></a><span data-ttu-id="bb21a-133">建議</span><span class="sxs-lookup"><span data-stu-id="bb21a-133">Recommendation</span></span>

<span data-ttu-id="bb21a-134">建議案例會根據其贊和不喜歡與其他使用者的相似程度，來預測特定使用者的建議專案清單。</span><span class="sxs-lookup"><span data-stu-id="bb21a-134">The recommendation scenario predicts a list of suggested items for a particular user, based on how similar their likes and dislikes are to other users'.</span></span>

<span data-ttu-id="bb21a-135">當您有一組使用者和一組「產品」（例如，購買的專案、電影、書籍或電視節目），以及一組使用者的「評等」產品時，您可以使用建議案例。</span><span class="sxs-lookup"><span data-stu-id="bb21a-135">You can use the recommendation scenario when you have a set of users and a set of "products", such as items to purchase, movies, books, or TV shows, along with a set of users' "ratings" of those products.</span></span>

## <a name="environment"></a><span data-ttu-id="bb21a-136">環境</span><span class="sxs-lookup"><span data-stu-id="bb21a-136">Environment</span></span>

<span data-ttu-id="bb21a-137">您可以在本機電腦上或在 Azure 上的雲端中定型您的機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="bb21a-137">You can train your machine learning model locally on your machine or in the cloud on Azure.</span></span>

<span data-ttu-id="bb21a-138">當您在本機定型時，您會在電腦資源的條件約束 (CPU、記憶體和磁片) 。</span><span class="sxs-lookup"><span data-stu-id="bb21a-138">When you train locally, you work within the constraints of your computer resources (CPU, memory, and disk).</span></span> <span data-ttu-id="bb21a-139">當您在雲端中進行定型時，您可以擴大資源以符合您的案例需求，特別是針對大型資料集。</span><span class="sxs-lookup"><span data-stu-id="bb21a-139">When you train in the cloud, you can scale up your resources to meet the demands of your scenario, especially for large datasets.</span></span>

<span data-ttu-id="bb21a-140">所有案例都支援本機定型。</span><span class="sxs-lookup"><span data-stu-id="bb21a-140">Local training is supported for all scenarios.</span></span>

<span data-ttu-id="bb21a-141">影像分類支援 Azure 定型。</span><span class="sxs-lookup"><span data-stu-id="bb21a-141">Azure training is supported for Image Classification.</span></span>

## <a name="data"></a><span data-ttu-id="bb21a-142">資料</span><span class="sxs-lookup"><span data-stu-id="bb21a-142">Data</span></span>

<span data-ttu-id="bb21a-143">一旦您選擇了您的案例，模型建立器會要求您提供資料集。</span><span class="sxs-lookup"><span data-stu-id="bb21a-143">Once you have chosen your scenario, Model Builder asks you to provide a dataset.</span></span> <span data-ttu-id="bb21a-144">資料用來定型、評估及選擇最適合您案例的模型。</span><span class="sxs-lookup"><span data-stu-id="bb21a-144">The data is used to train, evaluate, and choose the best model for your scenario.</span></span>

![顯示模型建立器步驟的圖表](media/model-builder-steps.png)

<span data-ttu-id="bb21a-146">模型產生器支援 tsv、.csv、.txt 格式的資料集，以及 SQL database 格式。</span><span class="sxs-lookup"><span data-stu-id="bb21a-146">Model Builder supports datasets in .tsv, .csv, .txt formats, as well as SQL database format.</span></span> <span data-ttu-id="bb21a-147">如果您有 .txt 檔案，資料行應該與或分隔， `,` `;` 而且檔案 `/t` 必須有標頭資料列。</span><span class="sxs-lookup"><span data-stu-id="bb21a-147">If you have a .txt file, columns should be separated with `,`, `;` or `/t` and the file must have a header row.</span></span>

<span data-ttu-id="bb21a-148">如果資料集是由影像所組成，則支援的檔案類型為 `.jpg` 和 `.png` 。</span><span class="sxs-lookup"><span data-stu-id="bb21a-148">If the dataset is made up of images, the supported file types are `.jpg` and `.png`.</span></span>

<span data-ttu-id="bb21a-149">如需詳細資訊，請參閱將 [定型資料載入模型](how-to-guides/load-data-model-builder.md)產生器。</span><span class="sxs-lookup"><span data-stu-id="bb21a-149">For more information, see [Load training data into Model Builder](how-to-guides/load-data-model-builder.md).</span></span>

### <a name="choose-the-output-to-predict-label"></a><span data-ttu-id="bb21a-150">選擇要預測的輸出 (標籤)</span><span class="sxs-lookup"><span data-stu-id="bb21a-150">Choose the output to predict (label)</span></span>

<span data-ttu-id="bb21a-151">資料集是定型範例資料列和屬性資料行的資料表。</span><span class="sxs-lookup"><span data-stu-id="bb21a-151">A dataset is a table of rows of training examples, and columns of attributes.</span></span> <span data-ttu-id="bb21a-152">每個資料列都有：</span><span class="sxs-lookup"><span data-stu-id="bb21a-152">Each row has:</span></span>

- <span data-ttu-id="bb21a-153">**標籤** (您想要預測的屬性)</span><span class="sxs-lookup"><span data-stu-id="bb21a-153">a **label** (the attribute that you want to predict)</span></span>
- <span data-ttu-id="bb21a-154">**特性** (作為輸入用來預測標籤的屬性)。</span><span class="sxs-lookup"><span data-stu-id="bb21a-154">**features** (attributes that are used as inputs to predict the label).</span></span>

<span data-ttu-id="bb21a-155">針對房價預測案例，可能的特性為：</span><span class="sxs-lookup"><span data-stu-id="bb21a-155">For the house-price prediction scenario, the features could be:</span></span>

- <span data-ttu-id="bb21a-156">房屋的坪數</span><span class="sxs-lookup"><span data-stu-id="bb21a-156">the square footage of the house</span></span>
- <span data-ttu-id="bb21a-157">房間和衛浴數量</span><span class="sxs-lookup"><span data-stu-id="bb21a-157">the number of bedrooms and bathrooms</span></span>
- <span data-ttu-id="bb21a-158">郵遞區號</span><span class="sxs-lookup"><span data-stu-id="bb21a-158">the zip code</span></span>

<span data-ttu-id="bb21a-159">標籤是坪數列、房間和衛浴值，以及郵遞區號資料列的歷史房價。</span><span class="sxs-lookup"><span data-stu-id="bb21a-159">The label is the historical house price for that row of square footage, bedroom, and bathroom values and zip code.</span></span>

![資料表顯示房價資料的資料列和資料行，具有大小、房間數、郵遞區號和價格標籤組成的特性](media/model-builder-data.png)

### <a name="example-datasets"></a><span data-ttu-id="bb21a-161">範例資料集</span><span class="sxs-lookup"><span data-stu-id="bb21a-161">Example datasets</span></span>

<span data-ttu-id="bb21a-162">如果您還沒有自己的資料，請嘗試下列資料集之一：</span><span class="sxs-lookup"><span data-stu-id="bb21a-162">If you don't have your own data yet, try out one of these datasets:</span></span>

|<span data-ttu-id="bb21a-163">狀況</span><span class="sxs-lookup"><span data-stu-id="bb21a-163">Scenario</span></span>|<span data-ttu-id="bb21a-164">範例</span><span class="sxs-lookup"><span data-stu-id="bb21a-164">Example</span></span>|<span data-ttu-id="bb21a-165">資料</span><span class="sxs-lookup"><span data-stu-id="bb21a-165">Data</span></span>|<span data-ttu-id="bb21a-166">標籤</span><span class="sxs-lookup"><span data-stu-id="bb21a-166">Label</span></span>|<span data-ttu-id="bb21a-167">特性</span><span class="sxs-lookup"><span data-stu-id="bb21a-167">Features</span></span>|
|-|-|-|-|-|
|<span data-ttu-id="bb21a-168">分類</span><span class="sxs-lookup"><span data-stu-id="bb21a-168">Classification</span></span>|<span data-ttu-id="bb21a-169">預測銷售異常</span><span class="sxs-lookup"><span data-stu-id="bb21a-169">Predict sales anomalies</span></span>|[<span data-ttu-id="bb21a-170">產品銷售資料</span><span class="sxs-lookup"><span data-stu-id="bb21a-170">product sales data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|<span data-ttu-id="bb21a-171">產品銷售</span><span class="sxs-lookup"><span data-stu-id="bb21a-171">Product Sales</span></span>|<span data-ttu-id="bb21a-172">Month</span><span class="sxs-lookup"><span data-stu-id="bb21a-172">Month</span></span>|
||<span data-ttu-id="bb21a-173">預測網站批註情感</span><span class="sxs-lookup"><span data-stu-id="bb21a-173">Predict sentiment of website comments</span></span>|[<span data-ttu-id="bb21a-174">網站留言資料</span><span class="sxs-lookup"><span data-stu-id="bb21a-174">website comment data</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|<span data-ttu-id="bb21a-175">標籤 (負面人氣時為 0，正面人氣時為 1)</span><span class="sxs-lookup"><span data-stu-id="bb21a-175">Label (0 when negative sentiment, 1 when positive)</span></span>|<span data-ttu-id="bb21a-176">留言、年度</span><span class="sxs-lookup"><span data-stu-id="bb21a-176">Comment, Year</span></span>|
||<span data-ttu-id="bb21a-177">預測詐騙信用卡交易</span><span class="sxs-lookup"><span data-stu-id="bb21a-177">Predict fraudulent credit card transactions</span></span>|[<span data-ttu-id="bb21a-178">信用卡資料</span><span class="sxs-lookup"><span data-stu-id="bb21a-178">credit card data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CCFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|<span data-ttu-id="bb21a-179">類別 (詐騙時為 1，否則為 0)</span><span class="sxs-lookup"><span data-stu-id="bb21a-179">Class (1 when fraudulent, 0 otherwise)</span></span>|<span data-ttu-id="bb21a-180">數量、V1-V28 (匿名特性)</span><span class="sxs-lookup"><span data-stu-id="bb21a-180">Amount, V1-V28 (anonymized features)</span></span>|
||<span data-ttu-id="bb21a-181">在 GitHub 存放庫中預測問題類型</span><span class="sxs-lookup"><span data-stu-id="bb21a-181">Predict the type of issue in a GitHub repository</span></span>|[<span data-ttu-id="bb21a-182">GitHub 問題資料</span><span class="sxs-lookup"><span data-stu-id="bb21a-182">GitHub issue data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|<span data-ttu-id="bb21a-183">區域</span><span class="sxs-lookup"><span data-stu-id="bb21a-183">Area</span></span>|<span data-ttu-id="bb21a-184">標題、描述</span><span class="sxs-lookup"><span data-stu-id="bb21a-184">Title, Description</span></span>|
|<span data-ttu-id="bb21a-185">值預測</span><span class="sxs-lookup"><span data-stu-id="bb21a-185">Value prediction</span></span>|<span data-ttu-id="bb21a-186">預測出租車費用價格</span><span class="sxs-lookup"><span data-stu-id="bb21a-186">Predict taxi fare price</span></span>|[<span data-ttu-id="bb21a-187">計程車費用資料</span><span class="sxs-lookup"><span data-stu-id="bb21a-187">taxi fare data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|<span data-ttu-id="bb21a-188">費用</span><span class="sxs-lookup"><span data-stu-id="bb21a-188">Fare</span></span>|<span data-ttu-id="bb21a-189">行車時間、距離</span><span class="sxs-lookup"><span data-stu-id="bb21a-189">Trip time, distance</span></span>|
|<span data-ttu-id="bb21a-190">影像分類</span><span class="sxs-lookup"><span data-stu-id="bb21a-190">Image classification</span></span>|<span data-ttu-id="bb21a-191">預測花卉的類別</span><span class="sxs-lookup"><span data-stu-id="bb21a-191">Predict the category of a flower</span></span> |[<span data-ttu-id="bb21a-192">花卉影像</span><span class="sxs-lookup"><span data-stu-id="bb21a-192">flower images</span></span>](http://download.tensorflow.org/example_images/flower_photos.tgz)|<span data-ttu-id="bb21a-193">花卉的類型：菊花、dandelion、玫瑰、sunflowers、tulips</span><span class="sxs-lookup"><span data-stu-id="bb21a-193">The type of flower: daisy, dandelion, roses, sunflowers, tulips</span></span>|<span data-ttu-id="bb21a-194">影像資料本身</span><span class="sxs-lookup"><span data-stu-id="bb21a-194">The image data itself</span></span>|
|<span data-ttu-id="bb21a-195">建議</span><span class="sxs-lookup"><span data-stu-id="bb21a-195">Recommendation</span></span>|<span data-ttu-id="bb21a-196">預測某人所喜歡的電影</span><span class="sxs-lookup"><span data-stu-id="bb21a-196">Predict movies that someone will like</span></span>|[<span data-ttu-id="bb21a-197">電影分級</span><span class="sxs-lookup"><span data-stu-id="bb21a-197">movie ratings</span></span>](http://files.grouplens.org/datasets/movielens/ml-latest-small.zip)|<span data-ttu-id="bb21a-198">使用者、電影</span><span class="sxs-lookup"><span data-stu-id="bb21a-198">Users, Movies</span></span>|<span data-ttu-id="bb21a-199">評等</span><span class="sxs-lookup"><span data-stu-id="bb21a-199">Ratings</span></span>|

## <a name="train"></a><span data-ttu-id="bb21a-200">定型</span><span class="sxs-lookup"><span data-stu-id="bb21a-200">Train</span></span>

<span data-ttu-id="bb21a-201">當您選取案例、環境、資料和標籤之後，模型建立器就會訓練模型。</span><span class="sxs-lookup"><span data-stu-id="bb21a-201">Once you select your scenario, environment, data, and label, Model Builder trains the model.</span></span>

### <a name="what-is-training"></a><span data-ttu-id="bb21a-202">什麼是定型？</span><span class="sxs-lookup"><span data-stu-id="bb21a-202">What is training?</span></span>

<span data-ttu-id="bb21a-203">定型模型建立器用來教導模型如何回答案例問題的自動化程序。</span><span class="sxs-lookup"><span data-stu-id="bb21a-203">Training is an automatic process by which Model Builder teaches your model how to answer questions for your scenario.</span></span> <span data-ttu-id="bb21a-204">一旦定型，模型就可以使用之前未見過的輸入資料來建立預測。</span><span class="sxs-lookup"><span data-stu-id="bb21a-204">Once trained, your model can make predictions with input data that it has not seen before.</span></span> <span data-ttu-id="bb21a-205">例如，如果您要預測房價且有新屋上市，您就可以預測其銷售價格。</span><span class="sxs-lookup"><span data-stu-id="bb21a-205">For example, if you are predicting house prices and a new house comes on the market, you can predict its sale price.</span></span>

<span data-ttu-id="bb21a-206">因為模型建立器使用自動化的機器學習服務 (AutoML)，所以它不需要任何輸入，也不需要您在定型期間調整。</span><span class="sxs-lookup"><span data-stu-id="bb21a-206">Because Model Builder uses automated machine learning (AutoML), it does not require any input or tuning from you during training.</span></span>

### <a name="how-long-should-i-train-for"></a><span data-ttu-id="bb21a-207">定型時間應該多長？</span><span class="sxs-lookup"><span data-stu-id="bb21a-207">How long should I train for?</span></span>

<span data-ttu-id="bb21a-208">模型產生器會使用 AutoML 來探索多個模型，以找出效能最佳的模型。</span><span class="sxs-lookup"><span data-stu-id="bb21a-208">Model Builder uses AutoML to explore multiple models to find you the best performing model.</span></span>

<span data-ttu-id="bb21a-209">較長的定型期間可讓 AutoML 使用更廣泛的設定來探索更多模型。</span><span class="sxs-lookup"><span data-stu-id="bb21a-209">Longer training periods allow AutoML to explore more models with a wider range of settings.</span></span>

<span data-ttu-id="bb21a-210">下表摘要說明在本機電腦上取得範例資料集套件的良好效能所花費的平均時間。</span><span class="sxs-lookup"><span data-stu-id="bb21a-210">The table below summarizes the average time taken to get good performance for a suite of example datasets, on a local machine.</span></span>

|<span data-ttu-id="bb21a-211">資料集大小</span><span class="sxs-lookup"><span data-stu-id="bb21a-211">Dataset size</span></span>|<span data-ttu-id="bb21a-212">定型的平均時間</span><span class="sxs-lookup"><span data-stu-id="bb21a-212">Average time to train</span></span>|
|------------|---------------------|
|<span data-ttu-id="bb21a-213">0-10 MB</span><span class="sxs-lookup"><span data-stu-id="bb21a-213">0 - 10 MB</span></span>|<span data-ttu-id="bb21a-214">10 秒</span><span class="sxs-lookup"><span data-stu-id="bb21a-214">10 sec</span></span>|
|<span data-ttu-id="bb21a-215">10-100 MB</span><span class="sxs-lookup"><span data-stu-id="bb21a-215">10 - 100 MB</span></span>|<span data-ttu-id="bb21a-216">10 分鐘</span><span class="sxs-lookup"><span data-stu-id="bb21a-216">10 min</span></span>|
|<span data-ttu-id="bb21a-217">100-500 MB</span><span class="sxs-lookup"><span data-stu-id="bb21a-217">100 - 500 MB</span></span>|<span data-ttu-id="bb21a-218">30 分鐘</span><span class="sxs-lookup"><span data-stu-id="bb21a-218">30 min</span></span>|
|<span data-ttu-id="bb21a-219">500-1 GB</span><span class="sxs-lookup"><span data-stu-id="bb21a-219">500 - 1 GB</span></span>|<span data-ttu-id="bb21a-220">60 分鐘</span><span class="sxs-lookup"><span data-stu-id="bb21a-220">60 min</span></span>|
|<span data-ttu-id="bb21a-221">1 GB +</span><span class="sxs-lookup"><span data-stu-id="bb21a-221">1 GB+</span></span>|<span data-ttu-id="bb21a-222">3小時</span><span class="sxs-lookup"><span data-stu-id="bb21a-222">3+ hours</span></span>|

<span data-ttu-id="bb21a-223">這些數位只是指南。</span><span class="sxs-lookup"><span data-stu-id="bb21a-223">These numbers are a guide only.</span></span> <span data-ttu-id="bb21a-224">定型的確切長度取決於：</span><span class="sxs-lookup"><span data-stu-id="bb21a-224">The exact length of training is dependent on:</span></span>

- <span data-ttu-id="bb21a-225"> (資料行) 用來當做模型輸入的功能數目</span><span class="sxs-lookup"><span data-stu-id="bb21a-225">the number of features (columns) being used to as input to the model</span></span>
- <span data-ttu-id="bb21a-226">資料行的類型</span><span class="sxs-lookup"><span data-stu-id="bb21a-226">the type of columns</span></span>
- <span data-ttu-id="bb21a-227">ML 工作</span><span class="sxs-lookup"><span data-stu-id="bb21a-227">the ML task</span></span>
- <span data-ttu-id="bb21a-228">用於定型之電腦的 CPU、磁片和記憶體效能</span><span class="sxs-lookup"><span data-stu-id="bb21a-228">the CPU, disk, and memory performance of the machine used for training</span></span>

<span data-ttu-id="bb21a-229">通常會建議您使用超過100的資料列做為資料集，但不會產生任何結果，而且可能需要花費很長的時間來定型。</span><span class="sxs-lookup"><span data-stu-id="bb21a-229">It's generally advised that you use more than 100 rows as datasets with less than that may not produce any results and may take a significantly longer time to train.</span></span>

## <a name="evaluate"></a><span data-ttu-id="bb21a-230">評估</span><span class="sxs-lookup"><span data-stu-id="bb21a-230">Evaluate</span></span>

<span data-ttu-id="bb21a-231">評估是測量模型良好程度的流程。</span><span class="sxs-lookup"><span data-stu-id="bb21a-231">Evaluation is the process of measuring how good your model is.</span></span> <span data-ttu-id="bb21a-232">模型產生器會使用定型的模型，以新的測試資料進行預測，然後測量預測的良好程度。</span><span class="sxs-lookup"><span data-stu-id="bb21a-232">Model Builder uses the trained model to make predictions with new test data, and then measures how good the predictions are.</span></span>

<span data-ttu-id="bb21a-233">模型建立器會將定型資料分割為定型集和測試集。</span><span class="sxs-lookup"><span data-stu-id="bb21a-233">Model Builder splits the training data into a training set and a test set.</span></span> <span data-ttu-id="bb21a-234">定型資料 (80%) 用來定型模型，而測試資料 (20%) 則保留用於評估模型。</span><span class="sxs-lookup"><span data-stu-id="bb21a-234">The training data (80%) is used to train your model and the test data (20%) is held back to evaluate your model.</span></span>

### <a name="how-do-i-understand-my-model-performance"></a><span data-ttu-id="bb21a-235">如何? 瞭解我的模型效能嗎？</span><span class="sxs-lookup"><span data-stu-id="bb21a-235">How do I understand my model performance?</span></span>

<span data-ttu-id="bb21a-236">案例會對應至機器學習服務工作。</span><span class="sxs-lookup"><span data-stu-id="bb21a-236">A scenario maps to a machine learning task.</span></span> <span data-ttu-id="bb21a-237">每個 ML 工作都有自己的一組評估度量。</span><span class="sxs-lookup"><span data-stu-id="bb21a-237">Each ML task has its own set of evaluation metrics.</span></span>

#### <a name="value-prediction"></a><span data-ttu-id="bb21a-238">值預測</span><span class="sxs-lookup"><span data-stu-id="bb21a-238">Value prediction</span></span>

<span data-ttu-id="bb21a-239">值預測問題的預設度量為 RSquared，RSquared 的值範圍介於0和1之間。</span><span class="sxs-lookup"><span data-stu-id="bb21a-239">The default metric for value prediction problems is RSquared, the value of RSquared ranges between 0 and 1.</span></span> <span data-ttu-id="bb21a-240">1是最可能的值，換句話說，更接近您的模型所執行的 RSquared 價值。</span><span class="sxs-lookup"><span data-stu-id="bb21a-240">1 is the best possible value or in other words the closer the value of RSquared to 1 the better your model is performing.</span></span>

<span data-ttu-id="bb21a-241">其他計量（例如絕對損失、平方損失和 RMS 遺失）都是額外的計量，可用來瞭解您的模型如何執行，並將其與其他值預測模型進行比較。</span><span class="sxs-lookup"><span data-stu-id="bb21a-241">Other metrics reported such as absolute-loss, squared-loss, and RMS loss are additional metrics, which can be used to understand how your model is performing and comparing it against other value prediction models.</span></span>

#### <a name="classification-2-categories"></a><span data-ttu-id="bb21a-242">分類 (2 類別) </span><span class="sxs-lookup"><span data-stu-id="bb21a-242">Classification (2 categories)</span></span>

<span data-ttu-id="bb21a-243">分類問題的預設度量為精確度。</span><span class="sxs-lookup"><span data-stu-id="bb21a-243">The default metric for classification problems is accuracy.</span></span> <span data-ttu-id="bb21a-244">精確度會定義您的模型在測試資料集上進行的正確預測比例。</span><span class="sxs-lookup"><span data-stu-id="bb21a-244">Accuracy defines the proportion of correct predictions your model is making over the test dataset.</span></span> <span data-ttu-id="bb21a-245">越接近100% 或1.0 就越好。</span><span class="sxs-lookup"><span data-stu-id="bb21a-245">The closer to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="bb21a-246">在 [曲線]) 下回報的其他計量（例如 AUC (區域），其測量真正的正面比率與 false 的正面比率應大於0.50，才能接受模型。</span><span class="sxs-lookup"><span data-stu-id="bb21a-246">Other metrics reported such as AUC (Area under the curve), which measures the true positive rate vs. the false positive rate should be greater than 0.50 for models to be acceptable.</span></span>

<span data-ttu-id="bb21a-247">其他計量（例如 F1 分數）可以用來控制精確度和召回率之間的平衡。</span><span class="sxs-lookup"><span data-stu-id="bb21a-247">Additional metrics like F1 score can be used to control the balance between Precision and Recall.</span></span>

#### <a name="classification-3-categories"></a><span data-ttu-id="bb21a-248">分類 (3 + 類別) </span><span class="sxs-lookup"><span data-stu-id="bb21a-248">Classification (3+ categories)</span></span>

<span data-ttu-id="bb21a-249">多重類別分類的預設度量為微精確度。</span><span class="sxs-lookup"><span data-stu-id="bb21a-249">The default metric for Multi-class classification is Micro Accuracy.</span></span> <span data-ttu-id="bb21a-250">越接近接近100% 或1.0 的微精確度越好。</span><span class="sxs-lookup"><span data-stu-id="bb21a-250">The closer the Micro Accuracy to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="bb21a-251">多重類別分類的另一項重要計量是宏精確度，類似于更接近1.0 的微精確度。</span><span class="sxs-lookup"><span data-stu-id="bb21a-251">Another important metric for Multi-class classification is Macro-accuracy, similar to Micro-accuracy the closer to 1.0 the better it is.</span></span> <span data-ttu-id="bb21a-252">最好的方式是將這兩種類型的精確度視為：</span><span class="sxs-lookup"><span data-stu-id="bb21a-252">A good way to think about these two types of accuracy is:</span></span>

- <span data-ttu-id="bb21a-253">微精確度：將傳入票證分類至正確小組的頻率為何？</span><span class="sxs-lookup"><span data-stu-id="bb21a-253">Micro-accuracy: How often does an incoming ticket get classified to the right team?</span></span>
- <span data-ttu-id="bb21a-254">宏精確度：對於平均小組而言，其小組的連入票證是正確的？</span><span class="sxs-lookup"><span data-stu-id="bb21a-254">Macro-accuracy: For an average team, how often is an incoming ticket correct for their team?</span></span>

### <a name="more-information-on-evaluation-metrics"></a><span data-ttu-id="bb21a-255">評估計量的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="bb21a-255">More information on evaluation metrics</span></span>

<span data-ttu-id="bb21a-256">如需詳細資訊，請參閱[模型評估計量](resources/metrics.md)。</span><span class="sxs-lookup"><span data-stu-id="bb21a-256">For more information, see [model evaluation metrics](resources/metrics.md).</span></span>

## <a name="improve"></a><span data-ttu-id="bb21a-257">改善</span><span class="sxs-lookup"><span data-stu-id="bb21a-257">Improve</span></span>

<span data-ttu-id="bb21a-258">如果您的模型效能分數不如預期，您可以：</span><span class="sxs-lookup"><span data-stu-id="bb21a-258">If your model performance score is not as good as you want it to be, you can:</span></span>

- <span data-ttu-id="bb21a-259">延長定型時間。</span><span class="sxs-lookup"><span data-stu-id="bb21a-259">Train for a longer period of time.</span></span> <span data-ttu-id="bb21a-260">使用更多時間，自動化機器學習引擎會以更多的演算法和設定進行實驗。</span><span class="sxs-lookup"><span data-stu-id="bb21a-260">With more time, the automated machine learning engine experiments with more algorithms and settings.</span></span>

- <span data-ttu-id="bb21a-261">新增更多資料。</span><span class="sxs-lookup"><span data-stu-id="bb21a-261">Add more data.</span></span> <span data-ttu-id="bb21a-262">有時候資料量不足以定型高品質的機器學習模型。這特別適用于具有少量範例的資料集。</span><span class="sxs-lookup"><span data-stu-id="bb21a-262">Sometimes the amount of data is not sufficient to train a high-quality machine learning model.This is especially true with datasets that have a small number of examples.</span></span>

- <span data-ttu-id="bb21a-263">平衡資料。</span><span class="sxs-lookup"><span data-stu-id="bb21a-263">Balance your data.</span></span> <span data-ttu-id="bb21a-264">針對分類工作，請務必平衡所有類別的定型集。</span><span class="sxs-lookup"><span data-stu-id="bb21a-264">For classification tasks, make sure that the training set is balanced across the categories.</span></span> <span data-ttu-id="bb21a-265">例如，如果您有四個類別的 100 個定型範例，有 90 筆記錄使用前兩個類別 (tag1 和 tag2)，只有剩餘的 10 筆記錄使用其他兩個類別 (tag3 和 tag4)，則資料失衡可能會導致模型難以正確預測 tag3 或 tag4。</span><span class="sxs-lookup"><span data-stu-id="bb21a-265">For example, if you have four classes for 100 training examples, and the two first classes (tag1 and tag2) are used for 90 records, but the other two (tag3 and tag4) are only used on the remaining 10 records, the lack of balanced data may cause your model to struggle to correctly predict tag3 or tag4.</span></span>

## <a name="code"></a><span data-ttu-id="bb21a-266">程式碼</span><span class="sxs-lookup"><span data-stu-id="bb21a-266">Code</span></span>

<span data-ttu-id="bb21a-267">在評估階段後，模型建立器會輸出模型檔案，以及可用來將模型新增至應用程式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="bb21a-267">After the evaluation phase, Model Builder outputs a model file, and code that you can use to add the model to your application.</span></span> <span data-ttu-id="bb21a-268">ML.NET 模型會儲存為 ZIP 檔案。</span><span class="sxs-lookup"><span data-stu-id="bb21a-268">ML.NET models are saved as a zip file.</span></span> <span data-ttu-id="bb21a-269">載入並使用模型的程式碼會新增為解決方案中新專案。</span><span class="sxs-lookup"><span data-stu-id="bb21a-269">The code to load and use your model is added as a new project in your solution.</span></span> <span data-ttu-id="bb21a-270">模型建立器也會新增範例主控台應用程式，您可以執行它以查看運行的模型。</span><span class="sxs-lookup"><span data-stu-id="bb21a-270">Model Builder also adds a sample console app that you can run to see your model in action.</span></span>

<span data-ttu-id="bb21a-271">此外，模型建立器會輸出產生模型的程式碼，以便您可以了解產生模型所用的步驟。</span><span class="sxs-lookup"><span data-stu-id="bb21a-271">In addition, Model Builder outputs the code that generated the model, so that you can understand the steps used to generate the model.</span></span> <span data-ttu-id="bb21a-272">您也可以使用模型定型程式碼以新資料重新定型模型。</span><span class="sxs-lookup"><span data-stu-id="bb21a-272">You can also use the model training code to retrain your model with new data.</span></span>

## <a name="whats-next"></a><span data-ttu-id="bb21a-273">接下來要做什麼？</span><span class="sxs-lookup"><span data-stu-id="bb21a-273">What's next?</span></span>

<span data-ttu-id="bb21a-274">[安裝](how-to-guides/install-model-builder.md)模型建立器 Visual Studio 延伸模組</span><span class="sxs-lookup"><span data-stu-id="bb21a-274">[Install](how-to-guides/install-model-builder.md) the Model Builder Visual Studio extension</span></span>

<span data-ttu-id="bb21a-275">請嘗試[價格預測或任何迴歸案例](tutorials/predict-prices-with-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="bb21a-275">Try [price prediction or any regression scenario](tutorials/predict-prices-with-model-builder.md)</span></span>
