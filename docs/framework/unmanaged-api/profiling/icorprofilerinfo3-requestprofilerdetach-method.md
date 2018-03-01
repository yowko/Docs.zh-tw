---
title: "ICorProfilerInfo3::RequestProfilerDetach 方法"
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
- ICorProfilerInfo3.RequestProfilerDetach Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::RequestProfilerDetach
helpviewer_keywords:
- RequestProfilerDetach method [.NET Framework profiling]
- ICorProfilerInfo3::RequestProfilerDetach method [.NET Framework profiling]
ms.assetid: ea102e62-0454-4477-bcf3-126773acd184
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 33a5c45bbb64029177a0a680243dd39a825683e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3requestprofilerdetach-method"></a>ICorProfilerInfo3::RequestProfilerDetach 方法
指示該執行階段中斷與分析工具的連結。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT RequestProfilerDetach(  
   [in] DWORD    dwExpectedCompletionMilliseconds);  
```  
  
#### <a name="parameters"></a>參數  
 `dwExpectedCompletionMilliseconds`  
 [in] 時間長度，以毫秒為單位，Common Language Runtime (CLR) 應該在檢查之前等待，以查看它是否能安全卸載分析工具 。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|中斷連結要求有效，而且現在中斷連結程序會在另一個執行緒上繼續。 中斷連結全部完成時，會發生 `ProfilerDetachSucceeded` 事件。|  
|E_ CORPROF_E_CALLBACK3_REQUIRED|分析工具失敗[iunknown:: Queryinterface](http://go.microsoft.com/fwlink/?LinkID=144867)嘗試[ICorProfilerCallback3](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)介面，它必須實作以支援中斷連結作業。 未嘗試中斷連結。|  
|CORPROF_E_IMMUTABLE_FLAGS_SET|因為分析工具在啟動時將旗標設定為不可變，造成無法中斷連結。 未嘗試中斷連結；分析工具仍然完整連結。|  
|CORPROF_E_IRREVERSIBLE_INSTRUMENTATION_PRESENT|中斷連結是不可能因為使用程式碼剖析工具檢測的 Microsoft intermediate language (MSIL) 程式碼，或插入`enter` / `leave`攔截程序。 未嘗試中斷連結；分析工具仍然完整連結。<br /><br /> **請注意**檢測的 MSIL 是使用分析工具所提供的程式碼[SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)方法。|  
|CORPROF_E_RUNTIME_UNINITIALIZED|在受管理的應用程式中，執行階段尚未初始化。 (也就是說，執行階段尚未完全載入。)當要求中斷連結在分析工具回呼可能會傳回此錯誤碼[icorprofilercallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)方法。|  
|CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT|`RequestProfilerDetach` 在不支援的時間呼叫。 會發生這個錯誤的 managed 執行緒上而不是從內部呼叫該方法[ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)方法或是從[ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)無法容許記憶體回收的方法。 如需詳細資訊，請參閱[CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md)。|  
  
## <a name="remarks"></a>備註  
 在中斷連結程序中，中斷連結的執行緒 (專為對分析工具中斷連結所建立的執行緒) 偶爾會檢查是否所有執行緒都結束分析工具的程式碼。 分析工具應該透過 `dwExpectedCompletionMilliseconds` 參數提供所需時間的估計。 要使用的理想值是分析工具花在任何指定的 `ICorProfilerCallback*` 方法上所需的典型時間量；此值不應小於分析工具預期所需最大時間量的一半。  
  
 中斷連結執行緒使用 `dwExpectedCompletionMilliseconds` 來決定睡眠多久之後，再檢查分析工具回呼程式碼是否已迅速卸離所有堆疊。 雖然下列演算法的詳細資料可能會在未來版本中的 CLR 有所變更，它也說明了一種 `dwExpectedCompletionMilliseconds` 能夠用來判斷何時可安全卸載分析工具的方式。 中斷連結執行緒先睡眠 `dwExpectedCompletionMilliseconds` 毫秒。 如果從睡眠狀態喚醒後，CLR 發現分析工具回呼程式碼是仍然存在，中斷連結執行緒會再次睡眠，此時兩次`dwExpectedCompletionMilliseconds`毫秒為單位。 從這個第二個睡眠狀態喚醒後，如果卸離執行緒發現分析工具回呼程式碼仍然存在，它會睡眠 10 分鐘後再檢查一次。 中斷連結執行緒會每隔 10 分鐘重新檢查一次。  
  
 如果分析工具指定 `dwExpectedCompletionMilliseconds` 為 0 (零) 時，CLR 會使用預設值為 5000，這表示它會在 5 秒後執行檢查，接著 10 秒後再次檢查，然後之後每隔 10 分鐘一次。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [ICorProfilerInfo3 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [程式碼剖析](../../../../docs/framework/unmanaged-api/profiling/index.md)
