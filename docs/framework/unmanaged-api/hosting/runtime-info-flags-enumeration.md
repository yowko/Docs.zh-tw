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
ms.openlocfilehash: 80643187045e7e96b9c18169c5e71287713d711f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73106243"
---
# <a name="runtime_info_flags-enumeration"></a>RUNTIME_INFO_FLAGS 列舉
包含值，指出應該傳回的通用語言執行時間（CLR）的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|表示不應包含目錄資訊。|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|表示不應包含版本資訊。|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|表示失敗時不應顯示錯誤對話方塊。|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|表示應該覆寫使用 SEM_FAILCRITICALERRORS 旗標呼叫[SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242)函數的效果。 也就是說，安裝對話方塊應該會在失敗時顯示，而不是隱藏。|  
|`RUNTIME_INFO_REQUEST_AMD64`|表示要求，以取得與 AMD-64 相容版本之執行時間的相關資訊。|  
|`RUNTIME_INFO_REQUEST_IA64`|表示要求，以取得與 IA-64 相容版本之執行時間的相關資訊。|  
|`RUNTIME_INFO_REQUEST_X86`|指出與 x86 相容版本的執行時間相關資訊的要求。|  
|`RUNTIME_INFO_UPGRADE_VERSION`|表示應該包含版本升級資訊。|  
  
## <a name="remarks"></a>備註  
 下列平臺架構旗標一次只能指定一個，而且無法合併：  
  
- RUNTIME_INFO_REQUEST_IA64  
  
- RUNTIME_INFO_REQUEST_AMD64  
  
- RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
