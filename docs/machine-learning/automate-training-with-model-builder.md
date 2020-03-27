---
title: 什麼是模型建立器且其如何運作？
description: 如何使用 ML.NET 模型建立器來自動定型機器學習服務模型
ms.date: 03/25/2020
ms.custom: overview, mlnet-tooling
ms.openlocfilehash: 9cf66455109908ebd9fc10e62cf4f067609b57d9
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344778"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a>什麼是模型建立器且其如何運作？

ML.NET 模型建立器是直覺式圖形化 Visual Studio 延伸模組，其用於建置、定型和部署自訂機器學習模型。

模型建立器會使用自動化的機器學習服務 (AutoML) 來探索不同機器學習服務演算法和設定，協助您找出最適合您案例的組合。

您不需要有機器學習專業知識也能使用模型建立器。 您只需要一些資料和待解決的問題。 模型建立器會產生程式碼，將模型新增至您的 .NET 應用程式。

![模型建立器 Visual Studio 延伸模組使用者介面動畫](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> 模型產生器目前為預覽版。

## <a name="scenario"></a>狀況

您可以在模型建立器中放入許多不同的案例，以產生應用程式的機器學習模型。

案例是您想要使用資料進行的預測類型描述。 例如：

- 根據歷史銷售資料預測未來的產品銷售量
- 根據客戶評論將人氣分類為正面或負面
- 偵測銀行交易是否為詐騙
- 將客戶意見反應問題路由至公司的正確小組

### <a name="which-machine-learning-scenario-is-right-for-me"></a>哪種機器學習服務案例適合我？

在模型產生器中，您需要選擇方案。 方案的類型取決於您嘗試進行的預測類型。

#### <a name="text-classification"></a>文字分類

分類用於將資料分類為類別。

![顯示二元分類範例的圖表，包括詐騙偵測、風險降低和應用程式檢測](media/binary-classification-examples.png)

![多元分類的範例，包括文件和產品分類、支援票證路由，以及客戶問題優先順序](media/multiclass-classification-examples.png)

#### <a name="value-prediction"></a>價值預測

迴歸用來預測數字。

![顯示迴歸範例的圖表，例如價格預測、銷售預測和預測性維護](media/regression-examples.png)

#### <a name="image-classification"></a>影像分類

圖像分類可用於識別不同類別的圖像。 例如，不同類型的地形或動物或製造缺陷。

如果您有一組圖像，並且希望將圖像分類為不同的類別，則可以使用圖像分類方案。

#### <a name="recommendation"></a>建議

建議方案根據特定使用者的喜歡和不喜歡程度預測特定使用者的建議專案清單。

當您有一組使用者和一組"產品"（如要購買的專案、電影、書籍或電視節目）以及一組使用者的"評分"時，可以使用推薦方案。

## <a name="environment"></a>環境

您可以在電腦或 Azure 上的雲中本地訓練機器學習模型。

在本地訓練時，您可以在電腦資源（CPU、記憶體和磁片）的約束下工作。 在雲中訓練時，可以擴展資源以滿足方案的需求，尤其是大型資料集。

支援針對所有方案進行本地培訓。

支援映射分類的 Azure 培訓。

## <a name="data"></a>資料

選擇方案後，模型產生器要求您提供資料集。 資料用來定型、評估及選擇最適合您案例的模型。

![顯示模型建立器步驟的圖表](media/model-builder-steps.png)

模型產生器支援以 .tsv、.csv、.txt 格式以及 SQL 資料庫格式進行資料集。 如果您有 .txt 檔，則列應與`,`分隔，`;`或者`/t`該檔必須具有標頭行。

如果資料集由圖像組成，則支援的檔案類型為`.jpg`和`.png`。

有關詳細資訊，請參閱[將訓練資料載入到模型產生器](how-to-guides/load-data-model-builder.md)中。

### <a name="choose-the-output-to-predict-label"></a>選擇要預測的輸出 (標籤)

資料集是定型範例資料列和屬性資料行的資料表。 每個資料列都有：

- **標籤** (您想要預測的屬性)
- **特性** (作為輸入用來預測標籤的屬性)。

針對房價預測案例，可能的特性為：

- 房屋的坪數
- 房間和衛浴數量
- 郵遞區號

標籤是坪數列、房間和衛浴值，以及郵遞區號資料列的歷史房價。

![資料表顯示房價資料的資料列和資料行，具有大小、房間數、郵遞區號和價格標籤組成的特性](media/model-builder-data.png)

### <a name="example-datasets"></a>範例資料集

如果您還沒有自己的資料，請嘗試下列資料集之一：

|狀況|範例|資料|標籤|特性|
|-|-|-|-|-|
|分類|預測銷售異常|[產品銷售資料](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|產品銷售|Month|
||預測網站評論的情緒|[網站留言資料](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|標籤 (負面人氣時為 0，正面人氣時為 1)|留言、年度|
||預測欺詐性信用卡交易|[信用卡資料](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|類別 (詐騙時為 1，否則為 0)|數量、V1-V28 (匿名特性)|
||預測 GitHub 存儲庫中的問題類型|[GitHub 問題資料](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|區域|標題、描述|
|價值預測|預測出租車票價|[計程車費用資料](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|費用|行車時間、距離|
|影像分類|預測問題的類別|[花圖像](http://download.tensorflow.org/example_images/flower_photos.tgz)|花的類型：雛菊、蒲公英、玫瑰、向日葵、鬱金香|圖像資料本身|
|建議|預測某人喜歡的電影|[電影分級](http://files.grouplens.org/datasets/movielens/ml-latest-small.zip)|使用者， 電影|評等|

## <a name="train"></a>定型

一旦選取案例、資料和標籤，模型建立器就會定型模型。

### <a name="what-is-training"></a>什麼是定型？

定型模型建立器用來教導模型如何回答案例問題的自動化程序。 一旦定型，模型就可以使用之前未見過的輸入資料來建立預測。 例如，如果您要預測房價且有新屋上市，您就可以預測其銷售價格。

因為模型建立器使用自動化的機器學習服務 (AutoML)，所以它不需要任何輸入，也不需要您在定型期間調整。

### <a name="how-long-should-i-train-for"></a>定型時間應該多長？

模型產生器使用 AutoML 來探索多個模型，以找到性能最佳的模型。

較長的培訓時間允許 AutoML 探索更多具有更廣泛設置的型號。

下表總結了在本地電腦上為一組示例資料集獲得良好性能所佔用的平均時間。

|資料集大小|平均培訓時間|
|------------|---------------------|
|0 - 10 MB|10 秒|
|10 - 100 MB|10 分鐘|
|100 - 500 MB|30 分鐘|
|500 - 1 GB|60 分鐘|
|1 GB*|3 小時以上|

這些數位只是指南。 培訓的確切時間取決於：

- 用作模型輸入的要素（列）數
- 列的類型
- ML 任務
- 用於定型的機器的 CPU、磁片和記憶體性能

## <a name="evaluate"></a>評估

評估是測量模型有多好的過程。 模型產生器使用經過訓練的模型使用新的測試資料進行預測，然後測量預測有多好。

模型建立器會將定型資料分割為定型集和測試集。 定型資料 (80%) 用來定型模型，而測試資料 (20%) 則保留用於評估模型。

### <a name="how-do-i-understand-my-model-performance"></a>如何瞭解我的模型性能？

方案映射到機器學習任務。 每個 ML 任務都有自己的評估指標集。

#### <a name="value-prediction"></a>價值預測

值預測問題的預設指標為 RSquared，RSquared 的值介於 0 和 1 之間。 1 是最佳值，換句話說，RSquared 的值越接近 1，您的模型性能就越好。

報告的其他指標（如絕對損失、平方損失和 RMS 損失）是其他指標，可用於瞭解模型的性能並將其與其他值預測模型進行比較。

#### <a name="classification-2-categories"></a>分類（2個類別）

分類問題的預設指標是準確性。 準確性定義模型在測試資料集上進行的正確預測的比例。 接近 100% 或 1.0 越好。

報告的其他指標（如 AUC（曲線下的區域），用於測量真實正率與誤報率應大於 0.50，模型應為可接受。

其他指標（如 F1 分數）可用於控制精度和召回之間的平衡。

#### <a name="classification-3-categories"></a>分類（3+類別）

多類分類的預設指標是"微精度"。 微精度越接近 100% 或 1.0 越好。

多類分類的另一個重要指標是宏觀精度，與微精度相似，接近 1.0 越好。 思考這兩種類型的準確性的一個好方法是：

- 微精度：進票多久被分類到正確的團隊？
- 宏觀準確性：對於一般團隊，進貨票證對於其團隊來說多久是正確的？

### <a name="more-information-on-evaluation-metrics"></a>有關評估指標的詳細資訊

如需詳細資訊，請參閱[模型評估計量](resources/metrics.md)。

## <a name="improve"></a>改善

如果您的模型效能分數不如預期，您可以：

- 延長定型時間。 隨著更多的時間，自動化機器學習引擎實驗與更多的演算法和設置。

- 新增更多資料。 有時資料數量不足，無法定型高品質的機器學習模型。

- 平衡資料。 針對分類工作，請務必平衡所有類別的定型集。 例如，如果您有四個類別的 100 個定型範例，有 90 筆記錄使用前兩個類別 (tag1 和 tag2)，只有剩餘的 10 筆記錄使用其他兩個類別 (tag3 和 tag4)，則資料失衡可能會導致模型難以正確預測 tag3 或 tag4。

## <a name="code"></a>程式碼

在評估階段後，模型建立器會輸出模型檔案，以及可用來將模型新增至應用程式的程式碼。 ML.NET 模型會儲存為 ZIP 檔案。 載入並使用模型的程式碼會新增為解決方案中新專案。 模型建立器也會新增範例主控台應用程式，您可以執行它以查看運行的模型。

此外，模型建立器會輸出產生模型的程式碼，以便您可以了解產生模型所用的步驟。 您也可以使用模型定型程式碼以新資料重新定型模型。

## <a name="whats-next"></a>下一步

[安裝](how-to-guides/install-model-builder.md)模型建立器 Visual Studio 延伸模組

請嘗試[價格預測或任何迴歸案例](tutorials/predict-prices-with-model-builder.md)
