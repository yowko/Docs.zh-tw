---
title: IGCHost::GetStats 方法
ms.date: 03/30/2017
api_name:
- IGCHost.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetStats
helpviewer_keywords:
- GetStats method, IGCHost interface [.NET Framework hosting]
- IGCHost::GetStats method [.NET Framework hosting]
ms.assetid: c4ae022c-46ac-4f19-9ddd-09b955f19412
topic_type:
- apiref
ms.openlocfilehash: c86786a34ff236fb57a1ea6bc4d00b9cd5c4a717
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134888"
---
# <a name="igchostgetstats-method"></a>IGCHost::GetStats 方法
取得垃圾收集系統目前狀態的統計資料。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a>參數  
 `pStats`  
 [in、out][COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)結構的指標，其中包含垃圾收集系統目前狀態的統計資料。  
  
## <a name="remarks"></a>備註  
 智慧配置系統可以使用統計資料來協助垃圾收集系統運作。 例如，配置系統可能會決定在檢查統計資料之後，它需要新增更多記憶體或強制集合。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** GCHost .idl，GCHost。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [IGCHost 介面](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
