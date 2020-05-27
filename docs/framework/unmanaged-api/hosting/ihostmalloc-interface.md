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
ms.openlocfilehash: 8f4e1cd7586df7d8e2a577d26f06eaed6b2c8bb7
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804608"
---
# <a name="ihostmalloc-interface"></a>IHostMalloc 介面
提供的方法可讓 common language runtime （CLR）透過主機要求堆積中的精細配置。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Alloc 方法](ihostmalloc-alloc-method.md)|要求主機從堆積配置要求的記憶體數量。|  
|[DebugAlloc 方法](ihostmalloc-debugalloc-method.md)|要求主機從堆積配置要求的記憶體數量，並另外追蹤記憶體的配置位置。|  
|[Free 方法](ihostmalloc-free-method.md)|釋放使用方法所配置的記憶體 `Alloc` 。|  
  
## <a name="remarks"></a>備註  
 CLR 會藉 `IHostMalloc` 由呼叫[IHostMemoryManager：： CreateMalloc](ihostmemorymanager-createmalloc-method.md)方法來取得實例的介面指標。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IHostMemoryManager 介面](ihostmemorymanager-interface.md)
- [裝載介面](hosting-interfaces.md)
