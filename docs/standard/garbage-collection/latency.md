---
title: 延遲模式
ms.date: 03/30/2017
helpviewer_keywords:
- garbage collection, intrusiveness
- garbage collection, latency modes
ms.assetid: 96278bb7-6eab-4612-8594-ceebfc887d81
ms.openlocfilehash: 2e7b30a50e2513c567abf2116ab5495e717a8e22
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94831191"
---
# <a name="latency-modes"></a>延遲模式

若要回收物件，垃圾收集行程 (GC) 必須停止應用程式中所有執行中的執行緒。 在這段期間內，垃圾收集行程是使用中的時間，稱為 *延遲*。

在某些情況下，例如當應用程式擷取資料或顯示內容時，完整記憶體回收會在關鍵時刻進行，而妨礙效能。 您可以藉由設定 <xref:System.Runtime.GCSettings.LatencyMode%2A?displayProperty=nameWithType> 屬性為 <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> 值的其中一個，來調整記憶體回收行程的干擾程度。

## <a name="low-latency-settings"></a>低延遲設定

使用「低」延遲設定表示您的應用程式中的垃圾收集行程行程干擾較少。 回收記憶體的垃圾收集更保守。

<xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> 列舉會提供兩個低延遲設定：

- [GCLatencyMode](xref:System.Runtime.GCLatencyMode.LowLatency) 會隱藏層代2回收，並且只執行層代0和1回收。 它只適合短時間使用。 經過一段較長的時間後，如果系統記憶體吃緊，則記憶體回收行程將會觸發回收，該回收可能會短暫暫停應用程式，並且中斷時間關鍵的作業。 這項設定僅適用於工作站記憶體回收。

- [GCLatencyMode](xref:System.Runtime.GCLatencyMode.SustainedLowLatency) 會隱藏前景層代2回收，並且只執行層代0、1和背景層代2回收。 它可以長時間使用，並且可用於工作站和伺服器記憶體回收。 如果停用背景垃圾收集，則無法使用此設定。

在低延遲期間，會隱藏層代 2 回收，除非發生下列情況：

- 系統從作業系統接收到記憶體不足的通知。

- 應用程式程式碼會藉由呼叫方法來引發集合 <xref:System.GC.Collect%2A?displayProperty=nameWithType> ，並為參數指定 2 `generation` 。

## <a name="scenarios"></a>案例

下表列出使用這些值的應用程式案例 <xref:System.Runtime.GCLatencyMode> ：

|延遲模式|應用程式案例|
|------------------|---------------------------|
|<xref:System.Runtime.GCLatencyMode.Batch>|針對沒有使用者介面 (UI) 或伺服器端作業的應用程式。<br /><br />停用背景垃圾收集時，這是工作站和伺服器垃圾收集的預設模式。 <xref:System.Runtime.GCLatencyMode.Batch> 模式也會覆寫 [>gcconcurrent>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) 設定，也就是說，它會防止背景或並行集合。|
|<xref:System.Runtime.GCLatencyMode.Interactive>|對於大部分有使用者介面的應用程式，<br /><br />這是工作站和伺服器垃圾收集的預設模式。 但是，如果裝載應用程式，則裝載進程的垃圾收集行程設定會優先執行。|
|<xref:System.Runtime.GCLatencyMode.LowLatency>|對於具有短期、對時間敏感作業的應用程式，其執行期間可能受到記憶體回收行程中斷的干擾。 例如，呈現動畫或資料取得函數的應用程式。|
|<xref:System.Runtime.GCLatencyMode.SustainedLowLatency>|適合的應用程式具有對時間敏感的作業，這些作業可能長時間持續執行，且這段執行時間內可能經常受到記憶體回收行程中斷的干擾。 例如，因為交易時間內市場資料不斷變化，而需要迅速回應的應用程式。<br /><br />這個模式會所產生的 Managed 堆積大小會比其他模式更大。 由於它不會壓縮 Managed 堆積，因此磁碟可能會高度分割。 確定有足夠的記憶體可供使用。|

## <a name="guidelines-for-using-low-latency"></a>使用低延遲的指導方針

當您使用 [GCLatencyMode LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency) 模式時，請考慮下列指導方針：

- 盡可能縮短這段低延遲的時間。

- 請避免在低延遲期間配置大量記憶體。 因為記憶體回收較少物件時，會造成記憶體不足的通知。

- 在低延遲模式中，將新配置的數目降至最低，特別是在大型物件堆積和釘選的物件上。

- 請注意無法配置的執行緒。 由於 <xref:System.Runtime.GCSettings.LatencyMode%2A> 屬性設定是整個進程，因此 <xref:System.OutOfMemoryException> 可以在任何配置的執行緒上產生例外狀況。

- 將低延遲程式碼包裝在限制執列區域中。 如需詳細資訊，請參閱 [限制執列區域](../../framework/performance/constrained-execution-regions.md)。

- 您也可以呼叫 <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%29?displayProperty=nameWithType> 方法，在低延遲期間強制層代 2 回收。

## <a name="see-also"></a>請參閱

- <xref:System.GC?displayProperty=nameWithType>
- [引發的集合](induced.md)
- [記憶體回收](index.md)
