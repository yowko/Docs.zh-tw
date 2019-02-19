---
title: ML.NET 模型定型的基本概念
description: 本文章說明的基本概念涵蓋 ML.NET 中的*模型定型*情節。 並非所有概念都與*使用現有模型進行預測*的更簡單情節相關。
ms.date: 02/13/2019
ms.topic: overview
ms.custom: mvc
ms.openlocfilehash: c47d5832527dca1416abfc55756dca48f1daf493
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2019
ms.locfileid: "56303656"
---
# <a name="basic-concepts-for-model-training-in-mlnet"></a><span data-ttu-id="c4836-104">ML.NET 模型定型的基本概念</span><span class="sxs-lookup"><span data-stu-id="c4836-104">Basic concepts for model training in ML.NET</span></span>

<span data-ttu-id="c4836-105">本文章說明的基本概念涵蓋 ML.NET 中的*模型定型*情節。</span><span class="sxs-lookup"><span data-stu-id="c4836-105">This article explains the basic concepts covering *model training* scenarios in ML.NET.</span></span> <span data-ttu-id="c4836-106">並非所有概念都與「使用現有模型進行預測」的更簡單案例相關。</span><span class="sxs-lookup"><span data-stu-id="c4836-106">Not all concepts are relevant to the more simple scenario of *prediction with an existing model*.</span></span>

## <a name="model-training-concepts"></a><span data-ttu-id="c4836-107">模型定型概念</span><span class="sxs-lookup"><span data-stu-id="c4836-107">Model training concepts</span></span>

<span data-ttu-id="c4836-108">本文件涵蓋下列與 ML.NET 模型定型相關的概念：</span><span class="sxs-lookup"><span data-stu-id="c4836-108">This document covers the following concepts related to model training in ML.NET:</span></span>

