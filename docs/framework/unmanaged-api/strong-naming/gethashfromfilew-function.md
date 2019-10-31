---
title: GetHashFromFileW 函式
ms.date: 03/30/2017
api_name:
- GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW function [.NET Framework strong naming]
ms.assetid: 97c2d7a6-5376-45a1-ba65-146a249147cc
topic_type:
- apiref
ms.openlocfilehash: db6f39119d143d27c0d3a80a9c65565d4dfd0d39
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140670"
---
# <a name="gethashfromfilew-function"></a>GetHashFromFileW 函式
產生以 Unicode 字串指定之檔案內容的雜湊。  
  
 這個函數已被取代。 請改用[ICLRStrongName：： GetHashFromFileW](../hosting/iclrstrongname-gethashfromfilew-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
## <a name="parameters"></a>參數  
 `wszFilePath`  
 在要雜湊之檔案的 Unicode 名稱。  
  
 `piHashAlg`  
 [in、out]產生雜湊時要使用的演算法。 有效的演算法是由 Win32 CryptoAPI 所定義。 如果 `piHashAlg` 設定為0，則會使用預設的演算法 CALG_SHA-1。  
  
 `pbHash`  
 脫銷包含所產生之雜湊的位元組陣列。  
  
 `cchHash`  
 在`pbHash`所指向之緩衝區的大小上限。  
  
 `pchHash`  
 脫銷`pbHash`的大小（以位元組為單位）。  
  
## <a name="remarks"></a>備註  
 此函式與[GetHashFromFile](gethashfromfile-function.md)相同，不同之處在于檔案名規格是 Unicode 而不是 ANSI。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Stackexchange.redis.strongname。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [GetHashFromFileW 方法](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [GetHashFromFile 方法](../hosting/iclrstrongname-gethashfromfile-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)
