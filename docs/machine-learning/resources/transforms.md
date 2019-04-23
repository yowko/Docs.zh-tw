---
title: 資料轉換 | ML.NET
description: 探索 ML.NET 中支援的特徵工程元件。
author: natke
ms.author: nakersha
ms.date: 04/02/2019
ms.openlocfilehash: 506abcc826059f4d252378b1bde0b852949a42e1
ms.sourcegitcommit: 8080271c246b57f4fb68c28369634bff46843424
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2019
ms.locfileid: "59553845"
---
# <a name="data-transformations"></a><span data-ttu-id="2f369-103">資料轉換</span><span class="sxs-lookup"><span data-stu-id="2f369-103">Data transformations</span></span>

<span data-ttu-id="2f369-104">資料轉換是用來針對模型定型準備資料。</span><span class="sxs-lookup"><span data-stu-id="2f369-104">Data transformations are used to prepare data for model training.</span></span> <span data-ttu-id="2f369-105">本指南中的轉換會傳回能實作 [IEstimator](xref:Microsoft.ML.IEstimator`1) 介面的類別。</span><span class="sxs-lookup"><span data-stu-id="2f369-105">The transformations in this guide return classes that implement the [IEstimator](xref:Microsoft.ML.IEstimator`1) interface.</span></span> <span data-ttu-id="2f369-106">資料轉換可以鏈結在一起。</span><span class="sxs-lookup"><span data-stu-id="2f369-106">Data transformations can be chained together.</span></span> <span data-ttu-id="2f369-107">每個轉換都會預期和產生特定類型及格式的資料，其已詳述於連結的參考文件中。</span><span class="sxs-lookup"><span data-stu-id="2f369-107">Each transformation both expects and produces data of specific types and formats, which are specified in the linked reference documentation.</span></span>

<span data-ttu-id="2f369-108">某些資料轉換需要定型資料以計算其參數。</span><span class="sxs-lookup"><span data-stu-id="2f369-108">Some data transformations require training data to calculate their parameters.</span></span> <span data-ttu-id="2f369-109">例如：<xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> 轉換器會在 `Fit()` 作業期間計算定型資料的平均數和變異數，並將那些參數用於 `Transform()` 作業。</span><span class="sxs-lookup"><span data-stu-id="2f369-109">For example: the <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> transformer calculates the mean and variance of the training data during the `Fit()` operation, and uses those parameters in the `Transform()` operation.</span></span> 

<span data-ttu-id="2f369-110">其他資料轉換並不需要定型資料。</span><span class="sxs-lookup"><span data-stu-id="2f369-110">Other data transformations don't require training data.</span></span> <span data-ttu-id="2f369-111">例如：<xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale*> 轉換可以在無須於 `Fit()` 作業期間查看任何定型資料的情況下執行 `Transform()` 作業。</span><span class="sxs-lookup"><span data-stu-id="2f369-111">For example: the <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale*> transformation can perform the `Transform()` operation without having seen any training data during the `Fit()` operation.</span></span>

## <a name="column-mapping-and-grouping"></a><span data-ttu-id="2f369-112">資料行對應及群組</span><span class="sxs-lookup"><span data-stu-id="2f369-112">Column mapping and grouping</span></span>

| <span data-ttu-id="2f369-113">資料轉換</span><span class="sxs-lookup"><span data-stu-id="2f369-113">Transform</span></span> | <span data-ttu-id="2f369-114">定義</span><span class="sxs-lookup"><span data-stu-id="2f369-114">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A> | <span data-ttu-id="2f369-115">將一或多個輸入資料行串連成新的輸出資料行</span><span class="sxs-lookup"><span data-stu-id="2f369-115">Concatenate one or more input columns into a new output column</span></span> |
| <xref:Microsoft.ML.TransformExtensionsCatalog.CopyColumns%2A> | <span data-ttu-id="2f369-116">複製並重新命名一或多個輸入資料行</span><span class="sxs-lookup"><span data-stu-id="2f369-116">Copy and rename one or more input columns</span></span> |
| <xref:Microsoft.ML.TransformExtensionsCatalog.DropColumns%2A> | <span data-ttu-id="2f369-117">卸除一或多個輸入資料行</span><span class="sxs-lookup"><span data-stu-id="2f369-117">Drop one or more input columns</span></span> |
| <xref:Microsoft.ML.TransformExtensionsCatalog.SelectColumns%2A> | <span data-ttu-id="2f369-118">選取一或多個資料行以將其自輸入資料中排除</span><span class="sxs-lookup"><span data-stu-id="2f369-118">Select one or more columns to keep from the input data</span></span> |

