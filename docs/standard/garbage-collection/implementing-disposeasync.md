---
title: 實作 DisposeAsync 方法
description: 瞭解如何執行 DisposeAsync 和 DisposeAsyncCore 方法，以執行非同步資源清除。
author: IEvangelist
ms.author: dapine
ms.date: 10/26/2020
dev_langs:
- csharp
helpviewer_keywords:
- DisposeAsync method
- garbage collection, DisposeAsync method
ms.openlocfilehash: 551dbc30f6f5c99c7bfa468d7d708789c06acb7b
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94827798"
---
# <a name="implement-a-disposeasync-method"></a><span data-ttu-id="abae9-103">實作 DisposeAsync 方法</span><span class="sxs-lookup"><span data-stu-id="abae9-103">Implement a DisposeAsync method</span></span>

<span data-ttu-id="abae9-104"><xref:System.IAsyncDisposable?displayProperty=nameWithType>介面是在 c # 8.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="abae9-104">The <xref:System.IAsyncDisposable?displayProperty=nameWithType> interface was introduced as part of C# 8.0.</span></span> <span data-ttu-id="abae9-105"><xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType>當您需要執行資源清除時，請執行方法，就像您在執行[Dispose 方法](implementing-dispose.md)時所做的一樣。</span><span class="sxs-lookup"><span data-stu-id="abae9-105">You implement the <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> method when you need to perform resource cleanup, just as you would when [implementing a Dispose method](implementing-dispose.md).</span></span> <span data-ttu-id="abae9-106">但是，其中一個主要差異在於，這項實行可進行非同步清除作業。</span><span class="sxs-lookup"><span data-stu-id="abae9-106">One of the key differences however, is that this implementation allows for asynchronous cleanup operations.</span></span> <span data-ttu-id="abae9-107"><xref:System.IAsyncDisposable.DisposeAsync> <xref:System.Threading.Tasks.ValueTask> 會傳回代表非同步處置作業的。</span><span class="sxs-lookup"><span data-stu-id="abae9-107">The <xref:System.IAsyncDisposable.DisposeAsync> returns a <xref:System.Threading.Tasks.ValueTask> that represents the asynchronous dispose operation.</span></span>

<span data-ttu-id="abae9-108">典型的情況是在實 <xref:System.IAsyncDisposable> 介面時，類別也會執行 <xref:System.IDisposable> 介面。</span><span class="sxs-lookup"><span data-stu-id="abae9-108">It is typical when implementing the <xref:System.IAsyncDisposable> interface that classes will also implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="abae9-109">介面的良好執行模式 <xref:System.IAsyncDisposable> 是針對同步或非同步處置做好準備。</span><span class="sxs-lookup"><span data-stu-id="abae9-109">A good implementation pattern of the <xref:System.IAsyncDisposable> interface is to be prepared for either synchronous or asynchronous dispose.</span></span> <span data-ttu-id="abae9-110">所有執行處置模式的指導方針也適用于非同步執行。</span><span class="sxs-lookup"><span data-stu-id="abae9-110">All of the guidance for implementing the dispose pattern also applies to the asynchronous implementation.</span></span> <span data-ttu-id="abae9-111">本文假設您已經熟悉如何 [執行 Dispose 方法](implementing-dispose.md)。</span><span class="sxs-lookup"><span data-stu-id="abae9-111">This article assumes that you're already familiar with how to [implement a Dispose method](implementing-dispose.md).</span></span>

## <a name="disposeasync-and-disposeasynccore"></a><span data-ttu-id="abae9-112">DisposeAsync ( # A1 和 DisposeAsyncCore ( # A3</span><span class="sxs-lookup"><span data-stu-id="abae9-112">DisposeAsync() and DisposeAsyncCore()</span></span>

<span data-ttu-id="abae9-113">介面會宣告 <xref:System.IAsyncDisposable> 單一無參數方法 <xref:System.IAsyncDisposable.DisposeAsync> 。</span><span class="sxs-lookup"><span data-stu-id="abae9-113">The <xref:System.IAsyncDisposable> interface declares a single parameterless method, <xref:System.IAsyncDisposable.DisposeAsync>.</span></span> <span data-ttu-id="abae9-114">任何非密封類別都應該有另一個 `DisposeAsyncCore()` 也會傳回的方法 <xref:System.Threading.Tasks.ValueTask> 。</span><span class="sxs-lookup"><span data-stu-id="abae9-114">Any non-sealed class should have an additional `DisposeAsyncCore()` method that also returns a <xref:System.Threading.Tasks.ValueTask>.</span></span>

