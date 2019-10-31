---
title: GetCORVersion 函式
ms.date: 03/30/2017
api_name:
- GetCORVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORVersion
helpviewer_keywords:
- GetCORVersion function [.NET Framework hosting]
ms.assetid: 2f09cd37-bf3a-4cc5-87b0-adc42a7eed31
topic_type:
- apiref
ms.openlocfilehash: 1283abaf6b08af1d842d8fe4469f7f6c15e38ec5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136427"
---
# <a name="getcorversion-function"></a>GetCORVersion 函式
傳回目前進程中執行之 common language runtime （CLR）的版本號碼。  
  
 此函式在 .NET Framework 4 中已被取代。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
## <a name="parameters"></a>參數  
 `pbuffer`  
 緩衝區的指標，其中 CLR 會傳回一個字串，指定目前載入進程中的執行階段版本。 傳回的字串會採用與傳遞給[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)的字串相同的格式，例如 "v 1.0.1216"。 如果執行時間尚未載入進程中，此函式會針對電腦上所安裝的最新執行階段版本，傳回適當的目錄資訊。  
  
 `cchBuffer`  
 可保留在 `pbuffer`中的字元數（`WCHAR`秒）。  
  
 `dwLength`  
 `pbuffer`中實際傳回的字元數指標。 如果 `pbuffer` 是 null 指標，則執行時間會傳回 E_POINTER。 如果字元數大於 `pbuffer` 的長度，則執行時間會傳回 ERROR_INSUFFICIENT_BUFFER。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
