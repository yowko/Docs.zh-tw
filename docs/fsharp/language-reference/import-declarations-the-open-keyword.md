---
title: 匯入宣告：open 關鍵字
description: '瞭解 F # 匯入宣告，以及它們如何指定模組或命名空間，而不需使用完整名稱，即可參考其元素。'
ms.date: 04/04/2019
ms.openlocfilehash: 2b88427ca92212fb4a7598447dd1a5e12061093a
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855084"
---
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="78ce0-103">匯入宣告： `open` 關鍵字</span><span class="sxs-lookup"><span data-stu-id="78ce0-103">Import declarations: The `open` keyword</span></span>

<span data-ttu-id="78ce0-104">匯*入*宣告會指定模組或命名空間，而不需使用完整名稱，即可參考其元素。</span><span class="sxs-lookup"><span data-stu-id="78ce0-104">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>

## <a name="syntax"></a><span data-ttu-id="78ce0-105">語法</span><span class="sxs-lookup"><span data-stu-id="78ce0-105">Syntax</span></span>

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a><span data-ttu-id="78ce0-106">備註</span><span class="sxs-lookup"><span data-stu-id="78ce0-106">Remarks</span></span>

> [!NOTE]
> <span data-ttu-id="78ce0-107">F # 的 docs.microsoft.com API 參考不完整。</span><span class="sxs-lookup"><span data-stu-id="78ce0-107">The docs.microsoft.com API reference for F# is not complete.</span></span> <span data-ttu-id="78ce0-108">如果您遇到任何中斷的連結，請改為參考[F # 核心程式庫檔](https://fsharp.github.io/fsharp-core-docs/)。</span><span class="sxs-lookup"><span data-stu-id="78ce0-108">If you encounter any broken links, reference [F# Core Library Documentation](https://fsharp.github.io/fsharp-core-docs/) instead.</span></span>

