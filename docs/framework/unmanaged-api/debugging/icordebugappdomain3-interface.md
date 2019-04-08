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
ms.openlocfilehash: 7c141ca9a8e1c74015883f45cb2eaa9183bb3d89
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177524"
---
# <a name="icordebugappdomain3-interface"></a>ICorDebugAppDomain3 介面
提供方法來擷取資訊的受管理的表示法[!INCLUDE[wrt](../../../../includes/wrt-md.md)]目前已載入應用程式定義域中的類型。 這個介面是 ICorDebugAppDomain 和 ICorDebugAppDomain2 介面的延伸模組。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|取得列舉值，所有快取[!INCLUDE[wrt](../../../../includes/wrt-md.md)]型別。|  
|[ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|取得列舉值的快取[!INCLUDE[wrt](../../../../includes/wrt-md.md)]其介面識別項為基礎的應用程式定義域中的類型。|  
  
## <a name="remarks"></a>備註  
 這個介面適用於偵錯工具的函式評估呼叫搭配`M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`。 當方法會擷取支援的介面識別項[!INCLUDE[wrt](../../../../includes/wrt-md.md)]伺服器物件，偵錯工具可以使用此介面中定義的方法，將其對應到對應至這些介面的 managed 型別。  
  
 若要擷取此介面的執行個體，請執行`QueryInterface`ICorDebugAppDomain 或 ICorDebugAppDomain2 介面的執行個體上。  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
