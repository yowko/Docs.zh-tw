---
title: BucketParameters 結構
ms.date: 03/30/2017
api_name:
- BucketParameters
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- BucketParameters
helpviewer_keywords:
- BucketParameters structure [.NET Framework hosting]
ms.assetid: 9432487e-f276-45d6-9a13-9a68024dbd46
topic_type:
- apiref
ms.openlocfilehash: 4d9de489bdeb0ab506f56ff08f4afb4cf6d0ab4f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178280"
---
# <a name="bucketparameters-structure"></a>BucketParameters 結構
存儲事件的類型名稱以及與事件關聯的當前異常的參數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _BucketParameters {  
    BOOL  fInited;
    WCHAR pszEventTypeName[255];
    WCHAR pszParams[10][255];
} BucketParameters;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`fInited`|`true`，如果此結構的其餘部分有效;如果此結構的其餘部分有效，則為否則， `false`.|  
|`pszEventTypeName`|事件種類的名稱。|  
|`pszParams`|字串陣列，每個字串都指定與事件關聯的當前異常的參數。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** MSCorEE.idl  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載結構](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
