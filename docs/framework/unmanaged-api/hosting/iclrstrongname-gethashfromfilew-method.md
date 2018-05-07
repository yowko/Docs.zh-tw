---
title: ICLRStrongName::GetHashFromFileW 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromFileW method [.NET Framework hosting]
ms.assetid: c6ff45fc-905d-4c6e-b00c-97c6c7c55d99
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 87600781c90fe5e6e049af74a68859955153f3b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="iclrstrongnamegethashfromfilew-method"></a>ICLRStrongName::GetHashFromFileW 方法
產生之雜湊的 Unicode 字串所指定的檔案內容。  
  
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
  
#### <a name="parameters"></a>參數  
 `wszFilePath`  
 [in]Unicode 雜湊的檔案名稱。  
  
 `piHashAlg`  
 [in、 out]要產生雜湊時所使用的演算法。 有效的演算法是由 Win32 CryptoAPI 所定義。 如果`piHashAlg`設為 0，則使用 CALG_SHA 1 的預設演算法。  
  
 `pbHash`  
 [out]位元組陣列，包含所產生的雜湊。  
  
 `cchHash`  
 [in]所指向之緩衝區的大小上限`pbHash`。  
  
 `pchHash`  
 [out]大小，以位元組為單位的`pbHash`。  
  
## <a name="return-value"></a>傳回值  
 `S_OK` 如果方法成功。否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](http://go.microsoft.com/fwlink/?LinkId=213878)清單)。  
  
## <a name="remarks"></a>備註  
 這個方法相當於[iclrstrongname:: Gethashfromfile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)方法，不同之處在於的檔案名稱的規格是 Unicode，而非 ANSI。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [GetHashFromFile 方法](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [ICLRStrongName 介面](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
