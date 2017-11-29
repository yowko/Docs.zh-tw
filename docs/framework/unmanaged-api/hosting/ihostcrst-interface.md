---
title: "IHostCrst 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostCrst
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostCrst
helpviewer_keywords: IHostCrst interface [.NET Framework hosting]
ms.assetid: ac298ebd-0815-47e4-a823-30b31baab903
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 59485d7a642ba8b3233d5d077062e89fb2ac9b14
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ihostcrst-interface"></a>IHostCrst 介面
可做為主機的關鍵區段的執行緒的表示法。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|[Enter 方法](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-enter-method.md)|進入重要區段。|  
|[Leave 方法](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-leave-method.md)|離開關鍵區段。|  
|[SetSpinCount 方法](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-setspincount-method.md)|設定關鍵區段的微調計數。|  
|[TryEnter 方法](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-tryenter-method.md)|嘗試立即進入重要區段，並報告成功或失敗。|  
  
## <a name="remarks"></a>備註  
 `IHostCrst`可讓 common language runtime (CLR) 直接通訊的關鍵區段中，主機的表示法，而不是使用 Win32 函式，例如`EnterCriticalSection`或`LeaveCriticalSection`。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICLRSyncManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [IHostSyncManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
