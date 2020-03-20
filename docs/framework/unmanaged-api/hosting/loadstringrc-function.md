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
ms.openlocfilehash: 56ae7b7cf3b577bfe41ebd0bdd98e0da68047b44
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176236"
---
# <a name="loadstringrc-function"></a>LoadStringRC 函式
使用當前執行緒的預設區域性將 HRESULT 值轉換為錯誤訊息。  
  
 此功能已在 .NET 框架 4 中棄用。  
  
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
 [在]A HRESULT。  
  
 `szBuffer`  
 [出]成功完成後包含錯誤訊息的緩衝區。  
  
 `iMax`  
 [在]錯誤訊息緩衝區的大小。  
  
 `bQuiet`  
 [在]忽視。  
  
## <a name="return-value"></a>傳回值  
 此方法返回 WinError.h 中定義的標準元件物件模型 （COM） 錯誤代碼，以及以下值。  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_INVALIDARG|`szBuffer`為空或`iMax`為零 （0）。|  
  
## <a name="remarks"></a>備註  
 如果方法未成功完成，`szBuffer`則包含一個空字串。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** MSCorEE.h  
  
 **庫：** MSCorE.dll 和 Mscorwks.dll. 使用 MSCorEE.dll 而不是 mscorwks.dll 來確保針對 .NET 框架的正確版本。  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [LoadStringRCEx 函式](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)
- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
