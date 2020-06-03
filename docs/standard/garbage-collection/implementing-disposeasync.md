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
# <a name="implement-a-disposeasync-method"></a>執行 DisposeAsync 方法

<xref:System.IAsyncDisposable?displayProperty=nameWithType>介面是在 c # 8.0 中引進。 <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType>當您需要執行資源清理時，您可以實作為方法，就像您在實作為[處置方法](implementing-dispose.md)時所做的一樣。 不過，其中一個主要差異在於，此實作為允許非同步清除作業。 <xref:System.IAsyncDisposable.DisposeAsync> <xref:System.Threading.Tasks.ValueTask> 會傳回表示非同步處置作業的。

通常在執行 <xref:System.IAsyncDisposable> 介面時，類別也會執行 <xref:System.IDisposable> 介面。 介面的良好執行模式 <xref:System.IAsyncDisposable> 是針對同步或非同步處置進行準備。 所有執行 dispose 模式的指導方針都適用于非同步執行。 本文假設您已經熟悉如何[執行 Dispose 方法](implementing-dispose.md)。

## <a name="disposeasync-and-disposeasynccore"></a>DisposeAsync （）和 DisposeAsyncCore （）

介面會宣告 <xref:System.IAsyncDisposable> 單一無參數方法 <xref:System.IAsyncDisposable.DisposeAsync> 。 任何非密封的類別都應該具有另一個也會傳回 `DisposeAsyncCore()` 的方法 <xref:System.Threading.Tasks.ValueTask> 。

- 沒有 `public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> 參數的執行。
- 其簽章 `protected virtual ValueTask DisposeAsyncCore()` 為的方法：

```csharp
protected virtual ValueTask DisposeAsyncCore()
{
}
```

`DisposeAsyncCore()`方法是 `virtual` 讓衍生類別可以在其覆寫中定義額外的清除。

### <a name="the-disposeasync-method"></a>DisposeAsync （）方法

`public`無參數 `DisposeAsync()` 方法會在語句中隱含地呼叫， `await using` 其目的是要釋放非受控資源、執行一般清除，並指出完成項（如果有的話）不需要執行。 釋放與 managed 物件相關聯的記憶體一律是[垃圾收集](index.md)行程的網域。 因此，它擁有標準實作：

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
> 相較于處置模式，非同步處置模式的一個主要差異在於，從到多載 <xref:System.IAsyncDisposable.DisposeAsync> 方法的呼叫 `Dispose(bool)` 會被指定 `false` 為引數。 <xref:System.IDisposable.Dispose?displayProperty=nameWithType>不過，在執行方法時， `true` 會改為傳遞。 這有助於確保與同步處置模式的功能相等，並進一步確保仍會叫用完成項程式碼路徑。 換句話說， `DisposeAsyncCore()` 方法會以非同步方式處置受管理的資源，因此您也不會想要同步處置它們。 因此，請呼叫， `Dispose(false)` 而不是 `Dispose(true)` 。

## <a name="implement-the-async-dispose-pattern"></a>執行非同步處置模式

所有非密封類別都應該視為潛在的基類，因為它們可以被繼承。 如果您針對任何可能的基類執行非同步處置模式，就必須提供 `protected virtual ValueTask DisposeAsyncCore()` 方法。 以下是使用的非同步處置模式的範例執行 <xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> 。

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/disposeasync.cs":::

先前的範例使用 <xref:System.Text.Json.Utf8JsonWriter> ，如需的詳細資訊 `System.Text.Json` ，請參閱[從 Newtonsoft 遷移至 system.object](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md)。

## <a name="using-async-disposable"></a>使用非同步可處置

若要適當地取用會執行介面的物件 <xref:System.IAsyncDisposable> ，您可以使用[await](../../csharp/language-reference/operators/await.md)，並搭配[使用](../../csharp/language-reference/keywords/using.md)關鍵字。 請考慮下列範例，其中 `ExampleAsyncDisposable` 類別會具現化，然後包裝在 `await using` 語句中。

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/proper-await-using.cs":::

> [!IMPORTANT]
> 使用 <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)> 介面的擴充方法 <xref:System.IAsyncDisposable> ，設定工作的接續在其原始內容或排程器上的封送處理方式。 如需的詳細資訊 `ConfigureAwait` ，請參閱[ConfigureAwait 常見問題](https://devblogs.microsoft.com/dotnet/configureawait-faq/)。

在不需要使用的情況下 `ConfigureAwait` ， `await using` 可以簡化語句，如下所示：

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-non-configureawait.cs":::

此外，它也可以撰寫成使用[using](../../csharp/whats-new/csharp-8.md#using-declarations)宣告的隱含範圍。

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-declaration.cs":::

## <a name="stacked-usings"></a>堆疊 using

在您建立和使用多個執行的物件的情況下 <xref:System.IAsyncDisposable> ， `using` 不當條件中的堆疊語句可能會防止對的呼叫 <xref:System.IAsyncDisposable.DisposeAsync> 。 為了協助避免潛在的顧慮，您應該避免堆疊，並改為遵循此範例模式：

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/stacked-await-usings.cs":::

## <a name="see-also"></a>另請參閱

- <xref:System.IAsyncDisposable>
- <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)>
