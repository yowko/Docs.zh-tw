---
title: while - C# 參考
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: 481d3f7b87dbe874de010825c3c7f052e4bc33c0
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738746"
---
# <a name="while-c-reference"></a><span data-ttu-id="63031-102">while (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="63031-102">while (C# Reference)</span></span>

<span data-ttu-id="63031-103">當指定的布林運算式評估為 `true` 時，`while` 陳述式會執行某個陳述式或陳述式區塊。</span><span class="sxs-lookup"><span data-stu-id="63031-103">The `while` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="63031-104">運算式是在每次執行迴圈之前評估，因此 `while` 迴圈會執行零次以上。</span><span class="sxs-lookup"><span data-stu-id="63031-104">Because that expression is evaluated before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="63031-105">這與 [do](do.md) 迴圈不同，此迴圈會執行一次或多次。</span><span class="sxs-lookup"><span data-stu-id="63031-105">This differs from the [do](do.md) loop, which executes one or more times.</span></span>

<span data-ttu-id="63031-106">您可以使用 [break](break.md) 陳述式在 `while` 陳述式區塊的任一點中斷迴圈。</span><span class="sxs-lookup"><span data-stu-id="63031-106">At any point within the `while` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="63031-107">您可以使用 [continue](continue.md) 陳述式直接逐步執行 `while` 運算式評估。</span><span class="sxs-lookup"><span data-stu-id="63031-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="63031-108">如果運算式評估為 `true`，即繼續執行迴圈中的第一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="63031-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="63031-109">否則會在迴圈之後的第一個陳述式繼續執行。</span><span class="sxs-lookup"><span data-stu-id="63031-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="63031-110">您還可以通過`while`[goto、](goto.md)[傳回](return.md)或[引發](throw.md)語句退出迴圈。</span><span class="sxs-lookup"><span data-stu-id="63031-110">You can also exit a `while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="63031-111">範例</span><span class="sxs-lookup"><span data-stu-id="63031-111">Example</span></span>

<span data-ttu-id="63031-112">下列範例會示範 `while` 陳述式的用法。</span><span class="sxs-lookup"><span data-stu-id="63031-112">The following example shows the usage of the `while` statement.</span></span> <span data-ttu-id="63031-113">選取 [執行]\*\*\*\* 執行範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="63031-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="63031-114">之後，您可以修改程式碼，然後再次執行它。</span><span class="sxs-lookup"><span data-stu-id="63031-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[while loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="63031-115">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="63031-115">C# language specification</span></span>

<span data-ttu-id="63031-116">如需詳細資訊，請參閱 [C# 語言規格](/dotnet/csharp/language-reference/language-specification/introduction)的 [while 陳述式](~/_csharplang/spec/statements.md#the-while-statement)一節。</span><span class="sxs-lookup"><span data-stu-id="63031-116">For more information, see [The while statement](~/_csharplang/spec/statements.md#the-while-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="63031-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63031-117">See also</span></span>

- [<span data-ttu-id="63031-118">C# 參考</span><span class="sxs-lookup"><span data-stu-id="63031-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="63031-119">C# 編程指南</span><span class="sxs-lookup"><span data-stu-id="63031-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="63031-120">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="63031-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="63031-121">做語句</span><span class="sxs-lookup"><span data-stu-id="63031-121">do statement</span></span>](do.md)
