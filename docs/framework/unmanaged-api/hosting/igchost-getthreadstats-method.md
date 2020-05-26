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
ms.openlocfilehash: 4a7a2da58e197749d492f24c7a12134508efef57
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805225"
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
 [in、out][COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md)結構的指標，其中包含指定之執行緒的垃圾收集統計資料。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** GCHost .idl，GCHost。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IGCHost 介面](igchost-interface.md)
