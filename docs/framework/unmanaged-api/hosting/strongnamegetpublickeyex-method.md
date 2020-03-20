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
ms.openlocfilehash: 93afe1afd9ea9637d039a8b4a4e81267d49c08b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176223"
---
# <a name="strongnamegetpublickeyex-method"></a>StrongNameGetPublicKeyEx 方法
從公開金鑰/私密金鑰對獲取公開金鑰，並指定雜湊演算法和簽名演算法。  
  
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
 [在]包含公開金鑰/私密金鑰對的金鑰容器的名稱。 如果`pbKeyBlob`為 null，`szKeyContainer`則必須在加密服務提供者 （CSP） 中指定有效的容器。 在這種情況下，`StrongNameGetPublicKeyEx`該方法從存儲在容器中的金鑰組中提取公開金鑰。  
  
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
  
 `uHashAlgId`  
 [在]程式集雜湊演算法。 有關已接受值的清單，請參閱備註部分。  
  
 `uReserved`  
 [在]保留供將來使用;預設值為 null。  
  
## <a name="return-value"></a>傳回值  
 `S_OK`如果方法成功完成;如果方法成功完成;否則，指示失敗的 HRESULT 值（請參閱清單[的常用 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。  
  
## <a name="remarks"></a>備註  
 公開金鑰包含在[PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)結構中。  
  
## <a name="remarks"></a>備註  
 下表顯示了`uHashAlgId`參數的接受值集。  
  
|名稱|值|  
|----------|-----------|  
|None|0|  
|SHA-1|0 x8004|  
|SHA-256|0x800c|  
|SHA-384|0x800d|  
|SHA-512|0x800e|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** MetaHost.h  
  
 **庫：** 作為資源包含在 MSCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameTokenFromPublicKey 方法](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [PublicKeyBlob 結構](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [ICLRStrongName 介面](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [StrongNameGetPublicKey 方法](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
