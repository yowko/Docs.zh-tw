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
ms.openlocfilehash: cb96c7e17627205db0573e56fc8c2a29e7717434
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181928"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a>ICLRStrongName::StrongNameGetPublicKey 方法
從公開金鑰/私密金鑰對獲取公開金鑰。 金鑰組可以作為加密服務提供者 （CSP） 中的金鑰容器名稱提供，也可以作為位元組的原創組合提供。  
  
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
 [在]包含公開金鑰/私密金鑰對的金鑰容器的名稱。 如果`pbKeyBlob`為 null，`szKeyContainer`則必須在 CSP 中指定有效的容器。 在這種情況下[，ICLRStrongNameName：：StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)方法從存儲在容器中的金鑰組中提取公開金鑰。  
  
 如果`pbKeyBlob`不是空，則假定金鑰組包含在金鑰二進位大型物件 （BLOB） 中。  
  
 金鑰必須是 1024 位裡維斯-沙米爾-阿德爾曼 （RSA） 簽名金鑰。 目前不支援其他類型的金鑰。  
  
 `pbKeyBlob`  
 [在]指向公開金鑰/私密金鑰對的指標。 此對採用 Win32`CryptExportKey`函數創建的格式。 如果`pbKeyBlob`為 null，則假定 指定的`szKeyContainer`鍵容器包含金鑰組。  
  
 `cbKeyBlob`  
 [在]的大小（以位元組為單位）的大小`pbKeyBlob`。  
  
 `ppbPublicKeyBlob`  
 [出]返回的公開金鑰 BLOB。 參數`ppbPublicKeyBlob`由通用語言運行時分配並返回到調用方。 調用方必須使用[ICLRStrongNameName：：StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)方法釋放記憶體。  
  
 `pcbPublicKeyBlob`  
 [出]返回的公開金鑰 BLOB 的大小。  
  
## <a name="return-value"></a>傳回值  
 `S_OK`如果方法成功完成;如果方法成功完成;否則，指示失敗的 HRESULT 值（請參閱清單[的常用 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。  
  
## <a name="remarks"></a>備註  
 公開金鑰包含在[PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)結構中。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** MetaHost.h  
  
 **庫：** 作為資源包含在 MSCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameTokenFromPublicKey 方法](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [PublicKeyBlob 結構](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [ICLRStrongName 介面](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
