---
title: IGCThreadControl::SuspensionEnding 方法
ms.date: 03/30/2017
api_name:
- IGCThreadControl.SuspensionEnding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SuspensionEnding
helpviewer_keywords:
- IGCThreadControl::SuspensionEnding method [.NET Framework hosting]
- SuspensionEnding method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 70814265-c734-4ddc-9502-fe8b28d2b414
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d0986645a8ce4076c27f39f2ae8004ef20bb4bdb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="igcthreadcontrolsuspensionending-method"></a>IGCThreadControl::SuspensionEnding 方法
通知主機執行階段會在記憶體回收或其他暫止後繼續處理執行緒。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
#### <a name="parameters"></a>參數  
 `Generation`  
 [in]其執行記憶體回收層代。  
  
## <a name="remarks"></a>備註  
 請勿重新排程期間的任何執行緒`SuspensionEnding`回呼。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IGCThreadControl 介面](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
