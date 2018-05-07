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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3e0d6f68ffa5280d4616d4fa4ac60b4cb86f6a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="igchostgetstats-method"></a>IGCHost::GetStats 方法
取得目前的記憶體回收系統狀態的統計資料。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pStats`  
 [in、 out]指標[COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)結構，包含記憶體回收系統的目前狀態的統計資料。  
  
## <a name="remarks"></a>備註  
 統計資料可供智慧型配置系統，以協助記憶體回收系統運作。 例如，配置系統可能決定檢視的統計資料，以便增加更多記憶體，或強制回收之後。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** GCHost.idl、 GCHost.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IGCHost 介面](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
