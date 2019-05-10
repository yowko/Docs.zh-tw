---
title: .NET Framework 中的效能計數器
ms.date: 03/30/2017
helpviewer_keywords:
- performance, .NET Framework applications
- performance counters
- performance monitoring, counters
ms.assetid: 06a4ae8c-eeb2-4d5a-817e-b1b95c0653e1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af558e6712d58e208bf05cdb7a0f847ec4517f0f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614302"
---
# <a name="performance-counters-in-the-net-framework"></a>.NET Framework 中的效能計數器
本主題提供一份您可以在中找到的效能計數器[Windows 效能監視器](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc749249%28v=ws.11%29)。  
  
- [例外狀況效能計數器](#exception)  
  
- [Interop 效能計數器](#interop)  
  
- [JIT 效能計數器](#jit)  
  
- [載入效能計數器](#loading)  
  
- [鎖定和執行緒效能計數器](#lockthread)  
  
- [記憶體效能計數器](#memory)  
  
- [網路效能計數器](#networking)  
  
- [安全性效能計數器](#security)  
  
<a name="exception"></a>   
## <a name="exception-performance-counters"></a>例外狀況效能計數器  
 效能主控台 .NET CLR 例外狀況分類包含計數器，此計數器提供應用程式擲回例外狀況的相關資訊。 下表描述的是這些效能計數器。  
  
|效能計數器|描述|  
|-------------------------|-----------------|  
|**# of Exceps Thrown**|顯示自應用程式啟動後擲回例外狀況的總數。 這包含 .NET 例外狀況和轉換成 .NET 例外狀況的 Unmanaged 例外狀況。 例如，從 Unmanaged 程式碼傳回的 HRESULT 會轉換成在 Managed 程式碼中的例外狀況。<br /><br /> 此計數器包含已處理和未處理的例外狀況。 重新擲回的例外狀況會再計算一次。|  
|**# of Exceps Thrown / Sec**|顯示每秒擲回的例外狀況數目。 這包含 .NET 例外狀況和轉換成 .NET 例外狀況的 Unmanaged 例外狀況。 例如，從 Unmanaged 程式碼傳回的 HRESULT 會轉換成在 Managed 程式碼中的例外狀況。<br /><br /> 此計數器包含已處理和未處理的例外狀況。 它不是時間累積下的平均數；它會顯示最後兩個樣本中觀察到的值之間的差異除以樣本間隔的持續時間。 此計數器是潛在的效能問題的指標，如果是大型 (> 100 個為單位) 擲回的例外狀況數。|  
|**# of Filters / Sec**|顯示每秒所執行的 .NET 例外狀況篩選數目。 不論例外狀況是否已處理，都會評估例外狀況篩選。<br /><br /> 這個計數器不是時間累積下的平均數；它會顯示最後兩個樣本中觀察到的值之間的差異除以樣本間隔的持續時間。|  
|**# of Finallys / Sec**|顯示每秒執行的 Finally 區塊數目。 不論 Try 區塊如何結束，都保證會執行 Finally 區塊。  只有例外狀況的 Finally 區塊會被列入計算；該計數器不會把正常程式碼路徑上的 Finally 區塊列入計算。<br /><br /> 這個計數器不是時間累積下的平均數；它會顯示最後兩個樣本中觀察到的值之間的差異除以樣本間隔的持續時間。|  
|**Throw to Catch Depth / Sec**|顯示從擲回例外狀況的框架周遊到處理例外狀況的框架之每秒堆疊框架數目。 當進入例外狀況處理常式時，此計數器會重設為零，因此巢狀例外狀況會顯示處理常式至處理常式的堆疊深度。<br /><br /> 這個計數器不是時間累積下的平均數；它會顯示最後兩個樣本中觀察到的值之間的差異除以樣本間隔的持續時間。|  
  
<a name="interop"></a>   
## <a name="interop-performance-counters"></a>Interop 效能計數器  
 效能主控台 .NET CLR Interop 分類包含計數器，此計數器提供應用程式與 COM 元件、COM + 服務以及外部類型程式庫互動的相關資訊。 下表描述的是這些效能計數器。  
  
|效能計數器|描述|  
|-------------------------|-----------------|  
|**# of CCWs**|顯示目前的 COM 可呼叫包裝函式 (CCW) 數目。 CCW 是被 Unmanaged 的 COM 用戶端所參考的 Managed 物件之 Proxy。 這個計數器表示被 Unmanaged 的 COM 程式碼所參考的 Managed 物件數目。|  
|**# of marshaling**|顯示自應用程式啟動後，已從 Managed 程式碼封送處理引數和傳回值至 Unmanaged 程式碼的總次數，反之亦然。 如果虛設常式是內嵌的，則不會遞增此計數器。 (虛設常式負責封送處理引數和傳回值)。 如果封送處理額外負荷很小，則虛設常式通常是內嵌的。|  
|**# of Stubs**|顯示目前由 Common Language Runtime 所建立的虛設常式數目。 在 COM Interop 呼叫或平台叫用呼叫期間，虛設常式負責從 Managed 程式碼封送處理引數和傳回值至 Unmanaged程式碼，反之亦然。|  
|**# of TLB exports / sec**|保留供未來使用。|  
|**# of TLB imports / sec**|保留供未來使用。|  
  
<a name="jit"></a>   
## <a name="jit-performance-counters"></a>JIT 效能計數器  
 效能主控台 .NET CLR JIT 分類包含計數器，此計數器提供經 JIT 編譯之程式碼的相關資訊。 下表描述的是這些效能計數器。  
  
|效能計數器|描述|  
|-------------------------|-----------------|  
|**# of IL Bytes JITted**|顯示自啟動應用程式後，在 Just-In-Time (JIT) 編譯器所編譯的 Microsoft 中繼語言 (MSIL) 位元組總數。 此計數器相當於 **Total # of IL Bytes Jitted** 計數器。|  
|**# of Methods JITted**|顯示自應用程式啟動後被 JIT 編譯的方法總數。 此計數器不包含先行 JIT 編譯完成的方法。|  
|**% Time in Jit**|顯示在自上次的 JIT 編譯階段後，花費在 JIT 編譯上的已耗用時間百分比。 在每個 JIT 編譯階段的結尾會更新此計數器。 JIT 編譯階段發生於當方法和其相依性被編譯時。|  
|**IL Bytes Jitted / sec**|顯示每秒被 JIT 編譯的 MSIL 位元組數目。 這個計數器不是時間累積下的平均數；它會顯示最後兩個樣本中觀察到的值之間的差異除以樣本間隔的持續時間。|  
|**Standard Jit Failures**|顯示自應用程式啟動後 JIT 編譯器已編譯失敗的方法之最高數量。 無法驗證 MSIL 或者在 JIT 編譯器中有內部錯誤時，就會發生此失敗。|  
|**Total # of IL Bytes Jitted**|顯示自應用程式啟動後被 JIT 編譯的 MSIL 總計位元組數。 此計數器相當於 **# of IL Bytes Jitted** 計數器。|  
  
<a name="loading"></a>   
## <a name="loading-performance-counters"></a>載入效能計數器  
 效能主控台 .NET CLR 載入分類包含計數器，此計數器提供已載入組件、類別和應用程式定義域的相關資訊。 下表描述的是這些效能計數器。  
  
|效能計數器|描述|  
|-------------------------|-----------------|  
|**% Time Loading**|保留供未來使用。|  
|**Assembly Search Length**|保留供未來使用。|  
|**Bytes in Loader Heap**|顯示目前在所有應用程式定義域中類別載入器認可的記憶體大小，以位元組為單位。 認可的記憶體是在磁碟分頁檔上保留的實體空間。|  
|**Current appdomains**|顯示目前在此應用程式中已載入的應用程式定義域數目。|  
|**Current Assemblies**|顯示在目前執行的應用程式中的所有應用程式定義域裡已載入的目前組件數目。 如果自多重應用程式定義域載入定義域中性組件，則此計數器只會遞增一次。|  
|**Current Classes Loaded**|顯示目前在所有組件中已載入的類別數目。|  
|**Rate of appdomains**|顯示每秒已載入的應用程式定義域數目。 這個計數器不是時間累積下的平均數；它會顯示最後兩個樣本中觀察到的值之間的差異除以樣本間隔的持續時間。|  
|**Rate of appdomains unloaded**|顯示每秒已卸載的應用程式定義域數目。 這個計數器不是時間累積下的平均數；它會顯示最後兩個樣本中觀察到的值之間的差異除以樣本間隔的持續時間。|  
|**Rate of Assemblies**|顯示每秒在所有應用程式定義域中已載入的組件數目。 如果自多重應用程式定義域載入定義域中性組件，則此計數器只會遞增一次。<br /><br /> 這個計數器不是時間累積下的平均數；它會顯示最後兩個樣本中觀察到的值之間的差異除以樣本間隔的持續時間。|  
|**Rate of Classes Loaded**|顯示每秒在所有組件中已載入的類別數目。 這個計數器不是時間累積下的平均數；它會顯示最後兩個樣本中觀察到的值之間的差異除以樣本間隔的持續時間。|  
|**Rate of Load Failures**|顯示每秒無法載入的類別數目。 這個計數器不是時間累積下的平均數；它會顯示最後兩個樣本中觀察到的值之間的差異除以樣本間隔的持續時間。<br /><br /> 發生載入失敗可能有許多原因，例如不當的安全性或無效的格式。 如需詳細資料，請參閱分析服務說明。|  
|**Total # of Load Failures**|顯示自啟動應用程式後類別無法載入的最高數量。<br /><br /> 發生載入失敗可能有許多原因，例如不當的安全性或無效的格式。 如需詳細資料，請參閱分析服務說明。|  
|**Total Appdomains**|顯示自應用程式啟動後已載入應用程式定義域的最高數量。|  
|**Total appdomains unloaded**|顯示自應用程式啟動後已卸載應用程式定義域的總數。 如果應用程式定義域已載入並已卸載多次，此計數器會在每次應用程式定義域已卸載時遞增。|  
|**Total Assemblies**|顯示自應用程式啟動後已載入組件的總數。 如果自多重應用程式定義域載入定義域中性組件，則此計數器只會遞增一次。|  
|**Total Classes Loaded**|顯示自啟動應用程式後在所有組件中已載入類別的累計數量。|  
  
<a name="lockthread"></a>   
## <a name="lock-and-thread-performance-counters"></a>鎖定和執行緒效能計數器  
 效能主控台 .NET CLR LocksAndThreads 分類包含計數器，此計數器提供應用程式使用之 Managed 鎖定及執行緒的相關資訊。 下表描述的是這些效能計數器。  
  
|效能計數器|描述|  
|-------------------------|-----------------|  
|**# of current logical Threads**|顯示目前在應用程式中 Managed 執行緒物件數目。 此計數器會維持執行中的和已停止的執行緒計數。 這個計數器不是時間累積下的平均數；它僅顯示最後觀察到的值。|  
|**# of current physical Threads**|顯示由 Common Language Runtime 建立及擁有的原生作業系統執行緒數目，這些執行緒用來做為 Managed 執行緒物件的基礎執行緒。 此計數器的值不包含在內部作業中執行階段所使用的執行緒；它是作業系統處理序中執行緒的子集。|  
|**# of current recognized threads**|顯示目前執行階段所辨識的執行緒數目。 這些執行緒會與對應的 Managed 執行緒物件相關聯。 執行階段不會建立這些執行緒，但是它們必須在執行階段內至少執行一次。<br /><br /> 只有唯一的執行緒會被追蹤；在執行緒結束後重新進入執行階段或重新建立的具有相同執行緒 ID 之執行緒不會被計算兩次。|  
|**# of total recognized Threads**|顯示自啟動應用程式後執行階段已辨識的執行緒總數。 這些執行緒會與對應的 Managed 執行緒物件相關聯。 執行階段不會建立這些執行緒，但是它們必須在執行階段內至少執行一次。<br /><br /> 只有唯一的執行緒會被追蹤；在執行緒結束後重新進入執行階段或重新建立的具有相同執行緒 ID 之執行緒不會被計算兩次。|  
|**Contention Rate / Sec**|顯示執行緒在執行階段無法順利嘗試擷取 Managed 鎖定的速率。|  
|**Current Queue Length**|顯示目前在應用程式中等待擷取 Managed 鎖定的執行緒總數。 這個計數器不是時間累積下的平均數；它顯示最後觀察到的值。|  
|**Queue Length / sec**|顯示每秒在應用程式中等待擷取鎖定的執行緒數目。 這個計數器不是時間累積下的平均數；它會顯示最後兩個樣本中觀察到的值之間的差異除以樣本間隔的持續時間。|  
|**Queue Length Peak**|顯示自應用程式啟動後等待擷取 Managed 鎖定的執行緒總數。|  
|**rate of recognized threads / sec**|顯示每秒執行階段所辨識的執行緒數目。 這些執行緒會與對應的 Managed 執行緒物件相關聯。 執行階段不會建立這些執行緒，但是它們必須在執行階段內至少執行一次。<br /><br /> 只有唯一的執行緒會被追蹤；在執行緒結束後重新進入執行階段或重新建立的具有相同執行緒 ID 之執行緒不會被計算兩次。<br /><br /> 這個計數器不是時間累積下的平均數；它會顯示最後兩個樣本中觀察到的值之間的差異除以樣本間隔的持續時間。|  
|**Total # of Contentions**|顯示執行緒在執行階段無法順利嘗試擷取 Managed 鎖定的總次數。|  
  
<a name="memory"></a>   
## <a name="memory-performance-counters"></a>記憶體效能計數器  
 效能主控台 .NET CLR 記憶體分類包含計數器，此計數器提供記憶體回收行程的相關資訊。 下表描述的是這些效能計數器。  
  
|效能計數器|描述|  
|-------------------------|-----------------|  
|**# Bytes in all Heaps**|顯示 **Gen 1 Heap Size**、**Gen 2 Heap Size** 和 **Large Object Heap Size** 計數器的總和。 這個計數器表示目前在記憶體回收堆積中配置的記憶體，以位元組為單位。|  
|**# GC Handles**|顯示目前使用中的記憶體回收控制代碼的數目。 記憶體回收控制代碼是 Common Language Runtime 和 Managed 環境的外部資源控制代碼。|  
|**# Gen 0 Collections**|顯示自應用程式啟動後層代 0 物件 (也就是最新且最近配置的物件) 被記憶體回收的次數。<br /><br /> 當層代 0 中可用的記憶體不足以滿足配置要求時，就會發生層代 0 記憶體回收。 此計數器會在層代 0 記憶體回收的結尾遞增。 較高的層代記憶體回收包含所有較低層代的回收。 當較高的層代 (層代 1 或 2) 記憶體回收發生時，這個計數器會明確地遞增。<br /><br /> 此計數器會顯示最後觀察到的值。 **_Global\_** 計數器的值不精確，應該予以忽略。|  
|**# Gen 1 Collections**|顯示自應用程式啟動後層代 1 物件被記憶體回收的次數。<br /><br /> 此計數器會在層代 1 記憶體回收的結尾遞增。 較高的層代記憶體回收包含所有較低層代的回收。 當較高的層代 (層代 2) 記憶體回收發生時，這個計數器會明確地遞增。<br /><br /> 此計數器會顯示最後觀察到的值。 **_Global\_** 計數器的值不精確，應該予以忽略。|  
|**# Gen 2 Collections**|顯示自應用程式啟動後層代 2 物件被記憶體回收的次數。 此計數器會在層代 2 記憶體回收的結尾遞增 (也稱為完整記憶體回收)。<br /><br /> 此計數器會顯示最後觀察到的值。 **_Global\_** 計數器的值不精確，應該予以忽略。|  
|**# Induced GC**|顯示因為明確呼叫 <xref:System.GC.Collect%2A?displayProperty=nameWithType> 而執行記憶體回收的最高次數。 最佳作法是讓記憶體回收行程調整其回收的頻率。|  
|**# of Pinned Objects**|顯示發生在最後一次記憶體回收中的 Pin 物件數目。 Pin 物件是記憶體回收行程無法在記憶體中移動的物件。 這個計數器只會在已經過記憶體回收的堆積中追蹤 Pin 物件。 例如，層代 0 記憶體回收造成只能在層代 0 堆積中列舉 Pin 物件。|  
|**# of Sink Blocks in use**|顯示目前使用中的同步區塊數目。 同步區塊為配置來儲存同步處理資訊之每一物件的資料結構。 它們會保存 Managed 物件的弱式參考，且必須由記憶體回收行程進行掃描。 同步區塊並不僅限於儲存同步處理資訊；它們也可以儲存 COM Interop 中繼資料。 此計數器表示大量使用同步處理原始物件的效能問題。|  
|**# Total committed Bytes**|顯示記憶體回收行程目前已認可的虛擬記憶體數目 (以位元組為單位)。 認可的記憶體是在磁碟分頁檔上已保留其空間的實體記憶體。|  
|**# Total reserved Bytes**|顯示記憶體回收行程目前保留的虛擬記憶體數目 (以位元組為單位)。 保留的記憶體是指在未使用磁碟或主記憶體分頁時，為應用程式保留的虛擬記憶體空間。|  
|**% Time in GC**|顯示自上次記憶體回收循環後所花費在執行記憶體回收的已耗用時間百分比。 這個計數器通常表示記憶體回收行程代表應用程式來回收和壓縮記憶體時所完成的工作。 這個計數器僅於每次記憶體回收的結尾更新。 這個計數器不是平均數；它的值反映最後觀察到的值。|  
|**Allocated Bytes/second**|顯示每秒在記憶體回收堆積上配置的位元組數目。 這個計數器於每次記憶體回收的結尾更新，而非每次配置時更新。 這個計數器不是時間累積下的平均數；它會顯示最後兩個樣本中觀察到的值之間的差異除以樣本間隔的持續時間。|  
|**Finalization Survivors**|顯示由於等候最終處理而未被回收的記憶體回收物件數目。 如果這些物件保存其他物件的參考，則這些物件也不會被記憶體回收，但此計數器不會將它們列入計算。 **Promoted Finalization-Memory from Gen 0** 計數器代表所有因最終處理而殘留下來的記憶體。<br /><br /> 這個計數器不是累計的；它只會在每次記憶體回收的結尾更新為該特定回收期間未回收物件的計數。 這個計數器表示因為最終處理而可能使應用程式造成的額外負荷。|  
|**Gen 0 heap size**|顯示可配置在層代 0 的最大位元組數目；它並不表示目前在層代 0 中配置的位元組數目。<br /><br /> 當上次回收後的配置超過此大小，就會發生層代 0 記憶體回收。 層代 0 大小由記憶體回收行程調整，而且可以在應用程式執行期間變更。 在層代 0 回收的結尾，層代 0 堆積會是 0 個位元組。 此計數器顯示叫用下一個層代 0 記憶體回收的配置大小，以位元組為單位。<br /><br /> 這個計數器於記憶體回收的結尾更新，而非每次配置時更新。|  
|**Gen 0 Promoted Bytes/Sec**|顯示每秒從層代 0 提升至層代 1 的位元組。 當記憶體未被回收時，記憶體就會被提升。 此計數器是每秒所建立的相對存留較久物件的指示器。<br /><br /> 這個計數器會顯示最後兩個樣本中觀察到的值之間的差異除以樣本間隔的持續時間。|  
|**Gen 1 heap size**|顯示目前層代 1 中的位元組數目；此計數器不會顯示層代 1 的最大大小。 在此層代中不會直接配置物件；它們會從上一個層代 0 記憶體回收提升。 這個計數器於記憶體回收的結尾更新，而非每次配置時更新。|  
|**Gen 1 Promoted Bytes/Sec**|顯示每秒從層代 1 提升至層代 2 的位元組。 只因等候最終處理而提升的物件並不包含在此計數器內。<br /><br /> 當記憶體未被回收時，記憶體就會被提升。 層代 2 中沒有任何提升，因為這是最舊的層代。 此計數器是每秒所建立的存留最久物件的指示器。<br /><br /> 這個計數器會顯示最後兩個樣本中觀察到的值之間的差異除以樣本間隔的持續時間。|  
|**Gen 2 heap size**|顯示目前層代 2 中的位元組數目。 在此層代中不會直接配置物件；它們會在上一次層代 1 記憶體回收期間從層代 1 提升。 這個計數器於記憶體回收的結尾更新，而非每次配置時更新。|  
|**Large Object Heap size**|顯示目前大型物件堆積的大小，以位元組為單位。 記憶體回收行程會將大於約 85,000 個位元組的物件視為大型物件處理，並且在特殊堆積中直接配置；這些物件不會透過不同層代升級。 這個計數器於記憶體回收的結尾更新，而非每次配置時更新。|  
|**處理序 ID**|顯示所監視之 CLR 處理序執行個體的處理序 ID。|  
|**Promoted Finalization-Memory from Gen 0**|顯示只因等待最終處理而從層代 0 提升至層代 1 的記憶體位元組數。 這個計數器不是累計的；它會顯示在上一次記憶體回收的結尾觀察到的值。|  
|**Promoted Memory from Gen 0**|顯示未被記憶體回收，且從層代 0 提升至層代 1 的記憶體位元組數。 只因等候最終處理而提升的物件並不包含在此計數器內。 這個計數器不是累計的；它會顯示在上一次記憶體回收的結尾觀察到的值。|  
|**Promoted Memory from Gen 1**|顯示未被記憶體回收，且從層代 1 提升至層代 2 的記憶體位元組數。 只因等候最終處理而提升的物件並不包含在此計數器內。 這個計數器不是累計的；它會顯示在上一次記憶體回收的結尾觀察到的值。 若上一次記憶體回收僅為層代 0 回收，則此計數器會重設為 0。|  
  
<a name="networking"></a>   
## <a name="networking-performance-counters"></a>網路效能計數器  
 效能主控台 .NET CLR Networking 分類包含計數器，此計數器提供應用程式在網路上傳送和接收資料的相關資訊。 下表描述的是這些效能計數器。  
  
|效能計數器|描述|  
|-------------------------|-----------------|  
|**Bytes Received**|自處理序啟動後，由 <xref:System.AppDomain> 中的所有 <xref:System.Net.Sockets.Socket> 物件接收的累計位元組總數。 此數目包含資料和任何未經 TCP/IP 定義的通訊協定資訊。|  
|**Bytes Sent**|自處理序啟動後，由 <xref:System.AppDomain> 中的所有 <xref:System.Net.Sockets.Socket> 物件傳送的累計位元組數。 此數目包含資料和任何未經 TCP/IP 定義的通訊協定資訊。|  
|**Connections Established**|自處理序啟動後，曾在 <xref:System.AppDomain> 中連接的 <xref:System.Net.Sockets.Socket> 累計資料流通訊端物件總數。|  
|**Datagrams Received**|自處理序啟動後，由 <xref:System.AppDomain> 中的所有 <xref:System.Net.Sockets.Socket> 物件接收的累計資料包封包總數。|  
|**Datagrams Sent**|自處理序啟動後，由 <xref:System.AppDomain> 中的所有 <xref:System.Net.Sockets.Socket> 物件傳送的累計資料包封包總數。|  
|**HttpWebRequest Average Lifetime**|自處理序開始後，完成在 <xref:System.AppDomain> 中最後一個間隔結束的所有 <xref:System.Net.HttpWebRequest> 物件的平均時間。|  
|**HttpWebRequest Average Queue Time**|自處理序開始後，在 <xref:System.AppDomain> 中最後一個間隔離開佇列的所有 <xref:System.Net.HttpWebRequest> 物件的平均佇列中時間。|  
|**HttpWebRequests Created/sec**|每秒在 <xref:System.AppDomain> 中，建立的 <xref:System.Net.HttpWebRequest> 物件數目。|  
|**HttpWebRequests Queued/sec**|每秒在 <xref:System.AppDomain> 中，加入至佇列的 <xref:System.Net.HttpWebRequest> 物件數目。|  
|**HttpWebRequests Aborted/sec**|每秒應用程式在 <xref:System.AppDomain> 中，呼叫 <xref:System.Net.HttpWebRequest.Abort%2A> 方法的 <xref:System.Net.HttpWebRequest> 物件數目。|  
|**HttpWebRequests Failed/sec**|每秒在 <xref:System.AppDomain> 中，從伺服器接收失敗狀態碼的 <xref:System.Net.HttpWebRequest> 物件數目。|  
  
 支援許多類別的網路效能計數器：  
  
- 測量某些事件發生次數的事件計數器。  
  
- 測量傳送或接收資料數量的資料計數器。  
  
- 測量不同處理序費時多久的持續期間計數器。 在物件從不同狀態送出後，測量物件在每個間隔的時間 (通常以秒為單位)。  
  
- 測量每個間隔中正在進行特定轉換之物件數目的每個間隔計數器 (一般而言以秒為單位)。  
  
 事件的網路效能計數器包含下列各項：  
  
- **Connections Established**  
  
- **Datagrams Received**  
  
- **Datagrams Sent**  
  
 這些效能計數器提供自處理序啟動後的計數。 已建立的 <xref:System.Net.Sockets.Socket> 連接計數包含應用程式為了已建立的資料流通訊端連接而呼叫的明確 <xref:System.Net.Sockets.Socket> 方法，以及由其他類別 (例如：<xref:System.Net.HttpWebRequest>、<xref:System.Net.FtpWebRequest>、<xref:System.Net.WebClient> 和 <xref:System.Net.Sockets.TcpClient>) 向 <xref:System.Net.Sockets.Socket> 類別所進行的呼叫。  
  
 **Datagrams Received** 和 **Datagrams Sent** 計數包含應用程式使用明確的 <xref:System.Net.Sockets.Socket> 方法呼叫，以及其他類別 (例如 <xref:System.Net.Sockets.UdpClient>) 對 <xref:System.Net.Sockets.Socket> 進行的內部呼叫，所傳送或接收的資料包封包。 類別的新執行個體。 在假定資料包的平均大小之下，**Datagrams Received** 和 **Datagrams Sent** 計數也可用來粗略測量有多少使用資料包傳送或接收的位元組。  
  
 資料的網路效能計數器包含下列各項：  
  
- **Bytes Received**  
  
- **Bytes Sent**  
  
 上述效能計數器提供自處理序啟動後的位元組計數。  
  
 有二種持續期間計數器來測量 <xref:System.Net.HttpWebRequest> 物件通過其整個生命週期或僅通過其中一部分要費時多久：  
  
- **HttpWebRequest Average Lifetime**  
  
- **HttpWebRequest Average Queue Time**  
  
 針對 **HttpWebRequest Average Lifetime** 計數器，大部分 <xref:System.Net.HttpWebRequest> 物件的存留期永遠都是從建立物件之際開始計算，直到應用程式關閉回應資料流為止。 有二種不常見的情況：  
  
- 若應用程式永不呼叫 <xref:System.Net.HttpWebRequest.GetResponse%2A> 或 <xref:System.Net.HttpWebRequest.BeginGetResponse%2A> 方法，則會忽略 <xref:System.Net.HttpWebRequest> 物件的存留期。  
  
- 若在呼叫 <xref:System.Net.HttpWebRequest.GetResponse%2A> 或 <xref:System.Net.HttpWebRequest.EndGetResponse%2A> 方法時，<xref:System.Net.HttpWebRequest> 物件擲回 <xref:System.Net.WebException>，則存留期會在例外狀況擲回後結束。 技術上來說，此時也會關閉基礎回應資料流 (傳回給使用者的回應資料流實際上是包含回應資料流複本的記憶體資料流)。  
  
 有四種計數器會追蹤每個間隔的特定 <xref:System.Net.HttpWebRequest> 物件問題。 這些效能計數器可協助應用程式開發人員、系統管理員及支援人員進一步了解 <xref:System.Net.HttpWebRequest> 物件的用途。 這些計數器包含下列各項：  
  
- **HttpWebRequests Created/sec**  
  
- **HttpWebRequests Queued/sec**  
  
- **HttpWebRequests Aborted/sec**  
  
- **HttpWebRequests Failed/sec**  
  
 針對 **HttpWebRequests Aborted/sec** 計數器，對 <xref:System.Net.HttpWebRequest.Abort%2A> 的內部呼叫也會列入計算。 這些內部呼叫通常由應用程式想測量的逾時所造成。  
  
 **HttpWebRequests Failed/sec** 計數器包含每秒從伺服器接收失敗狀態碼的 <xref:System.Net.HttpWebRequest> 物件數目。 這表示在要求的結尾收到來自 HTTP 伺服器的狀態碼不是介於 200 到 299 之間。 已處理並產生新要求 (例如許多 401 未經授權的狀態碼) 的狀態碼是否失敗將依據重試結果而定。 如果應用程式依據重試結果看到錯誤，則此計數器會遞增。  
  
 網路效能計數器可以使用 <xref:System.Diagnostics.PerformanceCounter> 和在 <xref:System.Diagnostics> 命名空間中的相關類別存取及管理。 網路效能計數器也可以使用 Windows 效能監視器主控台檢視。  
  
 需要在組態檔中啟用，才能使用網路效能計數器。 藉由組態檔中的單一設定可啟用或停用所有網路效能計數器。 不能啟用或停用個別的網路效能計數器。 如需詳細資訊，請參閱 [\<performanceCounter> 項目 (網路設定)](../../../docs/framework/configure-apps/file-schema/network/performancecounter-element-network-settings.md)。  
  
 如果已啟用網路計數器，這會建立並更新每個 AppDomain 和全域效能計數器。 如果停用，應用程式不會提供任何網路效能計數器資料。  
  
 效能計數器分為幾個類別。 應用程式可用下列範例程式碼列出所有類別：  
  
```csharp
PerformanceCounterCategory[] Array = PerformanceCounterCategory.GetCategories();  
for (int i = 0; i < Array.Length; i++)  
{  
    Console.Out.WriteLine("{0}. Name={1} Help={2}", i, Array[i].CategoryName, Array[i].CategoryHelp);  
}  
```  
  
 網路效能計數器會列在兩個類別：  
  
- 「.NET CLR 網路」- 由 .NET Framework 版本 2 導入的原始效能計數器，受 .NET Framework 版本 2 和更新版本支援。  
  
- 「.NET CLR 網路 4.0.0.0」 - 上述所有通訊端計數器再加上 .NET Framework 第 4 版及更新版本所支援的新效能計數器。 這些新的計數器會提供 <xref:System.Net.HttpWebRequest> 物件的效能資訊 。  
  
 如需存取和管理應用程式中效能計數器的詳細資訊，請參閱[效能計數器](../../../docs/framework/debug-trace-profile/performance-counters.md)。  
  
<a name="security"></a>   
## <a name="security-performance-counters"></a>安全性效能計數器  
 效能主控台 .NET CLR 安全性類別包含計數器，此計數器提供 Common Language Runtime 為應用程式執行安全性檢查的相關資訊。 下表描述的是這些效能計數器。  
  
|效能計數器|描述|  
|-------------------------|-----------------|  
|**# Link Time Checks**|顯示自應用程式啟動後連結時間程式碼存取安全性檢查的總數。 當呼叫端在 Just-In-Time (JIT) 編譯階段要求特定權限，則會執行連結時間程式碼存取安全性檢查。 對於每個呼叫端各執行一次連結時間檢查。 該計數並不表示嚴重的效能問題；它只會表示安全性系統的活動。|  
|**% Time in RT checks**|自上一個樣本後，顯示花費在執行執行階段程式碼存取安全性檢查的已耗用時間百分比。 此計數器會在 .NET Framework 安全性檢查的結尾時更新。 這不是平均數；它代表最後觀察到的值。|  
|**% Time Sig Authenticating**|保留供未來使用。|  
|**Stack Walk Depth**|在最後一個執行階段程式碼存取安全性檢查期間顯示堆疊深度。 執行階段程式碼存取安全性檢查都是藉由查核堆疊來執行的。 這個計數器不是平均數；它僅顯示最後觀察到的值。|  
|**Total Runtime Checks**|顯示自應用程式啟動後執行階段程式碼存取安全性檢查執行的總數。 當呼叫端要求特定權限時，會執行執行階段程式碼存取安全性檢查。 執行階段檢查在每次由呼叫端呼叫時進行，並且檢查目前呼叫端的執行緒堆疊。 搭配使用 **Stack Walk Depth** 計數器時，此計數器指出因安全性檢查而發生的效能降低。|  
  
## <a name="see-also"></a>另請參閱

- [效能計數器](../../../docs/framework/debug-trace-profile/performance-counters.md)
- [執行階段分析](../../../docs/framework/debug-trace-profile/runtime-profiling.md)
