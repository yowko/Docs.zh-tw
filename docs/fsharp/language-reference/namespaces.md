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
# <a name="namespaces"></a><span data-ttu-id="a1b9d-103">命名空間</span><span class="sxs-lookup"><span data-stu-id="a1b9d-103">Namespaces</span></span>

<span data-ttu-id="a1b9d-104">命名空間可讓您將名稱附加至F#程式元素的群組, 以將程式碼組織成相關功能的區域。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-104">A namespace lets you organize code into areas of related functionality by enabling you to attach a name to a grouping of F# program elements.</span></span> <span data-ttu-id="a1b9d-105">命名空間通常是檔案中F#的最上層元素。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-105">Namespaces are typically top-level elements in F# files.</span></span>

## <a name="syntax"></a><span data-ttu-id="a1b9d-106">語法</span><span class="sxs-lookup"><span data-stu-id="a1b9d-106">Syntax</span></span>

```fsharp
namespace [rec] [parent-namespaces.]identifier
```

## <a name="remarks"></a><span data-ttu-id="a1b9d-107">備註</span><span class="sxs-lookup"><span data-stu-id="a1b9d-107">Remarks</span></span>

<span data-ttu-id="a1b9d-108">如果您想要將程式碼放在命名空間中, 則檔案中的第一個宣告必須宣告命名空間。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-108">If you want to put code in a namespace, the first declaration in the file must declare the namespace.</span></span> <span data-ttu-id="a1b9d-109">整個檔案的內容接著會成為命名空間的一部分, 前提是檔案中不會有其他命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-109">The contents of the entire file then become part of the namespace, provided no other namespaces declaration exists further in the file.</span></span> <span data-ttu-id="a1b9d-110">如果是這種情況, 則所有程式碼必須等到下一個命名空間宣告, 才會被視為在第一個命名空間內。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-110">If that is the case, then all code up until the next namespace declaration is considered to be within the first namespace.</span></span>

<span data-ttu-id="a1b9d-111">命名空間不能直接包含值和函數。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-111">Namespaces cannot directly contain values and functions.</span></span> <span data-ttu-id="a1b9d-112">相反地, 值和函式必須包含在模組中, 而模組則包含在命名空間中。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-112">Instead, values and functions must be included in modules, and modules are included in namespaces.</span></span> <span data-ttu-id="a1b9d-113">命名空間可以包含類型 (模組)。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-113">Namespaces can contain types, modules.</span></span>

<span data-ttu-id="a1b9d-114">XML 檔批註可以在命名空間的上方宣告, 但會被忽略。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-114">XML doc comments can be declared above a namespace, but they're ignored.</span></span> <span data-ttu-id="a1b9d-115">編譯器指示詞也可以在命名空間的上方宣告。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-115">Compiler directives can also be declared above a namespace.</span></span>

<span data-ttu-id="a1b9d-116">命名空間可以使用 namespace 關鍵字明確宣告, 或在宣告模組時以隱含方式宣告。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-116">Namespaces can be declared explicitly with the namespace keyword, or implicitly when declaring a module.</span></span> <span data-ttu-id="a1b9d-117">若要明確宣告命名空間, 請使用 namespace 關鍵字並在後面加上命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-117">To declare a namespace explicitly, use the namespace keyword followed by the namespace name.</span></span> <span data-ttu-id="a1b9d-118">下列範例顯示的程式碼檔案會宣告具有類型`Widgets`的命名空間, 以及該命名空間中包含的模組。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-118">The following example shows a code file that declares a namespace `Widgets` with a type and a module included in that namespace.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

<span data-ttu-id="a1b9d-119">如果檔案的整個內容都在一個模組中, 您也可以使用`module`關鍵字, 並在完整的模組名稱中提供新的命名空間名稱, 以隱含方式宣告命名空間。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-119">If the entire contents of the file are in one module, you can also declare namespaces implicitly by using the `module` keyword and providing the new namespace name in the fully qualified module name.</span></span> <span data-ttu-id="a1b9d-120">下列範例顯示的程式碼檔案會宣告命名空間`Widgets`和包含函`WidgetsModule`式的模組。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-120">The following example shows a code file that declares a namespace `Widgets` and a module `WidgetsModule`, which contains a function.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

<span data-ttu-id="a1b9d-121">下列程式碼相當於上述程式碼, 但模組是本機模組宣告。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-121">The following code is equivalent to the preceding code, but the module is a local module declaration.</span></span> <span data-ttu-id="a1b9d-122">在此情況下, 命名空間必須出現在自己的行上。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-122">In that case, the namespace must appear on its own line.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/namespaces/snippet6402.fs)]

<span data-ttu-id="a1b9d-123">如果一個或多個命名空間中的同一個檔案需要一個以上的模組, 您就必須使用本機模組宣告。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-123">If more than one module is required in the same file in one or more namespaces, you must use local module declarations.</span></span> <span data-ttu-id="a1b9d-124">當您使用本機模組宣告時, 不能在模組宣告中使用限定的命名空間。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-124">When you use local module declarations, you cannot use the qualified namespace in the module declarations.</span></span> <span data-ttu-id="a1b9d-125">下列程式碼顯示具有命名空間宣告和兩個本機模組宣告的檔案。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-125">The following code shows a file that has a namespace declaration and two local module declarations.</span></span> <span data-ttu-id="a1b9d-126">在此情況下, 模組會直接包含在命名空間中;沒有與檔案同名的隱含建立模組。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-126">In this case, the modules are contained directly in the namespace; there is no implicitly created module that has the same name as the file.</span></span> <span data-ttu-id="a1b9d-127">檔案中的任何其他程式碼 (例如`do`系結) 都是在命名空間中, 而不是在內部模組中, 因此您必須使用模組名稱來限定模組成員。 `widgetFunction`</span><span class="sxs-lookup"><span data-stu-id="a1b9d-127">Any other code in the file, such as a `do` binding, is in the namespace but not in the inner modules, so you need to qualify the module member `widgetFunction` by using the module name.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

