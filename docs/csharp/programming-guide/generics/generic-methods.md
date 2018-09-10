---
title: 泛型方法 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
ms.openlocfilehash: 0fb5267e6324d3dffd1ad5a72ef3718c8cdd08b8
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44251478"
---
# <a name="generic-methods-c-programming-guide"></a><span data-ttu-id="50d03-102">泛型方法 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="50d03-102">Generic Methods (C# Programming Guide)</span></span>
<span data-ttu-id="50d03-103">泛型方法是使用型別參數宣告的方法，如下所示：</span><span class="sxs-lookup"><span data-stu-id="50d03-103">A generic method is a method that is declared with type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#22](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_1.cs)]  
  
 <span data-ttu-id="50d03-104">下列程式碼範例示範一種方法，使用型別引數的 `int`呼叫方法：</span><span class="sxs-lookup"><span data-stu-id="50d03-104">The following code example shows one way to call the method by using `int` for the type argument:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#23](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_2.cs)]  
  
 <span data-ttu-id="50d03-105">您也可以省略型別引數，編譯器會推斷它。</span><span class="sxs-lookup"><span data-stu-id="50d03-105">You can also omit the type argument and the compiler will infer it.</span></span> <span data-ttu-id="50d03-106">以下對 `Swap` 的呼叫，相當於先前的呼叫：</span><span class="sxs-lookup"><span data-stu-id="50d03-106">The following call to `Swap` is equivalent to the previous call:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#24](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_3.cs)]  
  
 <span data-ttu-id="50d03-107">相同的型別推斷規則適用於靜態方法和執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="50d03-107">The same rules for type inference apply to static methods and instance methods.</span></span> <span data-ttu-id="50d03-108">編譯器可以根據您傳入的方法引數推斷型別參數，但無法只從條件約束或傳回值推斷型別參數。</span><span class="sxs-lookup"><span data-stu-id="50d03-108">The compiler can infer the type parameters based on the method arguments you pass in; it cannot infer the type parameters only from a constraint or return value.</span></span> <span data-ttu-id="50d03-109">因此，型別推斷對沒有參數的方法不起作用。</span><span class="sxs-lookup"><span data-stu-id="50d03-109">Therefore type inference does not work with methods that have no parameters.</span></span> <span data-ttu-id="50d03-110">編譯時期先出現型別推斷，編譯器才嘗試解析多載的方法簽章。</span><span class="sxs-lookup"><span data-stu-id="50d03-110">Type inference occurs at compile time before the compiler tries to resolve overloaded method signatures.</span></span> <span data-ttu-id="50d03-111">編譯器會將型別推斷邏輯套用到所有共用相同名稱的泛型方法。</span><span class="sxs-lookup"><span data-stu-id="50d03-111">The compiler applies type inference logic to all generic methods that share the same name.</span></span> <span data-ttu-id="50d03-112">在多載解析步驟中，編譯器只包含型別推斷已成功的那些泛型方法。</span><span class="sxs-lookup"><span data-stu-id="50d03-112">In the overload resolution step, the compiler includes only those generic methods on which type inference succeeded.</span></span>  
  
 <span data-ttu-id="50d03-113">在泛型類別中，非泛型方法可以存取類別層級類型的參數，如下所示：</span><span class="sxs-lookup"><span data-stu-id="50d03-113">Within a generic class, non-generic methods can access the class-level type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#25](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_4.cs)]  
  
 <span data-ttu-id="50d03-114">如果您定義的泛型方法接受與包含類別相同的型別參數，編譯器會產生警告 CS0693，因為在方法範圍內，為內部 `T` 提供的引數會隱藏為外部 `T` 提供的引數。</span><span class="sxs-lookup"><span data-stu-id="50d03-114">If you define a generic method that takes the same type parameters as the containing class, the compiler generates warning CS0693 because within the method scope, the argument supplied for the inner `T` hides the argument supplied for the outer `T`.</span></span> <span data-ttu-id="50d03-115">在類別具現化後，如果您需要以不是提供的型別引數來彈性呼叫泛型類別方法，請考慮為方法的型別參數提供另一個識別碼，如下列範例中的 `GenericList2<T>` 所示。</span><span class="sxs-lookup"><span data-stu-id="50d03-115">If you require the flexibility of calling a generic class method with type arguments other than the ones provided when the class was instantiated, consider providing another identifier for the type parameter of the method, as shown in `GenericList2<T>` in the following example.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#26](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_5.cs)]  
  
 <span data-ttu-id="50d03-116">使用條件約束，在方法中的型別參數上啟用更多特定作業。</span><span class="sxs-lookup"><span data-stu-id="50d03-116">Use constraints to enable more specialized operations on type parameters in methods.</span></span> <span data-ttu-id="50d03-117">本版的 `Swap<T>` 現在名為 `SwapIfGreater<T>`，只能搭配實作 <xref:System.IComparable%601> 的型別引數一起使用。</span><span class="sxs-lookup"><span data-stu-id="50d03-117">This version of `Swap<T>`, now named `SwapIfGreater<T>`, can only be used with type arguments that implement <xref:System.IComparable%601>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#27](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_6.cs)]  
  
 <span data-ttu-id="50d03-118">泛型方法可以多載到數個型別參數上。</span><span class="sxs-lookup"><span data-stu-id="50d03-118">Generic methods can be overloaded on several type parameters.</span></span> <span data-ttu-id="50d03-119">例如，下列方法可以全都位於相同的類別中：</span><span class="sxs-lookup"><span data-stu-id="50d03-119">For example, the following methods can all be located in the same class:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#28](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_7.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="50d03-120">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="50d03-120">C# Language Specification</span></span>  
 <span data-ttu-id="50d03-121">如需詳細資訊，請參閱＜[C# 語言規格](../../../csharp/language-reference/language-specification/index.md)＞。</span><span class="sxs-lookup"><span data-stu-id="50d03-121">For more information, see the [C# Language Specification](../../../csharp/language-reference/language-specification/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50d03-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="50d03-122">See Also</span></span>

- <xref:System.Collections.Generic>  
- [<span data-ttu-id="50d03-123">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="50d03-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="50d03-124">泛型簡介</span><span class="sxs-lookup"><span data-stu-id="50d03-124">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
- [<span data-ttu-id="50d03-125">方法</span><span class="sxs-lookup"><span data-stu-id="50d03-125">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
