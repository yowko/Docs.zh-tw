---
title: ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList 方法
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList.IsStringAssemblyReferenceInList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList method [.NET Framework hosting]
- IsStringAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: e6121cc3-2f11-42c7-bdae-47808581ff71
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad7230731775cbc56dd0f1eaed72df19512d3733
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="iclrassemblyreferencelistisstringassemblyreferenceinlist-method"></a>ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList 方法
取得值，指出所提供的名稱是否符合清單中的組件的名稱。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT IsStringAssemblyReferenceInList (  
    [in] LPCWSTR pwzAssemblyName  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pwzAssemblyName`  
 [in]要搜尋的組件名稱。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|字串會出現在清單中。|  
|S_FALSE|字串不在清單中。|  
|E_FAIL|發生未知的嚴重失敗。 方法會傳回 E_FAIL 之後，就不再可在處理程序中使用通用語言執行平台。 裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICLRAssemblyIdentityManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [ICLRAssemblyReferenceList 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [IHostAssemblyManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [IHostAssemblyStore 介面](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
