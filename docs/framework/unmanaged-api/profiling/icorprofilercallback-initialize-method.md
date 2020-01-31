---
title: ICorProfilerCallback::Initialize 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Initialize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Initialize
helpviewer_keywords:
- Initialize method, ICorProfilerCallback interface [.NET Framework profiling]
- ICorProfilerCallback::Initialize method [.NET Framework profiling]
ms.assetid: dc5fab2a-4b45-4b12-8727-b89c9915f23e
topic_type:
- apiref
ms.openlocfilehash: e4a003b30c495852a3a68d44d92bef35c3ed7812
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866289"
---
# <a name="icorprofilercallbackinitialize-method"></a>ICorProfilerCallback::Initialize 方法
呼叫以在每次啟動新的 common language runtime （CLR）應用程式時初始化程式碼分析工具。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
## <a name="parameters"></a>參數

- `pICorProfilerInfoUnk`

  \[in] [IUnknown](/cpp/atl/iunknown)介面的指標，分析工具必須查詢[ICorProfilerInfo](icorprofilerinfo-interface.md)介面指標。  

## <a name="remarks"></a>備註  
 `Initialize` 呼叫是啟用（或停用）不變回呼的唯一機會。 一旦 `Initialize` 呼叫啟用回呼，稍後就無法使用[ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md)予以停用。 [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md)列舉的 COR_PRF_MONITOR_IMMUTABLE 值會指出哪些事件是不可變的。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [Shutdown 方法](icorprofilercallback-shutdown-method.md)
