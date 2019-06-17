---
title: 如何選擇 ML.NET 演算法
description: 了解如何選擇機器學習模型的 ML.NET 演算法
author: natke
ms.topic: overview
ms.date: 04/20/1029
ms.openlocfilehash: 89c3c612d79f02d58a16070feadb645b081dd3e3
ms.sourcegitcommit: 90f0bee0e8a416e45c78fa3ad4c91ef00e5228d5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2019
ms.locfileid: "66722629"
---
# <a name="how-to-choose-an-mlnet-algorithm"></a>如何選擇 ML.NET 演算法

針對每項 [ML.NET 工作](resources/tasks.md)，有多個定型演算法可供選擇。 要選擇哪一個，取決於您嘗試解決的問題、您資料的特性，以及您目前可使用的計算和儲存資源。 請務必注意，定型的機器學習模型是一種反覆運算程序。 您可能需要嘗試多種演算法，找出最適合的那一種。

演算法作用於**特性**。 特性是計算輸入資料所得出的數值。 它們是機器學習演算法的最佳輸入。 您使用一或多種[資料轉換](resources/transforms.md)，將未經處理的輸入資料轉換成特性。 例如，文字資料會轉換成一組字數統計和字詞組合統計。 一旦使用資料轉換從未經處理的資料類型擷取特性，它們就稱為**凸顯**。 例如，凸顯的文字或影像資料。

## <a name="trainer--algorithm--task"></a>定型器 = 演算法 + 工作

演算法是為產生**模型**所執行的數學。 不同演算法產生不同特性的模型。 

使用 ML.NET，相同演算法可以套用到不同的工作。 例如，隨機對偶座標上升法可用於二元分類、多元分類和迴歸。 不同之處在於如何解譯演算法的輸出，使符合工作。 

針對每種演算法/工作組合，ML.NET 提供執行定型演算法和完成解譯的元件。 這些元件稱為「定型器」。 例如，<xref:Microsoft.ML.Trainers.SdcaRegressionTrainer> 使用 **StochasticDualCoordinatedAscent** 演算法套用至**迴歸**工作。

## <a name="linear-algorithms"></a>線性演算法

線性演算法產生的模型會計算輸入資料和一組**權數**之線性組合的**分數**。 權數是在定型期間評估的模型參數。

線性演算法適用於[線性可分](https://en.wikipedia.org/wiki/Linear_separability)的特性。

使用線性演算法定型之前，應先將特性標準化。 這可防止某項特色對結果的影響超過其他特色。

一般而言，線性演算法可調整又快速，定型和預測的成本低廉。 它們可以調整特色數目，約為定型資料集的大小。

線性演算法對定型資料進行多次傳遞。 如果您的資料集貼合記憶體，則先將[快取檢查點](xref:Microsoft.ML.LearningPipelineExtensions.AppendCacheCheckpoint*)新增至 ML.NET 管線，再附加定型器，會讓定型執行更快速。

**線性定型器**

|演算法|屬性|定型器|
|---------|----------|--------|
|平均感知器|最適合文字分類|<xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>|
|隨機對偶座標上升法|好的預設效能不需要微調|<xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer> <xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer> <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer> <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer> <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>|
|L-BFGS|當特性數目很大時使用。 產生羅吉斯迴歸定型統計資料，但不像 AveragedPerceptronTrainer 縮放自如|<xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer> <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer> <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>|
|符號隨機梯度下降|最快速且最精確的線性二元分類定型器。 可隨處理器數目調整|<xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>|

## <a name="decision-tree-algorithms"></a>決策樹演算法

決策樹演算法建立的模型，包含一系列的決策：所有資料值的有效流程圖。

特性不需要為線性可分，也可以使用這種演算法。 而且特性不需要標準化，因為在決策流程中會單獨使用特性向量的個別值。

決策樹演算法通常非常精確。

除了一般化累加模型 (GAM) 外，樹狀模型在特性數目很大時會欠缺解釋性。

決策樹演算法需要更多資源，且不像線性演算法縮放自如。 它們也很適合貼近記憶體的資料集。

促進式決策樹是一整團的小型樹狀結構，其中每個樹狀結構都會評分輸入資料，並將分數傳遞到下一個樹狀結構，以產生更好的分數，整體中的每個樹狀結構都可以改善前一個樹狀結構。

**決策樹定型器**

|演算法|屬性|定型器|
|---------|----------|--------|
|輕量型梯度提升機器|最快速且最精確的二元分類樹狀定型器。 微調程度高|<xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>|
|快速的樹狀結構|用於特徵化影像資料。 復原不對稱的資料。 微調程度高 | <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>|
|快速樹系|適用於有很多雜訊的資料|<xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>|
|一般化累加模型 (GAM)|最適合處理適用樹狀演算法，但解釋性優先的問題|<xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>|

## <a name="matrix-factorization"></a>矩陣分解

|屬性|定型器|
|----------|--------|
|最適合大型資料集的分類疏鬆資料|<xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer>|

## <a name="meta-algorithms"></a>中繼演算法

這些定型器從二元定型器建立多元定型器。 搭配使用 <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer><xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>、<xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>、<xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer><xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer><xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>、<xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>。

|演算法|屬性|定型器|
|---------|----------|--------|
|一對多|此多元分類器每類別定型一個二元分類器，從所有其他類別中區分出該類別。 規模受限於要分類的類別數目|[OneVersusAllTrainer\<BinaryClassificationTrainer>](xref:Microsoft.ML.Trainers.OneVersusAllTrainer) |
|成對結合|此多元分類器針對每對類別定型二元分類演算法。 規模受限於類別數目，因為必須定型每對類別的組合。|[PairwiseCouplingTrainer\<BinaryClassificationTrainer>](xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer)|

## <a name="k-means"></a>K-Means

|屬性|定型器|
|----------|--------|
|用於叢集|<xref:Microsoft.ML.Trainers.KMeansTrainer>|

## <a name="principal-component-analysis"></a>主體元件分析

|屬性|定型器|
|----------|--------|
|用於異常偵測|<xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>|

## <a name="naive-bayes"></a>貝氏機率分類

|屬性|定型器|
|----------|--------|
|當特性獨立存在且定型資料集很小時，請使用此多元分類定型器。|<xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>|

## <a name="prior-trainer"></a>舊的定型器

|屬性|定型器|
|----------|--------|
|使用此二元分類定型器建立其他定型器的效能基準。 為有效率，其他定型器的計量應該比舊定型器好。 |<xref:Microsoft.ML.Trainers.PriorTrainer>|
