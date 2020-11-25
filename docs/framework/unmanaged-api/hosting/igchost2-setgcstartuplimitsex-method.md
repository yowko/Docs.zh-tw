---
title: IGCHost2::SetGCStartupLimitsEx 方法
ms.date: 03/30/2017
api_name:
- IGCHost2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2::SetGCStartupLimitsEx
helpviewer_keywords:
- IGCHost2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, IGCHost2 interface [.NET Framework hosting]
ms.assetid: bba941c2-1c57-46d3-bbf5-5fb92700c490
topic_type:
- apiref
ms.openlocfilehash: 4dca62903a123765ceb8bb251b79455ad0e4730a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726804"
---
# <a name="igchost2setgcstartuplimitsex-method"></a>IGCHost2::SetGCStartupLimitsEx 方法

設定層代0的區段大小和大小上限。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,  
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a>參數  

 `SegmentSize`  
 在垃圾收集系統所使用的區段大小。  
  
 `MaxGen0Size`  
 在層代0的大小上限。  
  
## <a name="remarks"></a>備註  

 `SetGCStartupLimitsEx`只有在啟動主機之前，才可以指定所設定的值。 這些值稍後無法變更。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** GCHost .idl、GCHost。h  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IGCHost2 介面](igchost2-interface.md)
