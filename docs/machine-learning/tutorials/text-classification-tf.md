---
title: 教學課程：使用預先定型的 TensorFlow 模型來分析電影評論的情感
description: 本教學課程說明如何使用預先定型的 TensorFlow 模型，將網站批註中的情感分類。 Binary 情感分類器是使用C# Visual Studio 開發的主控台應用程式。
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc
ms.author: nakersha
author: natke
ms.openlocfilehash: e25e884769ad62d3d888986b1475000b543b24b1
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700932"
---
# <a name="tutorial-analyze-sentiment-of-movie-reviews-using-a-pre-trained-tensorflow-model-in-mlnet"></a><span data-ttu-id="3a2a8-104">教學課程：在 ML.NET 中使用預先定型的 TensorFlow 模型來分析電影評論的情感</span><span class="sxs-lookup"><span data-stu-id="3a2a8-104">Tutorial: Analyze sentiment of movie reviews using a pre-trained TensorFlow model in ML.NET</span></span>

<span data-ttu-id="3a2a8-105">本教學課程說明如何使用預先定型的 TensorFlow 模型，將網站批註中的情感分類。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-105">This tutorial shows you how to use a pre-trained TensorFlow model to classify sentiment in website comments.</span></span> <span data-ttu-id="3a2a8-106">Binary 情感分類器是使用C# Visual Studio 開發的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-106">The binary sentiment classifier is a C# console application developed using Visual Studio.</span></span>

<span data-ttu-id="3a2a8-107">本教學課程中使用的 TensorFlow 模型已使用 IMDB 資料庫中的電影評論進行定型。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-107">The TensorFlow model used in this tutorial was trained using movie reviews from the IMDB database.</span></span> <span data-ttu-id="3a2a8-108">完成應用程式開發之後，您將能夠提供電影評論文字，而應用程式會告訴您此評論是否有正面或負面的情感。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-108">Once you have finished developing the application, you will be able to supply movie review text and the application will tell you whether the review has positive or negative sentiment.</span></span>

<span data-ttu-id="3a2a8-109">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="3a2a8-109">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="3a2a8-110">載入預先定型的 TensorFlow 模型</span><span class="sxs-lookup"><span data-stu-id="3a2a8-110">Load a pre-trained TensorFlow model</span></span>
> * <span data-ttu-id="3a2a8-111">將網站註解文字轉換成適用于模型的功能</span><span class="sxs-lookup"><span data-stu-id="3a2a8-111">Transform website comment text into features suitable for the model</span></span>
> * <span data-ttu-id="3a2a8-112">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="3a2a8-112">Use the model to make a prediction</span></span>

<span data-ttu-id="3a2a8-113">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3a2a8-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="3a2a8-114">Prerequisites</span></span>

* <span data-ttu-id="3a2a8-115">已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-115">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="setup"></a><span data-ttu-id="3a2a8-116">安裝程式</span><span class="sxs-lookup"><span data-stu-id="3a2a8-116">Setup</span></span>

### <a name="create-the-application"></a><span data-ttu-id="3a2a8-117">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="3a2a8-117">Create the application</span></span>

1. <span data-ttu-id="3a2a8-118">建立名為 "TextClassificationTF" 的 **.Net Core 主控台應用程式**。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-118">Create a **.NET Core Console Application** called "TextClassificationTF".</span></span>

2. <span data-ttu-id="3a2a8-119">在專案中建立一個名為 *Data* 的目錄以儲存資料集檔案。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-119">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="3a2a8-120">安裝「Microsoft.ML NuGet 套件」：</span><span class="sxs-lookup"><span data-stu-id="3a2a8-120">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="3a2a8-121">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-121">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="3a2a8-122">選擇 "nuget.org" 作為套件來源，然後選取 [瀏覽] 索引標籤。搜尋 **Microsoft.ML**，選取您想要的套件，然後選取 [安裝] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-122">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="3a2a8-123">同意您所選套件的授權條款，以繼續進行安裝。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-123">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span> <span data-ttu-id="3a2a8-124">針對**TensorFlow**重複這些步驟。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-124">Repeat these steps for **Microsoft.ML.TensorFlow**.</span></span>

### <a name="add-the-tensorflow-model-to-the-project"></a><span data-ttu-id="3a2a8-125">將 TensorFlow 模型加入至專案</span><span class="sxs-lookup"><span data-stu-id="3a2a8-125">Add the TensorFlow model to the project</span></span>

