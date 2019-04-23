---
title: IHostSecurityContext 介面
ms.date: 03/30/2017
api_name:
- IHostSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityContext
helpviewer_keywords:
- IHostSecurityContext interface [.NET Framework hosting]
ms.assetid: 88e2eac0-8ccb-404f-abbc-287d55159842
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d71b7e1265110a70329377ce8ab7430e1943c49
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124020"
---
# <a name="ihostsecuritycontext-interface"></a>IHostSecurityContext 介面
可讓 common language runtime (CLR) 會維護由主機實作的安全性內容資訊。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Capture 方法](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-capture-method.md)|取得的複製品`IHostSecurityContext`呼叫傳回的執行個體[ihostsecuritymanager:: Getsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)。|  
  
## <a name="remarks"></a>備註  
 主機可以控制執行緒權杖的所有程式碼存取 CLR 和使用者程式碼。 它也可以確保完整的安全性內容資訊傳遞到非同步作業或受限制的程式碼存取的字碼指標。 `IHostSecurityContext` 封裝此安全性內容資訊，對執行階段是不透明。 此資訊使用的執行階段擷取`Capture`，並將它移動跨執行緒集區背景工作項目分派、 完成項執行和模組和類別建構函式。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRHostProtectionManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [IHostSecurityManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
