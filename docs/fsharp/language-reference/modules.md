---
title: 模組 (F#)
description: '了解如何 F # 模組是 F # 程式碼，例如值、 類型和函式值，在 F # 程式中的群組。'
ms.date: 04/24/2017
ms.openlocfilehash: fb0aa1d508d1141933b4fbdf10633f67ed078dc7
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44342796"
---
# <a name="modules"></a><span data-ttu-id="5114c-103">模組</span><span class="sxs-lookup"><span data-stu-id="5114c-103">Modules</span></span>

<span data-ttu-id="5114c-104">在 F # 語言的內容*模組*是 F # 程式碼，例如值、 類型和函式值，在 F # 程式中的群組。</span><span class="sxs-lookup"><span data-stu-id="5114c-104">In the context of the F# language, a *module* is a grouping of F# code, such as values, types, and function values, in an F# program.</span></span> <span data-ttu-id="5114c-105">程式碼分組成不同模組有助於將相關程式碼整理到同一處，以及避免程式中發生名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="5114c-105">Grouping code in modules helps keep related code together and helps avoid name conflicts in your program.</span></span>

## <a name="syntax"></a><span data-ttu-id="5114c-106">語法</span><span class="sxs-lookup"><span data-stu-id="5114c-106">Syntax</span></span>

```fsharp
// Top-level module declaration.
module [accessibility-modifier] [qualified-namespace.]module-name
declarations
// Local module declaration.
module [accessibility-modifier] module-name =
    declarations
```

## <a name="remarks"></a><span data-ttu-id="5114c-107">備註</span><span class="sxs-lookup"><span data-stu-id="5114c-107">Remarks</span></span>

<span data-ttu-id="5114c-108">F # 模組是 F # 程式碼建構，例如類型、 值、 函式值，以及程式碼中的群組`do`繫結。</span><span class="sxs-lookup"><span data-stu-id="5114c-108">An F# module is a grouping of F# code constructs such as types, values, function values, and code in `do` bindings.</span></span> <span data-ttu-id="5114c-109">它會實作為具有只有靜態成員的 common language runtime (CLR) 類別。</span><span class="sxs-lookup"><span data-stu-id="5114c-109">It is implemented as a common language runtime (CLR) class that has only static members.</span></span> <span data-ttu-id="5114c-110">有兩種類型的模組宣告、 根據是否包含在模組中的整份檔案： 最上層模組宣告和本機模組宣告。</span><span class="sxs-lookup"><span data-stu-id="5114c-110">There are two types of module declarations, depending on whether the whole file is included in the module: a top-level module declaration and a local module declaration.</span></span> <span data-ttu-id="5114c-111">最上層模組宣告包含在模組中的整個檔案。</span><span class="sxs-lookup"><span data-stu-id="5114c-111">A top-level module declaration includes the whole file in the module.</span></span> <span data-ttu-id="5114c-112">最上層模組宣告只可以顯示為檔案中的第一個宣告。</span><span class="sxs-lookup"><span data-stu-id="5114c-112">A top-level module declaration can appear only as the first declaration in a file.</span></span>

<span data-ttu-id="5114c-113">在最上層模組的選擇性宣告的語法*限定命名空間*是巢狀命名空間名稱的順序，顯示包含的模組。</span><span class="sxs-lookup"><span data-stu-id="5114c-113">In the syntax for the top-level module declaration, the optional *qualified-namespace* is the sequence of nested namespace names that contains the module.</span></span> <span data-ttu-id="5114c-114">先前宣告沒有限定的命名空間。</span><span class="sxs-lookup"><span data-stu-id="5114c-114">The qualified namespace does not have to be previously declared.</span></span>

<span data-ttu-id="5114c-115">您沒有縮排在最上層模組中的宣告。</span><span class="sxs-lookup"><span data-stu-id="5114c-115">You do not have to indent declarations in a top-level module.</span></span> <span data-ttu-id="5114c-116">您沒有縮排在本機的模組中的所有宣告。</span><span class="sxs-lookup"><span data-stu-id="5114c-116">You do have to indent all declarations in local modules.</span></span> <span data-ttu-id="5114c-117">在本機的模組宣告中，只有在該模組宣告會縮排的宣告會是模組的一部分。</span><span class="sxs-lookup"><span data-stu-id="5114c-117">In a local module declaration, only the declarations that are indented under that module declaration are part of the module.</span></span>

<span data-ttu-id="5114c-118">如果程式碼檔案開頭不是最上層模組宣告或命名空間宣告，整個檔案的內容，包括本機的任何模組，就會變成隱含建立的最上層模組檔案，不含副檔名，具有相同名稱的一部分第一個字母轉換為大寫。</span><span class="sxs-lookup"><span data-stu-id="5114c-118">If a code file does not begin with a top-level module declaration or a namespace declaration, the whole contents of the file, including any local modules, becomes part of an implicitly created top-level module that has the same name as the file, without the extension, with the first letter converted to uppercase.</span></span> <span data-ttu-id="5114c-119">例如，請考慮下列檔案。</span><span class="sxs-lookup"><span data-stu-id="5114c-119">For example, consider the following file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6601.fs)]

