---
title: 機器學習工作
description: 探索 ML.NET 中支援的各種不同機器學習工作。
ms.date: 06/04/2018
author: aditidugar
ms.author: johalex
ms.openlocfilehash: 22249ac2d275a4168dbd8b03b90d9698fe90f2d1
ms.sourcegitcommit: d8bf4976eafe3289275be3811e7cb721bfff7e1e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34860639"
---
# <a name="machine-learning-tasks"></a>機器學習工作

建置機器學習模型時，您必須先定義希望利用資料來達成的目標。 之後，就可以挑選適合您情況的機器學習工作。 以下清單描述可供您選擇的各種不同機器學習工作，以及一些常見的使用案例。 

> [!NOTE]
> ML.NET 目前為預覽版。 目前並非所有機器學習工作都受到支援。 若要提交特定工作的要求，請在 [dotnet/machinelearning 存放庫](https://github.com/dotnet/machinelearning/issues)中開啟一個問題。

> [!NOTE]
> 目前，ML.NET 不支援含有影像的機器學習工作。 在未來的版本中將會新增支援。 

## <a name="binary-classification"></a>二元分類

這是一個[監督式機器學習](glossary.md#supervised-machine-learning)工作，可用來預測資料執行個體屬於兩個類別 (分類) 中的哪一個。 分類演算法的輸入是一組已加上標籤的範例，其中每個標籤都是 0 或 1 的整數。 二元分類演算法的輸出是一個分類器，可供您用來預測未加標籤之新執行個體的類別。 二元分類案例的範例包括：

* [理解 Twitter 評論的情感](../tutorials/sentiment-analysis.md)是「正面」還是「負面」。
* 診斷病患是否有某種疾病。
* 決定是否要將電子郵件標示為「垃圾郵件」。

## <a name="multi-class-classification"></a>多元分類

這是一個[監督式機器學習](glossary.md#supervised-machine-learning)工作，可用來預測資料執行個體的類別 (分類)。 分類演算法的輸入是一組已加上標籤的範例。 每個標籤都是介於 0 到 k-1 的整數，其中 k 是類別數。 分類演算法的輸出是一個分類器，可供您用來預測未加標籤之新執行個體的類別。 多元分類案例的範例包括：

* 判斷狗的品種，例如「西伯利亞哈士奇」、「黃金獵犬」、「貴賓狗」等。
* 理解影片評論是「正面」、「中立」還是「負面」。
* 將飯店評論分類成「地點」、「價格」、「整潔度」等。

## <a name="regression"></a>迴歸

這是一個[監督式機器學習](glossary.md#supervised-machine-learning)工作，可用來從一組相關的特徵預測標籤的值。 標籤可以有任何實際值，而不像在分類工作中那樣來自一組有限的值。 迴歸演算法會根據標籤的相關特徵建立標籤的相依性模型，以決定標籤會隨著特徵值的變化如何變更。 迴歸演算法的輸入是一組標籤為已知值的範例。 迴歸演算法的輸出是一個函式，可供您用來預測任何一組新輸入特徵的標籤值。 迴歸案例的範例包括：

* 根據房屋屬性 (例如房間數、地點、大小) 預測房價。
* 根據歷程記錄資料和目前的市場趨勢預測未來的股價。
* 根據廣告預算預測產品銷售額。

> [!NOTE]
> 目前，ML.NET 仍在為涉及時間序列的迴歸工作建立支援。

## <a name="clustering"></a>群集

這是一個[非監督式機器學習](glossary.md#unsupervised-machine-learning)工作，可用來將資料執行個體組成包含類似特性的群集。 群集也可用來在資料集內，識別您無法藉由瀏覽或簡單觀察以邏輯方式導出的關係。 群集演算法的輸入和輸出取決於所選擇的方法。 您可以採用以分佈、距心、連線或密度為基礎的方法。 ML.NET 目前支援使用 K 平均 (K-Means) 群集的距心型方法。 群集案例的範例包括：

* 根據選擇飯店時的習慣和特性，理解飯店賓客的區隔。
* 識別客戶區隔和人口統計，以協助建立目標性廣告活動。
* 根據製造計量來分類庫存。

## <a name="anomaly-detection-coming-soon"></a>異常偵測 (*即將推出*)

## <a name="ranking-coming-soon"></a>排名 (*即將推出*)

## <a name="recommendation-coming-soon"></a>建議 (*即將推出*)

