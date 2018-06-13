---
title: ICorDebugValue Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue
helpviewer_keywords:
- ICorDebugValue interface [.NET Framework debugging]
ms.assetid: b2f7007f-c446-4b18-aed1-a25cff8aee31
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0fe53490014a2a7d9acc0a426613af54867599e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422119"
---
# <a name="icordebugvalue-interface1"></a>ICorDebugValue Interface1
表示正在進行偵錯的處理序中的值。 值可以是讀取或寫入值。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CreateBreakpoint 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-createbreakpoint-method.md)|目前尚未實作這個方法。|  
|[GetAddress 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)|取得這個位址`ICorDebugValue`物件，它是正在進行偵錯。|  
|[GetSize 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)|取得以位元組為單位，這個大小，`ICorDebugValue`物件。|  
|[GetType 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)|取得這個的基本型別`ICorDebugValue`物件。|  
  
## <a name="remarks"></a>備註  
 一般情況下，當它傳回時，會傳遞值物件的擁有權。 收件者會負責在物件完成時，從物件移除參考。  
  
 根據位置已從擷取的值，值可能不會維持有效之後繼續此程序。 因此，在一般情況下，值不應該保留跨的呼叫[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)方法。  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
    
    
    
    
 [ICorDebugValue3 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
