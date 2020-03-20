---
title: LoadStringRCEx 函式
ms.date: 03/30/2017
api_name:
- LoadStringRCEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRCEx
helpviewer_keywords:
- LoadStringRCEx function [.NET Framework hosting]
ms.assetid: bc789636-ca14-4f07-8f77-9305874d7495
topic_type:
- apiref
ms.openlocfilehash: a300c2679ef11a84edb2ab89c8dea96e445c9ee3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177988"
---
# <a name="loadstringrcex-function"></a>LoadStringRCEx 函式
將 HRESULT 值轉換為指定區域性的相應錯誤訊息。  
  
 此功能已在 .NET 框架 4 中棄用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT LoadStringRCEx (  
    [in]  LCID    lcid,
    [in]  UINT    iResouceID,
    [out] LPWSTR  szBuffer,
    [in]  int     iMax,
    [in]  int     bQuiet,
    [out] int    *pcwchUsed  
);  
```  
  
## <a name="parameters"></a>參數  
 `lcid`  
 [在]區域性識別碼。 通過 -1`lcid`用於使用預設區域性。  
  
 `iResourceID`  
 [在]A HRESULT。  
  
 `szBuffer`  
 [出]成功完成後包含錯誤訊息的緩衝區。  
  
 `iMax`  
 [在]錯誤訊息緩衝區的大小。  
  
 `bQuiet`  
 [在]忽視。  
  
 `pcwchUsed`  
 [出]指向錯誤訊息長度的指標。  
  
## <a name="return-value"></a>傳回值  
 此方法返回 WinError.h 中定義的標準 COM 錯誤代碼，以及以下值。  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_INVALIDARG|`szBuffer`為空或`iMax`為零 （0）。|  
  
## <a name="remarks"></a>備註  
 如果方法未成功完成，`szBuffer`則包含一個空字串。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** MSCorEE.h  
  
 **庫：** MSCorEE.dll  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [LoadStringRC 函式](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)
- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
