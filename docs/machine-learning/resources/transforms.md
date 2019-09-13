---
title: 資料轉換
description: 探索 ML.NET 中支援的特徵工程元件。
author: natke
ms.author: nakersha
ms.date: 04/02/2019
ms.openlocfilehash: 25da3cceb3c9090661b34254ed240207aaf3b9d7
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929247"
---
# <a name="data-transformations"></a><span data-ttu-id="d1075-103">資料轉換</span><span class="sxs-lookup"><span data-stu-id="d1075-103">Data transformations</span></span>

<span data-ttu-id="d1075-104">資料轉換用來：</span><span class="sxs-lookup"><span data-stu-id="d1075-104">Data transformations are used to:</span></span>

- <span data-ttu-id="d1075-105">準備資料以進行模型定型</span><span class="sxs-lookup"><span data-stu-id="d1075-105">prepare data for model training</span></span>
- <span data-ttu-id="d1075-106">以 TensorFlow 或 ONNX 格式套用匯入的模型</span><span class="sxs-lookup"><span data-stu-id="d1075-106">apply an imported model in TensorFlow or ONNX format</span></span>
- <span data-ttu-id="d1075-107">在資料傳遞過模型之後進行後續處理</span><span class="sxs-lookup"><span data-stu-id="d1075-107">post-process data after it has been passed through a model</span></span>

<span data-ttu-id="d1075-108">本指南中的轉換會傳回能實作 [IEstimator](xref:Microsoft.ML.IEstimator%601) 介面的類別。</span><span class="sxs-lookup"><span data-stu-id="d1075-108">The transformations in this guide return classes that implement the [IEstimator](xref:Microsoft.ML.IEstimator%601) interface.</span></span> <span data-ttu-id="d1075-109">資料轉換可以鏈結在一起。</span><span class="sxs-lookup"><span data-stu-id="d1075-109">Data transformations can be chained together.</span></span> <span data-ttu-id="d1075-110">每個轉換都會預期和產生特定類型及格式的資料，其已詳述於連結的參考文件中。</span><span class="sxs-lookup"><span data-stu-id="d1075-110">Each transformation both expects and produces data of specific types and formats, which are specified in the linked reference documentation.</span></span>

<span data-ttu-id="d1075-111">某些資料轉換需要定型資料以計算其參數。</span><span class="sxs-lookup"><span data-stu-id="d1075-111">Some data transformations require training data to calculate their parameters.</span></span> <span data-ttu-id="d1075-112">例如：<xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> 轉換器會在 `Fit()` 作業期間計算定型資料的平均數和變異數，並將那些參數用於 `Transform()` 作業。</span><span class="sxs-lookup"><span data-stu-id="d1075-112">For example: the <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> transformer calculates the mean and variance of the training data during the `Fit()` operation, and uses those parameters in the `Transform()` operation.</span></span> 

<span data-ttu-id="d1075-113">其他資料轉換並不需要定型資料。</span><span class="sxs-lookup"><span data-stu-id="d1075-113">Other data transformations don't require training data.</span></span> <span data-ttu-id="d1075-114">例如：<xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale*> 轉換可以在無須於 `Fit()` 作業期間查看任何定型資料的情況下執行 `Transform()` 作業。</span><span class="sxs-lookup"><span data-stu-id="d1075-114">For example: the <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale*> transformation can perform the `Transform()` operation without having seen any training data during the `Fit()` operation.</span></span>

## <a name="column-mapping-and-grouping"></a><span data-ttu-id="d1075-115">資料行對應及群組</span><span class="sxs-lookup"><span data-stu-id="d1075-115">Column mapping and grouping</span></span>

