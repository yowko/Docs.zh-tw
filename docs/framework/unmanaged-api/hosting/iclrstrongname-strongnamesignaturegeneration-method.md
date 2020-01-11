---
title: ICLRStrongName::StrongNameSignatureGeneration 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureGeneration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureGeneration method [.NET Framework hosting]
ms.assetid: 4cdb1284-947a-4ed4-94c1-c5ff5cdfce56
topic_type:
- apiref
ms.openlocfilehash: ced7540afe931fb91240c770d76d205400157a51
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901094"
---
# <a name="iclrstrongnamestrongnamesignaturegeneration-method"></a>ICLRStrongName::StrongNameSignatureGeneration 方法
產生指定組件的強式名稱簽章。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT StrongNameSignatureGeneration (   
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
## <a name="parameters"></a>參數  
 `wszFilePath`  
 在檔案的路徑，該檔案包含將產生強式名稱簽章之元件的資訊清單。  
  
 `wszKeyContainer`  
 在包含公開/私密金鑰組的金鑰容器名稱。  
  
 如果 `pbKeyBlob` 為 null，`wszKeyContainer` 必須在密碼編譯服務提供者（CSP）內指定有效的容器。 在此情況下，會使用儲存在容器中的金鑰組來簽署檔案。  
  
 如果 `pbKeyBlob` 不是 null，則會假設金鑰組包含在金鑰二進位大型物件（BLOB）中。  
  
 金鑰必須是 1024-bit Rivest-Shamir-Adleman （RSA）簽署金鑰。 目前不支援其他類型的金鑰。  
  
 `pbKeyBlob`  
 在公開/私密金鑰組的指標。 這組會使用 Win32 `CryptExportKey` 函式所建立的格式。 如果 `pbKeyBlob` 是 null，則會假設 `wszKeyContainer` 指定的金鑰容器包含金鑰組。  
  
 `cbKeyBlob`  
 在`pbKeyBlob`的大小（以位元組為單位）。  
  
 `ppbSignatureBlob`  
 脫銷通用語言執行時間傳回簽章之位置的指標。 如果 `ppbSignatureBlob` 為 null，執行時間會將簽章儲存在 `wszFilePath`所指定的檔案中。  
  
 如果 `ppbSignatureBlob` 不是 null，通用語言執行時間會配置用來傳回簽章的空間。 呼叫端必須使用[ICLRStrongName：： StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)方法來釋放此空間。  
  
 `pcbSignatureBlob`  
 脫銷所傳回簽章的大小（以位元組為單位）。  
  
## <a name="return-value"></a>傳回值  
 如果方法順利完成，`S_OK`;否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。  
  
## <a name="remarks"></a>備註  
 為 `wszFilePath` 指定 null 以計算簽章的大小，而不建立簽章。  
  
 簽章可以直接儲存在檔案中，或傳回給呼叫端。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [StrongNameSignatureGenerationEx 方法](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [ICLRStrongName 介面](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
