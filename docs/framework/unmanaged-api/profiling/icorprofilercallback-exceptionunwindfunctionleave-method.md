---
title: ICorProfilerCallback::ExceptionUnwindFunctionLeave 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave method [.NET Framework profiling]
- ExceptionUnwindFunctionLeave method [.NET Framework profiling]
ms.assetid: ebaad1d5-ee0a-4cb0-96bc-8ba5d371b747
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a79a9c925392b0ab5e50269479b2f693f1a9b58d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackexceptionunwindfunctionleave-method"></a>ICorProfilerCallback::ExceptionUnwindFunctionLeave 方法
通知分析工具已完成回溯函式回溯階段的例外狀況處理。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ExceptionUnwindFunctionLeave();  
```  
  
## <a name="remarks"></a>備註  
 當`ExceptionUnwindFunctionLeave`呼叫方法、 函式的執行個體和其堆疊資料會從堆疊移除。  
  
 因為堆疊可能不是處於允許記憶體回收，分析工具不應該在這個呼叫時封鎖，因此無法啟用先佔式記憶體回收。 如果嘗試在程式碼剖析工具區塊和記憶體回收，則執行階段會封鎖此回呼傳回之前。  
  
 此外，此通話期間，程式碼剖析工具必須呼叫至 managed 程式碼或任何方式發生原因的 managed 記憶體配置。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ExceptionUnwindFunctionEnter 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)
