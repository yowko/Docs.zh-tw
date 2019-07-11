---
title: ICLRDebugManager::SetDacl 方法
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.SetDacl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::SetDacl
helpviewer_keywords:
- SetDacl method [.NET Framework hosting]
- ICLRDebugManager::SetDacl method [.NET Framework hosting]
ms.assetid: 52f4af3f-e02b-4c20-9fd9-e8e4f4d6fc31
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8c5d35af072b773786a8be5ad7d1e71a21c38b2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773072"
---
# <a name="iclrdebugmanagersetdacl-method"></a>ICLRDebugManager::SetDacl 方法
這個方法尚未實作。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetDacl (  
    [in] PACL pacl  
);  
```  
  
## <a name="parameters"></a>參數  
 `pacl`  
 [in]指標的存取控制清單 (ACL)。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|E_NOTIMPL|未實作方法。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRControl 介面](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLRDebugManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [GetDacl 方法](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-getdacl-method.md)
- [IHostControl 介面](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
