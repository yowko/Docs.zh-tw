---
title: ICorProfilerInfo7：： GetInMemorySymbolsLength 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type:
- COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
ms.openlocfilehash: 299a7495d9ca9215ad21301a3ac525fa6e49a01b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130335"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a>ICorProfilerInfo7：： GetInMemorySymbolsLength 方法
[在 .NET Framework 4.6.1 及更新版本中支援]  
  
 傳回記憶體中符號資料流程的長度。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
## <a name="parameters"></a>參數  
 `moduleId`  
 在包含記憶體中資料流程之模組的識別碼。  
  
 pCountSymbolBytes  
 脫銷`DWORD` 值的指標，當方法傳回時，會包含資料流程的長度（以位元組為單位）。  
  
## <a name="return-value"></a>傳回值  
 如果可以判斷記憶體資料流程的長度，則此方法會傳回 `S_OK`，即使它是零（0）也一樣。  
  
 如果使用 <xref:System.Reflection.Emit?displayProperty=nameWithType>建立方法，此方法會傳回 `CORPROF_E_MODULE_IS_DYNAMIC`。  
  
## <a name="remarks"></a>備註  
 如果模組具有記憶體中的符號，資料流程的長度會放在 `pCountSymbolBytes`中。 如果模組沒有記憶體中的符號，請 `*pCountSymbolBytes = 0`。  
  
> [!NOTE]
> 目前的執行不支援反映。發出。 如果模組是使用反映所建立，則方法會傳回 `CORPROF_E_MODULE_IS_DYNAMIC`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerInfo7 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
