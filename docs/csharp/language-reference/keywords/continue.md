---
title: continue (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: b3a9a17bb16ded19330cbc880b2e5e7271f269c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215666"
---
# <a name="continue-c-reference"></a><span data-ttu-id="ee590-102">continue (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="ee590-102">continue (C# Reference)</span></span>
<span data-ttu-id="ee590-103">`continue` 陳述式會將控制權轉移給其所在的封閉式 [while](../../../csharp/language-reference/keywords/while.md)、[do](../../../csharp/language-reference/keywords/do.md)、[for](../../../csharp/language-reference/keywords/for.md) 或 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 陳述式的下一個反覆項目。</span><span class="sxs-lookup"><span data-stu-id="ee590-103">The `continue` statement passes control to the next iteration of the enclosing [while](../../../csharp/language-reference/keywords/while.md), [do](../../../csharp/language-reference/keywords/do.md), [for](../../../csharp/language-reference/keywords/for.md), or [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement in which it appears.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee590-104">範例</span><span class="sxs-lookup"><span data-stu-id="ee590-104">Example</span></span>  
 <span data-ttu-id="ee590-105">在此範例中，計數器會初始化為從 1 計算到 10。</span><span class="sxs-lookup"><span data-stu-id="ee590-105">In this example, a counter is initialized to count from 1 to 10.</span></span> <span data-ttu-id="ee590-106">搭配使用 `continue` 陳述式與 `(i < 9)` 運算式，會略過 `continue` 與 `for` 主體結尾之間的陳述式。</span><span class="sxs-lookup"><span data-stu-id="ee590-106">By using the `continue` statement in conjunction with the expression `(i < 9)`, the statements between `continue` and the end of the `for` body are skipped.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/continue_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="ee590-107">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="ee590-107">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ee590-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="ee590-108">See Also</span></span>  
 [<span data-ttu-id="ee590-109">C# 參考</span><span class="sxs-lookup"><span data-stu-id="ee590-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ee590-110">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="ee590-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ee590-111">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="ee590-111">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="ee590-112">break 陳述式</span><span class="sxs-lookup"><span data-stu-id="ee590-112">break Statement</span></span>](/cpp/cpp/break-statement-cpp)  
 [<span data-ttu-id="ee590-113">跳躍陳述式</span><span class="sxs-lookup"><span data-stu-id="ee590-113">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)
