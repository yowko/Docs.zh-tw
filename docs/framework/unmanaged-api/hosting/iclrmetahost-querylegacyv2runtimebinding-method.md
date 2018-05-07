---
title: ICLRMetaHost::QueryLegacyV2RuntimeBinding 方法
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.RequestRuntimeLoadedNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::QueryLegacyV2RuntimeBinding
helpviewer_keywords:
- QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
- ICLRMetaHost::QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
ms.assetid: 9929817e-acc9-40b7-960c-598664e04b60
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1664c47e580730fb0000465f9010e024c64fec2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a>ICLRMetaHost::QueryLegacyV2RuntimeBinding 方法
傳回代表執行階段的舊版啟用原則已繫結，例如，使用的介面`useLegacyV2RuntimeActivationPolicy`屬性[\<啟動 > 項目](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)組態檔項目，直接使用舊版啟用應用程式開發介面，或藉由呼叫[iclrruntimeinfo:: Bindaslegacyv2runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
#### <a name="parameters"></a>參數  
 `riid`  
 [in]此參數唯一有效的值是的 Required.Currently `IID_ICLRRuntimeInfo`。  
  
 `ppUnk`  
 [out] 必要項。 此方法傳回時，包含指標[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)表示已繫結到舊版啟用原則的執行階段介面。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|這個方法順利完成，且傳回已繫結到舊版啟用原則的執行階段。|  
|S_FALSE|這個方法順利完成，但是尚未已繫結舊版執行階段。|  
|E_NOINTERFACE|此方法找到的執行階段已繫結到舊版啟用原則，但該執行階段不支援 `riid`。|  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICLRMetaHost 介面](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [裝載](../../../../docs/framework/unmanaged-api/hosting/index.md)
