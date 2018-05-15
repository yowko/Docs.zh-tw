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
# <a name="namespaces"></a><span data-ttu-id="7c6e3-103">命名空間</span><span class="sxs-lookup"><span data-stu-id="7c6e3-103">Namespaces</span></span>

<span data-ttu-id="7c6e3-104">命名空間可讓您將名稱附加至程式項目群組，將程式碼依相關功能分類。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-104">A namespace lets you organize code into areas of related functionality by enabling you to attach a name to a grouping of program elements.</span></span>


## <a name="syntax"></a><span data-ttu-id="7c6e3-105">語法</span><span class="sxs-lookup"><span data-stu-id="7c6e3-105">Syntax</span></span>

```fsharp
namespace [parent-namespaces.]identifier
```

## <a name="remarks"></a><span data-ttu-id="7c6e3-106">備註</span><span class="sxs-lookup"><span data-stu-id="7c6e3-106">Remarks</span></span>
<span data-ttu-id="7c6e3-107">如果您想要將程式碼放在命名空間中，在檔案中的第一個宣告必須宣告命名空間。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-107">If you want to put code in a namespace, the first declaration in the file must declare the namespace.</span></span> <span data-ttu-id="7c6e3-108">整個檔案的內容就會變成命名空間的一部分。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-108">The contents of the entire file then become part of the namespace.</span></span>

<span data-ttu-id="7c6e3-109">命名空間不能直接包含的值和函式。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-109">Namespaces cannot directly contain values and functions.</span></span> <span data-ttu-id="7c6e3-110">值和函式必須包含在模組中，而模組包含的命名空間中。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-110">Instead, values and functions must be included in modules, and modules are included in namespaces.</span></span> <span data-ttu-id="7c6e3-111">命名空間包含的模組類型。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-111">Namespaces can contain types, modules.</span></span>

<span data-ttu-id="7c6e3-112">命名空間可以明確宣告命名空間關鍵字，或以隱含方式宣告的模組時。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-112">Namespaces can be declared explicitly with the namespace keyword, or implicitly when declaring a module.</span></span> <span data-ttu-id="7c6e3-113">若要明確宣告命名空間，請使用命名空間關鍵字後面加上命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-113">To declare a namespace explicitly, use the namespace keyword followed by the namespace name.</span></span> <span data-ttu-id="7c6e3-114">下列範例示範具有類型和模組包含該命名空間中宣告命名空間 Widget 的程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-114">The following example shows a code file that declares a namespace Widgets with a type and a module included in that namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

<span data-ttu-id="7c6e3-115">如果其中一個模組中檔案的整個內容，您也可以宣告命名空間以隱含方式使用`module`關鍵字並提供完整的模組名稱中的新命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-115">If the entire contents of the file are in one module, you can also declare namespaces implicitly by using the `module` keyword and providing the new namespace name in the fully qualified module name.</span></span> <span data-ttu-id="7c6e3-116">下列範例示範宣告命名空間的程式碼檔案`Widgets`和模組`WidgetsModule`，其中包含函式。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-116">The following example shows a code file that declares a namespace `Widgets` and a module `WidgetsModule`, which contains a function.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

<span data-ttu-id="7c6e3-117">下列程式碼相當於上述的程式碼，但模組是本機模組宣告。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-117">The following code is equivalent to the preceding code, but the module is a local module declaration.</span></span> <span data-ttu-id="7c6e3-118">在此情況下，命名空間必須出現在自己的那一行。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-118">In that case, the namespace must appear on its own line.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/namespaces/snippet6402.fs)]

<span data-ttu-id="7c6e3-119">如果多個模組需要一個或多個命名空間中相同的檔案中，您必須使用本機模組宣告。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-119">If more than one module is required in the same file in one or more namespaces, you must use local module declarations.</span></span> <span data-ttu-id="7c6e3-120">當您使用本機模組宣告時，您無法使用限定的命名空間模組宣告中。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-120">When you use local module declarations, you cannot use the qualified namespace in the module declarations.</span></span> <span data-ttu-id="7c6e3-121">下列程式碼會示範具有命名空間宣告和兩個本機模組宣告的檔案。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-121">The following code shows a file that has a namespace declaration and two local module declarations.</span></span> <span data-ttu-id="7c6e3-122">在此情況下，模組會直接包含在命名空間。具有相同名稱的檔案沒有隱含建立的模組。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-122">In this case, the modules are contained directly in the namespace; there is no implicitly created module that has the same name as the file.</span></span> <span data-ttu-id="7c6e3-123">任何其他程式碼在檔案中，例如`do`繫結，是在命名空間，但不是在內部的模組中，因此您需要限定模組成員`widgetFunction`使用模組名稱。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-123">Any other code in the file, such as a `do` binding, is in the namespace but not in the inner modules, so you need to qualify the module member `widgetFunction` by using the module name.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

<span data-ttu-id="7c6e3-124">此範例的輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-124">The output of this example is as follows.</span></span>

```fsharp
Module1 10 20
Module2 5 6
```

<span data-ttu-id="7c6e3-125">如需詳細資訊，請參閱[模組](modules.md)。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-125">For more information, see [Modules](modules.md).</span></span>

