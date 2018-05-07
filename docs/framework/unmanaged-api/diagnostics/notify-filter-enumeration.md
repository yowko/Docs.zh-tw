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
ms.openlocfilehash: 98c3e1ed3da209cbded5d76d938d2420fce606be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="notifyfilter-enumeration"></a>NOTIFY_FILTER 列舉
識別偵錯工具功能的回呼。 如需詳細資訊，請參閱[inotifysource2:: Setnotifyfilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```  
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
|`NOTIFY_FILTER_ONSYNCCALLOUT`|表示[inotifysink2:: Onsynccallout](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md)叫用方法。|  
|`NOTIFY_FILTER_ONSYNCCALLENTER`|表示[inotifysink2:: Onsynccallenter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md)叫用方法。|  
|`NOTIFY_FILTER_ONSYNCCALLEXIT`|表示[inotifysink2:: Onsynccallexit](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md)叫用方法。|  
|`NOTIFY_FILTER_ONSYNCCALLRETURN`|表示[inotifysink2:: Onsynccallreturn](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md)叫用方法。|  
|`NOTIFY_FILTER_ALLSYNC`|表示所有[INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)叫用方法。|  
|`NOTIFY_FILTER_ALL`|啟動所有的現有及未來通知。|  
|`NOTIFY_FILTER_NONE`|指出應叫用任何通知方法。|  
  
## <a name="requirements"></a>需求  
 **標頭：** ProtocolNotify2.idl  
  
## <a name="see-also"></a>另請參閱  
 [診斷符號存放區列舉](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