<span data-ttu-id="a1b9d-128">此範例的輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-128">The output of this example is as follows.</span></span>

```fsharp
Module1 10 20
Module2 5 6
```

<span data-ttu-id="a1b9d-129">如需詳細資訊, 請參閱[模組](modules.md)。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-129">For more information, see [Modules](modules.md).</span></span>

## <a name="nested-namespaces"></a><span data-ttu-id="a1b9d-130">嵌套命名空間</span><span class="sxs-lookup"><span data-stu-id="a1b9d-130">Nested Namespaces</span></span>

<span data-ttu-id="a1b9d-131">當您建立嵌套命名空間時, 您必須完整限定它。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-131">When you create a nested namespace, you must fully qualify it.</span></span> <span data-ttu-id="a1b9d-132">否則, 您會建立新的最上層命名空間。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-132">Otherwise, you create a new top-level namespace.</span></span> <span data-ttu-id="a1b9d-133">命名空間宣告中會忽略縮排。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-133">Indentation is ignored in namespace declarations.</span></span>

<span data-ttu-id="a1b9d-134">下列範例顯示如何宣告嵌套命名空間。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-134">The following example shows how to declare a nested namespace.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a><span data-ttu-id="a1b9d-135">檔案和元件中的命名空間</span><span class="sxs-lookup"><span data-stu-id="a1b9d-135">Namespaces in Files and Assemblies</span></span>

<span data-ttu-id="a1b9d-136">命名空間可以在單一專案或編譯中跨越多個檔案。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-136">Namespaces can span multiple files in a single project or compilation.</span></span> <span data-ttu-id="a1b9d-137">「*命名空間片段*」一詞描述包含在一個檔案中的命名空間部分。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-137">The term *namespace fragment* describes the part of a namespace that is included in one file.</span></span> <span data-ttu-id="a1b9d-138">命名空間也可以跨越多個元件。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-138">Namespaces can also span multiple assemblies.</span></span> <span data-ttu-id="a1b9d-139">例如, `System`命名空間包含整個 .NET Framework, 這會跨越許多元件, 並包含許多嵌套的命名空間。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-139">For example, the `System` namespace includes the whole .NET Framework, which spans many assemblies and contains many nested namespaces.</span></span>

## <a name="global-namespace"></a><span data-ttu-id="a1b9d-140">全域命名空間</span><span class="sxs-lookup"><span data-stu-id="a1b9d-140">Global Namespace</span></span>

<span data-ttu-id="a1b9d-141">您可以使用預先定義`global`的命名空間, 將名稱放在 .net 最上層命名空間中。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-141">You use the predefined namespace `global` to put names in the .NET top-level namespace.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

<span data-ttu-id="a1b9d-142">您也可以使用全域來參考最上層的 .NET 命名空間, 例如, 解決與其他命名空間的名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-142">You can also use global to reference the top-level .NET namespace, for example, to resolve name conflicts with other namespaces.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

## <a name="recursive-namespaces"></a><span data-ttu-id="a1b9d-143">遞迴命名空間</span><span class="sxs-lookup"><span data-stu-id="a1b9d-143">Recursive namespaces</span></span>

<span data-ttu-id="a1b9d-144">命名空間也可以宣告為遞迴, 讓所有包含的程式碼都可以互相遞迴。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-144">Namespaces can also be declared as recursive to allow for all contained code to be mutually recursive.</span></span>  <span data-ttu-id="a1b9d-145">這是透過來`namespace rec`完成。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-145">This is done via `namespace rec`.</span></span> <span data-ttu-id="a1b9d-146">`namespace rec`使用可減輕無法在類型和模組之間撰寫相互引用程式碼的一些難題。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-146">Use of `namespace rec` can alleviate some pains in not being able to write mutually referential code between types and modules.</span></span> <span data-ttu-id="a1b9d-147">以下是這種情況的範例:</span><span class="sxs-lookup"><span data-stu-id="a1b9d-147">The following is an example of this:</span></span>

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

<span data-ttu-id="a1b9d-148">請注意, 例外`DontSqueezeTheBananaException`狀況和類別`Banana`都會彼此參考。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-148">Note that the exception `DontSqueezeTheBananaException` and the class `Banana` both refer to each other.</span></span>  <span data-ttu-id="a1b9d-149">此外, 模組`BananaHelpers`和類別`Banana`也會彼此參考。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-149">Additionally, the module `BananaHelpers` and the class `Banana` also refer to each other.</span></span> <span data-ttu-id="a1b9d-150">如果您已從F# `rec` `MutualReferences`命名空間移除關鍵字, 就無法在中表示。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-150">This wouldn't be possible to express in F# if you removed the `rec` keyword from the `MutualReferences` namespace.</span></span>

<span data-ttu-id="a1b9d-151">這項功能也適用于最上層[模組](modules.md)。</span><span class="sxs-lookup"><span data-stu-id="a1b9d-151">This feature is also available for top-level [Modules](modules.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a1b9d-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1b9d-152">See also</span></span>

- [<span data-ttu-id="a1b9d-153">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="a1b9d-153">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="a1b9d-154">模組</span><span class="sxs-lookup"><span data-stu-id="a1b9d-154">Modules</span></span>](modules.md)
- [<span data-ttu-id="a1b9d-155">F#RFC FS-1009-允許檔案內的相互參考型別和模組超過更大的範圍</span><span class="sxs-lookup"><span data-stu-id="a1b9d-155">F# RFC FS-1009 - Allow mutually referential types and modules over larger scopes within files</span></span>](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
