---
title: private (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: 89bc23e91bf693f0a95b75dffe2399cb7e865b50
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2018
---
# <a name="private-c-reference"></a><span data-ttu-id="95031-102">private (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="95031-102">private (C# Reference)</span></span>
<span data-ttu-id="95031-103">`private` 關鍵字是成員存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="95031-103">The `private` keyword is a member access modifier.</span></span> 
   
 > <span data-ttu-id="95031-104">此頁面涵蓋 `private` 存取。</span><span class="sxs-lookup"><span data-stu-id="95031-104">This page covers `private` access.</span></span> <span data-ttu-id="95031-105">`private` 關鍵字也是屬於 [`private protected`](./private-protected.md) 存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="95031-105">The `private` keyword is also part of the [`private protected`](./private-protected.md) access modifier.</span></span>
  
<span data-ttu-id="95031-106">私用存取是最嚴格的存取層級。</span><span class="sxs-lookup"><span data-stu-id="95031-106">Private access is the least permissive access level.</span></span> <span data-ttu-id="95031-107">私用成員只能在宣告它們的類別主體或結構主體內存取，如本範例所示：</span><span class="sxs-lookup"><span data-stu-id="95031-107">Private members are accessible only within the body of the class or the struct in which they are declared, as in this example:</span></span>  
  
```csharp  
class Employee  
{  
    private int i;  
    double d;   // private access by default  
}  
```  

 <span data-ttu-id="95031-108">相同主體內的巢狀型別也可以存取這些私用成員。</span><span class="sxs-lookup"><span data-stu-id="95031-108">Nested types in the same body can also access those private members.</span></span>  
  
 <span data-ttu-id="95031-109">在宣告私用成員的類別或結構外部參考私用成員是編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="95031-109">It is a compile-time error to reference a private member outside the class or the struct in which it is declared.</span></span>  
  
 <span data-ttu-id="95031-110">如需 `private` 和其他存取修飾詞的比較，請參閱[存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md)和[存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="95031-110">For a comparison of `private` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) and [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="95031-111">範例</span><span class="sxs-lookup"><span data-stu-id="95031-111">Example</span></span>  
 <span data-ttu-id="95031-112">在此範例中，`Employee` 類別包含兩個私用資料成員：`name` 和 `salary`。</span><span class="sxs-lookup"><span data-stu-id="95031-112">In this example, the `Employee` class contains two private data members, `name` and `salary`.</span></span> <span data-ttu-id="95031-113">作為私用成員，只有成員方法能加以存取。</span><span class="sxs-lookup"><span data-stu-id="95031-113">As private members, they cannot be accessed except by member methods.</span></span> <span data-ttu-id="95031-114">因此會新增名為 `GetName` 和 `Salary` 的公用方法，以允許對這些私用成員的控制存取。</span><span class="sxs-lookup"><span data-stu-id="95031-114">Public methods named `GetName` and `Salary` are added to allow controlled access to the private members.</span></span> <span data-ttu-id="95031-115">`name` 成員是透過公用方法存取，`salary` 成員則是透過公用唯讀屬性存取</span><span class="sxs-lookup"><span data-stu-id="95031-115">The `name` member is accessed by way of a public method, and the `salary` member is accessed by way of a public read-only property.</span></span> <span data-ttu-id="95031-116">(如需詳細資訊，請參閱[屬性](../../../csharp/programming-guide/classes-and-structs/properties.md))。</span><span class="sxs-lookup"><span data-stu-id="95031-116">(See [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md) for more information.)</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/private_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="95031-117">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="95031-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="95031-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="95031-118">See Also</span></span>  
 [<span data-ttu-id="95031-119">C# 參考</span><span class="sxs-lookup"><span data-stu-id="95031-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="95031-120">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="95031-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="95031-121">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="95031-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="95031-122">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="95031-122">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="95031-123">存取範圍層級</span><span class="sxs-lookup"><span data-stu-id="95031-123">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="95031-124">修飾詞</span><span class="sxs-lookup"><span data-stu-id="95031-124">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="95031-125">public</span><span class="sxs-lookup"><span data-stu-id="95031-125">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="95031-126">protected</span><span class="sxs-lookup"><span data-stu-id="95031-126">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="95031-127">internal</span><span class="sxs-lookup"><span data-stu-id="95031-127">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
