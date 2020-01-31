---
title: ICorProfilerInfo7：： ReadInMemorySymbols
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
ms.openlocfilehash: 53c01d2db44f4d0adf1ba5b9cc225ab49581aa5d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868339"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a>ICorProfilerInfo7：： ReadInMemorySymbols
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
 脫銷要將資料複製到其中之緩衝區的指標。 緩衝區應具有可用的空間 `countSymbolBytes`。  
  
 `countSymbolBytes`  
 在要複製的位元組數目。  
  
 `pCountSymbolBytesRead`  
 脫銷當此方法傳回時，會包含實際讀取的位元組數目。  
  
## <a name="return-value"></a>傳回值  
 `S_OK`，如果讀取的是非零的位元組數目，則為。  
  
 `CORPROF_E_MODULE_IS_DYNAMIC`，如果模組是使用 <xref:System.Reflection.Emit>所建立的。  
  
## <a name="remarks"></a>備註  
 `ReadInMemorySymbols` 方法會嘗試讀取記憶體中資料流程內從 offset `symbolsReadOffset` 開始的 `countSymbolBytes` 資料。 資料會複製到 `pSymbolBytes`，這應該會有 `countSymbolBytes` 的可用空間。     `pCountSymbolsBytesRead` 包含讀取的實際位元組數目，如果到達資料流程末端，則可能小於 `countSymbolBytes`。  
  
> [!NOTE]
> 目前的執行不支援反映。發出。 如果模組是使用反映所建立，則方法會傳回 `CORPROF_E_MODULE_IS_DYNAMIC`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerInfo7 介面](icorprofilerinfo7-interface.md)
