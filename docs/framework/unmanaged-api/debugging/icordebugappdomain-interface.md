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
ms.openlocfilehash: 140e67417f4fad552f972a93bc8c620b440b2370
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895178"
---
# <a name="icordebugappdomain-interface"></a>ICorDebugAppDomain 介面

提供偵錯應用程式定義域的方法。 這個介面是 ICorDebugController 的子類別。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Attach 方法](icordebugappdomain-attach-method.md)|將偵錯工具附加至應用程式域。|  
|[EnumerateAssemblies 方法](icordebugappdomain-enumerateassemblies-method.md)|取得應用程式域中元件的列舉值。|  
|[EnumerateBreakpoints 方法](icordebugappdomain-enumeratebreakpoints-method.md)|取得應用程式域中所有使用中中斷點的列舉值。|  
|[EnumerateSteppers 方法](icordebugappdomain-enumeratesteppers-method.md)|取得應用程式域中所有現用 steppers 的列舉值。|  
|[GetId 方法](icordebugappdomain-getid-method.md)|取得應用程式域的唯一識別碼。|  
|[GetModuleFromMetaDataInterface 方法](icordebugappdomain-getmodulefrommetadatainterface-method.md)|取得具有指定之中繼資料介面的 ICorDebugModule 物件。|  
|[GetName 方法](icordebugappdomain-getname-method.md)|取得應用程式域的名稱。|  
|[GetObject 方法](icordebugappdomain-getobject-method.md)|取得 common language runtime （CLR）應用程式域的介面指標。|  
|[GetProcess 方法](icordebugappdomain-getprocess-method.md)|取得包含應用程式域的進程。|  
|[IsAttached 方法](icordebugappdomain-isattached-method.md)|判斷偵錯工具是否附加至應用程式域。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
