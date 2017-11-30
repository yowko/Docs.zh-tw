---
title: "IHostThreadPoolManager 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostThreadPoolManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostThreadPoolManager
helpviewer_keywords: IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: c3a2cd90-7c4e-4374-bb87-b41befb8344f
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2773042c695320ab1e90d4c5d341e2df5f0f778f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ihostthreadpoolmanager-interface"></a>IHostThreadPoolManager 介面
提供方法讓 common language runtime (CLR) 來設定執行緒集區，以及佇列的執行緒集區的工作項目。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|[GetAvailableThreads 方法](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)|取得目前未處理的工作項目之執行緒集區中的執行緒數目。|  
|[GetMaxThreads 方法](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)|執行緒集區中，同時取得主機維護執行緒的數目上限。|  
|[GetMinThreads 方法](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)|取得主機維護的閒置執行緒數目最小要求的頁數。|  
|[QueueUserWorkItem 方法](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)|對於執行，函式，並提供物件，其中包含要由函式使用的資料。|  
|[SetMaxThreads 方法](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)|設定主應用程式可以維護執行緒集區中的執行緒的數目上限。|  
|[SetMinThreads 方法](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)|預期的要求中設定主應用程式必須維護的閒置執行緒的最小數目。|  
  
## <a name="remarks"></a>備註  
 主機不需要使用的呼叫中指定的值，設定執行緒集區`SetMaxThreads`和`SetMinThreads`方法。 在此情況下，主應用程式應該傳回 E_NOTIMPL 的 HRESULT 值，這些方法。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading>  
 <xref:System.Threading.ThreadPool>  
 [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
