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
ms.openlocfilehash: 6e1edb1d25a62a9a689c397339740e563d986c8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61700214"
---
# <a name="icordebugheapvalueisvalid-method"></a>ICorDebugHeapValue::IsValid 方法
取得值，指出此 ICorDebugHeapValue 所代表的物件是否有效。  
  
 這個方法已被取代，在.NET Framework 2.0 版。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
## <a name="parameters"></a>參數  
 `pbValid`  
 [out]布林值，指出是否在堆積上的這個值是有效的指標。  
  
## <a name="remarks"></a>備註  
 值不正確，如果它已經由記憶體回收行程回收。  
  
 這個方法已被取代。 在.NET Framework 2.0 中，所有值都是有效期限[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)呼叫時，在這段值都會失效。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
