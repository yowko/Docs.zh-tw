---
title: ICorDebugHeapValue::IsValid 方法
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue.IsValid
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue::IsValid
helpviewer_keywords:
- IsValid method [.NET Framework debugging]
- ICorDebugHeapValue::IsValid method [.NET Framework debugging]
ms.assetid: 68e20e62-203d-46d8-bb91-8d3c61cfacc3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95532d6721467b482b1d79d611f8055b606bb4a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugheapvalueisvalid-method"></a>ICorDebugHeapValue::IsValid 方法
取得值，指出此 ICorDebugHeapValue 所表示的物件是否有效。  
  
 .NET Framework 2.0 版中，這個方法已被取代。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbValid`  
 [out]布林值，指出是否在堆積上的這個值是有效的指標。  
  
## <a name="remarks"></a>備註  
 值不正確，如果它已經由記憶體回收行程回收。  
  
 這個方法已被取代。 在.NET Framework 2.0 中，所有值都都有效，直到[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)呼叫時，在這段值都會失效。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
