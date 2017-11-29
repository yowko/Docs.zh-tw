---
title: "ICLRMetaHostPolicy 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHostPolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHostPolicy
helpviewer_keywords: ICLRMetaHostPolicy interface [.NET Framework hosting]
ms.assetid: 1bdeccb6-0698-4c97-ad69-eae2b69e59f1
topic_type: apiref
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6b8cbe1d397e1214cfa4d3f4cbc3d6cdf2d3ccd5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostpolicy-interface"></a>ICLRMetaHostPolicy 介面
提供[GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)方法，讓指標回到通用的 language runtime (CLR) 介面，根據原則的條件，管理組件、 版本和組態檔。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|[GetRequestedRuntime 方法](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)|提供的慣用的 CLR 介面根據原則的條件，管理組件、 版本和組態檔。|  
  
## <a name="remarks"></a>備註  
 您可以取得此介面的參考，藉由呼叫[CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md)函式，如下列程式碼所示：  
  
```  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
>  這個介面不實際上不會載入或啟用 CLR，但只會傳回可用的版本會安裝或載入為基礎的慣用的 CLR 版本。  
  
 [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]裝載 API，將合併原則，讓主機有特定的需求可能會使用基本功能而不會產生非預期的負面影響。 例如，許多 MSCorEE.dll 匯出會繫結至特定的 CLR，雖然方法可能會以邏輯方式需要它。 [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md)列舉型別提供通用於大多數的主控件的繫結原則。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [在.NET Framework 4 和 4.5 加入的 CLR 裝載介面](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [裝載](../../../../docs/framework/unmanaged-api/hosting/index.md)
