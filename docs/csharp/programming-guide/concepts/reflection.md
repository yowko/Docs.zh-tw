---
title: 反映 (C#)
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: a56fb24b63e4d80dbb67b079466b67cd11672023
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711667"
---
# <a name="reflection-c"></a><span data-ttu-id="3097d-102">反映 (C#)</span><span class="sxs-lookup"><span data-stu-id="3097d-102">Reflection (C#)</span></span>

<span data-ttu-id="3097d-103">反映會提供描述元件、模組和類型的物件（屬於 <xref:System.Type>類型）。</span><span class="sxs-lookup"><span data-stu-id="3097d-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules, and types.</span></span> <span data-ttu-id="3097d-104">您可以使用反映來動態建立類型的執行個體、將類型繫結至現有的物件，或從現有的物件取得類型，並叫用其方法或存取其欄位及屬性。</span><span class="sxs-lookup"><span data-stu-id="3097d-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="3097d-105">如果您在程式碼中使用屬性，則反映可讓您存取它們。</span><span class="sxs-lookup"><span data-stu-id="3097d-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="3097d-106">如需詳細資訊，請參閱[屬性](../../../standard/attributes/index.md)。</span><span class="sxs-lookup"><span data-stu-id="3097d-106">For more information, see [Attributes](../../../standard/attributes/index.md).</span></span>

<span data-ttu-id="3097d-107">以下是一個簡單的反映範例，其中使用由 `Object` 基類的所有類型繼承的 <xref:System.Object.GetType> 方法，以取得變數的類型：</span><span class="sxs-lookup"><span data-stu-id="3097d-107">Here's a simple example of reflection using the <xref:System.Object.GetType> method - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>

> [!NOTE]
> <span data-ttu-id="3097d-108">請確定您在 *.cs*檔案的頂端新增 `using System;` 和 `using System.Reflection;`。</span><span class="sxs-lookup"><span data-stu-id="3097d-108">Make sure you add `using System;` and `using System.Reflection;` at the top of your *.cs* file.</span></span>

```csharp
// Using GetType to obtain type information:
int i = 42;
Type type = i.GetType();
Console.WriteLine(type);
```

<span data-ttu-id="3097d-109">輸出為： `System.Int32`。</span><span class="sxs-lookup"><span data-stu-id="3097d-109">The output is: `System.Int32`.</span></span>

<span data-ttu-id="3097d-110">下列範例使用反映以取得所載入組件的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="3097d-110">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>

```csharp
// Using Reflection to get information of an Assembly:
Assembly info = typeof(int).Assembly;
Console.WriteLine(info);
```

<span data-ttu-id="3097d-111">輸出為： `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`。</span><span class="sxs-lookup"><span data-stu-id="3097d-111">The output is: `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`.</span></span>

> [!NOTE]
> <span data-ttu-id="3097d-112">C# 關鍵字 `protected` 和 `internal` 在 IL 中沒有任何意義，而且不會用於反映 API 中。</span><span class="sxs-lookup"><span data-stu-id="3097d-112">The C# keywords `protected` and `internal` have no meaning in IL and are not used in the reflection APIs.</span></span> <span data-ttu-id="3097d-113">IL 中的對應詞彙是「系列」和「組件」。</span><span class="sxs-lookup"><span data-stu-id="3097d-113">The corresponding terms in IL are *Family* and *Assembly*.</span></span> <span data-ttu-id="3097d-114">若要使用反映來識別 `internal` 方法，請使用 <xref:System.Reflection.MethodBase.IsAssembly%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="3097d-114">To identify an `internal` method using reflection, use the <xref:System.Reflection.MethodBase.IsAssembly%2A> property.</span></span> <span data-ttu-id="3097d-115">若要識別 `protected internal` 方法，請使用 <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>。</span><span class="sxs-lookup"><span data-stu-id="3097d-115">To identify a `protected internal` method, use the <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span></span>

## <a name="reflection-overview"></a><span data-ttu-id="3097d-116">反映總覽</span><span class="sxs-lookup"><span data-stu-id="3097d-116">Reflection overview</span></span>

<span data-ttu-id="3097d-117">反映在下列情況下十分有用：</span><span class="sxs-lookup"><span data-stu-id="3097d-117">Reflection is useful in the following situations:</span></span>

- <span data-ttu-id="3097d-118">當您需要存取程式中繼資料中的屬性時。</span><span class="sxs-lookup"><span data-stu-id="3097d-118">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="3097d-119">如需詳細資訊，請參閱[擷取儲存於屬性中的資訊](../../../standard/attributes/retrieving-information-stored-in-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="3097d-119">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>
- <span data-ttu-id="3097d-120">如需檢查和具現化組件中的類型。</span><span class="sxs-lookup"><span data-stu-id="3097d-120">For examining and instantiating types in an assembly.</span></span>
- <span data-ttu-id="3097d-121">如需在執行階段建置新類型。</span><span class="sxs-lookup"><span data-stu-id="3097d-121">For building new types at runtime.</span></span> <span data-ttu-id="3097d-122">使用 <xref:System.Reflection.Emit> 中的類別。</span><span class="sxs-lookup"><span data-stu-id="3097d-122">Use classes in <xref:System.Reflection.Emit>.</span></span>
- <span data-ttu-id="3097d-123">對於執行晚期繫結，存取在執行階段建立的類型上的方法。</span><span class="sxs-lookup"><span data-stu-id="3097d-123">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="3097d-124">請參閱[動態載入和使用類型](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md)主題。</span><span class="sxs-lookup"><span data-stu-id="3097d-124">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>

## <a name="related-sections"></a><span data-ttu-id="3097d-125">相關章節</span><span class="sxs-lookup"><span data-stu-id="3097d-125">Related sections</span></span>

<span data-ttu-id="3097d-126">如需詳細資訊，請參閱：＜ ＞</span><span class="sxs-lookup"><span data-stu-id="3097d-126">For more information:</span></span>

- [<span data-ttu-id="3097d-127">反映</span><span class="sxs-lookup"><span data-stu-id="3097d-127">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)
- [<span data-ttu-id="3097d-128">檢視類型資訊</span><span class="sxs-lookup"><span data-stu-id="3097d-128">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)
- [<span data-ttu-id="3097d-129">反映和泛用類型</span><span class="sxs-lookup"><span data-stu-id="3097d-129">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)
- <xref:System.Reflection.Emit>
- [<span data-ttu-id="3097d-130">擷取儲存於屬性中的資訊</span><span class="sxs-lookup"><span data-stu-id="3097d-130">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)

## <a name="see-also"></a><span data-ttu-id="3097d-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="3097d-131">See also</span></span>

- [<span data-ttu-id="3097d-132">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="3097d-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3097d-133">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="3097d-133">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
