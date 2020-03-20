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
ms.openlocfilehash: fcdd4a3f07b4499fd2388b5d165c409da9150466
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176925"
---
# <a name="strongnamegetpublickey-function"></a>StrongNameGetPublicKey 函式
從私密/公開金鑰組取得公開金鑰。 金鑰組可以作為加密服務提供者 （CSP） 中的金鑰容器名稱提供，也可以作為位元組的原創組合提供。  
  
 此函數已被棄用。 改用[ICLR 強式名稱：：強式名稱GetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md)方法。  
  
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
 [在]包含公開金鑰/私密金鑰對的金鑰容器的名稱。 如果`pbKeyBlob`為 null，`szKeyContainer`則必須在 CSP 中指定有效的容器。 在這種情況下，`StrongNameGetPublicKey`從容器中存儲的金鑰組中提取公開金鑰。  
  
 如果`pbKeyBlob`不是空，則假定金鑰組包含在金鑰二進位大型物件 （BLOB） 中。  
  
 金鑰必須是 1024 位裡維斯-沙米爾-阿德爾曼 （RSA） 簽名金鑰。 目前不支援其他類型的金鑰。  
  
 `pbKeyBlob`  
 [在]指向公開金鑰/私密金鑰對的指標。 此對採用 Win32`CryptExportKey`函數創建的格式。 如果`pbKeyBlob`為 null，則假定 指定的`szKeyContainer`鍵容器包含金鑰組。  
  
 `cbKeyBlob`  
 [在]的大小（以位元組為單位）的大小`pbKeyBlob`。  
  
 `ppbPublicKeyBlob`  
 [出]返回的公開金鑰 BLOB。 參數`ppbPublicKeyBlob`由通用語言運行時分配並返回到調用方。 調用方必須使用[StrongNameFreeBuffer](strongnamefreebuffer-function.md)函數釋放記憶體。  
  
 `pcbPublicKeyBlob`  
 [出]返回的公開金鑰 BLOB 的大小。  
  
## <a name="return-value"></a>傳回值  
 `true`成功完成;否則， `false`.  
  
## <a name="remarks"></a>備註  
 公開金鑰包含在[PublicKeyBlob](publickeyblob-structure.md)結構中。  
  
 如果`StrongNameGetPublicKey`函數未成功完成，請調用[StrongNameErrorInfo 函數](strongnameerrorinfo-function.md)以檢索上次生成的錯誤。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標題：** 強式名稱.h  
  
 **庫：** 作為資源包含在 MsCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameGetPublicKey 方法](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [StrongNameTokenFromPublicKey 方法](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)
- [PublicKeyBlob 結構](publickeyblob-structure.md)