<span data-ttu-id="78ce0-109">每次使用完整的命名空間或模組路徑來參考程式碼，可以建立難以撰寫、讀取和維護的程式碼。</span><span class="sxs-lookup"><span data-stu-id="78ce0-109">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="78ce0-110">相反地，您可以對 `open` 常用的模組和命名空間使用關鍵字，如此一來，當您參考該模組或命名空間的成員時，就可以使用名稱的簡短形式，而不是完整名稱。</span><span class="sxs-lookup"><span data-stu-id="78ce0-110">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="78ce0-111">這個關鍵字類似 `using` c # 中的關鍵字、 `using namespace` Visual C++ 和 `Imports` Visual Basic。</span><span class="sxs-lookup"><span data-stu-id="78ce0-111">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="78ce0-112">提供的模組或命名空間必須位於相同的專案或參考的專案或元件中。</span><span class="sxs-lookup"><span data-stu-id="78ce0-112">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="78ce0-113">如果不是，您可以加入專案的參考，或使用 `-reference` 命令列選項 (或其縮寫， `-r`) 。</span><span class="sxs-lookup"><span data-stu-id="78ce0-113">If it is not, you can add a reference to the project, or use the `-reference` command-line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="78ce0-114">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="78ce0-114">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="78ce0-115">匯入宣告會在宣告後面的程式碼中提供名稱，最多可在封閉式命名空間、模組或檔案的結尾。</span><span class="sxs-lookup"><span data-stu-id="78ce0-115">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="78ce0-116">當您使用多個匯入宣告時，它們應該會出現在不同的行上。</span><span class="sxs-lookup"><span data-stu-id="78ce0-116">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="78ce0-117">下列程式碼顯示 `open` 如何使用關鍵字來簡化程式碼。</span><span class="sxs-lookup"><span data-stu-id="78ce0-117">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="78ce0-118">當一個以上的開啟模組或命名空間中出現相同名稱時，F # 編譯器不會發出錯誤或警告。</span><span class="sxs-lookup"><span data-stu-id="78ce0-118">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="78ce0-119">發生不明確的情況時，F # 會將喜好設定提供給最近開啟的模組或命名空間。</span><span class="sxs-lookup"><span data-stu-id="78ce0-119">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="78ce0-120">例如，在下列程式碼中， `empty` `Seq.empty` 即使 `empty` 位於和模組中，還是表示 `List` `Seq` 。</span><span class="sxs-lookup"><span data-stu-id="78ce0-120">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn "%A" empty
```

<span data-ttu-id="78ce0-121">因此，當您開啟的模組或命名空間（例如或）包含具有相同名稱的成員時，請務必小心， `List` `Seq` 改為考慮使用限定名稱。</span><span class="sxs-lookup"><span data-stu-id="78ce0-121">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="78ce0-122">您應該避免程式碼相依于匯入宣告順序的任何情況。</span><span class="sxs-lookup"><span data-stu-id="78ce0-122">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>

## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="78ce0-123">預設開啟的命名空間</span><span class="sxs-lookup"><span data-stu-id="78ce0-123">Namespaces That Are Open by Default</span></span>

<span data-ttu-id="78ce0-124">某些命名空間經常用在 F # 程式碼中，它們會以隱含方式開啟，而不需要明確的匯入宣告。</span><span class="sxs-lookup"><span data-stu-id="78ce0-124">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="78ce0-125">下表顯示預設開啟的命名空間。</span><span class="sxs-lookup"><span data-stu-id="78ce0-125">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="78ce0-126">命名空間</span><span class="sxs-lookup"><span data-stu-id="78ce0-126">Namespace</span></span>|<span data-ttu-id="78ce0-127">描述</span><span class="sxs-lookup"><span data-stu-id="78ce0-127">Description</span></span>|
|---------|-----------|
|`Microsoft.FSharp.Core`|<span data-ttu-id="78ce0-128">包含內建類型（例如和）的基本 F # 型別定義 `int` `float` 。</span><span class="sxs-lookup"><span data-stu-id="78ce0-128">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`Microsoft.FSharp.Core.Operators`|<span data-ttu-id="78ce0-129">包含基本的算數運算 `+` ，例如和 `*` 。</span><span class="sxs-lookup"><span data-stu-id="78ce0-129">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`Microsoft.FSharp.Collections`|<span data-ttu-id="78ce0-130">包含不可變的集合類別 `List` ，例如和 `Array` 。</span><span class="sxs-lookup"><span data-stu-id="78ce0-130">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`Microsoft.FSharp.Control`|<span data-ttu-id="78ce0-131">包含控制項結構的類型，例如延遲評估和非同步工作流程。</span><span class="sxs-lookup"><span data-stu-id="78ce0-131">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`Microsoft.FSharp.Text`|<span data-ttu-id="78ce0-132">包含格式化 IO 的函式，例如 `printf` 函數。</span><span class="sxs-lookup"><span data-stu-id="78ce0-132">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="78ce0-133">AutoOpen 屬性</span><span class="sxs-lookup"><span data-stu-id="78ce0-133">AutoOpen Attribute</span></span>

<span data-ttu-id="78ce0-134">`AutoOpen`如果您想要在參考元件時自動開啟命名空間或模組，可以將屬性套用至元件。</span><span class="sxs-lookup"><span data-stu-id="78ce0-134">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="78ce0-135">您也可以將 `AutoOpen` 屬性套用至模組，以便在父模組或命名空間開啟時自動開啟該模組。</span><span class="sxs-lookup"><span data-stu-id="78ce0-135">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="78ce0-136">如需詳細資訊，請參閱[AutoOpenAttribute 類別](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d)。</span><span class="sxs-lookup"><span data-stu-id="78ce0-136">For more information, see [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span></span>

## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="78ce0-137">RequireQualifiedAccess 屬性</span><span class="sxs-lookup"><span data-stu-id="78ce0-137">RequireQualifiedAccess Attribute</span></span>

<span data-ttu-id="78ce0-138">某些模組、記錄或等位類型可能會指定 `RequireQualifiedAccess` 屬性。</span><span class="sxs-lookup"><span data-stu-id="78ce0-138">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="78ce0-139">當您參考這些模組、記錄或等位的元素時，不論您是否包含匯入宣告，都必須使用限定名稱。</span><span class="sxs-lookup"><span data-stu-id="78ce0-139">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="78ce0-140">如果您在定義常用名稱的類型上策略性地使用此屬性，則有助於避免名稱衝突，進而讓程式碼更有彈性地進行程式庫中的變更。</span><span class="sxs-lookup"><span data-stu-id="78ce0-140">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="78ce0-141">如需詳細資訊，請參閱[RequireQualifiedAccessAttribute 類別](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D)。</span><span class="sxs-lookup"><span data-stu-id="78ce0-141">For more information, see [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span></span>

## <a name="see-also"></a><span data-ttu-id="78ce0-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78ce0-142">See also</span></span>

- [<span data-ttu-id="78ce0-143">F # 語言參考</span><span class="sxs-lookup"><span data-stu-id="78ce0-143">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="78ce0-144">命名空間</span><span class="sxs-lookup"><span data-stu-id="78ce0-144">Namespaces</span></span>](namespaces.md)
- [<span data-ttu-id="78ce0-145">模組</span><span class="sxs-lookup"><span data-stu-id="78ce0-145">Modules</span></span>](modules.md)
