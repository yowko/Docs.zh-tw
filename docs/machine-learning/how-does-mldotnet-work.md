---
title: 什麼是 ML.NET，它如何運作？
description: ML.NET 能讓您將機器學習新增至 .NET 應用程式。 使用這項功能，您可以使用應用程式可用的資料來建立自動預測。 本文說明 ML.NET 的機器學習基本概念。
ms.date: 04/10/2019
ms.topic: overview
ms.custom: mvc
ms.author: nakersha
author: natke
ms.openlocfilehash: 7f92049e19688df1fe2b834214950c9109cb0799
ms.sourcegitcommit: c4dfe37032c64a1fba2cc3d5947550d79f95e3b5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/13/2019
ms.locfileid: "67041534"
---
# <a name="what-is-mlnet-and-how-does-it-work"></a><span data-ttu-id="79b6b-105">什麼是 ML.NET，它如何運作？</span><span class="sxs-lookup"><span data-stu-id="79b6b-105">What is ML.NET and how does it work?</span></span>

<span data-ttu-id="79b6b-106">ML.NET 能讓您將機器學習新增至 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="79b6b-106">ML.NET gives you the ability to add machine learning to .NET applications.</span></span> <span data-ttu-id="79b6b-107">使用這項功能，您可以使用應用程式可用的資料來建立自動預測。</span><span class="sxs-lookup"><span data-stu-id="79b6b-107">With this capability, you can make automatic predictions using the data available to your application.</span></span> <span data-ttu-id="79b6b-108">本文說明 ML.NET 的機器學習基本概念。</span><span class="sxs-lookup"><span data-stu-id="79b6b-108">This article explains the basics of machine learning in ML.NET.</span></span> 

<span data-ttu-id="79b6b-109">您可使用 ML.NET 建立的預測類型範例包括：</span><span class="sxs-lookup"><span data-stu-id="79b6b-109">Examples of the type of predictions that you can make with ML.NET include:</span></span>

|||
|-|-|
|<span data-ttu-id="79b6b-110">分類/分類</span><span class="sxs-lookup"><span data-stu-id="79b6b-110">Classification/Categorization</span></span>|<span data-ttu-id="79b6b-111">自動將客戶的意見反應分成正負類別</span><span class="sxs-lookup"><span data-stu-id="79b6b-111">Automatically divide customer feedback into positive and negative categories</span></span>|
|<span data-ttu-id="79b6b-112">迴歸/預測連續值</span><span class="sxs-lookup"><span data-stu-id="79b6b-112">Regression/Predict continuous values</span></span>|<span data-ttu-id="79b6b-113">根據大小和位置預測房價</span><span class="sxs-lookup"><span data-stu-id="79b6b-113">Predict the price of houses based on size and location</span></span>|
|<span data-ttu-id="79b6b-114">異常偵測</span><span class="sxs-lookup"><span data-stu-id="79b6b-114">Anomaly Detection</span></span>|<span data-ttu-id="79b6b-115">偵測詐騙的銀行交易</span><span class="sxs-lookup"><span data-stu-id="79b6b-115">Detect fraudulent banking transactions</span></span> |
|<span data-ttu-id="79b6b-116">建議</span><span class="sxs-lookup"><span data-stu-id="79b6b-116">Recommendations</span></span>|<span data-ttu-id="79b6b-117">根據線上購物者之前的購買記錄，建議他們可能想要購買的產品</span><span class="sxs-lookup"><span data-stu-id="79b6b-117">Suggest products that online shoppers may want to buy, based on their previous purchases</span></span>|

## <a name="hello-mlnet-world"></a><span data-ttu-id="79b6b-118">Hello ML.NET World</span><span class="sxs-lookup"><span data-stu-id="79b6b-118">Hello ML.NET World</span></span>

<span data-ttu-id="79b6b-119">下列程式碼片段中程式碼會示範最簡單的 ML.NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="79b6b-119">The code in the following snippet demonstrates the simplest ML.NET application.</span></span> <span data-ttu-id="79b6b-120">此範例會建構線性迴歸模型，使用房子大小及價格資料來預測房價。</span><span class="sxs-lookup"><span data-stu-id="79b6b-120">This example constructs a linear regression model to predict house prices using house size and price data.</span></span> <span data-ttu-id="79b6b-121">在實際的應用程式中，您的資料和模型會更複雜。</span><span class="sxs-lookup"><span data-stu-id="79b6b-121">In your real-life applications, your data and model will be much more complex.</span></span>

 ```csharp
    using System;
    using Microsoft.ML;
    using Microsoft.ML.Data;
    
    class Program
    {
        public class HouseData
        {
            public float Size { get; set; }
            public float Price { get; set; }
        }
    
        public class Prediction
        {
            [ColumnName("Score")]
            public float Price { get; set; }
        }
    
        static void Main(string[] args)
        {
            MLContext mlContext = new MLContext();
    
            // 1. Import or create training data
            HouseData[] houseData = {
                new HouseData() { Size = 1.1F, Price = 1.2F },
                new HouseData() { Size = 1.9F, Price = 2.3F },
                new HouseData() { Size = 2.8F, Price = 3.0F },
                new HouseData() { Size = 3.4F, Price = 3.7F } };
            IDataView trainingData = mlContext.Data.LoadFromEnumerable(houseData);

            // 2. Specify data preparation and model training pipeline
            var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
                .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));
    
            // 3. Train model
            var model = pipeline.Fit(trainingData);
    
            // 4. Make a prediction
            var size = new HouseData() { Size = 2.5F };
            var price = mlContext.Model.CreatePredictionEngine<HouseData, Prediction>(model).Predict(size);

            Console.WriteLine($"Predicted price for size: {size.Size*1000} sq ft= {price.Price*100:C}k");

            // Predicted price for size: 2500 sq ft= $261.98k
        }
    } 
```

