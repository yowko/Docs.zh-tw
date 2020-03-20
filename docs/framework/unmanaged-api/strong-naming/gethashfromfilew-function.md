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
ms.openlocfilehash: 9db583c7064cb910b29e84437f31143dac0d3ec9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175079"
---
# <a name="gethashfromfilew-function"></a>GetHashFromFileW 函式
產生以 Unicode 字串指定之檔案內容的雜湊。  
  
 此函數已被棄用。 使用[ICLR 強式名稱：：獲取雜湊弗羅瓦](../hosting/iclrstrongname-gethashfromfilew-method.md)方法。  
  
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
 [在]要雜湊的檔的 Unicode 名稱。  
  
 `piHashAlg`  
 [進出]生成雜湊時使用的演算法。 有效的演算法是由 Win32 加密 API 定義的演算法。 如果`piHashAlg`設置為 0，則使用預設演算法CALG_SHA-1。  
  
 `pbHash`  
 [出]包含生成的雜湊的位元組陣列。  
  
 `cchHash`  
 [在]指向 的緩衝區的最大大小`pbHash`。  
  
 `pchHash`  
 [出]的大小（以位元組為單位）的大小`pbHash`。  
  
## <a name="remarks"></a>備註  
 此函數與[GetHashFromFile](gethashfromfile-function.md)相同，只不過檔案名規範是 Unicode 而不是 ANSI。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標題：** 強式名稱.h  
  
 **庫：** 作為資源包含在 MsCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [GetHashFromFileW 方法](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [GetHashFromFile 方法](../hosting/iclrstrongname-gethashfromfile-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)
