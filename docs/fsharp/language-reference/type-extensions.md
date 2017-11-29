---
title: "類型擴充 (F#)"
description: "了解如何 F # 型別延伸模組可讓您將新成員加入先前定義的物件類型。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c9d7ce27-f5ad-4766-b9e9-34187da5bc24
ms.openlocfilehash: f78f8689e95fc1547f1a2b17c615592c00051f7c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="type-extensions"></a>類型擴充

類型擴充功能可讓您將新成員加入至先前定義的物件類型。

## <a name="syntax"></a>語法

```fsharp
// Intrinsic extension.
type typename with
    member self-identifier.member-name =
        body
    ...
[ end ]

// Optional extension.
type typename with
    member self-identifier.member-name =
        body
    ...
[ end ]
```

## <a name="remarks"></a>備註
有兩種形式的類型擴充功能具有稍有不同的語法和行為。 *內建擴充*擴充功能會出現相同的命名空間或模組中，在相同原始程式檔，和相同的組件 （DLL 或可執行檔），為要擴充的類型。 *選擇性擴充功能*是出現原始的模組、 命名空間或要擴充之類型的組件外部的擴充功能。 類型會檢查透過反映，但選擇性擴充功能不這麼做時，內建的擴充功能會出現在型別。 選擇性擴充功能必須在模組中，而且它們才會進入範圍時，其中包含延伸模組已開啟。

在先前的語法， *typename*表示要擴充的型別。 可以存取任何型別可以擴充，但型別名稱必須是實際的型別名稱，而不是類型縮寫。 一種類型的擴充功能中，您可以定義多個成員。 *自我識別項*代表叫用的如同一般成員物件的執行個體。

`end`關鍵字是選擇性的輕量型語法。

就像其他類別類型上的成員可以使用類型擴充功能中定義的成員。 類似其他成員，它們可以是靜態或執行個體成員。 這些方法也稱為的*擴充方法*; 屬性稱為*擴充功能屬性*，依此類推。 選擇性擴充成員會編譯成靜態成員的物件執行個體被當做隱含的第一個參數。 不過，它們會如同執行個體成員或靜態成員，根據宣告的方式。 隱含擴充成員隨附做為型別的成員，而且可以無限制使用。

擴充方法不能為虛擬或抽象方法。 它們可以多載其他方法的名稱相同，但該編譯器會產生模稜兩可的呼叫在非擴充方法的喜好設定。

如果一種類型的多個內建型別延伸存在，所有成員必須都是唯一的。 針對選擇性型別擴充功能，為相同類型的不同類型擴充功能中的成員可以有相同的名稱。 只有當用戶端程式碼會開啟兩個不同的領域，定義了相同的成員名稱，則會發生模稜兩可的錯誤。

在下列範例中，模組中的類型具有內建型別延伸。 外部模組的用戶端程式碼，類型擴充功能會顯示為一般成員中所有各方面的類型。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3701.fs)]

您可以使用內建類型擴充功能來分隔成區段類型的定義。 這可以是用於管理大型的類型定義，例如，將編譯器產生的程式碼和撰寫程式碼分開，或將群組在一起由不同的人所建立，或不同功能相關聯的程式碼。

在下列範例中，選擇性型別延伸能擴充`System.Int32`擴充方法的型別`FromString`呼叫靜態成員`Parse`。 `testFromString`方法將示範就像任何執行個體成員一樣，會呼叫新的成員。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3702.fs)]

新的執行個體成員會出現的任何其他方法一樣`Int32`IntelliSense，但只包含延伸模組的模組開啟或其他在範圍中時的型別。

## <a name="generic-extension-methods"></a>泛型擴充方法
F # 3.1 之前, 的 F # 編譯器並不支援使用 C#-樣式的泛型型別變數、 陣列類型、 元組型別或 F # 函式類型做為 「 這個 」 參數的擴充方法。 F # 3.1 支援使用這些延伸模組成員。

比方說，F # 3.1 程式碼中，您可以使用擴充方法具有簽章，類似於 C# 中的下列語法：

```csharp
static member Method<T>(this T input, T other)
```

泛型型別參數受到限制時，這種方式就特別有用。 此外，您現在可以宣告如下 F # 程式碼中的擴充成員，並定義其他且語意豐富的擴充方法的集合。 在 F # 中，您通常定義擴充成員如下列範例所示：

```fsharp
open System.Collections.Generic

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq { for x in xs do for i in 1 .. n do yield x }
```

不過，若是泛型類型，型別變數可能不限制。 您現在可以宣告 C#-F # 若要解決這項限制中的樣式擴充成員。 當您合併這類宣告與 F # 的內嵌功能時，您可以擴充成員呈現泛型演算法。

請考慮下列宣告：

```fsharp
[<Extension>]
type ExtraCSharpStyleExtensionMethodsInFSharp () =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

藉由使用此宣告，您可以撰寫類似下面的範例的程式碼。

```fsharp
let listOfIntegers = [ 1 .. 100 ]
let listOfBigIntegers = [ 1I to 100I ]
let sum1 = listOfIntegers.Sum()
let sum2 = listOfBigIntegers.Sum()
```

這個程式碼，在相同的泛型算術程式碼會套用到兩種類型的清單沒有多載中，定義單一擴充功能的成員。


## <a name="see-also"></a>另請參閱
[F# 語言參考](index.md)

[成員](members/index.md)
