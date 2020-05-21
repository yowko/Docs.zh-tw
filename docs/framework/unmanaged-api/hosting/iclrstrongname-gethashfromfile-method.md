---
title: ICLRStrongName::GetHashFromFile 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromFile method [.NET Framework hosting]
- GetHashFromFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 9e50480a-8ada-4044-b2a5-97bb14ed3525
topic_type:
- apiref
ms.openlocfilehash: e4a5f6440a016176cf06704b342c173b29748e78
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762106"
---
# <a name="iclrstrongnamegethashfromfile-method"></a>ICLRStrongName::GetHashFromFile 方法
產生指定檔案內容的雜湊。  
  
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
 [in、out]產生雜湊時要使用的演算法。 有效的演算法是由 Win32 CryptoAPI 所定義。 如果 `piHashAlg` 設定為0，則會使用 CALG_SHA-1 的預設演算法。  
  
 `pbHash`  
 脫銷包含所產生之雜湊的位元組陣列。  
  
 `cchHash`  
 在指向的緩衝區大小上限 `pbHash` 。  
  
 `pchHash`  
 脫銷傳回之的大小（以位元組為單位） `pbHash` 。  
  
## <a name="return-value"></a>傳回值  
 `S_OK`如果方法已成功完成，則為，否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。  
  
## <a name="remarks"></a>備註  
 這個方法與[ICLRStrongName：： GetHashFromFileW](iclrstrongname-gethashfromfilew-method.md)方法相同，不同之處在于檔案名規格是 ANSI，而不是 Unicode。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [GetHashFromFileW 方法](iclrstrongname-gethashfromfilew-method.md)
- [ICLRStrongName 介面](iclrstrongname-interface.md)
