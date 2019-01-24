---
title: 機器學習工作 - ML.NET
description: 探索 ML.NET 中支援的各種不同機器學習工作與相關的工作。
ms.custom: seodec18
ms.date: 01/15/2019
author: jralexander
ms.openlocfilehash: 02b454d18eca36c94c27ae15665af5df2ec87905
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415698"
---
# <a name="machine-learning-tasks-in-mlnet"></a>ML.NET 中的機器學習工作

建置機器學習模型時，您必須先定義希望利用資料來達成的目標。 之後，就可以挑選適合您情況的機器學習工作。 以下清單描述可供您選擇的各種不同機器學習工作，以及一些常見的使用案例。

> [!NOTE]
> ML.NET 目前為預覽版。 目前並非所有機器學習工作都受到支援。 若要提交特定工作的要求，請在 [dotnet/machinelearning 存放庫](https://github.com/dotnet/machinelearning/issues)中建立一個問題。

## <a name="binary-classification"></a>二元分類

這是一個[監督式機器學習](glossary.md#supervised-machine-learning)工作，可用來預測資料執行個體屬於兩個類別 (分類) 中的哪一個。 分類演算法的輸入是一組已加上標籤的範例，其中每個標籤都是 0 或 1 的整數。 二元分類演算法的輸出是一個分類器，可供您用來預測未加標籤之新執行個體的類別。 二元分類案例的範例包括：

* [理解 Twitter 評論的情感](../tutorials/sentiment-analysis.md)是「正面」還是「負面」。
* 診斷病患是否有某種疾病。
* 決定是否要將電子郵件標示為「垃圾郵件」。
* 決定相片是否包含狗或水果。

如需詳細資訊，請參閱維基百科上的[二元分類](https://en.wikipedia.org/wiki/Binary_classification) \(英文\) 一文。

針對二元分類建議的學習工具：

* AveragedPerceptronTrainer
* StochasticGradientDescentClassificationTrainer
* LightGbmBinaryTrainer
* FastTreeBinaryClassificationTrainer
* SymSgdClassificationTrainer

### <a name="binary-classification-learners"></a>二元分類學習工具

下列學習工具適用於二元分類工作：

* [AveragedPerceptronTrainer](xref:Microsoft.ML.Trainers.Online.AveragedPerceptronTrainer)
* [BinaryClassificationGamTrainer](xref:Microsoft.ML.Trainers.FastTree.BinaryClassificationGamTrainer)
* [FastForestClassification](xref:Microsoft.ML.Trainers.FastTree.FastForestClassification)
* [FastTreeBinaryClassificationTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer)
* [FieldAwareFactorizationMachineTrainer](xref:Microsoft.ML.FactorizationMachine.FieldAwareFactorizationMachineTrainer)
* [LightGbmBinaryTrainer](xref:Microsoft.ML.LightGBM.LightGbmBinaryTrainer)
* [LinearSvmTrainer](xref:Microsoft.ML.Trainers.Online.LinearSvmTrainer)
* [LogisticRegression](xref:Microsoft.ML.Learners.LogisticRegression)
* [PriorTrainer](xref:Microsoft.ML.Trainers.PriorTrainer)
* [RandomTrainer](xref:Microsoft.ML.Trainers.RandomTrainer)
* [StochasticGradientDescentClassificationTrainer](xref:Microsoft.ML.Trainers.StochasticGradientDescentClassificationTrainer)
* [SymSgdClassificationTrainer](xref:Microsoft.ML.Trainers.SymSgd.SymSgdClassificationTrainer)

## <a name="multiclass-classification"></a>多元分類

這是一個[監督式機器學習](glossary.md#supervised-machine-learning)工作，可用來預測資料執行個體的類別 (分類)。 分類演算法的輸入是一組已加上標籤的範例。 每個標籤通常會啟動成文字。 接著，它會透過 TermTransform 執行，這會將它轉會為索引鍵 (數值) 型別。 分類演算法的輸出是一個分類器，可供您用來預測未加標籤之新執行個體的類別。 多元分類案例的範例包括：

* 判斷狗的品種，例如「西伯利亞哈士奇」、「黃金獵犬」、「貴賓狗」等。
* 理解影片評論是「正面」、「中立」還是「負面」。
* 將飯店評論分類成「地點」、「價格」、「整潔度」等。

如需詳細資訊，請參閱維基百科上的[多元分類](https://en.wikipedia.org/wiki/Multiclass_classification) \(英文\) 一文。

適用於多元分類的建議學習工具：

* OVA-AveragedPerceptronTrainer
* SdcaMultiClassTrainer
* LightGbmMulticlassTrainer
* OVA-FastTreeBinaryClassificationTrainer

>[!NOTE]
>OVA 和 PKPD 會將任何[二元分類學習工具](#binary-classification)升級以在多元分類資料集上運作。 如需詳細資訊，請參閱 [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest)。

### <a name="multiclass-classification-learners"></a>多元分類學習工具

下列學習工具適用於多元分類工作：

* [LightGbmMulticlassTrainer](xref:Microsoft.ML.LightGBM.LightGbmMulticlassTrainer)
* [MetaMulticlassTrainer<TTransformer,TModel>](xref:Microsoft.ML.Learners.MetaMulticlassTrainer%602)
* [MultiClassNaiveBayesTrainer](xref:Microsoft.ML.Trainers.MultiClassNaiveBayesTrainer)
* [Ova](xref:Microsoft.ML.Trainers.Ova)
* [Pkpd](xref:Microsoft.ML.Trainers.Pkpd)
* [SdcaMultiClassTrainer](xref:Microsoft.ML.Trainers.SdcaMultiClassTrainer)

## <a name="regression"></a>迴歸

這是一個[監督式機器學習](glossary.md#supervised-machine-learning)工作，可用來從一組相關的特徵預測標籤的值。 標籤可以有任何實際值，而不像在分類工作中那樣來自一組有限的值。 迴歸演算法會根據標籤的相關特徵建立標籤的相依性模型，以決定標籤會隨著特徵值的變化如何變更。 迴歸演算法的輸入是一組標籤為已知值的範例。 迴歸演算法的輸出是一個函式，可供您用來預測任何一組新輸入特徵的標籤值。 迴歸案例的範例包括：

* 根據房屋屬性 (例如房間數、地點、大小) 預測房價。
* 根據歷程記錄資料和目前的市場趨勢預測未來的股價。
* 根據廣告預算預測產品銷售額。

適用於迴歸的建議學習工具：

* FastTreeTweedieTrainer 
* LightGbmRegressorTrainer 
* SdcaRegressionTrainer 
* FastTreeRegressionTrainer

### <a name="regression-learners"></a>迴歸學習工具

下列學習工具適用於迴歸工作：

* [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer)
* [FastTreeTweedieTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer)
* [LightGbmRegressorTrainer](xref:Microsoft.ML.LightGBM.LightGbmRegressorTrainer)
* [OlsLinearRegressionTrainer](xref:Microsoft.ML.Trainers.HalLearners.OlsLinearRegressionTrainer)
* [OnlineGradientDescentTrainer](xref:Microsoft.ML.Trainers.Online.OnlineGradientDescentTrainer)
* [PoissonRegression](xref:Microsoft.ML.Trainers.PoissonRegression)
* [RegressionGamTrainer](xref:Microsoft.ML.Trainers.FastTree.RegressionGamTrainer)
* [SdcaRegressionTrainer](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer)
* [FastTree.SingleTrainer](xref:Microsoft.ML.Trainers.FastTree.SingleTrainer)
* [LightGBM.SingleTrainer](xref:Microsoft.ML.LightGBM.SingleTrainer)

## <a name="clustering"></a>群集

這是一個[非監督式機器學習](glossary.md#unsupervised-machine-learning)工作，可用來將資料執行個體組成包含類似特性的群集。 群集也可用來在資料集內，識別您無法藉由瀏覽或簡單觀察以邏輯方式導出的關係。 群集演算法的輸入和輸出取決於所選擇的方法。 您可以採用以分佈、距心、連線或密度為基礎的方法。 ML.NET 目前支援使用 K 平均 (K-Means) 群集的距心型方法。 群集案例的範例包括：

* 根據選擇飯店時的習慣和特性，理解飯店賓客的區隔。
* 識別客戶區隔和人口統計，以協助建立目標性廣告活動。
* 根據製造計量來分類庫存。

### <a name="clustering-learners"></a>叢集學習工具

下列學習工具適用於叢集工作：

* [KMeansPlusPlusTrainer](xref:Microsoft.ML.Trainers.KMeans.KMeansPlusPlusTrainer)

## <a name="anomaly-detection"></a>異常偵測

這項工作會使用主成分分析 (PCA) 建立異常偵測模型。 以 PCA 為基礎的異常偵測可協助建置模型，在這種情況中可輕鬆地從一個類別 (例如有效的交易) 取得定型資料，但難以取得足夠的目標異常狀況樣本。

PCA 是以機器學習所建立的技術，經常用於探索資料分析，因為它能顯示資料的內部結構，並說明資料中的差異。 PCA 藉由分析包含多個變數的資料來運作。 它會尋找變數之間的關聯性，並決定最適合擷取結果中差異的值組合。 這些組合的特徵值會用來建立更精簡的特徵空間，稱為主成分。

異常偵測包含了機器學習中許多重要的工作：

* 識別潛在的詐騙交易。
* 學習指出發生網路入侵的模式。
* 尋找異常的患者叢集。
* 檢查輸入到系統的值。

因為定義上異常是罕見事件，因此難以收集具代表性的資料樣本來進行模型化。 此類別中包含的演算法經過特別設計，用來解決使用不平衡的資料集建置和定型模型所發生的核心挑戰。

### <a name="anomaly-detection-learners"></a>異常偵測學習工具

下列學習工具適用於異常偵測工作：

* [RandomizedPcaTrainer](xref:Microsoft.ML.Trainers.PCA.RandomizedPcaTrainer)

## <a name="ranking"></a>排名

排名工作會從一組已加上標籤的範例建構排名工具。 此範例集包含能夠以指定條件評分的執行個體群組。 每個執行個體的排名標籤是 { 0, 1, 2, 3, 4 }。  排名工具已定型為使用每個執行個體的未知分數排名新的執行個體群組。 ML.NET 排名學習工具是以[機器學習排名](https://en.wikipedia.org/wiki/Learning_to_rank) \(英文\) 為基礎。

### <a name="ranking-learners"></a>排名學習工具

下列學習工具適用於排名工作：

* [FastTreeRankingTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer)
* [LightGbmRankingTrainer](xref:Microsoft.ML.LightGBM.LightGbmRankingTrainer)

## <a name="recommendation"></a>建議

建議工作可產生建議的產品或服務清單。 ML.NET 使用[矩陣分解 (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29) \(英文\)，這是一種[協同過濾](https://en.wikipedia.org/wiki/Collaborative_filtering)演算法，適用於在您目錄中有過往的產品評等資料時提供建議。 例如，您擁有使用者過往的電影評等資料，而想要建議使用者接下來可能想看的其他電影。

### <a name="recommendation-learners"></a>建議學習工具

下列學習工具適用於建議工作：

* [MatrixFactorizationTrainer](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer)
* [MatrixFactorizationPredictionTransformer](xref:Microsoft.ML.Trainers.Recommender.MatrixFactorizationPredictionTransformer)
