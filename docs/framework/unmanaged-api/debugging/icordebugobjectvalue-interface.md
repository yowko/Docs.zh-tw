---
title: ICorDebugObjectValue 介面
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue
helpviewer_keywords:
- ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 937de6a0-6fbf-4ddc-80ea-a6217b73e62b
topic_type:
- apiref
ms.openlocfilehash: 2a5a618491bf2c624669728d97a690cca315bff8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724672"
---
# <a name="icordebugobjectvalue-interface"></a>ICorDebugObjectValue 介面

"ICorDebugValue" 的子類別，表示包含物件的值。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetClass 方法](icordebugobjectvalue-getclass-method.md)|取得 <xref:System.Type> 這個所參考之物件的 common language runtime (CLR) 的介面指標 `ICorDebugObjectValue` 。|  
|[GetContext 方法](icordebugobjectvalue-getcontext-method.md)|未實作。|  
|[GetFieldValue 方法](icordebugobjectvalue-getfieldvalue-method.md)|取得 [ICorDebugValue](icordebugvalue-interface.md) 的介面指標，表示指定之類別的指定域值。|  
|[GetManagedCopy 方法](icordebugobjectvalue-getmanagedcopy-method.md)|已過時。 請不要呼叫此方法。|  
|[GetVirtualMethod 方法](icordebugobjectvalue-getvirtualmethod-method.md)|未實作。|  
|[IsValueClass 方法](icordebugobjectvalue-isvalueclass-method.md)|取得值，這個值會指出這個所參考的物件是否 `ICorDebugObjectValue` 為實值型別。|  
|[SetFromManagedCopy 方法](icordebugobjectvalue-setfrommanagedcopy-method.md)|已過時。 請不要呼叫此方法。|  
  
## <a name="remarks"></a>備註  

 `ICorDebugObjectValue`會維持有效，直到正在進行的進程繼續進行。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
