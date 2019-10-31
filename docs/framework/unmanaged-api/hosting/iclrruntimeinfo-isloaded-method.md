---
title: ICLRRuntimeInfo::IsLoaded 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoaded
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoaded
helpviewer_keywords:
- IsLoaded method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoaded method [.NET Framework hosting]
ms.assetid: fdc5a3a7-71ff-4025-99a1-59e4ee0bfe1b
topic_type:
- apiref
ms.openlocfilehash: e0ab16348abbaff00152f2b259ccafdd331174df
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136354"
---
# <a name="iclrruntimeinfoisloaded-method"></a>ICLRRuntimeInfo::IsLoaded 方法
指出與[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面相關聯的 common language RUNTIME （CLR）是否已載入進程中。 您也可以載入執行時間，而不需要啟動。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
## <a name="parameters"></a>參數  
 `hndProcess`  
 在進程的控制碼。  
  
 `pbLoaded`  
 [out] `true` 如果 CLR 已載入進程中，則為，否則，`false`。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_POINTER|`pbLoaded` 為 null。|  
  
## <a name="remarks"></a>備註  
 這個方法與下列函數和介面具有回溯相容性：  
  
- [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)介面（在 .NET Framework 版本1裝載 API 中）。  
  
- [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)介面（在 .NET Framework 2.0 裝載 API 中）。  
  
- 已淘汰的 `CorBindTo*` 函式（請參閱 .NET Framework 2.0 裝載 API 中已[淘汰的 CLR 裝載](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)函式）。  
  
 主機可以呼叫其中一個已被取代的 `CorBindTo*` 函式（例如[CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)函數），以具現化 CLR 的特定版本。 然後主機可以呼叫[ICLRMetaHost：： GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md)方法，並指定相同的版本號碼來取得[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面。  
  
 如果主機接著在傳回的[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面上呼叫 `IsLoaded` 方法，`pbLoaded` 會傳回 `true`;否則，它會傳回 `false`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICLRRuntimeInfo 介面](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [裝載](../../../../docs/framework/unmanaged-api/hosting/index.md)
