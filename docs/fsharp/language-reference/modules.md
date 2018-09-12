---
title: 模組 (F#)
description: '了解如何 F # 模組是 F # 程式碼，例如值、 類型和函式值，在 F # 程式中的群組。'
ms.date: 04/24/2017
ms.openlocfilehash: fb0aa1d508d1141933b4fbdf10633f67ed078dc7
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2018
ms.locfileid: "44514351"
---
# <a name="modules"></a>模組

在 F # 語言的內容*模組*是 F # 程式碼，例如值、 類型和函式值，在 F # 程式中的群組。 程式碼分組成不同模組有助於將相關程式碼整理到同一處，以及避免程式中發生名稱衝突。

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

F # 模組是 F # 程式碼建構，例如類型、 值、 函式值，以及程式碼中的群組`do`繫結。 它會實作為具有只有靜態成員的 common language runtime (CLR) 類別。 有兩種類型的模組宣告、 根據是否包含在模組中的整份檔案： 最上層模組宣告和本機模組宣告。 最上層模組宣告包含在模組中的整個檔案。 最上層模組宣告只可以顯示為檔案中的第一個宣告。

在最上層模組的選擇性宣告的語法*限定命名空間*是巢狀命名空間名稱的順序，顯示包含的模組。 先前宣告沒有限定的命名空間。

您沒有縮排在最上層模組中的宣告。 您沒有縮排在本機的模組中的所有宣告。 在本機的模組宣告中，只有在該模組宣告會縮排的宣告會是模組的一部分。

如果程式碼檔案開頭不是最上層模組宣告或命名空間宣告，整個檔案的內容，包括本機的任何模組，就會變成隱含建立的最上層模組檔案，不含副檔名，具有相同名稱的一部分第一個字母轉換為大寫。 例如，請考慮下列檔案。

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6601.fs)]

這個檔案會視為已撰寫以這種方式編譯：

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6602.fs)]

如果您有多個模組中的檔案時，您必須使用本機模組宣告每個模組。 如果封入的命名空間宣告，這些模組會封入命名空間的一部分。 如果封入的命名空間未在宣告中，模組就會變成隱含建立的最上層模組的一部分。 下列程式碼範例顯示包含多個模組的程式碼檔案。 編譯器會隱含地建立名為的最上層模組`Multiplemodules`，並`MyModule1`和`MyModule2`該最上層模組中巢狀。

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6603.fs)]

如果您有多個檔案在專案中，或在單一編譯中，或如果您要建置程式庫，您必須包含命名空間宣告或在檔案頂端的模組宣告。 F # 編譯器只會以隱含方式判斷模組名稱在 專案 或 編譯的命令列只能有一個檔案，而且您要建立應用程式時。

*存取範圍修飾詞*可以是下列其中之一： `public`， `private`， `internal`。 如需詳細資訊，請參閱[存取控制](access-control.md)。 預設值是公用。

## <a name="referencing-code-in-modules"></a>在模組中的參考程式碼

當您從另一個模組參考函式、 類型和值時，您必須使用限定的名稱，或開啟模組。 如果您使用限定的名稱，您必須指定命名空間、 模組，以及您想要的程式元素的識別碼。 如下所示以句點 （.） 分隔每個部分的完整路徑。

`Namespace1.Namespace2.ModuleName.Identifier`

您可以開啟模組或一或多個要簡化程式碼的命名空間。 如需有關開啟命名空間和模組的詳細資訊，請參閱[匯入宣告：`open`關鍵字](import-declarations-the-open-keyword.md)。

下列程式碼範例會顯示最上層的模組，其中包含檔案結尾之前的所有程式碼。

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6604.fs)]

若要使用此程式碼，從相同的專案中的另一個檔案，您會使用限定的名稱，或開啟模組才能使用函式，如下列範例所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6605.fs)]

## <a name="nested-modules"></a>巢狀的模組

可以是巢狀模組。 內部的模組必須而言，表示它們是內部的模組，而不是新的模組外部模組宣告縮排。 例如，比較下列兩個範例。 模組`Z`是內部的模組，下列程式碼。

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6607.fs)]

但模組`Z`是模組的同層級`Y`下列程式碼。

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6608.fs)]
模組`Z`也是同層級的模組中的下列程式碼，因為它就不會呈現在模組中的其他宣告就`Y`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6609.fs)]
最後，如果外部模組不有任何宣告，後面緊接跟著另一個模組宣告新的模組宣告會假設為內部的模組，但編譯器會警告您如果第二個模組定義就不會一直呈現 farther 比第一次。

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6610.fs)]
若要排除警告，縮排的內部模組。

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6611.fs)]
如果您想要在單一外部模組中的檔案中的所有程式碼，而且您想要的內部模組，外部模組不需要等號，並不需要的宣告，包括任何內部的模組宣告外部模組中，將會縮排。 內的內部模組宣告的宣告一定要縮排。 下列程式碼示範此案例。

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6612.fs)]

## <a name="recursive-modules"></a>遞迴模組

F # 4.1 引進了模組可讓所有內含的程式碼是相互遞迴的概念。  這透過完成`module rec`。  使用`module rec`可以減輕不能夠撰寫相互參考的程式碼類型和模組之間的一些難題。  這個範例如下：

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

請注意，例外狀況`DontSqueezeTheBananaException`和類別`Banana`都會指向彼此。  此外，模組`BananaHelpers`和類別`Banana`也彼此參考。  這不是來表示 F # 中，如果您移除可能`rec`關鍵字，從`RecursiveModule`模組。

這項功能，也可以在[命名空間](namespaces.md)F # 4.1。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)  
- [命名空間](namespaces.md)  
- [F # RFC FS-1009-允許透過檔案內的較大範圍的相互參考的類型和模組](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)  
