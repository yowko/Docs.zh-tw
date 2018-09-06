---
title: 例外狀況：try...with 運算式 (F#)
description: "了解如何使用 例外狀況處理 F # 'try...with' 運算式。"
ms.date: 05/16/2016
ms.openlocfilehash: 588960c0f8ccedb431c37d0f1314bf1a293b638c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "44042162"
---
# <a name="exceptions-the-trywith-expression"></a><span data-ttu-id="2afcf-103">例外狀況：try...with 運算式</span><span class="sxs-lookup"><span data-stu-id="2afcf-103">Exceptions: The try...with Expression</span></span>

<span data-ttu-id="2afcf-104">本主題描述`try...with`運算式，用於在 F # 語言中處理的例外狀況的運算式。</span><span class="sxs-lookup"><span data-stu-id="2afcf-104">This topic describes the `try...with` expression, the expression that is used for exception handling in the F# language.</span></span>

## <a name="syntax"></a><span data-ttu-id="2afcf-105">語法</span><span class="sxs-lookup"><span data-stu-id="2afcf-105">Syntax</span></span>

```fsharp
try
    expression1
with
| pattern1 -> expression2
| pattern2 -> expression3
...
```

## <a name="remarks"></a><span data-ttu-id="2afcf-106">備註</span><span class="sxs-lookup"><span data-stu-id="2afcf-106">Remarks</span></span>

<span data-ttu-id="2afcf-107">`try...with`運算式用來處理在 F # 中的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2afcf-107">The `try...with` expression is used to handle exceptions in F#.</span></span> <span data-ttu-id="2afcf-108">類似於`try...catch`C# 中的陳述式。</span><span class="sxs-lookup"><span data-stu-id="2afcf-108">It is similar to the `try...catch` statement in C#.</span></span> <span data-ttu-id="2afcf-109">在上述語法中中的程式碼*expression1*可能產生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2afcf-109">In the preceding syntax, the code in *expression1* might generate an exception.</span></span> <span data-ttu-id="2afcf-110">`try...with`運算式傳回的值。</span><span class="sxs-lookup"><span data-stu-id="2afcf-110">The `try...with` expression returns a value.</span></span> <span data-ttu-id="2afcf-111">如果擲不回任何例外狀況，整個運算式會傳回的值*expression1*。</span><span class="sxs-lookup"><span data-stu-id="2afcf-111">If no exception is thrown, the whole expression returns the value of *expression1*.</span></span> <span data-ttu-id="2afcf-112">如果發生例外狀況，每個*圖樣*例外狀況，以及針對對應的第一個模式比對會依次比較*運算式*，稱為*例外狀況處理常式*，則請針對該分支會執行，並整體的運算式傳回運算式的值在該例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="2afcf-112">If an exception is thrown, each *pattern* is compared in turn with the exception, and for the first matching pattern, the corresponding *expression*, known as the *exception handler*, for that branch is executed, and the overall expression returns the value of the expression in that exception handler.</span></span> <span data-ttu-id="2afcf-113">如果沒有模式會比對，在呼叫堆疊會傳播例外狀況，直到找到相符的處理常式。</span><span class="sxs-lookup"><span data-stu-id="2afcf-113">If no pattern matches, the exception propagates up the call stack until a matching handler is found.</span></span> <span data-ttu-id="2afcf-114">傳回例外狀況處理常式中的每個運算式的值的型別必須符合的運算式傳回的型別`try`區塊。</span><span class="sxs-lookup"><span data-stu-id="2afcf-114">The types of the values returned from each expression in the exception handlers must match the type returned from the expression in the `try` block.</span></span>

<span data-ttu-id="2afcf-115">通常，也發生錯誤，這表示沒有有效的值從每個例外狀況處理常式中的運算式可傳回。</span><span class="sxs-lookup"><span data-stu-id="2afcf-115">Frequently, the fact that an error occurred also means that there is no valid value that can be returned from the expressions in each exception handler.</span></span> <span data-ttu-id="2afcf-116">常見的模式是將運算式的型別是選項類型。</span><span class="sxs-lookup"><span data-stu-id="2afcf-116">A frequent pattern is to have the type of the expression be an option type.</span></span> <span data-ttu-id="2afcf-117">下列程式碼範例將示範這個模式。</span><span class="sxs-lookup"><span data-stu-id="2afcf-117">The following code example illustrates this pattern.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

<span data-ttu-id="2afcf-118">例外狀況可以是.NET 例外狀況，或者可以是 F # 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2afcf-118">Exceptions can be .NET exceptions, or they can be F# exceptions.</span></span> <span data-ttu-id="2afcf-119">您可以使用，以定義 F # 例外狀況`exception`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="2afcf-119">You can define F# exceptions by using the `exception` keyword.</span></span>

<span data-ttu-id="2afcf-120">您可以使用各種不同的模式，若要篩選的例外狀況類型和其他條件;下表摘要說明選項。</span><span class="sxs-lookup"><span data-stu-id="2afcf-120">You can use a variety of patterns to filter on the exception type and other conditions; the options are summarized in the following table.</span></span>

|<span data-ttu-id="2afcf-121">模式</span><span class="sxs-lookup"><span data-stu-id="2afcf-121">Pattern</span></span>|<span data-ttu-id="2afcf-122">描述</span><span class="sxs-lookup"><span data-stu-id="2afcf-122">Description</span></span>|
|-------|-----------|
|<span data-ttu-id="2afcf-123">:?</span><span class="sxs-lookup"><span data-stu-id="2afcf-123">:?</span></span> <span data-ttu-id="2afcf-124">*例外狀況類型*</span><span class="sxs-lookup"><span data-stu-id="2afcf-124">*exception-type*</span></span>|<span data-ttu-id="2afcf-125">比對指定的.NET 例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="2afcf-125">Matches the specified .NET exception type.</span></span>|
|<span data-ttu-id="2afcf-126">:?</span><span class="sxs-lookup"><span data-stu-id="2afcf-126">:?</span></span> <span data-ttu-id="2afcf-127">*例外狀況型別*做為*識別碼*</span><span class="sxs-lookup"><span data-stu-id="2afcf-127">*exception-type* as *identifier*</span></span>|<span data-ttu-id="2afcf-128">符合指定的.NET 例外狀況類型，但可讓例外狀況的已命名的值。</span><span class="sxs-lookup"><span data-stu-id="2afcf-128">Matches the specified .NET exception type, but gives the exception a named value.</span></span>|
|<span data-ttu-id="2afcf-129">*例外狀況名稱*(*引數*)</span><span class="sxs-lookup"><span data-stu-id="2afcf-129">*exception-name*(*arguments*)</span></span>|<span data-ttu-id="2afcf-130">比對的 F # 例外狀況類型並繫結引數。</span><span class="sxs-lookup"><span data-stu-id="2afcf-130">Matches an F# exception type and binds the arguments.</span></span>|
|<span data-ttu-id="2afcf-131">*identifier*</span><span class="sxs-lookup"><span data-stu-id="2afcf-131">*identifier*</span></span>|<span data-ttu-id="2afcf-132">符合任何例外狀況和繫結至例外狀況物件的名稱。</span><span class="sxs-lookup"><span data-stu-id="2afcf-132">Matches any exception and binds the name to the exception object.</span></span> <span data-ttu-id="2afcf-133">相當於 \**： 嗎？System.Exception 為 \* \* \* 識別碼*</span><span class="sxs-lookup"><span data-stu-id="2afcf-133">Equivalent to \**:? System.Exception as\*\*\*identifier*</span></span>|
|<span data-ttu-id="2afcf-134">*識別項*當*條件*</span><span class="sxs-lookup"><span data-stu-id="2afcf-134">*identifier* when *condition*</span></span>|<span data-ttu-id="2afcf-135">如果條件為 true 會比對任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2afcf-135">Matches any exception if the condition is true.</span></span>|

## <a name="examples"></a><span data-ttu-id="2afcf-136">範例</span><span class="sxs-lookup"><span data-stu-id="2afcf-136">Examples</span></span>

<span data-ttu-id="2afcf-137">下列程式碼範例說明使用各種不同例外狀況處理常式模式。</span><span class="sxs-lookup"><span data-stu-id="2afcf-137">The following code examples illustrate the use of the various exception handler patterns.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]

