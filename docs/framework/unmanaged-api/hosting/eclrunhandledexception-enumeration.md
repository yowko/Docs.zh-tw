---
title: EClrUnhandledException 列舉
ms.date: 03/30/2017
api_name:
- EClrUnhandledException
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrUnhandledException
helpviewer_keywords:
- EClrUnhandledException enumeration [.NET Framework hosting]
ms.assetid: d231044e-2b53-4836-93f9-8117ff0e5c3a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ba0c2ea7733f098b7fac95f51b5eb16d083174e8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779374"
---
# <a name="eclrunhandledexception-enumeration"></a>EClrUnhandledException 列舉
描述可用的選項，來管理使用者程式碼中未處理的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|指定預設的行為就會發生。 此程序會終止。|  
|`eHostDeterminedPolicy`|指定 common language runtime (CLR) 會忽略未處理例外狀況，並可讓主機判斷任何進一步的動作。|  
  
## <a name="remarks"></a>備註  
 若要指定 CLR 表現較早版本，請使用`eHostDeterminedPolicy`成員。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** MSCorEE.dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [EClrFailure 列舉](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [EClrOperation 列舉](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [ICLRPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [SetUnhandledExceptionPolicy 方法](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)
- [IHostPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