- <span data-ttu-id="abae9-115">沒有 `public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> 參數的實作為。</span><span class="sxs-lookup"><span data-stu-id="abae9-115">A `public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> implementation that has no parameters.</span></span>
- <span data-ttu-id="abae9-116">其簽章 `protected virtual ValueTask DisposeAsyncCore()` 為的方法：</span><span class="sxs-lookup"><span data-stu-id="abae9-116">A `protected virtual ValueTask DisposeAsyncCore()` method whose signature is:</span></span>

  ```csharp
  protected virtual ValueTask DisposeAsyncCore()
  {
  }
  ```

### <a name="the-disposeasync-method"></a><span data-ttu-id="abae9-117">DisposeAsync ( # A1 方法</span><span class="sxs-lookup"><span data-stu-id="abae9-117">The DisposeAsync() method</span></span>

<span data-ttu-id="abae9-118">`public`無參數 `DisposeAsync()` 方法會以隱含方式在 `await using` 語句中呼叫，而其用途是釋放未受管理的資源、執行一般清除，以及指出完成項（如果有的話）不需要執行。</span><span class="sxs-lookup"><span data-stu-id="abae9-118">The `public` parameterless `DisposeAsync()` method is called implicitly in an `await using` statement, and its purpose is to free unmanaged resources, perform general cleanup, and to indicate that the finalizer, if one is present, need not run.</span></span> <span data-ttu-id="abae9-119">釋放與受管理物件相關聯的記憶體一律是 [垃圾收集](index.md)行程的網域。</span><span class="sxs-lookup"><span data-stu-id="abae9-119">Freeing the memory associated with a managed object is always the domain of the [garbage collector](index.md).</span></span> <span data-ttu-id="abae9-120">因此，它擁有標準實作：</span><span class="sxs-lookup"><span data-stu-id="abae9-120">Because of this, it has a standard implementation:</span></span>

```csharp
public async ValueTask DisposeAsync()
{
    // Perform async cleanup.
    await DisposeAsyncCore();

    // Dispose of unmanaged resources.
    Dispose(false);
    // Suppress finalization.
    GC.SuppressFinalize(this);
}
```

> [!NOTE]
> <span data-ttu-id="abae9-121">相較于處置模式，非同步處置模式中的一個主要差異是，從多載 <xref:System.IAsyncDisposable.DisposeAsync> 方法的呼叫 `Dispose(bool)` 會被指定 `false` 為引數。</span><span class="sxs-lookup"><span data-stu-id="abae9-121">One primary difference in the async dispose pattern compared to the dispose pattern, is that the call from <xref:System.IAsyncDisposable.DisposeAsync> to the `Dispose(bool)` overload method is given `false` as an argument.</span></span> <span data-ttu-id="abae9-122">不過，在執行 <xref:System.IDisposable.Dispose?displayProperty=nameWithType> 方法時， `true` 會改為傳遞。</span><span class="sxs-lookup"><span data-stu-id="abae9-122">When implementing the <xref:System.IDisposable.Dispose?displayProperty=nameWithType> method, however, `true` is passed instead.</span></span> <span data-ttu-id="abae9-123">這有助於確保與同步處置模式的功能性相等，並進一步確保仍會叫用完成項程式碼路徑。</span><span class="sxs-lookup"><span data-stu-id="abae9-123">This helps ensure functional equivalence with the synchronous dispose pattern, and further ensures that finalizer code paths still get invoked.</span></span> <span data-ttu-id="abae9-124">換句話說，此 `DisposeAsyncCore()` 方法會以非同步方式處置受控資源，因此您也不想要以同步方式處置它們。</span><span class="sxs-lookup"><span data-stu-id="abae9-124">In other words, the `DisposeAsyncCore()` method will dispose of managed resources asynchronously, so you don't want to dispose of them synchronously as well.</span></span> <span data-ttu-id="abae9-125">因此，請呼叫， `Dispose(false)` 而不是 `Dispose(true)` 。</span><span class="sxs-lookup"><span data-stu-id="abae9-125">Therefore, call `Dispose(false)` instead of `Dispose(true)`.</span></span>

