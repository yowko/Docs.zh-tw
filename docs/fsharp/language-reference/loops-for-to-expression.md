---
title: 迴圈：for...to 運算式
description: F#查看 .。。to 運算式是用來在迴圈變數的值範圍內反復執行迴圈。
ms.date: 05/16/2016
ms.openlocfilehash: 882b6e48dd09efcb57f7ef2f419e68a6c43393a5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283908"
---
# <a name="loops-forto-expression"></a>迴圈：for...to 運算式

`for...to` 運算式是用來在迴圈變數的值範圍內反復執行迴圈。

## <a name="syntax"></a>語法

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a>備註

識別碼的型別是從*開始*和*完成*運算式的型別推斷而來。 這些運算式的類型必須是32位整數。

雖然在技術上是運算式，但 `for...to` 更像命令式程式設計語言中的傳統語句。 *主體運算式*的傳回類型必須是 `unit`。 下列範例示範 `for...to` 運算式的各種用法。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

上述程式碼的輸出如下。

```console
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a>請參閱

- [F# 語言參考](index.md)
- [迴圈：`for...in` 運算式](loops-for-in-expression.md)
- [迴圈：`while...do` 運算式](loops-while-do-expression.md)
