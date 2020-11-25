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
ms.openlocfilehash: da0d159da6eef7745c1fa7f7320d5e1355f6e413
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721877"
---
# <a name="getversionfromprocess-function"></a>GetVersionFromProcess 函式

取得與所指定進程控制碼相關聯之 common language runtime (CLR) 的版本號碼。  
  
 此函式已在 .NET Framework 4 中被取代。  
  
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
 擴展在成功完成方法時包含版本號碼字串的緩衝區。  
  
 `cchBuffer`  
 在版本緩衝區的長度。  
  
 `pdwLength`  
 擴展版本號碼字串的長度指標。  
  
## <a name="return-value"></a>傳回值  

 除了下列值以外，這個方法會傳回 (COM) 錯誤碼（如 Winerror.h 中所定義）的標準元件物件模型。  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_INVALIDARG|`pVersion` 為 null 且不 `cchBuffer` 是 null，反之亦然。<br /><br /> -或-<br /><br /> `hProcess` 不是有效的進程控制碼。<br /><br /> -或-<br /><br /> CLR 尚未載入。|  
|ERROR_INSUFFICIENT_BUFFER|`cchBuffer` 為 null 或小於版本字串的長度。|  
|E_NOTIMPL|Microsoft Windows 95、Microsoft Windows 98 或 Microsoft Windows Millennium Edition 作業系統上無法使用此方法。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [GetRequestedRuntimeInfo 函式](getrequestedruntimeinfo-function.md)
- [GetRequestedRuntimeVersion 函式](getrequestedruntimeversion-function.md)
- [已被取代的 CLR 裝載函式](deprecated-clr-hosting-functions.md)
