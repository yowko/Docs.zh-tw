---
title: 遞迴函式：rec 關鍵字 (F#)
description: "了解如何在 F # 'rec' 關鍵字使用 'let' 關鍵字定義遞迴函式。"
ms.date: 05/16/2016
ms.openlocfilehash: 5aab6ed8ab0fc3c0f0bcfc93c3ce6518ec53254f
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "48024515"
---
# <a name="recursive-functions-the-rec-keyword"></a>遞迴函式：rec 關鍵字

`rec`關鍵字可搭配使用`let`關鍵字來定義遞迴函式。

## <a name="syntax"></a>語法

```fsharp
// Recursive function:
let rec function-nameparameter-list =
function-body

// Mutually recursive functions:
let rec function1-nameparameter-list =
function1-body
and function2-nameparameter-list =
function2-body
...
```

## <a name="remarks"></a>備註

遞迴函式，呼叫本身的函式會明確地識別在 F # 語言中。 如此所定義的識別項可以在函式的範圍內。

下列程式碼說明遞迴函式來計算*n*<sup>th</sup> Fibonacci 數字。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

>[!NOTE]
在實務上，類似上述程式碼是浪費資源的記憶體和處理器時間，因為它牽涉到先前的計算值的重新計算。

方法為隱含型別; 中的遞迴不需要將`rec`關鍵字。 在類別中的 let 繫結不會隱含地遞迴。

## <a name="mutually-recursive-functions"></a>相互遞迴函式

函式的是有時*相互遞迴*，這表示呼叫表單的其中一個函式呼叫另一個會接著呼叫第一，使用任意多個呼叫之間的圓形。 您必須同時定義這類函式，在一個`let`繫結，使用`and`而連結在一起的關鍵字。

下列範例示範兩個相互遞迴函式。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a>另請參閱

- [函式](index.md)
