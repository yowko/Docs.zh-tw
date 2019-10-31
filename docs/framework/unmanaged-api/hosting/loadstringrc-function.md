---
title: LoadStringRC 函式
ms.date: 03/30/2017
api_name:
- LoadStringRC
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRC
helpviewer_keywords:
- LoadStringRC function [.NET Framework hosting]
ms.assetid: 752e49b4-987c-4c28-a118-1a0c1ed510c5
topic_type:
- apiref
ms.openlocfilehash: 66d4c14234c7929af443922f86098b46a4aa6eb7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122010"
---
# <a name="loadstringrc-function"></a>LoadStringRC 函式
使用目前線程的預設文化特性，將 HRESULT 值轉譯為錯誤訊息。  
  
 此函式在 .NET Framework 4 中已被取代。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet  
);  
```  
  
## <a name="parameters"></a>參數  
 `iResourceID`  
 在HRESULT。  
  
 `szBuffer`  
 脫銷一個緩衝區，其中包含成功完成時的錯誤訊息。  
  
 `iMax`  
 在錯誤訊息緩衝區的大小。  
  
 `bQuiet`  
 在忽略.  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回標準元件物件模型（COM）錯誤碼（如 Winerror.h 中所定義），以及下列值。  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_INVALIDARG|`szBuffer` 為 null 或 `iMax` 為零（0）。|  
  
## <a name="remarks"></a>備註  
 如果方法未順利完成，`szBuffer` 會包含空字串。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll 和 Mscorwks.dll。 請使用 Mscoree.dll 而不是 Mscorwks.dll，以確保您以正確的 .NET Framework 版本為目標。  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [LoadStringRCEx 函式](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)
- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
