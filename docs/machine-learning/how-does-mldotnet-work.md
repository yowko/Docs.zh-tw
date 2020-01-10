---
title: 什麼是 ML.NET，它如何運作？
description: 不論是在線上或是離線，ML.NET 都能讓您將機器學習新增至 .NET 應用程式。 使用此功能，您可以使用應用程式可用的資料來建立自動預測，而不需要連線至網路來使用 ML.NET。 本文說明 ML.NET 的機器學習基本概念。
ms.date: 11/5/2019
ms.topic: overview
ms.custom: mvc
ms.openlocfilehash: 98251c39a4bdaba8203c26c6a781a86efc46efa4
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740089"
---
# <a name="what-is-mlnet-and-how-does-it-work"></a><span data-ttu-id="0f892-105">什麼是 ML.NET，它如何運作？</span><span class="sxs-lookup"><span data-stu-id="0f892-105">What is ML.NET and how does it work?</span></span>

<span data-ttu-id="0f892-106">不論是在線上或是離線，ML.NET 都能讓您將機器學習新增至 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="0f892-106">ML.NET gives you the ability to add machine learning to .NET applications, in either online or offline scenarios.</span></span> <span data-ttu-id="0f892-107">使用這項功能，您可以使用應用程式可用的資料來建立自動預測。</span><span class="sxs-lookup"><span data-stu-id="0f892-107">With this capability, you can make automatic predictions using the data available to your application.</span></span>

<span data-ttu-id="0f892-108">ML.NET 的核心是機器學習**模型**。</span><span class="sxs-lookup"><span data-stu-id="0f892-108">Central to ML.NET is a machine learning **model**.</span></span> <span data-ttu-id="0f892-109">模型會指定將輸入資料轉換成預測所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="0f892-109">The model specifies the steps needed to transform your input data into a prediction.</span></span> <span data-ttu-id="0f892-110">透過 ML.NET，您可以藉由指定演算法來定型自訂模型，或者您也可以匯入預先定型的 TensorFlow 和 ONNX 模型。</span><span class="sxs-lookup"><span data-stu-id="0f892-110">With ML.NET, you can train a custom model by specifying an algorithm, or you can import pre-trained TensorFlow and ONNX models.</span></span>

<span data-ttu-id="0f892-111">一旦有了模型之後，您就可以將它新增至您的應用程式以進行預測。</span><span class="sxs-lookup"><span data-stu-id="0f892-111">Once you have a model, you can add it to your application to make the predictions.</span></span>

<span data-ttu-id="0f892-112">ML.NET 會使用 .NET Core，或使用 .NET Framework 在 windows、Linux 和 macOS 上執行。</span><span class="sxs-lookup"><span data-stu-id="0f892-112">ML.NET runs on Windows, Linux, and macOS using .NET Core, or Windows using .NET Framework.</span></span> <span data-ttu-id="0f892-113">所有平臺都支援64位。</span><span class="sxs-lookup"><span data-stu-id="0f892-113">64 bit is supported on all platforms.</span></span> <span data-ttu-id="0f892-114">Windows 上支援32位，但 TensorFlow、LightGBM 和 ONNX 相關的功能除外。</span><span class="sxs-lookup"><span data-stu-id="0f892-114">32 bit is supported on Windows, except for TensorFlow, LightGBM, and ONNX-related functionality.</span></span>

<span data-ttu-id="0f892-115">您可以使用 ML.NET 進行的預測類型範例：</span><span class="sxs-lookup"><span data-stu-id="0f892-115">Examples of the type of predictions that you can make with ML.NET:</span></span>

|||
|-|-|
|<span data-ttu-id="0f892-116">分類/分類</span><span class="sxs-lookup"><span data-stu-id="0f892-116">Classification/Categorization</span></span>|<span data-ttu-id="0f892-117">自動將客戶的意見反應分成正負類別</span><span class="sxs-lookup"><span data-stu-id="0f892-117">Automatically divide customer feedback into positive and negative categories</span></span>|
|<span data-ttu-id="0f892-118">迴歸/預測連續值</span><span class="sxs-lookup"><span data-stu-id="0f892-118">Regression/Predict continuous values</span></span>|<span data-ttu-id="0f892-119">根據大小和位置預測房價</span><span class="sxs-lookup"><span data-stu-id="0f892-119">Predict the price of houses based on size and location</span></span>|
|<span data-ttu-id="0f892-120">異常偵測</span><span class="sxs-lookup"><span data-stu-id="0f892-120">Anomaly Detection</span></span>|<span data-ttu-id="0f892-121">偵測詐騙的銀行交易</span><span class="sxs-lookup"><span data-stu-id="0f892-121">Detect fraudulent banking transactions</span></span> |
|<span data-ttu-id="0f892-122">建議</span><span class="sxs-lookup"><span data-stu-id="0f892-122">Recommendations</span></span>|<span data-ttu-id="0f892-123">根據線上購物者之前的購買記錄，建議他們可能想要購買的產品</span><span class="sxs-lookup"><span data-stu-id="0f892-123">Suggest products that online shoppers may want to buy, based on their previous purchases</span></span>|
|<span data-ttu-id="0f892-124">時間序列/順序資料</span><span class="sxs-lookup"><span data-stu-id="0f892-124">Time series/sequential data</span></span>|<span data-ttu-id="0f892-125">預測氣象/產品銷售</span><span class="sxs-lookup"><span data-stu-id="0f892-125">Forecast the weather/product sales</span></span>|
|<span data-ttu-id="0f892-126">影像分類</span><span class="sxs-lookup"><span data-stu-id="0f892-126">Image classification</span></span>|<span data-ttu-id="0f892-127">分類醫學影像中的 pathologies</span><span class="sxs-lookup"><span data-stu-id="0f892-127">Categorize pathologies in medical images</span></span>|

