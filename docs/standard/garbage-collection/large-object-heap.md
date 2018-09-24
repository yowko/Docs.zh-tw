---
title: Windows 系統上的大型物件堆積
ms.date: 05/02/2018
helpviewer_keywords:
- large object heap (LOH)"
- LOH
- garbage collection, large object heap
- GC [.NET ], large object heap
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8dfe3fdbf71918a7ed2b6dccca24f58688bc14f2
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46003083"
---
# <a name="the-large-object-heap-on-windows-systems"></a>Windows 系統上的大型物件堆積

.NET 記憶體回收行程 (GC) 會將物件區分成小型和大型的物件。 當物件是大型時，它的一些屬性就會變得比物件是小型時更加重要。 例如，要壓縮大型物件 (亦即，將記憶體中的大型物件複製到堆積上的其他地方) 時需要耗費大量資源。 因為這個緣故，.NET 記憶體回收行程會將大型物件放在大型物件堆積 (LOH) 中。 在本主題中，我們將深入探討大型物件堆積。 我們將討論什麼條件才能將物件區分為大型物件，如何回收這些大型物件，以及大型物件對效能有何種影響。

> [!IMPORTANT]
> 本主題只討論 Windows 系統上執行之 .NET Framework 和 .NET Core 的大型物件堆積。 它並未涵蓋在其他平台的 .NET 實作上執行的 LOH。

## <a name="how-an-object-ends-up-on-the-large-object-heap-and-how-gc-handles-them"></a>物件最後如何送入大型物件堆積以及 GC 如何處理它們

如果物件大於或等於 85,000 個位元組，就會視為大型物件。 這個數目取決於效能微調。 當物件配置要求是針對 85,000 個以上的位元組時，執行階段會將它配置在大型物件堆積上。

若要了解這表示什麼意思，請務必查看有關 .NET GC 的某些基本概念。

.NET 記憶體回收行程是層代式的回收行程。 它有三個層代：層代 0、層代 1 和層代 2。 具有 3 個層代的原因是，在精密微調的應用程式中，大部分的物件都會在 gen0 中結束。 例如，在伺服器應用程式中，與每個要求相關聯的配置應該在要求完成之後結束。 執行中的配置要求則會進入 gen1，並且在該處結束。 基本上，gen1 是扮演年輕物件區域與長期存留物件區域之間的緩衝區。

小物件一律會配置在層代 0 中，並根據其存留期，可能會提升至層代 1 或層代 2。 大型物件則一律配置在層代 2 中。

大型物件屬於層代 2，因為只有在層代 2 回收期間才會回收它們。 回收層代時，也會回收其所有較年輕的層代。 舉例來說，發生層代 1 GC 時，會同時回收層代 1 和 0。 而發生層代 2 GC 時，就會回收整個堆積。 基於這個理由，層代 2 GC 也稱為「完整 GC」。 本文引用層代 2 GC，而不是完整 GC，但這些詞彙可以互換。

層代提供 GC 堆積的邏輯檢視。 實際上，物件是存留在受控堆積區段中。 「受控堆積區段」是記憶體的區塊，由 GC 代替受控程式碼向 OS (透過呼叫 [VirtualAlloc 函式](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx)) 要求保留。 載入 CLR 時，GC 會配置兩個初始堆積區段：一個針對小型物件 (小型物件堆積或 SOH)，另一個針對大型物件 (大型物件堆積)。

藉由將受控物件置於這些受控堆積區段中，就可以滿足配置的要求了。 如果物件小於 85,000 個位元組，它會置於 SOH 的區段上；否則，它會置於 LOH 區段。 隨著愈來愈多的物件配置在區段之上，這些區段就會被認可 (以較小的區塊)。
對於 SOH，在 GC 之後存留下來的物件會提升至下一個層代。 層代 0 回收之後存留下來的物件目前被視為層代 1 物件，依此類推。 然而，通過最老層代存留的物件仍可視為屬於最老的層代。 換句話說，來自層代 2 的存留者就是層代 2 物件；來自 LOH 的存留者就是 LOH 的物件 (用 gen2 來回收)。

使用者的程式碼只能配置在層代 0 (小型物件) 或 LOH (大型物件) 中。 唯有 GC 才能「配置」物件於層代 1 (藉由提升來自層代 0 的存留者) 與層代 2 (藉由提升來自層代 1 和 2 的存留者) 中。

觸發記憶體回收時，GC 會追蹤所有作用中的物件，並且加以壓縮。 但因為壓縮要耗費大量資源，所以 GC 會「掃除」LOH；這可將無作用物件建立成一份可用清單，稍後再用此清單來滿足大型物件配置的要求。 鄰近的無作用物件會結合成為一個可用物件。

