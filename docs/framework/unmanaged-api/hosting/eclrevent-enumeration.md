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
ms.openlocfilehash: 5d6ec42da60a7b294177063b9f8bd5afbf352c62
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726817"
---
# <a name="eclrevent-enumeration"></a>EClrEvent 列舉

描述 common language runtime (CLR) 可供主機註冊回呼的事件。  
  
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
  
|member|描述|  
|------------|-----------------|  
|`Event_ClrDisabled`|指定嚴重的 CLR 錯誤。|  
|`Event_DomainUnload`|指定特定的卸載 <xref:System.AppDomain> 。|  
|`Event_MDAFired`|指定已產生 Managed 偵錯工具 (MDA) 訊息。|  
|`Event_StackOverflow`|指定發生堆疊溢位錯誤。|  
  
## <a name="remarks"></a>備註  

 主機可以藉 `EClrEvent` 由呼叫 [ICLROnEventManager](iclroneventmanager-interface.md) 介面的方法，為所描述的任何事件種類註冊回呼。 主機會呼叫 [ICLRControl：： GetCLRManager](iclrcontrol-getclrmanager-method.md) 方法，以取得這個介面的指標。  
  
 `Event_CLRDisabled`和 `Event_DomainUnload` 事件可以從不同的執行緒引發一次以上，以表示卸載或停用 CLR。  
  
 此 `Event_MDAFired` 事件會引發 [MDAInfo](mdainfo-structure.md) 實例的建立，其中包含 MDA 訊息的詳細資料。 如需有關 Mda 的詳細資訊，請參閱 [診斷 Managed 偵錯工具的錯誤](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IActionOnCLREvent 介面](iactiononclrevent-interface.md)
- [ICLRControl 介面](iclrcontrol-interface.md)
- [裝載列舉](hosting-enumerations.md)
