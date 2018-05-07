---
title: 遞迴函式：rec 關鍵字 (F#)
description: "了解如何 F # 'rec' 關鍵字使用 'let' 關鍵字來定義遞迴函式。"
ms.date: 05/16/2016
ms.openlocfilehash: 6039a48eae2b16aa1d82617176460d727a878d87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="recursive-functions-the-rec-keyword"></a>遞迴函式：rec 關鍵字

`rec`關鍵字會搭配`let`關鍵字來定義遞迴函式。


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
遞迴函式，呼叫本身，函式會明確地識別在 F # 語言中。 這讓正在定義的識別項使用的函式範圍中。

下列程式碼說明遞迴函式，會計算*n*個 Fibonacci 數字。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

>[!NOTE]
在實務上，類似的上述程式碼是不必要的記憶體和處理器時間，因為它牽涉到先前的計算值的重新計算。


方法都是隱含遞迴的類型; 內不需要新增`rec`關鍵字。 在類別中的 let 繫結沒有隱含地遞迴。


## <a name="mutually-recursive-functions"></a>相互遞迴函式
函式有時候是*相互遞迴*，這表示呼叫表單的其中一個函式呼叫另一個也就會呼叫第一個與任何數目的呼叫之間的圓形。 您必須同時定義這類函式，在一個`let`繫結，請使用`and`關鍵字來連結在一起。

下列範例示範兩個相互遞迴函式。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a>另請參閱
[函式](index.md)