### <a name="the-disposeasynccore-method"></a><span data-ttu-id="abae9-126">DisposeAsyncCore ( # A1 方法</span><span class="sxs-lookup"><span data-stu-id="abae9-126">The DisposeAsyncCore() method</span></span>

<span data-ttu-id="abae9-127">`DisposeAsyncCore()`方法的目的是要執行 managed 資源的非同步清除，或對的串聯呼叫 `DisposeAsync()` 。</span><span class="sxs-lookup"><span data-stu-id="abae9-127">The `DisposeAsyncCore()` method is intended to perform the asynchronous cleanup of managed resources or for cascading calls to `DisposeAsync()`.</span></span> <span data-ttu-id="abae9-128">當子類別繼承實作為的基類時，它會封裝常見的非同步清除作業 <xref:System.IAsyncDisposable> 。</span><span class="sxs-lookup"><span data-stu-id="abae9-128">It encapsulates the common asynchronous cleanup operations when a subclass inherits a base class that is an implementation of <xref:System.IAsyncDisposable>.</span></span> <span data-ttu-id="abae9-129">`DisposeAsyncCore()`方法 `virtual` 可讓衍生類別在其覆寫中定義額外的清除。</span><span class="sxs-lookup"><span data-stu-id="abae9-129">The `DisposeAsyncCore()` method is `virtual` so that derived classes can define additional cleanup in their overrides.</span></span>

> [!TIP]
> <span data-ttu-id="abae9-130">如果的實作為 <xref:System.IAsyncDisposable> `sealed` ，就 `DisposeAsyncCore()` 不需要方法，而非同步清除可以直接在方法中執行 <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="abae9-130">If an implementation of <xref:System.IAsyncDisposable> is `sealed`, the `DisposeAsyncCore()` method is not needed, and the asynchronous cleanup can be performed directly in the <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> method.</span></span>

## <a name="implement-the-async-dispose-pattern"></a><span data-ttu-id="abae9-131">執行非同步處置模式</span><span class="sxs-lookup"><span data-stu-id="abae9-131">Implement the async dispose pattern</span></span>

<span data-ttu-id="abae9-132">所有非密封類別都應該視為可能的基類，因為它們可以被繼承。</span><span class="sxs-lookup"><span data-stu-id="abae9-132">All non-sealed classes should be considered a potential base class, because they could be inherited.</span></span> <span data-ttu-id="abae9-133">如果您針對任何可能的基類執行非同步處置模式，則必須提供 `protected virtual ValueTask DisposeAsyncCore()` 方法。</span><span class="sxs-lookup"><span data-stu-id="abae9-133">If you implement the async dispose pattern for any potential base class, you must provide the `protected virtual ValueTask DisposeAsyncCore()` method.</span></span> <span data-ttu-id="abae9-134">以下是使用的非同步處置模式的範例執行 <xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="abae9-134">Here is an example implementation of the async dispose pattern that uses a <xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType>.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/disposeasync.cs":::

