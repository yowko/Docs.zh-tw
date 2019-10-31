---
title: 偵錯列舉
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
ms.openlocfilehash: 7948b78da1db5267ce53364af1e4a26ff73801e0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124324"
---
# <a name="debugging-enumerations"></a>偵錯列舉
本節說明偵錯 API 所使用的 Unmanaged 列舉。  
  
## <a name="in-this-section"></a>本章節內容  
 [CLR_DEBUGGING_PROCESS_FLAGS 列舉](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md)  
 提供[ICLRDebugging：： OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)方法所使用的值。  
  
 [CLRDataEnumMemoryFlags 列舉](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md)  
 指出[ICLRDataEnumMemoryRegions：： EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md)方法的呼叫應包含的記憶體區域。  
  
 [COR_PUB_ENUMPROCESS 列舉](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md)  
 識別所要列舉的類型。  
  
 [CorDebugBlockingReason 列舉](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingreason-enumeration.md)  
 指定給定物件上封鎖執行緒的原因。  
  
 CorDebugChainReason  
 指出呼叫鏈結初始化的原因。  
  
 [CorDebugCodeInvokeKind 列舉](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md)  
 描述匯出函式如何叫用 Managed 程式碼。  
  
 [CorDebugCodeInvokePurpose 列舉](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md)  
 描述匯出函式呼叫 Managed 程式碼的原因。  
  
 CorDebugCreateProcessFlags  
 提供可在[ICorDebug：： CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)方法的呼叫中使用的其他偵錯工具選項。  
  
 [CorDebugDebugEventKind 列舉](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)  
 表示[DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)方法解碼其資訊的事件種類。  
  
 [CorDebugDecodeEventFlagsWindows 列舉](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md)  
 提供 Windows 平台上之偵錯事件的其他資訊。  
  
 CorDebugExceptionCallbackType  
 表示從[ICorDebugManagedCallback2：： Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)事件進行的回呼類型。  
  
 [CorDebugExceptionFlags 列舉](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)  
 提供例外狀況的其他資訊。  
  
 CorDebugExceptionUnwindCallbackType  
 指出回呼在回溯階段期間通知的事件。  
  
 [CorDebugGCType 列舉](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md)  
 指出記憶體回收行程是在工作站或伺服器上執行。  
  
 [CorDebugGenerationTypes 列舉](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md)  
 指定 Managed 堆積上的記憶體區域產生方式。  
  
 CorDebugHandleType  
 指出控制代碼類型。  
  
 [CorDebugIlToNativeMappingTypes 列舉](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md)  
 指出特定範圍的原生指令是否對應於特殊程式碼區域。  
  
 CorDebugIntercept  
 指出可以逐步執行的程式碼類型。  
  
 [CorDebugInterfaceVersion 列舉](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md)  
 指定 .NET Framework 版本，或是引進介面之 .NET Framework 的版本。  
  
 CorDebugInternalFrameType  
 識別堆疊框架的類型。  
  
 [CorDebugJITCompilerFlags 列舉](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)  
 包含會影響 Managed Just-In-Time (JIT) 編譯器行為的值。  
  
 [CorDebugJITCompilerFlagsDeprecated 列舉](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflagsdeprecated-enumeration.md)  
 已過時。 請改用[CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)列舉的 `CORDEBUG_JIT_DEFAULT` 成員。  
  
 CorDebugMappingResult  
 提供如何取得指令指標 (IP) 值的詳細資料。  
  
 [CorDebugMDAFlags 列舉](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md)  
 指定會引發 Managed 偵錯助理 (MDA) 的執行緒狀態。  
  
 [CorDebugNGenPolicy 列舉](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md)  
 提供用來判定偵錯工具是否從原生影像快取載入原生 (NGen) 影像的值。  
  
 [CorDebugPlatform 列舉](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)  
 提供[ICorDebugDataTarget：： GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)方法所使用的目標平臺值。  
  
 [CorDebugRecordFormat 列舉](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
 描述包含原生例外狀況偵錯事件相關資訊之位元組陣列中的資料格式。  
  
 CorDebugRegister  
 指定與給定處理器架構相關聯的暫存器。  
  
 [CorDebugSetContextFlag 列舉](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md)  
 指出內容是來自堆疊的作用中 (或分葉) 框架，還是藉由從其他框架回溯而計算出來的。  
  
 [CorDebugStateChange 列舉](../../../../docs/framework/unmanaged-api/debugging/cordebugstatechange-enumeration.md)  
 描述依據處理序變更而必須捨棄的快取資料量。  
  
 CorDebugStepReason  
 指出個別步驟的結果。  
  
 CorDebugThreadState  
 指定要偵錯的執行緒狀態。  
  
 \>CorDebugUnmappedStop  
 指定可在步進器執行程式碼時觸發暫止的未對應程式碼類型。  
  
 CorDebugUserState  
 指出執行緒的使用者狀態。  
  
 [CorGCReferenceType 列舉](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)  
 識別要進行記憶體回收的物件來源。  
  
 [ILCodeKind 列舉](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)  
 提供值，指定偵錯工具是否能夠存取分析工具 ReJIT 檢測中加入的區域變數或程式碼。  
  
 [LoggingLevelEnum 列舉](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md)  
 指出當 Managed 執行緒記錄事件時，寫入至事件記錄檔之描述性訊息的嚴重性層級。  
  
 [LogSwitchCallReason 列舉](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md)  
 指出在切換偵錯/追蹤時所執行的作業。  
  
 [VariableLocationType 列舉](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 表示變數的原生位置類型。  
  
 [WriteableMetadataUpdateMode 列舉](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md)  
 提供值來指定偵錯工具是否可以看見對中繼資料的記憶體中更新。 

 [ClrDataSourceType 列舉](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)提供 CLRDATA_IL_ADDRESS_MAP 結構所使用的值。

## <a name="related-sections"></a>相關章節  
 [偵錯 Coclass](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [偵錯全域靜態函式](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [偵錯結構](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
