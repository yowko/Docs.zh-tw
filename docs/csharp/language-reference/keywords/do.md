---
title: do - C# 參考
ms.custom: seodec18
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 08f964b1e5c78a429dc50f81398d840f58ec4b13
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422843"
---
# <a name="do-c-reference"></a><span data-ttu-id="1ee69-102">do (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="1ee69-102">do (C# Reference)</span></span>

<span data-ttu-id="1ee69-103">當指定的布林運算式評估為 `true` 時，`do` 陳述式會執行某個陳述式或陳述式區塊。</span><span class="sxs-lookup"><span data-stu-id="1ee69-103">The `do` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="1ee69-104">運算式是在每次執行迴圈之後評估，因此 `do-while` 迴圈會執行一次以上。</span><span class="sxs-lookup"><span data-stu-id="1ee69-104">Because that expression is evaluated after each execution of the loop, a `do-while` loop executes one or more times.</span></span> <span data-ttu-id="1ee69-105">這與 [while](while.md) 迴圈不同，此迴圈會執行零次以上。</span><span class="sxs-lookup"><span data-stu-id="1ee69-105">This differs from the [while](while.md) loop, which executes zero or more times.</span></span>

<span data-ttu-id="1ee69-106">您可以使用 [break](break.md) 陳述式在 `do` 陳述式區塊的任一點中斷迴圈。</span><span class="sxs-lookup"><span data-stu-id="1ee69-106">At any point within the `do` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="1ee69-107">您可以使用 [continue](continue.md) 陳述式直接逐步執行 `while` 運算式評估。</span><span class="sxs-lookup"><span data-stu-id="1ee69-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="1ee69-108">如果運算式評估為 `true`，即繼續執行迴圈中的第一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="1ee69-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="1ee69-109">否則會在迴圈之後的第一個陳述式繼續執行。</span><span class="sxs-lookup"><span data-stu-id="1ee69-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="1ee69-110">您也可以使用 [goto](goto.md)、[return](return.md) 或 [throw](throw.md) 陳述式結束 `do-while` 迴圈。</span><span class="sxs-lookup"><span data-stu-id="1ee69-110">You also can exit a `do-while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="1ee69-111">範例</span><span class="sxs-lookup"><span data-stu-id="1ee69-111">Example</span></span>

<span data-ttu-id="1ee69-112">下列範例會示範 `do` 陳述式的用法。</span><span class="sxs-lookup"><span data-stu-id="1ee69-112">The following example shows the usage of the `do` statement.</span></span> <span data-ttu-id="1ee69-113">選取 [執行] 執行範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="1ee69-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="1ee69-114">之後，您可以修改程式碼，然後再次執行它。</span><span class="sxs-lookup"><span data-stu-id="1ee69-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="1ee69-115">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="1ee69-115">C# language specification</span></span>

<span data-ttu-id="1ee69-116">如需詳細資訊，請參閱 [C# 語言規格](/dotnet/csharp/language-reference/language-specification/introduction)的 [do 陳述式](~/_csharplang/spec/statements.md#the-do-statement)一節。</span><span class="sxs-lookup"><span data-stu-id="1ee69-116">For more information, see [The do statement](~/_csharplang/spec/statements.md#the-do-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="1ee69-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="1ee69-117">See also</span></span>

- [<span data-ttu-id="1ee69-118">C# 參考</span><span class="sxs-lookup"><span data-stu-id="1ee69-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1ee69-119">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="1ee69-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1ee69-120">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="1ee69-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1ee69-121">while 陳述式</span><span class="sxs-lookup"><span data-stu-id="1ee69-121">while statement</span></span>](while.md)
