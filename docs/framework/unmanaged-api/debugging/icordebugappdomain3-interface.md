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
ms.openlocfilehash: 644457edbf5035f6d946e1c83ff0053fb118288e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698230"
---
# <a name="icordebugappdomain3-interface"></a>ICorDebugAppDomain3 介面

提供方法，以取得目前在應用程式域中載入 Windows 執行階段類型之 managed 表示的相關資訊。 此介面是 ICorDebugAppDomain 和 ICorDebugAppDomain2 介面的延伸。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ICorDebugAppDomain3：： GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md)|取得所有快取 Windows 執行階段類型的列舉值。|  
|[ICorDebugAppDomain3：： GetCachedWinRTTypesForIIDs](icordebugappdomain3-getcachedwinrttypesforiids-method.md)|根據其介面識別碼，取得應用程式域中快取 Windows 執行階段類型的列舉值。|  
  
## <a name="remarks"></a>備註  

 這個介面的目的是要由偵錯工具與的函式評估呼叫一起使用 `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)` 。 當方法抓取 Windows 執行階段 server 物件所支援的介面識別碼時，偵錯工具可能會使用此介面中定義的方法，將它們對應至對應至這些介面的 managed 類型。  
  
 若要取出這個介面的實例，請 `QueryInterface` 在 ICorDebugAppDomain 或 ICorDebugAppDomain2 介面的實例上執行。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  

 **平臺：** Windows 執行階段  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
