---
title: "RUNTIME_INFO_FLAGS 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: RUNTIME_INFO_FLAGS
api_location: mscoree.dll
api_type: COM
f1_keywords: RUNTIME_INFO_FLAGS
helpviewer_keywords: RUNTIME_INFO_FLAGS enumeration [.NET Framework hosting]
ms.assetid: adba37be-f775-4cdb-8919-5746ce694f33
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 697111efbb4e3f705c881ec677f781b6e3e6959d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="runtimeinfoflags-enumeration"></a>RUNTIME_INFO_FLAGS 列舉
包含值，指出應該傳回 common language runtime (CLR) 的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum {  
  
    RUNTIME_INFO_UPGRADE_VERSION             = 0x01,  
    RUNTIME_INFO_REQUEST_IA64                = 0x02,  
    RUNTIME_INFO_REQUEST_AMD64               = 0x04,  
    RUNTIME_INFO_REQUEST_X86                 = 0x08,  
    RUNTIME_INFO_DONT_RETURN_DIRECTORY       = 0x10,  
    RUNTIME_INFO_DONT_RETURN_VERSION         = 0x20,  
    RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG      = 0x40,  
    RUNTIME_INFO_IGNORE_ERROR_MODE           = 0x1000  
  
} RUNTIME_INFO_FLAGS;  
```  
  
## <a name="members"></a>成員  
  
|成員|說明|  
|------------|-----------------|  
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|指出不應該包含目錄資訊。|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|指出不應該包含版本資訊。|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|表示不應該在發生錯誤時顯示錯誤對話方塊。|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|表示呼叫的效果[SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkId=255242) SEM_FAILCRITICALERRORS 旗標的函式應該覆寫。 也就是在發生錯誤，而不是要隱藏應該會顯示 [安裝] 對話方塊。|  
|`RUNTIME_INFO_REQUEST_AMD64`|表示要求的執行階段的 AMD 64 相容版本的相關資訊。|  
|`RUNTIME_INFO_REQUEST_IA64`|表示要求的執行階段 IA 64 相容版本的相關資訊。|  
|`RUNTIME_INFO_REQUEST_X86`|表示要求的執行階段與 x86 相容的版本資訊。|  
|`RUNTIME_INFO_UPGRADE_VERSION`|表示應該包含版本升級的資訊。|  
  
## <a name="remarks"></a>備註  
 下列平台架構旗標可以一次只能指定的一個，而且無法結合：  
  
-   RUNTIME_INFO_REQUEST_IA64  
  
-   RUNTIME_INFO_REQUEST_AMD64  
  
-   RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** MSCorEE.dll  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
