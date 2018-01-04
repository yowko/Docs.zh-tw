---
title: "ICLRRuntimeInfo::IsLoaded 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.IsLoaded
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::IsLoaded
helpviewer_keywords:
- IsLoaded method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoaded method [.NET Framework hosting]
ms.assetid: fdc5a3a7-71ff-4025-99a1-59e4ee0bfe1b
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4f1a83db3a5fc7b5f8b4ad763208fa31ab8f840e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfoisloaded-method"></a>ICLRRuntimeInfo::IsLoaded 方法
指出是否與 common language runtime (CLR) 相關聯[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面載入處理序。 可以載入執行階段，但也沒有開始。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
#### <a name="parameters"></a>參數  
 `hndProcess`  
 [in]處理序控制代碼。  
  
 `pbLoaded`  
 [out]`true` CLR 載入處理序; 否則如果`false`。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_POINTER|`pbLoaded` 為 null。|  
  
## <a name="remarks"></a>備註  
 這個方法是與舊版相容的下列功能和介面：  
  
-   [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)介面 （在.NET Framework 第 1 版裝載 API)。  
  
-   [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)介面 （在.NET Framework 2.0 裝載應用程式開發介面)。  
  
-   Deprecated`CorBindTo*`函式 (請參閱[已被取代的 CLR 裝載函數](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)裝載 API 的.NET Framework 2.0 中)。  
  
 主機可能呼叫其中一個已被取代`CorBindTo*`函式，例如[CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)函式，來具現化特定的 clr 版本。 然後再呼叫主機[iclrmetahost:: Getruntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md)方法並指定相同的版本號碼，才能取得[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面。  
  
 如果主機然後呼叫`IsLoaded`方法在傳回[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面，`pbLoaded`傳回`true`; 否則它會傳回`false`。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [ICLRRuntimeInfo 介面](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [裝載](../../../../docs/framework/unmanaged-api/hosting/index.md)
