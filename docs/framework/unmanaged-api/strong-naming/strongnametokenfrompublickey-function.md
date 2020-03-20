---
title: StrongNameTokenFromPublicKey 函式
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- StrongNameTokenFromPublicKey
helpviewer_keywords:
- StrongNameTokenFromPublicKey function [.NET Framework strong naming]
ms.assetid: 997e9e57-abb2-4217-bf20-1df621a75add
topic_type:
- apiref
ms.openlocfilehash: 20be3114908ef78966eead05ae8ba6333a491404
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175053"
---
# <a name="strongnametokenfrompublickey-function"></a>StrongNameTokenFromPublicKey 函式
取得代表公開金鑰的權杖。 強式名稱權杖是公開金鑰的縮寫形式。  
  
 此函數已被棄用。 改用[ICLR 強式名稱：：強式名稱權杖來自公共金鑰](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
BOOLEANStrongNameTokenFromPublicKey (
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a>參數  
 `pbPublicKeyBlob`  
 [在][公共金鑰Blob](publickeyblob-structure.md)類型的結構，其中包含用於生成強式名稱簽名的金鑰組的公共部分。  
  
 `cbPublicKeyBlob`  
 [在]的大小（以位元組為單位）的大小`pbPublicKeyBlob`。  
  
 `ppbStrongNameToken`  
 [出]與傳入的鍵對應的強式名稱權杖`pbPublicKeyBlob`。 通用語言運行時分配要返回權杖的記憶體。 調用方必須使用[StrongNameFreeBuffer](strongnamefreebuffer-function.md)函數釋放此記憶體。  
  
 `pcbStrongNameToken`  
 [出]返回的強式名稱權杖的大小（以位元組為單位）。  
  
## <a name="return-value"></a>傳回值  
 `true`成功完成;否則， `false`.  
  
## <a name="remarks"></a>備註  
 強式名稱權杖是公開金鑰的縮寫形式，用於在中繼資料中存儲關鍵資訊時節省空間。 具體而言，強式名稱權杖用於程式集引用以引用依存性程式集。  
  
 如果`StrongNameTokenFromPublicKey`函數未成功完成，請調用[StrongNameErrorInfo 函數](strongnameerrorinfo-function.md)以檢索上次生成的錯誤。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標題：** 強式名稱.h  
  
 **庫：** 作為資源包含在 mscoree.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameTokenFromPublicKey 方法](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [StrongNameGetPublicKey 方法](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [PublicKeyBlob 結構](publickeyblob-structure.md)
