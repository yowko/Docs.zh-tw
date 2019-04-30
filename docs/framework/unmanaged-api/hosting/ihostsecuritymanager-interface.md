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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f45379fe8640ef7e7b3917bac8d10ca956d75ffb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61957582"
---
# <a name="ihostsecuritymanager-interface"></a>IHostSecurityManager 介面
提供方法，讓存取權和控制權的目前執行中執行緒的安全性內容。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetSecurityContext 方法](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|取得要求[IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)從主應用程式。|  
|[ImpersonateLoggedOnUser 方法](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)|要求執行程式碼會使用目前的使用者身分識別的認證。|  
|[OpenThreadToken 方法](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-openthreadtoken-method.md)|開啟與目前執行緒相關聯的 discretionary 存取權杖。|  
|[RevertToSelf 方法](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)|終止目前的使用者身分識別模擬，並傳回原始的執行緒 token。|  
|[SetSecurityContext 方法](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)|設定目前執行中執行緒的安全性內容。|  
|[SetThreadToken 方法](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setthreadtoken-method.md)|設定目前執行中執行緒的控制代碼。|  
  
## <a name="remarks"></a>備註  
 主機可以控制執行緒權杖的所有程式碼存取的通用語言執行平台 (CLR) 」 和 「 使用者程式碼。 它也可以確保完整的安全性內容資訊傳遞到非同步作業或受限制的程式碼存取的字碼指標。 `IHostSecurityContext` 封裝此資訊安全內容資訊，也就是對 CLR 不透明。  
  
 CLR 會在內部處理 managed 的執行緒內容。 它會查詢處理序專屬`IHostSecurityManager`在下列情況：  
  
- 在完成項執行期間的完成項執行緒。  
  
- 在類別和模組的建構函式執行。  
  
- 在背景工作執行緒的呼叫中的非同步點[ihostthreadpoolmanager:: Queueuserworkitem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)方法。  
  
- 在服務的 I/O 完成連接埠。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IHostSecurityContext 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
