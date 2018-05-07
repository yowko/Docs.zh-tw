---
title: ICLRRuntimeInfo::GetRuntimeDirectory 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetRuntimeDirectory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetRuntimeDirectory
helpviewer_keywords:
- GetRuntimeDirectory method [.NET Framework hosting]
- ICLRRuntimeInfo::GetRuntimeDirectory method [.NET Framework hosting]
ms.assetid: 4401546e-4d48-453f-a1fb-b2ebda54df5c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f366e736c90ffd8cf588af3a6e5f6240426b9980
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="iclrruntimeinfogetruntimedirectory-method"></a>ICLRRuntimeInfo::GetRuntimeDirectory 方法
取得 common language runtime (CLR) 此介面相關聯的安裝目錄。  
  
 這個方法會取代[GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) .NET framework 2.0、 3.0 和 3.5 中所提供的函式。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetRuntimeDirectory(  
[out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
[in, out]  DWORD *pcchBuffer);  
```  
  
#### <a name="parameters"></a>參數  
 `pwzBuffer`  
 [out]傳回 CLR 安裝目錄。 安裝路徑是完整名稱。例如，"c:\windows\microsoft.net\framework\v1.0.3705\\"。  
  
 `pchBuffer`  
 [in、 out]指定的大小`pwzBuffer`以避免緩衝區滿溢。 如果`pwzBuffer`為 null，`pchBuffer`傳回的所需的大小`pwzBuffer`。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_POINTER|`pwzBuffer` 或 `pchBuffer` 為 null。|  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICLRRuntimeInfo 介面](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [裝載](../../../../docs/framework/unmanaged-api/hosting/index.md)
