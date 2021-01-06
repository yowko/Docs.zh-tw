---
title: 適用于 .NET 的 SOS 偵錯工具擴充功能
description: 瞭解適用于 .NET 的 SOS 偵錯工具擴充功能，其提供內部 CLR 環境的相關資訊。
ms.date: 12/21/2020
helpviewer_keywords:
- debugging extensions
- SOS debugging extensions
- SOS.dll
ms.openlocfilehash: a24b946c4ffda59e17f61c065d2846dc1a6effe0
ms.sourcegitcommit: c0b803bffaf101e12f071faf94ca21b46d04ff30
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/24/2020
ms.locfileid: "97764964"
---
# <a name="sos-debugging-extension"></a>SOS 調試延伸模組

SOS 偵錯工具擴充功能可讓您在即時程式和傾印上，查看在 .NET Core 執行時間內執行之程式碼的相關資訊。 此擴充功能會預先安裝 [dotnet](dotnet-dump.md) 傾印和 [Windbg/dbg](/windows-hardware/drivers/debugger/debugger-download-tools)，並且可以 [下載](dotnet-sos.md) 以搭配 LLDB 使用。  SOS 偵錯工具擴充功能適合用來收集 managed 堆積的相關資訊、尋找堆積損毀、顯示執行時間所使用的內部資料類型，以及查看執行時間內執行之所有 managed 程式碼的相關資訊。

## <a name="syntax"></a>語法

### <a name="windows"></a>Windows

`![command] [options]`

### <a name="linux-and-macos"></a>Linux 與 macOS

`sos [command] [options]`

許多命令在 lldb 底下都有別名或快捷方式：

`clrstack [options]`

## <a name="commands"></a>命令

下列命令表格也可在 [說明] **或** [ **soshelp**] 底下取得。  您可以使用個別的命令說明 `soshelp <command>` 。

