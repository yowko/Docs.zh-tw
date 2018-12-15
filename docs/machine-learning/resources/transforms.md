---
title: ML.NET 中的資料轉換
description: 探索 ML.NET 中支援的不同資料轉換。
author: JRAlexander
ms.date: 10/16/2018
ms.openlocfilehash: c169319937dac13747935e451952bd75d4cc174d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143944"
---
# <a name="data-transforms-in-mlnet"></a>ML.NET 中的資料轉換

下列表格包含 ML.NET 支援的所有資料轉換相關資訊 (選取資料轉換類型以巡覽至對應的表格)：

* [類別目錄](#categorical)
* [結合工具與分離工具](#combiners-and-segregators)
* [特徵選取](#feature-selection)
* [特徵化工具](#featurizers)
* [標籤剖析](#label-parsing)
* [遺失值](#missing-values)
* [正規化](#normalization)
* [資料列篩選](#row-filters)
* [結構描述](#schema)
* [文字處理與特徵化](#text-processing-and-featurization)
* [其他](#miscellaneous)

> [!NOTE]
> ML.NET 目前為預覽版。 目前並不支援所有資料轉換。 若要提出特定轉換的要求，請在 [dotnet/machinelearning](https://github.com/dotnet/machinelearning/issues) GitHub 存放庫中提出問題。

## <a name="categorical"></a>類別目錄

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.CategoricalHashOneHotVectorizer> | 使用雜湊式編碼對類別目錄變數進行編碼。 |
| <xref:Microsoft.ML.Legacy.Transforms.CategoricalOneHotVectorizer> | 使用以字詞字典為基礎的 one-hot 編碼對類別目錄進行編碼。 |

## <a name="combiners-and-segregators"></a>結合工具與分離工具

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.CombinerByContiguousGroupId> | 將純量資料行的值組成以連續群組識別碼為基礎的向量。 |
| <xref:Microsoft.ML.Legacy.Transforms.FeatureCombiner> | 將所有功能合併為一個功能資料行。 |
| <xref:Microsoft.ML.Legacy.Transforms.ManyHeterogeneousModelCombiner> | 將 TransformModels 和 PredictorModel 的序列合併成單一 PredictorModel。 |
| <xref:Microsoft.ML.Legacy.Transforms.ModelCombiner> | 將 TransformModels 序列合併成單一模型。 |
| <xref:Microsoft.ML.Legacy.Transforms.Segregator> | 取消向量資料行的群組並分成資料列序列；Group 轉換的相反。 |
| <xref:Microsoft.ML.Legacy.Transforms.TwoHeterogeneousModelCombiner> | 將 TransformModels 和 PredictorModel 合併成單一 PredictorModel。 |

## <a name="feature-selection"></a>特徵選取

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.FeatureSelectorByCount> | 選取非預設值計數大於等於閾值的位置。 |
| <xref:Microsoft.ML.Legacy.Transforms.FeatureSelectorByMutualInformation> | 使用標籤資料行選取所有指定資料行的前 k 個位置，並根據其相互資訊進行排序。 |

## <a name="featurizers"></a>特徵化工具

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.HashConverter> | 將資料行值轉換成雜湊。 這項轉換接受數值及文字輸入，也接受單一及向量值資料行。 |
| <xref:Microsoft.ML.Legacy.Transforms.TreeLeafFeaturizer> | 訓練整體樹狀或從檔案載入，然後將數值特徵向量對應至三個輸出：1. 包含整體樹狀中個別樹狀輸出的向量。 2. 指出整體樹狀中特徵向量所在分葉的向量。 3. 指出整體樹狀中特徵向量所在路徑的向量。 若同時指定模型檔案及訓練員，則向量會使用模型檔案。 若兩者皆未指定，則向量會訓練預設 FastTree 模型。 這可透過訓練針對其選擇性排列索引的迴歸模型，來處理索引鍵標籤。 |

## <a name="label-parsing"></a>標籤剖析

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.Dictionarizer> | 將輸入值 (文字、數字等) 轉換成字典中的索引。 |
| <xref:Microsoft.ML.Legacy.Transforms.LabelColumnKeyBooleanConverter> | 將標籤轉換成索引鍵或布林值，使其適合用於分類。 |
| <xref:Microsoft.ML.Legacy.Transforms.LabelIndicator> | OVA 使用的標籤重新對應。 |
| <xref:Microsoft.ML.Legacy.Transforms.LabelToFloatConverter> | 將標籤轉換成浮點數，使其適合用於迴歸。 |
| <xref:Microsoft.ML.Legacy.Transforms.PredictedLabelColumnOriginalValueConverter> | 將預測的標籤資料行轉換為其原始值 (除非其類型為布林值)。 |

## <a name="missing-values"></a>遺失值

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.MissingValueHandler> | 透過使用預設值或平均值/最小值/最大值取代遺失值，來處理遺失值 (僅限非文字資料行)。 若輸入資料行類型為數值，則可選擇性串連指標資料行。 |
| <xref:Microsoft.ML.Legacy.Transforms.MissingValueIndicator> | 使用相同數量的位置作為輸入資料行建立布林值輸出資料行，並在遺失輸入資料行中的值時，將輸出值設為 true。 |
| <xref:Microsoft.ML.Legacy.Transforms.MissingValuesDropper> | 從向量資料行移除所有 NA。 |
| <xref:Microsoft.ML.Legacy.Transforms.MissingValuesRowDropper> | 篩選出包含遺失值的資料列。 |
| <xref:Microsoft.ML.Legacy.Transforms.MissingValueSubstitutor> | 建立類型相同且輸入資料行大小也相同的輸出資料行，並在其中使用預設值或平均值/最小值/最大值取代遺失值 (僅限非文字資料行)。 |

## <a name="normalization"></a>正規化

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.BinNormalizer> | 值會指派給密度相等的 bin，並且單一值會對應到其 bin_number / number_of_bins。 |
| <xref:Microsoft.ML.Legacy.Transforms.ConditionalNormalizer> | 請只在需要的時候進行正規化。 |
| <xref:Microsoft.ML.Legacy.Transforms.GlobalContrastNormalizer> | 在輸入值上執行全域對比正規化：Y = (s * X - M) / D，其中 s 為比例、M 為平均數，D 則為 L2 範數或標準差。 | 
| <xref:Microsoft.ML.Legacy.Transforms.LogMeanVarianceNormalizer> | 根據計算的平均數和資料對數的變異數，對資料進行正規化。 |
| <xref:Microsoft.ML.Legacy.Transforms.LpNormalizer> | 透過將其調整為單位範數 (L2、L1 或 LInf) 來正規化個別向量 (資料列)。 在向量上執行下列運算 X: Y = (X - M) / D，其中 M 為平均數，D 為 L2 範數、L1 範數或 LInf 範數。 |
| <xref:Microsoft.ML.Legacy.Transforms.MeanVarianceNormalizer> | 根據計算的平均數和資料的變異數，對資料進行正規化。 |
| <xref:Microsoft.ML.Legacy.Transforms.MinMaxNormalizer> | 根據觀察到的資料最小值和最大值，對資料進行正規化。 |

## <a name="row-filters"></a>資料列篩選

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.RowRangeFilter> | 在類型為 Single、Double 或 Key (連續) 的資料行上篩選 dataview。 保留位於指定最小值/最大值範圍中的值。 一律會篩選掉 NaN。若輸入為 Key 類型，則最小值/最大值會視為百分比，代表該百分比包含的值數。 |
| <xref:Microsoft.ML.Legacy.Transforms.RowSkipAndTakeFilter> | 允許限制在選擇性位移的資料列子集進行輸入。 可用來實作資料分頁。 |
| <xref:Microsoft.ML.Legacy.Transforms.RowSkipFilter> | 允許利用跳過資料列數，來限制輸入資料列子集。 |
| <xref:Microsoft.ML.Legacy.Transforms.RowTakeFilter> | 允許利用跳過資料列數，來限制輸入資料列子集。 |

## <a name="schema"></a>結構描述

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.ColumnConcatenator> | 串連兩個相同項目類型的資料行。 |
| <xref:Microsoft.ML.Legacy.Transforms.ColumnCopier> | 從資料集複製資料行。|
| <xref:Microsoft.ML.Legacy.Transforms.ColumnDropper> | 從資料集卸除資料行。 |
| <xref:Microsoft.ML.Legacy.Transforms.ColumnSelector> | 選取一組資料行，卸除其他項目。 |
| <xref:Microsoft.ML.Legacy.Transforms.ColumnTypeConverter> | 使用標準轉換，將資料行轉換為不同類型。 |
| <xref:Microsoft.ML.Legacy.Transforms.KeyToTextConverter> | KeyToValueTransform 會利用 KeyValues 中繼資料，將索引鍵索引對應至 KeyValues 中繼資料中的對應值。 |
| <xref:Microsoft.ML.Legacy.Transforms.NGramTranslator> | 在指定的索引鍵向量中產生一袋 ngrams 計數 (長度為 1-n 的連續值序列)。 它會透過建置 ngrams 字典，並在袋中使用字典內的識別碼作為索引，來進行此動作。 | 
| <xref:Microsoft.ML.Legacy.Transforms.OptionalColumnCreator> | 若來源資料行在還原序列化之後不存在，則使用正確的類型和預設值來建立資料行。 |

## <a name="text-processing-and-featurization"></a>文字處理與特徵化

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.CharacterTokenizer> | 字元導向的權杖化工具，文字在其中會視為字元序列。 |
| <xref:Microsoft.ML.Legacy.Transforms.TextFeaturizer> | 將文字文件集合轉換成數值特徵向量的轉換。 特徵向量為指定權杖化文字中 (字和/或字元) ngrams 的正規化計數。 |
| <xref:Microsoft.ML.Legacy.Transforms.TextToKeyConverter> | 將輸入值 (文字、數字等) 轉換成字典中的索引。 |
| <xref:Microsoft.ML.Legacy.Transforms.WordEmbeddings> | 使用預先訓練模型，將文字權杖的向量轉換成數值向量的轉換。 如需此技術的詳細資訊，請參閱 [Word embedding](https://en.wikipedia.org/wiki/Word_embedding) (文字內嵌) 維基百科頁面。 |
| <xref:Microsoft.ML.Legacy.Transforms.WordTokenizer> | 此轉換的輸入為文字，輸出則為包含原始文字中單字 (權杖) 的文字向量。 分隔符號為空格鍵，但可指定任何其他字元 (或多個字元)。 |

## <a name="miscellaneous"></a>其他

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.ApproximateBootstrapSampler> | 近似啟動程序取樣。 |
| <xref:Microsoft.ML.Legacy.Transforms.BinaryPredictionScoreColumnsRenamer> | 針對二進位預測，重新命名 PredictedLabel 和 Score 資料行，以包含正類別的名稱。|
| <xref:Microsoft.ML.Legacy.Transforms.DataCache> | 使用指定快取選項進行快取。 |
| <xref:Microsoft.ML.Legacy.Transforms.DatasetScorer> | 使用預測模型計分資料集。 |
| <xref:Microsoft.ML.Legacy.Transforms.DatasetTransformScorer> | 使用轉換模型計分資料集。 |
| <xref:Microsoft.ML.Legacy.Transforms.NoOperation> | 不執行任何動作 |
| <xref:Microsoft.ML.Legacy.Transforms.RandomNumberGenerator> | 使用產生的數字序列新增資料行。 |
| <xref:Microsoft.ML.Legacy.Transforms.ScoreColumnSelector> | 僅選取最後的計分資料行和在引數中指定的額外資料行。 |
| <xref:Microsoft.ML.Legacy.Transforms.Scorer> | 將預測模型轉換成轉換模型。 |
| <xref:Microsoft.ML.Legacy.Transforms.SentimentAnalyzer> | 使用預先訓練的情感模型來為輸入字串計分。 |
| <xref:Microsoft.ML.Legacy.Transforms.TrainTestDatasetSplitter> | 將資料集分割為訓練及測試集。 |
