---
title: ICorDebugType2::GetTypeID 方法
ms.date: 03/30/2017
api_name:
- ICorDebugType2.GetTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetTypeID
helpviewer_keywords:
- GetTypeID method, ICorDebugType2 interface [.NET Framework debugging]
- ICorDebugType2.GetTypeID method [.NET Framework debugging]
ms.assetid: 0b933686-226e-4373-92b7-fac579ee7b1a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5bc1407f8444b78154981619742bd0da188c4335
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422067"
---
# <a name="icordebugtype2gettypeid-method"></a>ICorDebugType2::GetTypeID 方法
取得[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)此類型。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
#### <a name="parameters"></a>參數  
 `id`  
 [out]指標[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)此 ICorDebugType 的。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回值為 `S_OK`，如果失敗，則傳回失敗 `HRESULT` 程式碼。 `HRESULT`代碼包括下列：  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|`S_OK`|方法成功。 方法已擷取的有效[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)。|  
|`CORDBG_E_CLASS_NOT_LOADED`|尚未載入的型別。|  
|`CORDBG_E_UNSUPPORTED`|不支援的類型。|  
  
## <a name="remarks"></a>備註  
 這個方法從 ICorDebugType，表示類型可能會或可能有尚未載入執行階段中，為提供的對應[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)，這可充當不透明控制代碼識別執行階段中載入的型別。  
  
 當 ICorDebugType 代表的類型，尚未已載入，則這個方法會傳回`CORDBG_E_CLASS_NOT_LOADED`。  如果不支援的類型，它會傳回`CORDBG_E_UNSUPPORTED`。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebugType2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)
