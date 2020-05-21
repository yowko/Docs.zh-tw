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
ms.openlocfilehash: 6dbb3360132186c38c007fb5fa12a3724ca145aa
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762093"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a>ICLRStrongName::GetHashFromFileW 方法
產生以 Unicode 字串指定之檔案內容的雜湊。  
  
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
 [in、out]產生雜湊時要使用的演算法。 有效的演算法是由 Win32 CryptoAPI 所定義。 如果 `piHashAlg` 設定為0，則會使用 CALG_SHA-1 的預設演算法。  
  
 `pbHash`  
 脫銷包含所產生之雜湊的位元組陣列。  
  
 `cchHash`  
 在所指向之緩衝區的大小上限 `pbHash` 。  
  
 `pchHash`  
 脫銷的大小（以位元組為單位） `pbHash` 。  
  
## <a name="return-value"></a>傳回值  
 `S_OK`如果方法已成功完成，則為，否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。  
  
## <a name="remarks"></a>備註  
 這個方法與[ICLRStrongName：： GetHashFromFile](iclrstrongname-gethashfromfile-method.md)方法相同，不同之處在于檔案名規格是 Unicode 而不是 ANSI。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [GetHashFromFile 方法](iclrstrongname-gethashfromfile-method.md)
- [ICLRStrongName 介面](iclrstrongname-interface.md)
