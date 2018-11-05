---
title: 命名空間 (F#)
description: '了解 F # 命名空間如何讓您將組織成相關功能的程式碼，方法是讓您將名稱附加到的程式項目群組。'
ms.date: 04/24/2017
ms.openlocfilehash: 769a1241f76ac32d3a6a80bd637078493119bb3c
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "44178244"
---
# <a name="namespaces"></a><span data-ttu-id="7ec8d-103">命名空間</span><span class="sxs-lookup"><span data-stu-id="7ec8d-103">Namespaces</span></span>

<span data-ttu-id="7ec8d-104">命名空間可讓您將名稱附加至程式項目群組，將程式碼依相關功能分類。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-104">A namespace lets you organize code into areas of related functionality by enabling you to attach a name to a grouping of program elements.</span></span>

## <a name="syntax"></a><span data-ttu-id="7ec8d-105">語法</span><span class="sxs-lookup"><span data-stu-id="7ec8d-105">Syntax</span></span>

```fsharp
namespace [parent-namespaces.]identifier
```

## <a name="remarks"></a><span data-ttu-id="7ec8d-106">備註</span><span class="sxs-lookup"><span data-stu-id="7ec8d-106">Remarks</span></span>

<span data-ttu-id="7ec8d-107">如果您想要將程式碼放在命名空間，檔案中的第一個宣告必須宣告命名空間。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-107">If you want to put code in a namespace, the first declaration in the file must declare the namespace.</span></span> <span data-ttu-id="7ec8d-108">整個檔案的內容則會變成命名空間的一部分。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-108">The contents of the entire file then become part of the namespace.</span></span>

<span data-ttu-id="7ec8d-109">值和函式，不能直接包含命名空間。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-109">Namespaces cannot directly contain values and functions.</span></span> <span data-ttu-id="7ec8d-110">而值和函式必須包含在模組中，模組會包含命名空間中。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-110">Instead, values and functions must be included in modules, and modules are included in namespaces.</span></span> <span data-ttu-id="7ec8d-111">命名空間可以包含類型，模組。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-111">Namespaces can contain types, modules.</span></span>

<span data-ttu-id="7ec8d-112">命名空間可以明確宣告命名空間關鍵字，或以隱含方式宣告模組時。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-112">Namespaces can be declared explicitly with the namespace keyword, or implicitly when declaring a module.</span></span> <span data-ttu-id="7ec8d-113">若要明確宣告命名空間，使用命名空間關鍵字後面加上命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-113">To declare a namespace explicitly, use the namespace keyword followed by the namespace name.</span></span> <span data-ttu-id="7ec8d-114">下列範例示範宣告命名空間與型別，該命名空間中包含一個模組的小工具的程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-114">The following example shows a code file that declares a namespace Widgets with a type and a module included in that namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

<span data-ttu-id="7ec8d-115">如果其中一個模組中之檔案的整個內容，您也可以宣告命名空間會隱含地使用`module`關鍵字並提供新的命名空間名稱，在完整的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-115">If the entire contents of the file are in one module, you can also declare namespaces implicitly by using the `module` keyword and providing the new namespace name in the fully qualified module name.</span></span> <span data-ttu-id="7ec8d-116">下列範例示範宣告命名空間的程式碼檔案`Widgets`和模組`WidgetsModule`，其中包含函式。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-116">The following example shows a code file that declares a namespace `Widgets` and a module `WidgetsModule`, which contains a function.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

<span data-ttu-id="7ec8d-117">下列程式碼相當於上述程式碼，但此模組是在本機的模組宣告。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-117">The following code is equivalent to the preceding code, but the module is a local module declaration.</span></span> <span data-ttu-id="7ec8d-118">在此情況下，命名空間必須出現的那一行。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-118">In that case, the namespace must appear on its own line.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/namespaces/snippet6402.fs)]

<span data-ttu-id="7ec8d-119">如果在一或多個命名空間中相同的檔案需要多個模組，您必須使用本機模組宣告。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-119">If more than one module is required in the same file in one or more namespaces, you must use local module declarations.</span></span> <span data-ttu-id="7ec8d-120">當您使用本機模組宣告時，您無法使用限定的命名空間模組宣告中。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-120">When you use local module declarations, you cannot use the qualified namespace in the module declarations.</span></span> <span data-ttu-id="7ec8d-121">下列程式碼會顯示具有命名空間宣告和兩個本機模組宣告的檔案。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-121">The following code shows a file that has a namespace declaration and two local module declarations.</span></span> <span data-ttu-id="7ec8d-122">在此情況下，模組會直接包含在命名空間;沒有任何隱含建立的模組檔案具有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-122">In this case, the modules are contained directly in the namespace; there is no implicitly created module that has the same name as the file.</span></span> <span data-ttu-id="7ec8d-123">任何其他程式碼在檔案中，這類`do`繫結，是在命名空間，但不是在內部的模組中，因此您必須限定的模組成員`widgetFunction`所使用的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-123">Any other code in the file, such as a `do` binding, is in the namespace but not in the inner modules, so you need to qualify the module member `widgetFunction` by using the module name.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

<span data-ttu-id="7ec8d-124">此範例的輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-124">The output of this example is as follows.</span></span>

```fsharp
Module1 10 20
Module2 5 6
```

