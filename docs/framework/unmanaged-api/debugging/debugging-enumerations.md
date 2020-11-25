---
title: 偵錯列舉
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
ms.openlocfilehash: bdd4b60d068677ae2a0874b589294ba220f0d854
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722995"
---
# <a name="debugging-enumerations"></a>偵錯列舉

本節說明偵錯 API 所使用的 Unmanaged 列舉。  
  
## <a name="in-this-section"></a>本節內容  

 [CLR_DEBUGGING_PROCESS_FLAGS 列舉](clr-debugging-process-flags-enumeration.md)  
 提供 [ICLRDebugging：： OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) 方法所使用的值。  
  
 [CLRDataEnumMemoryFlags 列舉](clrdataenummemoryflags-enumeration.md)  
 指出呼叫 [ICLRDataEnumMemoryRegions：： EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) 方法應該包含的記憶體區域。  
  
 [COR_PUB_ENUMPROCESS 列舉](cor-pub-enumprocess-enumeration.md)  
 識別所要列舉的類型。  
  
 [CorDebugBlockingReason 列舉](cordebugblockingreason-enumeration.md)  
 指定給定物件上封鎖執行緒的原因。  
  
 CorDebugChainReason  
 指出呼叫鏈結初始化的原因。  
  
 [CorDebugCodeInvokeKind 列舉](cordebugcodeinvokekind-enumeration.md)  
 描述匯出函式如何叫用 Managed 程式碼。  
  
 [CorDebugCodeInvokePurpose 列舉](cordebugcodeinvokepurpose-enumeration.md)  
 描述匯出函式呼叫 Managed 程式碼的原因。  
  
 CorDebugCreateProcessFlags  
 提供可用於呼叫 [ICorDebug：： CreateProcess](icordebug-createprocess-method.md) 方法的其他偵錯工具選項。  
  
 [CorDebugDebugEventKind 列舉](cordebugdebugeventkind-enumeration.md)  
 表示 [DecodeEvent](icordebugprocess6-decodeevent-method.md) 方法解碼其資訊的事件種類。  
  
 [CorDebugDecodeEventFlagsWindows 列舉](cordebugdecodeeventflagswindows-enumeration.md)  
 提供 Windows 平台上之偵錯事件的其他資訊。  
  
 CorDebugExceptionCallbackType  
 指出從 [ICorDebugManagedCallback2：： Exception](icordebugmanagedcallback2-exception-method.md) 事件進行的回呼類型。  
  
 [CorDebugExceptionFlags 列舉](cordebugexceptionflags-enumeration.md)  
 提供例外狀況的其他資訊。  
  
 CorDebugExceptionUnwindCallbackType  
 指出回呼在回溯階段期間通知的事件。  
  
 [CorDebugGCType 列舉](cordebuggctype-enumeration.md)  
 指出記憶體回收行程是在工作站或伺服器上執行。  
  
 [CorDebugGenerationTypes 列舉](cordebuggenerationtypes-enumeration.md)  
 指定 Managed 堆積上的記憶體區域產生方式。  
  
 CorDebugHandleType  
 指出控制代碼類型。  
  
 [CorDebugIlToNativeMappingTypes 列舉](cordebugiltonativemappingtypes-enumeration.md)  
 指出特定範圍的原生指令是否對應於特殊程式碼區域。  
  
 CorDebugIntercept  
 指出可以逐步執行的程式碼類型。  
  
 [CorDebugInterfaceVersion 列舉](cordebuginterfaceversion-enumeration.md)  
 指定 .NET Framework 版本，或是引進介面之 .NET Framework 的版本。  
  
 CorDebugInternalFrameType  
 識別堆疊框架的類型。  
  
 [CorDebugJITCompilerFlags 列舉](cordebugjitcompilerflags-enumeration.md)  
 包含會影響 Managed Just-In-Time (JIT) 編譯器行為的值。  
  
 [CorDebugJITCompilerFlagsDeprecated 列舉](cordebugjitcompilerflagsdeprecated-enumeration.md)  
 已過時。 請改用 `CORDEBUG_JIT_DEFAULT` [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) 列舉的成員。  
  
 CorDebugMappingResult  
 提供如何取得指令指標 (IP) 值的詳細資料。  
  
 [CorDebugMDAFlags 列舉](cordebugmdaflags-enumeration.md)  
 指定會引發 Managed 偵錯助理 (MDA) 的執行緒狀態。  
  
 [CorDebugNGenPolicy 列舉](cordebugngenpolicy-enumeration.md)  
 提供用來判定偵錯工具是否從原生影像快取載入原生 (NGen) 影像的值。  
  
 [CorDebugPlatform 列舉](cordebugplatform-enumeration.md)  
 提供 [ICorDebugDataTarget：： GetPlatform](icordebugdatatarget-getplatform-method.md) 方法所使用的目標平臺值。  
  
 [CorDebugRecordFormat 列舉](cordebugrecordformat-enumeration.md)  
 描述包含原生例外狀況偵錯事件相關資訊之位元組陣列中的資料格式。  
  
 CorDebugRegister  
 指定與給定處理器架構相關聯的暫存器。  
  
 [CorDebugSetContextFlag 列舉](cordebugsetcontextflag-enumeration.md)  
 指出內容是來自堆疊的作用中 (或分葉) 框架，還是藉由從其他框架回溯而計算出來的。  
  
 [CorDebugStateChange 列舉](cordebugstatechange-enumeration.md)  
 描述依據處理序變更而必須捨棄的快取資料量。  
  
 CorDebugStepReason  
 指出個別步驟的結果。  
  
 CorDebugThreadState  
 指定要偵錯的執行緒狀態。  
  
 \>CorDebugUnmappedStop  
 指定可在步進器執行程式碼時觸發暫止的未對應程式碼類型。  
  
 CorDebugUserState  
 指出執行緒的使用者狀態。  
  
 [CorGCReferenceType 列舉](corgcreferencetype-enumeration.md)  
 識別要進行記憶體回收的物件來源。  
  
 [ILCodeKind 列舉](ilcodekind-enumeration.md)  
 提供值，指定偵錯工具是否能夠存取分析工具 ReJIT 檢測中加入的區域變數或程式碼。  
  
 [LoggingLevelEnum 列舉](logginglevelenum-enumeration.md)  
 指出當 Managed 執行緒記錄事件時，寫入至事件記錄檔之描述性訊息的嚴重性層級。  
  
 [LogSwitchCallReason 列舉](logswitchcallreason-enumeration.md)  
 指出在切換偵錯/追蹤時所執行的作業。  
  
 [VariableLocationType 列舉](variablelocationtype-enumeration.md)  
 指出變數的原生位置型別。  
  
 [WriteableMetadataUpdateMode 列舉](writeablemetadataupdatemode-enumeration.md)  
 提供值來指定偵錯工具是否可以看見對中繼資料的記憶體中更新。

 [ClrDataSourceType 列舉](clrdatasourcetype-enumeration.md) 提供 CLRDATA_IL_ADDRESS_MAP 結構所使用的值。

## <a name="related-sections"></a>相關章節  

 [偵錯 Coclass](debugging-coclasses.md)  
  
 [偵錯介面](debugging-interfaces.md)  
  
 [偵錯全域靜態函式](debugging-global-static-functions.md)  
  
 [偵錯結構](debugging-structures.md)
