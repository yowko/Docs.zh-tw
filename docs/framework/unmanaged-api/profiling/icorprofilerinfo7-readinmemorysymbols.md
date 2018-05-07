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
ms.openlocfilehash: 9874c8e567a89fd3977be360666c86406f2cd395
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a>ICorProfilerInfo7::ReadInMemorySymbols
[受到 [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] 和更新版本的支援]  
  
 從記憶體中的符號資料流讀取位元組。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
#### <a name="parameters"></a>參數  
 `moduleId`  
 [in]包含記憶體中資料流之模組的識別碼。  
  
 `symbolsReadOffset`  
 [in]要開始寫入讀取位元組的記憶體中資料流內的位移。  
  
 `pSymbolBytes`  
 [out]將資料複製到其中的緩衝區指標。 緩衝區應該有`countSymbolBytes`的可用空間。  
  
 `countSymbolBytes`  
 [in]要複製的位元組數目。  
  
 `pCountSymbolBytesRead`  
 [out]當方法傳回時，會包含實際讀取的位元組數目。  
  
## <a name="return-value"></a>傳回值  
 `S_OK`如果已讀取的非零位元組數目。  
  
 `CORPROF_E_MODULE_IS_DYNAMIC`如果模組使用建立<xref:System.Reflection.Emit>。  
  
## <a name="remarks"></a>備註  
 `ReadInMemorySymbols`方法會嘗試讀取`countSymbolBytes`資料位移處開始的`symbolsReadOffset`記憶體中資料流中。 將資料複製到`pSymbolBytes`，應該要有`countSymbolBytes`的可用空間。     `pCountSymbolsBytesRead` 包含實際讀取位元組數，可能會小於比`countSymbolBytes`如果已到達資料流結尾。  
  
> [!NOTE]
>  目前的實作不支援這些事件處理常式。 如果使用 Reflection.Emit 建立模組，則方法會傳回`CORPROF_E_MODULE_IS_DYNAMIC`。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorProfilerInfo7 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
