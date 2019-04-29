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
ms.openlocfilehash: 662863ec69e464dafe893552f1d81755313acc75
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786213"
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
  
## <a name="parameters"></a>參數  
 `moduleId`  
 [in]包含記憶體中資料流之模組的識別碼。  
  
 `symbolsReadOffset`  
 [in]要開始讀取位元組的記憶體資料流內的位移。  
  
 `pSymbolBytes`  
 [out]要將資料複製到其中的緩衝區指標。 緩衝區應該有`countSymbolBytes`的可用空間。  
  
 `countSymbolBytes`  
 [in]要複製的位元組數目。  
  
 `pCountSymbolBytesRead`  
 [out]當方法傳回時，會包含實際讀取的位元組數目。  
  
## <a name="return-value"></a>傳回值  
 `S_OK`如果已讀取的非零位元組數目。  
  
 `CORPROF_E_MODULE_IS_DYNAMIC`如果模組使用建立<xref:System.Reflection.Emit>。  
  
## <a name="remarks"></a>備註  
 `ReadInMemorySymbols`方法會嘗試讀取`countSymbolBytes`的資料位移處開始`symbolsReadOffset`記憶體資料流中。 將資料複製到`pSymbolBytes`，其中應該有`countSymbolBytes`的可用空間。     `pCountSymbolsBytesRead` 包含實際讀取，可能會較少的位元組數目比`countSymbolBytes`如果已到達資料流結尾。  
  
> [!NOTE]
>  目前的實作不支援這些事件處理常式。 如果使用 Reflection.Emit 建立模組，則方法會傳回`CORPROF_E_MODULE_IS_DYNAMIC`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo7 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
