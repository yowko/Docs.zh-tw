---
title: 偵錯介面
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
ms.openlocfilehash: c4b9cdc2bc90096ab7c3b041bd8aa2742b48c35c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179170"
---
# <a name="debugging-interfaces"></a>偵錯介面
本節說明 Unmanaged 介面，這類介面會處理通用語言執行平台 (CLR) 中所執行之程式的偵錯。  
  
## <a name="in-this-section"></a>本節內容  
 [ICLR 資料記憶區介面](iclrdataenummemoryregions-interface.md)\
 提供方法來列舉呼叫端所指定的記憶體區域。  
  
 [ICLRDataEnum記憶體區域回檔介面](iclrdataenummemoryregionscallback-interface.md)\
 提供回呼方法，讓 `EnumMemoryRegions` 向偵錯工具報告嘗試列舉指定之記憶體區域的結果。  
  
 [ICLR資料目標介面](iclrdatatarget-interface.md)\
 提供方法與目標 CLR 處理序互動。  
  
 [ICLRDataTarget2 介面](iclrdatatarget2-interface.md)\
 `ICLRDataTarget` 的子類別，資料存取服務層會使用它來管理目標處理序中的虛擬記憶體區域。  
  
 [ICLRDataTarget3 介面](iclrdatatarget3-interface.md)\
 [ICLRDataTarget2](iclrdatatarget2-interface.md)的子類，提供對異常資訊的訪問。  
  
 [ICLR調試介面](iclrdebugging-interface.md)\
 提供處理載入及卸載模組以進行偵錯的方法。  
  
 [ICLR調試庫提供程式介面](iclrdebugginglibraryprovider-interface.md)\
 包括[ProvideLibrary 方法](iclrdebugginglibraryprovider-providelibrary-method.md)，該方法獲取庫提供程式回檔介面，允許按需定位和載入通用語言運行時特定調試庫。  
  
 [ICLR元形定位器介面](iclrmetadatalocator-interface.md)\
 由資料存取服務層用來尋找目標處理序中之組件中繼資料的介面。  
  
 [ICorDebug 介面](icordebug-interface.md)\
 提供方法讓開發人員於 CLR 環境中為應用程式偵錯。  
  
 [ICorDebugApp域介面](icordebugappdomain-interface.md)\
 提供偵錯應用程式定義域的方法。  
  
 [ICorDebugAppDomain2 介面](icordebugappdomain2-interface.md)\
 提供方法來使用陣列、指標、函式指標和 ByRef 類型。 這個介面是 `ICorDebugAppDomain` 介面的擴充。  
  
 [ICorDebugAppDomain3 介面](icordebugappdomain3-interface.md)\
 提供了用於在應用程式域中處理 Windows 運行時類型的方法。 這個介面是 `ICorDebugAppDomain` 和 `ICorDebugAppDomain2` 介面的擴充。  
  
 [ICorDebugAppDomain4 介面](icordebugappdomain4-interface.md)\
 從邏輯上擴展[ICorDebugAppDomain](icordebugappdomain-interface.md)介面，以便從 COM 可調用包裝器獲取託管物件。  
  
 [ICorDebugAppDomainEnum 介面](icordebugappdomainenum-interface.md)\
 提供方法，此方法會傳回指定數目的 `ICorDebugAppDomain` 值 (從列舉類型中的下一個位置開始)。  
  
 [ICorDebugarray值介面](icordebugarrayvalue-interface.md)\
 表示一維或多維陣列之 `ICorDebugHeapValue` 的子類別。  
  
 [ICorDebug組裝介面](icordebugassembly-interface.md)\
 表示組件。  
  
 [ICorDebugAssembly2 介面](icordebugassembly2-interface.md)\
 表示組件。 這個介面是 `ICorDebugAssembly` 介面的擴充。  
  
 [ICorDebugAssembly3 介面](icordebugassembly3-interface.md)\
 從邏輯上講，擴展[ICorDebugAssembly](icordebugassembly-interface.md)介面，以支援容器程式集及其包含的程式集。 **僅適用於 .NET 原生。**  
  
 [ICorDebug組裝Enum介面](icordebugassemblyenum-interface.md)\
 實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugAssembly` 陣列。  
  
 [ICorDebugBlockingobjectenum 介面](icordebugblockingobjectenum-interface.md)\
 為[CorDebugBlockingObject 結構](cordebugblockingobject-structure.md)清單提供枚舉器。  
  
 [ICorDebugBox值介面](icordebugboxvalue-interface.md)\
 `ICorDebugHeapValue` 的子類別，表示 Boxed 值的類別物件。  
  
 [ICorDebug中斷點介面](icordebugbreakpoint-interface.md)\
 表示函式中的中斷點，或是某個值上的監看點。  
  
 [ICorDebug突破點Enum介面](icordebugbreakpointenum-interface.md)\
 實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugBreakpoint` 陣列。  
  
 [ICorDebug鏈介面](icordebugchain-interface.md)\
 表示實體或邏輯呼叫堆疊的區段。  
  
 [ICorDebugChainEnum 介面](icordebugchainenum-interface.md)\
 實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugChain` 陣列。  
  
 [ICorDebug 類介面](icordebugclass-interface.md)\
 表示類型，可以是基本類型或複雜類型 (亦即，使用者定義類型)。 如果是泛型類型，則 `ICorDebugClass` 表示未具現化的泛型類型。  
  
 [ICorDebugClass2 介面](icordebugclass2-interface.md)\
 表示泛型類別，或是具有 <xref:System.Type> 類型之方法參數的類別。 這個介面延伸 `ICorDebugClass`。  
  
 [ICorDebugCode介面](icordebugcode-interface1.md)\
 表示 Microsoft Intermediate Language (MSIL) 程式碼或機器碼的區段。  
  
 [ICorDebugCode2 介面](icordebugcode2-interface.md)\
 提供方法來擴充 `ICorDebugCode` 的功能。  
  
 [ICorDebugCode3 介面](icordebugcode3-interface.md)\
 提供擴展[ICorDebugCode 和](icordebugcode-interface1.md) [ICorDebugCode2](icordebugcode2-interface.md)的方法，以提供有關託管傳回值的資訊。  
  
 [ICorDebugCode4 介面](icordebugcode4-interface.md)\
 提供一種方法，使調試器能夠枚舉函數中的區域變數和參數。  
  
 [ICorDebugCodeEnum 介面](icordebugcodeenum-interface.md)\
 實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugCode` 陣列。  
  
 [ICorDebugcom物件值介面](icordebugcomobjectvalue-interface.md)\
 提供擷取快取介面物件的方法。  
  
 [ICorDebug上下文介面](icordebugcontext-interface.md)\
 表示內容物件。 尚未實作這個介面。  
  
 [ICorDebug控制器介面](icordebugcontroller-interface.md)\
 表示可以控制程式碼執行內容的範圍 (<xref:System.Diagnostics.Process> 或 <xref:System.AppDomain> 其中一項)。  
  
 [ICorDebug資料目標介面](icordebugdatatarget-interface.md)\
 提供回呼介面，該介面可供存取特定的目標處理序。  
  
 [ICorDebugDataTarget2 介面](icordebugdatatarget2-interface.md)\
 從邏輯上講擴展[ICorDebugDataTarget](icordebugdatatarget-interface.md)介面。 **僅適用於 .NET 原生。**  
  
 [ICorDebugDataTarget3 介面](icordebugdatatarget3-interface.md)\
 從邏輯上講[，ICorDebugDataTarget](icordebugdatatarget-interface.md)介面可以提供有關已載入模組的資訊。 **僅適用於 .NET 原生。**  
  
 [ICorDebugevent 介面](icordebugdebugevent-interface.md)\
 定義所有 `ICorDebug` 偵錯事件衍生的來源基底介面。 **僅適用於 .NET 原生。**  
  
 [ICordebugedit 和繼續錯誤資訊介面](icordebugeditandcontinueerrorinfo-interface.md)\
 已過時。 請勿使用這個介面。  
  
 [ICordebugedit 並繼續快照介面](icordebugeditandcontinuesnapshot-interface.md)\
 已過時。 請勿使用這個介面。  
  
 [ICorDebugEnum 介面](icordebugenum-interface1.md)\
 當做抽象基底介面來偵錯列舉值。  
  
 [ICorDebug錯誤資訊資訊介面](icordebugerrorinfoenum-interface.md)\
 已過時。 請勿使用這個介面。  
  
 [ICorDebugEval 介面](icordebugeval-interface.md)\
 提供方法讓偵錯工具執行所偵錯的程式碼內容中的程式碼。  
  
 [ICorDebugEval2 介面](icordebugeval2-interface.md)\
 擴充 `ICorDebugEval` 來提供泛型類型的支援。  
  
 [ICorDebugException調試事件介面](icordebugexceptiondebugevent-interface.md)\
 擴展[ICorDebugDebugEvent 介面](icordebugdebugevent-interface.md)以支援異常事件。 **僅適用於 .NET 原生。**  
  
 [ICorDebugException 物件調用StackEnum介面](icordebugexceptionobjectcallstackenum-interface.md)\
 提供例外狀況物件中內嵌之呼叫堆疊資訊的列舉值。  
  
 [ICorDebugException 物件值介面](icordebugexceptionobjectvalue-interface.md)\
 擴展[ICorDebugObjectValue](icordebugobjectvalue-interface.md)介面，從託管異常物件提供堆疊追蹤資訊。  
  
 [ICorDebugFrame 介面](icordebugframe-interface.md)\
 表示目前堆疊上的框架。  
  
 [ICorDebugFrameenum 介面](icordebugframeenum-interface.md)\
 實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugFrame` 陣列。  
  
 [ICorDebug功能介面](icordebugfunction-interface1.md)\
 表示 Managed 函式或方法。  
  
 [ICorDebug功能2介面](icordebugfunction2-interface.md)\
 以邏輯方式擴充 `ICorDebugFunction`，為 Just My Code 逐步執行的偵錯提供支援。  
  
 [ICorDebug功能3介面](icordebugfunction3-interface.md)\
 從邏輯上講[，ICorDebug函數](icordebugfunction-interface1.md)介面提供從 ReJIT 請求對代碼的訪問。  
  
 [ICorDebug功能中斷點介面](icordebugfunctionbreakpoint-interface.md)\
 擴充 `ICorDebugBreakpoint` 來支援函式內的中斷點。  
  
 [ICorDebugGC參考介面](icordebuggcreferenceenum-interface.md)\
 為將要記憶體回收的物件提供列舉值。  
  
 [ICorDebug 通用值介面](icordebuggenericvalue-interface.md)\
 套用至所有值之 `ICorDebugValue` 的子類別。 這個介面提供值的 Get 和 Set 方法。  
  
 [ICordebugguidtotypeenum 介面](icordebugguidtotypeenum-interface.md)\
 為對應 GUID 和其相應 `ICorDebugType` 物件的物件提供列舉值。  
  
 [ICorDebugHandle值介面](icordebughandlevalue-interface.md)\
 `ICorDebugReferenceValue` 的子類別，表示偵錯工具已建立記憶體回收控制代碼的參考值。  
  
 [ICorDebugHeapEnum 介面](icordebugheapenum-interface.md)\
 為 Managed 堆積上的物件提供列舉值。  
  
 [ICorDebugHeap分段介面](icordebugheapsegmentenum-interface.md)\
 為 Managed 堆積的記憶體區域提供列舉值。  
  
 [ICorDebugHeap值介面](icordebugheapvalue-interface.md)\
 `ICorDebugValue` 的子類別，表示 CLR 記憶體回收行程所回收的物件。  
  
 [ICorDebugHeapValue2 介面](icordebugheapvalue2-interface1.md)\
 `ICorDebugHeapValue` 的擴充，其支援執行階段控制代碼。  
  
 [ICorDebugHeapValue3 介面](icordebugheapvalue3-interface.md)\
 公開物件的監視器鎖定屬性。  
  
 [ICorDebugIL代碼介面](icordebugilcode-interface.md)\
 代表中繼語言 (IL) 程式碼的區段。  
  
 [ICorDebugILCode2 介面](icordebugilcode2-interface.md)\
 從邏輯上講[，ICorDebugILCode](icordebugilcode-interface.md)介面提供返回函數的本地變數簽名的權杖的方法，並將探測器的檢測中間語言 （IL） 偏移映射到原始方法 IL 偏移量。  
  
 [ICorDebugIL框架介面](icordebugilframe-interface.md)\
 表示 MSIL 程式碼的堆疊框架。  
  
 [ICorDebugILFrame2 介面](icordebugilframe2-interface.md)\
 `ICorDebugILFrame` 的邏輯擴充。  
  
 [ICorDebugILFrame3 介面](icordebugilframe3-interface.md)\
 提供封裝函式傳回值的方法。  
  
 [ICorDebugILFrame4 介面](icordebugilframe4-interface.md)\
 提供的方法可讓您在中繼語言 (IL) 程式碼的框架中，存取區域變數和程式碼。 參數可指定偵錯工具是否能夠存取在分析工具 ReJIT 檢測中加入的變數和程式碼。  
  
 [ICorDebug實例欄位符號介面](icordebuginstancefieldsymbol-interface.md)\
 代表執行個體欄位的偵錯符號資訊。 **僅適用於 .NET 原生。**  
  
 [ICorDebug 內部框架介面](icordebuginternalframe-interface.md)\
 識別偵錯工具的框架類型。  
  
 [ICorDebug 內部框架2介面](icordebuginternalframe2-interface.md)\
 提供有關內部幀的資訊，包括堆疊位址和相對於[ICorDebugFrame](icordebugframe-interface.md)物件的位置。  
  
 [ICorDebugLoaded模組介面](icordebugloadedmodule-interface.md)\
 提供載入模組的相關資訊。 **僅適用於 .NET 原生。**  
  
 [ICorDebug 託管回檔介面](icordebugmanagedcallback-interface.md)\
 提供方法來處理偵錯工具回呼。  
  
 [ICorDebug 託管回檔2介面](icordebugmanagedcallback2-interface.md)\
 提供方法來支援偵錯工具例外狀況處理和 Managed 偵錯助理 (MDA)。 `ICorDebugManagedCallback2` 是 `ICorDebugManagedCallback` 的邏輯擴充。  
  
 [ICorDebug 託管回檔3介面](icordebugmanagedcallback3-interface.md)\
 提供回呼方法，表示已引發啟用的自訂偵錯工具通知。  
  
 [ICordebugMDA 介面](icordebugmda-interface.md)\
 表示 Managed 偵錯助理 (MDA) 訊息。  
  
 [ICorDebug記憶體緩衝器介面](icordebugmemorybuffer-interface.md)\
 代表記憶體內部緩衝區。 **僅適用於 .NET 原生。**  
  
 [ICorDebug 合併裝配記錄介面](icordebugmergedassemblyrecord-interface.md)\
 提供合併組件的相關資訊。 **僅適用於 .NET 原生。**  
  
 [ICorDebugMetaDataLocator介面](icordebugmetadatalocator-interface.md)\
 提供中繼資料資訊給偵錯工具。  
  
 [ICorDebug模組介面](icordebugmodule-interface.md)\
 表示 CLR 模組，其為可執行檔或動態連結程式庫 (DLL)。  
  
 [ICorDebugModule2 介面](icordebugmodule2-interface.md)\
 當做 `ICorDebugModule` 的邏輯擴充。  
  
 [ICorDebug模組3介面](icordebugmodule3-interface.md)\
 建立動態模組的符號讀取器。  
  
 [ICorDebug模組中斷點介面](icordebugmodulebreakpoint-interface.md)\
 擴充 `ICorDebugBreakpoint`，以提供特定模組的存取權。  
  
 [ICorDebugModule調試事件介面](icordebugmoduledebugevent-interface.md)\
 擴展[ICorDebugDebugEvent 介面](icordebugdebugevent-interface.md)以支援模組層級事件。 **僅適用於 .NET 原生。**  
  
 [ICorDebugModuleEnum 介面](icordebugmoduleenum-interface.md)\
 實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugModule` 陣列。  
  
 [ICorDebugMutable資料目標介面](icordebugmutabledatatarget-interface.md)\
 擴展[ICorDebugDataTarget](icordebugdatatarget-interface.md)介面以支援可變數據目標。  
  
 [ICorDebug本機框架介面](icordebugnativeframe-interface.md)\
 用於原生框架的 `ICorDebugFrame` 特定實作。  
  
 [ICorDebug本機框架2介面](icordebugnativeframe2-interface.md)\
 提供測試父子框架關聯的方法。  
  
 [ICorDebugObjectEnum 介面](icordebugobjectenum-interface.md)\
 實作 `ICorDebugEnum` 方法，並根據物件陣列的相對虛擬位址 (RVA) 來列舉物件陣列。  
  
 [ICorDebug物件值介面](icordebugobjectvalue-interface.md)\
 `ICorDebugValue` 的子類別，表示包含物件的值。  
  
 [ICorDebug物件值2介面](icordebugobjectvalue2-interface.md)\
 擴充 `ICorDebugObjectValue` 來支援繼承和覆寫。  
  
 [ICorDebug進程介面](icordebugprocess-interface.md)\
 表示執行 Managed 程式碼的處理序。  
  
 [ICorDebugProcess2 介面](icordebugprocess2-interface1.md)\
 `ICorDebugProcess` 的邏輯擴充。  
  
 [ICorDebugProcess3 介面](icordebugprocess3-interface.md)\
 控制自訂偵錯工具通知。

 [ICorDebugProcess4 介面](icordebugprocess4-interface.md)\
 支援進程執行失控。
  
 [ICorDebugProcess5 介面](icordebugprocess5-interface.md)\
 擴展[ICorDebugProcess](icordebugprocess-interface.md)介面以支援對託管堆的訪問，提供有關託管物件的垃圾回收的資訊，並確定調試器是否從應用程式的本地本機映射緩存載入圖像。  
  
 [ICorDebugProcess6 介面](icordebugprocess6-interface.md)\
 從邏輯上講擴展[ICorDebugProcess](icordebugprocess-interface.md)介面，以啟用在本機異常調試事件中編碼的託管調試事件解碼和虛擬模組拆分等功能。 **僅適用於 .NET 原生。**  
  
 [ICorDebugProcess7 介面](icordebugprocess7-interface.md)\
 提供用來設定偵錯工具的方法，以控制代碼目標處理序中的記憶體中中繼資料更新。  
  
 [ICorDebugProcess8 介面](icordebugprocess8-interface.md)\
 從邏輯上講擴展[ICorDebugProcess](icordebugprocess-interface.md)介面，以啟用或禁用某些類型的[ICorDebug 託管回檔2](icordebugmanagedcallback2-interface.md)異常回檔。  
  
 [ICorDebugProcessEnum 介面](icordebugprocessenum-interface.md)\
 實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugProcess` 陣列。  
  
 [ICorDebug參考值介面](icordebugreferencevalue-interface.md)\
 支援參考類型的 `ICorDebugValue` 子類別。  
  
 [ICorDebug註冊集介面](icordebugregisterset-interface.md)\
 表示目前在機器上執行程式碼的可用暫存器集合。  
  
 [ICorDebug註冊集2介面](icordebugregisterset2-interface.md)\
 為具有 64 個以上暫存器的硬體平台，擴充 `ICorDebugRegisterSet` 的功能。  
  
 [ICorDebug遠端介面](icordebugremote-interface.md)\
 提供啟動或附加 Managed 偵錯工具至遠端目標處理序的功能。  
  
 [ICorDebug遠端目標介面](icordebugremotetarget-interface.md)\
 提供可讓您對 CLR 環境中的 Silverlight 應用程式進行偵錯的方法。  
  
 [ICorDebug運行時可展開幀介面](icordebugruntimeunwindableframe-interface.md)\
 提供 Unmanaged 方法的支援，這些方法需要通用語言執行平台 (CLR) 才能回溯框架。  
  
 [ICorDebugStackWalk介面](icordebugstackwalk-interface.md)\
 提供用來在執行緒堆疊上取得 Managed 方法或框架的方法。  
  
 [ICorDebug靜態欄位符號介面](icordebugstaticfieldsymbol-interface.md)\
 代表靜態欄位的偵錯符號資訊。 **僅適用於 .NET 原生。**  
  
 [ICorDebug步進器介面](icordebugstepper-interface.md)\
 表示偵錯工具在程式碼執行作業中所執行的步驟，做為命令的發出和完成之間的識別項，並可提供方法來取消步驟。  
  
 [ICorDebug步進2介面](icordebugstepper2-interface1.md)\
 提供 Just My Code (JMC) 偵錯的支援。  
  
 [ICorDebug步進介面](icordebugstepperenum-interface.md)\
 實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugStepper` 陣列。  
  
 [ICorDebugString值介面](icordebugstringvalue-interface.md)\
 套用至字串值之 `ICorDebugHeapValue` 的子類別。  
  
 [ICorDebug符號提供程式介面](icordebugsymbolprovider-interface.md)\
 提供可用來擷取偵錯符號資訊的方法。 **僅適用於 .NET 原生。**  
  
 [ICorDebug符號提供程式2介面](icordebugsymbolprovider2-interface.md)\
 從邏輯上講，擴展[ICorDebugSymbolProvider 介面](icordebugsymbolprovider-interface.md)以檢索其他調試符號資訊。 **僅適用於 .NET 原生。**  
  
 [ICorDebug執行緒介面](icordebugthread-interface.md)\
 表示處理序中的執行緒。 `ICorDebugThread` 執行個體的存留期與其所表示的執行緒之存留期相同。  
  
 [ICorDebugThread2 介面](icordebugthread2-interface.md)\
 當做 `ICorDebugThread` 的邏輯擴充。  
  
 [ICorDebugThread3 介面](icordebugthread3-interface.md)\
 提供[ICorDebugStackWalk](icordebugstackwalk-interface.md)的進入點和相應的介面。  
  
 [ICorDebugThread4 介面](icordebugthread4-interface.md)\
 提供執行緒封鎖資訊。  
  
 [ICorDebugThreadenum 介面](icordebugthreadenum-interface1.md)\
 實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugThread` 陣列。  
  
 [ICorDebug 類型介面](icordebugtype-interface.md)\
 表示類型，可以是基本類型或複雜類型 (亦即，使用者定義類型)。 如果是泛型類型，則 `ICorDebugType` 表示具現化的泛型類型。  
  
 [ICorDebugType2 介面](icordebugtype2-interface.md)\
 擴展[ICorDebugType](icordebugtype-interface.md)介面以檢索基本類型或複雜（使用者定義）類型的類型識別碼。  
  
 [ICorDebugTypeEnum 介面](icordebugtypeenum-interface.md)\
 實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugType` 陣列。  
  
 [ICorDebugUn託管回檔介面](icordebugunmanagedcallback-interface.md)\
 提供未直接與 CLR 有關之原生事件的告知。  
  
 [ICorDebug值](icordebugvalue-interface.md)\
 表示所偵錯之處理序中的讀取或寫入值。  
  
 [ICorDebugValue2](icordebugvalue2-interface.md)\
 擴充 `ICorDebugValue` 來提供 `ICorDebugType` 的支援。  
  
 [ICorDebugValue3 介面](icordebugvalue3-interface.md)\
 擴展"ICorDebugValue"和"ICorDebugValue2"介面，為大於 2 GB 的陣列提供支援。  
  
 [ICorDebugValue突破點](icordebugvaluebreakpoint-interface.md)\
 擴充 `ICorDebugBreakpoint`，以提供特定值的存取權。  
  
 [ICorDebugValueenum](icordebugvalueenum-interface.md)\
 實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugValue` 陣列。  
  
 [ICorDebug可變家庭介面](icordebugvariablehome-interface.md)\
 表示函數的區域變數或參數。  
  
 [ICorDebug可變家庭介面](icordebugvariablehomeenum-interface.md)\
 向函數中的區域變數和參數提供枚舉器。  
  
 [ICorDebug可變符號介面](icordebugvariablesymbol-interface.md)\
 擷取變數的偵錯符號資訊。 **僅適用於 .NET 原生。**  
  
 [ICorDebug虛擬釋放器介面](icordebugvirtualunwinder-interface.md)\
 提供可協助堆疊回溯的方法。 **僅適用於 .NET 原生。**  
  
 [ICorPublish 介面](icorpublish-interface.md)\
 當做發行處理序的一般介面。  
  
 [ICor發佈應用域介面](icorpublishappdomain-interface.md)\
 表示及提供與應用程式定義域有關的資訊。  
  
 [ICorPublishAppDomainEnum 介面](icorpublishappdomainenum-interface.md)\
 提供方法來周遊目前存在於處理序中之 `ICorPublishAppDomain` 物件的集合。  
  
 [ICorPublishEnum 介面](icorpublishenum-interface.md)\
 當做發行列舉值的抽象基底。  
  
 [ICor發佈過程介面](icorpublishprocess-interface.md)\
 提供存取處理序相關資訊的方法。  
  
 [ICorPublishProcessEnum 介面](icorpublishprocessenum-interface.md)\
 提供方法來周遊 `ICorPublishProcess` 物件的集合。  

 [ISOSDac介面介面](isosdacinterface-interface.md)\
 提供從 訪問資料的協助程式方法`SOS`。

 [IXCLRData方法定義介面](ixclrdatamethoddefinition-interface.md)\
 提供查詢有關方法定義的資訊的方法。

 [IXCLRData方法實例介面](ixclrdatamethodinstance-interface.md)\
 提供查詢方法實例資訊的方法。

 [IXCLR資料模組介面](ixclrdatamodule-interface.md)\
 提供查詢有關載入模組的資訊的方法。

 [IXCLR資料處理介面](ixclrdataprocess-interface.md)\
 提供了查詢有關進程的資訊的方法。
  
## <a name="related-sections"></a>相關章節  
 [調試同類](debugging-coclasses.md)\
 [調試全域靜態函數](debugging-global-static-functions.md)\
 [調試枚舉](debugging-enumerations.md)\
 [調試結構](debugging-structures.md)\