|命令|描述|
|-------------|-----------------|
|**bpmd** [**-nofuturemodule**] [ \<*module name*> \<*method name*> ] [**-md**  < `MethodDesc`>] **-list** **-clear** \<*pending breakpoint number*> **->-clearall**|在所指定模組中的指定方法上建立中斷點。<br /><br /> 如果指定的模組和方法尚未載入，這個命令便會在建立中斷點之前，等待已載入模組和已完成 Just-in-Time (JIT) 編譯的通知。<br /><br /> 您可以使用 **-list**、**-clear** 和 **-clearall** 選項來管理暫止中斷點的清單：<br /><br /> **-list** 選項會產生所有暫止中斷點的清單。 如果暫止中斷點具有非零的模組 ID，就是該特殊載入模組中函式的特定中斷點。 如果暫止中斷點具有零模組 ID，該中斷點就會套用至尚未載入的模組。<br /><br /> 使用 **-clear** 或 **-clearall** 選項可從清單中移除暫止中斷點。|
|**>clrstack** [**-a**] [**-l**] [**-p**] [**-n**] [**-f**] [**-r**] [**-all**]|僅提供 Managed 程式碼的堆疊追蹤。<br /><br /> **-p** 選項會顯示 Managed 函式的引數。<br /><br /> **-l** 選項會顯示框架中區域變數的相關資訊。 SOS 偵錯工具擴充功能無法取出區功能變數名稱稱，因此區功能變數名稱稱的輸出格式為 \<*local address*> **=** \<*value*> 。<br /><br /> **-A** 選項是 **-l** 和 **-p** 組合的快捷方式。<br /><br /> **-n** 選項會停用原始程式檔名稱和行號的顯示。 如果偵錯工具有指定 SYMOPT_LOAD_LINES 選項，SOS 將會查詢每個 Managed 框架的符號，而且如果成功，就會顯示對應的原始程式檔名稱和行號。 指定 **-n** (沒有行號) 參數即可停用這種行為。<br /><br /> (full 模式) 的 **-f** 選項會顯示原生框架，混合使用 managed 框架以及 managed 框架的元件名稱和函式位移。  搭配使用時，此選項不會顯示原生框架 `dotnet-dump` 。<br /><br />**-R** 選項會傾印每個堆疊框架的暫存器。<br /><br />**-All** 選項會傾印所有 managed 執行緒的堆疊。|
|**COMState**|列出每個執行緒和 `Context` 指標的 COM Apartment Model (如果有)。 只有在 Windows 上才支援這個命令。|
|**DumpArray** [**-start** \<*startIndex*> ] [**-length** \<*length*> ] [**-details**] [**-nofields**] \<*array object address*><br /><br /> -或-<br /><br /> **DA** [**-start** \<*startIndex*> ] [**-length** \<*length*> ] [**-detail**] [**-nofields**] *陣列物件位址*>|檢查陣列物件的元素。<br /><br /> **-start** 選項會指定開始顯示項目的索引。<br /><br /> **-length** 選項會指定要顯示多少項目。<br /><br /> **-details** 選項會使用 **DumpObj** 和 **DumpVC** 格式來顯示項目的詳細資料。<br /><br /> **-nofields** 選項會防止陣列顯示。 這個選項只有在指定 **-detail** 選項時才能使用。|
|**DumpAsync** (**DumpAsync**) [**-mt** \<*MethodTable address*> ] [**-type** \<*partial type name*> ] [**-等候**] [**-根目錄**]|DumpAsync 會進行垃圾收集的堆積，尋找代表非同步狀態機器的物件（當非同步方法的狀態傳送到堆積時建立）。  此命令會辨識定義為、、 `async void` `async Task` `async Task<T>` 、和的 `async ValueTask` 非同步狀態機器 `async ValueTask<T>` 。<br /><br />輸出中會包含每個找到的非同步狀態機器物件的詳細資料區塊。 這些詳細資料包括：<br />-非同步狀態機器物件的型別行，包括其 MethodTable 位址、其物件位址、大小，以及其型別名稱。<br />-包含在物件中之狀態機器類型名稱的行。<br />-狀態機器上的每個欄位清單。<br />-此狀態機器物件的接續行（如果有一或多個已註冊）。<br />-探索到這個非同步狀態機器物件的 GC 根。<br />|
|**DumpAssembly**\<*assembly address*>|顯示關於組件的資訊。<br /><br /> **DumpAssembly** 命令會列出多個模組 (如果這些模組存在)。<br /><br /> 您可以使用 **DumpDomain** 命令取得組件位址。|
|**DumpClass**\<*EEClass address*>|顯示與某個類型關聯之 `EEClass` 結構的資訊。<br /><br /> **DumpClass** 命令會顯示靜態欄位值，但不會顯示非靜態欄位值。<br /><br /> 使用 **DumpMT**、**DumpObj**、**Name2EE** 或 **Token2EE** 命令，以取得 `EEClass` 結構位址。|
|**>dumpdomain** [ \<*domain address*> ]|列舉載入於所指定 <xref:System.Reflection.Assembly> 物件位址內的每個 <xref:System.AppDomain> 物件。  當不使用參數進行呼叫時，**DumpDomain** 命令便會列出處理序中的所有 <xref:System.AppDomain> 物件。 由於 .NET Core 只有一個 <xref:System.AppDomain> ，因此 **>dumpdomain** 只會傳回一個物件。|
|**DumpHeap** [**-stat**] [**-strings**] [**-short**] [**-min** \<*size*> ] [**-max** \<*size*> ] [**-thinlock**] [**-startAtLowerBound**] [**-mt** \<*MethodTable address*> ] [**-type** \<*partial type name*> ] [*start* [*end*]]|顯示記憶體回收堆積的資訊，以及關於物件的回收統計資料。<br /><br /> **DumpHeap** 命令會在偵測到記憶體回收行程堆積中出現過多分割時顯示警告。<br /><br /> **-stat** 選項會將輸出限制為統計類型摘要。<br /><br /> **-strings** 選項會將輸出限制為統計字串值摘要。<br /><br /> **-short** 選項會將輸出限制為每個物件的位址。 這可讓您輕鬆地將輸出從命令由管道送到另一個偵錯工具命令以達成自動化。<br /><br /> **-min** 選項會忽略小於 `size` 參數的物件 (指定單位為位元組)。<br /><br /> **-max** 選項會忽略大於 `size` 參數的物件 (指定單位為位元組)。<br /><br /> **-thinlock** 選項會報告 ThinLocks。  如需詳細資訊，請參閱 **SyncBlk** 命令。<br /><br /> `-startAtLowerBound` 選項會強制堆積查核從所提供之位址範圍的下限開始。 在規劃階段期間，因為物件正在移動，通常都無法查核堆積。 這個選項會強制 **DumpHeap** 在指定的下限開始其查核。 您必須提供有效物件的位址，做為讓此選項運作的下限。 您可以顯示位於錯誤物件之位址的記憶體，以手動方式找出下一個方法資料表。 如果記憶體回收目前位於 `memcopy` 的呼叫中，您也可以將大小加到起始位址 (以參數的形式提供)，以尋找下一個物件的位址。<br /><br /> **-mt** 選項只會列出會對應至所指定 `MethodTable` 結構中的那些物件。<br /><br /> **-type** 選項只會列出其類型名稱即為所指定字串之子字串的物件。<br /><br /> `start` 參數會從指定的位址開始列出。<br /><br /> `end` 參數會在指定的位址停止列出。|
|**DumpIL** \<*Managed DynamicMethod object*> &#124;       \<*DynamicMethodDesc pointer*> &#124;        \<*MethodDesc pointer*>|顯示與 Managed 方法相關聯的 Microsoft 中繼語言 (MSIL)。<br /><br /> 動態 MSIL 的發出方式與從元件載入的 MSIL 不同。 動態 MSIL 會參考 Managed 物件陣列中的物件，而非參考中繼資料語彙基元。|
|**DumpLog** [**-addr** \<*addressOfStressLog*> ] [<*Filename*>]|將記憶體中壓力記錄檔的內容寫入指定的檔案。 如果沒有指定名稱，此命令便會在目前的目錄中建立名為 StressLog.txt 的檔案。<br /><br /> 記憶體中的壓力記錄可協助您診斷壓力失敗而不必使用鎖定或 I/O。 若要啟用壓力記錄檔，請在 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework 底下設定下列登錄機碼：<br /><br /> (DWORD) StressLog = 1<br /><br /> (DWORD) LogFacility = 0xffffffff<br /><br /> (DWORD) StressLogSize = 65536<br /><br /> 選擇性的 `-addr` 選項可讓您指定預設記錄檔以外的壓力記錄檔。|
|**DumpMD**\<*MethodDesc address*>|在指定的位址顯示 `MethodDesc` 結構的相關資訊。<br /><br /> 您可以使用 **IP2MD** 命令，從 Managed 函式取得 `MethodDesc` 結構位址。|
|**DumpMT** [**-MD**] \<*MethodTable address*>|顯示在所指定位址之方法資料表的相關資訊。 指定 **-MD** 選項，便會顯示與物件一起定義之所有方法的清單。<br /><br /> 每個 Managed 物件都包含一個方法資料表指標。|
|**DumpModule** [**-mt**] \<*Module address*>|顯示在所指定位址之模組的相關資訊。 **-mt** 選項會顯示定義在模組中的類型，以及由該模組所參考的類型。<br /><br /> 您可以使用 **DumpDomain** 或 **DumpAssembly** 命令來擷取模組的位址。|
|**>dumpobj** [**-nofields**] \<*object address*><br /><br /> -或-<br /><br /> **DO**\<*object address*>|顯示在所指定位址之物件的相關資訊。 **DumpObj** 命令會顯示欄位、`EEClass` 結構資訊、方法資料表，以及物件的大小。<br /><br /> 您可以使用 **DumpStackObjects** 命令來擷取物件的位址。<br /><br /> 您可以在類型的欄位上執行 **>dumpobj** 命令， `CLASS` 因為它們也是物件。<br /><br /> `-`**nofields** 選項可防止物件的欄位顯示，這對像是 String 的物件非常有用。|
|**DumpRuntimeTypes**|顯示記憶體回收行程堆積中的執行階段類型物件，並列出與其關聯的類型名稱和方法資料表。|
|**DumpStack** [**-EE**] [**-n**] [ `top` *stack* [ `bottom` *stac* `k` ]]|顯示堆疊追蹤。<br /><br /> **-EE** 選項會使 **DumpStack** 命令只顯示 Managed 函式。 使用 `top` 和 `bottom` 參數可限制在 x86 平台上顯示的堆疊框架。<br /><br /> **-n** 選項會停用原始程式檔名稱和行號的顯示。 如果偵錯工具有指定 SYMOPT_LOAD_LINES 選項，SOS 將會查詢每個 Managed 框架的符號，而且如果成功，就會顯示對應的原始程式檔名稱和行號。 指定 **-n** (沒有行號) 參數即可停用這種行為。<br /><br />
|**DumpSig** \<*sigaddr*>\<*moduleaddr*>|在指定的位址顯示 `Sig` 結構的相關資訊。|
|**DumpSigElem** \<*sigaddr*>\<*moduleaddr*>|顯示簽章物件的單一項目。 在大多數情況下，您都應該使用 **DumpSig** 來查看個別簽章物件。 不過，如果簽章已經以某種形式損毀，您可以使用 **DumpSigElem** 來讀取它的有效部分。|
|**DumpStackObjects** [**-verify**] [ `top` *stack* [ `bottom` *stack*]]<br /><br /> -或-<br /><br /> **DSO** [**-verify**] [ `top` *stack* [ `bottom` *stack*]]|顯示可在目前堆疊界限內找到的所有 Managed 物件。<br /><br /> **-verify** 選項會驗證物件欄位的每個非靜態 `CLASS` 欄位。<br /><br /> 使用 **DumpStackObject** 命令搭配堆疊追蹤命令，例如 **K** (windbg) 或 **bt** (lldb) 以及 **>clrstack** 命令，以判斷區域變數和參數的值。|
|**>dumpvc** \<*MethodTable address*>\<*Address*>|顯示在所指定位址之實值類別欄位的相關資訊。<br /><br /> **MethodTable** 參數可讓 **DumpVC** 命令正確地解譯欄位。 實值類別並未以方法資料表做為其第一個欄位。|
|**EEHeap** [**-gc**] [**-loader**]|顯示內部執行時間資料結構所耗用的進程記憶體相關資訊。<br /><br /> **-gc** 和 **-loader** 選項會將這個命令的輸出限制為記憶體回收行程或載入器資料結構。<br /><br /> 記憶體回收行程的資訊會列出 Managed 堆積中每個區段的範圍。  如果指標位於 **-gc** 所指定的區段範圍內，該指標就是物件指標。|
|**EEStack** [**-short**] [**-EE**]|在處理序中的所有執行緒上執行 **DumpStack** 命令。<br /><br /> **-EE** 選項會直接傳遞到 **DumpStack** 命令。 **-short** 參數會將輸出限制到下列種類的執行緒：<br /><br />具有鎖定的執行緒。<br /><br />已經停止以便允許記憶體回收的執行緒。<br /><br /> 目前在 Managed 程式碼中的執行緒。|
|**EHInfo** [ \<*MethodDesc address*> ] [ \<*Code address*> ]|顯示所指定方法中的例外狀況處理區塊。  這個命令會顯示子句區塊 (`try` 區塊) 和處理常式區塊 (`catch` 區塊) 的程式碼位址和位移。|
|**常見問題集**|顯示常見問題集。  `dotnet-dump`不支援此項目。|
|**FinalizeQueue** [**-detail**] &#124; [**-allReady**] [**-short**]|顯示所有已註冊為完成項的物件。<br /><br /> **-detail** 選項會顯示需要清除之任何 `SyncBlocks` 的額外資訊，以及等待清除之任何 `RuntimeCallableWrappers` (RCW) 的額外資訊。 當完成項執行緒執行時，便會快取和清除這兩種資料結構。<br /><br /> `-allReady` 選項會顯示已準備好進行最終處理的所有物件，無論它們已經由記憶體回收這樣標記，或是將由下一個記憶體回收所標記，都會包括在內。 在「準備最終處理」清單中的物件，也就是不再是根目錄的可最終處理物件。 這個選項可能非常昂貴，因為它會驗證可最終處理佇列中的所有物件是否依然為根目錄。<br /><br /> `-short` 選項會將輸出限制為每個物件的位址。 如果搭配使用它與 **-allReady**，它就會列舉具有完成項且不再為根目錄的所有物件。 如果單獨使用，它就會在可進行最終處理和「準備最終處理」的佇列中列出所有物件。|
|**FindAppDomain**\<*Object address*>|判斷在所指定位址之物件的應用程式定義域。|
|**FindRoots** **-gen** \<*N*> &#124; **-gen any** &#124;\<*object address*>|讓偵錯工具在所指定層代的下一個集合上的偵錯項目內中斷。 只要中斷發生，就會立即重設效果。 若要在下一個集合上中斷，您必須重新發出命令。 *\<object address>* 此命令的形式是在發生 **-gen** 或 **-gen any** 所造成的中斷之後使用。 此時，偵錯項目處於正確的狀態，可讓 **FindRoots** 從目前的不適用層代識別出物件的根。 只有在 Windows 上才支援。|
|**GCHandles** [**-perdomain**]|顯示處理序中記憶體回收行程控制代碼的統計資料。<br /><br /> **-perdomain** 選項會依據應用程式定義域來排列統計資料。<br /><br /> 使用 **GCHandles** 命令，便可找出由記憶體回收行程控制代碼遺漏造成的記憶體流失。 例如，當程式碼保留大型陣列時就會發生記憶體流失，其保留的原因是因為強式記憶體回收行程控制代碼依然指向該陣列，而捨棄控制代碼時卻未釋放陣列。 <br /><br />只有在 Windows 上才支援。|
|**GCHandleLeaks**|在處理序中搜尋強式和 Pin 記憶體回收行程控制代碼之任何參考的記憶體，並顯示結果。 如果有找到控制代碼，**GCHandleLeaks** 命令便會顯示該參考的位址。 如果在記憶體中沒有找到任何控制代碼，這個命令便會顯示通知。 只有在 Windows 上才支援。|
|**GCInfo**\<*MethodDesc address*>\<*Code address*>|顯示指出註冊位置或堆疊位置在何時包含 Managed 物件的資料。 進行記憶體回收時，回收行程必須知道物件參考的位置，以便能夠用新的物件指標值來更新這些參考。|
|**GCRoot** [**-nostacks**] [**-all**] \<*Object address*>|顯示在所指定位址之物件參考 (或根目錄) 的相關資訊。<br /><br /> **FindRoots** 命令會在整個 Managed 堆積和控制代碼表格中，檢查位於堆疊上之其他物件和控制代碼中的控制代碼。 然後，會在每個堆疊上搜尋物件的指標，並會搜尋完成項佇列。<br /><br /> 這個命令不會判斷堆疊根目錄是否有效或是已遭捨棄。 您可以使用 **>clrstack** 和 **U** 命令來將區域變數或引數值所屬的框架進行拆解，以判斷堆疊根目錄是否仍在使用中。<br /><br /> **-nostacks** 選項會將搜尋限制到記憶體回收行程控制代碼和可存取的物件。<br /><br /> **-All** 選項會強制顯示所有的根目錄，而不是只顯示唯一的根目錄。|
|**GCWhere**  *\<object address>*|顯示傳入之引數的記憶體回收堆積中的位置和大小。 當引數位於 Managed 堆積中，但不是有效的物件位址時，大小就會顯示為 0 (零)。|
|**Help** (**soshelp**) [ \<*command*> ] [ `faq` ]|顯示當未指定任何參數時的所有可用命令，或是顯示所指定命令的詳細說明資訊。<br /><br /> `faq` 參數會顯示常見問題集的解答。|
|**HeapStat** [**-inclUnrooted** &#124; **-iu**]|顯示每個堆積的層代大小，以及每個堆積上每個層代中的總可用空間。 如果指定 **-lines** 選項，報告就會包括來自於記憶體回收堆積，且不再為根目錄之 Managed 物件的相關資訊。 只有在 Windows 上才支援。|
|**HistClear**|釋放 `Hist` 命令系列所使用的任何資源。<br /><br /> 通常，您不需要明確地呼叫 `HistClear`，因為每個 `HistInit` 都會清除先前的資源。|
|**HistInit**|初始化在偵錯項目中儲存之壓力記錄檔中的 SOS 結構。|
|**HistObj** *<obj_address>*|會檢查所有壓力記錄檔重新配置記錄，並顯示可能會使位址被當做引數傳入之記憶體回收重新配置的鏈結。|
|**HistObjFind**  *<obj_address>*|顯示參考位於指定位址之物件的所有記錄檔項目。|
|**HistRoot***\<root>*|顯示與指定之根的提升和重新配置都相關的資訊。<br /><br /> 根值可以透過記憶體回收，用來追蹤物件的移動。|
|**IP2MD** (**IP2MD**) \<*Code address*>|顯示在已進行 JIT 編譯之程式碼中之指定位址的 `MethodDesc` 結構。|
|**ListNearObj** (**lno**) *<obj_address>*|顯示在指定的位址之前與之後的物件。 此命令會在記憶體回收堆積中，尋找看來像是 Managed 物件之有效開頭的位址 (根據有效方法資料表)，以及引數位址的後接物件。 只有在 Windows 上才支援。|
|**MinidumpMode** [**0**] [**1**]|防止在使用小型傾印時執行不安全的命令。<br /><br /> 傳遞 **0** 便可停用這項功能，而傳遞 **1** 便可啟用這項功能。 根據預設，**MinidumpMode** 值會設定為 **0**。<br /><br /> 以 **.dump /m** 命令或 **.dump** 命令建立的小型傾印，都具有有限的 CLR 特定資料，並只允許您正確執行 SOS 命令的子集。 有些命令可能會因未預期的錯誤而失敗，原因是沒有對應或是只有部分對應到必要的記憶體區域。 這個選項可防止您對小型傾印執行不安全的命令。 <br /><br />僅支援 Windbg。|
|**Name2EE** (**Name2EE**) \<*module name*>\<*type or method name*><br /><br /> -或-<br /><br /> **Name2EE** \<*module name*>**!**\<*type or method name*>|顯示所指定模組中之指定類型或方法的 `MethodTable` 結構和 `EEClass` 結構。<br /><br /> 指定的模組必須載入到處理序。<br /><br /> 若要取得適當的類型名稱，請使用 [Ildasm.exe (IL 反組譯工具)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) 瀏覽該模組。 您也可以將 `*` 當做模組名稱參數傳遞，以便搜尋所有已載入的 Managed 模組。 *module name* 參數也可以是模組的偵錯工具名稱，例如 `mscorlib` 或 `image00400000`。<br /><br /> 這個命令支援 <`module`>`!`<`type`> 的 Windows 偵錯工具語法。 這個類型必須具有完整名稱。|
|**ObjSize** [ \<*Object address*> ] &#124; [**-aggregate**] [**-stat**]|顯示所指定物件的大小。 如果未指定任何參數，**ObjSize** 命令會顯示在 Managed 執行緒上找到之所有物件的大小，並會顯示處理序中的所有記憶體回收行程控制代碼，以及這些控制代碼所指向之任何物件的總大小。 **ObjSize** 命令會包括父代和其他所有子物件的大小。<br /><br /> **-aggregate** 選項可搭配使用 **-stat** 引數，以取得依然為根目錄之類型的詳細檢視。 藉由使用 **!dumpheap -stat** 和 **!objsize -aggregate -stat**，您可以判斷哪些物件不再是根目錄，以及診斷各種記憶體問題。 <br /><br /> 只有在 Windows 上才支援。|
|**PrintException** [**-nested**] [**-行**] [ \<*Exception object address*> ]<br /><br /> -或-<br /><br /> **PE** [**-nested**] [ \<*Exception object address*> ]|顯示並格式化在所指定位址且衍生自 <xref:System.Exception> 類別之任何物件的欄位。 如果您未指定位址，**PrintException** 命令便會顯示目前執行緒上最近一次擲回的例外狀況。<br /><br /> **-nested** 選項會顯示巢狀例外狀況物件的詳細資料。<br /><br /> **-lines** 選項會顯示來源資訊 (如果存在)。<br /><br /> 您可以使用這個命令來格式化和檢視 `_stackTrace` 欄位，此欄位屬於二進位陣列。|
|**ProcInfo** [**-env**] [**-time**] [**-mem**]|顯示處理序的環境變數、核心 CPU 時間，以及記憶體使用統計資料。 僅支援 Windbg。|
|**RCWCleanupList**\<*RCWCleanupList address*>|顯示在所指定位址上正在等待清除之執行階段可呼叫包裝函式的清單。 僅支援 Windbg。|
|**SaveModule** \<*Base address*>\<*Filename*>|將在所指定位址上已載入記憶體的影像，寫入至指定的檔案。 僅支援 Windbg。|
|**SetHostRuntime** [ \<runtime-directory\> ]|此命令會設定 .NET Core 執行時間的路徑，以用來裝載在偵錯工具 (lldb) 中作為 SOS 一部分執行的 managed 程式碼。 執行時間必須至少為2.1.0 版或更高版本。 如果目錄中有空格，則必須以單引號括住 ( ' ) 。<br/><br/>通常，SOS 會嘗試找出已安裝的 .NET Core 執行時間，以自動執行其受控碼，但如果失敗，則可以使用此命令。 預設值是使用相同的執行時間 (>libcoreclr.dylib) 正在進行調試。 如果所要調試的預設執行時間無法執行 SOS 程式碼或版本小於2.1.0，請使用此命令。<br/><br/>如果您在執行 SOS 命令時收到下列錯誤訊息，請使用此命令將路徑設定為2.1.0 或更大的 .NET Core 執行時間。 <br/><br/>`(lldb) clrstack`<br/>`Error: Fail to initialize CoreCLR 80004005 ClrStack failed`<br/><br/>`(lldb) sethostruntime /usr/share/dotnet/shared/Microsoft.NETCore.App/2.1.6`<br/><br/>您可以使用命令介面中的 "dotnet--info" 來尋找已安裝的 .NET Core 執行時間路徑。|
|**SetSymbolServer** [**-ms**] [**-disable**] [**-log**] [**-loadsymbols**] [**-cache** \<cache-path> ] [**-directory** \<search-directory> ] [**-.sympath** \<windows-symbol-path> ] [ \<symbol-server-URL> ]|啟用符號伺服器下載支援。<br/><br/>**-Ms** 選項可讓您從公用 Microsoft 符號伺服器進行下載。<br/><br/>**-Disable** 選項會開啟符號下載支援。<br/><br/>**-Cache** \<cache-path> 選項會指定符號快取目錄。 如果未指定，預設值會是 $HOME/.dotnet/symbolcache。<br/><br/>**-Directory** 選項會新增用來搜尋符號的路徑。 可以是一個以上。<br/><br/>**-.Sympath** 選項會以 Windows 符號路徑格式新增伺服器、快取和目錄路徑。<br/><br/>**-Log** 選項會啟用符號下載記錄。<br/><br/>**-Loadsymbols** 選項會嘗試下載執行時間的原生 .net Core 符號。 支援 lldb 和 dotnet-傾印|
|**SOSFlush**|清除內部 SOS 快取。|
|**SOSStatus** [**-reset**]|顯示內部 SOS 狀態，或重設內部快取狀態。|
|**StopOnException** [**-衍生**] [**-create** &#124; **-create2**] \<*Exception*>\<*Pseudo-register number*>|導致偵錯工具會在擲回所指定例外狀況時停止，但是在擲回其他例外狀況時會繼續執行。<br /><br /> **-derived** 選項會攔截所指定的例外狀況，以及從所指定例外狀況衍生的每一個例外狀況。 <br /><br /> 僅支援 Windbg。|
|**>syncblk** [**-all** &#124; \<*syncblk number*> ]|顯示所指定 `SyncBlock` 結構，或是所有的 `SyncBlock` 結構。  如果您沒有傳遞任何引數，**SyncBlk** 命令便會顯示屬於某執行緒擁有之物件的對應 `SyncBlock` 結構。<br /><br /> `SyncBlock` 結構是專門放置並非每一個物件都要建立之額外資訊的容器。 其中可以包含 COM Interop 資料、雜湊碼，以及安全執行緒作業的鎖定資訊。|
|**ThreadPool**|顯示 Managed 執行緒集區的相關資訊，其中包括佇列中工作要求的數目、完成連接埠執行緒的數目，以及計時器的數目。|
|**執行緒** (**clrthreads**) [**-live**] [**-特殊**]|顯示處理序中的所有 Managed 執行緒。<br /><br /> **Threads** 命令會顯示偵錯工具簡略識別碼、CLR 執行緒識別碼，以及作業系統執行緒識別碼。  此外，**Threads** 命令也會顯示 Domain 資料行、APT 資料行和 Exception 資料行，分別指出執行緒執行所在的應用程式定義域、COM Apartment 模式和執行緒中最近一次擲回的例外狀況。<br /><br /> **-live** 選項會顯示與運作中執行緒建立關聯的執行緒。<br /><br /> **-special** 選項會顯示由 CLR 建立的所有特殊執行緒。 特殊執行緒包括記憶體回收執行緒 (在並行和伺服器記憶體回收中)、偵錯工具 Helper 執行緒、完成項執行緒、<xref:System.AppDomain> 卸載執行緒，以及執行緒集區計時器執行緒。|
|**ThreadState \<** *State value field* **>**|顯示執行緒的狀態。 `value` 參數為 **Threads** 報告輸出中 `State` 欄位的值。|
|**Token2EE** \<*module name*>\<*token*>|將所指定模組中的已指定中繼資料語彙基元轉變成 `MethodTable` 結構或 `MethodDesc` 結構。<br /><br /> 您可以將 `*` 當做模組名稱參數傳遞，便可了解該語彙基元對應至每一個載入之 Managed 模組中的哪個項目。 您也可以傳遞模組的偵錯工具名稱，例如 `mscorlib` 或 `image00400000`。|
|**U** [**-gcinfo**] [**-ehinfo**] [**-n**] \<*MethodDesc address*> &#124; \<*Code address*>|顯示由方法之 `MethodDesc` 結構指標，或是由方法主體內之程式碼位址所指定 Managed 方法的標註反組譯碼。 **U** 命令會顯示從開始到結束的整個方法，以及將中繼資料語彙基元轉換成名稱的註釋。<br /><br /> **-gcinfo** 選項會使 **U** 命令顯示方法的 `GCInfo` 結構。<br /><br /> **-ehinfo** 選項會顯示方法的例外狀況資訊。 您也可以使用 **EHInfo** 命令取得這項資訊。<br /><br /> **-n** 選項會停用原始程式檔名稱和行號的顯示。 如果偵錯工具有指定 SYMOPT_LOAD_LINES 選項，SOS 就會查詢每個 Managed 框架的符號，而且如果成功，就會顯示對應的原始程式檔名稱和行號。 您可以指定 **-n** 選項以停用這種行為。|
|**VerifyHeap**|檢查記憶體回收行程堆積是否有損毀徵兆，並顯示任何所發現的錯誤。<br /><br /> 堆積損毀的原因可能是平台叫用架構不正確的呼叫。 |
|**VerifyObj**\<*object address*>|檢查傳遞為引數的物件以找出損毀的症狀。 只有在 Windows 上才支援。|
|**存取 vmmap**|周遊虛擬位址空間，並顯示每個區域所套用的保護類型。 僅支援 Windbg。|
|**Vmstat**|提供虛擬位址空間的摘要檢視，並依據套用至該記憶體的各種保護類型 (無限制、保留、認可、私用、對應、影像) 進行排列。 TOTAL 資料行會顯示 AVERAGE 資料行乘以 BLK COUNT 資料行的結果。 僅支援 Windbg。|

### <a name="dotnet-dump"></a>Dotnet-Dump

如需的可用 SOS 命令清單 `dotnet-dump analyze` ，請參閱 [dotnet-](dotnet-dump.md#analyze-sos-commands)傾印。

### <a name="windows-debugger"></a>Windows 偵錯工具

您也可以使用 SOS 偵錯工具擴充功能，方法是將它載入至 [WinDbg/dbg 偵錯工具](/windows-hardware/drivers/debugger/debugger-download-tools) ，並在 Windows 偵錯工具中執行命令。  SOS 命令可用於即時進程或傾印。

若要將 SOS 偵錯工具擴充功能載入 Windows 偵錯工具，請在工具中執行下列命令：

```console
.loadby sos clr
```

WinDbg.exe 和 Visual Studio 都會使用對應於目前使用中之 Mscorwks.dll 版本的 SOS.dll 版本。 根據預設，您應該使用符合目前 Mscorwks.dll 版本的 SOS.dll 版本。

若要使用在另一部電腦上建立的傾印檔案，請確定此次安裝所隨附的 Mscorwks.dll 檔案位於您的符號路徑中，然後載入對應的 SOS.dll 版本。

若要載入特定版本的 SOS.dll，請在 Windows 偵錯工具中輸入下列命令：

```console
.load <full path to sos.dll>
```

### <a name="lldb-debugger"></a>LLDB 偵錯工具

如需設定 SOS 以進行 LLDB 的指示，請參閱 [dotnet-SOS](dotnet-sos.md)。 SOS 命令可用於即時進程或傾印。

依預設，您可以藉由輸入下列命令來連接所有 SOS 命令： `sos [command\_name]` 。 不過，常見的命令已有別名，因此您不需要 `sos` 前置詞：

| 命令                               | 函數
| ------------------------------------- | ---------------------------------------------------------------------------------------------
|    `bpmd`                             | 在指定的模組中，于指定的 managed 方法上建立中斷點。
|    `clrstack`                         | 僅提供 Managed 程式碼的堆疊追蹤。
|    `clrthreads`                       | 列出正在執行的受管理執行緒。
|    `clru`                             | 顯示 managed 方法的批註式反組解碼。
|    `dso`                              | 顯示可在目前堆疊界限內找到的所有 Managed 物件。
|    `dumpasync`                        | 顯示垃圾收集堆積上非同步狀態機器的相關資訊。
|    `dumpclass`                        | 顯示指定位址之結構的相關資訊 `EEClass` 。
|    `dumpdomain`                       | 顯示指定網域內所有 Appdomain 和所有元件的資訊。
|    `dumpheap`                         | 顯示垃圾收集堆積的相關資訊，以及物件的集合統計資料。
|    `dumpil`                           | 顯示與 Managed 方法相關聯的 Microsoft 中繼語言 (MSIL)。
|    `dumplog`                          | 將記憶體中壓力記錄檔的內容寫入指定的檔案。
|    `dumpmd`                           | 顯示指定位址之結構的相關資訊 `MethodDesc` 。
|    `dumpmodule`                       | 顯示指定位址上模組的相關資訊。
|    `dumpmt`                           | 顯示指定位址之方法資料表的相關資訊。
|    `dumpobj`                          | 顯示指定位址的物件資訊。
|    `dumpstack`                        | 顯示原生和 managed 堆疊追蹤。
|    `eeheap`                           | 顯示內部執行時間資料結構所耗用的進程記憶體相關資訊。
|    `eestack`                          | 會 `dumpstack` 在進程中的所有線程上執行。
|    `gcroot`                           | 在指定的位址上，顯示物件 (或根) 參考的相關資訊。
|    `histclear`                        | 釋放 >hist 命令系列所使用的任何資源。
|    `histinit`                         | 初始化在偵錯項目中儲存之壓力記錄檔中的 SOS 結構。
|    `histobj`                          | 會檢查所有壓力記錄檔重新配置記錄，並顯示可能會使位址被當做引數傳入之記憶體回收重新配置的鏈結。
|    `histobjfind`                      | 顯示在指定的位址參考物件的所有記錄專案。
|    `histroot`                         | 顯示與指定之根的提升和重新配置都相關的資訊。
|    `ip2md`                            | 顯示在已進行 JIT 編譯之程式碼中之指定位址的 `MethodDesc` 結構。
|    `loadsymbols`                      | 載入 .NET Core 原生模組符號。
|    `name2ee`                          | 顯示指定 `MethodTable` `EEClass` 模組中所指定類型或方法的和結構。
|    `pe`                               | 顯示並格式化在所指定位址且衍生自 <xref:System.Exception> 類別之任何物件的欄位。
|    `setclrpath`                       | 設定要載入 coreclr dac/dbi 檔案的路徑。 `setclrpath <path>`
|    `sethostruntime`                   | 設定或顯示在 SOS 中用來執行 managed 程式碼的 .NET Core 執行時間目錄。
|    `setsymbolserver`                  | 啟用符號伺服器支援。
|    `setsostid`                        | 設定目前的 OS tid/執行緒索引，而不是使用一個 lldb 提供的。 `setsostid <tid> <index>`
|    `sos`                              | 各種 coreclr 的調試命令。 如需詳細資訊，請參閱 ' soshelp '。 `sos <command-name> <args>`
|    `soshelp`                          | 如果未指定任何參數，則顯示所有可用的命令，或顯示指定命令的詳細說明資訊： `soshelp <command>`
|    `syncblk`                          | 顯示 SyncBlock 持有者資訊。

## <a name="windbgcdb-example-usage"></a>Windbg/cdb 範例使用方式

| 命令  | 描述
| - | -
| `!dumparray -start 2 -length 5 -detail 00ad28d0` | 顯示位址的陣列內容 `00ad28d0` 。  顯示會從第二個元素開始，然後連續顯示五個元素。
| `!dumpassembly 1ca248` | 顯示位址的元件內容 `1ca248` 。
| `!dumpheap` | 顯示垃圾收集行程堆積的相關資訊。
| `!DumpLog` | 將記憶體中壓力記錄檔的內容寫入至目前目錄中名為 StressLog.txt 的 (預設) 檔。
 `!dumpmd 902f40` | `MethodDesc`在位址顯示結構 `902f40` 。
| `!dumpmodule 1caa50` | 顯示位址上模組的相關資訊 `1caa50` 。
| `!DumpObj a79d40` | 顯示位址上物件的相關資訊 `a79d40` 。
| `!DumpVC 0090320c 00a79d9c` | `00a79d9c`使用位址上的方法資料表，在位址顯示值類別的欄位 `0090320c` 。
| `!eeheap` -gc | 顯示垃圾收集行程所使用的進程記憶體。
| `!finalizequeue` | 顯示排程進行最終處理的所有物件。
| `!findappdomain 00a79d98` |  判斷位於位址之物件的應用程式域 `00a79d98` 。
| `!gcinfo 5b68dbb8` | 顯示目前進程中的所有垃圾收集行程控制碼。
| `!name2ee unittest.exe MainClass.Main` | 顯示 `MethodTable` 模組中 `EEClass` 類別的方法和結構 `Main` `MainClass` `unittest.exe` 。
| `!token2ee unittest.exe 02000003` | 顯示有關模組中位址的元資料標記資訊 `02000003` `unittest.exe` 。

## <a name="lldb-example-usage"></a>LLDB 範例使用方式

| 命令  | 描述
| - | -
| `sos DumpArray -start 2 -length 5 -detail 00ad28d0` | 顯示位址的陣列內容 `00ad28d0` 。  顯示會從第二個元素開始，然後連續顯示五個元素。
| `sos DumpAssembly 1ca248` | 顯示位址的元件內容 `1ca248` 。
| `dumpheap` | 顯示垃圾收集行程堆積的相關資訊。
| `dumplog` | 將記憶體中壓力記錄檔的內容寫入至目前目錄中名為 StressLog.txt 的 (預設) 檔。
| `dumpmd 902f40` | `MethodDesc`在位址顯示結構 `902f40` 。
| `dumpmodule 1caa50` | 顯示位址上模組的相關資訊 `1caa50` 。
| `dumpobj a79d40` | 顯示位址上物件的相關資訊 `a79d40` 。
| `sos DumpVC 0090320c 00a79d9c` | `00a79d9c`使用位址上的方法資料表，在位址顯示值類別的欄位 `0090320c` 。
| `eeheap -gc` | 顯示垃圾收集行程所使用的進程記憶體。
| `sos FindAppDomain 00a79d98` | 判斷位於位址之物件的應用程式域 `00a79d98` 。
| `sos GCInfo 5b68dbb8` | 顯示目前進程中的所有垃圾收集行程控制碼。
| `name2ee unittest.exe MainClass.Main` | 顯示 `MethodTable` 模組中 `EEClass` 類別的方法和結構 `Main` `MainClass` `unittest.exe` 。
| `sos Token2EE unittest.exe 02000003` | 顯示有關模組中位址的元資料標記資訊 `02000003` `unittest.exe` 。
| `clrthreads` | 顯示 managed 執行緒。

## <a name="see-also"></a>請參閱

- [.NET 中傾印的簡介](dumps.md)
- [瞭解如何在 .NET Core 中偵測記憶體流失](debug-memory-leak.md)
- [收集和分析記憶體傾印的 blog](https://devblogs.microsoft.com/dotnet/collecting-and-analyzing-memory-dumps/)
- [傾印分析工具 (dotnet-傾印) ](dotnet-dump.md)
- [SOS 安裝工具 (dotnet-sos) ](dotnet-sos.md)
- [堆積分析工具 (dotnet-gcdump) ](dotnet-gcdump.md)
