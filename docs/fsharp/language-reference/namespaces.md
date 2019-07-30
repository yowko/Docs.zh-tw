---
title: 命名空間
description: 瞭解F#命名空間如何讓您將名稱附加至程式元素的群組, 以將程式碼組織成相關功能的區域。
ms.date: 12/08/2018
ms.openlocfilehash: d295f25cae81bc28b4fcb522bdcacde862f9517a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627372"
---
# <a name="namespaces"></a>命名空間

命名空間可讓您將名稱附加至F#程式元素的群組, 以將程式碼組織成相關功能的區域。 命名空間通常是檔案中F#的最上層元素。

## <a name="syntax"></a>語法

```fsharp
namespace [rec] [parent-namespaces.]identifier
```

## <a name="remarks"></a>備註

如果您想要將程式碼放在命名空間中, 則檔案中的第一個宣告必須宣告命名空間。 整個檔案的內容接著會成為命名空間的一部分, 前提是檔案中不會有其他命名空間宣告。 如果是這種情況, 則所有程式碼必須等到下一個命名空間宣告, 才會被視為在第一個命名空間內。

命名空間不能直接包含值和函數。 相反地, 值和函式必須包含在模組中, 而模組則包含在命名空間中。 命名空間可以包含類型 (模組)。

XML 檔批註可以在命名空間的上方宣告, 但會被忽略。 編譯器指示詞也可以在命名空間的上方宣告。

命名空間可以使用 namespace 關鍵字明確宣告, 或在宣告模組時以隱含方式宣告。 若要明確宣告命名空間, 請使用 namespace 關鍵字並在後面加上命名空間名稱。 下列範例顯示的程式碼檔案會宣告具有類型`Widgets`的命名空間, 以及該命名空間中包含的模組。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

如果檔案的整個內容都在一個模組中, 您也可以使用`module`關鍵字, 並在完整的模組名稱中提供新的命名空間名稱, 以隱含方式宣告命名空間。 下列範例顯示的程式碼檔案會宣告命名空間`Widgets`和包含函`WidgetsModule`式的模組。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

下列程式碼相當於上述程式碼, 但模組是本機模組宣告。 在此情況下, 命名空間必須出現在自己的行上。

[!code-fsharp[Main](~/samples/snippets/fsharp/namespaces/snippet6402.fs)]

如果一個或多個命名空間中的同一個檔案需要一個以上的模組, 您就必須使用本機模組宣告。 當您使用本機模組宣告時, 不能在模組宣告中使用限定的命名空間。 下列程式碼顯示具有命名空間宣告和兩個本機模組宣告的檔案。 在此情況下, 模組會直接包含在命名空間中;沒有與檔案同名的隱含建立模組。 檔案中的任何其他程式碼 (例如`do`系結) 都是在命名空間中, 而不是在內部模組中, 因此您必須使用模組名稱來限定模組成員。 `widgetFunction`

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

此範例的輸出如下所示。

```fsharp
Module1 10 20
Module2 5 6
```

如需詳細資訊, 請參閱[模組](modules.md)。

## <a name="nested-namespaces"></a>嵌套命名空間

當您建立嵌套命名空間時, 您必須完整限定它。 否則, 您會建立新的最上層命名空間。 命名空間宣告中會忽略縮排。

下列範例顯示如何宣告嵌套命名空間。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a>檔案和元件中的命名空間

命名空間可以在單一專案或編譯中跨越多個檔案。 「*命名空間片段*」一詞描述包含在一個檔案中的命名空間部分。 命名空間也可以跨越多個元件。 例如, `System`命名空間包含整個 .NET Framework, 這會跨越許多元件, 並包含許多嵌套的命名空間。

## <a name="global-namespace"></a>全域命名空間

您可以使用預先定義`global`的命名空間, 將名稱放在 .net 最上層命名空間中。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

您也可以使用全域來參考最上層的 .NET 命名空間, 例如, 解決與其他命名空間的名稱衝突。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

## <a name="recursive-namespaces"></a>遞迴命名空間

命名空間也可以宣告為遞迴, 讓所有包含的程式碼都可以互相遞迴。  這是透過來`namespace rec`完成。 `namespace rec`使用可減輕無法在類型和模組之間撰寫相互引用程式碼的一些難題。 以下是這種情況的範例:

```fsharp
namespace rec MutualReferences

type Orientation = Up | Down
type PeelState = Peeled | Unpeeled

// This exception depends on the type below.
exception DontSqueezeTheBananaException of Banana

type BananaPeel() = class end

type Banana(orientation : Orientation) =
    member val IsPeeled = false with get, set
    member val Orientation = orientation with get, set
    member val Sides: PeelState list = [ Unpeeled; Unpeeled; Unpeeled; Unpeeled] with get, set

    member self.Peel() = BananaHelpers.peel self // Note the dependency on the BananaHelpers module.
    member self.SqueezeJuiceOut() = raise (DontSqueezeTheBananaException self) // This member depends on the exception above.

module BananaHelpers =
    let peel (b: Banana) =
        let flip (banana: Banana) =
            match banana.Orientation with
            | Up -> 
                banana.Orientation <- Down
                banana
            | Down -> banana

        let peelSides (banana: Banana) =
            banana.Sides
            |> List.map (function
                         | Unpeeled -> Peeled
                         | Peeled -> Peeled)

        match b.Orientation with
        | Up ->   b |> flip |> peelSides
        | Down -> b |> peelSides
```

請注意, 例外`DontSqueezeTheBananaException`狀況和類別`Banana`都會彼此參考。  此外, 模組`BananaHelpers`和類別`Banana`也會彼此參考。 如果您已從F# `rec` `MutualReferences`命名空間移除關鍵字, 就無法在中表示。

這項功能也適用于最上層[模組](modules.md)。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [模組](modules.md)
- [F#RFC FS-1009-允許檔案內的相互參考型別和模組超過更大的範圍](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
