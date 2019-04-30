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
ms.openlocfilehash: 5774b7cdcfedfc407b626ab5052f5b4a77461e9b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049384"
---
# <a name="gethashfromfile-function"></a>GetHashFromFile 函式
產生指定檔案內容的雜湊。  
  
 此函式已被取代。 使用[iclrstrongname:: Gethashfromfile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)方法改為。  
  
## <a name="syntax"></a>語法  
  
```  
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
 [in]要雜湊之檔案的名稱。  
  
 `piHashAlg`  
 [in、 out]要產生的雜湊時所使用的演算法。 有效的演算法為 Win32 CryptoAPI 所定義。 如果`piHashAlg`設為 0，CALG_SHA-1 會使用預設演算法。  
  
 `pbHash`  
 [out]位元組陣列，包含產生的雜湊。  
  
 `cchHash`  
 [in]緩衝區的大小上限，`pbHash`指向。  
  
 `pchHash`  
 [out]大小，以位元組為單位傳回`pbHash`。  
  
## <a name="remarks"></a>備註  
 此函式是相同[GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md)，不同之處在於其檔案名稱規格的 ANSI，而非 Unicode。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** StrongName.h  
  
 **LIBRARY:** 包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [GetHashFromFile 方法](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [GetHashFromFileW 方法](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [ICLRStrongName 介面](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
