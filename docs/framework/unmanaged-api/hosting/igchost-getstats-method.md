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
ms.openlocfilehash: 67668aa7ff9faf035a047e485a8a3c8a451f45b9
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805242"
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
 [in、out][COR_GC_STATS](cor-gc-stats-structure.md)結構的指標，其中包含垃圾收集系統目前狀態的統計資料。  
  
## <a name="remarks"></a>備註  
 智慧配置系統可以使用統計資料來協助垃圾收集系統運作。 例如，配置系統可能會決定在檢查統計資料之後，它需要新增更多記憶體或強制集合。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** GCHost .idl，GCHost。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IGCHost 介面](igchost-interface.md)
