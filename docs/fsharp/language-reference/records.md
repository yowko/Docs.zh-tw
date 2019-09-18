---
title: 資料錄
description: 瞭解記錄F#如何代表已命名值的簡單匯總，並選擇性地包含成員。
ms.date: 06/09/2019
ms.openlocfilehash: 1ba002407b1ccbcbceed32df8636fb860e89e3b6
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053933"
---
# <a name="records"></a>資料錄

記錄表示具名值的簡單彙總，並選擇性地搭配成員。 它們可以是結構或參考型別。  它們預設是參考型別。

## <a name="syntax"></a>語法

```fsharp
[ attributes ]
type [accessibility-modifier] typename =
    { [ mutable ] label1 : type1;
      [ mutable ] label2 : type2;
      ... }
    [ member-list ]
```

## <a name="remarks"></a>備註

在先前的語法中， *typename*是記錄類型的名稱、 *label1*和*label2*是值的名稱，稱為*標籤*，而*type1*和*type2*是這些值的類型。 *成員清單*是類型的選擇性成員清單。  您可以使用`[<Struct>]`屬性來建立結構記錄，而不是參考型別的記錄。

以下是一些範例。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

當每個標籤都在不同的行上時，分號是選擇性的。

您可以在稱為「*記錄運算式*」的運算式中設定值。 編譯器會從所使用的標籤（如果標籤與其他記錄類型的不同）推斷類型。 大括弧（{}）用來括住記錄運算式。 下列程式碼顯示的記錄運算式會使用具有標籤`x` `y`和`z`的三個 float 元素來初始化記錄。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

如果可能有另一個也具有相同標籤的類型，請勿使用縮短的格式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

最近宣告類型的標籤優先于先前宣告的類型，因此在前述範例中， `mypoint3D`會推斷`Point3D`為。 您可以明確指定記錄類型，如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

您可以為記錄類型定義方法，就像類別類型一樣。

## <a name="creating-records-by-using-record-expressions"></a>使用記錄運算式建立記錄

您可以使用記錄中定義的標籤來初始化記錄。 執行此工作的運算式稱為*記錄運算式*。 使用大括弧括住記錄運算式，並使用分號作為分隔符號。

下列範例顯示如何建立記錄。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

記錄運算式和類型定義中最後一個欄位之後的分號是選擇性的，不論欄位是否全部都在同一行。

當您建立記錄時，必須提供每個欄位的值。 您不能在任何欄位的初始化運算式中參考其他欄位的值。

在下列程式碼中，的型`myRecord2`別是從欄位的名稱推斷而來。 （選擇性）您可以明確地指定類型名稱。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

當您必須複製現有的記錄，而且可能變更某些域值時，另一種形式的記錄結構會很有用。 下面這行程式碼將說明這一點。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

這種形式的記錄運算式稱為「*複製和更新記錄」運算式*。

記錄預設為不變;不過，您可以使用複製和更新運算式，輕鬆地建立已修改的記錄。 您也可以明確指定可變的欄位。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

請勿將 DefaultValue 屬性與記錄欄位搭配使用。 較好的方法是使用初始化為預設值的欄位來定義記錄的預設實例，然後使用複製和更新記錄運算式來設定與預設值不同的任何欄位。

```fsharp
// Rather than use [<DefaultValue>], define a default record.
type MyRecord =
    { Field1 : int
      Field2 : int }

let defaultRecord1 = { Field1 = 0; Field2 = 0 }
let defaultRecord2 = { Field1 = 1; Field2 = 25 }

// Use the with keyword to populate only a few chosen fields
// and leave the rest with default values.
let rr3 = { defaultRecord1 with Field2 = 42 }
```

## <a name="creating-mutually-recursive-records"></a>建立相互遞迴記錄

在建立記錄時，您可能會想要讓它相依于您之後想要定義的另一種類型。 這是編譯錯誤，除非您將記錄類型定義為 [相互遞迴]。

定義互斥的遞迴記錄是使用`and`關鍵字來完成。 這可讓您將兩個以上的記錄類型連結在一起。

例如，下列程式碼會將`Person`和`Address`類型定義為 [相互遞迴]：

```fsharp
// Create a Person type and use the Address type that is not defined
type Person =
  { Name: string
    Age: int
    Address: Address }
// Define the Address type which is used in the Person record
and Address =
  { Line1: string
    Line2: string
    PostCode: string
    Occupant: Person }
```

如果您要定義上一個範例，但不`and`含關鍵字，則不會編譯。 相互遞迴定義需要關鍵字。`and`

## <a name="pattern-matching-with-records"></a>記錄的模式比對

記錄可以搭配模式比對使用。 您可以明確指定某些欄位，並提供在發生比對時將指派之其他欄位的變數。 下列程式碼範例會說明這點。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

此程式碼的輸出如下所示。

```
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="differences-between-records-and-classes"></a>記錄與類別之間的差異

記錄欄位與類別不同，因為它們會自動公開為屬性，而且會用於建立和複製記錄。 記錄結構也不同于類別結構。 在記錄類型中，您不能定義一個函式。 相反地，本主題中所述的結構語法也適用。 類別在「函數參數」、「欄位」和「屬性」之間沒有直接關聯性。

如同聯集和結構類型，記錄具有結構化相等的語義。 類別具有參考相等的語義。 下列程式碼範例示範此工作。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

此程式碼的輸出如下所示：

```
The records are equal.
```

如果您使用類別撰寫相同的程式碼，這兩個類別物件將會不相等，因為這兩個值會代表堆積上的兩個物件，而且只會比較位址（除非`System.Object.Equals`類別類型會覆寫方法）。

如果您需要記錄的參考相等，請在記錄`[<ReferenceEquality>]`上方加入屬性。

## <a name="see-also"></a>另請參閱

- [F# 類型](fsharp-types.md)
- [類別](classes.md)
- [F# 語言參考](index.md)
- [參考-相等](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.referenceequalityattribute-class-%5bfsharp%5d)
- [模式比對](pattern-matching.md)
