---
title: 以統計方式解析的型別參數 (F#)
description: '了解如何使用 F # 以統計方式解析的型別參數，在編譯時期而不是在執行階段取代實際的類型。'
ms.date: 05/16/2016
ms.openlocfilehash: 12c2af4d9df7ae1e5e77efc9413eb8777459a83c
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="statically-resolved-type-parameters"></a>以統計方式解析的型別參數

A*以統計方式解析的型別參數*是型別參數，在編譯時期而不是在執行階段取代實際的類型。 它們前面附加插入號 (^) 符號。


## <a name="syntax"></a>語法

```
ˆtype-parameter
```

## <a name="remarks"></a>備註
在 F # 語言中，有兩種不同的型別參數。 第一類是標準的泛型類型參數。 這些以單引號 （'），像是`'T`和`'U`。 它們是相當於其他.NET Framework 語言中的泛型型別參數。 其他種類會以統計方式解析，且在插入號符號，指示`^T`和`^U`。

以統計方式解析的型別參數是主要適用於搭配成員條件約束時，也就是讓您指定型別引數，必須擁有特定成員，才能加以使用的條件約束。 沒有任何方法來建立這種條件約束使用一般的泛型型別參數。

下表摘要說明兩種型別參數之間的差異與相似之處。

|功能|泛型|以統計方式解析|
|-------|-------|-------------------|
|語法|`'T`, `'U`|`^T`, `^U`|
|解決時間|執行階段|編譯時間|
|成員條件約束|不能與成員條件約束。|可以搭配成員條件約束。|
|程式碼產生|使用標準的泛型型別參數的型別 （或方法） 產生的單一泛型類型或方法。|產生的型別和方法的多個具現化，每個輸入的需要。|
|使用類型|可以用於型別。|無法在類型上使用。|
|使用內嵌函式|否。 內嵌函式不能參數化，使用標準的泛型型別參數。|可以。 以統計方式解析的型別參數不能在函式或不是內嵌的方法。|

許多 F # 核心程式庫函數，特別是運算子，具有以統計方式解析型別參數。 這些函數和運算子會以內嵌方式，並造成數值計算的有效率的程式碼產生。

內嵌方法和函式使用運算子，或具有以統計方式解析型別參數，其他函式也可以使用本身以統計方式解析的型別參數。 通常，型別推斷會推斷這類內嵌函式具有以統計方式解析型別參數。 下列範例說明被推斷為具有以統計方式解析的型別參數的運算子定義。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

已解析的型別`(+@)`兩者的使用根據`(+)`和`(*)`，這兩個的而導致推斷成員以統計方式解析的型別參數條件約束的型別推斷。 解析的型別，如所示，F # 解譯器，如下所示。

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

從 F # 4.1 開始，您也可以指定具象型別名稱以統計方式解析的型別參數簽章中。  在舊版的語言中，型別名稱實際上無法由編譯器所推斷，但無法實際指定簽章中。  為準，F # 4.1，您也可以以統計方式解析的型別參數簽章中指定的具象型別名稱。 以下為範例：

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
[泛型](index.md)

[類型推斷](../type-inference.md)

[自動一般化](automatic-generalization.md)

[條件約束](constraints.md)

[內嵌函式](../functions/inline-functions.md)
