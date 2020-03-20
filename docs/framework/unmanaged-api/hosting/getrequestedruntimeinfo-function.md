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
ms.openlocfilehash: db721e1ef774c87de0fa7da178463d832a3da756
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178146"
---
# <a name="getrequestedruntimeinfo-function"></a>GetRequestedRuntimeInfo 函式
獲取有關應用程式請求的通用語言運行時 （CLR） 的版本和目錄資訊。  
  
 此功能已在 .NET 框架 4 中棄用。  
  
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
 [在]應用程式的名稱。  
  
 `pwszVersion`  
 [在]指定運行時的版本號的字串。  
  
 `pConfigurationFile`  
 [在]與`pExe`關聯的設定檔的名稱。  
  
 `startupFlags`  
 [在]一個或多個[STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)枚舉值。  
  
 `runtimeInfoFlags`  
 [在]一個或多個[RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md)枚舉值。  
  
 `pDirectory`  
 [出]一個緩衝區，在成功完成時包含到運行時的目錄路徑。  
  
 `dwDirectory`  
 [在]目錄緩衝區的長度。  
  
 `dwDirectoryLength`  
 [出]指向目錄路徑字串長度的指標。  
  
 `pVersion`  
 [出]一個緩衝區，在成功完成時包含運行時的版本號。  
  
 `cchBuffer`  
 [在]版本字串緩衝區的長度。  
  
 `dwlength`  
 [出]指向版本字串長度的指標。  
  
## <a name="return-value"></a>傳回值  
 此方法返回 WinError.h 中定義的標準元件物件模型 （COM） 錯誤代碼，以及以下值。  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|S_OK|已成功完成命令。|  
|ERROR_INSUFFICIENT_BUFFER|目錄緩衝區不夠大，無法存儲目錄路徑。<br /><br /> - 或 -<br /><br /> 版本緩衝區不夠大，無法存儲版本字串。|  
  
## <a name="remarks"></a>備註  
 該方法`GetRequestedRuntimeInfo`返回有關載入到進程中的版本的運行時資訊，這不一定是電腦上安裝的最新版本。  
  
 在 .NET 框架版本 2.0 中，可以使用如下`GetRequestedRuntimeInfo`方法獲取有關最新安裝版本的資訊：  
  
- 將`pExe`和`pwszVersion`參數`pConfigurationFile`指定為 null。  
  
- 在`runtimeInfoFlags`參數的枚舉中`RUNTIME_INFO_FLAGS`指定RUNTIME_INFO_UPGRADE_VERSION標誌。  
  
 在`GetRequestedRuntimeInfo`以下情況下，該方法不會返回最新的 CLR 版本：  
  
- 存在指定載入特定 CLR 版本的應用程式佈建檔。 請注意，即使為`pConfigurationFile`參數指定 null，.NET 框架也會使用設定檔。  
  
- [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)方法稱為指定較早的 CLR 版本。  
  
- 為早期 CLR 版本編譯的應用程式當前正在運行。  
  
 對於參數`runtimeInfoFlags`，一次只能指定枚舉的`RUNTIME_INFO_FLAGS`一個體系結構常量：  
  
- RUNTIME_INFO_REQUEST_IA64  
  
- RUNTIME_INFO_REQUEST_AMD64  
  
- RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** MSCorEE.h  
  
 **庫：** MSCorEE.dll  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [GetRequestedRuntimeVersion 函式](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [GetVersionFromProcess 函式](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