## <a name="hello-mlnet-world"></a><span data-ttu-id="0f892-128">Hello ML.NET World</span><span class="sxs-lookup"><span data-stu-id="0f892-128">Hello ML.NET World</span></span>

<span data-ttu-id="0f892-129">下列程式碼片段中程式碼會示範最簡單的 ML.NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="0f892-129">The code in the following snippet demonstrates the simplest ML.NET application.</span></span> <span data-ttu-id="0f892-130">此範例會建構線性迴歸模型，使用房子大小及價格資料來預測房價。</span><span class="sxs-lookup"><span data-stu-id="0f892-130">This example constructs a linear regression model to predict house prices using house size and price data.</span></span> 

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

## <a name="code-workflow"></a><span data-ttu-id="0f892-131">程式碼工作流程</span><span class="sxs-lookup"><span data-stu-id="0f892-131">Code workflow</span></span>

<span data-ttu-id="0f892-132">下圖代表應用程式程式碼結構，以及模型開發的反覆程序：</span><span class="sxs-lookup"><span data-stu-id="0f892-132">The following diagram represents the application code structure, as well as the iterative process of model development:</span></span>

- <span data-ttu-id="0f892-133">收集定型資料，並將其載入 **IDataView** 物件</span><span class="sxs-lookup"><span data-stu-id="0f892-133">Collect and load training data into an **IDataView** object</span></span>
- <span data-ttu-id="0f892-134">指定擷取特性的作業管線並套用機器學習演算法</span><span class="sxs-lookup"><span data-stu-id="0f892-134">Specify a pipeline of operations to extract features and apply a machine learning algorithm</span></span>
- <span data-ttu-id="0f892-135">對管線呼叫 **Fit()** 以定型模型</span><span class="sxs-lookup"><span data-stu-id="0f892-135">Train a model by calling **Fit()** on the pipeline</span></span>
- <span data-ttu-id="0f892-136">評估模型並反覆運算來加以改善</span><span class="sxs-lookup"><span data-stu-id="0f892-136">Evaluate the model and iterate to improve</span></span>
- <span data-ttu-id="0f892-137">將模型儲存成二進位格式，供應用程式使用</span><span class="sxs-lookup"><span data-stu-id="0f892-137">Save the model into binary format, for use in an application</span></span>
- <span data-ttu-id="0f892-138">將模型載回至 **ITransformer** 物件</span><span class="sxs-lookup"><span data-stu-id="0f892-138">Load the model back into an **ITransformer** object</span></span>
- <span data-ttu-id="0f892-139">呼叫 **CreatePredictionEngine.Predict()** 以建立預測</span><span class="sxs-lookup"><span data-stu-id="0f892-139">Make predictions by calling **CreatePredictionEngine.Predict()**</span></span>

![ML.NET 應用程式開發流程包括產生資料、開發管線、定型模型、評估模型和使用模型的元件](./media/mldotnet-annotated-workflow.png)

<span data-ttu-id="0f892-141">讓我們稍微深入探討這些概念。</span><span class="sxs-lookup"><span data-stu-id="0f892-141">Let's dig a little deeper into those concepts.</span></span>

## <a name="machine-learning-model"></a><span data-ttu-id="0f892-142">機器學習模型</span><span class="sxs-lookup"><span data-stu-id="0f892-142">Machine learning model</span></span>

<span data-ttu-id="0f892-143">ML.NET 模型是一個物件，包含要對輸入資料執行的轉換，以達成預測的輸出。</span><span class="sxs-lookup"><span data-stu-id="0f892-143">An ML.NET model is an object that contains transformations to perform on your input data to arrive at the predicted output.</span></span>

### <a name="basic"></a><span data-ttu-id="0f892-144">Basic</span><span class="sxs-lookup"><span data-stu-id="0f892-144">Basic</span></span>

