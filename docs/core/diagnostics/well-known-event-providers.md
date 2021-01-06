---
title: .NET 中的知名事件提供者
description: 檢查 .NET 執行時間和程式庫所發佈的提供者和事件。
ms.topic: reference
ms.date: 12/21/2020
ms.openlocfilehash: 03d505f33e300b094958676bb768fb542d828aeb
ms.sourcegitcommit: c3093e9d106d8ca87cc86eef1f2ae4ecfb392118
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97738199"
---
# <a name="well-known-event-providers-in-net"></a>.NET 中的知名事件提供者

.NET 執行時間和程式庫會透過數個不同的事件提供者來寫入診斷事件。 視您的診斷需求而定，您可以選擇適當的提供者來啟用。 本文描述 .NET 執行時間和程式庫中最常使用的一些事件提供者。

## <a name="coreclr"></a>CoreCLR

### <a name="microsoft-windows-dotnetruntime-provider"></a>DotNETRuntime 的提供者

此提供者會從 .NET 執行時間發出各種事件，包括 GC、載入器、JIT、例外狀況和其他事件。 深入瞭解此提供者在 [執行時間提供者事件清單](../../fundamentals/diagnostics/runtime-events.md)中的每個事件。

### <a name="microsoft-dotnetcore-sampleprofiler-provider"></a>"Microsoft DotNETCore-SampleProfiler" 提供者

此提供者是 .NET 運行時間事件提供者，用於受控呼叫堆疊的 CPU 取樣。 啟用時，會每隔10毫秒捕獲每個執行緒之 managed 呼叫堆疊的快照集。 若要啟用此捕捉，您必須指定 <xref:System.Diagnostics.Tracing.EventLevel> `Informational` 或更高版本。

## <a name="framework-libraries"></a>Framework 程式庫

### <a name="microsoft-extensions-dependencyinjection-provider"></a>"Microsoft DependencyInjection" 提供者

此提供者會從 DependencyInjection 記錄資訊。 下表顯示提供者所記錄的事件 `Microsoft-Extensions-DependencyInjection` ：

|事件名稱|層級|描述|
|----------|-----|-----------|
|`CallSiteBuilt`|詳細資訊 (5)|已建立呼叫位置。|
|`ServiceResolved`|詳細資訊 (5)|服務已解決。|
|`ExpressionTreeGenerated`|詳細資訊 (5)|已產生運算式樹狀架構。|
|`DynamicMethodBuilt`|詳細資訊 (5)|已 <xref:System.Reflection.Emit.DynamicMethod> 建立。|

### <a name="systembuffersarraypooleventsource-provider"></a>"ArrayPoolEventSource" 提供者

此提供者會從 ArrayPool 記錄資訊。 下表顯示記錄的事件 `ArrayPoolEventSource` ：

|事件名稱|層級|描述|
|----------|-----|-----------|
|`BufferRented`|詳細資訊 (5)|已成功租用緩衝區。|
|`BufferAllocated`|告知性 (4)|緩衝區是由集區配置。|
|`BufferReturned`|詳細資訊 (5)|緩衝區會傳回集區。|
|`BufferTrimmed`|告知性 (4)|因為記憶體壓力或非使用狀態，所以嘗試釋放緩衝區。|
|`BufferTrimPoll`|告知性 (4)|正在進行修剪緩衝區的檢查。|

### <a name="systemnethttp-provider"></a>"System .Net. Http" 提供者

此提供者會從 HTTP 堆疊記錄資訊。 下表顯示提供者所記錄的事件 `System.Net.Http` ：

|事件名稱|層級|描述|
|----------|-----|-----------|
|RequestStart|告知性 (4)|HTTP 要求已開始。|
|RequestStop|告知性 (4)|HTTP 要求已完成。|
|RequestFailed|錯誤 (2) |HTTP 要求失敗。|
|ConnectionEstablished|告知性 (4)|已建立 HTTP 連接。|
|ConnectionClosed|告知性 (4)|HTTP 連接已關閉。|
|RequestLeftQueue|告知性 (4)|HTTP 要求已離開要求佇列。|
|RequestHeadersStart|告知性 (4)|標頭的 HTTP 要求已開始。|
|RequestHeaderStop|告知性 (4)|標頭的 HTTP 要求已完成。|
|RequestContentStart|告知性 (4)|已開始內容的 HTTP 要求。|
|RequestContentStop|告知性 (4)|已完成內容的 HTTP 要求。|
|ResponseHeadersStart|告知性 (4)|標頭的 HTTP 回應已開始。|
|ResponseHeaderStop|告知性 (4)|標頭的 HTTP 回應已完成。|
|ResponseContentStart|告知性 (4)|已開始內容的 HTTP 回應。|
|ResponseContentStop|告知性 (4)|內容的 HTTP 回應已完成。|

