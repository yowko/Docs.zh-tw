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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0915027ce6a3768ff854eafc5496c5057081cc4d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946207"
---
# <a name="icordebugtypegetclass-method"></a>ICorDebugType::GetClass 方法
取得表示未具現化的泛型型別 ICorDebugClass 介面指標。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppClass`  
 [out]位址指標`ICorDebugClass`介面，表示未具現化的泛型型別。  
  
## <a name="remarks"></a>備註  
 `GetClass` 您可以只在某些情況下呼叫。 呼叫[icordebugtype:: Gettype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)再呼叫`GetClass`。 如果`ICorDebugType::GetType`傳回 CorElementType 值，這個值是 ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE，`GetClass`可以呼叫以取得泛型型別未具現化的型別。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