<span data-ttu-id="0f892-145">最基本的模型是二維線性迴歸，其中一個持續數量和另一個成正比，如上述的房價範例所示。</span><span class="sxs-lookup"><span data-stu-id="0f892-145">The most basic model is two-dimensional linear regression, where one continuous quantity is proportional to another, as in the house price example above.</span></span>

![使用偏差和加權參數的線性迴歸模型](./media/linear-regression-model.svg)

<span data-ttu-id="0f892-147">此模型就只是：$Price = b + Size \* w$。</span><span class="sxs-lookup"><span data-stu-id="0f892-147">The model is simply: $Price = b + Size \* w$.</span></span> <span data-ttu-id="0f892-148">參數 $b$ 和 $w$ 的評估方式是根據一組 (大小、價格) 對組來調整線條。</span><span class="sxs-lookup"><span data-stu-id="0f892-148">The parameters $b$ and $w$ are estimated by fitting a line on a set of (size, price) pairs.</span></span> <span data-ttu-id="0f892-149">用來尋找模型參數的資料稱為**定型資料**。</span><span class="sxs-lookup"><span data-stu-id="0f892-149">The data used to find the parameters of the model is called **training data**.</span></span> <span data-ttu-id="0f892-150">機器學習模型的輸入稱為**特性**。</span><span class="sxs-lookup"><span data-stu-id="0f892-150">The inputs of a machine learning model are called **features**.</span></span> <span data-ttu-id="0f892-151">在本例中，$Size$ 是唯一的特性。</span><span class="sxs-lookup"><span data-stu-id="0f892-151">In this example, $Size$ is the only feature.</span></span> <span data-ttu-id="0f892-152">用來定型機器學習模型的實況資料稱為**標籤**。</span><span class="sxs-lookup"><span data-stu-id="0f892-152">The ground-truth values used to train a machine learning model are called **labels**.</span></span> <span data-ttu-id="0f892-153">在這裡，定型資料集的 $Price$ 值是標籤。</span><span class="sxs-lookup"><span data-stu-id="0f892-153">Here, the $Price$ values in the training data set are the labels.</span></span>

### <a name="more-complex"></a><span data-ttu-id="0f892-154">更複雜</span><span class="sxs-lookup"><span data-stu-id="0f892-154">More complex</span></span>

<span data-ttu-id="0f892-155">更複雜模型會使用交易的文字描述將財務交易分類成類別。</span><span class="sxs-lookup"><span data-stu-id="0f892-155">A more complex model classifies financial transactions into categories using the transaction text description.</span></span>

<span data-ttu-id="0f892-156">每條交易描述會移除多餘的字詞和字元，並計算字詞和字元組合，細分成一組特性。</span><span class="sxs-lookup"><span data-stu-id="0f892-156">Each transaction description is broken down into a set of features by removing redundant words and characters, and counting word and character combinations.</span></span> <span data-ttu-id="0f892-157">以定型資料中的類別集為基礎，用特性集定型線性模型。</span><span class="sxs-lookup"><span data-stu-id="0f892-157">The feature set is used to train a linear model based on the set of categories in the training data.</span></span> <span data-ttu-id="0f892-158">新描述與定型集中的描述愈相似，愈可能指派給同一分類。</span><span class="sxs-lookup"><span data-stu-id="0f892-158">The more similar a new description is to the ones in the training set, the more likely it will be assigned to the same category.</span></span>

![文字分類模型](./media/text-classification-model.svg)

<span data-ttu-id="0f892-160">房價模型和文字分類模型都是**線性**模型。</span><span class="sxs-lookup"><span data-stu-id="0f892-160">Both the house price model and the text classification model are **linear** models.</span></span> <span data-ttu-id="0f892-161">根據資料本質以及要解決的問題本質，您也可以使用**決策樹**模型、**一般化累加**模型和其他模型。</span><span class="sxs-lookup"><span data-stu-id="0f892-161">Depending on the nature of your data and the problem you are solving, you can also use **decision tree** models, **generalized additive** models, and others.</span></span> <span data-ttu-id="0f892-162">您可以在[任務](./resources/tasks.md)中深入了解模型。</span><span class="sxs-lookup"><span data-stu-id="0f892-162">You can find out more about the models in [Tasks](./resources/tasks.md).</span></span>

## <a name="data-preparation"></a><span data-ttu-id="0f892-163">資料準備</span><span class="sxs-lookup"><span data-stu-id="0f892-163">Data preparation</span></span>