.NET Core 和 .NET Framework (從 .NET Framework 4.5.1 開始) 包含 <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType> 屬性，可讓使用者指定 LOH 應該在下一個完整封鎖 GC 期間進行壓縮。 而且在未來，.NET 可能會決定自動壓縮 LOH。 這表示如果您配置了大型物件，並且想要確定它們不會更動，那麼您仍然應該將其固定。

圖 1 說明的案例，是 GC 在第一個層代 0 GC 之後形成了層代 1，其中 `Obj1` 和 `Obj3` 已無作用；以及 GC 在第一個層代 1 GC 之後形成了層代 2，其中 `Obj2` 和 `Obj5` 已無作用。 請注意，此圖和下圖僅供說明之用；它們包含一些物件，可更清楚顯示堆積上發生的狀況。 事實上，GC 中通常涉及更多的物件。

![圖 1：層代 0 GC 和層代 1 GC](media/loh/loh-figure-1.jpg)  
圖 1：層代 0 和層代 1 GC。

圖 2 顯示在發現 `Obj1` 和 `Obj2` 無作用的層代 2 GC 之後，GC 會使用 `Obj1` 和 `Obj2` 曾經佔用的記憶體形成連續的可用空間，這之後將用來滿足 `Obj4` 的配置要求。 在最後的物件 `Obj3` 之後，一直到區段結尾的空間，仍然可以用來滿足更多的配置要求。

![圖 2：在層代 2 GC 之後](media/loh/loh-figure-2.jpg)  
圖 2：在層代 2 GC 之後

如果沒有足夠的可用空間來處理大型物件配置的要求，GC 會先嘗試從 OS 取得更多區段。 如果該作業失敗，它就會觸發層代 2 GC，以期釋放一些空間。

