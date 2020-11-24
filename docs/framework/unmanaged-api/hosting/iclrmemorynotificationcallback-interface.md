---
title: ICLRMemoryNotificationCallback 介面
ms.date: 03/30/2017
api_name:
- ICLRMemoryNotificationCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMemoryNotificationCallback
helpviewer_keywords:
- ICLRMemoryNotificationCallback interface [.NET Framework hosting]
ms.assetid: 873639e2-4837-4568-83b3-4493e67e4174
topic_type:
- apiref
ms.openlocfilehash: 5762a354bec485cb382b5460dfd2a337f79bee1a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689533"
---
# <a name="iclrmemorynotificationcallback-interface"></a>ICLRMemoryNotificationCallback 介面

允許主機使用類似 Win32 函數的方法來報告記憶體壓力條件 `CreateMemoryResourceNotification` 。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[OnMemoryNotification 方法](iclrmemorynotificationcallback-onmemorynotification-method.md)|通知 common language runtime (CLR) 電腦上的記憶體負載。|  
  
## <a name="remarks"></a>備註  

 主機 `ICLRMemoryNotificationCallback` 會使用介面來要求 CLR 可用記憶體資源。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IHostMemoryManager 介面](ihostmemorymanager-interface.md)
- [裝載介面](hosting-interfaces.md)