- <span data-ttu-id="c4836-109">[*資料*](#data)，以 `IDataView` 介面表示。</span><span class="sxs-lookup"><span data-stu-id="c4836-109">[*Data*](#data) represented as an `IDataView` interface.</span></span>
  - <span data-ttu-id="c4836-110">在 ML.NET 中，資料相當於 SQL 檢視：它是延遲評估、不可變、可支援資料指標、異質性、結構描述化的資料集。</span><span class="sxs-lookup"><span data-stu-id="c4836-110">In ML.NET, data is similar to a SQL view: It's a lazily evaluated, immutable, cursorable, heterogenous, schematized dataset.</span></span> 
  - <span data-ttu-id="c4836-111">有關資料介面的絕佳文件是 [IDataView 設計原則](https://github.com/dotnet/machinelearning/blob/master/docs/code/IDataViewDesignPrinciples.md)。</span><span class="sxs-lookup"><span data-stu-id="c4836-111">An excellent document about the data interface is [IDataView Design Principles](https://github.com/dotnet/machinelearning/blob/master/docs/code/IDataViewDesignPrinciples.md).</span></span>
- <span data-ttu-id="c4836-112">[*轉換器* ](#transformer)，以 `ITransformer` 介面表示。</span><span class="sxs-lookup"><span data-stu-id="c4836-112">[*Transformer*](#transformer) represented as `ITransformer` interface.</span></span>
  - <span data-ttu-id="c4836-113">轉換器是一種元件，其會取得資料、對其執行一些運作，並傳回新的轉換資料。</span><span class="sxs-lookup"><span data-stu-id="c4836-113">A transformer is a component that takes data, does some work on it, and returns new transformed data.</span></span>
  - <span data-ttu-id="c4836-114">例如，您可以將機器學習模型視為取得功能並傳回預測的轉換器。</span><span class="sxs-lookup"><span data-stu-id="c4836-114">For example, you can think of a machine learning model as a transformer that takes features and returns predictions.</span></span>
  - <span data-ttu-id="c4836-115">另一個範例是文字權杖化工具，其會取得單一文字資料行，並輸出向量資料行，其中具有從文字中擷取的個別文字。</span><span class="sxs-lookup"><span data-stu-id="c4836-115">Another example, text tokenizer takes a single text column and outputs a vector column with individual words extracted out of the texts.</span></span>
- <span data-ttu-id="c4836-116">[*資料讀取器*](#data-reader)，以 `IDataReader<T>` 介面表示。</span><span class="sxs-lookup"><span data-stu-id="c4836-116">[*Data reader*](#data-reader) represented as an `IDataReader<T>` interface.</span></span>
  - <span data-ttu-id="c4836-117">資料讀取器是用來建立資料的 ML.NET 元件。</span><span class="sxs-lookup"><span data-stu-id="c4836-117">The data reader is ML.NET component to create data.</span></span> <span data-ttu-id="c4836-118">它會取得 `T` 的執行個體，並傳回其中資料。</span><span class="sxs-lookup"><span data-stu-id="c4836-118">It takes an instance of `T` and returns data out of it.</span></span> 
  - <span data-ttu-id="c4836-119">例如，*TextLoader* 是 `IDataReader<IMultiStreamSource>`。</span><span class="sxs-lookup"><span data-stu-id="c4836-119">For example, a *TextLoader* is an `IDataReader<IMultiStreamSource>`.</span></span> <span data-ttu-id="c4836-120">它會取得來源並產生資料。</span><span class="sxs-lookup"><span data-stu-id="c4836-120">It takes the source and produces data.</span></span> 
- <span data-ttu-id="c4836-121">[*評估工具*](#estimator)，以 `IEstimator<T>` 介面表示。</span><span class="sxs-lookup"><span data-stu-id="c4836-121">[*Estimator*](#estimator) represented as an `IEstimator<T>` interface.</span></span>
  - <span data-ttu-id="c4836-122">這是從資料學習的物件。</span><span class="sxs-lookup"><span data-stu-id="c4836-122">This is an object that learns from data.</span></span> <span data-ttu-id="c4836-123">學習的結果是*轉換器*。</span><span class="sxs-lookup"><span data-stu-id="c4836-123">The result of the learning is a *transformer*.</span></span>
  - <span data-ttu-id="c4836-124">您可以將機器學習*演算法*視為評估工具，其會根據資料學習，並產生機器學習*模型*。</span><span class="sxs-lookup"><span data-stu-id="c4836-124">You can think of a machine learning *algorithm* as an estimator that learns on data and produces a machine learning *model*.</span></span>
- <span data-ttu-id="c4836-125">[*預測函數*](#prediction-function)，以 `PredictionEngine<TSrc, TDst>` 類別表示。</span><span class="sxs-lookup"><span data-stu-id="c4836-125">[*Prediction function*](#prediction-function) represented as a `PredictionEngine<TSrc, TDst>` class.</span></span>
  - <span data-ttu-id="c4836-126">預測函數可以視為將轉換器套用至某個資料列 (例如預測時間) 的機器。</span><span class="sxs-lookup"><span data-stu-id="c4836-126">The prediction function can be seen as a machine that applies a transformer to one row, such as at prediction time.</span></span>

## <a name="data"></a><span data-ttu-id="c4836-127">資料</span><span class="sxs-lookup"><span data-stu-id="c4836-127">Data</span></span>

<span data-ttu-id="c4836-128">在 ML.NET 中，資料相當於 SQL 檢視：它是延遲評估、可支援資料指標、異質性、結構描述化的資料集。</span><span class="sxs-lookup"><span data-stu-id="c4836-128">In ML.NET, data is similar to a SQL view: It's a lazily evaluated, cursorable, heterogenous, schematized dataset.</span></span>

- <span data-ttu-id="c4836-129">它具有*結構描述* (`ISchema` 介面的執行個體)，其中包含資料檢視資料行的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c4836-129">It has *Schema* (an instance of an `ISchema` interface) that contains the information about the data view's columns.</span></span>
  - <span data-ttu-id="c4836-130">每個資料行都有*名稱*、*類型*，以及任意一組與其相關聯的*中繼資料*。</span><span class="sxs-lookup"><span data-stu-id="c4836-130">Each column has a *Name*, a *Type*, and an arbitrary set of *metadata* associated with it.</span></span>
  - <span data-ttu-id="c4836-131">資料行的*中繼資料*包含像是向量資料行的插槽名稱這類資訊。</span><span class="sxs-lookup"><span data-stu-id="c4836-131">The column's *metadata* contains information like slot names of a vector column and the like.</span></span> <span data-ttu-id="c4836-132">中繼資料本身是以另一個一列*資料*表示，此資料對於每個資料行都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="c4836-132">The metadata itself is represented as another one-row *data* that is unique to each column.</span></span>
  - <span data-ttu-id="c4836-133">資料檢視是*資料指標*的來源。</span><span class="sxs-lookup"><span data-stu-id="c4836-133">The data view is a source of *cursors*.</span></span> <span data-ttu-id="c4836-134">想想 SQL 資料指標：資料指標是一種物件，其會逐一查看資料，一次一個資料列，並呈現可用資料。</span><span class="sxs-lookup"><span data-stu-id="c4836-134">Think SQL cursors: A cursor is an object that iterates through the data, one row at a time, and presents the available data.</span></span>
  - <span data-ttu-id="c4836-135">當然，資料可以視需要具有多個作用中的資料指標。</span><span class="sxs-lookup"><span data-stu-id="c4836-135">Naturally, data can have as many active cursors over it as needed.</span></span> <span data-ttu-id="c4836-136">由於資料本身不可變，因此資料指標是真正獨立的。</span><span class="sxs-lookup"><span data-stu-id="c4836-136">Since data itself is immutable, cursors are truly independent.</span></span>
  - <span data-ttu-id="c4836-137">資料指標通常只會存取資料行子集：為了提高效率，ML.NET 只會計算資料指標所需的資料行值。</span><span class="sxs-lookup"><span data-stu-id="c4836-137">Cursors typically access only a subset of columns: For efficiency, ML.NET computes only the values of columns that are needed by the cursor.</span></span>

## <a name="transformer"></a><span data-ttu-id="c4836-138">轉換器</span><span class="sxs-lookup"><span data-stu-id="c4836-138">Transformer</span></span>

<span data-ttu-id="c4836-139">轉換器是一種元件，其會取得資料、對其執行一些運作，並傳回新的轉換資料。</span><span class="sxs-lookup"><span data-stu-id="c4836-139">A transformer is a component that takes data, does some work on it, and returns new transformed data.</span></span>

<span data-ttu-id="c4836-140">ML.NET 中大部分的轉換器傾向於一次操作一個*輸入資料行*，以及產生*輸出資料行*。</span><span class="sxs-lookup"><span data-stu-id="c4836-140">Most transformers in ML.NET tend to operate on one *input column* at a time, and produce the *output column*.</span></span> <span data-ttu-id="c4836-141">例如，`new HashTransformer("bar", "foo")` 會從資料行 "foo" 取得值、將其雜湊，並將它們放入資料行 "bar" 中。</span><span class="sxs-lookup"><span data-stu-id="c4836-141">For example, a `new HashTransformer("bar", "foo")` takes the values from column "foo", hashes them, and puts them into column "bar".</span></span> 

<span data-ttu-id="c4836-142">輸入和輸出資料行名稱相同也是很常見的。</span><span class="sxs-lookup"><span data-stu-id="c4836-142">It's also common that the input and output column names are the same.</span></span> <span data-ttu-id="c4836-143">在此情況下，舊資料行會取代為新資料行。</span><span class="sxs-lookup"><span data-stu-id="c4836-143">In this case, the old column is replaced with the new one.</span></span> <span data-ttu-id="c4836-144">例如，`new HashTransformer("foo")` 會從資料行 "foo" 取得值、將其雜湊，並將它們放回資料行 "foo" 中。</span><span class="sxs-lookup"><span data-stu-id="c4836-144">For example, a `new HashTransformer("foo")` takes the values from column "foo", hashes them, and puts them back into "foo".</span></span> 

<span data-ttu-id="c4836-145">在呼叫 `Transform` 時，任何轉換器都會產生新的資料檢視。</span><span class="sxs-lookup"><span data-stu-id="c4836-145">Any transformer, produces a new data view when `Transform` is called.</span></span> <span data-ttu-id="c4836-146">請記住，資料檢視是不可變的。</span><span class="sxs-lookup"><span data-stu-id="c4836-146">Remember, data views are immutable.</span></span>

<span data-ttu-id="c4836-147">另一個重要考量是，因為資料會延遲評估，所以*轉換器也會延遲執行*。</span><span class="sxs-lookup"><span data-stu-id="c4836-147">Another important consideration is that, because data is lazily evaluated, *transformers are lazy too*.</span></span> <span data-ttu-id="c4836-148">基本上，在您呼叫之後</span><span class="sxs-lookup"><span data-stu-id="c4836-148">Essentially, after you call</span></span>

```csharp
var newData = transformer.Transform(oldData)
```

<span data-ttu-id="c4836-149">沒有實際計算發生。</span><span class="sxs-lookup"><span data-stu-id="c4836-149">no actual computation happens.</span></span> <span data-ttu-id="c4836-150">只有在您從 `newData` 取得資料指標，並開始使用值之後，`newData` 才會叫用 `transformer` 轉換邏輯 (即使如此，只會在需要問題中的 `transformer` 時，才會發生此情況，以產生所要求的資料行)。</span><span class="sxs-lookup"><span data-stu-id="c4836-150">Only after you get a cursor from `newData` and start consuming the value does `newData` invoke the `transformer` transformation logic (and even then, it only happens if the `transformer` in question is needed to produce the requested columns).</span></span>

### <a name="transformer-chains"></a><span data-ttu-id="c4836-151">轉換器鏈結</span><span class="sxs-lookup"><span data-stu-id="c4836-151">Transformer chains</span></span>

<span data-ttu-id="c4836-152">轉換器有個很有用的屬性，「您可以將轉換器的循序應用程式建置為另一個轉換器」：</span><span class="sxs-lookup"><span data-stu-id="c4836-152">A useful property of a transformer is that *you can build a sequential application of transformers as yet another transformer*:</span></span>

```csharp
var fullTransformer = transformer1.Append(transformer2).Append(transformer3);
```

<span data-ttu-id="c4836-153">此屬性常用於 ML.NET：通常，定型的 ML.NET 模型是轉換器的鏈結，亦即，基於所有意圖和目的，視為一個*轉換器*。</span><span class="sxs-lookup"><span data-stu-id="c4836-153">This property is commonly used in ML.NET: typically, the trained ML.NET model is a chain of transformers, which is, for all intents and purposes, a *transformer*.</span></span>

## <a name="data-reader"></a><span data-ttu-id="c4836-154">資料讀取器</span><span class="sxs-lookup"><span data-stu-id="c4836-154">Data reader</span></span>

<span data-ttu-id="c4836-155">資料讀取器是用來「建立」資料的 ML.NET 元件：它會取得 `T` 的執行個體，並傳回其中資料。</span><span class="sxs-lookup"><span data-stu-id="c4836-155">The data reader is an ML.NET component to 'create' data: it takes an instance of `T` and returns data out of it.</span></span>

<span data-ttu-id="c4836-156">需要注意的有趣屬性是，您可以將轉換器附加至現有的資料讀取器來建立資料讀取器。</span><span class="sxs-lookup"><span data-stu-id="c4836-156">An interesting property to note is that you can create a data reader by attaching a transformer to an existing data reader.</span></span> <span data-ttu-id="c4836-157">如此一來，您可以具有轉換行為加入其中的讀取器：</span><span class="sxs-lookup"><span data-stu-id="c4836-157">This way you can have a reader with transformation behavior baked in:</span></span>

```csharp
var newReader = reader.Append(transformer1).Append(transformer2)
```

<span data-ttu-id="c4836-158">轉換器的另一個類似之處是，因為資料會延遲評估，所以*讀取器會延遲執行*：呼叫 `reader.Read()` 時，沒有 (或最少) 實際「讀取」發生：僅在產生的資料要求資料指標時，讀取器才會開始運作。</span><span class="sxs-lookup"><span data-stu-id="c4836-158">Another similarity to transformers is that, since data is lazily evaluated, *readers are lazy*: no (or minimal) actual 'reading' happens when you call `reader.Read()`: only when a cursor is requested on the resulting data does the reader begin to work.</span></span>

## <a name="estimator"></a><span data-ttu-id="c4836-159">評估工具</span><span class="sxs-lookup"><span data-stu-id="c4836-159">Estimator</span></span>

<span data-ttu-id="c4836-160">*評估工具*是從資料學習的物件。</span><span class="sxs-lookup"><span data-stu-id="c4836-160">The *estimator* is an object that learns from data.</span></span> <span data-ttu-id="c4836-161">學習的結果是*轉換器*。</span><span class="sxs-lookup"><span data-stu-id="c4836-161">The result of the learning is a *transformer*.</span></span>

<span data-ttu-id="c4836-162">在 ML.NET 中，使用此屬性來建立學習管線，將不同的評估工具鏈結在一起：</span><span class="sxs-lookup"><span data-stu-id="c4836-162">In ML.NET, use this property to create learning pipelines that chain together different estimators:</span></span>

```csharp
MLContext mlContext = new MLContext(seed: 0);

var pipeline = mlContext.Transforms.CopyColumns("Label","FareAmount")
    .Append(mlContext.Transforms.Categorical.OneHotEncoding("VendorId"))
    .Append(mlContext.Transforms.Categorical.OneHotEncoding("RateCode"))
    .Append(mlContext.Transforms.Categorical.OneHotEncoding("PaymentType"))
    .Append(mlContext.Transforms.Concatenate("Features","VendorId","RateCode","PassengerCount","TripTime","TripDistance","PaymentType"))
    .Append(mlContext.Regression.Trainers.FastTree("Label","Features"));

var model = pipeline.Fit(dataView);
```

<span data-ttu-id="c4836-163">評估工具的一個重要屬性是，*評估工具是積極的，而不會延遲*：每次呼叫 `Fit` 都會導致學習發生，這可能是耗時作業。</span><span class="sxs-lookup"><span data-stu-id="c4836-163">One important property of estimators is that *estimators are eager, not lazy*: every call to `Fit` is causing learning to happen, which is potentially a time-consuming operation.</span></span>

## <a name="prediction-function"></a><span data-ttu-id="c4836-164">預測函數</span><span class="sxs-lookup"><span data-stu-id="c4836-164">Prediction function</span></span>

<span data-ttu-id="c4836-165">預測函式可以視為將轉換器套用至某個資料列的元件。</span><span class="sxs-lookup"><span data-stu-id="c4836-165">The prediction function can be seen as a component that applies a transformer to one row.</span></span>

<span data-ttu-id="c4836-166">一旦您取得模型 (透過 `Fit()` 定型或從某處載入的 *轉換器*)，就可以使用它，正常呼叫 `model.Transform(data)` 來進行預測。</span><span class="sxs-lookup"><span data-stu-id="c4836-166">Once you get the model (a *transformer* either trained via `Fit()`, or loaded from somewhere), you can use it to make predictions using the normal calls to `model.Transform(data)`.</span></span> <span data-ttu-id="c4836-167">不過，當您在真實情節中使用此模型時，通常沒有很多範例做為預測依據。</span><span class="sxs-lookup"><span data-stu-id="c4836-167">However, when you use this model in a real-life scenario, you often don't have many examples to predict on.</span></span> <span data-ttu-id="c4836-168">反之，您一次有一個範例，因此您需要立即對它們做出及時預測。</span><span class="sxs-lookup"><span data-stu-id="c4836-168">Instead, you have one example at a time, and you need to make timely predictions on them immediately.</span></span>

<span data-ttu-id="c4836-169">當然，您可以將此縮小為批次預測：</span><span class="sxs-lookup"><span data-stu-id="c4836-169">Of course, you can reduce this to the batch prediction:</span></span>

- <span data-ttu-id="c4836-170">建立只有一個資料列的資料檢視。</span><span class="sxs-lookup"><span data-stu-id="c4836-170">Create a data view with exactly one row.</span></span>
- <span data-ttu-id="c4836-171">呼叫 `model.Transform(data)` 來取得預測的資料檢視。</span><span class="sxs-lookup"><span data-stu-id="c4836-171">Call `model.Transform(data)` to get the predicted data view.</span></span>
- <span data-ttu-id="c4836-172">透過產生的資料取得資料指標。</span><span class="sxs-lookup"><span data-stu-id="c4836-172">Get a cursor over the resulting data.</span></span>
- <span data-ttu-id="c4836-173">將資料指標前進一步，以到達第一個 (且唯一的) 資料列。</span><span class="sxs-lookup"><span data-stu-id="c4836-173">Advance the cursor one step to get to the first (and only) row.</span></span>
- <span data-ttu-id="c4836-174">從中擷取預測值。</span><span class="sxs-lookup"><span data-stu-id="c4836-174">Extract the predicted values out of it.</span></span>

<span data-ttu-id="c4836-175">實作上述演算法的方法為，使用[結構描述理解](https://github.com/dotnet/machinelearning/blob/master/docs/code/SchemaComprehension.md)與兩個使用者定義的物件 `InputExample` 和 `OutputPrediction` 搭配，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c4836-175">The preceding algorithm can be implemented using the [schema comprehension](https://github.com/dotnet/machinelearning/blob/master/docs/code/SchemaComprehension.md), with two user-defined objects `InputExample` and `OutputPrediction` as follows:</span></span>

```csharp
var inputData = mlContext.Data.ReadFromEnumerable(new InputExample[] { example });
var outputData = model.Transform(inputData);
var output = mlContext.CreateEnumerable<OutputPrediction>(outputData,reuseRowObject:false).First();
```

<span data-ttu-id="c4836-176">但這樣做很麻煩，且會產生效能成本。</span><span class="sxs-lookup"><span data-stu-id="c4836-176">But this is cumbersome and incurs performance costs.</span></span> <span data-ttu-id="c4836-177">反之，預測函數物件可透過擴充方法 `CreatePredictionEngine` 執行相同工作，但更快速且更方便：</span><span class="sxs-lookup"><span data-stu-id="c4836-177">Instead, a prediction function object performs the same work, but faster and more convenient, via an extension method `CreatePredictionEngine`:</span></span>

```csharp
var predictionEngine = model.CreatePredictionEngine<InputExample,OutputPrediction>(mlContext);
var prediction = predictionEngine.Predict(example);
```

<span data-ttu-id="c4836-178">預測函數是*不可重入的/安全執行緒*。</span><span class="sxs-lookup"><span data-stu-id="c4836-178">The prediction function is *not re-entrant / thread-safe*.</span></span> <span data-ttu-id="c4836-179">如果您想要同時使用多個執行緒進行預測，則需要每個執行緒具有一個預測函數。</span><span class="sxs-lookup"><span data-stu-id="c4836-179">If you want to conduct predictions simultaneously with multiple threads, you need to have a prediction function per thread.</span></span>
