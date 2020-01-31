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
ms.openlocfilehash: d403a8bfba3599a60d8af72307590f5a569480dd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791301"
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
 `GetClass` 只能在特定條件下呼叫。 呼叫[ICorDebugType：： GetType](icordebugtype-gettype-method.md) ，再呼叫 `GetClass`。 如果 `ICorDebugType::GetType` 傳回 ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE 的 CorElementType 值，則可以呼叫 `GetClass` 來取得泛型型別的未具現化型別。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