## <a name="code-workflow"></a><span data-ttu-id="79b6b-122">程式碼工作流程</span><span class="sxs-lookup"><span data-stu-id="79b6b-122">Code workflow</span></span>

<span data-ttu-id="79b6b-123">下圖代表應用程式程式碼結構，以及模型開發的反覆程序：</span><span class="sxs-lookup"><span data-stu-id="79b6b-123">The following diagram represents the application code structure, as well as the iterative process of model development:</span></span>
- <span data-ttu-id="79b6b-124">收集定型資料，並將其載入 **IDataView** 物件</span><span class="sxs-lookup"><span data-stu-id="79b6b-124">Collect and load training data into an **IDataView** object</span></span>
- <span data-ttu-id="79b6b-125">指定擷取特性的作業管線並套用機器學習演算法</span><span class="sxs-lookup"><span data-stu-id="79b6b-125">Specify a pipeline of operations to extract features and apply a machine learning algorithm</span></span>
- <span data-ttu-id="79b6b-126">對管線呼叫 **Fit()** 以定型模型</span><span class="sxs-lookup"><span data-stu-id="79b6b-126">Train a model by calling **Fit()** on the pipeline</span></span>
- <span data-ttu-id="79b6b-127">評估模型並反覆運算來加以改善</span><span class="sxs-lookup"><span data-stu-id="79b6b-127">Evaluate the model and iterate to improve</span></span>
- <span data-ttu-id="79b6b-128">將模型儲存成二進位格式，供應用程式使用</span><span class="sxs-lookup"><span data-stu-id="79b6b-128">Save the model into binary format, for use in an application</span></span>
- <span data-ttu-id="79b6b-129">將模型載回至 **ITransformer** 物件</span><span class="sxs-lookup"><span data-stu-id="79b6b-129">Load the model back into an **ITransformer** object</span></span>
- <span data-ttu-id="79b6b-130">呼叫 **CreatePredictionEngine.Predict()** 以建立預測</span><span class="sxs-lookup"><span data-stu-id="79b6b-130">Make predictions by calling **CreatePredictionEngine.Predict()**</span></span>

![ML.NET 應用程式開發流程包括產生資料、開發管線、定型模型、評估模型和使用模型的元件](./media/mldotnet-annotated-workflow.png) 

<span data-ttu-id="79b6b-132">讓我們稍微深入探討這些概念。</span><span class="sxs-lookup"><span data-stu-id="79b6b-132">Let's dig a little deeper into those concepts.</span></span>

## <a name="machine-learning-model"></a><span data-ttu-id="79b6b-133">機器學習模型</span><span class="sxs-lookup"><span data-stu-id="79b6b-133">Machine learning model</span></span>

<span data-ttu-id="79b6b-134">ML.NET 模型是一個物件，包含要對輸入資料執行的轉換，以達成預測的輸出。</span><span class="sxs-lookup"><span data-stu-id="79b6b-134">An ML.NET model is an object that contains transformations to perform on your input data to arrive at the predicted output.</span></span>

### <a name="basic"></a><span data-ttu-id="79b6b-135">基本</span><span class="sxs-lookup"><span data-stu-id="79b6b-135">Basic</span></span>

<span data-ttu-id="79b6b-136">最基本的模型是二維線性迴歸，其中一個持續數量和另一個成正比，如上述的房價範例所示。</span><span class="sxs-lookup"><span data-stu-id="79b6b-136">The most basic model is two-dimensional linear regression, where one continuous quantity is proportional to another, as in the house price example above.</span></span> 

![使用偏差和加權參數的線性迴歸模型](./media/linear-regression-model.svg)

