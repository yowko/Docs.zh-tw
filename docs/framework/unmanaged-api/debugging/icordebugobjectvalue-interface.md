---
title: ICorDebugObjectValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugObjectValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugObjectValue
helpviewer_keywords: ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 937de6a0-6fbf-4ddc-80ea-a6217b73e62b
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: acbfbbb8f7374b1ab783371d318bd3bcf89963fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugobjectvalue-interface1"></a>ICorDebugObjectValue Interface1
「 ICorDebugValue"，表示包含物件的值的子類別。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|[GetClass 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|Common language runtime (CLR) 中取得的介面指標<xref:System.Type>物件的這個`ICorDebugObjectValue`參考。|  
|[GetContext 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|未實作。|  
|[GetFieldValue 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|取得的介面指標[ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md)表示指定類別的指定之欄位的值。|  
|[GetManagedCopy 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|已過時。 請勿呼叫這個方法。|  
|[GetVirtualMethod 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|未實作。|  
|[IsValueClass 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|取得值，指出物件是否參考由此`ICorDebugObjectValue`是實值類型。|  
|[SetFromManagedCopy 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|已過時。 請勿呼叫這個方法。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugObjectValue`就持續有效，直到進行偵錯處理序會繼續。  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 
