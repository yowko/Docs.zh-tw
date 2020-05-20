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
ms.openlocfilehash: 23d68e8e4bbd87779e3b49f0c40f5a5ab9f5124f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617213"
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
 緩衝區的指標，其中 CLR 會傳回一個字串，指定目前載入進程中的執行階段版本。 傳回的字串會採用與傳遞給[CorBindToRuntimeEx](corbindtoruntimeex-function.md)的字串相同的格式，例如 "v 1.0.1216"。 如果執行時間尚未載入進程中，此函式會針對電腦上所安裝的最新執行階段版本，傳回適當的目錄資訊。  
  
 `cchBuffer`  
 `WCHAR`可以保留在中的字元數 `pbuffer` 。  
  
 `dwLength`  
 中實際傳回的字元數指標 `pbuffer` 。 如果 `pbuffer` 是 null 指標，執行時間會傳回 E_POINTER。 如果字元數大於的長度，則執行時間會傳回 `pbuffer` ERROR_INSUFFICIENT_BUFFER。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [已被取代的 CLR 裝載函式](deprecated-clr-hosting-functions.md)