<span data-ttu-id="0f892-164">在大部分的情況下，您所用的資料不適合直接用來定型機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="0f892-164">In most cases, the data that you have available isn't suitable to be used directly to train a machine learning model.</span></span> <span data-ttu-id="0f892-165">原始資料必須先備妥或預先處理，然後才能用來尋找模型的參數。</span><span class="sxs-lookup"><span data-stu-id="0f892-165">The raw data needs to be prepared, or pre-processed, before it can be used to find the parameters of your model.</span></span> <span data-ttu-id="0f892-166">您的資料可能需要從字串值轉換成數值表示。</span><span class="sxs-lookup"><span data-stu-id="0f892-166">Your data may need to be converted from string values to a numerical representation.</span></span> <span data-ttu-id="0f892-167">您的輸入資料中可能有多餘資訊。</span><span class="sxs-lookup"><span data-stu-id="0f892-167">You might have redundant information in your input data.</span></span> <span data-ttu-id="0f892-168">您可能需要縮小或擴充您輸入資料的維度。</span><span class="sxs-lookup"><span data-stu-id="0f892-168">You may need to reduce or expand the dimensions of your input data.</span></span> <span data-ttu-id="0f892-169">您的資料可能需要標準化或調整。</span><span class="sxs-lookup"><span data-stu-id="0f892-169">Your data might need to be normalized or scaled.</span></span>

<span data-ttu-id="0f892-170">[ML.NET 教學課程](./tutorials/index.md)會教導您用於特定機器學習工作之文字、影像、數值和時間序列資料的不同資料處理管線。</span><span class="sxs-lookup"><span data-stu-id="0f892-170">The [ML.NET tutorials](./tutorials/index.md) teach you about different data processing pipelines for text, image, numerical, and time-series data used for specific machine learning tasks.</span></span>

<span data-ttu-id="0f892-171">[如何準備您的資料](./how-to-guides/prepare-data-ml-net.md)會示範如何更廣泛地套用資料準備。</span><span class="sxs-lookup"><span data-stu-id="0f892-171">[How to prepare your data](./how-to-guides/prepare-data-ml-net.md) shows you how to apply data preparation more generally.</span></span>

<span data-ttu-id="0f892-172">您可以在＜資源＞一節中找到所有[可用轉換](./resources/transforms.md)的附錄。</span><span class="sxs-lookup"><span data-stu-id="0f892-172">You can find an appendix of all of the [available transformations](./resources/transforms.md) in the resources section.</span></span>

## <a name="model-evaluation"></a><span data-ttu-id="0f892-173">模型評估</span><span class="sxs-lookup"><span data-stu-id="0f892-173">Model evaluation</span></span>

<span data-ttu-id="0f892-174">定型模型之後，您怎麼知道它對未來的預測有多準？</span><span class="sxs-lookup"><span data-stu-id="0f892-174">Once you have trained your model, how do you know how well it will make future predictions?</span></span> <span data-ttu-id="0f892-175">使用 ML.NET，您可以利用某些新的測試資料來評估模型。</span><span class="sxs-lookup"><span data-stu-id="0f892-175">With ML.NET, you can evaluate your model against some new test data.</span></span>

<span data-ttu-id="0f892-176">每種機器學習工作都有針對測試資料集，用來評估模型正確性和精確度的計量。</span><span class="sxs-lookup"><span data-stu-id="0f892-176">Each type of machine learning task has metrics used to evaluate the accuracy and precision of the model against the test data set.</span></span>

<span data-ttu-id="0f892-177">在房價範例中，我們使用了**迴歸**工作。</span><span class="sxs-lookup"><span data-stu-id="0f892-177">For our house price example, we used the **Regression** task.</span></span> <span data-ttu-id="0f892-178">若要評估模型，請將下列程式碼新增至原始範例。</span><span class="sxs-lookup"><span data-stu-id="0f892-178">To evaluate the model, add the following code to the original sample.</span></span>

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

<span data-ttu-id="0f892-179">評估計量會告訴您錯誤有點低，且預測輸出和測試輸出之間的關聯性很高。</span><span class="sxs-lookup"><span data-stu-id="0f892-179">The evaluation metrics tell you that the error is low-ish, and that correlation between the predicted output and the test output is high.</span></span> <span data-ttu-id="0f892-180">很簡單！</span><span class="sxs-lookup"><span data-stu-id="0f892-180">That was easy!</span></span> <span data-ttu-id="0f892-181">在實際範例中，需要更多微調才能達到良好的模型計量。</span><span class="sxs-lookup"><span data-stu-id="0f892-181">In real examples, it takes more tuning to achieve good model metrics.</span></span>

## <a name="mlnet-architecture"></a><span data-ttu-id="0f892-182">ML.NET 架構</span><span class="sxs-lookup"><span data-stu-id="0f892-182">ML.NET architecture</span></span>

<span data-ttu-id="0f892-183">在本節中，我們要探討 ML.NET 的架構模式。</span><span class="sxs-lookup"><span data-stu-id="0f892-183">In this section, we go through the architectural patterns of ML.NET.</span></span> <span data-ttu-id="0f892-184">如果您是有經驗的 .NET 開發人員，對這些模式有些很熟悉，有些則較不熟悉。</span><span class="sxs-lookup"><span data-stu-id="0f892-184">If you are an experienced .NET developer, some of these patterns will be familiar to you, and some will be less familiar.</span></span> <span data-ttu-id="0f892-185">跟上來一探究竟吧！</span><span class="sxs-lookup"><span data-stu-id="0f892-185">Hold tight, while we dive in!</span></span>

