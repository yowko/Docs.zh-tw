---
title: using 陳述式 - C# 參考
ms.date: 05/29/2020
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: b889d2fcbdf854dbe8948744810f9b74e9f0dac2
ms.sourcegitcommit: 5280b2aef60a1ed99002dba44e4b9e7f6c830604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/03/2020
ms.locfileid: "84307042"
---
# <a name="using-statement-c-reference"></a><span data-ttu-id="ec29f-102">using 陳述式 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="ec29f-102">using statement (C# Reference)</span></span>

<span data-ttu-id="ec29f-103">提供方便的語法，以確保正確使用 <xref:System.IDisposable> 物件。</span><span class="sxs-lookup"><span data-stu-id="ec29f-103">Provides a convenient syntax that ensures the correct use of <xref:System.IDisposable> objects.</span></span> <span data-ttu-id="ec29f-104">從 c # 8.0 開始， `using` 語句可確保正確使用 <xref:System.IAsyncDisposable> 物件。</span><span class="sxs-lookup"><span data-stu-id="ec29f-104">Beginning in C# 8.0, the `using` statement ensures the correct use of <xref:System.IAsyncDisposable> objects.</span></span>

## <a name="example"></a><span data-ttu-id="ec29f-105">範例</span><span class="sxs-lookup"><span data-stu-id="ec29f-105">Example</span></span>

<span data-ttu-id="ec29f-106">下列範例顯示如何使用 `using` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ec29f-106">The following example shows how to use the `using` statement.</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetFirstExample":::

<span data-ttu-id="ec29f-107">從 c # 8.0 開始，您可以針對 `using` 不需要大括弧的語句使用下列替代語法：</span><span class="sxs-lookup"><span data-stu-id="ec29f-107">Beginning with C# 8.0, you can use the following alternative syntax for the `using` statement that doesn't require braces:</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernUsing":::

## <a name="remarks"></a><span data-ttu-id="ec29f-108">備註</span><span class="sxs-lookup"><span data-stu-id="ec29f-108">Remarks</span></span>

<span data-ttu-id="ec29f-109"><xref:System.IO.File> 和 <xref:System.Drawing.Font> 是 Managed 類型的範例，這些類型會存取 Unmanaged 資源 (在本例中為檔案控制代碼和裝置內容)。</span><span class="sxs-lookup"><span data-stu-id="ec29f-109"><xref:System.IO.File> and <xref:System.Drawing.Font> are examples of managed types that access unmanaged resources (in this case file handles and device contexts).</span></span> <span data-ttu-id="ec29f-110">還有許多其他類型的 Unmanaged 資源，以及封裝這些資源的類別庫類型。</span><span class="sxs-lookup"><span data-stu-id="ec29f-110">There are many other kinds of unmanaged resources and class library types that encapsulate them.</span></span> <span data-ttu-id="ec29f-111">所有這類類型都必須執行 <xref:System.IDisposable> 介面或 <xref:System.IAsyncDisposable> 介面。</span><span class="sxs-lookup"><span data-stu-id="ec29f-111">All such types must implement the <xref:System.IDisposable> interface, or the <xref:System.IAsyncDisposable> interface.</span></span>

