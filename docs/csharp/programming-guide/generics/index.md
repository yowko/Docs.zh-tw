---
title: "泛型 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
caps.latest.revision: 23
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 1e548df4de2c07934313311a7ffcfae82be76000
ms.openlocfilehash: de81058173b0985577474e8601aa84d4e83336a5
ms.contentlocale: zh-tw
ms.lasthandoff: 08/29/2017

---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="a1297-102">泛型 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="a1297-102">Generics (C# Programming Guide)</span></span>
<span data-ttu-id="a1297-103">泛型是在 C# 語言和 Common Language Runtime (CLR) 的 2.0 版中新增的功能。</span><span class="sxs-lookup"><span data-stu-id="a1297-103">Generics were added to version 2.0 of the C# language and the common language runtime (CLR).</span></span> <span data-ttu-id="a1297-104">泛型將型別參數的概念引進 .NET Framework 中，使得類別和方法在設計時，可以先行擱置一或多個類型的規格，直到用戶端程式碼對類別或方法進行宣告或具現化時再行處理。</span><span class="sxs-lookup"><span data-stu-id="a1297-104">Generics introduce to the .NET Framework the concept of type parameters, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="a1297-105">例如，您可以使用泛型型別參數 T，撰寫一個類別供其他用戶端程式碼使用，而不會在執行階段產生轉換或 boxing 作業的成本或風險，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a1297-105">For example, by using a generic type parameter T you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>  
  
 <span data-ttu-id="a1297-106">[!code-cs[csProgGuideGenerics#1](../../../csharp/programming-guide/generics/codesnippet/CSharp/index_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="a1297-106">[!code-cs[csProgGuideGenerics#1](../../../csharp/programming-guide/generics/codesnippet/CSharp/index_1.cs)]</span></span>  
  
## <a name="generics-overview"></a><span data-ttu-id="a1297-107">泛型概觀</span><span class="sxs-lookup"><span data-stu-id="a1297-107">Generics Overview</span></span>  
  
-   <span data-ttu-id="a1297-108">使用泛型型別以最佳化程式碼重複使用、型別安全和效能。</span><span class="sxs-lookup"><span data-stu-id="a1297-108">Use generic types to maximize code reuse, type safety, and performance.</span></span>  
  
-   <span data-ttu-id="a1297-109">泛型的最常見用法是建立集合類別。</span><span class="sxs-lookup"><span data-stu-id="a1297-109">The most common use of generics is to create collection classes.</span></span>  
  
-   <span data-ttu-id="a1297-110">.NET Framework 類別庫包含 <xref:System.Collections.Generic> 命名空間中的數種新泛型集合類別。</span><span class="sxs-lookup"><span data-stu-id="a1297-110">The .NET Framework class library contains several new generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="a1297-111">您應該盡可能使用這些類別，而不是使用類似在 <xref:System.Collections> 命名空間中的 <xref:System.Collections.ArrayList> 類別。</span><span class="sxs-lookup"><span data-stu-id="a1297-111">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>  
  
-   <span data-ttu-id="a1297-112">您可以建立自己的泛型介面、類別、方法、事件和委派。</span><span class="sxs-lookup"><span data-stu-id="a1297-112">You can create your own generic interfaces, classes, methods, events and delegates.</span></span>  
  
-   <span data-ttu-id="a1297-113">泛型類別可限制為允許存取特定資料類型上的方法。</span><span class="sxs-lookup"><span data-stu-id="a1297-113">Generic classes may be constrained to enable access to methods on particular data types.</span></span>  
  
-   <span data-ttu-id="a1297-114">泛型資料類型中所使用的類型相關資訊，可在執行階段透過反映取得。</span><span class="sxs-lookup"><span data-stu-id="a1297-114">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a1297-115">相關章節</span><span class="sxs-lookup"><span data-stu-id="a1297-115">Related Sections</span></span>  
 <span data-ttu-id="a1297-116">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="a1297-116">For more information:</span></span>  
  
-   [<span data-ttu-id="a1297-117">泛型簡介</span><span class="sxs-lookup"><span data-stu-id="a1297-117">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
  
-   [<span data-ttu-id="a1297-118">泛型的優點</span><span class="sxs-lookup"><span data-stu-id="a1297-118">Benefits of Generics</span></span>](../../../csharp/programming-guide/generics/benefits-of-generics.md)  
  
-   [<span data-ttu-id="a1297-119">泛型型別參數</span><span class="sxs-lookup"><span data-stu-id="a1297-119">Generic Type Parameters</span></span>](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
-   [<span data-ttu-id="a1297-120">型別參數的條件約束</span><span class="sxs-lookup"><span data-stu-id="a1297-120">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
-   [<span data-ttu-id="a1297-121">泛型類別</span><span class="sxs-lookup"><span data-stu-id="a1297-121">Generic Classes</span></span>](../../../csharp/programming-guide/generics/generic-classes.md)  
  
-   [<span data-ttu-id="a1297-122">泛型介面</span><span class="sxs-lookup"><span data-stu-id="a1297-122">Generic Interfaces</span></span>](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
-   [<span data-ttu-id="a1297-123">泛型方法</span><span class="sxs-lookup"><span data-stu-id="a1297-123">Generic Methods</span></span>](../../../csharp/programming-guide/generics/generic-methods.md)  
  
-   [<span data-ttu-id="a1297-124">泛型委派</span><span class="sxs-lookup"><span data-stu-id="a1297-124">Generic Delegates</span></span>](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
-   [<span data-ttu-id="a1297-125">C++ 範本和 C# 泛型之間的差異</span><span class="sxs-lookup"><span data-stu-id="a1297-125">Differences Between C++ Templates and C# Generics</span></span>](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
-   [<span data-ttu-id="a1297-126">泛型和反映</span><span class="sxs-lookup"><span data-stu-id="a1297-126">Generics and Reflection</span></span>](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
-   [<span data-ttu-id="a1297-127">執行階段中的泛型</span><span class="sxs-lookup"><span data-stu-id="a1297-127">Generics in the Run Time</span></span>](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
-   [<span data-ttu-id="a1297-128">.NET Framework 類別庫中的泛型</span><span class="sxs-lookup"><span data-stu-id="a1297-128">Generics in the .NET Framework Class Library</span></span>](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="a1297-129">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="a1297-129">C# Language Specification</span></span>  
 <span data-ttu-id="a1297-130">如需詳細資訊，請參閱＜[C# 語言規格](../../../csharp/language-reference/language-specification/index.md)＞。</span><span class="sxs-lookup"><span data-stu-id="a1297-130">For more information, see the [C# Language Specification](../../../csharp/language-reference/language-specification/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1297-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1297-131">See Also</span></span>  
 <span data-ttu-id="a1297-132"><xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="a1297-132"><xref:System.Collections.Generic></span></span>   
 <span data-ttu-id="a1297-133">[C# 程式設計指南](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="a1297-133">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="a1297-134">[類型](../../../csharp/programming-guide/types/index.md) </span><span class="sxs-lookup"><span data-stu-id="a1297-134">[Types](../../../csharp/programming-guide/types/index.md) </span></span>  
 <span data-ttu-id="a1297-135">[\<類型參數>](../../../csharp/programming-guide/xmldoc/typeparam.md) </span><span class="sxs-lookup"><span data-stu-id="a1297-135">[\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md) </span></span>  
 [<span data-ttu-id="a1297-136">\<類型參數參考></span><span class="sxs-lookup"><span data-stu-id="a1297-136">\<typeparamref></span></span>](../../../csharp/programming-guide/xmldoc/typeparamref.md)

