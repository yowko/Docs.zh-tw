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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e50421dc15dd30f1811dbe5ebef2ff2f7a0a9483
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755820"
---
# <a name="icorprofilercallbackinitialize-method"></a>ICorProfilerCallback::Initialize 方法
呼叫以初始化程式碼剖析工具，每次啟動新的 common language runtime (CLR) 應用程式時。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
## <a name="parameters"></a>參數  
 `pICorProfilerInfoUnk`  
 [在 ](/cpp/atl/iunknown)分析工具必須查詢的介面[ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)介面指標。  
  
## <a name="remarks"></a>備註  
 `Initialize`呼叫是唯一的機會，啟用 （或停用） 是固定不變的回呼。 一旦啟用回呼`Initialize`呼叫時，它不能使用停用之後[icorprofilerinfo:: Seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)。 COR_PRF_MONITOR_IMMUTABLE 值[COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列舉，指出哪些事件是固定不變。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Shutdown 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)
