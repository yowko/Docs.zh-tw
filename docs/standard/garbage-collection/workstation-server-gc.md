---
title: '工作站與伺服器垃圾收集 (GC) '
description: 瞭解 .NET 中的工作站和伺服器垃圾收集。
ms.date: 04/21/2020
helpviewer_keywords:
- garbage collection, workstation
- garbage collection, server
- workstation garbage collection
- server garbage collection
ms.openlocfilehash: 640b5f42c1f841c2537284e4721e827248e3d300
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2020
ms.locfileid: "87917005"
---
# <a name="workstation-and-server-garbage-collection"></a>工作站和伺服器記憶體回收

記憶體回收行程會自行調整而且可在各種案例中運作。 不過，您可以根據工作負載的特性來[設定垃圾收集的類型](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection)。 CLR 會提供下列記憶體回收類型：

- 工作站垃圾收集 (GC) ，這是針對用戶端應用程式所設計。 這是獨立應用程式的預設 GC 類別。 例如，針對裝載的應用程式（由 ASP.NET 所主控），主機會決定預設的 GC 類別。

  工作站記憶體回收可能是並行或非並行的。 並行 (或*背景*) 垃圾收集可讓受控執行緒在垃圾收集期間繼續作業。 [背景垃圾收集](background-gc.md)會取代 .NET Framework 4 和更新版本中的[並行垃圾收集](background-gc.md#concurrent-garbage-collection)。

- 伺服器記憶體回收，適用於需要高輸送量和延展性的伺服器應用程式。

  - 在 .NET Core 中，伺服器垃圾收集可以是非並行或背景。

  - 在 .NET Framework 4.5 和更新版本中，伺服器垃圾收集可以是非並行或背景。 在 .NET Framework 4 和舊版中，伺服器垃圾收集為非並行的。

下圖顯示在伺服器上執行垃圾收集的專用線程：

![伺服器記憶體回收執行緒](media/gc-server.png)

## <a name="performance-considerations"></a>效能考量

### <a name="workstation-gc"></a>工作站 GC

以下是工作站記憶體回收的執行緒和效能考量：

- 此回收會針對觸發記憶體回收的使用者執行緒進行，而且維持相同的優先權。 因為使用者執行緒通常會以一般優先權執行，所以記憶體回收行程 (在一般優先權執行緒上執行) 必須與其他執行緒爭用 CPU 時間。 在伺服器或工作站垃圾收集上，不會暫停執行機器碼的 (執行緒。 ) 

- 工作站垃圾收集一律會在只有一個處理器的電腦上使用，不論[設定](../../core/run-time-config/garbage-collector.md#workstation-vs-server)為何。

### <a name="server-gc"></a>伺服器 GC

以下是伺服器記憶體回收的執行緒和效能考量：

- 此回收會針對以 `THREAD_PRIORITY_HIGHEST` 優先權層級執行的多個專屬執行緒進行。

- 執行記憶體回收的堆積和專屬執行緒是針對每個 CPU 提供的，而且這些堆積會同時回收。 每個堆積都包含小型物件堆積和大型物件堆積，而且所有堆積都可由使用者程式碼存取。 不同堆積上的物件可以彼此參考。

- 因為多個記憶體回收執行緒會一起運作，所以就相同大小堆積而言，伺服器記憶體回收的速度比工作站記憶體回收的速度要快。

- 伺服器記憶體回收通常具有較大的區段。 不過，這只是一般化：區段大小是特定執行，而且可能會變更。 請不要在調整應用程式時，假設垃圾收集行程所配置的區段大小。

- 伺服器記憶體回收可能會耗用大量資源。 例如，假設有12個處理常式在具有四個處理器的電腦上執行伺服器 GC。 如果所有處理常式都是同時收集垃圾，它們會互相干擾，因為同一個處理器上有12個執行緒排程。 如果處理常式是作用中的，最好不要讓它們全部使用伺服器 GC。

如果您執行的是數百個應用程式實例，請考慮使用已停用並行垃圾收集的工作站垃圾收集。 這樣會產生較少的內容切換，因此可能會改善效能。

## <a name="see-also"></a>另請參閱

- [背景垃圾收集](background-gc.md)
- [用於垃圾收集的執行時間設定選項](../../core/run-time-config/garbage-collector.md)