<span data-ttu-id="79b6b-138">此模型就只是：$Price = b + Size \* w$。</span><span class="sxs-lookup"><span data-stu-id="79b6b-138">The model is simply: $Price = b + Size \* w$.</span></span> <span data-ttu-id="79b6b-139">參數 $b$ 和 $w$ 的評估方式是根據一組 (大小、價格) 對組來調整線條。</span><span class="sxs-lookup"><span data-stu-id="79b6b-139">The parameters $b$ and $w$ are estimated by fitting a line on a set of (size, price) pairs.</span></span> <span data-ttu-id="79b6b-140">用來尋找模型參數的資料稱為**定型資料**。</span><span class="sxs-lookup"><span data-stu-id="79b6b-140">The data used to find the parameters of the model is called **training data**.</span></span> <span data-ttu-id="79b6b-141">機器學習模型的輸入稱為**特性**。</span><span class="sxs-lookup"><span data-stu-id="79b6b-141">The inputs of a machine learning model are called **features**.</span></span> <span data-ttu-id="79b6b-142">在本例中，$Size$ 是唯一的特性。</span><span class="sxs-lookup"><span data-stu-id="79b6b-142">In this example, $Size$ is the only feature.</span></span> <span data-ttu-id="79b6b-143">用來定型機器學習模型的實況資料稱為**標籤**。</span><span class="sxs-lookup"><span data-stu-id="79b6b-143">The ground-truth values used to train a machine learning model are called **labels**.</span></span> <span data-ttu-id="79b6b-144">在這裡，定型資料集的 $Price$ 值是標籤。</span><span class="sxs-lookup"><span data-stu-id="79b6b-144">Here, the $Price$ values in the training data set are the labels.</span></span>

### <a name="more-complex"></a><span data-ttu-id="79b6b-145">更複雜</span><span class="sxs-lookup"><span data-stu-id="79b6b-145">More complex</span></span>

<span data-ttu-id="79b6b-146">更複雜模型會使用交易的文字描述將財務交易分類成類別。</span><span class="sxs-lookup"><span data-stu-id="79b6b-146">A more complex model classifies financial transactions into categories using the transaction text description.</span></span>

<span data-ttu-id="79b6b-147">每條交易描述會移除多餘的字詞和字元，並計算字詞和字元組合，細分成一組特性。</span><span class="sxs-lookup"><span data-stu-id="79b6b-147">Each transaction description is broken down into a set of features by removing redundant words and characters, and counting word and character combinations.</span></span> <span data-ttu-id="79b6b-148">以定型資料中的類別集為基礎，用特性集定型線性模型。</span><span class="sxs-lookup"><span data-stu-id="79b6b-148">The feature set is used to train a linear model based on the set of categories in the training data.</span></span> <span data-ttu-id="79b6b-149">新描述與定型集中的描述愈相似，愈可能指派給同一分類。</span><span class="sxs-lookup"><span data-stu-id="79b6b-149">The more similar a new description is to the ones in the training set, the more likely it will be assigned to the same category.</span></span> 

![文字分類模型](./media/text-classification-model.svg)

<span data-ttu-id="79b6b-151">房價模型和文字分類模型都是**線性**模型。</span><span class="sxs-lookup"><span data-stu-id="79b6b-151">Both the house price model and the text classification model are **linear** models.</span></span> <span data-ttu-id="79b6b-152">根據資料本質以及要解決的問題本質，您也可以使用**決策樹**模型、**一般化累加**模型和其他模型。</span><span class="sxs-lookup"><span data-stu-id="79b6b-152">Depending on the nature of your data and the problem you are solving, you can also use **decision tree** models, **generalized additive** models, and others.</span></span> <span data-ttu-id="79b6b-153">您可以在[任務](./resources/tasks.md)中深入了解模型。</span><span class="sxs-lookup"><span data-stu-id="79b6b-153">You can find out more about the models in [Tasks](./resources/tasks.md).</span></span>

## <a name="data-preparation"></a><span data-ttu-id="79b6b-154">資料準備</span><span class="sxs-lookup"><span data-stu-id="79b6b-154">Data preparation</span></span>

<span data-ttu-id="79b6b-155">在大部分的情況下，您所用的資料不適合直接用來定型機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="79b6b-155">In most cases, the data that you have available isn't suitable to be used directly to train a machine learning model.</span></span> <span data-ttu-id="79b6b-156">未經處理資料需要經過準備或前置處理，才能用來尋找您模型的參數。</span><span class="sxs-lookup"><span data-stu-id="79b6b-156">The raw data needs to be prepared, or pre-processed before it can be used to find the parameters of your model.</span></span> <span data-ttu-id="79b6b-157">您的資料可能需要從字串值轉換成數值表示。</span><span class="sxs-lookup"><span data-stu-id="79b6b-157">Your data may need to be converted from string values to a numerical representation.</span></span> <span data-ttu-id="79b6b-158">您的輸入資料中可能有多餘資訊。</span><span class="sxs-lookup"><span data-stu-id="79b6b-158">You might have redundant information in your input data.</span></span> <span data-ttu-id="79b6b-159">您可能需要縮小或擴充您輸入資料的維度。</span><span class="sxs-lookup"><span data-stu-id="79b6b-159">You may need to reduce or expand the dimensions of your input data.</span></span> <span data-ttu-id="79b6b-160">您的資料可能需要標準化或調整。</span><span class="sxs-lookup"><span data-stu-id="79b6b-160">Your data might need to be normalized or scaled.</span></span>

