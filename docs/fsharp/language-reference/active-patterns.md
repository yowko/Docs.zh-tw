---
title: 現用模式
description: 瞭解如何使用現用模式來定義以程式F#設計語言細分輸入資料的命名分割區。
ms.date: 05/16/2016
ms.openlocfilehash: 0c1315f2386b3cea2def698f4725e4c1cf030609
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083086"
---
# <a name="active-patterns"></a>現用模式

*現用模式*可讓您定義用來細分輸入資料的命名分割，如此一來，您就可以在模式比對運算式中使用這些名稱，就像您針對區分聯集所做的一樣。 您可以使用作用中的模式，以自訂方式分解每個部分的資料。

## <a name="syntax"></a>語法

```fsharp
// Active pattern of one choice.
let (|identifier|) [arguments] valueToMatch= expression

// Active Pattern with multiple choices.
// Uses a FSharp.Core.Choice<_,...,_> based on the number of case names. In F#, the limitation n <= 7 applies.
let (|identifer1|identifier2|...|) valueToMatch = expression

// Partial active pattern definition.
// Uses a FSharp.Core.option<_> to represent if the type is satisfied at the call site.
let (|identifier|_|) [arguments ] valueToMatch = expression
```

## <a name="remarks"></a>備註

在先前的語法中，識別碼是以*引數*表示之輸入資料的資料分割名稱，換句話說，是引數的所有值集合的子集名稱。 現用模式定義中最多可以有七個數據分割。 *運算式*描述要將資料分解成的表單。 您可以使用現用模式定義來定義規則，以判斷指定為引數的值屬於哪些已命名的分割區。 （| 和 |）符號稱為*香蕉剪輯*，而這種類型的 let 系結所建立的函式稱為作用中辨識*器*。

例如，請考慮下列具有引數的現用模式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

您可以使用模式比對運算式中的現用模式，如下列範例所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

此程式的輸出如下所示：

```console
7 is odd
11 is odd
32 is even
```

使用中模式的另一種用法是以多種方式分解資料類型，例如，當相同的基礎資料有各種可能的標記法時。 例如， `Color`物件可能會分解成 RGB 標記法或 HSB 標記法。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

上述程式的輸出如下所示：

```console
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

結合使用現用模式時，這兩種方式可讓您將資料分割和分解成適當的形式，並針對計算最方便的形式，在適當的資料上執行適當的計算。

產生的模式比對運算式可讓您以方便閱讀的方式寫入資料，大幅簡化可能複雜的分支和資料分析程式碼。

## <a name="partial-active-patterns"></a>部分現用模式

有時候，您只需要分割部分的輸入空間。 在這種情況下，您會撰寫一組符合某些輸入但無法符合其他輸入的部分模式。 不一定會產生值的現用模式稱為「*部分現用模式*」;它們具有屬於選項類型的傳回值。 若要定義部分現用模式，請在香蕉剪輯內的\_模式清單結尾使用萬用字元（）。 下列程式碼說明如何使用部分現用模式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

上一個範例的輸出如下所示：

```console
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

使用部分現用模式時，有時個別的選擇可能不相鄰或互斥，但它們不需要。 在下列範例中，模式正方形和模式 Cube 不是連續的，因為有些數位同時為正方形和 cube，例如64。 下列程式會使用和模式來結合正方形和 Cube 模式。 它會列印出最多1000的所有整數，其中同時為正方形和 cube，以及僅為 cube。 

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

其輸出如下：

```console
1 is a cube and a square
8 is a cube
27 is a cube
64 is a cube and a square
125 is a cube
216 is a cube
343 is a cube
512 is a cube
729 is a cube and a square
1000 is a cube
```

## <a name="parameterized-active-patterns"></a>參數化現用模式

現用模式一律會針對要比對的專案使用至少一個引數，但它們也可能會採用其他引數，在此情況下，會套用*參數化現用模式*的名稱。 其他引數可讓一般模式特製化。 例如，使用正則運算式來剖析字串的現用模式通常會包含正則運算式做為額外的參數，如下列程式碼所示，這也會使用`Integer`先前程式碼範例中定義的部分現用模式。 在此範例中，會提供使用適用于各種日期格式之正則運算式的字串，以自訂一般 ParseRegex 現用模式。 整數現用模式是用來將相符的字串轉換成可傳遞至 DateTime 函數的整數。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

先前程式碼的輸出如下所示：

```console
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

現用模式不限於模式比對運算式，您也可以在 let-系結上使用它們。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

先前程式碼的輸出如下所示：

```console
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [比對運算式](match-expressions.md)
