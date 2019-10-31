---
title: ICorDebugNativeFrame::GetLocalMemoryRegisterValue 方法
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalMemoryRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalMemoryRegisterValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalMemoryRegisterValue method [.NET Framework debugging]
- GetLocalMemoryRegisterValue method
ms.assetid: 33a19f6e-1029-4d53-af64-19591c6e58ee
topic_type:
- apiref
ms.openlocfilehash: 788ce2d47769caa72518e0357a0affdff5862699
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137276"
---
# <a name="icordebugnativeframegetlocalmemoryregistervalue-method"></a>ICorDebugNativeFrame::GetLocalMemoryRegisterValue 方法
取得引數或區域變數的值，其中的 low 單字和 high 單字會分別儲存在這個原生框架的指定暫存器和記憶體位置中。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetLocalMemoryRegisterValue (  
    [in] CORDB_ADDRESS      highWordAddress,  
    [in] CorDebugRegister   lowWordRegister,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a>參數  
 `highWordAddress`  
 在`CORDB_ADDRESS` 值，指定包含值高位字的記憶體位置。  
  
 `lowWordRegister`  
 在"CorDebugRegister" 列舉的值，指定包含值之低字的暫存器。  
  
 `cbSigBlob`  
 在整數，指定 `pvSigBlob` 參數所參考的二進位中繼資料簽章大小。  
  
 `pvSigBlob`  
 在`PCCOR_SIGNATURE` 值，指向數值型別的二進位中繼資料簽章。  
  
 `ppValue`  
 脫銷"ICorDebugValue" 物件位址的指標，代表儲存在指定的暫存器和記憶體位置的已抓取值。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱
