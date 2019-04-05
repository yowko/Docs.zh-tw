---
title: 匯入宣告：Open 關鍵字
description: 深入了解F#匯入宣告，以及如何指定模組或命名空間不需使用完整限定的名稱，您可以參考其項目。
ms.date: 04/04/2019
ms.openlocfilehash: ad64190c3243c57a185f3b864270fca80590f079
ms.sourcegitcommit: 68eb5c4928e2b082f178a42c16f73fedf52c2ab8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59054997"
---
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="12537-103">匯入宣告：`open`關鍵字</span><span class="sxs-lookup"><span data-stu-id="12537-103">Import Declarations: The `open` Keyword</span></span>

> [!NOTE]
> <span data-ttu-id="12537-104">本文中的 API 參考連結將帶您前往 MSDN。</span><span class="sxs-lookup"><span data-stu-id="12537-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="12537-105">docs.microsoft.com API 參考不完整。</span><span class="sxs-lookup"><span data-stu-id="12537-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="12537-106">*匯入宣告*指定的模組或命名空間不需使用完整限定的名稱，您可以參考其項目。</span><span class="sxs-lookup"><span data-stu-id="12537-106">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>

## <a name="syntax"></a><span data-ttu-id="12537-107">語法</span><span class="sxs-lookup"><span data-stu-id="12537-107">Syntax</span></span>

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a><span data-ttu-id="12537-108">備註</span><span class="sxs-lookup"><span data-stu-id="12537-108">Remarks</span></span>