<span data-ttu-id="79b6b-161">[ML.NET 教學課程](./tutorials/index.md)會教導您用於特定機器學習工作之文字、影像、數值和時間序列資料的不同資料處理管線。</span><span class="sxs-lookup"><span data-stu-id="79b6b-161">The [ML.NET tutorials](./tutorials/index.md) teach you about different data processing pipelines for text, image, numerical, and time-series data used for specific machine learning tasks.</span></span>

<span data-ttu-id="79b6b-162">[如何準備您的資料](./how-to-guides/prepare-data-ml-net.md)會示範如何更全面地套用資料準備。</span><span class="sxs-lookup"><span data-stu-id="79b6b-162">[How to prepare your data](./how-to-guides/prepare-data-ml-net.md) shows you how to applied data preparation more generally.</span></span>

<span data-ttu-id="79b6b-163">您可以在＜資源＞一節中找到所有[可用轉換](./resources/transforms.md)的附錄。</span><span class="sxs-lookup"><span data-stu-id="79b6b-163">You can find an appendix of all of the [available transformations](./resources/transforms.md) in the resources section.</span></span>

## <a name="model-evaluation"></a><span data-ttu-id="79b6b-164">模型評估</span><span class="sxs-lookup"><span data-stu-id="79b6b-164">Model evaluation</span></span>

<span data-ttu-id="79b6b-165">定型模型之後，您怎麼知道它對未來的預測有多準？</span><span class="sxs-lookup"><span data-stu-id="79b6b-165">Once you have trained your model, how do you know how well it will make future predictions?</span></span> <span data-ttu-id="79b6b-166">使用 ML.NET，您可以利用某些新的測試資料來評估模型。</span><span class="sxs-lookup"><span data-stu-id="79b6b-166">With ML.NET, you can evaluate your model against some new test data.</span></span> 

<span data-ttu-id="79b6b-167">每種機器學習工作都有針對測試資料集，用來評估模型正確性和精確度的計量。</span><span class="sxs-lookup"><span data-stu-id="79b6b-167">Each type of machine learning task has metrics used to evaluate the accuracy and precision of the model against the test data set.</span></span>

<span data-ttu-id="79b6b-168">在房價範例中，我們使用了**迴歸**工作。</span><span class="sxs-lookup"><span data-stu-id="79b6b-168">For our house price example, we used the **Regression** task.</span></span> <span data-ttu-id="79b6b-169">若要評估模型，請將下列程式碼新增至原始範例。</span><span class="sxs-lookup"><span data-stu-id="79b6b-169">To evaluate the model, add the following code to the original sample.</span></span>

```csharp
        HouseData[] testHouseData =
        {
            new HouseData() { Size = 1.1F, Price = 0.98F },
            new HouseData() { Size = 1.9F, Price = 2.1F },
            new HouseData() { Size = 2.8F, Price = 2.9F },
            new HouseData() { Size = 3.4F, Price = 3.6F }
        };

        var testHouseDataView = mlContext.Data.LoadFromEnumerable(testHouseData);
        var testPriceDataView = model.Transform(testHouseDataView);
                
        var metrics = mlContext.Regression.Evaluate(testPriceDataView, labelColumnName: "Price");

        Console.WriteLine($"R^2: {metrics.RSquared:0.##}");
        Console.WriteLine($"RMS error: {metrics.RootMeanSquaredError:0.##}");

        // R^2: 0.96
        // RMS error: 0.19
```

<span data-ttu-id="79b6b-170">評估計量會告訴您錯誤有點低，且預測輸出和測試輸出之間的關聯性很高。</span><span class="sxs-lookup"><span data-stu-id="79b6b-170">The evaluation metrics tell you that the error is low-ish, and that correlation between the predicted output and the test output is high.</span></span> <span data-ttu-id="79b6b-171">很簡單！</span><span class="sxs-lookup"><span data-stu-id="79b6b-171">That was easy!</span></span> <span data-ttu-id="79b6b-172">在實際範例中，需要更多微調才能達到良好的模型計量。</span><span class="sxs-lookup"><span data-stu-id="79b6b-172">In real examples, it takes more tuning to achieve good model metrics.</span></span>

## <a name="mlnet-architecture"></a><span data-ttu-id="79b6b-173">ML.NET 架構</span><span class="sxs-lookup"><span data-stu-id="79b6b-173">ML.NET architecture</span></span>