<span data-ttu-id="7ec8d-125">如需詳細資訊，請參閱 <<c0> [ 模組](modules.md)。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-125">For more information, see [Modules](modules.md).</span></span>

## <a name="nested-namespaces"></a><span data-ttu-id="7ec8d-126">巢狀命名空間</span><span class="sxs-lookup"><span data-stu-id="7ec8d-126">Nested Namespaces</span></span>

<span data-ttu-id="7ec8d-127">當您建立巢狀命名空間時，您必須完整限定。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-127">When you create a nested namespace, you must fully qualify it.</span></span> <span data-ttu-id="7ec8d-128">否則，您會建立新的最上層命名空間。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-128">Otherwise, you create a new top-level namespace.</span></span> <span data-ttu-id="7ec8d-129">命名空間宣告中，會忽略縮排。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-129">Indentation is ignored in namespace declarations.</span></span>

<span data-ttu-id="7ec8d-130">下列範例示範如何宣告巢狀命名空間。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-130">The following example shows how to declare a nested namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a><span data-ttu-id="7ec8d-131">檔案和組件中的命名空間</span><span class="sxs-lookup"><span data-stu-id="7ec8d-131">Namespaces in Files and Assemblies</span></span>

<span data-ttu-id="7ec8d-132">命名空間可以跨多個檔案中的單一專案或編譯。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-132">Namespaces can span multiple files in a single project or compilation.</span></span> <span data-ttu-id="7ec8d-133">詞彙*命名空間片段*描述包含在一個檔案的命名空間的一部分。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-133">The term *namespace fragment* describes the part of a namespace that is included in one file.</span></span> <span data-ttu-id="7ec8d-134">命名空間也能橫跨多個組件。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-134">Namespaces can also span multiple assemblies.</span></span> <span data-ttu-id="7ec8d-135">比方說，`System`命名空間包含整個.NET Framework 中，這會跨越許多組件，並包含許多巢狀命名空間。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-135">For example, the `System` namespace includes the whole .NET Framework, which spans many assemblies and contains many nested namespaces.</span></span>

## <a name="global-namespace"></a><span data-ttu-id="7ec8d-136">全域命名空間</span><span class="sxs-lookup"><span data-stu-id="7ec8d-136">Global Namespace</span></span>

<span data-ttu-id="7ec8d-137">您使用預先定義的命名空間`global`將.NET 的最上層命名空間中的名稱。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-137">You use the predefined namespace `global` to put names in the .NET top-level namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

<span data-ttu-id="7ec8d-138">您也可以使用全域參考最上層的.NET 命名空間，例如，若要解決與其他命名空間的名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-138">You can also use global to reference the top-level .NET namespace, for example, to resolve name conflicts with other namespaces.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

## <a name="recursive-namespaces"></a><span data-ttu-id="7ec8d-139">遞迴命名空間</span><span class="sxs-lookup"><span data-stu-id="7ec8d-139">Recursive namespaces</span></span>

<span data-ttu-id="7ec8d-140">F # 4.1 導入了可讓要相互遞迴所有內含的程式碼的命名空間的概念。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-140">F# 4.1 introduces the notion of namespaces which allow for all contained code to be mutually recursive.</span></span>  <span data-ttu-id="7ec8d-141">這透過完成`namespace rec`。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-141">This is done via `namespace rec`.</span></span>  <span data-ttu-id="7ec8d-142">使用`namespace rec`可以減輕不能夠撰寫相互參考的程式碼類型和模組之間的一些難題。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-142">Use of `namespace rec` can alleviate some pains in not being able to write mutually referential code between types and modules.</span></span>  <span data-ttu-id="7ec8d-143">這個範例如下：</span><span class="sxs-lookup"><span data-stu-id="7ec8d-143">The following is an example of this:</span></span>

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

<span data-ttu-id="7ec8d-144">請注意，例外狀況`DontSqueezeTheBananaException`和類別`Banana`都會指向彼此。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-144">Note that the exception `DontSqueezeTheBananaException` and the class `Banana` both refer to each other.</span></span>  <span data-ttu-id="7ec8d-145">此外，模組`BananaHelpers`和類別`Banana`也彼此參考。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-145">Additionally, the module `BananaHelpers` and the class `Banana` also refer to each other.</span></span>  <span data-ttu-id="7ec8d-146">這不是來表示 F # 中，如果您移除可能`rec`關鍵字，從`MutualReferences`命名空間。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-146">This would not be possible to express in F# if you removed the `rec` keyword from the `MutualReferences` namespace.</span></span>

<span data-ttu-id="7ec8d-147">這項功能也是適用於最上層[模組](modules.md)中 F # 4.1 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-147">This feature is also available for top-level [Modules](modules.md) in F# 4.1 or higher.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ec8d-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ec8d-148">See also</span></span>

- [<span data-ttu-id="7ec8d-149">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="7ec8d-149">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="7ec8d-150">模組</span><span class="sxs-lookup"><span data-stu-id="7ec8d-150">Modules</span></span>](modules.md)
- [<span data-ttu-id="7ec8d-151">F # RFC FS-1009-允許透過檔案內的較大範圍的相互參考的類型和模組</span><span class="sxs-lookup"><span data-stu-id="7ec8d-151">F# RFC FS-1009 - Allow mutually referential types and modules over larger scopes within files</span></span>](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
