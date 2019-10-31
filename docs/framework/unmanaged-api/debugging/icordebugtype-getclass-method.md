---
title: ICorDebugType::GetClass 方法
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetClass
helpviewer_keywords:
- ICorDebugType::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: 2644f48b-db3c-429f-ae62-76f1c98a1af5
topic_type:
- apiref
ms.openlocfilehash: 3a895f432ed640cc35a492df0c91cece34893062
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122371"
---
# <a name="icordebugtypegetclass-method"></a>ICorDebugType::GetClass 方法
取得 ICorDebugClass 的介面指標，表示未具現化的泛型型別。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppClass`  
 脫銷表示未具現化泛型型別之 `ICorDebugClass` 介面的位址指標。  
  
## <a name="remarks"></a>備註  
 `GetClass` 只能在特定條件下呼叫。 呼叫[ICorDebugType：： GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) ，再呼叫 `GetClass`。 如果 `ICorDebugType::GetType` 傳回 ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE 的 CorElementType 值，則可以呼叫 `GetClass` 以取得泛型型別的未具現化類型。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
