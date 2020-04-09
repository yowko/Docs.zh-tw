---
title: using 陳述式 - C# 參考
ms.date: 04/07/2020
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: a237a90b4782e0460857c3d5d887771bcc8ccaaf
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989177"
---
# <a name="using-statement-c-reference"></a><span data-ttu-id="870cf-102">using 陳述式 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="870cf-102">using statement (C# Reference)</span></span>

<span data-ttu-id="870cf-103">提供方便的語法，以確保正確使用 <xref:System.IDisposable> 物件。</span><span class="sxs-lookup"><span data-stu-id="870cf-103">Provides a convenient syntax that ensures the correct use of <xref:System.IDisposable> objects.</span></span> <span data-ttu-id="870cf-104">從 C# 8.0`using`開始,語句可<xref:System.IAsyncDisposable>確保正確使用 物件。</span><span class="sxs-lookup"><span data-stu-id="870cf-104">Beginning in C# 8.0, the `using` statement ensures the correct use of <xref:System.IAsyncDisposable> objects.</span></span>

## <a name="example"></a><span data-ttu-id="870cf-105">範例</span><span class="sxs-lookup"><span data-stu-id="870cf-105">Example</span></span>

<span data-ttu-id="870cf-106">下列範例顯示如何使用 `using` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="870cf-106">The following example shows how to use the `using` statement.</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetFirstExample":::

<span data-ttu-id="870cf-107">從 C# 8.0 開始,對於不需要大`using`括弧的 語句,可以使用以下替代語法:</span><span class="sxs-lookup"><span data-stu-id="870cf-107">Beginning with C# 8.0, you can use the following alternative syntax for the `using` statement that doesn't require braces:</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernUsing":::

## <a name="remarks"></a><span data-ttu-id="870cf-108">備註</span><span class="sxs-lookup"><span data-stu-id="870cf-108">Remarks</span></span>

<span data-ttu-id="870cf-109"><xref:System.IO.File> 和 <xref:System.Drawing.Font> 是 Managed 類型的範例，這些類型會存取 Unmanaged 資源 (在本例中為檔案控制代碼和裝置內容)。</span><span class="sxs-lookup"><span data-stu-id="870cf-109"><xref:System.IO.File> and <xref:System.Drawing.Font> are examples of managed types that access unmanaged resources (in this case file handles and device contexts).</span></span> <span data-ttu-id="870cf-110">還有許多其他類型的 Unmanaged 資源，以及封裝這些資源的類別庫類型。</span><span class="sxs-lookup"><span data-stu-id="870cf-110">There are many other kinds of unmanaged resources and class library types that encapsulate them.</span></span> <span data-ttu-id="870cf-111">所有此類類型都必須實現<xref:System.IDisposable>介面<xref:System.IAsyncDisposable>或介面。</span><span class="sxs-lookup"><span data-stu-id="870cf-111">All such types must implement the <xref:System.IDisposable> interface, or the <xref:System.IAsyncDisposable> interface.</span></span>

<span data-ttu-id="870cf-112">當 `IDisposable` 物件的存留期限制為單一方法時，您應該在 `using` 陳述式中宣告它並加以具現化。</span><span class="sxs-lookup"><span data-stu-id="870cf-112">When the lifetime of an `IDisposable` object is limited to a single method, you should declare and instantiate it in the `using` statement.</span></span> <span data-ttu-id="870cf-113">`using` 陳述式會以正確的方式呼叫物件上的 <xref:System.IDisposable.Dispose%2A> 方法，而且 (當您如稍早所示使用它時) 它也會在一呼叫 <xref:System.IDisposable.Dispose%2A> 時讓物件本身超出範圍。</span><span class="sxs-lookup"><span data-stu-id="870cf-113">The `using` statement calls the <xref:System.IDisposable.Dispose%2A> method on the object in the correct way, and (when you use it as shown earlier) it also causes the object itself to go out of scope as soon as <xref:System.IDisposable.Dispose%2A> is called.</span></span> <span data-ttu-id="870cf-114">在塊`using`中,對像是唯讀的,不能修改或重新分配。</span><span class="sxs-lookup"><span data-stu-id="870cf-114">Within the `using` block, the object is read-only and can't be modified or reassigned.</span></span> <span data-ttu-id="870cf-115">如果物件`IAsyncDisposable`支援`IDisposable`,`using`而非 ,<xref:System.IAsyncDisposable.DisposeAsync%2A>`awaits`文<xref:System.Threading.Tasks.Task>句呼叫與傳回的 。</span><span class="sxs-lookup"><span data-stu-id="870cf-115">If the object implements `IAsyncDisposable` instead of `IDisposable`, the `using` statement calls the <xref:System.IAsyncDisposable.DisposeAsync%2A> and `awaits` the returned <xref:System.Threading.Tasks.Task>.</span></span>

