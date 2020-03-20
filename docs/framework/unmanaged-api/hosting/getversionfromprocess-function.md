---
title: GetVersionFromProcess 函式
ms.date: 03/30/2017
api_name:
- GetVersionFromProcess
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetVersionFromProcess
helpviewer_keywords:
- GetVersionFromProcess function [.NET Framework hosting]
ms.assetid: a9f7f824-64a1-408d-8607-91c7f19d21fe
topic_type:
- apiref
ms.openlocfilehash: a04a0c5e6865c3664d2cb5fb341c3625e35d4d7c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178122"
---
# <a name="getversionfromprocess-function"></a>GetVersionFromProcess 函式
獲取與指定進程控制碼關聯的通用語言運行時 （CLR） 的版本號。  
  
 此功能已在 .NET 框架 4 中棄用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *dwLength  
);  
```  
  
## <a name="parameters"></a>參數  
 `hProcess`  
 [在]進程的控制碼。  
  
 `pVersion`  
 [出]在成功完成方法後包含版本號字串的緩衝區。  
  
 `cchBuffer`  
 [在]版本緩衝區的長度。  
  
 `pdwLength`  
 [出]指向版本號字串長度的指標。  
  
## <a name="return-value"></a>傳回值  
 此方法返回 WinError.h 中定義的標準元件物件模型 （COM） 錯誤代碼，以及以下值。  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_INVALIDARG|`pVersion`為空，`cchBuffer`不為空，反之亦然。<br /><br /> -或-<br /><br /> `hProcess`不是進程的有效控制碼。<br /><br /> -或-<br /><br /> 未載入 CLR。|  
|ERROR_INSUFFICIENT_BUFFER|`cchBuffer`為空或小於版本字串的長度。|  
|E_NOTIMPL|此方法在 Microsoft Windows 95、微軟 Windows 98 或 Microsoft Windows 千年版作業系統上不可用。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** MSCorEE.h  
  
 **庫：** MSCorEE.dll  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [GetRequestedRuntimeInfo 函式](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [GetRequestedRuntimeVersion 函式](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