<span data-ttu-id="ec29f-112">當 `IDisposable` 物件的存留期限制為單一方法時，您應該在 `using` 陳述式中宣告它並加以具現化。</span><span class="sxs-lookup"><span data-stu-id="ec29f-112">When the lifetime of an `IDisposable` object is limited to a single method, you should declare and instantiate it in the `using` statement.</span></span> <span data-ttu-id="ec29f-113">`using` 陳述式會以正確的方式呼叫物件上的 <xref:System.IDisposable.Dispose%2A> 方法，而且 (當您如稍早所示使用它時) 它也會在一呼叫 <xref:System.IDisposable.Dispose%2A> 時讓物件本身超出範圍。</span><span class="sxs-lookup"><span data-stu-id="ec29f-113">The `using` statement calls the <xref:System.IDisposable.Dispose%2A> method on the object in the correct way, and (when you use it as shown earlier) it also causes the object itself to go out of scope as soon as <xref:System.IDisposable.Dispose%2A> is called.</span></span> <span data-ttu-id="ec29f-114">在 `using` 區塊內，物件是唯讀的，無法修改或重新指派。</span><span class="sxs-lookup"><span data-stu-id="ec29f-114">Within the `using` block, the object is read-only and can't be modified or reassigned.</span></span> <span data-ttu-id="ec29f-115">如果物件會執行 `IAsyncDisposable` ，而不是 `IDisposable` ，則 `using` 語句會呼叫 <xref:System.IAsyncDisposable.DisposeAsync%2A> 和 `awaits` 傳回的 <xref:System.Threading.Tasks.ValueTask> 。</span><span class="sxs-lookup"><span data-stu-id="ec29f-115">If the object implements `IAsyncDisposable` instead of `IDisposable`, the `using` statement calls the <xref:System.IAsyncDisposable.DisposeAsync%2A> and `awaits` the returned <xref:System.Threading.Tasks.ValueTask>.</span></span> <span data-ttu-id="ec29f-116">如需的詳細資訊 <xref:System.IAsyncDisposable> ，請參閱[執行 DisposeAsync 方法](../../../standard/garbage-collection/implementing-disposeasync.md)。</span><span class="sxs-lookup"><span data-stu-id="ec29f-116">For more information on <xref:System.IAsyncDisposable>, see [Implement a DisposeAsync method](../../../standard/garbage-collection/implementing-disposeasync.md).</span></span>

<span data-ttu-id="ec29f-117">`using`語句可確保 <xref:System.IDisposable.Dispose%2A> <xref:System.IAsyncDisposable.DisposeAsync%2A> 即使在區塊內發生例外狀況，也會呼叫（或） `using` 。</span><span class="sxs-lookup"><span data-stu-id="ec29f-117">The `using` statement ensures that <xref:System.IDisposable.Dispose%2A> (or <xref:System.IAsyncDisposable.DisposeAsync%2A>) is called even if an exception occurs within the `using` block.</span></span> <span data-ttu-id="ec29f-118">您可以藉由將物件放在 `try` 區塊內，然後 <xref:System.IDisposable.Dispose%2A> 在區塊中呼叫（或）來達到相同的結果 <xref:System.IAsyncDisposable.DisposeAsync%2A> `finally` ; 事實上，這就是 `using` 編譯器轉譯語句的方式。</span><span class="sxs-lookup"><span data-stu-id="ec29f-118">You can achieve the same result by putting the object inside a `try` block and then calling <xref:System.IDisposable.Dispose%2A> (or <xref:System.IAsyncDisposable.DisposeAsync%2A>) in a `finally` block; in fact, this is how the `using` statement is translated by the compiler.</span></span> <span data-ttu-id="ec29f-119">稍早的程式碼範例會在編譯時期展開為下列程式碼 (注意額外的大括號是為了建立物件的有限範圍)：</span><span class="sxs-lookup"><span data-stu-id="ec29f-119">The code example earlier expands to the following code at compile time (note the extra curly braces to create the limited scope for the object):</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetTryFinallyExample":::

<span data-ttu-id="ec29f-120">較新的 `using` 語句語法會轉譯成類似的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ec29f-120">The newer `using` statement syntax translates to similar code.</span></span> <span data-ttu-id="ec29f-121">`try`區塊會在宣告變數的位置開啟。</span><span class="sxs-lookup"><span data-stu-id="ec29f-121">The `try` block opens where the variable is declared.</span></span> <span data-ttu-id="ec29f-122">`finally`區塊會加入封閉區塊的結尾，通常是在方法的結尾處。</span><span class="sxs-lookup"><span data-stu-id="ec29f-122">The `finally` block is added at the close of the enclosing block, typically at the end of a method.</span></span>

<span data-ttu-id="ec29f-123">如需有關語句的詳細資訊 `try` - `finally` ，請參閱[try finally](try-finally.md)文章。</span><span class="sxs-lookup"><span data-stu-id="ec29f-123">For more information about the `try`-`finally` statement, see the [try-finally](try-finally.md) article.</span></span>

