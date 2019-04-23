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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 21533b5173bcd91d0c944fbde4eafc9817de8315
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220054"
---
# <a name="corprfsuspendreason-enumeration"></a>COR_PRF_SUSPEND_REASON 列舉
表示執行階段已暫止的原因。  
  
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
  
|成員|描述|  
|------------|-----------------|  
|`COR_PRF_FIELD_SUSPEND_OTHER`|執行階段會暫停，未指定原因。|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|執行階段暫止記憶體回收集合要求。<br /><br /> 之間發生的記憶體回收相關集合回呼[icorprofilercallback:: Runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)並[icorprofilercallback:: Runtimeresumestarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md)回呼。|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|執行階段會暫停，讓`AppDomain`可以關機。<br /><br /> 執行階段暫停期間，執行階段會判斷哪一個執行緒都會在`AppDomain`也就是正在關閉，並將它們設定成在恢復時中止。 有沒有`AppDomain`-在這個暫止期間的特定回呼。|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|執行階段會暫停，以便推銷程式碼進行。<br /><br /> 推銷程式碼都能彼此吻合僅當在 just-in-time (JIT) 編譯器在作用中與啟用推銷程式碼。 程式碼之間發生的推銷回呼`ICorProfilerCallback::RuntimeSuspendFinished`和`ICorProfilerCallback::RuntimeResumeStarted`回呼。 **注意：** 所以此值不用於 2.0 CLR JIT 不在.NET Framework 2.0 版中，講述函式。|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|執行階段會暫停，讓它可以關閉。 它必須暫止所有執行緒完成作業。|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|執行階段會暫停進行同處理序偵錯。|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|執行階段會暫停以準備進行記憶體回收。|  
|`COR_PRF_SUSPEND_FOR_REJIT`|執行階段會暫停進行 JIT 重新編譯。|  
  
## <a name="remarks"></a>備註  
 允許未受管理的程式碼中的所有執行階段執行緒繼續執行，直到嘗試重新進入執行階段，此時它們也會擱置直到執行階段繼續。 這也適用於新的執行緒進入執行階段。 在執行階段內的所有執行緒都在可中斷的程式碼，也就是如果立即暫止，或要求暫止執行到可中斷的程式碼。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [分析列舉](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
