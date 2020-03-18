---
title: 教程：使用 TensorFlow 模型分析審核情緒
description: 本教程介紹如何使用預先訓練的 TensorFlow 模型對網站評論中的情緒進行分類。 二進位情緒分類器是使用 Visual Studio 開發的 C# 主控台應用程式。
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 688c5b83cef8f21eef8fa24521a85449a9cfbd48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "78241113"
---
# <a name="tutorial-analyze-sentiment-of-movie-reviews-using-a-pre-trained-tensorflow-model-in-mlnet"></a><span data-ttu-id="fc8c9-104">教程：在ML.NET中使用預先訓練的 TensorFlow 模型分析電影評論的情緒</span><span class="sxs-lookup"><span data-stu-id="fc8c9-104">Tutorial: Analyze sentiment of movie reviews using a pre-trained TensorFlow model in ML.NET</span></span>

<span data-ttu-id="fc8c9-105">本教程介紹如何使用預先訓練的 TensorFlow 模型對網站評論中的情緒進行分類。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-105">This tutorial shows you how to use a pre-trained TensorFlow model to classify sentiment in website comments.</span></span> <span data-ttu-id="fc8c9-106">二進位情緒分類器是使用 Visual Studio 開發的 C# 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-106">The binary sentiment classifier is a C# console application developed using Visual Studio.</span></span>

<span data-ttu-id="fc8c9-107">本教程中使用的 TensorFlow 模型使用 IMDB 資料庫中的電影評論進行了訓練。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-107">The TensorFlow model used in this tutorial was trained using movie reviews from the IMDB database.</span></span> <span data-ttu-id="fc8c9-108">一旦你完成了應用程式的發展，你將能夠提供電影評論文本，應用程式會告訴你，審查是正面的還是負面的情緒。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-108">Once you have finished developing the application, you will be able to supply movie review text and the application will tell you whether the review has positive or negative sentiment.</span></span>

<span data-ttu-id="fc8c9-109">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="fc8c9-109">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="fc8c9-110">載入預先訓練的 TensorFlow 模型</span><span class="sxs-lookup"><span data-stu-id="fc8c9-110">Load a pre-trained TensorFlow model</span></span>
> * <span data-ttu-id="fc8c9-111">將網站評論文本轉換為適合模型的功能</span><span class="sxs-lookup"><span data-stu-id="fc8c9-111">Transform website comment text into features suitable for the model</span></span>
> * <span data-ttu-id="fc8c9-112">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="fc8c9-112">Use the model to make a prediction</span></span>

<span data-ttu-id="fc8c9-113">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fc8c9-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="fc8c9-114">Prerequisites</span></span>

* <span data-ttu-id="fc8c9-115">[Visual Studio 2017 版本 15.6 或更高版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)安裝了".NET 核心跨平臺開發"工作負載。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-115">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="setup"></a><span data-ttu-id="fc8c9-116">安裝程式</span><span class="sxs-lookup"><span data-stu-id="fc8c9-116">Setup</span></span>

### <a name="create-the-application"></a><span data-ttu-id="fc8c9-117">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="fc8c9-117">Create the application</span></span>

1. <span data-ttu-id="fc8c9-118">創建一個稱為"文本分類TF"**的 .NET 核心主控台應用程式**。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-118">Create a **.NET Core Console Application** called "TextClassificationTF".</span></span>

2. <span data-ttu-id="fc8c9-119">在專案中創建名為*Data*的目錄以保存資料集檔。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-119">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="fc8c9-120">安裝「Microsoft.ML NuGet 套件」\*\*\*\*：</span><span class="sxs-lookup"><span data-stu-id="fc8c9-120">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="fc8c9-121">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-121">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="fc8c9-122">選擇"nuget.org"作為包源，然後選擇 **"流覽**"選項卡。搜索**Microsoft.ML，** 選擇所需的包，然後選擇"**安裝**"按鈕。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-122">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="fc8c9-123">同意您所選套件的授權條款，以繼續進行安裝。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-123">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span> <span data-ttu-id="fc8c9-124">重複這些步驟的**微軟.ML.TensorFlow**和**SciSharp.TensorFlow.Redist**.</span><span class="sxs-lookup"><span data-stu-id="fc8c9-124">Repeat these steps for **Microsoft.ML.TensorFlow** and **SciSharp.TensorFlow.Redist**.</span></span>

