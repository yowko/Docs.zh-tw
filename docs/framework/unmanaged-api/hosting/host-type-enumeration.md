---
title: HOST_TYPE 列舉
ms.date: 03/30/2017
api_name:
- HOST_TYPE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- HOST_TYPE
helpviewer_keywords:
- HOST_TYPE enumeration [.NET Framework hosting]
ms.assetid: 51f848be-84c5-4036-9839-c762c576bbf5
topic_type:
- apiref
ms.openlocfilehash: cc0cea10b4a209583fb7afb551a6b80d52ad7f62
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127020"
---
# <a name="host_type-enumeration"></a>HOST_TYPE 列舉
包含值，指定啟動應用程式的主控制項類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|從 AppLaunch 啟動應用程式。<br /><br /> 對於部分信任的應用程式，請使用此值。|  
|`HOST_TYPE_CORFLAG`|直接啟動應用程式。 也就是從本身的 .exe 檔案啟動應用程式。<br /><br /> 對於完全信任的應用程式，請使用此值。|  
|`HOST_TYPE_DEFAULT`|與 HOST_TYPE_APPLAUNCH 相同。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
