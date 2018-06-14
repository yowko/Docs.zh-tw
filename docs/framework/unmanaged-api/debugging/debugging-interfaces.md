---
title: 偵錯介面
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 991e333c53101a2be2a8a19d3960c3d0879619be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33409928"
---
# <a name="debugging-interfaces"></a>偵錯介面
本節說明 Unmanaged 介面，這類介面會處理通用語言執行平台 (CLR) 中所執行之程式的偵錯。  
  
## <a name="in-this-section"></a>本節內容  
 [ICLRDataEnumMemoryRegions 介面](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)  
 提供方法來列舉呼叫端所指定的記憶體區域。  
  
 [ICLRDataEnumMemoryRegionsCallback 介面](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)  
 提供回呼方法，讓 `EnumMemoryRegions` 向偵錯工具報告嘗試列舉指定之記憶體區域的結果。  
  
 [ICLRDataTarget 介面](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 提供方法與目標 CLR 處理序互動。  
  
 [ICLRDataTarget2 介面](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 `ICLRDataTarget` 的子類別，資料存取服務層會使用它來管理目標處理序中的虛擬記憶體區域。  
  
 [ICLRDataTarget3 介面](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 子類別[ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)可提供存取例外狀況資訊。  
  
 [ICLRDebugging 介面](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md)  
 提供處理載入及卸載模組以進行偵錯的方法。  
  
 [ICLRDebuggingLibraryProvider 介面](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)  
 包含[ProvideLibrary 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md)方法，就會取得程式庫提供者回呼介面，common language runtime 版本特定偵錯程式庫找到並載入需求。  
  
 [ICLRMetadataLocator 介面](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)  
 由資料存取服務層用來尋找目標處理序中之組件中繼資料的介面。  
  
 [ICorDebug 介面](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 提供方法讓開發人員於 CLR 環境中為應用程式偵錯。  
  
 [ICorDebugAppDomain 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md)  
 提供偵錯應用程式定義域的方法。  
  
 [ICorDebugAppDomain2 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-interface.md)  
 提供方法來使用陣列、指標、函式指標和 ByRef 類型。 這個介面是 `ICorDebugAppDomain` 介面的擴充。  
  
 [ICorDebugAppDomain3 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)  
 提供在應用程式定義域中使用 [!INCLUDE[wrt](../../../../includes/wrt-md.md)]類型的方法。 這個介面是 `ICorDebugAppDomain` 和 `ICorDebugAppDomain2` 介面的擴充。  
  
 [ICorDebugAppDomain4 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)  
 以邏輯方式擴充[ICorDebugAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md)介面，以從 COM 可呼叫包裝函式取得 managed 的物件。  
  
 [ICorDebugAppDomainEnum 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md)  
 提供方法，此方法會傳回指定數目的 `ICorDebugAppDomain` 值 (從列舉類型中的下一個位置開始)。  
  
 [ICorDebugArrayValue 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-interface.md)  
 表示一維或多維陣列之 `ICorDebugHeapValue` 的子類別。  
  
 [ICorDebugAssembly 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md)  
 表示組件。  
  
 [ICorDebugAssembly2 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly2-interface.md)  
 表示組件。 這個介面是 `ICorDebugAssembly` 介面的擴充。  
  
 [ICorDebugAssembly3 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 以邏輯方式擴充[ICorDebugAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md)介面，以提供支援給容器組件及其所包含的組件。 **適用於僅限.NET Native。**  
  
 [ICorDebugAssemblyEnum 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugassemblyenum-interface.md)  
 實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugAssembly` 陣列。  
  
 [ICorDebugBlockingObjectEnum 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
 提供列舉值的清單[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)結構。  
  
 [ICorDebugBoxValue 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugboxvalue-interface.md)  
 `ICorDebugHeapValue` 的子類別，表示 Boxed 值的類別物件。  
  
 [ICorDebugBreakpoint 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-interface.md)  
 表示函式中的中斷點，或是某個值上的監看點。  
  
 [ICorDebugBreakpointEnum 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-interface.md)  
 實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugBreakpoint` 陣列。  
  
 [ICorDebugChain 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md)  
 表示實體或邏輯呼叫堆疊的區段。  
  
 [ICorDebugChainEnum 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugchainenum-interface.md)  
 實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugChain` 陣列。  
  
 [ICorDebugClass 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)  
 表示類型，可以是基本類型或複雜類型 (亦即，使用者定義類型)。 如果是泛型類型，則 `ICorDebugClass` 表示未具現化的泛型類型。  
  
 [ICorDebugClass2 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-interface.md)  
 表示泛型類別，或是具有 <xref:System.Type> 類型之方法參數的類別。 這個介面延伸 `ICorDebugClass`。  
  
 [ICorDebugCode 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)  
 表示 Microsoft Intermediate Language (MSIL) 程式碼或機器碼的區段。  
  
 [ICorDebugCode2 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md)  
 提供方法來擴充 `ICorDebugCode` 的功能。  
  
 [ICorDebugCode3 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 提供方法，以擴充[ICorDebugCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)和[ICorDebugCode2](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md)提供 managed 傳回值的相關資訊。  
  
 [ICorDebugCode4 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)  
 提供方法，以允許列舉的本機變數和引數的函式中的偵錯工具。  
  
 [ICorDebugCodeEnum 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugcodeenum-interface.md)  
 實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugCode` 陣列。  
  
 [ICorDebugComObjectValue 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)  
 提供擷取快取介面物件的方法。  
  
 [ICorDebugContext 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugcontext-interface.md)  
 表示內容物件。 尚未實作這個介面。  
  
 [ICorDebugController 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-interface.md)  
 表示可以控制程式碼執行內容的範圍 (<xref:System.Diagnostics.Process> 或 <xref:System.AppDomain> 其中一項)。  
  
 [ICorDebugDataTarget 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 提供回呼介面，該介面可供存取特定的目標處理序。  
  
 [ICorDebugDataTarget2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 以邏輯方式擴充[ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)介面。 **適用於僅限.NET Native。**  
  
 [ICorDebugDataTarget3 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)  
 以邏輯方式擴充[ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)介面，以提供載入模組的相關資訊。 **適用於僅限.NET Native。**  
  
 [ICorDebugDebugEvent 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 定義所有 `ICorDebug` 偵錯事件衍生的來源基底介面。 **適用於僅限.NET Native。**  
  
 [ICorDebugEditAndContinueErrorInfo 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinueerrorinfo-interface.md)  
 已過時。 請勿使用這個介面。  
  
 [ICorDebugEditAndContinueSnapshot 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinuesnapshot-interface.md)  
 已過時。 請勿使用這個介面。  
  
 [ICorDebugEnum 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)  
 當做抽象基底介面來偵錯列舉值。  
  
 [ICorDebugErrorInfoEnum 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugerrorinfoenum-interface.md)  
 已過時。 請勿使用這個介面。  
  
 [ICorDebugEval 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-interface.md)  
 提供方法讓偵錯工具執行所偵錯的程式碼內容中的程式碼。  
  
 [ICorDebugEval2 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-interface.md)  
 擴充 `ICorDebugEval` 來提供泛型類型的支援。  
  
 [ICorDebugExceptionDebugEvent 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 擴充[ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)介面，以支援例外狀況事件。 **適用於僅限.NET Native。**  
  
 [ICorDebugExceptionObjectCallStackEnum 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
 提供例外狀況物件中內嵌之呼叫堆疊資訊的列舉值。  
  
 [ICorDebugExceptionObjectValue 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)  
 擴充[ICorDebugObjectValue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md)介面，以提供從 managed 例外狀況物件的堆疊追蹤資訊。  
  
 [ICorDebugFrame 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md)  
 表示目前堆疊上的框架。  
  
 [ICorDebugFrameEnum 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-interface.md)  
 實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugFrame` 陣列。  
  
 [ICorDebugFunction 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md)  
 表示 Managed 函式或方法。  
  
 [ICorDebugFunction2 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-interface.md)  
 以邏輯方式擴充 `ICorDebugFunction`，為 Just My Code 逐步執行的偵錯提供支援。  
  
 [ICorDebugFunction3 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)  
 以邏輯方式擴充[ICorDebugFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md)介面，以提供對 ReJIT 要求的程式碼存取。  
  
 [ICorDebugFunctionBreakpoint 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-interface.md)  
 擴充 `ICorDebugBreakpoint` 來支援函式內的中斷點。  
  
 [ICorDebugGCReferenceEnum 介面](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
 為將要記憶體回收的物件提供列舉值。  
  
 [ICorDebugGenericValue 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-interface.md)  
 套用至所有值之 `ICorDebugValue` 的子類別。 這個介面提供值的 Get 和 Set 方法。  
  
 [ICorDebugGuidToTypeEnum 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
 為對應 GUID 和其相應 `ICorDebugType` 物件的物件提供列舉值。  
  
 [ICorDebugHandleValue 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-interface.md)  
 `ICorDebugReferenceValue` 的子類別，表示偵錯工具已建立記憶體回收控制代碼的參考值。  
  
 [ICorDebugHeapEnum 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
 為 Managed 堆積上的物件提供列舉值。  
  
 [ICorDebugHeapSegmentEnum 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
 為 Managed 堆積的記憶體區域提供列舉值。  
  
 [ICorDebugHeapValue 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-interface.md)  
 `ICorDebugValue` 的子類別，表示 CLR 記憶體回收行程所回收的物件。  
  
 [ICorDebugHeapValue2 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue2-interface1.md)  
 `ICorDebugHeapValue` 的擴充，其支援執行階段控制代碼。  
  
 [ICorDebugHeapValue3 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md)  
 公開物件的監視器鎖定屬性。  
  
 [ICorDebugILCode 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 代表中繼語言 (IL) 程式碼的區段。  
  
 [ICorDebugILCode2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 以邏輯方式擴充[ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)介面，提供方法，傳回的語彙基元函式的區域變數簽章，而且，它將對應剖析工具檢測中繼語言 (IL) 位移至原始方法 IL位移。  
  
 [ICorDebugILFrame 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-interface.md)  
 表示 MSIL 程式碼的堆疊框架。  
  
 [ICorDebugILFrame2 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-interface.md)  
 `ICorDebugILFrame` 的邏輯擴充。  
  
 [ICorDebugILFrame3 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)  
 提供封裝函式傳回值的方法。  
  
 [ICorDebugILFrame4 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 提供的方法可讓您在中繼語言 (IL) 程式碼的框架中，存取區域變數和程式碼。 參數可指定偵錯工具是否能夠存取在分析工具 ReJIT 檢測中加入的變數和程式碼。  
  
 [ICorDebugInstanceFieldSymbol 介面](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 代表執行個體欄位的偵錯符號資訊。 **適用於僅限.NET Native。**  
  
 [ICorDebugInternalFrame 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-interface.md)  
 識別偵錯工具的框架類型。  
  
 [ICorDebugInternalFrame2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 提供內部框架，包括堆疊位址和位置的相關資訊[ICorDebugFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md)物件。  
  
 [ICorDebugLoadedModule 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 提供載入模組的相關資訊。 **適用於僅限.NET Native。**  
  
 [ICorDebugManagedCallback 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)  
 提供方法來處理偵錯工具回呼。  
  
 [ICorDebugManagedCallback2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 提供方法來支援偵錯工具例外狀況處理和 Managed 偵錯助理 (MDA)。 `ICorDebugManagedCallback2` 是 `ICorDebugManagedCallback` 的邏輯擴充。  
  
 [ICorDebugManagedCallback3 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)  
 提供回呼方法，表示已引發啟用的自訂偵錯工具通知。  
  
 [ICorDebugMDA 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 表示 Managed 偵錯助理 (MDA) 訊息。  
  
 [ICorDebugMemoryBuffer 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 代表記憶體內部緩衝區。 **適用於僅限.NET Native。**  
  
 [ICorDebugMergedAssemblyRecord 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 提供合併之組件的相關資訊。 **適用於僅限.NET Native。**  
  
 [ICorDebugMetaDataLocator 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-interface.md)  
 提供中繼資料資訊給偵錯工具。  
  
 [ICorDebugModule 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-interface.md)  
 表示 CLR 模組，其為可執行檔或動態連結程式庫 (DLL)。  
  
 [ICorDebugModule2 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-interface.md)  
 當做 `ICorDebugModule` 的邏輯擴充。  
  
 [ICorDebugModule3 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule3-interface.md)  
 建立動態模組的符號讀取器。  
  
 [ICorDebugModuleBreakpoint 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-interface.md)  
 擴充 `ICorDebugBreakpoint`，以提供特定模組的存取權。  
  
 [ICorDebugModuleDebugEvent 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
 擴充[ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)介面，以支援模組層級事件。 **適用於僅限.NET Native。**  
  
 [ICorDebugModuleEnum 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-interface.md)  
 實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugModule` 陣列。  
  
 [ICorDebugMutableDataTarget 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 擴充[ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)介面，以支援可變動的資料目標。  
  
 [ICorDebugNativeFrame 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-interface.md)  
 用於原生框架的 `ICorDebugFrame` 特定實作。  
  
 [ICorDebugNativeFrame2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 提供測試父子框架關聯的方法。  
  
 [ICorDebugObjectEnum 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-interface.md)  
 實作 `ICorDebugEnum` 方法，並根據物件陣列的相對虛擬位址 (RVA) 來列舉物件陣列。  
  
 [ICorDebugObjectValue 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md)  
 `ICorDebugValue` 的子類別，表示包含物件的值。  
  
 [ICorDebugObjectValue2 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue2-interface.md)  
 擴充 `ICorDebugObjectValue` 來支援繼承和覆寫。  
  
 [ICorDebugProcess 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)  
 表示執行 Managed 程式碼的處理序。  
  
 [ICorDebugProcess2 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-interface1.md)  
 `ICorDebugProcess` 的邏輯擴充。  
  
 [ICorDebugProcess3 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)  
 控制自訂偵錯工具通知。  
  
 [ICorDebugProcess5 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 擴充[ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)介面，以支援存取 managed 堆積，以提供的受管理物件，記憶體回收的相關資訊，以及判斷偵錯工具是否從應用程式載入映像的本機原生映像快取。  
  
 [ICorDebugProcess6 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 以邏輯方式擴充[ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)介面，以啟用功能，例如解碼會以原生例外狀況偵錯事件，以及虛擬模組分割編碼的 managed 偵錯事件。 **適用於僅限.NET Native。**  
  
 [ICorDebugProcess7 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)  
 提供用來設定偵錯工具的方法，以控制代碼目標處理序中的記憶體中中繼資料更新。  
  
 [ICorDebugProcess8 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)  
 以邏輯方式擴充[ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)介面，以啟用或停用特定類型的[ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)例外狀況回呼。  
  
 [ICorDebugProcessEnum 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugprocessenum-interface.md)  
 實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugProcess` 陣列。  
  
 [ICorDebugReferenceValue 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-interface.md)  
 支援參考類型的 `ICorDebugValue` 子類別。  
  
 [ICorDebugRegisterSet 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 表示目前在機器上執行程式碼的可用暫存器集合。  
  
 [ICorDebugRegisterSet2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 為具有 64 個以上暫存器的硬體平台，擴充 `ICorDebugRegisterSet` 的功能。  
  
 [ICorDebugRemote 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 提供啟動或附加 Managed 偵錯工具至遠端目標處理序的功能。  
  
 [ICorDebugRemoteTarget 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 提供可讓您對 CLR 環境中的 Silverlight 應用程式進行偵錯的方法。  
  
 [ICorDebugRuntimeUnwindableFrame 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugruntimeunwindableframe-interface.md)  
 提供 Unmanaged 方法的支援，這些方法需要通用語言執行平台 (CLR) 才能回溯框架。  
  
 [ICorDebugStackWalk 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 提供用來在執行緒堆疊上取得 Managed 方法或框架的方法。  
  
 [ICorDebugStaticFieldSymbol 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 代表靜態欄位的偵錯符號資訊。 **適用於僅限.NET Native。**  
  
 [ICorDebugStepper 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-interface.md)  
 表示偵錯工具在程式碼執行作業中所執行的步驟，做為命令的發出和完成之間的識別項，並可提供方法來取消步驟。  
  
 [ICorDebugStepper2 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-interface1.md)  
 提供 Just My Code (JMC) 偵錯的支援。  
  
 [ICorDebugStepperEnum 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-interface.md)  
 實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugStepper` 陣列。  
  
 [ICorDebugStringValue 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-interface.md)  
 套用至字串值之 `ICorDebugHeapValue` 的子類別。  
  
 [ICorDebugSymbolProvider 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 提供可用來擷取偵錯符號資訊的方法。 **適用於僅限.NET Native。**  
  
 [ICorDebugSymbolProvider2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 以邏輯方式擴充[ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)介面，以擷取其他偵錯符號資訊。 **適用於僅限.NET Native。**  
  
 [ICorDebugThread 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-interface.md)  
 表示處理序中的執行緒。 `ICorDebugThread` 執行個體的存留期與其所表示的執行緒之存留期相同。  
  
 [ICorDebugThread2 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interface.md)  
 當做 `ICorDebugThread` 的邏輯擴充。  
  
 [ICorDebugThread3 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md)  
 提供的進入點[ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)及對應介面。  
  
 [ICorDebugThread4 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 提供執行緒封鎖資訊。  
  
 [ICorDebugThreadEnum 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-interface1.md)  
 實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugThread` 陣列。  
  
 [ICorDebugType 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md)  
 表示類型，可以是基本類型或複雜類型 (亦即，使用者定義類型)。 如果是泛型類型，則 `ICorDebugType` 表示具現化的泛型類型。  
  
 [ICorDebugType2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)  
 擴充[ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md)介面擷取類型識別項的基底類型或複雜 （使用者定義） 的型別。  
  
 [ICorDebugTypeEnum 介面 1](../../../../docs/framework/unmanaged-api/debugging/icordebugtypeenum-interface.md)  
 實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugType` 陣列。  
  
 [ICorDebugUnmanagedCallback 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)  
 提供未直接與 CLR 有關之原生事件的告知。  
  
 「 ICorDebugValue"  
 表示所偵錯之處理序中的讀取或寫入值。  
  
 「 ICorDebugValue2"  
 擴充 `ICorDebugValue` 來提供 `ICorDebugType` 的支援。  
  
 [ICorDebugValue3 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 擴充的 」 ICorDebugValue"和"ICorDebugValue2 」 介面以支援大於 2 GB 的陣列。  
  
 「 ICorDebugValueBreakpoint"  
 擴充 `ICorDebugBreakpoint`，以提供特定值的存取權。  
  
 「 ICorDebugValueEnum"  
 實作 `ICorDebugEnum` 方法，並列舉 `ICorDebugValue` 陣列。  
  
 [ICorDebugVariableHome 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 代表本機變數或函式的引數。  
  
 [ICorDebugVariableHomeEnum 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
 提供的本機變數和引數的函式中的列舉值。  
  
 [ICorDebugVariableSymbol 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 擷取變數的偵錯符號資訊。 **適用於僅限.NET Native。**  
  
 [ICorDebugVirtualUnwinder 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-interface.md)  
 提供可協助堆疊回溯的方法。 **適用於僅限.NET Native。**  
  
 [ICorPublish 介面](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)  
 當做發行處理序的一般介面。  
  
 [ICorPublishAppDomain 介面](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)  
 表示及提供與應用程式定義域有關的資訊。  
  
 [ICorPublishAppDomainEnum 介面](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
 提供方法來周遊目前存在於處理序中之 `ICorPublishAppDomain` 物件的集合。  
  
 [ICorPublishEnum 介面](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)  
 當做發行列舉值的抽象基底。  
  
 [ICorPublishProcess 介面](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)  
 提供存取處理序相關資訊的方法。  
  
 [ICorPublishProcessEnum 介面](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
 提供方法來周遊 `ICorPublishProcess` 物件的集合。  
  
## <a name="related-sections"></a>相關章節  
 [偵錯 Coclass](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [偵錯全域靜態函式](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [偵錯列舉](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [偵錯結構](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
