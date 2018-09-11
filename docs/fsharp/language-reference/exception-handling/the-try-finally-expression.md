---
title: 例外狀況：try...finally 運算式 (F#)
description: "了解如何在 F # 'try...最後' 運算式可讓您執行清除程式碼，即使程式碼區塊擲回例外狀況。"
ms.date: 05/16/2016
ms.openlocfilehash: 546a6b0619de6f51044600dc1ead73c6d5211299
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44275141"
---
# <a name="exceptions-the-tryfinally-expression"></a><span data-ttu-id="77c75-103">例外狀況：try...finally 運算式</span><span class="sxs-lookup"><span data-stu-id="77c75-103">Exceptions: The try...finally Expression</span></span>

<span data-ttu-id="77c75-104">`try...finally`運算式可讓您執行清除程式碼，即使程式碼區塊擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="77c75-104">The `try...finally` expression enables you to execute clean-up code even if a block of code throws an exception.</span></span>

## <a name="syntax"></a><span data-ttu-id="77c75-105">語法</span><span class="sxs-lookup"><span data-stu-id="77c75-105">Syntax</span></span>

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a><span data-ttu-id="77c75-106">備註</span><span class="sxs-lookup"><span data-stu-id="77c75-106">Remarks</span></span>

<span data-ttu-id="77c75-107">`try...finally`運算式可用於執行中的程式碼*expression2*在前述的語法，不論是否在執行期間會產生例外狀況*expression1*。</span><span class="sxs-lookup"><span data-stu-id="77c75-107">The `try...finally` expression can be used to execute the code in *expression2* in the preceding syntax regardless of whether an exception is generated during the execution of *expression1*.</span></span>

<span data-ttu-id="77c75-108">型別*expression2*並不含完整的運算式; 的值時不會發生例外狀況傳回的類型是中的最後一個值*expression1*。</span><span class="sxs-lookup"><span data-stu-id="77c75-108">The type of *expression2* does not contribute to the value of the whole expression; the type returned when an exception does not occur is the last value in *expression1*.</span></span> <span data-ttu-id="77c75-109">例外狀況發生時，會傳回任何值，並傳送至下一個相符例外狀況處理常式的呼叫堆疊的控制流程。</span><span class="sxs-lookup"><span data-stu-id="77c75-109">When an exception does occur, no value is returned and the flow of control transfers to the next matching exception handler up the call stack.</span></span> <span data-ttu-id="77c75-110">如果不找到任何例外狀況處理常式，則會終止程式。</span><span class="sxs-lookup"><span data-stu-id="77c75-110">If no exception handler is found, the program terminates.</span></span> <span data-ttu-id="77c75-111">在執行中相符的處理常式的程式碼或程式終止中的程式碼之前`finally`會執行分支。</span><span class="sxs-lookup"><span data-stu-id="77c75-111">Before the code in a matching handler is executed or the program terminates, the code in the `finally` branch is executed.</span></span>

<span data-ttu-id="77c75-112">下列程式碼示範如何使用`try...finally`運算式。</span><span class="sxs-lookup"><span data-stu-id="77c75-112">The following code demonstrates the use of the `try...finally` expression.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

<span data-ttu-id="77c75-113">在主控台輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="77c75-113">The output to the console is as follows.</span></span>

```
Closing stream
Exception handled.
```

<span data-ttu-id="77c75-114">之前已處理外部例外狀況，您可以從輸出中看到，關閉資料流和檔案`test.txt`包含文字`test1`，指出已排清緩衝區，並寫入磁碟，即使例外狀況傳送控制外部例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="77c75-114">As you can see from the output, the stream was closed before the outer exception was handled, and the file `test.txt` contains the text `test1`, which indicates that the buffers were flushed and written to disk even though the exception transferred control to the outer exception handler.</span></span>

<span data-ttu-id="77c75-115">請注意，`try...with`個別從建構`try...finally`建構。</span><span class="sxs-lookup"><span data-stu-id="77c75-115">Note that the `try...with` construct is a separate construct from the `try...finally` construct.</span></span> <span data-ttu-id="77c75-116">因此，如果您的程式碼需要兩`with`區塊和`finally`區塊中，您必須將巢狀化的兩個建構，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="77c75-116">Therefore, if your code requires both a `with` block and a `finally` block, you have to nest the two constructs, as in the following code example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

<span data-ttu-id="77c75-117">在 計算運算式的內容，包括循序項運算式與非同步的工作流程**try...最後**運算式可能會有的自訂實作。</span><span class="sxs-lookup"><span data-stu-id="77c75-117">In the context of computation expressions, including sequence expressions and asynchronous workflows, **try...finally** expressions can have a custom implementation.</span></span> <span data-ttu-id="77c75-118">如需詳細資訊，請參閱 <<c0> [ 計算運算式](../computation-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="77c75-118">For more information, see [Computation Expressions](../computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="77c75-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77c75-119">See also</span></span>

- [<span data-ttu-id="77c75-120">例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="77c75-120">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="77c75-121">例外狀況：`try...with` 運算式</span><span class="sxs-lookup"><span data-stu-id="77c75-121">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)
