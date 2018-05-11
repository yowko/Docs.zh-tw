---
title: 命名空間 (F#)
description: '了解如何使用 F # 命名空間可讓您組織成區域的相關功能的程式碼，讓您以將名稱附加至一組程式元素。'
ms.date: 04/24/2017
ms.openlocfilehash: 151079864f18fff79dac108889b68b3acf1566a1
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
---
# <a name="namespaces"></a>命名空間

命名空間可讓您將名稱附加至程式項目群組，將程式碼依相關功能分類。


## <a name="syntax"></a>語法

```fsharp
namespace [parent-namespaces.]identifier
```

## <a name="remarks"></a>備註
如果您想要將程式碼放在命名空間中，在檔案中的第一個宣告必須宣告命名空間。 整個檔案的內容就會變成命名空間的一部分。

命名空間不能直接包含的值和函式。 值和函式必須包含在模組中，而模組包含的命名空間中。 命名空間包含的模組類型。

命名空間可以明確宣告命名空間關鍵字，或以隱含方式宣告的模組時。 若要明確宣告命名空間，請使用命名空間關鍵字後面加上命名空間名稱。 下列範例示範具有類型和模組包含該命名空間中宣告命名空間 Widget 的程式碼檔案。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

如果其中一個模組中檔案的整個內容，您也可以宣告命名空間以隱含方式使用`module`關鍵字並提供完整的模組名稱中的新命名空間名稱。 下列範例示範宣告命名空間的程式碼檔案`Widgets`和模組`WidgetsModule`，其中包含函式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

下列程式碼相當於上述的程式碼，但模組是本機模組宣告。 在此情況下，命名空間必須出現在自己的那一行。

[!code-fsharp[Main](../../../samples/snippets/fsharp/namespaces/snippet6402.fs)]

如果多個模組需要一個或多個命名空間中相同的檔案中，您必須使用本機模組宣告。 當您使用本機模組宣告時，您無法使用限定的命名空間模組宣告中。 下列程式碼會示範具有命名空間宣告和兩個本機模組宣告的檔案。 在此情況下，模組會直接包含在命名空間。具有相同名稱的檔案沒有隱含建立的模組。 任何其他程式碼在檔案中，例如`do`繫結，是在命名空間，但不是在內部的模組中，因此您需要限定模組成員`widgetFunction`使用模組名稱。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

此範例的輸出如下所示。

```fsharp
Module1 10 20
Module2 5 6
```

如需詳細資訊，請參閱[模組](modules.md)。

## <a name="nested-namespaces"></a>巢狀命名空間
當您建立巢狀命名空間時，您必須完整限定。 否則，您會建立新的最上層命名空間。 命名空間宣告中，會忽略縮排。

下列範例會示範如何宣告巢狀命名空間。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a>檔案和組件中的命名空間
命名空間可以跨越多個檔案中的單一專案或編譯。 詞彙*命名空間片段*描述包含在一個檔案中的命名空間的一部分。 命名空間也可以跨越多個組件。 例如，`System`命名空間包含整個.NET Framework 中，跨越許多組件，並且包含許多巢狀命名空間。


## <a name="global-namespace"></a>全域命名空間
您使用預先定義的命名空間`global`，將名稱置於.NET 最上層命名空間。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

您也可以使用全域參考最上層的.NET 命名空間，例如，若要解決與其他命名空間的名稱衝突。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

## <a name="recursive-namespaces"></a>遞迴命名空間

F # 4.1 導入的命名空間可讓所有包含的程式碼是相互遞迴的概念。  這是透過`namespace rec`。  使用`namespace rec`可以減輕無法撰寫相互參考的程式碼類型和模組之間的一些難題。  此動作的範例如下：

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

請注意，例外狀況`DontSqueezeTheBananaException`和類別`Banana`兩者來互相參考。  此外，此模組`BananaHelpers`和類別`Banana`也彼此參考。  這並不是 F # 中表示，如果您移除可能`rec`關鍵字`MutualReferences`命名空間。

這項功能也會提供的最上層[模組](modules.md)在 F # 4.1 或更高版本。

## <a name="see-also"></a>另請參閱
[F# 語言參考](index.md)

[模組](modules.md)

[F # RFC FS 1009-允許透過較大的範圍內的檔案進行相互參考的類型和模組](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