> [!NOTE]
> <span data-ttu-id="3a2a8-126">本教學課程的模型來自[dotnet/machinelearning-testdata](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) GitHub 存放庫。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-126">The model for this tutorial is from the [dotnet/machinelearning-testdata](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) GitHub repo.</span></span> <span data-ttu-id="3a2a8-127">模型為 TensorFlow SavedModel 格式。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-127">The model is in TensorFlow SavedModel format.</span></span>

1. <span data-ttu-id="3a2a8-128">下載[sentiment_model zip](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true)檔案，並將其解壓縮。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-128">Download the [sentiment_model zip file](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true), and unzip.</span></span>

    <span data-ttu-id="3a2a8-129">Zip 檔案包含：</span><span class="sxs-lookup"><span data-stu-id="3a2a8-129">The zip file contains:</span></span>

    * <span data-ttu-id="3a2a8-130">`saved_model.pb`： TensorFlow 模型本身。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-130">`saved_model.pb`: the TensorFlow model itself.</span></span> <span data-ttu-id="3a2a8-131">此模型會採用固定長度（大小600）整數陣列的特徵，代表 IMDB 審核字串中的文字，並輸出兩個加總為1的機率：輸入評論具有正面情感的機率，以及輸入審核的機率負面情感。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-131">The model takes a fixed length (size 600) integer array of features representing the text in an IMDB review string, and outputs two probabilities which sum to 1: the probability that the input review has positive sentiment, and the probability that the input review has negative sentiment.</span></span>
    * <span data-ttu-id="3a2a8-132">`imdb_word_index.csv`：從個別單字到整數值的對應。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-132">`imdb_word_index.csv`: a mapping from individual words to an integer value.</span></span> <span data-ttu-id="3a2a8-133">對應是用來產生 TensorFlow 模型的輸入特徵。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-133">The mapping is used to generate the input features for the TensorFlow model.</span></span>

2. <span data-ttu-id="3a2a8-134">將最內層`sentiment_model`目錄的內容複寫到您的*TextClassificationTF*專案`sentiment_model`目錄。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-134">Copy the contents of the innermost `sentiment_model` directory into your *TextClassificationTF* project `sentiment_model` directory.</span></span> <span data-ttu-id="3a2a8-135">此目錄包含本教學課程所需的模型和其他支援檔案，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="3a2a8-135">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![sentiment_model 目錄內容](./media/text-classification-tf/sentiment-model-files.png)

3. <span data-ttu-id="3a2a8-137">在方案總管中，以滑鼠右鍵按一下目錄和子目錄中`sentiment_model`的每個檔案，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-137">In Solution Explorer, right-click each of the files in the `sentiment_model` directory and subdirectory and select **Properties**.</span></span> <span data-ttu-id="3a2a8-138">在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="add-using-statements-and-global-variables"></a><span data-ttu-id="3a2a8-139">加入 using 語句和全域變數</span><span class="sxs-lookup"><span data-stu-id="3a2a8-139">Add using statements and global variables</span></span>

