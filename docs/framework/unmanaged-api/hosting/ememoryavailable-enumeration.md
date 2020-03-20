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
ms.openlocfilehash: 0073a532f680d8764ec9e76ea22326a630457043
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176431"
---
# <a name="ememoryavailable-enumeration"></a>EMemoryAvailable 列舉
包含指示電腦上可用實體記憶體量的值。 這些值以邏輯方式映射到 Windows API 中`CreateMemoryResourceNotification`函數返回的高記憶體和低記憶體的事件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3
} EMemoryAvailable;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|大量的實體記憶體可用。|  
|`eMemoryAvailableLow`|幾乎沒有可用的實體記憶體。|  
|`eMemoryAvailableNeutral`|可用的實體記憶體是中性的。|  
  
## <a name="remarks"></a>備註  
 此值由主機傳遞到通用語言運行時 （CLR），方法是使用對[ICLR 記憶體通知回檔的調用：：在記憶體通知方法上](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** MSCorEE.h  
  
 **庫：** MSCorEE.dll  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
