---
title: "迴圈：while...do 運算式 (F#)"
description: "請參閱如何時...執行運算式用來執行 （迴圈） 的反覆執行，而指定的測試條件為 true。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 0416ffca-7ed9-4aff-9493-e001fdba8c9b
ms.openlocfilehash: 5f10fda84a5e748856eb7b2c63ad46cc1fba44bb
ms.sourcegitcommit: 8ed4ebc15b5ef89d06a7507dc9d5e306e30accf7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2017
---
# <a name="loops-whiledo-expression"></a>迴圈：while...do 運算式

`while...do`運算式用來執行 （迴圈） 的反覆執行，而指定的測試條件為 true。


## <a name="syntax"></a>語法

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a>備註
*測試運算式*評估; 如果它是`true`、*主體運算式*執行和測試運算式會評估一次。 *主體運算式*型別必須`unit`。 如果測試運算式`false`，在反覆項目結束。

下列範例說明使用`while...do`運算式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

先前的程式碼的輸出是介於 1 到 20 之間的隨機數字的資料流的最後一個為 10。

```
13 19 8 18 16 2 10
Found a 10!
```

>[!NOTE] 
您可以使用`while...do`在循序項運算式和其他計算的運算式，在此情況下的自訂的版本`while...do`運算式使用。 如需詳細資訊，請參閱[序列](sequences.md)，[非同步工作流程](asynchronous-workflows.md)，和[計算運算式](computation-expressions.md)。


## <a name="see-also"></a>另請參閱
[F# 語言參考](index.md)

[迴圈：`for...in` 運算式](loops-for-in-expression.md)

[迴圈：`for...to` 運算式](loops-for-to-expression.md)
