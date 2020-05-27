---
title: WAIT_OPTION 列舉
ms.date: 03/30/2017
api_name:
- WAIT_OPTION
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAIT_OPTION
helpviewer_keywords:
- WAIT_OPTION enumeration [.NET Framework hosting]
ms.assetid: 962fc293-8ded-4b3b-90ce-2c21a4f1b244
topic_type:
- apiref
ms.openlocfilehash: 4c57a3fde3565a21800c60794b6c2d1c7616ddd8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007997"
---
# <a name="wait_option-enumeration"></a>WAIT_OPTION 列舉
包含值，指出當 common language runtime （CLR）區塊要求的作業時，主機應採取的動作。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|當 CLR 呼叫[IHostTask：： Alert](ihosttask-alert-method.md)方法時，通知主機應該喚醒工作。|  
|`WAIT_MSGPUMP`|當執行緒遭到封鎖時，通知主機必須在目前的 OS 執行緒上提取訊息。 執行時間只會線上程上指定此值 <xref:System.Threading.ApartmentState.STA> 。|  
|`WAIT_NOTINDEADLOCK`|通知主機，主機無法中斷指定的同步處理要求。 也就是，主機無法傳回 `HOST_E_DEADLOCK` 。|  
  
## <a name="remarks"></a>備註  
 [IHostTaskManager：： Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md)和[IHostTaskManager：： SwitchToTask](ihosttaskmanager-switchtotask-method.md)方法都採用此類型的參數。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載列舉](hosting-enumerations.md)
