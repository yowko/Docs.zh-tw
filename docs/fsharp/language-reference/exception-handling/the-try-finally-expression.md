---
title: 例外狀況：Try...try...finally 運算式
description: F#瞭解「try .。。最後, 即使程式碼區塊擲回例外狀況, 也可以讓您執行清除程式碼。
ms.date: 05/16/2016
ms.openlocfilehash: 03fbda1ef5d55560232f0217f603fc04c0af0eb4
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630282"
---
# <a name="exceptions-the-tryfinally-expression"></a><span data-ttu-id="bfa69-103">例外狀況：Try...try...finally 運算式</span><span class="sxs-lookup"><span data-stu-id="bfa69-103">Exceptions: The try...finally Expression</span></span>

<span data-ttu-id="bfa69-104">`try...finally`運算式可讓您執行清理程式碼, 即使程式碼區塊擲回例外狀況也一樣。</span><span class="sxs-lookup"><span data-stu-id="bfa69-104">The `try...finally` expression enables you to execute clean-up code even if a block of code throws an exception.</span></span>

## <a name="syntax"></a><span data-ttu-id="bfa69-105">語法</span><span class="sxs-lookup"><span data-stu-id="bfa69-105">Syntax</span></span>

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a><span data-ttu-id="bfa69-106">備註</span><span class="sxs-lookup"><span data-stu-id="bfa69-106">Remarks</span></span>

<span data-ttu-id="bfa69-107">運算式可用來在上述語法中, 以運算式2執行程式碼, 而不論是否在執行*運算式*的過程中產生例外狀況。 `try...finally`</span><span class="sxs-lookup"><span data-stu-id="bfa69-107">The `try...finally` expression can be used to execute the code in *expression2* in the preceding syntax regardless of whether an exception is generated during the execution of *expression1*.</span></span>

<span data-ttu-id="bfa69-108">*運算式*類型不會對整個運算式的值造成影響;未發生例外狀況時傳回的型別, 是*運算式*類型中的最後一個值。</span><span class="sxs-lookup"><span data-stu-id="bfa69-108">The type of *expression2* does not contribute to the value of the whole expression; the type returned when an exception does not occur is the last value in *expression1*.</span></span> <span data-ttu-id="bfa69-109">發生例外狀況時, 不會傳回任何值, 而且控制權的流程會傳送至呼叫堆疊的下一個相符的例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="bfa69-109">When an exception does occur, no value is returned and the flow of control transfers to the next matching exception handler up the call stack.</span></span> <span data-ttu-id="bfa69-110">如果找不到任何例外狀況處理常式, 則程式會終止。</span><span class="sxs-lookup"><span data-stu-id="bfa69-110">If no exception handler is found, the program terminates.</span></span> <span data-ttu-id="bfa69-111">在執行比對處理常式中的程式碼或程式終止之前, 會執行`finally`分支中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="bfa69-111">Before the code in a matching handler is executed or the program terminates, the code in the `finally` branch is executed.</span></span>

<span data-ttu-id="bfa69-112">下列程式碼示範`try...finally`運算式的用法。</span><span class="sxs-lookup"><span data-stu-id="bfa69-112">The following code demonstrates the use of the `try...finally` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

<span data-ttu-id="bfa69-113">主控台的輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="bfa69-113">The output to the console is as follows.</span></span>

```
Closing stream
Exception handled.
```

<span data-ttu-id="bfa69-114">如您在輸出中所見, 在處理外部例外狀況之前, 資料流程已關閉, 而且`test.txt`檔案包含文字`test1`, 這表示緩衝區已排清並寫入磁片, 即使已傳送例外狀況也是一樣。控制外部例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="bfa69-114">As you can see from the output, the stream was closed before the outer exception was handled, and the file `test.txt` contains the text `test1`, which indicates that the buffers were flushed and written to disk even though the exception transferred control to the outer exception handler.</span></span>

<span data-ttu-id="bfa69-115">請注意, `try...with`結構是`try...finally`來自結構的個別結構。</span><span class="sxs-lookup"><span data-stu-id="bfa69-115">Note that the `try...with` construct is a separate construct from the `try...finally` construct.</span></span> <span data-ttu-id="bfa69-116">因此, 如果您的`with`程式碼同時需要區塊`finally`和區塊, 您就必須將這兩個結構加以嵌套, 如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="bfa69-116">Therefore, if your code requires both a `with` block and a `finally` block, you have to nest the two constructs, as in the following code example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

<span data-ttu-id="bfa69-117">在計算運算式 (包括順序運算式和非同步工作流程) 的內容中,**嘗試 .。。最後**, 運算式可以有自訂的實作為。</span><span class="sxs-lookup"><span data-stu-id="bfa69-117">In the context of computation expressions, including sequence expressions and asynchronous workflows, **try...finally** expressions can have a custom implementation.</span></span> <span data-ttu-id="bfa69-118">如需詳細資訊, 請參閱[計算運算式](../computation-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="bfa69-118">For more information, see [Computation Expressions](../computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bfa69-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bfa69-119">See also</span></span>

- [<span data-ttu-id="bfa69-120">例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="bfa69-120">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="bfa69-121">例外狀況：`try...with`運算式</span><span class="sxs-lookup"><span data-stu-id="bfa69-121">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)
