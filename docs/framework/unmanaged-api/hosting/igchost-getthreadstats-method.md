---
title: IGCHost::GetThreadStats 方法
ms.date: 03/30/2017
api_name:
- IGCHost.GetThreadStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetThreadStats
helpviewer_keywords:
- IGCHost::GetThreadStats method [.NET Framework hosting]
- GetThreadStats method [.NET Framework hosting]
ms.assetid: 826baa9b-9218-4736-a509-7ab193b125a0
topic_type:
- apiref
ms.openlocfilehash: 36eeb7ed4f80979ef2edb930e65963a1db0c894f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134910"
---
# <a name="igchostgetthreadstats-method"></a>IGCHost::GetThreadStats 方法
取得垃圾收集的每個執行緒統計資料。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetThreadStats (  
    [in] DWORD *pFiberCookie,  
    [in, out] COR_GC_THREAD_STATS *pStats  
);  
```  
  
## <a name="parameters"></a>參數  
 `pFiberCookie`  
 在光纖 cookie 的指標，指定要取得其統計資料的執行緒。  
  
 `pStats`  
 [in、out][COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md)結構的指標，其中包含指定之執行緒的垃圾收集統計資料。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** GCHost .idl，GCHost。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [IGCHost 介面](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
