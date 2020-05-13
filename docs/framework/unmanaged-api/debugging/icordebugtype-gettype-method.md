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
ms.openlocfilehash: ac42c6254182ea775377a448a54d527b234c97dc
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379918"
---
# <a name="icordebugtypegettype-method"></a>ICorDebugType::GetType 方法
取得 CorElementType 值，描述這個 ICorDebugType 所表示之 common language runtime （CLR）的原生類型 <xref:System.Type> 。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
## <a name="parameters"></a>參數  
 `ty`  
 脫銷列舉值的指標 `CorElementType` ，指出這個所代表的 CLR <xref:System.Type> `ICorDebugType` 。  
  
## <a name="remarks"></a>備註  
 如果的值 `ty` 是 ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE，則可以呼叫[ICorDebugType：： GetClass](icordebugtype-getclass-method.md)方法來取得泛型型別的未具現化類型，否則不會呼叫 `ICorDebugType::GetClass` 。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
