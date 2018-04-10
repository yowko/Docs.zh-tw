---
title: while (C# 參考)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 420b409689d877c3e1ac744e8d7a65500cf8f964
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="while-c-reference"></a><span data-ttu-id="8ca05-102">while (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="8ca05-102">while (C# Reference)</span></span>
<span data-ttu-id="8ca05-103">`while` 陳述式會執行陳述式或陳述式區塊，直到指定的運算式評估為 `false` 為止。</span><span class="sxs-lookup"><span data-stu-id="8ca05-103">The `while` statement executes a statement or a block of statements until a specified expression evaluates to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ca05-104">範例</span><span class="sxs-lookup"><span data-stu-id="8ca05-104">Example</span></span>  
 [!code-csharp[csrefKeywordsIteration#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="8ca05-105">範例</span><span class="sxs-lookup"><span data-stu-id="8ca05-105">Example</span></span>  
 [!code-csharp[csrefKeywordsIteration#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="8ca05-106">範例</span><span class="sxs-lookup"><span data-stu-id="8ca05-106">Example</span></span>  
 <span data-ttu-id="8ca05-107">`while` 運算式的測試是在每次執行迴圈之前發生，因此 `while` 迴圈會執行零次或多次。</span><span class="sxs-lookup"><span data-stu-id="8ca05-107">Because the test of the `while` expression takes place before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="8ca05-108">這與 [do](../../../csharp/language-reference/keywords/do.md) 迴圈不同，此迴圈會執行一次或多次。</span><span class="sxs-lookup"><span data-stu-id="8ca05-108">This differs from the [do](../../../csharp/language-reference/keywords/do.md) loop, which executes one or more times.</span></span>  
  
 <span data-ttu-id="8ca05-109">[break](../../../csharp/language-reference/keywords/break.md)、[goto](../../../csharp/language-reference/keywords/goto.md)、[return](../../../csharp/language-reference/keywords/return.md) 或 [throw](../../../csharp/language-reference/keywords/throw.md) 陳述式將控制權轉移到迴圈外部時，即可終止 `while` 迴圈。</span><span class="sxs-lookup"><span data-stu-id="8ca05-109">A `while` loop can be terminated when a [break](../../../csharp/language-reference/keywords/break.md), [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), or [throw](../../../csharp/language-reference/keywords/throw.md) statement transfers control outside the loop.</span></span> <span data-ttu-id="8ca05-110">若要將控制權傳遞給下一個反覆運算，而不結束迴圈，請使用 [continue](../../../csharp/language-reference/keywords/continue.md) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="8ca05-110">To pass control to the next iteration without exiting the loop, use the [continue](../../../csharp/language-reference/keywords/continue.md) statement.</span></span> <span data-ttu-id="8ca05-111">請注意三個先前範例中的輸出差異，根據遞增 `int n` 的位置而定。</span><span class="sxs-lookup"><span data-stu-id="8ca05-111">Notice the difference in output in the three previous examples, depending on where `int n` is incremented.</span></span> <span data-ttu-id="8ca05-112">在下面的範例中，不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="8ca05-112">In the example below no output is generated.</span></span>  
  
 [!code-csharp[csrefKeywordsIteration#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="8ca05-113">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="8ca05-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8ca05-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ca05-114">See Also</span></span>  
 [<span data-ttu-id="8ca05-115">C# 參考</span><span class="sxs-lookup"><span data-stu-id="8ca05-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8ca05-116">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="8ca05-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8ca05-117">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="8ca05-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="8ca05-118">while 陳述式 (C++)</span><span class="sxs-lookup"><span data-stu-id="8ca05-118">while Statement (C++)</span></span>](/cpp/cpp/while-statement-cpp)  
 [<span data-ttu-id="8ca05-119">反覆運算陳述式</span><span class="sxs-lookup"><span data-stu-id="8ca05-119">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