<span data-ttu-id="79b6b-174">在本節中，我們要探討 ML.NET 的架構模式。</span><span class="sxs-lookup"><span data-stu-id="79b6b-174">In this section, we go through the architectural patterns of ML.NET.</span></span> <span data-ttu-id="79b6b-175">如果您是有經驗的 .NET 開發人員，對這些模式有些很熟悉，有些則較不熟悉。</span><span class="sxs-lookup"><span data-stu-id="79b6b-175">If you are an experienced .NET developer, some of these patterns will be familiar to you, and some will be less familiar.</span></span> <span data-ttu-id="79b6b-176">跟上來一探究竟吧！</span><span class="sxs-lookup"><span data-stu-id="79b6b-176">Hold tight, while we dive in!</span></span>

<span data-ttu-id="79b6b-177">ML.NET 應用程式以 <xref:Microsoft.ML.MLContext> 物件開始。</span><span class="sxs-lookup"><span data-stu-id="79b6b-177">An ML.NET application starts with an <xref:Microsoft.ML.MLContext> object.</span></span> <span data-ttu-id="79b6b-178">此單一物件包含**目錄**。</span><span class="sxs-lookup"><span data-stu-id="79b6b-178">This singleton object contains **catalogs**.</span></span> <span data-ttu-id="79b6b-179">目錄是資料載入儲存、轉換、定型器和模型作業元件的處理站。</span><span class="sxs-lookup"><span data-stu-id="79b6b-179">A catalog is a factory for data loading and saving, transforms, trainers, and model operation components.</span></span> <span data-ttu-id="79b6b-180">每個目錄物件都有建立不同類型元件的方法：</span><span class="sxs-lookup"><span data-stu-id="79b6b-180">Each catalog object has methods to create the different types of components:</span></span>

||||
|-|-|-|
|<span data-ttu-id="79b6b-181">資料載入及儲存</span><span class="sxs-lookup"><span data-stu-id="79b6b-181">Data loading and saving</span></span>||<xref:Microsoft.ML.DataOperationsCatalog>|
|<span data-ttu-id="79b6b-182">資料準備</span><span class="sxs-lookup"><span data-stu-id="79b6b-182">Data preparation</span></span>||<xref:Microsoft.ML.TransformsCatalog>|
|<span data-ttu-id="79b6b-183">定型演算法</span><span class="sxs-lookup"><span data-stu-id="79b6b-183">Training algorithms</span></span>|<span data-ttu-id="79b6b-184">二元分類</span><span class="sxs-lookup"><span data-stu-id="79b6b-184">Binary classification</span></span>|<xref:Microsoft.ML.BinaryClassificationCatalog>|
||<span data-ttu-id="79b6b-185">多元分類</span><span class="sxs-lookup"><span data-stu-id="79b6b-185">Multiclass classification</span></span>|<xref:Microsoft.ML.MulticlassClassificationCatalog>|
||<span data-ttu-id="79b6b-186">異常偵測</span><span class="sxs-lookup"><span data-stu-id="79b6b-186">Anomaly detection</span></span>|<xref:Microsoft.ML.AnomalyDetectionCatalog>|
||<span data-ttu-id="79b6b-187">排名</span><span class="sxs-lookup"><span data-stu-id="79b6b-187">Ranking</span></span>|<xref:Microsoft.ML.RankingCatalog>|
||<span data-ttu-id="79b6b-188">回復</span><span class="sxs-lookup"><span data-stu-id="79b6b-188">Regression</span></span>|<xref:Microsoft.ML.RegressionCatalog>|
||<span data-ttu-id="79b6b-189">建議</span><span class="sxs-lookup"><span data-stu-id="79b6b-189">Recommendation</span></span>|<xref:Microsoft.ML.RecommendationCatalog>|
|<span data-ttu-id="79b6b-190">模型使用方式</span><span class="sxs-lookup"><span data-stu-id="79b6b-190">Model usage</span></span> ||<xref:Microsoft.ML.ModelOperationsCatalog>|

<span data-ttu-id="79b6b-191">您可以巡覽至上述每個類別的建立方法。</span><span class="sxs-lookup"><span data-stu-id="79b6b-191">You can navigate to the creation methods in each of the above categories.</span></span> <span data-ttu-id="79b6b-192">使用 Visual Studio，會透過 IntelliSense 顯示目錄。</span><span class="sxs-lookup"><span data-stu-id="79b6b-192">Using Visual Studio, the catalogs show up via IntelliSense.</span></span>

   ![適用於迴歸定型器的 Intellisense](./media/catalog-intellisense.png)

### <a name="build-the-pipeline"></a><span data-ttu-id="79b6b-194">建置管線</span><span class="sxs-lookup"><span data-stu-id="79b6b-194">Build the pipeline</span></span>

