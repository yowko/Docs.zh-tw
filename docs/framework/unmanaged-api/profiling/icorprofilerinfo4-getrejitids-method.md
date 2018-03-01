---
title: "ICorProfilerInfo4::GetReJITIDs 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fb1e507bea6f52e4959f241f1507807a76c0ec5a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo4getrejitids-method"></a>ICorProfilerInfo4::GetReJITIDs 方法
傳回識別 JIT 重新編譯的所有版本的指定函式仍配置的識別碼的陣列。 這包括 JIT 重新編譯版本的函式已後續還原，但尚未釋出 （例如，應用程式定義域，其中包含已還原的函式仍在使用中時）。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
#### <a name="parameters"></a>參數  
 `functionId`  
 [in]`FunctionID`函式執行個體，這是要列舉的版本。  
  
 `cReJitIds`  
 [in]在配置的 JIT 重新編譯識別碼數目`reJitIds`陣列。  
  
 `pcReJitIds`  
 [out]JIT 重新編譯識別碼的實際數目。  
  
 `reJitIds`  
 [out]呼叫端配置的陣列會包含指定的函式的 JIT 重新編譯識別碼。  
  
## <a name="remarks"></a>備註  
 `GetReJITIDs`列舉 active JIT 重新編譯指定的函式執行個體的識別碼。 它會依照相同的使用狀況模式，與其他`ICorProfilerInfo`函式接受呼叫端配置的緩衝區。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [ICorProfilerInfo4 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [程式碼剖析](../../../../docs/framework/unmanaged-api/profiling/index.md)
