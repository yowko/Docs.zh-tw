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
ms.openlocfilehash: 37f606a67bef79936c81b2a36f12a00d24bd82f1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680530"
---
# <a name="ihostsecuritymanager-interface"></a>IHostSecurityManager 介面

提供方法，可讓您存取和控制目前執行中線程的安全性內容。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetSecurityContext 方法](ihostsecuritymanager-getsecuritycontext-method.md)|從主機取得要求的 [IHostSecurityCoNtext](ihostsecuritycontext-interface.md) 。|  
|[ImpersonateLoggedOnUser 方法](ihostsecuritymanager-impersonateloggedonuser-method.md)|要求使用目前使用者身分識別的認證來執行程式碼。|  
|[OpenThreadToken 方法](ihostsecuritymanager-openthreadtoken-method.md)|開啟與目前線程相關聯的任意存取權杖。|  
|[RevertToSelf 方法](ihostsecuritymanager-reverttoself-method.md)|終止目前使用者身分識別的模擬，並傳回原始執行緒 token。|  
|[SetSecurityContext 方法](ihostsecuritymanager-setsecuritycontext-method.md)|設定目前執行中線程的安全性內容。|  
|[SetThreadToken 方法](ihostsecuritymanager-setthreadtoken-method.md)|設定目前執行中線程的控制碼。|  
  
## <a name="remarks"></a>備註  

 主機可以透過 common language runtime (CLR) 和使用者程式碼，控制執行緒權杖的所有程式碼存取。 它也可以確保在非同步作業或具有限制程式碼存取的程式碼點之間傳遞完整的安全性內容資訊。 `IHostSecurityContext` 封裝此安全性內容資訊，這對 CLR 而言是不透明的。  
  
 CLR 會在內部處理 managed 執行緒內容。 它會 `IHostSecurityManager` 在下列情況下查詢特定進程：  
  
- 在完成項執行緒上，于完成項執行期間。  
  
- 在類別和模組的函式執行期間。  
  
- 在背景工作執行緒上的非同步點上，呼叫 [IHostThreadPoolManager：： QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md) 方法。  
  
- 提供 i/o 完成埠的服務。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IHostSecurityContext 介面](ihostsecuritycontext-interface.md)
- [裝載介面](hosting-interfaces.md)
