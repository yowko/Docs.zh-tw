---
title: 實作 DisposeAsync 方法
description: 瞭解如何執行 DisposeAsync 和 DisposeAsyncCore 方法，以執行非同步資源清除。
author: IEvangelist
ms.author: dapine
ms.date: 10/26/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
helpviewer_keywords:
- DisposeAsync method
- garbage collection, DisposeAsync method
ms.openlocfilehash: 5aa82c507c22a4795f39267ac8f435599fb9cd92
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687718"
---
# <a name="implement-a-disposeasync-method"></a>實作 DisposeAsync 方法

<xref:System.IAsyncDisposable?displayProperty=nameWithType>介面是在 c # 8.0 中引進。 <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType>當您需要執行資源清除時，請執行方法，就像您在執行[Dispose 方法](implementing-dispose.md)時所做的一樣。 但是，其中一個主要差異在於，這項實行可進行非同步清除作業。 <xref:System.IAsyncDisposable.DisposeAsync> <xref:System.Threading.Tasks.ValueTask> 會傳回代表非同步處置作業的。

典型的情況是在實 <xref:System.IAsyncDisposable> 介面時，類別也會執行 <xref:System.IDisposable> 介面。 介面的良好執行模式 <xref:System.IAsyncDisposable> 是針對同步或非同步處置做好準備。 所有執行處置模式的指導方針也適用于非同步執行。 本文假設您已經熟悉如何 [執行 Dispose 方法](implementing-dispose.md)。

## <a name="disposeasync-and-disposeasynccore"></a>DisposeAsync ( # A1 和 DisposeAsyncCore ( # A3

介面會宣告 <xref:System.IAsyncDisposable> 單一無參數方法 <xref:System.IAsyncDisposable.DisposeAsync> 。 任何非密封類別都應該有另一個 `DisposeAsyncCore()` 也會傳回的方法 <xref:System.Threading.Tasks.ValueTask> 。

