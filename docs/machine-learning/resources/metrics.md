---
title: ML.NET 計量
description: 了解用於評估 ML.NET 模型效能的計量
ms.date: 04/29/2019
author: ''
ms.openlocfilehash: 802f0a8fd32c492c8d9f89933b183802cb178cb3
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053048"
---
# <a name="model-evaluation-metrics-in-mlnet"></a>ML.NET 中的模型評估計量

## <a name="metrics-for-binary-classification"></a>二元分類計量

| 計量   |      說明      |  尋找 |
|-----------|-----------------------|-----------|
| **準確度** |  [準確度](https://en.wikipedia.org/wiki/Accuracy_and_precision#In_binary_classification)是使用測試資料集進行正確預測的比例。 它是正確預測數佔總輸入樣本數的比例。 只有在每個類別所屬樣本數類似時才適用。| **越接近 1.00 越好**。 但剛好 1.00 表示有問題 (通常是標籤/目標外洩、過度擬合或使用定型資料進行測試)。 當測試資料失衡 (大部分執行個體屬於其中一個類別)、資料集很小，或是分數接近 0.00 或 1.00 時，則表示準確度未真正獲得分類器的效果，因此您需要檢查其他計量。 |
| **AUC** |    [aucROC](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) 或「曲線下的區域」：這是測量由掃掠真肯定率與誤判率所建立曲線下的區域。  |   **越接近 1.00 越好**。 它應該大於 0.50，模型才可被接受；AUC 為 0.50 或更小的模型則毫無價值。 |
| **AUCPR** | [aucPR](https://www.coursera.org/lecture/ml-classification/precision-recall-curve-rENu8) 或「PR (精確度-重新叫用率) 曲線的曲線下區域」：適合在類別非常失衡 (資料集高度扭曲) 時用於測量預測是否成功。 |  **越接近 1.00 越好**。 接近 1.00 的高分顯示分類器傳回精確的結果 (高精確度)，並傳回大部分為全面肯定的結果 (高重新叫用率)。 |
| **F1 分數** | [F1 分數](https://en.wikipedia.org/wiki/F1_score)也稱為「平衡 F 分數或 F 量值」。 它是精確度和重新叫用率的調和平均數。 當您想要在精確度與重新叫用率之間取得平衡時，F1 分數會很有幫助。| **越接近 1.00 越好**。  F1 分數在 1.00 達到其最佳值，而最差分數為 0.00。 它會告訴您分類器有多精確。 |

如需二元分類計量的進一步詳細資訊，請閱讀下列文章：

- [Accuracy, Precision, Recall or F1?](https://towardsdatascience.com/accuracy-precision-recall-or-f1-331fb37c5cb9) (準確度、精確度、重新叫用率或 F1？)
- [BinaryClassificationMetrics Class](xref:Microsoft.ML.Data.BinaryClassificationMetrics) (BinaryClassificationMetrics 類別)
- [The Relationship Between Precision-Recall and ROC Curves](http://pages.cs.wisc.edu/~jdavis/davisgoadrichcamera2.pdf) (PR 曲線與 ROC 曲線之間的關聯性)

## <a name="metrics-for-multi-class-classification"></a>多元分類計量

| 計量   |      說明      |  尋找 |
|-----------|-----------------------|-----------|
| **微準確度** |  [微平均準確度](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.MicroAccuracy)彙總所有類別的比重來計算平均計量。 它是正確預測的執行個體分數。 微平均不會將類別成員資格納入考量。 基本上，每個樣本類別配對佔準確度計量的比重會相等。 | **越接近 1.00 越好**。 在多元分類工作中，如果您懷疑類別失衡 (例如 您擁有某個類別的範例數比其他類別的範例數更多)，則微準確度優於宏準確度。|
| **宏準確度** | [宏平均準確度](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.MacroAccuracy)是類別層級的平均準確度。 每個類別的準確度會經過計算，而宏準確度是這些準確度的平均。 基本上，每個類別佔準確度計量的比重會相等。 少數類別會加上與較大類別相同的權重。 宏平均計量為每個類別提供相同的權數，無論資料集包含該類別中多少執行個體。 |  **越接近 1.00 越好**。  它會單獨計算每個類別的計量，然後求其平均 (因此對所有類別一視同仁) |
| **對數損失**| [對數損失](http://wiki.fast.ai/index.php/Log_Loss)測量分類模型的效能，其中預測輸入是介於 0.00 到 1.00 之間的機率值。 對數損失會隨著預測機率與實際標籤的偏離而增加。 | **越接近 0.00 越好**。 完美模型的對數損失值為 0.00。 我們的機器學習模型目標是將此值降到最低。|
| **對數損失降低** | [對數損失降低](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.LogLossReduction)可解譯為分類器優於隨機預測。| **範圍介於 -inf 到 1.00 之間，其中 1.00 表示完美的預測，而 0.00 表示平均預測**。 例如，如果值等於 0.20，則可以解譯為「正確預測的機率比隨機猜測好 20%」|

微準確度通常更符合 ML 預測的商務需求。 如果您想要選取單一計量來選擇多元分類工作品質，通常應該是微準確度。

支援票證分類工作範例 (將傳入票證對應至支援小組)

- 微準確度 -- 傳入票證分類到正確小組的頻率為何？
- 宏準確度 -- 對於一個普通小組而言，傳入票證對其小組正確的頻率為何？

在此範例中，宏準確度會加權調整小型團隊，讓每年只會取得 10 個票證的小型團隊等同於每年取得 1 萬個票證的大型團隊。 在此案例中，微準確度與「公司將我的票證路由程序最佳化可省下多少時間/金錢」的商務需求較相關。

如需多元分類計量的進一步詳細資訊，請閱讀下列文章：

- [Micro- and Macro-average of Precision, Recall and F-Score](http://rushdishams.blogspot.com/2011/08/micro-and-macro-average-of-precision.html) (精確度、重新叫用率和 F 分數的微準確度和宏準確度)
- [Multiclass Classification with Imbalanced Dataset](https://towardsdatascience.com/machine-learning-multiclass-classification-with-imbalanced-data-set-29f6a177c1a) (失衡資料集的多元分類)

## <a name="metrics-for-regression"></a>迴歸計量

| 計量   |      說明      |  尋找 |
|-----------|-----------------------|-----------|
| **R 平方** |  [R 平方 (R2)](https://en.wikipedia.org/wiki/Coefficient_of_determination) 或「決定係數」以介於 -inf 到 1.00 之間的值來表示模型的預測能力。 1.00 表示有完全擬合；擬合也可能很差，因此分數可以是負數。 分數 0.00 表示模型將猜測到標籤的預測值。 R2 測量實際測試資料值與預測值有多接近。 | **越接近 1.00，品質就越好**。 不過，有時低 R 平方值 (例如 0.50) 可能完全正常或適合您的情節，而高 R 平方值不一定良好且值得懷疑。 |
| **絕對損失** |  [絕對損失](https://en.wikipedia.org/wiki/Mean_absolute_error)或「平均絕對誤差 (MAE)」測量預測與實際結果有多接近。 它是所有模型誤差的平均，其中模型誤差係指所預測標籤值與正確標籤值之間的絕對差。 此預測誤差是針對每個記錄到的測試資料集計算而來。 最後，會針對所有記錄到的絕對誤差，計算其平均值。| **越接近 0.00，品質就越好。** 請注意，平均絕對誤差使用與所測量資料相同的標尺 (不會正規化為特定範圍)。 只有模型屬於相同資料集或標籤值分佈類似的資料集時，才能使用絕對損失、平方損失和 RMS 損失在這些模型之間進行比較。 |
| **平方損失** |  [平方損失](https://en.wikipedia.org/wiki/Mean_squared_error)或「均方誤差 (MSE)」(也稱為「均方差 (MSD)」) 可告訴您迴歸線與一組測試資料值有多接近。 做法是計算點到迴歸線的距離 (這些距離即為「誤差」(E))，然後求其平方。 平方會提供較多權數給較大的偏差。 | 它一律是非負數，且**值越接近 0.00 越好**。 視您的資料而定，可能無法取得非常小的均方誤差值。|
| **RMS 損失** |  [RMS 損失](https://en.wikipedia.org/wiki/Root-mean-square_deviation)或「均方根誤差 (RMSE)」(也稱為「均方根差 (RMSD)」) 可測量模型預測值與建立模型的環境中實際觀察值之間的偏差。 RMS 損失是平方損失的平方根，並具有相同的單位作為標籤，類似於絕對損失，但提供較多的權數給較大的偏差。 均方根誤差常用於氣候學、預測和迴歸分析來驗證實驗結果。 | 它一律是非負數，且**值越接近 0.00 越好**。 RMSD 是準確度量值，用於比較特定資料集 (而非資料集之間) 不同模型的預測誤差，因為它會視標尺而定。|

如需迴歸計量的進一步詳細資訊，請閱讀下列文章：

- [Regression Analysis:How Do I Interpret R-squared and Assess the Goodness-of-Fit?](https://blog.minitab.com/blog/adventures-in-statistics-2/regression-analysis-how-do-i-interpret-r-squared-and-assess-the-goodness-of-fit) (迴歸分析：如何解譯 R 平方和評定擬合優度？)
- [How To Interpret R-squared in Regression Analysis](https://statisticsbyjim.com/regression/interpret-r-squared-regression) (如何解譯迴歸分析中的 R 平方)
- [R-Squared Definition](https://www.investopedia.com/terms/r/r-squared.asp) (R 平方定義)
- [Mean Squared Error Definition](https://www.statisticshowto.datasciencecentral.com/mean-squared-error/) (均方誤差定義)
- [What are Mean Squared Error and Root Mean Squared Error?](https://www.vernier.com/til/1014/) (什麼是均方誤差和均方根誤差？)
