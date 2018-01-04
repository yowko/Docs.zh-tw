---
title: "GetVersionFromProcess 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetVersionFromProcess
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: GetVersionFromProcess
helpviewer_keywords: GetVersionFromProcess function [.NET Framework hosting]
ms.assetid: a9f7f824-64a1-408d-8607-91c7f19d21fe
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: db5054ab9b71eb93005fc0315acba82d807487ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="getversionfromprocess-function"></a>GetVersionFromProcess 函式
取得 common language runtime (CLR) 與指定的處理序控制代碼相關聯的版本號碼。  
  
 此函式中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *dwLength  
);  
```  
  
#### <a name="parameters"></a>參數  
 `hProcess`  
 [in]處理程序控制代碼。  
  
 `pVersion`  
 [out]這種緩衝區包含此方法成功完成時的版本號碼字串。  
  
 `cchBuffer`  
 [in]版本緩衝區的長度。  
  
 `pdwLength`  
 [out]指標的版本號碼字串的長度。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回標準的元件物件模型 (COM) 的錯誤代碼，除了下列的值定義了 WinError.h 中。  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_INVALIDARG|`pVersion`為 null 和`cchBuffer`不是 null，反之亦然。<br /><br /> -或-<br /><br /> `hProcess`不是有效的處理常式至處理序。<br /><br /> -或-<br /><br /> 未載入 CLR。|  
|ERROR_INSUFFICIENT_BUFFER|`cchBuffer`為 null 或小於版本字串的長度。|  
|E_NOTIMPL|無法在 Microsoft Windows 95、 Microsoft Windows 98、 或 Microsoft Windows Me 作業系統上使用這個方法。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** MSCorEE.dll  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [GetRequestedRuntimeInfo 函式](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 [GetRequestedRuntimeVersion 函式](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
