---
title: ICorDebugGenericValue 介面
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue
helpviewer_keywords:
- ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: bc14f408-b359-4c8c-ade2-888ccdf7261b
topic_type:
- apiref
ms.openlocfilehash: cfa0950ca2ef4e969258c147b762fa95e52a82e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705809"
---
# <a name="icordebuggenericvalue-interface"></a>ICorDebugGenericValue 介面

適用于所有值的 "ICorDebugValue" 子類別。 這個介面提供值的 Get 和 Set 方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetValue 方法](icordebuggenericvalue-getvalue-method.md)|將值複製到指定的緩衝區。|  
|[SetValue 方法](icordebuggenericvalue-setvalue-method.md)|從指定的緩衝區複製新值。|  
  
## <a name="remarks"></a>備註  

 `ICorDebugGenericValue` 是子介面，因為它無法遠端處理。  
  
 若為參考型別，則此值為參考，而不是參考的內容。  
  
 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
