---
title: ICorDebugAppDomain3 介面
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3
helpviewer_keywords:
- ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 875ef5be-c1e7-4d95-97e9-d3a667aeaba0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 256fd900fa73948b4ca42ac6b6f21f145effc461
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025889"
---
# <a name="icordebugappdomain3-interface"></a>ICorDebugAppDomain3 介面
提供方法來擷取目前已載入應用程式定義域中的 Windows 執行階段類型的 managed 表示法的相關資訊。 這個介面是 ICorDebugAppDomain 和 ICorDebugAppDomain2 介面的延伸模組。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|取得所有快取的 Windows 執行階段類型的列舉值。|  
|[ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|取得其介面識別項為基礎的應用程式定義域中快取的 Windows 執行階段類型的列舉值。|  
  
## <a name="remarks"></a>備註  
 這個介面適用於偵錯工具的函式評估呼叫搭配`M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`。 方法會擷取支援的 Windows 執行階段伺服器物件的介面識別項，偵錯工具可以將其對應到對應至這些介面的 managed 類型中使用此介面中定義的方法。  
  
 若要擷取此介面的執行個體，請執行`QueryInterface`ICorDebugAppDomain 或 ICorDebugAppDomain2 介面的執行個體上。  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** Windows 執行階段  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