### <a name="add-the-tensorflow-model-to-the-project"></a><span data-ttu-id="fc8c9-125">將 TensorFlow 模型添加到專案中</span><span class="sxs-lookup"><span data-stu-id="fc8c9-125">Add the TensorFlow model to the project</span></span>

> [!NOTE]
> <span data-ttu-id="fc8c9-126">本教程的模型來自[dotnet/機器學習測試資料](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model)GitHub 存儲庫。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-126">The model for this tutorial is from the [dotnet/machinelearning-testdata](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) GitHub repo.</span></span> <span data-ttu-id="fc8c9-127">該模型採用 TensorFlow 保存模型格式。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-127">The model is in TensorFlow SavedModel format.</span></span>

1. <span data-ttu-id="fc8c9-128">下載[sentiment_model壓縮檔](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true)，並解壓縮。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-128">Download the [sentiment_model zip file](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true), and unzip.</span></span>

    <span data-ttu-id="fc8c9-129">ZIP 檔案包含：</span><span class="sxs-lookup"><span data-stu-id="fc8c9-129">The zip file contains:</span></span>

    * <span data-ttu-id="fc8c9-130">`saved_model.pb`：TensorFlow 模型本身。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-130">`saved_model.pb`: the TensorFlow model itself.</span></span> <span data-ttu-id="fc8c9-131">模型採用表示 IMDB 審核字串中文本的固定長度（大小 600）整數陣列，並輸出兩個概率，總和為 1：輸入審核具有正情緒的概率，以及輸入評審具有的概率負面情緒。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-131">The model takes a fixed length (size 600) integer array of features representing the text in an IMDB review string, and outputs two probabilities which sum to 1: the probability that the input review has positive sentiment, and the probability that the input review has negative sentiment.</span></span>
    * <span data-ttu-id="fc8c9-132">`imdb_word_index.csv`：從單個單詞到整數值的映射。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-132">`imdb_word_index.csv`: a mapping from individual words to an integer value.</span></span> <span data-ttu-id="fc8c9-133">映射用於生成 TensorFlow 模型的輸入要素。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-133">The mapping is used to generate the input features for the TensorFlow model.</span></span>

2. <span data-ttu-id="fc8c9-134">將最`sentiment_model`內側目錄的內容複寫到*文本分類TF*專案`sentiment_model`目錄中。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-134">Copy the contents of the innermost `sentiment_model` directory into your *TextClassificationTF* project `sentiment_model` directory.</span></span> <span data-ttu-id="fc8c9-135">此目錄包含本教學課程所需的模型和其他支援檔案，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="fc8c9-135">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![sentiment_model目錄內容](./media/text-classification-tf/sentiment-model-files.png)

3. <span data-ttu-id="fc8c9-137">在解決方案資源管理器中，按右鍵`sentiment_model`目錄和子目錄中的每個檔，然後選擇**屬性**。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-137">In Solution Explorer, right-click each of the files in the `sentiment_model` directory and subdirectory and select **Properties**.</span></span> <span data-ttu-id="fc8c9-138">在 **"高級"** 下，將 **"複製到輸出目錄**"的值更改為 **"如果更新"，則將其更改為"複製**"。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="add-using-statements-and-global-variables"></a><span data-ttu-id="fc8c9-139">使用語句和全域變數添加</span><span class="sxs-lookup"><span data-stu-id="fc8c9-139">Add using statements and global variables</span></span>

