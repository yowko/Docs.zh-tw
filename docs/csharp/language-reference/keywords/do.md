---
title: "do (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords: do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d24078d3fb985f643fb66aa456900d03d2ff3fce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="do-c-reference"></a><span data-ttu-id="4441c-102">do (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="4441c-102">do (C# Reference)</span></span>
<span data-ttu-id="4441c-103">`do` 陳述式會重複執行陳述式或陳述式區塊，直到指定的運算式評估為 `false` 為止。</span><span class="sxs-lookup"><span data-stu-id="4441c-103">The `do` statement executes a statement or a block of statements repeatedly until a specified expression evaluates to `false`.</span></span> <span data-ttu-id="4441c-104">迴圈的主體必須括在大括弧 `{}` 中，除非它的構成是單一陳述式。</span><span class="sxs-lookup"><span data-stu-id="4441c-104">The body of the loop must be enclosed in braces, `{}`, unless it consists of a single statement.</span></span> <span data-ttu-id="4441c-105">在此情況下，大括弧為選擇性。</span><span class="sxs-lookup"><span data-stu-id="4441c-105">In that case, the braces are optional.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4441c-106">範例</span><span class="sxs-lookup"><span data-stu-id="4441c-106">Example</span></span>  
 <span data-ttu-id="4441c-107">在下例中，只要變數 `x` 小於 5，`do-while` 迴圈陳述式就會一直執行。</span><span class="sxs-lookup"><span data-stu-id="4441c-107">In the following example, the `do-while` loop statements execute as long as the variable `x` is less than 5.</span></span>  
  
 [!code-csharp[csrefKeywordsIteration#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/do_1.cs)]  
  
 <span data-ttu-id="4441c-108">不同於 [while](../../../csharp/language-reference/keywords/while.md) 陳述式，條件運算式在評估之前只會執行一次 `do-while` 迴圈。</span><span class="sxs-lookup"><span data-stu-id="4441c-108">Unlike the [while](../../../csharp/language-reference/keywords/while.md) statement, a `do-while` loop is executed one time before the conditional expression is evaluated.</span></span>  
  
 <span data-ttu-id="4441c-109">您可以使用 [break](../../../csharp/language-reference/keywords/break.md) 陳述式在 `do-while` 區塊的任一點中斷迴圈。</span><span class="sxs-lookup"><span data-stu-id="4441c-109">At any point in the `do-while` block, you can break out of the loop using the [break](../../../csharp/language-reference/keywords/break.md) statement.</span></span> <span data-ttu-id="4441c-110">您可以使用 [continue](../../../csharp/language-reference/keywords/continue.md) 陳述式直接逐步執行 `while` 運算式評估陳述式。</span><span class="sxs-lookup"><span data-stu-id="4441c-110">You can step directly to the `while` expression evaluation statement by using the [continue](../../../csharp/language-reference/keywords/continue.md) statement.</span></span> <span data-ttu-id="4441c-111">如果 `while` 運算式評估為 true，就繼續執行迴圈中的第一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="4441c-111">If the `while` expression evaluates to true, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="4441c-112">如果運算式評估為 false，就繼續執行 `do-while` 迴圈後面的第一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="4441c-112">If the expression evaluates to false, execution continues at the first statement after the `do-while` loop.</span></span>  
  
 <span data-ttu-id="4441c-113">[goto](../../../csharp/language-reference/keywords/goto.md)、[return](../../../csharp/language-reference/keywords/return.md) 或 [throw](../../../csharp/language-reference/keywords/throw.md) 陳述式也可以結束 `do-while` 迴圈。</span><span class="sxs-lookup"><span data-stu-id="4441c-113">A `do-while` loop can also be exited by the [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), or [throw](../../../csharp/language-reference/keywords/throw.md) statements.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="4441c-114">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="4441c-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4441c-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4441c-115">See Also</span></span>  
 [<span data-ttu-id="4441c-116">C# 參考</span><span class="sxs-lookup"><span data-stu-id="4441c-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="4441c-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="4441c-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4441c-118">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="4441c-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="4441c-119">do-while 陳述式 (C++)</span><span class="sxs-lookup"><span data-stu-id="4441c-119">do-while Statement (C++)</span></span>](/cpp/cpp/do-while-statement-cpp)  
 [<span data-ttu-id="4441c-120">反覆運算陳述式</span><span class="sxs-lookup"><span data-stu-id="4441c-120">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
