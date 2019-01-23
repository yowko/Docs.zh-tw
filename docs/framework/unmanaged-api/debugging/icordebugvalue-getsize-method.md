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
ms.openlocfilehash: fb0030a25dd48ab4236ec2b51891e0ac41aac902
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612615"
---
# <a name="icordebugvaluegetsize-method"></a>ICorDebugValue::GetSize 方法
取得大小，以位元組為單位，這個 「 ICorDebugValue 」 物件。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pSize`  
 [out]大小 （位元組），這個值物件。  
  
## <a name="remarks"></a>備註  
 如果此值的型別是參考型別，這個方法會傳回指標的大小，而不是物件的大小。  
  
 `ICorDebugValue::GetSize`方法會傳回`COR_E_OVERFLOW`大於 64 位元平台上為 4 GB 的物件。 使用[ICorDebugValue3::GetSize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)方法改為物件，會超過 4 GB。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [GetSize64 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)