1. <span data-ttu-id="3a2a8-140">在 *Program.cs* 檔案頂端新增下列額外的 `using` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="3a2a8-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TextClassificationTF/Program.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="3a2a8-141">在`Main`方法上方建立兩個全域變數，以保存已儲存的模型檔案路徑和功能向量長度。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-141">Create two global variables right above the `Main` method to hold the saved model file path, and the feature vector length.</span></span>

   [!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TextClassificationTF/Program.cs#DeclareGlobalVariables "Declare global variables")]

    * <span data-ttu-id="3a2a8-142">`_modelPath`這是定型模型的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-142">`_modelPath` is the file path of the trained model.</span></span>
    * <span data-ttu-id="3a2a8-143">`FeatureLength`這是模型所預期的整數功能陣列長度。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-143">`FeatureLength` is the length of the integer feature array that the model is expecting.</span></span>

### <a name="model-the-data"></a><span data-ttu-id="3a2a8-144">建立資料模型</span><span class="sxs-lookup"><span data-stu-id="3a2a8-144">Model the data</span></span>

<span data-ttu-id="3a2a8-145">電影評論是自由格式的文字。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-145">Movie reviews are free form text.</span></span> <span data-ttu-id="3a2a8-146">您的應用程式會將文字轉換成模型所預期的輸入格式，這幾個不同的階段。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-146">Your application converts the text into the input format expected by the model in a number of discrete stages.</span></span>

<span data-ttu-id="3a2a8-147">第一種方式是將文字分割成不同的字組，然後使用提供的對應檔案，將每個單字對應到整數編碼。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-147">The first is to split the text into separate words and use the provided mapping file to map each word onto an integer encoding.</span></span> <span data-ttu-id="3a2a8-148">此轉換的結果是可變長度的整數陣列，其長度會對應到句子中的單字數目。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-148">The result of this transformation is a variable length integer array with a length corresponding to the number of words in the sentence.</span></span>

|<span data-ttu-id="3a2a8-149">屬性</span><span class="sxs-lookup"><span data-stu-id="3a2a8-149">Property</span></span>| <span data-ttu-id="3a2a8-150">值</span><span class="sxs-lookup"><span data-stu-id="3a2a8-150">Value</span></span>|<span data-ttu-id="3a2a8-151">Type</span><span class="sxs-lookup"><span data-stu-id="3a2a8-151">Type</span></span>|
|-------------|-----------------------|------|
|<span data-ttu-id="3a2a8-152">ReviewText</span><span class="sxs-lookup"><span data-stu-id="3a2a8-152">ReviewText</span></span>|<span data-ttu-id="3a2a8-153">這部電影真的不錯</span><span class="sxs-lookup"><span data-stu-id="3a2a8-153">this film is really good</span></span>|<span data-ttu-id="3a2a8-154">string</span><span class="sxs-lookup"><span data-stu-id="3a2a8-154">string</span></span>|
|<span data-ttu-id="3a2a8-155">VariableLengthFeatures</span><span class="sxs-lookup"><span data-stu-id="3a2a8-155">VariableLengthFeatures</span></span>|<span data-ttu-id="3a2a8-156">14、22、9、66、78,。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-156">14,22,9,66,78,...</span></span> |<span data-ttu-id="3a2a8-157">int []</span><span class="sxs-lookup"><span data-stu-id="3a2a8-157">int[]</span></span>|

<span data-ttu-id="3a2a8-158">然後，可變長度功能陣列會調整為固定長度的600。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-158">The variable length feature array is then resized to a fixed length of 600.</span></span> <span data-ttu-id="3a2a8-159">這是 TensorFlow 模型所預期的長度。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-159">This is the length that the TensorFlow model expects.</span></span>

|<span data-ttu-id="3a2a8-160">屬性</span><span class="sxs-lookup"><span data-stu-id="3a2a8-160">Property</span></span>| <span data-ttu-id="3a2a8-161">值</span><span class="sxs-lookup"><span data-stu-id="3a2a8-161">Value</span></span>|<span data-ttu-id="3a2a8-162">Type</span><span class="sxs-lookup"><span data-stu-id="3a2a8-162">Type</span></span>|
|-------------|-----------------------|------|
|<span data-ttu-id="3a2a8-163">ReviewText</span><span class="sxs-lookup"><span data-stu-id="3a2a8-163">ReviewText</span></span>|<span data-ttu-id="3a2a8-164">這部電影真的不錯</span><span class="sxs-lookup"><span data-stu-id="3a2a8-164">this film is really good</span></span>|<span data-ttu-id="3a2a8-165">string</span><span class="sxs-lookup"><span data-stu-id="3a2a8-165">string</span></span>|
|<span data-ttu-id="3a2a8-166">VariableLengthFeatures</span><span class="sxs-lookup"><span data-stu-id="3a2a8-166">VariableLengthFeatures</span></span>|<span data-ttu-id="3a2a8-167">14、22、9、66、78,。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-167">14,22,9,66,78,...</span></span> |<span data-ttu-id="3a2a8-168">int []</span><span class="sxs-lookup"><span data-stu-id="3a2a8-168">int[]</span></span>|
|<span data-ttu-id="3a2a8-169">功能</span><span class="sxs-lookup"><span data-stu-id="3a2a8-169">Features</span></span>|<span data-ttu-id="3a2a8-170">14、22、9、66、78,。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-170">14,22,9,66,78,...</span></span> |<span data-ttu-id="3a2a8-171">int [600]</span><span class="sxs-lookup"><span data-stu-id="3a2a8-171">int[600]</span></span>|

1. <span data-ttu-id="3a2a8-172">在`Main`方法之後，為您的輸入資料建立類別：</span><span class="sxs-lookup"><span data-stu-id="3a2a8-172">Create a class for your input data, after the `Main` method:</span></span>

    [!code-csharp[MovieReviewClass](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#MovieReviewClass "Declare movie review type")]

    <span data-ttu-id="3a2a8-173">輸入資料類別`MovieReview` `string`具有使用者批註的（`ReviewText`）。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-173">The input data class, `MovieReview`, has a `string` for user comments (`ReviewText`).</span></span>

1. <span data-ttu-id="3a2a8-174">在`Main`方法之後，建立變數長度功能的類別：</span><span class="sxs-lookup"><span data-stu-id="3a2a8-174">Create a class for the variable length features, after the `Main` method:</span></span>

    [!code-csharp[VariableLengthFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#VariableLengthFeatures "Declare variable length features type")]

    <span data-ttu-id="3a2a8-175">屬性具有 [VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) 屬性，可將它指定為向量。`VariableLengthFeatures`</span><span class="sxs-lookup"><span data-stu-id="3a2a8-175">The `VariableLengthFeatures` property has a [VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) attribute to designate it as a vector.</span></span>  <span data-ttu-id="3a2a8-176">所有向量元素都必須是相同的類型。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-176">All of the vector elements must be the same type.</span></span> <span data-ttu-id="3a2a8-177">在具有大量資料行的資料集內，將多個資料行當做單一向量載入，可減少套用資料轉換時的資料傳遞數目。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-177">In data sets with a large number of columns, loading multiple columns as a single vector reduces the number of data passes when you apply data transformations.</span></span>

    <span data-ttu-id="3a2a8-178">這個類別會用於`ResizeFeatures`動作中。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-178">This class is used in the `ResizeFeatures` action.</span></span> <span data-ttu-id="3a2a8-179">其屬性的名稱（在此案例中只有一個）用來指示 DataView 中的哪些資料行可以當做自訂對應動作的_輸入_使用。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-179">The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _input_ to the custom mapping action.</span></span>

1. <span data-ttu-id="3a2a8-180">在`Main`方法之後，建立固定長度功能的類別：</span><span class="sxs-lookup"><span data-stu-id="3a2a8-180">Create a class for the fixed length features, after the `Main` method:</span></span>

    [!code-csharp[FixedLengthFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#FixedLengthFeatures)]

    <span data-ttu-id="3a2a8-181">這個類別會用於`ResizeFeatures`動作中。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-181">This class is used in the `ResizeFeatures` action.</span></span> <span data-ttu-id="3a2a8-182">其屬性的名稱（在此案例中只有一個）用來指示 DataView 中的哪些資料行可以當做自訂對應動作的_輸出_使用。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-182">The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _output_ of the custom mapping action.</span></span>

    <span data-ttu-id="3a2a8-183">請注意，屬性`Features`的名稱是由 TensorFlow 模型所決定。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-183">Note that the name of the property `Features` is determined by the TensorFlow model.</span></span> <span data-ttu-id="3a2a8-184">您無法變更此屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-184">You cannot change this property name.</span></span>

1. <span data-ttu-id="3a2a8-185">在`Main`方法之後，建立預測的類別：</span><span class="sxs-lookup"><span data-stu-id="3a2a8-185">Create a class for the prediction after the `Main` method:</span></span>

    [!code-csharp[Prediction](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#Prediction "Declare prediction class")]

    <span data-ttu-id="3a2a8-186">`MovieReviewSentimentPrediction` 是在模型定型後所使用的預測類別。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-186">`MovieReviewSentimentPrediction` is the prediction class used after the model training.</span></span> <span data-ttu-id="3a2a8-187">`MovieReviewSentimentPrediction`具有單一`float`陣列（`Prediction`）和`VectorType`屬性。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-187">`MovieReviewSentimentPrediction` has a single `float` array (`Prediction`) and a `VectorType` attribute.</span></span>

### <a name="create-the-mlcontext-lookup-dictionary-and-action-to-resize-features"></a><span data-ttu-id="3a2a8-188">建立 MLCoNtext、查閱字典，以及調整功能大小的動作</span><span class="sxs-lookup"><span data-stu-id="3a2a8-188">Create the MLContext, lookup dictionary, and action to resize features</span></span>

<span data-ttu-id="3a2a8-189">[MLContext 類別](xref:Microsoft.ML.MLContext)是所有 ML.NET 作業的起點。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-189">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="3a2a8-190">將 `mlContext` 初始化會建立新的 ML.NET 環境，可在模型建立工作流程物件間共用。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-190">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="3a2a8-191">就概念而言，類似於 Entity Framework 中的 `DBContext`。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-191">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

1. <span data-ttu-id="3a2a8-192">將 `Main` 方法中的 `Console.WriteLine("Hello World!")` 程式碼行取代為下列程式碼，以宣告 mlContext 變數並將它初始化：</span><span class="sxs-lookup"><span data-stu-id="3a2a8-192">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

   [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateMLContext "Create the ML Context")]

1. <span data-ttu-id="3a2a8-193">建立字典，使用[`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A)方法從檔案載入對應資料，以將單字編碼為整數，如下表所示：</span><span class="sxs-lookup"><span data-stu-id="3a2a8-193">Create a dictionary to encode words as integers by using the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method to load mapping data from a file, as seen in the following table:</span></span>

    |<span data-ttu-id="3a2a8-194">字組</span><span class="sxs-lookup"><span data-stu-id="3a2a8-194">Word</span></span>     |<span data-ttu-id="3a2a8-195">索引</span><span class="sxs-lookup"><span data-stu-id="3a2a8-195">Index</span></span>    |
    |---------|---------|
    |<span data-ttu-id="3a2a8-196">小子</span><span class="sxs-lookup"><span data-stu-id="3a2a8-196">kids</span></span>     |  <span data-ttu-id="3a2a8-197">362</span><span class="sxs-lookup"><span data-stu-id="3a2a8-197">362</span></span>    |
    |<span data-ttu-id="3a2a8-198">要</span><span class="sxs-lookup"><span data-stu-id="3a2a8-198">want</span></span>     |  <span data-ttu-id="3a2a8-199">181</span><span class="sxs-lookup"><span data-stu-id="3a2a8-199">181</span></span>    |
    |<span data-ttu-id="3a2a8-200">發生</span><span class="sxs-lookup"><span data-stu-id="3a2a8-200">wrong</span></span>    |  <span data-ttu-id="3a2a8-201">355</span><span class="sxs-lookup"><span data-stu-id="3a2a8-201">355</span></span>    |
    |<span data-ttu-id="3a2a8-202">效果</span><span class="sxs-lookup"><span data-stu-id="3a2a8-202">effects</span></span>  |  <span data-ttu-id="3a2a8-203">302</span><span class="sxs-lookup"><span data-stu-id="3a2a8-203">302</span></span>    |
    |<span data-ttu-id="3a2a8-204">感受</span><span class="sxs-lookup"><span data-stu-id="3a2a8-204">feeling</span></span>  |  <span data-ttu-id="3a2a8-205">547</span><span class="sxs-lookup"><span data-stu-id="3a2a8-205">547</span></span>    |

    <span data-ttu-id="3a2a8-206">新增下列程式碼以建立查找對應：</span><span class="sxs-lookup"><span data-stu-id="3a2a8-206">Add the code below to create the lookup map:</span></span>

    [!code-csharp[CreateLookupMap](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateLookupMap)]

1. <span data-ttu-id="3a2a8-207">`Action`加入以將可變長度的文字陣列大小調整為固定大小的整數陣列，並使用下一行程式碼：</span><span class="sxs-lookup"><span data-stu-id="3a2a8-207">Add an `Action` to resize the variable length word integer array to an integer array of fixed size, with the next lines of code:</span></span>

   [!code-csharp[ResizeFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#ResizeFeatures)]

## <a name="load-the-pre-trained-tensorflow-model"></a><span data-ttu-id="3a2a8-208">載入預先定型的 TensorFlow 模型</span><span class="sxs-lookup"><span data-stu-id="3a2a8-208">Load the pre-trained TensorFlow model</span></span>

1. <span data-ttu-id="3a2a8-209">新增程式碼以載入 TensorFlow 模型：</span><span class="sxs-lookup"><span data-stu-id="3a2a8-209">Add code to load the TensorFlow model:</span></span>

    [!code-csharp[LoadTensorFlowModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#LoadTensorFlowModel)]

    <span data-ttu-id="3a2a8-210">載入模型之後，您可以將它的輸入和輸出架構解壓縮。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-210">Once the model is loaded, you can extract its input and output schema.</span></span> <span data-ttu-id="3a2a8-211">架構會顯示為感興趣並僅供學習之用。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-211">The schemas are displayed for interest and learning only.</span></span> <span data-ttu-id="3a2a8-212">您不需要這段程式碼，最終應用程式就能運作：</span><span class="sxs-lookup"><span data-stu-id="3a2a8-212">You do not need this code for the final application to function:</span></span>

    [!code-csharp[GetModelSchema](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#GetModelSchema)]

    <span data-ttu-id="3a2a8-213">輸入架構是整數編碼單字的固定長度陣列。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-213">The input schema is the fixed-length array of integer encoded words.</span></span> <span data-ttu-id="3a2a8-214">輸出架構是機率的浮點數組，表示評論的情感是負數或正數。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-214">The output schema is a float array of probabilities indicating whether a review's sentiment is negative, or positive .</span></span> <span data-ttu-id="3a2a8-215">這些值會加總為1，因為正的機率是情感為負值的機率補數。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-215">These values sum to 1, as the probability of being positive is the complement of the probability of the sentiment being negative.</span></span>

## <a name="create-the-mlnet-pipeline"></a><span data-ttu-id="3a2a8-216">建立 ML.NET 管線</span><span class="sxs-lookup"><span data-stu-id="3a2a8-216">Create the ML.NET pipeline</span></span>

1. <span data-ttu-id="3a2a8-217">建立管線，並使用[TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A)轉換將輸入文字分割成單字，以將文字分成單字，做為下一行程式碼：</span><span class="sxs-lookup"><span data-stu-id="3a2a8-217">Create the pipeline and split the input text into words using [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform to break the text into words as the next line of code:</span></span>

   [!code-csharp[TokenizeIntoWords](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#TokenizeIntoWords)]

   <span data-ttu-id="3a2a8-218">[TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A)轉換會使用空格，將文字/字串剖析成單字。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-218">The [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform uses spaces to parse the text/string into words.</span></span> <span data-ttu-id="3a2a8-219">它會建立新的資料行，並根據使用者定義的分隔符號，將每個輸入字串分割成子字串的向量。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-219">It creates a new column and splits each input string to a vector of substrings based on the user-defined separator.</span></span>

1. <span data-ttu-id="3a2a8-220">使用您在上方宣告的查閱資料表，將單字對應到其整數編碼：</span><span class="sxs-lookup"><span data-stu-id="3a2a8-220">Map the words onto their integer encoding using the lookup table that you declared above:</span></span>

    [!code-csharp[MapValue](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#MapValue)]

1. <span data-ttu-id="3a2a8-221">將可變長度的整數編碼方式調整為模型所需的固定長度：</span><span class="sxs-lookup"><span data-stu-id="3a2a8-221">Resize the variable length integer encodings to the fixed-length one required by the model:</span></span>

    [!code-csharp[CustomMapping](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CustomMapping)]

1. <span data-ttu-id="3a2a8-222">使用已載入的 TensorFlow 模型將輸入分類：</span><span class="sxs-lookup"><span data-stu-id="3a2a8-222">Classify the input with the loaded TensorFlow model:</span></span>

    [!code-csharp[ScoreTensorFlowModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#ScoreTensorFlowModel)]

    <span data-ttu-id="3a2a8-223">會呼叫`Prediction/Softmax`TensorFlow 模型輸出。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-223">The TensorFlow model output is called `Prediction/Softmax`.</span></span> <span data-ttu-id="3a2a8-224">請注意，此`Prediction/Softmax`名稱是由 TensorFlow 模型所決定。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-224">Note that the name `Prediction/Softmax` is determined by the TensorFlow model.</span></span> <span data-ttu-id="3a2a8-225">您無法變更此名稱。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-225">You cannot change this name.</span></span>

1. <span data-ttu-id="3a2a8-226">為輸出預測建立新的資料行：</span><span class="sxs-lookup"><span data-stu-id="3a2a8-226">Create a new column for the output prediction:</span></span>

    [!code-csharp[SnippetCopyColumns](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#SnippetCopyColumns)]

    <span data-ttu-id="3a2a8-227">您必須將資料`Prediction/Softmax`行複製到一個，其名稱可做為C#類別中的屬性： `Prediction`。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-227">You need to copy the `Prediction/Softmax` column into one with a name that can be used as a property in a C# class: `Prediction`.</span></span> <span data-ttu-id="3a2a8-228">屬性名稱中不允許字元。`/` C#</span><span class="sxs-lookup"><span data-stu-id="3a2a8-228">The `/` character is not allowed in a C# property name.</span></span>

## <a name="create-the-mlnet-model-from-the-pipeline"></a><span data-ttu-id="3a2a8-229">從管線建立 ML.NET 模型</span><span class="sxs-lookup"><span data-stu-id="3a2a8-229">Create the ML.NET model from the pipeline</span></span>

1. <span data-ttu-id="3a2a8-230">新增程式碼，以從管線建立模型：</span><span class="sxs-lookup"><span data-stu-id="3a2a8-230">Add the code to create the model from the pipeline:</span></span>

    [!code-csharp[SnippetCreateModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#SnippetCreateModel)]

    <span data-ttu-id="3a2a8-231">ML.NET 模型是藉由呼叫`Fit`方法，從管線中的估算器鏈建立而來。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-231">An ML.NET model is created from the chain of estimators in the pipeline by calling the `Fit` method.</span></span> <span data-ttu-id="3a2a8-232">在此情況下，我們不會調整任何資料來建立模型，因為 TensorFlow 模型先前已定型。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-232">In this case, we are not fitting any data to create the model, as the TensorFlow model has already been previously trained.</span></span> <span data-ttu-id="3a2a8-233">我們會提供空的資料檢視物件，以滿足`Fit`方法的需求。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-233">We supply an empty data view object to satisfy the requirements of the `Fit` method.</span></span>

## <a name="use-the-model-to-make-a-prediction"></a><span data-ttu-id="3a2a8-234">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="3a2a8-234">Use the model to make a prediction</span></span>

1. <span data-ttu-id="3a2a8-235">`PredictSentiment` 在`Main`方法下方新增方法：</span><span class="sxs-lookup"><span data-stu-id="3a2a8-235">Add the `PredictSentiment` method below the `Main` method:</span></span>

    ```csharp
    public static void PredictSentiment(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. <span data-ttu-id="3a2a8-236">新增下列程式碼，以建立`PredictionEngine`做為`PredictSentiment()`方法中的第一行：</span><span class="sxs-lookup"><span data-stu-id="3a2a8-236">Add the following code to create the `PredictionEngine` as the first line in the `PredictSentiment()` method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreatePredictionEngine)]

    <span data-ttu-id="3a2a8-237">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602)是一個方便的 API，可讓您在單一資料實例上執行預測。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-237">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="3a2a8-238">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) 不是安全執行緒。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-238">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="3a2a8-239">可接受在單一執行緒或原型環境中使用。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-239">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="3a2a8-240">為了改善生產環境中的效能和執行緒安全，請使用 `PredictionEnginePool` 服務，這會建立[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)物件的[@no__t 2](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) ，以供整個應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-240">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="3a2a8-241">請參閱本指南，以瞭解如何[在 ASP.NET Core WEB API 中使用 `PredictionEnginePool`](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/serve-model-web-api-ml-net#register-predictionenginepool-for-use-in-the-application)</span><span class="sxs-lookup"><span data-stu-id="3a2a8-241">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/serve-model-web-api-ml-net#register-predictionenginepool-for-use-in-the-application)</span></span>

    > [!NOTE]
    > <span data-ttu-id="3a2a8-242">`PredictionEnginePool` 服務延伸模組目前處於預覽狀態。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-242">`PredictionEnginePool` service extension is currently in preview.</span></span>

1. <span data-ttu-id="3a2a8-243">透過建立 `MovieReview` 的執行個體，在 `Predict()` 方法中新增評論，以測試定型模型的預測：</span><span class="sxs-lookup"><span data-stu-id="3a2a8-243">Add a comment to test the trained model's prediction in the `Predict()` method by creating an instance of `MovieReview`:</span></span>

    [!code-csharp[CreateTestData](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateTestData)]

1. <span data-ttu-id="3a2a8-244">藉`Prediction Engine`由在`PredictSentiment()`方法中新增下一行程式碼，將測試批註資料傳遞給：</span><span class="sxs-lookup"><span data-stu-id="3a2a8-244">Pass the test comment data to the `Prediction Engine` by adding the next lines of code in the `PredictSentiment()` method:</span></span>

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#Predict)]

1. <span data-ttu-id="3a2a8-245">[Predict （）](xref:Microsoft.ML.PredictionEngine%602.Predict%2A)函數會對單一資料列進行預測：</span><span class="sxs-lookup"><span data-stu-id="3a2a8-245">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span></span>

    |<span data-ttu-id="3a2a8-246">屬性</span><span class="sxs-lookup"><span data-stu-id="3a2a8-246">Property</span></span>| <span data-ttu-id="3a2a8-247">值</span><span class="sxs-lookup"><span data-stu-id="3a2a8-247">Value</span></span>|<span data-ttu-id="3a2a8-248">Type</span><span class="sxs-lookup"><span data-stu-id="3a2a8-248">Type</span></span>|
    |-------------|-----------------------|------|
    |<span data-ttu-id="3a2a8-249">預測</span><span class="sxs-lookup"><span data-stu-id="3a2a8-249">Prediction</span></span>|<span data-ttu-id="3a2a8-250">[0.5459937，0.454006255]</span><span class="sxs-lookup"><span data-stu-id="3a2a8-250">[0.5459937, 0.454006255]</span></span>|<span data-ttu-id="3a2a8-251">float []</span><span class="sxs-lookup"><span data-stu-id="3a2a8-251">float[]</span></span>|

1. <span data-ttu-id="3a2a8-252">使用下列程式碼來顯示情感預測：</span><span class="sxs-lookup"><span data-stu-id="3a2a8-252">Display sentiment prediction using the following code:</span></span>

    [!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#DisplayPredictions)]

1. <span data-ttu-id="3a2a8-253">`PredictSentiment`在`Main`方法的結尾新增對的呼叫：</span><span class="sxs-lookup"><span data-stu-id="3a2a8-253">Add a call to `PredictSentiment` at the end of the `Main` method:</span></span>

    [!code-csharp[CallPredictSentiment](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CallPredictSentiment)]

## <a name="results"></a><span data-ttu-id="3a2a8-254">結果</span><span class="sxs-lookup"><span data-stu-id="3a2a8-254">Results</span></span>

<span data-ttu-id="3a2a8-255">建置並執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-255">Build and run your application.</span></span>

<span data-ttu-id="3a2a8-256">您的結果應該與以下類似。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-256">Your results should be similar to the following.</span></span> <span data-ttu-id="3a2a8-257">處理期間會顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-257">During processing, messages are displayed.</span></span> <span data-ttu-id="3a2a8-258">您可能會看到警告或處理訊息。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-258">You may see warnings, or processing messages.</span></span> <span data-ttu-id="3a2a8-259">為了讓結果變得清楚，這些訊息已從下列結果中移除。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-259">These messages have been removed from the following results for clarity.</span></span>

```console
Number of classes: 2
Is sentiment/review positive ? Yes
```

<span data-ttu-id="3a2a8-260">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="3a2a8-260">Congratulations!</span></span> <span data-ttu-id="3a2a8-261">您現在已成功建立機器學習模型，以在 ML.NET 中重複使用預先定型`TensorFlow`的模型來分類和預測訊息情感。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-261">You've now successfully built a machine learning model for classifying and predicting messages sentiment by reusing a pre-trained `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="3a2a8-262">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="3a2a8-262">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) repository.</span></span>

<span data-ttu-id="3a2a8-263">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="3a2a8-263">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="3a2a8-264">載入預先定型的 TensorFlow 模型</span><span class="sxs-lookup"><span data-stu-id="3a2a8-264">Load a pre-trained TensorFlow model</span></span>
> * <span data-ttu-id="3a2a8-265">將網站註解文字轉換成適用于模型的功能</span><span class="sxs-lookup"><span data-stu-id="3a2a8-265">Transform website comment text into features suitable for the model</span></span>
> * <span data-ttu-id="3a2a8-266">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="3a2a8-266">Use the model to make a prediction</span></span>
