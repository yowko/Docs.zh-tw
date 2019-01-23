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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a2db1aea04ae060623bc39a52ed6990f6137f82
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54606438"
---
# <a name="hosttype-enumeration"></a>HOST_TYPE 列舉
包含指定的啟動應用程式的主機類型的值。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|啟動從 AppLaunch.exe 應用程式。<br /><br /> 部分信任的應用程式中使用此值。|  
|`HOST_TYPE_CORFLAG`|直接啟動應用程式。 也就是啟動應用程式與它自己的.exe 檔案。<br /><br /> 使用此值為完全受信任的應用程式。|  
|`HOST_TYPE_DEFAULT`|HOST_TYPE_APPLAUNCH 相同。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** MSCorEE.dll  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
