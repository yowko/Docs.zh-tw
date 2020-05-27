---
title: StrongNameGetPublicKeyEx 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameGetPublicKeyEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameGetPublicKeyEx
helpviewer_keywords:
- StrongNameGetPublicKeyEx method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameGetPublicKeyEx method [.NET Framework hosting]
ms.assetid: 63d8260c-fb32-4f8f-a357-768afd570f68
topic_type:
- apiref
ms.openlocfilehash: 1904a98f254a988ce035847a4cdeede182aa07bf
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006368"
---
# <a name="strongnamegetpublickeyex-method"></a>StrongNameGetPublicKeyEx 方法
從公開/私密金鑰組取得公開金鑰，並指定雜湊演算法和簽章演算法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   pwzKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
    [in]  ULONG     uHashAlgId,  
    [in]  ULONG     uReserved,  
);  
```  
  
## <a name="parameters"></a>參數  
 `pwzKeyContainer`  
 在包含公開/私密金鑰組的金鑰容器名稱。 如果 `pbKeyBlob` 為 null， `szKeyContainer` 必須在密碼編譯服務提供者（CSP）內指定有效的容器。 在此情況下， `StrongNameGetPublicKeyEx` 方法會從儲存在容器中的金鑰組中解壓縮公開金鑰。  
  
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
  
 `uHashAlgId`  
 在元件雜湊演算法。 如需接受值的清單，請參閱備註一節。  
  
 `uReserved`  
 在保留供日後使用;預設值為 null。  
  
## <a name="return-value"></a>傳回值  
 `S_OK`如果方法已成功完成，則為，否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。  
  
## <a name="remarks"></a>備註  
 公開金鑰包含在[PublicKeyBlob](../strong-naming/publickeyblob-structure.md)結構中。  
  
## <a name="remarks"></a>備註  
 下表顯示參數的可接受值集 `uHashAlgId` 。  
  
|Name|值|  
|----------|-----------|  
|無|0|  
|SHA-1|0x8004|  
|SHA-256|0x800c|  
|SHA-384|0x800d|  
|SHA-512|0x800e|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameTokenFromPublicKey 方法](iclrstrongname-strongnametokenfrompublickey-method.md)
- [PublicKeyBlob 結構](../strong-naming/publickeyblob-structure.md)
- [ICLRStrongName 介面](iclrstrongname-interface.md)
- [StrongNameGetPublicKey 方法](iclrstrongname-strongnamegetpublickey-method.md)
