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
ms.openlocfilehash: 26df1599af247bd08d3702d4ef3c5aa2f648620c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720369"
---
# <a name="icorprofilercallbackinitialize-method"></a>ICorProfilerCallback::Initialize 方法

每當新的 common language runtime (CLR) 應用程式啟動時呼叫，就會將程式碼分析工具初始化。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
## <a name="parameters"></a>參數

- `pICorProfilerInfoUnk`

  \[in] 程式碼剖析工具必須查詢[ICorProfilerInfo](icorprofilerinfo-interface.md)介面指標的[IUnknown](/cpp/atl/iunknown)介面指標。  

## <a name="remarks"></a>備註  

 `Initialize`呼叫是啟用 (或停用不可變) 回呼的唯一機會。 一旦呼叫啟用回呼 `Initialize` ，之後就無法使用 [ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md)停用回呼。 [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md)列舉的 COR_PRF_MONITOR_IMMUTABLE 值指出哪些事件是不可變的。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [Shutdown 方法](icorprofilercallback-shutdown-method.md)