## <a name="nested-namespaces"></a><span data-ttu-id="7c6e3-126">巢狀命名空間</span><span class="sxs-lookup"><span data-stu-id="7c6e3-126">Nested Namespaces</span></span>
<span data-ttu-id="7c6e3-127">當您建立巢狀命名空間時，您必須完整限定。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-127">When you create a nested namespace, you must fully qualify it.</span></span> <span data-ttu-id="7c6e3-128">否則，您會建立新的最上層命名空間。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-128">Otherwise, you create a new top-level namespace.</span></span> <span data-ttu-id="7c6e3-129">命名空間宣告中，會忽略縮排。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-129">Indentation is ignored in namespace declarations.</span></span>

<span data-ttu-id="7c6e3-130">下列範例會示範如何宣告巢狀命名空間。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-130">The following example shows how to declare a nested namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a><span data-ttu-id="7c6e3-131">檔案和組件中的命名空間</span><span class="sxs-lookup"><span data-stu-id="7c6e3-131">Namespaces in Files and Assemblies</span></span>
<span data-ttu-id="7c6e3-132">命名空間可以跨越多個檔案中的單一專案或編譯。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-132">Namespaces can span multiple files in a single project or compilation.</span></span> <span data-ttu-id="7c6e3-133">詞彙*命名空間片段*描述包含在一個檔案中的命名空間的一部分。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-133">The term *namespace fragment* describes the part of a namespace that is included in one file.</span></span> <span data-ttu-id="7c6e3-134">命名空間也可以跨越多個組件。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-134">Namespaces can also span multiple assemblies.</span></span> <span data-ttu-id="7c6e3-135">例如，`System`命名空間包含整個.NET Framework 中，跨越許多組件，並且包含許多巢狀命名空間。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-135">For example, the `System` namespace includes the whole .NET Framework, which spans many assemblies and contains many nested namespaces.</span></span>


## <a name="global-namespace"></a><span data-ttu-id="7c6e3-136">全域命名空間</span><span class="sxs-lookup"><span data-stu-id="7c6e3-136">Global Namespace</span></span>
<span data-ttu-id="7c6e3-137">您使用預先定義的命名空間`global`，將名稱置於.NET 最上層命名空間。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-137">You use the predefined namespace `global` to put names in the .NET top-level namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

<span data-ttu-id="7c6e3-138">您也可以使用全域參考最上層的.NET 命名空間，例如，若要解決與其他命名空間的名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-138">You can also use global to reference the top-level .NET namespace, for example, to resolve name conflicts with other namespaces.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

## <a name="recursive-namespaces"></a><span data-ttu-id="7c6e3-139">遞迴命名空間</span><span class="sxs-lookup"><span data-stu-id="7c6e3-139">Recursive namespaces</span></span>

<span data-ttu-id="7c6e3-140">F # 4.1 導入的命名空間可讓所有包含的程式碼是相互遞迴的概念。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-140">F# 4.1 introduces the notion of namespaces which allow for all contained code to be mutually recursive.</span></span>  <span data-ttu-id="7c6e3-141">這是透過`namespace rec`。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-141">This is done via `namespace rec`.</span></span>  <span data-ttu-id="7c6e3-142">使用`namespace rec`可以減輕無法撰寫相互參考的程式碼類型和模組之間的一些難題。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-142">Use of `namespace rec` can alleviate some pains in not being able to write mutually referential code between types and modules.</span></span>  <span data-ttu-id="7c6e3-143">此動作的範例如下：</span><span class="sxs-lookup"><span data-stu-id="7c6e3-143">The following is an example of this:</span></span>

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

<span data-ttu-id="7c6e3-144">請注意，例外狀況`DontSqueezeTheBananaException`和類別`Banana`兩者來互相參考。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-144">Note that the exception `DontSqueezeTheBananaException` and the class `Banana` both refer to each other.</span></span>  <span data-ttu-id="7c6e3-145">此外，此模組`BananaHelpers`和類別`Banana`也彼此參考。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-145">Additionally, the module `BananaHelpers` and the class `Banana` also refer to each other.</span></span>  <span data-ttu-id="7c6e3-146">這並不是 F # 中表示，如果您移除可能`rec`關鍵字`MutualReferences`命名空間。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-146">This would not be possible to express in F# if you removed the `rec` keyword from the `MutualReferences` namespace.</span></span>

<span data-ttu-id="7c6e3-147">這項功能也會提供的最上層[模組](modules.md)在 F # 4.1 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="7c6e3-147">This feature is also available for top-level [Modules](modules.md) in F# 4.1 or higher.</span></span>

## <a name="see-also"></a><span data-ttu-id="7c6e3-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c6e3-148">See Also</span></span>
[<span data-ttu-id="7c6e3-149">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="7c6e3-149">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="7c6e3-150">模組</span><span class="sxs-lookup"><span data-stu-id="7c6e3-150">Modules</span></span>](modules.md)

[<span data-ttu-id="7c6e3-151">F # RFC FS 1009-允許透過較大的範圍內的檔案進行相互參考的類型和模組</span><span class="sxs-lookup"><span data-stu-id="7c6e3-151">F# RFC FS-1009 - Allow mutually referential types and modules over larger scopes within files</span></span>](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
