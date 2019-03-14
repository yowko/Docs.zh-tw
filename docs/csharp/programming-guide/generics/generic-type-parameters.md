---
title: 泛型型別參數 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: 10feb47ce3dfe9e356da381e0d62e6d220c9452a
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57677418"
---
# <a name="generic-type-parameters-c-programming-guide"></a><span data-ttu-id="2a123-102">泛型型別參數 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="2a123-102">Generic type parameters (C# Programming Guide)</span></span>

<span data-ttu-id="2a123-103">在泛型型別或方法定義中，當型別參數建立泛型型別的執行個體時，它們是用戶端指定之特定類型的預留位置。</span><span class="sxs-lookup"><span data-stu-id="2a123-103">In a generic type or method definition, a type parameter is a placeholder for a specific type that a client specifies when they create an instance of the generic type.</span></span> <span data-ttu-id="2a123-104">泛型類別，例如[泛型簡介](../../../csharp/programming-guide/generics/introduction-to-generics.md)中所列的 `GenericList<T>`，不能以現況使用，因為它其實不是類型，更像是類型的藍圖。</span><span class="sxs-lookup"><span data-stu-id="2a123-104">A generic class, such as `GenericList<T>` listed in [Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md), cannot be used as-is because it is not really a type; it is more like a blueprint for a type.</span></span> <span data-ttu-id="2a123-105">若要使用 `GenericList<T>`，用戶端程式碼必須在角括弧內指定型別引數，宣告並具現化建構的類型。</span><span class="sxs-lookup"><span data-stu-id="2a123-105">To use `GenericList<T>`, client code must declare and instantiate a constructed type by specifying a type argument inside the angle brackets.</span></span> <span data-ttu-id="2a123-106">此特定類別的型別引數可以是由編譯器辨識出的任何類型。</span><span class="sxs-lookup"><span data-stu-id="2a123-106">The type argument for this particular class can be any type recognized by the compiler.</span></span> <span data-ttu-id="2a123-107">您可以建立任何數目的建構類型執行個體，每一個使用不同的型別引數，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2a123-107">Any number of constructed type instances can be created, each one using a different type argument, as follows:</span></span>  
  
[!code-csharp[csProgGuideGenerics#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#7)]  
  
<span data-ttu-id="2a123-108">這些 `GenericList<T>` 執行個體的每一個中，類別中出現的每個 `T`，在執行階段會被型別引數取代。</span><span class="sxs-lookup"><span data-stu-id="2a123-108">In each of these instances of `GenericList<T>`, every occurrence of `T` in the class is substituted at run time with the type argument.</span></span> <span data-ttu-id="2a123-109">透過這個替代，我們已經使用單一類別定義建立了三個類型安全且有效率的不同物件。</span><span class="sxs-lookup"><span data-stu-id="2a123-109">By means of this substitution, we have created three separate type-safe and efficient objects using a single class definition.</span></span> <span data-ttu-id="2a123-110">如需 CLR 如何執行此替代的詳細資訊，請參閱[執行階段中的泛型](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)。</span><span class="sxs-lookup"><span data-stu-id="2a123-110">For more information on how this substitution is performed by the CLR, see [Generics in the Run Time](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span></span>  
  
## <a name="type-parameter-naming-guidelines"></a><span data-ttu-id="2a123-111">型別參數命名方針</span><span class="sxs-lookup"><span data-stu-id="2a123-111">Type parameter naming guidelines</span></span>  
  
- <span data-ttu-id="2a123-112">**務必**使用描述性的名稱命名泛型型別參數，除非單一字母名稱足以表明，而且描述性名稱不會新增值。</span><span class="sxs-lookup"><span data-stu-id="2a123-112">**Do** name generic type parameters with descriptive names, unless a single letter name is completely self explanatory and a descriptive name would not add value.</span></span>  
  
   [!code-csharp[csProgGuideGenerics#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#8)]  
  
- <span data-ttu-id="2a123-113">單一字母型別參數的類型**請考慮**使用 T 做為型別參數名稱。</span><span class="sxs-lookup"><span data-stu-id="2a123-113">**Consider** using T as the type parameter name for types with one single letter type parameter.</span></span>  
  
   [!code-csharp[csProgGuideGenerics#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#9)]  
  
- <span data-ttu-id="2a123-114">描述性型別參數名稱前面**務必**加上 "T"。</span><span class="sxs-lookup"><span data-stu-id="2a123-114">**Do** prefix descriptive type parameter names with "T".</span></span>  
  
   [!code-csharp[csProgGuideGenerics#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#10)]  
  
- <span data-ttu-id="2a123-115">**請考慮**在參數名稱中指出放在型別參數上的條件約束。</span><span class="sxs-lookup"><span data-stu-id="2a123-115">**Consider** indicating constraints placed on a type parameter in the name of parameter.</span></span> <span data-ttu-id="2a123-116">例如，參數的條件約束為 `ISession` 可能稱為 `TSession`。</span><span class="sxs-lookup"><span data-stu-id="2a123-116">For example, a parameter constrained to `ISession` may be called `TSession`.</span></span>

<span data-ttu-id="2a123-117">程式碼分析規則 [CA1715](/visualstudio/code-quality/ca1715-identifiers-should-have-correct-prefix) 可用於確保適當地命名型別參數。</span><span class="sxs-lookup"><span data-stu-id="2a123-117">The code analysis rule [CA1715](/visualstudio/code-quality/ca1715-identifiers-should-have-correct-prefix) can be used to ensure that type parameters are named appropriately.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2a123-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a123-118">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="2a123-119">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="2a123-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="2a123-120">泛型</span><span class="sxs-lookup"><span data-stu-id="2a123-120">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
- [<span data-ttu-id="2a123-121">C++ 範本和 C# 泛型之間的差異</span><span class="sxs-lookup"><span data-stu-id="2a123-121">Differences Between C++ Templates and C# Generics</span></span>](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)
