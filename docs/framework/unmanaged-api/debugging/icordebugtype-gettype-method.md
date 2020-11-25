---
title: ICorDebugType::GetType 方法
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetType
helpviewer_keywords:
- ICorDebugType::GetType method [.NET Framework debugging]
- GetType method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: d6e64534-4d47-4ad0-a340-7590e07e2b4a
topic_type:
- apiref
ms.openlocfilehash: f0f45d5f0b2ea8cefa6bd36e909ae43d80c968ed
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700882"
---
# <a name="icordebugtypegettype-method"></a>ICorDebugType::GetType 方法

取得 CorElementType 值，這個值描述 <xref:System.Type> 此 ICorDebugType 所表示之 common language runtime (CLR) 的原生類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
## <a name="parameters"></a>參數  

 `ty`  
 擴展列舉值的指標 `CorElementType` ，表示這個所代表的 CLR <xref:System.Type> `ICorDebugType` 。  
  
## <a name="remarks"></a>備註  

 如果的值 `ty` 為 ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE，可能會呼叫 [ICorDebugType：： GetClass](icordebugtype-getclass-method.md) 方法，以取得泛型型別的未具現化型別; 否則，請勿呼叫 `ICorDebugType::GetClass` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
