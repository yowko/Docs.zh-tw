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
ms.openlocfilehash: 899d6e74902e47f1f41b849bd5c25048baa175f7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617135"
---
# <a name="getrequestedruntimeversionforclsid-function"></a>GetRequestedRuntimeVersionForCLSID 函式
針對具有指定的類別，取得適當的 common language runtime （CLR）版本資訊 `CLSID` 。  
  
 此函式在 .NET Framework 4 中已被取代。  
  
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
 在 `CLSID`元件的。  
  
 `pVersion`  
 脫銷 一個緩衝區，其中包含成功完成時的版本號碼字串。  
  
 `cchBuffer`  
 在 緩衝區的大小（以寬字元為單位） `pVersion` 。  
  
 `dwLength`  
 脫銷所傳回緩衝區的長度（以位元組為單位）。  
  
 `dwResolutionFlags`  
 在 其中一個 CLSID_RESOLUTION_FLAGS 值。 支援下列值：  
  
- CLSID_RESOLUTION_DEFAULT：（0x0）指定應該使用預設 interop 行為。  
  
- CLSID_RESOLUTION_REGISTERED：（0x1）指定應搜尋登錄，並套用填充碼原則。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|說明|  
|-------------|-----------------|  
|S_OK|已成功傳回函數。|  
|E_INVALIDARG|其中一個參數的類型或格式無效。|  
|ERROR_INSUFFICIENT_BUFFER|`pVersion`緩衝區不夠大，無法保存整個版本字串。|  
|REGDB_E_CLASSNOTREG|未向指定的註冊任何類別 `CLSID` 。|  
|E_POINTER|`dwLength`是 null，或 `cchBuffer` 夠大而無法保存版本字串，但卻 `pVersion` 是 null。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [已被取代的 CLR 裝載函式](deprecated-clr-hosting-functions.md)
