---
title: 清除 Unmanaged 資源
description: 瞭解如何清除未由 .NET 垃圾收集行程處理的非受控資源，例如檔案、windows、& 網路或資料庫連接。
ms.date: 05/13/2020
helpviewer_keywords:
- Close method
- Dispose method
- garbage collector
- garbage collection, unmanaged resources
- cleanup operations
- explicit cleanups
- unmanaged resource cleanup
- Finalize method
ms.assetid: a17b0066-71c2-4ba4-9822-8e19332fc213
ms.openlocfilehash: edfb01411df3d974073a397a20f58acdcd8521f3
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94827499"
---
# <a name="cleaning-up-unmanaged-resources"></a>清除 Unmanaged 資源

針對您的應用程式所建立的大部分物件，您可以依賴 [.net 垃圾收集](index.md) 行程來處理記憶體管理。 但是，當您建立包含非受控資源的物件時，您必須在完成使用這些資源時，明確地釋放這些資源。 最常見的非受控資源類型是包裝作業系統資源的物件，例如檔案、windows、網路連接或資料庫連接。 雖然記憶體回收行程能夠追蹤封裝 Unmanaged 資源的物件存留期，但是它並不知道如何釋放和清除 Unmanaged 資源。

如果您的類型使用 Unmanaged 資源，則應該執行下列作業：

- 實作[處置模式](implementing-dispose.md)。 這需要您提供執行， <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 以啟用具決定性的非受控資源版本。 <xref:System.IDisposable.Dispose%2A>當物件 (及其使用的資源) 不再需要時，您的型別的取用者會呼叫。 <xref:System.IDisposable.Dispose%2A> 方法會立即釋放 Unmanaged 資源。

- 如果您的型別取用者忘記呼叫 <xref:System.IDisposable.Dispose%2A> ，請提供方法讓您的非受控資源釋出。 作法有二：

  - 使用安全控制代碼包裝您的 Unmanaged 資源。 這是建議使用的技巧。 安全控制碼衍生自 <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> 抽象類別，並包含健全的 <xref:System.Object.Finalize%2A> 方法。 當您使用安全控制代碼時，只要實作 <xref:System.IDisposable> 介面並且在 <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> 實作中呼叫安全控制代碼的 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 方法即可。 如果未呼叫 <xref:System.IDisposable.Dispose%2A> 方法，記憶體回收行程會自動呼叫安全控制代碼的完成項。

    —**或**-

  - 覆寫 <xref:System.Object.Finalize%2A?displayProperty=nameWithType> 方法。 最終處理可在類型消費者未呼叫 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 以決定性的方式處理 Unmanaged 資源時，進行非決定性的 Unmanaged 資源釋放。 藉由 [覆](../../csharp/programming-guide/classes-and-structs/destructors.md) 寫方法來定義完成項 <xref:System.Object.Finalize%2A?displayProperty=nameWithType> 。

  > [!WARNING]
  > 不過，因為物件完成可能是複雜且容易發生錯誤的作業，所以建議您使用安全控制碼，而不是提供您自己的完成項。

這樣類型的消費者就可以直接呼叫您的 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 實作來釋放 Unmanaged 資源所使用的記憶體。 當您正確實作 <xref:System.IDisposable.Dispose%2A> 方法時，安全控制代碼的 <xref:System.Object.Finalize%2A> 方法或是自有的 <xref:System.Object.Finalize%2A?displayProperty=nameWithType> 方法覆寫便會成為一種防護措施，可在未呼叫 <xref:System.IDisposable.Dispose%2A> 方法時清除資源。

## <a name="in-this-section"></a>本節內容

[執行 dispose 方法](implementing-dispose.md) 會描述如何執行處置模式來釋放非受控資源。

[使用可執行 `IDisposable` 的物件](using-objects.md)描述型別的取用者如何確保 <xref:System.IDisposable.Dispose%2A> 會呼叫其實作為。 我們建議使用 c # `using` (或 Visual Basic `Using`) 語句來這麼做。

## <a name="reference"></a>參考

| 類型/成員 | 說明 |
|--|--|
| <xref:System.IDisposable?displayProperty=nameWithType> | 定義用於釋放 Unmanaged 資源的 <xref:System.IDisposable.Dispose%2A> 方法。 |
| <xref:System.Object.Finalize%2A?displayProperty=nameWithType> | 提供的用途是在 <xref:System.IDisposable.Dispose%2A> 方法未釋放 Unmanaged 資源時，進行物件最終處理。 |
| <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> | 隱藏最終處理。 這個方法通常會從 `Dispose` 方法呼叫，以便防止執行完成項。 |
