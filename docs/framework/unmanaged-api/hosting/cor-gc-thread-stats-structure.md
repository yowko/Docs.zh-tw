---
title: COR_GC_THREAD_STATS 結構
ms.date: 03/30/2017
api_name:
- COR_GC_THREAD_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS
helpviewer_keywords:
- COR_GC_THREAD_STATS structure [.NET Framework hosting]
ms.assetid: 01f9a59b-7679-4d42-9ced-4a8981625c3d
topic_type:
- apiref
ms.openlocfilehash: 64e0c466edcd8863244e6ed184c18422b5f66875
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178273"
---
# <a name="cor_gc_thread_stats-structure"></a>COR_GC_THREAD_STATS 結構
包含與垃圾回收相關的每個執行緒統計資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;
    ULONG      Flags;
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`PerThreadAllocation`|在與當前`COR_GC_THREAD_STATS`實例關聯的執行緒上分配的記憶體位元組數。 每次發生生成零垃圾回收時，此數位將清除為零。|  
|`Flags`|在最近的垃圾回收中提升為更高一代的位元組數。|  
  
## <a name="remarks"></a>備註  
 [ICLR任務：getMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md)採用類型的`COR_GC_THREAD_STATS`輸出參數。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** GCHost.idl  
  
 **庫：** 作為資源包含在 MSCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載結構](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [IHostTask 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
