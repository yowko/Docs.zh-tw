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
ms.openlocfilehash: 8aef78c7cf70e6b2d97af9c47d57908b86729ff7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122076"
---
# <a name="ihostthreadpoolmanager-interface"></a>IHostThreadPoolManager 介面
提供的方法可讓 common language runtime （CLR）設定執行緒集區，並將工作專案排入執行緒集區佇列。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetAvailableThreads 方法](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)|取得執行緒集區中目前未處理工作專案的執行緒數目。|  
|[GetMaxThreads 方法](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)|取得主機線上程集區中同時維護的執行緒數目上限。|  
|[GetMinThreads 方法](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)|取得主機在預期要求中維持的最小閒置執行緒數目。|  
|[QueueUserWorkItem 方法](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)|將函式排入佇列以便執行，並提供包含函數所要使用之資料的物件。|  
|[SetMaxThreads 方法](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)|設定主機可以線上程集區中維護的執行緒數目上限。|  
|[SetMinThreads 方法](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)|設定主機必須在要求中維持的最小閒置執行緒數目。|  
  
## <a name="remarks"></a>備註  
 主機不需要使用對 `SetMaxThreads` 和 `SetMinThreads` 方法的呼叫中指定的值來設定執行緒集區。 在此情況下，主機應該會從這些方法傳回 E_NOTIMPL 的 HRESULT 值。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- <xref:System.Threading>
- <xref:System.Threading.ThreadPool>
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
