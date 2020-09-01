---
description: do - C# 參考
title: do - C# 參考
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 601231f23a58e8af8339a733677f0bbd92bb4ffc
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89126953"
---
# <a name="do-c-reference"></a><span data-ttu-id="f4cd4-103">do (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="f4cd4-103">do (C# Reference)</span></span>

<span data-ttu-id="f4cd4-104">當指定的布林運算式評估為 `true` 時，`do` 陳述式會執行某個陳述式或陳述式區塊。</span><span class="sxs-lookup"><span data-stu-id="f4cd4-104">The `do` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="f4cd4-105">運算式是在每次執行迴圈之後評估，因此 `do-while` 迴圈會執行一次以上。</span><span class="sxs-lookup"><span data-stu-id="f4cd4-105">Because that expression is evaluated after each execution of the loop, a `do-while` loop executes one or more times.</span></span> <span data-ttu-id="f4cd4-106">這與 [while](while.md) 迴圈不同，此迴圈會執行零次以上。</span><span class="sxs-lookup"><span data-stu-id="f4cd4-106">This differs from the [while](while.md) loop, which executes zero or more times.</span></span>

<span data-ttu-id="f4cd4-107">您可以使用 [break](break.md) 陳述式在 `do` 陳述式區塊的任一點中斷迴圈。</span><span class="sxs-lookup"><span data-stu-id="f4cd4-107">At any point within the `do` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="f4cd4-108">您可以使用 [continue](continue.md) 陳述式直接逐步執行 `while` 運算式評估。</span><span class="sxs-lookup"><span data-stu-id="f4cd4-108">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="f4cd4-109">如果運算式評估為 `true`，即繼續執行迴圈中的第一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="f4cd4-109">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="f4cd4-110">否則會在迴圈之後的第一個陳述式繼續執行。</span><span class="sxs-lookup"><span data-stu-id="f4cd4-110">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="f4cd4-111">您也可以使用 `do-while` [goto](goto.md)、 [return](return.md)或 [throw](throw.md) 語句來結束迴圈。</span><span class="sxs-lookup"><span data-stu-id="f4cd4-111">You can also exit a `do-while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="f4cd4-112">範例</span><span class="sxs-lookup"><span data-stu-id="f4cd4-112">Example</span></span>

<span data-ttu-id="f4cd4-113">下列範例會示範 `do` 陳述式的用法。</span><span class="sxs-lookup"><span data-stu-id="f4cd4-113">The following example shows the usage of the `do` statement.</span></span> <span data-ttu-id="f4cd4-114">選取 [執行]\*\*\*\* 執行範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="f4cd4-114">Select **Run** to run the example code.</span></span> <span data-ttu-id="f4cd4-115">之後，您可以修改程式碼，然後再次執行它。</span><span class="sxs-lookup"><span data-stu-id="f4cd4-115">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[do loop example](snippets/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="f4cd4-116">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="f4cd4-116">C# language specification</span></span>

<span data-ttu-id="f4cd4-117">如需詳細資訊，請參閱 [C# 語言規格](/dotnet/csharp/language-reference/language-specification/introduction)的 [do 陳述式](~/_csharplang/spec/statements.md#the-do-statement)一節。</span><span class="sxs-lookup"><span data-stu-id="f4cd4-117">For more information, see [The do statement](~/_csharplang/spec/statements.md#the-do-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="f4cd4-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4cd4-118">See also</span></span>

- [<span data-ttu-id="f4cd4-119">C # 參考</span><span class="sxs-lookup"><span data-stu-id="f4cd4-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f4cd4-120">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f4cd4-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f4cd4-121">C # 關鍵字</span><span class="sxs-lookup"><span data-stu-id="f4cd4-121">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f4cd4-122">while 陳述式</span><span class="sxs-lookup"><span data-stu-id="f4cd4-122">while statement</span></span>](while.md)
