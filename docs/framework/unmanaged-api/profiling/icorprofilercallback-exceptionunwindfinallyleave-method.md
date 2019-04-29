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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7ba62ab2c4df73b570fb1c76adaee44a2a2ce8c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597150"
---
# <a name="icorprofilercallbackexceptionunwindfinallyleave-method"></a>ICorProfilerCallback::ExceptionUnwindFinallyLeave 方法
通知分析工具，回溯階段的例外狀況處理已離開`finally`子句。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ExceptionUnwindFinallyLeave();  
```  
  
## <a name="remarks"></a>備註  
 因為堆疊可能無法在狀態，讓記憶體回收，分析工具不應在此呼叫期間封鎖，因此無法啟用先佔式記憶體回收。 如果嘗試此程式碼剖析工具封鎖和進行記憶體回收，則執行階段將會封鎖此回呼傳回之前。  
  
 此外，此呼叫期間，分析工具必須呼叫至 managed 程式碼，或以任何方式造成 managed 記憶體配置。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ExceptionUnwindFinallyEnter 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)