<span data-ttu-id="5114c-120">這個檔案會視為已撰寫以這種方式編譯：</span><span class="sxs-lookup"><span data-stu-id="5114c-120">This file would be compiled as if it were written in this manner:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6602.fs)]

<span data-ttu-id="5114c-121">如果您有多個模組中的檔案時，您必須使用本機模組宣告每個模組。</span><span class="sxs-lookup"><span data-stu-id="5114c-121">If you have multiple modules in a file, you must use a local module declaration for each module.</span></span> <span data-ttu-id="5114c-122">如果封入的命名空間宣告，這些模組會封入命名空間的一部分。</span><span class="sxs-lookup"><span data-stu-id="5114c-122">If an enclosing namespace is declared, these modules are part of the enclosing namespace.</span></span> <span data-ttu-id="5114c-123">如果封入的命名空間未在宣告中，模組就會變成隱含建立的最上層模組的一部分。</span><span class="sxs-lookup"><span data-stu-id="5114c-123">If an enclosing namespace is not declared, the modules become part of the implicitly created top-level module.</span></span> <span data-ttu-id="5114c-124">下列程式碼範例顯示包含多個模組的程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="5114c-124">The following code example shows a code file that contains multiple modules.</span></span> <span data-ttu-id="5114c-125">編譯器會隱含地建立名為的最上層模組`Multiplemodules`，並`MyModule1`和`MyModule2`該最上層模組中巢狀。</span><span class="sxs-lookup"><span data-stu-id="5114c-125">The compiler implicitly creates a top-level module named `Multiplemodules`, and `MyModule1` and `MyModule2` are nested in that top-level module.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6603.fs)]

<span data-ttu-id="5114c-126">如果您有多個檔案在專案中，或在單一編譯中，或如果您要建置程式庫，您必須包含命名空間宣告或在檔案頂端的模組宣告。</span><span class="sxs-lookup"><span data-stu-id="5114c-126">If you have multiple files in a project or in a single compilation, or if you are building a library, you must include a namespace declaration or module declaration at the top of the file.</span></span> <span data-ttu-id="5114c-127">F # 編譯器只會以隱含方式判斷模組名稱在 專案 或 編譯的命令列只能有一個檔案，而且您要建立應用程式時。</span><span class="sxs-lookup"><span data-stu-id="5114c-127">The F# compiler only determines a module name implicitly when there is only one file in a project or compilation command line, and you are creating an application.</span></span>

<span data-ttu-id="5114c-128">*存取範圍修飾詞*可以是下列其中之一： `public`， `private`， `internal`。</span><span class="sxs-lookup"><span data-stu-id="5114c-128">The *accessibility-modifier* can be one of the following: `public`, `private`, `internal`.</span></span> <span data-ttu-id="5114c-129">如需詳細資訊，請參閱[存取控制](access-control.md)。</span><span class="sxs-lookup"><span data-stu-id="5114c-129">For more information, see [Access Control](access-control.md).</span></span> <span data-ttu-id="5114c-130">預設值是公用。</span><span class="sxs-lookup"><span data-stu-id="5114c-130">The default is public.</span></span>

