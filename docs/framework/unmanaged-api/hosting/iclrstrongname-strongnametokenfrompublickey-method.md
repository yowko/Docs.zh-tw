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
ms.openlocfilehash: c727d4524bc40ab90eee90faf16788140a73ad9a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677657"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a>ICLRStrongName::StrongNameTokenFromPublicKey 方法

取得代表公開金鑰的 token。 強式名稱權杖是公開金鑰的縮寫形式。  
  
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
 在 [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) 類型的結構，其中包含用來產生強式名稱簽章之金鑰組的公開部分。  
  
 `cbPublicKeyBlob`  
 在的大小（以位元組為單位） `pbPublicKeyBlob` 。  
  
 `ppbStrongNameToken`  
 擴展與傳入的金鑰組應的強式名稱標記 `pbPublicKeyBlob` 。 Common language runtime 會配置要傳回權杖的記憶體。 呼叫端必須使用 [ICLRStrongName：： StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) 方法釋放這個記憶體。  
  
 `pcbStrongNameToken`  
 擴展傳回之強式名稱 token 的大小（以位元組為單位）。  
  
## <a name="return-value"></a>傳回值  

 `S_OK` 如果方法成功完成，則為，否則，表示失敗 (的 HRESULT 值會看到清單) 的 [一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values) 。  
  
## <a name="remarks"></a>備註  

 強式名稱權杖是公開金鑰的縮寫形式，用來節省在中繼資料中儲存金鑰資訊時的空間。 具體而言，強式名稱標記會在元件參考中用來參考相依元件。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結 **庫：** 以資源的形式包含在 mscoree.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameGetPublicKey 方法](iclrstrongname-strongnamegetpublickey-method.md)
- [PublicKeyBlob 結構](../strong-naming/publickeyblob-structure.md)
- [ICLRStrongName 介面](iclrstrongname-interface.md)
