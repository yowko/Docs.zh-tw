---
title: 什麼是模型建立器且其如何運作？
description: 如何使用 ML.NET 模型建立器來自動定型機器學習服務模型
author: natke
ms.date: 06/26/2019
ms.custom: overview
ms.openlocfilehash: 6049db79753986544de18faebfd047aa190af153
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539792"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a>什麼是模型建立器且其如何運作？

ML.NET 模型建立器是易於了解的圖形化 Visual Studio 延伸模組，其用於建置、定型和部署自訂機器學習模型。

模型建立器會使用自動化的機器學習服務 (AutoML) 來探索不同機器學習服務演算法和設定，協助您找出最適合您案例的組合。

您不需要有機器學習專業知識也能使用模型建立器。 您只需要一些資料和待解決的問題。 模型建立器會產生程式碼，將模型新增至您的 .NET 應用程式。

![模型建立器 Visual Studio 延伸模組使用者介面動畫](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> 模型建立器目前為預覽版。

## <a name="scenarios"></a>案例

您可以在模型建立器中放入許多不同的案例，以產生應用程式的機器學習模型。

案例是您希望用資料建立的預測型別描述。 例如：
- 根據歷史銷售資料預測未來的產品銷售量
- 根據客戶評論將人氣分類為正面或負面
- 偵測銀行交易是否為詐騙
- 將客戶意見反應問題路由至公司的正確小組

在模型建立器中，您需要將您的案例對應到 [ML.NET 工作](resources/tasks.md)。 您可以使用模型建立器處理**迴歸** (預測數字) 和**分類** (預測類別)。

### <a name="which-machine-learning-scenario-is-right-for-me"></a>哪種機器學習服務案例適合我？

模型建立器附有情感分析、問題分類、價格預測和自訂案例的範本。 這些範本可以作為特定 ML.NET 案例的起點使用。

#### <a name="sentiment-analysis-binary-classification"></a>情感分析 (二元分類)

情感分析可用來預測客戶意見反應的正面或負面人氣。 這是二元分類工作的範例。

二元分類用來將資料分類為兩種類別 (是/否、通過/失敗、true/false、正/負)。 它可用來回答下列問題：

- 此電子郵件是垃圾郵件嗎？ (垃圾郵件偵測)
- 哪些申請者符合成員資格？ (申請篩選)
- 哪些帳戶可能不會準時付款？ (風險降低)
- 此信用卡交易為詐騙嗎？ (詐騙偵測)

如果您的案例需要分類成兩種類別，您可以使用此範本處理您的資料集。

#### <a name="issue-classification-multiclass-classification"></a>問題分類 (多元分類)

問題分類可使用問題標題和描述來分類客戶意見反應問題 (例如，針對 GitHub)。 這是多元分類工作的範例。

多元分類可用來將資料分類為三或多個類別。 它可用來回答下列問題：

- 我該將支援票證路由到哪個部門？ (路由支援票證)
- 客戶問題的優先順序為何？ (客戶問題的優先順序)
- 產品屬於哪個類別？ (產品分類)
- 哪種文件？ (文件/電子郵件分類)

如果您想要將資料分類為三或多個類別，您可以使用問題分類範本處理您的案例。

#### <a name="price-prediction-regression"></a>價格預測 (迴歸)

價格預測可使用位置、大小和其他房屋特性來預測房價。 它是迴歸工作的範例。

迴歸用來預測數字。 它可用來回答下列問題：

- 房屋的售價為何？ (價格預測)
- 機械組件多久之後需要維修？ (預測性維護)
- 此乾燥機的含水量為何？ (機器監視)
- 此區域的年度總銷售額為何？ (銷售預測)

如果您想要使用自己的資料集來預測數值，針對您的案例您可以使用價格預測範本。

#### <a name="custom-scenario-choose-your-task"></a>自訂案例 (選擇您的工作)

自訂案例可讓您選擇自己的工作。 挑選最能處理問題的案例。

自訂案例可讓您選擇自己的機器學習服務工作。 在前面的範本中，機器學習服務工作已固定為以下案例︰二元分類、多元分類或迴歸。 在此範本中，您可以選擇您想要用在您資料上的 ML 工作。

## <a name="data"></a>資料

一旦案例對應到工作，模型建立器就會要求您提供資料集。 資料用來定型、評估及選擇最適合您案例的模型。 您也需要選擇您想要預測的輸出。

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

### <a name="data-formats"></a>資料格式

模型建立器對資料有下列限制：

- 資料必須儲存在檔案 (有標頭資料列的 .csv 或 .tsv) 或 SQL Server 資料庫中。
- 定型資料集的限制為 1 GB
- SQL Server 的定型上限為 100,000 筆資料列
- SQL Server 資料會在定型前從伺服器複製到您的本機電腦

### <a name="example-datasets"></a>範例資料集

如果您還沒有自己的資料，請嘗試下列資料集之一：

|情節|ML 工作|資料|標籤|功能|
|-|-|-|-|-|
|價格預測|迴歸|[計程車費用資料](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|費用|行車時間、距離|
|異常偵測|二進位分類|[產品銷售資料](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|產品銷售|月份|
|情感分析|二進位分類|[網站留言資料](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_SentimentAnalysis/SentimentAnalysis/Data/wikiDetoxAnnotated40kRows.tsv)|標籤 (負面人氣時為 0，正面人氣時為 1)|留言、年度|
|詐騙偵測|二進位分類|[信用卡資料](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|類別 (詐騙時為 1，否則為 0)|數量、V1-V28 (匿名特性)|
|文字分類|多元分類|[GitHub 問題資料](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|區域圖|標題、描述|

## <a name="train"></a>定型

一旦選取案例、資料和標籤，模型建立器就會定型模型。

### <a name="what-is-training"></a>什麼是定型？

定型模型建立器用來教導模型如何回答案例問題的自動化程序。 一旦定型，模型就可以使用之前未見過的輸入資料來建立預測。 例如，如果您要預測房價且有新屋上市，您就可以預測其銷售價格。

因為模型建立器使用自動化的機器學習服務 (AutoML)，所以它不需要任何輸入，也不需要您在定型期間調整。

### <a name="how-long-should-i-train-for"></a>定型時間應該多長？

您可以提供定型時間。 一般情況下，定型時間愈長，就會產生愈精確的模型。 當定型資料集的大小增加時，也會需要更長的定型時間。 下表提供增加資料集大小的一些定型時間指導方針。

資料集大小  | 資料集型別       | Avg.定型時間
------------- | ------------------ | --------------
0 - 10 MB     | 數值和文字   | 10 秒
10 - 100 MB   | 數值和文字   | 10 分鐘
100 - 500 MB  | 數值和文字   | 30 分鐘
500 - 1 GB    | 數值和文字   | 60 分鐘
1 GB+         | 數值和文字   | 3 小時以上

定型的確切時間也取決於：

- 資料行的型別，文字或數值
- 機器學習服務工作的型別 (迴歸或分類)
- 用於定型的資料列數目
- 用於定型的特性資料行數目

模型建立器已通過 1-TB 資料集的縮放測試，但建置此大小資料集的高品質模型最多可能耗時四天！

## <a name="evaluate"></a>評估

評估是使用定型模型以新測試資料來建立預測，然後測量預測有多準確的程序。

模型建立器會將定型資料分割為定型集和測試集。 定型資料 (80%) 用來定型模型，而測試資料 (20%) 則保留用於評估模型。  用於評估的計量取決於 ML 工作。 如需詳細資訊，請參閱[模型評估計量](resources/metrics.md)。

### <a name="sentiment-analysis-binary-classification"></a>情感分析 (二元分類)

二元分類問題的預設計量為**精確度**。 精確度會定義模型對測試資料集建立的正確預測比例。 **越接近 100% 越好**。

其他回報計量，例如測量真陽性率和偽陽性率的 AUC (曲線下面積) 應大於 0.50 才是可以接受的模型。

其他計量，例如 F1 分數可用來控制精確度 (該類別總預測數的正確預測率) 與回收 (該類別實際成員總數的正確預測比例) 之間的平衡。

### <a name="issue-classification-multiclass-classification"></a>問題分類 (多元分類)

多元分類問題的預設計量是**微精確度**。 **越接近 100% 越好**。

資料分類成多個類別的問題有兩種精確度：

- 微精確度：所有執行個體的正確預測分數。 在問題分類案例中，微精確度是指派給正確類別的發生問題比例。
- 宏準確度：類別層級的平均準確度。 在問題分類案例中，會測量每個類別的精確度，然後平均分類的精確度。 針對此計量，所有類別都有相同的權重。 若為完美平衡的資料集 (即每個類別的範例數都相同)，微精確度和宏精確度相同。

### <a name="price-prediction-regression"></a>價格預測 (迴歸)

迴歸問題的預設計量為 **RSquared**。 1 是最可能的值。 RSquared 越接近 1，模型就越好。

其他回報計量，例如絕對損失、平方損失和 RMS 損失，都可以用來了解您的模型，並和其他迴歸模型比較。

## <a name="improve"></a>改善

如果您的模型效能分數不如預期，您可以：

* 延長定型時間。 時間較長，自動化的機器學習引擎就會嘗試更多演算法及設定。

* 新增更多資料。 有時資料數量不足，無法定型高品質的機器學習模型。

* 平衡資料。 針對分類工作，請務必平衡所有類別的定型集。 例如，如果您有四個類別的 100 個定型範例，有 90 筆記錄使用前兩個類別 (tag1 和 tag2)，只有剩餘的 10 筆記錄使用其他兩個類別 (tag3 和 tag4)，則資料失衡可能會導致模型難以正確預測 tag3 或 tag4。

## <a name="code"></a>程式碼

在評估階段後，模型建立器會輸出模型檔案，以及可用來將模型新增至應用程式的程式碼。 ML.NET 模型會儲存為 ZIP 檔案。 載入並使用模型的程式碼會新增為解決方案中新專案。 模型建立器也會新增範例主控台應用程式，您可以執行它以查看運行的模型。

此外，模型建立器會輸出產生模型的程式碼，以便您可以了解產生模型所用的步驟。 您也可以使用模型定型程式碼以新資料重新定型模型。

## <a name="whats-next"></a>後續步驟

請嘗試[價格預測或任何迴歸案例](tutorials/predict-prices-with-model-builder.md)
