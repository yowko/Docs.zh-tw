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
ms.openlocfilehash: 1aa5c9f5dd7dd63e69c2eed1f6dd8ad6f007f01f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727532"
---
# <a name="loadstringrcex-function"></a>LoadStringRCEx 函式

針對指定的文化特性，將 HRESULT 值轉譯為適當的錯誤訊息。  
  
 此函式已在 .NET Framework 4 中被取代。  
  
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
 在文化特性識別碼。 的傳遞-1 會 `lcid` 使用預設文化特性。  
  
 `iResourceID`  
 在HRESULT。  
  
 `szBuffer`  
 擴展在成功完成時包含錯誤訊息的緩衝區。  
  
 `iMax`  
 在錯誤訊息緩衝區的大小。  
  
 `bQuiet`  
 在忽視。  
  
 `pcwchUsed`  
 擴展錯誤訊息長度的指標。  
  
## <a name="return-value"></a>傳回值  

 除了下列值以外，這個方法會傳回 Winerror.h 中定義的標準 COM 錯誤碼。  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_INVALIDARG|`szBuffer` 為 null，或 `iMax` 為零 (0) 。|  
  
## <a name="remarks"></a>備註  

 如果方法未順利完成，就會 `szBuffer` 包含空字串。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [LoadStringRC 函式](loadstringrc-function.md)
- [已被取代的 CLR 裝載函式](deprecated-clr-hosting-functions.md)
