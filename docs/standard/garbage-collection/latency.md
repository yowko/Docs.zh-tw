---
title: 延遲模式
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, intrusiveness
- garbage collection, latency modes
ms.assetid: 96278bb7-6eab-4612-8594-ceebfc887d81
ms.openlocfilehash: a8eaf0c80aa32978eead80c51a905cbcd66a537b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "74283599"
---
# <a name="latency-modes"></a>延遲模式

要回收物件，垃圾回收器 （GC） 必須停止應用程式中的所有執行執行緒。 垃圾回收器處於活動狀態的時間段稱為其*延遲*。

在某些情況下，例如當應用程式擷取資料或顯示內容時，完整記憶體回收會在關鍵時刻進行，而妨礙效能。 您可以藉由設定 <xref:System.Runtime.GCSettings.LatencyMode%2A?displayProperty=nameWithType> 屬性為 <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> 值的其中一個，來調整記憶體回收行程的干擾程度。

## <a name="low-latency-settings"></a>低延遲設置

使用"低"延遲設置意味著垃圾回收器在應用程式中侵入較少。 垃圾回收對回收記憶體更加保守。

<xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> 列舉會提供兩個低延遲設定：

- [GC延遲模式.低延遲](xref:System.Runtime.GCLatencyMode.LowLatency)禁止第 2 代集合，並且僅執行第 0 代和第 1 代集合。 它只適合短時間使用。 經過一段較長的時間後，如果系統記憶體吃緊，則記憶體回收行程將會觸發回收，該回收可能會短暫暫停應用程式，並且中斷時間關鍵的作業。 這項設定僅適用於工作站記憶體回收。

- [GC延遲模式.持續低延遲](xref:System.Runtime.GCLatencyMode.SustainedLowLatency)抑制前景第 2 代集合，僅執行第 0 代、1 和後臺第 2 代集合。 它可以長時間使用，並且可用於工作站和伺服器記憶體回收。 如果禁用後臺垃圾回收，則無法使用此設置。

在低延遲期間，會隱藏層代 2 回收，除非發生下列情況：

- 系統從作業系統接收到記憶體不足的通知。

- 應用程式代碼通過調用<xref:System.GC.Collect%2A?displayProperty=nameWithType>方法並為`generation`參數指定 2 來誘導集合。

## <a name="scenarios"></a>案例

下表列出了用於使用<xref:System.Runtime.GCLatencyMode>這些值的應用程式方案：

|延遲模式|應用程式案例|
|------------------|---------------------------|
|<xref:System.Runtime.GCLatencyMode.Batch>|對於沒有使用者介面 （UI） 或伺服器端操作的應用程式。<br /><br />禁用後臺垃圾回收後，這是工作站和伺服器垃圾回收的預設模式。 <xref:System.Runtime.GCLatencyMode.Batch>模式還覆蓋[gcConcurrent](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)設置，即它阻止後臺或併發集合。|
|<xref:System.Runtime.GCLatencyMode.Interactive>|對於大部分有使用者介面的應用程式，<br /><br />這是工作站和伺服器垃圾回收的預設模式。 但是，如果託管了應用，則託管進程的垃圾回收器設置將優先。|
|<xref:System.Runtime.GCLatencyMode.LowLatency>|對於具有短期、對時間敏感作業的應用程式，其執行期間可能受到記憶體回收行程中斷的干擾。 例如，呈現動畫或資料獲取功能的應用程式。|
|<xref:System.Runtime.GCLatencyMode.SustainedLowLatency>|適合的應用程式具有對時間敏感的作業，這些作業可能長時間持續執行，且這段執行時間內可能經常受到記憶體回收行程中斷的干擾。 例如，因為交易時間內市場資料不斷變化，而需要迅速回應的應用程式。<br /><br />這個模式會所產生的 Managed 堆積大小會比其他模式更大。 由於它不會壓縮 Managed 堆積，因此磁碟可能會高度分割。 確定有足夠的記憶體可供使用。|

## <a name="guidelines-for-using-low-latency"></a>使用低延遲的指南

使用[GC延遲模式.低延遲](xref:System.Runtime.GCLatencyMode.LowLatency)模式時，請考慮以下準則：

- 盡可能縮短這段低延遲的時間。

- 請避免在低延遲期間配置大量記憶體。 因為記憶體回收較少物件時，會造成記憶體不足的通知。

- 在低延遲模式下，儘量減少新分配的數量，特別是分配給大型物件堆和固定物件。

- 請注意無法配置的執行緒。 由於<xref:System.Runtime.GCSettings.LatencyMode%2A>屬性設置是進程範圍的，<xref:System.OutOfMemoryException>因此可以在分配的任何執行緒上生成異常。

- 在受限執列區域中包裝低延遲代碼。 有關詳細資訊，請參閱[約束執列區域](../../../docs/framework/performance/constrained-execution-regions.md)。

- 您也可以呼叫 <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%29?displayProperty=nameWithType> 方法，在低延遲期間強制層代 2 回收。

## <a name="see-also"></a>另請參閱

- <xref:System.GC?displayProperty=nameWithType>
- [引發的收集](../../../docs/standard/garbage-collection/induced.md)
- [記憶體回收](../../../docs/standard/garbage-collection/index.md)
