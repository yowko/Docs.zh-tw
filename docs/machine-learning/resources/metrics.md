---
title: ML.NET 計量
description: 了解用於評估 ML.NET 模型效能的計量
ms.date: 12/17/2019
ms.openlocfilehash: 8e823fd8cc344c1b8e0ecd709b527137368cbfa0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399214"
---
# <a name="evaluate-your-mlnet-model-with-metrics"></a>使用指標評估ML.NET模型

瞭解用於評估ML.NET模型的指標。

評估指標特定于模型執行的機器學習任務類型。

例如，對於分類任務，通過測量預測類別與實體類別匹配程度來評估模型。 對於聚類，評估基於群集項彼此的接近程度，以及群集之間的分離程度。

## <a name="evaluation-metrics-for-binary-classification"></a>二進位分類的評估指標

| 計量   |      描述      |  尋找 |
|-----------|-----------------------|-----------|
| **精度** |  [準確度](https://en.wikipedia.org/wiki/Accuracy_and_precision#In_binary_classification)是使用測試資料集進行正確預測的比例。 它是正確預測數佔總輸入樣本數的比例。 如果每個類的樣本數量相似，則效果良好。| **越接近 1.00 越好**。 但剛好 1.00 表示有問題 (通常是標籤/目標外洩、過度擬合或使用定型資料進行測試)。 當測試資料不平衡時（其中大多數實例屬於其中一個類），資料集較小，或分數接近 0.00 或 1.00，則準確性不會真正捕獲分類器的有效性，您需要檢查其他指標。 |
| **AUC** |    [aucROC](https://en.wikipedia.org/wiki/Receiver_operating_characteristic)或*曲線下的面積*測量通過掃描真實正率與誤報率創建的曲線下的區域。  |   **越接近 1.00 越好**。 模型應大於 0.50，才能被接受。 AUC 小於 0.50 的模型毫無價值。 |
| **AUCPR** | *精度-召回曲線曲線下的* [aucPR](https://www.coursera.org/lecture/ml-classification/precision-recall-curve-rENu8)或區域：當類不平衡時預測成功的有用度量（高度偏斜資料集）。 |  **越接近 1.00 越好**。 接近 1.00 的高分顯示分類器傳回精確的結果 (高精確度)，並傳回大部分為全面肯定的結果 (高重新叫用率)。 |
| **F1 分數** | [F1 分數](https://en.wikipedia.org/wiki/F1_score)也稱為「平衡 F 分數或 F 量值」**。 它是精確度和重新叫用率的調和平均數。 當您想要在精確度與重新叫用率之間取得平衡時，F1 分數會很有幫助。| **越接近 1.00 越好**。  F1 分數在 1.00 達到其最佳值，而最差分數為 0.00。 它會告訴您分類器有多精確。 |

如需二元分類計量的進一步詳細資訊，請閱讀下列文章：

- [精度、精度、召回還是 F1？](https://towardsdatascience.com/accuracy-precision-recall-or-f1-331fb37c5cb9)
- [BinaryClassificationMetrics Class](xref:Microsoft.ML.Data.BinaryClassificationMetrics) (BinaryClassificationMetrics 類別)
- [The Relationship Between Precision-Recall and ROC Curves](http://pages.cs.wisc.edu/~jdavis/davisgoadrichcamera2.pdf) (PR 曲線與 ROC 曲線之間的關聯性)

## <a name="evaluation-metrics-for-multi-class-classification"></a>多類分類的評估指標

| 計量   |      描述      |  尋找 |
|-----------|-----------------------|-----------|
| **微準確度** |  [微平均準確度](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.MicroAccuracy)彙總所有類別的比重來計算平均計量。 它是正確預測的執行個體分數。 微平均不會將類別成員資格納入考量。 基本上，每個樣本類別配對佔準確度計量的比重會相等。 | **越接近 1.00 越好**。 在多元分類工作中，如果您懷疑類別失衡 (例如 您擁有某個類別的範例數比其他類別的範例數更多)，則微準確度優於宏準確度。|
| **宏準確度** | [宏平均準確度](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.MacroAccuracy)是類別層級的平均準確度。 每個類別的準確度會經過計算，而宏準確度是這些準確度的平均。 基本上，每個類別佔準確度計量的比重會相等。 少數類別會加上與較大類別相同的權重。 宏平均計量為每個類別提供相同的權數，無論資料集包含該類別中多少執行個體。 |  **越接近 1.00 越好**。  它會單獨計算每個類別的計量，然後求其平均 (因此對所有類別一視同仁) |
| **日誌丟失**| [對數損失](http://wiki.fast.ai/index.php/Log_Loss)測量分類模型的效能，其中預測輸入是介於 0.00 到 1.00 之間的機率值。 對數損失會隨著預測機率與實際標籤的偏離而增加。 | **越接近 0.00 越好**。 完美模型的對數損失值為 0.00。 我們的機器學習模型目標是將此值降到最低。|
| **對數損失降低** | [對數損失降低](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.LogLossReduction)可解譯為分類器優於隨機預測。| **範圍介於 -inf 到 1.00 之間，其中 1.00 表示完美的預測，而 0.00 表示平均預測**。 例如，如果值等於 0.20，則可以解譯為「正確預測的機率比隨機猜測好 20%」|

微準確度通常更符合 ML 預測的商務需求。 如果您想要選取單一計量來選擇多元分類工作品質，通常應該是微準確度。

支援票證分類工作範例 (將傳入票證對應至支援小組)

- 微準確度 -- 傳入票證分類到正確小組的頻率為何？
- 宏準確度 -- 對於一個普通小組而言，傳入票證對其小組正確的頻率為何？

在本示例中，宏觀準確性超重小團隊;一支每年只拿到10張門票的小團隊，與一支每年擁有1萬張門票的大型團隊一樣重要。 在此案例中，微準確度與「公司將我的票證路由程序最佳化可省下多少時間/金錢」的商務需求較相關。

如需多元分類計量的進一步詳細資訊，請閱讀下列文章：

- [精度、召回和 F-Score 的微觀和宏觀平均值](https://rushdishams.blogspot.com/2011/08/micro-and-macro-average-of-precision.html)
- [Multiclass Classification with Imbalanced Dataset](https://towardsdatascience.com/machine-learning-multiclass-classification-with-imbalanced-data-set-29f6a177c1a) (失衡資料集的多元分類)

## <a name="evaluation-metrics-for-regression-and-recommendation"></a>回歸和建議的評估指標

回歸任務和建議任務都預測數位。 在回歸的情況下，數位可以是受輸入屬性影響的任何輸出屬性。 對於建議，該數位通常是評級值（例如 1 和 5 之間）或"是/否"建議（分別由 1 和 0 表示）。

| 計量   |      描述      |  尋找 |
|----------|-----------------------|-----------|
| **R 平方** |  [R 平方 (R2)](https://en.wikipedia.org/wiki/Coefficient_of_determination) 或「決定係數」** 以介於 -inf 到 1.00 之間的值來表示模型的預測能力。 1.00 表示有完全擬合；擬合也可能很差，因此分數可以是負數。 分數 0.00 表示模型將猜測到標籤的預測值。 R2 測量實際測試資料值與預測值有多接近。 | **越接近 1.00，品質就越好**。 不過，有時低 R 平方值 (例如 0.50) 可能完全正常或適合您的情節，而高 R 平方值不一定良好且值得懷疑。 |
| **絕對損失** |  [絕對損失](https://en.wikipedia.org/wiki/Mean_absolute_error)或「平均絕對誤差 (MAE)」** 測量預測與實際結果有多接近。 它是所有模型誤差的平均，其中模型誤差係指所預測標籤值與正確標籤值之間的絕對差。 此預測誤差是針對每個記錄到的測試資料集計算而來。 最後，會針對所有記錄到的絕對誤差，計算其平均值。| **越接近 0.00，品質就越好。** 平均絕對誤差使用與所測量資料相同的比例（未歸化為特定範圍）。 只有模型屬於相同資料集或標籤值分佈類似的資料集時，才能使用絕對損失、平方損失和 RMS 損失以在這些模型之間進行比較。 |
| **平方損耗** |  [平方損失](https://en.wikipedia.org/wiki/Mean_squared_error)或*均值平方誤差 （MSE）* 也稱為*均方偏差 （MSD），* 通過從點到迴歸線的距離（這些距離是誤差 E）並四分排列，告訴您迴歸線與一組測試資料值的距離有多近。 平方會提供較多權數給較大的偏差。 | 它一律是非負數，且**值越接近 0.00 越好**。 視您的資料而定，可能無法取得非常小的均方誤差值。|
| **RMS 損失** |  [RMS 損失](https://en.wikipedia.org/wiki/Root-mean-square_deviation)或*根均值平方誤差 （RMSE）* （也稱為*根均方平方偏差， RMSD*）， 測量模型預測的值與從正在建模的環境中觀察到的值之間的差異。 RMS 損失是平方損失的平方根，且具有與標籤相同的單位，類似於絕對損失，但提供較多權數給較大的偏差。 均方根誤差常用於氣候學、預測和迴歸分析來驗證實驗結果。 | 它一律是非負數，且**值越接近 0.00 越好**。 RMSD 是準確度量值，用於比較特定資料集 (而非資料集之間) 不同模型的預測誤差，因為它會視標尺而定。|

如需迴歸計量的進一步詳細資訊，請閱讀下列文章：

- [迴歸分析：如何解釋 R 平方和評估擬合的優劣？](https://blog.minitab.com/blog/adventures-in-statistics-2/regression-analysis-how-do-i-interpret-r-squared-and-assess-the-goodness-of-fit)
- [How To Interpret R-squared in Regression Analysis](https://statisticsbyjim.com/regression/interpret-r-squared-regression) (如何解譯迴歸分析中的 R 平方)
- [R-Squared Definition](https://www.investopedia.com/terms/r/r-squared.asp) (R 平方定義)
- [Mean Squared Error Definition](https://www.statisticshowto.datasciencecentral.com/mean-squared-error/) (均方誤差定義)
- [What are Mean Squared Error and Root Mean Squared Error?](https://www.vernier.com/til/1014/) (什麼是均方誤差和均方根誤差？)

## <a name="evaluation-metrics-for-clustering"></a>聚類評估指標

| 計量   |      描述      |  尋找 |
|----------|-----------------------|-----------|
|**平均距離**|資料點與其分配的群集的中心之間的距離平均值。 平均距離是資料點與聚類質心的接近量的度量。 它是衡量群集"緊密"程度的度量。|接近**0**的值更好。 平均距離越接近零，資料越聚類。 但請注意，如果群集數量增加，此指標將減少，在極端情況下（每個不同的資料點是都是其自己的群集），則此指標將等於零。
|**大衛斯·布林丁指數**|群集內距離與群集之間距離的平均比率。 群集越緊密，群集之間的距離越遠，此值越低。|接近**0**的值更好。 相距較遠且分散較少的群集將產生更好的分數。|
|**標準化互資訊**|當用於訓練聚類模型的訓練資料還附帶接地真實標籤（即受監督聚類）時，可以使用。 標準化相互資訊指標測量是否將類似的資料點分配給同一群集，不同的資料點是否分配給不同的群集。 正常化的相互資訊是介於 0 和 1 之間的值|接近**1**的值更好|

## <a name="evaluation-metrics-for-ranking"></a>排名評估指標

| 計量   |      描述      |  尋找 |
|----------|-----------------------|-----------|
|**貼現累積收益**|貼現累積收益 （DCG） 是排名品質的度量。 它來自兩個假設。 其一：高度相關的專案在排名順序上顯示較高時更有用。 二：有用性跟蹤相關性，即相關性越高，項越有用。 為排名訂單中的特定頭寸計算貼現累積收益。 它將相關性分級除以排名指數的對數和興趣位置。 它使用 $sum_{i}0}p} [frac ]rel_i] [log_{i{1}$ 相關性分級提供給排名訓練演算法作為地面真理標籤計算。 對於排名表中的每個職位，提供一個 DCG 值，因此名稱為貼現累積**收益**。 |**值越高越好**|
|**標準化貼現累計收益**|標準化 DCG 允許比較不同長度的排名清單的指標|**接近 1 的值更好**|

## <a name="evaluation-metrics-for-anomaly-detection"></a>異常檢測的評估指標

| 計量   |      描述      |  尋找 |
|----------|-----------------------|-----------|
|**ROC 曲線下的面積**|接收器運算子曲線下的區域測量模型分離異常和常用資料點的路數。|**接近 1 的值更好**。 只有大於 0.5 的值才能證明模型的有效性。 值 0.5 或以下表示模型不比隨機將輸入分配給異常和通常的類別更好|
|**誤報計數的檢測速率**|誤報計數的檢測率是正確識別異常數與測試集中異常總數的比率，由每個誤報編制索引。 也就是說，每個誤報項的誤報計數檢測率值。|**接近 1 的值更好**。 如果沒有誤報，則此值為 1|
