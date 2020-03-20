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
ms.openlocfilehash: bdafacfe52d678aacfcd44de1e924bcb88547424
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178197"
---
# <a name="getcorsystemdirectory-function"></a>GetCORSystemDirectory 函式
返回載入到進程中的通用語言運行時 （CLR） 的安裝目錄。 安裝目錄完全限定，例如，"c：_windows_microsoft.net_framework_v1.0.3705"。  
  
 這個函數已被取代。 它被[ICLRRuntimeInfo 取代：獲取](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md).NET 框架 4 中提供的 RuntimeDirectory 方法。  
  
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
 [出]運行時返回一個字串，其中包含載入到進程的運行時安裝目錄的完全限定名稱。 如果運行時尚未載入到進程中，該函數將返回電腦上安裝的最新版本的運行時的相應目錄資訊。  
  
 `cchBuffer`  
 [在]的大小（以位元組為單位）的大小`pbuffer`。  
  
 `dwLength`  
 [出]中`pbuffer`返回的字元數。  
  
## <a name="remarks"></a>備註  
  
> [!CAUTION]
> 請勿在運行 CLR 版本 4 的進程中使用此功能。 如果電腦上安裝了 CLR 的早期版本，則此功能將返回該版本的安裝目錄。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** MSCorEE.h  
  
 **庫：** MSCorEE.dll  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
