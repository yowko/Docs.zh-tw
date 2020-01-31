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
ms.openlocfilehash: 534e0672820cc2509f32765274ad970fda69ec5d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866503"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a>ICorProfilerCallback::ExceptionCatcherEnter 方法
通知分析工具，控制項正傳遞至適當的 `catch` 區塊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
## <a name="parameters"></a>參數

- `functionId`

  \[in] 包含 `catch` 區塊之函式的識別碼。
  
- `objectId`

  中的 \[] 所處理之例外狀況的識別碼。

## <a name="remarks"></a>備註  
 只有當 catch 點位於以即時（JIT）編譯器編譯的程式碼中時，才會呼叫 `ExceptionCatcherEnter` 方法。 在非受控碼或執行時間的內部程式碼中攔截到的例外狀況不會呼叫此通知。 因為 `ExceptionThrown` 通知之後，垃圾收集可能已經移動物件，所以會再次傳遞 `objectId` 值。  
  
 分析工具不應在此方法的執行中封鎖，因為堆疊可能不是處於允許垃圾收集的狀態，因此無法啟用「搶先垃圾收集」。 如果分析工具在此處封鎖並嘗試垃圾收集，執行時間將會封鎖，直到這個回呼傳回為止。  
  
 分析工具的此方法的執行不應呼叫 managed 程式碼，或以任何方式進行，以造成 managed 記憶體配置。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [ExceptionCatcherLeave 方法](icorprofilercallback-exceptioncatcherleave-method.md)
