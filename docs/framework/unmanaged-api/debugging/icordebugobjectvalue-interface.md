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
ms.openlocfilehash: e104f8c522af2ee4cd42332b7459f4a2fd185511
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792693"
---
# <a name="icordebugobjectvalue-interface"></a>ICorDebugObjectValue 介面

"ICorDebugValue" 的子類別，表示包含物件的值。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetClass 方法](icordebugobjectvalue-getclass-method.md)|取得此 `ICorDebugObjectValue` 參考之物件的 common language runtime （CLR） <xref:System.Type> 介面指標。|  
|[GetContext 方法](icordebugobjectvalue-getcontext-method.md)|未實作。|  
|[GetFieldValue 方法](icordebugobjectvalue-getfieldvalue-method.md)|取得[ICorDebugValue](icordebugvalue-interface.md)的介面指標，表示指定類別之指定欄位的值。|  
|[GetManagedCopy 方法](icordebugobjectvalue-getmanagedcopy-method.md)|已過時。 請勿呼叫此方法。|  
|[GetVirtualMethod 方法](icordebugobjectvalue-getvirtualmethod-method.md)|未實作。|  
|[IsValueClass 方法](icordebugobjectvalue-isvalueclass-method.md)|取得值，指出這個 `ICorDebugObjectValue` 所參考的物件是否為實值型別。|  
|[SetFromManagedCopy 方法](icordebugobjectvalue-setfrommanagedcopy-method.md)|已過時。 請勿呼叫此方法。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugObjectValue` 會維持有效，直到正在進行調試的進程繼續進行為止。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
