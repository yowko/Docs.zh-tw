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
ms.openlocfilehash: c3676cb32ceaf6f241672751f0feafbd3cb83e05
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968867"
---
# <a name="icordebugappdomain3-interface"></a>ICorDebugAppDomain3 介面
提供方法, 以取得目前載入應用程式域之 Windows 執行階段類型的 managed 標記法的相關資訊。 這個介面是 ICorDebugAppDomain 和 ICorDebugAppDomain2 介面的延伸。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|取得所有快取 Windows 執行階段類型的列舉值。|  
|[ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|根據介面識別碼, 取得應用程式域中快取 Windows 執行階段類型的列舉值。|  
  
## <a name="remarks"></a>備註  
 這個介面適用于偵錯工具搭配的函式評估呼叫`M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`使用。 當方法抓取 Windows 執行階段 server 物件所支援的介面識別碼時, 偵錯工具可能會使用在這個介面中定義的方法, 將它們對應到與這些介面相對應的 managed 類型。  
  
 若要取得此介面的實例, 請`QueryInterface`在 ICorDebugAppDomain 或 ICorDebugAppDomain2 介面的實例上執行。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** Windows 執行階段  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
