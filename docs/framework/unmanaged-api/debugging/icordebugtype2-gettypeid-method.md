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
ms.openlocfilehash: 2a4a0bfae6f9a1970f0d4aca8b37f8fc68194462
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725686"
---
# <a name="icordebugtype2gettypeid-method"></a>ICorDebugType2：： GetTypeID 方法

取得此類型的 [COR_TYPEID](cor-typeid-structure.md) 。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
## <a name="parameters"></a>參數  

 `id`  
 擴展這個 ICorDebugType 之 [COR_TYPEID](cor-typeid-structure.md) 的指標。  
  
## <a name="return-value"></a>傳回值  

 如果成功，傳回值為 `S_OK`，如果失敗，則傳回失敗 `HRESULT` 程式碼。 這些 `HRESULT` 代碼包含下列各項：  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|`S_OK`|方法成功。 方法已取出有效的 [COR_TYPEID](cor-typeid-structure.md)。|  
|`CORDBG_E_CLASS_NOT_LOADED`|尚未載入類型。|  
|`CORDBG_E_UNSUPPORTED`|不支援這種類型。|  
  
## <a name="remarks"></a>備註  

 這個方法會提供 ICorDebugType 的對應，其代表可能或可能尚未載入執行時間的型別，以做為識別載入執行時間之型別的不透明控制碼的 [COR_TYPEID](cor-typeid-structure.md)。  
  
 當 ICorDebugType 表示的類型尚未載入時，這個方法會傳回 `CORDBG_E_CLASS_NOT_LOADED` 。  如果類型不受支援，則會傳回 `CORDBG_E_UNSUPPORTED` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugType2 介面](icordebugtype2-interface.md)
