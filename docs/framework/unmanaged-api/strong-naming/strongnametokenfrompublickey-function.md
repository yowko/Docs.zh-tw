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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 197504cbb0dd66c0cf43dee718026fc63e918d60
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798858"
---
# <a name="strongnametokenfrompublickey-function"></a>StrongNameTokenFromPublicKey 函式
取得代表公開金鑰的權杖。 強式名稱 token 是公用金鑰的縮寫格式。  
  
 這個函數已被取代。 請改用[ICLRStrongName：： StrongNameTokenFromPublicKey](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)方法。  
  
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
 在[PublicKeyBlob](publickeyblob-structure.md)類型的結構，其中包含用來產生強式名稱簽章之金鑰組的公開部分。  
  
 `cbPublicKeyBlob`  
 在的大小（以位元組為單位`pbPublicKeyBlob`）。  
  
 `ppbStrongNameToken`  
 脫銷對應至傳入`pbPublicKeyBlob`之金鑰的強式名稱 token。 Common language runtime 會配置要在其中傳回 token 的記憶體。 呼叫端必須使用[StrongNameFreeBuffer](strongnamefreebuffer-function.md)函數釋放這個記憶體。  
  
 `pcbStrongNameToken`  
 脫銷傳回之強式名稱 token 的大小（以位元組為單位）。  
  
## <a name="return-value"></a>傳回值  
 `true`成功完成時;否則為`false`。  
  
## <a name="remarks"></a>備註  
 強式名稱 token 是在將金鑰資訊儲存在中繼資料中時，用來節省空間的公用金鑰的簡短形式。 具體而言，強式名稱標記會在元件參考中用來參考相依元件。  
  
 如果 `StrongNameTokenFromPublicKey` 函式未順利完成，請呼叫 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 函式，以取出最後產生的錯誤。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Stackexchange.redis.strongname。h  
  
 **LIBRARY:** 包含為 mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameTokenFromPublicKey 方法](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [StrongNameGetPublicKey 方法](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [PublicKeyBlob 結構](publickeyblob-structure.md)
