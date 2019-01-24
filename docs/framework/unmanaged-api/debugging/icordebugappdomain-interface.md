---
title: ICorDebugAppDomain 介面 1
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain
helpviewer_keywords:
- ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9588ac26c698a8369f1ae4be89af7440a2dd1de4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546302"
---
# <a name="icordebugappdomain-interface1"></a>ICorDebugAppDomain 介面 1
提供偵錯應用程式定義域的方法。 這個介面是 ICorDebugController 的子類別。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Attach 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|將偵錯工具附加至應用程式定義域中。|  
|[EnumerateAssemblies 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|取得組件的列舉值，應用程式定義域中。|  
|[EnumerateBreakpoints 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|取得應用程式定義域中所有使用中的中斷點列舉值。|  
|[EnumerateSteppers 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|應用程式定義域中取得所有作用中的 steppers 的列舉值。|  
|[GetId 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|取得應用程式定義域的唯一識別碼。|  
|[GetModuleFromMetaDataInterface 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|取得與指定之中繼資料介面的 ICorDebugModule 物件。|  
|[GetName 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|取得應用程式定義域的名稱。|  
|[GetObject 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|Common language runtime (CLR) 應用程式定義域中取得的介面指標。|  
|[GetProcess 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|取得包含應用程式定義域的處理序。|  
|[IsAttached 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|決定是否要將偵錯工具附加至應用程式定義域。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
