---
title: ICLRRuntimeInfo::GetVersionString 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetVersionString
helpviewer_keywords:
- ICLRRuntimeInfo::GetVersionString method [.NET Framework hosting]
- GetVersionString method, ICLRRuntimeInfo interface [.NET Framework hosting]
ms.assetid: 98b097ef-2276-4dd9-8551-b03c972e8179
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c80b85171ac9dab270a267cf2dd33a9f1c23d60
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650303"
---
# <a name="iclrruntimeinfogetversionstring-method"></a>ICLRRuntimeInfo::GetVersionString 方法
取得 common language runtime (CLR) 版本資訊與相關給定[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面。  
  
 這個方法會取代以下函數：  
  
- [GetRequestedRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
  
- [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetVersionString(  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a>參數  
 `pwzBuffer`  
 [out].NET Framework 編譯版本，格式為"v*A*。*B*[。*X*]"。 *A*， *B*，以及*X*是對應至主要版本、 次要版本和組建編號的十進位數字。 *X*是選擇性的。 如果*X*已不存在，沒有任何結尾的句點。  
  
> [!NOTE]
>  C:\Windows\Microsoft.NET\Framework 底下所顯示的樣子，這個參數必須符合.NET Framework 版本中，目錄名稱。  
  
 範例值為"v1.0.3705"、"v1.1.4322"、"v2.0.50727"和"v4.0。*x*"，其中*x*取決於已安裝的組建編號。 請注意，"v"前置詞是必要的。  
  
 `pchBuffer`  
 [in、 out]指定的大小`pwzBuffer`以避免緩衝區滿溢。 如果`pwzBuffer`已`null`，`pchBuffer`傳回的所需的大小`pwzBuffer`以便預先配置。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_POINTER|`pwzBuffer` 或 `pchBuffer` 為 null。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRRuntimeInfo 介面](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [.NET Framework 4 和 4.5 中新增的 CLR 裝載介面](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [裝載](../../../../docs/framework/unmanaged-api/hosting/index.md)
