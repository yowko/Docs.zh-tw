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
# <a name="modules"></a><span data-ttu-id="90e99-103">模組</span><span class="sxs-lookup"><span data-stu-id="90e99-103">Modules</span></span>

<span data-ttu-id="90e99-104">在F#語言的內容中,*模組*是F# F#程式碼的群組, 例如值、類型和函數值。</span><span class="sxs-lookup"><span data-stu-id="90e99-104">In the context of the F# language, a *module* is a grouping of F# code, such as values, types, and function values, in an F# program.</span></span> <span data-ttu-id="90e99-105">程式碼分組成不同模組有助於將相關程式碼整理到同一處，以及避免程式中發生名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="90e99-105">Grouping code in modules helps keep related code together and helps avoid name conflicts in your program.</span></span>

## <a name="syntax"></a><span data-ttu-id="90e99-106">語法</span><span class="sxs-lookup"><span data-stu-id="90e99-106">Syntax</span></span>

```fsharp
// Top-level module declaration.
module [accessibility-modifier] [qualified-namespace.]module-name
declarations
// Local module declaration.
module [accessibility-modifier] module-name =
    declarations
```

## <a name="remarks"></a><span data-ttu-id="90e99-107">備註</span><span class="sxs-lookup"><span data-stu-id="90e99-107">Remarks</span></span>

<span data-ttu-id="90e99-108">F#模組是程式F#代碼結構的群組, 例如類型、值、函數值和系結中`do`的程式碼。</span><span class="sxs-lookup"><span data-stu-id="90e99-108">An F# module is a grouping of F# code constructs such as types, values, function values, and code in `do` bindings.</span></span> <span data-ttu-id="90e99-109">它會實作為僅具有靜態成員的 common language runtime (CLR) 類別。</span><span class="sxs-lookup"><span data-stu-id="90e99-109">It is implemented as a common language runtime (CLR) class that has only static members.</span></span> <span data-ttu-id="90e99-110">有兩種類型的模組宣告, 視模組中是否包含整個檔案而定: 最上層模組宣告和本機模組宣告。</span><span class="sxs-lookup"><span data-stu-id="90e99-110">There are two types of module declarations, depending on whether the whole file is included in the module: a top-level module declaration and a local module declaration.</span></span> <span data-ttu-id="90e99-111">最上層模組宣告包含模組中的整個檔案。</span><span class="sxs-lookup"><span data-stu-id="90e99-111">A top-level module declaration includes the whole file in the module.</span></span> <span data-ttu-id="90e99-112">最上層模組宣告只能出現為檔案中的第一個宣告。</span><span class="sxs-lookup"><span data-stu-id="90e99-112">A top-level module declaration can appear only as the first declaration in a file.</span></span>

<span data-ttu-id="90e99-113">在最上層模組宣告的語法中, 選擇性的*限定命名空間*是包含模組之嵌套命名空間名稱的序列。</span><span class="sxs-lookup"><span data-stu-id="90e99-113">In the syntax for the top-level module declaration, the optional *qualified-namespace* is the sequence of nested namespace names that contains the module.</span></span> <span data-ttu-id="90e99-114">限定的命名空間不一定要預先宣告。</span><span class="sxs-lookup"><span data-stu-id="90e99-114">The qualified namespace does not have to be previously declared.</span></span>

<span data-ttu-id="90e99-115">您不需要在最上層模組中縮排宣告。</span><span class="sxs-lookup"><span data-stu-id="90e99-115">You do not have to indent declarations in a top-level module.</span></span> <span data-ttu-id="90e99-116">您必須將本機模組中的所有宣告縮排。</span><span class="sxs-lookup"><span data-stu-id="90e99-116">You do have to indent all declarations in local modules.</span></span> <span data-ttu-id="90e99-117">在本機模組宣告中, 只有在該模組宣告下縮排的宣告是模組的一部分。</span><span class="sxs-lookup"><span data-stu-id="90e99-117">In a local module declaration, only the declarations that are indented under that module declaration are part of the module.</span></span>

