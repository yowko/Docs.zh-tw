---
title: LogSwitchCallReason 列舉
ms.date: 03/30/2017
api_name:
- LogSwitchCallReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LogSwitchCallReason
helpviewer_keywords:
- LogSwitchCallReason enumeration [.NET Framework debugging]
ms.assetid: 5bbb8d1b-bbc4-47b0-b1b1-2d54cc0be291
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bba39446d9ca5164d98337e93e83725cfa503903
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54515322"
---
# <a name="logswitchcallreason-enumeration"></a>LogSwitchCallReason 列舉
指出在切換偵錯/追蹤時所執行的作業。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum LogSwitchCallReason {  
    SWITCH_CREATE,  
    SWITCH_MODIFY,  
    SWITCH_DELETE  
} LogSwitchCallReason;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`SWITCH_CREATE`|建立偵錯/追蹤參數。|  
|`SWITCH_MODIFY`|偵錯/追蹤交換器已修改。|  
|`SWITCH_DELETE`|偵錯/追蹤參數已被刪除。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [偵錯列舉](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