<span data-ttu-id="79b6b-195">每個目錄中都是一組擴充方法。</span><span class="sxs-lookup"><span data-stu-id="79b6b-195">Inside each catalog is a set of extension methods.</span></span> <span data-ttu-id="79b6b-196">讓我們看看如何使用擴充方法建立定型管線。</span><span class="sxs-lookup"><span data-stu-id="79b6b-196">Let's look at how extension methods are used to create a training pipeline.</span></span>

```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
        .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));
```

<span data-ttu-id="79b6b-197">在程式碼片段中，`Concatenate` 和 `Sdca` 都是目錄中的方法。</span><span class="sxs-lookup"><span data-stu-id="79b6b-197">In the snippet, `Concatenate` and `Sdca` are both methods in the catalog.</span></span> <span data-ttu-id="79b6b-198">它們會各自建立附加至管線的 [IEstimator](xref:Microsoft.ML.IEstimator%601) 物件。</span><span class="sxs-lookup"><span data-stu-id="79b6b-198">They each create an [IEstimator](xref:Microsoft.ML.IEstimator%601) object that is appended to the pipeline.</span></span>

<span data-ttu-id="79b6b-199">此時，只會建立物件。</span><span class="sxs-lookup"><span data-stu-id="79b6b-199">At this point, the objects are created only.</span></span> <span data-ttu-id="79b6b-200">尚未開始執行。</span><span class="sxs-lookup"><span data-stu-id="79b6b-200">No execution has happened.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="79b6b-201">將模型定型</span><span class="sxs-lookup"><span data-stu-id="79b6b-201">Train the model</span></span>

<span data-ttu-id="79b6b-202">管線中一旦建立物件，資料就可用來定型模型。</span><span class="sxs-lookup"><span data-stu-id="79b6b-202">Once the objects in the pipeline have been created, data can be used to train the model.</span></span>

```csharp
    var model = pipeline.Fit(trainingData);
```

<span data-ttu-id="79b6b-203">呼叫 `Fit()` 會使用輸入定型資料來評估模型的參數。</span><span class="sxs-lookup"><span data-stu-id="79b6b-203">Calling `Fit()` uses the input training data to estimate the parameters of the model.</span></span> <span data-ttu-id="79b6b-204">這就是定型模型。</span><span class="sxs-lookup"><span data-stu-id="79b6b-204">This is known as training the model.</span></span> <span data-ttu-id="79b6b-205">請記住，上述的線性迴歸模型有兩個模型參數：**偏差**和**權數**。</span><span class="sxs-lookup"><span data-stu-id="79b6b-205">Remember, the linear regression model above had two model parameters: **bias** and **weight**.</span></span> <span data-ttu-id="79b6b-206">呼叫 `Fit()` 之後，即已知參數值。</span><span class="sxs-lookup"><span data-stu-id="79b6b-206">After the `Fit()` call, the values of the parameters are known.</span></span> <span data-ttu-id="79b6b-207">大部分模型的參數都比這個模型多。</span><span class="sxs-lookup"><span data-stu-id="79b6b-207">Most models will have many more parameters than this.</span></span>

<span data-ttu-id="79b6b-208">您可以在[如何定型模型](./how-to-guides/train-machine-learning-model-ml-net.md)中深入了解模型定型</span><span class="sxs-lookup"><span data-stu-id="79b6b-208">You can learn more about model training in [How to train your model](./how-to-guides/train-machine-learning-model-ml-net.md)</span></span>

<span data-ttu-id="79b6b-209">產生的模型物件會實作 <xref:Microsoft.ML.ITransformer> 介面。</span><span class="sxs-lookup"><span data-stu-id="79b6b-209">The resulting model object implements the <xref:Microsoft.ML.ITransformer> interface.</span></span> <span data-ttu-id="79b6b-210">亦即，模型會將輸入資料轉換成預測。</span><span class="sxs-lookup"><span data-stu-id="79b6b-210">That is, the model transforms input data into predictions.</span></span>

```csharp
   IDataView predictions = model.Transform(inputData);
```

### <a name="use-the-model"></a><span data-ttu-id="79b6b-211">使用模型</span><span class="sxs-lookup"><span data-stu-id="79b6b-211">Use the model</span></span>

<span data-ttu-id="79b6b-212">您可以將大量輸入資料或一次一筆輸入資料轉換成預測。</span><span class="sxs-lookup"><span data-stu-id="79b6b-212">You can transform input data into predictions in bulk, or one input at a time.</span></span> <span data-ttu-id="79b6b-213">在房價範例中，我們兩種都做了：大量資料是用於評估模型，一次一筆資料則是為了建立新的預測。</span><span class="sxs-lookup"><span data-stu-id="79b6b-213">In the house price example, we did both: in bulk for the purpose of evaluating the model, and one at a time to make a new prediction.</span></span> <span data-ttu-id="79b6b-214">讓我們看看建立單一預測。</span><span class="sxs-lookup"><span data-stu-id="79b6b-214">Let's look at making single predictions.</span></span>

