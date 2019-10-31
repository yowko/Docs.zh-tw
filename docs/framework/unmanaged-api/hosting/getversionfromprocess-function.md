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
ms.openlocfilehash: 76c033b11f3212241827d74f4fe18ee881f20b64
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127042"
---
# <a name="getversionfromprocess-function"></a>GetVersionFromProcess 函式
取得與指定的進程控制碼相關聯之 common language runtime （CLR）的版本號碼。  
  
 此函式在 .NET Framework 4 中已被取代。  
  
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
 在進程的控制碼。  
  
 `pVersion`  
 脫銷一個緩衝區，其中包含成功完成方法時的版本號碼字串。  
  
 `cchBuffer`  
 在版本緩衝區的長度。  
  
 `pdwLength`  
 脫銷版本號碼字串長度的指標。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回標準元件物件模型（COM）錯誤碼（如 Winerror.h 中所定義），以及下列值。  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_INVALIDARG|`pVersion` 為 null，且 `cchBuffer` 不是 null，或反之亦然。<br /><br /> -或-<br /><br /> `hProcess` 不是有效的進程控制碼。<br /><br /> -或-<br /><br /> 未載入 CLR。|  
|ERROR_INSUFFICIENT_BUFFER|`cchBuffer` 為 null 或小於版本字串的長度。|  
|E_NOTIMPL|這個方法無法在 Microsoft Windows 95、Microsoft Windows 98 或 Microsoft Windows Millennium Edition 作業系統上使用。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [GetRequestedRuntimeInfo 函式](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [GetRequestedRuntimeVersion 函式](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
