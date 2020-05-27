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
ms.openlocfilehash: a05cbe985c2cfebb67756fdfb54398b36e87f441
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008505"
---
# <a name="loadstringrcex-function"></a>LoadStringRCEx 函式
針對指定的文化特性，將 HRESULT 值轉譯為適當的錯誤訊息。  
  
 此函式在 .NET Framework 4 中已被取代。  
  
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
 在文化特性識別碼。 傳遞-1 表示 `lcid` 要使用預設文化特性。  
  
 `iResourceID`  
 在HRESULT。  
  
 `szBuffer`  
 脫銷一個緩衝區，其中包含成功完成時的錯誤訊息。  
  
 `iMax`  
 在錯誤訊息緩衝區的大小。  
  
 `bQuiet`  
 在忽略.  
  
 `pcwchUsed`  
 脫銷錯誤訊息長度的指標。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回標準 COM 錯誤碼（如 Winerror.h 中所定義），以及下列值。  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_INVALIDARG|`szBuffer`為 null，或 `iMax` 為零（0）。|  
  
## <a name="remarks"></a>備註  
 如果方法未順利完成，則會 `szBuffer` 包含空字串。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [LoadStringRC 函式](loadstringrc-function.md)
- [已被取代的 CLR 裝載函式](deprecated-clr-hosting-functions.md)
