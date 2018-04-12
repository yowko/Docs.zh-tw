---
title: C++ 樣板和 C# 泛型之間的差異 (C# 程式設計手冊)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], vs. C++ templates
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: aea1b51c26a8f3de56ea66b9cf89e75bfeb59d81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-c-templates-and-c-generics-c-programming-guide"></a><span data-ttu-id="12eba-102">C++ 樣板和 C# 泛型之間的差異 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="12eba-102">Differences Between C++ Templates and C# Generics (C# Programming Guide)</span></span>
<span data-ttu-id="12eba-103">C# 泛型和 C++ 範本都是支援參數化型別的語言功能。</span><span class="sxs-lookup"><span data-stu-id="12eba-103">C# Generics and C++ templates are both language features that provide support for parameterized types.</span></span> <span data-ttu-id="12eba-104">不過，這兩個之間有許多差異。</span><span class="sxs-lookup"><span data-stu-id="12eba-104">However, there are many differences between the two.</span></span> <span data-ttu-id="12eba-105">在語法層級，C# 泛型是沒有 C++ 範本複雜性之參數化型別的較簡單方式。</span><span class="sxs-lookup"><span data-stu-id="12eba-105">At the syntax level, C# generics are a simpler approach to parameterized types without the complexity of C++ templates.</span></span> <span data-ttu-id="12eba-106">此外，C# 不會嘗試提供 C++ 範本所提供的所有功能。</span><span class="sxs-lookup"><span data-stu-id="12eba-106">In addition, C# does not attempt to provide all of the functionality that C++ templates provide.</span></span> <span data-ttu-id="12eba-107">在實作層級，主要差異是在執行階段執行 C# 泛型型別替代，因而保留具現化物件的泛型型別資訊。</span><span class="sxs-lookup"><span data-stu-id="12eba-107">At the implementation level, the primary difference is that C# generic type substitutions are performed at runtime and generic type information is thereby preserved for instantiated objects.</span></span> <span data-ttu-id="12eba-108">如需詳細資訊，請參閱[執行階段中的泛型](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)。</span><span class="sxs-lookup"><span data-stu-id="12eba-108">For more information, see [Generics in the Run Time](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span></span>  
  
 <span data-ttu-id="12eba-109">下列是 C# 泛型與 C++ 範本之間的主要差異：</span><span class="sxs-lookup"><span data-stu-id="12eba-109">The following are the key differences between C# Generics and C++ templates:</span></span>  
  
-   <span data-ttu-id="12eba-110">C# 泛型所提供的彈性量與 C++ 範本不同。</span><span class="sxs-lookup"><span data-stu-id="12eba-110">C# generics do not provide the same amount of flexibility as C++ templates.</span></span> <span data-ttu-id="12eba-111">例如，雖然它可以呼叫使用者定義運算子，但是無法在 C# 泛型類別中呼叫算術運算子。</span><span class="sxs-lookup"><span data-stu-id="12eba-111">For example, it is not possible to call arithmetic operators in a C# generic class, although it is possible to call user defined operators.</span></span>  
  
-   <span data-ttu-id="12eba-112">C# 不允許非類型範本參數，例如 `template C<int i> {}`。</span><span class="sxs-lookup"><span data-stu-id="12eba-112">C# does not allow non-type template parameters, such as `template C<int i> {}`.</span></span>  
  
-   <span data-ttu-id="12eba-113">C# 不支援明確特製化，即特定類型之範本的自訂實作。</span><span class="sxs-lookup"><span data-stu-id="12eba-113">C# does not support explicit specialization; that is, a custom implementation of a template for a specific type.</span></span>  
  
-   <span data-ttu-id="12eba-114">C# 不支援部分特製化：類型引數子集的自訂實作。</span><span class="sxs-lookup"><span data-stu-id="12eba-114">C# does not support partial specialization: a custom implementation for a subset of the type arguments.</span></span>  
  
-   <span data-ttu-id="12eba-115">C# 不允許使用型別參數作為泛型型別的基底類別。</span><span class="sxs-lookup"><span data-stu-id="12eba-115">C# does not allow the type parameter to be used as the base class for the generic type.</span></span>  
  
-   <span data-ttu-id="12eba-116">C# 不允許型別參數具有預設類型。</span><span class="sxs-lookup"><span data-stu-id="12eba-116">C# does not allow type parameters to have default types.</span></span>  
  
-   <span data-ttu-id="12eba-117">在 C# 中，雖然可以使用建構的類型作為泛型，但是泛型型別參數本身不能是泛型。</span><span class="sxs-lookup"><span data-stu-id="12eba-117">In C#, a generic type parameter cannot itself be a generic, although constructed types can be used as generics.</span></span> <span data-ttu-id="12eba-118">C++ 確實允許範本參數。</span><span class="sxs-lookup"><span data-stu-id="12eba-118">C++ does allow template parameters.</span></span>  
  
-   <span data-ttu-id="12eba-119">C++ 允許不適用於範本中所有型別參數的程式碼，接著檢查用作型別參數的特定類型。</span><span class="sxs-lookup"><span data-stu-id="12eba-119">C++ allows code that might not be valid for all type parameters in the template, which is then checked for the specific type used as the type parameter.</span></span> <span data-ttu-id="12eba-120">C# 需要撰寫類別中的程式碼，因此，將會使用符合條件約束的任何類型。</span><span class="sxs-lookup"><span data-stu-id="12eba-120">C# requires code in a class to be written in such a way that it will work with any type that satisfies the constraints.</span></span> <span data-ttu-id="12eba-121">例如，在 C++ 中，可以撰寫在型別參數的物件上使用算術運算子 `+` 和 `-` 的函式，這樣會在使用不支援這些運算子的類型來具現化範本時產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="12eba-121">For example, in C++ it is possible to write a function that uses the arithmetic operators `+` and `-` on objects of the type parameter, which will produce an error at the time of instantiation of the template with a type that does not support these operators.</span></span> <span data-ttu-id="12eba-122">C# 不允許這項作業；允許的唯一語言建構是可從條件約束推算的語言建構。</span><span class="sxs-lookup"><span data-stu-id="12eba-122">C# disallows this; the only language constructs allowed are those that can be deduced from the constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12eba-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12eba-123">See Also</span></span>  
 [<span data-ttu-id="12eba-124">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="12eba-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="12eba-125">泛型簡介</span><span class="sxs-lookup"><span data-stu-id="12eba-125">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [<span data-ttu-id="12eba-126">範本</span><span class="sxs-lookup"><span data-stu-id="12eba-126">Templates</span></span>](/cpp/cpp/templates-cpp)
