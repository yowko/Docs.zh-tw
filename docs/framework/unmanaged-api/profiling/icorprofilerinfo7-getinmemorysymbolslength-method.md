---
title: 'ICorProfilerInfo7:: GetInMemorySymbolsLength 方法'
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type:
- COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 157b0e215f8afa58cccb3d54a65baa9c307ba966
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955417"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a>ICorProfilerInfo7:: GetInMemorySymbolsLength 方法
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
 脫銷`DWORD`值的指標, 當方法傳回時, 會包含資料流程的長度 (以位元組為單位)。  
  
## <a name="return-value"></a>傳回值  
 `S_OK`如果可以判斷記憶體資料流程的長度, 則此方法會傳回, 即使它是零 (0) 也一樣。  
  
 `CORPROF_E_MODULE_IS_DYNAMIC`如果方法是使用<xref:System.Reflection.Emit?displayProperty=nameWithType>建立的, 則方法會傳回。  
  
## <a name="remarks"></a>備註  
 如果模組具有記憶體中的符號, 資料流程的長度會放在中`pCountSymbolBytes`。 如果模組沒有記憶體中的符號, `*pCountSymbolBytes = 0`則為。  
  
> [!NOTE]
> 目前的執行不支援反映。發出。 如果模組是使用反映所建立, 則方法`CORPROF_E_MODULE_IS_DYNAMIC`會傳回。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Corprof.idl .idl, Corprof.idl。h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo7 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
