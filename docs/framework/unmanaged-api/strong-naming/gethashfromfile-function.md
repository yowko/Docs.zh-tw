---
title: GetHashFromFile 函式
ms.date: 03/30/2017
api_name:
- GetHashFromFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFile
helpviewer_keywords:
- GetHashFromFile function [.NET Framework strong naming]
ms.assetid: b3c526a4-8fb4-4ad6-b6af-42ce9c06492e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e79c1d89d767832022d487681e0515e5e92a7f3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799224"
---
# <a name="gethashfromfile-function"></a>GetHashFromFile 函式
產生指定檔案內容的雜湊。  
  
 這個函數已被取代。 請改用[ICLRStrongName：： GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a>參數  
 `szFilePath`  
 在要雜湊的檔案名。  
  
 `piHashAlg`  
 [in、out]產生雜湊時要使用的演算法。 有效的演算法是由 Win32 CryptoAPI 所定義。 如果`piHashAlg`設定為0，則會使用預設演算法 CALG_SHA-1。  
  
 `pbHash`  
 脫銷包含所產生之雜湊的位元組陣列。  
  
 `cchHash`  
 在`pbHash`指向的緩衝區大小上限。  
  
 `pchHash`  
 脫銷傳回`pbHash`之的大小（以位元組為單位）。  
  
## <a name="remarks"></a>備註  
 此函式與[GetHashFromFileW](gethashfromfilew-function.md)相同，不同之處在于檔案名規格是 ANSI，而不是 Unicode。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Stackexchange.redis.strongname。h  
  
 **LIBRARY:** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [GetHashFromFile 方法](../hosting/iclrstrongname-gethashfromfile-method.md)
- [GetHashFromFileW 方法](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)