<span data-ttu-id="90e99-118">如果程式碼檔案不是以最上層模組宣告或命名空間宣告開頭, 則檔案的整個內容 (包括任何本機模組) 會成為隱含建立之最上層模組的一部分, 該模組具有與檔案相同的名稱, 但不含副檔名。第一個字母轉換成大寫。</span><span class="sxs-lookup"><span data-stu-id="90e99-118">If a code file does not begin with a top-level module declaration or a namespace declaration, the whole contents of the file, including any local modules, becomes part of an implicitly created top-level module that has the same name as the file, without the extension, with the first letter converted to uppercase.</span></span> <span data-ttu-id="90e99-119">例如, 請考慮下列檔案。</span><span class="sxs-lookup"><span data-stu-id="90e99-119">For example, consider the following file.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6601.fs)]

<span data-ttu-id="90e99-120">這個檔案會編譯成以這種方式撰寫的:</span><span class="sxs-lookup"><span data-stu-id="90e99-120">This file would be compiled as if it were written in this manner:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6602.fs)]

<span data-ttu-id="90e99-121">如果您在檔案中有多個模組, 您必須針對每個模組使用本機模組宣告。</span><span class="sxs-lookup"><span data-stu-id="90e99-121">If you have multiple modules in a file, you must use a local module declaration for each module.</span></span> <span data-ttu-id="90e99-122">如果宣告了封閉式命名空間, 這些模組就是封閉命名空間的一部分。</span><span class="sxs-lookup"><span data-stu-id="90e99-122">If an enclosing namespace is declared, these modules are part of the enclosing namespace.</span></span> <span data-ttu-id="90e99-123">如果未宣告封入命名空間, 則模組會成為隱含建立之最上層模組的一部分。</span><span class="sxs-lookup"><span data-stu-id="90e99-123">If an enclosing namespace is not declared, the modules become part of the implicitly created top-level module.</span></span> <span data-ttu-id="90e99-124">下列程式碼範例顯示包含多個模組的程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="90e99-124">The following code example shows a code file that contains multiple modules.</span></span> <span data-ttu-id="90e99-125">編譯器會隱含地建立名為`Multiplemodules`的最上層模組`MyModule1` , 而`MyModule2`和會嵌套在該最上層的模組中。</span><span class="sxs-lookup"><span data-stu-id="90e99-125">The compiler implicitly creates a top-level module named `Multiplemodules`, and `MyModule1` and `MyModule2` are nested in that top-level module.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6603.fs)]

<span data-ttu-id="90e99-126">如果您在專案或單一編譯中有多個檔案, 或者如果您要建立程式庫, 則必須在檔案頂端包含命名空間宣告或模組宣告。</span><span class="sxs-lookup"><span data-stu-id="90e99-126">If you have multiple files in a project or in a single compilation, or if you are building a library, you must include a namespace declaration or module declaration at the top of the file.</span></span> <span data-ttu-id="90e99-127">當F#專案或編譯命令列中只有一個檔案, 而且您正在建立應用程式時, 編譯器只會隱含地判斷模組名稱。</span><span class="sxs-lookup"><span data-stu-id="90e99-127">The F# compiler only determines a module name implicitly when there is only one file in a project or compilation command line, and you are creating an application.</span></span>

<span data-ttu-id="90e99-128">*協助工具修飾*詞可以是下列其中一項: `public`、 `private`、 `internal`。</span><span class="sxs-lookup"><span data-stu-id="90e99-128">The *accessibility-modifier* can be one of the following: `public`, `private`, `internal`.</span></span> <span data-ttu-id="90e99-129">如需詳細資訊，請參閱[存取控制](access-control.md)。</span><span class="sxs-lookup"><span data-stu-id="90e99-129">For more information, see [Access Control](access-control.md).</span></span> <span data-ttu-id="90e99-130">預設值是公用。</span><span class="sxs-lookup"><span data-stu-id="90e99-130">The default is public.</span></span>

## <a name="referencing-code-in-modules"></a><span data-ttu-id="90e99-131">參考模組中的程式碼</span><span class="sxs-lookup"><span data-stu-id="90e99-131">Referencing Code in Modules</span></span>

