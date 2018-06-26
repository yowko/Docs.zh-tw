---
title: while (C# 參考)
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: c082107472ac53d05b3b43dd4d9d8afc508a16cb
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34565861"
---
# <a name="while-c-reference"></a><span data-ttu-id="d9f3b-102">while (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="d9f3b-102">while (C# Reference)</span></span>

<span data-ttu-id="d9f3b-103">指定的運算式評估為 `true` 時，`while` 陳述式會執行陳述式或陳述式區塊。</span><span class="sxs-lookup"><span data-stu-id="d9f3b-103">The `while` statement executes a statement or a block of statements while a specified boolean expression evaluates to `true`.</span></span> <span data-ttu-id="d9f3b-104">運算式是在每次執行迴圈之前評估，因此 `while` 迴圈會執行零次以上。</span><span class="sxs-lookup"><span data-stu-id="d9f3b-104">Because that expression is evaluated before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="d9f3b-105">這與 [do](do.md) 迴圈不同，此迴圈會執行一次或多次。</span><span class="sxs-lookup"><span data-stu-id="d9f3b-105">This differs from the [do](do.md) loop, which executes one or more times.</span></span>

<span data-ttu-id="d9f3b-106">您可以使用 [break](break.md) 陳述式在 `while` 陳述式區塊的任一點中斷迴圈。</span><span class="sxs-lookup"><span data-stu-id="d9f3b-106">At any point within the `while` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="d9f3b-107">您可以使用 [continue](continue.md) 陳述式直接逐步執行 `while` 運算式評估。</span><span class="sxs-lookup"><span data-stu-id="d9f3b-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="d9f3b-108">如果運算式評估為 `true`，即繼續執行迴圈中的第一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="d9f3b-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="d9f3b-109">否則會在迴圈之後的第一個陳述式繼續執行。</span><span class="sxs-lookup"><span data-stu-id="d9f3b-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="d9f3b-110">您也可以使用 [goto](goto.md)、[return](return.md) 或 [throw](throw.md) 陳述式結束 `while` 迴圈。</span><span class="sxs-lookup"><span data-stu-id="d9f3b-110">You also can exit a `while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="d9f3b-111">範例</span><span class="sxs-lookup"><span data-stu-id="d9f3b-111">Example</span></span>

<span data-ttu-id="d9f3b-112">下列範例會示範 `while` 陳述式的用法。</span><span class="sxs-lookup"><span data-stu-id="d9f3b-112">The following example shows the usage of the `while` statement.</span></span> <span data-ttu-id="d9f3b-113">選取 [執行] 執行範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="d9f3b-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="d9f3b-114">之後，您可以修改程式碼，然後再次執行它。</span><span class="sxs-lookup"><span data-stu-id="d9f3b-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[while loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="d9f3b-115">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="d9f3b-115">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="d9f3b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9f3b-116">See also</span></span>

 [<span data-ttu-id="d9f3b-117">C# 參考</span><span class="sxs-lookup"><span data-stu-id="d9f3b-117">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="d9f3b-118">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="d9f3b-118">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="d9f3b-119">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="d9f3b-119">C# Keywords</span></span>](index.md)  
 [<span data-ttu-id="d9f3b-120">while 陳述式 (C++)</span><span class="sxs-lookup"><span data-stu-id="d9f3b-120">while Statement (C++)</span></span>](/cpp/cpp/while-statement-cpp)  
 [<span data-ttu-id="d9f3b-121">反覆運算陳述式</span><span class="sxs-lookup"><span data-stu-id="d9f3b-121">Iteration Statements</span></span>](iteration-statements.md)  
 [<span data-ttu-id="d9f3b-122">do 陳述式</span><span class="sxs-lookup"><span data-stu-id="d9f3b-122">do statement</span></span>](do.md)  