在層代 1 或層代 2 GC 期間，記憶體回收行程將沒有作用中物件的區段釋放歸還給 OS (藉由呼叫 [VirtualFree 函式](https://msdn.microsoft.com/library/windows/desktop/aa366892(v=vs.85).aspx))。 從最後的作用中物件到區段結尾的空間會取消認可。(gen0/gen1 存留的暫時區段除外，記憶體回收行程確實會保持部分已認可，因為您的應用程式將立即開始在其中配置)。 可用空間雖然重設過，但仍然是經認可的，這表示 OS 並不必將其中的資料寫回磁碟中。

由於在層代 2 GC 期間只會收集 LOH，因此只能在這類 GC 期間釋放 LOH 區段。 圖 3 說明的案例，是記憶體回收行程將一個區段 (區段 2) 釋放釋放歸還 OS，並在其餘區段上取消認可更多空間的情況。 如果它必須使用位於區段結尾的已取消認可空間，來滿足大型物件配置要求，就會再次認可記憶體。 (如需認可/取消認可的說明，請參閱 [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) 的文件。

![圖 3：層代 2 GC 之後的 LOH](media/loh/loh-figure-3.jpg)  
圖 3：層代 2 GC 之後的 LOH

## <a name="when-is-a-large-object-collected"></a>何時收集大型物件？

一般情況下，發生下列 3 種情況其中之一時，就會發生 GC：

- 配置超過層代 0 或大型物件的臨界值。

  臨界值是層代的屬性。 當記憶體回收行程將物件配置到層代中時，就會設定層代的臨界值。 若超過臨界值，則會在該層代上觸發 GC。 當您配置小型或大型物件時，會分別取用層代 0 和 LOH 的臨界值。 如果記憶體回收行程配置到層代 1 和 2，就會取用其臨界值。 這些臨界值會隨著程式的執行而動態地調整。

  這是一般的情況；大部分 GC 的發生原因是由於受控堆積上的配置。

- 已呼叫 <xref:System.GC.Collect%2A?displayProperty=nameWithType> 方法。

  如果呼叫無參數的 <xref:System.GC.Collect?displayProperty=nameWithType> 方法或另一個多載傳遞 <xref:System.GC.MaxGeneration?displayProperty=nameWithType> 作為引數，LOH 會連同受控堆積的其餘部分一起回收。

- 系統處於記憶體不足的狀況。

  當記憶體回收行程從 OS 收到高記憶體通知時，會發生這種情況。 如果記憶體回收行程認為執行層代 2 GC 會提高生產力，則會觸發層代 2 GC。

## <a name="loh-performance-implications"></a>LOH 效能的影響

大型物件堆積上的配置會以下列方式影響效能。

- 配置成本。

  CLR 會保證它送出的每個新物件都已清除。 這表示大型物件的配置成本，是完全由記憶體清除來掌控的 (除非它觸發 GC)。 如果要花 2 個週期的時間才能清除一個位元組，就表示要花 170,000 個週期才能清除最小的大型物件。 在 2GHz 電腦上清除 16MB 物件的記憶體大約需要 16 毫秒。 這是相當大的成本。

- 回收成本。

  因為 LOH 和層代 2 會一起回收，如果超過其中一項的臨界值時，就會觸發層代 2 回收。 如果因為 LOH 而觸發了層代 2 回收，那麼在 GC 之後，層代 2 不一定會變得更小。 如果在層代 2 上沒有太多資料，其影響極小。 但是如果層代 2 很大，一旦觸發許多層代 2 GC，就可能會造成效能問題。 如果暫時配置了許多大型物件，而且您的 SOH 很大，則執行 GC 可能會花費太多時間。 此外，如果您繼續配置並釋放相當大的物件，配置的成本就會暴增。

- 含有參考類型的陣列元素。

  LOH 上的非常大型物件通常都是陣列 (非常大的執行個體物件極為罕見)。 如果陣列中的元素有許多參考，則會帶來元素中沒有許多參考時不會具有的成本。 如果元素未包含任何參考，記憶體回收行程根本不需要處理整個陣列。 例如，如果您使用陣列來儲存二元樹狀結構中的節點，實作它的方法之一，就是根據所有實際節點，逐一參考節點的右邊和左邊節點：

  ```csharp
  class Node
  {
     Data d;
     Node left;
     Node right;
  };

  Node[] binary_tr = new Node [num_nodes];
  ```

  如果 `num_nodes` 很大，記憶體回收行程需要每個元素至少處理兩個參考。 另一個方法是儲存右邊與左邊節點的索引：

  ```csharp
  class Node
  {
     Data d;
     uint left_index;
     uint right_index;
  } ;
  ```

  請不要將左邊節點的資料參考為 `left.d`，應將它參考為 `binary_tr[left_index].d`。 而記憶體回收行程不需要查看左邊和右邊節點的任何參考。

在這三個因素中，前兩個通常比第三個更加重要。 因此，建議您配置可複使用的大型物件集區，而不是配置暫存大型物件。

## <a name="collecting-performance-data-for-the-loh"></a>收集 LOH 的效能資料

收集特定區域的效能資料之前，您應該已經完成下列作業：

1. 已找到您應該查看此區域的證據。

2. 已排除您所知未找到任何項目能夠說明所看到效能問題的其他區域。

如需記憶體和 CPU 基本概念的詳細資訊，請參閱部落格 [Understand the problem before you try to find a solution](https://blogs.msdn.microsoft.com/maoni/2006/09/01/understand-the-problem-before-you-try-to-find-a-solution/) (了解問題，再嘗試找出解決方案)。

您可以使用下列工具來收集 LOH 效能的相關資料：

- [.NET CLR 記憶體效能計數器](#net-clr-memory-performance-counters)

- [ETW 事件](#etw-events)

- [偵錯工具](#a-debugger)

### <a name="net-clr-memory-performance-counters"></a>.NET CLR 記憶體效能計數器

在調查效能問題時，這些效能計數器通常是很好的起點 (即使我們建議您使用 [ETW 事件](#etw))。 您可以新增所需的計數器來設定效能監視器，如圖 4 所示。 與 LOH 相關的是：

- **層代 2 回收**

   顯示自處理序啟動後發生層代 2 GC 的次數。 此計數器會在層代 2 回收 (也稱為完整記憶體回收) 的結尾處遞增。 此計數器會顯示最後觀察到的值。

- **Large Object Heap size**

   顯示 LOH 的目前大小 (以位元組為單位)，包括可用空間。 這個計數器於記憶體回收的結尾更新，而非每次配置時更新。

查看效能計數器的常用方式，就是利用效能監視器 (perfmon.exe)。 請使用 [新增計數器]，為您關心的處理序新增有意義的計數器。 您可以將效能計數器資料儲存到記錄檔中，如圖 4 所示。

![圖 4：新增效能計數器。](media/loh/perfcounter.png)  
圖 4：層代 2 GC 之後的 LOH

效能計數器也可以用程式設計的方式來查詢。 許多人都會使用這種方式在日常測試程序中收集相關資訊。 當他們發覺到計數器有不正常的數值時，就可以使用其他方式取得詳細資料，來協助進行調查。

> [!NOTE]
> 建議您使用 ETW 事件而不是效能計數器，因為 ETW 提供更豐富的資訊。

### <a name="etw"></a>ETW

記憶體回收行程提供一組豐富的 ETW 事件，可協助您了解堆積正在執行的作業和原因。 下列部落格文章顯示如何收集和了解使用 ETW 的 GC 事件：

- [GC ETW Events - 1](https://blogs.msdn.microsoft.com/maoni/2014/12/22/gc-etw-events-1/) (GC ETW 事件 - 1)

- [GC ETW Events - 2](https://blogs.msdn.microsoft.com/maoni/2014/12/25/gc-etw-events-2/) (GC ETW 事件 - 2)

- [GC ETW Events - 3](https://blogs.msdn.microsoft.com/maoni/2014/12/25/gc-etw-events-3/) (GC ETW 事件 - 3)

- [GC ETW Events - 4](https://blogs.msdn.microsoft.com/maoni/2014/12/30/gc-etw-events-4/) (GC ETW 事件 - 4)

若要識別暫存 LOH 配置所造成的過多層代 2 GC，請查看 GC 的 [Trigger Reason] \(觸發原因\) 資料行。 對於只配置暫存大型物件的簡單測試，您可以使用下列 [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) 命令列收集 ETW 事件的相關資訊：

```console
perfview /GCCollectOnly /AcceptEULA /nogui collect
```

結果看起來如下：

![圖 5：使用 PerfView 檢查 ETW 事件](media/loh/perfview.png)  
圖 5：使用 PerfView 顯示的 ETW 事件

如您所見，所有的 GC 都是層代 2 GC，而且它們都是由 AllocLarge 所觸發，這表示配置大型物件時觸發了此 GC。 我們知道這些配置是暫時的，因為 [LOH Survival Rate %] \(LOH 未回收率 %\) 資料行顯示 1%。

您可以收集其他 ETW 事件，讓您知道何者配置了這些大型物件。 下列命令列：

```console
perfview /GCOnly /AcceptEULA /nogui collect
```

會收集 AllocationTick 事件，大約每隔 100K 的配置就會引發該事件。 換句話說，每次配置大型物件時，就會引發事件。 接著，您可以查看其中一個 GC 堆積配置檢視，這些檢視可向您顯示已配置大型物件的呼叫堆疊：

![圖 6：GC 堆積配置檢視](media/loh/perfview2.png)  
圖 6：GC 堆積配置檢視

如您所見，這是非常簡單的測試，只會從其 `Main` 方法配置大型物件。

### <a name="a-debugger"></a>偵錯工具

如果您只具有記憶體傾印，而且需要查看哪些物件實際在 LOH 上，您可以使用 .NET 所提供的 [SoS 偵錯工具延伸模組](http://msdn2.microsoft.com/ms404370.aspx)。

> [!NOTE]
> 本節中提及的偵錯命令適用於 [Windows 偵錯工具](https://www.microsoft.com/whdc/devtools/debugging/default.mspx)。

下圖顯示分析 LOH 的範例輸出：

```
0:003> .loadby sos mscorwks
0:003> !eeheap -gc
Number of GC Heaps: 1
generation 0 starts at 0x013e35ec
sdgeneration 1 starts at 0x013e1b6c
generation 2 starts at 0x013e1000
ephemeral segment allocation context: none
segment   begin allocated     size
0018f2d0 790d5588 790f4b38 0x0001f5b0(128432)
013e0000 013e1000 013e35f8 0x000025f8(9720)
Large object heap starts at 0x023e1000
segment   begin allocated     size
023e0000 023e1000 033db630 0x00ffa630(16754224)
033e0000 033e1000 043cdf98 0x00fecf98(16699288)
043e0000 043e1000 05368b58 0x00f87b58(16284504)
Total Size 0x2f90cc8(49876168)
------------------------------
GC Heap Size 0x2f90cc8(49876168)
0:003> !dumpheap -stat 023e1000 033db630
total 133 objects
Statistics:
MT   Count   TotalSize Class Name
001521d0       66     2081792     Free
7912273c       63     6663696 System.Byte[]
7912254c       4     8008736 System.Object[]
Total 133 objects
```

LOH 堆積的大小是 (16,754,224 + 16,699,288 + 16,284,504) = 49,738,016 個位元組。 在位址 023e1000 和 033db630 之間，<xref:System.Object?displayProperty=nameWithType> 物件的陣列佔用了 8,008,736 個位元組、<xref:System.Byte?displayProperty=nameWithType> 物件的陣列佔用了 6,663,696 個位元組，而可用空間佔用了 2,081,792 個位元組。

有時候，偵錯工具會顯示 LOH 大小總計是小於 85,000 個位元組。 這是因為執行階段本身會使用 LOH 來配置一些比大型物件小的物件。

因為 LOH 並未壓縮，所以有時候 LOH 會被認為是造成片段的來源。 片段意指：

- 受控堆積的片段，以受管理物件之間的可用空間數量表示。 在 SoS 中，`!dumpheap –type Free` 命令會顯示受控物件之間的可用空間數量。

- 虛擬記憶體 (VM) 位址空間的片段，這是標示為 `MEM_FREE` 的記憶體。 您可以在 windbg 中使用各種偵錯工具命令來取得它。

   下列範例會顯示 VM 空間中的片段：

   ```
   0:000> !address
   00000000 : 00000000 - 00010000
   Type     00000000
   Protect 00000001 PAGE_NOACCESS
   State   00010000 MEM_FREE
   Usage   RegionUsageFree
   00010000 : 00010000 - 00002000
   Type     00020000 MEM_PRIVATE
   Protect 00000004 PAGE_READWRITE
   State   00001000 MEM_COMMIT
   Usage   RegionUsageEnvironmentBlock
   00012000 : 00012000 - 0000e000
   Type     00000000
   Protect 00000001 PAGE_NOACCESS
   State   00010000 MEM_FREE
   Usage   RegionUsageFree
   … [omitted]
   -------------------- Usage SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Pct(Busy)   Usage
   701000 (   7172) : 00.34%   20.69%   : RegionUsageIsVAD
   7de15000 ( 2062420) : 98.35%   00.00%   : RegionUsageFree
   1452000 (   20808) : 00.99%   60.02%   : RegionUsageImage
   300000 (   3072) : 00.15%   08.86%   : RegionUsageStack
   3000 (     12) : 00.00%   00.03%   : RegionUsageTeb
   381000 (   3588) : 00.17%   10.35%   : RegionUsageHeap
   0 (       0) : 00.00%   00.00%   : RegionUsagePageHeap
   1000 (       4) : 00.00%   00.01%   : RegionUsagePeb
   1000 (       4) : 00.00%   00.01%   : RegionUsageProcessParametrs
   2000 (       8) : 00.00%   00.02%   : RegionUsageEnvironmentBlock
   Tot: 7fff0000 (2097088 KB) Busy: 021db000 (34668 KB)

   -------------------- Type SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Usage
   7de15000 ( 2062420) : 98.35%   : <free>
   1452000 (   20808) : 00.99%   : MEM_IMAGE
   69f000 (   6780) : 00.32%   : MEM_MAPPED
   6ea000 (   7080) : 00.34%   : MEM_PRIVATE

   -------------------- State SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Usage
   1a58000 (   26976) : 01.29%   : MEM_COMMIT
   7de15000 ( 2062420) : 98.35%   : MEM_FREE
   783000 (   7692) : 00.37%   : MEM_RESERVE

   Largest free region: Base 01432000 - Size 707ee000 (1843128 KB)
   ```

經常可以看到 VM 片段，這是由需要經常進行記憶體回收的暫存大型物件所造成的，因為這樣才能從 OS 取得新的受控堆積區段，並將空的區段釋放歸還給 OS。

若要驗證 LOH 是否會造成 VM 片段，您可以在 [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) 和 [VirtualFree](https://msdn.microsoft.com/library/windows/desktop/aa366892(v=vs.85).aspx) 上設定中斷點，以查看何者會呼叫它們。 例如，若要查看何者會嘗試從 OS 配置大於 8MB 的虛擬記憶體區塊，您可以設定中斷點如下：

```console
bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"
```

此命令會中斷並進入偵錯工具，並且只有在配置大小大於 8MB (0x800000) 的情況下呼叫 [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) 時，才會顯示呼叫堆疊。

CLR 2.0 中新增了稱為 *VM Hoarding* 的功能，對於經常取得再釋放區段 (包括在大型與小型物件堆積上) 的案例，此功能非常有用。 若要指定 VM Hoarding，您可以透過裝載 API 指定稱為 `STARTUP_HOARD_GC_VM` 的啟動旗標。 CLR 會取消認可這些區段上的記憶體並將其放置於待命清單上，而不會將空的區段釋放歸還給 OS。 (請注意，CLR 不會對太大的區段執行這項操作)。CLR 稍後會使用這些區段來滿足新的區段要求。 下次您的應用程式需要新的區段時，CLR 如果能夠找到夠大的區段，就會使用此待命清單中的區段。

對於想要保存已取得區段以避免發生記憶體不足例外狀況的應用程式 (例如本身是系統上所執行之主控項應用程式的某些伺服器應用程式) 來說，VM hoarding 也很有用。

強烈建議您在使用這項功能時仔細測試應用程式，以確保應用程式的記憶體使用情形相當穩定。
