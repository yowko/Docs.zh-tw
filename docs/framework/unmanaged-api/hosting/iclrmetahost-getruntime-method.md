---
title: ICLRMetaHost::GetRuntime 方法
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetRuntime
helpviewer_keywords:
- GetRuntime method [.NET Framework hosting]
- ICLRMetaHost::GetRuntime method [.NET Framework hosting]
ms.assetid: a10749f1-ab91-47cf-982f-d8ccd2e81bd2
topic_type:
- apiref
ms.openlocfilehash: 093fa64a7d51e0c2fdc304d2bb4f1c9f7b03e2ec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730405"
---
# <a name="iclrmetahostgetruntime-method"></a>ICLRMetaHost::GetRuntime 方法

取得 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 介面，這個介面會對應至特定版本的 common language RUNTIME (CLR) 。 這個方法會取代搭配[STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md)旗標使用的[CorBindToRuntimeEx](corbindtoruntimeex-function.md)函數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in] REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
## <a name="parameters"></a>參數  

 `pwzVersion`  
 在儲存在中繼資料中的 .NET Framework 編譯版本，格式為 "v *A*。*B*[.*X*]」。 *A*、 *B* 和 *X* 是對應至主要版本、次要版本和組建編號的十進位數。  
  
> [!NOTE]
> 此參數必須符合 .NET Framework 版本的目錄名稱，因為它會出現在 C:\Windows\Microsoft.NET\Framework 或 C:\Windows\Microsoft.NET\Framework64. 底下  
  
 範例值為 "v v1.0.3705"、"v 1.1.4322"、"v 2.0.50727" 和 "v 4.0。*X*"，其中 *X* 取決於已安裝的組建編號。 需要 "v" 前置詞。  
  
 `riid`  
 在所需介面的識別碼。 目前，此參數唯一有效的值為 IID_ICLRRuntimeInfo。  
  
 `ppRuntime`  
 擴展 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 介面的指標，該介面對應至要求的執行時間。  
  
## <a name="return-value"></a>傳回值  

 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_POINTER|`pwzVersion` 或 `ppRuntime` 為 null。|  
  
## <a name="remarks"></a>備註  

 這個方法會與舊版介面一致地互動，例如 [ICorRuntimeHost](icorruntimehost-interface.md) 介面和舊版函式，例如已被取代的函式 `CorBindTo*` (在 .NET FRAMEWORK 2.0 裝載 API) 中看到已被 [取代的 CLR 裝載](deprecated-clr-hosting-functions.md) 函式。 也就是說，新的 API 可以看到使用舊版 API 載入的執行時間，而且舊版 API 可以看到以新 API 載入的執行時間。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRMetaHost 介面](iclrmetahost-interface.md)
- [已被取代的 CLR 裝載介面和 Coclass](deprecated-clr-hosting-interfaces-and-coclasses.md)
- [CLR 裝載介面](clr-hosting-interfaces.md)
- [已被取代的 CLR 裝載函式](deprecated-clr-hosting-functions.md)
- [裝載](index.md)
