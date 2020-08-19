---
title: 類型擴充
description: '瞭解 F # 類型延伸模組如何讓您將新成員加入至先前定義的物件類型。'
ms.date: 02/05/2020
ms.openlocfilehash: 8fdb2d5e527643b23d24a6118e8cef6b11f1a546
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559124"
---
# <a name="type-extensions"></a>類型延伸模組

類型延伸 (也稱為 _增強指定_) 是一系列的功能，可讓您將新成員加入至先前定義的物件類型。 這三項功能包括：

- 內建類型延伸模組
- 選擇性類型延伸模組
- 擴充方法

每個都可以在不同的案例中使用，而且有不同的取捨。

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
    [<Extension>]
    static member self-identifier.extension-name (ty: typename, [args]) =
        body
    ...
```

## <a name="intrinsic-type-extensions"></a>內建類型延伸模組

內建類型延伸模組是延伸使用者定義型別的延伸模組。

內建類型延伸模組必須定義在相同的檔案中 **，以及** 在其所擴充之類型的相同命名空間或模組中。 任何其他定義都會導致它們成為 [選用的類型延伸](type-extensions.md#optional-type-extensions)模組。

內建類型延伸模組有時可讓您以更清楚的方式來分隔類型宣告中的功能。 下列範例示範如何定義內建類型延伸：

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

使用類型擴充功能可讓您分隔下列各項：

- 型別的宣告 `Variant`
- 根據其「圖形」來列印類別的功能 `Variant`
- 使用物件樣式表示法存取列印功能的方式 `.`

這是將所有專案定義為成員的替代方案 `Variant` 。 雖然它並非原本就更好的方法，但是在某些情況下，它可以是更清楚的功能表示。

內建類型延伸模組會編譯為它們所擴充之類型的成員，並且在反映檢查型別時出現在類型上。

## <a name="optional-type-extensions"></a>選擇性類型延伸模組

選擇性類型延伸模組是在要擴充之類型的原始模組、命名空間或元件之外出現的延伸模組。

選擇性類型延伸模組適用于擴充您自己未定義的類型。 例如：

```fsharp
module Extensions

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq {
            for x in xs do
                for _ in 1 .. n -> x
        }
```

您現在可以存取 `RepeatElements` 相同的成員，只要 <xref:System.Collections.Generic.IEnumerable%601> `Extensions` 模組是在您所使用的範圍中開啟即可。

由反映檢查時，選擇性的延伸模組不會出現在擴充類型上。 選用的延伸模組必須在模組中，而且只有在包含擴充功能的模組是開啟或在範圍內時，才會在範圍內。

選擇性的擴充成員會編譯成靜態成員，而靜態成員會以隱含方式將物件實例傳遞為第一個參數。 不過，它們的作用就像是實例成員或靜態成員（根據其宣告方式）。

C # 或 Visual Basic 取用者也看不到選用的擴充成員。 它們只能在其他 F # 程式碼中使用。

## <a name="generic-limitation-of-intrinsic-and-optional-type-extensions"></a>內建和選擇性類型延伸的一般限制

您可以在類型變數受到條件約束的泛型型別上宣告類型延伸。 需求是延伸宣告的條件約束符合宣告型別的條件約束。

但是，即使在宣告的型別和型別延伸之間符合條件約束，也有可能是因為在類型參數上強加不同需求的擴充成員主體所推斷的條件約束，而不是宣告的型別。 例如：

```fsharp
open System.Collections.Generic

// NOT POSSIBLE AND FAILS TO COMPILE!
//
// The member 'Sum' has a different requirement on 'T than the type IEnumerable<'T>
type IEnumerable<'T> with
    member this.Sum() = Seq.sum this
```

沒有任何方法可讓此程式碼使用選擇性的類型延伸模組：

- 同樣地， `Sum` 成員在 (上具有不同的條件約束 `'T` `static member get_Zero` ，且) 與類型延伸模組所定義的不同 `static member (+)` 。
- 將類型延伸修改為具有相同的條件約束， `Sum` 將不再符合中的定義條件約束 `IEnumerable<'T>` 。
- `member this.Sum`將變更為 `member inline this.Sum` 會提供類型條件約束不相符的錯誤。

您需要的是「float in space」的靜態方法，而且可以像是延伸型別一樣呈現。 這就是需要擴充方法的地方。

## <a name="extension-methods"></a>擴充方法

最後，擴充方法 (有時稱為「c # 樣式延伸成員」 ) 可以在 F # 中宣告為類別上的靜態成員方法。

當您想要在會限制型別變數的泛型型別上定義延伸時，擴充方法會很有用。 例如：

```fsharp
namespace Extensions

open System.Collections.Generic
open System.Runtime.CompilerServices

[<Extension>]
type IEnumerableExtensions =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

使用時，此程式碼會使其顯示為 `Sum` 在上定義的 <xref:System.Collections.Generic.IEnumerable%601> ，只要已 `Extensions` 開啟或在範圍內即可。

為了讓擴充功能可供 VB.NET 程式碼使用， `ExtensionAttribute` 元件層級需要額外的程式碼：

```fsharp
module AssemblyInfo
open System.Runtime.CompilerServices
[<assembly:Extension>]
do ()
```

## <a name="other-remarks"></a>其他備註

類型延伸也有下列屬性：

- 您可以擴充任何可以存取的類型。
- 內建和選擇性類型延伸模組可以定義 _任何_ 成員類型，而不只是方法。 例如，擴充屬性也是可行的。
- `self-identifier`[語法](type-extensions.md#syntax)中的標記代表所叫用之型別的實例，就像一般成員一樣。
- 擴充成員可以是靜態或實例成員。
- 類型延伸的型別變數必須符合宣告型別的條件約束。

類型延伸也有下列限制：

- 類型延伸模組不支援虛擬或抽象方法。
- 類型延伸模組不支援以增強指定覆寫方法。
- 類型延伸模組不支援 [靜態解析的型別參數](./generics/statically-resolved-type-parameters.md)。
- 選擇性類型延伸模組不支援做為增強指定的函式。
- 類型縮寫不能定義為類型 [縮寫](type-abbreviations.md)。
- 類型延伸模組對 (而言是不正確， `byref<'T>` 不過它們可以) 宣告。
- 類型延伸模組對屬性而言無效 (但可以) 宣告。
- 您可以定義多載相同名稱之其他方法的擴充功能，但 F # 編譯器會在有不明確的呼叫時，將喜好設定提供給非擴充方法。

最後，如果有多個類型的內建類型延伸，則所有成員都必須是唯一的。 對於選擇性的類型延伸，相同類型之不同類型延伸中的成員可以有相同的名稱。 只有當用戶端程式代碼開啟兩個定義相同成員名稱的不同範圍時，才會發生不明確的錯誤。

## <a name="see-also"></a>另請參閱

- [F # 語言參考](index.md)
- [成員](./members/index.md)
