---
title: 機器學習資料轉換 - ML.NET
description: 探索 ML.NET 中支援的特徵工程元件。
author: JRAlexander
ms.custom: seodec18
ms.date: 01/14/2019
ms.openlocfilehash: 54dffec37318b79edf546ba1f6e1145e35782bfb
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415347"
---
# <a name="machine-learning-data-transforms---mlnet"></a><span data-ttu-id="b4555-103">機器學習資料轉換 - ML.NET</span><span class="sxs-lookup"><span data-stu-id="b4555-103">Machine learning data transforms - ML.NET</span></span>

<span data-ttu-id="b4555-104">下表包含 ML.NET 中支援的所有資料轉換相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b4555-104">The following tables contain information about all of the data transforms supported in ML.NET.</span></span>

> [!NOTE]
> <span data-ttu-id="b4555-105">ML.NET 目前為預覽版。</span><span class="sxs-lookup"><span data-stu-id="b4555-105">ML.NET is currently in Preview.</span></span> <span data-ttu-id="b4555-106">目前並不支援所有資料轉換。</span><span class="sxs-lookup"><span data-stu-id="b4555-106">Not all data transforms are currently supported.</span></span> <span data-ttu-id="b4555-107">若要提出特定轉換的要求，請在 [dotnet/machinelearning](https://github.com/dotnet/machinelearning/issues) GitHub 存放庫中提出問題。</span><span class="sxs-lookup"><span data-stu-id="b4555-107">To submit a request for a certain transform, open an issue in the [dotnet/machinelearning](https://github.com/dotnet/machinelearning/issues) GitHub repository.</span></span>

## <a name="combiners-and-segregators"></a><span data-ttu-id="b4555-108">結合工具與分離工具</span><span class="sxs-lookup"><span data-stu-id="b4555-108">Combiners and segregators</span></span>

| <span data-ttu-id="b4555-109">資料轉換</span><span class="sxs-lookup"><span data-stu-id="b4555-109">Transform</span></span> | <span data-ttu-id="b4555-110">定義</span><span class="sxs-lookup"><span data-stu-id="b4555-110">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.Transforms.GroupTransform> | <span data-ttu-id="b4555-111">將純量資料行的值組成以連續群組識別碼為基礎的向量。</span><span class="sxs-lookup"><span data-stu-id="b4555-111">Groups values of a scalar column into a vector based on a contiguous group ID.</span></span> |
| <xref:Microsoft.ML.Transforms.UngroupTransform> | <span data-ttu-id="b4555-112">取消向量資料行的群組並分成資料列序列；Group 轉換的相反。</span><span class="sxs-lookup"><span data-stu-id="b4555-112">Un-groups vector columns into sequences of rows, inverse of Group transform.</span></span> |

## <a name="conversions"></a><span data-ttu-id="b4555-113">轉換</span><span class="sxs-lookup"><span data-stu-id="b4555-113">Conversions</span></span> 

| <span data-ttu-id="b4555-114">資料轉換</span><span class="sxs-lookup"><span data-stu-id="b4555-114">Transform</span></span> | <span data-ttu-id="b4555-115">定義</span><span class="sxs-lookup"><span data-stu-id="b4555-115">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.Transforms.Conversions.HashingTransformer> | <span data-ttu-id="b4555-116">雜湊處理單一值資料行或向量資料行。</span><span class="sxs-lookup"><span data-stu-id="b4555-116">Hashes either single valued columns or vector columns.</span></span> <span data-ttu-id="b4555-117">針對向量資料行，它會個別雜湊處理每個位置。</span><span class="sxs-lookup"><span data-stu-id="b4555-117">For vector columns, it hashes each slot separately.</span></span> <span data-ttu-id="b4555-118">它可以雜湊處理文字值或索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="b4555-118">It can hash either text values or key values.</span></span> |
| <xref:Microsoft.ML.Transforms.Conversions.HashJoiningTransform> | <span data-ttu-id="b4555-119">將多個資料行值轉換成雜湊。</span><span class="sxs-lookup"><span data-stu-id="b4555-119">Converts multiple column values into hashes.</span></span> <span data-ttu-id="b4555-120">這項轉換接受數值及文字輸入，也接受單一及向量值資料行。</span><span class="sxs-lookup"><span data-stu-id="b4555-120">This transform accepts both numeric and text inputs, both single and vector-valued columns.</span></span> |
| <xref:Microsoft.ML.Transforms.Conversions.KeyToBinaryVectorMappingTransformer> | <span data-ttu-id="b4555-121">將索引鍵轉換成二進位向量資料行。</span><span class="sxs-lookup"><span data-stu-id="b4555-121">Converts a key to a binary vector column.</span></span> |
| <xref:Microsoft.ML.Transforms.Conversions.KeyToValueMappingTransformer > | <span data-ttu-id="b4555-122">利用 KeyValues 中繼資料，將索引鍵索引對應至 KeyValues 中繼資料中的對應值。</span><span class="sxs-lookup"><span data-stu-id="b4555-122">Utilizes KeyValues metadata to map key indices to the corresponding values in the KeyValues metadata.</span></span> |
| <xref:Microsoft.ML.Transforms.Conversions.KeyToVectorMappingTransformer> | <span data-ttu-id="b4555-123">將索引鍵轉換成向量資料行。</span><span class="sxs-lookup"><span data-stu-id="b4555-123">Converts a key to a vector column.</span></span> |
| <xref:Microsoft.ML.Transforms.Conversions.TypeConvertingTransformer> | <span data-ttu-id="b4555-124">變更基礎資料行類型 (前提是該類型可以轉換)。</span><span class="sxs-lookup"><span data-stu-id="b4555-124">Changes underlying column type provided the type can be converted.</span></span> |
| <xref:Microsoft.ML.Transforms.Conversions.ValueToKeyMappingTransformer> | <span data-ttu-id="b4555-125">將輸入值 (文字、數字等) 轉換成字典中的索引。</span><span class="sxs-lookup"><span data-stu-id="b4555-125">Converts input values (words, numbers, etc.) to index in a dictionary.</span></span> |


## <a name="deep-learning"></a><span data-ttu-id="b4555-126">深度學習</span><span class="sxs-lookup"><span data-stu-id="b4555-126">Deep learning</span></span>

| <span data-ttu-id="b4555-127">資料轉換</span><span class="sxs-lookup"><span data-stu-id="b4555-127">Transform</span></span> | <span data-ttu-id="b4555-128">定義</span><span class="sxs-lookup"><span data-stu-id="b4555-128">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.Transforms.OnnxTransform> | <span data-ttu-id="b4555-129">提供資料給現有的 ONNX 模型並傳回分數 (預測)。</span><span class="sxs-lookup"><span data-stu-id="b4555-129">Provides data to an existing ONNX model and returns the score (prediction).</span></span> |
| <xref:Microsoft.ML.Transforms.TensorFlowTransform> | <span data-ttu-id="b4555-130">可使用預先定型的 TensorFlow 模型計分或重新定型 TensorFlow 模型。</span><span class="sxs-lookup"><span data-stu-id="b4555-130">Can either score with pretrained TensorFlow model or retrain TensorFlow model.</span></span> |

## <a name="feature-extraction"></a><span data-ttu-id="b4555-131">特徵擷取</span><span class="sxs-lookup"><span data-stu-id="b4555-131">Feature extraction</span></span>

| <span data-ttu-id="b4555-132">資料轉換</span><span class="sxs-lookup"><span data-stu-id="b4555-132">Transform</span></span> | <span data-ttu-id="b4555-133">定義</span><span class="sxs-lookup"><span data-stu-id="b4555-133">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.Transforms.Text.CustomStopWordsRemovingTransform> | <span data-ttu-id="b4555-134">透過比較個別語彙基元 (不區分大小寫的比較) 與停用字詞，來移除指定的停用字詞清單。</span><span class="sxs-lookup"><span data-stu-id="b4555-134">Removes specified list of stop words by comparing individual tokens (case-insensitive comparison) to the stopwords.</span></span>| 
| <xref:Microsoft.ML.ImageAnalytics.ImageGrayscaleTransform> | <span data-ttu-id="b4555-135">擷取一或多個 ImageType 資料行，並將其轉換成相同影像的灰階表示。</span><span class="sxs-lookup"><span data-stu-id="b4555-135">Takes one or more ImageType columns and converts them to a greyscale representation of the same image.</span></span>|
| <xref:Microsoft.ML.ImageAnalytics.ImageLoaderTransform> | <span data-ttu-id="b4555-136">擷取一或多個 ReadOnlyMemory 資料行，並以 ImageType 形式載入。</span><span class="sxs-lookup"><span data-stu-id="b4555-136">Takes one or more ReadOnlyMemory columns and loads them as an ImageType.</span></span> |
| <xref:Microsoft.ML.ImageAnalytics.ImagePixelExtractorTransform> | <span data-ttu-id="b4555-137">擷取一或多個 ImageType 資料行，並將其轉換成向量表示。</span><span class="sxs-lookup"><span data-stu-id="b4555-137">Takes one or more ImageType columns and converts them into a vector representation.</span></span>|
| <xref:Microsoft.ML.ImageAnalytics.ImageResizerTransform> | <span data-ttu-id="b4555-138">擷取一或多個 ImageType 資料行，並將其大小調整為提供的高度和寬度。</span><span class="sxs-lookup"><span data-stu-id="b4555-138">Takes one or more ImageType columns and resizes them to  the provided height and width.</span></span>|
| <xref:Microsoft.ML.Transforms.Text.LatentDirichletAllocationTransformer> | <span data-ttu-id="b4555-139">實作 LightLDA，這是隱含狄利克雷分布 (Latent Dirichlet Allocation) 的最新實作。</span><span class="sxs-lookup"><span data-stu-id="b4555-139">Implements LightLDA, a state-of-the-art implementation of Latent Dirichlet Allocation.</span></span>|
| <xref:Microsoft.ML.Transforms.LoadTransform> | <span data-ttu-id="b4555-140">從指定的模型檔載入特定轉換。</span><span class="sxs-lookup"><span data-stu-id="b4555-140">Loads specific transforms from the specified model file.</span></span> <span data-ttu-id="b4555-141">可讓您從序列化鏈結進行「揀選」轉換，或將預先定型的轉換套用至不同 (但仍相容) 的資料檢視。</span><span class="sxs-lookup"><span data-stu-id="b4555-141">Allows for 'cherry picking' transforms from a serialized chain, or to apply a pre-trained transform to a different (but still compatible) data view.</span></span> |
| <xref:Microsoft.ML.Transforms.Text.NgramExtractingTransformer> | <span data-ttu-id="b4555-142">在指定的索引鍵向量中產生一袋 ngrams 計數 (長度為 1-n 的連續值序列)。</span><span class="sxs-lookup"><span data-stu-id="b4555-142">Produces a bag of counts of ngrams (sequences of consecutive values of length 1-n) in a given vector of keys.</span></span> <span data-ttu-id="b4555-143">它會透過建置 ngrams 字典，並在袋中使用字典內的識別碼作為索引，來進行此動作。</span><span class="sxs-lookup"><span data-stu-id="b4555-143">It does so by building a dictionary of ngrams and using the id in the dictionary as the index in the bag.</span></span> | 
| <xref:Microsoft.ML.Transforms.Text.NgramExtractorTransform> | <span data-ttu-id="b4555-144">將語彙基元化的文字集合 (ReadOnlyMemory 向量) 或索引鍵向量轉換成數值特徵向量。</span><span class="sxs-lookup"><span data-stu-id="b4555-144">Turns a collection of tokenized text (vector of ReadOnlyMemory), or vectors of keys into numerical feature vectors.</span></span> <span data-ttu-id="b4555-145">特徵向量是 n 元語法計數 (長度為 1-n 的連續語彙基元 (字組或索引鍵) 序列)。</span><span class="sxs-lookup"><span data-stu-id="b4555-145">The feature vectors are counts of ngrams (sequences of consecutive tokens -words or keys- of length 1-n).</span></span> | 
| <xref:Microsoft.ML.Transforms.Text.NgramHashExtractingTransformer> | <span data-ttu-id="b4555-146">使用雜湊，將語彙基元化的文字集合 (ReadOnlyMemory 向量) 轉換成數值特徵向量。</span><span class="sxs-lookup"><span data-stu-id="b4555-146">Turns a collection of tokenized text (vector of ReadOnlyMemory) into numerical feature vectors using hashing.</span></span> | 
| <xref:Microsoft.ML.Transforms.Text.NgramHashingTransformer> | <span data-ttu-id="b4555-147">在指定的文字中產生一袋 n 元語法計數 (長度為 1-n 的連續字組序列)。</span><span class="sxs-lookup"><span data-stu-id="b4555-147">Produces a bag of counts of ngrams (sequences of consecutive words of length 1-n) in a given text.</span></span> | 
| <xref:Microsoft.ML.Transforms.Categorical.OneHotEncodingTransformer> | <span data-ttu-id="b4555-148">透過建置以資料為依據的類別字典，並使用字典中的識別碼作為陣列中索引，來將類別值轉換成指標陣列</span><span class="sxs-lookup"><span data-stu-id="b4555-148">Converts the categorical value into an indicator array by building a dictionary of categories based on the data and using the id in the dictionary as the index in the array</span></span> |
| <xref:Microsoft.ML.Transforms.Projections.PcaTransform> | <span data-ttu-id="b4555-149">計算特徵向量在低順位子空間上的投影。</span><span class="sxs-lookup"><span data-stu-id="b4555-149">Computes the projection of the feature vector onto a low-rank subspace.</span></span> |
| <xref:Microsoft.ML.Transforms.Text.SentimentAnalyzingTransformer> | <span data-ttu-id="b4555-150">使用預先訓練的情感模型來為輸入字串計分。</span><span class="sxs-lookup"><span data-stu-id="b4555-150">Uses a pretrained sentiment model to score input strings.</span></span> |
| <xref:Microsoft.ML.Transforms.Text.StopWordsRemovingTransformer> | <span data-ttu-id="b4555-151">透過比較個別語彙基元 (不區分大小寫的比較) 與停用字詞，來移除特定語言的停用字詞清單 (最常見的字組)。</span><span class="sxs-lookup"><span data-stu-id="b4555-151">Removes language-specific list of stop words (most common words) by comparing individual tokens (case-insensitive comparison) to the stopwords.</span></span> |
| <xref:Microsoft.ML.Transforms.Text.WordBagBuildingTransformer> | <span data-ttu-id="b4555-152">在指定的文字中產生一袋 n 元語法計數 (連續字組序列)。</span><span class="sxs-lookup"><span data-stu-id="b4555-152">Produces a bag of counts of ngrams (sequences of consecutive words) in a given text.</span></span> <span data-ttu-id="b4555-153">它會透過建置 ngrams 字典，並在袋中使用字典內的識別碼作為索引，來進行此動作。</span><span class="sxs-lookup"><span data-stu-id="b4555-153">It does so by building a dictionary of ngrams and using the id in the dictionary as the index in the bag.</span></span> |
| <xref:Microsoft.ML.Transforms.Text.WordHashBagProducingTransformer> | <span data-ttu-id="b4555-154">在指定的文字中產生一袋 n 元語法計數 (長度為 1-n 的連續字組序列)。</span><span class="sxs-lookup"><span data-stu-id="b4555-154">Produces a bag of counts of ngrams (sequences of consecutive words of length 1-n) in a given text.</span></span> <span data-ttu-id="b4555-155">它會透過雜湊處理每個 n 元語法，並使用雜湊值作為袋中的索引，來進行此動作。</span><span class="sxs-lookup"><span data-stu-id="b4555-155">It does so by hashing each ngram and using the hash value as the index in the bag.</span></span> |
| <xref:Microsoft.ML.Transforms.Text.WordTokenizingTransformer> | <span data-ttu-id="b4555-156">使用分隔字元，將文字分隔為字組。</span><span class="sxs-lookup"><span data-stu-id="b4555-156">Splits the text into words using the separator character(s).</span></span> |


## <a name="image-model-featurizers"></a><span data-ttu-id="b4555-157">影像模型特徵化工具</span><span class="sxs-lookup"><span data-stu-id="b4555-157">Image model featurizers</span></span>

| <span data-ttu-id="b4555-158">資料轉換</span><span class="sxs-lookup"><span data-stu-id="b4555-158">Transform</span></span> | <span data-ttu-id="b4555-159">定義</span><span class="sxs-lookup"><span data-stu-id="b4555-159">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.Transforms.AlexNetExtension> | <span data-ttu-id="b4555-160">這是搭配 <xref:Microsoft.ML.Transforms.DnnImageFeaturizerEstimator> 使用的延伸模組方法，以便使用預先定型的 [AlexNet](https://en.wikipedia.org/wiki/AlexNet) 模型。</span><span class="sxs-lookup"><span data-stu-id="b4555-160">This is an extension method to be used with the <xref:Microsoft.ML.Transforms.DnnImageFeaturizerEstimator> in order to use a pretrained [AlexNet](https://en.wikipedia.org/wiki/AlexNet) model.</span></span> <span data-ttu-id="b4555-161">包含此延伸模組的 NuGet 也一定會包含二進位模型檔。</span><span class="sxs-lookup"><span data-stu-id="b4555-161">The NuGet containing this extension is also guaranteed to include the binary model file.</span></span> | 
| <xref:Microsoft.ML.Transforms.ResNet18Extension> | <span data-ttu-id="b4555-162">這是搭配 <xref:Microsoft.ML.Transforms.DnnImageFeaturizerEstimator> 使用的延伸模組方法，以便使用預先定型的 ResNet18 模型。</span><span class="sxs-lookup"><span data-stu-id="b4555-162">This is an extension method to be used with the <xref:Microsoft.ML.Transforms.DnnImageFeaturizerEstimator> to use a pretrained ResNet18 model.</span></span> <span data-ttu-id="b4555-163">包含此延伸模組的 NuGet 也一定會包含二進位模型檔。</span><span class="sxs-lookup"><span data-stu-id="b4555-163">The NuGet containing this extension is also guaranteed to include the binary model file.</span></span> |
| <xref:Microsoft.ML.Transforms.ResNet50Extension> | <span data-ttu-id="b4555-164">這是搭配 <xref:Microsoft.ML.Transforms.DnnImageFeaturizerEstimator> 使用的延伸模組方法，以便使用預先定型的 ResNet50 模型。</span><span class="sxs-lookup"><span data-stu-id="b4555-164">This is an extension method to be used with the <xref:Microsoft.ML.Transforms.DnnImageFeaturizerEstimator> to use a pretrained ResNet50model.</span></span> <span data-ttu-id="b4555-165">包含此延伸模組的 NuGet 也一定會包含二進位模型檔。</span><span class="sxs-lookup"><span data-stu-id="b4555-165">The NuGet containing this extension is also guaranteed to include the binary model file.</span></span> |
| <xref:Microsoft.ML.Transforms.ResNet101Extension> | <span data-ttu-id="b4555-166">這是搭配 <xref:Microsoft.ML.Transforms.DnnImageFeaturizerEstimator> 使用的延伸模組方法，以便使用預先定型的 ResNet101 模型。</span><span class="sxs-lookup"><span data-stu-id="b4555-166">This is an extension method to be used with the <xref:Microsoft.ML.Transforms.DnnImageFeaturizerEstimator> to use a pretrained ResNet101 model.</span></span> <span data-ttu-id="b4555-167">包含此延伸模組的 NuGet 也一定會包含二進位模型檔。</span><span class="sxs-lookup"><span data-stu-id="b4555-167">The NuGet containing this extension is also guaranteed to include the binary model file.</span></span> |

## <a name="label-parsing"></a><span data-ttu-id="b4555-168">標籤剖析</span><span class="sxs-lookup"><span data-stu-id="b4555-168">Label parsing</span></span>

| <span data-ttu-id="b4555-169">資料轉換</span><span class="sxs-lookup"><span data-stu-id="b4555-169">Transform</span></span> | <span data-ttu-id="b4555-170">定義</span><span class="sxs-lookup"><span data-stu-id="b4555-170">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.Transforms.LabelConvertTransform> |  <span data-ttu-id="b4555-171">轉換標籤。</span><span class="sxs-lookup"><span data-stu-id="b4555-171">Converts labels.</span></span> |
| <xref:Microsoft.ML.Transforms.LabelIndicatorTransform> | <span data-ttu-id="b4555-172">將多元分類標籤重新對應至二進位 True、False 標籤，主要用於 OVA。</span><span class="sxs-lookup"><span data-stu-id="b4555-172">Remaps multiclass labels to binary True, False labels, primarily for use with OVA.</span></span>|

## <a name="missing-values"></a><span data-ttu-id="b4555-173">遺失值</span><span class="sxs-lookup"><span data-stu-id="b4555-173">Missing values</span></span>

| <span data-ttu-id="b4555-174">資料轉換</span><span class="sxs-lookup"><span data-stu-id="b4555-174">Transform</span></span> | <span data-ttu-id="b4555-175">定義</span><span class="sxs-lookup"><span data-stu-id="b4555-175">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.Transforms.MissingValueDroppingTransformer> | <span data-ttu-id="b4555-176">捨棄資料行中的遺失值。</span><span class="sxs-lookup"><span data-stu-id="b4555-176">Drops missing values from columns.</span></span> |
| <xref:Microsoft.ML.Transforms.MissingValueIndicatorTransform> | <span data-ttu-id="b4555-177">使用相同數量的位置作為輸入資料行建立布林值輸出資料行，並在遺失輸入資料行中的值時，將輸出值設為 true。</span><span class="sxs-lookup"><span data-stu-id="b4555-177">Creates a boolean output column with the same number of slots as the input column, where the output value is true if the value in the input column is missing.</span></span> |
| <xref:Microsoft.ML.Transforms.MissingValueReplacingTransformer> | <span data-ttu-id="b4555-178">透過使用預設值或平均值/最小值/最大值取代遺失值，來處理遺失值 (僅限非文字資料行)。</span><span class="sxs-lookup"><span data-stu-id="b4555-178">Handle missing values by replacing them with either the default value or the mean/min/max value (for non-text columns only).</span></span> |

## <a name="normalization"></a><span data-ttu-id="b4555-179">正規化</span><span class="sxs-lookup"><span data-stu-id="b4555-179">Normalization</span></span>

| <span data-ttu-id="b4555-180">資料轉換</span><span class="sxs-lookup"><span data-stu-id="b4555-180">Transform</span></span> | <span data-ttu-id="b4555-181">定義</span><span class="sxs-lookup"><span data-stu-id="b4555-181">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.Transforms.Projections.LpNormalizingTransformer> | <span data-ttu-id="b4555-182">Lp-Norm (以向量/資料列方式) 正規化轉換。</span><span class="sxs-lookup"><span data-stu-id="b4555-182">Lp-Norm (vector/row-wise) normalization transform.</span></span> |
| <xref:Microsoft.ML.Transforms.Normalizers.MeanVarDblAggregator> | <span data-ttu-id="b4555-183">計算向量值資料行的平均數和變異數。</span><span class="sxs-lookup"><span data-stu-id="b4555-183">Computes the mean and variance for a vector valued column.</span></span> <span data-ttu-id="b4555-184">它會追蹤目前平均數和 M2 (平均數值差的總平方和)、NAN 數目和非零項目數目。</span><span class="sxs-lookup"><span data-stu-id="b4555-184">It tracks the current mean and the M2 (sum of squared diffs of the values from the mean), the number of NaNs and the number of non-zero elements.</span></span> |
| <xref:Microsoft.ML.Transforms.Normalizers.MeanVarSngAggregator> | <span data-ttu-id="b4555-185">計算向量值資料行的平均數和變異數。</span><span class="sxs-lookup"><span data-stu-id="b4555-185">Computes the mean and variance for a vector valued column.</span></span> <span data-ttu-id="b4555-186">它會追蹤目前平均數和 M2 (平均數值差的總平方和)、NAN 數目和非零項目數目。</span><span class="sxs-lookup"><span data-stu-id="b4555-186">It tracks the current mean and the M2 (sum of squared diffs of the values from the mean), the number of NaNs and the number of non-zero elements.</span></span> |
| <xref:Microsoft.ML.Transforms.Normalizers.MinMaxDblAggregator> | <span data-ttu-id="b4555-187">追蹤向量值資料行的最小值、最大值、非疏鬆值數目 (vCount) 和 ProcessValue() 呼叫數目 (trainCount)。</span><span class="sxs-lookup"><span data-stu-id="b4555-187">Tracks min, max, number of non-sparse values (vCount) and number of ProcessValue() calls (trainCount) for a vector valued column.</span></span> |
| <xref:Microsoft.ML.Transforms.Normalizers.NormalizeTransform> | <span data-ttu-id="b4555-188">標準化特徵範圍。</span><span class="sxs-lookup"><span data-stu-id="b4555-188">Standardizes feature ranges.</span></span> |
| <xref:Microsoft.ML.Transforms.Normalizers.NormalizingTransformer> |<span data-ttu-id="b4555-189">標準化特徵範圍。</span><span class="sxs-lookup"><span data-stu-id="b4555-189">Standardizes feature ranges.</span></span> |

## <a name="onnx"></a><span data-ttu-id="b4555-190">Onnx</span><span class="sxs-lookup"><span data-stu-id="b4555-190">Onnx</span></span>

| <span data-ttu-id="b4555-191">資料轉換</span><span class="sxs-lookup"><span data-stu-id="b4555-191">Transform</span></span> | <span data-ttu-id="b4555-192">定義</span><span class="sxs-lookup"><span data-stu-id="b4555-192">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.Transforms.OnnxTransform> | <span data-ttu-id="b4555-193">為使用 ONNX 標準 v1.2 的預先定型 ONNX 模型計分</span><span class="sxs-lookup"><span data-stu-id="b4555-193">Scores pre-trained ONNX models which use the ONNX standard v1.2</span></span> |

## <a name="preprocessing"></a><span data-ttu-id="b4555-194">前置處理</span><span class="sxs-lookup"><span data-stu-id="b4555-194">Preprocessing</span></span>
| <span data-ttu-id="b4555-195">資料轉換</span><span class="sxs-lookup"><span data-stu-id="b4555-195">Transform</span></span> | <span data-ttu-id="b4555-196">定義</span><span class="sxs-lookup"><span data-stu-id="b4555-196">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.Transforms.BootstrapSamplingTransformer> | <span data-ttu-id="b4555-197">近似使用波氏取樣的自助取樣 (Bootstrap Sampling)。</span><span class="sxs-lookup"><span data-stu-id="b4555-197">Approximates bootstrap sampling using Poisson sampling.</span></span> |
| <xref:Microsoft.ML.Transforms.Projections.RandomFourierFeaturizingTransformer> | <span data-ttu-id="b4555-198">產生隨機傅立葉特徵。</span><span class="sxs-lookup"><span data-stu-id="b4555-198">Produces random Fourier feature.</span></span> |
| <xref:Microsoft.ML.Transforms.Text.TokenizingByCharactersTransformer> | <span data-ttu-id="b4555-199">字元導向的權杖化工具，文字在其中會視為字元序列。</span><span class="sxs-lookup"><span data-stu-id="b4555-199">Character-oriented tokenizer where text is considered a sequence of characters.</span></span> |
| <xref:Microsoft.ML.Transforms.Projections.VectorWhiteningTransformer> | <span data-ttu-id="b4555-200">簡化最佳化以協助找出權數。</span><span class="sxs-lookup"><span data-stu-id="b4555-200">Simplfies optimization to assist with identifying weights.</span></span> |

## <a name="row-filters"></a><span data-ttu-id="b4555-201">資料列篩選</span><span class="sxs-lookup"><span data-stu-id="b4555-201">Row Filters</span></span>

| <span data-ttu-id="b4555-202">資料轉換</span><span class="sxs-lookup"><span data-stu-id="b4555-202">Transform</span></span> | <span data-ttu-id="b4555-203">定義</span><span class="sxs-lookup"><span data-stu-id="b4555-203">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.Transforms.RowShufflingTransformer> | <span data-ttu-id="b4555-204">使用指定數目的資料列集區，輪換要執行的隨機化資料指標嘗試。</span><span class="sxs-lookup"><span data-stu-id="b4555-204">Shuffles a randomized cursor attempt to perform using a pool of a given number of rows.</span></span>  |
| <xref:Microsoft.ML.Transforms.SkipFilter> | <span data-ttu-id="b4555-205">允許利用跳過資料列數，來限制輸入資料列子集。</span><span class="sxs-lookup"><span data-stu-id="b4555-205">Allows limiting input to a subset of rows by skipping a number of rows.</span></span> |
| <xref:Microsoft.ML.Transforms.SkipTakeFilter> | <span data-ttu-id="b4555-206">允許限制在選擇性位移的資料列子集進行輸入。</span><span class="sxs-lookup"><span data-stu-id="b4555-206">Allows limiting input to a subset of rows at an optional offset.</span></span> <span data-ttu-id="b4555-207">可用來實作資料分頁。</span><span class="sxs-lookup"><span data-stu-id="b4555-207">Can be used to implement data paging.</span></span> <span data-ttu-id="b4555-208">使用 SkipTakeFilter.SkipArguments 建立時，其行為會如同 `SkipFilter`。</span><span class="sxs-lookup"><span data-stu-id="b4555-208">When created with SkipTakeFilter.SkipArguments behaves as `SkipFilter`.</span></span>
| <xref:Microsoft.ML.Transforms.TakeFilter> | <span data-ttu-id="b4555-209">允許利用跳過資料列數，來限制輸入資料列子集。</span><span class="sxs-lookup"><span data-stu-id="b4555-209">Allows limiting input to a subset of rows by taking N first rows.</span></span> |


## <a name="schema"></a><span data-ttu-id="b4555-210">結構描述</span><span class="sxs-lookup"><span data-stu-id="b4555-210">Schema</span></span>

| <span data-ttu-id="b4555-211">資料轉換</span><span class="sxs-lookup"><span data-stu-id="b4555-211">Transform</span></span> | <span data-ttu-id="b4555-212">定義</span><span class="sxs-lookup"><span data-stu-id="b4555-212">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.Transforms.ColumnCopyingTransformer> | <span data-ttu-id="b4555-213">從資料集複製資料行。</span><span class="sxs-lookup"><span data-stu-id="b4555-213">Duplicates columns from the dataset.</span></span>|
| <xref:Microsoft.ML.Transforms.ColumnSelectingTransformer> | <span data-ttu-id="b4555-214">從所指定輸入中選取要捨棄或保留的一組資料行。</span><span class="sxs-lookup"><span data-stu-id="b4555-214">Selects a set of columns to drop or keep from a given input.</span></span> |
| <xref:Microsoft.ML.Transforms.FeatureSelection.SlotsDroppingTransformer> | <span data-ttu-id="b4555-215">捨棄資料行中的位置。</span><span class="sxs-lookup"><span data-stu-id="b4555-215">Drops slots from columns.</span></span>|
| <xref:Microsoft.ML.Transforms.OptionalColumnTransform> | <span data-ttu-id="b4555-216">使用指定的類型和預設值建立新資料行。</span><span class="sxs-lookup"><span data-stu-id="b4555-216">Creates a new column with the specified type and default values.</span></span> |
| <xref:Microsoft.ML.Transforms.RangeFilter> | <span data-ttu-id="b4555-217">在類型為 Single、Double 或 Key (連續) 的資料行上篩選 dataview。</span><span class="sxs-lookup"><span data-stu-id="b4555-217">Filters a dataview on a column of type Single, Double or Key (contiguous).</span></span> <span data-ttu-id="b4555-218">保留位於指定最小值/最大值範圍中的值。</span><span class="sxs-lookup"><span data-stu-id="b4555-218">Keeps the values that are in the specified min/max range.</span></span> <span data-ttu-id="b4555-219">一律會篩選掉 NaN。若輸入為 Key 類型，則最小值/最大值會視為百分比，代表該百分比包含的值數。</span><span class="sxs-lookup"><span data-stu-id="b4555-219">NaNs are always filtered out. If the input is a Key type, the min/max are considered percentages of the number of values.</span></span> |

## <a name="tensorflow"></a><span data-ttu-id="b4555-220">Tensorflow</span><span class="sxs-lookup"><span data-stu-id="b4555-220">TensorFlow</span></span>

| <span data-ttu-id="b4555-221">資料轉換</span><span class="sxs-lookup"><span data-stu-id="b4555-221">Transform</span></span> | <span data-ttu-id="b4555-222">定義</span><span class="sxs-lookup"><span data-stu-id="b4555-222">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.Transforms.TensorFlowTransform> | <span data-ttu-id="b4555-223">使用預先定型的 TensorFlow 模型計分或重新定型 TensorFlow 模型。</span><span class="sxs-lookup"><span data-stu-id="b4555-223">Either scores with pretrained TensorFlow model or retrains TensorFlow model.</span></span> |

## <a name="text-processing-and-featurization"></a><span data-ttu-id="b4555-224">文字處理與特徵化</span><span class="sxs-lookup"><span data-stu-id="b4555-224">Text processing and featurization</span></span>

| <span data-ttu-id="b4555-225">資料轉換</span><span class="sxs-lookup"><span data-stu-id="b4555-225">Transform</span></span> | <span data-ttu-id="b4555-226">定義</span><span class="sxs-lookup"><span data-stu-id="b4555-226">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.Transforms.Text.TextNormalizingTransformer> | <span data-ttu-id="b4555-227">文字正規化轉換，可將文字大小寫正規化，以及移除變音符號、標點符號及/或數字。</span><span class="sxs-lookup"><span data-stu-id="b4555-227">A text normalization transform that allows normalizing text case, removing diacritical marks, punctuation marks and/or numbers.</span></span> <span data-ttu-id="b4555-228">可對文字輸入及語彙基元/文字向量 (ReadOnlyMemory 向量) 進行此轉換。</span><span class="sxs-lookup"><span data-stu-id="b4555-228">The transform operates on text input as well as vector of tokens/text (vector of ReadOnlyMemory).</span></span> |
| <xref:Microsoft.ML.Transforms.Text.TokenizingByCharactersTransformer> | <span data-ttu-id="b4555-229">字元導向的權杖化工具，文字在其中會視為字元序列。</span><span class="sxs-lookup"><span data-stu-id="b4555-229">Character-oriented tokenizer where text is considered a sequence of characters.</span></span> |

## <a name="time-series"></a><span data-ttu-id="b4555-230">時間序列</span><span class="sxs-lookup"><span data-stu-id="b4555-230">Time series</span></span>

| <span data-ttu-id="b4555-231">資料轉換</span><span class="sxs-lookup"><span data-stu-id="b4555-231">Transform</span></span> | <span data-ttu-id="b4555-232">定義</span><span class="sxs-lookup"><span data-stu-id="b4555-232">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.TimeSeriesProcessing.ExponentialAverageTransform> | <span data-ttu-id="b4555-233">取得所有值的加權平均：ExpAvg(y_t) = a \* y_t + (1-a) \* ExpAvg(y_(t-1))。</span><span class="sxs-lookup"><span data-stu-id="b4555-233">Takes a weighted average of the values: ExpAvg(y_t) = a \* y_t + (1-a) \* ExpAvg(y_(t-1)).</span></span> |
| <xref:Microsoft.ML.TimeSeriesProcessing.IidChangePointDetector> | <span data-ttu-id="b4555-234">根據自適性核心密度估計和隨機過程，</span><span class="sxs-lookup"><span data-stu-id="b4555-234">Implements the change point detector transform for an i.i.d.</span></span> <span data-ttu-id="b4555-235">實作 i.i.d. 序列 (隨機樣本) 的變點檢測器轉換。</span><span class="sxs-lookup"><span data-stu-id="b4555-235">sequence (random sample) based on adaptive kernel density estimation and martingales.</span></span> |
| <xref:Microsoft.ML.TimeSeriesProcessing.IidSpikeDetector> | <span data-ttu-id="b4555-236">根據自適性核心密度估計，</span><span class="sxs-lookup"><span data-stu-id="b4555-236">Implements the spike detector transform for an i.i.d.</span></span> <span data-ttu-id="b4555-237">實作 i.i.d. 序列 (隨機樣本) 的峰點檢測器轉換。</span><span class="sxs-lookup"><span data-stu-id="b4555-237">sequence (random sample) based on adaptive kernel density estimation.</span></span> |
| <xref:Microsoft.ML.TimeSeriesProcessing.MovingAverageTransform> | <span data-ttu-id="b4555-238">提供滑動視窗值的加權平均。</span><span class="sxs-lookup"><span data-stu-id="b4555-238">Provides a weighted average of the sliding window values.</span></span> |
| <xref:Microsoft.ML.TimeSeriesProcessing.PercentileThresholdTransform> | <span data-ttu-id="b4555-239">決定時間序列現值是否屬於滑動視窗臨界數值百分位數。</span><span class="sxs-lookup"><span data-stu-id="b4555-239">Decides whether the time-series current value belongs to the sliding window top values percentile.</span></span> |
| <xref:Microsoft.ML.TimeSeriesProcessing.PValueTransform> | <span data-ttu-id="b4555-240">根據滑動視窗中的其他值，計算序列現值的經驗 p 值。</span><span class="sxs-lookup"><span data-stu-id="b4555-240">Computes the series current value empirical p-value based on the other values in the sliding window.</span></span> |
| <xref:Microsoft.ML.TimeSeriesProcessing.SlidingWindowTransform> | <span data-ttu-id="b4555-241">輸出 Single 類型時間序列上的滑動視窗。</span><span class="sxs-lookup"><span data-stu-id="b4555-241">Outputs a sliding window on a time series of type Single.</span></span> |
| <xref:Microsoft.ML.TimeSeriesProcessing.SsaChangePointDetector> | <span data-ttu-id="b4555-242">根據時間序列的奇異譜 (Singular Spectrum) 模型，實作變點檢測器轉換。</span><span class="sxs-lookup"><span data-stu-id="b4555-242">Implements the change point detector transform based on Singular Spectrum modeling of the time-series.</span></span> |
| <xref:Microsoft.ML.TimeSeriesProcessing.SsaSpikeDetector> | <span data-ttu-id="b4555-243">根據時間序列的奇異譜 (Singular Spectrum) 模型，實作峰值檢測器轉換。</span><span class="sxs-lookup"><span data-stu-id="b4555-243">Implements the spike detector transform based on Singular Spectrum modeling of the time-series.</span></span> |

## <a name="miscellaneous"></a><span data-ttu-id="b4555-244">其他</span><span class="sxs-lookup"><span data-stu-id="b4555-244">Miscellaneous</span></span>

| <span data-ttu-id="b4555-245">資料轉換</span><span class="sxs-lookup"><span data-stu-id="b4555-245">Transform</span></span> | <span data-ttu-id="b4555-246">定義</span><span class="sxs-lookup"><span data-stu-id="b4555-246">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.Transforms.CompositeTransformer> | <span data-ttu-id="b4555-247">建立複合資料轉換。</span><span class="sxs-lookup"><span data-stu-id="b4555-247">Creates a Composite DataTransform.</span></span> |
| <xref:Microsoft.ML.Transforms.CustomMappingTransformer%602> | <span data-ttu-id="b4555-248">為提供的 `IDataView` 產生額外資料行。</span><span class="sxs-lookup"><span data-stu-id="b4555-248">Generates additional columns to the provided `IDataView`.</span></span> <span data-ttu-id="b4555-249">它不會變更資料列數目，可視為將使用者的函式應用至每一列輸入資料的結果。</span><span class="sxs-lookup"><span data-stu-id="b4555-249">It doesn't change the number of rows and can be seen as a result of application of the user's function to every row of the input data.</span></span>|
| <xref:Microsoft.ML.Transforms.GenerateNumberTransform> | <span data-ttu-id="b4555-250">使用產生的數字序列新增資料行。</span><span class="sxs-lookup"><span data-stu-id="b4555-250">Adds a column with a generated number sequence.</span></span> |
| <xref:Microsoft.ML.Transforms.ProduceIdTransform> | <span data-ttu-id="b4555-251">產生以資料指標識別碼作為資料行的資料行。</span><span class="sxs-lookup"><span data-stu-id="b4555-251">Produces a column with the cursor's ID as a column.</span></span> |
| <xref:Microsoft.ML.Transforms.RandomNumberGenerator> | <span data-ttu-id="b4555-252">產生亂數。</span><span class="sxs-lookup"><span data-stu-id="b4555-252">Generates a random number.</span></span> |
