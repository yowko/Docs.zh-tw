---
title: Boolean 運算子 (F#)
description: '深入了解 F # 程式語言中可用的布林運算子。'
ms.date: 05/16/2016
ms.openlocfilehash: f8516ceb531907400f98dc4226d2985d3119e9e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="boolean-operators"></a>Boolean 運算子

本主題說明在 F # 語言中布林運算子的支援。


## <a name="summary-of-boolean-operators"></a>布林運算子的摘要
下表摘要說明在 F # 語言中使用布林運算子。 唯一支援的這些運算子的類型是`bool`型別。

|運算子|描述|
|--------|-----------|
|`not`|布林值的否定|
|<code>&#124;&#124;</code>|布林值 OR|
|`&&`|布林值 AND|

布林值 AND 和 OR 運算子執行*最短路徑評估*，也就是評估運算子的右運算式只在必要時若要判斷整體運算式的結果。 第二個運算式的`&&`運算子會評估，只有第一個運算式評估為`true`; 的第二個運算式`||`運算子會評估，只有第一個運算式評估為`false`。

## <a name="see-also"></a>另請參閱
[位元運算子](bitwise-operators.md)

[算術運算子](arithmetic-operators.md)

[符號和運算子參考](index.md)
