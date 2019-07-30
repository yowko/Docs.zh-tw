---
title: 模組
description: 瞭解F#模組如何將F# F#程式碼分組 (例如值、類型和函數值)。
ms.date: 04/24/2017
ms.openlocfilehash: 685ab638e7e1b6c8d47d1a316483abcc18e40199
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627435"
---
# <a name="modules"></a>模組

在F#語言的內容中,*模組*是F# F#程式碼的群組, 例如值、類型和函數值。 程式碼分組成不同模組有助於將相關程式碼整理到同一處，以及避免程式中發生名稱衝突。

## <a name="syntax"></a>語法

```fsharp
// Top-level module declaration.
module [accessibility-modifier] [qualified-namespace.]module-name
declarations
// Local module declaration.
module [accessibility-modifier] module-name =
    declarations
```

## <a name="remarks"></a>備註

F#模組是程式F#代碼結構的群組, 例如類型、值、函數值和系結中`do`的程式碼。 它會實作為僅具有靜態成員的 common language runtime (CLR) 類別。 有兩種類型的模組宣告, 視模組中是否包含整個檔案而定: 最上層模組宣告和本機模組宣告。 最上層模組宣告包含模組中的整個檔案。 最上層模組宣告只能出現為檔案中的第一個宣告。

在最上層模組宣告的語法中, 選擇性的*限定命名空間*是包含模組之嵌套命名空間名稱的序列。 限定的命名空間不一定要預先宣告。

您不需要在最上層模組中縮排宣告。 您必須將本機模組中的所有宣告縮排。 在本機模組宣告中, 只有在該模組宣告下縮排的宣告是模組的一部分。

如果程式碼檔案不是以最上層模組宣告或命名空間宣告開頭, 則檔案的整個內容 (包括任何本機模組) 會成為隱含建立之最上層模組的一部分, 該模組具有與檔案相同的名稱, 但不含副檔名。第一個字母轉換成大寫。 例如, 請考慮下列檔案。

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6601.fs)]

這個檔案會編譯成以這種方式撰寫的:

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6602.fs)]

如果您在檔案中有多個模組, 您必須針對每個模組使用本機模組宣告。 如果宣告了封閉式命名空間, 這些模組就是封閉命名空間的一部分。 如果未宣告封入命名空間, 則模組會成為隱含建立之最上層模組的一部分。 下列程式碼範例顯示包含多個模組的程式碼檔案。 編譯器會隱含地建立名為`Multiplemodules`的最上層模組`MyModule1` , 而`MyModule2`和會嵌套在該最上層的模組中。

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6603.fs)]

如果您在專案或單一編譯中有多個檔案, 或者如果您要建立程式庫, 則必須在檔案頂端包含命名空間宣告或模組宣告。 當F#專案或編譯命令列中只有一個檔案, 而且您正在建立應用程式時, 編譯器只會隱含地判斷模組名稱。

*協助工具修飾*詞可以是下列其中一項: `public`、 `private`、 `internal`。 如需詳細資訊，請參閱[存取控制](access-control.md)。 預設值是公用。

## <a name="referencing-code-in-modules"></a>參考模組中的程式碼

當您從另一個模組參考函數、類型和值時, 您必須使用限定名稱或開啟模組。 如果您使用限定名稱, 則必須指定命名空間、模組, 以及所需之程式元素的識別碼。 您可以使用點 (.) 來分隔限定路徑的每個部分, 如下所示。

`Namespace1.Namespace2.ModuleName.Identifier`

您可以開啟模組或一或多個命名空間, 以簡化程式碼。 如需有關開啟命名空間和模組的詳細[資訊, 請參閱匯入宣告:`open`關鍵字。](import-declarations-the-open-keyword.md)

下列程式碼範例顯示最上層模組, 其中包含直到檔案結尾為止的所有程式碼。

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6604.fs)]

若要從相同專案中的另一個檔案使用此程式碼, 您可以使用限定名稱, 或在使用函式之前開啟模組, 如下列範例所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6605.fs)]

## <a name="nested-modules"></a>嵌套模組

模組可以嵌套。 內部模組必須縮排為外部模組宣告, 以表示它們是內部模組, 而不是新模組。 例如, 比較下列兩個範例。 模組`Z`是下列程式碼中的內部模組。

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6607.fs)]

但是模組`Z`在下列程式碼中`Y`是模組的同級。

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6608.fs)]
模組`Z`也是下列程式碼中的同輩模組, 因為它不會縮排至模組`Y`中的其他宣告。

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6609.fs)]
最後, 如果外部模組沒有宣告, 後面緊接著另一個模組宣告, 則會假設新的模組宣告為內部模組, 但編譯器會在第二個模組定義的縮排距離比頭.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6610.fs)]
若要排除警告, 請將內部模組縮排。

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6611.fs)]
如果您想要將檔案中的所有程式碼都放在單一外部模組中, 而您想要使用內部模組, 則外部模組不需要等號, 而且外部模組中的宣告 (包括任何內部模組宣告) 都不必縮排。 內部模組宣告內的宣告必須縮排。 下列程式碼會顯示這種情況。

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6612.fs)]

## <a name="recursive-modules"></a>遞迴模組

F#4.1 引進模組的概念, 可讓所有包含的程式碼互相遞迴。  這是透過來`module rec`完成。  `module rec`使用可減輕無法在類型和模組之間撰寫相互引用程式碼的一些難題。  以下是這種情況的範例:

```fsharp
module rec RecursiveModule =
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

請注意, 例外`DontSqueezeTheBananaException`狀況和類別`Banana`都會彼此參考。  此外, 模組`BananaHelpers`和類別`Banana`也會彼此參考。  如果您已從F# `rec` `RecursiveModule`模組中移除關鍵字, 這將無法在中表示。

這項功能也可以在具有 4.1 F#的[命名空間](namespaces.md)中使用。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [命名空間](namespaces.md)
- [F#RFC FS-1009-允許檔案內的相互參考型別和模組超過更大的範圍](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
