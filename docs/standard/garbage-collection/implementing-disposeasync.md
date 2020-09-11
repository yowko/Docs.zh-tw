---
title: 實作 DisposeAsync 方法
description: 瞭解如何執行 DisposeAsync 和 DisposeAsyncCore 方法，以執行非同步資源清除。
author: IEvangelist
ms.author: dapine
ms.date: 09/10/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
helpviewer_keywords:
- DisposeAsync method
- garbage collection, DisposeAsync method
ms.openlocfilehash: 88adf9e484baa0e65e2ff093b4649cf35b8c86dc
ms.sourcegitcommit: 6d4ee46871deb9ea1e45bb5f3784474e240bbc26
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2020
ms.locfileid: "90022905"
---
# <a name="implement-a-disposeasync-method"></a><span data-ttu-id="1a3e0-103">實作 DisposeAsync 方法</span><span class="sxs-lookup"><span data-stu-id="1a3e0-103">Implement a DisposeAsync method</span></span>

<span data-ttu-id="1a3e0-104"><xref:System.IAsyncDisposable?displayProperty=nameWithType>介面是在 c # 8.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-104">The <xref:System.IAsyncDisposable?displayProperty=nameWithType> interface was introduced as part of C# 8.0.</span></span> <span data-ttu-id="1a3e0-105"><xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType>當您需要執行資源清除時，請執行方法，就像您在執行[Dispose 方法](implementing-dispose.md)時所做的一樣。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-105">You implement the <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> method when you need to perform resource cleanup, just as you would when [implementing a Dispose method](implementing-dispose.md).</span></span> <span data-ttu-id="1a3e0-106">但是，其中一個主要差異在於，這項實行可進行非同步清除作業。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-106">One of the key differences however, is that this implementation allows for asynchronous cleanup operations.</span></span> <span data-ttu-id="1a3e0-107"><xref:System.IAsyncDisposable.DisposeAsync> <xref:System.Threading.Tasks.ValueTask> 會傳回代表非同步處置作業的。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-107">The <xref:System.IAsyncDisposable.DisposeAsync> returns a <xref:System.Threading.Tasks.ValueTask> that represents the asynchronous dispose operation.</span></span>

<span data-ttu-id="1a3e0-108">典型的情況是在實 <xref:System.IAsyncDisposable> 介面時，類別也會執行 <xref:System.IDisposable> 介面。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-108">It is typical when implementing the <xref:System.IAsyncDisposable> interface that classes will also implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="1a3e0-109">介面的良好執行模式 <xref:System.IAsyncDisposable> 是針對同步或非同步處置做好準備。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-109">A good implementation pattern of the <xref:System.IAsyncDisposable> interface is to be prepared for either synchronous, or asynchronous dispose.</span></span> <span data-ttu-id="1a3e0-110">所有執行處置模式的指導方針也適用于非同步執行。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-110">All of the guidance for implementing the dispose pattern also applies to the asynchronous implementation.</span></span> <span data-ttu-id="1a3e0-111">本文假設您已經熟悉如何 [執行 Dispose 方法](implementing-dispose.md)。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-111">This article assumes that you're already familiar with how to [implement a Dispose method](implementing-dispose.md).</span></span>

## <a name="disposeasync-and-disposeasynccore"></a><span data-ttu-id="1a3e0-112">DisposeAsync ( # A1 和 DisposeAsyncCore ( # A3</span><span class="sxs-lookup"><span data-stu-id="1a3e0-112">DisposeAsync() and DisposeAsyncCore()</span></span>

<span data-ttu-id="1a3e0-113">介面會宣告 <xref:System.IAsyncDisposable> 單一無參數方法 <xref:System.IAsyncDisposable.DisposeAsync> 。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-113">The <xref:System.IAsyncDisposable> interface declares a single parameterless method, <xref:System.IAsyncDisposable.DisposeAsync>.</span></span> <span data-ttu-id="1a3e0-114">任何非密封類別都應該有另一個 `DisposeAsyncCore()` 也會傳回的方法 <xref:System.Threading.Tasks.ValueTask> 。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-114">Any non-sealed class should have an additional `DisposeAsyncCore()` method that also returns a <xref:System.Threading.Tasks.ValueTask>.</span></span>

- <span data-ttu-id="1a3e0-115">沒有 `public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> 參數的實作為。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-115">A `public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> implementation that has no parameters.</span></span>
- <span data-ttu-id="1a3e0-116">其簽章 `protected virtual ValueTask DisposeAsyncCore()` 為的方法：</span><span class="sxs-lookup"><span data-stu-id="1a3e0-116">A `protected virtual ValueTask DisposeAsyncCore()` method whose signature is:</span></span>

  ```csharp
  protected virtual ValueTask DisposeAsyncCore()
  {
  }
  ```

