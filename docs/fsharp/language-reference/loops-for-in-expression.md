---
title: "迴圈：for...in 運算式 (F#)"
description: "請參閱如何 F # for...in..運算式中迴圈建構用來反覆查看的可列舉集合中的模式比對。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f54e3228-4aec-4d0a-ae37-bc3376508284
ms.openlocfilehash: d86aeb3bdd975261e59004d636354a740bd95c47
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="loops-forin-expression"></a>迴圈：for...in 運算式

此迴圈建構用來反覆查看的可列舉集合，例如範圍運算式、 序列、 清單、 陣列或其他支援列舉的建構中的某個模式的相符項目。


## <a name="syntax"></a>語法

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a>備註
`for...in`運算式可以相較於`for each`其他.NET 語言中的陳述式因為它用來循環的可列舉集合中的值。 不過，`for...in`也支援整個集合，而不是只是反覆項目集合上比對的模式。

可列舉的運算式可以指定成可列舉集合，或使用`..`運算子，為整數類型的範圍。 可列舉集合包括清單、 序列、 陣列、 集合、 對應等等。 實作的任何類型`System.Collections.IEnumerable`可用。

當您使用 express 範圍`..`運算子，您可以使用下列語法。

*啟動*... *[完成]*

您也可以使用包含呼叫遞增值的版本*略過*，在下列程式碼中。

*啟動*... *略過*... *[完成]*

當您使用整數類資料的範圍和簡單的計數器變數作為模式時，問題通常是在每個反覆項目，以 1 遞增計數器變數，但如果範圍包含略過值時，此計數器會遞增略過值改為。

在模式比對的值也可用在本文的運算式。

下列程式碼範例說明使用`for...in`運算式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

輸出如下。

```
1
5
100
450
788
```

下列範例示範如何迴圈時的順序，以及如何使用 tuple 模式，而不是簡單的變數。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5202.fs)]

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

下列範例會示範如何在迴圈的一個簡單的整數範圍內。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

Function1 的輸出如下所示。

```
1 2 3 4 5 6 7 8 9 10
```

下列範例會示範如何使用 skip 2，其中包含的範圍的項目範圍內執行迴圈。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

輸出`function2`如下所示。

```
1 3 5 7 9
```

下列範例會示範如何使用的字元範圍。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

輸出`function3`如下所示。

```
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

下列範例會示範如何使用反向反覆項目中的負 skip 值。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

輸出`function4`如下所示。

```
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

開頭和結尾範圍也可以是運算式，例如函式，如下列程式碼所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

輸出`function5`與這個輸入如下所示。

```
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

項目不需要在迴圈中時下, 一個範例顯示使用萬用字元字元 (_)。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

輸出如下。

```
Number of elements in list1: 5
```

`Note`您可以使用`for...in`在循序項運算式和其他計算的運算式，在此情況下的自訂的版本`for...in`運算式使用。 如需詳細資訊，請參閱[序列](sequences.md)，[非同步工作流程](asynchronous-workflows.md)，和[計算運算式](computation-expressions.md)。


## <a name="see-also"></a>另請參閱
[F# 語言參考](index.md)

[迴圈：`for...to` 運算式](loops-for-to-expression.md)

[迴圈：`while...do` 運算式](loops-while-do-expression.md)
