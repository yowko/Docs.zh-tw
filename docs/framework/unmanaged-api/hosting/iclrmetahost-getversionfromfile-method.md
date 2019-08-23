---
title: ICLRMetaHost::GetVersionFromFile 方法
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetVersionFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetVersionFromFile
helpviewer_keywords:
- ICLRMetaHost::GetVersionFromFile method [.NET Framework hosting]
- GetVersionFromFile method [.NET Framework hosting]
ms.assetid: 55bb3eb4-f665-42fc-973c-465567570e82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd5d2e820bd1d733bb4ab968a89174124bc91357
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962931"
---
# <a name="iclrmetahostgetversionfromfile-method"></a>ICLRMetaHost::GetVersionFromFile 方法
取得元件的原始 .NET Framework 編譯版本 (儲存在中繼資料中), 並指定其檔案路徑。 這個方法會取代[GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md)函數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetVersionFromFile (  
    [in] LPCWSTR pwzFilePath,  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBuffer);  
);  
```  
  
## <a name="parameters"></a>參數  
 `pwzFilePath`  
 在完整的元件檔案路徑。  
  
 `pwzbuffer`  
 脫銷儲存在中繼資料中的 .NET Framework 編譯版本, 格式為 "v*A*。*B*[.*X*] "。 *A*、 *B*和*X*是對應至主要版本、次要版本和組建編號的十進位數。 此字串的長度限制為 MAX_PATH。  
  
> [!NOTE]
> 此輸出符合 .NET Framework 版本的目錄名稱, 因為它出現在 C:\Windows\Microsoft.NET\Framework。  
  
 範例值為 "v v1.0.3705"、"v 1.1.4322"、"v 2.0.50727" 和 "v4.0"。*X*", 其中*X*取決於安裝的組建編號。 請注意, 需要 "v" 前置詞。  
  
 `pcchBuffer`  
 [in、out]`pwzbuffer`要避免緩衝區溢位的大小。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|說明|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_POINTER|`pwzbuffer` 或 `pcchBuffer` 為 null。|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|緩衝區太小。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost.h  
  
 **LIBRARY:** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRMetaHost 介面](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [裝載](../../../../docs/framework/unmanaged-api/hosting/index.md)
