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
ms.openlocfilehash: ea2b70f37668587fb02513ab54da6c1915e2918d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176977"
---
# <a name="gethashfromfile-function"></a>GetHashFromFile 函式
產生指定檔案內容的雜湊。  
  
 此函數已被棄用。 改用[ICLR 強式名稱：：獲取雜湊檔](../hosting/iclrstrongname-gethashfromfile-method.md)方法。  
  
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
 [在]要雜湊的檔的名稱。  
  
 `piHashAlg`  
 [進出]生成雜湊時使用的演算法。 有效的演算法是由 Win32 加密 API 定義的演算法。 如果`piHashAlg`設置為 0，則使用預設演算法CALG_SHA-1。  
  
 `pbHash`  
 [出]包含生成的雜湊的位元組陣列。  
  
 `cchHash`  
 [在]`pbHash`指向的緩衝區的最大大小。  
  
 `pchHash`  
 [出]返回`pbHash`的大小（以位元組為單位）。  
  
## <a name="remarks"></a>備註  
 此函數與[GetHashFromFileW](gethashfromfilew-function.md)相同，只不過檔案名規範是 ANSI 而不是 Unicode。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標題：** 強式名稱.h  
  
 **庫：** 作為資源包含在 MsCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [GetHashFromFile 方法](../hosting/iclrstrongname-gethashfromfile-method.md)
- [GetHashFromFileW 方法](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)
