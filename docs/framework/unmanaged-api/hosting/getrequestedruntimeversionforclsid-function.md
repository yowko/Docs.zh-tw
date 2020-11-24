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
ms.openlocfilehash: 3afb89a42d7e26c5e89e6f9458ef3406cc0102ca
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684183"
---
# <a name="getrequestedruntimeversionforclsid-function"></a>GetRequestedRuntimeVersionForCLSID 函式

取得適當的 common language runtime (CLR) 具有指定之類別的版本資訊 `CLSID` 。  
  
 此函式已在 .NET Framework 4 中被取代。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,
    [out]  LPWSTR     pVersion,
    [in]  DWORD      cchBuffer,
    [out] DWORD*     dwLength,
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
## <a name="parameters"></a>參數  

 `rclsid`  
 在 `CLSID` 元件的。  
  
 `pVersion`  
 擴展 在成功完成時包含版本號碼字串的緩衝區。  
  
 `cchBuffer`  
 在 緩衝區的大小（以寬字元為單位） `pVersion` 。  
  
 `dwLength`  
 擴展傳回之緩衝區的長度（以位元組為單位）。  
  
 `dwResolutionFlags`  
 在 其中一個 CLSID_RESOLUTION_FLAGS 值。 支援下列值：  
  
- CLSID_RESOLUTION_DEFAULT： (0x0) 指定應使用預設 interop 行為。  
  
- CLSID_RESOLUTION_REGISTERED： (0x1) 指定應搜尋登錄並套用填充碼原則。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|函數傳回成功。|  
|E_INVALIDARG|其中一個參數的類型或格式無效。|  
|ERROR_INSUFFICIENT_BUFFER|`pVersion`緩衝區不夠大，無法容納整個版本字串。|  
|REGDB_E_CLASSNOTREG|未向指定的註冊任何類別 `CLSID` 。|  
|E_POINTER|`dwLength` 為 null，或 `cchBuffer` 夠大，足以容納版本字串，但卻 `pVersion` 是 null。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [已被取代的 CLR 裝載函式](deprecated-clr-hosting-functions.md)
