---
title: 結構 (F#)
description: '深入了解 F # 結構，壓縮物件型別通常比具有少量資料且行為簡單類型的類別更有效率。'
ms.date: 05/16/2016
ms.openlocfilehash: 08af88132dda28883e246b94585ff4ed8bd2f16a
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46321058"
---
# <a name="structures"></a>結構

A*結構*是一種精簡的物件類型，可能會比具有少量資料且行為簡單類型的類別更有效率。

## <a name="syntax"></a>語法

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    struct
        type-definition-elements-and-members
    end
// or
[ attributes ]
[<StructAttribute>]
type [accessibility-modifier] type-name =
    type-definition-elements-and-members
```

## <a name="remarks"></a>備註

結構*實值型別*、 它們儲存在堆疊上的直接或，作為，所以這表示欄位或類型陣列的元素，內嵌在父代。 有別於類別與記錄，結構具有以值傳遞的語意。 這表示它們主要對於經常存取及複製的小型資料彙總相當實用。

在先前的語法中，顯示了兩個表單。 第一個表單的語法略為複雜，但使用卻很頻繁，因為當您使用 `struct` 和 `end` 關鍵字時，可以省略出現在第二個表單中的 `StructAttribute` 屬性。 您可以將 `StructAttribute` 縮寫為只有 `Struct`。

*型別-定義-項目-和-成員*在先前的語法表示的成員宣告和定義。 結構可以具有建構函式及可變動和不可變的欄位，同時它們可以宣告成員及介面實作。 如需詳細資訊，請參閱 <<c0> [ 成員](members/index.md)。

結構無法參與繼承、不能包含 `let` 或 `do` 繫結，且不得以遞迴方式包含其本身類型的欄位 (不過它們可以包含參考其本身類型的參考儲存格)。

因為結構不允許 `let` 繫結，因此您必須使用 `val` 關鍵字來宣告結構中的欄位。 `val` 關鍵字會定義欄位及其類型，但不允許進行初始化。 相反地，`val` 宣告會初始化為零或 null。 基於這個理由，具有隱含建構函式 (也就是緊接在宣告中結構名稱後的指定參數) 的結構，需要 `val` 宣告加上 `DefaultValue` 屬性的附註。 具有已定義的建構函式之結構，仍然支援零初始化。 因此，`DefaultValue` 屬性是一種零值對於欄位有效的宣告。 結構的隱含建構函式不會執行任何動作，因為類型上不允許 `let` 和 `do` 繫結，但傳入的隱含建構函式參數值均可用作為私用欄位。

明確建構函式可能會牽涉到欄位值的初始化。 當您的結構有明確的建構函式時，它仍然可以支援零初始化。不過，請勿在 `DefaultValue` 宣告上使用 `val` 屬性，因為它與明確建構函式相衝突。 如需詳細資訊`val`宣告，請參閱[明確欄位：`val`關鍵字](members/explicit-fields-the-val-keyword.md)。

結構上允許屬性和存取範圍修飾詞，並遵循與其他類型相同的規則。 如需詳細資訊，請參閱 <<c0> [ 屬性](attributes.md)並[存取控制](access-control.md)。

下列程式碼範例說明結構定義。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="byreflike-structs"></a>ByRefLike 結構

您可以定義您自己的結構可以符合`byref`-例如語意： 請參閱 < [Byref](byrefs.md)如需詳細資訊。 做法是使用<xref:System.Runtime.CompilerServices.IsByRefLikeAttribute>屬性：

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike` 並不表示`Struct`。 兩者都必須要有型別。

「`byref`-例如"F # 中的結構是堆疊繫結值型別。 永遠不會在 managed 堆積上配置。 A `byref`-就像結構適用於高效能的程式設計，因為它會強制執行設定的強式存留期和非擷取相關的檢查。 規則包括：

* 它們可用來當做函式參數、 方法參數、 區域變數、 方法會傳回。
* 它們不能是靜態或執行個體的類別或一般結構的成員。
* 它們無法擷取任何關閉的建構 (`async`方法或 lambda 運算式)。
* 它們不能當做泛型參數。

雖然很希望這些規則會限制使用方式，如此一來滿足承諾的高效能運算以安全的方式。

## <a name="readonly-structs"></a>唯讀結構

您可以標註結構與<xref:System.Runtime.CompilerServices.IsReadOnlyAttribute>屬性。 例如: 

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsReadOnly` 並不表示`Struct`。 您必須新增具有`IsReadOnly`結構。

使用這個屬性會發出中繼資料，讓 F # 和 C# 以將其視為知道`inref<'T>`和`in ref`分別。

定義 readonly 結構內可變動的值會產生錯誤。

## <a name="struct-records-and-discriminated-unions"></a>結構的記錄和差別聯的集

可代表[記錄](records.md)並[差別聯集](discriminated-unions.md)使用的結構為`[<Struct>]`屬性。  請參閱 < 若要深入了每個發行項。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [類別](classes.md)
- [記錄](records.md)
- [成員](members/index.md)
