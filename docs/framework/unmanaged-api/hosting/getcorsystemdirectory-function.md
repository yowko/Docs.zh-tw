---
title: GetCORSystemDirectory 函式
ms.date: 03/30/2017
api_name:
- GetCORSystemDirectory
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORSystemDirectory
helpviewer_keywords:
- GetCORSystemDirectory function [.NET Framework hosting]
ms.assetid: 3dcd16a7-dafc-4ca8-b5cd-20ffb37db91d
topic_type:
- apiref
ms.openlocfilehash: 63fb505a92683fda21b6e71a6ca891ca35afba1d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136417"
---
# <a name="getcorsystemdirectory-function"></a>GetCORSystemDirectory 函式
傳回載入進程的 common language runtime （CLR）的安裝目錄。 安裝目錄是完整的，例如 "c:\windows\microsoft.net\framework\v1.0.3705"。  
  
 這個函數已被取代。 它已由 .NET Framework 4 中提供的[ICLRRuntimeInfo：： GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md)方法所取代。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCORSystemDirectory (   
    [out] LPWSTR  pbuffer,     
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
## <a name="parameters"></a>參數  
 `pbuffer`  
 脫銷一個緩衝區，執行時間會傳回一個字串，其中包含載入進程之執行時間的完整安裝目錄名稱。 如果執行時間尚未載入進程中，此函式會針對電腦上所安裝的最新執行階段版本，傳回適當的目錄資訊。  
  
 `cchBuffer`  
 在`pbuffer`的大小（以位元組為單位）。  
  
 `dwLength`  
 脫銷`pbuffer`中傳回的字元數。  
  
## <a name="remarks"></a>備註  
  
> [!CAUTION]
> 請勿在執行 CLR 第4版的進程中使用此函數。 如果電腦上已安裝舊版的 CLR，此函式會傳回該版本的安裝目錄。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
