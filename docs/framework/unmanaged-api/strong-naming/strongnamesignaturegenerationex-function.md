---
title: "StrongNameSignatureGenerationEx 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- StrongNameSignatureGenerationEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureGenerationEx
helpviewer_keywords:
- StrongNameSignatureGenerationEx function [.NET Framework strong naming]
ms.assetid: 9a75469e-aa49-4e32-ad48-3bafd5202f09
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4f68befd145649e6d8921e160d302cdb81000a9a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamesignaturegenerationex-function"></a>StrongNameSignatureGenerationEx 函式
產生強式名稱簽章的指定組件中，根據指定的旗標。  
  
 此函式已被取代。 使用[iclrstrongname:: Strongnamesignaturegenerationex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)方法改為。  
  
## <a name="syntax"></a>語法  
  
```  
BOOLEAN StrongNameSignatureGenerationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob,  
    [in]  DWORD     dwFlags  
);  
```  
  
#### <a name="parameters"></a>參數  
 `wszFilePath`  
 [in]包含產生強式名稱簽章的組件資訊清單檔案的路徑。  
  
 `wszKeyContainer`  
 [in]包含 public/private 金鑰組的金鑰容器名稱。  
  
 如果`pbKeyBlob`為 null，`wszKeyContainer`必須指定有效的容器內的密碼編譯服務提供者 (CSP)。 在此情況下，儲存在容器中的金鑰組用來簽署檔案。  
  
 如果`pbKeyBlob`不是 null，金鑰組會假設要包含在索引鍵二進位大型物件 (BLOB)。  
  
 `pbKeyBlob`  
 [in]公開/私密金鑰組指標。 此配對的格式建立 win32`CryptExportKey`函式。 如果`pbKeyBlob`是 null，所指定的金鑰容器`wszKeyContainer`假設為包含金鑰組。  
  
 `cbKeyBlob`  
 [in]大小，以位元組為單位的`pbKeyBlob`。  
  
 `ppbSignatureBlob`  
 [out]Common language runtime 會回到此處簽章的位置指標。 如果`ppbSignatureBlob`是 null，執行階段會儲存簽章中所指定的檔案`wszFilePath`。  
  
 如果`ppbSignatureBlob`是不是 null，common language runtime 配置的空間，以傳回簽章。 呼叫端必須釋放此空間使用[StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)函式。  
  
 `pcbSignatureBlob`  
 [out]大小，以位元組為單位傳回的簽章。  
  
 `dwFlags`  
 [in]一或多個下列值：  
  
-   `SN_SIGN_ALL_FILES`(0x00000001)-重新整理所有連結模組雜湊。  
  
-   `SN_TEST_SIGN`(0x00000002)-測試簽署組件。  
  
## <a name="return-value"></a>傳回值  
 `true`如果成功地完成。否則， `false`。  
  
## <a name="remarks"></a>備註  
 指定 null`wszFilePath`計算簽章的大小，而不需要建立簽章。  
  
 簽章可以直接儲存在檔案中，或傳回給呼叫者。  
  
 如果`SN_SIGN_ALL_FILES`指定，但不包含公開金鑰 (兩者`pbKeyBlob`和`wszFilePath`都是 null)，連結模組的雜湊都會重新計算，但不重新簽署組件。  
  
 如果`SN_TEST_SIGN`指定，則表示組件已簽署為強式名稱不會修改通用語言執行階段標頭。  
  
 如果`StrongNameSignatureGenerationEx`函式未順利完成，請呼叫[StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)函式可擷取的最後一個產生的錯誤。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** StrongName.h  
  
 **程式庫：**包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [StrongNameSignatureGenerationEx 方法](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)  
 [StrongNameSignatureGeneration 方法](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)  
 [ICLRStrongName 介面](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