## <a name="normalization-and-scaling"></a><span data-ttu-id="2f369-119">標準化和調整</span><span class="sxs-lookup"><span data-stu-id="2f369-119">Normalization and scaling</span></span>

| <span data-ttu-id="2f369-120">資料轉換</span><span class="sxs-lookup"><span data-stu-id="2f369-120">Transform</span></span> | <span data-ttu-id="2f369-121">定義</span><span class="sxs-lookup"><span data-stu-id="2f369-121">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> | <span data-ttu-id="2f369-122">減去 (定型資料的) 平均數並除以 (定型資料的) 變異數</span><span class="sxs-lookup"><span data-stu-id="2f369-122">Subtract the mean (of the training data) and divide by the variance (of the training data)</span></span> |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLogMeanVariance%2A> | <span data-ttu-id="2f369-123">依定型資料的對數進行標準化</span><span class="sxs-lookup"><span data-stu-id="2f369-123">Normalize based on the logarithm of the training data</span></span> |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLpNorm%2A> | <span data-ttu-id="2f369-124">依據輸入向量的 [lp-norm](https://en.wikipedia.org/wiki/Lp_space#The_p-norm_in_finite_dimensions) 來對它進行調整，其中 p 為 1、2 或無限。</span><span class="sxs-lookup"><span data-stu-id="2f369-124">Scale input vectors by their [lp-norm](https://en.wikipedia.org/wiki/Lp_space#The_p-norm_in_finite_dimensions), where p is 1, 2 or infinity.</span></span> <span data-ttu-id="2f369-125">預設為 l2 (歐幾里得距離) 範數</span><span class="sxs-lookup"><span data-stu-id="2f369-125">Defaults to the l2 (Euclidean distance) norm</span></span> |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeGlobalContrast%2A> | <span data-ttu-id="2f369-126">透過減去資料列資料的平均數並除以標準差或 (資料列資料的) l2 範數，並乘以可設定的比例因素 (預設為 2)，來調整資料列中的每個值</span><span class="sxs-lookup"><span data-stu-id="2f369-126">Scale each value in a row by subtracting the mean of the row data and divide by either the standard deviation or l2-norm (of the row data), and multiply by a configurable scale factor (default 2)</span></span> |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A> | <span data-ttu-id="2f369-127">將輸入值指派至 bin 目錄並除以 bin 的數目，以產生介於 0 與 1 的浮點值。</span><span class="sxs-lookup"><span data-stu-id="2f369-127">Assign the input value to a bin index and divide by the number of bins to produce a float value between 0 and 1.</span></span> <span data-ttu-id="2f369-128">系統會以能將定型資料平均分散到所有 bin 上的方式計算 bin 界線</span><span class="sxs-lookup"><span data-stu-id="2f369-128">The bin boundaries are calculated to evenly distribute the training data across bins</span></span> |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeSupervisedBinning%2A> | <span data-ttu-id="2f369-129">根據 bin 與標籤資料行的關聯性將輸入值指派至該 bin</span><span class="sxs-lookup"><span data-stu-id="2f369-129">Assign the input value to a bin based on its correlation with label column</span></span> |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A> | <span data-ttu-id="2f369-130">依定型資料中最小及最大值之間的差異來調整輸入</span><span class="sxs-lookup"><span data-stu-id="2f369-130">Scale the input by the difference between the minimum and maximum values in the training data</span></span> |

## <a name="conversions-between-data-types"></a><span data-ttu-id="2f369-131">資料類型之間的轉換</span><span class="sxs-lookup"><span data-stu-id="2f369-131">Conversions between data types</span></span>

| <span data-ttu-id="2f369-132">資料轉換</span><span class="sxs-lookup"><span data-stu-id="2f369-132">Transform</span></span> | <span data-ttu-id="2f369-133">定義</span><span class="sxs-lookup"><span data-stu-id="2f369-133">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.ConvertType%2A> | <span data-ttu-id="2f369-134">將某個輸入資料行的類型轉換成新的類型</span><span class="sxs-lookup"><span data-stu-id="2f369-134">Convert the type of an input column to a new type</span></span> |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValue*> | <span data-ttu-id="2f369-135">根據所提供的對應字典將值對應至索引鍵 (類別)</span><span class="sxs-lookup"><span data-stu-id="2f369-135">Map values to keys (categories) based on the supplied dictionary of mappings</span></span> |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*> | <span data-ttu-id="2f369-136">透過從輸入資料建立對應來將值對應至索引鍵 (類別)</span><span class="sxs-lookup"><span data-stu-id="2f369-136">Map values to keys (categories) by creating the mapping from the input data</span></span> |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue*> | <span data-ttu-id="2f369-137">將索引鍵轉換為其原始值</span><span class="sxs-lookup"><span data-stu-id="2f369-137">Convert keys back to their original values</span></span> |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToVector*> | <span data-ttu-id="2f369-138">將索引鍵轉換為原始值的向量</span><span class="sxs-lookup"><span data-stu-id="2f369-138">Convert keys back to vectors of original values</span></span> |
| <xref:Microsoft.ML.ConversionsCatalog.MapKeyToBinaryVector*> | <span data-ttu-id="2f369-139">將索引鍵轉換為原始值的二進位向量</span><span class="sxs-lookup"><span data-stu-id="2f369-139">Convert keys back to a binary vector of original values</span></span> |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash*> | <span data-ttu-id="2f369-140">對輸入資料行中的值進行雜湊處理</span><span class="sxs-lookup"><span data-stu-id="2f369-140">Hash the value in the input column</span></span> |

## <a name="text-transformations"></a><span data-ttu-id="2f369-141">文字轉換</span><span class="sxs-lookup"><span data-stu-id="2f369-141">Text transformations</span></span>

| <span data-ttu-id="2f369-142">資料轉換</span><span class="sxs-lookup"><span data-stu-id="2f369-142">Transform</span></span> | <span data-ttu-id="2f369-143">定義</span><span class="sxs-lookup"><span data-stu-id="2f369-143">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.TextCatalog.FeaturizeText*> | <span data-ttu-id="2f369-144">將文字資料行轉換為標準化 ngram 和 char-gram 計數的浮動陣列</span><span class="sxs-lookup"><span data-stu-id="2f369-144">Transform a text column into a float array of normalized ngrams and char-grams counts</span></span> | 
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoWords*> | <span data-ttu-id="2f369-145">將一或多個文字資料行分割為個別字詞</span><span class="sxs-lookup"><span data-stu-id="2f369-145">Split one or more text columns into individual words</span></span> |
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoCharactersAsKeys*> | <span data-ttu-id="2f369-146">將一或多個文字資料行分割為於一組主題上的個別字元浮點數</span><span class="sxs-lookup"><span data-stu-id="2f369-146">Split one or more text columns into individual characters floats over a set of topics</span></span> |
| <xref:Microsoft.ML.TextCatalog.NormalizeText*> | <span data-ttu-id="2f369-147">變更大小寫，移除變音符號、標點符號及數字</span><span class="sxs-lookup"><span data-stu-id="2f369-147">Change case, remove diacritical marks, punctuation marks and numbers</span></span> |
| <xref:Microsoft.ML.TextCatalog.ProduceNgrams*> | <span data-ttu-id="2f369-148">將文字資料行轉換為一袋 ngram 計數 (連續字詞的序列)</span><span class="sxs-lookup"><span data-stu-id="2f369-148">Transform text column into a bag of counts of ngrams (sequences of consecutive words)</span></span>|
| <xref:Microsoft.ML.TextCatalog.ProduceWordBags*> | <span data-ttu-id="2f369-149">將文字資料行轉換為一袋 ngram 向量計數</span><span class="sxs-lookup"><span data-stu-id="2f369-149">Transform text column into a bag of counts of ngrams vector</span></span> |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedNgrams*> | <span data-ttu-id="2f369-150">將文字資料行轉換為雜湊 ngram 計數的向量</span><span class="sxs-lookup"><span data-stu-id="2f369-150">Transform text column into a vector of hashed ngram counts</span></span> |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedWordBags*> | <span data-ttu-id="2f369-151">將文字資料行轉換為一袋雜湊 ngram 計數</span><span class="sxs-lookup"><span data-stu-id="2f369-151">Transform text column into a bag of hashed ngram counts</span></span> |
| <xref:Microsoft.ML.TextCatalog.RemoveDefaultStopWords*>  | <span data-ttu-id="2f369-152">從輸入資料行針對指定語言移除預設停用字詞</span><span class="sxs-lookup"><span data-stu-id="2f369-152">Remove default stop words for the specified language from input columns</span></span> |
| <xref:Microsoft.ML.TextCatalog.RemoveStopWords*> | <span data-ttu-id="2f369-153">從輸入資料行移除指定停用字詞</span><span class="sxs-lookup"><span data-stu-id="2f369-153">Removes specified stop words from input columns</span></span> |
| <xref:Microsoft.ML.TextCatalog.LatentDirichletAllocation*> | <span data-ttu-id="2f369-154">將文件 (以浮點數向量表示) 轉換為一組主題上的浮點數向量</span><span class="sxs-lookup"><span data-stu-id="2f369-154">Transform a document (represented as a vector of floats) into a vector of floats over a set of topics</span></span> |
| <xref:Microsoft.ML.TextCatalog.ApplyWordEmbedding*> | <span data-ttu-id="2f369-155">使用預先定型的模型將文字權杖的向量轉換成句子向量</span><span class="sxs-lookup"><span data-stu-id="2f369-155">Convert vectors of text tokens into sentence vectors using a pre-trained model</span></span> |

## <a name="image-transformations"></a><span data-ttu-id="2f369-156">影像轉換</span><span class="sxs-lookup"><span data-stu-id="2f369-156">Image transformations</span></span>

| <span data-ttu-id="2f369-157">資料轉換</span><span class="sxs-lookup"><span data-stu-id="2f369-157">Transform</span></span> | <span data-ttu-id="2f369-158">定義</span><span class="sxs-lookup"><span data-stu-id="2f369-158">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale*> | <span data-ttu-id="2f369-159">將影像轉換為灰階</span><span class="sxs-lookup"><span data-stu-id="2f369-159">Convert an image to grayscale</span></span> |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToImage*> | <span data-ttu-id="2f369-160">將像素的向量轉換為 <xref:Microsoft.ML.Transforms.Image.ImageDataViewType></span><span class="sxs-lookup"><span data-stu-id="2f369-160">Convert a vector of pixels to <xref:Microsoft.ML.Transforms.Image.ImageDataViewType></span></span> |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*> | <span data-ttu-id="2f369-161">將來自輸入影像的像素轉換為數字向量</span><span class="sxs-lookup"><span data-stu-id="2f369-161">Convert pixels from input image into a vector of numbers</span></span> |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*> | <span data-ttu-id="2f369-162">從資料夾將影像載入記憶體</span><span class="sxs-lookup"><span data-stu-id="2f369-162">Load images from a folder into memory</span></span> |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*> | <span data-ttu-id="2f369-163">調整影像大小</span><span class="sxs-lookup"><span data-stu-id="2f369-163">Resize images</span></span> |

## <a name="categorical-data-transformations"></a><span data-ttu-id="2f369-164">類別資料轉換</span><span class="sxs-lookup"><span data-stu-id="2f369-164">Categorical data transformations</span></span>

| <span data-ttu-id="2f369-165">資料轉換</span><span class="sxs-lookup"><span data-stu-id="2f369-165">Transform</span></span> | <span data-ttu-id="2f369-166">定義</span><span class="sxs-lookup"><span data-stu-id="2f369-166">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*> | <span data-ttu-id="2f369-167">將一或多個文字資料行轉換為 [one-hot](https://en.wikipedia.org/wiki/One-hot) \(英文\) 編碼向量</span><span class="sxs-lookup"><span data-stu-id="2f369-167">Convert one or more text columns into [one-hot](https://en.wikipedia.org/wiki/One-hot) encoded vectors</span></span> |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotHashEncoding*> | <span data-ttu-id="2f369-168">將一或多個文字資料行轉換為以雜湊為基礎的 one-hot 編碼向量</span><span class="sxs-lookup"><span data-stu-id="2f369-168">Convert one more text columns into hash-based one-hot encoded vectors</span></span> |

## <a name="missing-values"></a><span data-ttu-id="2f369-169">遺失值</span><span class="sxs-lookup"><span data-stu-id="2f369-169">Missing values</span></span>

| <span data-ttu-id="2f369-170">資料轉換</span><span class="sxs-lookup"><span data-stu-id="2f369-170">Transform</span></span> | <span data-ttu-id="2f369-171">定義</span><span class="sxs-lookup"><span data-stu-id="2f369-171">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.ExtensionsCatalog.IndicateMissingValues*> | <span data-ttu-id="2f369-172">建立新的布林值輸出資料行，其值在輸入資料行中的值遺失時為 true</span><span class="sxs-lookup"><span data-stu-id="2f369-172">Create a new boolean output column, the value of which is true when the value in the input column is missing</span></span> |
| <xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*> | <span data-ttu-id="2f369-173">建立新的輸出資料行，其值在輸入資料行中的值遺失時會被設為預設值，否則則會為輸入值</span><span class="sxs-lookup"><span data-stu-id="2f369-173">Create a new output column, the value of which is set to a default value if the value is missing from the input column, and the input value otherwise</span></span> |

## <a name="feature-selection"></a><span data-ttu-id="2f369-174">特徵選取</span><span class="sxs-lookup"><span data-stu-id="2f369-174">Feature selection</span></span>

| <span data-ttu-id="2f369-175">資料轉換</span><span class="sxs-lookup"><span data-stu-id="2f369-175">Transform</span></span> | <span data-ttu-id="2f369-176">定義</span><span class="sxs-lookup"><span data-stu-id="2f369-176">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnCount*> | <span data-ttu-id="2f369-177">選取其非預設值大於某個閾值的特徵</span><span class="sxs-lookup"><span data-stu-id="2f369-177">Select features whose non-default values are greater than a threshold</span></span> |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnMutualInformation*> | <span data-ttu-id="2f369-178">選取其標籤資料行中的資料最具相依性的特徵</span><span class="sxs-lookup"><span data-stu-id="2f369-178">Select the features on which the data in the label column is most dependent</span></span> |

## <a name="custom-transformations"></a><span data-ttu-id="2f369-179">自訂轉換</span><span class="sxs-lookup"><span data-stu-id="2f369-179">Custom transformations</span></span>

| <span data-ttu-id="2f369-180">資料轉換</span><span class="sxs-lookup"><span data-stu-id="2f369-180">Transform</span></span> | <span data-ttu-id="2f369-181">定義</span><span class="sxs-lookup"><span data-stu-id="2f369-181">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.CustomMappingCatalog.CustomMapping*> | <span data-ttu-id="2f369-182">搭配使用者定義的對應將現有資料行轉換為新的資料行</span><span class="sxs-lookup"><span data-stu-id="2f369-182">Transform existing columns onto new ones with a user-defined mapping</span></span> |
