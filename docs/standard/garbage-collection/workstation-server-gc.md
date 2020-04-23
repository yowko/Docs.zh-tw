---
title: 工作站與伺服器垃圾回收 (GC)
description: 在 .NET 中瞭解工作站和伺服器垃圾回收。
ms.date: 04/21/2020
helpviewer_keywords:
- garbage collection, workstation
- garbage collection, server
- workstation garbage collection
- server garbage collection
ms.openlocfilehash: 6b8e5f6802e5d44669b95d43d4e897fa4a418512
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82103552"
---
# <a name="workstation-and-server-garbage-collection"></a>工作站和伺服器記憶體回收

記憶體回收行程會自行調整而且可在各種案例中運作。 但是,您可以根據工作負載的特徵[設定垃圾回收的類型](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection)。 CLR 會提供下列記憶體回收類型：

- 工作站垃圾回收 (GC),專為用戶端應用設計。 它是獨立應用的預設 GC 風格。 對於託管應用(例如,由ASP.NET託管的應用,主機確定預設 GC 風格。

  工作站記憶體回收可能是並行或非並行的。 併發 (或*後台*) 垃圾回收使託管線程能夠在垃圾回收期間繼續操作。 [後臺垃圾資源](background-gc.md)將取代 .NET 框架 4 和更高版本中[的併發垃圾回收](background-gc.md#concurrent-garbage-collection)。

- 伺服器記憶體回收，適用於需要高輸送量和延展性的伺服器應用程式。

  - 在 .NET Core 中,伺服器垃圾回收可以是非併發或後台。

  - 在 .NET 框架 4.5 和更高版本中,伺服器垃圾回收可以是非併發或後臺。 在 .NET 框架 4 和早期版本中,伺服器垃圾回收是非併發的。

下圖顯示了在伺服器上執行垃圾回收的專用線程:

![伺服器記憶體回收執行緒](./media/gc-server.png)

## <a name="performance-considerations"></a>效能考量

### <a name="workstation-gc"></a>工作站 GC

以下是工作站記憶體回收的執行緒和效能考量：

- 此回收會針對觸發記憶體回收的使用者執行緒進行，而且維持相同的優先權。 因為使用者執行緒通常會以一般優先權執行，所以記憶體回收行程 (在一般優先權執行緒上執行) 必須與其他執行緒爭用 CPU 時間。 (運行本機代碼的線程不會在伺服器或工作站垃圾回收上掛起。

- 工作站垃圾資源的資源可以用於只有一個處理器的電腦,而不考慮[設定設定](../../core/run-time-config/garbage-collector.md#systemgcservercomplus_gcserver)。

### <a name="server-gc"></a>伺服器 GC

以下是伺服器記憶體回收的執行緒和效能考量：

- 此回收會針對以 `THREAD_PRIORITY_HIGHEST` 優先權層級執行的多個專屬執行緒進行。

- 執行記憶體回收的堆積和專屬執行緒是針對每個 CPU 提供的，而且這些堆積會同時回收。 每個堆積都包含小型物件堆積和大型物件堆積，而且所有堆積都可由使用者程式碼存取。 不同堆積上的物件可以彼此參考。

- 因為多個記憶體回收執行緒會一起運作，所以就相同大小堆積而言，伺服器記憶體回收的速度比工作站記憶體回收的速度要快。

- 伺服器記憶體回收通常具有較大的區段。 但是,這隻是一個概括:段大小特定於實現,可能會發生變化。 調整應用時,不要對垃圾回收器分配的段大小進行假設。

- 伺服器記憶體回收可能會耗用大量資源。 例如,假設有 12 個程序使用伺服器 GC 運行在具有四個處理器的電腦上。 如果所有進程都同時收集垃圾,它們就會相互干擾,因為同一處理器上將安排 12 個線程。 如果進程處於活動狀態,則讓所有進程都使用伺服器 GC 不是個好主意。

如果您正在運行應用程式的數百個實例,請考慮使用禁用併發垃圾回收的工作站垃圾回收。 這樣會產生較少的內容切換，因此可能會改善效能。

## <a name="see-also"></a>另請參閱

- [後臺垃圾回收](background-gc.md)
- [垃圾資源回收的執行時設定選項](../../core/run-time-config/garbage-collector.md)
