---
title: ICorDebugProcess5::GetTypeLayout 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeLayout
helpviewer_keywords:
- ICorDebugProcess5::GetTypeLayout method [.NET Framework debugging]
- GetTypeLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: bd62f5d1-e874-41f1-81e5-a29a7572c15d
topic_type:
- apiref
ms.openlocfilehash: 861af4ba9c6f4d4bdb16abb9d4e1fd79debac59b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205568"
---
# <a name="icordebugprocess5gettypelayout-method"></a>ICorDebugProcess5::GetTypeLayout 方法
根據物件的類型識別碼，取得記憶體中之配置的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetTypeLayout(    [in] COR_TYPEID id,     [out] COR_TYPE_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a>參數  
 `id`  
 在[COR_TYPEID](cor-typeid-structure.md) token，指定需要其配置的類型。  
  
 `pLayout`  
 脫銷[COR_TYPE_LAYOUT](cor-type-layout-structure.md)結構的指標，其中包含記憶體中物件配置的相關資訊。  
  
## <a name="remarks"></a>備註  
 `ICorDebugProcess5::GetTypeLayout`方法會根據它的[COR_TYPEID](cor-typeid-structure.md)提供物件的相關資訊，而其他[ICorDebugProcess5](icordebugprocess5-interface.md)方法會傳回此值。 這項資訊是由方法所填入的[COR_TYPE_LAYOUT](cor-type-layout-structure.md)結構所提供。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [COR_TYPE_LAYOUT 結構](cor-type-layout-structure.md)
- [ICorDebugProcess5 介面](icordebugprocess5-interface.md)
- [偵錯介面](debugging-interfaces.md)
