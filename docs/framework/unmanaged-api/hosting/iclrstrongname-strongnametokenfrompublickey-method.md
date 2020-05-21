---
title: ICLRStrongName::StrongNameTokenFromPublicKey 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey method [.NET Framework hosting]
- StrongNameTokenFromPublicKey method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 7962ce88-7e86-4a6f-8298-621b01ffc3c2
topic_type:
- apiref
ms.openlocfilehash: e61a652072b424d1245518c832f9b0856e0f2021
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762600"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a>ICLRStrongName::StrongNameTokenFromPublicKey 方法
取得表示公開金鑰的 token。 強式名稱 token 是公用金鑰的縮寫格式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT StrongNameTokenFromPublicKey (
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a>參數  
 `pbPublicKeyBlob`  
 在[PublicKeyBlob](../strong-naming/publickeyblob-structure.md)類型的結構，其中包含用來產生強式名稱簽章之金鑰組的公開部分。  
  
 `cbPublicKeyBlob`  
 在的大小（以位元組為單位） `pbPublicKeyBlob` 。  
  
 `ppbStrongNameToken`  
 脫銷對應至傳入之金鑰的強式名稱 token `pbPublicKeyBlob` 。 Common language runtime 會配置要在其中傳回 token 的記憶體。 呼叫端必須使用[ICLRStrongName：： StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md)方法來釋放這個記憶體。  
  
 `pcbStrongNameToken`  
 脫銷傳回之強式名稱 token 的大小（以位元組為單位）。  
  
## <a name="return-value"></a>傳回值  
 `S_OK`如果方法已成功完成，則為，否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。  
  
## <a name="remarks"></a>備註  
 強式名稱 token 是公用金鑰的簡短形式，用來儲存中繼資料中的金鑰資訊時，用來節省空間。 具體而言，強式名稱標記會在元件參考中用來參考相依元件。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結**庫：** 包含為 mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameGetPublicKey 方法](iclrstrongname-strongnamegetpublickey-method.md)
- [PublicKeyBlob 結構](../strong-naming/publickeyblob-structure.md)
- [ICLRStrongName 介面](iclrstrongname-interface.md)