<span data-ttu-id="870cf-116">語句`using`可<xref:System.IDisposable.Dispose%2A>確保<xref:System.IAsyncDisposable.DisposeAsync%2A>(或`using`) 即使塊中發生異常, 也會呼叫 。</span><span class="sxs-lookup"><span data-stu-id="870cf-116">The `using` statement ensures that <xref:System.IDisposable.Dispose%2A> (or <xref:System.IAsyncDisposable.DisposeAsync%2A>) is called even if an exception occurs within the `using` block.</span></span> <span data-ttu-id="870cf-117">通過將物件放在`try`<xref:System.IDisposable.Dispose%2A>塊中然後調用(<xref:System.IAsyncDisposable.DisposeAsync%2A>或`finally`在塊中;實際上,編譯器`using`就是這樣轉換 語句)來實現相同的結果。</span><span class="sxs-lookup"><span data-stu-id="870cf-117">You can achieve the same result by putting the object inside a `try` block and then calling <xref:System.IDisposable.Dispose%2A> (or <xref:System.IAsyncDisposable.DisposeAsync%2A> in a `finally` block; in fact, this is how the `using` statement is translated by the compiler.</span></span> <span data-ttu-id="870cf-118">稍早的程式碼範例會在編譯時期展開為下列程式碼 (注意額外的大括號是為了建立物件的有限範圍)：</span><span class="sxs-lookup"><span data-stu-id="870cf-118">The code example earlier expands to the following code at compile time (note the extra curly braces to create the limited scope for the object):</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetTryFinallyExample":::

<span data-ttu-id="870cf-119">較新的`using`語句語法轉換為類似的代碼。</span><span class="sxs-lookup"><span data-stu-id="870cf-119">The newer `using` statement syntax translates to similar code.</span></span> <span data-ttu-id="870cf-120">塊`try`將在聲明變數的位置打開。</span><span class="sxs-lookup"><span data-stu-id="870cf-120">The `try` block opens where the variable is declared.</span></span> <span data-ttu-id="870cf-121">塊`finally`在封閉塊的末尾添加,通常在方法的末尾。</span><span class="sxs-lookup"><span data-stu-id="870cf-121">The `finally` block is added at the close of the enclosing block, typically at the end of a method.</span></span>

<span data-ttu-id="870cf-122">有關該語句的詳細資訊,`try`-`finally`請參閱[最後嘗試](try-finally.md)一文。</span><span class="sxs-lookup"><span data-stu-id="870cf-122">For more information about the `try`-`finally` statement, see the [try-finally](try-finally.md) article.</span></span>

<span data-ttu-id="870cf-123">可以在單個`using`語句中聲明類型的多個實例,如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="870cf-123">Multiple instances of a type can be declared in a single `using` statement, as shown in the following example.</span></span> <span data-ttu-id="870cf-124">請注意,在單個語句中聲明多個變數時,不能使用`var`隱式類型變數 ( ):</span><span class="sxs-lookup"><span data-stu-id="870cf-124">Notice that you can't use implicitly typed variables (`var`) when you declare multiple variables in a single statement:</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareMultipleVariables":::

<span data-ttu-id="870cf-125">您可以使用與 C# 8 一起引入的新語法組合同一類型的多個聲明,如以下範例所示:</span><span class="sxs-lookup"><span data-stu-id="870cf-125">You can combine multiple declarations of the same type using the new syntax introduced with C# 8 as well, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernMultipleVariables":::

<span data-ttu-id="870cf-126">您可以實例化資源物件,然後將變數傳遞給`using`語句,但這不是最佳做法。</span><span class="sxs-lookup"><span data-stu-id="870cf-126">You can instantiate the resource object and then pass the variable to the `using` statement, but this isn't a best practice.</span></span> <span data-ttu-id="870cf-127">在此情況下，控制權離開 `using` 區塊之後，物件仍會留在範圍內，不過它可能無法再存取其非受控資源。</span><span class="sxs-lookup"><span data-stu-id="870cf-127">In this case, after control leaves the `using` block, the object remains in scope but probably has no access to its unmanaged resources.</span></span> <span data-ttu-id="870cf-128">換句話說，它不再是完全初始化。</span><span class="sxs-lookup"><span data-stu-id="870cf-128">In other words, it's not fully initialized anymore.</span></span> <span data-ttu-id="870cf-129">如果您嘗試在 `using` 區塊外部使用該物件，則會有導致擲回例外狀況的風險。</span><span class="sxs-lookup"><span data-stu-id="870cf-129">If you try to use the object outside the `using` block, you risk causing an exception to be thrown.</span></span> <span data-ttu-id="870cf-130">因此,最好實例化`using`語句中的物件並將其範圍限制`using`為 塊。</span><span class="sxs-lookup"><span data-stu-id="870cf-130">For this reason, it's better to instantiate the object in the `using` statement and limit its scope to the `using` block.</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareBeforeUsing":::

<span data-ttu-id="870cf-131">如需處置 `IDisposable` 物件的詳細資訊，請參閱[使用實作 IDisposable 的物件](../../../standard/garbage-collection/using-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="870cf-131">For more information about disposing of `IDisposable` objects, see [Using objects that implement IDisposable](../../../standard/garbage-collection/using-objects.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="870cf-132">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="870cf-132">C# language specification</span></span>

<span data-ttu-id="870cf-133">如需詳細資訊，請參閱 [C# 語言規格](/dotnet/csharp/language-reference/language-specification/introduction)中的 [using 陳述式](~/_csharplang/spec/statements.md#the-using-statement)。</span><span class="sxs-lookup"><span data-stu-id="870cf-133">For more information, see [The using statement](~/_csharplang/spec/statements.md#the-using-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="870cf-134">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="870cf-134">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="870cf-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="870cf-135">See also</span></span>

- [<span data-ttu-id="870cf-136">C# 參考</span><span class="sxs-lookup"><span data-stu-id="870cf-136">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="870cf-137">C# 編程指南</span><span class="sxs-lookup"><span data-stu-id="870cf-137">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="870cf-138">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="870cf-138">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="870cf-139">using 指示詞</span><span class="sxs-lookup"><span data-stu-id="870cf-139">using Directive</span></span>](using-directive.md)
- [<span data-ttu-id="870cf-140">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="870cf-140">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="870cf-141">使用實作 IDisposable 的物件</span><span class="sxs-lookup"><span data-stu-id="870cf-141">Using objects that implement IDisposable</span></span>](../../../standard/garbage-collection/using-objects.md)
- [<span data-ttu-id="870cf-142">IDisposable 介面</span><span class="sxs-lookup"><span data-stu-id="870cf-142">IDisposable interface</span></span>](xref:System.IDisposable)
- [<span data-ttu-id="870cf-143">在 C# 8.0 中使用敘述</span><span class="sxs-lookup"><span data-stu-id="870cf-143">using statement in C# 8.0</span></span>](~/_csharplang/proposals/csharp-8.0/using.md)
