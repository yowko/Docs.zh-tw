---
title: ICorDebugType2：： GetTypeID 方法
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
ms.openlocfilehash: 631f605fd18559b36071964e35a15761cd4c8228
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791234"
---
# <a name="icordebugtype2gettypeid-method"></a>ICorDebugType2：： GetTypeID 方法
取得這個類型的[COR_TYPEID](cor-typeid-structure.md) 。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
## <a name="parameters"></a>參數  
 `id`  
 脫銷這個 ICorDebugType 之[COR_TYPEID](cor-typeid-structure.md)的指標。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回值為 `S_OK`，如果失敗，則傳回失敗 `HRESULT` 程式碼。 `HRESULT` 碼包括下列各項：  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|`S_OK`|方法成功。 方法已取出有效的[COR_TYPEID](cor-typeid-structure.md)。|  
|`CORDBG_E_CLASS_NOT_LOADED`|尚未載入類型。|  
|`CORDBG_E_UNSUPPORTED`|不支援這種類型。|  
  
## <a name="remarks"></a>備註  
 這個方法會提供 ICorDebugType 的對應，其代表可能或可能尚未載入執行時間中的類型到[COR_TYPEID](cor-typeid-structure.md)，這是用來識別載入執行時間之類型的不透明控制碼。  
  
 當 ICorDebugType 所代表的類型尚未載入時，這個方法會傳回 `CORDBG_E_CLASS_NOT_LOADED`。  如果不支援此類型，它會傳回 `CORDBG_E_UNSUPPORTED`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugType2 介面](icordebugtype2-interface.md)