<span data-ttu-id="ec29f-124">一個類型的多個實例可以在單一語句中宣告 `using` ，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ec29f-124">Multiple instances of a type can be declared in a single `using` statement, as shown in the following example.</span></span> <span data-ttu-id="ec29f-125">請注意， `var` 當您在單一語句中宣告多個變數時，無法使用隱含類型變數（）：</span><span class="sxs-lookup"><span data-stu-id="ec29f-125">Notice that you can't use implicitly typed variables (`var`) when you declare multiple variables in a single statement:</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareMultipleVariables":::

<span data-ttu-id="ec29f-126">您也可以使用 c # 8 引進的新語法結合相同類型的多個宣告，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ec29f-126">You can combine multiple declarations of the same type using the new syntax introduced with C# 8 as well, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernMultipleVariables":::

<span data-ttu-id="ec29f-127">您可以具現化資源物件，然後將該變數傳遞給 `using` 語句，但這不是最佳作法。</span><span class="sxs-lookup"><span data-stu-id="ec29f-127">You can instantiate the resource object and then pass the variable to the `using` statement, but this isn't a best practice.</span></span> <span data-ttu-id="ec29f-128">在此情況下，控制權離開 `using` 區塊之後，物件仍會留在範圍內，不過它可能無法再存取其非受控資源。</span><span class="sxs-lookup"><span data-stu-id="ec29f-128">In this case, after control leaves the `using` block, the object remains in scope but probably has no access to its unmanaged resources.</span></span> <span data-ttu-id="ec29f-129">換句話說，它不再是完全初始化。</span><span class="sxs-lookup"><span data-stu-id="ec29f-129">In other words, it's not fully initialized anymore.</span></span> <span data-ttu-id="ec29f-130">如果您嘗試在 `using` 區塊外部使用該物件，則會有導致擲回例外狀況的風險。</span><span class="sxs-lookup"><span data-stu-id="ec29f-130">If you try to use the object outside the `using` block, you risk causing an exception to be thrown.</span></span> <span data-ttu-id="ec29f-131">基於這個理由，最好在語句中具現化物件 `using` ，並將其範圍限制為 `using` 區塊。</span><span class="sxs-lookup"><span data-stu-id="ec29f-131">For this reason, it's better to instantiate the object in the `using` statement and limit its scope to the `using` block.</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareBeforeUsing":::

<span data-ttu-id="ec29f-132">如需處置 `IDisposable` 物件的詳細資訊，請參閱[使用實作 IDisposable 的物件](../../../standard/garbage-collection/using-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="ec29f-132">For more information about disposing of `IDisposable` objects, see [Using objects that implement IDisposable](../../../standard/garbage-collection/using-objects.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ec29f-133">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="ec29f-133">C# language specification</span></span>

<span data-ttu-id="ec29f-134">如需詳細資訊，請參閱 [C# 語言規格](/dotnet/csharp/language-reference/language-specification/introduction)中的 [using 陳述式](~/_csharplang/spec/statements.md#the-using-statement)。</span><span class="sxs-lookup"><span data-stu-id="ec29f-134">For more information, see [The using statement](~/_csharplang/spec/statements.md#the-using-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="ec29f-135">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="ec29f-135">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec29f-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec29f-136">See also</span></span>

- [<span data-ttu-id="ec29f-137">C # 參考</span><span class="sxs-lookup"><span data-stu-id="ec29f-137">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ec29f-138">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="ec29f-138">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ec29f-139">C # 關鍵字</span><span class="sxs-lookup"><span data-stu-id="ec29f-139">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ec29f-140">using 指示詞</span><span class="sxs-lookup"><span data-stu-id="ec29f-140">using Directive</span></span>](using-directive.md)
- [<span data-ttu-id="ec29f-141">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="ec29f-141">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="ec29f-142">使用實作 IDisposable 的物件</span><span class="sxs-lookup"><span data-stu-id="ec29f-142">Using objects that implement IDisposable</span></span>](../../../standard/garbage-collection/using-objects.md)
- [<span data-ttu-id="ec29f-143">IDisposable 介面</span><span class="sxs-lookup"><span data-stu-id="ec29f-143">IDisposable interface</span></span>](xref:System.IDisposable)
- [<span data-ttu-id="ec29f-144">c # 8.0 中的 using 語句</span><span class="sxs-lookup"><span data-stu-id="ec29f-144">using statement in C# 8.0</span></span>](~/_csharplang/proposals/csharp-8.0/using.md)
