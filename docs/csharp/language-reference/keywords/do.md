---
title: "do (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- do_CSharpKeyword
- do
dev_langs:
- CSharp
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
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
ms.openlocfilehash: 58a9361c440bc1b17c5ab929ff7b45ba71ce50a4
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="do-c-reference"></a><span data-ttu-id="1f0e9-102">do (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="1f0e9-102">do (C# Reference)</span></span>
<span data-ttu-id="1f0e9-103">`do` 陳述式會重複執行陳述式或陳述式區塊，直到指定的運算式評估為 `false` 為止。</span><span class="sxs-lookup"><span data-stu-id="1f0e9-103">The `do` statement executes a statement or a block of statements repeatedly until a specified expression evaluates to `false`.</span></span> <span data-ttu-id="1f0e9-104">迴圈的主體必須括在大括弧 `{}` 中，除非它的構成是單一陳述式。</span><span class="sxs-lookup"><span data-stu-id="1f0e9-104">The body of the loop must be enclosed in braces, `{}`, unless it consists of a single statement.</span></span> <span data-ttu-id="1f0e9-105">在此情況下，大括弧為選擇性。</span><span class="sxs-lookup"><span data-stu-id="1f0e9-105">In that case, the braces are optional.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f0e9-106">範例</span><span class="sxs-lookup"><span data-stu-id="1f0e9-106">Example</span></span>  
 <span data-ttu-id="1f0e9-107">在下例中，只要變數 `x` 小於 5，`do-while` 迴圈陳述式就會一直執行。</span><span class="sxs-lookup"><span data-stu-id="1f0e9-107">In the following example, the `do-while` loop statements execute as long as the variable `x` is less than 5.</span></span>  
  
 <span data-ttu-id="1f0e9-108">[!code-cs[csrefKeywordsIteration#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/do_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="1f0e9-108">[!code-cs[csrefKeywordsIteration#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/do_1.cs)]</span></span>  
  
 <span data-ttu-id="1f0e9-109">不同於 [while](../../../csharp/language-reference/keywords/while.md) 陳述式，條件運算式在評估之前只會執行一次 `do-while` 迴圈。</span><span class="sxs-lookup"><span data-stu-id="1f0e9-109">Unlike the [while](../../../csharp/language-reference/keywords/while.md) statement, a `do-while` loop is executed one time before the conditional expression is evaluated.</span></span>  
  
 <span data-ttu-id="1f0e9-110">您可以使用 [break](../../../csharp/language-reference/keywords/break.md) 陳述式在 `do-while` 區塊的任一點中斷迴圈。</span><span class="sxs-lookup"><span data-stu-id="1f0e9-110">At any point in the `do-while` block, you can break out of the loop using the [break](../../../csharp/language-reference/keywords/break.md) statement.</span></span> <span data-ttu-id="1f0e9-111">您可以使用 [continue](../../../csharp/language-reference/keywords/continue.md) 陳述式直接逐步執行 `while` 運算式評估陳述式。</span><span class="sxs-lookup"><span data-stu-id="1f0e9-111">You can step directly to the `while` expression evaluation statement by using the [continue](../../../csharp/language-reference/keywords/continue.md) statement.</span></span> <span data-ttu-id="1f0e9-112">如果 `while` 運算式評估為 true，就繼續執行迴圈中的第一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="1f0e9-112">If the `while` expression evaluates to true, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="1f0e9-113">如果運算式評估為 false，就繼續執行 `do-while` 迴圈後面的第一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="1f0e9-113">If the expression evaluates to false, execution continues at the first statement after the `do-while` loop.</span></span>  
  
 <span data-ttu-id="1f0e9-114">[goto](../../../csharp/language-reference/keywords/goto.md)、[return](../../../csharp/language-reference/keywords/return.md) 或 [throw](../../../csharp/language-reference/keywords/throw.md) 陳述式也可以結束 `do-while` 迴圈。</span><span class="sxs-lookup"><span data-stu-id="1f0e9-114">A `do-while` loop can also be exited by the [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), or [throw](../../../csharp/language-reference/keywords/throw.md) statements.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="1f0e9-115">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="1f0e9-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1f0e9-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f0e9-116">See Also</span></span>  
 <span data-ttu-id="1f0e9-117">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="1f0e9-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="1f0e9-118">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="1f0e9-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="1f0e9-119">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="1f0e9-119">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="1f0e9-120">[do-while 陳述式 (C++)](/cpp/cpp/do-while-statement-cpp) </span><span class="sxs-lookup"><span data-stu-id="1f0e9-120">[do-while Statement (C++)](/cpp/cpp/do-while-statement-cpp) </span></span>  
 [<span data-ttu-id="1f0e9-121">反覆運算陳述式</span><span class="sxs-lookup"><span data-stu-id="1f0e9-121">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)

