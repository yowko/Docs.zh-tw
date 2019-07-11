---
title: NOTIFY_FILTER 列舉
ms.date: 03/30/2017
api_name:
- NOTIFY_FILTER
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- NOTIFY_FILTER
helpviewer_keywords:
- NOTIFY_FILTER enumeration [.NET Framework debugging]
ms.assetid: 4789d08f-8683-45d3-ac30-73d48c61e470
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09c36dd65c8a4202f13d362668f74cd9a362e35a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744364"
---
# <a name="notifyfilter-enumeration"></a>NOTIFY_FILTER 列舉
識別偵錯工具的函式的回呼。 如需詳細資訊，請參閱 < [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum tagNOTIFY_FILTER  
{  
    NOTIFY_FILTER_ONSYNCCALLOUT    = 0x1,  
    NOTIFY_FILTER_ONSYNCCALLENTER  = 0x2,  
    NOTIFY_FILTER_ONSYNCCALLEXIT   = 0x4,  
    NOTIFY_FILTER_ONSYNCCALLRETURN = 0x8,  
    NOTIFY_FILTER_ALLSYNC = NOTIFY_FILTER_ONSYNCCALLOUT | NOTIFY_FILTER_ONSYNCCALLENTER | NOTIFY_FILTER_ONSYNCCALLEXIT | NOTIFY_FILTER_ONSYNCCALLRETURN,  
    NOTIFY_FILTER_ALL              = 0xffffffff,  
    NOTIFY_FILTER_NONE             = 0  
};  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`NOTIFY_FILTER_ONSYNCCALLOUT`|指出[INotifySink2::OnSyncCallOut](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md)應該叫用方法。|  
|`NOTIFY_FILTER_ONSYNCCALLENTER`|指出[INotifySink2::OnSyncCallEnter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md)應該叫用方法。|  
|`NOTIFY_FILTER_ONSYNCCALLEXIT`|指出[INotifySink2::OnSyncCallExit](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md)應該叫用方法。|  
|`NOTIFY_FILTER_ONSYNCCALLRETURN`|指出[INotifySink2::OnSyncCallReturn](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md)應該叫用方法。|  
|`NOTIFY_FILTER_ALLSYNC`|表示所有[INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)應該叫用方法。|  
|`NOTIFY_FILTER_ALL`|啟動所有現有和未來的通知。|  
|`NOTIFY_FILTER_NONE`|表示不應該叫用沒有通知方法。|  
  
## <a name="requirements"></a>需求  
 **標頭：** ProtocolNotify2.idl  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區列舉](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