```csharp
    var size = new HouseData() { Size = 2.5F };
    var predEngine = model.CreatePredictionEngine<HouseData, Prediction>(mlContext);
    var price = predEngine.Predict(size);
```
 
<span data-ttu-id="79b6b-215">`CreatePredictionEngine()` 方法接受輸入類別和輸出類別。</span><span class="sxs-lookup"><span data-stu-id="79b6b-215">The `CreatePredictionEngine()` method takes an input class and an output class.</span></span> <span data-ttu-id="79b6b-216">欄位名稱及/或程式碼屬性決定模型定型和預測期間所用的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="79b6b-216">The field names and/or code attributes determine the names of the data columns used during model training and prediction.</span></span> <span data-ttu-id="79b6b-217">您可以閱讀＜做法＞一節中的[如何建立單一預測](./how-to-guides/single-predict-model-ml-net.md)。</span><span class="sxs-lookup"><span data-stu-id="79b6b-217">You can read about  [How to make a single prediction](./how-to-guides/single-predict-model-ml-net.md) in the How-to section.</span></span>

### <a name="data-models-and-schema"></a><span data-ttu-id="79b6b-218">資料模型和結構描述</span><span class="sxs-lookup"><span data-stu-id="79b6b-218">Data models and schema</span></span>

<span data-ttu-id="79b6b-219">ML.NET 機器學習管線的核心是 [DataView](xref:Microsoft.ML.IDataView) 物件。</span><span class="sxs-lookup"><span data-stu-id="79b6b-219">At the core of an ML.NET machine learning pipeline are [DataView](xref:Microsoft.ML.IDataView) objects.</span></span>

<span data-ttu-id="79b6b-220">管線中的每個轉換都有輸入結構描述 (轉換預期在其輸入中看到的資料名稱、類型和大小) 以及輸出結構描述 (轉換在轉換後產生的資料名稱、類型和大小)。</span><span class="sxs-lookup"><span data-stu-id="79b6b-220">Each transformation in the pipeline has an input schema (data names, types, and sizes that the transform expects to see on its input); and an output schema (data names, types, and sizes that the transform produces after the transformation).</span></span> 

<span data-ttu-id="79b6b-221">如果管線中來自轉換之輸出結構描述不符合下一個轉換的輸入結構描述，則 ML.NET 會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="79b6b-221">If the output schema from one transform in the pipeline doesn't match the input schema of the next transform, ML.NET will throw an exception.</span></span>

<span data-ttu-id="79b6b-222">資料檢視物件具有資料行和資料列。</span><span class="sxs-lookup"><span data-stu-id="79b6b-222">A data view object has columns and rows.</span></span> <span data-ttu-id="79b6b-223">每個資料行都有名稱和類型以及長度。</span><span class="sxs-lookup"><span data-stu-id="79b6b-223">Each column has a name and a type and a length.</span></span> <span data-ttu-id="79b6b-224">例如：房價範例的輸入資料行為**大小**和**價格**。</span><span class="sxs-lookup"><span data-stu-id="79b6b-224">For example: the input columns in the house price example are **Size** and **Price**.</span></span> <span data-ttu-id="79b6b-225">它們都是類型，其數量為純量而非向量。</span><span class="sxs-lookup"><span data-stu-id="79b6b-225">They are both type  and they are scalar quantities rather than vector ones.</span></span>

   ![具有房價預測資料的 ML.NET 資料檢視範例](./media/ml-net-dataview.png)

<span data-ttu-id="79b6b-227">所有 ML.NET 演算法都在尋找向量的輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="79b6b-227">All ML.NET algorithms look for an input column that is a vector.</span></span> <span data-ttu-id="79b6b-228">根據預設，此向量資料行稱為**特性**。</span><span class="sxs-lookup"><span data-stu-id="79b6b-228">By default this vector column is called **Features**.</span></span> <span data-ttu-id="79b6b-229">這就是為什麼我們要在房價範例中，把 [大小]  資料行串連到稱為 [特性]  的新資料行。</span><span class="sxs-lookup"><span data-stu-id="79b6b-229">This is why we concatenated the **Size** column into a new column called **Features** in our house price example.</span></span>

 ```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
 ```

