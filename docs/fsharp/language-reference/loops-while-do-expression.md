---
title: 迴圈：while...do 運算式 (F#)
description: 請參閱如何時...執行運算式用來執行反覆執行 （迴圈），而指定的測試條件為 true。
ms.date: 05/16/2016
ms.openlocfilehash: 5cf4461669221f91cb50e238c25494f03a10bbc2
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44208502"
---
# <a name="loops-whiledo-expression"></a>迴圈：while...do 運算式

`while...do`運算式用來執行反覆執行 （迴圈），而指定的測試條件為 true。

## <a name="syntax"></a>語法

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a>備註

*測試運算式*評估; 如果`true`，則*主體運算式*執行和測試運算式會評估一次。 *主體運算式*型別必須`unit`。 如果測試運算式`false`，反覆項目結束。

下列範例示範如何將`while...do`運算式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

先前的程式碼的輸出是介於 1 到 20 之間的隨機數字的資料流的最後一個為 10。

```
13 19 8 18 16 2 10
Found a 10!
```

>[!NOTE]
您可以使用`while...do`循序項運算式和其他計算的運算式，在此情況下的自訂的版本`while...do`運算式的使用方式。 如需詳細資訊，請參閱 <<c0> [ 序列](sequences.md)，[非同步工作流程](asynchronous-workflows.md)，並[計算運算式](computation-expressions.md)。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [迴圈：`for...in` 運算式](loops-for-in-expression.md)
- [迴圈：`for...to` 運算式](loops-for-to-expression.md)
