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
ms.openlocfilehash: 8038d0abc93e058e6bde897bbf2261d8f1df885a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732316"
---
# <a name="gethashfromfilew-function"></a>GetHashFromFileW 函式

產生以 Unicode 字串指定之檔案內容的雜湊。  
  
 此函數已被取代。 請改用 [ICLRStrongName：： GetHashFromFileW](../hosting/iclrstrongname-gethashfromfilew-method.md) 方法。  
  
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
 [in，out]產生雜湊時要使用的演算法。 有效的演算法是由 Win32 CryptoAPI 定義的演算法。 如果 `piHashAlg` 設定為0，則會使用預設的演算法 CALG_SHA-1。  
  
 `pbHash`  
 擴展位元組陣列，其中包含產生的雜湊。  
  
 `cchHash`  
 在所指向之緩衝區的大小上限 `pbHash` 。  
  
 `pchHash`  
 擴展的大小（以位元組為單位） `pbHash` 。  
  
## <a name="remarks"></a>備註  

 這個函式與 [GetHashFromFile](gethashfromfile-function.md)相同，不同之處在于檔案名規格是 Unicode 而非 ANSI。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Stackexchange.redis.strongname。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [GetHashFromFileW 方法](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [GetHashFromFile 方法](../hosting/iclrstrongname-gethashfromfile-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)
