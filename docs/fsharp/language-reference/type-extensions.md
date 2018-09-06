---
title: 類型擴充 (F#)
description: '了解 F # 類型擴充功能如何讓您將新成員加入先前定義的物件類型。'
ms.date: 07/20/2018
ms.openlocfilehash: 27238db1fd0803f62c32755fbc4ab7688f5c107e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43874975"
---
# <a name="type-extensions"></a>類型擴充功能

輸入擴充功能 (也稱為_增強指定_) 是一系列的功能，可讓您將新成員新增至先前定義的物件類型。 三個功能如下：

* 內建類型擴充功能
* 選擇性類型擴充功能
* 擴充方法

每個可用於不同的案例，並有不同的優缺點。

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

## <a name="intrinsic-type-extensions"></a>內建類型擴充功能

內建類型擴充功能是擴充的使用者定義型別類型擴充功能。

內建類型擴充功能必須定義在相同的檔案**和**在相同的命名空間或模組做為其延伸的類型。 任何其他定義將會導致它們正在[選擇性類型擴充](type-extensions.md#optional-type-extensions)。

內建類型擴充有時候是簡潔的方式，將功能分開的型別宣告。 下列範例示範如何定義內建類型擴充功能：

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

使用類型擴充功能，可讓您將下列各項：

* Deklarace`Variant`類型
* 若要列印的功能`Variant`根據其 「 圖形 」 類別
* 若要存取物件樣式的列印功能的方式`.`-標記法

這是定義為成員的所有項目上的替代`Variant`。 雖然不是原本就更好的方法，它可能會更簡潔的功能，在某些情況下表示。

內建類型擴充會編譯為型別的擴充，而反映檢查類型時，會出現在類型上的成員。

## <a name="optional-type-extensions"></a>選擇性類型擴充功能

選擇性類型擴充會出現原始模組、 命名空間或要擴充型別的組件外部的延伸模組。

選擇性類型擴充可用於擴充您還沒有定義您自己的類型。 例如: 

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

您現在可以存取`RepeatElements`好像是隸屬<xref:System.Collections.Generic.IEnumerable%601>只要`Extensions`模組會開啟您在範圍中。

擴充的型別，當反映檢查上沒有出現選擇性擴充功能。 選擇性擴充功能必須在模組中，而且時，它們只能在範圍中包含的延伸模組的模組已開啟，或不在範圍內。

選擇性擴充成員會編譯成靜態成員的物件執行個體隱含傳遞做為第一個參數。 不過，它們就像它們是執行個體成員或靜態成員，根據這些宣告的方式。

## <a name="generic-limitation-of-intrinsic-and-optional-type-extensions"></a>內建函式和選擇性類型擴充功能的一般限制

很可能限於型別變數是泛型型別上宣告的型別延伸模組。 這個需求是延伸模組宣告的條件約束符合宣告的型別條件約束。

不過，即使宣告的型別和型別延伸模組之間比對條件約束，就可以加諸的宣告型別與型別參數上的不同需求擴充成員的主體所推斷的條件約束。 例如: 

```fsharp
open System.Collections.Generic

// NOT POSSIBLE AND FAILS TO COMPILE!
//
// The member 'Sum' has a different requirement on 'T than the type IEnumerable<'T>
type IEnumerable<'T> with
    member this.Sum() = Seq.sum this
```

沒有任何方法可以取得此程式碼以使用選擇性類型擴充功能：

* 現況`Sum`成員有不同的條件約束`'T`(`static member get_Zero`和`static member (+)`) 比類型擴充功能的定義。
* 修改類型擴充功能，能夠以相同的條件約束`Sum`就不再符合定義的條件約束上`IEnumerable<'T>`。
* 進行變更的成員，才能`member inline Sum`將會不相符類型條件約束發生錯誤

預期是 「 浮動在空間 」，可以呈現，彷彿它們所擴充類型的靜態方法。 這是其中的擴充方法會變得必要。

## <a name="extension-methods"></a>擴充方法

最後，（有時稱為 「 C# 樣式擴充成員 」） 的擴充方法可以宣告在 F # 中為靜態成員方法的類別上。

擴充方法可用於當您想要將會限制型別變數的泛型型別上定義擴充功能。 例如: 

```fsharp
namespace Extensions

open System.Runtime.CompilerServices

[<Extension>]
type IEnumerableExtensions() =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

使用時，此程式碼會讓它看起來好像`Sum`上定義<xref:System.Collections.Generic.IEnumerable%601>，只要`Extensions`已開啟，或在範圍內。

## <a name="other-remarks"></a>其他備註

類型延伸模組也會有下列屬性：

* 任何可以存取的型別可加以擴充。
* 內建函式和選擇性類型擴充功能可以定義_任何_成員型別，不只是方法。 讓擴充功能屬性也是可行的例如。
* `self-identifier`權杖[語法](type-extensions.md#syntax)表示叫用，就像一般成員類型的執行個體。
* 擴充的成員可以是靜態或執行個體成員。
* 類型擴充功能上的型別變數必須符合宣告的型別條件的約束。

型別擴充功能也有下列限制：

* 類型擴充功能不支援虛擬或抽象方法。
* 類型擴充功能的增強指定為不支援覆寫方法。
* 不支援類型擴充功能[以靜態方式解析的類型參數](generics/statically-resolved-type-parameters.md)。
* 選擇性類型擴充功能的增強指定為不支援的建構函式。
* 類型擴充功能不能定義於[類型縮寫](type-abbreviations.md)。
* 類型擴充功能不一定適用於`byref<'T>`（不過它們可以宣告）。
* 類型擴充功能不適用於屬性 （不過它們可以宣告）。
* 您可以定義多載相同名稱的其他方法的擴充功能，但 F # 編譯器可讓非擴充方法的喜好設定時，不會模稜兩可的呼叫。

最後，如果多個內建類型擴充功能有一種類型，所有成員必須都是唯一的。 對於選擇性類型擴充成相同類型的不同類型擴充中的成員可以有相同的名稱。 只有當用戶端程式碼會開啟兩個不同的領域，定義了相同成員名稱，則會發生模稜兩可錯誤。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [成員](members/index.md)
