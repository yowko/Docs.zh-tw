---
title: "GetRequestedRuntimeInfo 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetRequestedRuntimeInfo
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: GetRequestedRuntimeInfo
helpviewer_keywords: GetRequestedRuntimeInfo function [.NET Framework hosting]
ms.assetid: 0dfd7cdc-c116-4e25-b56a-ac7b0378c942
topic_type: apiref
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 49459001d3764988eff7b7a4381a843c44e596cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="getrequestedruntimeinfo-function"></a>GetRequestedRuntimeInfo 函式
取得 common language runtime (CLR) 應用程式所要求的版本和目錄資訊。  
  
 此函式中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
#### <a name="parameters"></a>參數  
 `pExe`  
 [in]應用程式的名稱。  
  
 `pwszVersion`  
 [in]指定執行階段的版本號碼的字串。  
  
 `pConfigurationFile`  
 [in]相關聯的組態檔的名稱`pExe`。  
  
 `startupFlags`  
 [in]一或多個[STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)列舉值。  
  
 `runtimeInfoFlags`  
 [in]一或多個[RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md)列舉值。  
  
 `pDirectory`  
 [out]包含成功完成時執行階段的目錄路徑的緩衝區。  
  
 `dwDirectory`  
 [in]目錄緩衝區的長度。  
  
 `dwDirectoryLength`  
 [out]目錄路徑字串的長度指標。  
  
 `pVersion`  
 [out]這種緩衝區包含成功完成時執行階段的版本號碼。  
  
 `cchBuffer`  
 [in]版本字串緩衝區的長度。  
  
 `dwlength`  
 [out]版本字串的長度指標。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回標準的元件物件模型 (COM) 的錯誤代碼，除了下列的值定義了 WinError.h 中。  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|S_OK|已成功完成命令。|  
|ERROR_INSUFFICIENT_BUFFER|目錄緩衝區不足夠儲存的目錄路徑。<br /><br /> -或-<br /><br /> 版本緩衝區不足夠儲存的版本字串。|  
  
## <a name="remarks"></a>備註  
 `GetRequestedRuntimeInfo`方法會傳回執行階段載入處理序，不一定是最新版本的電腦上安裝的版本資訊。  
  
 在.NET Framework 2.0 版中，您可以取得最新的安裝版本的相關資訊，使用`GetRequestedRuntimeInfo`方法，如下所示：  
  
-   指定`pExe`， `pwszVersion`，和`pConfigurationFile`參數為 null。  
  
-   指定在 RUNTIME_INFO_UPGRADE_VERSION 旗標`RUNTIME_INFO_FLAGS`列舉`runtimeInfoFlags`參數。  
  
 `GetRequestedRuntimeInfo`方法不會傳回最新的 CLR 版本，在下列情況下：  
  
-   指定正在載入特定的 CLR 版本的應用程式組態檔存在。 請注意，.NET Framework 會使用組態檔，即使您指定 null`pConfigurationFile`參數。  
  
-   [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)指定舊版 CLR 呼叫方法。  
  
-   目前正在執行針對舊版 CLR 編譯的應用程式。  
  
 如`runtimeInfoFlags`參數，您可以指定其中一個架構的常數`RUNTIME_INFO_FLAGS`列舉一次：  
  
-   RUNTIME_INFO_REQUEST_IA64  
  
-   RUNTIME_INFO_REQUEST_AMD64  
  
-   RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** MSCorEE.dll  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [GetRequestedRuntimeVersion 函式](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 [GetVersionFromProcess 函式](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
