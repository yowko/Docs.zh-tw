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
ms.openlocfilehash: b120b854e1787824808dd64d95b0fa78ba6c9fa2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705484"
---
# <a name="getrequestedruntimeinfo-function"></a>GetRequestedRuntimeInfo 函式

取得應用程式要求的 common language runtime (CLR) 的版本和目錄資訊。  
  
 此函式已在 .NET Framework 4 中被取代。  
  
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
 在字串，指定執行時間的版本號碼。  
  
 `pConfigurationFile`  
 在與相關聯的設定檔名稱 `pExe` 。  
  
 `startupFlags`  
 在一或多個 [STARTUP_FLAGS](startup-flags-enumeration.md) 的列舉值。  
  
 `runtimeInfoFlags`  
 在一或多個 [RUNTIME_INFO_FLAGS](runtime-info-flags-enumeration.md) 的列舉值。  
  
 `pDirectory`  
 擴展在成功完成時包含執行時間目錄路徑的緩衝區。  
  
 `dwDirectory`  
 在目錄緩衝區的長度。  
  
 `dwDirectoryLength`  
 擴展目錄路徑字串長度的指標。  
  
 `pVersion`  
 擴展緩衝區，其中包含成功完成時的執行階段版本號碼。  
  
 `cchBuffer`  
 在版本字串緩衝區的長度。  
  
 `dwlength`  
 擴展版本字串長度的指標。  
  
## <a name="return-value"></a>傳回值  

 除了下列值以外，這個方法會傳回 (COM) 錯誤碼（如 Winerror.h 中所定義）的標準元件物件模型。  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|S_OK|已成功完成命令。|  
|ERROR_INSUFFICIENT_BUFFER|目錄緩衝區不夠大，無法儲存目錄路徑。<br /><br /> - 或 -<br /><br /> 版本緩衝區不夠大，無法儲存版本字串。|  
  
## <a name="remarks"></a>備註  

 `GetRequestedRuntimeInfo`方法會傳回載入至進程之版本的執行時間資訊，這不一定是電腦上安裝的最新版本。  
  
 在 .NET Framework 2.0 版中，您可以使用方法來取得最新安裝版本的相關資訊，如下所示 `GetRequestedRuntimeInfo` ：  
  
- 將 `pExe` 、 `pwszVersion` 和參數指定 `pConfigurationFile` 為 null。  
  
- 在參數的列舉中指定 RUNTIME_INFO_UPGRADE_VERSION 旗標 `RUNTIME_INFO_FLAGS` `runtimeInfoFlags` 。  
  
 `GetRequestedRuntimeInfo`在下列情況下，方法不會傳回最新的 CLR 版本：  
  
- 指定載入特定 CLR 版本的應用程式佈建檔存在。 請注意，即使您為參數指定 null，.NET Framework 也會使用設定檔案 `pConfigurationFile` 。  
  
- 呼叫 [CorBindToRuntimeEx](corbindtoruntimeex-function.md) 方法時指定了較早的 CLR 版本。  
  
- 針對先前的 CLR 版本編譯的應用程式目前正在執行。  
  
 針對 `runtimeInfoFlags` 參數，您一次只能指定列舉的其中一個架構常數 `RUNTIME_INFO_FLAGS` ：  
  
- RUNTIME_INFO_REQUEST_IA64  
  
- RUNTIME_INFO_REQUEST_AMD64  
  
- RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [GetRequestedRuntimeVersion 函式](getrequestedruntimeversion-function.md)
- [GetVersionFromProcess 函式](getversionfromprocess-function.md)
- [已被取代的 CLR 裝載函式](deprecated-clr-hosting-functions.md)