<span data-ttu-id="79b6b-230">所有演算法也都會在執行預測之後，建立新的資料行。</span><span class="sxs-lookup"><span data-stu-id="79b6b-230">All algorithms also create new columns after they have performed a prediction.</span></span> <span data-ttu-id="79b6b-231">這些新資料行的固定名稱取決於機器學習演算法類型。</span><span class="sxs-lookup"><span data-stu-id="79b6b-231">The fixed names of these new columns depend on the type of machine learning algorithm.</span></span> <span data-ttu-id="79b6b-232">若為迴歸工作，其中一個新資料行稱為 [分數]  。</span><span class="sxs-lookup"><span data-stu-id="79b6b-232">For the regression task, one of the new columns is called **Score**.</span></span> <span data-ttu-id="79b6b-233">這就是為什麼我們要使用這個名稱作為價格資料的屬性。</span><span class="sxs-lookup"><span data-stu-id="79b6b-233">This is why we attributed our price data with this name.</span></span>

```csharp
    public class Prediction
    {
        [ColumnName("Score")]
        public float Price { get; set; }
    }
```    

<span data-ttu-id="79b6b-234">您可以在[機器學習工作](resources/tasks.md)指南中深入了解不同機器學習工作的輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="79b6b-234">You can find out more about output columns of different machine learning tasks in the [Machine Learning Tasks](resources/tasks.md) guide.</span></span>

<span data-ttu-id="79b6b-235">DataView 物件的重要屬性是它們都**延遲**評估。</span><span class="sxs-lookup"><span data-stu-id="79b6b-235">An important property of DataView objects is that they are evaluated **lazily**.</span></span> <span data-ttu-id="79b6b-236">資料檢視只會在模型定型和評估期間以及資料預測期間載入及操作。</span><span class="sxs-lookup"><span data-stu-id="79b6b-236">Data views are only loaded and operated on during model training and evaluation, and data prediction.</span></span> <span data-ttu-id="79b6b-237">當您撰寫和測試 ML.NET 應用程式時，您可以呼叫 [Preview](xref:Microsoft.ML.DebuggerExtensions.Preview*) 方法，使用 Visual Studio 偵錯工具看一下任何資料檢視物件。</span><span class="sxs-lookup"><span data-stu-id="79b6b-237">While you are writing and testing your ML.NET application, you can use the Visual Studio debugger to take a peek at any data view object by calling the [Preview](xref:Microsoft.ML.DebuggerExtensions.Preview*) method.</span></span>

```csharp
    var debug = testPriceDataView.Preview();
```

<span data-ttu-id="79b6b-238">您可以在偵錯工具中觀看 `debug` 變數，並檢查其內容。</span><span class="sxs-lookup"><span data-stu-id="79b6b-238">You can watch the `debug` variable in the debugger and examine its contents.</span></span> <span data-ttu-id="79b6b-239">請勿在實際程式碼中使用 Preview 方法，因為它會大幅降低效能。</span><span class="sxs-lookup"><span data-stu-id="79b6b-239">Do not use the Preview method in production code, as it significantly degrades performance.</span></span>

### <a name="model-deployment"></a><span data-ttu-id="79b6b-240">模型部署</span><span class="sxs-lookup"><span data-stu-id="79b6b-240">Model Deployment</span></span>

<span data-ttu-id="79b6b-241">在實際的應用程式中，您的模型定型和評估程式碼與預測無關。</span><span class="sxs-lookup"><span data-stu-id="79b6b-241">In real-life applications, your model training and evaluation code will be separate from your prediction.</span></span> <span data-ttu-id="79b6b-242">事實上，這兩項活動通常是由不同的小組執行。</span><span class="sxs-lookup"><span data-stu-id="79b6b-242">In fact, these two activities are often performed by separate teams.</span></span> <span data-ttu-id="79b6b-243">您的模型開發小組可以儲存模型，供預測應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="79b6b-243">Your model development team can save the model for use in the prediction application.</span></span>

```csharp   
   mlContext.Model.Save(model, trainingData.Schema,"model.zip");
```

## <a name="where-to-now"></a><span data-ttu-id="79b6b-244">接下來去哪？</span><span class="sxs-lookup"><span data-stu-id="79b6b-244">Where to now?</span></span>

<span data-ttu-id="79b6b-245">您可以在[教學課程](./tutorials/index.md)中了解如何使用不同機器學習工作搭配更實際的資料集來建置應用程式。</span><span class="sxs-lookup"><span data-stu-id="79b6b-245">You can learn how to build applications using different machine learning tasks with more realistic data sets in the [tutorials](./tutorials/index.md).</span></span>

<span data-ttu-id="79b6b-246">或者您可以在[操作指南](./how-to-guides/index.md)中深入了解特定的主題。</span><span class="sxs-lookup"><span data-stu-id="79b6b-246">Or you can learn about specific topics in more depth in the [How To Guides](./how-to-guides/index.md).</span></span>

<span data-ttu-id="79b6b-247">如果您很急切，您可以直接深入 [API 參考文件](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet)！</span><span class="sxs-lookup"><span data-stu-id="79b6b-247">And if you're super keen, you can dive straight into the [API Reference documentation](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet)!</span></span>
