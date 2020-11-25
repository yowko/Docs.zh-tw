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
ms.openlocfilehash: 2530c7fcd63f81b566d6623a533bd8e2af084047
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702156"
---
# <a name="ihostmalloc-interface"></a>IHostMalloc 介面

提供可讓 common language runtime (CLR) 從堆積要求更精細配置的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Alloc 方法](ihostmalloc-alloc-method.md)|要求主機從堆積配置所要求的記憶體數量。|  
|[DebugAlloc 方法](ihostmalloc-debugalloc-method.md)|要求主機從堆積配置所要求的記憶體數量，並進一步追蹤配置記憶體的位置。|  
|[Free 方法](ihostmalloc-free-method.md)|釋放使用方法所配置的記憶體 `Alloc` 。|  
  
## <a name="remarks"></a>備註  

 CLR 會 `IHostMalloc` 呼叫 [IHostMemoryManager：： CreateMalloc](ihostmemorymanager-createmalloc-method.md) 方法，以取得實例的介面指標。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IHostMemoryManager 介面](ihostmemorymanager-interface.md)
- [裝載介面](hosting-interfaces.md)
