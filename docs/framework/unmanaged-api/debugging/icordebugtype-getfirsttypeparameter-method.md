---
title: ICorDebugType::GetFirstTypeParameter 方法
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetFirstTypeParameter
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetFirstTypeParameter
helpviewer_keywords:
- ICorDebugType::GetFirstTypeParameter method [.NET Framework debugging]
- GetFirstTypeParameter method [.NET Framework debugging]
ms.assetid: 35bb594f-af6a-4349-83fe-e98702674e03
topic_type:
- apiref
ms.openlocfilehash: 4dbc042143e68dc962eb21b2bf741cbaefc1977e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122349"
---
# <a name="icordebugtypegetfirsttypeparameter-method"></a>ICorDebugType::GetFirstTypeParameter 方法
取得 ICorDebugType 的介面指標，表示此 `ICorDebugType`所表示之類型的第一個 <xref:System.Type> 參數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetFirstTypeParameter (  
    [out] ICorDebugType   **value  
);  
```  
  
## <a name="parameters"></a>參數  
 `value`  
 脫銷表示第一個參數之 `ICorDebugType` 物件的位址指標。  
  
## <a name="remarks"></a>備註  
 當類型的其他資訊包含最多一個型別參數時，可以呼叫 `GetFirstTypeParameter`。 特別是，如果類型是 ELEMENT_TYPE_ARRAY、ELEMENT_TYPE_SZARRAY、ELEMENT_TYPE_BYREF 或 ELEMENT_TYPE_PTR （如[ICorDebugType：： GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)方法所指示），則可以使用它。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