<span data-ttu-id="90e99-132">當您從另一個模組參考函數、類型和值時, 您必須使用限定名稱或開啟模組。</span><span class="sxs-lookup"><span data-stu-id="90e99-132">When you reference functions, types, and values from another module, you must either use a qualified name or open the module.</span></span> <span data-ttu-id="90e99-133">如果您使用限定名稱, 則必須指定命名空間、模組, 以及所需之程式元素的識別碼。</span><span class="sxs-lookup"><span data-stu-id="90e99-133">If you use a qualified name, you must specify the namespaces, the module, and the identifier for the program element you want.</span></span> <span data-ttu-id="90e99-134">您可以使用點 (.) 來分隔限定路徑的每個部分, 如下所示。</span><span class="sxs-lookup"><span data-stu-id="90e99-134">You separate each part of the qualified path with a dot (.), as follows.</span></span>

`Namespace1.Namespace2.ModuleName.Identifier`

<span data-ttu-id="90e99-135">您可以開啟模組或一或多個命名空間, 以簡化程式碼。</span><span class="sxs-lookup"><span data-stu-id="90e99-135">You can open the module or one or more of the namespaces to simplify the code.</span></span> <span data-ttu-id="90e99-136">如需有關開啟命名空間和模組的詳細[資訊, 請參閱匯入宣告:`open`關鍵字。](import-declarations-the-open-keyword.md)</span><span class="sxs-lookup"><span data-stu-id="90e99-136">For more information about opening namespaces and modules, see [Import Declarations: The `open` Keyword](import-declarations-the-open-keyword.md).</span></span>

<span data-ttu-id="90e99-137">下列程式碼範例顯示最上層模組, 其中包含直到檔案結尾為止的所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="90e99-137">The following code example shows a top-level module that contains all the code up to the end of the file.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6604.fs)]

<span data-ttu-id="90e99-138">若要從相同專案中的另一個檔案使用此程式碼, 您可以使用限定名稱, 或在使用函式之前開啟模組, 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="90e99-138">To use this code from another file in the same project, you either use qualified names or you open the module before you use the functions, as shown in the following examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6605.fs)]

## <a name="nested-modules"></a><span data-ttu-id="90e99-139">嵌套模組</span><span class="sxs-lookup"><span data-stu-id="90e99-139">Nested Modules</span></span>

<span data-ttu-id="90e99-140">模組可以嵌套。</span><span class="sxs-lookup"><span data-stu-id="90e99-140">Modules can be nested.</span></span> <span data-ttu-id="90e99-141">內部模組必須縮排為外部模組宣告, 以表示它們是內部模組, 而不是新模組。</span><span class="sxs-lookup"><span data-stu-id="90e99-141">Inner modules must be indented as far as outer module declarations to indicate that they are inner modules, not new modules.</span></span> <span data-ttu-id="90e99-142">例如, 比較下列兩個範例。</span><span class="sxs-lookup"><span data-stu-id="90e99-142">For example, compare the following two examples.</span></span> <span data-ttu-id="90e99-143">模組`Z`是下列程式碼中的內部模組。</span><span class="sxs-lookup"><span data-stu-id="90e99-143">Module `Z` is an inner module in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6607.fs)]

