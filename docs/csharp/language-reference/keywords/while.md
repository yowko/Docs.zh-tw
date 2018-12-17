---
title: while - C# 參考
ms.custom: seodec18
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: d360db7b9b740bef997327dda9b628c1edab0f35
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242564"
---
# <a name="while-c-reference"></a><span data-ttu-id="13f6c-102">while (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="13f6c-102">while (C# Reference)</span></span>

<span data-ttu-id="13f6c-103">當指定的布林運算式評估為 `true` 時，`while` 陳述式會執行某個陳述式或陳述式區塊。</span><span class="sxs-lookup"><span data-stu-id="13f6c-103">The `while` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="13f6c-104">運算式是在每次執行迴圈之前評估，因此 `while` 迴圈會執行零次以上。</span><span class="sxs-lookup"><span data-stu-id="13f6c-104">Because that expression is evaluated before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="13f6c-105">這與 [do](do.md) 迴圈不同，此迴圈會執行一次或多次。</span><span class="sxs-lookup"><span data-stu-id="13f6c-105">This differs from the [do](do.md) loop, which executes one or more times.</span></span>

<span data-ttu-id="13f6c-106">您可以使用 [break](break.md) 陳述式在 `while` 陳述式區塊的任一點中斷迴圈。</span><span class="sxs-lookup"><span data-stu-id="13f6c-106">At any point within the `while` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="13f6c-107">您可以使用 [continue](continue.md) 陳述式直接逐步執行 `while` 運算式評估。</span><span class="sxs-lookup"><span data-stu-id="13f6c-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="13f6c-108">如果運算式評估為 `true`，即繼續執行迴圈中的第一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="13f6c-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="13f6c-109">否則會在迴圈之後的第一個陳述式繼續執行。</span><span class="sxs-lookup"><span data-stu-id="13f6c-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="13f6c-110">您也可以使用 [goto](goto.md)、[return](return.md) 或 [throw](throw.md) 陳述式結束 `while` 迴圈。</span><span class="sxs-lookup"><span data-stu-id="13f6c-110">You also can exit a `while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="13f6c-111">範例</span><span class="sxs-lookup"><span data-stu-id="13f6c-111">Example</span></span>

<span data-ttu-id="13f6c-112">下列範例會示範 `while` 陳述式的用法。</span><span class="sxs-lookup"><span data-stu-id="13f6c-112">The following example shows the usage of the `while` statement.</span></span> <span data-ttu-id="13f6c-113">選取 [執行] 執行範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="13f6c-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="13f6c-114">之後，您可以修改程式碼，然後再次執行它。</span><span class="sxs-lookup"><span data-stu-id="13f6c-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[while loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="13f6c-115">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="13f6c-115">C# language specification</span></span>

<span data-ttu-id="13f6c-116">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的 [while 陳述式](~/_csharplang/spec/statements.md#the-while-statement)一節。</span><span class="sxs-lookup"><span data-stu-id="13f6c-116">For more information, see [The while statement](~/_csharplang/spec/statements.md#the-while-statement) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="13f6c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13f6c-117">See also</span></span>

- [<span data-ttu-id="13f6c-118">C# 參考</span><span class="sxs-lookup"><span data-stu-id="13f6c-118">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="13f6c-119">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="13f6c-119">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="13f6c-120">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="13f6c-120">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="13f6c-121">反覆運算陳述式</span><span class="sxs-lookup"><span data-stu-id="13f6c-121">Iteration Statements</span></span>](iteration-statements.md)  
- [<span data-ttu-id="13f6c-122">do 陳述式</span><span class="sxs-lookup"><span data-stu-id="13f6c-122">do statement</span></span>](do.md)  
