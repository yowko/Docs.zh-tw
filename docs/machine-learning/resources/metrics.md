---
title: ML.NET 計量
description: 了解用於評估 ML.NET 模型效能的計量
ms.date: 12/17/2019
ms.openlocfilehash: 046e0a3feea2da702dfef5ca9ce4f498fce5fb26
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2020
ms.locfileid: "91804818"
---
# <a name="evaluate-your-mlnet-model-with-metrics"></a>使用計量來評估您的 ML.NET 模型

瞭解用來評估 ML.NET 模型的計量。

評估計量是模型所執行之機器學習工作的型別所特有的。

例如，針對分類工作，會測量預測類別與實際分類的程度，來評估模型。 針對叢集，評估是以接近叢集專案彼此的程度，以及叢集之間的分隔程度為基礎。

## <a name="evaluation-metrics-for-binary-classification"></a>二元分類的評估計量

| 計量   |      描述      |  尋找 |
|-----------|-----------------------|-----------|
| **精確度** |  [準確度](https://en.wikipedia.org/wiki/Accuracy_and_precision#In_binary_classification)是使用測試資料集進行正確預測的比例。 它是正確預測數佔總輸入樣本數的比例。 如果每個類別都有類似的樣本數，它就會很有作用。| **越接近 1.00 越好**。 但剛好 1.00 表示有問題 (通常是標籤/目標外洩、過度擬合或使用定型資料進行測試)。 當測試資料不對稱 (其中大部分的實例都屬於其中一個類別) 、資料集很小，或分數方法0.00 或1.00，則精確度並不會真正獲得分類器的效用，而您必須檢查其他度量。 |
| **AUC** |    *曲線下*的[aucROC](https://en.wikipedia.org/wiki/Receiver_operating_characteristic)或區域會測量實際的正值率與誤報的正負率，以測量所建立之曲線下的區域。  |   **越接近 1.00 越好**。 它應該大於0.50，才能接受模型。 AUC 為0.50 或更少的模型為毫無價值。 |
| **AUCPR** | *精確度回收曲線曲線下*的 AucPR 或區域：當類別不平衡 (高度扭曲的資料集) 時，可發揮預測成功的實用量值。 |  **越接近 1.00 越好**。 接近 1.00 的高分顯示分類器傳回精確的結果 (高精確度)，並傳回大部分為全面肯定的結果 (高重新叫用率)。 |
| **F1 分數** | [F1 分數](https://en.wikipedia.org/wiki/F1_score)也稱為「平衡 F 分數或 F 量值」**。 它是精確度和重新叫用率的調和平均數。 當您想要在精確度與重新叫用率之間取得平衡時，F1 分數會很有幫助。| **越接近 1.00 越好**。  F1 分數在 1.00 達到其最佳值，而最差分數為 0.00。 它會告訴您分類器有多精確。 |

如需二元分類計量的進一步詳細資訊，請閱讀下列文章：

- [精確度、有效位數、召回率或 F1？](https://towardsdatascience.com/accuracy-precision-recall-or-f1-331fb37c5cb9)
- [BinaryClassificationMetrics Class](xref:Microsoft.ML.Data.BinaryClassificationMetrics) (BinaryClassificationMetrics 類別)
- [The Relationship Between Precision-Recall and ROC Curves](http://pages.cs.wisc.edu/~jdavis/davisgoadrichcamera2.pdf) (PR 曲線與 ROC 曲線之間的關聯性)

## <a name="evaluation-metrics-for-multi-class-classification"></a>多重類別分類的評估計量

| 計量   |      描述      |  尋找 |
|-----------|-----------------------|-----------|
| **微準確度** |  [微平均準確度](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.MicroAccuracy)彙總所有類別的比重來計算平均計量。 它是正確預測的執行個體分數。 微平均不會將類別成員資格納入考量。 基本上，每個樣本類別配對佔準確度計量的比重會相等。 | **越接近 1.00 越好**。 在多元分類工作中，如果您懷疑類別失衡 (例如 您擁有某個類別的範例數比其他類別的範例數更多)，則微準確度優於宏準確度。|
| **宏準確度** | [宏平均準確度](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.MacroAccuracy)是類別層級的平均準確度。 每個類別的準確度會經過計算，而宏準確度是這些準確度的平均。 基本上，每個類別佔準確度計量的比重會相等。 少數類別會加上與較大類別相同的權重。 宏平均計量為每個類別提供相同的權數，無論資料集包含該類別中多少執行個體。 |  **越接近 1.00 越好**。  它會單獨計算每個類別的計量，然後求其平均 (因此對所有類別一視同仁) |
| **記錄檔遺失**| 對數損失測量分類模型的效能，其中預測輸入是介於 0.00 到 1.00 之間的機率值。 對數損失會隨著預測機率與實際標籤的偏離而增加。 | **越接近 0.00 越好**。 完美模型的對數損失值為 0.00。 我們的機器學習模型目標是將此值降到最低。|
| **對數損失降低** | [對數損失降低](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.LogLossReduction)可解譯為分類器優於隨機預測。| **範圍介於 -inf 到 1.00 之間，其中 1.00 表示完美的預測，而 0.00 表示平均預測**。 例如，如果值等於 0.20，則可以解譯為「正確預測的機率比隨機猜測好 20%」|

微準確度通常更符合 ML 預測的商務需求。 如果您想要選取單一計量來選擇多元分類工作品質，通常應該是微準確度。

支援票證分類工作範例 (將傳入票證對應至支援小組)

- 微準確度 -- 傳入票證分類到正確小組的頻率為何？
- 宏準確度 -- 對於一個普通小組而言，傳入票證對其小組正確的頻率為何？

宏精確度 overweights 此範例中的小型團隊;每年只取得10個票證的小型團隊，其數量會與每年1萬個票證的大型小組相同。 在此案例中，微準確度與「公司將我的票證路由程序最佳化可省下多少時間/金錢」的商務需求較相關。

如需多元分類計量的進一步詳細資訊，請閱讀下列文章：

- [精確度、召回率和 F 分數的微和宏平均值](https://rushdishams.blogspot.com/2011/08/micro-and-macro-average-of-precision.html)
- [Multiclass Classification with Imbalanced Dataset](https://towardsdatascience.com/machine-learning-multiclass-classification-with-imbalanced-data-set-29f6a177c1a) (失衡資料集的多元分類)

## <a name="evaluation-metrics-for-regression-and-recommendation"></a>回歸和建議的評估度量

回歸和建議工作都會預測數位。 在回歸的情況下，數位可以是任何會受到輸入屬性影響的輸出屬性。 若為建議，此數目通常是介於1到5之間的評等值 (例如) ，或分別以1和0表示) 的是/否建議 (。

| 計量   |      描述      |  尋找 |
|----------|-----------------------|-----------|
| **R 平方** |  [R 平方 (R2)](https://en.wikipedia.org/wiki/Coefficient_of_determination) 或「決定係數」** 以介於 -inf 到 1.00 之間的值來表示模型的預測能力。 1.00 表示有完全擬合；擬合也可能很差，因此分數可以是負數。 分數 0.00 表示模型將猜測到標籤的預測值。 R2 測量實際測試資料值與預測值有多接近。 | **越接近 1.00，品質就越好**。 不過，有時低 R 平方值 (例如 0.50) 可能完全正常或適合您的情節，而高 R 平方值不一定良好且值得懷疑。 |
| **絕對損失** |  [絕對損失](https://en.wikipedia.org/wiki/Mean_absolute_error)或「平均絕對誤差 (MAE)」** 測量預測與實際結果有多接近。 它是所有模型誤差的平均，其中模型誤差係指所預測標籤值與正確標籤值之間的絕對差。 此預測誤差是針對每個記錄到的測試資料集計算而來。 最後，會針對所有記錄到的絕對誤差，計算其平均值。| **越接近 0.00，品質就越好。** 平均絕對錯誤會使用與所測量資料相同的比例 (不會正規化為特定範圍) 。 只有模型屬於相同資料集或標籤值分佈類似的資料集時，才能使用絕對損失、平方損失和 RMS 損失以在這些模型之間進行比較。 |
| **平方-遺失** |  [平方](https://en.wikipedia.org/wiki/Mean_squared_error) 差或 *Mean 平方誤差 (MSE) *，也稱為 *平均平方差 (MSD) *，可讓您從點到迴歸線的距離，告訴您如何將迴歸線與一組測試資料值接近， (這些距離是錯誤 E) 並加以求。 平方會提供較多權數給較大的偏差。 | 它一律是非負數，且**值越接近 0.00 越好**。 視您的資料而定，可能無法取得非常小的均方誤差值。|
| **RMS 損失** |  [RMS 遺失](https://en.wikipedia.org/wiki/Root-mean-square_deviation) 或 *方根平方誤差 (RMSE) * (也稱為「 *根平均平方差，RMSD*) ，測量模型所預測的值與正在模型化環境中觀察到的值之間的差異。 RMS 損失是平方損失的平方根，且具有與標籤相同的單位，類似於絕對損失，但提供較多權數給較大的偏差。 均方根誤差常用於氣候學、預測和迴歸分析來驗證實驗結果。 | 它一律是非負數，且**值越接近 0.00 越好**。 RMSD 是準確度量值，用於比較特定資料集 (而非資料集之間) 不同模型的預測誤差，因為它會視標尺而定。|

如需迴歸計量的進一步詳細資訊，請閱讀下列文章：

- [迴歸分析：如何解讀 R 平方並評估符合度？](https://blog.minitab.com/blog/adventures-in-statistics-2/regression-analysis-how-do-i-interpret-r-squared-and-assess-the-goodness-of-fit)
- [How To Interpret R-squared in Regression Analysis](https://statisticsbyjim.com/regression/interpret-r-squared-regression) (如何解譯迴歸分析中的 R 平方)
- [R-Squared Definition](https://www.investopedia.com/terms/r/r-squared.asp) (R 平方定義)
- [Mean Squared Error Definition](https://www.statisticshowto.datasciencecentral.com/mean-squared-error/) (均方誤差定義)
- [What are Mean Squared Error and Root Mean Squared Error?](https://www.vernier.com/til/1014/) (什麼是均方誤差和均方根誤差？)

## <a name="evaluation-metrics-for-clustering"></a>群集的評估度量

| 計量   |      描述      |  尋找 |
|----------|-----------------------|-----------|
|**平均距離**|資料點與其指派叢集中心之間的平均距離。 平均距離是資料點與叢集距心之間鄰近性的量值。 它是「嚴格」叢集的測量方式。|接近 **0** 的值比較好。 平均距離越接近零，資料的叢集就越多。 不過請注意，如果叢集數目增加，此計量將會減少，而在極端情況下 (，其中每個不同的資料點都是它自己的叢集) 它會等於零。
|**Davies Bouldin 索引**|叢集間距離與叢集之間距離之間的平均比例。 叢集越緊密，叢集越進一步，此值就越低。|接近 **0** 的值比較好。 距離較低且散佈較低的叢集，將會產生更好的分數。|
|**正規化的相互資訊**|當用來定型群集模型的定型資料也隨附于 (也就是受監督的叢集) 時，可以使用。 正規化的相互資訊計量會測量是否將類似的資料點指派給相同的叢集，以及將不同的資料點指派給不同的叢集。 正規化的相互資訊是介於0和1之間的值|較接近 **1** 的值比較好|

## <a name="evaluation-metrics-for-ranking"></a>排名的評估計量

| 計量   |      描述      |  尋找 |
|----------|-----------------------|-----------|
|**折扣累積增益**|折扣累積增益 (DCG) 是等級品質的量值。 它衍生自兩個假設。 一種：高度相關的專案在依排名順序出現較高時更有用。 二：實用性會追蹤相關性，也就是相關性愈高，專案越有用。 針對排名順序中的特定位置計算折扣累積增益。 它會將相關性評分除以排名索引的對數到感興趣的位置。 其計算方式是使用 $ \ sum_ {i = 0} ^ {p} \frac {rel_i} {\ log_ {e} {i + 1}} $ 相關性 gradings 會提供給排名定型演算法作為真實的標籤。 針對排名資料表中的每個位置提供一個 DCG 值，因此折扣累計 **增益**的名稱。 |**較高的值更好**|
|**正規化折扣累積增益**|正規化 DCG 可讓計量針對不同長度的排名清單進行比較|**較接近1的值比較好**|

## <a name="evaluation-metrics-for-anomaly-detection"></a>異常偵測的評估計量

| 計量   |      描述      |  尋找 |
|----------|-----------------------|-----------|
|**ROC 曲線下的區域**|收件者運算子曲線下的區域會測量模型區隔異常和一般資料點的程度。|**較接近1的值比較好**。 只有大於0.5 的值會示範模型的有效性。 0.5 或以下的值表示模型不如將輸入隨機配置到異常和一般類別|
|**偵測速率（錯誤）正計數**|偵測速率（以 false 為限）是正確識別的異常數目與測試集內的異常總數的比率，以每個錯誤的正數來編制索引。 也就是說，每個錯誤正面專案的偵測速率值為 false 正計數。|**較接近1的值比較好**。 如果沒有任何誤報，則此值為1。|
