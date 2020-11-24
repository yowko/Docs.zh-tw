---
title: ICLRStrongName::StrongNameTokenFromAssemblyEx 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameTokenFromAssemblyEx method [.NET Framework hosting]
ms.assetid: 648ea90e-5e60-40a0-a56a-3e61bf2fba7c
topic_type:
- apiref
ms.openlocfilehash: 35fe86f856360814cfbb5453bfb6e5efaaef02fd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677722"
---
# <a name="iclrstrongnamestrongnametokenfromassemblyex-method"></a>ICLRStrongName::StrongNameTokenFromAssemblyEx 方法

從指定的元件檔案建立強式名稱權杖，並傳回權杖所代表的公開金鑰。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a>參數  

 `wszFilePath`  
 在元件的可攜式可執行檔 (PE) 檔的路徑。  
  
 `ppbStrongNameToken`  
 擴展傳回的強式名稱 token。  
  
 `pcbStrongNameToken`  
 擴展強式名稱權杖的大小（以位元組為單位）。  
  
 `ppbPublicKeyBlob`  
 擴展傳回的公開金鑰。  
  
 `pcbPublicKeyBlob`  
 擴展公開金鑰的大小（以位元組為單位）。  
  
## <a name="return-value"></a>傳回值  

 `S_OK` 如果方法成功完成，則為，否則，表示失敗 (的 HRESULT 值會看到清單) 的 [一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values) 。  
  
## <a name="remarks"></a>備註  

 強式名稱權杖是公開金鑰的縮寫形式。 權杖是從用來簽署元件的公開金鑰建立的64位雜湊。 權杖是元件強式名稱的一部分，而且可以從元件中繼資料讀取。  
  
 在抓取金鑰並建立權杖之後，您應該呼叫 [ICLRStrongName：： StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) 方法來釋放已配置的記憶體。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameTokenFromAssembly 方法](iclrstrongname-strongnametokenfromassembly-method.md)
- [ICLRStrongName 介面](iclrstrongname-interface.md)