<span data-ttu-id="0f892-186">ML.NET 應用程式以 <xref:Microsoft.ML.MLContext> 物件開始。</span><span class="sxs-lookup"><span data-stu-id="0f892-186">An ML.NET application starts with an <xref:Microsoft.ML.MLContext> object.</span></span> <span data-ttu-id="0f892-187">此單一物件包含**目錄**。</span><span class="sxs-lookup"><span data-stu-id="0f892-187">This singleton object contains **catalogs**.</span></span> <span data-ttu-id="0f892-188">目錄是資料載入儲存、轉換、定型器和模型作業元件的處理站。</span><span class="sxs-lookup"><span data-stu-id="0f892-188">A catalog is a factory for data loading and saving, transforms, trainers, and model operation components.</span></span> <span data-ttu-id="0f892-189">每個目錄物件都有建立不同類型元件的方法：</span><span class="sxs-lookup"><span data-stu-id="0f892-189">Each catalog object has methods to create the different types of components:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="0f892-190">資料載入及儲存</span><span class="sxs-lookup"><span data-stu-id="0f892-190">Data loading and saving</span></span>||<xref:Microsoft.ML.DataOperationsCatalog>||
|<span data-ttu-id="0f892-191">資料準備</span><span class="sxs-lookup"><span data-stu-id="0f892-191">Data preparation</span></span>||<xref:Microsoft.ML.TransformsCatalog>||
|<span data-ttu-id="0f892-192">定型演算法</span><span class="sxs-lookup"><span data-stu-id="0f892-192">Training algorithms</span></span>|<span data-ttu-id="0f892-193">二元分類</span><span class="sxs-lookup"><span data-stu-id="0f892-193">Binary classification</span></span>|<xref:Microsoft.ML.BinaryClassificationCatalog>||
||<span data-ttu-id="0f892-194">多元分類</span><span class="sxs-lookup"><span data-stu-id="0f892-194">Multiclass classification</span></span>|<xref:Microsoft.ML.MulticlassClassificationCatalog>||
||<span data-ttu-id="0f892-195">異常偵測</span><span class="sxs-lookup"><span data-stu-id="0f892-195">Anomaly detection</span></span>|<xref:Microsoft.ML.AnomalyDetectionCatalog>||
||<span data-ttu-id="0f892-196">群集</span><span class="sxs-lookup"><span data-stu-id="0f892-196">Clustering</span></span>|<xref:Microsoft.ML.ClusteringCatalog>||
||<span data-ttu-id="0f892-197">正在預測</span><span class="sxs-lookup"><span data-stu-id="0f892-197">Forecasting</span></span>|<xref:Microsoft.ML.ForecastingCatalog>||
||<span data-ttu-id="0f892-198">排名</span><span class="sxs-lookup"><span data-stu-id="0f892-198">Ranking</span></span>|<xref:Microsoft.ML.RankingCatalog>||
||<span data-ttu-id="0f892-199">回復</span><span class="sxs-lookup"><span data-stu-id="0f892-199">Regression</span></span>|<xref:Microsoft.ML.RegressionCatalog>||
||<span data-ttu-id="0f892-200">建議</span><span class="sxs-lookup"><span data-stu-id="0f892-200">Recommendation</span></span>|<xref:Microsoft.ML.RecommendationCatalog>|<span data-ttu-id="0f892-201">新增 `Microsoft.ML.Recommender` NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="0f892-201">add the `Microsoft.ML.Recommender` NuGet package</span></span>|
||<span data-ttu-id="0f892-202">TimeSeries</span><span class="sxs-lookup"><span data-stu-id="0f892-202">TimeSeries</span></span>|<xref:Microsoft.ML.TimeSeriesCatalog>|<span data-ttu-id="0f892-203">新增 `Microsoft.ML.TimeSeries` NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="0f892-203">add the `Microsoft.ML.TimeSeries` NuGet package</span></span>|
|<span data-ttu-id="0f892-204">模型使用方式</span><span class="sxs-lookup"><span data-stu-id="0f892-204">Model usage</span></span> ||<xref:Microsoft.ML.ModelOperationsCatalog>||

<span data-ttu-id="0f892-205">您可以巡覽至上述每個類別的建立方法。</span><span class="sxs-lookup"><span data-stu-id="0f892-205">You can navigate to the creation methods in each of the above categories.</span></span> <span data-ttu-id="0f892-206">使用 Visual Studio，會透過 IntelliSense 顯示目錄。</span><span class="sxs-lookup"><span data-stu-id="0f892-206">Using Visual Studio, the catalogs show up via IntelliSense.</span></span>

   ![適用於迴歸定型器的 Intellisense](./media/catalog-intellisense.png)

### <a name="build-the-pipeline"></a><span data-ttu-id="0f892-208">建置管線</span><span class="sxs-lookup"><span data-stu-id="0f892-208">Build the pipeline</span></span>

