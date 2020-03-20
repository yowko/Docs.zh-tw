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
ms.openlocfilehash: d7f481e5c61ec65d2e7414bd47227866f3435028
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176899"
---
# <a name="strongnamesignaturegeneration-function"></a>StrongNameSignatureGeneration 函式
產生指定組件的強式名稱簽章。  
  
 此函數已被棄用。 改用[ICLR 強式名稱：：強式名稱簽名生成](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)方法。  
  
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
 [在]包含將為其生成強式名稱簽名的組件資訊清單的檔的路徑。  
  
 `wszKeyContainer`  
 [在]包含公開金鑰/私密金鑰對的金鑰容器的名稱。  
  
 如果`pbKeyBlob`為 null，`wszKeyContainer`則必須在加密服務提供者 （CSP） 中指定有效的容器。 在這種情況下，存儲在容器中的金鑰組用於對檔進行簽名。  
  
 如果`pbKeyBlob`不是空，則假定金鑰組包含在金鑰二進位大型物件 （BLOB） 中。  
  
 金鑰必須是 1024 位裡維斯-沙米爾-阿德爾曼 （RSA） 簽名金鑰。 目前不支援其他類型的金鑰。  
  
 `pbKeyBlob`  
 [在]指向公開金鑰/私密金鑰對的指標。 此對採用 Win32`CryptExportKey`函數創建的格式。 如果`pbKeyBlob`為 null，則假定 指定的`wszKeyContainer`鍵容器包含金鑰組。  
  
 `cbKeyBlob`  
 [在]的大小（以位元組為單位）的大小`pbKeyBlob`。  
  
 `ppbSignatureBlob`  
 [出]指向公共語言運行時返回簽名的位置的指標。 如果`ppbSignatureBlob`為 null，運行時將簽名存儲在 指定的`wszFilePath`檔中。  
  
 如果`ppbSignatureBlob`為 null，則通用語言運行時會分配用於返回簽名的空間。 調用方必須使用[強式名稱自由緩衝區](strongnamefreebuffer-function.md)函數釋放此空間。  
  
 `pcbSignatureBlob`  
 [出]返回的簽名的大小（以位元組為單位）。  
  
## <a name="return-value"></a>傳回值  
 `true`成功完成;否則， `false`.  
  
## <a name="remarks"></a>備註  
 指定 null`wszFilePath`以計算簽名的大小而不創建簽名。  
  
 簽名可以直接存儲在檔中，也可以返回到調用方。  
  
 如果`StrongNameSignatureGeneration`函數未成功完成，請調用[StrongNameErrorInfo 函數](strongnameerrorinfo-function.md)以檢索上次生成的錯誤。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標題：** 強式名稱.h  
  
 **庫：** 作為資源包含在 MsCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameSignatureGeneration 方法](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [StrongNameSignatureGenerationEx 方法](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)
