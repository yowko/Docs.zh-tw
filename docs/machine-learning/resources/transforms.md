---
title: 機器學習資料轉換 - ML.NET
description: 探索 ML.NET 中支援的特徵工程元件。
author: JRAlexander
ms.custom: seodec18
ms.date: 01/14/2019
ms.openlocfilehash: e649c9a27f0409cb9cdfb554963b5c0e732991f2
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355401"
---
# <a name="machine-learning-data-transforms---mlnet"></a>機器學習資料轉換 - ML.NET

下表包含 ML.NET 中支援的所有資料轉換相關資訊。

> [!NOTE]
> ML.NET 目前為預覽版。 目前並不支援所有資料轉換。 若要提出特定轉換的要求，請在 [dotnet/machinelearning](https://github.com/dotnet/machinelearning/issues) GitHub 存放庫中提出問題。

## <a name="combiners-and-segregators"></a>結合工具與分離工具

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Transforms.GroupTransform> | 將純量資料行的值組成以連續群組識別碼為基礎的向量。 |
| <xref:Microsoft.ML.Transforms.UngroupTransform> | 取消向量資料行的群組並分成資料列序列；Group 轉換的相反。 |

## <a name="conversions"></a>轉換

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Transforms.Conversions.HashingTransformer> | 雜湊處理單一值資料行或向量資料行。 針對向量資料行，它會個別雜湊處理每個位置。 它可以雜湊處理文字值或索引鍵值。 |
| <xref:Microsoft.ML.Transforms.Conversions.HashJoiningTransform> | 將多個資料行值轉換成雜湊。 此轉換接受數值及文字輸入，也接受單一及向量值資料行。 |
| <xref:Microsoft.ML.Transforms.Conversions.KeyToBinaryVectorMappingTransformer> | 將索引鍵轉換成二進位向量資料行。 |
| <xref:Microsoft.ML.Transforms.Conversions.KeyToValueMappingTransformer > | 利用 KeyValues 中繼資料，將索引鍵索引對應至 KeyValues 中繼資料中的對應值。 |
| <xref:Microsoft.ML.Transforms.Conversions.KeyToVectorMappingTransformer> | 將索引鍵轉換成向量資料行。 |
| <xref:Microsoft.ML.Transforms.Conversions.TypeConvertingTransformer> | 變更基礎資料行類型 (前提是該類型可以轉換)。 |
| <xref:Microsoft.ML.Transforms.Conversions.ValueToKeyMappingTransformer> | 將輸入值 (文字、數字等) 轉換成字典中的索引。 |

## <a name="deep-learning"></a>深度學習

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Transforms.OnnxTransform> | 提供資料給現有的 ONNX 模型並傳回分數 (預測)。 |
| <xref:Microsoft.ML.Transforms.TensorFlowTransform> | 可使用預先定型的 TensorFlow 模型計分或重新定型 TensorFlow 模型。 |

## <a name="feature-extraction"></a>特徵擷取

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Transforms.Text.CustomStopWordsRemovingTransform> | 透過比較個別語彙基元 (不區分大小寫的比較) 與停用字詞，來移除指定的停用字詞清單。|
| <xref:Microsoft.ML.ImageAnalytics.ImageGrayscaleTransform> | 擷取一或多個 ImageType 資料行，並將其轉換成相同影像的灰階表示。|
| <xref:Microsoft.ML.ImageAnalytics.ImageLoaderTransform> | 擷取一或多個 ReadOnlyMemory 資料行，並以 ImageType 形式載入。 |
| <xref:Microsoft.ML.ImageAnalytics.ImagePixelExtractorTransform> | 擷取一或多個 ImageType 資料行，並將其轉換成向量表示。|
| <xref:Microsoft.ML.ImageAnalytics.ImageResizerTransform> | 擷取一或多個 ImageType 資料行，並將其大小調整為提供的高度和寬度。|
| <xref:Microsoft.ML.Transforms.Text.LatentDirichletAllocationTransformer> | 實作 LightLDA，這是隱含狄利克雷分布 (Latent Dirichlet Allocation) 的最新實作。|
| <xref:Microsoft.ML.Transforms.LoadTransform> | 從指定的模型檔載入特定轉換。 可讓您從序列化鏈結進行「揀選」轉換，或將預先定型的轉換套用至不同 (但仍相容) 的資料檢視。 |
| <xref:Microsoft.ML.Transforms.Text.NgramExtractingTransformer> | 在指定的索引鍵向量中產生一袋 ngrams 計數 (長度為 1-n 的連續值序列)。 它會透過建置 ngrams 字典，並在袋中使用字典內的識別碼作為索引，來進行此動作。 |
| <xref:Microsoft.ML.Transforms.Text.NgramExtractorTransform> | 將語彙基元化的文字集合 (ReadOnlyMemory 向量) 或索引鍵向量轉換成數值特徵向量。 特徵向量是 n 元語法計數 (長度為 1-n 的連續語彙基元 (字組或索引鍵) 序列)。 |
| <xref:Microsoft.ML.Transforms.Text.NgramHashExtractingTransformer> | 使用雜湊，將語彙基元化的文字集合 (ReadOnlyMemory 向量) 轉換成數值特徵向量。 |
| <xref:Microsoft.ML.Transforms.Text.NgramHashingTransformer> | 在指定的文字中產生一袋 n 元語法計數 (長度為 1-n 的連續字組序列)。 |
| <xref:Microsoft.ML.Transforms.Categorical.OneHotEncodingTransformer> | 透過建置以資料為依據的類別字典，並使用字典中的識別碼作為陣列中索引，來將類別值轉換成指標陣列 |
| <xref:Microsoft.ML.Transforms.Projections.PcaTransform> | 計算特徵向量在低順位子空間上的投影。 |
| <xref:Microsoft.ML.Transforms.Text.SentimentAnalyzingTransformer> | 使用預先訓練的情感模型來為輸入字串計分。 |
| <xref:Microsoft.ML.Transforms.Text.StopWordsRemovingTransformer> | 透過比較個別語彙基元 (不區分大小寫的比較) 與停用字詞，來移除特定語言的停用字詞清單 (最常見的字組)。 |
| <xref:Microsoft.ML.Transforms.Text.WordBagBuildingTransformer> | 在指定的文字中產生一袋 n 元語法計數 (連續字組序列)。 它會透過建置 ngrams 字典，並在袋中使用字典內的識別碼作為索引，來進行此動作。 |
| <xref:Microsoft.ML.Transforms.Text.WordHashBagProducingTransformer> | 在指定的文字中產生一袋 n 元語法計數 (長度為 1-n 的連續字組序列)。 它會透過雜湊處理每個 n 元語法，並使用雜湊值作為袋中的索引，來進行此動作。 |
| <xref:Microsoft.ML.Transforms.Text.WordTokenizingTransformer> | 使用分隔字元，將文字分隔為字組。 |


## <a name="image-model-featurizers"></a>影像模型特徵化工具

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Transforms.AlexNetExtension> | 這是搭配 <xref:Microsoft.ML.Transforms.DnnImageFeaturizerEstimator> 使用的延伸模組方法，以便使用預先定型的 [AlexNet](https://en.wikipedia.org/wiki/AlexNet) 模型。 包含此延伸模組的 NuGet 也一定會包含二進位模型檔。 |
| <xref:Microsoft.ML.Transforms.ResNet18Extension> | 這是搭配 <xref:Microsoft.ML.Transforms.DnnImageFeaturizerEstimator> 使用的延伸模組方法，以便使用預先定型的 ResNet18 模型。 包含此延伸模組的 NuGet 也一定會包含二進位模型檔。 |
| <xref:Microsoft.ML.Transforms.ResNet50Extension> | 這是搭配 <xref:Microsoft.ML.Transforms.DnnImageFeaturizerEstimator> 使用的延伸模組方法，以便使用預先定型的 ResNet50 模型。 包含此延伸模組的 NuGet 也一定會包含二進位模型檔。 |
| <xref:Microsoft.ML.Transforms.ResNet101Extension> | 這是搭配 <xref:Microsoft.ML.Transforms.DnnImageFeaturizerEstimator> 使用的延伸模組方法，以便使用預先定型的 ResNet101 模型。 包含此延伸模組的 NuGet 也一定會包含二進位模型檔。 |

## <a name="label-parsing"></a>標籤剖析

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Transforms.LabelConvertTransform> |  轉換標籤。 |
| <xref:Microsoft.ML.Transforms.LabelIndicatorTransform> | 將多元分類標籤重新對應至二進位 True、False 標籤，主要用於 OVA。|

## <a name="missing-values"></a>遺失值

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Transforms.MissingValueDroppingTransformer> | 捨棄資料行中的遺失值。 |
| <xref:Microsoft.ML.Transforms.MissingValueIndicatorTransform> | 使用相同數量的位置作為輸入資料行建立布林值輸出資料行，並在遺失輸入資料行中的值時，將輸出值設為 true。 |
| <xref:Microsoft.ML.Transforms.MissingValueReplacingTransformer> | 透過使用預設值或平均值/最小值/最大值取代遺失值，來處理遺失值 (僅限非文字資料行)。 |

## <a name="normalization"></a>正規化

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Transforms.Projections.LpNormalizingTransformer> | Lp-Norm (以向量/資料列方式) 正規化轉換。 |
| <xref:Microsoft.ML.Transforms.Normalizers.MeanVarDblAggregator> | 計算向量值資料行的平均數和變異數。 它會追蹤目前平均數和 M2 (平均數值差的總平方和)、NAN 數目和非零項目數目。 |
| <xref:Microsoft.ML.Transforms.Normalizers.MeanVarSngAggregator> | 計算向量值資料行的平均數和變異數。 它會追蹤目前平均數和 M2 (平均數值差的總平方和)、NAN 數目和非零項目數目。 |
| <xref:Microsoft.ML.Transforms.Normalizers.MinMaxDblAggregator> | 追蹤向量值資料行的最小值、最大值、非疏鬆值數目 (vCount) 和 ProcessValue() 呼叫數目 (trainCount)。 |
| <xref:Microsoft.ML.Transforms.Normalizers.NormalizeTransform> | 標準化特徵範圍。 |
| <xref:Microsoft.ML.Transforms.Normalizers.NormalizingTransformer> |標準化特徵範圍。 |

## <a name="onnx"></a>Onnx

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Transforms.OnnxTransform> | 為使用 ONNX 標準 v1.2 的預先定型 ONNX 模型計分 |

## <a name="preprocessing"></a>前置處理
| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Transforms.BootstrapSamplingTransformer> | 近似使用波氏取樣的自助取樣 (Bootstrap Sampling)。 |
| <xref:Microsoft.ML.Transforms.Projections.RandomFourierFeaturizingTransformer> | 產生隨機傅立葉特徵。 |
| <xref:Microsoft.ML.Transforms.Text.TokenizingByCharactersTransformer> | 字元導向的權杖化工具，文字在其中會視為字元序列。 |
| <xref:Microsoft.ML.Transforms.Projections.VectorWhiteningTransformer> | 簡化最佳化以協助找出權數。 |

## <a name="row-filters"></a>資料列篩選

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Transforms.RowShufflingTransformer> | 使用指定數目的資料列集區，輪換要執行的隨機化資料指標嘗試。  |
| <xref:Microsoft.ML.Transforms.SkipFilter> | 允許利用跳過資料列數，來限制輸入資料列子集。 |
| <xref:Microsoft.ML.Transforms.SkipTakeFilter> | 允許限制在選擇性位移的資料列子集進行輸入。 可用來實作資料分頁。 使用 SkipTakeFilter.SkipArguments 建立時，其行為會如同 `SkipFilter`。
| <xref:Microsoft.ML.Transforms.TakeFilter> | 允許利用跳過資料列數，來限制輸入資料列子集。 |


## <a name="schema"></a>結構描述

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Transforms.ColumnCopyingTransformer> | 從資料集複製資料行。|
| <xref:Microsoft.ML.Transforms.ColumnSelectingTransformer> | 從所指定輸入中選取要捨棄或保留的一組資料行。 |
| <xref:Microsoft.ML.Transforms.FeatureSelection.SlotsDroppingTransformer> | 捨棄資料行中的位置。|
| <xref:Microsoft.ML.Transforms.OptionalColumnTransform> | 使用指定的類型和預設值建立新資料行。 |
| <xref:Microsoft.ML.Transforms.RangeFilter> | 在類型為 Single、Double 或 Key (連續) 的資料行上篩選 dataview。 保留位於指定最小值/最大值範圍中的值。 一律會篩選掉 NaN。若輸入為 Key 類型，則最小值/最大值會視為百分比，代表該百分比包含的值數。 |

## <a name="tensorflow"></a>Tensorflow

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Transforms.TensorFlowTransform> | 使用預先定型的 TensorFlow 模型計分或重新定型 TensorFlow 模型。 |

## <a name="text-processing-and-featurization"></a>文字處理與特徵化

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Transforms.Text.TextNormalizingTransformer> | 文字正規化轉換，可將文字大小寫正規化，以及移除變音符號、標點符號及/或數字。 可對文字輸入及語彙基元/文字向量 (ReadOnlyMemory 向量) 進行此轉換。 |
| <xref:Microsoft.ML.Transforms.Text.TokenizingByCharactersTransformer> | 字元導向的權杖化工具，文字在其中會視為字元序列。 |

## <a name="time-series"></a>時間序列

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.TimeSeriesProcessing.ExponentialAverageTransform> | 取得所有值的加權平均：ExpAvg(y_t) = a * y_t + (1-a) * ExpAvg(y_(t-1))。 |
| <xref:Microsoft.ML.TimeSeriesProcessing.IidChangePointDetector> | 根據自適性核心密度估計和隨機過程， 實作 i.i.d. 序列 (隨機樣本) 的變點檢測器轉換。 |
| <xref:Microsoft.ML.TimeSeriesProcessing.IidSpikeDetector> | 根據自適性核心密度估計， 實作 i.i.d. 序列 (隨機樣本) 的峰點檢測器轉換。 |
| <xref:Microsoft.ML.TimeSeriesProcessing.MovingAverageTransform> | 提供滑動視窗值的加權平均。 |
| <xref:Microsoft.ML.TimeSeriesProcessing.PercentileThresholdTransform> | 決定時間序列現值是否屬於滑動視窗臨界數值百分位數。 |
| <xref:Microsoft.ML.TimeSeriesProcessing.PValueTransform> | 根據滑動視窗中的其他值，計算序列現值的經驗 p 值。 |
| <xref:Microsoft.ML.TimeSeriesProcessing.SlidingWindowTransform> | 輸出 Single 類型時間序列上的滑動視窗。 |
| <xref:Microsoft.ML.TimeSeriesProcessing.SsaChangePointDetector> | 根據時間序列的奇異譜 (Singular Spectrum) 模型，實作變點檢測器轉換。 |
| <xref:Microsoft.ML.TimeSeriesProcessing.SsaSpikeDetector> | 根據時間序列的奇異譜 (Singular Spectrum) 模型，實作峰值檢測器轉換。 |

## <a name="miscellaneous"></a>其他

| 資料轉換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Transforms.CompositeTransformer> | 建立複合資料轉換。 |
| <xref:Microsoft.ML.Transforms.CustomMappingTransformer%602> | 為提供的 `IDataView` 產生額外資料行。 它不會變更資料列數目，可視為將使用者的函式應用至每一列輸入資料的結果。|
| <xref:Microsoft.ML.Transforms.GenerateNumberTransform> | 使用產生的數字序列新增資料行。 |
| <xref:Microsoft.ML.Transforms.ProduceIdTransform> | 產生以資料指標識別碼作為資料行的資料行。 |
| <xref:Microsoft.ML.Transforms.RandomNumberGenerator> | 產生亂數。 |
