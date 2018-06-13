---
title: goto (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: 2dd70a30b885dcdae9637b02e8c34ac39f4879fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216800"
---
# <a name="goto-c-reference"></a><span data-ttu-id="62dfa-102">goto (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="62dfa-102">goto (C# Reference)</span></span>
<span data-ttu-id="62dfa-103">`goto` 陳述式會將程式控制權直接轉移到標記陳述式。</span><span class="sxs-lookup"><span data-stu-id="62dfa-103">The `goto` statement transfers the program control directly to a labeled statement.</span></span>  
  
 <span data-ttu-id="62dfa-104">`goto` 的一個常見用法是將控制權轉移到特定的切換案例標籤，或 `switch` 陳述式中的預設標籤。</span><span class="sxs-lookup"><span data-stu-id="62dfa-104">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>  
  
 <span data-ttu-id="62dfa-105">`goto` 陳述式也適用於跳出深度巢狀的迴圈。</span><span class="sxs-lookup"><span data-stu-id="62dfa-105">The `goto` statement is also useful to get out of deeply nested loops.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62dfa-106">範例</span><span class="sxs-lookup"><span data-stu-id="62dfa-106">Example</span></span>  
 <span data-ttu-id="62dfa-107">下列範例示範如何在 [switch](../../../csharp/language-reference/keywords/switch.md) 陳述式中使用 `goto`。</span><span class="sxs-lookup"><span data-stu-id="62dfa-107">The following example demonstrates using `goto` in a [switch](../../../csharp/language-reference/keywords/switch.md) statement.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="62dfa-108">範例</span><span class="sxs-lookup"><span data-stu-id="62dfa-108">Example</span></span>  
 <span data-ttu-id="62dfa-109">下列範例示範如何使用 `goto` 跳出巢狀迴圈。</span><span class="sxs-lookup"><span data-stu-id="62dfa-109">The following example demonstrates using `goto` to break out from nested loops.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="62dfa-110">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="62dfa-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="62dfa-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="62dfa-111">See Also</span></span>  
 [<span data-ttu-id="62dfa-112">C# 參考</span><span class="sxs-lookup"><span data-stu-id="62dfa-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="62dfa-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="62dfa-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="62dfa-114">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="62dfa-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="62dfa-115">goto 陳述式</span><span class="sxs-lookup"><span data-stu-id="62dfa-115">goto Statement</span></span>](/cpp/cpp/goto-statement-cpp)  
 [<span data-ttu-id="62dfa-116">跳躍陳述式</span><span class="sxs-lookup"><span data-stu-id="62dfa-116">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)
