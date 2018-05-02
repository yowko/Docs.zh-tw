---
title: 泛型 (C# 程式設計手冊)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
caps.latest.revision: 23
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 026b8350a75794cf1101bef69d1bf15f474f103d
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="da05e-102">泛型 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="da05e-102">Generics (C# Programming Guide)</span></span>
<span data-ttu-id="da05e-103">泛型是在 C# 語言和 Common Language Runtime (CLR) 的 2.0 版中新增的功能。</span><span class="sxs-lookup"><span data-stu-id="da05e-103">Generics were added to version 2.0 of the C# language and the common language runtime (CLR).</span></span> <span data-ttu-id="da05e-104">泛型將型別參數的概念引進 .NET Framework 中，使得類別和方法在設計時，可以先行擱置一或多個類型的規格，直到用戶端程式碼對類別或方法進行宣告或具現化時再行處理。</span><span class="sxs-lookup"><span data-stu-id="da05e-104">Generics introduce to the .NET Framework the concept of type parameters, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="da05e-105">例如，您可以使用泛型型別參數 T，撰寫一個類別供其他用戶端程式碼使用，而不會在執行階段產生轉換或 boxing 作業的成本或風險，如下所示：</span><span class="sxs-lookup"><span data-stu-id="da05e-105">For example, by using a generic type parameter T you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#1](../../../csharp/programming-guide/generics/codesnippet/CSharp/index_1.cs)]  
  
## <a name="generics-overview"></a><span data-ttu-id="da05e-106">泛型概觀</span><span class="sxs-lookup"><span data-stu-id="da05e-106">Generics Overview</span></span>  
  
-   <span data-ttu-id="da05e-107">使用泛型型別以最佳化程式碼重複使用、型別安全和效能。</span><span class="sxs-lookup"><span data-stu-id="da05e-107">Use generic types to maximize code reuse, type safety, and performance.</span></span>  
  
-   <span data-ttu-id="da05e-108">泛型的最常見用法是建立集合類別。</span><span class="sxs-lookup"><span data-stu-id="da05e-108">The most common use of generics is to create collection classes.</span></span>  
  
-   <span data-ttu-id="da05e-109">.NET Framework 類別庫包含 <xref:System.Collections.Generic> 命名空間中的數種新泛型集合類別。</span><span class="sxs-lookup"><span data-stu-id="da05e-109">The .NET Framework class library contains several new generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="da05e-110">您應該盡可能使用這些類別，而不是使用類似在 <xref:System.Collections> 命名空間中的 <xref:System.Collections.ArrayList> 類別。</span><span class="sxs-lookup"><span data-stu-id="da05e-110">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>  
  
-   <span data-ttu-id="da05e-111">您可以建立自己的泛型介面、類別、方法、事件和委派。</span><span class="sxs-lookup"><span data-stu-id="da05e-111">You can create your own generic interfaces, classes, methods, events and delegates.</span></span>  
  
-   <span data-ttu-id="da05e-112">泛型類別可限制為允許存取特定資料類型上的方法。</span><span class="sxs-lookup"><span data-stu-id="da05e-112">Generic classes may be constrained to enable access to methods on particular data types.</span></span>  
  
-   <span data-ttu-id="da05e-113">泛型資料類型中所使用的類型相關資訊，可在執行階段透過反映取得。</span><span class="sxs-lookup"><span data-stu-id="da05e-113">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="da05e-114">相關章節</span><span class="sxs-lookup"><span data-stu-id="da05e-114">Related Sections</span></span>  
 <span data-ttu-id="da05e-115">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="da05e-115">For more information:</span></span>  
  
-   [<span data-ttu-id="da05e-116">泛型簡介</span><span class="sxs-lookup"><span data-stu-id="da05e-116">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
  
-   [<span data-ttu-id="da05e-117">泛型的優點</span><span class="sxs-lookup"><span data-stu-id="da05e-117">Benefits of Generics</span></span>](../../../csharp/programming-guide/generics/benefits-of-generics.md)  
  
-   [<span data-ttu-id="da05e-118">泛型型別參數</span><span class="sxs-lookup"><span data-stu-id="da05e-118">Generic Type Parameters</span></span>](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
-   [<span data-ttu-id="da05e-119">型別參數的條件約束</span><span class="sxs-lookup"><span data-stu-id="da05e-119">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
-   [<span data-ttu-id="da05e-120">泛型類別</span><span class="sxs-lookup"><span data-stu-id="da05e-120">Generic Classes</span></span>](../../../csharp/programming-guide/generics/generic-classes.md)  
  
-   [<span data-ttu-id="da05e-121">泛型介面</span><span class="sxs-lookup"><span data-stu-id="da05e-121">Generic Interfaces</span></span>](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
-   [<span data-ttu-id="da05e-122">泛型方法</span><span class="sxs-lookup"><span data-stu-id="da05e-122">Generic Methods</span></span>](../../../csharp/programming-guide/generics/generic-methods.md)  
  
-   [<span data-ttu-id="da05e-123">泛型委派</span><span class="sxs-lookup"><span data-stu-id="da05e-123">Generic Delegates</span></span>](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
-   [<span data-ttu-id="da05e-124">C++ 範本和 C# 泛型之間的差異</span><span class="sxs-lookup"><span data-stu-id="da05e-124">Differences Between C++ Templates and C# Generics</span></span>](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
-   [<span data-ttu-id="da05e-125">泛型和反映</span><span class="sxs-lookup"><span data-stu-id="da05e-125">Generics and Reflection</span></span>](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
-   [<span data-ttu-id="da05e-126">執行階段中的泛型</span><span class="sxs-lookup"><span data-stu-id="da05e-126">Generics in the Run Time</span></span>](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="da05e-127">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="da05e-127">C# Language Specification</span></span>  
 <span data-ttu-id="da05e-128">如需詳細資訊，請參閱＜[C# 語言規格](../../../csharp/language-reference/language-specification/index.md)＞。</span><span class="sxs-lookup"><span data-stu-id="da05e-128">For more information, see the [C# Language Specification](../../../csharp/language-reference/language-specification/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da05e-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="da05e-129">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="da05e-130">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="da05e-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="da05e-131">型別</span><span class="sxs-lookup"><span data-stu-id="da05e-131">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
 [<span data-ttu-id="da05e-132">\<typeparam></span><span class="sxs-lookup"><span data-stu-id="da05e-132">\<typeparam></span></span>](../../../csharp/programming-guide/xmldoc/typeparam.md)  
 [<span data-ttu-id="da05e-133">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="da05e-133">\<typeparamref></span></span>](../../../csharp/programming-guide/xmldoc/typeparamref.md)  
 [<span data-ttu-id="da05e-134">.NET 的泛型</span><span class="sxs-lookup"><span data-stu-id="da05e-134">Generics in .NET</span></span>](../../../standard/generics/index.md)  