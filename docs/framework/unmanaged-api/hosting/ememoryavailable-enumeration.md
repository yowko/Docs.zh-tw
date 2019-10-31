---
title: EMemoryAvailable 列舉
ms.date: 03/30/2017
api_name:
- EMemoryAvailable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryAvailable
helpviewer_keywords:
- EMemoryAvailable enumeration [.NET Framework hosting]
ms.assetid: 38e72a06-dbed-473b-a59b-7e0b3ea4f2af
topic_type:
- apiref
ms.openlocfilehash: aec3c5f140df7eab10ea2bfa33634a4d853adcb0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134295"
---
# <a name="ememoryavailable-enumeration"></a>EMemoryAvailable 列舉
包含值，指出電腦上的可用實體記憶體數量。 這些值會以邏輯方式對應至 Windows API 中 `CreateMemoryResourceNotification` 函式所傳回之高和低記憶體的事件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3   
} EMemoryAvailable;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|有足夠的實體記憶體可供使用。|  
|`eMemoryAvailableLow`|有極少的實體記憶體可供使用。|  
|`eMemoryAvailableNeutral`|可用的實體記憶體是中性的。|  
  
## <a name="remarks"></a>備註  
 此值會透過呼叫[ICLRMemoryNotificationCallback：： OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)方法，由主機傳遞至 common language RUNTIME （CLR）。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
