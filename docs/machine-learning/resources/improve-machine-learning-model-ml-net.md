---
title: 操作說明：改善模型正確性
description: 了解如何改善模型正確性
ms.date: 04/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc
ms.openlocfilehash: 8bb47102ede8e135090b1381eb815dccd512e03d
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557816"
---
# <a name="improve-mlnet-model-accuracy"></a>改善 ML.NET 模型正確性

了解如何改善模型的正確性。

## <a name="reframe-the-problem"></a>重構問題

有時候，改善模型可能與資料或用來定型模型的技巧無關。 可能只是問錯了問題。 請考慮從不同的角度看問題，並利用資料擷取潛在指標和隱藏的關聯性，以精簡問題。

## <a name="provide-more-data-samples"></a>提供更多的資料樣本

像人類一樣，得到的定型演算法愈多，愈可能提升效能。 提升模型效能的方法之一，是向演算法提供更多的定型資料樣本。 它學習的資料愈多，能夠正確識別的案例就愈多。

## <a name="add-context-to-the-data"></a>將內容新增至資料

單一資料點的意義很難解讀。 建置圍繞資料點的內容，有助於演算法以及主題專家做出更好的決策。 例如，房屋有三個臥房的事實，並不是很好的價格指標。 不過，如果您新增內容，且現在知道它位在主要都會區的郊區、平均年齡為 38、平均家庭收入為 80,000 USD、學校位列前百分之 20，則演算法就有較多的決策基礎資訊。 此內容全都可新增為機器學習模型的輸入特性。

## <a name="use-meaningful-data-and-features"></a>使用有意義的資料和特性

雖然更多資料樣本和特性有利於改善模型的正確性，但它們也可能帶入雜訊，因為並非所有的資料和特性都有意義。 因此，請務必了解哪些特性對演算法決策影響最大。 使用 Permutation Feature Importance (PFI) 等技巧，有利於識別這些主要特性，且不僅可協助說明模型，還可使用輸出作為特性選取方法，減少進入定型程序的雜訊特性量。

瀏覽下列[連結](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md)了解 PFI 用法

## <a name="cross-validation"></a>交叉驗證

交叉驗證是一種定型和模型評估技巧，會將資料分割成幾個分割，在這些分割上定型多個演算法。 這項技巧藉由定型程序提供的資料，改善模型的穩定性。 除了提升看不見的觀察值效能之外，在資料限制的環境中，它是使用較小資料集定型模型的有效工具。

請瀏覽下列連結，以了解[如何在 ML.NET 中使用交叉驗證](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md)

## <a name="hyperparameter-tuning"></a>超參數微調

定型機器學習模型是一種反覆探勘程序。 例如，什麼是使用 K-means 演算法定型模型時的最佳叢集數？ 答案取決於許多因素，例如資料的結構。 尋找該數字可能需要試驗不同的 k 值，然後評估效能以判斷哪個值是最佳的效能。 微調這些參數以找出最佳模型的做法，就是所謂的超參數微調。

## <a name="choose-a-different-algorithm"></a>選擇不同的演算法

迴歸和分類等機器學習工作，包含各種演算法實作。 可能是您嘗試解決的問題以及您的資料結構方式，不適合目前的演算法。 在此情況下，請考慮使用不同的演算法處理工作，看看它能否從您的資料學得更好。

下列連結提供更多[演算法選擇指引](../how-to-choose-an-ml-net-algorithm.md)。
