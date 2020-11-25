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
ms.openlocfilehash: ee9f9cd9a9f35c6c54497ad382bb6f9817d186bd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732368"
---
# <a name="gethashfromfile-function"></a>GetHashFromFile 函式

產生指定檔案內容的雜湊。  
  
 此函數已被取代。 請改用 [ICLRStrongName：： GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md) 方法。  
  
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
 在要雜湊處理的檔案名。  
  
 `piHashAlg`  
 [in，out]產生雜湊時要使用的演算法。 有效的演算法是由 Win32 CryptoAPI 定義的演算法。 如果 `piHashAlg` 設定為0，則會使用預設的演算法 CALG_SHA-1。  
  
 `pbHash`  
 擴展位元組陣列，其中包含產生的雜湊。  
  
 `cchHash`  
 在指向的緩衝區大小上限 `pbHash` 。  
  
 `pchHash`  
 擴展傳回之的大小（以位元組為單位） `pbHash` 。  
  
## <a name="remarks"></a>備註  

 此函式與 [GetHashFromFileW](gethashfromfilew-function.md)相同，不同之處在于檔案名規格為 ANSI 而非 Unicode。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Stackexchange.redis.strongname。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [GetHashFromFile 方法](../hosting/iclrstrongname-gethashfromfile-method.md)
- [GetHashFromFileW 方法](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)
