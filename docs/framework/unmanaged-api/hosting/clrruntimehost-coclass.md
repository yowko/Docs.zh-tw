---
title: CLRRuntimeHost Coclass
ms.date: 03/30/2017
api_name:
- CLRRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CLRRuntimeHost
helpviewer_keywords:
- CLRRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 2ac9cbf5-8a2d-4e4f-8831-0dad8ef0a897
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 841b05ca1037d82046820554878d883f94687d34
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779142"
---
# <a name="clrruntimehost-coclass"></a>CLRRuntimeHost Coclass
提供介面來管理執行程式碼執行階段。  
  
## <a name="syntax"></a>語法  
  
```cpp  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a>介面  
  
|介面|描述|  
|---------------|-----------------|  
|[ICLRRuntimeHost 介面](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)|提供方法來控制執行階段應用程式的執行。|  
|[ICLRValidator 介面](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)|提供用於驗證的可攜式執行檔的影像及詳細的報告驗證錯誤的方法。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.idl  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載 Coclass](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
