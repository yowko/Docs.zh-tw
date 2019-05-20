---
title: 資料轉換
description: 探索 ML.NET 中支援的特徵工程元件。
author: natke
ms.author: nakersha
ms.date: 04/02/2019
ms.openlocfilehash: 7ea06e19b4651017079a6ae57136f033e0ce981c
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2019
ms.locfileid: "65558019"
---
# <a name="data-transformations"></a>資料轉換

資料轉換是用來針對模型定型準備資料。 本指南中的轉換會傳回能實作 [IEstimator](xref:Microsoft.ML.IEstimator%601) 介面的類別。 資料轉換可以鏈結在一起。 每個轉換都會預期和產生特定類型及格式的資料，其已詳述於連結的參考文件中。

某些資料轉換需要定型資料以計算其參數。 例如：<xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> 轉換器會在 `Fit()` 作業期間計算定型資料的平均數和變異數，並將那些參數用於 `Transform()` 作業。 

其他資料轉換並不需要定型資料。 例如：<xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale*> 轉換可以在無須於 `Fit()` 作業期間查看任何定型資料的情況下執行 `Transform()` 作業。

## <a name="column-mapping-and-grouping"></a>資料行對應及群組

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A> | 將一或多個輸入資料行串連成新的輸出資料行 |
| <xref:Microsoft.ML.TransformExtensionsCatalog.CopyColumns%2A> | 複製並重新命名一或多個輸入資料行 |
| <xref:Microsoft.ML.TransformExtensionsCatalog.DropColumns%2A> | 卸除一或多個輸入資料行 |
| <xref:Microsoft.ML.TransformExtensionsCatalog.SelectColumns%2A> | 選取一或多個資料行以將其自輸入資料中排除 |

## <a name="normalization-and-scaling"></a>標準化和調整

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> | 減去 (定型資料的) 平均數並除以 (定型資料的) 變異數 |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLogMeanVariance%2A> | 依定型資料的對數進行標準化 |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLpNorm%2A> | 依據輸入向量的 [lp-norm](https://en.wikipedia.org/wiki/Lp_space#The_p-norm_in_finite_dimensions) 來對它進行調整，其中 p 為 1、2 或無限。 預設為 l2 (歐幾里得距離) 範數 |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeGlobalContrast%2A> | 透過減去資料列資料的平均數並除以標準差或 (資料列資料的) l2 範數，並乘以可設定的比例因素 (預設為 2)，來調整資料列中的每個值 |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A> | 將輸入值指派至 bin 目錄並除以 bin 的數目，以產生介於 0 與 1 的浮點值。 系統會以能將定型資料平均分散到所有 bin 上的方式計算 bin 界線 |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeSupervisedBinning%2A> | 根據 bin 與標籤資料行的關聯性將輸入值指派至該 bin |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A> | 依定型資料中最小及最大值之間的差異來調整輸入 |

## <a name="conversions-between-data-types"></a>資料類型之間的轉換

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.ConvertType%2A> | 將某個輸入資料行的類型轉換成新的類型 |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValue*> | 根據所提供的對應字典將值對應至索引鍵 (類別) |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*> | 透過從輸入資料建立對應來將值對應至索引鍵 (類別) |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue*> | 將索引鍵轉換為其原始值 |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToVector*> | 將索引鍵轉換為原始值的向量 |
| <xref:Microsoft.ML.ConversionsCatalog.MapKeyToBinaryVector*> | 將索引鍵轉換為原始值的二進位向量 |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash*> | 對輸入資料行中的值進行雜湊處理 |

## <a name="text-transformations"></a>文字轉換

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.TextCatalog.FeaturizeText*> | 將文字資料行轉換為標準化 ngram 和 char-gram 計數的浮動陣列 | 
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoWords*> | 將一或多個文字資料行分割為個別字詞 |
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoCharactersAsKeys*> | 將一或多個文字資料行分割為於一組主題上的個別字元浮點數 |
| <xref:Microsoft.ML.TextCatalog.NormalizeText*> | 變更大小寫，移除變音符號、標點符號及數字 |
| <xref:Microsoft.ML.TextCatalog.ProduceNgrams*> | 將文字資料行轉換為一袋 ngram 計數 (連續字詞的序列)|
| <xref:Microsoft.ML.TextCatalog.ProduceWordBags*> | 將文字資料行轉換為一袋 ngram 向量計數 |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedNgrams*> | 將文字資料行轉換為雜湊 ngram 計數的向量 |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedWordBags*> | 將文字資料行轉換為一袋雜湊 ngram 計數 |
| <xref:Microsoft.ML.TextCatalog.RemoveDefaultStopWords*>  | 從輸入資料行針對指定語言移除預設停用字詞 |
| <xref:Microsoft.ML.TextCatalog.RemoveStopWords*> | 從輸入資料行移除指定停用字詞 |
| <xref:Microsoft.ML.TextCatalog.LatentDirichletAllocation*> | 將文件 (以浮點數向量表示) 轉換為一組主題上的浮點數向量 |
| <xref:Microsoft.ML.TextCatalog.ApplyWordEmbedding*> | 使用預先定型的模型將文字權杖的向量轉換成句子向量 |

## <a name="image-transformations"></a>影像轉換

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale*> | 將影像轉換為灰階 |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToImage*> | 將像素的向量轉換為 <xref:Microsoft.ML.Transforms.Image.ImageDataViewType> |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*> | 將來自輸入影像的像素轉換為數字向量 |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*> | 從資料夾將影像載入記憶體 |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*> | 調整影像大小 |

## <a name="categorical-data-transformations"></a>類別資料轉換

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*> | 將一或多個文字資料行轉換為 [one-hot](https://en.wikipedia.org/wiki/One-hot) \(英文\) 編碼向量 |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotHashEncoding*> | 將一或多個文字資料行轉換為以雜湊為基礎的 one-hot 編碼向量 |

## <a name="missing-values"></a>遺失值

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.ExtensionsCatalog.IndicateMissingValues*> | 建立新的布林值輸出資料行，其值在輸入資料行中的值遺失時為 true |
| <xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*> | 建立新的輸出資料行，其值在輸入資料行中的值遺失時會被設為預設值，否則則會為輸入值 |

## <a name="feature-selection"></a>特徵選取

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnCount*> | 選取其非預設值大於某個閾值的特徵 |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnMutualInformation*> | 選取其標籤資料行中的資料最具相依性的特徵 |

## <a name="custom-transformations"></a>自訂轉換

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.CustomMappingCatalog.CustomMapping*> | 搭配使用者定義的對應將現有資料行轉換為新的資料行 |
