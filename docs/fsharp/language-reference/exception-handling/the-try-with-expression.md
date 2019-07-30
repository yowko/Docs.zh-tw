---
title: 例外狀況：Try...with 運算式
description: 瞭解如何使用F# 「試試 ...」具有「例外狀況處理」的運算式。
ms.date: 05/16/2016
ms.openlocfilehash: e4d615086a93e26b76cca460e797659ca13792b5
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630255"
---
# <a name="exceptions-the-trywith-expression"></a><span data-ttu-id="05ac8-103">例外狀況：Try...with 運算式</span><span class="sxs-lookup"><span data-stu-id="05ac8-103">Exceptions: The try...with Expression</span></span>

<span data-ttu-id="05ac8-104">本主題描述`try...with`運算式, 這是在F#語言中用於例外狀況處理的運算式。</span><span class="sxs-lookup"><span data-stu-id="05ac8-104">This topic describes the `try...with` expression, the expression that is used for exception handling in the F# language.</span></span>

## <a name="syntax"></a><span data-ttu-id="05ac8-105">語法</span><span class="sxs-lookup"><span data-stu-id="05ac8-105">Syntax</span></span>

```fsharp
try
    expression1
with
| pattern1 -> expression2
| pattern2 -> expression3
...
```

## <a name="remarks"></a><span data-ttu-id="05ac8-106">備註</span><span class="sxs-lookup"><span data-stu-id="05ac8-106">Remarks</span></span>

<span data-ttu-id="05ac8-107">運算式是用來處理中F#的例外狀況。 `try...with`</span><span class="sxs-lookup"><span data-stu-id="05ac8-107">The `try...with` expression is used to handle exceptions in F#.</span></span> <span data-ttu-id="05ac8-108">這類似于中`try...catch` C#的語句。</span><span class="sxs-lookup"><span data-stu-id="05ac8-108">It is similar to the `try...catch` statement in C#.</span></span> <span data-ttu-id="05ac8-109">在上述語法中,*運算式*中的程式碼可能會產生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="05ac8-109">In the preceding syntax, the code in *expression1* might generate an exception.</span></span> <span data-ttu-id="05ac8-110">`try...with`運算式會傳回值。</span><span class="sxs-lookup"><span data-stu-id="05ac8-110">The `try...with` expression returns a value.</span></span> <span data-ttu-id="05ac8-111">如果未擲回任何例外狀況, 則整個運算式會傳回值為*運算式*。</span><span class="sxs-lookup"><span data-stu-id="05ac8-111">If no exception is thrown, the whole expression returns the value of *expression1*.</span></span> <span data-ttu-id="05ac8-112">如果擲回例外狀況, 每個*模式*會依序與例外狀況進行比較, 而針對第一個比對模式, 會執行對應的*運算式*(稱為*例外狀況處理常式*), 並使用整體運算式傳回該例外狀況處理常式中運算式的值。</span><span class="sxs-lookup"><span data-stu-id="05ac8-112">If an exception is thrown, each *pattern* is compared in turn with the exception, and for the first matching pattern, the corresponding *expression*, known as the *exception handler*, for that branch is executed, and the overall expression returns the value of the expression in that exception handler.</span></span> <span data-ttu-id="05ac8-113">如果沒有符合的模式, 例外狀況會傳播呼叫堆疊, 直到找到相符的處理常式為止。</span><span class="sxs-lookup"><span data-stu-id="05ac8-113">If no pattern matches, the exception propagates up the call stack until a matching handler is found.</span></span> <span data-ttu-id="05ac8-114">在例外狀況處理常式中, 從每個運算式傳回的數值型別, 必須符合從`try`區塊中的運算式傳回的類型。</span><span class="sxs-lookup"><span data-stu-id="05ac8-114">The types of the values returned from each expression in the exception handlers must match the type returned from the expression in the `try` block.</span></span>

<span data-ttu-id="05ac8-115">通常, 發生錯誤的事實也表示沒有可從每個例外狀況處理常式中的運算式傳回的有效值。</span><span class="sxs-lookup"><span data-stu-id="05ac8-115">Frequently, the fact that an error occurred also means that there is no valid value that can be returned from the expressions in each exception handler.</span></span> <span data-ttu-id="05ac8-116">常見的模式是讓運算式的類型是選項類型。</span><span class="sxs-lookup"><span data-stu-id="05ac8-116">A frequent pattern is to have the type of the expression be an option type.</span></span> <span data-ttu-id="05ac8-117">下列程式碼範例說明此模式。</span><span class="sxs-lookup"><span data-stu-id="05ac8-117">The following code example illustrates this pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

<span data-ttu-id="05ac8-118">例外狀況可以是 .NET 例外狀況, 也可以F#是例外狀況。</span><span class="sxs-lookup"><span data-stu-id="05ac8-118">Exceptions can be .NET exceptions, or they can be F# exceptions.</span></span> <span data-ttu-id="05ac8-119">您可以使用F# `exception`關鍵字來定義例外狀況。</span><span class="sxs-lookup"><span data-stu-id="05ac8-119">You can define F# exceptions by using the `exception` keyword.</span></span>

