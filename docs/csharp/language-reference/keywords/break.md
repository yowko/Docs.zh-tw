---
title: break (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: 0cfe722bfefc1befd8a453f4454b05b3e4a0da76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215046"
---
# <a name="break-c-reference"></a><span data-ttu-id="2bd2c-102">break (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="2bd2c-102">break (C# Reference)</span></span>
<span data-ttu-id="2bd2c-103">`break` 陳述式會終止其所在的最接近封閉式迴圈或 [switch](../../../csharp/language-reference/keywords/switch.md) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="2bd2c-103">The `break` statement terminates the closest enclosing loop or [switch](../../../csharp/language-reference/keywords/switch.md) statement in which it appears.</span></span> <span data-ttu-id="2bd2c-104">控制權會轉移到已終止陳述式之後的陳述式 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="2bd2c-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bd2c-105">範例</span><span class="sxs-lookup"><span data-stu-id="2bd2c-105">Example</span></span>  
 <span data-ttu-id="2bd2c-106">在此範例中，條件式陳述式包含假設從 1 計算到 100 的計數器；不過，`break` 陳述式會在計算 4 次之後終止迴圈。</span><span class="sxs-lookup"><span data-stu-id="2bd2c-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="2bd2c-107">範例</span><span class="sxs-lookup"><span data-stu-id="2bd2c-107">Example</span></span>  
 <span data-ttu-id="2bd2c-108">在此範例中，`break` 陳述式是用來破壞內部巢狀迴圈，並將控制權返回外部迴圈。</span><span class="sxs-lookup"><span data-stu-id="2bd2c-108">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="2bd2c-109">範例</span><span class="sxs-lookup"><span data-stu-id="2bd2c-109">Example</span></span>  
 <span data-ttu-id="2bd2c-110">這個範例示範如何在 [switch](../../../csharp/language-reference/keywords/switch.md) 陳述式中使用 `break`。</span><span class="sxs-lookup"><span data-stu-id="2bd2c-110">This example demonstrates the use of `break` in a [switch](../../../csharp/language-reference/keywords/switch.md) statement.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_3.cs)]  
  
 <span data-ttu-id="2bd2c-111">如果您已輸入 `4`，則輸出會是︰</span><span class="sxs-lookup"><span data-stu-id="2bd2c-111">If you entered `4`, the output would be:</span></span>  
  
```  
Enter your selection (1, 2, or 3): 4  
Sorry, invalid selection.  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="2bd2c-112">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="2bd2c-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2bd2c-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="2bd2c-113">See Also</span></span>  
 [<span data-ttu-id="2bd2c-114">C# 參考</span><span class="sxs-lookup"><span data-stu-id="2bd2c-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="2bd2c-115">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="2bd2c-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2bd2c-116">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="2bd2c-116">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="2bd2c-117">switch</span><span class="sxs-lookup"><span data-stu-id="2bd2c-117">switch</span></span>](../../../csharp/language-reference/keywords/switch.md)  
 [<span data-ttu-id="2bd2c-118">跳躍陳述式</span><span class="sxs-lookup"><span data-stu-id="2bd2c-118">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)  
 [<span data-ttu-id="2bd2c-119">反覆運算陳述式</span><span class="sxs-lookup"><span data-stu-id="2bd2c-119">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