<span data-ttu-id="90e99-144">但是模組`Z`在下列程式碼中`Y`是模組的同級。</span><span class="sxs-lookup"><span data-stu-id="90e99-144">But module `Z` is a sibling to module `Y` in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6608.fs)]
<span data-ttu-id="90e99-145">模組`Z`也是下列程式碼中的同輩模組, 因為它不會縮排至模組`Y`中的其他宣告。</span><span class="sxs-lookup"><span data-stu-id="90e99-145">Module `Z` is also a sibling module in the following code, because it is not indented as far as other declarations in module `Y`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6609.fs)]
<span data-ttu-id="90e99-146">最後, 如果外部模組沒有宣告, 後面緊接著另一個模組宣告, 則會假設新的模組宣告為內部模組, 但編譯器會在第二個模組定義的縮排距離比頭.</span><span class="sxs-lookup"><span data-stu-id="90e99-146">Finally, if the outer module has no declarations and is followed immediately by another module declaration, the new module declaration is assumed to be an inner module, but the compiler will warn you if the second module definition is not indented farther than the first.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6610.fs)]
<span data-ttu-id="90e99-147">若要排除警告, 請將內部模組縮排。</span><span class="sxs-lookup"><span data-stu-id="90e99-147">To eliminate the warning, indent the inner module.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6611.fs)]
<span data-ttu-id="90e99-148">如果您想要將檔案中的所有程式碼都放在單一外部模組中, 而您想要使用內部模組, 則外部模組不需要等號, 而且外部模組中的宣告 (包括任何內部模組宣告) 都不必縮排。</span><span class="sxs-lookup"><span data-stu-id="90e99-148">If you want all the code in a file to be in a single outer module and you want inner modules, the outer module does not require the equal sign, and the declarations, including any inner module declarations, that will go in the outer module do not have to be indented.</span></span> <span data-ttu-id="90e99-149">內部模組宣告內的宣告必須縮排。</span><span class="sxs-lookup"><span data-stu-id="90e99-149">Declarations inside the inner module declarations do have to be indented.</span></span> <span data-ttu-id="90e99-150">下列程式碼會顯示這種情況。</span><span class="sxs-lookup"><span data-stu-id="90e99-150">The following code shows this case.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6612.fs)]

## <a name="recursive-modules"></a><span data-ttu-id="90e99-151">遞迴模組</span><span class="sxs-lookup"><span data-stu-id="90e99-151">Recursive modules</span></span>

<span data-ttu-id="90e99-152">F#4.1 引進模組的概念, 可讓所有包含的程式碼互相遞迴。</span><span class="sxs-lookup"><span data-stu-id="90e99-152">F# 4.1 introduces the notion of modules which allow for all contained code to be mutually recursive.</span></span>  <span data-ttu-id="90e99-153">這是透過來`module rec`完成。</span><span class="sxs-lookup"><span data-stu-id="90e99-153">This is done via `module rec`.</span></span>  <span data-ttu-id="90e99-154">`module rec`使用可減輕無法在類型和模組之間撰寫相互引用程式碼的一些難題。</span><span class="sxs-lookup"><span data-stu-id="90e99-154">Use of `module rec` can alleviate some pains in not being able to write mutually referential code between types and modules.</span></span>  <span data-ttu-id="90e99-155">以下是這種情況的範例:</span><span class="sxs-lookup"><span data-stu-id="90e99-155">The following is an example of this:</span></span>

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

<span data-ttu-id="90e99-156">請注意, 例外`DontSqueezeTheBananaException`狀況和類別`Banana`都會彼此參考。</span><span class="sxs-lookup"><span data-stu-id="90e99-156">Note that the exception `DontSqueezeTheBananaException` and the class `Banana` both refer to each other.</span></span>  <span data-ttu-id="90e99-157">此外, 模組`BananaHelpers`和類別`Banana`也會彼此參考。</span><span class="sxs-lookup"><span data-stu-id="90e99-157">Additionally, the module `BananaHelpers` and the class `Banana` also refer to each other.</span></span>  <span data-ttu-id="90e99-158">如果您已從F# `rec` `RecursiveModule`模組中移除關鍵字, 這將無法在中表示。</span><span class="sxs-lookup"><span data-stu-id="90e99-158">This would not be possible to express in F# if you removed the `rec` keyword from the `RecursiveModule` module.</span></span>

<span data-ttu-id="90e99-159">這項功能也可以在具有 4.1 F#的[命名空間](namespaces.md)中使用。</span><span class="sxs-lookup"><span data-stu-id="90e99-159">This capability is also possible in [Namespaces](namespaces.md) with F# 4.1.</span></span>

## <a name="see-also"></a><span data-ttu-id="90e99-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90e99-160">See also</span></span>

- [<span data-ttu-id="90e99-161">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="90e99-161">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="90e99-162">命名空間</span><span class="sxs-lookup"><span data-stu-id="90e99-162">Namespaces</span></span>](namespaces.md)
- [<span data-ttu-id="90e99-163">F#RFC FS-1009-允許檔案內的相互參考型別和模組超過更大的範圍</span><span class="sxs-lookup"><span data-stu-id="90e99-163">F# RFC FS-1009 - Allow mutually referential types and modules over larger scopes within files</span></span>](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