| <span data-ttu-id="d1075-116">資料轉換</span><span class="sxs-lookup"><span data-stu-id="d1075-116">Transform</span></span> | <span data-ttu-id="d1075-117">定義</span><span class="sxs-lookup"><span data-stu-id="d1075-117">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A> | <span data-ttu-id="d1075-118">將一或多個輸入資料行串連成新的輸出資料行</span><span class="sxs-lookup"><span data-stu-id="d1075-118">Concatenate one or more input columns into a new output column</span></span> |
| <xref:Microsoft.ML.TransformExtensionsCatalog.CopyColumns%2A> | <span data-ttu-id="d1075-119">複製並重新命名一或多個輸入資料行</span><span class="sxs-lookup"><span data-stu-id="d1075-119">Copy and rename one or more input columns</span></span> |
| <xref:Microsoft.ML.TransformExtensionsCatalog.DropColumns%2A> | <span data-ttu-id="d1075-120">卸除一或多個輸入資料行</span><span class="sxs-lookup"><span data-stu-id="d1075-120">Drop one or more input columns</span></span> |
| <xref:Microsoft.ML.TransformExtensionsCatalog.SelectColumns%2A> | <span data-ttu-id="d1075-121">選取一或多個資料行以將其自輸入資料中排除</span><span class="sxs-lookup"><span data-stu-id="d1075-121">Select one or more columns to keep from the input data</span></span> |

## <a name="normalization-and-scaling"></a><span data-ttu-id="d1075-122">標準化和調整</span><span class="sxs-lookup"><span data-stu-id="d1075-122">Normalization and scaling</span></span>

