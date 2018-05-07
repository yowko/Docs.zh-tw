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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 28f6bdbc3e382f82b7fdd632b9fc8c4d422629c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="esymbolreadingpolicy-enumeration"></a>ESymbolReadingPolicy 列舉
包含值，設定原則的讀取程式資料庫 (PDB) 檔案。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`eSymbolReadingAlways`|指定偵錯工具應該一律讀取 PDB 檔案。|  
|`eSymbolReadingFullTrustOnly`|指定偵錯工具應該讀取與完全信任組件相關聯的 PDB 檔案。|  
|`eSymbolReadingNever`|指定偵錯工具應該永遠不會讀取 PDB 檔案。|  
  
## <a name="remarks"></a>備註  
 `ESymbolReadingPolicy`列舉會搭配[iclrdebugmanager:: Setsymbolreadingpolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** MSCorEE.dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
