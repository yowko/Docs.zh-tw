---
title: 類型擴充
description: 瞭解類型F#擴充功能如何讓您將新成員加入至先前定義的物件類型。
ms.date: 02/08/2019
ms.openlocfilehash: 502b8636052139b39c800447870c6076a8cd2643
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630196"
---
# <a name="type-extensions"></a>類型延伸模組

類型延伸模組 (也稱為_augmentations_) 是一系列的功能, 可讓您將新成員加入至先前定義的物件類型。 這三項功能包括:

* 內建類型延伸模組
* 選擇性類型擴充功能
* 擴充方法

每個都可以用於不同的案例, 而且有不同的取捨。

## <a name="syntax"></a>語法

```fsharp
// Intrinsic and optional extensions
type typename with
    member self-identifier.member-name =
        body
    ...

// Extension methods
open System.Runtime.CompilerServices

[<Extension>]
type Extensions() =
    [static] member self-identifier.extension-name (ty: typename, [args]) =
        body
    ...
```

## <a name="intrinsic-type-extensions"></a>內建類型延伸模組

內建類型延伸模組是擴充使用者定義類型的類型延伸。

內建類型延伸模組必須在相同的檔案中 **, 以及**與所擴充之類型相同的命名空間或模組中定義。 任何其他定義都會導致它們成為[選擇性的類型延伸](type-extensions.md#optional-type-extensions)。

內建類型延伸有時是將功能與類型宣告分開的更清楚方式。 下列範例顯示如何定義內建類型延伸模組:

```fsharp
namespace Example

type Variant =
    | Num of int
    | Str of string
  
module Variant =
    let print v =
        match v with
        | Num n -> printf "Num %d" n
        | Str s -> printf "Str %s" s

// Add a member to Variant as an extension
type Variant with
    member x.Print() = Variant.print x
```

使用類型延伸可讓您分隔下列各項:

* `Variant`類型的宣告
* 根據其「圖形`Variant` 」列印類別的功能
* 使用物件樣式`.`標記法來存取列印功能的方式

這是將所有專案定義為成員`Variant`的替代方法。 雖然它不是原本較好的方法, 但在某些情況下, 它可能是更清楚的功能表示。

內建類型延伸模組會編譯為它們所擴充之類型的成員, 而且會在反映的類型檢查時出現在類型上。

## <a name="optional-type-extensions"></a>選擇性類型擴充功能

選擇性的類型延伸模組是一種延伸模組, 它會出現在要擴充之類型的原始模組、命名空間或元件外部。

選擇性類型延伸模組適用于擴充您尚未自行定義的類型。 例如：

```fsharp
module Extensions

open System.Collections.Generic

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq {
            for x in xs do
                for i in 1 .. n do
                    yield x
        }
```

您現在可以存取`RepeatElements` , 就像它是的<xref:System.Collections.Generic.IEnumerable%601>成員一樣, 只要`Extensions`在您工作的範圍中開啟模組即可。

當反映進行檢查時, 選擇性擴充功能不會出現在擴充類型上。 選擇性擴充功能必須在模組中, 而且只有在包含擴充功能的模組已開啟或在範圍內時, 才會在範圍中。

選擇性的延伸模組成員會編譯成靜態成員, 其中會以隱含方式將物件實例當做第一個參數傳遞。 不過, 它們的行為就像是實例成員或靜態成員 (根據它們的宣告方式而定)。

選擇性的擴充成員也不會對C#或 VB 取用者顯示。 它們只能在其他F#程式碼中使用。

## <a name="generic-limitation-of-intrinsic-and-optional-type-extensions"></a>內建和選擇性類型延伸的一般限制

在型別變數受條件約束的泛型型別上, 可以宣告型別延伸。 其需求是延伸模組宣告的條件約束符合宣告類型的條件約束。

不過, 即使在宣告的型別與型別延伸之間有相符的條件約束, 條件約束也可能會受到擴充成員的主體的推斷, 而這項要求在型別參數上會有不同的需求, 而不是宣告的型別。 例如：

```fsharp
open System.Collections.Generic

// NOT POSSIBLE AND FAILS TO COMPILE!
//
// The member 'Sum' has a different requirement on 'T than the type IEnumerable<'T>
type IEnumerable<'T> with
    member this.Sum() = Seq.sum this
```

沒有任何方法可以取得此程式碼以使用選擇性的類型延伸模組:

* 也就是, `Sum`成員在 (`static member get_Zero`和`static member (+)`) 上`'T`具有與類型延伸所定義之不同的條件約束。
* `Sum`將類型延伸模組修改為具有與相同的條件約束, 將不再符合上`IEnumerable<'T>`定義的條件約束。
* 將`member this.Sum`變更`member inline this.Sum`為會提供類型條件約束不相符的錯誤。

所需的是「以空格浮點數」的靜態方法, 可以如同擴充類型般呈現。 這是必要的擴充方法。

## <a name="extension-methods"></a>擴充方法

最後, 擴充方法 (有時稱為「C#樣式延伸成員」) 可以在中F#宣告為類別的靜態成員方法。

當您想要在將限制型別變數的泛型型別上定義延伸模組時, 擴充方法很有用。 例如：

```fsharp
namespace Extensions

open System.Runtime.CompilerServices

[<Extension>]
type IEnumerableExtensions() =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

使用時, 此`Sum`程式碼會使其看起來像是在上<xref:System.Collections.Generic.IEnumerable%601>定義, 只要`Extensions`已開啟或在範圍內即可。

## <a name="other-remarks"></a>其他備註

型別延伸也具有下列屬性:

* 可存取的任何類型都可以擴充。
* 內建和選擇性類型延伸模組可以定義_任何_成員類型, 而不只是方法。 例如, 也可以提供延伸模組屬性。
* [語法](type-extensions.md#syntax)`self-identifier`中的標記代表所叫用之類型的實例, 就像一般成員一樣。
* 擴充成員可以是靜態或實例成員。
* 類型擴充功能上的類型變數必須符合宣告類型的條件約束。

類型延伸模組也有下列限制:

* 型別延伸不支援虛擬或抽象方法。
* 型別延伸不支援將方法覆寫為 augmentations。
* 型別延伸不支援以[靜態方式解析的型別參數](./generics/statically-resolved-type-parameters.md)。
* 選擇性類型擴充功能不支援以 augmentations 形式的函式。
* 型別延伸不能定義在[型別縮寫](type-abbreviations.md)上。
* 類型延伸模組對`byref<'T>`無效 (雖然可以宣告)。
* 類型延伸模組對屬性而言是不正確 (雖然可以宣告)。
* 您可以定義多載相同名稱之其他方法的延伸模組, 但F#如果有不明確的呼叫, 則編譯器會提供非擴充方法的喜好設定。

最後, 如果一個類型有多個內建類型延伸模組, 則所有成員都必須是唯一的。 對於選擇性的類型擴充, 不同類型延伸模組中相同類型的成員可以具有相同的名稱。 只有當用戶端程式代碼開啟兩個不同的範圍來定義相同的成員名稱時, 才會發生模糊錯誤。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [成員](./members/index.md)