<span data-ttu-id="0f892-209">每個目錄中都是一組擴充方法。</span><span class="sxs-lookup"><span data-stu-id="0f892-209">Inside each catalog is a set of extension methods.</span></span> <span data-ttu-id="0f892-210">讓我們看看如何使用擴充方法建立定型管線。</span><span class="sxs-lookup"><span data-stu-id="0f892-210">Let's look at how extension methods are used to create a training pipeline.</span></span>

```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
        .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));
```

<span data-ttu-id="0f892-211">在程式碼片段中，`Concatenate` 和 `Sdca` 都是目錄中的方法。</span><span class="sxs-lookup"><span data-stu-id="0f892-211">In the snippet, `Concatenate` and `Sdca` are both methods in the catalog.</span></span> <span data-ttu-id="0f892-212">它們會各自建立附加至管線的 [IEstimator](xref:Microsoft.ML.IEstimator%601) 物件。</span><span class="sxs-lookup"><span data-stu-id="0f892-212">They each create an [IEstimator](xref:Microsoft.ML.IEstimator%601) object that is appended to the pipeline.</span></span>

<span data-ttu-id="0f892-213">此時，只會建立物件。</span><span class="sxs-lookup"><span data-stu-id="0f892-213">At this point, the objects are created only.</span></span> <span data-ttu-id="0f892-214">尚未開始執行。</span><span class="sxs-lookup"><span data-stu-id="0f892-214">No execution has happened.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="0f892-215">將模型定型</span><span class="sxs-lookup"><span data-stu-id="0f892-215">Train the model</span></span>

<span data-ttu-id="0f892-216">管線中一旦建立物件，資料就可用來定型模型。</span><span class="sxs-lookup"><span data-stu-id="0f892-216">Once the objects in the pipeline have been created, data can be used to train the model.</span></span>

```csharp
    var model = pipeline.Fit(trainingData);
```

<span data-ttu-id="0f892-217">呼叫 `Fit()` 會使用輸入定型資料來評估模型的參數。</span><span class="sxs-lookup"><span data-stu-id="0f892-217">Calling `Fit()` uses the input training data to estimate the parameters of the model.</span></span> <span data-ttu-id="0f892-218">這就是所謂的「定型」(Training) 模型。</span><span class="sxs-lookup"><span data-stu-id="0f892-218">This is known as training the model.</span></span> <span data-ttu-id="0f892-219">請記住，上述的線性迴歸模型有兩個模型參數：**偏差**和**權數**。</span><span class="sxs-lookup"><span data-stu-id="0f892-219">Remember, the linear regression model above had two model parameters: **bias** and **weight**.</span></span> <span data-ttu-id="0f892-220">呼叫 `Fit()` 之後，即已知參數值。</span><span class="sxs-lookup"><span data-stu-id="0f892-220">After the `Fit()` call, the values of the parameters are known.</span></span> <span data-ttu-id="0f892-221">大部分模型的參數都比這個模型多。</span><span class="sxs-lookup"><span data-stu-id="0f892-221">Most models will have many more parameters than this.</span></span>

<span data-ttu-id="0f892-222">您可以在[如何訓練模型](./how-to-guides/train-machine-learning-model-ml-net.md)中深入瞭解模型定型。</span><span class="sxs-lookup"><span data-stu-id="0f892-222">You can learn more about model training in [How to train your model](./how-to-guides/train-machine-learning-model-ml-net.md).</span></span>

<span data-ttu-id="0f892-223">產生的模型物件會實作 <xref:Microsoft.ML.ITransformer> 介面。</span><span class="sxs-lookup"><span data-stu-id="0f892-223">The resulting model object implements the <xref:Microsoft.ML.ITransformer> interface.</span></span> <span data-ttu-id="0f892-224">亦即，模型會將輸入資料轉換成預測。</span><span class="sxs-lookup"><span data-stu-id="0f892-224">That is, the model transforms input data into predictions.</span></span>

```csharp
   IDataView predictions = model.Transform(inputData);
```

### <a name="use-the-model"></a><span data-ttu-id="0f892-225">使用模型</span><span class="sxs-lookup"><span data-stu-id="0f892-225">Use the model</span></span>

<span data-ttu-id="0f892-226">您可以將大量輸入資料或一次一筆輸入資料轉換成預測。</span><span class="sxs-lookup"><span data-stu-id="0f892-226">You can transform input data into predictions in bulk, or one input at a time.</span></span> <span data-ttu-id="0f892-227">在房價範例中，我們兩種都做了：大量資料是用於評估模型，一次一筆資料則是為了建立新的預測。</span><span class="sxs-lookup"><span data-stu-id="0f892-227">In the house price example, we did both: in bulk for the purpose of evaluating the model, and one at a time to make a new prediction.</span></span> <span data-ttu-id="0f892-228">讓我們看看建立單一預測。</span><span class="sxs-lookup"><span data-stu-id="0f892-228">Let's look at making single predictions.</span></span>

