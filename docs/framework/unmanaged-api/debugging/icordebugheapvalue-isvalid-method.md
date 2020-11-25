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
ms.openlocfilehash: d9150d15ac183b65b87448424f265693ed7b7ab7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726570"
---
# <a name="icordebugheapvalueisvalid-method"></a>ICorDebugHeapValue::IsValid 方法

取得值，這個值表示此 ICorDebugHeapValue 所表示的物件是否有效。  
  
 在 .NET Framework 版本2.0 中，此方法已被取代。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
## <a name="parameters"></a>參數  

 `pbValid`  
 擴展布林值的指標，指出堆積上的此值是否有效。  
  
## <a name="remarks"></a>備註  

 如果它已經由垃圾收集行程回收，則該值無效。  
  
 這個方法已被取代。 在 .NET Framework 2.0 中，在呼叫 [ICorDebugController：： Continue](icordebugcontroller-continue-method.md) 之前，所有值都是有效的，此時值會失效。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
