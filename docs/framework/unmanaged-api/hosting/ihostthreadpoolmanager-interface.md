---
title: IHostThreadPoolManager 介面
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager
helpviewer_keywords:
- IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: c3a2cd90-7c4e-4374-bb87-b41befb8344f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7fc0a271a9c62406d2942f387a5458e21211116
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522722"
---
# <a name="ihostthreadpoolmanager-interface"></a>IHostThreadPoolManager 介面
提供方法，啟用 common language runtime (CLR) 來設定執行緒集區，以及執行緒集區的工作項目佇列。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetAvailableThreads 方法](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)|取得目前未處理的工作項目之執行緒集區中的執行緒數目。|  
|[GetMaxThreads 方法](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)|執行緒集區中，同時取得主機維護執行緒的數目上限。|  
|[GetMinThreads 方法](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)|預期的要求中取得主控件保留的閒置執行緒的數目下限。|  
|[QueueUserWorkItem 方法](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)|函式，以執行排入佇列，並提供包含要使用的函式資料的物件。|  
|[SetMaxThreads 方法](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)|設定主應用程式可以維護執行緒集區中的執行緒最大數目。|  
|[SetMinThreads 方法](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)|預期的要求中設定主應用程式必須維護的閒置執行緒的數目下限。|  
  
## <a name="remarks"></a>備註  
 主應用程式不需要使用的呼叫中指定的值，設定執行緒集區`SetMaxThreads`和`SetMinThreads`方法。 在此情況下，主應用程式應該從這些方法會傳回 E_NOTIMPL HRESULT 值。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Threading>
- <xref:System.Threading.ThreadPool>
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
