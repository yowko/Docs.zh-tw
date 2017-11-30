---
title: "protected (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords: protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 18278ed28f899d9030d6056eca9bbe83ebec04c4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="protected-c-reference"></a><span data-ttu-id="03545-102">protected (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="03545-102">protected (C# Reference)</span></span>
<span data-ttu-id="03545-103">`protected` 關鍵字是成員存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="03545-103">The `protected` keyword is a member access modifier.</span></span> 

 > <span data-ttu-id="03545-104">此頁面都涵蓋`protected`存取。</span><span class="sxs-lookup"><span data-stu-id="03545-104">This page covers `protected` access.</span></span> <span data-ttu-id="03545-105">`protected`關鍵字也是屬於[ `protected internal` ](./protected-internal.md)和[ `private protected` ](./private-protected.md)存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="03545-105">The `protected` keyword is also part of the [`protected internal`](./protected-internal.md) and [`private protected`](./private-protected.md) access modifiers.</span></span> 

<span data-ttu-id="03545-106">受保護的成員可在其類別內由衍生類別執行個體存取。</span><span class="sxs-lookup"><span data-stu-id="03545-106">A protected member is accessible within its class and by derived class instances.</span></span> 

<span data-ttu-id="03545-107">如需 `protected` 和其他存取修飾詞的比較，請參閱[存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="03545-107">For a comparison of `protected` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> 
  
## <a name="example"></a><span data-ttu-id="03545-108">範例</span><span class="sxs-lookup"><span data-stu-id="03545-108">Example</span></span>  
 <span data-ttu-id="03545-109">只有在存取是透過衍生類別類型進行時，才可以存取衍生類別中屬於基底類別的受保護成員。</span><span class="sxs-lookup"><span data-stu-id="03545-109">A protected member of a base class is accessible in a derived class only if the access occurs through the derived class type.</span></span> <span data-ttu-id="03545-110">例如，請考慮下列程式碼區段：</span><span class="sxs-lookup"><span data-stu-id="03545-110">For example, consider the following code segment:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_1.cs)]  
  
 <span data-ttu-id="03545-111">陳述式 `a.x = 10` 會產生錯誤，因為它是在靜態方法 Main 中發出，而不是在類別 B 的執行個體中發出。</span><span class="sxs-lookup"><span data-stu-id="03545-111">The statement `a.x = 10` generates an error because it is made within the static method Main, and not an instance of class B.</span></span>  
  
 <span data-ttu-id="03545-112">結構成員不可以是受保護的成員，因為無法繼承結構。</span><span class="sxs-lookup"><span data-stu-id="03545-112">Struct members cannot be protected because the struct cannot be inherited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03545-113">範例</span><span class="sxs-lookup"><span data-stu-id="03545-113">Example</span></span>  
 <span data-ttu-id="03545-114">在此範例中，`DerivedPoint` 類別衍生自 `Point`。</span><span class="sxs-lookup"><span data-stu-id="03545-114">In this example, the class `DerivedPoint` is derived from `Point`.</span></span> <span data-ttu-id="03545-115">因此，您可以直接從衍生類別存取基底類別的受保護成員。</span><span class="sxs-lookup"><span data-stu-id="03545-115">Therefore, you can access the protected members of the base class directly from the derived class.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_2.cs)]  
  
 <span data-ttu-id="03545-116">如果您將 `x` 和 `y` 的存取層級變更為 [private](../../../csharp/language-reference/keywords/private.md)，編譯器會發出錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="03545-116">If you change the access levels of `x` and `y` to [private](../../../csharp/language-reference/keywords/private.md), the compiler will issue the error messages:</span></span>  
  
 `'Point.y' is inaccessible due to its protection level.`  
  
 `'Point.x' is inaccessible due to its protection level.`  
  
## <a name="c-language-specification"></a><span data-ttu-id="03545-117">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="03545-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="03545-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03545-118">See Also</span></span>  
 [<span data-ttu-id="03545-119">C# 參考</span><span class="sxs-lookup"><span data-stu-id="03545-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="03545-120">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="03545-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="03545-121">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="03545-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="03545-122">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="03545-122">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="03545-123">存取範圍層級</span><span class="sxs-lookup"><span data-stu-id="03545-123">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="03545-124">修飾詞</span><span class="sxs-lookup"><span data-stu-id="03545-124">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="03545-125">public</span><span class="sxs-lookup"><span data-stu-id="03545-125">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="03545-126">private</span><span class="sxs-lookup"><span data-stu-id="03545-126">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="03545-127">internal</span><span class="sxs-lookup"><span data-stu-id="03545-127">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)  
 <span data-ttu-id="03545-128">[Internal virtual 關鍵字的安全性考量](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="03545-128">[Security concerns for internal virtual keywords](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span></span>