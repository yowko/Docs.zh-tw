---
title: "存取範圍定義域 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
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
ms.openlocfilehash: 90faf22d8a7d515ae8bd062f0b95f4be5e051f79
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="accessibility-domain-c-reference"></a><span data-ttu-id="24c5d-102">存取範圍定義域 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="24c5d-102">Accessibility Domain (C# Reference)</span></span>
<span data-ttu-id="24c5d-103">成員的存取範圍定義域指定可參考成員的程式區段。</span><span class="sxs-lookup"><span data-stu-id="24c5d-103">The accessibility domain of a member specifies in which program sections a member can be referenced.</span></span> <span data-ttu-id="24c5d-104">如果成員巢狀在另一個類型內，則其存取範圍定義域是由成員的[存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md)和立即包含類型的存取範圍定義域所決定。</span><span class="sxs-lookup"><span data-stu-id="24c5d-104">If the member is nested within another type, its accessibility domain is determined by both the [accessibility level](../../../csharp/language-reference/keywords/accessibility-levels.md) of the member and the accessibility domain of the immediately containing type.</span></span>  
  
 <span data-ttu-id="24c5d-105">最上層類型的存取範圍定義域是至少在其中宣告之專案的程式文字。</span><span class="sxs-lookup"><span data-stu-id="24c5d-105">The accessibility domain of a top-level type is at least the program text of the project that it is declared in.</span></span> <span data-ttu-id="24c5d-106">亦即，定義域包括此專案的所有原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="24c5d-106">That is, the domain includes all of the source files of this project.</span></span> <span data-ttu-id="24c5d-107">巢狀型別的存取範圍定義域是至少在其中宣告之類型的程式文字。</span><span class="sxs-lookup"><span data-stu-id="24c5d-107">The accessibility domain of a nested type is at least the program text of the type in which it is declared.</span></span> <span data-ttu-id="24c5d-108">亦即，定義域是包括所有巢狀型別的類型主體。</span><span class="sxs-lookup"><span data-stu-id="24c5d-108">That is, the domain is the type body, which includes all nested types.</span></span> <span data-ttu-id="24c5d-109">巢狀型別的存取範圍定義域絕不會超過包含類型的存取範圍定義域。</span><span class="sxs-lookup"><span data-stu-id="24c5d-109">The accessibility domain of a nested type never exceeds that of the containing type.</span></span> <span data-ttu-id="24c5d-110">下列範例示範這些概念。</span><span class="sxs-lookup"><span data-stu-id="24c5d-110">These concepts are demonstrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24c5d-111">範例</span><span class="sxs-lookup"><span data-stu-id="24c5d-111">Example</span></span>  
 <span data-ttu-id="24c5d-112">這個範例包含最上層類型 `T1` 以及兩個巢狀類別 `M1` 和 `M2`。</span><span class="sxs-lookup"><span data-stu-id="24c5d-112">This example contains a top-level type, `T1`, and two nested classes, `M1` and `M2`.</span></span> <span data-ttu-id="24c5d-113">這些類別包含具有不同已宣告存取範圍的欄位。</span><span class="sxs-lookup"><span data-stu-id="24c5d-113">The classes contain fields that have different declared accessibilities.</span></span> <span data-ttu-id="24c5d-114">在 `Main` 方法中，註解在每個陳述式的後面，表示每個成員的存取領域。</span><span class="sxs-lookup"><span data-stu-id="24c5d-114">In the `Main` method, a comment follows each statement to indicate the accessibility domain of each member.</span></span> <span data-ttu-id="24c5d-115">請注意，會註解化嘗試參考無法存取成員的陳述式。</span><span class="sxs-lookup"><span data-stu-id="24c5d-115">Notice that the statements that try to reference the inaccessible members are commented out.</span></span> <span data-ttu-id="24c5d-116">如果您想要查看因參考無法存取的成員而造成的編譯器錯誤，請一次移除一個註解。</span><span class="sxs-lookup"><span data-stu-id="24c5d-116">If you want to see the compiler errors caused by referencing an inaccessible member, remove the comments one at a time.</span></span>  
  
 <span data-ttu-id="24c5d-117">[!code-cs[csrefKeywordsModifiers#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/accessibility-domain_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="24c5d-117">[!code-cs[csrefKeywordsModifiers#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/accessibility-domain_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="24c5d-118">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="24c5d-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="24c5d-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24c5d-119">See Also</span></span>  
 <span data-ttu-id="24c5d-120">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="24c5d-120">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="24c5d-121">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="24c5d-121">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="24c5d-122">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="24c5d-122">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="24c5d-123">[存取修飾詞](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="24c5d-123">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="24c5d-124">[存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="24c5d-124">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) </span></span>  
 <span data-ttu-id="24c5d-125">[使用存取範圍層級的限制](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="24c5d-125">[Restrictions on Using Accessibility Levels](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md) </span></span>  
 <span data-ttu-id="24c5d-126">[存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="24c5d-126">[Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span></span>  
 <span data-ttu-id="24c5d-127">[public](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="24c5d-127">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="24c5d-128">[private](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="24c5d-128">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 <span data-ttu-id="24c5d-129">[protected](../../../csharp/language-reference/keywords/protected.md) </span><span class="sxs-lookup"><span data-stu-id="24c5d-129">[protected](../../../csharp/language-reference/keywords/protected.md) </span></span>  
 [<span data-ttu-id="24c5d-130">internal</span><span class="sxs-lookup"><span data-stu-id="24c5d-130">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)

