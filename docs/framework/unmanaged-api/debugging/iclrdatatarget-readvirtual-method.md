---
title: ICLRDataTarget::ReadVirtual 方法
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.ReadVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::ReadVirtual
helpviewer_keywords:
- ReadVirtual method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::ReadVirtual method [.NET Framework debugging]
ms.assetid: da3769eb-1828-4aa1-b9ed-db4842136a43
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7911d09c97c5401bff827ca5fb0a8766933778f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738665"
---
# <a name="iclrdatatargetreadvirtual-method"></a>ICLRDataTarget::ReadVirtual 方法
讀取指定的虛擬記憶體位址的資料儲存至指定的緩衝區。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ReadVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [out, size_is(bytesRequested), length_is(*bytesRead)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesRead  
);  
```  
  
## <a name="parameters"></a>參數  
 `address`  
 [in]CLRDATA_ADDRESS 儲存的虛擬記憶體位址。  
  
 `buffer`  
 [out]接收資料的緩衝區指標。  
  
 `bytesRequested`  
 [in]緩衝區的長度。  
  
 `bytesRead`  
 [out]傳回的位元組數目指標。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** ClrData.idl, ClrData.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRDataTarget 介面](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
