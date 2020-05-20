---
title: ICLRRuntimeInfo::BindAsLegacyV2Runtime 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.BindAsLegacyV2Runtime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime
helpviewer_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime method [.NET Framework hosting]
- BindAsLegacyV2Runtime method [.NET Framework hosting]
ms.assetid: 65fd55ac-4a24-4479-9384-a2e8013bfb2b
topic_type:
- apiref
ms.openlocfilehash: 4390f379e5092cc59d123631f5e6d8da82e2bd7f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703899"
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a>ICLRRuntimeInfo::BindAsLegacyV2Runtime 方法
將目前的執行時間系結至所有舊版 common language runtime （CLR）第2版啟用原則決策。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 Hresult：  
  
|HRESULT|說明|  
|-------------|-----------------|  
|S_OK|任一系結成功，或此執行時間已系結為舊版 CLR 版本2啟用原則執行時間。|  
|CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND|不同的執行時間已系結至舊版 CLR 第2版啟用原則。|  
  
## <a name="remarks"></a>備註  
 如果目前的執行時間已系結至所有舊版 CLR 版本2啟用原則決策（例如，藉由在 `useLegacyV2RuntimeActivationPolicy` 設定檔中使用[ \< 啟動>](../../configure-apps/file-schema/startup/startup-element.md)專案上的屬性），則這個方法不會傳回錯誤結果，而是會 S_OK 結果，就像方法已成功系結舊版啟用原則一樣。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRRuntimeInfo 介面](iclrruntimeinfo-interface.md)
- [裝載介面](hosting-interfaces.md)
- [裝載](index.md)
- [\<啟動> 元素](../../configure-apps/file-schema/startup/startup-element.md)
