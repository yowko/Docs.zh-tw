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
ms.openlocfilehash: e774905939640d2748344ad3f6e12a96f9868d9f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213799"
---
# <a name="icordebugheapvalueisvalid-method"></a>ICorDebugHeapValue::IsValid 方法
取得值，指出此 ICorDebugHeapValue 所表示的物件是否有效。  
  
 這個方法已在 .NET Framework 版本2.0 中被取代。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
## <a name="parameters"></a>參數  
 `pbValid`  
 脫銷布林值的指標，指出堆積上的這個值是否有效。  
  
## <a name="remarks"></a>備註  
 如果垃圾收集行程已回收值，則該值無效。  
  
 這個方法已被取代。 在 .NET Framework 2.0 中，所有值都是有效的，直到呼叫[ICorDebugController：： Continue](icordebugcontroller-continue-method.md)為止，此時值會無效。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
