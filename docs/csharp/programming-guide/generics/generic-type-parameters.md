---
title: 泛型型別參數 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: 48fa90226b7a8a36f5f432921cf5d999e76c6fa8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681634"
---
# <a name="generic-type-parameters-c-programming-guide"></a><span data-ttu-id="5f2ac-102">泛型型別參數 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="5f2ac-102">Generic Type Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="5f2ac-103">在泛型型別或方法定義中，當型別參數具現化泛型型別的變數時，它們是用戶端指定之特定類型的預留位置。</span><span class="sxs-lookup"><span data-stu-id="5f2ac-103">In a generic type or method definition, a type parameters is a placeholder for a specific type that a client specifies when they instantiate a variable of the generic type.</span></span> <span data-ttu-id="5f2ac-104">泛型類別，例如[泛型簡介](../../../csharp/programming-guide/generics/introduction-to-generics.md)中所列的 `GenericList<T>`，不能以現況使用，因為它其實不是類型，更像是類型的藍圖。</span><span class="sxs-lookup"><span data-stu-id="5f2ac-104">A generic class, such as `GenericList<T>` listed in [Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md), cannot be used as-is because it is not really a type; it is more like a blueprint for a type.</span></span> <span data-ttu-id="5f2ac-105">若要使用 `GenericList<T>`，用戶端程式碼必須在角括弧內指定型別引數，宣告並具現化建構的類型。</span><span class="sxs-lookup"><span data-stu-id="5f2ac-105">To use `GenericList<T>`, client code must declare and instantiate a constructed type by specifying a type argument inside the angle brackets.</span></span> <span data-ttu-id="5f2ac-106">此特定類別的型別引數可以是由編譯器辨識出的任何類型。</span><span class="sxs-lookup"><span data-stu-id="5f2ac-106">The type argument for this particular class can be any type recognized by the compiler.</span></span> <span data-ttu-id="5f2ac-107">您可以建立任何數目的建構類型執行個體，每一個使用不同的型別引數，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5f2ac-107">Any number of constructed type instances can be created, each one using a different type argument, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#7](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_1.cs)]  
  
 <span data-ttu-id="5f2ac-108">這些 `GenericList<T>` 執行個體的每一個中，類別中出現的每個 `T`，在執行階段都會被型別引數取代。</span><span class="sxs-lookup"><span data-stu-id="5f2ac-108">In each of these instances of `GenericList<T>`, every occurrence of `T` in the class will be substituted at run time with the type argument.</span></span> <span data-ttu-id="5f2ac-109">透過這個替代，我們已經使用單一類別定義建立了三個類型安全且有效率的不同物件。</span><span class="sxs-lookup"><span data-stu-id="5f2ac-109">By means of this substitution, we have created three separate type-safe and efficient objects using a single class definition.</span></span> <span data-ttu-id="5f2ac-110">如需 CLR 如何執行此替代的詳細資訊，請參閱[執行階段中的泛型](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)。</span><span class="sxs-lookup"><span data-stu-id="5f2ac-110">For more information on how this substitution is performed by the CLR, see [Generics in the Run Time](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span></span>  
  
## <a name="type-parameter-naming-guidelines"></a><span data-ttu-id="5f2ac-111">型別參數命名方針</span><span class="sxs-lookup"><span data-stu-id="5f2ac-111">Type Parameter Naming Guidelines</span></span>  
  
-   <span data-ttu-id="5f2ac-112">**務必**使用描述性的名稱命名泛型型別參數，除非單一字母名稱足以表明，而且描述性名稱不會新增值。</span><span class="sxs-lookup"><span data-stu-id="5f2ac-112">**Do** name generic type parameters with descriptive names, unless a single letter name is completely self explanatory and a descriptive name would not add value.</span></span>  
  
     [!code-csharp[csProgGuideGenerics#8](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_2.cs)]  
  
-   <span data-ttu-id="5f2ac-113">單一字母型別參數的類型**請考慮**使用 T 做為型別參數名稱。</span><span class="sxs-lookup"><span data-stu-id="5f2ac-113">**Consider** using T as the type parameter name for types with one single letter type parameter.</span></span>  
  
     [!code-csharp[csProgGuideGenerics#9](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_3.cs)]  
  
-   <span data-ttu-id="5f2ac-114">描述性型別參數名稱前面**務必**加上 "T"。</span><span class="sxs-lookup"><span data-stu-id="5f2ac-114">**Do** prefix descriptive type parameter names with "T".</span></span>  
  
     [!code-csharp[csProgGuideGenerics#10](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_4.cs)]  
  
-   <span data-ttu-id="5f2ac-115">**請考慮**在參數名稱中指出放在型別參數上的條件約束。</span><span class="sxs-lookup"><span data-stu-id="5f2ac-115">**Consider** indicating constraints placed on a type parameter in the name of parameter.</span></span> <span data-ttu-id="5f2ac-116">例如，參數的條件約束為 `ISession` 可能稱為 `TSession`。</span><span class="sxs-lookup"><span data-stu-id="5f2ac-116">For example, a parameter constrained to `ISession` may be called `TSession`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f2ac-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f2ac-117">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="5f2ac-118">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="5f2ac-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="5f2ac-119">泛型</span><span class="sxs-lookup"><span data-stu-id="5f2ac-119">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
- [<span data-ttu-id="5f2ac-120">C++ 範本和 C# 泛型之間的差異</span><span class="sxs-lookup"><span data-stu-id="5f2ac-120">Differences Between C++ Templates and C# Generics</span></span>](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)
