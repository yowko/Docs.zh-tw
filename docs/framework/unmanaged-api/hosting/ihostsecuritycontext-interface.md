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
ms.openlocfilehash: 993d16818b25dfefe1f53c7afd06bc9857d9eb24
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121527"
---
# <a name="ihostsecuritycontext-interface"></a>IHostSecurityContext 介面
允許 common language runtime （CLR）維護主機所執行的安全性內容資訊。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Capture 方法](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-capture-method.md)|取得從[IHostSecurityManager：： GetSecurityCoNtext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)的呼叫所傳回之 `IHostSecurityContext` 實例的複製。|  
  
## <a name="remarks"></a>備註  
 主機可以同時控制 CLR 和使用者程式碼對執行緒標記的所有程式碼存取。 它也可以確保以限制的程式碼存取，在非同步作業或程式碼點之間傳遞完整的安全性內容資訊。 `IHostSecurityContext` 封裝此安全性內容資訊，這對執行時間而言是不透明的。 執行時間會使用 `Capture`來捕捉這項資訊，並將它移到執行緒集區的背景工作專案分派、完成項執行，以及模組和類別的函式。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICLRHostProtectionManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [IHostSecurityManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