<span data-ttu-id="05ac8-120">您可以使用各種不同的模式來篩選例外狀況類型和其他條件;下表摘要說明這些選項。</span><span class="sxs-lookup"><span data-stu-id="05ac8-120">You can use a variety of patterns to filter on the exception type and other conditions; the options are summarized in the following table.</span></span>

|<span data-ttu-id="05ac8-121">模式</span><span class="sxs-lookup"><span data-stu-id="05ac8-121">Pattern</span></span>|<span data-ttu-id="05ac8-122">說明</span><span class="sxs-lookup"><span data-stu-id="05ac8-122">Description</span></span>|
|-------|-----------|
|<span data-ttu-id="05ac8-123">:?</span><span class="sxs-lookup"><span data-stu-id="05ac8-123">:?</span></span> <span data-ttu-id="05ac8-124">*exception-type*</span><span class="sxs-lookup"><span data-stu-id="05ac8-124">*exception-type*</span></span>|<span data-ttu-id="05ac8-125">符合指定的 .NET 例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="05ac8-125">Matches the specified .NET exception type.</span></span>|
|<span data-ttu-id="05ac8-126">:?</span><span class="sxs-lookup"><span data-stu-id="05ac8-126">:?</span></span> <span data-ttu-id="05ac8-127">*例外狀況-類型*做為*識別碼*</span><span class="sxs-lookup"><span data-stu-id="05ac8-127">*exception-type* as *identifier*</span></span>|<span data-ttu-id="05ac8-128">符合指定的 .NET 例外狀況類型, 但提供例外狀況的已命名值。</span><span class="sxs-lookup"><span data-stu-id="05ac8-128">Matches the specified .NET exception type, but gives the exception a named value.</span></span>|
|<span data-ttu-id="05ac8-129">*exception-name*(*arguments*)</span><span class="sxs-lookup"><span data-stu-id="05ac8-129">*exception-name*(*arguments*)</span></span>|<span data-ttu-id="05ac8-130">符合F#例外狀況類型, 並系結引數。</span><span class="sxs-lookup"><span data-stu-id="05ac8-130">Matches an F# exception type and binds the arguments.</span></span>|
|<span data-ttu-id="05ac8-131">*identifier*</span><span class="sxs-lookup"><span data-stu-id="05ac8-131">*identifier*</span></span>|<span data-ttu-id="05ac8-132">符合任何例外狀況, 並將名稱系結至例外狀況物件。</span><span class="sxs-lookup"><span data-stu-id="05ac8-132">Matches any exception and binds the name to the exception object.</span></span> <span data-ttu-id="05ac8-133">相當於 **:？Exception 作為**_識別碼_</span><span class="sxs-lookup"><span data-stu-id="05ac8-133">Equivalent to **:? System.Exception as**_identifier_</span></span>|
|<span data-ttu-id="05ac8-134">*條件*的*識別碼*</span><span class="sxs-lookup"><span data-stu-id="05ac8-134">*identifier* when *condition*</span></span>|<span data-ttu-id="05ac8-135">如果條件為 true, 則符合任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="05ac8-135">Matches any exception if the condition is true.</span></span>|

## <a name="examples"></a><span data-ttu-id="05ac8-136">範例</span><span class="sxs-lookup"><span data-stu-id="05ac8-136">Examples</span></span>

<span data-ttu-id="05ac8-137">下列程式碼範例說明如何使用各種例外狀況處理常式模式。</span><span class="sxs-lookup"><span data-stu-id="05ac8-137">The following code examples illustrate the use of the various exception handler patterns.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]

> [!NOTE]
> <span data-ttu-id="05ac8-138">結構是`try...finally`運算式中的另一個運算式。 `try...with`</span><span class="sxs-lookup"><span data-stu-id="05ac8-138">The `try...with` construct is a separate expression from the `try...finally` expression.</span></span> <span data-ttu-id="05ac8-139">因此, 如果您的`with`程式碼同時需要區塊`finally`和區塊, 您就必須將這兩個運算式加以嵌套。</span><span class="sxs-lookup"><span data-stu-id="05ac8-139">Therefore, if your code requires both a `with` block and a `finally` block, you will have to nest the two expressions.</span></span>

> [!NOTE]
> <span data-ttu-id="05ac8-140">您可以在`try...with`非同步工作流程和其他計算運算式中使用, 在此情況下會使用`try...with`自訂版本的運算式。</span><span class="sxs-lookup"><span data-stu-id="05ac8-140">You can use `try...with` in asynchronous workflows and other computation expressions, in which case a customized version of the `try...with` expression is used.</span></span> <span data-ttu-id="05ac8-141">如需詳細資訊, 請參閱[非同步工作流程](../asynchronous-workflows.md)和[計算運算式](../computation-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="05ac8-141">For more information, see [Asynchronous Workflows](../asynchronous-workflows.md), and [Computation Expressions](../computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="05ac8-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05ac8-142">See also</span></span>

- [<span data-ttu-id="05ac8-143">例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="05ac8-143">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="05ac8-144">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="05ac8-144">Exception Types</span></span>](exception-types.md)
- [<span data-ttu-id="05ac8-145">例外狀況：`try...finally`運算式</span><span class="sxs-lookup"><span data-stu-id="05ac8-145">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)
