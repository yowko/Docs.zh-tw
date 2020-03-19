---
title: 結構
description: 瞭解 F# 結構，對於具有少量資料和簡單行為的類型，通常比類更有效。
ms.date: 05/16/2016
ms.openlocfilehash: 1e9652cc4776e4d1d52eb20e41b6dd87a6c5ba05
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400278"
---
# <a name="structures"></a>結構

*結構*是一種緊湊的物件類型，對於具有少量資料和簡單行為的類型，該類型可能比類更有效。

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

結構是*數值型別*，這意味著它們直接存儲在堆疊上，或者當它們用作欄位或陣列元素時，它們在父類型中內聯。 有別於類別與記錄，結構具有以值傳遞的語意。 這表示它們主要對於經常存取及複製的小型資料彙總相當實用。

在先前的語法中，顯示了兩個表單。 第一個表單的語法略為複雜，但使用卻很頻繁，因為當您使用 `struct` 和 `end` 關鍵字時，可以省略出現在第二個表單中的 `StructAttribute` 屬性。 您可以將 `StructAttribute` 縮寫為只有 `Struct`。

前一個語法中*的類型定義元素和成員*表示成員聲明和定義。 結構可以具有建構函式及可變動和不可變的欄位，同時它們可以宣告成員及介面實作。 有關詳細資訊，請參閱[成員](./members/index.md)。

結構無法參與繼承、不能包含 `let` 或 `do` 繫結，且不得以遞迴方式包含其本身類型的欄位 (不過它們可以包含參考其本身類型的參考儲存格)。

因為結構不允許 `let` 繫結，因此您必須使用 `val` 關鍵字來宣告結構中的欄位。 `val` 關鍵字會定義欄位及其類型，但不允許進行初始化。 相反地，`val` 宣告會初始化為零或 null。 基於這個理由，具有隱含建構函式 (也就是緊接在宣告中結構名稱後的指定參數) 的結構，需要 `val` 宣告標註 `DefaultValue` 屬性。 具有已定義的建構函式之結構，仍然支援零初始化。 因此，`DefaultValue` 屬性是一種零值對於欄位有效的宣告。 結構的隱含建構函式不會執行任何動作，因為類型上不允許 `let` 和 `do` 繫結，但傳入的隱含建構函式參數值均可用作為私用欄位。

明確建構函式可能會牽涉到欄位值的初始化。 當您的結構有明確的建構函式時，它仍然可以支援零初始化。不過，請勿在 `DefaultValue` 宣告上使用 `val` 屬性，因為它與明確建構函式相衝突。 有關`val`聲明的詳細資訊，請參閱[顯式欄位：`val`關鍵字](./members/explicit-fields-the-val-keyword.md)。

結構上允許屬性和存取範圍修飾詞，並遵循與其他類型相同的規則。 有關詳細資訊，請參閱[屬性](attributes.md)和[存取控制](access-control.md)。

下列程式碼範例說明結構定義。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="byreflike-structs"></a>按參考樣結構

您可以定義可以遵循`byref`類似語義的您自己的結構：有關詳細資訊，請參閱[Byrefs。](byrefs.md) 這與屬性一<xref:System.Runtime.CompilerServices.IsByRefLikeAttribute>起完成：

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike`並不意味著`Struct`. 兩者都必須存在於類型上。

F#`byref`中的"類似"結構是一種堆疊綁定數值型別。 它永遠不會在託管堆上分配。 `byref`類似結構對於高性能程式設計非常有用，因為它通過一組有關存留期和非捕獲的強檢查強制執行。 規則包括：

- 它們可用作函數參數、方法參數、區域變數、方法返回。
- 它們不能是類的靜態或實例成員或正常結構。
- 它們不能被任何閉包構造（`async`方法或 lambda 運算式）捕獲。
- 它們不能用作泛型參數。

儘管這些規則非常強烈地限制了使用，但它們這樣做是為了以安全的方式實現高性能計算的承諾。

## <a name="readonly-structs"></a>唯讀結構

您可以使用<xref:System.Runtime.CompilerServices.IsReadOnlyAttribute>屬性對結構進行分項。 例如：

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsReadOnly`並不意味著`Struct`. 必須同時添加兩者才能有`IsReadOnly`一個結構。

使用此屬性會發出中繼資料，讓 F# 和 C# 知道它分別`inref<'T>`將其`in ref`視為 和 。

在唯讀結構內定義可變值會產生錯誤。

## <a name="struct-records-and-discriminated-unions"></a>結構記錄和歧視聯盟

您可以將["記錄](records.md)"和["歧視聯合"](discriminated-unions.md)表示為具有`[<Struct>]`屬性的結構。  請參閱每篇文章以瞭解更多資訊。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [類](classes.md)
- [記錄](records.md)
- [成員](./members/index.md)
