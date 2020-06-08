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
ms.openlocfilehash: ea4fc8ab39d616415106150f56f4b7afd5f68237
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500100"
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
 `Initialize`呼叫是啟用（或停用）不變回呼的唯一機會。 一旦呼叫啟用回呼 `Initialize` ，稍後將無法使用[ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md)予以停用。 [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md)列舉的 COR_PRF_MONITOR_IMMUTABLE 值會指出哪些事件是不可變的。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [Shutdown 方法](icorprofilercallback-shutdown-method.md)
