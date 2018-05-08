---
title: 作用中的模式 (F#)
description: '了解如何定義具名細分 F # 程式語言中的輸入的資料的資料分割使用作用中的模式。'
ms.date: 05/16/2016
ms.openlocfilehash: b8c3270b1efbeb3495ac69bf1217fddf8a5a73e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="active-patterns"></a>現用模式

*現用模式*讓您定義具名的資料分割細分輸入的資料，好讓您可以使用這些名稱在模式比對運算式一樣，差別等位的。 您可以使用作用中的模式，以自訂方式分解每個部分的資料。


## <a name="syntax"></a>語法

```fsharp
// Complete active pattern definition.
let (|identifer1|identifier2|...|) [ arguments ] = expression
// Partial active pattern definition.
let (|identifier|_|) [ arguments ] = expression
```

## <a name="remarks"></a>備註
在上一個語法中的識別項是輸入所表示之資料分割的名稱*引數*，或，也就是說，針對一組引數的所有值的子集的名稱。 現用模式定義中可以有最多七個資料分割。 *運算式*說明用來將資料分解成表單。 現用模式定義可用來定義規則，以判斷其中一個具名的資料分割指定為引數屬於的值。 (| 和 |) 的符號指*banana 短片*，這種類型的 let 繫結所建立的函式稱為*現用辨識器*。

例如，請考慮下列的現用模式的引數。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

您可以使用現用模式中的模式比對運算式，如下列範例所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

這個程式的輸出如下所示：

```
7 is odd
11 is odd
32 is even
```

現用模式的另一個用途是分解以多種方式，例如當相同的基礎資料有可能的各種表示相互轉換的資料類型。 例如，`Color`物件無法分解成代表的 RGB 或 HSB 表示法。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

上述程式的輸出如下所示：

```
Red
 Red: 255 Green: 0 Blue: 0
 Hue: 360.000000 Saturation: 1.000000 Brightness: 0.500000
Black
 Red: 0 Green: 0 Blue: 0
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.000000
White
 Red: 255 Green: 255 Blue: 255
 Hue: 0.000000 Saturation: 0.000000 Brightness: 1.000000
Gray
 Red: 128 Green: 128 Blue: 128
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.501961
BlanchedAlmond
 Red: 255 Green: 235 Blue: 205
 Hue: 36.000000 Saturation: 1.000000 Brightness: 0.901961
```

在組合，這兩種方式使用使用中模式的資料分割可讓您將資料分解成適當的表單並在最方便的計算表單中的適當資料上執行適當的計算。

產生的模式比對運算式啟用便利的方式，是很容易閱讀，大幅簡化的潛在的複雜分支 」 和 「 資料分析程式碼中撰寫的資料。


## <a name="partial-active-patterns"></a>部分現用模式
有時候，您需要資料分割中只有部分輸入的空間。 在此情況下，您撰寫一組部分模式，其中符合某些輸入，但無法比對其他輸入。 作用中永遠不會產生值的模式稱為*部分現用模式*; 它們具有傳回值的選項類型。 若要定義部分的現用模式，您可以使用萬用字元 (_) 內 banana 短片模式的清單結尾處。 下列程式碼說明如何使用部分的現用模式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

前一個範例的輸出如下所示：

```
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

當使用部分現用模式時，有時個別選擇可以脫離或互斥的但它們不需要是。 在下列範例中，模式平方和 Cube 的模式不是脫離的因為一些數字是平方和 cube，例如 64。 下列程式會列印出所有整數最多 1000000 的平方和 cube。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

其輸出如下：

```
1
64
729
4096
15625
46656
117649
262144
531441
1000000
```

## <a name="parameterized-active-patterns"></a>參數化的現用模式
作用中的模式都需要至少一個引數的項目相符，但它們可能需要其他引數，在此情況下名稱*參數化的現用模式*套用。 其他引數可讓一般模式將特製化。 例如，作用中的模式，可用於規則運算式剖析字串通常包含規則運算式做為額外的參數，如下列程式碼，也會使用部分現用模式`Integer`先前的程式碼範例中所定義。 在此範例中，使用規則運算式進行各種日期格式的字串給自訂一般 ParseRegex 現用模式。 整數現用模式用來比對的字串轉換為可以傳遞給 DateTime 建構函式的整數。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

先前的程式碼的輸出如下所示：

```
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

現用模式不只限於模式比對運算式，您也可以使用它們 let 繫結上。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

先前的程式碼的輸出如下所示：

```
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a>另請參閱
[F# 語言參考](index.md)

[比對運算式](match-expressions.md)

