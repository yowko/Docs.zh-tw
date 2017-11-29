---
title: "匯入宣告：open 關鍵字 (F#)"
description: "了解 F # 匯入宣告，以及如何指定模組或命名空間而不需要使用完整限定的名稱，您可以參考其項目。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 1e98e48c-52e9-4314-8954-85d5583125f0
ms.openlocfilehash: a6d79bed3dd202657d06956edf9499a9b21a5f03
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="034ce-104">匯入宣告：`open`關鍵字</span><span class="sxs-lookup"><span data-stu-id="034ce-104">Import Declarations: The `open` Keyword</span></span>

> [!NOTE]
<span data-ttu-id="034ce-105">本文中的 API 參考連結將帶您前往 MSDN。</span><span class="sxs-lookup"><span data-stu-id="034ce-105">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="034ce-106">docs.microsoft.com API 參考不完整。</span><span class="sxs-lookup"><span data-stu-id="034ce-106">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="034ce-107">*匯入宣告*指定的模組或命名空間而不需要使用完整限定的名稱，您可以參考其項目。</span><span class="sxs-lookup"><span data-stu-id="034ce-107">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>


## <a name="syntax"></a><span data-ttu-id="034ce-108">語法</span><span class="sxs-lookup"><span data-stu-id="034ce-108">Syntax</span></span>

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a><span data-ttu-id="034ce-109">備註</span><span class="sxs-lookup"><span data-stu-id="034ce-109">Remarks</span></span>
<span data-ttu-id="034ce-110">每次使用命名空間或模組的完整的路徑來參考程式碼可以建立，因而難以撰寫、 讀取和維護的程式碼。</span><span class="sxs-lookup"><span data-stu-id="034ce-110">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="034ce-111">相反地，您可以使用`open`關鍵字經常使用的模組和命名空間，因此當您參考該模組或命名空間的成員，您可以使用名稱的簡短形式，而不是完整限定名稱。</span><span class="sxs-lookup"><span data-stu-id="034ce-111">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="034ce-112">這個關鍵字是類似於`using`關鍵字在 C# 中， `using namespace` Visual c + + 和`Imports`在 Visual Basic 中。</span><span class="sxs-lookup"><span data-stu-id="034ce-112">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="034ce-113">模組或命名空間提供必須在相同的專案或參考的專案或組件中。</span><span class="sxs-lookup"><span data-stu-id="034ce-113">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="034ce-114">如果不是，您可以將參考加入專案，或使用`-reference`命令`-`列選項 (或其縮寫， `-r`)。</span><span class="sxs-lookup"><span data-stu-id="034ce-114">If it is not, you can add a reference to the project, or use the `-reference` command`-`line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="034ce-115">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="034ce-115">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="034ce-116">匯入宣告，讓程式碼所示的宣告，封入命名空間、 模組或檔案結尾之前，您可以使用的名稱。</span><span class="sxs-lookup"><span data-stu-id="034ce-116">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="034ce-117">當您使用多個匯入宣告時，它們應該會出現在不同行。</span><span class="sxs-lookup"><span data-stu-id="034ce-117">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="034ce-118">下列程式碼將示範如何使用`open`關鍵字來簡化程式碼。</span><span class="sxs-lookup"><span data-stu-id="034ce-118">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="034ce-119">F # 編譯器不會發出錯誤或警告，當多個開啟的模組或命名空間中相同名稱時，就會發生模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="034ce-119">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="034ce-120">發生模稜兩可時，F # 提供更最近開啟的模組或命名空間的喜好設定。</span><span class="sxs-lookup"><span data-stu-id="034ce-120">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="034ce-121">例如，在下列程式碼，`empty`表示`Seq.empty`，即使`empty`兩者都位於`List`和`Seq`模組。</span><span class="sxs-lookup"><span data-stu-id="034ce-121">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn "%A" empty
```

<span data-ttu-id="034ce-122">因此，要特別小心當您開啟模組或命名空間這類`List`或`Seq`包含具有相同名稱; 相反地，請考慮使用限定的名稱的成員。</span><span class="sxs-lookup"><span data-stu-id="034ce-122">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="034ce-123">您應該避免任何的情況下所在的程式碼是依存於匯入宣告的順序。</span><span class="sxs-lookup"><span data-stu-id="034ce-123">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>


## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="034ce-124">開啟預設的命名空間</span><span class="sxs-lookup"><span data-stu-id="034ce-124">Namespaces That Are Open by Default</span></span>
<span data-ttu-id="034ce-125">F # 它們會以隱含方式開啟而不需要明確匯入宣告的程式碼經常會使用某些命名空間。</span><span class="sxs-lookup"><span data-stu-id="034ce-125">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="034ce-126">下表顯示開啟的預設命名空間。</span><span class="sxs-lookup"><span data-stu-id="034ce-126">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="034ce-127">命名空間</span><span class="sxs-lookup"><span data-stu-id="034ce-127">Namespace</span></span>|<span data-ttu-id="034ce-128">說明</span><span class="sxs-lookup"><span data-stu-id="034ce-128">Description</span></span>|
|---------|-----------|
|`Microsoft.FSharp.Core`|<span data-ttu-id="034ce-129">包含基本 F # 型別定義的內建類型，例如`int`和`float`。</span><span class="sxs-lookup"><span data-stu-id="034ce-129">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`Microsoft.FSharp.Core.Operators`|<span data-ttu-id="034ce-130">包含基本的算術運算，例如`+`和`*`。</span><span class="sxs-lookup"><span data-stu-id="034ce-130">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`Microsoft.FSharp.Collections`|<span data-ttu-id="034ce-131">包含不可變的集合類別，例如`List`和`Array`。</span><span class="sxs-lookup"><span data-stu-id="034ce-131">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`Microsoft.FSharp.Control`|<span data-ttu-id="034ce-132">包含型別，例如延遲評估和非同步工作流程的控制建構。</span><span class="sxs-lookup"><span data-stu-id="034ce-132">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`Microsoft.FSharp.Text`|<span data-ttu-id="034ce-133">包含函式為格式化的 IO，例如`printf`函式。</span><span class="sxs-lookup"><span data-stu-id="034ce-133">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="034ce-134">AutoOpen 屬性</span><span class="sxs-lookup"><span data-stu-id="034ce-134">AutoOpen Attribute</span></span>
<span data-ttu-id="034ce-135">您可以套用`AutoOpen`屬性的組件，如果您想要在參考的組件時，自動開啟命名空間或模組。</span><span class="sxs-lookup"><span data-stu-id="034ce-135">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="034ce-136">您也可以套用`AutoOpen`屬性設定為要開啟 父模組或命名空間時，自動開啟該模組的模組。</span><span class="sxs-lookup"><span data-stu-id="034ce-136">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="034ce-137">如需詳細資訊，請參閱[Core.AutoOpenAttribute 類別](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d)。</span><span class="sxs-lookup"><span data-stu-id="034ce-137">For more information, see [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span></span>


## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="034ce-138">RequireQualifiedAccess 屬性</span><span class="sxs-lookup"><span data-stu-id="034ce-138">RequireQualifiedAccess Attribute</span></span>
<span data-ttu-id="034ce-139">某些模組、 記錄或等位型別可能會指定`RequireQualifiedAccess`屬性。</span><span class="sxs-lookup"><span data-stu-id="034ce-139">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="034ce-140">當您參考的那些模組、 記錄或等位的項目時，您必須使用限定的名稱，不論您是否包含匯入宣告。</span><span class="sxs-lookup"><span data-stu-id="034ce-140">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="034ce-141">如果您使用這個屬性策略性上類型會定義最常使用的名稱，有助於避免發生名稱衝突，因而使程式碼更有彈性的程式庫中的變更。</span><span class="sxs-lookup"><span data-stu-id="034ce-141">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="034ce-142">如需詳細資訊，請參閱[Core.RequireQualifiedAccessAttribute 類別](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D)。</span><span class="sxs-lookup"><span data-stu-id="034ce-142">For more information, see [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span></span>


## <a name="see-also"></a><span data-ttu-id="034ce-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="034ce-143">See Also</span></span>
[<span data-ttu-id="034ce-144"># 語言參考</span><span class="sxs-lookup"><span data-stu-id="034ce-144"># Language Reference</span></span>](index.md)

[<span data-ttu-id="034ce-145">命名空間</span><span class="sxs-lookup"><span data-stu-id="034ce-145">Namespaces</span></span>](namespaces.md)

[<span data-ttu-id="034ce-146">模組</span><span class="sxs-lookup"><span data-stu-id="034ce-146">Modules</span></span>](modules.md)

