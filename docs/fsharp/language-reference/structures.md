---
title: "結構 (F#)"
description: "深入了解 F # 結構，壓縮物件型別通常更有效率的類別，只需要編寫小量的資料和簡單行為的類型。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 50819506-3210-418f-9602-0ee1c9a52177
ms.openlocfilehash: 542b69a5aacb8fcfb0e8f6d6c943fe1954c4c59c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="structures"></a>結構

A*結構*可以更有效率的類別具有少量資料和簡單行為的類型是精簡的物件類型。

## <a name="syntax"></a>語法

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    struct
        type-definition-elements
    end
// or
[ attributes ]
[<StructAttribute>]
type [accessibility-modifier] type-name =
    type-definition-elements
```

## <a name="remarks"></a>備註
兩個結構*實值型別的*，也就是說，它們會儲存在堆疊上直接或，做為使用中時的欄位或陣列元素的父系中的內嵌輸入。 有別於類別與記錄，結構具有以值傳遞的語意。 這表示它們主要對於經常存取及複製的小型資料彙總相當實用。

在先前的語法中，顯示了兩個表單。 第一個表單的語法略為複雜，但使用卻很頻繁，因為當您使用 `struct` 和 `end` 關鍵字時，可以省略出現在第二個表單中的 `StructAttribute` 屬性。 您可以將 `StructAttribute` 縮寫為只有 `Struct`。

*類型定義項目*先前語法中代表成員宣告和定義。 結構可以具有建構函式及可變動和不可變的欄位，同時它們可以宣告成員及介面實作。 如需詳細資訊，請參閱[成員](members/index.md)。

結構無法參與繼承、不能包含 `let` 或 `do` 繫結，且不得以遞迴方式包含其本身類型的欄位 (不過它們可以包含參考其本身類型的參考儲存格)。

因為結構不允許 `let` 繫結，因此您必須使用 `val` 關鍵字來宣告結構中的欄位。 `val` 關鍵字會定義欄位及其類型，但不允許進行初始化。 相反地，`val` 宣告會初始化為零或 null。 基於這個理由，具有隱含建構函式 (也就是緊接在宣告中結構名稱後的指定參數) 的結構，需要 `val` 宣告加上 `DefaultValue` 屬性的附註。 具有已定義的建構函式之結構，仍然支援零初始化。 因此，`DefaultValue` 屬性是一種零值對於欄位有效的宣告。 結構的隱含建構函式不會執行任何動作，因為類型上不允許 `let` 和 `do` 繫結，但傳入的隱含建構函式參數值均可用作為私用欄位。

明確建構函式可能會牽涉到欄位值的初始化。 當您的結構有明確的建構函式時，它仍然可以支援零初始化。不過，請勿在 `DefaultValue` 宣告上使用 `val` 屬性，因為它與明確建構函式相衝突。 如需有關`val`宣告，請參閱[明確欄位：`val`關鍵字](members/explicit-fields-the-val-keyword.md)。

結構上允許屬性和存取範圍修飾詞，並遵循與其他類型相同的規則。 如需詳細資訊，請參閱[屬性](attributes.md)和[存取控制](access-control.md)。

下列程式碼範例說明結構定義。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="struct-records-and-discriminated-unions"></a>結構的記錄和差別聯的集

從 F # 4.1 開始，您可以表示[記錄](records.md)和[差別等位](discriminated-unions.md)為結構與`[<Struct>]`屬性。  請參閱 < 若要進一步了解每個發行項。
    
## <a name="see-also"></a>另請參閱
[F# 語言參考](index.md)

[類別](classes.md)

[記錄](records.md)

[成員](members/index.md)
