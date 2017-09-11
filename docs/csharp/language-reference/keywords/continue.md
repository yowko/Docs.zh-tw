---
title: "continue (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- continue_CSharpKeyword
- continue
dev_langs:
- CSharp
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4a0dcedb32b153c31ec5ed799f66062463307db9
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="continue-c-reference"></a><span data-ttu-id="d4147-102">continue (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="d4147-102">continue (C# Reference)</span></span>
<span data-ttu-id="d4147-103">`continue` 陳述式會將控制權轉移給其所在的封閉式 [while](../../../csharp/language-reference/keywords/while.md)、[do](../../../csharp/language-reference/keywords/do.md)、[for](../../../csharp/language-reference/keywords/for.md) 或 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 陳述式的下一個反覆項目。</span><span class="sxs-lookup"><span data-stu-id="d4147-103">The `continue` statement passes control to the next iteration of the enclosing [while](../../../csharp/language-reference/keywords/while.md), [do](../../../csharp/language-reference/keywords/do.md), [for](../../../csharp/language-reference/keywords/for.md), or [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement in which it appears.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4147-104">範例</span><span class="sxs-lookup"><span data-stu-id="d4147-104">Example</span></span>  
 <span data-ttu-id="d4147-105">在此範例中，計數器會初始化為從 1 計算到 10。</span><span class="sxs-lookup"><span data-stu-id="d4147-105">In this example, a counter is initialized to count from 1 to 10.</span></span> <span data-ttu-id="d4147-106">搭配使用 `continue` 陳述式與 `(i < 9)` 運算式，會略過 `continue` 與 `for` 主體結尾之間的陳述式。</span><span class="sxs-lookup"><span data-stu-id="d4147-106">By using the `continue` statement in conjunction with the expression `(i < 9)`, the statements between `continue` and the end of the `for` body are skipped.</span></span>  
  
 <span data-ttu-id="d4147-107">[!code-cs[csrefKeywordsJump#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/continue_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="d4147-107">[!code-cs[csrefKeywordsJump#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/continue_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="d4147-108">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="d4147-108">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d4147-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4147-109">See Also</span></span>  
 <span data-ttu-id="d4147-110">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="d4147-110">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="d4147-111">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="d4147-111">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="d4147-112">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="d4147-112">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="d4147-113">[break 陳述式](/cpp/cpp/break-statement-cpp) </span><span class="sxs-lookup"><span data-stu-id="d4147-113">[break Statement](/cpp/cpp/break-statement-cpp) </span></span>  
 [<span data-ttu-id="d4147-114">跳躍陳述式</span><span class="sxs-lookup"><span data-stu-id="d4147-114">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)

