---
title: "COR_PRF_SUSPEND_REASON 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_SUSPEND_REASON
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_SUSPEND_REASON
helpviewer_keywords: COR_PRF_SUSPEND_REASON enumeration [.NET Framework profiling]
ms.assetid: 75594833-bed3-47b2-a426-b75c5fe6fbcf
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: aef9688d3da047645d53f6fcf113153393780c8c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="corprfsuspendreason-enumeration"></a>COR_PRF_SUSPEND_REASON 列舉
指出執行階段已暫止的原因。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum {  
    COR_PRF_SUSPEND_OTHER                   = 0x00,  
    COR_PRF_SUSPEND_FOR_GC                  = 0x01,  
    COR_PRF_SUSPEND_FOR_APPDOMAIN_SHUTDOWN  = 0x02,  
    COR_PRF_SUSPEND_FOR_CODE_PITCHING       = 0x03,  
    COR_PRF_SUSPEND_FOR_SHUTDOWN            = 0x04,  
    COR_PRF_SUSPEND_FOR_INPROC_DEBUGGER     = 0x06,  
    COR_PRF_SUSPEND_FOR_GC_PREP             = 0x07,    COR_PRF_SUSPEND_FOR_REJIT               = 8  
} COR_PRF_SUSPEND_REASON;  
```  
  
## <a name="members"></a>成員  
  
|成員|說明|  
|------------|-----------------|  
|`COR_PRF_FIELD_SUSPEND_OTHER`|執行階段會暫停，未指定原因。|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|執行階段會暫停服務記憶體回收要求。<br /><br /> 記憶體回收相關集合回呼之間發生[icorprofilercallback:: Runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)和[icorprofilercallback:: Runtimeresumestarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md)回呼。|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|執行階段會暫停，讓`AppDomain`可以關機。<br /><br /> 執行階段暫停時，執行階段會判定哪一個執行緒中`AppDomain`也就是正在關閉，並將它們設中止時即會回復。 有沒有`AppDomain`-擱置期間的特定回呼。|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|執行階段會暫停，以便推銷程式碼進行。<br /><br /> 推銷程式碼展示僅當在 just-in-time (JIT) 編譯器在作用中與推銷程式碼啟用。 程式碼之間發生推銷碼回呼`ICorProfilerCallback::RuntimeSuspendFinished`和`ICorProfilerCallback::RuntimeResumeStarted`回呼。 **注意：** CLR JIT 不形函式在.NET Framework 2.0 版中，所以此值不會使用 2.0 中。|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|執行階段會暫停，讓它可以關機。 它必須暫停所有執行緒完成作業。|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|暫止執行階段同處理序偵錯。|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|執行階段會暫停來準備記憶體回收。|  
|`COR_PRF_SUSPEND_FOR_REJIT`|執行階段會暫停進行 JIT 重新編譯。|  
  
## <a name="remarks"></a>備註  
 允許在 unmanaged 程式碼中的所有執行階段執行緒繼續執行，直到嘗試重新進入執行階段，此時它們也會暫止之前執行階段會繼續執行。 這也適用於新的執行緒進入執行階段。 在執行階段內的所有執行緒會立即暫停，如果它們是在可中斷的程式碼，或是要求暫止時執行到可中斷的程式碼。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [分析列舉](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
