---
title: SOS.dll (SOS 偵錯擴充功能)
ms.date: 03/30/2017
helpviewer_keywords:
- debugging extensions
- SOS debugging extensions
- SOS.dll
ms.assetid: 9ac1b522-77ab-4cdc-852a-20fcdc9ae498
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2c6f2d001c6513211cf15993285e3564f7613402
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47205104"
---
# <a name="sosdll-sos-debugging-extension"></a>SOS.dll (SOS 偵錯擴充功能)

SOS 偵錯延伸模組副檔名 (SOS.dll) 提供內部 Common Language Runtime (CLR) 環境的相關資訊，以協助您在 Windows 偵錯工具 (WinDbg.exe) 和 Visual Studio 中偵錯受控程式。 這個工具需要您的專案已啟用非 Managed 偵錯。 SOS.dll 會隨著 .NET Framework 自動安裝。 若要在 Visual Studio 中使用 SOS.dll，請安裝 [Windows 驅動程式套件 (WDK)](/windows-hardware/drivers/download-the-wdk)。

## <a name="syntax"></a>語法

```shell
![command] [options]
```

## <a name="commands"></a>命令

|命令|描述|
|-------------|-----------------|
|**AnalyzeOOM** (**ao**)|顯示在記憶體回收堆積的配置要求上，最後發生的記憶體不足 (OOM) 資訊。 (在伺服器記憶體回收中，它會顯示每個記憶體回收堆積上的 OOM (如果存在))。|
|**BPMD** [**-nofuturemodule**] [\<*module name*> \<*method name*>] [**-md** <`MethodDesc`>] **-list** **-clear** \<*pending breakpoint number*> **-clearall**|在所指定模組中的指定方法上建立中斷點。<br /><br /> 如果指定的模組和方法尚未載入，這個命令便會在建立中斷點之前，等待已載入模組和已完成 Just-in-Time (JIT) 編譯的通知。<br /><br /> 您可以使用 **-list**、**-clear** 和 **-clearall** 選項來管理暫止中斷點的清單：<br /><br /> **-list** 選項會產生所有暫止中斷點的清單。 如果暫止中斷點具有非零的模組 ID，就是該特殊載入模組中函式的特定中斷點。 如果暫止中斷點具有零模組 ID，該中斷點就會套用至尚未載入的模組。<br /><br /> 使用 **-clear** 或 **-clearall** 選項可從清單中移除暫止中斷點。|
|**CLRStack** [**-a**] [**-l**] [**-p**] [**-n**]|僅提供 Managed 程式碼的堆疊追蹤。<br /><br /> **-p** 選項會顯示 Managed 函式的引數。<br /><br /> **-l** 選項會顯示框架中區域變數的相關資訊。 SOS 偵錯擴充功能無法擷取區域名稱，因此區域名稱之輸出的格式會是 \<*local address*> **=** \<*value*>。<br /><br /> **-a** (全部) 選項是 **-l** 與 **-p** 組合的捷徑。<br /><br /> **-n** 選項會停用原始程式檔名稱和行號的顯示。 如果偵錯工具有指定 SYMOPT_LOAD_LINES 選項，SOS 將會查詢每個 Managed 框架的符號，而且如果成功，就會顯示對應的原始程式檔名稱和行號。 指定 **-n** (沒有行號) 參數即可停用這種行為。<br /><br /> SOS 偵錯擴充功能不會在 x64 和 IA-64 架構平台上顯示轉換框架。|
|**COMState**|列出每個執行緒和 `Context` 指標的 COM Apartment Model (如果有)。|
|**DumpArray** [**-start** \<*startIndex*>] [**-length** \<*length*>] [**-details**] [**-nofields**] \<*array object address*><br /><br /> -或-<br /><br /> **DA** [**-start** \<*startIndex*>] [**-length** \<*length*>] [**-detail**] [**-nofields**] *array object address*>|檢查陣列物件的元素。<br /><br /> **-start** 選項會指定開始顯示項目的索引。<br /><br /> **-length** 選項會指定要顯示多少項目。<br /><br /> **-details** 選項會使用 **DumpObj** 和 **DumpVC** 格式來顯示項目的詳細資料。<br /><br /> **-nofields** 選項會防止陣列顯示。 這個選項只有在指定 **-detail** 選項時才能使用。|
|**DumpAssembly** \<*assembly address*>|顯示關於組件的資訊。<br /><br /> **DumpAssembly** 命令會列出多個模組 (如果這些模組存在)。<br /><br /> 您可以使用 **DumpDomain** 命令取得組件位址。|
|**DumpClass** \<*EEClass address*>|顯示與某個類型關聯之 `EEClass` 結構的資訊。<br /><br /> **DumpClass** 命令會顯示靜態欄位值，但不會顯示非靜態欄位值。<br /><br /> 使用 **DumpMT**、**DumpObj**、**Name2EE** 或 **Token2EE** 命令，以取得 `EEClass` 結構位址。|
|**DumpDomain** [\<*domain address*>]|列舉載入於所指定 <xref:System.Reflection.Assembly> 物件位址內的每個 <xref:System.AppDomain> 物件。  當不使用參數進行呼叫時，**DumpDomain** 命令便會列出處理序中的所有 <xref:System.AppDomain> 物件。|
|**DumpHeap** [**-stat**] [**-strings**] [**-short**] [**-min** \<*size*>] [**-max** \<*size*>] [**-thinlock**] [**-startAtLowerBound**] [**-mt** \<*MethodTable address*>] [**-type** \<*partial type name*>][*start* [*end*]]|顯示記憶體回收堆積的資訊，以及關於物件的回收統計資料。<br /><br /> **DumpHeap** 命令會在偵測到記憶體回收行程堆積中出現過多分割時顯示警告。<br /><br /> **-stat** 選項會將輸出限制為統計類型摘要。<br /><br /> **-strings** 選項會將輸出限制為統計字串值摘要。<br /><br /> **-short** 選項會將輸出限制為每個物件的位址。 這可讓您輕鬆地將輸出從命令由管道送到另一個偵錯工具命令以達成自動化。<br /><br /> **-min** 選項會忽略小於 `size` 參數的物件 (指定單位為位元組)。<br /><br /> **-max** 選項會忽略大於 `size` 參數的物件 (指定單位為位元組)。<br /><br /> **-thinlock** 選項會報告 ThinLocks。  如需詳細資訊，請參閱 **SyncBlk** 命令。<br /><br /> `-startAtLowerBound` 選項會強制堆積查核從所提供之位址範圍的下限開始。 在規劃階段期間，因為物件正在移動，通常都無法查核堆積。 這個選項會強制 **DumpHeap** 在指定的下限開始其查核。 您必須提供有效物件的位址，做為讓此選項運作的下限。 您可以顯示位於錯誤物件之位址的記憶體，以手動方式找出下一個方法資料表。 如果記憶體回收目前位於 `memcopy` 的呼叫中，您也可以將大小加到起始位址 (以參數的形式提供)，以尋找下一個物件的位址。<br /><br /> **-mt** 選項只會列出會對應至所指定 `MethodTable` 結構中的那些物件。<br /><br /> **-type** 選項只會列出其類型名稱即為所指定字串之子字串的物件。<br /><br /> `start` 參數會從指定的位址開始列出。<br /><br /> `end` 參數會在指定的位址停止列出。|
|**DumpIL** \<*Managed DynamicMethod object*> &#124;       \<*DynamicMethodDesc pointer*> &#124;        \<*MethodDesc pointer*>|顯示與 Managed 方法相關聯的 Microsoft 中繼語言 (MSIL)。<br /><br /> 請注意，動態 MSIL 的發出方式不同於從組件載入的 MSIL。 動態 MSIL 會參考 Managed 物件陣列中的物件，而非參考中繼資料語彙基元。|
|**DumpLog** [**-addr** \<*addressOfStressLog*>] [<*Filenam*`e`>]|將記憶體中壓力記錄檔的內容寫入指定的檔案。 如果沒有指定名稱，此命令便會在目前的目錄中建立名為 StressLog.txt 的檔案。<br /><br /> 記憶體中的壓力記錄可協助您診斷壓力失敗而不必使用鎖定或 I/O。 若要啟用壓力記錄檔，請在 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework 底下設定下列登錄機碼：<br /><br /> (DWORD) StressLog = 1<br /><br /> (DWORD) LogFacility = 0xffffffff<br /><br /> (DWORD) StressLogSize = 65536<br /><br /> 選擇性的 `-addr` 選項可讓您指定預設記錄檔以外的壓力記錄檔。|
|**DumpMD** \<*MethodDesc address*>|在指定的位址顯示 `MethodDesc` 結構的相關資訊。<br /><br /> 您可以使用 **IP2MD** 命令，從 Managed 函式取得 `MethodDesc` 結構位址。|
|**DumpMT** [**-MD**] \<*MethodTable address*>|顯示在所指定位址之方法資料表的相關資訊。 指定 **-MD** 選項，便會顯示與物件一起定義之所有方法的清單。<br /><br /> 每個 Managed 物件都包含一個方法資料表指標。|
|**DumpMethodSig** \<*sigaddr*> <*moduleadd*`r`>|在指定的位址顯示 `MethodSig` 結構的相關資訊。|
|**DumpModule** [**-mt**] \<*Module address*>|顯示在所指定位址之模組的相關資訊。 **-mt** 選項會顯示定義在模組中的類型，以及由該模組所參考的類型。<br /><br /> 您可以使用 **DumpDomain** 或 **DumpAssembly** 命令來擷取模組的位址。|
|**DumpObj** [**-nofields**] \<*object address*><br /><br /> -或-<br /><br /> **DO** \<*object address*>|顯示在所指定位址之物件的相關資訊。 **DumpObj** 命令會顯示欄位、`EEClass` 結構資訊、方法資料表，以及物件的大小。<br /><br /> 您可以使用 **DumpStackObjects** 命令來擷取物件的位址。<br /><br /> 請注意，您可以對 `CLASS` 類型的欄位執行 **DumpObj** 命令，因為這些欄位也是物件。<br /><br /> `-`**nofields** 選項可防止物件的欄位顯示，這對像是 String 的物件非常有用。|
|**DumpRuntimeTypes**|顯示記憶體回收行程堆積中的執行階段類型物件，並列出與其關聯的類型名稱和方法資料表。|
|**DumpStack** [**-EE**] [**-n**] [`top` *stack* [`bottom` *stac*`k`]]|顯示堆疊追蹤。<br /><br /> **-EE** 選項會使 **DumpStack** 命令只顯示 Managed 函式。 使用 `top` 和 `bottom` 參數可限制在 x86 平台上顯示的堆疊框架。<br /><br /> **-n** 選項會停用原始程式檔名稱和行號的顯示。 如果偵錯工具有指定 SYMOPT_LOAD_LINES 選項，SOS 將會查詢每個 Managed 框架的符號，而且如果成功，就會顯示對應的原始程式檔名稱和行號。 指定 **-n** (沒有行號) 參數即可停用這種行為。<br /><br /> 在 x86 和 x64 平台上，**DumpStack** 命令會建立詳細的堆疊追蹤。<br /><br /> 在 IA-64 架構平台上，**DumpStack** 命令會模擬偵錯工具的 **K** 命令。 IA-64 架構平台會忽略 `top` 和 `bottom` 參數。|
|**DumpSig** \<*sigaddr*> \<*moduleaddr*>|在指定的位址顯示 `Sig` 結構的相關資訊。|
|**DumpSigElem** \<*sigaddr*> \<*moduleaddr*>|顯示簽章物件的單一項目。 在大多數情況下，您都應該使用 **DumpSig** 來查看個別簽章物件。 不過，如果簽章已經以某種形式損毀，您可以使用 **DumpSigElem** 來讀取它的有效部分。|
|**DumpStackObjects** [**-verify**] [`top` *stack* [`bottom` *stack*]]<br /><br /> -或-<br /><br /> **DSO** [**-verify**] [`top` *stack* [`bottom` *stack*]]|顯示可在目前堆疊界限內找到的所有 Managed 物件。<br /><br /> **-verify** 選項會驗證物件欄位的每個非靜態 `CLASS` 欄位。<br /><br /> 使用 **DumpStackObject** 命令和追蹤命令 (例如 **K** 命令和 **CLRStack** 命令)，即可判斷區域變數和參數的值。|
|**DumpVC** \<*MethodTable address*> \<*Address*>|顯示在所指定位址之實值類別欄位的相關資訊。<br /><br /> **MethodTable** 參數可讓 **DumpVC** 命令正確地解譯欄位。 實值類別並未以方法資料表做為其第一個欄位。|
|**EEHeap** [**-gc**] [**-loader**]|顯示由內部 CLR 資料結構使用的處理序記憶體相關資訊。<br /><br /> **-gc** 和 **-loader** 選項會將這個命令的輸出限制為記憶體回收行程或載入器資料結構。<br /><br /> 記憶體回收行程的資訊會列出 Managed 堆積中每個區段的範圍。  如果指標位於 **-gc** 所指定的區段範圍內，該指標就是物件指標。|
|**EEStack** [**-short**] [**-EE**]|在處理序中的所有執行緒上執行 **DumpStack** 命令。<br /><br /> **-EE** 選項會直接傳遞到 **DumpStack** 命令。 **-short** 參數會將輸出限制到下列種類的執行緒：<br /><br /> 具有鎖定的執行緒。<br /><br /> 已經停止以便允許記憶體回收的執行緒。<br /><br /> 目前在 Managed 程式碼中的執行緒。|
|**EEVersion**|顯示 CLR 版本。|
|**EHInfo** [\<*MethodDesc address*>] [\<*Code address*>]|顯示所指定方法中的例外狀況處理區塊。  這個命令會顯示子句區塊 (`try` 區塊) 和處理常式區塊 (`catch` 區塊) 的程式碼位址和位移。|
|**常見問題集**|顯示常見問題集。|
|**FinalizeQueue** [**-detail**] &#124; [**-allReady**] [**-short**]|顯示所有已註冊為完成項的物件。<br /><br /> **-detail** 選項會顯示需要清除之任何 `SyncBlocks` 的額外資訊，以及等待清除之任何 `RuntimeCallableWrappers` (RCW) 的額外資訊。 當完成項執行緒執行時，便會快取和清除這兩種資料結構。<br /><br /> `-allReady` 選項會顯示已準備好進行最終處理的所有物件，無論它們已經由記憶體回收這樣標記，或是將由下一個記憶體回收所標記，都會包括在內。 在「準備最終處理」清單中的物件，也就是不再是根目錄的可最終處理物件。 這個選項可能非常昂貴，因為它會驗證可最終處理佇列中的所有物件是否依然為根目錄。<br /><br /> `-short` 選項會將輸出限制為每個物件的位址。 如果搭配使用它與 **-allReady**，它就會列舉具有完成項且不再為根目錄的所有物件。 如果單獨使用，它就會在可進行最終處理和「準備最終處理」的佇列中列出所有物件。|
|**FindAppDomain** \<*Object address*>|判斷在所指定位址之物件的應用程式定義域。|
|**FindRoots** **-gen** \<*N*> &#124; **-gen any** &#124;\<*object address*>|讓偵錯工具在所指定層代的下一個集合上的偵錯項目內中斷。 只要中斷發生，就會立即重設效果。 若要在下一個集合上中斷，您必須重新發出命令。 發生 **-gen** 或 **-gen any** 之後，將會使用這個命令的 *\<object address>* 形式。 此時，偵錯項目處於正確的狀態，可讓 **FindRoots** 從目前的不適用層代識別出物件的根。|
|**GCHandles** [**-perdomain**]|顯示處理序中記憶體回收行程控制代碼的統計資料。<br /><br /> **-perdomain** 選項會依據應用程式定義域來排列統計資料。<br /><br /> 使用 **GCHandles** 命令，便可找出由記憶體回收行程控制代碼遺漏造成的記憶體流失。 例如，當程式碼保留大型陣列時就會發生記憶體流失，其保留的原因是因為強式記憶體回收行程控制代碼依然指向該陣列，而捨棄控制代碼時卻未釋放陣列。|
|**GCHandleLeaks**|在處理序中搜尋強式和 Pin 記憶體回收行程控制代碼之任何參考的記憶體，並顯示結果。 如果有找到控制代碼，**GCHandleLeaks** 命令便會顯示該參考的位址。 如果在記憶體中沒有找到任何控制代碼，這個命令便會顯示通知。|
|**GCInfo** \<*MethodDesc address*>\<*Code address*>|顯示指出註冊位置或堆疊位置在何時包含 Managed 物件的資料。 進行記憶體回收時，回收行程必須知道物件參考的位置，以便能夠用新的物件指標值來更新這些參考。|
|**GCRoot** [**-nostacks**] \<*Object address*>|顯示在所指定位址之物件參考 (或根目錄) 的相關資訊。<br /><br /> **FindRoots** 命令會在整個 Managed 堆積和控制代碼表格中，檢查位於堆疊上之其他物件和控制代碼中的控制代碼。 然後，會在每個堆疊上搜尋物件的指標，並會搜尋完成項佇列。<br /><br /> 這個命令不會判斷堆疊根目錄是否有效或是已遭捨棄。 使用 **CLRStack** 和 **U** 命令，便可分解區域或引數值所屬的框架，以便判斷該堆疊根目錄是否仍在使用中。<br /><br /> **-nostacks** 選項會將搜尋限制到記憶體回收行程控制代碼和可能執行的物件。|
|**GCWhere**  *\<object address>*|顯示傳入之引數的記憶體回收堆積中的位置和大小。 當引數位於 Managed 堆積中，但不是有效的物件位址時，大小就會顯示為 0 (零)。|
|**help** [\<*command*>] [`faq`]|顯示當未指定任何參數時的所有可用命令，或是顯示所指定命令的詳細說明資訊。<br /><br /> `faq` 參數會顯示常見問題集的解答。|
|**HeapStat** [**-inclUnrooted** &#124; **-iu**]|顯示每個堆積的層代大小，以及每個堆積上每個層代中的總可用空間。 如果指定 **-lines** 選項，報告就會包括來自於記憶體回收堆積，且不再為根目錄之 Managed 物件的相關資訊。|
|**HistClear**|釋放 `Hist` 命令系列所使用的任何資源。<br /><br /> 通常，您不需要明確地呼叫 `HistClear`，因為每個 `HistInit` 都會清除先前的資源。|
|**HistInit**|初始化在偵錯項目中儲存之壓力記錄檔中的 SOS 結構。|
|**HistObj** *<obj_address>*|會檢查所有壓力記錄檔重新配置記錄，並顯示可能會使位址被當做引數傳入之記憶體回收重新配置的鏈結。|
|**HistObjFind**  *<obj_address>*|顯示參考位於指定位址之物件的所有記錄檔項目。|
|**HistRoot** *\<root>*|顯示與指定之根的提升和重新配置都相關的資訊。<br /><br /> 根值可以透過記憶體回收，用來追蹤物件的移動。|
|**IP2MD** \<*Code address*>|顯示在已進行 JIT 編譯之程式碼中之指定位址的 `MethodDesc` 結構。|
|`ListNearObj` (`lno`) *<obj_address>*|顯示在指定的位址之前與之後的物件。 此命令會在記憶體回收堆積中，尋找看來像是 Managed 物件之有效開頭的位址 (根據有效方法資料表)，以及引數位址的後接物件。|
|**MinidumpMode** [**0**] [**1**]|防止在使用小型傾印時執行不安全的命令。<br /><br /> 傳遞 **0** 便可停用這項功能，而傳遞 **1** 便可啟用這項功能。 根據預設，**MinidumpMode** 值會設定為 **0**。<br /><br /> 以 **.dump /m** 命令或 **.dump** 命令建立的小型傾印，都具有有限的 CLR 特定資料，並只允許您正確執行 SOS 命令的子集。 有些命令可能會因未預期的錯誤而失敗，原因是沒有對應或是只有部分對應到必要的記憶體區域。 這個選項可防止您對小型傾印執行不安全的命令。|
|**Name2EE** \<*module name*> \<*type or method name*><br /><br /> -或-<br /><br /> **Name2EE** \<*module name*>**!**\<*type or method name*>|顯示所指定模組中之指定類型或方法的 `MethodTable` 結構和 `EEClass` 結構。<br /><br /> 指定的模組必須載入到處理序。<br /><br /> 若要取得適當的類型名稱，請使用 [Ildasm.exe (IL 反組譯工具)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) 瀏覽該模組。 您也可以將 `*` 當做模組名稱參數傳遞，以便搜尋所有已載入的 Managed 模組。 *module name* 參數也可以是模組的偵錯工具名稱，例如 `mscorlib` 或 `image00400000`。<br /><br /> 這個命令支援 <`module`>`!`<`type`> 的 Windows 偵錯工具語法。 這個類型必須具有完整名稱。|
|**ObjSize** [\<*Object address*>] &#124; [**-aggregate**] [**-stat**]|顯示所指定物件的大小。 如果未指定任何參數，**ObjSize** 命令會顯示在 Managed 執行緒上找到之所有物件的大小，並會顯示處理序中的所有記憶體回收行程控制代碼，以及這些控制代碼所指向之任何物件的總大小。 **ObjSize** 命令會包括父代和其他所有子物件的大小。<br /><br /> **-aggregate** 選項可搭配使用 **-stat** 引數，以取得依然為根目錄之類型的詳細檢視。 藉由使用 **!dumpheap -stat** 和 **!objsize -aggregate -stat**，您可以判斷哪些物件不再是根目錄，以及診斷各種記憶體問題。|
|**PrintException** [**-nested**] [**-lines**] [\<*Exception object address*>]<br /><br /> -或-<br /><br /> **PE** [**-nested**] [\<*Exception object address*>]|顯示並格式化在所指定位址且衍生自 <xref:System.Exception> 類別之任何物件的欄位。 如果您未指定位址，**PrintException** 命令便會顯示目前執行緒上最近一次擲回的例外狀況。<br /><br /> **-nested** 選項會顯示巢狀例外狀況物件的詳細資料。<br /><br /> **-lines** 選項會顯示來源資訊 (如果存在)。<br /><br /> 您可以使用這個命令來格式化和檢視 `_stackTrace` 欄位，此欄位屬於二進位陣列。|
|**ProcInfo** [**-env**] [**-time**] [**-mem**]|顯示處理序的環境變數、核心 CPU 時間，以及記憶體使用統計資料。|
|**RCWCleanupList** \<*RCWCleanupList address*>|顯示在所指定位址上正在等待清除之執行階段可呼叫包裝函式的清單。|
|**SaveModule** \<*Base address*> \<*Filename*>|將在所指定位址上已載入記憶體的影像，寫入至指定的檔案。|
|**SOSFlush**|清除內部 SOS 快取。|
|**StopOnException** [**-derived**] [**-create** &#124; **-create2**] \<*Exception*> \<*Pseudo-register number*>|導致偵錯工具會在擲回所指定例外狀況時停止，但是在擲回其他例外狀況時會繼續執行。<br /><br /> **-derived** 選項會攔截所指定的例外狀況，以及從所指定例外狀況衍生的每一個例外狀況。|
|**SyncBlk** [**-all** &#124; \<*syncblk number*>]|顯示所指定 `SyncBlock` 結構，或是所有的 `SyncBlock` 結構。  如果您沒有傳遞任何引數，**SyncBlk** 命令便會顯示屬於某執行緒擁有之物件的對應 `SyncBlock` 結構。<br /><br /> `SyncBlock` 結構是專門放置並非每一個物件都要建立之額外資訊的容器。 其中可以包含 COM Interop 資料、雜湊碼，以及安全執行緒作業的鎖定資訊。|
|**ThreadPool**|顯示 Managed 執行緒集區的相關資訊，其中包括佇列中工作要求的數目、完成連接埠執行緒的數目，以及計時器的數目。|
|**Token2EE** \<*module name*> \<*token*>|將所指定模組中的已指定中繼資料語彙基元轉變成 `MethodTable` 結構或 `MethodDesc` 結構。<br /><br /> 您可以將 `*` 當做模組名稱參數傳遞，便可了解該語彙基元對應至每一個載入之 Managed 模組中的哪個項目。 您也可以傳遞模組的偵錯工具名稱，例如 `mscorlib` 或 `image00400000`。|
|**Threads** [**-live**] [**-special**]|顯示處理序中的所有 Managed 執行緒。<br /><br /> **Threads** 命令會顯示偵錯工具簡略識別碼、CLR 執行緒識別碼，以及作業系統執行緒識別碼。  此外，**Threads** 命令也會顯示 Domain 資料行、APT 資料行和 Exception 資料行，分別指出執行緒執行所在的應用程式定義域、COM Apartment 模式和執行緒中最近一次擲回的例外狀況。<br /><br /> **-live** 選項會顯示與運作中執行緒建立關聯的執行緒。<br /><br /> **-special** 選項會顯示由 CLR 建立的所有特殊執行緒。 特殊執行緒包括記憶體回收執行緒 (在並行和伺服器記憶體回收中)、偵錯工具 Helper 執行緒、完成項執行緒、<xref:System.AppDomain> 卸載執行緒，以及執行緒集區計時器執行緒。|
|**ThreadState \<** *State value field* **>**|顯示執行緒的狀態。 `value` 參數為 **Threads** 報告輸出中 `State` 欄位的值。<br /><br /> 範例：<br /><br /> `0:003> !Threads     ThreadCount:      2     UnstartedThread:  0     BackgroundThread: 1     PendingThread:    0     DeadThread:       0     Hosted Runtime:   no                                           PreEmptive   GC Alloc           Lock            ID OSID ThreadOBJ    State     GC       Context       Domain   Count APT Exception        0    1  250 0019b068      a020 Disabled 02349668:02349fe8 0015def0     0 MTA        2    2  944 001a6020      b220 Enabled  00000000:00000000 0015def0     0 MTA (Finalizer)     0:003> !ThreadState b220         Legal to Join         Background         CLR Owns         CoInitialized         In Multi Threaded Apartment`|
|**TraverseHeap** [**-xml**] \<*filename*>|使用 CLR 分析工具可了解的格式，將堆積資訊寫入至指定的檔案。 **-xml** 選項會使 **TraverseHeap** 命令將檔案的格式設定為 XML。<br /><br /> 您可以從 [Microsoft 下載中心](https://go.microsoft.com/fwlink/?LinkID=67325)下載 CLR 分析工具。|
|**U** [**-gcinfo**] [**-ehinfo**] [**-n**] \<*MethodDesc address*> &#124; \<*Code address*>|顯示由方法之 `MethodDesc` 結構指標，或是由方法主體內之程式碼位址所指定 Managed 方法的標註反組譯碼。 **U** 命令會顯示從開始到結束的整個方法，以及將中繼資料語彙基元轉換成名稱的註釋。<br /><br /> **-gcinfo** 選項會使 **U** 命令顯示方法的 `GCInfo` 結構。<br /><br /> **-ehinfo** 選項會顯示方法的例外狀況資訊。 您也可以使用 **EHInfo** 命令取得這項資訊。<br /><br /> **-n** 選項會停用原始程式檔名稱和行號的顯示。 如果偵錯工具有指定 SYMOPT_LOAD_LINES 選項，SOS 就會查詢每個 Managed 框架的符號，而且如果成功，就會顯示對應的原始程式檔名稱和行號。 您可以指定 **-n** 選項以停用這種行為。|
|**VerifyHeap**|檢查記憶體回收行程堆積是否有損毀徵兆，並顯示任何所發現的錯誤。<br /><br /> 堆積損毀的原因可能是平台叫用架構不正確的呼叫。|
|**VerifyObj** \<*object address*>|檢查傳遞為引數的物件以找出損毀的症狀。|
|**VMMap**|周遊虛擬位址空間，並顯示每個區域所套用的保護類型。|
|**VMStat**|提供虛擬位址空間的摘要檢視，並依據套用至該記憶體的各種保護類型 (無限制、保留、認可、私用、對應、影像) 進行排列。 TOTAL 資料行會顯示 AVERAGE 資料行乘以 BLK COUNT 資料行的結果。|

## <a name="remarks"></a>備註

SOS 偵錯延伸模組讓您能夠檢視在 CLR 內執行之程式碼的相關資訊。 例如，您可以使用 SOS 偵錯擴充功能來顯示 Managed 堆積的相關資訊、尋找堆積損毀、顯示執行階段所使用的內部資料類型，並檢視在執行階段內執行之所有 Managed 程式碼的資訊。

若要在 Visual Studio 中使用 SOS 偵錯擴充功能，請安裝 [Windows 驅動程式套件 (WDK)](/windows-hardware/drivers/download-the-wdk)。 如需 Visual Studio 的整合式偵錯環境的詳細資訊，請參閱[偵錯環境](/windows-hardware/drivers/debugger/debuggers-in-the-debugging-tools-for-windows-package)。

您可以將它載入 [WinDbg.exe 偵錯工具](/windows-hardware/drivers/debugger/debugger-download-tools)，以及在 WinDbg.exe 中執行命令，以使用 SOS 偵錯擴充功能。

若要將 SOS 偵錯擴充功能載入至 WinDbg.exe 偵錯工具，請在此工具中執行下列命令：

```
.loadby sos clr
```

WinDbg.exe 和 Visual Studio 都會使用對應於目前使用中之 Mscorwks.dll 版本的 SOS.dll 版本。 根據預設，您應該使用符合目前 Mscorwks.dll 版本的 SOS.dll 版本。

若要使用在另一部電腦上建立的傾印檔案，請確定此次安裝所隨附的 Mscorwks.dll 檔案位於您的符號路徑中，然後載入對應的 SOS.dll 版本。

若要載入特定的 SOS.dll 版本，請在 Windows 偵錯工具中輸入下列命令：

```
.load <full path to sos.dll>
```

## <a name="examples"></a>範例

下列命令會顯示在位址 `00ad28d0` 之陣列的內容。  顯示會從第二個元素開始，然後連續顯示五個元素。

```
!dumparray -start 2 -length 5 -detail 00ad28d0
```

 下列命令會顯示在位址 `1ca248` 之組件的內容。

```
!dumpassembly 1ca248
```

 下列命令會顯示記憶體回收行程堆積的相關資訊。

```
!dumpheap
```

 下列命令會將記憶體中壓力記錄檔的內容，寫入目前目錄中名為 StressLog.txt 的預設檔案。

```
!DumpLog
```

 下列命令會顯示在位址 `MethodDesc` 的 `902f40` 結構。

```
!dumpmd 902f40
```

 下列命令會顯示在位址 `1caa50` 之模組的相關資訊。

```
!dumpmodule 1caa50
```

 下列命令會顯示在位址 `a79d40` 之物件的相關資訊。

```
!DumpObj a79d40
```

 下列命令會使用在位址 `00a79d9c` 的方法資料表，來顯示在位址 `0090320c` 之實值類別的欄位。

```
!DumpVC 0090320c 00a79d9c
```

 下列命令會顯示記憶體回收行程所使用的處理序記憶體。

```
!eeheap -gc
```

 下列命令會顯示已排程為最終處理的所有物件。

```
!finalizequeue
```

 下列命令會判斷在位址 `00a79d98`之物件的應用程式定義域。

```
!findappdomain 00a79d98
```

 下列命令會顯示目前處理序中的所有記憶體回收行程控制代碼。

```
!gcinfo 5b68dbb8
```

 下列命令會顯示 `MethodTable` 模組中，`EEClass` 類別之 `Main` 方法的 `MainClass` 和 `unittest.exe` 結構。

```
!name2ee unittest.exe MainClass.Main
```

 下列命令會顯示 `02000003` 模組中，在位址 `unittest.exe` 之中繼資料語彙基元的相關資訊。

```
!token2ee unittest.exe 02000003
```

## <a name="see-also"></a>另請參閱

- [工具](../../../docs/framework/tools/index.md)
- [命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)