---
title: 泛型 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: 7d212aeaa7d7a8c3f152f8610a7ef3fe5de0fe23
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589601"
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="044b5-102">泛型 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="044b5-102">Generics (C# Programming Guide)</span></span>
<span data-ttu-id="044b5-103">泛型是在 C# 語言和 Common Language Runtime (CLR) 的 2.0 版中新增的功能。</span><span class="sxs-lookup"><span data-stu-id="044b5-103">Generics were added to version 2.0 of the C# language and the common language runtime (CLR).</span></span> <span data-ttu-id="044b5-104">泛型將型別參數的概念引進 .NET Framework 中，使得類別和方法在設計時，可以先行擱置一或多個類型的規格，直到用戶端程式碼對類別或方法進行宣告或具現化時再行處理。</span><span class="sxs-lookup"><span data-stu-id="044b5-104">Generics introduce to the .NET Framework the concept of type parameters, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="044b5-105">例如，您可以使用泛型型別參數 T，撰寫一個類別供其他用戶端程式碼使用，而不會在執行階段產生轉換或 boxing 作業的成本或風險，如下所示：</span><span class="sxs-lookup"><span data-stu-id="044b5-105">For example, by using a generic type parameter T you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]  

<span data-ttu-id="044b5-106">泛型類別和方法將再使用性、型別安全和效率三者結合在一起，發揮了非泛型類別和方法所無法提供的功能。</span><span class="sxs-lookup"><span data-stu-id="044b5-106">Generic classes and methods combine reusability, type safety and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="044b5-107">泛型最常搭配在其上操作的集合和方法使用。</span><span class="sxs-lookup"><span data-stu-id="044b5-107">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="044b5-108">.NET Framework 2.0 版類別庫提供了新的命名空間 <xref:System.Collections.Generic>，其中包含數個新的泛型集合類別。</span><span class="sxs-lookup"><span data-stu-id="044b5-108">Version 2.0 of the .NET Framework class library provides a new namespace, <xref:System.Collections.Generic>, which contains several new generic-based collection classes.</span></span> <span data-ttu-id="044b5-109">建議以 .NET Framework 2.0 和更新版本為目標的所有應用程式都使用新的泛型集合類別，而不是舊版的非泛型集合類別，例如 <xref:System.Collections.ArrayList>。</span><span class="sxs-lookup"><span data-stu-id="044b5-109">It is recommended that all applications that target the .NET Framework 2.0 and later use the new generic collection classes instead of the older non-generic counterparts such as <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="044b5-110">如需詳細資訊，請參閱 [.NET 的泛型](../../../standard/generics/index.md)。</span><span class="sxs-lookup"><span data-stu-id="044b5-110">For more information, see [Generics in .NET](../../../standard/generics/index.md).</span></span>  
  
 <span data-ttu-id="044b5-111">當然，您也可以建立自訂的泛型型別和方法，自行處理泛型化的問題，並設計型別安全且有效率的模式。</span><span class="sxs-lookup"><span data-stu-id="044b5-111">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="044b5-112">下列程式碼範例顯示一個簡單的泛型連結清單類別，以供示範之用</span><span class="sxs-lookup"><span data-stu-id="044b5-112">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="044b5-113">(在大部分情況下，您應該使用 .NET Framework 類別庫提供的 <xref:System.Collections.Generic.List%601> 類別，而不要自行建立類別)。在幾個位置會使用型別參數 `T`，這些位置一般會使用具象類型來表示清單中儲存的項目類型。</span><span class="sxs-lookup"><span data-stu-id="044b5-113">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by the .NET Framework class library instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="044b5-114">這個參數可以用於下列方面：</span><span class="sxs-lookup"><span data-stu-id="044b5-114">It is used in the following ways:</span></span>  
  
- <span data-ttu-id="044b5-115">作為 `AddHead` 方法中的方法參數類型。</span><span class="sxs-lookup"><span data-stu-id="044b5-115">As the type of a method parameter in the `AddHead` method.</span></span>  
  
- <span data-ttu-id="044b5-116">作為巢狀 `Node` 類別中 `Data` 屬性的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="044b5-116">As the return type of the `Data` property in the nested `Node` class.</span></span>  
  
- <span data-ttu-id="044b5-117">作為巢狀類別中私用成員 `data` 的類型。</span><span class="sxs-lookup"><span data-stu-id="044b5-117">As the type of the private member `data` in the nested class.</span></span>  
  
 <span data-ttu-id="044b5-118">請注意，T 可用於巢狀 `Node` 類別。</span><span class="sxs-lookup"><span data-stu-id="044b5-118">Note that T is available to the nested `Node` class.</span></span> <span data-ttu-id="044b5-119">當 `GenericList<T>` 以具象類型具現化時 (例如具現化為 `GenericList<int>`)，所出現的每個 `T` 都會以 `int` 取代。</span><span class="sxs-lookup"><span data-stu-id="044b5-119">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]  
  
 <span data-ttu-id="044b5-120">下列程式碼範例示範用戶端程式碼如何使用泛型 `GenericList<T>` 類別建立整數清單。</span><span class="sxs-lookup"><span data-stu-id="044b5-120">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="044b5-121">您只要變更型別引數，就能輕鬆修改下列的程式碼來建立字串清單或任何其他自訂類型的清單：</span><span class="sxs-lookup"><span data-stu-id="044b5-121">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]  
  
