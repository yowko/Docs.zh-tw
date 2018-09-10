---
title: 資料轉換
description: 探索 ML.NET 中支援的不同資料轉換。
ms.date: 08/08/2018
author: jralexander
ms.author: johalex
ms.openlocfilehash: 3c483f4a263052eb15435775a47f514893eee049
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519391"
---
# <a name="data-transforms"></a><span data-ttu-id="82ca7-103">資料轉換</span><span class="sxs-lookup"><span data-stu-id="82ca7-103">Data transforms</span></span>

<span data-ttu-id="82ca7-104">下列表格包含 ML.NET 支援的所有資料轉換相關資訊 (選取資料轉換類型以巡覽至對應的表格)：</span><span class="sxs-lookup"><span data-stu-id="82ca7-104">The following tables contain information about all of the data transforms supported in ML.NET (select the data transform type to navigate to the corresponding table):</span></span>

* [<span data-ttu-id="82ca7-105">類別目錄</span><span class="sxs-lookup"><span data-stu-id="82ca7-105">Categorical</span></span>](#categorical)
* [<span data-ttu-id="82ca7-106">結合工具與分離工具</span><span class="sxs-lookup"><span data-stu-id="82ca7-106">Combiners and segregators</span></span>](#combiners-and-segregators)
* [<span data-ttu-id="82ca7-107">特徵選取</span><span class="sxs-lookup"><span data-stu-id="82ca7-107">Feature selection</span></span>](#feature-selection)
* [<span data-ttu-id="82ca7-108">特徵化工具</span><span class="sxs-lookup"><span data-stu-id="82ca7-108">Featurizers</span></span>](#featurizers)
* [<span data-ttu-id="82ca7-109">標籤剖析</span><span class="sxs-lookup"><span data-stu-id="82ca7-109">Label parsing</span></span>](#label-parsing)
* [<span data-ttu-id="82ca7-110">遺失值</span><span class="sxs-lookup"><span data-stu-id="82ca7-110">Missing Values</span></span>](#missing-values)
* [<span data-ttu-id="82ca7-111">正規化</span><span class="sxs-lookup"><span data-stu-id="82ca7-111">Normalization</span></span>](#normalization)
* [<span data-ttu-id="82ca7-112">資料列篩選</span><span class="sxs-lookup"><span data-stu-id="82ca7-112">Row filters</span></span>](#row-filters)
* [<span data-ttu-id="82ca7-113">結構描述</span><span class="sxs-lookup"><span data-stu-id="82ca7-113">Schema</span></span>](#schema)
* [<span data-ttu-id="82ca7-114">文字處理與特徵化</span><span class="sxs-lookup"><span data-stu-id="82ca7-114">Text processing and featurization</span></span>](#text-processing-and-featurization)
* [<span data-ttu-id="82ca7-115">其他</span><span class="sxs-lookup"><span data-stu-id="82ca7-115">Miscellaneous</span></span>](#miscellaneous)

> [!NOTE]
> <span data-ttu-id="82ca7-116">ML.NET 目前為預覽版。</span><span class="sxs-lookup"><span data-stu-id="82ca7-116">ML.NET is currently in Preview.</span></span> <span data-ttu-id="82ca7-117">目前並不支援所有資料轉換。</span><span class="sxs-lookup"><span data-stu-id="82ca7-117">Not all data transforms are currently supported.</span></span> <span data-ttu-id="82ca7-118">若要提出特定轉換的要求，請在 [dotnet/machinelearning](https://github.com/dotnet/machinelearning/issues) GitHub 存放庫中提出問題。</span><span class="sxs-lookup"><span data-stu-id="82ca7-118">To submit a request for a certain transform, open an issue in the [dotnet/machinelearning](https://github.com/dotnet/machinelearning/issues) GitHub repository.</span></span>

## <a name="categorical"></a><span data-ttu-id="82ca7-119">類別目錄</span><span class="sxs-lookup"><span data-stu-id="82ca7-119">Categorical</span></span>

| <span data-ttu-id="82ca7-120">Transform</span><span class="sxs-lookup"><span data-stu-id="82ca7-120">Transform</span></span> | <span data-ttu-id="82ca7-121">定義</span><span class="sxs-lookup"><span data-stu-id="82ca7-121">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.Transforms.CategoricalHashOneHotVectorizer> | <span data-ttu-id="82ca7-122">使用雜湊式編碼對類別目錄變數進行編碼。</span><span class="sxs-lookup"><span data-stu-id="82ca7-122">Encodes the categorical variable with hash-based encoding.</span></span> |
| <xref:Microsoft.ML.Transforms.CategoricalOneHotVectorizer> | <span data-ttu-id="82ca7-123">使用以字詞字典為基礎的 one-hot 編碼對類別目錄進行編碼。</span><span class="sxs-lookup"><span data-stu-id="82ca7-123">Encodes the categorical variable with one-hot encoding based on a term dictionary.</span></span> |

## <a name="combiners-and-segregators"></a><span data-ttu-id="82ca7-124">結合工具與分離工具</span><span class="sxs-lookup"><span data-stu-id="82ca7-124">Combiners and segregators</span></span>

| <span data-ttu-id="82ca7-125">Transform</span><span class="sxs-lookup"><span data-stu-id="82ca7-125">Transform</span></span> | <span data-ttu-id="82ca7-126">定義</span><span class="sxs-lookup"><span data-stu-id="82ca7-126">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.Transforms.CombinerByContiguousGroupId> | <span data-ttu-id="82ca7-127">將純量資料行的值組成以連續群組識別碼為基礎的向量。</span><span class="sxs-lookup"><span data-stu-id="82ca7-127">Groups values of a scalar column into a vector based on a contiguous group ID.</span></span> |
| <xref:Microsoft.ML.Transforms.FeatureCombiner> | <span data-ttu-id="82ca7-128">將所有功能合併為一個功能資料行。</span><span class="sxs-lookup"><span data-stu-id="82ca7-128">Combines all the features into one feature column.</span></span> |
| <xref:Microsoft.ML.Transforms.ManyHeterogeneousModelCombiner> | <span data-ttu-id="82ca7-129">將 TransformModels 和 PredictorModel 的序列合併成單一 PredictorModel。</span><span class="sxs-lookup"><span data-stu-id="82ca7-129">Combines a sequence of TransformModels and a PredictorModel into a single PredictorModel.</span></span> |
| <xref:Microsoft.ML.Transforms.ModelCombiner> | <span data-ttu-id="82ca7-130">將 TransformModels 序列合併成單一模型。</span><span class="sxs-lookup"><span data-stu-id="82ca7-130">Combines a sequence of TransformModels into a single model.</span></span> |
| <xref:Microsoft.ML.Transforms.Segregator> | <span data-ttu-id="82ca7-131">取消向量資料行的群組並分成資料列序列；Group 轉換的相反。</span><span class="sxs-lookup"><span data-stu-id="82ca7-131">Ungroups vector columns into sequences of rows; the inverse of Group transform.</span></span> |
| <xref:Microsoft.ML.Transforms.TwoHeterogeneousModelCombiner> | <span data-ttu-id="82ca7-132">將 TransformModels 和 PredictorModel 合併成單一 PredictorModel。</span><span class="sxs-lookup"><span data-stu-id="82ca7-132">Combines a TransformModel and a PredictorModel into a single PredictorModel.</span></span> |

## <a name="feature-selection"></a><span data-ttu-id="82ca7-133">特徵選取</span><span class="sxs-lookup"><span data-stu-id="82ca7-133">Feature selection</span></span>

| <span data-ttu-id="82ca7-134">Transform</span><span class="sxs-lookup"><span data-stu-id="82ca7-134">Transform</span></span> | <span data-ttu-id="82ca7-135">定義</span><span class="sxs-lookup"><span data-stu-id="82ca7-135">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.Transforms.FeatureSelectorByCount> | <span data-ttu-id="82ca7-136">選取非預設值計數大於等於閾值的位置。</span><span class="sxs-lookup"><span data-stu-id="82ca7-136">Selects the slots for which the count of non-default values is greater than or equal to a threshold.</span></span> |
| <xref:Microsoft.ML.Transforms.FeatureSelectorByMutualInformation> | <span data-ttu-id="82ca7-137">使用標籤資料行選取所有指定資料行的前 k 個位置，並根據其相互資訊進行排序。</span><span class="sxs-lookup"><span data-stu-id="82ca7-137">Selects the top k slots across all specified columns ordered by their mutual information with the label column.</span></span> |

## <a name="featurizers"></a><span data-ttu-id="82ca7-138">特徵化工具</span><span class="sxs-lookup"><span data-stu-id="82ca7-138">Featurizers</span></span>

| <span data-ttu-id="82ca7-139">Transform</span><span class="sxs-lookup"><span data-stu-id="82ca7-139">Transform</span></span> | <span data-ttu-id="82ca7-140">定義</span><span class="sxs-lookup"><span data-stu-id="82ca7-140">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.Transforms.HashConverter> | <span data-ttu-id="82ca7-141">將資料行值轉換成雜湊。</span><span class="sxs-lookup"><span data-stu-id="82ca7-141">Converts column values into hashes.</span></span> <span data-ttu-id="82ca7-142">這項轉換接受數值及文字輸入，也接受單一及向量值資料行。</span><span class="sxs-lookup"><span data-stu-id="82ca7-142">This transform accepts both numeric and text inputs, both single and vector-valued columns.</span></span> |
| <xref:Microsoft.ML.Transforms.TreeLeafFeaturizer> | <span data-ttu-id="82ca7-143">訓練整體樹狀或從檔案載入，然後將數值特徵向量對應至三個輸出：1.</span><span class="sxs-lookup"><span data-stu-id="82ca7-143">Trains a tree ensemble, or loads it from a file, then maps a numeric feature vector to three outputs: 1.</span></span> <span data-ttu-id="82ca7-144">包含整體樹狀中個別樹狀輸出的向量。</span><span class="sxs-lookup"><span data-stu-id="82ca7-144">A vector containing the individual tree outputs of the tree ensemble.</span></span> <span data-ttu-id="82ca7-145">2.</span><span class="sxs-lookup"><span data-stu-id="82ca7-145">2.</span></span> <span data-ttu-id="82ca7-146">指出整體樹狀中特徵向量所在分葉的向量。</span><span class="sxs-lookup"><span data-stu-id="82ca7-146">A vector indicating the leaves that the feature vector falls on in the tree ensemble.</span></span> <span data-ttu-id="82ca7-147">3.</span><span class="sxs-lookup"><span data-stu-id="82ca7-147">3.</span></span> <span data-ttu-id="82ca7-148">指出整體樹狀中特徵向量所在路徑的向量。</span><span class="sxs-lookup"><span data-stu-id="82ca7-148">A vector indicating the paths that the feature vector falls on in the tree ensemble.</span></span> <span data-ttu-id="82ca7-149">若同時指定模型檔案及訓練員，則向量會使用模型檔案。</span><span class="sxs-lookup"><span data-stu-id="82ca7-149">If both a model file and a trainer are specified, the vector will use the model file.</span></span> <span data-ttu-id="82ca7-150">若兩者皆未指定，則向量會訓練預設 FastTree 模型。</span><span class="sxs-lookup"><span data-stu-id="82ca7-150">If neither are specified, the vector will train a default FastTree model.</span></span> <span data-ttu-id="82ca7-151">這可透過訓練針對其選擇性排列索引的迴歸模型，來處理索引鍵標籤。</span><span class="sxs-lookup"><span data-stu-id="82ca7-151">This can handle key labels by training a regression model towards their optionally permuted indices.</span></span> |

## <a name="label-parsing"></a><span data-ttu-id="82ca7-152">標籤剖析</span><span class="sxs-lookup"><span data-stu-id="82ca7-152">Label parsing</span></span>

| <span data-ttu-id="82ca7-153">Transform</span><span class="sxs-lookup"><span data-stu-id="82ca7-153">Transform</span></span> | <span data-ttu-id="82ca7-154">定義</span><span class="sxs-lookup"><span data-stu-id="82ca7-154">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.Transforms.Dictionarizer> | <span data-ttu-id="82ca7-155">將輸入值 (文字、數字等) 轉換成字典中的索引。</span><span class="sxs-lookup"><span data-stu-id="82ca7-155">Converts input values (words, numbers, etc.) to index in a dictionary.</span></span> |
| <xref:Microsoft.ML.Transforms.LabelColumnKeyBooleanConverter> | <span data-ttu-id="82ca7-156">將標籤轉換成索引鍵或布林值，使其適合用於分類。</span><span class="sxs-lookup"><span data-stu-id="82ca7-156">Transforms the label to either key or bool (if needed) to make it suitable for classification.</span></span> |
| <xref:Microsoft.ML.Transforms.LabelIndicator> | <span data-ttu-id="82ca7-157">OVA 使用的標籤重新對應。</span><span class="sxs-lookup"><span data-stu-id="82ca7-157">Label remapper used by OVA.</span></span> |
| <xref:Microsoft.ML.Transforms.LabelToFloatConverter> | <span data-ttu-id="82ca7-158">將標籤轉換成浮點數，使其適合用於迴歸。</span><span class="sxs-lookup"><span data-stu-id="82ca7-158">Transforms the label to float to make it suitable for regression.</span></span> |
| <xref:Microsoft.ML.Transforms.PredictedLabelColumnOriginalValueConverter> | <span data-ttu-id="82ca7-159">將預測的標籤資料行轉換為其原始值 (除非其類型為布林值)。</span><span class="sxs-lookup"><span data-stu-id="82ca7-159">Transforms a predicted label column to its original values, unless it is of type bool.</span></span> |

## <a name="missing-values"></a><span data-ttu-id="82ca7-160">遺失值</span><span class="sxs-lookup"><span data-stu-id="82ca7-160">Missing Values</span></span>

| <span data-ttu-id="82ca7-161">Transform</span><span class="sxs-lookup"><span data-stu-id="82ca7-161">Transform</span></span> | <span data-ttu-id="82ca7-162">定義</span><span class="sxs-lookup"><span data-stu-id="82ca7-162">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.Transforms.MissingValueHandler> | <span data-ttu-id="82ca7-163">透過使用預設值或平均值/最小值/最大值取代遺失值，來處理遺失值 (僅限非文字資料行)。</span><span class="sxs-lookup"><span data-stu-id="82ca7-163">Handle missing values by replacing them with either the default value or the mean/min/max value (for non-text columns only).</span></span> <span data-ttu-id="82ca7-164">若輸入資料行類型為數值，則可選擇性串連指標資料行。</span><span class="sxs-lookup"><span data-stu-id="82ca7-164">An indicator column can optionally be concatenated, if the input column type is numeric.</span></span> |
| <xref:Microsoft.ML.Transforms.MissingValueIndicator> | <span data-ttu-id="82ca7-165">使用相同數量的位置作為輸入資料行建立布林值輸出資料行，並在遺失輸入資料行中的值時，將輸出值設為 true。</span><span class="sxs-lookup"><span data-stu-id="82ca7-165">Create a boolean output column with the same number of slots as the input column, where the output value is true if the value in the input column is missing.</span></span> |
| <xref:Microsoft.ML.Transforms.MissingValuesDropper> | <span data-ttu-id="82ca7-166">從向量資料行移除所有 NA。</span><span class="sxs-lookup"><span data-stu-id="82ca7-166">Removes NAs from vector columns.</span></span> |
| <xref:Microsoft.ML.Transforms.MissingValuesRowDropper> | <span data-ttu-id="82ca7-167">篩選出包含遺失值的資料列。</span><span class="sxs-lookup"><span data-stu-id="82ca7-167">Filters out rows that contain missing values.</span></span> |
| <xref:Microsoft.ML.Transforms.MissingValueSubstitutor> | <span data-ttu-id="82ca7-168">建立類型相同且輸入資料行大小也相同的輸出資料行，並在其中使用預設值或平均值/最小值/最大值取代遺失值 (僅限非文字資料行)。</span><span class="sxs-lookup"><span data-stu-id="82ca7-168">Create an output column of the same type and size of the input column, where missing values are replaced with either the default value or the mean/min/max value (for non-text columns only).</span></span> |

## <a name="normalization"></a><span data-ttu-id="82ca7-169">正規化</span><span class="sxs-lookup"><span data-stu-id="82ca7-169">Normalization</span></span>

| <span data-ttu-id="82ca7-170">Transform</span><span class="sxs-lookup"><span data-stu-id="82ca7-170">Transform</span></span> | <span data-ttu-id="82ca7-171">定義</span><span class="sxs-lookup"><span data-stu-id="82ca7-171">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.Transforms.BinNormalizer> | <span data-ttu-id="82ca7-172">值會指派給密度相等的 bin，並且單一值會對應到其 bin_number / number_of_bins。</span><span class="sxs-lookup"><span data-stu-id="82ca7-172">The values are assigned into equidensity bins and a value is mapped to its bin_number / number_of_bins.</span></span> |
| <xref:Microsoft.ML.Transforms.ConditionalNormalizer> | <span data-ttu-id="82ca7-173">請只在需要的時候進行正規化。</span><span class="sxs-lookup"><span data-stu-id="82ca7-173">Normalize the columns only if needed.</span></span> |
| <xref:Microsoft.ML.Transforms.GlobalContrastNormalizer> | <span data-ttu-id="82ca7-174">在輸入值上執行全域對比正規化：Y = (s \* X - M) / D，其中 s 為比例、M 為平均數，D 則為 L2 範數或標準差。</span><span class="sxs-lookup"><span data-stu-id="82ca7-174">Performs a global contrast normalization on input values: Y = (s \* X - M) / D, where s is a scale, M is mean and D is either L2 norm or standard deviation.</span></span> | 
| <xref:Microsoft.ML.Transforms.LogMeanVarianceNormalizer> | <span data-ttu-id="82ca7-175">根據計算的平均數和資料對數的變異數，對資料進行正規化。</span><span class="sxs-lookup"><span data-stu-id="82ca7-175">Normalizes the data based on the computed mean and variance of the logarithm of the data.</span></span> |
| <xref:Microsoft.ML.Transforms.LpNormalizer> | <span data-ttu-id="82ca7-176">透過將其調整為單位範數 (L2、L1 或 LInf) 來正規化個別向量 (資料列)。</span><span class="sxs-lookup"><span data-stu-id="82ca7-176">Normalize vectors (rows) individually by rescaling them to the unit norm (L2, L1 or LInf).</span></span> <span data-ttu-id="82ca7-177">在向量上執行下列運算 X: Y = (X - M) / D，其中 M 為平均數，D 為 L2 範數、L1 範數或 LInf 範數。</span><span class="sxs-lookup"><span data-stu-id="82ca7-177">Performs the following operation on a vector X: Y = (X - M) / D, where M is mean and D is either the L2 norm, the L1 norm, or the LInf norm.</span></span> |
| <xref:Microsoft.ML.Transforms.MeanVarianceNormalizer> | <span data-ttu-id="82ca7-178">根據計算的平均數和資料的變異數，對資料進行正規化。</span><span class="sxs-lookup"><span data-stu-id="82ca7-178">Normalizes the data based on the computed mean and variance of the data.</span></span> |
| <xref:Microsoft.ML.Transforms.MinMaxNormalizer> | <span data-ttu-id="82ca7-179">根據觀察到的資料最小值和最大值，對資料進行正規化。</span><span class="sxs-lookup"><span data-stu-id="82ca7-179">Normalizes the data based on the observed minimum and maximum values of the data.</span></span> |
| <xref:Microsoft.ML.Transforms.SupervisedBinNormalizer> | <span data-ttu-id="82ca7-180">與 <xref:Microsoft.ML.Transforms.BinNormalizer> 相似，但會根據標籤資料行的相互關聯計算 bin，而非相等密度。</span><span class="sxs-lookup"><span data-stu-id="82ca7-180">Similar to <xref:Microsoft.ML.Transforms.BinNormalizer>, but calculates bins based on correlation with the label column, not equidensity.</span></span> <span data-ttu-id="82ca7-181">新的值為 bin_number / number_of_bins。</span><span class="sxs-lookup"><span data-stu-id="82ca7-181">The new value is bin_number / number_of_bins.</span></span> |

## <a name="row-filters"></a><span data-ttu-id="82ca7-182">資料列篩選</span><span class="sxs-lookup"><span data-stu-id="82ca7-182">Row Filters</span></span>

| <span data-ttu-id="82ca7-183">Transform</span><span class="sxs-lookup"><span data-stu-id="82ca7-183">Transform</span></span> | <span data-ttu-id="82ca7-184">定義</span><span class="sxs-lookup"><span data-stu-id="82ca7-184">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.Transforms.RowRangeFilter> | <span data-ttu-id="82ca7-185">在類型為 Single、Double 或 Key (連續) 的資料行上篩選 dataview。</span><span class="sxs-lookup"><span data-stu-id="82ca7-185">Filters a dataview on a column of type Single, Double or Key (contiguous).</span></span> <span data-ttu-id="82ca7-186">保留位於指定最小值/最大值範圍中的值。</span><span class="sxs-lookup"><span data-stu-id="82ca7-186">Keeps the values that are in the specified min/max range.</span></span> <span data-ttu-id="82ca7-187">一律會篩選掉 NaN。若輸入為 Key 類型，則最小值/最大值會視為百分比，代表該百分比包含的值數。</span><span class="sxs-lookup"><span data-stu-id="82ca7-187">NaNs are always filtered out. If the input is a Key type, the min/max are considered percentages of the number of values.</span></span> |
| <xref:Microsoft.ML.Transforms.RowSkipAndTakeFilter> | <span data-ttu-id="82ca7-188">允許限制在選擇性位移的資料列子集進行輸入。</span><span class="sxs-lookup"><span data-stu-id="82ca7-188">Allows limiting input to a subset of rows at an optional offset.</span></span> <span data-ttu-id="82ca7-189">可用來實作資料分頁。</span><span class="sxs-lookup"><span data-stu-id="82ca7-189">Can be used to implement data paging.</span></span> |
| <xref:Microsoft.ML.Transforms.RowSkipFilter> | <span data-ttu-id="82ca7-190">允許利用跳過資料列數，來限制輸入資料列子集。</span><span class="sxs-lookup"><span data-stu-id="82ca7-190">Allows limiting input to a subset of rows by skipping a number of rows.</span></span> |
| <xref:Microsoft.ML.Transforms.RowTakeFilter> | <span data-ttu-id="82ca7-191">允許利用跳過資料列數，來限制輸入資料列子集。</span><span class="sxs-lookup"><span data-stu-id="82ca7-191">Allows limiting input to a subset of rows by taking N first rows.</span></span> |

## <a name="schema"></a><span data-ttu-id="82ca7-192">結構描述</span><span class="sxs-lookup"><span data-stu-id="82ca7-192">Schema</span></span>

| <span data-ttu-id="82ca7-193">Transform</span><span class="sxs-lookup"><span data-stu-id="82ca7-193">Transform</span></span> | <span data-ttu-id="82ca7-194">定義</span><span class="sxs-lookup"><span data-stu-id="82ca7-194">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.Transforms.ColumnConcatenator> | <span data-ttu-id="82ca7-195">串連兩個相同項目類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="82ca7-195">Concatenates two columns of the same item type.</span></span> |
| <xref:Microsoft.ML.Transforms.ColumnCopier> | <span data-ttu-id="82ca7-196">從資料集複製資料行。</span><span class="sxs-lookup"><span data-stu-id="82ca7-196">Duplicates columns from the dataset.</span></span>|
| <xref:Microsoft.ML.Transforms.ColumnDropper> | <span data-ttu-id="82ca7-197">從資料集卸除資料行。</span><span class="sxs-lookup"><span data-stu-id="82ca7-197">Drops columns from the dataset.</span></span> |
| <xref:Microsoft.ML.Transforms.ColumnSelector> | <span data-ttu-id="82ca7-198">選取一組資料行，卸除其他項目。</span><span class="sxs-lookup"><span data-stu-id="82ca7-198">Selects a set of columns, dropping all others.</span></span> |
| <xref:Microsoft.ML.Transforms.ColumnTypeConverter> | <span data-ttu-id="82ca7-199">使用標準轉換，將資料行轉換為不同類型。</span><span class="sxs-lookup"><span data-stu-id="82ca7-199">Converts a column to a different type, using standard conversions.</span></span> |
| <xref:Microsoft.ML.Transforms.KeyToTextConverter> | <span data-ttu-id="82ca7-200">KeyToValueTransform 會利用 KeyValues 中繼資料，將索引鍵索引對應至 KeyValues 中繼資料中的對應值。</span><span class="sxs-lookup"><span data-stu-id="82ca7-200">KeyToValueTransform utilizes KeyValues metadata to map key indices to the corresponding values in the KeyValues metadata.</span></span> |
| <xref:Microsoft.ML.Transforms.NGramTranslator> | <span data-ttu-id="82ca7-201">在指定的索引鍵向量中產生一袋 ngrams 計數 (長度為 1-n 的連續值序列)。</span><span class="sxs-lookup"><span data-stu-id="82ca7-201">Produces a bag of counts of ngrams (sequences of consecutive values of length 1-n) in a given vector of keys.</span></span> <span data-ttu-id="82ca7-202">它會透過建置 ngrams 字典，並在袋中使用字典內的識別碼作為索引，來進行此動作。</span><span class="sxs-lookup"><span data-stu-id="82ca7-202">It does so by building a dictionary of ngrams and using the id in the dictionary as the index in the bag.</span></span> | 
| <xref:Microsoft.ML.Transforms.OptionalColumnCreator> | <span data-ttu-id="82ca7-203">若來源資料行在還原序列化之後不存在，則使用正確的類型和預設值來建立資料行。</span><span class="sxs-lookup"><span data-stu-id="82ca7-203">If the source column does not exist after deserialization, create a column with the right type and default values.</span></span> |

## <a name="text-processing-and-featurization"></a><span data-ttu-id="82ca7-204">文字處理與特徵化</span><span class="sxs-lookup"><span data-stu-id="82ca7-204">Text processing and featurization</span></span>

| <span data-ttu-id="82ca7-205">Transform</span><span class="sxs-lookup"><span data-stu-id="82ca7-205">Transform</span></span> | <span data-ttu-id="82ca7-206">定義</span><span class="sxs-lookup"><span data-stu-id="82ca7-206">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.Transforms.CharacterTokenizer> | <span data-ttu-id="82ca7-207">字元導向的權杖化工具，文字在其中會視為字元序列。</span><span class="sxs-lookup"><span data-stu-id="82ca7-207">Character-oriented tokenizer where text is considered a sequence of characters.</span></span> |
| <xref:Microsoft.ML.Transforms.TextFeaturizer> | <span data-ttu-id="82ca7-208">將文字文件集合轉換成數值特徵向量的轉換。</span><span class="sxs-lookup"><span data-stu-id="82ca7-208">A transform that turns a collection of text documents into numerical feature vectors.</span></span> <span data-ttu-id="82ca7-209">特徵向量為指定權杖化文字中 (字和/或字元) ngrams 的正規化計數。</span><span class="sxs-lookup"><span data-stu-id="82ca7-209">The feature vectors are normalized counts of (word and/or character) ngrams in a given tokenized text.</span></span> |
| <xref:Microsoft.ML.Transforms.TextToKeyConverter> | <span data-ttu-id="82ca7-210">將輸入值 (文字、數字等) 轉換成字典中的索引。</span><span class="sxs-lookup"><span data-stu-id="82ca7-210">Converts input values (words, numbers, etc.) to index in a dictionary.</span></span> |
| <xref:Microsoft.ML.Transforms.WordEmbeddings> | <span data-ttu-id="82ca7-211">使用預先訓練模型，將文字權杖的向量轉換成數值向量的轉換。</span><span class="sxs-lookup"><span data-stu-id="82ca7-211">A transform that converts vectors of text tokens into numeric vectors using a pre-trained model.</span></span> <span data-ttu-id="82ca7-212">如需此技術的詳細資訊，請參閱 [Word embedding](https://en.wikipedia.org/wiki/Word_embedding) (文字內嵌) 維基百科頁面。</span><span class="sxs-lookup"><span data-stu-id="82ca7-212">For more information about the technique, see the [Word embedding](https://en.wikipedia.org/wiki/Word_embedding) Wikipedia page.</span></span> |
| <xref:Microsoft.ML.Transforms.WordTokenizer> | <span data-ttu-id="82ca7-213">此轉換的輸入為文字，輸出則為包含原始文字中單字 (權杖) 的文字向量。</span><span class="sxs-lookup"><span data-stu-id="82ca7-213">The input to this transform is text, and the output is a vector of text containing the words (tokens) in the original text.</span></span> <span data-ttu-id="82ca7-214">分隔符號為空格鍵，但可指定任何其他字元 (或多個字元)。</span><span class="sxs-lookup"><span data-stu-id="82ca7-214">The separator is space, but any other character (or multiple characters) can be specified.</span></span> |

## <a name="miscellaneous"></a><span data-ttu-id="82ca7-215">其他</span><span class="sxs-lookup"><span data-stu-id="82ca7-215">Miscellaneous</span></span>

| <span data-ttu-id="82ca7-216">Transform</span><span class="sxs-lookup"><span data-stu-id="82ca7-216">Transform</span></span> | <span data-ttu-id="82ca7-217">定義</span><span class="sxs-lookup"><span data-stu-id="82ca7-217">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.Transforms.ApproximateBootstrapSampler> | <span data-ttu-id="82ca7-218">近似啟動程序取樣。</span><span class="sxs-lookup"><span data-stu-id="82ca7-218">Approximate bootstrap sampling.</span></span> |
| <xref:Microsoft.ML.Transforms.BinaryPredictionScoreColumnsRenamer> | <span data-ttu-id="82ca7-219">針對二進位預測，重新命名 PredictedLabel 和 Score 資料行，以包含正類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="82ca7-219">For binary prediction, renames the PredictedLabel and Score columns to include the name of the positive class.</span></span>|
| <xref:Microsoft.ML.Transforms.DataCache> | <span data-ttu-id="82ca7-220">使用指定快取選項進行快取。</span><span class="sxs-lookup"><span data-stu-id="82ca7-220">Caches using the specified cache option.</span></span> |
| <xref:Microsoft.ML.Transforms.DatasetScorer> | <span data-ttu-id="82ca7-221">使用預測模型計分資料集。</span><span class="sxs-lookup"><span data-stu-id="82ca7-221">Scores a dataset with a predictor model.</span></span> |
| <xref:Microsoft.ML.Transforms.DatasetTransformScorer> | <span data-ttu-id="82ca7-222">使用轉換模型計分資料集。</span><span class="sxs-lookup"><span data-stu-id="82ca7-222">Scores a dataset with a transform model.</span></span> |
| <xref:Microsoft.ML.Transforms.NoOperation> | <span data-ttu-id="82ca7-223">不執行任何動作</span><span class="sxs-lookup"><span data-stu-id="82ca7-223">Does nothing.</span></span> |
| <xref:Microsoft.ML.Transforms.RandomNumberGenerator> | <span data-ttu-id="82ca7-224">使用產生的數字序列新增資料行。</span><span class="sxs-lookup"><span data-stu-id="82ca7-224">Adds a column with a generated number sequence.</span></span> |
| <xref:Microsoft.ML.Transforms.ScoreColumnSelector> | <span data-ttu-id="82ca7-225">僅選取最後的計分資料行和在引數中指定的額外資料行。</span><span class="sxs-lookup"><span data-stu-id="82ca7-225">Selects only the last score columns and the extra columns specified in the arguments.</span></span> |
| <xref:Microsoft.ML.Transforms.Scorer> | <span data-ttu-id="82ca7-226">將預測模型轉換成轉換模型。</span><span class="sxs-lookup"><span data-stu-id="82ca7-226">Turns the predictor model into a transform model.</span></span> |
| <xref:Microsoft.ML.Transforms.SentimentAnalyzer> | <span data-ttu-id="82ca7-227">使用預先訓練的情感模型來為輸入字串計分。</span><span class="sxs-lookup"><span data-stu-id="82ca7-227">Uses a pretrained sentiment model to score input strings.</span></span> |
| <xref:Microsoft.ML.Transforms.TrainTestDatasetSplitter> | <span data-ttu-id="82ca7-228">將資料集分割為訓練及測試集。</span><span class="sxs-lookup"><span data-stu-id="82ca7-228">Splits the dataset into train and test sets.</span></span> |
