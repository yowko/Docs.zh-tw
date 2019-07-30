---
title: 迴圈：for...in 運算式
description: F#查看 .。。在運算式迴圈結構中, 是用來反復查看可列舉集合中的模式相符專案。
ms.date: 05/16/2016
ms.openlocfilehash: 640b0f91f6c641f3b49a99dc67abe7e4c31911ea
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630722"
---
# <a name="loops-forin-expression"></a>迴圈：for...in 運算式

這個迴圈結構是用來反復查看可列舉集合中的模式相符專案, 例如範圍運算式、序列、清單、陣列或其他支援列舉的結構。

## <a name="syntax"></a>語法

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a>備註

運算式可以與其他 .net 語言中`for each`的語句比較, 因為它是用來對可列舉集合中的值進行迴圈處理。 `for...in` 不過, `for...in`也支援在集合上進行模式比對, 而不只是在整個集合上反覆運算。

可列舉的運算式可以指定為可列舉集合, 或使用`..`運算子做為整數類型的範圍。 可列舉集合包含清單、序列、陣列、集合、對應等等。 `System.Collections.IEnumerable`可以使用任何可執行檔型別。

當您使用`..`運算子來表示範圍時, 您可以使用下列語法。

*啟動*。 *finish*

您也可以使用包含名為*skip*之遞增值的版本, 如下列程式碼所示。

*啟動*。 *略過*。 *finish*

當您使用整數範圍和簡單計數器變數做為模式時, 一般的行為是在每個反復專案上將計數器變數遞增 1, 但如果範圍包含 skip 值, 則會改由 skip 值來遞增計數器。

在此模式中符合的值也可以在主體運算式中使用。

下列程式碼範例說明`for...in`運算式的用法。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

輸出如下。

```
1
5
100
450
788
```

下列範例顯示如何在序列上執行迴圈, 以及如何使用元組模式, 而不是簡單變數。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5202.fs)]

輸出如下。

```
1 squared is 1
2 squared is 4
3 squared is 9
4 squared is 16
5 squared is 25
6 squared is 36
7 squared is 49
8 squared is 64
9 squared is 81
10 squared is 100
```

下列範例示範如何在簡單的整數範圍內執行迴圈。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

Function1 的輸出如下所示。

```
1 2 3 4 5 6 7 8 9 10
```

下列範例示範如何使用略過2的範圍來迴圈, 其中包括範圍的每個其他元素。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

的輸出`function2`如下所示。

```
1 3 5 7 9
```

下列範例顯示如何使用字元範圍。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

的輸出`function3`如下所示。

```
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

下列範例顯示如何使用反向反覆運算的負略過值。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

的輸出`function4`如下所示。

```
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

範圍的開始和結束也可以是運算式, 例如函式, 如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

`function5`具有此輸入的輸出如下所示。

```
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

下一個範例顯示當迴圈中不需要元素時\_, 使用萬用字元 ()。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

輸出如下。

```
Number of elements in list1: 5
```

`Note`您可以在`for...in`序列運算式和其他計算運算式中使用, 在此情況下會使用自`for...in`定義版本的運算式。 如需詳細資訊, 請參閱[序列](sequences.md)、[非同步工作流程](asynchronous-workflows.md)和[計算運算式](computation-expressions.md)。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [環回`for...to`運算式](loops-for-to-expression.md)
- [環回`while...do`運算式](loops-while-do-expression.md)
