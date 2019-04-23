---
title: 機器學習工作 - ML.NET
description: 探索 ML.NET 中支援的各種不同機器學習工作與相關的工作。
ms.custom: seodec18
ms.date: 04/12/2019
author: natke
ms.openlocfilehash: bfed9cf12f8d539c4327549e5305415ce096e022
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613157"
---
# <a name="machine-learning-tasks-in-mlnet"></a>ML.NET 中的機器學習工作

建置機器學習模型時，您必須先定義希望利用資料來達成的目標。 這可讓您挑選適合您情況的機器學習工作。 以下清單描述可供您選擇的各種不同機器學習工作，以及一些常見的使用案例。

一旦您決定哪一個工作適用於您的案例，您就必須選擇最佳演算法來訓練模型。 每個工作的區段中列出了可用的演算法。

## <a name="binary-classification"></a>二元分類

這是一個[監督式機器學習](glossary.md#supervised-machine-learning)工作，可用來預測資料執行個體屬於兩個類別 (分類) 中的哪一個。 分類演算法的輸入是一組已加上標籤的範例，其中每個標籤都是 0 或 1 的整數。 二元分類演算法的輸出是一個分類器，可供您用來預測未加標籤之新執行個體的類別。 二元分類案例的範例包括：

* [理解 Twitter 評論的情感](../tutorials/sentiment-analysis.md)是「正面」還是「負面」。
* 診斷病患是否有某種疾病。
* 決定是否要將電子郵件標示為「垃圾郵件」。
* 決定相片是否包含狗或水果。

如需詳細資訊，請參閱維基百科上的[二元分類](https://en.wikipedia.org/wiki/Binary_classification) \(英文\) 一文。

### <a name="binary-classification-training-algorithms"></a>二元分類的訓練演算法

您可以使用下列演算法訓練二元分類模型：

* <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>
* <xref:Microsoft.ML.Trainers.LinearSvmTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.PriorTrainer>
* <xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer>
* <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>

## <a name="multiclass-classification"></a>多元分類

這是一個[監督式機器學習](glossary.md#supervised-machine-learning)工作，可用來預測資料執行個體的類別 (分類)。 分類演算法的輸入是一組已加上標籤的範例。 每個標籤通常會啟動成文字。 接著，它會透過 TermTransform 執行，這會將它轉會為索引鍵 (數值) 型別。 分類演算法的輸出是一個分類器，可供您用來預測未加標籤之新執行個體的類別。 多元分類案例的範例包括：

* 判斷狗的品種，例如「西伯利亞哈士奇」、「黃金獵犬」、「貴賓狗」等。
* 理解影片評論是「正面」、「中立」還是「負面」。
* 將飯店評論分類成「地點」、「價格」、「整潔度」等。

如需詳細資訊，請參閱維基百科上的[多元分類](https://en.wikipedia.org/wiki/Multiclass_classification) \(英文\) 一文。

>[!NOTE]
>One-Vs-All 將任何[二元分類學習工具](#binary-classification)升級，以在多元分類資料集上運作。 如需詳細資訊，請參閱 [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest)。

### <a name="multiclass-classification-training-algorithms"></a>多元分類訓練演算法

您可以使用下列訓練演算法訓練多元分類模型：

* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer>

## <a name="regression"></a>回復

這是一個[監督式機器學習](glossary.md#supervised-machine-learning)工作，可用來從一組相關的特徵預測標籤的值。 標籤可以有任何實際值，而不像在分類工作中那樣來自一組有限的值。 迴歸演算法會根據標籤的相關特徵建立標籤的相依性模型，以決定標籤會隨著特徵值的變化如何變更。 迴歸演算法的輸入是一組標籤為已知值的範例。 迴歸演算法的輸出是一個函式，可供您用來預測任何一組新輸入特徵的標籤值。 迴歸案例的範例包括：

* 根據房屋屬性 (例如房間數、地點、大小) 預測房價。
* 根據歷程記錄資料和目前的市場趨勢預測未來的股價。
* 根據廣告預算預測產品銷售額。

### <a name="regression-training-algorithms"></a>迴歸訓練演算法

您可以使用下列演算法訓練迴歸模型：

* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>

## <a name="clustering"></a>群集

這是一個[非監督式機器學習](glossary.md#unsupervised-machine-learning)工作，可用來將資料執行個體組成包含類似特性的群集。 群集也可用來在資料集內，識別您無法藉由瀏覽或簡單觀察以邏輯方式導出的關係。 群集演算法的輸入和輸出取決於所選擇的方法。 您可以採用以分佈、距心、連線或密度為基礎的方法。 ML.NET 目前支援使用 K 平均 (K-Means) 群集的距心型方法。 群集案例的範例包括：

* 根據選擇飯店時的習慣和特性，理解飯店賓客的區隔。
* 識別客戶區隔和人口統計，以協助建立目標性廣告活動。
* 根據製造計量來分類庫存。

### <a name="clustering-training-algorithms"></a>叢集訓練演算法

您可以使用下列演算法訓練叢集模型：

* <xref:Microsoft.ML.Trainers.KMeansTrainer>

## <a name="anomaly-detection"></a>異常偵測

這項工作會使用主成分分析 (PCA) 建立異常偵測模型。 以 PCA 為基礎的異常偵測可協助建置模型，在這種情況中可輕鬆地從一個類別 (例如有效的交易) 取得定型資料，但難以取得足夠的目標異常狀況樣本。

PCA 是以機器學習所建立的技術，經常用於探索資料分析，因為它能顯示資料的內部結構，並說明資料中的差異。 PCA 藉由分析包含多個變數的資料來運作。 它會尋找變數之間的關聯性，並決定最適合擷取結果中差異的值組合。 這些組合的特徵值會用來建立更精簡的特徵空間，稱為主成分。

異常偵測包含了機器學習中許多重要的工作：

* 識別潛在的詐騙交易。
* 學習指出發生網路入侵的模式。
* 尋找異常的患者叢集。
* 檢查輸入到系統的值。

因為定義上異常是罕見事件，因此難以收集具代表性的資料樣本來進行模型化。 此類別中包含的演算法經過特別設計，用來解決使用不平衡的資料集建置和定型模型所發生的核心挑戰。

### <a name="anomaly-detection-training-algorithms"></a>異常偵測訓練演算法

您可以使用下列演算法訓練異常偵測模型：

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

## <a name="ranking"></a>排名

排名工作會從一組已加上標籤的範例建構排名工具。 此範例集包含能夠以指定條件評分的執行個體群組。 每個執行個體的排名標籤是 { 0, 1, 2, 3, 4 }。  排名工具已定型為使用每個執行個體的未知分數排名新的執行個體群組。 ML.NET 排名學習工具是以[機器學習排名](https://en.wikipedia.org/wiki/Learning_to_rank) \(英文\) 為基礎。

### <a name="ranking-training-algorithms"></a>排名訓練演算法

您可以使用下列演算法訓練排名模型：

* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>

## <a name="recommendation"></a>建議

建議工作可產生建議的產品或服務清單。 ML.NET 使用[矩陣分解 (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29) \(英文\)，這是一種[協同過濾](https://en.wikipedia.org/wiki/Collaborative_filtering)演算法，適用於在您目錄中有過往的產品評等資料時提供建議。 例如，您擁有使用者過往的電影評等資料，而想要建議使用者接下來可能想看的其他電影。

### <a name="recommendation-training-algorithms"></a>建議訓練演算法

您可以使用下列演算法訓練建議模型：

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>