## <a name="referencing-code-in-modules"></a><span data-ttu-id="5114c-131">在模組中的參考程式碼</span><span class="sxs-lookup"><span data-stu-id="5114c-131">Referencing Code in Modules</span></span>

<span data-ttu-id="5114c-132">當您從另一個模組參考函式、 類型和值時，您必須使用限定的名稱，或開啟模組。</span><span class="sxs-lookup"><span data-stu-id="5114c-132">When you reference functions, types, and values from another module, you must either use a qualified name or open the module.</span></span> <span data-ttu-id="5114c-133">如果您使用限定的名稱，您必須指定命名空間、 模組，以及您想要的程式元素的識別碼。</span><span class="sxs-lookup"><span data-stu-id="5114c-133">If you use a qualified name, you must specify the namespaces, the module, and the identifier for the program element you want.</span></span> <span data-ttu-id="5114c-134">如下所示以句點 （.） 分隔每個部分的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="5114c-134">You separate each part of the qualified path with a dot (.), as follows.</span></span>

`Namespace1.Namespace2.ModuleName.Identifier`

<span data-ttu-id="5114c-135">您可以開啟模組或一或多個要簡化程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="5114c-135">You can open the module or one or more of the namespaces to simplify the code.</span></span> <span data-ttu-id="5114c-136">如需有關開啟命名空間和模組的詳細資訊，請參閱[匯入宣告：`open`關鍵字](import-declarations-the-open-keyword.md)。</span><span class="sxs-lookup"><span data-stu-id="5114c-136">For more information about opening namespaces and modules, see [Import Declarations: The `open` Keyword](import-declarations-the-open-keyword.md).</span></span>

<span data-ttu-id="5114c-137">下列程式碼範例會顯示最上層的模組，其中包含檔案結尾之前的所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="5114c-137">The following code example shows a top-level module that contains all the code up to the end of the file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6604.fs)]

<span data-ttu-id="5114c-138">若要使用此程式碼，從相同的專案中的另一個檔案，您會使用限定的名稱，或開啟模組才能使用函式，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="5114c-138">To use this code from another file in the same project, you either use qualified names or you open the module before you use the functions, as shown in the following examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6605.fs)]

## <a name="nested-modules"></a><span data-ttu-id="5114c-139">巢狀的模組</span><span class="sxs-lookup"><span data-stu-id="5114c-139">Nested Modules</span></span>

<span data-ttu-id="5114c-140">可以是巢狀模組。</span><span class="sxs-lookup"><span data-stu-id="5114c-140">Modules can be nested.</span></span> <span data-ttu-id="5114c-141">內部的模組必須而言，表示它們是內部的模組，而不是新的模組外部模組宣告縮排。</span><span class="sxs-lookup"><span data-stu-id="5114c-141">Inner modules must be indented as far as outer module declarations to indicate that they are inner modules, not new modules.</span></span> <span data-ttu-id="5114c-142">例如，比較下列兩個範例。</span><span class="sxs-lookup"><span data-stu-id="5114c-142">For example, compare the following two examples.</span></span> <span data-ttu-id="5114c-143">模組`Z`是內部的模組，下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="5114c-143">Module `Z` is an inner module in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6607.fs)]

