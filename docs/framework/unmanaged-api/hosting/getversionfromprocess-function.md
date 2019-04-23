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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 452104939acf5de7bb151cba00d65fb6631c98d5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124081"
---
# <a name="getversionfromprocess-function"></a>GetVersionFromProcess 函式
取得 common language runtime (CLR) 與指定的處理序控制代碼相關聯的版本號碼。  
  
 此函式中的過時[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *dwLength  
);  
```  
  
## <a name="parameters"></a>參數  
 `hProcess`  
 [in]處理序控制代碼。  
  
 `pVersion`  
 [out]這種緩衝區包含此方法成功完成時的版本號碼字串。  
  
 `cchBuffer`  
 [in]版本緩衝區的長度。  
  
 `pdwLength`  
 [out]版本號碼的字串長度的指標。  
  
## <a name="return-value"></a>傳回值  
 中所定義 WinError.h，除了下列的值，這個方法會傳回標準的元件物件模型 (COM) 錯誤代碼。  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_INVALIDARG|`pVersion` 為 null 及`cchBuffer`不是 null，或反之亦然。<br /><br /> -或-<br /><br /> `hProcess` 不是有效的控制代碼至處理序。<br /><br /> -或-<br /><br /> 無法載入 CLR。|  
|ERROR_INSUFFICIENT_BUFFER|`cchBuffer` 為 null 或版本字串的長度大於或等於。|  
|E_NOTIMPL|這個方法並不適用於 Microsoft Windows 95、 Microsoft Windows 98 或 Microsoft Windows Millennium Edition 作業系統。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** MSCorEE.dll  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [GetRequestedRuntimeInfo 函式](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [GetRequestedRuntimeVersion 函式](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
