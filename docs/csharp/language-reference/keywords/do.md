---
title: do (C# 參考)
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: b918b378623a239803fb4e0a65fcf82fd677b21f
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37961322"
---
# <a name="do-c-reference"></a><span data-ttu-id="e45ca-102">do (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="e45ca-102">do (C# Reference)</span></span>

<span data-ttu-id="e45ca-103">指定的運算式評估為 `true` 時，`do` 陳述式會執行陳述式或陳述式區塊。</span><span class="sxs-lookup"><span data-stu-id="e45ca-103">The `do` statement executes a statement or a block of statements while a specified boolean expression evaluates to `true`.</span></span> <span data-ttu-id="e45ca-104">運算式是在每次執行迴圈之後評估，因此 `do-while` 迴圈會執行一次以上。</span><span class="sxs-lookup"><span data-stu-id="e45ca-104">Because that expression is evaluated after each execution of the loop, a `do-while` loop executes one or more times.</span></span> <span data-ttu-id="e45ca-105">這與 [while](while.md) 迴圈不同，此迴圈會執行零次以上。</span><span class="sxs-lookup"><span data-stu-id="e45ca-105">This differs from the [while](while.md) loop, which executes zero or more times.</span></span>

<span data-ttu-id="e45ca-106">您可以使用 [break](break.md) 陳述式在 `do` 陳述式區塊的任一點中斷迴圈。</span><span class="sxs-lookup"><span data-stu-id="e45ca-106">At any point within the `do` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="e45ca-107">您可以使用 [continue](continue.md) 陳述式直接逐步執行 `while` 運算式評估。</span><span class="sxs-lookup"><span data-stu-id="e45ca-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="e45ca-108">如果運算式評估為 `true`，即繼續執行迴圈中的第一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="e45ca-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="e45ca-109">否則會在迴圈之後的第一個陳述式繼續執行。</span><span class="sxs-lookup"><span data-stu-id="e45ca-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="e45ca-110">您也可以使用 [goto](goto.md)、[return](return.md) 或 [throw](throw.md) 陳述式結束 `do-while` 迴圈。</span><span class="sxs-lookup"><span data-stu-id="e45ca-110">You also can exit a `do-while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="e45ca-111">範例</span><span class="sxs-lookup"><span data-stu-id="e45ca-111">Example</span></span>

<span data-ttu-id="e45ca-112">下列範例會示範 `do` 陳述式的用法。</span><span class="sxs-lookup"><span data-stu-id="e45ca-112">The following example shows the usage of the `do` statement.</span></span> <span data-ttu-id="e45ca-113">選取 [執行] 執行範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="e45ca-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="e45ca-114">之後，您可以修改程式碼，然後再次執行它。</span><span class="sxs-lookup"><span data-stu-id="e45ca-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="e45ca-115">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="e45ca-115">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="e45ca-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e45ca-116">See also</span></span>

 [<span data-ttu-id="e45ca-117">C# 參考</span><span class="sxs-lookup"><span data-stu-id="e45ca-117">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="e45ca-118">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="e45ca-118">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="e45ca-119">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="e45ca-119">C# Keywords</span></span>](index.md)  
 [<span data-ttu-id="e45ca-120">do-while 陳述式 (C++)</span><span class="sxs-lookup"><span data-stu-id="e45ca-120">do-while Statement (C++)</span></span>](/cpp/cpp/do-while-statement-cpp)  
 [<span data-ttu-id="e45ca-121">反覆運算陳述式</span><span class="sxs-lookup"><span data-stu-id="e45ca-121">Iteration Statements</span></span>](iteration-statements.md)  
 [<span data-ttu-id="e45ca-122">while 陳述式</span><span class="sxs-lookup"><span data-stu-id="e45ca-122">while statement</span></span>](while.md)  
