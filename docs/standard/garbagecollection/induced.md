---
title: "引發的回收"
description: "引發的回收"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 3e09b9dd-a800-4e56-b468-619f910ae22e
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: e120ba44f16b7e4c697d94d270b2ddcc9ae83c48
ms.lasthandoff: 03/02/2017

---

# <a name="induced-collections"></a>引發的回收

大部分情況下，記憶體回收行程會判斷執行回收的最佳時間，請讓記憶體回收行程獨立執行。 在罕見的情況下，強制回收可能會改善您應用程式的效能。 在這些情況下，您可以使用 [GC.Collect](xref:System.GC.Collect) 方法強制進行記憶體回收，來引發記憶體回收。 

在應用程式碼特定位置所使用的記憶體數量大幅下降時，請使用 [Collect](xref:System.GC.Collect) 方法。 例如，如果您的應用程式使用具有數個控制項的複雜對話方塊，則在關閉對話方塊時呼叫 [Collect](xref:System.GC.Collect) 可透過立即回收對話方塊所使用的記憶體來改善效能。 請確定您的應用程式沒有太頻繁地進行記憶體回收，原因是如果記憶體回收行程嘗試在非最佳時間回收物件，則這樣可能會降低效能。 您可以將 [GCCollectionMode.Optimized](xref:System.GCCollectionMode.Optimized) 列舉值提供給 [Collect](xref:System.GC.Collect) 方法，只在回收具備生產力時才進行回收 (如下節所討論)。

## <a name="gc-collection-mode"></a>GC 收集模式

您可以使用其中一個 [GC.Collect](xref:System.GC.Collect) 方法多載，其包含 [GCCollectionMode](xref:System.GCCollectionMode) 值來指定強制回收行為，如下所示。

GCCollectionMode 值 | 說明
---------------------- | ----------- 
[Default](xref:System.GCCollectionMode.Default) | 使用 .NET Framework 執行版本的預設記憶體回收設定。
[Forced](xref:System.GCCollectionMode.Forced) | 強制立即進行記憶體回收。 這等於呼叫 [GC.Collect()](xref:System.GC.Collect) 多載。 它會導致完整封鎖回收所有層代。 在強制立即完整封鎖記憶體回收之前，將 [GCSettings.LargeObjectHeapCompactionMode](xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode) 屬性設定為 [GCLargeObjectHeapCompactionMode.CompactOnce](xref:System.Runtime.GCLargeObjectHeapCompactionMode.CompactOnce)，也可以壓縮大型物件堆積。 
[Optimized](xref:System.GCCollectionMode.Optimized) | 可讓記憶體回收行程判斷目前時間是否最適合回收物件。 記憶體回收行程可能會判斷回收的生產力不足無法進行調整，在此情況下會返回，而不是回收物件。
 
## <a name="background-or-blocking-collections"></a>背景或封鎖回收

您可以呼叫 [GC.Collect(Int32, GCCollectionMode, Boolean)](xref:System.GC.Collect(System.Int32,System.GCCollectionMode,System.Boolean)) 方法多載，來指定是否封鎖引發的回收。 執行的回收類型取決於方法的 *mode* 與 *blocking* 參數組合。 *mode* 是 [GCCollectionMode](xref:System.GCCollectionMode) 列舉的成員，而 *blocking* 是 [Boolean](xref:System.Boolean) 值。 下表摘要說明模式和封鎖引數的互動。 

*mode* | *blocking* = true | *blocking* = false
------ | ----------------- | ------------------
[Forced](xref:System.GCCollectionMode.Forced) 或 [Default](xref:System.GCCollectionMode.Default) | 會盡快執行封鎖回收。 如果正在進行背景回收，而且層代是 0 或 1，則 [Collect(Int32, GCCollectionMode, Boolean)](xref:System.GC.Collect(System.Int32,System.GCCollectionMode,System.Boolean)) 方法會立即觸發封鎖回收，並在回收完成時返回。 如果正在進行背景回收，而且 generation 參數是 2，則方法會等到背景回收完成，並觸發封鎖層代 2 回收，然後返回。 | 會盡快執行回收。 [Collect(Int32, GCCollectionMode, Boolean)](xref:System.GC.Collect(System.Int32,System.GCCollectionMode,System.Boolean)) 方法會要求背景回收，但這不是必然；根據情況，可能仍然會執行封鎖回收。 如果已在進行背景回收，則這個方法會立即返回。 
[Optimized](xref:System.GCCollectionMode.Optimized) | 根據記憶體回收行程的狀態和 generation 參數，可能會執行封鎖回收。 記憶體回收行程會嘗試提供最佳效能。 | 根據記憶體回收行程的狀態，可能會執行回收。 [Collect(Int32, GCCollectionMode, Boolean)](xref:System.GC.Collect(System.Int32,System.GCCollectionMode,System.Boolean)) 方法會要求背景回收，但這不是必然；根據情況，可能仍然會執行封鎖回收。 記憶體回收行程會嘗試提供最佳效能。 如果已在進行背景回收，則這個方法會立即返回。 
 
## <a name="see-also"></a>另請參閱

[延遲模式](latency.md)

[.NET 中的記憶體回收](index.md)

