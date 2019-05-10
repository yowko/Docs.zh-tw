---
title: RUNTIME_INFO_FLAGS 列舉
ms.date: 03/30/2017
api_name:
- RUNTIME_INFO_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- RUNTIME_INFO_FLAGS
helpviewer_keywords:
- RUNTIME_INFO_FLAGS enumeration [.NET Framework hosting]
ms.assetid: adba37be-f775-4cdb-8919-5746ce694f33
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0f4b6e024d75d9334f91373f9d3bbd2c5e41093
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622515"
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
  
|成員|描述|  
|------------|-----------------|  
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|表示不應該包含目錄資訊。|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|表示不應該包含版本資訊。|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|表示不應在失敗時顯示錯誤對話方塊。|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|指出呼叫的效果[SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242)應該覆寫 SEM_FAILCRITICALERRORS 旗標的函式。 亦即，[安裝] 對話方塊中，應該會顯示發生錯誤時，而不是要隱藏。|  
|`RUNTIME_INFO_REQUEST_AMD64`|表示要求的執行階段的 AMD 64 相容版本的相關資訊。|  
|`RUNTIME_INFO_REQUEST_IA64`|表示要求的執行階段的 IA-64-相容版本的相關資訊。|  
|`RUNTIME_INFO_REQUEST_X86`|表示要求的執行階段與 x86 相容的版本資訊。|  
|`RUNTIME_INFO_UPGRADE_VERSION`|表示應該包含版本升級資訊。|  
  
## <a name="remarks"></a>備註  
 下列平台架構旗標可以一次只能指定的一個，而且無法結合：  
  
- RUNTIME_INFO_REQUEST_IA64  
  
- RUNTIME_INFO_REQUEST_AMD64  
  
- RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** MSCorEE.dll  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
