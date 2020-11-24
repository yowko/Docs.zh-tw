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
ms.openlocfilehash: e7ef3f300c8cfa0c275d15913e171abe09385eea
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681193"
---
# <a name="getcorversion-function"></a>GetCORVersion 函式

傳回在目前進程中執行之 common language runtime (CLR) 的版本號碼。  
  
 此函式已在 .NET Framework 4 中被取代。  
  
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
 緩衝區的指標，其中 CLR 會傳回字串，以指定目前載入處理常式的執行階段版本。 傳回的字串會採用與傳遞給 [CorBindToRuntimeEx](corbindtoruntimeex-function.md)的字串相同的格式，例如 "v 1.0.1216"。 如果執行時間尚未載入到進程中，此函式會傳回電腦上所安裝執行時間最新版本的適當目錄資訊。  
  
 `cchBuffer`  
 `WCHAR`可以保留 (s) 字元數 `pbuffer` 。  
  
 `dwLength`  
 實際傳回的字元數指標 `pbuffer` 。 如果 `pbuffer` 為 null 指標，則執行時間會傳回 E_POINTER。 如果字元數超過的長度，則執行時間會傳回 `pbuffer` ERROR_INSUFFICIENT_BUFFER。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [已被取代的 CLR 裝載函式](deprecated-clr-hosting-functions.md)
