---
title: 什麼是模型建立器且其如何運作？
description: 如何使用 ML.NET 模型建立器來自動定型機器學習服務模型
author: natke
ms.date: 08/07/2019
ms.custom: overview
ms.openlocfilehash: a871c3a3751a93bdf0104c873215b164616f0664
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69611460"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a>什麼是模型建立器且其如何運作？

ML.NET 模型建立器是直覺式圖形化 Visual Studio 延伸模組，其用於建置、定型和部署自訂機器學習模型。

模型建立器會使用自動化的機器學習服務 (AutoML) 來探索不同機器學習服務演算法和設定，協助您找出最適合您案例的組合。

您不需要有機器學習專業知識也能使用模型建立器。 您只需要一些資料和待解決的問題。 模型建立器會產生程式碼，將模型新增至您的 .NET 應用程式。

![模型建立器 Visual Studio 延伸模組使用者介面動畫](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> 模型建立器目前為預覽版。

## <a name="scenarios"></a>案例

您可以在模型建立器中放入許多不同的案例，以產生應用程式的機器學習模型。

案例是您想要使用資料進行的預測類型描述。 例如：
- 根據歷史銷售資料預測未來的產品銷售量
- 根據客戶評論將人氣分類為正面或負面
- 偵測銀行交易是否為詐騙
- 將客戶意見反應問題路由至公司的正確小組

## <a name="choose-a-model-type"></a>選擇模型類型

在模型建立器中，您需要選取機器學習模型類型。 模型類型取決於您嘗試進行的預測類型。

在預測數字的案例中，機器學習模型類型稱為`regression`。

在預測類別的案例中，模型類型為 `classification`。 分類有兩種類型：
- 其中只有 2 個類別：`binary classification`。
- 其中有三個或多個類別：`multiclass classification`。

### <a name="which-model-type-is-right-for-me"></a>哪一種模型類型適合我？

#### <a name="predict-a-category-when-there-are-only-two-categories"></a>預測類別 (當只有兩個類別時)

二元分類用來將資料分類為兩個類別 (是/否、通過/失敗、true/false、正/負)。

![顯示二元分類範例的圖表，包括詐騙偵測、風險降低和應用程式檢測](media/binary-classification-examples.png)

情感分析可用來預測客戶意見反應的正面或負面人氣。 這是二元分類模型類型的範例。

如果您的案例需要分類成兩種類別，您可以使用此範本處理您的資料集。

#### <a name="predict-a-category-when-there-are-three-or-more-categories"></a>預測類別 (當有三個或多個類別時)

多元分類可用來將資料分類為三或多個類別。 

![多元分類的範例，包括文件和產品分類、支援票證路由，以及客戶問題優先順序](media/multiclass-classification-examples.png)

問題分類可使用問題標題和描述來分類客戶意見反應問題 (例如，針對 GitHub)。 這是多元分類模型類型的範例。

如果您想要將資料分類為三或多個類別，您可以使用問題分類範本處理您的案例。

#### <a name="predict-a-number"></a>預測數字

迴歸用來預測數字。

![顯示迴歸範例的圖表，例如價格預測、銷售預測和預測性維護](media/regression-examples.png)

價格預測可使用位置、大小和其他房屋特性來預測房價。 這是迴歸模型類型的範例。

如果您想要使用自己的資料集來預測數值，針對您的案例您可以使用價格預測範本。

#### <a name="custom-scenario-choose-your-model-type"></a>自訂案例 (選擇您的模型類型)

自訂案例可讓您手動選擇模型類型。

## <a name="data"></a>資料

一旦選擇了模型類型，模型建立器就會要求您提供資料集。 資料用來定型、評估及選擇最適合您案例的模型。

![顯示模型建立器步驟的圖表](media/model-builder-steps.png)

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

|情節|模型類型|資料|標籤|功能|
|-|-|-|-|-|
|價格預測|迴歸|[計程車費用資料](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|費用|行車時間、距離|
|異常偵測|二進位分類|[產品銷售資料](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|產品銷售|月份|
|情感分析|二進位分類|[網站留言資料](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|標籤 (負面人氣時為 0，正面人氣時為 1)|留言、年度|
|詐騙偵測|二進位分類|[信用卡資料](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|類別 (詐騙時為 1，否則為 0)|數量、V1-V28 (匿名特性)|
|文字分類|多元分類|[GitHub 問題資料](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|區域圖|標題、描述|

## <a name="train"></a>定型

一旦選取案例、資料和標籤，模型建立器就會定型模型。

### <a name="what-is-training"></a>什麼是定型？

定型模型建立器用來教導模型如何回答案例問題的自動化程序。 一旦定型，模型就可以使用之前未見過的輸入資料來建立預測。 例如，如果您要預測房價且有新屋上市，您就可以預測其銷售價格。

因為模型建立器使用自動化的機器學習服務 (AutoML)，所以它不需要任何輸入，也不需要您在定型期間調整。

## <a name="evaluate"></a>評估

評估是使用定型模型以新測試資料來建立預測，然後測量預測有多準確的程序。

模型建立器會將定型資料分割為定型集和測試集。 定型資料 (80%) 用來定型模型，而測試資料 (20%) 則保留用於評估模型。 模型建立器使用計量來測量模型的完善程度。 所使用的特定計量會視模型類型而定。 如需詳細資訊，請參閱[模型評估計量](resources/metrics.md)。

## <a name="improve"></a>改善

如果您的模型效能分數不如預期，您可以：

* 延長定型時間。 時間較長，自動化的機器學習引擎就會嘗試更多演算法及設定。

* 新增更多資料。 有時資料數量不足，無法定型高品質的機器學習模型。

* 平衡資料。 針對分類工作，請務必平衡所有類別的定型集。 例如，如果您有四個類別的 100 個定型範例，有 90 筆記錄使用前兩個類別 (tag1 和 tag2)，只有剩餘的 10 筆記錄使用其他兩個類別 (tag3 和 tag4)，則資料失衡可能會導致模型難以正確預測 tag3 或 tag4。

## <a name="code"></a>程式碼

在評估階段後，模型建立器會輸出模型檔案，以及可用來將模型新增至應用程式的程式碼。 ML.NET 模型會儲存為 ZIP 檔案。 載入並使用模型的程式碼會新增為解決方案中新專案。 模型建立器也會新增範例主控台應用程式，您可以執行它以查看運行的模型。

此外，模型建立器會輸出產生模型的程式碼，以便您可以了解產生模型所用的步驟。 您也可以使用模型定型程式碼以新資料重新定型模型。

## <a name="whats-next"></a>後續步驟

[安裝](how-to-guides/install-model-builder.md)模型建立器 Visual Studio 延伸模組

請嘗試[價格預測或任何迴歸案例](tutorials/predict-prices-with-model-builder.md)
