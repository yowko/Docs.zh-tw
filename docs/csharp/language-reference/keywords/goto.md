---
title: "goto (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- goto_CSharpKeyword
- goto
dev_langs:
- CSharp
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
caps.latest.revision: 22
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
ms.openlocfilehash: cd298809ab883f425f3bb88239f2951ab98cc03e
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="goto-c-reference"></a><span data-ttu-id="340e8-102">goto (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="340e8-102">goto (C# Reference)</span></span>
<span data-ttu-id="340e8-103">`goto` 陳述式會將程式控制權直接轉移到標記陳述式。</span><span class="sxs-lookup"><span data-stu-id="340e8-103">The `goto` statement transfers the program control directly to a labeled statement.</span></span>  
  
 <span data-ttu-id="340e8-104">`goto` 的一個常見用法是將控制權轉移到特定的切換案例標籤，或 `switch` 陳述式中的預設標籤。</span><span class="sxs-lookup"><span data-stu-id="340e8-104">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>  
  
 <span data-ttu-id="340e8-105">`goto` 陳述式也適用於跳出深度巢狀的迴圈。</span><span class="sxs-lookup"><span data-stu-id="340e8-105">The `goto` statement is also useful to get out of deeply nested loops.</span></span>  
  
## <a name="example"></a><span data-ttu-id="340e8-106">範例</span><span class="sxs-lookup"><span data-stu-id="340e8-106">Example</span></span>  
 <span data-ttu-id="340e8-107">下列範例示範如何在 [switch](../../../csharp/language-reference/keywords/switch.md) 陳述式中使用 `goto`。</span><span class="sxs-lookup"><span data-stu-id="340e8-107">The following example demonstrates using `goto` in a [switch](../../../csharp/language-reference/keywords/switch.md) statement.</span></span>  
  
 <span data-ttu-id="340e8-108">[!code-cs[csrefKeywordsJump#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="340e8-108">[!code-cs[csrefKeywordsJump#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="340e8-109">範例</span><span class="sxs-lookup"><span data-stu-id="340e8-109">Example</span></span>  
 <span data-ttu-id="340e8-110">下列範例示範如何使用 `goto` 跳出巢狀迴圈。</span><span class="sxs-lookup"><span data-stu-id="340e8-110">The following example demonstrates using `goto` to break out from nested loops.</span></span>  
  
 <span data-ttu-id="340e8-111">[!code-cs[csrefKeywordsJump#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="340e8-111">[!code-cs[csrefKeywordsJump#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="340e8-112">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="340e8-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="340e8-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="340e8-113">See Also</span></span>  
 <span data-ttu-id="340e8-114">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="340e8-114">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="340e8-115">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="340e8-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="340e8-116">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="340e8-116">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="340e8-117">[goto Statement](/cpp/cpp/goto-statement-cpp) (goto 陳述式) </span><span class="sxs-lookup"><span data-stu-id="340e8-117">[goto Statement](/cpp/cpp/goto-statement-cpp) </span></span>  
 [<span data-ttu-id="340e8-118">跳躍陳述式</span><span class="sxs-lookup"><span data-stu-id="340e8-118">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)