### <a name="the-disposeasync-method"></a><span data-ttu-id="1a3e0-117">DisposeAsync ( # A1 方法</span><span class="sxs-lookup"><span data-stu-id="1a3e0-117">The DisposeAsync() method</span></span>

<span data-ttu-id="1a3e0-118">`public`無參數 `DisposeAsync()` 方法會以隱含方式在 `await using` 語句中呼叫，而其用途是釋放未受管理的資源、執行一般清除，以及指出完成項（如果有的話）不需要執行。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-118">The `public` parameterless `DisposeAsync()` method is called implicitly in an `await using` statement, and its purpose is to free unmanaged resources, perform general cleanup, and to indicate that the finalizer, if one is present, need not run.</span></span> <span data-ttu-id="1a3e0-119">釋放與受管理物件相關聯的記憶體一律是 [垃圾收集](index.md)行程的網域。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-119">Freeing the memory associated with a managed object is always the domain of the [garbage collector](index.md).</span></span> <span data-ttu-id="1a3e0-120">因此，它擁有標準實作：</span><span class="sxs-lookup"><span data-stu-id="1a3e0-120">Because of this, it has a standard implementation:</span></span>

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
> <span data-ttu-id="1a3e0-121">相較于處置模式，非同步處置模式中的一個主要差異是，從多載 <xref:System.IAsyncDisposable.DisposeAsync> 方法的呼叫 `Dispose(bool)` 會被指定 `false` 為引數。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-121">One primary difference in the async dispose pattern compared to the dispose pattern, is that the call from <xref:System.IAsyncDisposable.DisposeAsync> to the `Dispose(bool)` overload method is given `false` as an argument.</span></span> <span data-ttu-id="1a3e0-122"><xref:System.IDisposable.Dispose?displayProperty=nameWithType>不過，在執行方法時， `true` 會改為傳遞。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-122">When implementing the <xref:System.IDisposable.Dispose?displayProperty=nameWithType> method, however; `true` is passed instead.</span></span> <span data-ttu-id="1a3e0-123">這有助於確保與同步處置模式的功能性相等，並進一步確保仍會叫用完成項程式碼路徑。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-123">This helps ensure functional equivalence with the synchronous dispose pattern, and further ensures that finalizer code paths still get invoked.</span></span> <span data-ttu-id="1a3e0-124">換句話說，此 `DisposeAsyncCore()` 方法會以非同步方式處置受控資源，因此您也不想要以同步方式處置它們。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-124">In other words, the `DisposeAsyncCore()` method will dispose of managed resources asynchronously, so you don't want to dispose of them synchronously as well.</span></span> <span data-ttu-id="1a3e0-125">因此，請呼叫， `Dispose(false)` 而不是 `Dispose(true)` 。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-125">Therefore, call `Dispose(false)` instead of `Dispose(true)`.</span></span>

### <a name="the-disposeasynccore-method"></a><span data-ttu-id="1a3e0-126">DisposeAsyncCore ( # A1 方法</span><span class="sxs-lookup"><span data-stu-id="1a3e0-126">The DisposeAsyncCore() method</span></span>

<span data-ttu-id="1a3e0-127">`DisposeAsyncCore()`方法的目的是要執行 managed 資源的非同步清除，或對的串聯呼叫 `DisposeAsync()` 。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-127">The `DisposeAsyncCore()` method is intended to perform the asynchronous cleanup of managed resources or for cascading calls to `DisposeAsync()`.</span></span> <span data-ttu-id="1a3e0-128">當子類別繼承實作為的基類時，它會封裝常見的非同步清除作業 <xref:System.IAsyncDisposable> 。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-128">It encapsulates the common asynchronous cleanup operations when a subclass inherits a base class that is an implementation of <xref:System.IAsyncDisposable>.</span></span> <span data-ttu-id="1a3e0-129">`DisposeAsyncCore()`方法 `virtual` 可讓衍生類別在其覆寫中定義額外的清除。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-129">The `DisposeAsyncCore()` method is `virtual` so that derived classes can define additional cleanup in their overrides.</span></span>

> [!TIP]
> <span data-ttu-id="1a3e0-130">如果的實作為 <xref:System.IAsyncDisposable> `sealed` ，就 `DisposeAsyncCore()` 不需要方法，而非同步清除可以直接在方法中執行 <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-130">If an implementation of <xref:System.IAsyncDisposable> is `sealed`, the `DisposeAsyncCore()` method is not needed, and the asynchronous cleanup can be performed directly in the <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> method.</span></span>

