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
ms.openlocfilehash: f6e25bfe11880730f6f447ccc0406d716d185624
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501491"
---
# <a name="ihostsecuritycontext-interface"></a>IHostSecurityContext 介面
允許 common language runtime （CLR）維護主機所執行的安全性內容資訊。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Capture 方法](ihostsecuritycontext-capture-method.md)|取得 `IHostSecurityContext` 從呼叫[IHostSecurityManager：： GetSecurityCoNtext](ihostsecuritymanager-getsecuritycontext-method.md)傳回之實例的複本。|  
  
## <a name="remarks"></a>備註  
 主機可以同時控制 CLR 和使用者程式碼對執行緒標記的所有程式碼存取。 它也可以確保以限制的程式碼存取，在非同步作業或程式碼點之間傳遞完整的安全性內容資訊。 `IHostSecurityContext`封裝此安全性內容資訊，這對執行時間而言是不透明的。 執行時間會使用來捕捉這項資訊 `Capture` ，並將它移到執行緒集區的背景工作專案分派、完成項執行，以及模組和類別的函式。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRHostProtectionManager 介面](iclrhostprotectionmanager-interface.md)
- [IHostSecurityManager 介面](ihostsecuritymanager-interface.md)
- [裝載介面](hosting-interfaces.md)
