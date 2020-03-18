---
title: 泛型 - C# 程式設計手冊
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: c7252180c9c98a8ca99c8cc6b3faaf8b1b8f0749
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79167488"
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="89c53-102">泛型 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="89c53-102">Generics (C# Programming Guide)</span></span>

<span data-ttu-id="89c53-103">泛型將類型參數的概念引入 .NET Framework，從而可以設計類和方法，在用戶端代碼聲明和具現化類或方法之前，可以延遲一個或多個類型的規範。</span><span class="sxs-lookup"><span data-stu-id="89c53-103">Generics introduce the concept of type parameters to the .NET Framework, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="89c53-104">例如，通過使用泛型型別參數`T`，可以編寫一個其他用戶端代碼可以使用的類，而不會產生運行時強制轉換或裝箱操作的成本或風險，如下所示：</span><span class="sxs-lookup"><span data-stu-id="89c53-104">For example, by using a generic type parameter `T`, you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>

[!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]

<span data-ttu-id="89c53-105">泛型類和方法以非泛型類無法實現的方式將再使用性、型別安全性和效率結合起來。</span><span class="sxs-lookup"><span data-stu-id="89c53-105">Generic classes and methods combine reusability, type safety, and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="89c53-106">泛型最常搭配在其上操作的集合和方法使用。</span><span class="sxs-lookup"><span data-stu-id="89c53-106">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="89c53-107">命名<xref:System.Collections.Generic>空間包含多個基於泛型的集合類。</span><span class="sxs-lookup"><span data-stu-id="89c53-107">The <xref:System.Collections.Generic> namespace contains several generic-based collection classes.</span></span> <span data-ttu-id="89c53-108">非泛型集合（如<xref:System.Collections.ArrayList>不推薦）是為相容性目的維護的。</span><span class="sxs-lookup"><span data-stu-id="89c53-108">The non-generic collections, such as <xref:System.Collections.ArrayList> are not recommended and are maintained for compatibility purposes.</span></span> <span data-ttu-id="89c53-109">如需詳細資訊，請參閱 [.NET 的泛型](../../../standard/generics/index.md)。</span><span class="sxs-lookup"><span data-stu-id="89c53-109">For more information, see [Generics in .NET](../../../standard/generics/index.md).</span></span>

<span data-ttu-id="89c53-110">當然，您也可以建立自訂的泛型型別和方法，自行處理泛型化的問題，並設計型別安全且有效率的模式。</span><span class="sxs-lookup"><span data-stu-id="89c53-110">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="89c53-111">下列程式碼範例顯示一個簡單的泛型連結清單類別，以供示範之用</span><span class="sxs-lookup"><span data-stu-id="89c53-111">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="89c53-112">（在大多數情況下，應使用 .NET <xref:System.Collections.Generic.List%601> Framework 類庫提供的類，而不是創建自己的類。類型參數`T`用於多個位置，其中通常使用具體類型來指示存儲在清單中的項的類型。</span><span class="sxs-lookup"><span data-stu-id="89c53-112">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by the .NET Framework class library instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="89c53-113">這個參數可以用於下列方面：</span><span class="sxs-lookup"><span data-stu-id="89c53-113">It is used in the following ways:</span></span>

- <span data-ttu-id="89c53-114">作為 `AddHead` 方法中的方法參數類型。</span><span class="sxs-lookup"><span data-stu-id="89c53-114">As the type of a method parameter in the `AddHead` method.</span></span>
- <span data-ttu-id="89c53-115">作為巢狀 `Node` 類別中 `Data` 屬性的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="89c53-115">As the return type of the `Data` property in the nested `Node` class.</span></span>
- <span data-ttu-id="89c53-116">作為巢狀類別中私用成員 `data` 的類型。</span><span class="sxs-lookup"><span data-stu-id="89c53-116">As the type of the private member `data` in the nested class.</span></span>

 <span data-ttu-id="89c53-117">請注意，`T`嵌套`Node`類可用。</span><span class="sxs-lookup"><span data-stu-id="89c53-117">Note that `T` is available to the nested `Node` class.</span></span> <span data-ttu-id="89c53-118">當 `GenericList<T>` 以具象類型具現化時 (例如具現化為 `GenericList<int>`)，所出現的每個 `T` 都會以 `int` 取代。</span><span class="sxs-lookup"><span data-stu-id="89c53-118">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>

[!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]

<span data-ttu-id="89c53-119">下列程式碼範例示範用戶端程式碼如何使用泛型 `GenericList<T>` 類別建立整數清單。</span><span class="sxs-lookup"><span data-stu-id="89c53-119">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="89c53-120">您只要變更型別引數，就能輕鬆修改下列的程式碼來建立字串清單或任何其他自訂類型的清單：</span><span class="sxs-lookup"><span data-stu-id="89c53-120">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>

[!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]

## <a name="generics-overview"></a><span data-ttu-id="89c53-121">泛型概述</span><span class="sxs-lookup"><span data-stu-id="89c53-121">Generics overview</span></span>

- <span data-ttu-id="89c53-122">使用泛型型別以最佳化程式碼重複使用、型別安全和效能。</span><span class="sxs-lookup"><span data-stu-id="89c53-122">Use generic types to maximize code reuse, type safety, and performance.</span></span>
- <span data-ttu-id="89c53-123">泛型的最常見用法是建立集合類別。</span><span class="sxs-lookup"><span data-stu-id="89c53-123">The most common use of generics is to create collection classes.</span></span>
- <span data-ttu-id="89c53-124">.NET Framework 類別庫包含 <xref:System.Collections.Generic> 命名空間中的數種新泛型集合類別。</span><span class="sxs-lookup"><span data-stu-id="89c53-124">The .NET Framework class library contains several new generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="89c53-125">您應該盡可能使用這些類別，而不是使用類似在 <xref:System.Collections> 命名空間中的 <xref:System.Collections.ArrayList> 類別。</span><span class="sxs-lookup"><span data-stu-id="89c53-125">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>
- <span data-ttu-id="89c53-126">您可以創建自己的通用介面、類、方法、事件和委託。</span><span class="sxs-lookup"><span data-stu-id="89c53-126">You can create your own generic interfaces, classes, methods, events, and delegates.</span></span>
- <span data-ttu-id="89c53-127">泛型類別可限制為允許存取特定資料類型上的方法。</span><span class="sxs-lookup"><span data-stu-id="89c53-127">Generic classes may be constrained to enable access to methods on particular data types.</span></span>
- <span data-ttu-id="89c53-128">泛型資料類型中所使用的類型相關資訊，可在執行階段透過反映取得。</span><span class="sxs-lookup"><span data-stu-id="89c53-128">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>

## <a name="related-sections"></a><span data-ttu-id="89c53-129">相關章節</span><span class="sxs-lookup"><span data-stu-id="89c53-129">Related sections</span></span>

- [<span data-ttu-id="89c53-130">泛型型別參數</span><span class="sxs-lookup"><span data-stu-id="89c53-130">Generic Type Parameters</span></span>](generic-type-parameters.md)
- [<span data-ttu-id="89c53-131">型別參數的條件約束</span><span class="sxs-lookup"><span data-stu-id="89c53-131">Constraints on Type Parameters</span></span>](constraints-on-type-parameters.md)
- [<span data-ttu-id="89c53-132">通用類</span><span class="sxs-lookup"><span data-stu-id="89c53-132">Generic Classes</span></span>](generic-classes.md)
- [<span data-ttu-id="89c53-133">泛型介面</span><span class="sxs-lookup"><span data-stu-id="89c53-133">Generic Interfaces</span></span>](generic-interfaces.md)
- [<span data-ttu-id="89c53-134">通用方法</span><span class="sxs-lookup"><span data-stu-id="89c53-134">Generic Methods</span></span>](generic-methods.md)
- [<span data-ttu-id="89c53-135">通用委託</span><span class="sxs-lookup"><span data-stu-id="89c53-135">Generic Delegates</span></span>](generic-delegates.md)
- [<span data-ttu-id="89c53-136">C++ 範本和 C# 泛型之間的差異</span><span class="sxs-lookup"><span data-stu-id="89c53-136">Differences Between C++ Templates and C# Generics</span></span>](differences-between-cpp-templates-and-csharp-generics.md)
- [<span data-ttu-id="89c53-137">泛型和反映</span><span class="sxs-lookup"><span data-stu-id="89c53-137">Generics and Reflection</span></span>](generics-and-reflection.md)
- [<span data-ttu-id="89c53-138">執行階段中的泛型</span><span class="sxs-lookup"><span data-stu-id="89c53-138">Generics in the Run Time</span></span>](generics-in-the-run-time.md)

## <a name="c-language-specification"></a><span data-ttu-id="89c53-139">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="89c53-139">C# language specification</span></span>

<span data-ttu-id="89c53-140">有關詳細資訊，請參閱[C# 語言規範](~/_csharplang/spec/types.md#constructed-types)。</span><span class="sxs-lookup"><span data-stu-id="89c53-140">For more information, see the [C# Language Specification](~/_csharplang/spec/types.md#constructed-types).</span></span>

## <a name="see-also"></a><span data-ttu-id="89c53-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89c53-141">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="89c53-142">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="89c53-142">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="89c53-143">型別</span><span class="sxs-lookup"><span data-stu-id="89c53-143">Types</span></span>](../types/index.md)
- [<span data-ttu-id="89c53-144">\<類型帕拉姆></span><span class="sxs-lookup"><span data-stu-id="89c53-144">\<typeparam></span></span>](../xmldoc/typeparam.md)
- [<span data-ttu-id="89c53-145">\<類型帕阿姆夫></span><span class="sxs-lookup"><span data-stu-id="89c53-145">\<typeparamref></span></span>](../xmldoc/typeparamref.md)
- [<span data-ttu-id="89c53-146">.NET 的泛型</span><span class="sxs-lookup"><span data-stu-id="89c53-146">Generics in .NET</span></span>](../../../standard/generics/index.md)