1. <span data-ttu-id="fc8c9-140">在 *Program.cs* 檔案頂端新增下列額外的 `using` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="fc8c9-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

   [!code-csharp[AddUsings](../../../samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="fc8c9-141">在`Main`方法的正上方創建兩個全域變數，以保存保存的模型檔路徑和要素向量長度。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-141">Create two global variables right above the `Main` method to hold the saved model file path, and the feature vector length.</span></span>

   [!code-csharp[DeclareGlobalVariables](../../../samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

    * <span data-ttu-id="fc8c9-142">`_modelPath`是訓練模型的檔路徑。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-142">`_modelPath` is the file path of the trained model.</span></span>
    * <span data-ttu-id="fc8c9-143">`FeatureLength`是模型期望的整數要素陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-143">`FeatureLength` is the length of the integer feature array that the model is expecting.</span></span>

### <a name="model-the-data"></a><span data-ttu-id="fc8c9-144">將資料模型化</span><span class="sxs-lookup"><span data-stu-id="fc8c9-144">Model the data</span></span>

<span data-ttu-id="fc8c9-145">電影評論是免費形式文本。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-145">Movie reviews are free form text.</span></span> <span data-ttu-id="fc8c9-146">應用程式將文本轉換為模型在多個離散階段中期望的輸入格式。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-146">Your application converts the text into the input format expected by the model in a number of discrete stages.</span></span>

<span data-ttu-id="fc8c9-147">第一種是將文本拆分為單獨的單詞，並使用提供的映射檔將每個單詞映射到整數編碼。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-147">The first is to split the text into separate words and use the provided mapping file to map each word onto an integer encoding.</span></span> <span data-ttu-id="fc8c9-148">此轉換的結果是一個可變長度整數陣列，其長度對應于句子中的單詞數。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-148">The result of this transformation is a variable length integer array with a length corresponding to the number of words in the sentence.</span></span>

|<span data-ttu-id="fc8c9-149">屬性</span><span class="sxs-lookup"><span data-stu-id="fc8c9-149">Property</span></span>| <span data-ttu-id="fc8c9-150">值</span><span class="sxs-lookup"><span data-stu-id="fc8c9-150">Value</span></span>|<span data-ttu-id="fc8c9-151">類型</span><span class="sxs-lookup"><span data-stu-id="fc8c9-151">Type</span></span>|
|-------------|-----------------------|------|
|<span data-ttu-id="fc8c9-152">評論文本</span><span class="sxs-lookup"><span data-stu-id="fc8c9-152">ReviewText</span></span>|<span data-ttu-id="fc8c9-153">這部電影真的很好</span><span class="sxs-lookup"><span data-stu-id="fc8c9-153">this film is really good</span></span>|<span data-ttu-id="fc8c9-154">字串</span><span class="sxs-lookup"><span data-stu-id="fc8c9-154">string</span></span>|
|<span data-ttu-id="fc8c9-155">可變長度特徵</span><span class="sxs-lookup"><span data-stu-id="fc8c9-155">VariableLengthFeatures</span></span>|<span data-ttu-id="fc8c9-156">14,22,9,66,78,...</span><span class="sxs-lookup"><span data-stu-id="fc8c9-156">14,22,9,66,78,...</span></span> |<span data-ttu-id="fc8c9-157">int_</span><span class="sxs-lookup"><span data-stu-id="fc8c9-157">int[]</span></span>|

<span data-ttu-id="fc8c9-158">然後，可變長度要素陣列將大小調整為固定長度為 600。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-158">The variable length feature array is then resized to a fixed length of 600.</span></span> <span data-ttu-id="fc8c9-159">這是 TensorFlow 模型期望的長度。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-159">This is the length that the TensorFlow model expects.</span></span>

|<span data-ttu-id="fc8c9-160">屬性</span><span class="sxs-lookup"><span data-stu-id="fc8c9-160">Property</span></span>| <span data-ttu-id="fc8c9-161">值</span><span class="sxs-lookup"><span data-stu-id="fc8c9-161">Value</span></span>|<span data-ttu-id="fc8c9-162">類型</span><span class="sxs-lookup"><span data-stu-id="fc8c9-162">Type</span></span>|
|-------------|-----------------------|------|
|<span data-ttu-id="fc8c9-163">評論文本</span><span class="sxs-lookup"><span data-stu-id="fc8c9-163">ReviewText</span></span>|<span data-ttu-id="fc8c9-164">這部電影真的很好</span><span class="sxs-lookup"><span data-stu-id="fc8c9-164">this film is really good</span></span>|<span data-ttu-id="fc8c9-165">字串</span><span class="sxs-lookup"><span data-stu-id="fc8c9-165">string</span></span>|
|<span data-ttu-id="fc8c9-166">可變長度特徵</span><span class="sxs-lookup"><span data-stu-id="fc8c9-166">VariableLengthFeatures</span></span>|<span data-ttu-id="fc8c9-167">14,22,9,66,78,...</span><span class="sxs-lookup"><span data-stu-id="fc8c9-167">14,22,9,66,78,...</span></span> |<span data-ttu-id="fc8c9-168">int_</span><span class="sxs-lookup"><span data-stu-id="fc8c9-168">int[]</span></span>|
|<span data-ttu-id="fc8c9-169">特性</span><span class="sxs-lookup"><span data-stu-id="fc8c9-169">Features</span></span>|<span data-ttu-id="fc8c9-170">14,22,9,66,78,...</span><span class="sxs-lookup"><span data-stu-id="fc8c9-170">14,22,9,66,78,...</span></span> |<span data-ttu-id="fc8c9-171">int[600]</span><span class="sxs-lookup"><span data-stu-id="fc8c9-171">int[600]</span></span>|

1. <span data-ttu-id="fc8c9-172">在`Main`方法之後為輸入資料創建類：</span><span class="sxs-lookup"><span data-stu-id="fc8c9-172">Create a class for your input data, after the `Main` method:</span></span>

    [!code-csharp[MovieReviewClass](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#MovieReviewClass "Declare movie review type")]

    <span data-ttu-id="fc8c9-173">輸入資料類`MovieReview`（ 具有`string`用於使用者注釋的`ReviewText`。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-173">The input data class, `MovieReview`, has a `string` for user comments (`ReviewText`).</span></span>

1. <span data-ttu-id="fc8c9-174">在`Main`方法之後為可變長度要素創建類：</span><span class="sxs-lookup"><span data-stu-id="fc8c9-174">Create a class for the variable length features, after the `Main` method:</span></span>

    [!code-csharp[VariableLengthFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#VariableLengthFeatures "Declare variable length features type")]

    <span data-ttu-id="fc8c9-175">屬性`VariableLengthFeatures`具有[向量類型](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A)屬性，用於將其指定為向量。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-175">The `VariableLengthFeatures` property has a [VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) attribute to designate it as a vector.</span></span>  <span data-ttu-id="fc8c9-176">所有向量元素必須相同類型。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-176">All of the vector elements must be the same type.</span></span> <span data-ttu-id="fc8c9-177">在具有大量列的資料集中，將多個列載入為單個向量會減少應用資料轉換時的資料傳遞次數。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-177">In data sets with a large number of columns, loading multiple columns as a single vector reduces the number of data passes when you apply data transformations.</span></span>

    <span data-ttu-id="fc8c9-178">類用於`ResizeFeatures`操作。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-178">This class is used in the `ResizeFeatures` action.</span></span> <span data-ttu-id="fc8c9-179">其屬性的名稱（本例中只有一個）用於指示 DataView 中的哪些列可用作自訂映射操作的_輸入_。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-179">The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _input_ to the custom mapping action.</span></span>

1. <span data-ttu-id="fc8c9-180">在`Main`方法之後為固定長度要素創建類：</span><span class="sxs-lookup"><span data-stu-id="fc8c9-180">Create a class for the fixed length features, after the `Main` method:</span></span>

    [!code-csharp[FixedLengthFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#FixedLengthFeatures)]

    <span data-ttu-id="fc8c9-181">類用於`ResizeFeatures`操作。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-181">This class is used in the `ResizeFeatures` action.</span></span> <span data-ttu-id="fc8c9-182">其屬性的名稱（本例中只有一個）用於指示 DataView 中的哪些列可用作自訂映射操作的_輸出_。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-182">The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _output_ of the custom mapping action.</span></span>

    <span data-ttu-id="fc8c9-183">請注意，屬性`Features`的名稱由 TensorFlow 模型確定。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-183">Note that the name of the property `Features` is determined by the TensorFlow model.</span></span> <span data-ttu-id="fc8c9-184">不能更改此屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-184">You cannot change this property name.</span></span>

1. <span data-ttu-id="fc8c9-185">在`Main`方法之後為預測創建類：</span><span class="sxs-lookup"><span data-stu-id="fc8c9-185">Create a class for the prediction after the `Main` method:</span></span>

    [!code-csharp[Prediction](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#Prediction "Declare prediction class")]

    <span data-ttu-id="fc8c9-186">`MovieReviewSentimentPrediction` 是在模型定型後所使用的預測類別。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-186">`MovieReviewSentimentPrediction` is the prediction class used after the model training.</span></span> <span data-ttu-id="fc8c9-187">`MovieReviewSentimentPrediction`具有單個`float`陣列 （`Prediction`）`VectorType`和屬性。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-187">`MovieReviewSentimentPrediction` has a single `float` array (`Prediction`) and a `VectorType` attribute.</span></span>

### <a name="create-the-mlcontext-lookup-dictionary-and-action-to-resize-features"></a><span data-ttu-id="fc8c9-188">創建 MLCoNtext、查找字典和調整功能大小的操作</span><span class="sxs-lookup"><span data-stu-id="fc8c9-188">Create the MLContext, lookup dictionary, and action to resize features</span></span>

<span data-ttu-id="fc8c9-189">[MLContext 類別](xref:Microsoft.ML.MLContext)是所有 ML.NET 作業的起點。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-189">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="fc8c9-190">將 `mlContext` 初始化會建立新的 ML.NET 環境，可在模型建立工作流程物件間共用。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-190">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="fc8c9-191">就概念而言，類似於 Entity Framework 中的 `DBContext`。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-191">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

1. <span data-ttu-id="fc8c9-192">將 `Main` 方法中的 `Console.WriteLine("Hello World!")` 程式碼行取代為下列程式碼，以宣告 mlContext 變數並將它初始化：</span><span class="sxs-lookup"><span data-stu-id="fc8c9-192">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

   [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateMLContext "Create the ML Context")]

1. <span data-ttu-id="fc8c9-193">使用[`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A)方法載入檔中的映射資料，創建字典將單詞編碼為整數，如下表所示：</span><span class="sxs-lookup"><span data-stu-id="fc8c9-193">Create a dictionary to encode words as integers by using the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method to load mapping data from a file, as seen in the following table:</span></span>

    |<span data-ttu-id="fc8c9-194">Word</span><span class="sxs-lookup"><span data-stu-id="fc8c9-194">Word</span></span>     |<span data-ttu-id="fc8c9-195">索引</span><span class="sxs-lookup"><span data-stu-id="fc8c9-195">Index</span></span>    |
    |---------|---------|
    |<span data-ttu-id="fc8c9-196">孩子</span><span class="sxs-lookup"><span data-stu-id="fc8c9-196">kids</span></span>     |  <span data-ttu-id="fc8c9-197">362</span><span class="sxs-lookup"><span data-stu-id="fc8c9-197">362</span></span>    |
    |<span data-ttu-id="fc8c9-198">want</span><span class="sxs-lookup"><span data-stu-id="fc8c9-198">want</span></span>     |  <span data-ttu-id="fc8c9-199">181</span><span class="sxs-lookup"><span data-stu-id="fc8c9-199">181</span></span>    |
    |<span data-ttu-id="fc8c9-200">錯</span><span class="sxs-lookup"><span data-stu-id="fc8c9-200">wrong</span></span>    |  <span data-ttu-id="fc8c9-201">355</span><span class="sxs-lookup"><span data-stu-id="fc8c9-201">355</span></span>    |
    |<span data-ttu-id="fc8c9-202">effects</span><span class="sxs-lookup"><span data-stu-id="fc8c9-202">effects</span></span>  |  <span data-ttu-id="fc8c9-203">302</span><span class="sxs-lookup"><span data-stu-id="fc8c9-203">302</span></span>    |
    |<span data-ttu-id="fc8c9-204">感覺</span><span class="sxs-lookup"><span data-stu-id="fc8c9-204">feeling</span></span>  |  <span data-ttu-id="fc8c9-205">547</span><span class="sxs-lookup"><span data-stu-id="fc8c9-205">547</span></span>    |

    <span data-ttu-id="fc8c9-206">添加以下代碼以創建查找映射：</span><span class="sxs-lookup"><span data-stu-id="fc8c9-206">Add the code below to create the lookup map:</span></span>

    [!code-csharp[CreateLookupMap](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateLookupMap)]

1. <span data-ttu-id="fc8c9-207">添加`Action`用於將可變長度字整數陣列的大小調整到固定大小的整數陣列，並包含下一行代碼：</span><span class="sxs-lookup"><span data-stu-id="fc8c9-207">Add an `Action` to resize the variable length word integer array to an integer array of fixed size, with the next lines of code:</span></span>

   [!code-csharp[ResizeFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#ResizeFeatures)]

## <a name="load-the-pre-trained-tensorflow-model"></a><span data-ttu-id="fc8c9-208">載入預先訓練的 TensorFlow 模型</span><span class="sxs-lookup"><span data-stu-id="fc8c9-208">Load the pre-trained TensorFlow model</span></span>

1. <span data-ttu-id="fc8c9-209">添加代碼以載入 TensorFlow 模型：</span><span class="sxs-lookup"><span data-stu-id="fc8c9-209">Add code to load the TensorFlow model:</span></span>

    [!code-csharp[LoadTensorFlowModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#LoadTensorFlowModel)]

    <span data-ttu-id="fc8c9-210">載入模型後，可以提取其輸入和輸出架構。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-210">Once the model is loaded, you can extract its input and output schema.</span></span> <span data-ttu-id="fc8c9-211">圖解僅供興趣和學習。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-211">The schemas are displayed for interest and learning only.</span></span> <span data-ttu-id="fc8c9-212">不需要此代碼才能使最終應用程式正常運行：</span><span class="sxs-lookup"><span data-stu-id="fc8c9-212">You do not need this code for the final application to function:</span></span>

    [!code-csharp[GetModelSchema](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#GetModelSchema)]

    <span data-ttu-id="fc8c9-213">輸入架構是整數編碼詞的固定長度陣列。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-213">The input schema is the fixed-length array of integer encoded words.</span></span> <span data-ttu-id="fc8c9-214">輸出架構是一個浮動概率陣列，指示評論的情緒是負的還是正的。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-214">The output schema is a float array of probabilities indicating whether a review's sentiment is negative, or positive .</span></span> <span data-ttu-id="fc8c9-215">這些值總和為 1，因為正值的概率是情緒為負的概率的補數。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-215">These values sum to 1, as the probability of being positive is the complement of the probability of the sentiment being negative.</span></span>

## <a name="create-the-mlnet-pipeline"></a><span data-ttu-id="fc8c9-216">創建ML.NET管道</span><span class="sxs-lookup"><span data-stu-id="fc8c9-216">Create the ML.NET pipeline</span></span>

1. <span data-ttu-id="fc8c9-217">創建管道並使用[TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A)轉換將輸入文本拆分為單詞，將文本拆分為單詞作為下一行代碼：</span><span class="sxs-lookup"><span data-stu-id="fc8c9-217">Create the pipeline and split the input text into words using [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform to break the text into words as the next line of code:</span></span>

   [!code-csharp[TokenizeIntoWords](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#TokenizeIntoWords)]

   <span data-ttu-id="fc8c9-218">["標記到"轉換](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A)使用空格將文本/字串解析為單詞。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-218">The [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform uses spaces to parse the text/string into words.</span></span> <span data-ttu-id="fc8c9-219">它創建一個新列，並根據使用者定義的分隔符號將每個輸入字串拆分為子字串向量。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-219">It creates a new column and splits each input string to a vector of substrings based on the user-defined separator.</span></span>

1. <span data-ttu-id="fc8c9-220">使用上面聲明的查閱資料表將單詞映射到其整數編碼：</span><span class="sxs-lookup"><span data-stu-id="fc8c9-220">Map the words onto their integer encoding using the lookup table that you declared above:</span></span>

    [!code-csharp[MapValue](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#MapValue)]

1. <span data-ttu-id="fc8c9-221">將可變長度整數編碼的大小調整到模型所需的固定長度編碼：</span><span class="sxs-lookup"><span data-stu-id="fc8c9-221">Resize the variable length integer encodings to the fixed-length one required by the model:</span></span>

    [!code-csharp[CustomMapping](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CustomMapping)]

1. <span data-ttu-id="fc8c9-222">使用載入的 TensorFlow 模型對輸入進行分類：</span><span class="sxs-lookup"><span data-stu-id="fc8c9-222">Classify the input with the loaded TensorFlow model:</span></span>

    [!code-csharp[ScoreTensorFlowModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#ScoreTensorFlowModel)]

    <span data-ttu-id="fc8c9-223">張力流模型輸出稱為`Prediction/Softmax`。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-223">The TensorFlow model output is called `Prediction/Softmax`.</span></span> <span data-ttu-id="fc8c9-224">請注意，名稱`Prediction/Softmax`由 TensorFlow 模型確定。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-224">Note that the name `Prediction/Softmax` is determined by the TensorFlow model.</span></span> <span data-ttu-id="fc8c9-225">您不能更改此名稱。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-225">You cannot change this name.</span></span>

1. <span data-ttu-id="fc8c9-226">為輸出預測創建新列：</span><span class="sxs-lookup"><span data-stu-id="fc8c9-226">Create a new column for the output prediction:</span></span>

    [!code-csharp[SnippetCopyColumns](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#SnippetCopyColumns)]

    <span data-ttu-id="fc8c9-227">您需要將`Prediction/Softmax`列複製到一個名稱中，該名稱可用作 C# 類中的屬性： `Prediction`。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-227">You need to copy the `Prediction/Softmax` column into one with a name that can be used as a property in a C# class: `Prediction`.</span></span> <span data-ttu-id="fc8c9-228">C# 屬性名稱中不允許該`/`字元。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-228">The `/` character is not allowed in a C# property name.</span></span>

## <a name="create-the-mlnet-model-from-the-pipeline"></a><span data-ttu-id="fc8c9-229">從管道創建ML.NET模型</span><span class="sxs-lookup"><span data-stu-id="fc8c9-229">Create the ML.NET model from the pipeline</span></span>

1. <span data-ttu-id="fc8c9-230">添加代碼以從管道創建模型：</span><span class="sxs-lookup"><span data-stu-id="fc8c9-230">Add the code to create the model from the pipeline:</span></span>

    [!code-csharp[SnippetCreateModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#SnippetCreateModel)]

    <span data-ttu-id="fc8c9-231">通過調用`Fit`方法，從管道中的估計器鏈創建ML.NET模型。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-231">An ML.NET model is created from the chain of estimators in the pipeline by calling the `Fit` method.</span></span> <span data-ttu-id="fc8c9-232">在這種情況下，我們未擬合任何資料來創建模型，因為 TensorFlow 模型以前已經過訓練。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-232">In this case, we are not fitting any data to create the model, as the TensorFlow model has already been previously trained.</span></span> <span data-ttu-id="fc8c9-233">我們提供一個空資料檢視物件，以滿足`Fit`該方法的要求。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-233">We supply an empty data view object to satisfy the requirements of the `Fit` method.</span></span>

## <a name="use-the-model-to-make-a-prediction"></a><span data-ttu-id="fc8c9-234">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="fc8c9-234">Use the model to make a prediction</span></span>

1. <span data-ttu-id="fc8c9-235">在`PredictSentiment``Main`方法下方添加方法：</span><span class="sxs-lookup"><span data-stu-id="fc8c9-235">Add the `PredictSentiment` method below the `Main` method:</span></span>

    ```csharp
    public static void PredictSentiment(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. <span data-ttu-id="fc8c9-236">添加以下代碼以創建`PredictionEngine``PredictSentiment()`方法中的第一行：</span><span class="sxs-lookup"><span data-stu-id="fc8c9-236">Add the following code to create the `PredictionEngine` as the first line in the `PredictSentiment()` method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreatePredictionEngine)]

    <span data-ttu-id="fc8c9-237">[預測引擎](xref:Microsoft.ML.PredictionEngine%602)是一個方便的 API，它允許您對單個資料實例執行預測。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-237">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="fc8c9-238">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)不是執行緒安全的。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-238">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="fc8c9-239">在單線程或原型環境中使用是可以接受的。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-239">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="fc8c9-240">為提高生產環境中的性能和執行緒安全性，請使用`PredictionEnginePool`該服務，該服務創建一個[`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601)[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)物件，供整個應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-240">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="fc8c9-241">請參閱有關如何[`PredictionEnginePool`在 ASP.NET核心 Web API 中使用](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)的本指南。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-241">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="fc8c9-242">`PredictionEnginePool` 服務延伸模組目前處於預覽狀態。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-242">`PredictionEnginePool` service extension is currently in preview.</span></span>

1. <span data-ttu-id="fc8c9-243">透過建立 `MovieReview` 的執行個體，在 `Predict()` 方法中新增評論，以測試定型模型的預測：</span><span class="sxs-lookup"><span data-stu-id="fc8c9-243">Add a comment to test the trained model's prediction in the `Predict()` method by creating an instance of `MovieReview`:</span></span>

    [!code-csharp[CreateTestData](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateTestData)]

1. <span data-ttu-id="fc8c9-244">`Prediction Engine`通過在`PredictSentiment()`方法中添加下一行代碼，將測試注釋資料傳遞給 ：</span><span class="sxs-lookup"><span data-stu-id="fc8c9-244">Pass the test comment data to the `Prediction Engine` by adding the next lines of code in the `PredictSentiment()` method:</span></span>

    [!code-csharp[Predict](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#Predict)]

1. <span data-ttu-id="fc8c9-245">[預測（）](xref:Microsoft.ML.PredictionEngine%602.Predict%2A)函數對一行資料進行預測：</span><span class="sxs-lookup"><span data-stu-id="fc8c9-245">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span></span>

    |<span data-ttu-id="fc8c9-246">屬性</span><span class="sxs-lookup"><span data-stu-id="fc8c9-246">Property</span></span>| <span data-ttu-id="fc8c9-247">值</span><span class="sxs-lookup"><span data-stu-id="fc8c9-247">Value</span></span>|<span data-ttu-id="fc8c9-248">類型</span><span class="sxs-lookup"><span data-stu-id="fc8c9-248">Type</span></span>|
    |-------------|-----------------------|------|
    |<span data-ttu-id="fc8c9-249">預測</span><span class="sxs-lookup"><span data-stu-id="fc8c9-249">Prediction</span></span>|<span data-ttu-id="fc8c9-250">[0.5459937, 0.454006255]</span><span class="sxs-lookup"><span data-stu-id="fc8c9-250">[0.5459937, 0.454006255]</span></span>|<span data-ttu-id="fc8c9-251">浮動\*</span><span class="sxs-lookup"><span data-stu-id="fc8c9-251">float[]</span></span>|

1. <span data-ttu-id="fc8c9-252">使用以下代碼顯示情緒預測：</span><span class="sxs-lookup"><span data-stu-id="fc8c9-252">Display sentiment prediction using the following code:</span></span>

    [!code-csharp[DisplayPredictions](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#DisplayPredictions)]

1. <span data-ttu-id="fc8c9-253">在`Main`方法末尾添加`PredictSentiment`調用：</span><span class="sxs-lookup"><span data-stu-id="fc8c9-253">Add a call to `PredictSentiment` at the end of the `Main` method:</span></span>

    [!code-csharp[CallPredictSentiment](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CallPredictSentiment)]

## <a name="results"></a><span data-ttu-id="fc8c9-254">結果</span><span class="sxs-lookup"><span data-stu-id="fc8c9-254">Results</span></span>

<span data-ttu-id="fc8c9-255">建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-255">Build and run your application.</span></span>

<span data-ttu-id="fc8c9-256">您的結果應該與以下類似。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-256">Your results should be similar to the following.</span></span> <span data-ttu-id="fc8c9-257">處理期間會顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-257">During processing, messages are displayed.</span></span> <span data-ttu-id="fc8c9-258">您可能會看到警告或處理訊息。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-258">You may see warnings, or processing messages.</span></span> <span data-ttu-id="fc8c9-259">為了讓結果變得清楚，這些訊息已從下列結果中移除。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-259">These messages have been removed from the following results for clarity.</span></span>

```console
Number of classes: 2
Is sentiment/review positive ? Yes
```

<span data-ttu-id="fc8c9-260">恭喜！</span><span class="sxs-lookup"><span data-stu-id="fc8c9-260">Congratulations!</span></span> <span data-ttu-id="fc8c9-261">現在，您已經成功地構建了機器學習模型，通過重用ML.NET預先訓練的`TensorFlow`模型來分類和預測消息情緒。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-261">You've now successfully built a machine learning model for classifying and predicting messages sentiment by reusing a pre-trained `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="fc8c9-262">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="fc8c9-262">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) repository.</span></span>

<span data-ttu-id="fc8c9-263">在本教學課程中，您已了解如何：</span><span class="sxs-lookup"><span data-stu-id="fc8c9-263">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="fc8c9-264">載入預先訓練的 TensorFlow 模型</span><span class="sxs-lookup"><span data-stu-id="fc8c9-264">Load a pre-trained TensorFlow model</span></span>
> * <span data-ttu-id="fc8c9-265">將網站評論文本轉換為適合模型的功能</span><span class="sxs-lookup"><span data-stu-id="fc8c9-265">Transform website comment text into features suitable for the model</span></span>
> * <span data-ttu-id="fc8c9-266">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="fc8c9-266">Use the model to make a prediction</span></span>