<span data-ttu-id="12537-109">使用完整的命名空間或模組路徑來參考程式碼每次可以建立很難寫入、 讀取和維護的程式碼。</span><span class="sxs-lookup"><span data-stu-id="12537-109">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="12537-110">相反地，您可以使用`open`關鍵字常用模組及命名空間，因此當您參考該模組或命名空間的成員，您可以使用名稱的簡短形式，而不是完整限定名稱。</span><span class="sxs-lookup"><span data-stu-id="12537-110">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="12537-111">這個關鍵字是類似於`using`C# 關鍵字`using namespace`Visual c + + 和`Imports`Visual Basic 中。</span><span class="sxs-lookup"><span data-stu-id="12537-111">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="12537-112">模組或命名空間提供必須在相同的專案或參考的專案或組件中。</span><span class="sxs-lookup"><span data-stu-id="12537-112">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="12537-113">如果不是，您可以將參考加入專案，或使用`-reference`命令`-`列選項 (或其縮寫， `-r`)。</span><span class="sxs-lookup"><span data-stu-id="12537-113">If it is not, you can add a reference to the project, or use the `-reference` command`-`line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="12537-114">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="12537-114">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="12537-115">匯入宣告可讓您可在程式碼所示的宣告，封入命名空間、 模組或檔案結尾之前的名稱。</span><span class="sxs-lookup"><span data-stu-id="12537-115">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="12537-116">當您使用多個匯入宣告時，它們應該會出現在不同行上。</span><span class="sxs-lookup"><span data-stu-id="12537-116">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="12537-117">下列程式碼示範如何使用`open`關鍵字來簡化程式碼。</span><span class="sxs-lookup"><span data-stu-id="12537-117">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="12537-118">F#編譯器不會發出錯誤或警告時相同的名稱，就會發生多個開啟的模組或命名空間中時，會發生模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="12537-118">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="12537-119">發生模稜兩可時，F#提供更多最近開啟的模組或命名空間的喜好設定。</span><span class="sxs-lookup"><span data-stu-id="12537-119">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="12537-120">例如，在下列程式碼中，`empty`意味著`Seq.empty`，即使`empty`兩者都位於`List`和`Seq`模組。</span><span class="sxs-lookup"><span data-stu-id="12537-120">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn "%A" empty
```

<span data-ttu-id="12537-121">因此，要特別小心當您開啟模組或命名空間這類`List`或`Seq`，其中包含具有相同的名稱; 相反地，請考慮使用限定的名稱的成員。</span><span class="sxs-lookup"><span data-stu-id="12537-121">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="12537-122">您應該避免任何情況下，在其中的程式碼是取決於匯入宣告的順序。</span><span class="sxs-lookup"><span data-stu-id="12537-122">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>

## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="12537-123">開啟預設的命名空間</span><span class="sxs-lookup"><span data-stu-id="12537-123">Namespaces That Are Open by Default</span></span>

<span data-ttu-id="12537-124">某些命名空間會因此常常會用於F#程式碼，它們會以隱含方式開啟而不需要明確的匯入宣告。</span><span class="sxs-lookup"><span data-stu-id="12537-124">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="12537-125">下表顯示已開啟預設的命名空間。</span><span class="sxs-lookup"><span data-stu-id="12537-125">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="12537-126">命名空間</span><span class="sxs-lookup"><span data-stu-id="12537-126">Namespace</span></span>|<span data-ttu-id="12537-127">描述</span><span class="sxs-lookup"><span data-stu-id="12537-127">Description</span></span>|
|---------|-----------|
|`Microsoft.FSharp.Core`|<span data-ttu-id="12537-128">包含基本F#類型的內建型別定義，例如`int`並`float`。</span><span class="sxs-lookup"><span data-stu-id="12537-128">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`Microsoft.FSharp.Core.Operators`|<span data-ttu-id="12537-129">包含基本算術運算，例如`+`和`*`。</span><span class="sxs-lookup"><span data-stu-id="12537-129">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`Microsoft.FSharp.Collections`|<span data-ttu-id="12537-130">包含不可變的集合類別，例如`List`和`Array`。</span><span class="sxs-lookup"><span data-stu-id="12537-130">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`Microsoft.FSharp.Control`|<span data-ttu-id="12537-131">包含控制項的建構，例如延遲評估和非同步工作流程的型別。</span><span class="sxs-lookup"><span data-stu-id="12537-131">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`Microsoft.FSharp.Text`|<span data-ttu-id="12537-132">包含函式為格式化的 IO，例如`printf`函式。</span><span class="sxs-lookup"><span data-stu-id="12537-132">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="12537-133">AutoOpen 屬性</span><span class="sxs-lookup"><span data-stu-id="12537-133">AutoOpen Attribute</span></span>

<span data-ttu-id="12537-134">您可以套用`AutoOpen`屬性至組件，如果您想要在參考的組件時，自動開啟命名空間或模組。</span><span class="sxs-lookup"><span data-stu-id="12537-134">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="12537-135">您也可以套用`AutoOpen`屬性加入至父模組或命名空間開啟時自動開啟該模組的模組。</span><span class="sxs-lookup"><span data-stu-id="12537-135">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="12537-136">如需詳細資訊，請參閱 < [Core.AutoOpenAttribute 類別](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d)。</span><span class="sxs-lookup"><span data-stu-id="12537-136">For more information, see [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span></span>

## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="12537-137">RequireQualifiedAccess 屬性</span><span class="sxs-lookup"><span data-stu-id="12537-137">RequireQualifiedAccess Attribute</span></span>

<span data-ttu-id="12537-138">某些模組、 記錄或等位型別可能會指定`RequireQualifiedAccess`屬性。</span><span class="sxs-lookup"><span data-stu-id="12537-138">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="12537-139">當您參考的那些模組、 記錄或等位的項目時，您必須使用限定的名稱，不論您是否包含匯入宣告。</span><span class="sxs-lookup"><span data-stu-id="12537-139">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="12537-140">如果您使用這個屬性策略性上型別會定義最常使用的名稱，您可以協助避免發生名稱衝突，並藉此讓程式碼更有彈性的程式庫中的變更。</span><span class="sxs-lookup"><span data-stu-id="12537-140">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="12537-141">如需詳細資訊，請參閱 < [Core.RequireQualifiedAccessAttribute 類別](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D)。</span><span class="sxs-lookup"><span data-stu-id="12537-141">For more information, see [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span></span>

## <a name="see-also"></a><span data-ttu-id="12537-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12537-142">See also</span></span>

- [<span data-ttu-id="12537-143">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="12537-143">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="12537-144">命名空間</span><span class="sxs-lookup"><span data-stu-id="12537-144">Namespaces</span></span>](namespaces.md)
- [<span data-ttu-id="12537-145">模組</span><span class="sxs-lookup"><span data-stu-id="12537-145">Modules</span></span>](modules.md)
