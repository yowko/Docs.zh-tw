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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2acade14f9d30ca7bf0d098d6f58c80a367f621c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795937"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a>ICLRStrongName::StrongNameGetPublicKey 方法
取得從公開/私密金鑰組的公開金鑰。 可以提供的金鑰組，做為密碼編譯服務提供者 (CSP) 內的金鑰容器名稱，或是為未經處理位元組的集合。  
  
## <a name="syntax"></a>語法  
  
```  
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
 [in]包含 public/private 金鑰組的金鑰容器名稱。 如果`pbKeyBlob`為 null，`szKeyContainer`必須指定 CSP 內是有效的容器。 在此情況下， [iclrstrongname:: Strongnamegetpublickey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)方法會從容器中所儲存的金鑰組擷取公開金鑰。  
  
 如果`pbKeyBlob`不是 null，金鑰組會假設要包含在索引鍵二進位大型物件 (BLOB)。  
  
 索引鍵必須是 1024年位元 Rivest-shamir-adleman/digital signature Standard (RSA) 簽署金鑰。 目前支援其他類型的金鑰。  
  
 `pbKeyBlob`  
 [in]Public/private 金鑰組指標。 此配對的格式建立 win32`CryptExportKey`函式。 如果`pbKeyBlob`是 null，藉由指定之金鑰容器`szKeyContainer`會假設包含金鑰組。  
  
 `cbKeyBlob`  
 [in]大小，以位元組為單位的`pbKeyBlob`。  
  
 `ppbPublicKeyBlob`  
 [out]傳回的公開金鑰 BLOB。 `ppbPublicKeyBlob`參數是由 common language runtime 配置，並傳回給呼叫端。 呼叫端必須使用釋放記憶體[iclrstrongname:: Strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)方法。  
  
 `pcbPublicKeyBlob`  
 [out]傳回的公開金鑰 BLOB 的大小。  
  
## <a name="return-value"></a>傳回值  
 `S_OK` 如果這個方法順利完成否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)清單)。  
  
## <a name="remarks"></a>備註  
 中包含的公開金鑰[PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)結構。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameTokenFromPublicKey 方法](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [PublicKeyBlob 結構](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [ICLRStrongName 介面](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
