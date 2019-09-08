---
title: GetHashFromHandle 函式
ms.date: 03/30/2017
api_name:
- GetHashFromHandle
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle function [.NET Framework strong naming]
ms.assetid: 9e00337f-b307-4602-9bc3-965a8dbf02cd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3eac353252f5a97402cbd883895b3e397c39edd6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799176"
---
# <a name="gethashfromhandle-function"></a>GetHashFromHandle 函式
使用指定的雜湊演算法產生以指定檔案控制代碼指定之檔案的雜湊。  
  
 這個函數已被取代。 請改用[ICLRStrongName：： GetHashFromHandle](../hosting/iclrstrongname-gethashfromhandle-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a>參數  
 `hFile`  
 在要雜湊之檔案的控制碼。  
  
 `piHashAlg`  
 [in、out]指定雜湊演算法的常數。 預設演算法使用零。  
  
 `pbHash`  
 脫銷傳回的雜湊緩衝區。  
  
 `cchHash`  
 在要求的大小`pbHash`上限。  
  
 `pchHash`  
 脫銷傳回`pbHash`之的大小（以位元組為單位）。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Stackexchange.redis.strongname。h  
  
 **LIBRARY:** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [GetHashFromHandle 方法](../hosting/iclrstrongname-gethashfromhandle-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)
