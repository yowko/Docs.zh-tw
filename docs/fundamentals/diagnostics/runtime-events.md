---
title: 運行時間事件
description: 檢查 .NET 執行時間發出的診斷事件， (可搭配 ETW、LTTng 或 EventPipe 使用的 CoreCLR) 。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- runtime events (CoreCLR)
- ETW, EventPipe runtime events (CoreCLR)
ms.openlocfilehash: 33fa7275ce40934ce043b4d0dba5749c37515755
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "96586637"
---
# <a name="net-runtime-events"></a>.NET 運行時間事件

.NET 執行時間 (CoreCLR) 發出各種事件，可用來診斷 .NET 應用程式的問題，這些問題可透過各種機制（例如 `ETW` 、和）使用 `LTTng` `EventPipe` 。

本檔是 .NET Core 執行時間所引發事件的參考。

針對 .NET Framework 中的運行時間事件，請參閱 [CLR ETW 事件](../../framework/performance/clr-etw-events.md)。

## <a name="in-this-section"></a>本節內容

[爭用事件](runtime-contention-events.md)\
這些事件會收集監視器鎖定爭用的相關資訊。

[垃圾收集事件](runtime-garbage-collection-events.md)\
這些事件收集到記憶體回收的相關資訊。 它們有助於診斷和偵測，包括決定執行垃圾收集的次數、在垃圾收集期間釋放多少記憶體等等。

[例外狀況事件](runtime-exception-events.md)\
這些運行時間事件會捕捉擲回之例外狀況的相關資訊。

[Interop 事件](runtime-interop-events.md)\
這些運行時間事件會捕獲一般中繼語言 (CIL) 存根產生的相關資訊。

[載入器和系結器事件](runtime-loader-binder-events.md)\
這些事件會收集載入和卸載元件和模組的相關資訊。

[方法事件](runtime-method-events.md)\
這些事件會收集方法的特定資訊。 若要進行符號解析，需使用這些事件的承載。 此外，這些事件會提供實用資訊，例如呼叫方法的次數。

[執行緒事件](runtime-thread-events.md)\
這些事件會收集背景工作和 I/O 執行緒的資訊。

[類型事件](runtime-type-events.md)\
這些事件會收集有關型別系統的資訊。
