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
ms.openlocfilehash: 8cc28d9ccd40c65d225a96b269562c9d3dfa2124
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729885"
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
 在包含公開/私密金鑰組的金鑰容器名稱。 如果 `pbKeyBlob` 是 null，則 `szKeyContainer` 必須在密碼編譯服務提供者中指定有效的容器， (CSP) 。 在此情況下， `StrongNameGetPublicKeyEx` 方法會從儲存在容器中的金鑰組解壓縮公開金鑰。  
  
 如果不 `pbKeyBlob` 是 null，則會假設金鑰組包含在 (BLOB) 的金鑰二進位大型物件中。  
  
 金鑰必須是 1024-bit Rivest-Shamir-Adleman (RSA) 簽署金鑰。 目前不支援其他類型的金鑰。  
  
 `pbKeyBlob`  
 在公開/私密金鑰組的指標。 此配對的格式是 Win32 函數所建立的格式 `CryptExportKey` 。 如果 `pbKeyBlob` 是 null，則會假設指定的金鑰容器 `szKeyContainer` 包含金鑰組。  
  
 `cbKeyBlob`  
 在的大小（以位元組為單位） `pbKeyBlob` 。  
  
 `ppbPublicKeyBlob`  
 擴展傳回的公開金鑰 BLOB。 `ppbPublicKeyBlob`參數是由 common language runtime 所配置，並傳回給呼叫端。 呼叫端必須使用 [ICLRStrongName：： StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) 方法釋放記憶體。  
  
 `pcbPublicKeyBlob`  
 擴展傳回之公開金鑰 BLOB 的大小。  
  
 `uHashAlgId`  
 在元件雜湊演算法。 如需接受值的清單，請參閱「備註」一節。  
  
 `uReserved`  
 在保留供日後使用;預設值為 null。  
  
## <a name="return-value"></a>傳回值  

 `S_OK` 如果方法成功完成，則為，否則，表示失敗 (的 HRESULT 值會看到清單) 的 [一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values) 。  
  
## <a name="remarks"></a>備註  

 公開金鑰包含在 [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) 結構中。  
  
## <a name="remarks"></a>備註  

 下表顯示參數接受的值集 `uHashAlgId` 。  
  
|名稱|值|  
|----------|-----------|  
|None|0|  
|SHA-1|0x8004|  
|SHA-256|0x800c|  
|SHA-384|0x800d|  
|SHA-512|0x800e|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameTokenFromPublicKey 方法](iclrstrongname-strongnametokenfrompublickey-method.md)
- [PublicKeyBlob 結構](../strong-naming/publickeyblob-structure.md)
- [ICLRStrongName 介面](iclrstrongname-interface.md)
- [StrongNameGetPublicKey 方法](iclrstrongname-strongnamegetpublickey-method.md)
