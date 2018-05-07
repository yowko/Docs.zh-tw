---
title: GetAppIdAuthority 函式
ms.date: 03/30/2017
api_name:
- GetAppIdAuthority
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- GetAppIdAuthority
helpviewer_keywords:
- GetAppIdAuthority function [.NET Framework fusion]
ms.assetid: 9f968dad-0d09-47fb-bebc-94c39a0d16ad
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 419884cfd4cbcbcdaa999c221b56ee9873a90241
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="getappidauthority-function"></a>GetAppIdAuthority 函式
取得指標[IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)管理應用程式識別與參考索引鍵的執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetAppIdAuthority (  
    [out] IAppIdAuthority **ppIAppIdAuthority  
 );  
```  
  
#### <a name="parameters"></a>參數  
 `ppIAppIdAuthority`  
 [out]傳回`IAppIdAuthority`指標。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Isolation.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IAppIdAuthority 介面](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)  
 [融合全域靜態函式](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
