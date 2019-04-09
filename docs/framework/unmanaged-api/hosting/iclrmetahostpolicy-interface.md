---
title: ICLRMetaHostPolicy 介面
ms.date: 03/30/2017
api_name:
- ICLRMetaHostPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHostPolicy
helpviewer_keywords:
- ICLRMetaHostPolicy interface [.NET Framework hosting]
ms.assetid: 1bdeccb6-0698-4c97-ad69-eae2b69e59f1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 93507ac72b79210dc3a267fea39a6a7b2874916a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188561"
---
# <a name="iclrmetahostpolicy-interface"></a>ICLRMetaHostPolicy 介面
提供[GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)方法，這個方法會傳回根據原則準則的通用語言執行平台 (CLR) 介面的指標，管理組件、 版本和組態檔。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetRequestedRuntime 方法](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)|提供的慣用的 CLR 介面根據原則準則、 管理組件、 版本和組態檔。|  
  
## <a name="remarks"></a>備註  
 您可以取得此介面的參考，藉由呼叫[CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md)函式，如下列程式碼所示：  
  
```  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
>  此介面實際上不會不會載入或啟用 CLR，但只會傳回可用的版本安裝或載入為基礎的慣用的 CLR 版本。  
  
 [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]裝載 API 合併原則，好讓主機的特定需求可能會使用基本功能而不會產生非預期的負面影響。 比方說，許多 MSCorEE.dll 匯出會繫結至特定的 CLR，雖然方法可能會以邏輯方式需要它。 [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md)列舉型別提供通用於大部分的主控件的繫結原則。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [.NET Framework 4 和 4.5 中新增的 CLR 裝載介面](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [裝載](../../../../docs/framework/unmanaged-api/hosting/index.md)
