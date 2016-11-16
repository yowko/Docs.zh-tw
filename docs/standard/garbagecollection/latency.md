---
title: "延遲模式"
description: "延遲模式"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/18/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 810bd8be-5a48-42c6-b080-3afdb31fc61b
translationtype: Human Translation
ms.sourcegitcommit: de0dab146fc811e895dc32f98f877db5e757f82b
ms.openlocfilehash: e063482aaa1fad01f8e0cd9e8552c87a0b247571

---

# <a name="latency-modes"></a>延遲模式

為了回收物件，記憶體回收行程必須停止應用程式中所有正在執行的執行緒。 在某些情況下，例如當應用程式擷取資料或顯示內容時，完整記憶體回收會在關鍵時刻進行，而妨礙效能。 您可以將 [GCSettings.LatencyMode](xref:System.Runtime.GCSettings.LatencyMode) 屬性設定為其中一個 [System.Runtime.GCLatencyMode](xref:System.Runtime.GCLatencyMode) 值，來調整記憶體回收行程的干擾程度。 

延遲指的是記憶體回收行程干擾應用程式的時間。 在低延遲期間，記憶體回收行程會更加保守，也較不干擾啟用物件。 [System.Runtime.GCLatencyMode](xref:System.Runtime.GCLatencyMode) 列舉提供兩個低延遲設定：

* [LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency) 會隱藏層代 2 回收，並且只執行層代 0 和 1 回收。 它只適合短時間使用。 經過一段較長的時間後，如果系統記憶體吃緊，則記憶體回收行程將會觸發回收，該回收可能會短暫暫停應用程式，並且中斷時間關鍵的作業。 這項設定僅適用於工作站記憶體回收。 

* [SustainedLowLatency](xref:System.Runtime.GCLatencyMode.SustainedLowLatency) 會隱藏前景層代 2 回收，並且只執行層代 0、1 和背景層代 2 回收。 它可以長時間使用，並且可用於工作站和伺服器記憶體回收。 如果已停用[並行記憶體回收](https://msdn.microsoft.com/library/yhwwzef8.aspx)，則無法使用這個設定。

在低延遲期間，會隱藏層代 2 回收，除非發生下列情況：

* 系統從作業系統接收到記憶體不足的通知。

* 應用程式碼會呼叫 [GC.Collect](xref:System.GC.Collect(System.Int32)) 方法並將 generation 參數指定為 2 來進行回收。

下表列出使用 [GCLatencyMode](xref:System.Runtime.GCLatencyMode) 值的應用程式案例。

延遲模式 | 應用程式案例
------------ | --------------------- 
[Batch](xref:System.Runtime.GCLatencyMode.Batch) | 對於沒有 UI 或伺服器端作業的應用程式。 這是[並行記憶體回收](https://msdn.microsoft.com/library/yhwwzef8.aspx)停用時的預設模式。
[Interactive](xref:System.Runtime.GCLatencyMode.Interactive) | 對於大部分有使用者介面的應用程式， 對於沒有 UI 或伺服器端作業的應用程式。 這是[並行記憶體回收](https://msdn.microsoft.com/library/yhwwzef8.aspx)啟用時的預設模式。
[LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency) | 對於具有短期、對時間敏感作業的應用程式，其執行期間可能受到記憶體回收行程中斷的干擾。 例如，應用程式使用動畫呈現或資料擷取的函式。
[SustainedLowLatency](xref:System.Runtime.GCLatencyMode.SustainedLowLatency) | 適合的應用程式具有對時間敏感的作業，這些作業可能長時間持續執行，且這段執行時間內可能經常受到記憶體回收行程中斷的干擾。 例如，因為交易時間內市場資料不斷變化，而需要迅速回應的應用程式。   這個模式會所產生的 Managed 堆積大小會比其他模式更大。 由於它不會壓縮 Managed 堆積，因此磁碟可能會高度分割。 確定有足夠的記憶體可供使用。
 
## <a name="guidelines-for-using-low-latency"></a>使用低延遲的指導方針

當您使用 [LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency) 模式時，請考慮下列指導方針：

* 盡可能縮短這段低延遲的時間。

* 請避免在低延遲期間配置大量記憶體。 因為記憶體回收較少物件時，會造成記憶體不足的通知。 

* 在低延遲模式時，盡量減少配置數目，特別是配置到大型物件堆積和 Pin 物件的數目。 

* 請注意無法配置的執行緒。 因為 [LatencyMode](xref:System.Runtime.GCSettings.LatencyMode) 屬性設定為整個處理序，或許會在可能配置的任何執行緒中產生 [OutOfMemoryException](xref:System.OutOfMemoryException)。 

* 您也可以呼叫 [GC.Collect(Int32, GCCollectionMode)](xref:System.GC.Collect(System.Int32,System.GCCollectionMode)) 方法，在低延遲期間強制層代 2 回收。

## <a name="see-also"></a>另請參閱

[System.GC](xref:System.GC)

[引發的收集](induced.md)

[.NET 中的記憶體回收](index.md)



<!--HONumber=Nov16_HO1-->


