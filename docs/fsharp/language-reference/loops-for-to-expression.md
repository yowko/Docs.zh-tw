---
title: 迴圈：for...to 運算式 (F#)
description: '請參閱如何 F # for...in...運算式用來在迴圈中逐一查看某個範圍的迴圈變數的值。'
ms.date: 05/16/2016
ms.openlocfilehash: 8160fd30c4f3afe8bb6b58f468802ef1c0ef32ee
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "43800465"
---
# <a name="loops-forto-expression"></a>迴圈：for...to 運算式

`for...to`運算式用來在迴圈中逐一查看某個範圍的迴圈變數的值。

## <a name="syntax"></a>語法

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a>備註

識別項型別推斷的型別*開始*並*完成*運算式。 這些運算式的類型必須是 32 位元整數。

雖然技術上的運算式，`for...to`則更像傳統的陳述式，在命令式程式設計語言。 傳回型別*主體運算式*必須是`unit`。 下列範例顯示的各種用法`for...to`運算式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

上述程式碼的輸出如下。

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [迴圈：`for...in` 運算式](loops-for-in-expression.md)
- [迴圈：`while...do` 運算式](loops-while-do-expression.md)
