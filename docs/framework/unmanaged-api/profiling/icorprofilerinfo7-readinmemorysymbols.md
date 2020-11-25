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
ms.openlocfilehash: 6917900b7494550992dfa82f45ed0140f95e68cb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733616"
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
 在記憶體內資料流程中要開始讀取位元組的位移。  
  
 `pSymbolBytes`  
 擴展要將資料複製到其中的緩衝區指標。 緩衝區應該有 `countSymbolBytes` 可用的空間。  
  
 `countSymbolBytes`  
 在要複製的位元組數目。  
  
 `pCountSymbolBytesRead`  
 擴展當方法傳回時，會包含所讀取的實際位元組數目。  
  
## <a name="return-value"></a>傳回值  

 `S_OK`如果讀取了非零的位元組數目，則為。  
  
 `CORPROF_E_MODULE_IS_DYNAMIC`如果模組是使用建立的，則為 <xref:System.Reflection.Emit> 。  
  
## <a name="remarks"></a>備註  

 `ReadInMemorySymbols`方法會嘗試 `countSymbolBytes` 從 `symbolsReadOffset` 記憶體內資料流程內的位移開始讀取資料。 資料會複製到 `pSymbolBytes` ，且預期會有 `countSymbolBytes` 可用的空間。     `pCountSymbolsBytesRead` 包含讀取的實際位元組數目， `countSymbolBytes` 如果到達資料流程末端，則可能小於。  
  
> [!NOTE]
> 目前的執行不支援反映。發出。 如果模組是使用反映來建立，則方法會傳回 `CORPROF_E_MODULE_IS_DYNAMIC` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo7 介面](icorprofilerinfo7-interface.md)