## <a name="implement-the-async-dispose-pattern"></a><span data-ttu-id="1a3e0-131">執行非同步處置模式</span><span class="sxs-lookup"><span data-stu-id="1a3e0-131">Implement the async dispose pattern</span></span>

<span data-ttu-id="1a3e0-132">所有非密封類別都應該視為可能的基類，因為它們可以被繼承。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-132">All non-sealed classes should be considered a potential base class, because they could be inherited.</span></span> <span data-ttu-id="1a3e0-133">如果您針對任何可能的基類執行非同步處置模式，則必須提供 `protected virtual ValueTask DisposeAsyncCore()` 方法。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-133">If you implement the async dispose pattern for any potential base class, you must provide the `protected virtual ValueTask DisposeAsyncCore()` method.</span></span> <span data-ttu-id="1a3e0-134">以下是使用的非同步處置模式的範例執行 <xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-134">Here is an example implementation of the async dispose pattern that uses a <xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType>.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/disposeasync.cs":::

<span data-ttu-id="1a3e0-135">上述範例使用 <xref:System.Text.Json.Utf8JsonWriter> 。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-135">The preceding example uses the <xref:System.Text.Json.Utf8JsonWriter>.</span></span> <span data-ttu-id="1a3e0-136">如需的詳細資訊 `System.Text.Json` ，請參閱 [如何從 Newtonsoft.Js移至 System.Text.Js](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md)。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-136">For more information about `System.Text.Json`, see [How to migrate from Newtonsoft.Json to System.Text.Json](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

## <a name="implement-both-dispose-and-async-dispose-patterns"></a><span data-ttu-id="1a3e0-137">同時執行 dispose 和 async 處置模式</span><span class="sxs-lookup"><span data-stu-id="1a3e0-137">Implement both dispose and async dispose patterns</span></span>

<span data-ttu-id="1a3e0-138">您可能需要同時執行 <xref:System.IDisposable> 和 <xref:System.IAsyncDisposable> 介面，特別是當您的類別範圍包含這些實值的實例時。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-138">You may need to implement both the <xref:System.IDisposable> and <xref:System.IAsyncDisposable> interfaces, especially when your class scope contains instances of these implementations.</span></span> <span data-ttu-id="1a3e0-139">這麼做可確保您可以適當地串聯清除呼叫。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-139">Doing so ensures that you can properly cascade clean up calls.</span></span> <span data-ttu-id="1a3e0-140">以下是範例類別，可同時執行兩個介面，並示範適當的清除指引。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-140">Here is an example class that implements both interfaces and demonstrates the proper guidance for cleanup.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/dispose-and-disposeasync.cs":::

<span data-ttu-id="1a3e0-141"><xref:System.IDisposable.Dispose?displayProperty=nameWithType>和實 <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> 作為簡單的未定案程式碼。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-141">The <xref:System.IDisposable.Dispose?displayProperty=nameWithType> and <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> implementations are both simple boilerplate code.</span></span> <span data-ttu-id="1a3e0-142">`Dispose(bool)`和 `DisposeAsyncCore()` 方法一開始會先檢查是否 `_disposed` 為 `true` ，而且只會在它的時候執行 `false` 。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-142">The `Dispose(bool)` and `DisposeAsyncCore()` methods start by checking if `_disposed` is `true`, and will only run when it's `false`.</span></span>

<span data-ttu-id="1a3e0-143">在多載 `Dispose(bool)` 方法中， <xref:System.IDisposable> 如果實例不是，則會有條件地處置實例 `null` 。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-143">In the `Dispose(bool)` overload method, the <xref:System.IDisposable> instance is conditionally disposed of if it is not `null`.</span></span> <span data-ttu-id="1a3e0-144"><xref:System.IAsyncDisposable>實例會轉換為 <xref:System.IDisposable> ，而且如果也不會 `null` 處置它。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-144">The <xref:System.IAsyncDisposable> instance is casted as <xref:System.IDisposable>, and if it is also not `null` it is disposed of as well.</span></span> <span data-ttu-id="1a3e0-145">這兩個實例都會指派給 `null` 。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-145">Both instances are then assigned to `null`.</span></span>

<span data-ttu-id="1a3e0-146">使用 `DisposeAsyncCore()` 方法時，會遵循相同的邏輯方法。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-146">With the `DisposeAsyncCore()` method, the same logical approach is followed.</span></span> <span data-ttu-id="1a3e0-147">如果 <xref:System.IAsyncDisposable> 實例不是 `null` ，則會等待其對進行的呼叫 `DisposeAsync().ConfigureAwait(false)` 。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-147">If the <xref:System.IAsyncDisposable> instance is not `null`, its call to `DisposeAsync().ConfigureAwait(false)` is awaited.</span></span> <span data-ttu-id="1a3e0-148">如果 <xref:System.IDisposable> 實例也是的實作為 <xref:System.IAsyncDisposable> ，它也會以非同步方式處置。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-148">If the <xref:System.IDisposable> instance is also an implementation of <xref:System.IAsyncDisposable>, it's also disposed of asynchronously.</span></span> <span data-ttu-id="1a3e0-149">這兩個實例都會指派給 `null` 。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-149">Both instances are then assigned to `null`.</span></span>

## <a name="using-async-disposable"></a><span data-ttu-id="1a3e0-150">使用非同步可處置</span><span class="sxs-lookup"><span data-stu-id="1a3e0-150">Using async disposable</span></span>

<span data-ttu-id="1a3e0-151">若要適當地使用可執行介面的物件 <xref:System.IAsyncDisposable> ，您可以使用 [await](../../csharp/language-reference/operators/await.md)，同時 [使用](../../csharp/language-reference/keywords/using-statement.md) 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-151">To properly consume an object that implements the <xref:System.IAsyncDisposable> interface, you use the [await](../../csharp/language-reference/operators/await.md), and [using](../../csharp/language-reference/keywords/using-statement.md) keywords together.</span></span> <span data-ttu-id="1a3e0-152">請考慮下列範例，其中 `ExampleAsyncDisposable` 類別會具現化，然後包裝在 `await using` 語句中。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-152">Consider the following example, where the `ExampleAsyncDisposable` class is instantiated and then wrapped in an `await using` statement.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/proper-await-using.cs":::

> [!IMPORTANT]
> <span data-ttu-id="1a3e0-153">使用 <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)> 介面的擴充方法 <xref:System.IAsyncDisposable> ，設定如何在其原始內容或排程器上封送處理工作的接續。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-153">Use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)> extension method of the <xref:System.IAsyncDisposable> interface to configure how the continuation of the task is marshalled on its original context or scheduler.</span></span> <span data-ttu-id="1a3e0-154">如需的詳細資訊 `ConfigureAwait` ，請參閱 [ConfigureAwait 常見問題](https://devblogs.microsoft.com/dotnet/configureawait-faq/)。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-154">For more information on `ConfigureAwait`, see [ConfigureAwait FAQ](https://devblogs.microsoft.com/dotnet/configureawait-faq/).</span></span>

<span data-ttu-id="1a3e0-155">在不需要使用的情況下 `ConfigureAwait` ， `await using` 可以簡化語句，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1a3e0-155">For situations where the usage of `ConfigureAwait` is not needed, the `await using` statement could be simplified as follows:</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-non-configureawait.cs":::

<span data-ttu-id="1a3e0-156">此外，它也可以撰寫成使用 [using](../../csharp/whats-new/csharp-8.md#using-declarations)宣告的隱含範圍設定。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-156">Furthermore, it could be written to use the implicit scoping of a [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations).</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-declaration.cs":::

## <a name="stacked-usings"></a><span data-ttu-id="1a3e0-157">堆疊 using</span><span class="sxs-lookup"><span data-stu-id="1a3e0-157">Stacked usings</span></span>

<span data-ttu-id="1a3e0-158">在您建立並使用多個執行的物件的情況下 <xref:System.IAsyncDisposable> ， `using` 不當條件中的堆疊語句可能會妨礙的呼叫 <xref:System.IAsyncDisposable.DisposeAsync> 。</span><span class="sxs-lookup"><span data-stu-id="1a3e0-158">In situations where you create and use multiple objects that implement <xref:System.IAsyncDisposable>, it's possible that stacking `using` statements in errant conditions could prevent calls to <xref:System.IAsyncDisposable.DisposeAsync>.</span></span> <span data-ttu-id="1a3e0-159">為了協助防止潛在的問題，您應該避免堆疊，而改為遵循此範例模式：</span><span class="sxs-lookup"><span data-stu-id="1a3e0-159">In order to help prevent potential concern, you should avoid stacking, and instead follow this example pattern:</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/stacked-await-usings.cs":::

## <a name="see-also"></a><span data-ttu-id="1a3e0-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a3e0-160">See also</span></span>

- <xref:System.IAsyncDisposable>
- <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)>
