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
ms.openlocfilehash: 2ac645cbaaa45554568874653be016e4691bbd2f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707473"
---
# <a name="icorprofilerinfo4getrejitids-method"></a>ICorProfilerInfo4::GetReJITIDs 方法

傳回識別碼陣列，識別仍配置之指定函式的所有 JIT 重新編譯版本。 這包括 JIT 重新編譯的函式版本，這些函式已在後續還原，但尚未釋出 (例如，當包含已還原函式的應用程式域仍在使用中時) 。  
  
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
 在 `FunctionID` 要列舉版本之函式實例的。  
  
 `cReJitIds`  
 在在陣列中配置的 JIT 重新編譯識別碼數目 `reJitIds` 。  
  
 `pcReJitIds`  
 擴展JIT 重新編譯之識別碼的實際數目。  
  
 `reJitIds`  
 擴展呼叫端配置的陣列，其中將包含指定之函式的 JIT 重新編譯識別碼。  
  
## <a name="remarks"></a>備註  

 `GetReJITIDs` 列舉指定之函式實例的作用中 JIT 重新編譯識別碼。 它會遵循與接受呼叫端配置之緩衝區的其他函式相同的使用模式 `ICorProfilerInfo` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo4 介面](icorprofilerinfo4-interface.md)
- [分析介面](profiling-interfaces.md)
- [程式碼剖析](index.md)
