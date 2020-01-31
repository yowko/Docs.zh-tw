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
ms.openlocfilehash: 9069498a4f62f4d9dbb50a7075323b14c3cc5ab9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868443"
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
 在要列舉版本之函式實例的 `FunctionID`。  
  
 `cReJitIds`  
 在在 `reJitIds` 陣列中配置的 JIT 重新編譯識別碼數目。  
  
 `pcReJitIds`  
 脫銷JIT 重新編譯識別碼的實際數目。  
  
 `reJitIds`  
 脫銷呼叫端配置的陣列，其中將包含所指定函式的 JIT 重新編譯識別碼。  
  
## <a name="remarks"></a>備註  
 `GetReJITIDs` 列舉指定函式實例的使用中 JIT 重新編譯識別碼。 它會遵循與其他接受呼叫者配置緩衝區的 `ICorProfilerInfo` 函式相同的使用模式。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerInfo4 介面](icorprofilerinfo4-interface.md)
- [分析介面](profiling-interfaces.md)
- [程式碼剖析](index.md)
