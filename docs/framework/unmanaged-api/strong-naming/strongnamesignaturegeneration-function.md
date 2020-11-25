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
ms.openlocfilehash: 78a89c07b9a7ddbccee9716de37c96d23635f87b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708521"
---
# <a name="strongnamesignaturegeneration-function"></a>StrongNameSignatureGeneration 函式

產生指定組件的強式名稱簽章。  
  
 此函數已被取代。 請改用 [ICLRStrongName：： StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) 方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
 在檔案的路徑，該檔案包含將產生強式名稱簽章之元件的資訊清單。  
  
 `wszKeyContainer`  
 在包含公開/私密金鑰組的金鑰容器名稱。  
  
 如果 `pbKeyBlob` 是 null，則 `wszKeyContainer` 必須在密碼編譯服務提供者中指定有效的容器， (CSP) 。 在此情況下，會使用儲存在容器中的金鑰組來簽署檔案。  
  
 如果不 `pbKeyBlob` 是 null，則會假設金鑰組包含在 (BLOB) 的金鑰二進位大型物件中。  
  
 金鑰必須是 1024-bit Rivest-Shamir-Adleman (RSA) 簽署金鑰。 目前不支援其他類型的金鑰。  
  
 `pbKeyBlob`  
 在公開/私密金鑰組的指標。 此配對的格式是 Win32 函數所建立的格式 `CryptExportKey` 。 如果 `pbKeyBlob` 是 null，則會假設指定的金鑰容器 `wszKeyContainer` 包含金鑰組。  
  
 `cbKeyBlob`  
 在的大小（以位元組為單位） `pbKeyBlob` 。  
  
 `ppbSignatureBlob`  
 擴展Common language runtime 傳回簽章之位置的指標。 如果 `ppbSignatureBlob` 是 null，則執行時間會將簽章儲存在所指定的檔案中 `wszFilePath` 。  
  
 如果不 `ppbSignatureBlob` 是 null，則 common language runtime 會配置要傳回簽章的空間。 呼叫端必須使用 [StrongNameFreeBuffer](strongnamefreebuffer-function.md) 函式釋放此空間。  
  
 `pcbSignatureBlob`  
 擴展所傳回簽章的大小（以位元組為單位）。  
  
## <a name="return-value"></a>傳回值  

 `true` 成功完成時;否則為 `false` 。  
  
## <a name="remarks"></a>備註  

 針對計算簽章的 `wszFilePath` 大小而不建立簽章，請指定 null。  
  
 簽章可以直接儲存在檔案中，或傳回給呼叫端。  
  
 如果函式 `StrongNameSignatureGeneration` 未順利完成，請呼叫 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 函式來取出最後產生的錯誤。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Stackexchange.redis.strongname。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameSignatureGeneration 方法](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [StrongNameSignatureGenerationEx 方法](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)
