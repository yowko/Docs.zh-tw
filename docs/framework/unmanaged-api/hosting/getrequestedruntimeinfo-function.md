---
title: GetRequestedRuntimeInfo 函式
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeInfo
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeInfo
helpviewer_keywords:
- GetRequestedRuntimeInfo function [.NET Framework hosting]
ms.assetid: 0dfd7cdc-c116-4e25-b56a-ac7b0378c942
topic_type:
- apiref
ms.openlocfilehash: cd1d9e768698115bee22e35699b044e0c3526d2d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136316"
---
# <a name="getrequestedruntimeinfo-function"></a>GetRequestedRuntimeInfo 函式
取得應用程式所要求之 common language runtime （CLR）的版本和目錄資訊。  
  
 此函式在 .NET Framework 4 中已被取代。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetRequestedRuntimeInfo (  
    [in]  LPCWSTR  pExe,   
    [in]  LPCWSTR  pwszVersion,   
    [in]  LPCWSTR  pConfigurationFile,   
    [in]  DWORD    startupFlags,   
    [in]  DWORD    runtimeInfoFlags,   
    [out] LPWSTR   pDirectory,   
    [in]  DWORD    dwDirectory,   
    [out] DWORD   *dwDirectoryLength,   
    [out] LPWSTR   pVersion,   
    [in]  DWORD    cchBuffer,   
    [out] DWORD   *dwlength  
);  
```  
  
## <a name="parameters"></a>參數  
 `pExe`  
 在應用程式的名稱。  
  
 `pwszVersion`  
 在指定執行時間版本號碼的字串。  
  
 `pConfigurationFile`  
 在與 `pExe`相關聯之設定檔的名稱。  
  
 `startupFlags`  
 在一或多個[STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)列舉值。  
  
 `runtimeInfoFlags`  
 在一或多個[RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md)列舉值。  
  
 `pDirectory`  
 脫銷一個緩衝區，其中包含成功完成時，執行時間的目錄路徑。  
  
 `dwDirectory`  
 在目錄緩衝區的長度。  
  
 `dwDirectoryLength`  
 脫銷目錄路徑字串長度的指標。  
  
 `pVersion`  
 脫銷包含成功完成時，執行時間版本號碼的緩衝區。  
  
 `cchBuffer`  
 在版本字串緩衝區的長度。  
  
 `dwlength`  
 脫銷版本字串長度的指標。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回標準元件物件模型（COM）錯誤碼（如 Winerror.h 中所定義），以及下列值。  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|S_OK|已成功完成命令。|  
|ERROR_INSUFFICIENT_BUFFER|目錄緩衝區不夠大，無法儲存目錄路徑。<br /><br /> -或-<br /><br /> 版本緩衝區不夠大，無法儲存版本字串。|  
  
## <a name="remarks"></a>備註  
 `GetRequestedRuntimeInfo` 方法會傳回載入進程中之版本的相關執行時間資訊，這不一定是電腦上所安裝的最新版本。  
  
 在 .NET Framework 版本2.0 中，您可以使用 `GetRequestedRuntimeInfo` 方法來取得最新已安裝版本的相關資訊，如下所示：  
  
- 將 `pExe`、`pwszVersion`和 `pConfigurationFile` 參數指定為 null。  
  
- 在 `RUNTIME_INFO_FLAGS` 列舉中指定 `runtimeInfoFlags` 參數的 RUNTIME_INFO_UPGRADE_VERSION 旗標。  
  
 在下列情況下，`GetRequestedRuntimeInfo` 方法不會傳回最新的 CLR 版本：  
  
- 指定載入特定 CLR 版本的應用程式佈建檔已存在。 請注意，即使您為 `pConfigurationFile` 參數指定 null，.NET Framework 還是會使用設定檔。  
  
- 呼叫[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)方法時，指定了較早的 CLR 版本。  
  
- 已針對舊版 CLR 版本編譯的應用程式目前正在執行。  
  
 針對 `runtimeInfoFlags` 參數，您一次只能指定一個 `RUNTIME_INFO_FLAGS` 列舉的架構常數：  
  
- RUNTIME_INFO_REQUEST_IA64  
  
- RUNTIME_INFO_REQUEST_AMD64  
  
- RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [GetRequestedRuntimeVersion 函式](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [GetVersionFromProcess 函式](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
