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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f453867f6b46265fdbf567b4374ddc64b4efe84
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563889"
---
# <a name="corgcthreadstats-structure"></a>COR_GC_THREAD_STATS 結構
包含有關記憶體回收的每個執行緒統計資料。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;   
    ULONG      Flags;   
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`PerThreadAllocation`|目前與相關聯的執行緒上配置的記憶體位元組數目`COR_GC_THREAD_STATS`執行個體。 每次在層代 0 記憶體回收時清除這個數字為零。|  
|`Flags`|位元組數目提升至更高的層代最新的回收。|  
  
## <a name="remarks"></a>備註  
 [Iclrtask:: Getmemstats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md)會採用輸出參數的型別`COR_GC_THREAD_STATS`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** GCHost.idl  
  
 **程式庫：** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [裝載結構](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [IHostTask 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
