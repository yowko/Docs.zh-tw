---
title: 匯入宣告：open 關鍵字
description: '瞭解 F # 匯入宣告，以及它們如何指定模組或命名空間，而您可以參考其元素，而不需使用完整名稱。'
ms.date: 08/15/2020
ms.openlocfilehash: 6420df071f86159c44606c2710331d5f587023cc
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557603"
---
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="4e665-103">匯入宣告： `open` 關鍵字</span><span class="sxs-lookup"><span data-stu-id="4e665-103">Import declarations: The `open` keyword</span></span>

<span data-ttu-id="4e665-104">匯 *入* 宣告會指定模組或命名空間，而您可以參考其元素，而不需使用完整名稱。</span><span class="sxs-lookup"><span data-stu-id="4e665-104">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>

## <a name="syntax"></a><span data-ttu-id="4e665-105">語法</span><span class="sxs-lookup"><span data-stu-id="4e665-105">Syntax</span></span>

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a><span data-ttu-id="4e665-106">備註</span><span class="sxs-lookup"><span data-stu-id="4e665-106">Remarks</span></span>

<span data-ttu-id="4e665-107">每次使用完整命名空間或模組路徑來參考程式碼，可以建立難以撰寫、讀取和維護的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4e665-107">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="4e665-108">相反地，您可以將 `open` 關鍵字用於常用的模組和命名空間，如此一來，當您參考該模組或命名空間的成員時，就可以使用名稱的簡短形式，而不是完整名稱。</span><span class="sxs-lookup"><span data-stu-id="4e665-108">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="4e665-109">這個關鍵字類似于 `using` c # 中的關鍵字、 `using namespace` Visual C++ 中和 `Imports` Visual Basic。</span><span class="sxs-lookup"><span data-stu-id="4e665-109">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="4e665-110">提供的模組或命名空間必須位於相同的專案或參考的專案或元件中。</span><span class="sxs-lookup"><span data-stu-id="4e665-110">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="4e665-111">如果不是，您可以加入專案的參考，或使用 `-reference` 命令列選項 (或其縮寫 `-r`) 。</span><span class="sxs-lookup"><span data-stu-id="4e665-111">If it is not, you can add a reference to the project, or use the `-reference` command-line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="4e665-112">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="4e665-112">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="4e665-113">匯入宣告會讓宣告後面的程式碼中的名稱可供使用，最多可包含在封入命名空間、模組或檔案的結尾。</span><span class="sxs-lookup"><span data-stu-id="4e665-113">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="4e665-114">當您使用多個匯入宣告時，它們應該會出現在不同的行上。</span><span class="sxs-lookup"><span data-stu-id="4e665-114">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="4e665-115">下列程式碼顯示 `open` 如何使用關鍵字來簡化程式碼。</span><span class="sxs-lookup"><span data-stu-id="4e665-115">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="4e665-116">當有多個開啟的模組或命名空間中發生不明確的名稱時，F # 編譯器不會發出錯誤或警告。</span><span class="sxs-lookup"><span data-stu-id="4e665-116">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="4e665-117">發生多義性時，F # 會優先偏好最近開啟的模組或命名空間。</span><span class="sxs-lookup"><span data-stu-id="4e665-117">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="4e665-118">例如，在下列程式碼中， `empty` `Seq.empty` 即使 `empty` 位於和模組中，也是一樣 `List` `Seq` 。</span><span class="sxs-lookup"><span data-stu-id="4e665-118">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn "%A" empty
```

<span data-ttu-id="4e665-119">因此，當您開啟包含具有相同名稱之成員的模組或命名空間時，請小心， `List` `Seq` 改為考慮使用限定名稱。</span><span class="sxs-lookup"><span data-stu-id="4e665-119">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="4e665-120">您應該避免程式碼相依于匯入宣告順序的任何情況。</span><span class="sxs-lookup"><span data-stu-id="4e665-120">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>

## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="4e665-121">預設會開啟的命名空間</span><span class="sxs-lookup"><span data-stu-id="4e665-121">Namespaces That Are Open by Default</span></span>

<span data-ttu-id="4e665-122">有些命名空間在 F # 程式碼中經常會用到，因此會隱含地開啟，而不需要明確的匯入宣告。</span><span class="sxs-lookup"><span data-stu-id="4e665-122">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="4e665-123">下表顯示預設開啟的命名空間。</span><span class="sxs-lookup"><span data-stu-id="4e665-123">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="4e665-124">命名空間</span><span class="sxs-lookup"><span data-stu-id="4e665-124">Namespace</span></span>|<span data-ttu-id="4e665-125">描述</span><span class="sxs-lookup"><span data-stu-id="4e665-125">Description</span></span>|
|---------|-----------|
|`FSharp.Core`|<span data-ttu-id="4e665-126">包含內建類型（例如和）的基本 F # 型別定義 `int` `float` 。</span><span class="sxs-lookup"><span data-stu-id="4e665-126">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`FSharp.Core.Operators`|<span data-ttu-id="4e665-127">包含基本的算數運算 `+` ，例如和 `*` 。</span><span class="sxs-lookup"><span data-stu-id="4e665-127">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`FSharp.Collections`|<span data-ttu-id="4e665-128">包含不可變的集合類別 `List` ，例如和 `Array` 。</span><span class="sxs-lookup"><span data-stu-id="4e665-128">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`FSharp.Control`|<span data-ttu-id="4e665-129">包含控制項結構的類型，例如延遲評估和非同步工作流程。</span><span class="sxs-lookup"><span data-stu-id="4e665-129">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`FSharp.Text`|<span data-ttu-id="4e665-130">包含格式化 IO 的函式，例如 `printf` 函數。</span><span class="sxs-lookup"><span data-stu-id="4e665-130">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="4e665-131">AutoOpen 屬性</span><span class="sxs-lookup"><span data-stu-id="4e665-131">AutoOpen Attribute</span></span>

<span data-ttu-id="4e665-132">`AutoOpen`如果您想要在參考元件時自動開啟命名空間或模組，您可以將屬性套用至元件。</span><span class="sxs-lookup"><span data-stu-id="4e665-132">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="4e665-133">您也可以將 `AutoOpen` 屬性套用至模組，以在父模組或命名空間開啟時自動開啟該模組。</span><span class="sxs-lookup"><span data-stu-id="4e665-133">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="4e665-134">如需詳細資訊，請參閱 [AutoOpenAttribute](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-autoopenattribute.html)。</span><span class="sxs-lookup"><span data-stu-id="4e665-134">For more information, see [AutoOpenAttribute](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-autoopenattribute.html).</span></span>

## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="4e665-135">RequireQualifiedAccess 屬性</span><span class="sxs-lookup"><span data-stu-id="4e665-135">RequireQualifiedAccess Attribute</span></span>

<span data-ttu-id="4e665-136">某些模組、記錄或等位類型可能會指定 `RequireQualifiedAccess` 屬性。</span><span class="sxs-lookup"><span data-stu-id="4e665-136">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="4e665-137">當您參考這些模組、記錄或等位的專案時，您必須使用限定名稱，不論是否包含匯入宣告。</span><span class="sxs-lookup"><span data-stu-id="4e665-137">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="4e665-138">如果您策略性地在定義常用名稱的類型上使用此屬性，則有助於避免名稱衝突，進而使程式碼在程式庫中的變更時更具彈性。</span><span class="sxs-lookup"><span data-stu-id="4e665-138">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="4e665-139">如需詳細資訊，請參閱 [RequireQualifiedAccessAttribute](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html)。</span><span class="sxs-lookup"><span data-stu-id="4e665-139">For more information, see [RequireQualifiedAccessAttribute](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html).</span></span>

## <a name="see-also"></a><span data-ttu-id="4e665-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e665-140">See also</span></span>

- [<span data-ttu-id="4e665-141">F # 語言參考</span><span class="sxs-lookup"><span data-stu-id="4e665-141">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="4e665-142">命名空間</span><span class="sxs-lookup"><span data-stu-id="4e665-142">Namespaces</span></span>](namespaces.md)
- [<span data-ttu-id="4e665-143">單元</span><span class="sxs-lookup"><span data-stu-id="4e665-143">Modules</span></span>](modules.md)
