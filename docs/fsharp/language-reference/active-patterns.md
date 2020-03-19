---
title: 現用模式
description: 瞭解如何使用活動模式定義在 F# 程式設計語言中細分輸入資料的命名分區。
ms.date: 05/16/2016
ms.openlocfilehash: 898ef201369683bfd49d53e863e86f919f5837fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187064"
---
# <a name="active-patterns"></a>現用模式

*活動模式*使您能夠定義細分輸入資料的命名分區，以便可以在模式匹配運算式中使用這些名稱，就像對受歧視聯合一樣。 您可以使用作用中的模式，以自訂方式分解每個部分的資料。

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

在前面的語法中，識別碼是由*參數*表示的輸入資料分區的名稱，或者換句話說，是參數所有值集的子集的名稱。 活動模式定義中最多隻能有七個分區。 運算式*描述*要將資料分解到的表單。 可以使用活動模式定義定義規則，以確定作為參數給定的值屬於哪個命名分區。 （* 和 |） 符號稱為*香蕉剪輯*，這種類型的 let 綁定創建的函數稱為*活動識別器*。

例如，請考慮以下具有參數的活動模式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

您可以在模式匹配運算式中使用活動模式，如以下示例所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

此程式的輸出如下：

```console
7 is odd
11 is odd
32 is even
```

活動模式的另一個用途是以多種方式分解資料類型，例如當同一基礎資料具有各種可能的表示形式時。 例如，`Color`物件可以分解為 RGB 表示形式或滙豐表示形式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

上述程式的輸出如下：

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

結合，這兩種使用活動模式的方法使您能夠將資料分區和分解為適當的形式，並在最方便的計算形式中對適當的資料執行適當的計算。

生成的模式匹配運算式使資料能夠以易於讀的便捷方式寫入，從而大大簡化了潛在的複雜分支和資料分析代碼。

## <a name="partial-active-patterns"></a>部分活動模式

有時，您只需要分區部分輸入空間。 在這種情況下，您編寫一組部分模式，每個模式與某些輸入匹配，但無法匹配其他輸入。 並不總是生成值的活動模式稱為*部分活動模式*;它們具有作為選項類型的傳回值。 要定義部分活動模式，請使用在香蕉夾內模式清單末尾\_的萬用字元 （ ） 。 以下代碼說明了部分活動模式的使用。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

上一個示例的輸出如下所示：

```console
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

使用部分活動模式時，有時各個選項可以是脫節的，也可以是互斥的，但它們不需要。 在下面的示例中，模式方形和模式立方體並不脫節，因為某些數位既是正方形，也是立方體，如 64。 以下程式使用 AND 模式組合方形和立方體模式。 它列印出所有整數最多 1000 個，這些整數既是正方形和立方體，也是僅多維資料集的整數。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

輸出如下所示：

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

## <a name="parameterized-active-patterns"></a>參數化活動模式

活動模式始終對要匹配的項至少採用一個參數，但它們也可能採用其他參數，在這種情況下，名稱*參數化的活動模式*適用。 其他參數允許將常規模式專門化。 例如，使用正則運算式解析字串的活動模式通常包括正則運算式作為額外參數，如以下代碼，該代碼還使用前一個代碼示例中定義的部分活動模式`Integer`。 在此示例中，為各種日期格式提供正則運算式的字串用於自訂常規 ParseRegex 活動模式。 整數活動模式用於將匹配的字串轉換為可傳遞給 DateTime 建構函式的整數。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

前一個代碼的輸出如下：

```console
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

活動模式不僅局限于模式匹配運算式，還可以在 let 綁定上使用它們。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

前一個代碼的輸出如下：

```console
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [比對運算式](match-expressions.md)