- 沒有 `public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> 參數的實作為。
- 其簽章 `protected virtual ValueTask DisposeAsyncCore()` 為的方法：

  ```csharp
  protected virtual ValueTask DisposeAsyncCore()
  {
  }
  ```

### <a name="the-disposeasync-method"></a>DisposeAsync ( # A1 方法

`public`無參數 `DisposeAsync()` 方法會以隱含方式在 `await using` 語句中呼叫，而其用途是釋放未受管理的資源、執行一般清除，以及指出完成項（如果有的話）不需要執行。 釋放與受管理物件相關聯的記憶體一律是 [垃圾收集](index.md)行程的網域。 因此，它擁有標準實作：

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
> 相較于處置模式，非同步處置模式中的一個主要差異是，從多載 <xref:System.IAsyncDisposable.DisposeAsync> 方法的呼叫 `Dispose(bool)` 會被指定 `false` 為引數。 不過，在執行 <xref:System.IDisposable.Dispose?displayProperty=nameWithType> 方法時， `true` 會改為傳遞。 這有助於確保與同步處置模式的功能性相等，並進一步確保仍會叫用完成項程式碼路徑。 換句話說，此 `DisposeAsyncCore()` 方法會以非同步方式處置受控資源，因此您也不想要以同步方式處置它們。 因此，請呼叫， `Dispose(false)` 而不是 `Dispose(true)` 。

### <a name="the-disposeasynccore-method"></a>DisposeAsyncCore ( # A1 方法

`DisposeAsyncCore()`方法的目的是要執行 managed 資源的非同步清除，或對的串聯呼叫 `DisposeAsync()` 。 當子類別繼承實作為的基類時，它會封裝常見的非同步清除作業 <xref:System.IAsyncDisposable> 。 `DisposeAsyncCore()`方法 `virtual` 可讓衍生類別在其覆寫中定義額外的清除。

> [!TIP]
> 如果的實作為 <xref:System.IAsyncDisposable> `sealed` ，就 `DisposeAsyncCore()` 不需要方法，而非同步清除可以直接在方法中執行 <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> 。

## <a name="implement-the-async-dispose-pattern"></a>執行非同步處置模式

所有非密封類別都應該視為可能的基類，因為它們可以被繼承。 如果您針對任何可能的基類執行非同步處置模式，則必須提供 `protected virtual ValueTask DisposeAsyncCore()` 方法。 以下是使用的非同步處置模式的範例執行 <xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> 。

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/disposeasync.cs":::

上述範例使用 <xref:System.Text.Json.Utf8JsonWriter> 。 如需的詳細資訊 `System.Text.Json` ，請參閱 [如何從 Newtonsoft.Js移至 System.Text.Js](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md)。

## <a name="implement-both-dispose-and-async-dispose-patterns"></a>同時執行 dispose 和 async 處置模式

您可能需要同時執行 <xref:System.IDisposable> 和 <xref:System.IAsyncDisposable> 介面，特別是當您的類別範圍包含這些實值的實例時。 這麼做可確保您可以適當地串聯清除呼叫。 以下是範例類別，可同時執行兩個介面，並示範適當的清除指引。

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/dispose-and-disposeasync.cs":::

<xref:System.IDisposable.Dispose?displayProperty=nameWithType>和實 <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> 作為簡單的未定案程式碼。

在多載 `Dispose(bool)` 方法中， <xref:System.IDisposable> 如果實例不是，則會有條件地處置實例 `null` 。 <xref:System.IAsyncDisposable>實例會轉換成 <xref:System.IDisposable> ，如果也不是，則也 `null` 會處置它。 這兩個實例都會指派給 `null` 。

使用 `DisposeAsyncCore()` 方法時，會遵循相同的邏輯方法。 如果 <xref:System.IAsyncDisposable> 實例不是 `null` ，則會等待其對進行的呼叫 `DisposeAsync().ConfigureAwait(false)` 。 如果 <xref:System.IDisposable> 實例也是的實作為 <xref:System.IAsyncDisposable> ，它也會以非同步方式處置。 這兩個實例都會指派給 `null` 。

## <a name="using-async-disposable"></a>使用非同步可處置

若要適當地使用可執行介面的物件 <xref:System.IAsyncDisposable> ，您可以使用 [await](../../csharp/language-reference/operators/await.md) 並一起 [使用](../../csharp/language-reference/keywords/using-statement.md) 關鍵字。 請考慮下列範例，其中 `ExampleAsyncDisposable` 類別會具現化，然後包裝在 `await using` 語句中。

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/proper-await-using.cs":::

> [!IMPORTANT]
> 使用 <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)> 介面的擴充方法 <xref:System.IAsyncDisposable> ，設定如何在其原始內容或排程器上封送處理工作的接續。 如需的詳細資訊 `ConfigureAwait` ，請參閱 [ConfigureAwait 常見問題](https://devblogs.microsoft.com/dotnet/configureawait-faq/)。

在不需要使用的情況下 `ConfigureAwait` ， `await using` 可以簡化語句，如下所示：

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-non-configureawait.cs":::

此外，它也可以撰寫成使用 [using](../../csharp/whats-new/csharp-8.md#using-declarations)宣告的隱含範圍設定。

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-declaration.cs":::

## <a name="stacked-usings"></a>堆疊 using

在您建立並使用多個可執行檔物件的情況下 <xref:System.IAsyncDisposable> ，堆疊 `await using` 語句可能 <xref:System.Threading.Tasks.ValueTask.ConfigureAwait%2A> 會妨礙 <xref:System.IAsyncDisposable.DisposeAsync> 不當條件中的呼叫。 為確保 <xref:System.IAsyncDisposable.DisposeAsync> 一律會呼叫，您應該避免堆疊。 下列三個程式碼範例會顯示可接受的模式。

### <a name="acceptable-pattern-one"></a>可接受的模式一

:::code language="csharp" id="one" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/stacked-await-usings.cs":::

在上述範例中，每個非同步清除作業都會明確限定在 `await using` 區塊下。 外部範圍是由設定其括弧括住的方式來定義，如此 `objOne` `objTwo` `objTwo` 一來，就會先加以處置，然後再進行 `objOne` 。 這兩個實例都有等候的 `IAsyncDisposable` <xref:System.IAsyncDisposable.DisposeAsync> 方法，因此執行其非同步清除作業。 呼叫是嵌套的，而不是堆疊。

### <a name="acceptable-pattern-two"></a>可接受的模式二

:::code language="csharp" id="two" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/stacked-await-usings.cs":::

在上述範例中，每個非同步清除作業都會明確限定在 `await using` 區塊下。 在每個區塊結束時，對應的 `IAsyncDisposable` 實例會 <xref:System.IAsyncDisposable.DisposeAsync> 等待其方法，藉此執行其非同步清除作業。 這些呼叫是連續的，不會堆疊。 在此案例中 `objOne` ，會先處置，然後 `objTwo` 處置。

### <a name="acceptable-pattern-three"></a>可接受的模式三

:::code language="csharp" id="three" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/stacked-await-usings.cs":::

在上述範例中，每個非同步清除作業都會以隱含的範圍使用包含的方法主體。 在封閉區塊的結尾， `IAsyncDisposable` 實例會執行其非同步清除作業。 這會以與其宣告的相反循序執行，這表示 `objTwo` 會在之前處置 `objOne` 。

### <a name="unacceptable-pattern"></a>無法接受的模式

如果從函式擲回例外狀況 `AnotherAsyncDisposable` ，則 `objOne` 無法正確處置：

:::code language="csharp" id="dontdothis" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/stacked-await-usings.cs":::

> [!TIP]
> 請避免此模式，因為它可能會導致非預期的行為。

## <a name="see-also"></a>另請參閱

- <xref:System.IAsyncDisposable>
- <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)>
