---
title: GetRequestedRuntimeVersionForCLSID 函式
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersionForCLSID
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersionForCLSID
helpviewer_keywords:
- GetRequestedRuntimeVersionForCLSID function [.NET Framework hosting]
ms.assetid: 5bb12f9a-0612-434b-b4ed-2db636a20bec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8d3a7168ce0ee3484384ae0e2d10ca00367fc9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="getrequestedruntimeversionforclsid-function"></a>GetRequestedRuntimeVersionForCLSID 函式
取得適當 common language runtime (CLR) 版本資訊與指定類別`CLSID`。  
  
 此函式中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,   
    [out]  LPWSTR     pVersion,   
    [in]  DWORD      cchBuffer,   
    [out] DWORD*     dwLength,   
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
#### <a name="parameters"></a>參數  
 `rclsid`  
 [in] `CLSID`的元件。  
  
 `pVersion`  
 [out] 這種緩衝區包含成功完成時的版本號碼字串。  
  
 `cchBuffer`  
 [in] 大小，以寬字元為單位的`pVersion`緩衝區。  
  
 `dwLength`  
 [out]傳回的緩衝區長度，單位為位元組。  
  
 `dwResolutionFlags`  
 [in] CLSID_RESOLUTION_FLAGS 值的其中一個。 支援下列值：  
  
-   CLSID_RESOLUTION_DEFAULT: (0x0) 指定該預設 interop 行為應該使用。  
  
-   CLSID_RESOLUTION_REGISTERED: (0x1) 登錄也應搜尋和填充碼原則的指定應該套用。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|此函式成功傳回。|  
|E_INVALIDARG|其中一個參數具有無效的類型或格式。|  
|ERROR_INSUFFICIENT_BUFFER|`pVersion`緩衝區不夠大，足以容納整個版本字串。|  
|REGDB_E_CLASSNOTREG|沒有任何類別登錄具有指定`CLSID`。|  
|E_POINTER|`dwLength` 為 null，或`cchBuffer`夠大，無法保存的版本字串，但`pVersion`為 null。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
