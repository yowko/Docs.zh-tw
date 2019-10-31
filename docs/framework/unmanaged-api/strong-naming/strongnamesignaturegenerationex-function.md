---
title: StrongNameSignatureGenerationEx 函式
ms.date: 03/30/2017
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
ms.openlocfilehash: e8f63a6379af8f2b7b88c511840622d49d65d587
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141582"
---
# <a name="strongnamesignaturegenerationex-function"></a>StrongNameSignatureGenerationEx 函式
根據指定的旗標，產生指定元件的強式名稱簽章。  
  
 這個函數已被取代。 請改用[ICLRStrongName：： StrongNameSignatureGenerationEx](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
  
## <a name="parameters"></a>參數  
 `wszFilePath`  
 在檔案的路徑，該檔案包含將產生強式名稱簽章之元件的資訊清單。  
  
 `wszKeyContainer`  
 在包含公開/私密金鑰組的金鑰容器名稱。  
  
 如果 `pbKeyBlob` 為 null，`wszKeyContainer` 必須在密碼編譯服務提供者（CSP）內指定有效的容器。 在此情況下，會使用儲存在容器中的金鑰組來簽署檔案。  
  
 如果 `pbKeyBlob` 不是 null，則會假設金鑰組包含在金鑰二進位大型物件（BLOB）中。  
  
 `pbKeyBlob`  
 在公開/私密金鑰組的指標。 這組會使用 Win32 `CryptExportKey` 函式所建立的格式。 如果 `pbKeyBlob` 是 null，則會假設 `wszKeyContainer` 指定的金鑰容器包含金鑰組。  
  
 `cbKeyBlob`  
 在`pbKeyBlob`的大小（以位元組為單位）。  
  
 `ppbSignatureBlob`  
 脫銷通用語言執行時間傳回簽章之位置的指標。 如果 `ppbSignatureBlob` 為 null，執行時間會將簽章儲存在 `wszFilePath`所指定的檔案中。  
  
 如果 `ppbSignatureBlob` 不是 null，通用語言執行時間會配置用來傳回簽章的空間。 呼叫端必須使用[StrongNameFreeBuffer](strongnamefreebuffer-function.md)函數釋放此空間。  
  
 `pcbSignatureBlob`  
 脫銷所傳回簽章的大小（以位元組為單位）。  
  
 `dwFlags`  
 在下列一個或多個值：  
  
- `SN_SIGN_ALL_FILES` （0x00000001）-重新計算連結模組的所有雜湊。  
  
- `SN_TEST_SIGN` （0x00000002）-測試-簽署元件。  
  
## <a name="return-value"></a>傳回值  
 成功完成時 `true`;否則，`false`。  
  
## <a name="remarks"></a>備註  
 為 `wszFilePath` 指定 null 以計算簽章的大小，而不建立簽章。  
  
 簽章可以直接儲存在檔案中，或傳回給呼叫端。  
  
 如果指定了 `SN_SIGN_ALL_FILES`，但不包含公開金鑰（`pbKeyBlob` 和 `wszFilePath` 都是 null），則會重新計算連結模組的雜湊，但不會重新簽署元件。  
  
 如果指定了 `SN_TEST_SIGN`，則不會修改 common language runtime 標頭，以指出元件是以強式名稱簽署。  
  
 如果 `StrongNameSignatureGenerationEx` 函式未順利完成，請呼叫[StrongNameErrorInfo](strongnameerrorinfo-function.md)函式，以取出最後產生的錯誤。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Stackexchange.redis.strongname。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [StrongNameSignatureGenerationEx 方法](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [StrongNameSignatureGeneration 方法](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)
