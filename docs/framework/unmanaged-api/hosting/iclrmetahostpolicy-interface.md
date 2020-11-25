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
ms.openlocfilehash: 515b73b019c683bd3e5aa3b895ee5623e75e4ad0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707603"
---
# <a name="iclrmetahostpolicy-interface"></a>ICLRMetaHostPolicy 介面

提供 [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) 方法，此方法會根據原則準則、managed 元件、版本和設定檔案，將指標傳回給 common language RUNTIME (CLR) 介面。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetRequestedRuntime 方法](iclrmetahostpolicy-getrequestedruntime-method.md)|根據原則準則、managed 元件、版本和設定檔提供慣用的 CLR 介面。|  
  
## <a name="remarks"></a>備註  

 您可以藉由呼叫 [CLRCreateInstance](clrcreateinstance-function.md) 函數來取得此介面的參考，如下列程式碼所示：  
  
```cpp  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
> 這個介面不會實際載入或啟用 CLR，而只會根據已安裝或載入的可用版本傳回慣用的 CLR 版本。  
  
 .NET Framework 4 裝載 API 會合並原則，讓具有特定需求的主機可以使用基本功能，而不會產生非預期的懲罰。 例如，許多 MSCorEE.dll 的匯出都會系結至特定的 CLR，雖然方法可能不會以邏輯方式要求它。 [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md)列舉會提供大多數主機通用的系結原則。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [.NET Framework 4 和 4.5 中新增的 CLR 裝載介面](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [裝載介面](hosting-interfaces.md)
- [裝載](index.md)