```csharp
    var size = new HouseData() { Size = 2.5F };
    var predEngine = mlContext.CreatePredictionEngine<HouseData, Prediction>(model);
    var price = predEngine.Predict(size);
```

<span data-ttu-id="0f892-229">`CreatePredictionEngine()` 方法接受輸入類別和輸出類別。</span><span class="sxs-lookup"><span data-stu-id="0f892-229">The `CreatePredictionEngine()` method takes an input class and an output class.</span></span> <span data-ttu-id="0f892-230">欄位名稱及/或程式碼屬性決定模型定型和預測期間所用的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="0f892-230">The field names and/or code attributes determine the names of the data columns used during model training and prediction.</span></span> <span data-ttu-id="0f892-231">您可以閱讀＜做法＞一節中的[如何建立單一預測](./how-to-guides/single-predict-model-ml-net.md)。</span><span class="sxs-lookup"><span data-stu-id="0f892-231">You can read about  [How to make a single prediction](./how-to-guides/single-predict-model-ml-net.md) in the How-to section.</span></span>

### <a name="data-models-and-schema"></a><span data-ttu-id="0f892-232">資料模型和結構描述</span><span class="sxs-lookup"><span data-stu-id="0f892-232">Data models and schema</span></span>

<span data-ttu-id="0f892-233">ML.NET 機器學習管線的核心是 [DataView](xref:Microsoft.ML.IDataView) 物件。</span><span class="sxs-lookup"><span data-stu-id="0f892-233">At the core of an ML.NET machine learning pipeline are [DataView](xref:Microsoft.ML.IDataView) objects.</span></span>

