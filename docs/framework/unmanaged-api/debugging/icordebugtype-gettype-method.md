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
ms.openlocfilehash: 25ffbf73fbefbb3c584450283c3080dfc11ee598
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791246"
---
# <a name="icordebugtypegettype-method"></a>ICorDebugType::GetType 方法
取得 CorElementType 值，描述此 ICorDebugType 所表示之 common language runtime （CLR） <xref:System.Type> 的原生類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
## <a name="parameters"></a>參數  
 `ty`  
 脫銷`CorElementType` 列舉值的指標，表示此 `ICorDebugType` 所代表的 CLR <xref:System.Type>。  
  
## <a name="remarks"></a>備註  
 如果 `ty` 的值是 ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE，可以呼叫[ICorDebugType：： GetClass](icordebugtype-getclass-method.md)方法來取得泛型型別的未具現化型別。否則，請勿呼叫 `ICorDebugType::GetClass`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
