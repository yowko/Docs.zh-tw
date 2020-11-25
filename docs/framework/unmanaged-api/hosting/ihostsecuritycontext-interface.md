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
ms.openlocfilehash: aafaa1d648396ddaa76193fa15cf7f74394777a9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724802"
---
# <a name="ihostsecuritycontext-interface"></a>IHostSecurityContext 介面

允許 common language runtime (CLR) 維護主機所執行的安全性內容資訊。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Capture 方法](ihostsecuritycontext-capture-method.md)|取得 `IHostSecurityContext` 從呼叫 [IHostSecurityManager：： GetSecurityCoNtext](ihostsecuritymanager-getsecuritycontext-method.md)所傳回之實例的複本。|  
  
## <a name="remarks"></a>備註  

 主機可以透過 CLR 和使用者程式碼控制執行緒權杖的所有程式碼存取。 它也可以確保在非同步作業或具有限制程式碼存取的程式碼點之間傳遞完整的安全性內容資訊。 `IHostSecurityContext` 封裝此安全性內容資訊，這對執行時間而言是不透明的。 執行時間會使用來捕捉此資訊 `Capture` ，並將其移動到執行緒集區背景工作專案分派、完成項執行，以及模組和類別的函式。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRHostProtectionManager 介面](iclrhostprotectionmanager-interface.md)
- [IHostSecurityManager 介面](ihostsecuritymanager-interface.md)
- [裝載介面](hosting-interfaces.md)
