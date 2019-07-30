---
title: 迴圈：while...do 運算式
description: 查看 while .。。當指定的測試條件為 true 時, 會使用 do expression 來執行反復執行 (迴圈)。
ms.date: 05/16/2016
ms.openlocfilehash: f05bdd9f8f4b9446d59f68e1231fb75e18e9b526
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630762"
---
# <a name="loops-whiledo-expression"></a>迴圈：while...do 運算式

當`while...do`指定的測試條件為 true 時, 會使用運算式來執行反復執行 (迴圈)。

## <a name="syntax"></a>語法

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a>備註

*測試運算式*會進行評估;如果為`true`, 則會執行本文*運算式*, 並再次評估測試運算式。 內文*運算式*的類型`unit`必須是。 如果測試運算式為, `false`則反復專案會結束。

下列範例說明`while...do`運算式的用法。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

先前程式碼的輸出是介於1到20之間的亂數字資料流程, 最後一個是10。

```
13 19 8 18 16 2 10
Found a 10!
```

> [!NOTE]
> 您可以在`while...do`序列運算式和其他計算運算式中使用, 在此情況下會使用自`while...do`定義版本的運算式。 如需詳細資訊, 請參閱[序列](sequences.md)、[非同步工作流程](asynchronous-workflows.md)和[計算運算式](computation-expressions.md)。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [環回`for...in`運算式](loops-for-in-expression.md)
- [環回`for...to`運算式](loops-for-to-expression.md)
