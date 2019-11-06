---
title: IHostMalloc 介面
ms.date: 03/30/2017
api_name:
- IHostMAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc
helpviewer_keywords:
- IHostMAlloc interface [.NET Framework hosting]
ms.assetid: e3c6643b-6fc7-4a99-959d-4b7b4e63fdee
topic_type:
- apiref
ms.openlocfilehash: abc6cca185b318be016f92ac8c97d21f7af5940a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136770"
---
# <a name="ihostmalloc-interface"></a>IHostMalloc 介面
提供的方法可讓 common language runtime （CLR）透過主機要求堆積中的精細配置。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Alloc 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|要求主機從堆積配置要求的記憶體數量。|  
|[DebugAlloc 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|要求主機從堆積配置要求的記憶體數量，並另外追蹤記憶體的配置位置。|  
|[Free 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|釋放使用 `Alloc` 方法所配置的記憶體。|  
  
## <a name="remarks"></a>備註  
 CLR 會藉由呼叫[IHostMemoryManager：： CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)方法，取得 `IHostMalloc` 實例的介面指標。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [IHostMemoryManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
