---
title: EClrEvent 列舉
ms.date: 03/30/2017
api_name:
- EClrEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrEvent
helpviewer_keywords:
- EClrEvent enumeration [.NET Framework hosting]
ms.assetid: 7c36a7c2-75a2-4971-bc23-abf54c812154
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1e003ba23f680c4a5525a956d758aac6b823eb9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769716"
---
# <a name="eclrevent-enumeration"></a>EClrEvent 列舉
描述通用語言執行平台 (CLR) 事件，主機可以註冊的回呼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum {  
    Event_ClrDisabled,  
    Event_DomainUnload,  
    Event_MDAFired,  
    Event_StackOverflow  
} EClrEvent;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`Event_ClrDisabled`|指定嚴重的 CLR 錯誤。|  
|`Event_DomainUnload`|指定特定的卸載<xref:System.AppDomain>。|  
|`Event_MDAFired`|指定已產生 Managed 偵錯助理 (MDA) 訊息。|  
|`Event_StackOverflow`|指定發生堆疊溢位錯誤。|  
  
## <a name="remarks"></a>備註  
 主機可以註冊的任何事件類型所描述的回呼`EClrEvent`藉由呼叫的方法[ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)介面。 主機取得這個介面的指標，藉由呼叫[iclrcontrol:: Getclrmanager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)方法。  
  
 `Event_CLRDisabled`和`Event_DomainUnload`可以引發事件，一次以上，並從不同的執行緒，以表示卸載或 CLR 的停用。  
  
 `Event_MDAFired`事件引發建立[MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)包含 MDA 訊息的詳細資料的執行個體。 如需有關 Mda 的詳細資訊，請參閱 < [Managed 偵錯助理診斷錯誤](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** MSCorEE.dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IActionOnCLREvent 介面](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [ICLRControl 介面](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
