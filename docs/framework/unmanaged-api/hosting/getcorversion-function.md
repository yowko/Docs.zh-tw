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
ms.openlocfilehash: 1f40f27651d2d75cf2c3e4d7d1c21e1f47d402af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178196"
---
# <a name="getcorversion-function"></a>GetCORVersion 函式
返回當前進程中運行的通用語言運行時 （CLR） 的版本號。  
  
 此功能已在 .NET 框架 4 中棄用。  
  
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
 指向緩衝區的指標，其中 CLR 返回一個字串，指定當前載入到進程的運行時的版本。 返回的字串採用與傳遞給[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)的字串相同的形式，例如"v1.0.1216"。 如果運行時尚未載入到進程中，該函數將返回電腦上安裝的最新版本的運行時的相應目錄資訊。  
  
 `cchBuffer`  
 可在 中`pbuffer`持有的字元`WCHAR`數 。  
  
 `dwLength`  
 指向 中`pbuffer`實際返回的字元數的指標。 如果`pbuffer`為空指標，則運行時返回E_POINTER。 如果字元數大於，則`pbuffer`長度 為 ，運行時將返回ERROR_INSUFFICIENT_BUFFER。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** MSCorEE.h  
  
 **庫：** MSCorEE.dll  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
