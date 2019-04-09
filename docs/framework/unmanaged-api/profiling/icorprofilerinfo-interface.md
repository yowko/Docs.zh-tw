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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b979b5f4ee849b96cd29b6c8e2e6a8932e88c182
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201711"
---
# <a name="icorprofilerinfo-interface"></a>ICorProfilerInfo 介面
提供方法，以供進行通訊與 common language runtime (CLR) 控制事件監視，並要求資訊的程式碼分析工具。  
  
> [!NOTE]
>  每個方法`ICorProfilerInfo`介面傳回 HRESULT，表示成功或失敗。 如需可能的傳回碼的清單，請參閱 CorError.h。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[BeginInprocDebugging 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md)|初始化同處理序偵錯支援。 這個方法是在.NET Framework 2.0 版中已過時。|  
|[EndInprocDebugging 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-endinprocdebugging-method.md)|關閉同處理序偵錯工作階段。 這個方法是在.NET Framework 2.0 版中已過時。|  
|[ForceGC 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)|強制記憶體回收在執行階段內發生。|  
|[GetAppDomainInfo 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getappdomaininfo-method.md)|取得指定的應用程式網域的相關資訊。|  
|[GetAssemblyInfo 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getassemblyinfo-method.md)|取得指定的組件的相關資訊。|  
|[GetClassFromObject 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromobject-method.md)|取得`ClassID`的<br /><br /> 物件，指定其`ObjectID`。|  
|[GetClassFromToken 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromtoken-method.md)|指定中繼資料語彙基元的情況下取得類別的識別碼。 這個方法是在.NET Framework 2.0 版中已過時。 使用[ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)方法改為。|  
|[GetClassIDInfo 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md)|取得指定的類別父模組和中繼資料語彙基元。|  
|[GetCodeInfo 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcodeinfo-method.md)|取得與指定函式識別碼相關聯的機器碼範圍。 這個方法已過時。 使用[ICorProfilerInfo2::GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)方法改為。|  
|[GetCurrentThreadID 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcurrentthreadid-method.md)|如果它是受管理的執行緒，請取得目前執行緒的識別碼。|  
|[GetEventMask 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)|取得目前的分析工具想要從 CLR 接收事件通知的事件類別目錄。|  
|[GetFunctionFromIP 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md)|對應的 managed 程式碼指令指標`FunctionID`。|  
|[GetFunctionFromToken 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromtoken-method.md)|取得函式的識別碼。 這個方法是在.NET Framework 2.0 版中已過時。 使用[ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)方法改為。|  
|[GetFunctionInfo 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctioninfo-method.md)|取得父類別和中繼資料語彙基元指定的函式。|  
|[GetHandleFromThread 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-gethandlefromthread-method.md)|會對應至 Win32 執行緒控制代碼之執行緒的識別碼。|  
|[GetILFunctionBody 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbody-method.md)|Microsoft intermediate language (MSIL) 程式碼，開始標頭中取得方法主體的指標。|  
|[GetILFunctionBodyAllocator 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)|取得提供方法來配置記憶體來用於交換方法主體的 MSIL 程式碼中的介面。|  
|[GetILToNativeMapping 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)|取得從 MSIL 位移的對應，以包含在指定的函式的程式碼的原生位移。|  
|[GetInprocInspectionInterface 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getinprocinspectioninterface-method.md)|ICorDebugProcess 介面取得物件，可進行查詢。 這個方法是在.NET Framework 2.0 版中已過時。|  
|[GetInprocInspectionIThisThread 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getinprocinspectionithisthread-method.md)|ICorDebugThread 介面取得的可查詢的物件。 這個方法是在.NET Framework 2.0 版中已過時。|  
|[GetModuleInfo 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md)|根據模組 ID，傳回模組的檔案名稱和模組的父組件 ID。|  
|[GetModuleMetaData 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md)|取得對應至指定的模組的中繼資料介面執行個體。|  
|[GetObjectSize 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md)|取得指定之物件的大小。|  
|[GetThreadContext 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadcontext-method.md)|取得目前與指定的執行緒相關聯的內容識別。|  
|[GetThreadInfo 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadinfo-method.md)|取得指定的執行緒目前的 Win32 執行緒身分識別。|  
|[GetTokenAndMetadataFromFunction 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-gettokenandmetadatafromfunction-method.md)|取得中繼資料語彙基元和中繼資料介面，可用於語彙基元指定的函式的執行個體。|  
|[IsArrayClass 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-isarrayclass-method.md)|判斷指定的類別是否為陣列類別。|  
|[SetEnterLeaveFunctionHooks 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md)|指定要呼叫 「 輸入 」、 「 保留 」 和 「 tailcall"勾點的受管理的函式的分析工具實作函式。|  
|[SetEventMask 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)|設定值，這個值，指定分析工具想要從 CLR 接收通知的事件類型。|  
|[SetFunctionIDMapper 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)|指定將被呼叫來對應 `FunctionID` 值到替代值的程式碼剖析工具實作函式，這會被傳遞至分析工具函式進入/離開的攔截。|  
|[SetFunctionReJIT 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionrejit-method.md)|未實作。 請勿使用。|  
|[SetILFunctionBody 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)|取代指定的模組中指定的函式的主體。|  
|[SetILInstrumentedCodeMap 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)|指定之位移的指定函式的原始 MSIL 如何對應至新的函式的程式碼剖析工具修改 MSIL 位移。|  
  
## <a name="remarks"></a>備註  
 程式碼剖析工具呼叫中的方法`ICorProfilerInfo`CLR 控制事件監視以及要求資訊與通訊的介面。  
  
 方法的`ICorProfilerInfo`介面由 CLR 使用無限制執行緒模型。 每個方法會傳回 HRESULT，表示成功或失敗。 如需可能的傳回碼的清單，請參閱 CorError.h。  
  
 CLR 通過，透過分析工具的實作[icorprofilercallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)、`ICorProfilerInfo`在初始化期間的每個程式碼剖析工具的介面。 程式碼剖析工具接著可以呼叫的方法`ICorProfilerInfo`介面，以取得正在執行的 CLR 控制下的 managed 程式碼的相關資訊。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerInfo2 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
