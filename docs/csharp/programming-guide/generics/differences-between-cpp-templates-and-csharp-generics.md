---
title: C++ 樣板和 C# 泛型之間的差異 - C# 程式設計指南
description: '深入瞭解 c + + 範本和 c # 泛型之間的差異。 兩者都是支援參數化型別的語言功能。'
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], vs. C++ templates
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
ms.openlocfilehash: 58b424e4dacd8b691c353f4eda1950f9710ef081
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167362"
---
# <a name="differences-between-c-templates-and-c-generics-c-programming-guide"></a><span data-ttu-id="20f2d-104">C++ 樣板和 C# 泛型之間的差異 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="20f2d-104">Differences Between C++ Templates and C# Generics (C# Programming Guide)</span></span>

<span data-ttu-id="20f2d-105">C# 泛型和 C++ 範本都是支援參數化型別的語言功能。</span><span class="sxs-lookup"><span data-stu-id="20f2d-105">C# Generics and C++ templates are both language features that provide support for parameterized types.</span></span> <span data-ttu-id="20f2d-106">不過，這兩個之間有許多差異。</span><span class="sxs-lookup"><span data-stu-id="20f2d-106">However, there are many differences between the two.</span></span> <span data-ttu-id="20f2d-107">在語法層級，C# 泛型是沒有 C++ 範本複雜性之參數化型別的較簡單方式。</span><span class="sxs-lookup"><span data-stu-id="20f2d-107">At the syntax level, C# generics are a simpler approach to parameterized types without the complexity of C++ templates.</span></span> <span data-ttu-id="20f2d-108">此外，C# 不會嘗試提供 C++ 範本所提供的所有功能。</span><span class="sxs-lookup"><span data-stu-id="20f2d-108">In addition, C# does not attempt to provide all of the functionality that C++ templates provide.</span></span> <span data-ttu-id="20f2d-109">在實作層級，主要差異是在執行階段執行 C# 泛型型別替代，因而保留具現化物件的泛型型別資訊。</span><span class="sxs-lookup"><span data-stu-id="20f2d-109">At the implementation level, the primary difference is that C# generic type substitutions are performed at runtime and generic type information is thereby preserved for instantiated objects.</span></span> <span data-ttu-id="20f2d-110">如需詳細資訊，請參閱[執行階段中的泛型](./generics-in-the-run-time.md)。</span><span class="sxs-lookup"><span data-stu-id="20f2d-110">For more information, see [Generics in the Run Time](./generics-in-the-run-time.md).</span></span>  
  
 <span data-ttu-id="20f2d-111">下列是 C# 泛型與 C++ 範本之間的主要差異：</span><span class="sxs-lookup"><span data-stu-id="20f2d-111">The following are the key differences between C# Generics and C++ templates:</span></span>  
  
- <span data-ttu-id="20f2d-112">C# 泛型所提供的彈性量與 C++ 範本不同。</span><span class="sxs-lookup"><span data-stu-id="20f2d-112">C# generics do not provide the same amount of flexibility as C++ templates.</span></span> <span data-ttu-id="20f2d-113">例如，雖然它可以呼叫使用者定義運算子，但是無法在 C# 泛型類別中呼叫算術運算子。</span><span class="sxs-lookup"><span data-stu-id="20f2d-113">For example, it is not possible to call arithmetic operators in a C# generic class, although it is possible to call user defined operators.</span></span>  
  
- <span data-ttu-id="20f2d-114">C# 不允許非類型範本參數，例如 `template C<int i> {}`。</span><span class="sxs-lookup"><span data-stu-id="20f2d-114">C# does not allow non-type template parameters, such as `template C<int i> {}`.</span></span>  
  
- <span data-ttu-id="20f2d-115">C# 不支援明確特製化，即特定類型之範本的自訂實作。</span><span class="sxs-lookup"><span data-stu-id="20f2d-115">C# does not support explicit specialization; that is, a custom implementation of a template for a specific type.</span></span>  
  
- <span data-ttu-id="20f2d-116">C# 不支援部分特製化：類型引數子集的自訂實作。</span><span class="sxs-lookup"><span data-stu-id="20f2d-116">C# does not support partial specialization: a custom implementation for a subset of the type arguments.</span></span>  
  
- <span data-ttu-id="20f2d-117">C# 不允許使用型別參數作為泛型型別的基底類別。</span><span class="sxs-lookup"><span data-stu-id="20f2d-117">C# does not allow the type parameter to be used as the base class for the generic type.</span></span>  
  
- <span data-ttu-id="20f2d-118">C# 不允許型別參數具有預設類型。</span><span class="sxs-lookup"><span data-stu-id="20f2d-118">C# does not allow type parameters to have default types.</span></span>  
  
- <span data-ttu-id="20f2d-119">在 C# 中，雖然可以使用建構的類型作為泛型，但是泛型型別參數本身不能是泛型。</span><span class="sxs-lookup"><span data-stu-id="20f2d-119">In C#, a generic type parameter cannot itself be a generic, although constructed types can be used as generics.</span></span> <span data-ttu-id="20f2d-120">C++ 確實允許範本參數。</span><span class="sxs-lookup"><span data-stu-id="20f2d-120">C++ does allow template parameters.</span></span>  
  
- <span data-ttu-id="20f2d-121">C++ 允許不適用於範本中所有型別參數的程式碼，接著檢查用作型別參數的特定類型。</span><span class="sxs-lookup"><span data-stu-id="20f2d-121">C++ allows code that might not be valid for all type parameters in the template, which is then checked for the specific type used as the type parameter.</span></span> <span data-ttu-id="20f2d-122">C# 需要撰寫類別中的程式碼，因此，將會使用符合條件約束的任何類型。</span><span class="sxs-lookup"><span data-stu-id="20f2d-122">C# requires code in a class to be written in such a way that it will work with any type that satisfies the constraints.</span></span> <span data-ttu-id="20f2d-123">例如，在 C++ 中，可以撰寫在型別參數的物件上使用算術運算子 `+` 和 `-` 的函式，這樣會在使用不支援這些運算子的類型來具現化範本時產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="20f2d-123">For example, in C++ it is possible to write a function that uses the arithmetic operators `+` and `-` on objects of the type parameter, which will produce an error at the time of instantiation of the template with a type that does not support these operators.</span></span> <span data-ttu-id="20f2d-124">C# 不允許這項作業；允許的唯一語言建構是可從條件約束推算的語言建構。</span><span class="sxs-lookup"><span data-stu-id="20f2d-124">C# disallows this; the only language constructs allowed are those that can be deduced from the constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20f2d-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20f2d-125">See also</span></span>

- [<span data-ttu-id="20f2d-126">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="20f2d-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="20f2d-127">泛型簡介</span><span class="sxs-lookup"><span data-stu-id="20f2d-127">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="20f2d-128">範本</span><span class="sxs-lookup"><span data-stu-id="20f2d-128">Templates</span></span>](/cpp/cpp/templates-cpp)