>[!NOTE]
<span data-ttu-id="2afcf-138">`try...with`建構是從個別運算式`try...finally`運算式。</span><span class="sxs-lookup"><span data-stu-id="2afcf-138">The `try...with` construct is a separate expression from the `try...finally` expression.</span></span> <span data-ttu-id="2afcf-139">因此，如果您的程式碼需要兩`with`區塊和`finally`區塊中，您必須將巢狀化兩個運算式。</span><span class="sxs-lookup"><span data-stu-id="2afcf-139">Therefore, if your code requires both a `with` block and a `finally` block, you will have to nest the two expressions.</span></span>

>[!NOTE]
<span data-ttu-id="2afcf-140">您可以使用`try...with`中的非同步工作流程和其他計算運算式，在其中案例的自訂的版本`try...with`運算式的使用方式。</span><span class="sxs-lookup"><span data-stu-id="2afcf-140">You can use `try...with` in asynchronous workflows and other computation expressions, in which case a customized version of the `try...with` expression is used.</span></span> <span data-ttu-id="2afcf-141">如需詳細資訊，請參閱 <<c0> [ 非同步工作流程](../asynchronous-workflows.md)，並[計算運算式](../computation-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="2afcf-141">For more information, see [Asynchronous Workflows](../asynchronous-workflows.md), and [Computation Expressions](../computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2afcf-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2afcf-142">See also</span></span>

- [<span data-ttu-id="2afcf-143">例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="2afcf-143">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="2afcf-144">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="2afcf-144">Exception Types</span></span>](exception-types.md)
- [<span data-ttu-id="2afcf-145">例外狀況：`try...finally` 運算式</span><span class="sxs-lookup"><span data-stu-id="2afcf-145">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)
