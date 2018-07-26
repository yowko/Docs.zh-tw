---
title: protected (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: a3115fe82b452f52ee75cf222302ece0fc67b330
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2018
ms.locfileid: "39243622"
---
# <a name="protected-c-reference"></a><span data-ttu-id="45722-102">protected (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="45722-102">protected (C# Reference)</span></span>
<span data-ttu-id="45722-103">`protected` 關鍵字是成員存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="45722-103">The `protected` keyword is a member access modifier.</span></span> 

 > <span data-ttu-id="45722-104">此頁面涵蓋 `protected` 存取。</span><span class="sxs-lookup"><span data-stu-id="45722-104">This page covers `protected` access.</span></span> <span data-ttu-id="45722-105">`protected` 關鍵字也是屬於 [`protected internal`](./protected-internal.md) 和 [`private protected`](./private-protected.md) 存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="45722-105">The `protected` keyword is also part of the [`protected internal`](./protected-internal.md) and [`private protected`](./private-protected.md) access modifiers.</span></span> 

<span data-ttu-id="45722-106">受保護的成員可在其類別內由衍生類別執行個體存取。</span><span class="sxs-lookup"><span data-stu-id="45722-106">A protected member is accessible within its class and by derived class instances.</span></span> 

<span data-ttu-id="45722-107">如需 `protected` 和其他存取修飾詞的比較，請參閱[存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="45722-107">For a comparison of `protected` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> 
  
## <a name="example"></a><span data-ttu-id="45722-108">範例</span><span class="sxs-lookup"><span data-stu-id="45722-108">Example</span></span>  
 <span data-ttu-id="45722-109">只有在存取是透過衍生類別類型進行時，才可以存取衍生類別中屬於基底類別的受保護成員。</span><span class="sxs-lookup"><span data-stu-id="45722-109">A protected member of a base class is accessible in a derived class only if the access occurs through the derived class type.</span></span> <span data-ttu-id="45722-110">例如，請考慮下列程式碼區段：</span><span class="sxs-lookup"><span data-stu-id="45722-110">For example, consider the following code segment:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_1.cs)]  
  
 <span data-ttu-id="45722-111">陳述式 `a.x = 10` 會產生錯誤，因為它是在靜態方法 Main 中發出，而不是在類別 B 的執行個體中發出。</span><span class="sxs-lookup"><span data-stu-id="45722-111">The statement `a.x = 10` generates an error because it is made within the static method Main, and not an instance of class B.</span></span>  
  
 <span data-ttu-id="45722-112">結構成員不可以是受保護的成員，因為無法繼承結構。</span><span class="sxs-lookup"><span data-stu-id="45722-112">Struct members cannot be protected because the struct cannot be inherited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45722-113">範例</span><span class="sxs-lookup"><span data-stu-id="45722-113">Example</span></span>  
 <span data-ttu-id="45722-114">在此範例中，`DerivedPoint` 類別衍生自 `Point`。</span><span class="sxs-lookup"><span data-stu-id="45722-114">In this example, the class `DerivedPoint` is derived from `Point`.</span></span> <span data-ttu-id="45722-115">因此，您可以直接從衍生類別存取基底類別的受保護成員。</span><span class="sxs-lookup"><span data-stu-id="45722-115">Therefore, you can access the protected members of the base class directly from the derived class.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_2.cs)]  
  
 <span data-ttu-id="45722-116">如果您將 `x` 和 `y` 的存取層級變更為 [private](../../../csharp/language-reference/keywords/private.md)，編譯器會發出錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="45722-116">If you change the access levels of `x` and `y` to [private](../../../csharp/language-reference/keywords/private.md), the compiler will issue the error messages:</span></span>  
  
 `'Point.y' is inaccessible due to its protection level.`  
  
 `'Point.x' is inaccessible due to its protection level.`  
  
## <a name="c-language-specification"></a><span data-ttu-id="45722-117">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="45722-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="45722-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="45722-118">See Also</span></span>  
 [<span data-ttu-id="45722-119">C# 參考</span><span class="sxs-lookup"><span data-stu-id="45722-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="45722-120">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="45722-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="45722-121">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="45722-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="45722-122">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="45722-122">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="45722-123">存取範圍層級</span><span class="sxs-lookup"><span data-stu-id="45722-123">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="45722-124">修飾詞</span><span class="sxs-lookup"><span data-stu-id="45722-124">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="45722-125">public</span><span class="sxs-lookup"><span data-stu-id="45722-125">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="45722-126">private</span><span class="sxs-lookup"><span data-stu-id="45722-126">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="45722-127">internal</span><span class="sxs-lookup"><span data-stu-id="45722-127">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)  
 <span data-ttu-id="45722-128">[internal virtual 關鍵字的安全性考量](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="45722-128">[Security concerns for internal virtual keywords](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span></span>