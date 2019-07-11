---
title: ICorDebugDataTarget::ReadVirtual 方法
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.ReadVirtual Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::ReadVirtual
helpviewer_keywords:
- ICorDebugDataTarget::ReadVirtual method [.NET Framework debugging]
- ReadVirtual method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: 55e57640-b3d2-413d-b4f4-fbc27fb8e37c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c9d42c85502c12d4d77694626a533c69af97da67
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750257"
---
# <a name="icordebugdatatargetreadvirtual-method"></a>ICorDebugDataTarget::ReadVirtual 方法
取得從指定的位址、 開始的連續記憶體區塊，並傳回它在提供的緩衝區。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ReadVirtual(  
    [in] CORDB_ADDRESS   address,  
    [out, size_is(bytesRequested), length_is(*pBytesRead)]  
          BYTE *     pBuffer,  
    [in]  ULONG32    bytesRequested,  
    [out] ULONG32 *  pBytesRead);  
```  
  
## <a name="parameters"></a>參數  
 `address`  
 [in]起始要求的記憶體位址。  
  
 `pbuffer`  
 [out]將儲存記憶體緩衝區。  
  
 `bytesRequested`  
 [in]若要從目標位址取得的位元組數目。  
  
 `pBytesRead`  
 [out]從目標位址實際讀取的位元組數目。 這可以是少於`bytesRequested`。  
  
## <a name="remarks"></a>備註  
 如果可以讀取的第一個位元組 （在指定的開始位址），呼叫應該會傳回成功 （以支援有效讀取具有自我描述的長度，例如 null 結尾字串的資料結構）。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugDataTarget 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
