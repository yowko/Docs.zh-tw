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
ms.openlocfilehash: b20e18d5f4314a0ab1442ac7bd5c6514e4db85d5
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609478"
---
# <a name="notify_filter-enumeration"></a>NOTIFY_FILTER 列舉
識別偵錯工具函式的回呼。 如需詳細資訊，請參閱[INotifySource2：： SetNotifyFilter](inotifysource2-setnotifyfilter-method.md)方法。  
  
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
  
|成員|說明|  
|------------|-----------------|  
|`NOTIFY_FILTER_ONSYNCCALLOUT`|表示應該叫用[INotifySink2：： OnSyncCallOut](inotifysink2-onsynccallout-method.md)方法。|  
|`NOTIFY_FILTER_ONSYNCCALLENTER`|表示應該叫用[INotifySink2：： OnSyncCallEnter](inotifysink2-onsynccallenter-method.md)方法。|  
|`NOTIFY_FILTER_ONSYNCCALLEXIT`|表示應該叫用[INotifySink2：： OnSyncCallExit](inotifysink2-onsynccallexit-method.md)方法。|  
|`NOTIFY_FILTER_ONSYNCCALLRETURN`|表示應該叫用[INotifySink2：： OnSyncCallReturn](inotifysink2-onsynccallreturn-method.md)方法。|  
|`NOTIFY_FILTER_ALLSYNC`|表示應該叫用所有的[INotifySink2](inotifysink2-interface.md)方法。|  
|`NOTIFY_FILTER_ALL`|啟用所有現有和未來的通知。|  
|`NOTIFY_FILTER_NONE`|表示不應叫用任何通知方法。|  
  
## <a name="requirements"></a>需求  
 **標頭：** ProtocolNotify2 .idl  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區列舉](diagnostics-symbol-store-enumerations.md)
