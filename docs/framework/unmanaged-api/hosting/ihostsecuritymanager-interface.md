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
ms.openlocfilehash: b2c334c7a757c2f4044d08787bdae93ffc2804e4
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803889"
---
# <a name="ihostsecuritymanager-interface"></a>IHostSecurityManager 介面
提供的方法可讓您存取和控制目前執行之執行緒的安全性內容。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetSecurityContext 方法](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|從主機取得要求的[IHostSecurityCoNtext](ihostsecuritycontext-interface.md) 。|  
|[ImpersonateLoggedOnUser 方法](ihostsecuritymanager-impersonateloggedonuser-method.md)|要求使用目前使用者識別的認證來執行程式碼。|  
|[OpenThreadToken 方法](ihostsecuritymanager-openthreadtoken-method.md)|開啟與目前線程相關聯的任意存取權杖。|  
|[RevertToSelf 方法](ihostsecuritymanager-reverttoself-method.md)|終止目前使用者身分識別的模擬，並傳回原始的執行緒 token。|  
|[SetSecurityContext 方法](ihostsecuritymanager-setsecuritycontext-method.md)|設定目前執行中線程的安全性內容。|  
|[SetThreadToken 方法](ihostsecuritymanager-setthreadtoken-method.md)|設定目前執行中線程的控制碼。|  
  
## <a name="remarks"></a>備註  
 主機可以透過 common language runtime （CLR）和使用者程式碼，控制執行緒標記的所有程式碼存取。 它也可以確保以限制的程式碼存取，在非同步作業或程式碼點之間傳遞完整的安全性內容資訊。 `IHostSecurityContext`封裝此安全性內容資訊，這對 CLR 而言是不透明的。  
  
 CLR 會在內部處理 managed 執行緒內容。 它會 `IHostSecurityManager` 在下列情況中查詢特定進程：  
  
- 在完成項執行緒中，于完成項執行期間。  
  
- 在類別和模組的函式執行期間。  
  
- 在背景工作執行緒上的非同步點上，呼叫[IHostThreadPoolManager：： QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md)方法。  
  
- I/o 完成通訊埠的服務。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IHostSecurityContext 介面](ihostsecuritycontext-interface.md)
- [裝載介面](hosting-interfaces.md)
