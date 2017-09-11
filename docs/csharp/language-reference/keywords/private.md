---
title: "private (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- private_CSharpKeyword
- private
dev_langs:
- CSharp
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
caps.latest.revision: 17
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
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c18fd87b12bf3f7f1a1d1ef0dfded8643308169c
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="private-c-reference"></a><span data-ttu-id="86c91-102">private (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="86c91-102">private (C# Reference)</span></span>
<span data-ttu-id="86c91-103">`private` 關鍵字是成員存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="86c91-103">The `private` keyword is a member access modifier.</span></span> <span data-ttu-id="86c91-104">私用存取是最嚴格的存取層級。</span><span class="sxs-lookup"><span data-stu-id="86c91-104">Private access is the least permissive access level.</span></span> <span data-ttu-id="86c91-105">私用成員只能在宣告它們的類別主體或結構主體內存取，如本範例所示：</span><span class="sxs-lookup"><span data-stu-id="86c91-105">Private members are accessible only within the body of the class or the struct in which they are declared, as in this example:</span></span>  
  
```  
class Employee  
{  
    private int i;  
    double d;   // private access by default  
}  
```  
  
 <span data-ttu-id="86c91-106">相同主體內的巢狀型別也可以存取這些私用成員。</span><span class="sxs-lookup"><span data-stu-id="86c91-106">Nested types in the same body can also access those private members.</span></span>  
  
 <span data-ttu-id="86c91-107">在宣告私用成員的類別或結構外部參考私用成員是編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="86c91-107">It is a compile-time error to reference a private member outside the class or the struct in which it is declared.</span></span>  
  
 <span data-ttu-id="86c91-108">如需 `private` 和其他存取修飾詞的比較，請參閱[存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md)和[存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="86c91-108">For a comparison of `private` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) and [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="86c91-109">範例</span><span class="sxs-lookup"><span data-stu-id="86c91-109">Example</span></span>  
 <span data-ttu-id="86c91-110">在此範例中，`Employee` 類別包含兩個私用資料成員：`name` 和 `salary`。</span><span class="sxs-lookup"><span data-stu-id="86c91-110">In this example, the `Employee` class contains two private data members, `name` and `salary`.</span></span> <span data-ttu-id="86c91-111">作為私用成員，只有成員方法能加以存取。</span><span class="sxs-lookup"><span data-stu-id="86c91-111">As private members, they cannot be accessed except by member methods.</span></span> <span data-ttu-id="86c91-112">因此會新增名為 `GetName` 和 `Salary` 的公用方法，以允許對這些私用成員的控制存取。</span><span class="sxs-lookup"><span data-stu-id="86c91-112">Public methods named `GetName` and `Salary` are added to allow controlled access to the private members.</span></span> <span data-ttu-id="86c91-113">`name` 成員是透過公用方法存取，`salary` 成員則是透過公用唯讀屬性存取</span><span class="sxs-lookup"><span data-stu-id="86c91-113">The `name` member is accessed by way of a public method, and the `salary` member is accessed by way of a public read-only property.</span></span> <span data-ttu-id="86c91-114">(如需詳細資訊，請參閱[屬性](../../../csharp/programming-guide/classes-and-structs/properties.md))。</span><span class="sxs-lookup"><span data-stu-id="86c91-114">(See [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md) for more information.)</span></span>  
  
 <span data-ttu-id="86c91-115">[!code-cs[csrefKeywordsModifiers#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/private_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="86c91-115">[!code-cs[csrefKeywordsModifiers#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/private_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="86c91-116">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="86c91-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="86c91-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86c91-117">See Also</span></span>  
 <span data-ttu-id="86c91-118">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="86c91-118">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="86c91-119">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="86c91-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="86c91-120">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="86c91-120">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="86c91-121">[存取修飾詞](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="86c91-121">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="86c91-122">[存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="86c91-122">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) </span></span>  
 <span data-ttu-id="86c91-123">[修飾詞](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="86c91-123">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="86c91-124">[public](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="86c91-124">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="86c91-125">[protected](../../../csharp/language-reference/keywords/protected.md) </span><span class="sxs-lookup"><span data-stu-id="86c91-125">[protected](../../../csharp/language-reference/keywords/protected.md) </span></span>  
 [<span data-ttu-id="86c91-126">internal</span><span class="sxs-lookup"><span data-stu-id="86c91-126">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)

