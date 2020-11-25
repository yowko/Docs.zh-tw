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
ms.openlocfilehash: 16f95f8fce20f2cf46d4cda214e4494bd288bf60
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727545"
---
# <a name="loadstringrc-function"></a>LoadStringRC 函式

使用目前線程的預設文化特性，將 HRESULT 值轉譯為錯誤訊息。  
  
 此函式已在 .NET Framework 4 中被取代。  
  
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
 擴展在成功完成時包含錯誤訊息的緩衝區。  
  
 `iMax`  
 在錯誤訊息緩衝區的大小。  
  
 `bQuiet`  
 在忽視。  
  
## <a name="return-value"></a>傳回值  

 除了下列值以外，這個方法會傳回 (COM) 錯誤碼（如 Winerror.h 中所定義）的標準元件物件模型。  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_INVALIDARG|`szBuffer` 為 null 或 `iMax` 為零 (0) 。|  
  
## <a name="remarks"></a>備註  

 如果方法未順利完成，就會 `szBuffer` 包含空字串。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** MSCorEE.dll 和 Mscorwks.dll。 使用 MSCorEE.dll 而不是 Mscorwks.dll，以確保您以正確的 .NET Framework 版本為目標。  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [LoadStringRCEx 函式](loadstringrcex-function.md)
- [已被取代的 CLR 裝載函式](deprecated-clr-hosting-functions.md)