<span data-ttu-id="0f892-234">管線中的每個轉換都有輸入結構描述 (轉換預期在其輸入中看到的資料名稱、類型和大小) 以及輸出結構描述 (轉換在轉換後產生的資料名稱、類型和大小)。</span><span class="sxs-lookup"><span data-stu-id="0f892-234">Each transformation in the pipeline has an input schema (data names, types, and sizes that the transform expects to see on its input); and an output schema (data names, types, and sizes that the transform produces after the transformation).</span></span> <span data-ttu-id="0f892-235">下列文件提供 [IDataView 介面及其型別系統](https://xadupre.github.io/machinelearningext/mlnetdocs/idataviewtypesystem.html)的深入說明。</span><span class="sxs-lookup"><span data-stu-id="0f892-235">The following document provides an in-depth explanation of the [IDataView interface and its type system](https://xadupre.github.io/machinelearningext/mlnetdocs/idataviewtypesystem.html).</span></span>

<span data-ttu-id="0f892-236">如果管線中來自轉換之輸出結構描述不符合下一個轉換的輸入結構描述，則 ML.NET 會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0f892-236">If the output schema from one transform in the pipeline doesn't match the input schema of the next transform, ML.NET will throw an exception.</span></span>

<span data-ttu-id="0f892-237">資料檢視物件具有資料行和資料列。</span><span class="sxs-lookup"><span data-stu-id="0f892-237">A data view object has columns and rows.</span></span> <span data-ttu-id="0f892-238">每個資料行都有名稱和類型以及長度。</span><span class="sxs-lookup"><span data-stu-id="0f892-238">Each column has a name and a type and a length.</span></span> <span data-ttu-id="0f892-239">例如，房屋價格範例中的輸入資料行是**大小**和**價格**。</span><span class="sxs-lookup"><span data-stu-id="0f892-239">For example, the input columns in the house price example are **Size** and **Price**.</span></span> <span data-ttu-id="0f892-240">兩者都是型別，而且都是純量數量，而不是向量。</span><span class="sxs-lookup"><span data-stu-id="0f892-240">They are both type and they are scalar quantities rather than vector ones.</span></span>

   ![具有房價預測資料的 ML.NET 資料檢視範例](./media/ml-net-dataview.png)

<span data-ttu-id="0f892-242">所有 ML.NET 演算法都在尋找向量的輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="0f892-242">All ML.NET algorithms look for an input column that is a vector.</span></span> <span data-ttu-id="0f892-243">根據預設，此向量資料行稱為**特性**。</span><span class="sxs-lookup"><span data-stu-id="0f892-243">By default this vector column is called **Features**.</span></span> <span data-ttu-id="0f892-244">這就是為什麼我們要在房價範例中，把 [大小] 資料行串連到稱為 [特性]的新資料行。</span><span class="sxs-lookup"><span data-stu-id="0f892-244">This is why we concatenated the **Size** column into a new column called **Features** in our house price example.</span></span>

 ```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
 ```

<span data-ttu-id="0f892-245">所有演算法也都會在執行預測之後，建立新的資料行。</span><span class="sxs-lookup"><span data-stu-id="0f892-245">All algorithms also create new columns after they have performed a prediction.</span></span> <span data-ttu-id="0f892-246">這些新資料行的固定名稱取決於機器學習演算法類型。</span><span class="sxs-lookup"><span data-stu-id="0f892-246">The fixed names of these new columns depend on the type of machine learning algorithm.</span></span> <span data-ttu-id="0f892-247">若為迴歸工作，其中一個新資料行稱為 [分數]。</span><span class="sxs-lookup"><span data-stu-id="0f892-247">For the regression task, one of the new columns is called **Score**.</span></span> <span data-ttu-id="0f892-248">這就是為什麼我們要使用這個名稱作為價格資料的屬性。</span><span class="sxs-lookup"><span data-stu-id="0f892-248">This is why we attributed our price data with this name.</span></span>

```csharp
    public class Prediction
    {
        [ColumnName("Score")]
        public float Price { get; set; }
    }
```

<span data-ttu-id="0f892-249">您可以在[機器學習工作](resources/tasks.md)指南中深入了解不同機器學習工作的輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="0f892-249">You can find out more about output columns of different machine learning tasks in the [Machine Learning Tasks](resources/tasks.md) guide.</span></span>

<span data-ttu-id="0f892-250">DataView 物件的重要屬性是它們都**延遲**評估。</span><span class="sxs-lookup"><span data-stu-id="0f892-250">An important property of DataView objects is that they are evaluated **lazily**.</span></span> <span data-ttu-id="0f892-251">資料檢視只會在模型定型和評估期間以及資料預測期間載入及操作。</span><span class="sxs-lookup"><span data-stu-id="0f892-251">Data views are only loaded and operated on during model training and evaluation, and data prediction.</span></span> <span data-ttu-id="0f892-252">當您撰寫和測試 ML.NET 應用程式時，您可以呼叫 [Preview](xref:Microsoft.ML.DebuggerExtensions.Preview*) 方法，使用 Visual Studio 偵錯工具看一下任何資料檢視物件。</span><span class="sxs-lookup"><span data-stu-id="0f892-252">While you are writing and testing your ML.NET application, you can use the Visual Studio debugger to take a peek at any data view object by calling the [Preview](xref:Microsoft.ML.DebuggerExtensions.Preview*) method.</span></span>

```csharp
    var debug = testPriceDataView.Preview();
```

<span data-ttu-id="0f892-253">您可以在偵錯工具中觀看 `debug` 變數，並檢查其內容。</span><span class="sxs-lookup"><span data-stu-id="0f892-253">You can watch the `debug` variable in the debugger and examine its contents.</span></span> <span data-ttu-id="0f892-254">請勿在實際程式碼中使用 Preview 方法，因為它會大幅降低效能。</span><span class="sxs-lookup"><span data-stu-id="0f892-254">Do not use the Preview method in production code, as it significantly degrades performance.</span></span>

### <a name="model-deployment"></a><span data-ttu-id="0f892-255">模型部署</span><span class="sxs-lookup"><span data-stu-id="0f892-255">Model Deployment</span></span>

<span data-ttu-id="0f892-256">在實際的應用程式中，您的模型定型和評估程式碼與預測無關。</span><span class="sxs-lookup"><span data-stu-id="0f892-256">In real-life applications, your model training and evaluation code will be separate from your prediction.</span></span> <span data-ttu-id="0f892-257">事實上，這兩項活動通常是由不同的小組執行。</span><span class="sxs-lookup"><span data-stu-id="0f892-257">In fact, these two activities are often performed by separate teams.</span></span> <span data-ttu-id="0f892-258">您的模型開發小組可以儲存模型，供預測應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="0f892-258">Your model development team can save the model for use in the prediction application.</span></span>

```csharp
   mlContext.Model.Save(model, trainingData.Schema,"model.zip");
```

## <a name="next-steps"></a><span data-ttu-id="0f892-259">後續步驟</span><span class="sxs-lookup"><span data-stu-id="0f892-259">Next steps</span></span>

* <span data-ttu-id="0f892-260">瞭解如何使用不同的機器學習工作，在[教學](./tutorials/index.md)課程中搭配更實際的資料集來建立應用程式。</span><span class="sxs-lookup"><span data-stu-id="0f892-260">Learn how to build applications using different machine learning tasks with more realistic data sets in the [tutorials](./tutorials/index.md).</span></span>

* <span data-ttu-id="0f892-261">深入瞭解[如何指南](./how-to-guides/index.md)中的特定主題。</span><span class="sxs-lookup"><span data-stu-id="0f892-261">Learn about specific topics in more depth in the [How To Guides](./how-to-guides/index.md).</span></span>

* <span data-ttu-id="0f892-262">如果您很榮幸，可以直接深入探索[API 參考檔](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet)。</span><span class="sxs-lookup"><span data-stu-id="0f892-262">If you're super keen, you can dive straight into the [API Reference documentation](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet).</span></span>
