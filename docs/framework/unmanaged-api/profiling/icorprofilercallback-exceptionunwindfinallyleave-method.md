---
title: ICorProfilerCallback::ExceptionUnwindFinallyLeave 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFinallyLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave method [.NET Framework profiling]
- ExceptionUnwindFinallyLeave method [.NET Framework profiling]
ms.assetid: 2350351e-f253-4c0c-a191-f952bc5700e6
topic_type:
- apiref
ms.openlocfilehash: f53d1d66eef0f745e1a0c51c3234ac66eec07315
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866360"
---
# <a name="icorprofilercallbackexceptionunwindfinallyleave-method"></a>ICorProfilerCallback::ExceptionUnwindFinallyLeave 方法
通知分析工具，例外狀況處理的回溯階段已離開 `finally` 子句。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ExceptionUnwindFinallyLeave();  
```  
  
## <a name="remarks"></a>備註  
 分析工具不應在此呼叫期間封鎖，因為堆疊可能不是處於允許垃圾收集的狀態，因此無法啟用「搶先垃圾收集」。 如果分析工具在此封鎖並嘗試垃圾收集，執行時間將會封鎖，直到這個回呼傳回為止。  
  
 此外，在此呼叫期間，分析工具不得呼叫 managed 程式碼，或以任何方式執行 managed 記憶體配置。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [ExceptionUnwindFinallyEnter 方法](icorprofilercallback-exceptionunwindfinallyenter-method.md)
