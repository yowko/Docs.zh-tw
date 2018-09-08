---
title: 資料錄 (F#)
description: '了解 F # 記錄代表具名的值，並選擇性地使用成員的簡單彙總的方式。'
ms.date: 05/16/2016
ms.openlocfilehash: 6103d96b6b80a9e2ed168755958dbe800f7fa862
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44189724"
---
# <a name="records"></a>資料錄

記錄表示具名值的簡單彙總，並選擇性地搭配成員。  從 F # 4.1 開始，它們可以是結構或參考類型。  它們是預設的參考型別。

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

在先前語法中， *typename*是記錄型別名稱*label1*並*label2*名稱的值，稱為*標籤*，並*type1*並*type2*是這些值的類型。 *成員清單*是選用的 成員類型的清單。  您可以使用`[<Struct>]`屬性來建立結構的記錄，而不是參考類型的記錄。

以下是一些範例。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

在不同行上每個標籤時，分號是選擇性的。

您可以設定值，在運算式中稱為*記錄運算式*。 編譯器會推斷的型別與使用 （如果標籤為完全不同於其他記錄類型的項目） 的標籤。 大括號 （{}） 括住記錄運算式。 下列程式碼會顯示記錄運算式初始化的記錄中包含三個標籤的 float 元素`x`，`y`和`z`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

如果可能有另一個型別也有相同的標籤，請務必使用縮短的格式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

最近宣告之型別的標籤優先於先前宣告的型別，因此在上述範例中，`mypoint3D`被推斷為`Point3D`。 您可以明確指定記錄類型，如下列程式碼所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

可以定義方法，如同類別類型的記錄類型。

## <a name="creating-records-by-using-record-expressions"></a>使用記錄運算式建立記錄

您可以使用記錄中所定義的標籤，來初始化記錄。 此運算式指*記錄運算式*。 使用大括號括住記錄運算式，並以分號作為分隔符號。

下列範例示範如何建立記錄。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

記錄運算式和型別定義中的最後一個欄位之後分號是選擇性的不論是否在一行中的所有欄位。

當您建立一筆記錄時，您必須提供每個欄位的值。 您不能參考任何欄位的初始化運算式中的其他欄位的值。

下列程式碼的型別`myRecord2`從欄位的名稱來推斷。 （選擇性） 您也可以明確指定的型別名稱。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

您必須複製現有的記錄，並可能變更的某些欄位值時，記錄建構的另一種很有用。 下列程式碼說明這點。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

這種形式的記錄運算式稱為*複製並更新記錄運算式*。

記錄是不可變的預設值;不過，您可以使用複製和更新的運算式來輕鬆建立修改過的記錄。 您也可以明確指定的可變動的欄位。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

不使用記錄欄位的 DefaultValue 屬性。 更好的方法是定義預設執行個體的記錄與欄位初始化為預設值然後使用複製和更新記錄運算式來設定不同的預設值的任何欄位。

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

## <a name="pattern-matching-with-records"></a>模式比對與記錄

記錄可以搭配模式比對。 您可以明確指定某些欄位，並提供變數的相符項目，就會發生時要指派其他欄位。 下列程式碼範例會說明這點。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

此程式碼的輸出如下所示。

```
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="differences-between-records-and-classes"></a>記錄和類別之間的差異

記錄欄位和類別不同，它們會自動公開為屬性，而且它們是用於建立和複製的記錄。 記錄建構也不同於類別的建構。 在 記錄類型，您無法定義建構函式。 相反地，適用於本主題中所述的建構語法。 類別具有建構函式參數、 欄位和屬性之間沒有直接關聯性。

等位和結構類型，例如記錄都有結構相等語意。 類別具有參考相等語意。 下列程式碼範例示範此工作。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

此程式碼的輸出如下所示：

```
The records are equal.
```

因為兩個值代表在堆積上的兩個物件，而且只有位址會相較，兩個類別物件如果您撰寫相同的程式碼使用類別時，應該不相等 (除非覆寫的類別型別`System.Object.Equals`方法)。

如果您需要參考記錄的等號比較，請將屬性加入`[<ReferenceEquality>]`上述記錄。

## <a name="see-also"></a>另請參閱

- [F# 類型](fsharp-types.md)
- [類別](classes.md)
- [F# 語言參考](index.md)
- [參考相等](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.referenceequalityattribute-class-%5bfsharp%5d)
- [模式比對](pattern-matching.md)
