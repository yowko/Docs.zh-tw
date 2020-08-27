---
title: 記錄
description: '瞭解 F # 記錄如何代表簡單的命名值匯總，並選擇性地包含成員。'
ms.date: 08/15/2020
ms.openlocfilehash: a72c0f15b58407e7d759e2fb5a1b35a7fc0d29e3
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812350"
---
# <a name="records"></a>記錄

記錄表示具名值的簡單彙總，並選擇性地搭配成員。 可以是結構或參考型別。  它們預設為參考類型。

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

在先前的語法中， *typename* 是記錄類型的名稱， *label1* 和 *label2* 是值的名稱（稱為 *標籤*），而 *type1* 和 *type2* 是這些值的類型。 *成員清單* 是類型的選擇性成員清單。  您可以使用 `[<Struct>]` 屬性來建立結構記錄，而不是參考型別的記錄。

以下有一些範例。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

當每個標籤都在不同的行上時，分號是選擇性的。

您可以在稱為 *記錄運算式*的運算式中設定值。 如果標籤與其他記錄類型) 的不同，則編譯器會從所使用的標籤推斷類型 (。 括弧 ( {} ) 括住記錄運算式。 下列程式碼會顯示記錄運算式，該運算式會使用具有標籤和的三個 float 元素來初始化記錄 `x` `y` `z` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

如果有另一種類型也有相同的標籤，請勿使用縮寫的表單。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

最近宣告類型的標籤優先于先前宣告的型別，因此在上述範例中， `mypoint3D` 會推斷為 `Point3D` 。 您可以明確地指定記錄類型，如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

您可以針對記錄類型定義方法，就像類別類型一樣。

## <a name="creating-records-by-using-record-expressions"></a>使用記錄運算式建立記錄

您可以使用記錄中定義的標籤來初始化記錄。 執行這項工作的運算式稱為「 *記錄運算式*」。 使用大括弧來括住記錄運算式，並使用分號做為分隔符號。

下列範例顯示如何建立記錄。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

在記錄運算式和類型定義中，最後一個欄位後面的分號是選擇性的，不論這些欄位是否全都在同一行。

當您建立記錄時，必須提供每個欄位的值。 您無法在初始化運算式中參考任何欄位的其他欄位值。

在下列程式碼中，的型別 `myRecord2` 是從欄位名稱推斷而來。 （選擇性）您可以明確地指定型別名稱。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

當您必須複製現有的記錄，而且可能變更部分域值時，另一種形式的記錄結構可能很有用。 下面這行程式碼將說明這一點。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

這種形式的記錄運算式稱為「 *複製和更新記錄運算式*」。

依預設，記錄是不可變的;不過，您可以使用複製和更新運算式，輕鬆地建立修改過的記錄。 您也可以明確地指定可變欄位。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

請勿使用 DefaultValue 屬性搭配記錄欄位。 更好的方法是使用已初始化為預設值的欄位來定義記錄的預設實例，然後使用複製和更新記錄運算式來設定與預設值不同的任何欄位。

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

建立記錄時，您可能會想要讓它相依于您稍後要定義的另一種類型。 這是編譯錯誤，除非您將記錄類型定義為相互遞迴。

使用關鍵字來定義相互遞迴記錄 `and` 。 這可讓您將2個以上的記錄類型連結在一起。

例如，下列程式碼會將 `Person` 和 `Address` 類型定義為相互遞迴：

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

如果您要定義先前的範例而不指定 `and` 關鍵字，則不會進行編譯。 `and`相互遞迴定義必須有關鍵詞。

## <a name="pattern-matching-with-records"></a>使用記錄進行模式比對

記錄可以搭配模式比對使用。 您可以明確指定某些欄位，並提供變數給將在相符時指派的其他欄位。 下列程式碼範例會說明這點。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

此程式碼的輸出如下所示。

```console
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="records-and-members"></a>記錄和成員

您可以在記錄上指定成員，就像您可以使用類別一樣。 不支援欄位。 常見的方法是定義 `Default` 靜態成員，以便輕鬆地記錄結構：

```fsharp
type Person =
  { Name: string
    Age: int
    Address: string }

    static member Default =
        { Name = "Phillip"
          Age = 12
          Address = "123 happy fun street" }

let defaultPerson = Person.Default
```

如果您使用自我識別碼，該識別碼會參考其成員所呼叫之記錄的實例：

```fsharp
type Person =
  { Name: string
    Age: int
    Address: string }

    member this.WeirdToString() =
        this.Name + this.Address + string this.Age

let p = { Name = "a"; Age = 12; Address = "abc123 }
let weirdString = p.WeirdToString()
```

## <a name="differences-between-records-and-classes"></a>記錄與類別之間的差異

記錄欄位與類別不同之處在于它們會自動公開為屬性，並用於建立和複製記錄。 記錄結構與類別結構也不同。 在記錄類型中，您無法定義函數。 相反地，本主題所述的結構語法也適用。 類別在兩個函式參數、欄位和屬性之間沒有直接關聯性。

如同 union 和 structure 型別，記錄具有結構化相等的語法。 類別具有參考相等的語法。 下列程式碼範例示範此工作。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

此程式碼的輸出如下所示：

```console
The records are equal.
```

如果您以類別撰寫相同的程式碼，這兩個類別物件將會不相等，因為這兩個值會在堆積上代表兩個物件，而只有位址會 (比較，除非類別類型會覆寫 `System.Object.Equals`) 的方法。

如果您需要記錄的參考相等，請在 `[<ReferenceEquality>]` 記錄上方加入屬性。

## <a name="see-also"></a>請參閱

- [F# 類型](fsharp-types.md)
- [類別](classes.md)
- [F # 語言參考](index.md)
- [參考相等](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-referenceequalityattribute.html)
- [模式比對](pattern-matching.md)
