---
title: 執行 DisposeAsync 方法
description: ''
ms.date: 06/02/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
helpviewer_keywords:
- DisposeAsync method
- garbage collection, DisposeAsync method
ms.openlocfilehash: c4f541d5a4f5b5fd31b344a299789d86cd78424c
ms.sourcegitcommit: 5280b2aef60a1ed99002dba44e4b9e7f6c830604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/03/2020
ms.locfileid: "84311011"
---
# <a name="implement-a-disposeasync-method"></a><span data-ttu-id="aaa56-102">執行 DisposeAsync 方法</span><span class="sxs-lookup"><span data-stu-id="aaa56-102">Implement a DisposeAsync method</span></span>

<span data-ttu-id="aaa56-103"><xref:System.IAsyncDisposable?displayProperty=nameWithType>介面是在 c # 8.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="aaa56-103">The <xref:System.IAsyncDisposable?displayProperty=nameWithType> interface was introduced as part of C# 8.0.</span></span> <span data-ttu-id="aaa56-104"><xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType>當您需要執行資源清理時，您可以實作為方法，就像您在實作為[處置方法](implementing-dispose.md)時所做的一樣。</span><span class="sxs-lookup"><span data-stu-id="aaa56-104">You implement the <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> method when you need to perform resource cleanup, just as you would when [implementing a Dispose method](implementing-dispose.md).</span></span> <span data-ttu-id="aaa56-105">不過，其中一個主要差異在於，此實作為允許非同步清除作業。</span><span class="sxs-lookup"><span data-stu-id="aaa56-105">One of the key differences however, is that this implementation allows for asynchronous cleanup operations.</span></span> <span data-ttu-id="aaa56-106"><xref:System.IAsyncDisposable.DisposeAsync> <xref:System.Threading.Tasks.ValueTask> 會傳回表示非同步處置作業的。</span><span class="sxs-lookup"><span data-stu-id="aaa56-106">The <xref:System.IAsyncDisposable.DisposeAsync> returns a <xref:System.Threading.Tasks.ValueTask> that represents the asynchronous dispose operation.</span></span>

<span data-ttu-id="aaa56-107">通常在執行 <xref:System.IAsyncDisposable> 介面時，類別也會執行 <xref:System.IDisposable> 介面。</span><span class="sxs-lookup"><span data-stu-id="aaa56-107">It is typical that when implementing the <xref:System.IAsyncDisposable> interface, classes will also implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="aaa56-108">介面的良好執行模式 <xref:System.IAsyncDisposable> 是針對同步或非同步處置進行準備。</span><span class="sxs-lookup"><span data-stu-id="aaa56-108">A good implementation pattern of the <xref:System.IAsyncDisposable> interface is to be prepared for either synchronous, or asynchronous dispose.</span></span> <span data-ttu-id="aaa56-109">所有執行 dispose 模式的指導方針都適用于非同步執行。</span><span class="sxs-lookup"><span data-stu-id="aaa56-109">All of the guidance for implementing the dispose pattern applies to the asynchronous implementation.</span></span> <span data-ttu-id="aaa56-110">本文假設您已經熟悉如何[執行 Dispose 方法](implementing-dispose.md)。</span><span class="sxs-lookup"><span data-stu-id="aaa56-110">This article assumes that you're already familiar with how to [implement a Dispose method](implementing-dispose.md).</span></span>

## <a name="disposeasync-and-disposeasynccore"></a><span data-ttu-id="aaa56-111">DisposeAsync （）和 DisposeAsyncCore （）</span><span class="sxs-lookup"><span data-stu-id="aaa56-111">DisposeAsync() and DisposeAsyncCore()</span></span>

<span data-ttu-id="aaa56-112">介面會宣告 <xref:System.IAsyncDisposable> 單一無參數方法 <xref:System.IAsyncDisposable.DisposeAsync> 。</span><span class="sxs-lookup"><span data-stu-id="aaa56-112">The <xref:System.IAsyncDisposable> interface declares a single parameterless method, <xref:System.IAsyncDisposable.DisposeAsync>.</span></span> <span data-ttu-id="aaa56-113">任何非密封的類別都應該具有另一個也會傳回 `DisposeAsyncCore()` 的方法 <xref:System.Threading.Tasks.ValueTask> 。</span><span class="sxs-lookup"><span data-stu-id="aaa56-113">Any non-sealed class should have an additional `DisposeAsyncCore()` method that also returns a <xref:System.Threading.Tasks.ValueTask>.</span></span>

- <span data-ttu-id="aaa56-114">沒有 `public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> 參數的執行。</span><span class="sxs-lookup"><span data-stu-id="aaa56-114">A `public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> implementation that has no parameters.</span></span>
- <span data-ttu-id="aaa56-115">其簽章 `protected virtual ValueTask DisposeAsyncCore()` 為的方法：</span><span class="sxs-lookup"><span data-stu-id="aaa56-115">A `protected virtual ValueTask DisposeAsyncCore()` method whose signature is:</span></span>