<span data-ttu-id="abae9-135">上述範例使用 <xref:System.Text.Json.Utf8JsonWriter> 。</span><span class="sxs-lookup"><span data-stu-id="abae9-135">The preceding example uses the <xref:System.Text.Json.Utf8JsonWriter>.</span></span> <span data-ttu-id="abae9-136">如需的詳細資訊 `System.Text.Json` ，請參閱 [如何從 Newtonsoft.Js移至 System.Text.Js](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md)。</span><span class="sxs-lookup"><span data-stu-id="abae9-136">For more information about `System.Text.Json`, see [How to migrate from Newtonsoft.Json to System.Text.Json](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

## <a name="implement-both-dispose-and-async-dispose-patterns"></a><span data-ttu-id="abae9-137">同時執行 dispose 和 async 處置模式</span><span class="sxs-lookup"><span data-stu-id="abae9-137">Implement both dispose and async dispose patterns</span></span>

<span data-ttu-id="abae9-138">您可能需要同時執行 <xref:System.IDisposable> 和 <xref:System.IAsyncDisposable> 介面，特別是當您的類別範圍包含這些實值的實例時。</span><span class="sxs-lookup"><span data-stu-id="abae9-138">You may need to implement both the <xref:System.IDisposable> and <xref:System.IAsyncDisposable> interfaces, especially when your class scope contains instances of these implementations.</span></span> <span data-ttu-id="abae9-139">這麼做可確保您可以適當地串聯清除呼叫。</span><span class="sxs-lookup"><span data-stu-id="abae9-139">Doing so ensures that you can properly cascade clean up calls.</span></span> <span data-ttu-id="abae9-140">以下是範例類別，可同時執行兩個介面，並示範適當的清除指引。</span><span class="sxs-lookup"><span data-stu-id="abae9-140">Here is an example class that implements both interfaces and demonstrates the proper guidance for cleanup.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/dispose-and-disposeasync.cs":::

<span data-ttu-id="abae9-141"><xref:System.IDisposable.Dispose?displayProperty=nameWithType>和實 <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> 作為簡單的未定案程式碼。</span><span class="sxs-lookup"><span data-stu-id="abae9-141">The <xref:System.IDisposable.Dispose?displayProperty=nameWithType> and <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> implementations are both simple boilerplate code.</span></span>

<span data-ttu-id="abae9-142">在多載 `Dispose(bool)` 方法中， <xref:System.IDisposable> 如果實例不是，則會有條件地處置實例 `null` 。</span><span class="sxs-lookup"><span data-stu-id="abae9-142">In the `Dispose(bool)` overload method, the <xref:System.IDisposable> instance is conditionally disposed of if it is not `null`.</span></span> <span data-ttu-id="abae9-143"><xref:System.IAsyncDisposable>實例會轉換成 <xref:System.IDisposable> ，如果也不是，則也 `null` 會處置它。</span><span class="sxs-lookup"><span data-stu-id="abae9-143">The <xref:System.IAsyncDisposable> instance is cast as <xref:System.IDisposable>, and if it is also not `null`, it is disposed of as well.</span></span> <span data-ttu-id="abae9-144">這兩個實例都會指派給 `null` 。</span><span class="sxs-lookup"><span data-stu-id="abae9-144">Both instances are then assigned to `null`.</span></span>

<span data-ttu-id="abae9-145">使用 `DisposeAsyncCore()` 方法時，會遵循相同的邏輯方法。</span><span class="sxs-lookup"><span data-stu-id="abae9-145">With the `DisposeAsyncCore()` method, the same logical approach is followed.</span></span> <span data-ttu-id="abae9-146">如果 <xref:System.IAsyncDisposable> 實例不是 `null` ，則會等待其對進行的呼叫 `DisposeAsync().ConfigureAwait(false)` 。</span><span class="sxs-lookup"><span data-stu-id="abae9-146">If the <xref:System.IAsyncDisposable> instance is not `null`, its call to `DisposeAsync().ConfigureAwait(false)` is awaited.</span></span> <span data-ttu-id="abae9-147">如果 <xref:System.IDisposable> 實例也是的實作為 <xref:System.IAsyncDisposable> ，它也會以非同步方式處置。</span><span class="sxs-lookup"><span data-stu-id="abae9-147">If the <xref:System.IDisposable> instance is also an implementation of <xref:System.IAsyncDisposable>, it's also disposed of asynchronously.</span></span> <span data-ttu-id="abae9-148">這兩個實例都會指派給 `null` 。</span><span class="sxs-lookup"><span data-stu-id="abae9-148">Both instances are then assigned to `null`.</span></span>

## <a name="using-async-disposable"></a><span data-ttu-id="abae9-149">使用非同步可處置</span><span class="sxs-lookup"><span data-stu-id="abae9-149">Using async disposable</span></span>

<span data-ttu-id="abae9-150">若要適當地使用可執行介面的物件 <xref:System.IAsyncDisposable> ，您可以使用 [await](../../csharp/language-reference/operators/await.md) 並一起 [使用](../../csharp/language-reference/keywords/using-statement.md) 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="abae9-150">To properly consume an object that implements the <xref:System.IAsyncDisposable> interface, you use the [await](../../csharp/language-reference/operators/await.md) and [using](../../csharp/language-reference/keywords/using-statement.md) keywords together.</span></span> <span data-ttu-id="abae9-151">請考慮下列範例，其中 `ExampleAsyncDisposable` 類別會具現化，然後包裝在 `await using` 語句中。</span><span class="sxs-lookup"><span data-stu-id="abae9-151">Consider the following example, where the `ExampleAsyncDisposable` class is instantiated and then wrapped in an `await using` statement.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/proper-await-using.cs":::

> [!IMPORTANT]
> <span data-ttu-id="abae9-152">使用 <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)> 介面的擴充方法 <xref:System.IAsyncDisposable> ，設定如何在其原始內容或排程器上封送處理工作的接續。</span><span class="sxs-lookup"><span data-stu-id="abae9-152">Use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)> extension method of the <xref:System.IAsyncDisposable> interface to configure how the continuation of the task is marshalled on its original context or scheduler.</span></span> <span data-ttu-id="abae9-153">如需的詳細資訊 `ConfigureAwait` ，請參閱 [ConfigureAwait 常見問題](https://devblogs.microsoft.com/dotnet/configureawait-faq/)。</span><span class="sxs-lookup"><span data-stu-id="abae9-153">For more information on `ConfigureAwait`, see [ConfigureAwait FAQ](https://devblogs.microsoft.com/dotnet/configureawait-faq/).</span></span>

<span data-ttu-id="abae9-154">在不需要使用的情況下 `ConfigureAwait` ， `await using` 可以簡化語句，如下所示：</span><span class="sxs-lookup"><span data-stu-id="abae9-154">For situations where the usage of `ConfigureAwait` is not needed, the `await using` statement could be simplified as follows:</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-non-configureawait.cs":::

<span data-ttu-id="abae9-155">此外，它也可以撰寫成使用 [using](../../csharp/whats-new/csharp-8.md#using-declarations)宣告的隱含範圍設定。</span><span class="sxs-lookup"><span data-stu-id="abae9-155">Furthermore, it could be written to use the implicit scoping of a [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations).</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-declaration.cs":::

## <a name="stacked-usings"></a><span data-ttu-id="abae9-156">堆疊 using</span><span class="sxs-lookup"><span data-stu-id="abae9-156">Stacked usings</span></span>

<span data-ttu-id="abae9-157">在您建立並使用多個可執行檔物件的情況下 <xref:System.IAsyncDisposable> ，堆疊 `await using` 語句可能 <xref:System.Threading.Tasks.ValueTask.ConfigureAwait%2A> 會妨礙 <xref:System.IAsyncDisposable.DisposeAsync> 不當條件中的呼叫。</span><span class="sxs-lookup"><span data-stu-id="abae9-157">In situations where you create and use multiple objects that implement <xref:System.IAsyncDisposable>, it's possible that stacking `await using` statements with <xref:System.Threading.Tasks.ValueTask.ConfigureAwait%2A> could prevent calls to <xref:System.IAsyncDisposable.DisposeAsync> in errant conditions.</span></span> <span data-ttu-id="abae9-158">為確保 <xref:System.IAsyncDisposable.DisposeAsync> 一律會呼叫，您應該避免堆疊。</span><span class="sxs-lookup"><span data-stu-id="abae9-158">To ensure that <xref:System.IAsyncDisposable.DisposeAsync> is always called, you should avoid stacking.</span></span> <span data-ttu-id="abae9-159">下列三個程式碼範例會顯示可接受的模式。</span><span class="sxs-lookup"><span data-stu-id="abae9-159">The following three code examples show acceptable patterns to use instead.</span></span>

### <a name="acceptable-pattern-one"></a><span data-ttu-id="abae9-160">可接受的模式一</span><span class="sxs-lookup"><span data-stu-id="abae9-160">Acceptable pattern one</span></span>

:::code language="csharp" id="one" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/stacked-await-usings.cs":::

<span data-ttu-id="abae9-161">在上述範例中，每個非同步清除作業都會明確限定在 `await using` 區塊下。</span><span class="sxs-lookup"><span data-stu-id="abae9-161">In the preceding example, each asynchronous clean up operation is explicitly scoped under the `await using` block.</span></span> <span data-ttu-id="abae9-162">外部範圍是由設定其括弧括住的方式來定義，如此 `objOne` `objTwo` `objTwo` 一來，就會先加以處置，然後再進行 `objOne` 。</span><span class="sxs-lookup"><span data-stu-id="abae9-162">The outer scope is defined by how `objOne` sets its braces, enclosing `objTwo`, as such `objTwo` is disposed first, followed by `objOne`.</span></span> <span data-ttu-id="abae9-163">這兩個實例都有等候的 `IAsyncDisposable` <xref:System.IAsyncDisposable.DisposeAsync> 方法，因此執行其非同步清除作業。</span><span class="sxs-lookup"><span data-stu-id="abae9-163">Both `IAsyncDisposable` instances have there <xref:System.IAsyncDisposable.DisposeAsync> methods awaited, thus performing its asynchronous clean up operation.</span></span> <span data-ttu-id="abae9-164">呼叫是嵌套的，而不是堆疊。</span><span class="sxs-lookup"><span data-stu-id="abae9-164">The calls are nested, not stacked.</span></span>

### <a name="acceptable-pattern-two"></a><span data-ttu-id="abae9-165">可接受的模式二</span><span class="sxs-lookup"><span data-stu-id="abae9-165">Acceptable pattern two</span></span>

:::code language="csharp" id="two" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/stacked-await-usings.cs":::

<span data-ttu-id="abae9-166">在上述範例中，每個非同步清除作業都會明確限定在 `await using` 區塊下。</span><span class="sxs-lookup"><span data-stu-id="abae9-166">In the preceding example, each asynchronous clean up operation is explicitly scoped under the `await using` block.</span></span> <span data-ttu-id="abae9-167">在每個區塊結束時，對應的 `IAsyncDisposable` 實例會 <xref:System.IAsyncDisposable.DisposeAsync> 等待其方法，藉此執行其非同步清除作業。</span><span class="sxs-lookup"><span data-stu-id="abae9-167">At the end of each block, the corresponding `IAsyncDisposable` instance has its <xref:System.IAsyncDisposable.DisposeAsync> method awaited, thus performing its asynchronous clean up operation.</span></span> <span data-ttu-id="abae9-168">這些呼叫是連續的，不會堆疊。</span><span class="sxs-lookup"><span data-stu-id="abae9-168">The calls are sequential, not stacked.</span></span> <span data-ttu-id="abae9-169">在此案例中 `objOne` ，會先處置，然後 `objTwo` 處置。</span><span class="sxs-lookup"><span data-stu-id="abae9-169">In this scenario `objOne` is disposed first, then `objTwo` is disposed.</span></span>

### <a name="acceptable-pattern-three"></a><span data-ttu-id="abae9-170">可接受的模式三</span><span class="sxs-lookup"><span data-stu-id="abae9-170">Acceptable pattern three</span></span>

:::code language="csharp" id="three" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/stacked-await-usings.cs":::

<span data-ttu-id="abae9-171">在上述範例中，每個非同步清除作業都會以隱含的範圍使用包含的方法主體。</span><span class="sxs-lookup"><span data-stu-id="abae9-171">In the preceding example, each asynchronous clean up operation is implicitly scoped with the containing method body.</span></span> <span data-ttu-id="abae9-172">在封閉區塊的結尾， `IAsyncDisposable` 實例會執行其非同步清除作業。</span><span class="sxs-lookup"><span data-stu-id="abae9-172">At the end of the enclosing block, the `IAsyncDisposable` instances perform their asynchronous clean up operations.</span></span> <span data-ttu-id="abae9-173">這會以與其宣告的相反循序執行，這表示 `objTwo` 會在之前處置 `objOne` 。</span><span class="sxs-lookup"><span data-stu-id="abae9-173">This runs in reverse order from which they were declared, meaning that `objTwo` is disposed before `objOne`.</span></span>

### <a name="unacceptable-pattern"></a><span data-ttu-id="abae9-174">無法接受的模式</span><span class="sxs-lookup"><span data-stu-id="abae9-174">Unacceptable pattern</span></span>

<span data-ttu-id="abae9-175">如果從函式擲回例外狀況 `AnotherAsyncDisposable` ，則 `objOne` 無法正確處置：</span><span class="sxs-lookup"><span data-stu-id="abae9-175">If an exception is thrown from the `AnotherAsyncDisposable` constructor, then `objOne` does not get properly disposed:</span></span>

:::code language="csharp" id="dontdothis" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/stacked-await-usings.cs":::

> [!TIP]
> <span data-ttu-id="abae9-176">請避免此模式，因為它可能會導致非預期的行為。</span><span class="sxs-lookup"><span data-stu-id="abae9-176">Avoid this pattern as it could lead to unexpected behavior.</span></span>

## <a name="see-also"></a><span data-ttu-id="abae9-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="abae9-177">See also</span></span>

- <xref:System.IAsyncDisposable>
- <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)>
