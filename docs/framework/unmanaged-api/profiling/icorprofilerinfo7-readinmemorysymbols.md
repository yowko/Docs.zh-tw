---
title: ICorProfilerInfo7::ReadInMemorySymbols
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.ReadInMemorySymbols
api_location:
- CorProf.idl
- CorProf.h
- CorGuids.lib
api_type:
- COM
ms.assetid: 1745a0b9-8332-4777-a670-b549bff3b901
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95b463b23c230d620d746e48da49d75238ef2cb7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955365"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a>ICorProfilerInfo7::ReadInMemorySymbols
[在 .NET Framework 4.6.1 及更新版本中支援]  
  
 從記憶體中的符號資料流程讀取位元組。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a>參數  
 `moduleId`  
 在包含記憶體中資料流程之模組的識別碼。  
  
 `symbolsReadOffset`  
 在記憶體內部資料流程內要開始讀取位元組的位移。  
  
 `pSymbolBytes`  
 脫銷要將資料複製到其中之緩衝區的指標。 緩衝區應該有`countSymbolBytes`可用的空間。  
  
 `countSymbolBytes`  
 在要複製的位元組數目。  
  
 `pCountSymbolBytesRead`  
 脫銷當此方法傳回時, 會包含實際讀取的位元組數目。  
  
## <a name="return-value"></a>傳回值  
 `S_OK`如果讀取非零的位元組數目, 則為。  
  
 `CORPROF_E_MODULE_IS_DYNAMIC`, 如果模組是使用<xref:System.Reflection.Emit>建立的, 則為。  
  
## <a name="remarks"></a>備註  
 方法會嘗試從記憶體`countSymbolBytes`中資料流程內的位移`symbolsReadOffset`開始讀取資料。 `ReadInMemorySymbols` 資料會複製到`pSymbolBytes`, 這應該會有`countSymbolBytes`可用的空間。     `pCountSymbolsBytesRead`包含讀取的實際位元組數目, `countSymbolBytes`如果到達資料流程末端, 則可能小於。  
  
> [!NOTE]
> 目前的執行不支援反映。發出。 如果模組是使用反映所建立, 則方法`CORPROF_E_MODULE_IS_DYNAMIC`會傳回。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Corprof.idl .idl, Corprof.idl。h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo7 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
