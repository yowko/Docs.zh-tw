---
title: 後臺垃圾回收
description: 瞭解 .NET 中的後台垃圾回收,以及它在工作站和伺服器垃圾回收中有何不同。
ms.date: 04/21/2020
helpviewer_keywords:
- garbage collection, background
- background garbage collection
ms.openlocfilehash: dcb1d348e679e07646273b8fbc4ea29b44ee4974
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82103559"
---
# <a name="background-garbage-collection"></a>後臺垃圾回收

在後台垃圾回收 (GC) 中,臨時代 (0 和 1) 根據需要收集,而第 2 代的收集正在進行中。 後台垃圾回收在一個或多個專用線程上執行,具體取決於它是後台還是伺服器 GC,並且僅適用於第 2 代集合。

默認情況下啟用後台垃圾回收。 可以使用 .NET Framework 應用中的[gc併發](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)配置設置或 .NET Core 應用中[的 System.GC.併發](../../core/run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent)設定啟用或禁用它。

> [!NOTE]
> 後臺垃圾回收將替換[併發垃圾回收](#concurrent-garbage-collection),並在 .NET 框架 4 和更高版本中提供。 在 .NET 框架 4 中,它僅支援*工作站*垃圾回收。 從 .NET 框架 4.5 開始,後臺垃圾回收可用於*工作站*和*伺服器*垃圾回收。

在後台垃圾回收期間對臨時代的收集稱為*前景*垃圾回收。 進行前景記憶體回收時，所有 Managed 執行緒都會暫停。

當後台垃圾回收正在進行,並且您在第 0 代中分配了足夠的物件時,CLR 將執行第 0 代或第 1 代前臺垃圾回收。 專屬的背景記憶體回收執行緒會在經常安全點檢查，以便判斷是否存在前景記憶體回收的要求。 如果有，背景回收就會自行暫停，讓前景記憶體回收能夠進行。 前臺垃圾回收完成後,將恢復專用後台垃圾回收線程和用戶線程。

背景記憶體回收會移除並行記憶體回收所加諸的配置限制，因為暫時記憶體回收可能會在背景記憶體回收期間進行。 後台垃圾回收可以刪除臨時代中的死物件。 如果需要,它還可以在第 1 代垃圾回收期間展開堆。

## <a name="background-workstation-vs-server-gc"></a>背景工作站與伺服器 GC

從 .NET 框架 4.5 開始,後台垃圾回收可用於伺服器 GC。 後台 GC 是伺服器垃圾回收的預設模式。

後台伺服器垃圾回收功能與後台工作站垃圾回收類似,但有一些區別:

- 後台工作站垃圾回收使用一個專用後台垃圾回收線程,而後台伺服器垃圾回收使用多個線程。 通常,每個邏輯處理器都有一個專用線程。

- 與工作站後台垃圾回收線程不同,後台伺服器 GC 線程不會超時。

下圖顯示了在單獨的專用線程上執行的背景*工作站*垃圾回收:

![背景工作站記憶體回收](./media/fundamentals/background-workstation-garbage-collection.png)

下圖顯示了在單獨的專用線程上執行的背景*伺服器*垃圾回收:

![背景伺服器記憶體回收](./media/fundamentals/background-server-garbage-collection.png)

## <a name="concurrent-garbage-collection"></a>並行的記憶體回收

> [!TIP]
> 本節適用於：
>
> - .NET 框架 3.5 及更早版本用於工作站垃圾回收
> - .NET 框架 4 及更早版本用於伺服器垃圾回收
>
> 並行垃圾在更高版本中被後台垃圾回收替換。

在工作站或伺服器垃圾回收中,可以[啟用併發垃圾回收](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md),使線程與在收集的大部分持續時間內執行垃圾回收的專用線程同時運行。 此選項僅影響第 2 代中的垃圾回收;因此,此選項僅影響第 2 代中的垃圾回收。第 0 代和 1 始終是非併發的,因為它們完成得快。

並行記憶體回收會將回收期間的暫停降到最低，藉以加快互動式應用程式的回應速度。 當並行記憶體回收執行緒正在執行時，Managed 執行緒幾乎可以繼續執行。 這會在記憶體回收進行時縮短暫停時間。

並行記憶體回收會針對專屬執行緒執行。 默認情況下,CLR 運行工作站垃圾回收,並在單處理器和多處理器計算機上啟用併發垃圾回收。

下列圖例顯示在分開的專屬執行緒上執行的並行記憶體回收。

![並行記憶體回收執行緒](./media/gc-concurrent.png)

## <a name="see-also"></a>另請參閱

- [工作站和伺服器記憶體回收](workstation-server-gc.md)
- [垃圾資源回收的執行時設定選項](../../core/run-time-config/garbage-collector.md)
