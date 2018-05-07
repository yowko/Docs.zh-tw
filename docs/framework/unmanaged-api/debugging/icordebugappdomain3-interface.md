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
ms.openlocfilehash: 7c130b92fd5114d067730da3b7cd138d98cf0577
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugappdomain3-interface"></a>ICorDebugAppDomain3 介面
提供方法來擷取資訊的受管理的表示法[!INCLUDE[wrt](../../../../includes/wrt-md.md)]目前載入的應用程式定義域中的類型。 這個介面是 ICorDebugAppDomain 和 ICorDebugAppDomain2 介面的擴充功能。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Icordebugappdomain3:: Getcachedwinrttypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|取得列舉值，所有快取[!INCLUDE[wrt](../../../../includes/wrt-md.md)]型別。|  
|[Icordebugappdomain3:: Getcachedwinrttypesforiids](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|取得列舉值的快取[!INCLUDE[wrt](../../../../includes/wrt-md.md)]應用程式定義域中的類型取決於其介面識別項。|  
  
## <a name="remarks"></a>備註  
 這個介面是用於偵錯工具的函式評估呼叫搭配`M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`。 當方法會擷取所支援的介面識別碼[!INCLUDE[wrt](../../../../includes/wrt-md.md)]伺服器物件時，偵錯工具可能會使用此介面中定義的方法以對應至對應到這些介面的 managed 型別。  
  
 若要擷取此介面的執行個體，執行`QueryInterface`ICorDebugAppDomain 或 ICorDebugAppDomain2 介面的執行個體上。  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
