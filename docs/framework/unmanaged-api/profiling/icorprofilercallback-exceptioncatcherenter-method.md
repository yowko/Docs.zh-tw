---
title: ICorProfilerCallback::ExceptionCatcherEnter 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCatcherEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter method [.NET Framework profiling]
- ExceptionCatcherEnter method [.NET Framework profiling]
ms.assetid: 41462329-a648-46f0-ae6d-728b94c31aa9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a9b47e1d1bfa1d8f6c970e95fe25f62a690d3b91
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143860"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a>ICorProfilerCallback::ExceptionCatcherEnter 方法
通知控制項已傳遞至適當的分析工具`catch`區塊。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
## <a name="parameters"></a>參數  
 `functionId`  
 [in]包含的函式的識別項`catch`區塊。  
  
 `objectId`  
 [in]正在處理的例外狀況的識別項。  
  
## <a name="remarks"></a>備註  
 `ExceptionCatcherEnter`只有 catch 點是在 just-in-time (JIT) 編譯器編譯的程式碼呼叫方法。 在 unmanaged 程式碼，或執行階段內部的程式碼中攔截到例外狀況不會呼叫這項通知。 `objectId`值會傳遞一次進行記憶體回收可能移因為物件由於`ExceptionThrown`通知。  
  
 因為堆疊可能無法在狀態，讓記憶體回收，分析工具不應在實作這個方法封鎖，因此無法啟用先佔式記憶體回收。 如果分析工具會封鎖這裡並嘗試進行記憶體回收、 執行階段將會封鎖，直到此回呼中傳回。  
  
 Managed 程式碼，或以任何方式造成 managed 記憶體配置，不應該呼叫這個方法的程式碼剖析工具的實作。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ExceptionCatcherLeave 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)
