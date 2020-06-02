---
title: 背景垃圾收集
description: 瞭解 .NET 中的背景垃圾收集，以及它在工作站和伺服器垃圾收集中的差異。
ms.date: 04/21/2020
helpviewer_keywords:
- garbage collection, background
- background garbage collection
ms.openlocfilehash: e2e25dcfff759d68087006b63544bf688798c029
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286076"
---
# <a name="background-garbage-collection"></a>背景垃圾收集

在背景垃圾收集（GC）中，當層代2的集合正在進行時，會視需要收集暫時層代（0和1）。 背景垃圾收集會在一或多個專用線程上執行，視其為背景或伺服器 GC 而定，而且只適用于層代2回收。

預設會啟用背景垃圾收集。 您可以使用 .NET Framework apps 中的[gcConcurrent](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)設定，或 .net Core 應用程式中的[system.object](../../core/run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent)設定來啟用或停用它。

> [!NOTE]
> 背景垃圾收集會取代[並行垃圾收集](#concurrent-garbage-collection)，並在 .NET Framework 4 和更新版本中提供。 在 .NET Framework 4 中，只有*工作站*垃圾收集才支援此功能。 從 .NET Framework 4.5 開始，背景垃圾收集適用于*工作站*和*伺服器*垃圾收集。

背景垃圾收集期間暫時層代的集合，稱為「*前景*垃圾收集」。 進行前景記憶體回收時，所有 Managed 執行緒都會暫停。

當背景垃圾收集正在進行中，而且您已在層代0中配置足夠的物件時，CLR 會執行層代0或第1代的前景垃圾收集。 專屬的背景記憶體回收執行緒會在經常安全點檢查，以便判斷是否存在前景記憶體回收的要求。 如果有，背景回收就會自行暫停，讓前景記憶體回收能夠進行。 前景垃圾收集完成之後，專用的背景垃圾收集執行緒和使用者執行緒就會繼續。

背景記憶體回收會移除並行記憶體回收所加諸的配置限制，因為暫時記憶體回收可能會在背景記憶體回收期間進行。 背景垃圾收集可以移除暫時層代中的無作用物件。 它也可以在層代1垃圾收集期間視需要擴充堆積。

## <a name="background-workstation-vs-server-gc"></a>背景工作站與伺服器 GC 的比較

從 .NET Framework 4.5 開始，會提供伺服器 GC 的背景垃圾收集。 背景 GC 是伺服器垃圾收集的預設模式。

背景伺服器垃圾收集的功能類似于背景工作站垃圾收集，但有一些差異：

- 背景工作站垃圾收集使用一個專用的背景垃圾收集執行緒，而背景伺服器垃圾收集則使用多個執行緒。 一般來說，每個邏輯處理器都有專用的執行緒。

- 不同于工作站背景垃圾收集執行緒，背景伺服器 GC 執行緒不會超時。

下圖顯示在另一個專用線程上執行的背景*工作站*垃圾收集：

![背景工作站記憶體回收](./media/fundamentals/background-workstation-garbage-collection.png)

下圖顯示在不同的專用線程上執行的背景*伺服器*垃圾收集：

![背景伺服器記憶體回收](./media/fundamentals/background-server-garbage-collection.png)

## <a name="concurrent-garbage-collection"></a>並行的記憶體回收

> [!TIP]
> 本節適用於：
>
> - 適用于工作站垃圾收集的 .NET Framework 3.5 和更早版本
> - .NET Framework 4 和更早版本進行伺服器垃圾收集
>
> 在較新版本中，會以背景垃圾收集取代並行的垃圾收集。

在 [工作站] 或 [伺服器垃圾收集] 中，您可以[啟用並行垃圾收集](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)，讓執行緒可以與在集合大部分持續時間內執行垃圾收集的專用線程並存執行。 此選項只會影響層代2中的垃圾收集;層代0和1一律為非並行，因為它們會快速完成。

並行記憶體回收會將回收期間的暫停降到最低，藉以加快互動式應用程式的回應速度。 當並行記憶體回收執行緒正在執行時，Managed 執行緒幾乎可以繼續執行。 這會在記憶體回收進行時縮短暫停時間。

並行記憶體回收會針對專屬執行緒執行。 根據預設，CLR 會執行工作站垃圾收集，同時在單處理器和多處理器電腦上啟用並行垃圾收集。

下列圖例顯示在分開的專屬執行緒上執行的並行記憶體回收。

![並行記憶體回收執行緒](./media/gc-concurrent.png)

## <a name="see-also"></a>另請參閱

- [工作站和伺服器記憶體回收](workstation-server-gc.md)
- [用於垃圾收集的執行時間設定選項](../../core/run-time-config/garbage-collector.md)
