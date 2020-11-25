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
ms.openlocfilehash: ff346d8f7ba321904a8d91079298b58039e6eb54
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727597"
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
 在要雜湊處理的檔案名。  
  
 `piHashAlg`  
 [in，out]產生雜湊時要使用的演算法。 有效的演算法是由 Win32 CryptoAPI 定義的演算法。 如果 `piHashAlg` 設定為0，則會使用預設的演算法 CALG_SHA-1。  
  
 `pbHash`  
 擴展位元組陣列，其中包含產生的雜湊。  
  
 `cchHash`  
 在指向的緩衝區大小上限 `pbHash` 。  
  
 `pchHash`  
 擴展傳回之的大小（以位元組為單位） `pbHash` 。  
  
## <a name="return-value"></a>傳回值  

 `S_OK` 如果方法成功完成，則為，否則，表示失敗 (的 HRESULT 值會看到清單) 的 [一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values) 。  
  
## <a name="remarks"></a>備註  

 這個方法與 [ICLRStrongName：： GetHashFromFileW](iclrstrongname-gethashfromfilew-method.md) 方法相同，不同之處在于檔案名規格是 ANSI 而不是 Unicode。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [GetHashFromFileW 方法](iclrstrongname-gethashfromfilew-method.md)
- [ICLRStrongName 介面](iclrstrongname-interface.md)
