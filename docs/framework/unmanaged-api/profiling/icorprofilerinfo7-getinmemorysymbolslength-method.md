---
title: 'Icorprofilerinfo7:: Getinmemorysymbolslength 方法'
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
ms.openlocfilehash: 5e662270fc8db3fb85e058e8d4f3346f58f79bb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a>Icorprofilerinfo7:: Getinmemorysymbolslength 方法
[在 .NET Framework 4.6.1 及更新版本中支援]  
  
 傳回的記憶體中的符號資料流的長度。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
#### <a name="parameters"></a>參數  
 `moduleId`  
 [in]包含記憶體中資料流之模組的識別碼。  
  
 pCountSymbolBytes  
 [out]指標`DWORD`值，這個方法傳回時，包含以位元組為單位的資料流的長度值。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回`S_OK`如果記憶體資料流的長度可以判斷，即使它是零 (0)。  
  
 方法會傳回`CORPROF_E_MODULE_IS_DYNAMIC`如果方法使用建立<xref:System.Reflection.Emit?displayProperty=nameWithType>。  
  
## <a name="remarks"></a>備註  
 如果模組有記憶體中的符號，資料流的長度會置於`pCountSymbolBytes`。 如果模組沒有記憶體中的符號， `*pCountSymbolBytes = 0`。  
  
> [!NOTE]
>  目前的實作不支援這些事件處理常式。 如果使用 Reflection.Emit 建立模組，則方法會傳回`CORPROF_E_MODULE_IS_DYNAMIC`。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorProfilerInfo7 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
