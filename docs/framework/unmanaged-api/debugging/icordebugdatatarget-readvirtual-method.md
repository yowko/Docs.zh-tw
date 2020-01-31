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
ms.openlocfilehash: 20cea94961a250c3981d892910da1dcee20a060b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783732"
---
# <a name="icordebugdatatargetreadvirtual-method"></a>ICorDebugDataTarget::ReadVirtual 方法
從指定的位址開始，取得連續記憶體的區塊，並將它傳回給提供的緩衝區。  
  
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
 在要求之記憶體的起始位址。  
  
 `pbuffer`  
 脫銷將儲存記憶體的緩衝區。  
  
 `bytesRequested`  
 在要從目標位址取得的位元組數目。  
  
 `pBytesRead`  
 脫銷實際從目標位址讀取的位元組數目。 這可能少於 `bytesRequested`。  
  
## <a name="remarks"></a>備註  
 如果可以讀取第一個位元組（在指定的起始位址），則呼叫應該會傳回 success （以支援有效率地讀取具有自我描述長度的資料結構，例如以 null 終止的字串）。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugDataTarget 介面](icordebugdatatarget-interface.md)
- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
