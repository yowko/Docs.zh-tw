---
title: MALLOC_TYPE 列舉
ms.date: 03/30/2017
api_name:
- MALLOC_TYPE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MALLOC_TYPE
helpviewer_keywords:
- MALLOC_TYPE Enumeration
ms.assetid: c02476f9-23a2-4af7-9282-aa9c42c7429b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 695f69c8d9c3a295a705971743733339cf8aab13
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211942"
---
# <a name="malloctype-enumeration"></a>MALLOC_TYPE 列舉
包含值，指定要配置的記憶體的特性。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|配置的記憶體可以包含可執行檔。|  
|`MALLOC_THREADSAFE`|配置的記憶體是安全執行緒。 也就是不需要任何同步處理多個執行緒可以存取的記憶體。<br /><br /> 如果未設定此旗標，則必須序列化物件上的呼叫。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** MSCorEE.dll  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
