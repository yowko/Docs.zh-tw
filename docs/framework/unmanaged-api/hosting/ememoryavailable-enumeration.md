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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 139cf540617e278eeaae8a2a5acf10dd797d5d10
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ememoryavailable-enumeration"></a>EMemoryAvailable 列舉
包含值，表示電腦上的可用實體記憶體數量。 這些值以邏輯方式對應至事件的記憶體從傳回的最高和最低`CreateMemoryResourceNotification`Win32 API 中的函式。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3   
} EMemoryAvailable;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|足夠的實體記憶體使用。|  
|`eMemoryAvailableLow`|使用實體記憶體很少。|  
|`eMemoryAvailableNeutral`|可用的實體記憶體是中性。|  
  
## <a name="remarks"></a>備註  
 這個值會傳遞由 common language runtime (CLR) 主機所使用的呼叫[iclrmemorynotificationcallback:: Onmemorynotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** MSCorEE.dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