| <span data-ttu-id="d1075-123">資料轉換</span><span class="sxs-lookup"><span data-stu-id="d1075-123">Transform</span></span> | <span data-ttu-id="d1075-124">定義</span><span class="sxs-lookup"><span data-stu-id="d1075-124">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> | <span data-ttu-id="d1075-125">減去 (定型資料的) 平均數並除以 (定型資料的) 變異數</span><span class="sxs-lookup"><span data-stu-id="d1075-125">Subtract the mean (of the training data) and divide by the variance (of the training data)</span></span> |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLogMeanVariance%2A> | <span data-ttu-id="d1075-126">依定型資料的對數進行標準化</span><span class="sxs-lookup"><span data-stu-id="d1075-126">Normalize based on the logarithm of the training data</span></span> |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLpNorm%2A> | <span data-ttu-id="d1075-127">依據輸入向量的 [lp-norm](https://en.wikipedia.org/wiki/Lp_space#The_p-norm_in_finite_dimensions) 來對它進行調整，其中 p 為 1、2 或無限。</span><span class="sxs-lookup"><span data-stu-id="d1075-127">Scale input vectors by their [lp-norm](https://en.wikipedia.org/wiki/Lp_space#The_p-norm_in_finite_dimensions), where p is 1, 2 or infinity.</span></span> <span data-ttu-id="d1075-128">預設為 l2 (歐幾里得距離) 範數</span><span class="sxs-lookup"><span data-stu-id="d1075-128">Defaults to the l2 (Euclidean distance) norm</span></span> |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeGlobalContrast%2A> | <span data-ttu-id="d1075-129">透過減去資料列資料的平均數並除以標準差或 (資料列資料的) l2 範數，並乘以可設定的比例因素 (預設為 2)，來調整資料列中的每個值</span><span class="sxs-lookup"><span data-stu-id="d1075-129">Scale each value in a row by subtracting the mean of the row data and divide by either the standard deviation or l2-norm (of the row data), and multiply by a configurable scale factor (default 2)</span></span> |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A> | <span data-ttu-id="d1075-130">將輸入值指派至 bin 目錄並除以 bin 的數目，以產生介於 0 與 1 的浮點值。</span><span class="sxs-lookup"><span data-stu-id="d1075-130">Assign the input value to a bin index and divide by the number of bins to produce a float value between 0 and 1.</span></span> <span data-ttu-id="d1075-131">系統會以能將定型資料平均分散到所有 bin 上的方式計算 bin 界線</span><span class="sxs-lookup"><span data-stu-id="d1075-131">The bin boundaries are calculated to evenly distribute the training data across bins</span></span> |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeSupervisedBinning%2A> | <span data-ttu-id="d1075-132">根據 bin 與標籤資料行的關聯性將輸入值指派至該 bin</span><span class="sxs-lookup"><span data-stu-id="d1075-132">Assign the input value to a bin based on its correlation with label column</span></span> |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A> | <span data-ttu-id="d1075-133">依定型資料中最小及最大值之間的差異來調整輸入</span><span class="sxs-lookup"><span data-stu-id="d1075-133">Scale the input by the difference between the minimum and maximum values in the training data</span></span> |

## <a name="conversions-between-data-types"></a><span data-ttu-id="d1075-134">資料類型之間的轉換</span><span class="sxs-lookup"><span data-stu-id="d1075-134">Conversions between data types</span></span>

| <span data-ttu-id="d1075-135">資料轉換</span><span class="sxs-lookup"><span data-stu-id="d1075-135">Transform</span></span> | <span data-ttu-id="d1075-136">定義</span><span class="sxs-lookup"><span data-stu-id="d1075-136">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.ConvertType%2A> | <span data-ttu-id="d1075-137">將某個輸入資料行的類型轉換成新的類型</span><span class="sxs-lookup"><span data-stu-id="d1075-137">Convert the type of an input column to a new type</span></span> |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValue*> | <span data-ttu-id="d1075-138">根據所提供的對應字典將值對應至索引鍵 (類別)</span><span class="sxs-lookup"><span data-stu-id="d1075-138">Map values to keys (categories) based on the supplied dictionary of mappings</span></span> |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*> | <span data-ttu-id="d1075-139">透過從輸入資料建立對應來將值對應至索引鍵 (類別)</span><span class="sxs-lookup"><span data-stu-id="d1075-139">Map values to keys (categories) by creating the mapping from the input data</span></span> |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue*> | <span data-ttu-id="d1075-140">將索引鍵轉換為其原始值</span><span class="sxs-lookup"><span data-stu-id="d1075-140">Convert keys back to their original values</span></span> |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToVector*> | <span data-ttu-id="d1075-141">將索引鍵轉換為原始值的向量</span><span class="sxs-lookup"><span data-stu-id="d1075-141">Convert keys back to vectors of original values</span></span> |
| <xref:Microsoft.ML.ConversionsCatalog.MapKeyToBinaryVector*> | <span data-ttu-id="d1075-142">將索引鍵轉換為原始值的二進位向量</span><span class="sxs-lookup"><span data-stu-id="d1075-142">Convert keys back to a binary vector of original values</span></span> |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash*> | <span data-ttu-id="d1075-143">對輸入資料行中的值進行雜湊處理</span><span class="sxs-lookup"><span data-stu-id="d1075-143">Hash the value in the input column</span></span> |

## <a name="text-transformations"></a><span data-ttu-id="d1075-144">文字轉換</span><span class="sxs-lookup"><span data-stu-id="d1075-144">Text transformations</span></span>

| <span data-ttu-id="d1075-145">資料轉換</span><span class="sxs-lookup"><span data-stu-id="d1075-145">Transform</span></span> | <span data-ttu-id="d1075-146">定義</span><span class="sxs-lookup"><span data-stu-id="d1075-146">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.TextCatalog.FeaturizeText*> | <span data-ttu-id="d1075-147">將文字資料行轉換為標準化 ngram 和 char-gram 計數的浮動陣列</span><span class="sxs-lookup"><span data-stu-id="d1075-147">Transform a text column into a float array of normalized ngrams and char-grams counts</span></span> | 
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoWords*> | <span data-ttu-id="d1075-148">將一或多個文字資料行分割為個別字詞</span><span class="sxs-lookup"><span data-stu-id="d1075-148">Split one or more text columns into individual words</span></span> |
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoCharactersAsKeys*> | <span data-ttu-id="d1075-149">將一或多個文字資料行分割為於一組主題上的個別字元浮點數</span><span class="sxs-lookup"><span data-stu-id="d1075-149">Split one or more text columns into individual characters floats over a set of topics</span></span> |
| <xref:Microsoft.ML.TextCatalog.NormalizeText*> | <span data-ttu-id="d1075-150">變更大小寫，移除變音符號、標點符號及數字</span><span class="sxs-lookup"><span data-stu-id="d1075-150">Change case, remove diacritical marks, punctuation marks, and numbers</span></span> |
| <xref:Microsoft.ML.TextCatalog.ProduceNgrams*> | <span data-ttu-id="d1075-151">將文字資料行轉換為一袋 ngram 計數 (連續字詞的序列)</span><span class="sxs-lookup"><span data-stu-id="d1075-151">Transform text column into a bag of counts of ngrams (sequences of consecutive words)</span></span>|
| <xref:Microsoft.ML.TextCatalog.ProduceWordBags*> | <span data-ttu-id="d1075-152">將文字資料行轉換為一袋 ngram 向量計數</span><span class="sxs-lookup"><span data-stu-id="d1075-152">Transform text column into a bag of counts of ngrams vector</span></span> |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedNgrams*> | <span data-ttu-id="d1075-153">將文字資料行轉換為雜湊 ngram 計數的向量</span><span class="sxs-lookup"><span data-stu-id="d1075-153">Transform text column into a vector of hashed ngram counts</span></span> |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedWordBags*> | <span data-ttu-id="d1075-154">將文字資料行轉換為一袋雜湊 ngram 計數</span><span class="sxs-lookup"><span data-stu-id="d1075-154">Transform text column into a bag of hashed ngram counts</span></span> |
| <xref:Microsoft.ML.TextCatalog.RemoveDefaultStopWords*>  | <span data-ttu-id="d1075-155">從輸入資料行針對指定語言移除預設停用字詞</span><span class="sxs-lookup"><span data-stu-id="d1075-155">Remove default stop words for the specified language from input columns</span></span> |
| <xref:Microsoft.ML.TextCatalog.RemoveStopWords*> | <span data-ttu-id="d1075-156">從輸入資料行移除指定停用字詞</span><span class="sxs-lookup"><span data-stu-id="d1075-156">Removes specified stop words from input columns</span></span> |
| <xref:Microsoft.ML.TextCatalog.LatentDirichletAllocation*> | <span data-ttu-id="d1075-157">將文件 (以浮點數向量表示) 轉換為一組主題上的浮點數向量</span><span class="sxs-lookup"><span data-stu-id="d1075-157">Transform a document (represented as a vector of floats) into a vector of floats over a set of topics</span></span> |
| <xref:Microsoft.ML.TextCatalog.ApplyWordEmbedding*> | <span data-ttu-id="d1075-158">使用預先定型的模型將文字權杖的向量轉換成句子向量</span><span class="sxs-lookup"><span data-stu-id="d1075-158">Convert vectors of text tokens into sentence vectors using a pre-trained model</span></span> |

## <a name="image-transformations"></a><span data-ttu-id="d1075-159">影像轉換</span><span class="sxs-lookup"><span data-stu-id="d1075-159">Image transformations</span></span>

| <span data-ttu-id="d1075-160">資料轉換</span><span class="sxs-lookup"><span data-stu-id="d1075-160">Transform</span></span> | <span data-ttu-id="d1075-161">定義</span><span class="sxs-lookup"><span data-stu-id="d1075-161">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale*> | <span data-ttu-id="d1075-162">將影像轉換為灰階</span><span class="sxs-lookup"><span data-stu-id="d1075-162">Convert an image to grayscale</span></span> |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToImage*> | <span data-ttu-id="d1075-163">將像素的向量轉換為 <xref:Microsoft.ML.Transforms.Image.ImageDataViewType></span><span class="sxs-lookup"><span data-stu-id="d1075-163">Convert a vector of pixels to <xref:Microsoft.ML.Transforms.Image.ImageDataViewType></span></span> |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*> | <span data-ttu-id="d1075-164">將來自輸入影像的像素轉換為數字向量</span><span class="sxs-lookup"><span data-stu-id="d1075-164">Convert pixels from input image into a vector of numbers</span></span> |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*> | <span data-ttu-id="d1075-165">從資料夾將影像載入記憶體</span><span class="sxs-lookup"><span data-stu-id="d1075-165">Load images from a folder into memory</span></span> |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*> | <span data-ttu-id="d1075-166">調整影像大小</span><span class="sxs-lookup"><span data-stu-id="d1075-166">Resize images</span></span> |
| <xref:Microsoft.ML.OnnxCatalog.DnnFeaturizeImage*> | <span data-ttu-id="d1075-167">套用預先定型的深度神經網路 (DNN) 模型，將輸入影像轉換成特徵向量</span><span class="sxs-lookup"><span data-stu-id="d1075-167">Applies a pre-trained deep neural network (DNN) model to transform an input image into a feature vector</span></span> |

## <a name="categorical-data-transformations"></a><span data-ttu-id="d1075-168">類別資料轉換</span><span class="sxs-lookup"><span data-stu-id="d1075-168">Categorical data transformations</span></span>

| <span data-ttu-id="d1075-169">資料轉換</span><span class="sxs-lookup"><span data-stu-id="d1075-169">Transform</span></span> | <span data-ttu-id="d1075-170">定義</span><span class="sxs-lookup"><span data-stu-id="d1075-170">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*> | <span data-ttu-id="d1075-171">將一或多個文字資料行轉換為 [one-hot](https://en.wikipedia.org/wiki/One-hot) \(英文\) 編碼向量</span><span class="sxs-lookup"><span data-stu-id="d1075-171">Convert one or more text columns into [one-hot](https://en.wikipedia.org/wiki/One-hot) encoded vectors</span></span> |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotHashEncoding*> | <span data-ttu-id="d1075-172">將一或多個文字資料行轉換為以雜湊為基礎的 one-hot 編碼向量</span><span class="sxs-lookup"><span data-stu-id="d1075-172">Convert one or more text columns into hash-based one-hot encoded vectors</span></span> |

## <a name="time-series-data-transformations"></a><span data-ttu-id="d1075-173">時間序列資料轉換</span><span class="sxs-lookup"><span data-stu-id="d1075-173">Time series data transformations</span></span>

| <span data-ttu-id="d1075-174">資料轉換</span><span class="sxs-lookup"><span data-stu-id="d1075-174">Transform</span></span> | <span data-ttu-id="d1075-175">定義</span><span class="sxs-lookup"><span data-stu-id="d1075-175">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectAnomalyBySrCnn*> | <span data-ttu-id="d1075-176">使用光譜殘留 (SR) 演算法偵測輸入時間序列資料中的異常</span><span class="sxs-lookup"><span data-stu-id="d1075-176">Detect anomalies in the input time series data using the Spectral Residual (SR) algorithm</span></span> |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectChangePointBySsa*> | <span data-ttu-id="d1075-177">使用單一頻譜分析 (SSA) 偵測時間序列資料中的變更點</span><span class="sxs-lookup"><span data-stu-id="d1075-177">Detect change points in time series data using singular spectrum analysis (SSA)</span></span> |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectIidChangePoint*> | <span data-ttu-id="d1075-178">使用彈性核心密度估計和鞅分數，偵測獨立和相同分散式 (IID) 時間序列資料中的變更點</span><span class="sxs-lookup"><span data-stu-id="d1075-178">Detect change points in independent and identically distributed (IID) time series data using adaptive kernel density estimations and martingale scores</span></span> |
| <xref:Microsoft.ML.TimeSeriesCatalog.ForecastBySsa*> | <span data-ttu-id="d1075-179">使用單一頻譜分析 (SSA) 預測時間序列資料</span><span class="sxs-lookup"><span data-stu-id="d1075-179">Forecast time series data using singular spectrum analysis (SSA)</span></span> |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectSpikeBySsa*> | <span data-ttu-id="d1075-180">使用單一頻譜分析 (SSA) 偵測時間序列資料中的尖峰</span><span class="sxs-lookup"><span data-stu-id="d1075-180">Detect spikes in time series data using singular spectrum analysis (SSA)</span></span> |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectIidSpike*> | <span data-ttu-id="d1075-181">使用彈性核心密度估計和鞅分數，偵測獨立和相同分散式 (IID) 時間序列資料中的尖峰</span><span class="sxs-lookup"><span data-stu-id="d1075-181">Detect spikes in independent and identically distributed (IID) time series data using adaptive kernel density estimations and martingale scores</span></span> |

## <a name="missing-values"></a><span data-ttu-id="d1075-182">遺失值</span><span class="sxs-lookup"><span data-stu-id="d1075-182">Missing values</span></span>

| <span data-ttu-id="d1075-183">資料轉換</span><span class="sxs-lookup"><span data-stu-id="d1075-183">Transform</span></span> | <span data-ttu-id="d1075-184">定義</span><span class="sxs-lookup"><span data-stu-id="d1075-184">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.ExtensionsCatalog.IndicateMissingValues*> | <span data-ttu-id="d1075-185">建立新的布林值輸出資料行，其值在輸入資料行中的值遺失時為 true</span><span class="sxs-lookup"><span data-stu-id="d1075-185">Create a new boolean output column, the value of which is true when the value in the input column is missing</span></span> |
| <xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*> | <span data-ttu-id="d1075-186">建立新的輸出資料行，其值在輸入資料行中的值遺失時會被設為預設值，否則則會為輸入值</span><span class="sxs-lookup"><span data-stu-id="d1075-186">Create a new output column, the value of which is set to a default value if the value is missing from the input column, and the input value otherwise</span></span> |

## <a name="feature-selection"></a><span data-ttu-id="d1075-187">特徵選取</span><span class="sxs-lookup"><span data-stu-id="d1075-187">Feature selection</span></span>

| <span data-ttu-id="d1075-188">資料轉換</span><span class="sxs-lookup"><span data-stu-id="d1075-188">Transform</span></span> | <span data-ttu-id="d1075-189">定義</span><span class="sxs-lookup"><span data-stu-id="d1075-189">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnCount*> | <span data-ttu-id="d1075-190">選取其非預設值大於某個閾值的特徵</span><span class="sxs-lookup"><span data-stu-id="d1075-190">Select features whose non-default values are greater than a threshold</span></span> |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnMutualInformation*> | <span data-ttu-id="d1075-191">選取其標籤資料行中的資料最具相依性的特徵</span><span class="sxs-lookup"><span data-stu-id="d1075-191">Select the features on which the data in the label column is most dependent</span></span> |

## <a name="feature-transformations"></a><span data-ttu-id="d1075-192">功能轉換</span><span class="sxs-lookup"><span data-stu-id="d1075-192">Feature transformations</span></span>

| <span data-ttu-id="d1075-193">資料轉換</span><span class="sxs-lookup"><span data-stu-id="d1075-193">Transform</span></span> | <span data-ttu-id="d1075-194">定義</span><span class="sxs-lookup"><span data-stu-id="d1075-194">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.KernelExpansionCatalog.ApproximatedKernelMap*> | <span data-ttu-id="d1075-195">將每個輸入向量對應至較低維度的功能空間，其中內部產品會近似核心函式，以便可以將功能當作線性演算法的輸入使用</span><span class="sxs-lookup"><span data-stu-id="d1075-195">Map each input vector onto a lower dimensional feature space, where inner products approximate a kernel function, so that the features can be used as inputs to the linear algorithms</span></span> |
| <xref:Microsoft.ML.PcaCatalog.ProjectToPrincipalComponents*> | <span data-ttu-id="d1075-196">套用主體元件分析演算法，以減少輸入特徵向量的維度</span><span class="sxs-lookup"><span data-stu-id="d1075-196">Reduce the dimensions of the input feature vector by applying the Principal Component Analysis algorithm</span></span> |

## <a name="explainability-transformations"></a><span data-ttu-id="d1075-197">可解釋性轉換</span><span class="sxs-lookup"><span data-stu-id="d1075-197">Explainability transformations</span></span>

| <span data-ttu-id="d1075-198">資料轉換</span><span class="sxs-lookup"><span data-stu-id="d1075-198">Transform</span></span> | <span data-ttu-id="d1075-199">定義</span><span class="sxs-lookup"><span data-stu-id="d1075-199">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.ExplainabilityCatalog.CalculateFeatureContribution*> | <span data-ttu-id="d1075-200">為特徵向量的每個元素計算貢獻分數</span><span class="sxs-lookup"><span data-stu-id="d1075-200">Calculate contribution scores for each element of a feature vector</span></span> |

## <a name="calibration-transformations"></a><span data-ttu-id="d1075-201">校正轉換</span><span class="sxs-lookup"><span data-stu-id="d1075-201">Calibration transformations</span></span>

| <span data-ttu-id="d1075-202">資料轉換</span><span class="sxs-lookup"><span data-stu-id="d1075-202">Transform</span></span> | <span data-ttu-id="d1075-203">定義</span><span class="sxs-lookup"><span data-stu-id="d1075-203">Definition</span></span> |
| --- | --- |
|<xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Platt%28System.String%2CSystem.String%2CSystem.String%29> | <span data-ttu-id="d1075-204">使用羅吉斯回歸搭配使用定型資料估計的參數，將二元分類器原始分數轉換成類別機率</span><span class="sxs-lookup"><span data-stu-id="d1075-204">Transforms a binary classifier raw score into a class probability using logistic regression with parameters estimated using the training data</span></span> |
| <xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Platt%28System.Double%2CSystem.Double%2CSystem.String%29> | <span data-ttu-id="d1075-205">使用羅吉斯回歸搭配固定參數，將二元分類器原始分數轉換成類別機率</span><span class="sxs-lookup"><span data-stu-id="d1075-205">Transforms a binary classifier raw score into a class probability using logistic regression with fixed parameters</span></span> |
| <xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Naive*> | <span data-ttu-id="d1075-206">藉由將分數指派給 Bin，並根據各 Bin 間的分佈計算機率，將二元分類器原始分數轉換成類別機率</span><span class="sxs-lookup"><span data-stu-id="d1075-206">Transforms a binary classifier raw score into a class probability by assigning scores to bins, and calculating the probability based on the distribution among the bins</span></span> |
| <xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Isotonic*> | <span data-ttu-id="d1075-207">藉由將分數指派給 Bin 來將二元分類器原始分數轉換成類別機率，其中會使用定型資料來估計界限的位置和 Bin 的大小</span><span class="sxs-lookup"><span data-stu-id="d1075-207">Transforms a binary classifier raw score into a class probability by assigning scores to bins, where the position of boundaries and the size of bins are estimated using the training data</span></span>  |

## <a name="deep-learning-transformations"></a><span data-ttu-id="d1075-208">深度學習轉換</span><span class="sxs-lookup"><span data-stu-id="d1075-208">Deep learning transformations</span></span>

| <span data-ttu-id="d1075-209">資料轉換</span><span class="sxs-lookup"><span data-stu-id="d1075-209">Transform</span></span> | <span data-ttu-id="d1075-210">定義</span><span class="sxs-lookup"><span data-stu-id="d1075-210">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*> | <span data-ttu-id="d1075-211">使用匯入的 ONNX 模型轉換輸入資料</span><span class="sxs-lookup"><span data-stu-id="d1075-211">Transform the input data with an imported ONNX model</span></span> |
| <xref:Microsoft.ML.TensorflowCatalog.LoadTensorFlowModel*> | <span data-ttu-id="d1075-212">使用匯入的 TensorFlow 模型轉換輸入資料</span><span class="sxs-lookup"><span data-stu-id="d1075-212">Transform the input data with an imported TensorFlow model</span></span> |

## <a name="custom-transformations"></a><span data-ttu-id="d1075-213">自訂轉換</span><span class="sxs-lookup"><span data-stu-id="d1075-213">Custom transformations</span></span>

| <span data-ttu-id="d1075-214">資料轉換</span><span class="sxs-lookup"><span data-stu-id="d1075-214">Transform</span></span> | <span data-ttu-id="d1075-215">定義</span><span class="sxs-lookup"><span data-stu-id="d1075-215">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.CustomMappingCatalog.CustomMapping*> | <span data-ttu-id="d1075-216">搭配使用者定義的對應將現有資料行轉換為新的資料行</span><span class="sxs-lookup"><span data-stu-id="d1075-216">Transform existing columns onto new ones with a user-defined mapping</span></span> |
