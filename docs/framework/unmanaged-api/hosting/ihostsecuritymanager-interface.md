---
title: IHostSecurityManager 介面
ms.date: 03/30/2017
api_name:
- IHostSecurityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager
helpviewer_keywords:
- IHostSecurityManager interface [.NET Framework hosting]
ms.assetid: c3be2cbd-2d93-438b-9888-9a0251b63c03
topic_type:
- apiref
ms.openlocfilehash: 9b7cc41848e41976f388e38bf22c9ea0f90abbae
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121484"
---
# <a name="ihostsecuritymanager-interface"></a>IHostSecurityManager 介面
提供的方法可讓您存取和控制目前執行之執行緒的安全性內容。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetSecurityContext 方法](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|從主機取得要求的[IHostSecurityCoNtext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) 。|  
|[ImpersonateLoggedOnUser 方法](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)|要求使用目前使用者識別的認證來執行程式碼。|  
|[OpenThreadToken 方法](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-openthreadtoken-method.md)|開啟與目前線程相關聯的任意存取權杖。|  
|[RevertToSelf 方法](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)|終止目前使用者身分識別的模擬，並傳回原始的執行緒 token。|  
|[SetSecurityContext 方法](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)|設定目前執行中線程的安全性內容。|  
|[SetThreadToken 方法](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setthreadtoken-method.md)|設定目前執行中線程的控制碼。|  
  
## <a name="remarks"></a>備註  
 主機可以透過 common language runtime （CLR）和使用者程式碼，控制執行緒標記的所有程式碼存取。 它也可以確保以限制的程式碼存取，在非同步作業或程式碼點之間傳遞完整的安全性內容資訊。 `IHostSecurityContext` 封裝此安全性內容資訊，這對 CLR 而言是不透明的。  
  
 CLR 會在內部處理 managed 執行緒內容。 在下列情況下，它會查詢進程特定的 `IHostSecurityManager`：  
  
- 在完成項執行緒中，于完成項執行期間。  
  
- 在類別和模組的函式執行期間。  
  
- 在背景工作執行緒上的非同步點上，呼叫[IHostThreadPoolManager：： QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)方法。  
  
- I/o 完成通訊埠的服務。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [IHostSecurityContext 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
