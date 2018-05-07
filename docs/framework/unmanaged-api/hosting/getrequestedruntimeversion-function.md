---
title: GetRequestedRuntimeVersion 函式
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersion
helpviewer_keywords:
- GetRequestedRuntimeVersion function [.NET Framework hosting]
ms.assetid: 82f596a4-483d-4509-b0c5-a84c53c3da1b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 977f63b58ccbc709fb9383acf64686fc92808da4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="getrequestedruntimeversion-function"></a>GetRequestedRuntimeVersion 函式
取得 common language runtime (CLR) 所指定的應用程式要求的版本號碼。 如果未安裝該版本，取得要求的版本之前安裝的最新版本。  
  
 此函式中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *pdwLength  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pExe`  
 [in]應用程式的名稱。  
  
 `pVersion`  
 [out]這種緩衝區包含成功完成時的版本號碼字串。  
  
 `cchBuffer`  
 [in]版本緩衝區的長度。  
  
 `pdwLength`  
 [out]指標的版本號碼字串的長度。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回標準的元件物件模型 (COM) 的錯誤代碼，除了下列的值定義了 WinError.h 中。  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|S_OK|已成功完成命令。|  
|ERROR_INSUFFICIENT_BUFFER|版本緩衝區不足夠儲存的版本字串。|  
|E_POINTER|`pdwLength` 為 null。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** MSCorEE.dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [GetRequestedRuntimeInfo 函式](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 [GetVersionFromProcess 函式](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
