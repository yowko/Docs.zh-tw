---
title: COR_PRF_SUSPEND_REASON 列舉
ms.date: 03/30/2017
api_name:
- COR_PRF_SUSPEND_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SUSPEND_REASON
helpviewer_keywords:
- COR_PRF_SUSPEND_REASON enumeration [.NET Framework profiling]
ms.assetid: 75594833-bed3-47b2-a426-b75c5fe6fbcf
topic_type:
- apiref
ms.openlocfilehash: d2d9ca77e764fe439753f1174a42af5ef80faa59
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447714"
---
# <a name="cor_prf_suspend_reason-enumeration"></a>COR_PRF_SUSPEND_REASON 列舉
指出執行時間暫止的原因。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`COR_PRF_FIELD_SUSPEND_OTHER`|執行時間因未指定的原因而暫止。|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|執行時間已暫止，以服務垃圾收集要求。<br /><br /> 垃圾收集相關的回呼會在[ICorProfilerCallback：： RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)和[ICorProfilerCallback：： RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md)回呼之間發生。|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|執行時間已暫停，因此可以關閉 `AppDomain`。<br /><br /> 當執行時間暫止時，執行時間會判斷哪些執行緒位於正在關閉的 `AppDomain` 中，並將它們設定為在繼續執行時中止。 在此暫止期間，沒有任何 `AppDomain`特定的回呼。|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|執行時間已暫止，因此可以進行程式碼推銷。<br /><br /> 只有在已啟用程式碼推銷的即時（JIT）編譯器處於作用中狀態時，才會進行程式碼推銷接踵而來。 程式碼推銷回呼會在 `ICorProfilerCallback::RuntimeSuspendFinished` 和 `ICorProfilerCallback::RuntimeResumeStarted` 回呼之間發生。 **注意：** CLR JIT 不會在 .NET Framework 版本2.0 中使用函式，因此此值不會用於2.0。|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|執行時間已暫止，使其可以關閉。 它必須暫停所有線程才能完成作業。|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|執行時間已暫止以進行同進程的偵錯工具。|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|執行時間已暫止，準備進行垃圾收集。|  
|`COR_PRF_SUSPEND_FOR_REJIT`|執行時間已暫停以進行 JIT 重新編譯。|  
  
## <a name="remarks"></a>備註  
 在非受控碼中的所有運行時間表程，都允許繼續執行，直到它們嘗試重新進入執行時間為止，此時它們也會暫止，直到執行時間繼續為止。 這也適用于輸入執行時間的新執行緒。 執行時間中的所有線程如果處於可中斷的程式碼中，就會立即暫停，或在到達可中斷的程式碼時要求暫停。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [分析列舉](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
