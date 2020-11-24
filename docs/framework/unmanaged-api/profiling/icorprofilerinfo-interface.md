---
title: ICorProfilerInfo 介面
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo
helpviewer_keywords:
- ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: eb4e4ce0-06e7-4469-bbc4-edc2eb5da4b1
topic_type:
- apiref
ms.openlocfilehash: a029784a28036e531670ad373893b4256c5864c4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671183"
---
# <a name="icorprofilerinfo-interface"></a>ICorProfilerInfo 介面

提供程式碼分析工具用來與 common language runtime (CLR) 通訊的方法，以控制事件監視和要求資訊。  
  
> [!NOTE]
> 介面中的每個方法會傳回 `ICorProfilerInfo` HRESULT，以表示成功或失敗。 如需可能的傳回碼清單，請參閱 Corerror.h。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[BeginInprocDebugging 方法](icorprofilerinfo-begininprocdebugging-method.md)|初始化同進程的偵錯工具支援。 此方法在 .NET Framework 版本2.0 中已淘汰。|  
|[EndInprocDebugging 方法](icorprofilerinfo-endinprocdebugging-method.md)|關閉同進程的偵錯工具。 此方法在 .NET Framework 版本2.0 中已淘汰。|  
|[ForceGC 方法](icorprofilerinfo-forcegc-method.md)|強制在執行時間中進行垃圾收集。|  
|[GetAppDomainInfo 方法](icorprofilerinfo-getappdomaininfo-method.md)|取得指定之應用程式域的相關資訊。|  
|[GetAssemblyInfo 方法](icorprofilerinfo-getassemblyinfo-method.md)|取得指定元件的相關資訊。|  
|[GetClassFromObject 方法](icorprofilerinfo-getclassfromobject-method.md)|取得 `ClassID`<br /><br /> 物件，指定它的 `ObjectID` 。|  
|[GetClassFromToken 方法](icorprofilerinfo-getclassfromtoken-method.md)|取得類別的識別碼，指定元資料標記。 此方法在 .NET Framework 版本2.0 中已淘汰。 請改用 [ICorProfilerInfo2：： GetClassFromTokenAndTypeArgs](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) 方法。|  
|[GetClassIDInfo 方法](icorprofilerinfo-getclassidinfo-method.md)|取得指定類別的父模組和元資料標記。|  
|[GetCodeInfo 方法](icorprofilerinfo-getcodeinfo-method.md)|取得與指定函式識別碼相關聯的機器碼範圍。 這個方法已過時。 請改用 [ICorProfilerInfo2：： GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) 方法。|  
|[GetCurrentThreadID 方法](icorprofilerinfo-getcurrentthreadid-method.md)|取得目前線程的識別碼（如果它是 managed 執行緒）。|  
|[GetEventMask 方法](icorprofilerinfo-geteventmask-method.md)|取得分析工具想要從 CLR 接收事件通知的目前事件類別目錄。|  
|[GetFunctionFromIP 方法](icorprofilerinfo-getfunctionfromip-method.md)|將 managed 程式碼指令指標對應至 `FunctionID` 。|  
|[GetFunctionFromToken 方法](icorprofilerinfo-getfunctionfromtoken-method.md)|取得函數的識別碼。 此方法在 .NET Framework 版本2.0 中已淘汰。 請改用 [ICorProfilerInfo2：： GetFunctionFromTokenAndTypeArgs](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) 方法。|  
|[GetFunctionInfo 方法](icorprofilerinfo-getfunctioninfo-method.md)|取得指定之函式的父類別和元資料標記。|  
|[GetHandleFromThread 方法](icorprofilerinfo-gethandlefromthread-method.md)|將執行緒的識別碼對應至 Win32 執行緒控制碼。|  
|[GetILFunctionBody 方法](icorprofilerinfo-getilfunctionbody-method.md)|從標頭開始，取得 Microsoft 中繼語言 (MSIL 的方法主體指標) 程式碼。|  
|[GetILFunctionBodyAllocator 方法](icorprofilerinfo-getilfunctionbodyallocator-method.md)|取得介面，這個介面會提供方法來配置要用於在 MSIL 程式碼中交換方法主體的記憶體。|  
|[GetILToNativeMapping 方法](icorprofilerinfo-getiltonativemapping-method.md)|取得從 MSIL 位移到指定函式中所包含之程式碼的原生位移的對應。|  
|[GetInprocInspectionInterface 方法](icorprofilerinfo-getinprocinspectioninterface-method.md)|取得可針對 ICorDebugProcess 介面進行查詢的物件。 此方法在 .NET Framework 版本2.0 中已淘汰。|  
|[GetInprocInspectionIThisThread 方法](icorprofilerinfo-getinprocinspectionithisthread-method.md)|取得可針對 ICorDebugThread 介面進行查詢的物件。 此方法在 .NET Framework 版本2.0 中已淘汰。|  
|[GetModuleInfo 方法](icorprofilerinfo-getmoduleinfo-method.md)|根據模組 ID，傳回模組的檔案名稱和模組的父組件 ID。|  
|[GetModuleMetaData 方法](icorprofilerinfo-getmodulemetadata-method.md)|取得對應至指定模組的中繼資料介面實例。|  
|[GetObjectSize 方法](icorprofilerinfo-getobjectsize-method.md)|取得指定之物件的大小。|  
|[GetThreadContext 方法](icorprofilerinfo-getthreadcontext-method.md)|取得目前與指定的執行緒相關聯的內容身分識別。|  
|[GetThreadInfo 方法](icorprofilerinfo-getthreadinfo-method.md)|取得指定執行緒目前的 Win32 執行緒識別。|  
|[GetTokenAndMetadataFromFunction 方法](icorprofilerinfo-gettokenandmetadatafromfunction-method.md)|取得中繼資料 token 和中繼資料介面的實例，這個中繼資料介面可用於指定之函式的標記。|  
|[IsArrayClass 方法](icorprofilerinfo-isarrayclass-method.md)|判斷指定的類別是否為數組類別。|  
|[SetEnterLeaveFunctionHooks 方法](icorprofilerinfo-setenterleavefunctionhooks-method.md)|指定要在 managed 函式的 "enter"、"leave" 和 "tailcall" 攔截上呼叫的程式碼剖析工具所執行的函式。|  
|[SetEventMask 方法](icorprofilerinfo-seteventmask-method.md)|設定值，這個值會指定分析工具想要從 CLR 接收通知的事件種類。|  
|[SetFunctionIDMapper 方法](icorprofilerinfo-setfunctionidmapper-method.md)|指定將被呼叫來對應 `FunctionID` 值到替代值的程式碼剖析工具實作函式，這會被傳遞至分析工具函式進入/離開的攔截。|  
|[SetFunctionReJIT 方法](icorprofilerinfo-setfunctionrejit-method.md)|未實作。 請勿使用。|  
|[SetILFunctionBody 方法](icorprofilerinfo-setilfunctionbody-method.md)|取代指定模組中指定之函數的主體。|  
|[SetILInstrumentedCodeMap 方法](icorprofilerinfo-setilinstrumentedcodemap-method.md)|指定指定函式的原始 MSIL 位移如何對應至函式的 profiler 修改過之 MSIL 的新位移。|  
  
## <a name="remarks"></a>備註  

 分析工具會在介面中呼叫方法 `ICorProfilerInfo` ，以與 CLR 通訊以控制事件監視和要求資訊。  
  
 介面的方法 `ICorProfilerInfo` 是使用無限制執行緒模型，由 CLR 所執行。 每個方法會傳回 HRESULT，表示成功或失敗。 如需可能的傳回碼清單，請參閱 Corerror.h。  
  
 CLR 會透過程式碼剖析工具的 [ICorProfilerCallback：： Initialize 的實：： Initialize](icorprofilercallback-initialize-method.md)， `ICorProfilerInfo` 在初始化期間對每個程式碼分析工具的介面進行傳遞。 然後，程式碼分析工具可以呼叫介面的方法 `ICorProfilerInfo` ，以取得在 CLR 控制下執行之 managed 程式碼的相關資訊。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [分析介面](profiling-interfaces.md)
- [ICorProfilerInfo2 介面](icorprofilerinfo2-interface.md)
