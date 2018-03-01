---
title: "ICorProfilerInfo 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 08852b10f59e9c400b60287d78c8eb8eed5f109f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo-interface"></a>ICorProfilerInfo 介面
提供程式碼分析工具用來通訊與 common language runtime (CLR)，以控制事件監視及要求資訊的方法。  
  
> [!NOTE]
>  在每個方法`ICorProfilerInfo`介面會傳回 HRESULT，表示成功或失敗。 可能的傳回碼的清單，請參閱 CorError.h。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[BeginInprocDebugging 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md)|初始化同處理序偵錯支援。 這個方法是.NET Framework 2.0 版中已過時。|  
|[EndInprocDebugging 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-endinprocdebugging-method.md)|關閉同處理序的偵錯工作階段。 這個方法是.NET Framework 2.0 版中已過時。|  
|[ForceGC 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)|強制記憶體回收發生在執行階段中。|  
|[GetAppDomainInfo 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getappdomaininfo-method.md)|取得指定的應用程式定義域有關的資訊。|  
|[GetAssemblyInfo 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getassemblyinfo-method.md)|取得指定的組件的相關資訊。|  
|[GetClassFromObject 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromobject-method.md)|取得`ClassID`的<br /><br /> 物件，指定其`ObjectID`。|  
|[GetClassFromToken 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromtoken-method.md)|取得指定中繼資料語彙基元的類別識別碼。 這個方法是.NET Framework 2.0 版中已過時。 使用[icorprofilerinfo2:: Getclassfromtokenandtypeargs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)方法改為。|  
|[GetClassIDInfo 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md)|取得父模組和中繼資料語彙基元，為指定的類別。|  
|[GetCodeInfo 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcodeinfo-method.md)|取得與指定函式識別碼相關聯的機器碼範圍。 這個方法已過時。 使用[icorprofilerinfo2:: Getcodeinfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)方法改為。|  
|[GetCurrentThreadID 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcurrentthreadid-method.md)|取得目前執行緒的識別碼，如果有 managed 的執行緒。|  
|[GetEventMask 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)|取得分析工具要從 CLR 接收事件通知的目前事件分類。|  
|[GetFunctionFromIP 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md)|對應的 managed 程式碼指令指標`FunctionID`。|  
|[GetFunctionFromToken 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromtoken-method.md)|取得函式的識別碼。 這個方法是.NET Framework 2.0 版中已過時。 使用[icorprofilerinfo2:: Getfunctionfromtokenandtypeargs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)方法改為。|  
|[GetFunctionInfo 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctioninfo-method.md)|取得父類別和中繼資料語彙基元的指定函式。|  
|[GetHandleFromThread 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-gethandlefromthread-method.md)|將執行緒的 ID 對應至 Win32 執行緒控制代碼。|  
|[GetILFunctionBody 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbody-method.md)|取得 Microsoft intermediate language (MSIL) 程式碼中，開始標頭在方法主體的指標。|  
|[GetILFunctionBodyAllocator 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)|取得的介面會提供方法來配置記憶體来用於方法主體的 MSIL 程式碼中交換。|  
|[GetILToNativeMapping 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)|到原生位移的指定函式中所包含的程式碼，取得從 MSIL 位移的對應。|  
|[GetInprocInspectionInterface 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getinprocinspectioninterface-method.md)|ICorDebugProcess 介面取得物件，可以進行查詢。 這個方法是.NET Framework 2.0 版中已過時。|  
|[GetInprocInspectionIThisThread 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getinprocinspectionithisthread-method.md)|ICorDebugThread 介面取得的可查詢的物件。 這個方法是.NET Framework 2.0 版中已過時。|  
|[GetModuleInfo 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md)|根據模組 ID，傳回模組的檔案名稱和模組的父組件 ID。|  
|[GetModuleMetaData 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md)|取得對應至指定的模組的中繼資料介面執行個體。|  
|[GetObjectSize 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md)|取得指定之物件的大小。|  
|[GetThreadContext 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadcontext-method.md)|取得目前與指定的執行緒相關聯的內容識別。|  
|[GetThreadInfo 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadinfo-method.md)|取得指定執行緒的目前 Win32 執行緒識別。|  
|[GetTokenAndMetadataFromFunction 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-gettokenandmetadatafromfunction-method.md)|取得中繼資料語彙基元和可用於語彙基元的指定函式的中繼資料介面的執行個體。|  
|[IsArrayClass 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-isarrayclass-method.md)|判斷指定的類別是否為陣列類別。|  
|[SetEnterLeaveFunctionHooks 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md)|指定程式碼剖析工具實作函式上 「 輸入 」、 「 保留 」 和 「 tailcall"攔截 managed 函式的呼叫。|  
|[SetEventMask 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)|設定值，指定分析工具想要從 CLR 接收通知的事件類型。|  
|[SetFunctionIDMapper 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)|指定將被呼叫來對應 `FunctionID` 值到替代值的程式碼剖析工具實作函式，這會被傳遞至分析工具函式進入/離開的攔截。|  
|[SetFunctionReJIT 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionrejit-method.md)|未實作。 請勿使用。|  
|[SetILFunctionBody 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)|取代指定的模組中的指定函式的主體。|  
|[SetILInstrumentedCodeMap 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)|指定之位移的指定函式的原始 MSIL 如何對應至新的函式的程式碼剖析工具修改 MSIL 位移。|  
  
## <a name="remarks"></a>備註  
 程式碼剖析工具呼叫中的方法`ICorProfilerInfo`與 CLR 以控制事件監視及要求資訊進行通訊的介面。  
  
 方法的`ICorProfilerInfo`介面由使用無限制執行緒模型的 CLR 實作。 每個方法會傳回 HRESULT，表示成功或失敗。 可能的傳回碼的清單，請參閱 CorError.h。  
  
 CLR 通過，透過程式碼剖析工具實作[icorprofilercallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)、`ICorProfilerInfo`初始化期間的每個程式碼分析工具的介面。 接著程式碼分析工具可以呼叫的方法`ICorProfilerInfo`介面，以取得在 CLR 的控制項下執行的 managed 程式碼的相關資訊。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [ICorProfilerInfo2 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
