---
title: ICorDebugValue::GetSize 方法
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugValue interface [.NET Framework debugging]
- ICorDebugValue::GetSize method [.NET Framework debugging]
ms.assetid: 445a9ee3-e050-4f3a-931a-96b0efb00110
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0023b8ad815b9204ed56791698c7242dfe90bec4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugvaluegetsize-method"></a>ICorDebugValue::GetSize 方法
取得大小，以位元組為單位，此 「 ICorDebugValue 」 物件。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pSize`  
 [out]以位元組為單位，此值物件的大小。  
  
## <a name="remarks"></a>備註  
 如果值的類型是參考型別，這個方法會傳回指標的大小，而不是物件的大小。  
  
 `ICorDebugValue::GetSize`方法會傳回`COR_E_OVERFLOW`大於 4 GB，在 64 位元平台上的物件。 使用[icordebugvalue3:: Getsize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)方法的物件，是大於 4 GB。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
    
 [GetSize64 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)