```csharp
protected virtual ValueTask DisposeAsyncCore()
{
}
```

<span data-ttu-id="aaa56-116">`DisposeAsyncCore()`方法是 `virtual` 讓衍生類別可以在其覆寫中定義額外的清除。</span><span class="sxs-lookup"><span data-stu-id="aaa56-116">The `DisposeAsyncCore()` method is `virtual` so that derived classes can define additional cleanup in their overrides.</span></span>

### <a name="the-disposeasync-method"></a><span data-ttu-id="aaa56-117">DisposeAsync （）方法</span><span class="sxs-lookup"><span data-stu-id="aaa56-117">The DisposeAsync() method</span></span>

<span data-ttu-id="aaa56-118">`public`無參數 `DisposeAsync()` 方法會在語句中隱含地呼叫， `await using` 其目的是要釋放非受控資源、執行一般清除，並指出完成項（如果有的話）不需要執行。</span><span class="sxs-lookup"><span data-stu-id="aaa56-118">The `public` parameterless `DisposeAsync()` method is called implicitly in an `await using` statement, and its purpose is to free unmanaged resources, perform general cleanup, and to indicate that the finalizer, if one is present, needn't run.</span></span> <span data-ttu-id="aaa56-119">釋放與 managed 物件相關聯的記憶體一律是[垃圾收集](index.md)行程的網域。</span><span class="sxs-lookup"><span data-stu-id="aaa56-119">Freeing the memory associated with a managed object is always the domain of the [garbage collector](index.md).</span></span> <span data-ttu-id="aaa56-120">因此，它擁有標準實作：</span><span class="sxs-lookup"><span data-stu-id="aaa56-120">Because of this, it has a standard implementation:</span></span>

```csharp
public async ValueTask DisposeAsync()
{
    // Perform async cleanup.
    await DisposeAsyncCore();

    // Dispose of managed resources.
    Dispose(false);
    // Suppress finalization.
    GC.SuppressFinalize(this);
}
```

> [!NOTE]
> <span data-ttu-id="aaa56-121">相較于處置模式，非同步處置模式的一個主要差異在於，從到多載 <xref:System.IAsyncDisposable.DisposeAsync> 方法的呼叫 `Dispose(bool)` 會被指定 `false` 為引數。</span><span class="sxs-lookup"><span data-stu-id="aaa56-121">One primary difference in the async dispose pattern compared to the dispose pattern, is that the call from <xref:System.IAsyncDisposable.DisposeAsync> to the `Dispose(bool)` overload method is given `false` as an argument.</span></span> <span data-ttu-id="aaa56-122"><xref:System.IDisposable.Dispose?displayProperty=nameWithType>不過，在執行方法時， `true` 會改為傳遞。</span><span class="sxs-lookup"><span data-stu-id="aaa56-122">When implementing the <xref:System.IDisposable.Dispose?displayProperty=nameWithType> method, however; `true` is passed instead.</span></span> <span data-ttu-id="aaa56-123">這有助於確保與同步處置模式的功能相等，並進一步確保仍會叫用完成項程式碼路徑。</span><span class="sxs-lookup"><span data-stu-id="aaa56-123">This helps ensure functional equivalence with the synchronous dispose pattern, and further ensures that finalizer code paths still get invoked.</span></span> <span data-ttu-id="aaa56-124">換句話說， `DisposeAsyncCore()` 方法會以非同步方式處置受管理的資源，因此您也不會想要同步處置它們。</span><span class="sxs-lookup"><span data-stu-id="aaa56-124">In other words, the `DisposeAsyncCore()` method will dispose of managed resources asynchronously, so you don't want to dispose of them synchronously as well.</span></span> <span data-ttu-id="aaa56-125">因此，請呼叫， `Dispose(false)` 而不是 `Dispose(true)` 。</span><span class="sxs-lookup"><span data-stu-id="aaa56-125">Therefore, call `Dispose(false)` instead of `Dispose(true)`.</span></span>

## <a name="implement-the-async-dispose-pattern"></a><span data-ttu-id="aaa56-126">執行非同步處置模式</span><span class="sxs-lookup"><span data-stu-id="aaa56-126">Implement the async dispose pattern</span></span>

<span data-ttu-id="aaa56-127">所有非密封類別都應該視為潛在的基類，因為它們可以被繼承。</span><span class="sxs-lookup"><span data-stu-id="aaa56-127">All non-sealed classes should be considered a potential base class, because they could be inherited.</span></span> <span data-ttu-id="aaa56-128">如果您針對任何可能的基類執行非同步處置模式，就必須提供 `protected virtual ValueTask DisposeAsyncCore()` 方法。</span><span class="sxs-lookup"><span data-stu-id="aaa56-128">If you implement the async dispose pattern for any potential base class, you must provide the `protected virtual ValueTask DisposeAsyncCore()` method.</span></span> <span data-ttu-id="aaa56-129">以下是使用的非同步處置模式的範例執行 <xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="aaa56-129">Here is an example implementation of the async dispose pattern that uses a <xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType>.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/disposeasync.cs":::

<span data-ttu-id="aaa56-130">先前的範例使用 <xref:System.Text.Json.Utf8JsonWriter> ，如需的詳細資訊 `System.Text.Json` ，請參閱[從 Newtonsoft 遷移至 system.object](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md)。</span><span class="sxs-lookup"><span data-stu-id="aaa56-130">The previous example used the <xref:System.Text.Json.Utf8JsonWriter>, for more information on `System.Text.Json`, see, [migrate from Newtonsoft.Json to System.Text.Json](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

## <a name="using-async-disposable"></a><span data-ttu-id="aaa56-131">使用非同步可處置</span><span class="sxs-lookup"><span data-stu-id="aaa56-131">Using async disposable</span></span>

<span data-ttu-id="aaa56-132">若要適當地取用會執行介面的物件 <xref:System.IAsyncDisposable> ，您可以使用[await](../../csharp/language-reference/operators/await.md)，並搭配[使用](../../csharp/language-reference/keywords/using.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="aaa56-132">To properly consume an object that implements the <xref:System.IAsyncDisposable> interface, you use the [await](../../csharp/language-reference/operators/await.md), and [using](../../csharp/language-reference/keywords/using.md) keywords together.</span></span> <span data-ttu-id="aaa56-133">請考慮下列範例，其中 `ExampleAsyncDisposable` 類別會具現化，然後包裝在 `await using` 語句中。</span><span class="sxs-lookup"><span data-stu-id="aaa56-133">Consider the following example, where the `ExampleAsyncDisposable` class is instantiated, then wrapped in an `await using` statement.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/proper-await-using.cs":::

> [!IMPORTANT]
> <span data-ttu-id="aaa56-134">使用 <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)> 介面的擴充方法 <xref:System.IAsyncDisposable> ，設定工作的接續在其原始內容或排程器上的封送處理方式。</span><span class="sxs-lookup"><span data-stu-id="aaa56-134">Use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)> extension method of the <xref:System.IAsyncDisposable> interface to configure how the continuation of the task is marshalled on its original context or scheduler.</span></span> <span data-ttu-id="aaa56-135">如需的詳細資訊 `ConfigureAwait` ，請參閱[ConfigureAwait 常見問題](https://devblogs.microsoft.com/dotnet/configureawait-faq/)。</span><span class="sxs-lookup"><span data-stu-id="aaa56-135">For more information on `ConfigureAwait`, see [ConfigureAwait FAQ](https://devblogs.microsoft.com/dotnet/configureawait-faq/).</span></span>

<span data-ttu-id="aaa56-136">在不需要使用的情況下 `ConfigureAwait` ， `await using` 可以簡化語句，如下所示：</span><span class="sxs-lookup"><span data-stu-id="aaa56-136">For situations where the usage of `ConfigureAwait` is not needed, the `await using` statement could be simplified as follows:</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-non-configureawait.cs":::

<span data-ttu-id="aaa56-137">此外，它也可以撰寫成使用[using](../../csharp/whats-new/csharp-8.md#using-declarations)宣告的隱含範圍。</span><span class="sxs-lookup"><span data-stu-id="aaa56-137">Furthermore, it could be written to use the implicit scoping of a [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations).</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-declaration.cs":::

## <a name="stacked-usings"></a><span data-ttu-id="aaa56-138">堆疊 using</span><span class="sxs-lookup"><span data-stu-id="aaa56-138">Stacked usings</span></span>

<span data-ttu-id="aaa56-139">在您建立和使用多個執行的物件的情況下 <xref:System.IAsyncDisposable> ， `using` 不當條件中的堆疊語句可能會防止對的呼叫 <xref:System.IAsyncDisposable.DisposeAsync> 。</span><span class="sxs-lookup"><span data-stu-id="aaa56-139">In situations where you create and use multiple objects that implement <xref:System.IAsyncDisposable>, it's possible that stacking `using` statements in errant conditions could prevent calls to <xref:System.IAsyncDisposable.DisposeAsync>.</span></span> <span data-ttu-id="aaa56-140">為了協助避免潛在的顧慮，您應該避免堆疊，並改為遵循此範例模式：</span><span class="sxs-lookup"><span data-stu-id="aaa56-140">In order to help prevent potential concern, you should avoid stacking, and instead follow this example pattern:</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/stacked-await-usings.cs":::

## <a name="see-also"></a><span data-ttu-id="aaa56-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aaa56-141">See also</span></span>

- <xref:System.IAsyncDisposable>
- <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)>
