---
title: "while (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- while_CSharpKeyword
- while
dev_langs:
- CSharp
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
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
ms.openlocfilehash: ed531c83dba02b38576bf8354b1ff92f075048bc
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="while-c-reference"></a><span data-ttu-id="ab4a9-102">while (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="ab4a9-102">while (C# Reference)</span></span>
<span data-ttu-id="ab4a9-103">`while` 陳述式會執行陳述式或陳述式區塊，直到指定的運算式評估為 `false` 為止。</span><span class="sxs-lookup"><span data-stu-id="ab4a9-103">The `while` statement executes a statement or a block of statements until a specified expression evaluates to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab4a9-104">範例</span><span class="sxs-lookup"><span data-stu-id="ab4a9-104">Example</span></span>  
 <span data-ttu-id="ab4a9-105">[!code-cs[csrefKeywordsIteration#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="ab4a9-105">[!code-cs[csrefKeywordsIteration#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab4a9-106">範例</span><span class="sxs-lookup"><span data-stu-id="ab4a9-106">Example</span></span>  
 <span data-ttu-id="ab4a9-107">[!code-cs[csrefKeywordsIteration#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="ab4a9-107">[!code-cs[csrefKeywordsIteration#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab4a9-108">範例</span><span class="sxs-lookup"><span data-stu-id="ab4a9-108">Example</span></span>  
 <span data-ttu-id="ab4a9-109">`while` 運算式的測試是在每次執行迴圈之前發生，因此 `while` 迴圈會執行零次或多次。</span><span class="sxs-lookup"><span data-stu-id="ab4a9-109">Because the test of the `while` expression takes place before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="ab4a9-110">這與 [do](../../../csharp/language-reference/keywords/do.md) 迴圈不同，此迴圈會執行一次或多次。</span><span class="sxs-lookup"><span data-stu-id="ab4a9-110">This differs from the [do](../../../csharp/language-reference/keywords/do.md) loop, which executes one or more times.</span></span>  
  
 <span data-ttu-id="ab4a9-111">[break](../../../csharp/language-reference/keywords/break.md)、[goto](../../../csharp/language-reference/keywords/goto.md)、[return](../../../csharp/language-reference/keywords/return.md) 或 [throw](../../../csharp/language-reference/keywords/throw.md) 陳述式將控制權轉移到迴圈外部時，即可終止 `while` 迴圈。</span><span class="sxs-lookup"><span data-stu-id="ab4a9-111">A `while` loop can be terminated when a [break](../../../csharp/language-reference/keywords/break.md), [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), or [throw](../../../csharp/language-reference/keywords/throw.md) statement transfers control outside the loop.</span></span> <span data-ttu-id="ab4a9-112">若要將控制權傳遞給下一個反覆運算，而不結束迴圈，請使用 [continue](../../../csharp/language-reference/keywords/continue.md) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ab4a9-112">To pass control to the next iteration without exiting the loop, use the [continue](../../../csharp/language-reference/keywords/continue.md) statement.</span></span> <span data-ttu-id="ab4a9-113">請注意三個先前範例中的輸出差異，根據遞增 `int n` 的位置而定。</span><span class="sxs-lookup"><span data-stu-id="ab4a9-113">Notice the difference in output in the three previous examples, depending on where `int n` is incremented.</span></span> <span data-ttu-id="ab4a9-114">在下面的範例中，不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="ab4a9-114">In the example below no output is generated.</span></span>  
  
 <span data-ttu-id="ab4a9-115">[!code-cs[csrefKeywordsIteration#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="ab4a9-115">[!code-cs[csrefKeywordsIteration#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_3.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="ab4a9-116">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="ab4a9-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ab4a9-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab4a9-117">See Also</span></span>  
 <span data-ttu-id="ab4a9-118">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="ab4a9-118">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="ab4a9-119">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="ab4a9-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="ab4a9-120">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="ab4a9-120">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="ab4a9-121">[while 陳述式 (C++)](/cpp/cpp/while-statement-cpp) </span><span class="sxs-lookup"><span data-stu-id="ab4a9-121">[while Statement (C++)](/cpp/cpp/while-statement-cpp) </span></span>  
 [<span data-ttu-id="ab4a9-122">反覆運算陳述式</span><span class="sxs-lookup"><span data-stu-id="ab4a9-122">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)

