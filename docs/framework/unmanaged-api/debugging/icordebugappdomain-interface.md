---
title: ICorDebugAppDomain 介面
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
ms.openlocfilehash: 12753ab65f9339e8f6c3049bb72755e87464eb1a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963101"
---
# <a name="icordebugappdomain-interface"></a>ICorDebugAppDomain 介面

提供偵錯應用程式定義域的方法。 這個介面是 ICorDebugController 的子類別。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|[Attach 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|將偵錯工具附加至應用程式域。|  
|[EnumerateAssemblies 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|取得應用程式域中元件的列舉值。|  
|[EnumerateBreakpoints 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|取得應用程式域中所有使用中中斷點的列舉值。|  
|[EnumerateSteppers 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|取得應用程式域中所有現用 steppers 的列舉值。|  
|[GetId 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|取得應用程式域的唯一識別碼。|  
|[GetModuleFromMetaDataInterface 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|取得具有指定之中繼資料介面的 ICorDebugModule 物件。|  
|[GetName 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|取得應用程式域的名稱。|  
|[GetObject 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|取得 common language runtime (CLR) 應用程式域的介面指標。|  
|[GetProcess 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|取得包含應用程式域的進程。|  
|[IsAttached 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|判斷偵錯工具是否附加至應用程式域。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
