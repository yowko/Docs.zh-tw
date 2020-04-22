---
title: 匯入宣告：open 關鍵字
description: 瞭解 F# 匯入聲明及其如何指定模組或命名空間,這些模組或命名空間的元素無需使用完全限定的名稱即可引用。
ms.date: 04/04/2019
ms.openlocfilehash: 0baef27c7dc3181b9da0defb1c793fec04269c09
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021539"
---
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="983e7-103">匯入宣告：`open` 關鍵字</span><span class="sxs-lookup"><span data-stu-id="983e7-103">Import Declarations: The `open` Keyword</span></span>

> [!NOTE]
> <span data-ttu-id="983e7-104">本文中的 API 參考連結將帶您前往 MSDN。</span><span class="sxs-lookup"><span data-stu-id="983e7-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="983e7-105">docs.microsoft.com API 參考不完整。</span><span class="sxs-lookup"><span data-stu-id="983e7-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="983e7-106">*匯入聲明*指定一個模組或命名空間,這些模組或命名空間的元素無需使用完全限定的名稱即可引用。</span><span class="sxs-lookup"><span data-stu-id="983e7-106">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>

## <a name="syntax"></a><span data-ttu-id="983e7-107">語法</span><span class="sxs-lookup"><span data-stu-id="983e7-107">Syntax</span></span>

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a><span data-ttu-id="983e7-108">備註</span><span class="sxs-lookup"><span data-stu-id="983e7-108">Remarks</span></span>