### <a name="systemnetnameresolution-provider"></a>"System NameResolution" 提供者

此提供者會記錄與功能變數名稱解析相關的資訊。 下表顯示記錄的事件 `System.Net.NameResolution` ：

|事件名稱|層級|描述|
|----------|-----|-----------|
|`ResolutionStart`|告知性 (4)|已開始網域名稱解析。|
|`ResolutionStop`|告知性 (4)|定義域名稱解析已完成。|
|`ResolutionFailed`|告知性 (4)|定義域名稱解析失敗。|

### <a name="systemnetsockets-provider"></a>「系統 .Net 通訊端」提供者

此提供者會記錄來自的資訊 <xref:System.Net.Sockets.Socket> 。 下表顯示提供者所記錄的事件 `System.Net.Sockets` ：

|事件名稱|層級|描述|
|----------|-----|-----------|
|`ConnectStart`|告知性 (4)|已開始嘗試啟動通訊端連接。|
|`ConnectStop`|告知性 (4)|嘗試啟動通訊端連接已完成。|
|`ConnectFailed`|告知性 (4)|嘗試啟動通訊端連線失敗。|
|`AcceptStart`|告知性 (4)|已開始接受通訊端連接的嘗試。|
|`AcceptStop`|告知性 (4)|嘗試接受通訊端連接已完成。|
|`AcceptFailed`|告知性 (4)|嘗試接受通訊端連線失敗。|

### <a name="systemthreadingtaskstpleventsource-provider"></a>"TplEventSource" 提供者

此提供者會記錄工作 [平行程式庫](../../standard/parallel-programming/task-parallel-library-tpl.md)的資訊，例如工作排程器事件。 下表顯示記錄的事件 `TplEventSource` ：

|事件名稱|關鍵字|層級|描述|
|----------|-------|-----|-----------|
|`TaskScheduled`|`TaskTransfer`(`0x1`)<br /><br />`Tasks`(`0x2`)|告知性 (4)|會排入工作排程器的 <xref:System.Threading.Tasks.Task> 佇列。|
|`TaskStarted`|`Tasks`(`0x2`)|告知性 (4)|<xref:System.Threading.Tasks.Task>已開始執行。|
|`TaskCompleted`|`TaskStops`(`0x40`)|告知性 (4)|<xref:System.Threading.Tasks.Task>已完成執行。|
|`TaskWaitBegin`|`TaskTransfer`(`0x1`)<br /><br />`TaskWait`(`0x2`)|告知性 (4)|在完成的隱含或明確等候開始時引發 <xref:System.Threading.Tasks.Task> 。|
|`TaskWaitEnd`|`Tasks`(`0x2`)|詳細資訊 (5)|在等候完成時引發 <xref:System.Threading.Tasks.Task> 。|
|`TaskWaitContinuationStarted`|`Tasks`(`0x2`)|詳細資訊 (5)|當與相關聯的工作 (方法) 開始時引發 `TaskWaitEnd` 。|
|`TaskWaitContinuationCompleted`|`TaskStops`(`0x40`)|詳細資訊 (5)|當與相關聯的工作 (方法) 完成時引發 `TaskWaitEnd` 。|
|`AwaitTaskContinuationScheduled`|`TaskTransfer`(`0x1`)<br /><br />`Tasks`(`0x2`)|告知性 (4)|當已排程的非同步接續時引發 <xref:System.Threading.Tasks.Task> 。|

## <a name="aspnet-core"></a>ASP.NET Core

ASP.NET Core 也會提供數個事件，以協助您診斷 ASP.NET Core 堆疊中的問題。

若要深入瞭解 ASP.NET Core 中的事件，以及如何使用它們，請參閱使用 [.Net Core 進行記錄和 ASP.NET Core](/aspnet/core/fundamentals/logging/)。
