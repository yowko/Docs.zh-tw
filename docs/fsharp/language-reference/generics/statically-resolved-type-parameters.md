---
title: 以統計方式解析的型別參數
description: 瞭解如何使用F#靜態解析的類型參數 (在編譯時期以實際類型取代, 而不是在執行時間)。
ms.date: 05/16/2016
ms.openlocfilehash: 43ed79b6e5f43a499a27b05e26472b021c455e44
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630590"
---
# <a name="statically-resolved-type-parameters"></a>以統計方式解析的型別參數

*靜態解析的類型參數*是在編譯時期 (而不是在執行時間) 取代為實際類型的類型參數。 它們前面會加上插入號 (^) 符號。

## <a name="syntax"></a>語法

```
ˆtype-parameter
```

## <a name="remarks"></a>備註

在F#語言中, 有兩種不同類型的型別參數。 第一種是標準的泛型型別參數。 這些會以單引號 (') 表示, 如同`'T`和。 `'U` 它們相當於其他 .NET Framework 語言中的泛型型別參數。 另一種方法是以靜態方式解析, 並以插入號符號表示`^T` , `^U`如同和。

靜態解析的類型參數主要適用于結合成員條件約束, 這是條件約束, 可讓您指定類型引數必須有特定成員或成員, 才能使用。 您無法使用一般泛型型別參數來建立這種條件約束。

下表摘要說明兩種類型參數之間的相似性和差異。

|功能|泛型|靜態解析|
|-------|-------|-------------------|
|語法|`'T`、 `'U`|`^T`、 `^U`|
|解決時間|執行階段|編譯時間|
|成員條件約束|不能與成員條件約束搭配使用。|可以與成員條件約束搭配使用。|
|程式碼產生|具有標準泛型型別參數的類型 (或方法) 會產生單一泛型型別或方法。|會產生類型和方法的多個具現化, 每個所需的類型各一個。|
|搭配類型使用|可以用於類型。|不能用在類型上。|
|搭配內嵌函數使用|資料分割 內嵌函式不能以標準泛型型別參數參數化。|可以。 靜態解析的類型參數不能用於非內嵌的函式或方法。|

許多F#核心程式庫函式 (尤其是運算子) 都有靜態解析的類型參數。 這些函式和運算子是內嵌的, 可讓您以有效率的方式產生數值計算的程式碼。

使用運算子的內嵌方法和函式, 或使用其他具有靜態解析類型參數的函式, 也可以使用靜態解析的類型參數本身。 通常, 型別推斷會推斷這類內嵌函式, 使其具有靜態解析的型別參數。 下列範例說明的運算子定義, 會推斷為具有靜態解析的類型參數。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

已解決的型`(+@)`別是以`(+)`和`(*)`的使用為基礎, 這兩者都會導致型別推斷在靜態解析的型別參數上推斷成員條件約束。 如F#解譯器所示, 已解析的類型如下。

```fsharp
^a -> ^c -> ^d
when (^a or ^b) : (static member ( + ) : ^a * ^b -> ^d) and
(^a or ^c) : (static member ( * ) : ^a * ^c -> ^b)
```

輸出如下。

```
2
1.500000
```

從F# 4.1 開始, 您也可以在以靜態方式解析的類型參數簽章中指定具體的類型名稱。  在舊版的語言中, 編譯器實際上可以推斷類型名稱, 但實際上無法在簽章中指定。  從 4.1 F# , 您也可以在以靜態方式解析的類型參數簽章中指定具體的類型名稱。 以下為範例：

```fsharp
let inline konst x _ = x

type CFunctor() = 
    static member inline fmap (f: ^a -> ^b, a: ^a list) = List.map f a
    static member inline fmap (f: ^a -> ^b, a: ^a option) =
        match a with
        | None -> None
        | Some x -> Some (f x)

    // default implementation of replace
    static member inline replace< ^a, ^b, ^c, ^d, ^e when ^a :> CFunctor and (^a or ^d): (static member fmap: (^b -> ^c) * ^d -> ^e) > (a, f) =
        ((^a or ^d) : (static member fmap : (^b -> ^c) * ^d -> ^e) (konst a, f))

    // call overridden replace if present
    static member inline replace< ^a, ^b, ^c when ^b: (static member replace: ^a * ^b -> ^c)>(a: ^a, f: ^b) =
        (^b : (static member replace: ^a * ^b -> ^c) (a, f))

let inline replace_instance< ^a, ^b, ^c, ^d when (^a or ^c): (static member replace: ^b * ^c -> ^d)> (a: ^b, f: ^c) =
        ((^a or ^c): (static member replace: ^b * ^c -> ^d) (a, f))

// Note the concrete type 'CFunctor' specified in the signature
let inline replace (a: ^a) (f: ^b): ^a0 when (CFunctor or  ^b): (static member replace: ^a *  ^b ->  ^a0) =
    replace_instance<CFunctor, _, _, _> (a, f)
```

## <a name="see-also"></a>另請參閱

- [泛型](index.md)
- [類型推斷](../type-inference.md)
- [自動一般化](automatic-generalization.md)
- [條件約束](constraints.md)
- [內嵌函式](../functions/inline-functions.md)
