---
title: ESymbolReadingPolicy 列舉
ms.date: 03/30/2017
api_name:
- ESymbolReadingPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ESymbolReadingPolicy
helpviewer_keywords:
- ESymbolReadingPolicy enumeration [.NET Framework hosting]
ms.assetid: 4dc6c80d-b694-480b-a378-d5b18420ce17
topic_type:
- apiref
ms.openlocfilehash: 786ff6895383fc18dcfedb26fab344f80f04c1df
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138200"
---
# <a name="esymbolreadingpolicy-enumeration"></a>ESymbolReadingPolicy 列舉
包含設定讀取程式資料庫（PDB）檔案之原則的值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`eSymbolReadingAlways`|指定偵錯工具應該一律讀取 PDB 檔案。|  
|`eSymbolReadingFullTrustOnly`|指定偵錯工具應該唯讀取與完全信任元件相關聯的 PDB 檔案。|  
|`eSymbolReadingNever`|指定偵錯工具絕對不應讀取 PDB 檔案。|  
  
## <a name="remarks"></a>備註  
 `ESymbolReadingPolicy` 列舉會與[ICLRDebugManager：： SetSymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)方法搭配使用。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
