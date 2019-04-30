---
title: StrongNameSignatureGeneration 函式
ms.date: 03/30/2017
api_name:
- StrongNameSignatureGeneration
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration function [.NET Framework strong naming]
ms.assetid: 839b765c-3e41-44ce-bf1b-dc10453db18e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e7df65c28fad6fa79ec7a18d8511955330b2817
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049345"
---
# <a name="strongnamesignaturegeneration-function"></a>StrongNameSignatureGeneration 函式
產生指定組件的強式名稱簽章。  
  
 此函式已被取代。 使用[iclrstrongname:: Strongnamesignaturegeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)方法改為。  
  
## <a name="syntax"></a>語法  
  
```  
BOOLEAN StrongNameSignatureGeneration (   
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
 [in]包含產生的強式名稱簽章的組件資訊清單檔案的路徑。  
  
 `wszKeyContainer`  
 [in]包含 public/private 金鑰組的金鑰容器名稱。  
  
 如果`pbKeyBlob`為 null，`wszKeyContainer`必須指定有效的容器內的密碼編譯服務提供者 (CSP)。 在此情況下，儲存在容器中的金鑰組來簽署檔案。  
  
 如果`pbKeyBlob`不是 null，金鑰組會假設要包含在索引鍵二進位大型物件 (BLOB)。  
  
 索引鍵必須是 1024年位元 Rivest-shamir-adleman/digital signature Standard (RSA) 簽署金鑰。 目前支援其他類型的金鑰。  
  
 `pbKeyBlob`  
 [in]Public/private 金鑰組指標。 此配對的格式建立 win32`CryptExportKey`函式。 如果`pbKeyBlob`是 null，藉由指定之金鑰容器`wszKeyContainer`會假設包含金鑰組。  
  
 `cbKeyBlob`  
 [in]大小，以位元組為單位的`pbKeyBlob`。  
  
 `ppbSignatureBlob`  
 [out]Common language runtime 會傳回簽章的位置指標。 如果`ppbSignatureBlob`是 null，執行階段存放區簽章中所指定的檔案`wszFilePath`。  
  
 如果`ppbSignatureBlob`是不是 null，common language runtime 配置的空間，在其中傳回的簽章。 呼叫端必須使用此空間釋放[StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)函式。  
  
 `pcbSignatureBlob`  
 [out]大小，以位元組為單位傳回的簽章。  
  
## <a name="return-value"></a>傳回值  
 `true` 如果成功地完成;否則， `false`。  
  
## <a name="remarks"></a>備註  
 指定 null`wszFilePath`來計算簽章的大小，而不需建立簽章。  
  
 簽章可以是直接存放在檔案中，或傳回給呼叫端。  
  
 如果`StrongNameSignatureGeneration`函式未順利完成，請呼叫[StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)函式來擷取最後一個產生的錯誤。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** StrongName.h  
  
 **LIBRARY:** 包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameSignatureGeneration 方法](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [StrongNameSignatureGenerationEx 方法](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [ICLRStrongName 介面](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
