---
title: StrongNameGetPublicKey 函式
ms.date: 03/30/2017
api_name:
- StrongNameGetPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey function [.NET Framework strong naming]
ms.assetid: 5b58c87f-3f72-40df-9b9a-291076931cc3
topic_type:
- apiref
ms.openlocfilehash: c97cc0c1d4c022583d0823abeff998e2ed5f719e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710970"
---
# <a name="strongnamegetpublickey-function"></a>StrongNameGetPublicKey 函式

從私密/公開金鑰組取得公開金鑰。 金鑰組可以在密碼編譯服務提供者中提供作為金鑰容器名稱， (CSP) 或原始的位元組集合。  
  
 此函數已被取代。 請改用 [ICLRStrongName：： StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md) 方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
BOOLEAN StrongNameGetPublicKey (
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a>參數  

 `szKeyContainer`  
 在包含公開/私密金鑰組的金鑰容器名稱。 如果 `pbKeyBlob` 是 null，則 `szKeyContainer` 必須在 CSP 內指定有效的容器。 在此情況下，請 `StrongNameGetPublicKey` 從儲存在容器中的金鑰組解壓縮公開金鑰。  
  
 如果不 `pbKeyBlob` 是 null，則會假設金鑰組包含在 (BLOB) 的金鑰二進位大型物件中。  
  
 金鑰必須是 1024-bit Rivest-Shamir-Adleman (RSA) 簽署金鑰。 目前不支援其他類型的金鑰。  
  
 `pbKeyBlob`  
 在公開/私密金鑰組的指標。 此配對的格式是 Win32 函數所建立的格式 `CryptExportKey` 。 如果 `pbKeyBlob` 是 null，則會假設指定的金鑰容器 `szKeyContainer` 包含金鑰組。  
  
 `cbKeyBlob`  
 在的大小（以位元組為單位） `pbKeyBlob` 。  
  
 `ppbPublicKeyBlob`  
 擴展傳回的公開金鑰 BLOB。 `ppbPublicKeyBlob`參數是由 common language runtime 所配置，並傳回給呼叫端。 呼叫端必須使用 [StrongNameFreeBuffer](strongnamefreebuffer-function.md) 函數釋放記憶體。  
  
 `pcbPublicKeyBlob`  
 擴展傳回之公開金鑰 BLOB 的大小。  
  
## <a name="return-value"></a>傳回值  

 `true` 成功完成時;否則為 `false` 。  
  
## <a name="remarks"></a>備註  

 公開金鑰包含在 [PublicKeyBlob](publickeyblob-structure.md) 結構中。  
  
 如果函式 `StrongNameGetPublicKey` 未順利完成，請呼叫 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 函式來取出最後產生的錯誤。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Stackexchange.redis.strongname。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameGetPublicKey 方法](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [StrongNameTokenFromPublicKey 方法](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)
- [PublicKeyBlob 結構](publickeyblob-structure.md)
