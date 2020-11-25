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
ms.openlocfilehash: 21b01156afceb24ab5c132894fae6922d7b97e59
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733291"
---
# <a name="getcorsystemdirectory-function"></a>GetCORSystemDirectory 函式

傳回載入至進程之 common language runtime (CLR) 的安裝目錄。 安裝目錄是完整的，例如 "c:\windows\microsoft.net\framework\v1.0.3705"。  
  
 這個函數已被取代。 它是由 .NET Framework 4 中提供的 [ICLRRuntimeInfo：： GetRuntimeDirectory](iclrruntimeinfo-getruntimedirectory-method.md) 方法所取代。  
  
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
 擴展緩衝區，其中執行時間會傳回字串，其中包含載入至進程之執行時間的完整安裝目錄名稱。 如果執行時間尚未載入到進程中，此函式會傳回電腦上所安裝執行時間最新版本的適當目錄資訊。  
  
 `cchBuffer`  
 在的大小（以位元組為單位） `pbuffer` 。  
  
 `dwLength`  
 擴展傳回的字元數 `pbuffer` 。  
  
## <a name="remarks"></a>備註  
  
> [!CAUTION]
> 請勿在執行 CLR 第4版的進程中使用此函數。 如果電腦上已安裝較早版本的 CLR，此函式會傳回該版本的安裝目錄。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [已被取代的 CLR 裝載函式](deprecated-clr-hosting-functions.md)
