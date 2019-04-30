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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d2d48e5fb070ec0334de579d2e28146177a87b1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049475"
---
# <a name="icorprofilerinfo4getrejitids-method"></a>ICorProfilerInfo4::GetReJITIDs 方法
傳回識別 JIT 重新編譯的所有版本指定的函式仍配置的識別碼陣列。 這包括已後續還原，但尚未釋放 （比方說，當應用程式定義域，其中包含已還原的函式是仍在使用中） 的函式的 JIT 重新編譯版本。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
## <a name="parameters"></a>參數  
 `functionId`  
 [in]`FunctionID`函式執行個體，要列舉的版本。  
  
 `cReJitIds`  
 [in]在中所配置的 JIT 重新編譯識別碼數目`reJitIds`陣列。  
  
 `pcReJitIds`  
 [out]JIT 重新編譯識別碼實際數目。  
  
 `reJitIds`  
 [out]呼叫端配置的陣列會包含指定的函式的 JIT 重新編譯識別碼。  
  
## <a name="remarks"></a>備註  
 `GetReJITIDs` 列舉指定的函式執行個體的作用中 JIT 重新編譯識別碼。 它會遵循相同的使用方式模式與其他`ICorProfilerInfo`接受呼叫端配置緩衝區的函式。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo4 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [程式碼剖析](../../../../docs/framework/unmanaged-api/profiling/index.md)
