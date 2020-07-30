---
title: 反映 (C#)
description: '反映會提供描述 c # 中元件、模組和類型的物件。 如果您的程式碼包含屬性，反映可讓您存取它們。'
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: 4d4f4c082dd2d58e212bae53524e5dd4fd06fb75
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302798"
---
# <a name="reflection-c"></a><span data-ttu-id="36f9b-104">反映 (C#)</span><span class="sxs-lookup"><span data-stu-id="36f9b-104">Reflection (C#)</span></span>

<span data-ttu-id="36f9b-105">反映提供 <xref:System.Type> 描述元件、模組和類型的物件（類型為）。</span><span class="sxs-lookup"><span data-stu-id="36f9b-105">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules, and types.</span></span> <span data-ttu-id="36f9b-106">您可以使用反映來動態建立類型的執行個體、將類型繫結至現有的物件，或從現有的物件取得類型，並叫用其方法或存取其欄位及屬性。</span><span class="sxs-lookup"><span data-stu-id="36f9b-106">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="36f9b-107">如果您在程式碼中使用屬性，則反映可讓您存取它們。</span><span class="sxs-lookup"><span data-stu-id="36f9b-107">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="36f9b-108">如需詳細資訊，請參閱[屬性](../../../standard/attributes/index.md)。</span><span class="sxs-lookup"><span data-stu-id="36f9b-108">For more information, see [Attributes](../../../standard/attributes/index.md).</span></span>

<span data-ttu-id="36f9b-109">以下是使用繼承自基類的所有類型之方法的簡單反映範例， <xref:System.Object.GetType> `Object` 以取得變數的類型：</span><span class="sxs-lookup"><span data-stu-id="36f9b-109">Here's a simple example of reflection using the <xref:System.Object.GetType> method - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>

> [!NOTE]
> <span data-ttu-id="36f9b-110">請確定您在 `using System;` `using System.Reflection;` *.cs*檔案的頂端新增和。</span><span class="sxs-lookup"><span data-stu-id="36f9b-110">Make sure you add `using System;` and `using System.Reflection;` at the top of your *.cs* file.</span></span>

```csharp
// Using GetType to obtain type information:
int i = 42;
Type type = i.GetType();
Console.WriteLine(type);
```

<span data-ttu-id="36f9b-111">輸出為： `System.Int32` 。</span><span class="sxs-lookup"><span data-stu-id="36f9b-111">The output is: `System.Int32`.</span></span>

<span data-ttu-id="36f9b-112">下列範例使用反映以取得所載入組件的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="36f9b-112">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>

```csharp
// Using Reflection to get information of an Assembly:
Assembly info = typeof(int).Assembly;
Console.WriteLine(info);
```

<span data-ttu-id="36f9b-113">輸出為： `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e` 。</span><span class="sxs-lookup"><span data-stu-id="36f9b-113">The output is: `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`.</span></span>

> [!NOTE]
> <span data-ttu-id="36f9b-114">C# 關鍵字 `protected` 和 `internal` 在 IL 中沒有任何意義，而且不會用於反映 API 中。</span><span class="sxs-lookup"><span data-stu-id="36f9b-114">The C# keywords `protected` and `internal` have no meaning in IL and are not used in the reflection APIs.</span></span> <span data-ttu-id="36f9b-115">IL 中的對應詞彙是「系列」\*\* 和「組件」\*\*。</span><span class="sxs-lookup"><span data-stu-id="36f9b-115">The corresponding terms in IL are *Family* and *Assembly*.</span></span> <span data-ttu-id="36f9b-116">若要使用反映來識別 `internal` 方法，請使用 <xref:System.Reflection.MethodBase.IsAssembly%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="36f9b-116">To identify an `internal` method using reflection, use the <xref:System.Reflection.MethodBase.IsAssembly%2A> property.</span></span> <span data-ttu-id="36f9b-117">若要識別 `protected internal` 方法，請使用 <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>。</span><span class="sxs-lookup"><span data-stu-id="36f9b-117">To identify a `protected internal` method, use the <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span></span>

## <a name="reflection-overview"></a><span data-ttu-id="36f9b-118">反映總覽</span><span class="sxs-lookup"><span data-stu-id="36f9b-118">Reflection overview</span></span>

<span data-ttu-id="36f9b-119">反映在下列情況下十分有用：</span><span class="sxs-lookup"><span data-stu-id="36f9b-119">Reflection is useful in the following situations:</span></span>

- <span data-ttu-id="36f9b-120">當您需要存取程式中繼資料中的屬性時。</span><span class="sxs-lookup"><span data-stu-id="36f9b-120">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="36f9b-121">如需詳細資訊，請參閱[擷取儲存於屬性中的資訊](../../../standard/attributes/retrieving-information-stored-in-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="36f9b-121">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>
- <span data-ttu-id="36f9b-122">如需檢查和具現化組件中的類型。</span><span class="sxs-lookup"><span data-stu-id="36f9b-122">For examining and instantiating types in an assembly.</span></span>
- <span data-ttu-id="36f9b-123">如需在執行階段建置新類型。</span><span class="sxs-lookup"><span data-stu-id="36f9b-123">For building new types at runtime.</span></span> <span data-ttu-id="36f9b-124">使用 <xref:System.Reflection.Emit> 中的類別。</span><span class="sxs-lookup"><span data-stu-id="36f9b-124">Use classes in <xref:System.Reflection.Emit>.</span></span>
- <span data-ttu-id="36f9b-125">對於執行晚期繫結，存取在執行階段建立的類型上的方法。</span><span class="sxs-lookup"><span data-stu-id="36f9b-125">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="36f9b-126">請參閱[動態載入和使用類型](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md)主題。</span><span class="sxs-lookup"><span data-stu-id="36f9b-126">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>

## <a name="related-sections"></a><span data-ttu-id="36f9b-127">相關章節</span><span class="sxs-lookup"><span data-stu-id="36f9b-127">Related sections</span></span>

<span data-ttu-id="36f9b-128">其他資訊：</span><span class="sxs-lookup"><span data-stu-id="36f9b-128">For more information:</span></span>

- [<span data-ttu-id="36f9b-129">反射</span><span class="sxs-lookup"><span data-stu-id="36f9b-129">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)
- [<span data-ttu-id="36f9b-130">檢視類型資訊</span><span class="sxs-lookup"><span data-stu-id="36f9b-130">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)
- [<span data-ttu-id="36f9b-131">反映和泛用類型</span><span class="sxs-lookup"><span data-stu-id="36f9b-131">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)
- <xref:System.Reflection.Emit>
- [<span data-ttu-id="36f9b-132">擷取儲存於屬性中的資訊</span><span class="sxs-lookup"><span data-stu-id="36f9b-132">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)

## <a name="see-also"></a><span data-ttu-id="36f9b-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36f9b-133">See also</span></span>

- [<span data-ttu-id="36f9b-134">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="36f9b-134">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="36f9b-135">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="36f9b-135">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
