---
title: "IHostMalloc 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMAlloc
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMAlloc
helpviewer_keywords: IHostMAlloc interface [.NET Framework hosting]
ms.assetid: e3c6643b-6fc7-4a99-959d-4b7b4e63fdee
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f788456065a5508441b9fec38ad4a7f531f9f303
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmalloc-interface"></a>IHostMalloc 介面
提供方法讓 common language runtime (CLR) 會從透過主機堆積要求更細緻的配置。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|[Alloc 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|要求主機從堆積配置要求的記憶體數量。|  
|[DebugAlloc 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|要求主機從堆積配置要求的記憶體數量，並額外追蹤記憶體配置的位置。|  
|[Free 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|釋放記憶體取消配置使用`Alloc`方法。|  
  
## <a name="remarks"></a>備註  
 CLR 取得的介面指標`IHostMalloc`藉由呼叫的執行個體[ihostmemorymanager:: Createmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IHostMemoryManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