<span data-ttu-id="5114c-144">但模組`Z`是模組的同層級`Y`下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="5114c-144">But module `Z` is a sibling to module `Y` in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6608.fs)]
<span data-ttu-id="5114c-145">模組`Z`也是同層級的模組中的下列程式碼，因為它就不會呈現在模組中的其他宣告就`Y`。</span><span class="sxs-lookup"><span data-stu-id="5114c-145">Module `Z` is also a sibling module in the following code, because it is not indented as far as other declarations in module `Y`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6609.fs)]
<span data-ttu-id="5114c-146">最後，如果外部模組不有任何宣告，後面緊接跟著另一個模組宣告新的模組宣告會假設為內部的模組，但編譯器會警告您如果第二個模組定義就不會一直呈現 farther 比第一次。</span><span class="sxs-lookup"><span data-stu-id="5114c-146">Finally, if the outer module has no declarations and is followed immediately by another module declaration, the new module declaration is assumed to be an inner module, but the compiler will warn you if the second module definition is not indented farther than the first.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6610.fs)]
<span data-ttu-id="5114c-147">若要排除警告，縮排的內部模組。</span><span class="sxs-lookup"><span data-stu-id="5114c-147">To eliminate the warning, indent the inner module.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6611.fs)]
<span data-ttu-id="5114c-148">如果您想要在單一外部模組中的檔案中的所有程式碼，而且您想要的內部模組，外部模組不需要等號，並不需要的宣告，包括任何內部的模組宣告外部模組中，將會縮排。</span><span class="sxs-lookup"><span data-stu-id="5114c-148">If you want all the code in a file to be in a single outer module and you want inner modules, the outer module does not require the equal sign, and the declarations, including any inner module declarations, that will go in the outer module do not have to be indented.</span></span> <span data-ttu-id="5114c-149">內的內部模組宣告的宣告一定要縮排。</span><span class="sxs-lookup"><span data-stu-id="5114c-149">Declarations inside the inner module declarations do have to be indented.</span></span> <span data-ttu-id="5114c-150">下列程式碼示範此案例。</span><span class="sxs-lookup"><span data-stu-id="5114c-150">The following code shows this case.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6612.fs)]

## <a name="recursive-modules"></a><span data-ttu-id="5114c-151">遞迴模組</span><span class="sxs-lookup"><span data-stu-id="5114c-151">Recursive modules</span></span>

<span data-ttu-id="5114c-152">F # 4.1 引進了模組可讓所有內含的程式碼是相互遞迴的概念。</span><span class="sxs-lookup"><span data-stu-id="5114c-152">F# 4.1 introduces the notion of modules which allow for all contained code to be mutually recursive.</span></span>  <span data-ttu-id="5114c-153">這透過完成`module rec`。</span><span class="sxs-lookup"><span data-stu-id="5114c-153">This is done via `module rec`.</span></span>  <span data-ttu-id="5114c-154">使用`module rec`可以減輕不能夠撰寫相互參考的程式碼類型和模組之間的一些難題。</span><span class="sxs-lookup"><span data-stu-id="5114c-154">Use of `module rec` can alleviate some pains in not being able to write mutually referential code between types and modules.</span></span>  <span data-ttu-id="5114c-155">這個範例如下：</span><span class="sxs-lookup"><span data-stu-id="5114c-155">The following is an example of this:</span></span>

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

<span data-ttu-id="5114c-156">請注意，例外狀況`DontSqueezeTheBananaException`和類別`Banana`都會指向彼此。</span><span class="sxs-lookup"><span data-stu-id="5114c-156">Note that the exception `DontSqueezeTheBananaException` and the class `Banana` both refer to each other.</span></span>  <span data-ttu-id="5114c-157">此外，模組`BananaHelpers`和類別`Banana`也彼此參考。</span><span class="sxs-lookup"><span data-stu-id="5114c-157">Additionally, the module `BananaHelpers` and the class `Banana` also refer to each other.</span></span>  <span data-ttu-id="5114c-158">這不是來表示 F # 中，如果您移除可能`rec`關鍵字，從`RecursiveModule`模組。</span><span class="sxs-lookup"><span data-stu-id="5114c-158">This would not be possible to express in F# if you removed the `rec` keyword from the `RecursiveModule` module.</span></span>

<span data-ttu-id="5114c-159">這項功能，也可以在[命名空間](namespaces.md)F # 4.1。</span><span class="sxs-lookup"><span data-stu-id="5114c-159">This capability is also possible in [Namespaces](namespaces.md) with F# 4.1.</span></span>

## <a name="see-also"></a><span data-ttu-id="5114c-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5114c-160">See also</span></span>

- [<span data-ttu-id="5114c-161">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="5114c-161">F# Language Reference</span></span>](index.md)  
- [<span data-ttu-id="5114c-162">命名空間</span><span class="sxs-lookup"><span data-stu-id="5114c-162">Namespaces</span></span>](namespaces.md)  
- [<span data-ttu-id="5114c-163">F # RFC FS-1009-允許透過檔案內的較大範圍的相互參考的類型和模組</span><span class="sxs-lookup"><span data-stu-id="5114c-163">F# RFC FS-1009 - Allow mutually referential types and modules over larger scopes within files</span></span>](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)  