<span data-ttu-id="983e7-109">每次使用完全限定的命名空間或模組路徑引用代碼可以創建難以編寫、讀取和維護的代碼。</span><span class="sxs-lookup"><span data-stu-id="983e7-109">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="983e7-110">相反,`open`您可以將關鍵字用於常用的模組和命名空間,以便在引用該模組或命名空間的成員時,可以使用名稱的簡短形式而不是完全限定的名稱。</span><span class="sxs-lookup"><span data-stu-id="983e7-110">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="983e7-111">此關鍵字類似於 C#`using`中的關鍵字、Visual `using namespace` C++ 和`Imports`Visual Basic 中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="983e7-111">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="983e7-112">提供的模組或命名空間必須位於同一專案或引用的專案或程式集中。</span><span class="sxs-lookup"><span data-stu-id="983e7-112">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="983e7-113">如果不是,則可以添加對專案的引用,或使用`-reference`命令行選項(或其縮寫。 `-r`</span><span class="sxs-lookup"><span data-stu-id="983e7-113">If it is not, you can add a reference to the project, or use the `-reference` command-line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="983e7-114">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="983e7-114">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="983e7-115">匯入聲明使聲明後面的代碼中的名稱可用,最多到封閉命名空間、模組或檔的結尾。</span><span class="sxs-lookup"><span data-stu-id="983e7-115">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="983e7-116">使用多個導入聲明時,它們應顯示在單獨的行上。</span><span class="sxs-lookup"><span data-stu-id="983e7-116">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="983e7-117">以下代碼顯示了`open`關鍵字用於簡化代碼的使用。</span><span class="sxs-lookup"><span data-stu-id="983e7-117">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="983e7-118">當多個打開的模組或命名空間中出現相同名稱時,F# 編譯器不會發出錯誤或警告。</span><span class="sxs-lookup"><span data-stu-id="983e7-118">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="983e7-119">當出現模稜兩可時,F# 優先考慮最近打開的模組或命名空間。</span><span class="sxs-lookup"><span data-stu-id="983e7-119">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="983e7-120">例如,在以下代碼中,`empty``Seq.empty`表示`empty`,即使`List``Seq`位於和模組中也是如此。</span><span class="sxs-lookup"><span data-stu-id="983e7-120">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn "%A" empty
```

<span data-ttu-id="983e7-121">因此,在打開模組或命名空間(如`List``Seq`或包含具有相同名稱的成員)時要小心;相反,請考慮使用限定名稱。</span><span class="sxs-lookup"><span data-stu-id="983e7-121">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="983e7-122">應避免代碼依賴於導入聲明的順序的任何情況。</span><span class="sxs-lookup"><span data-stu-id="983e7-122">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>

## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="983e7-123">預設視窗開啟的命名空間</span><span class="sxs-lookup"><span data-stu-id="983e7-123">Namespaces That Are Open by Default</span></span>

<span data-ttu-id="983e7-124">某些命名空間在 F# 代碼中非常頻繁,因此無需顯式導入聲明即可隱式打開。</span><span class="sxs-lookup"><span data-stu-id="983e7-124">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="983e7-125">下表顯示了默認情況下打開的命名空間。</span><span class="sxs-lookup"><span data-stu-id="983e7-125">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="983e7-126">命名空間</span><span class="sxs-lookup"><span data-stu-id="983e7-126">Namespace</span></span>|<span data-ttu-id="983e7-127">描述</span><span class="sxs-lookup"><span data-stu-id="983e7-127">Description</span></span>|
|---------|-----------|
|`Microsoft.FSharp.Core`|<span data-ttu-id="983e7-128">包含內建型態(如`int``float`和) 的基本 F# 類型定義。</span><span class="sxs-lookup"><span data-stu-id="983e7-128">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`Microsoft.FSharp.Core.Operators`|<span data-ttu-id="983e7-129">包含基本算術運算,如`+``*`和 。</span><span class="sxs-lookup"><span data-stu-id="983e7-129">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`Microsoft.FSharp.Collections`|<span data-ttu-id="983e7-130">包含不可變的集合類別,`List`如`Array`與 。</span><span class="sxs-lookup"><span data-stu-id="983e7-130">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`Microsoft.FSharp.Control`|<span data-ttu-id="983e7-131">包含控件構造的類型,如惰性評估和異步工作流。</span><span class="sxs-lookup"><span data-stu-id="983e7-131">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`Microsoft.FSharp.Text`|<span data-ttu-id="983e7-132">包含格式化 IO 的`printf`功能, 如函數。</span><span class="sxs-lookup"><span data-stu-id="983e7-132">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="983e7-133">自動開啟屬性</span><span class="sxs-lookup"><span data-stu-id="983e7-133">AutoOpen Attribute</span></span>

<span data-ttu-id="983e7-134">如果要在引用程式集`AutoOpen`時自動打開命名空間或模組,則可以將該屬性應用於程式集。</span><span class="sxs-lookup"><span data-stu-id="983e7-134">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="983e7-135">您還可以將`AutoOpen`該屬性應用於模組,以在打開父模組或命名空間時自動打開該模組。</span><span class="sxs-lookup"><span data-stu-id="983e7-135">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="983e7-136">有關詳細資訊,請參閱[Core.AutoOpenattribute 類別](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d)。</span><span class="sxs-lookup"><span data-stu-id="983e7-136">For more information, see [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span></span>

## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="983e7-137">需要限定存取屬性</span><span class="sxs-lookup"><span data-stu-id="983e7-137">RequireQualifiedAccess Attribute</span></span>

<span data-ttu-id="983e7-138">某些模組、記錄或聯合類型可以指定該`RequireQualifiedAccess`屬性。</span><span class="sxs-lookup"><span data-stu-id="983e7-138">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="983e7-139">引用這些模組、記錄或聯合的元素時,無論是否包含導入聲明,都必須使用限定名稱。</span><span class="sxs-lookup"><span data-stu-id="983e7-139">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="983e7-140">如果在定義常用名稱的類型上戰略性地使用此屬性,則有助於避免名稱衝突,從而使代碼對庫中的更改更具彈性。</span><span class="sxs-lookup"><span data-stu-id="983e7-140">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="983e7-141">有關詳細資訊,請參閱[Core.要求限定 Access 屬性類別](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D)。</span><span class="sxs-lookup"><span data-stu-id="983e7-141">For more information, see [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span></span>

## <a name="see-also"></a><span data-ttu-id="983e7-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="983e7-142">See also</span></span>

- [<span data-ttu-id="983e7-143">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="983e7-143">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="983e7-144">命名空間</span><span class="sxs-lookup"><span data-stu-id="983e7-144">Namespaces</span></span>](namespaces.md)
- [<span data-ttu-id="983e7-145">模組</span><span class="sxs-lookup"><span data-stu-id="983e7-145">Modules</span></span>](modules.md)
