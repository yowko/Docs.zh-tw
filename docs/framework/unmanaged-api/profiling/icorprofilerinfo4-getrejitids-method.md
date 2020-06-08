---
title: ICorProfilerInfo4::GetReJITIDs 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetReJITIDs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetReJITIDs
helpviewer_keywords:
- GetReJITIDs method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetReJITIDs method [.NET Framework profiling]
ms.assetid: 634ac28c-a5b7-4fc3-af84-256c24ca8177
topic_type:
- apiref
ms.openlocfilehash: ba15440df79dded95a8afa9438657d064e167f36
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495966"
---
# <a name="icorprofilerinfo4getrejitids-method"></a>ICorProfilerInfo4::GetReJITIDs 方法
傳回識別碼的陣列，識別仍然配置的指定函式的所有 JIT 重新編譯版本。 這包括 JIT 重新編譯的函式版本，這些函數之後已還原但尚未釋放（例如，當包含已還原函式的應用程式域仍在使用中時）。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
## <a name="parameters"></a>參數  
 `functionId`  
 在`FunctionID`要列舉版本之函式實例的。  
  
 `cReJitIds`  
 在在陣列中配置的 JIT 重新編譯識別碼數目 `reJitIds` 。  
  
 `pcReJitIds`  
 脫銷JIT 重新編譯識別碼的實際數目。  
  
 `reJitIds`  
 脫銷呼叫端配置的陣列，其中將包含所指定函式的 JIT 重新編譯識別碼。  
  
## <a name="remarks"></a>備註  
 `GetReJITIDs`列舉指定函式實例之使用中 JIT 重新編譯的識別碼。 它會遵循與其他接受呼叫者配置緩衝區的函式相同的使用模式 `ICorProfilerInfo` 。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo4 介面](icorprofilerinfo4-interface.md)
- [分析介面](profiling-interfaces.md)
- [程式碼剖析](index.md)
