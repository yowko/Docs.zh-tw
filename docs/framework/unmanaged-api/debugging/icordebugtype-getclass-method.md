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
ms.openlocfilehash: ff2258faa8bc766c8c769f4e135f868334516b96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugtypegetclass-method"></a>ICorDebugType::GetClass 方法
取得表示未具現化的泛型型別 ICorDebugClass 介面指標。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppClass`  
 [out]位址指標`ICorDebugClass`表示未具現化的泛型類型的介面。  
  
## <a name="remarks"></a>備註  
 `GetClass` 只有在某些情況下，可以被呼叫。 呼叫[icordebugtype:: Gettype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)之前先呼叫`GetClass`。 如果`ICorDebugType::GetType`傳回 ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE，CorElementType 值`GetClass`可以呼叫以取得泛型類型的未具現化的型別。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
