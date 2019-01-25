---
title: ICLRMetaHost::ExitProcess 方法
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.ExitProcess
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::ExitProcess
helpviewer_keywords:
- ICLRMetaHost::ExitProcess method [.NET Framework hosting]
- ExitProcess method, ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: b4df98cc-4e4e-407b-b8f4-e0076afef3a4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bbf3c00eafe47556c6b46e1acb687a19df5a2b28
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601750"
---
# <a name="iclrmetahostexitprocess-method"></a>ICLRMetaHost::ExitProcess 方法
嘗試先關閉所有已載入的執行階段依正常程序，然後終止處理序。 會取代[CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)函式。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
#### <a name="parameters"></a>參數  
 `iExitCode`  
 [in]處理序結束代碼。  
  
## <a name="return-value"></a>傳回值  
 這個方法永遠不會傳回，因此它的傳回值會是未定義。  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost.h  
  
 **程式庫：** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [ICLRMetaHost 介面](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [裝載](../../../../docs/framework/unmanaged-api/hosting/index.md)
