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
ms.openlocfilehash: 6132e94544b30486b70ecfec49c1ddd5e3c0f50b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178108"
---
# <a name="getrequestedruntimeversionforclsid-function"></a>GetRequestedRuntimeVersionForCLSID 函式
獲取具有指定的`CLSID`類的相應通用語言運行時 （CLR） 版本資訊。  
  
 此功能已在 .NET 框架 4 中棄用。  
  
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
 [在] 元件`CLSID`的 。  
  
 `pVersion`  
 [出] 成功完成後包含版本號字串的緩衝區。  
  
 `cchBuffer`  
 [在] `pVersion`緩衝區的大小（以寬字元表示）。  
  
 `dwLength`  
 [出]返回的緩衝區的長度（以位元組為單位）。  
  
 `dwResolutionFlags`  
 [在] 值CLSID_RESOLUTION_FLAGS之一。 支援下列值：  
  
- CLSID_RESOLUTION_DEFAULT：（0x0）指定應使用預設交互操作行為。  
  
- CLSID_RESOLUTION_REGISTERED：（0x1）指定應搜索註冊表並應用 shim 策略。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|函數已成功返回。|  
|E_INVALIDARG|其中一個參數的類型或格式無效。|  
|ERROR_INSUFFICIENT_BUFFER|緩衝區`pVersion`不夠大，無法容納整個版本字串。|  
|REGDB_E_CLASSNOTREG|沒有在指定的`CLSID`中註冊了類。|  
|E_POINTER|`dwLength`為 null，`cchBuffer`或足夠大以容納版本字串，但`pVersion`為 null。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** MSCorEE.h  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
