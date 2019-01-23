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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ec8e5dfc92a818bfc23c28f3058086c3bd1a8ed
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597940"
---
# <a name="loadstringrcex-function"></a>LoadStringRCEx 函式
將 HRESULT 值轉譯成適當的錯誤訊息指定的文化特性。  
  
 此函式中的過時[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT LoadStringRCEx (  
    [in]  LCID    lcid,   
    [in]  UINT    iResouceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet,   
    [out] int    *pcwchUsed  
);  
```  
  
#### <a name="parameters"></a>參數  
 `lcid`  
 [in]文化特性識別項。 傳遞 – 1`lcid`若要使用的預設文化特性。  
  
 `iResourceID`  
 [in]HRESULT。  
  
 `szBuffer`  
 [out]這種緩衝區包含成功完成時的錯誤訊息。  
  
 `iMax`  
 [in]錯誤訊息緩衝區的大小。  
  
 `bQuiet`  
 [in]略過。  
  
 `pcwchUsed`  
 [out]錯誤訊息的長度指標。  
  
## <a name="return-value"></a>傳回值  
 中所定義 WinError.h，除了下列的值，這個方法會傳回標準的 COM 錯誤代碼。  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_INVALIDARG|`szBuffer` 為 null，或`iMax`為零 (0)。|  
  
## <a name="remarks"></a>備註  
 如果方法未成功完成`szBuffer`包含空字串。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** MSCorEE.dll  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [LoadStringRC 函式](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)
- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
