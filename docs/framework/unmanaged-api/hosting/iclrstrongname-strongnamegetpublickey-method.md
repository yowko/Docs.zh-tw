---
title: ICLRStrongName::StrongNameGetPublicKey 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetPublicKey method [.NET Framework hosting]
ms.assetid: a31dcaa9-a404-4c1d-8cc7-081827c52935
topic_type:
- apiref
ms.openlocfilehash: 5a20bde64830617090c92afe5fae3a603cf9103b
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763123"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a>ICLRStrongName::StrongNameGetPublicKey 方法
從公開/私密金鑰組取得公開金鑰。 金鑰組可以提供為密碼編譯服務提供者（CSP）內的金鑰容器名稱，或做為原始的位元組集合。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a>參數  
 `szKeyContainer`  
 在包含公開/私密金鑰組的金鑰容器名稱。 如果 `pbKeyBlob` 為 null， `szKeyContainer` 必須在 CSP 內指定有效的容器。 在此情況下， [ICLRStrongName：： StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md)方法會從儲存在容器中的金鑰組中，抽取出公開金鑰。  
  
 如果不 `pbKeyBlob` 是 null，則會假設金鑰組包含在金鑰二進位大型物件（BLOB）中。  
  
 金鑰必須是 1024-bit Rivest-Shamir-Adleman （RSA）簽署金鑰。 目前不支援其他類型的金鑰。  
  
 `pbKeyBlob`  
 在公開/私密金鑰組的指標。 這組會使用 Win32 函式所建立的格式 `CryptExportKey` 。 如果 `pbKeyBlob` 為 null，則會假設指定的金鑰容器 `szKeyContainer` 包含金鑰組。  
  
 `cbKeyBlob`  
 在的大小（以位元組為單位） `pbKeyBlob` 。  
  
 `ppbPublicKeyBlob`  
 脫銷傳回的公開金鑰 BLOB。 `ppbPublicKeyBlob`參數是由 common language runtime 配置，並傳回給呼叫端。 呼叫端必須使用[ICLRStrongName：： StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md)方法來釋放記憶體。  
  
 `pcbPublicKeyBlob`  
 脫銷傳回的公開金鑰 BLOB 的大小。  
  
## <a name="return-value"></a>傳回值  
 `S_OK`如果方法已成功完成，則為，否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。  
  
## <a name="remarks"></a>備註  
 公開金鑰包含在[PublicKeyBlob](../strong-naming/publickeyblob-structure.md)結構中。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameTokenFromPublicKey 方法](iclrstrongname-strongnametokenfrompublickey-method.md)
- [PublicKeyBlob 結構](../strong-naming/publickeyblob-structure.md)
- [ICLRStrongName 介面](iclrstrongname-interface.md)
