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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9be512bab30e08ddeb7deadf8a29263e928549a1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134604"
---
# <a name="gethashfromfilew-function"></a>GetHashFromFileW 函式
產生以 Unicode 字串指定之檔案內容的雜湊。  
  
 此函式已被取代。 使用[iclrstrongname:: Gethashfromfilew](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)方法改為。  
  
## <a name="syntax"></a>語法  
  
```  
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
 [in]要雜湊之檔案的 Unicode 名稱。  
  
 `piHashAlg`  
 [in、 out]要產生的雜湊時所使用的演算法。 有效的演算法為 Win32 CryptoAPI 所定義。 如果`piHashAlg`設為 0，CALG_SHA-1 會使用預設演算法。  
  
 `pbHash`  
 [out]位元組陣列，包含產生的雜湊。  
  
 `cchHash`  
 [in]所指向的緩衝區大小上限`pbHash`。  
  
 `pchHash`  
 [out]大小，以位元組為單位的`pbHash`。  
  
## <a name="remarks"></a>備註  
 此函式是相同[GetHashFromFile](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md)，不同之處在於，檔案名稱規格會是 Unicode，而不是 ANSI。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** StrongName.h  
  
 **LIBRARY:** 包含做為 MsCorEE.dll 中的資源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [GetHashFromFileW 方法](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [GetHashFromFile 方法](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [ICLRStrongName 介面](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
