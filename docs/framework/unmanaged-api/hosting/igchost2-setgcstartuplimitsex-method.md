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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f92667191cad163998d233e1110365de65c0340c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="igchost2setgcstartuplimitsex-method"></a>IGCHost2::SetGCStartupLimitsEx 方法
層代 0 設定區段的大小和大小上限。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,  
    [in] SIZE_T MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a>參數  
 `SegmentSize`  
 [in]記憶體回收系統所使用的區段大小。  
  
 `MaxGen0Size`  
 [in]層代 0 的大小上限。  
  
## <a name="remarks"></a>備註  
 值，`SetGCStartupLimitsEx`可以指定只在主應用程式啟動之前。 無法在稍後變更這些值。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** GCHost.idl、 GCHost.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IGCHost2 介面](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)