## <a name="generics-overview"></a><span data-ttu-id="044b5-122">泛型概觀</span><span class="sxs-lookup"><span data-stu-id="044b5-122">Generics Overview</span></span>  
  
- <span data-ttu-id="044b5-123">使用泛型型別以最佳化程式碼重複使用、型別安全和效能。</span><span class="sxs-lookup"><span data-stu-id="044b5-123">Use generic types to maximize code reuse, type safety, and performance.</span></span>  
  
- <span data-ttu-id="044b5-124">泛型的最常見用法是建立集合類別。</span><span class="sxs-lookup"><span data-stu-id="044b5-124">The most common use of generics is to create collection classes.</span></span>  
  
- <span data-ttu-id="044b5-125">.NET Framework 類別庫包含 <xref:System.Collections.Generic> 命名空間中的數種新泛型集合類別。</span><span class="sxs-lookup"><span data-stu-id="044b5-125">The .NET Framework class library contains several new generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="044b5-126">您應該盡可能使用這些類別，而不是使用類似在 <xref:System.Collections> 命名空間中的 <xref:System.Collections.ArrayList> 類別。</span><span class="sxs-lookup"><span data-stu-id="044b5-126">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>  
  
- <span data-ttu-id="044b5-127">您可以建立自己的泛型介面、類別、方法、事件和委派。</span><span class="sxs-lookup"><span data-stu-id="044b5-127">You can create your own generic interfaces, classes, methods, events and delegates.</span></span>  
  
- <span data-ttu-id="044b5-128">泛型類別可限制為允許存取特定資料類型上的方法。</span><span class="sxs-lookup"><span data-stu-id="044b5-128">Generic classes may be constrained to enable access to methods on particular data types.</span></span>  
  
- <span data-ttu-id="044b5-129">泛型資料類型中所使用的類型相關資訊，可在執行階段透過反映取得。</span><span class="sxs-lookup"><span data-stu-id="044b5-129">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="044b5-130">相關章節</span><span class="sxs-lookup"><span data-stu-id="044b5-130">Related Sections</span></span>  
 <span data-ttu-id="044b5-131">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="044b5-131">For more information:</span></span>  
  
- [<span data-ttu-id="044b5-132">泛型型別參數</span><span class="sxs-lookup"><span data-stu-id="044b5-132">Generic Type Parameters</span></span>](./generic-type-parameters.md)  
  
- [<span data-ttu-id="044b5-133">型別參數的條件約束</span><span class="sxs-lookup"><span data-stu-id="044b5-133">Constraints on Type Parameters</span></span>](./constraints-on-type-parameters.md)  
  
- [<span data-ttu-id="044b5-134">泛型類別</span><span class="sxs-lookup"><span data-stu-id="044b5-134">Generic Classes</span></span>](./generic-classes.md)  
  
- [<span data-ttu-id="044b5-135">泛型介面</span><span class="sxs-lookup"><span data-stu-id="044b5-135">Generic Interfaces</span></span>](./generic-interfaces.md)  
  
- [<span data-ttu-id="044b5-136">泛型方法</span><span class="sxs-lookup"><span data-stu-id="044b5-136">Generic Methods</span></span>](./generic-methods.md)  
  
- [<span data-ttu-id="044b5-137">泛型委派</span><span class="sxs-lookup"><span data-stu-id="044b5-137">Generic Delegates</span></span>](./generic-delegates.md)  
  
- [<span data-ttu-id="044b5-138">C++ 範本和 C# 泛型之間的差異</span><span class="sxs-lookup"><span data-stu-id="044b5-138">Differences Between C++ Templates and C# Generics</span></span>](./differences-between-cpp-templates-and-csharp-generics.md)  
  
- [<span data-ttu-id="044b5-139">泛型和反映</span><span class="sxs-lookup"><span data-stu-id="044b5-139">Generics and Reflection</span></span>](./generics-and-reflection.md)  
  
- [<span data-ttu-id="044b5-140">執行階段中的泛型</span><span class="sxs-lookup"><span data-stu-id="044b5-140">Generics in the Run Time</span></span>](./generics-in-the-run-time.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="044b5-141">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="044b5-141">C# Language Specification</span></span>  
 <span data-ttu-id="044b5-142">如需詳細資訊，請參閱＜[C# 語言規格](~/_csharplang/spec/types.md#constructed-types)＞。</span><span class="sxs-lookup"><span data-stu-id="044b5-142">For more information, see the [C# Language Specification](~/_csharplang/spec/types.md#constructed-types).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="044b5-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="044b5-143">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="044b5-144">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="044b5-144">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="044b5-145">型別</span><span class="sxs-lookup"><span data-stu-id="044b5-145">Types</span></span>](../types/index.md)
- [<span data-ttu-id="044b5-146">\<typeparam></span><span class="sxs-lookup"><span data-stu-id="044b5-146">\<typeparam></span></span>](../xmldoc/typeparam.md)
- [<span data-ttu-id="044b5-147">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="044b5-147">\<typeparamref></span></span>](../xmldoc/typeparamref.md)
- [<span data-ttu-id="044b5-148">.NET 的泛型</span><span class="sxs-lookup"><span data-stu-id="044b5-148">Generics in .NET</span></span>](../../../standard/generics/index.md)
