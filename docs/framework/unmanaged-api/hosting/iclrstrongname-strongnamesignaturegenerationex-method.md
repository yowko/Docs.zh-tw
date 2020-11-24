---
title: ICLRStrongName::StrongNameSignatureGenerationEx 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureGenerationEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureGenerationEx
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureGenerationEx method [.NET Framework hosting]
- StrongNameSignatureGenerationEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: c3f34584-c6e2-41fd-bb44-e44da8546309
topic_type:
- apiref
ms.openlocfilehash: 78cc043953e6288df136b43590831569d112afef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674511"
---
# <a name="iclrstrongnamestrongnamesignaturegenerationex-method"></a>ICLRStrongName::StrongNameSignatureGenerationEx 方法

根據指定的旗標，產生指定元件的強式名稱簽章。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT StrongNameSignatureGenerationEx (  
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
  
 如果 `pbKeyBlob` 是 null，則 `wszKeyContainer` 必須在密碼編譯服務提供者中指定有效的容器， (CSP) 。 在此情況下，會使用儲存在容器中的金鑰組來簽署檔案。  
  
 如果不 `pbKeyBlob` 是 null，則會假設金鑰組包含在 (BLOB) 的金鑰二進位大型物件中。  
  
 `pbKeyBlob`  
 在公開/私密金鑰組的指標。 此配對的格式是 Win32 函數所建立的格式 `CryptExportKey` 。 如果 `pbKeyBlob` 是 null，則會假設指定的金鑰容器 `wszKeyContainer` 包含金鑰組。  
  
 `cbKeyBlob`  
 在的大小（以位元組為單位） `pbKeyBlob` 。  
  
 `ppbSignatureBlob`  
 擴展Common language runtime 傳回簽章之位置的指標。 如果 `ppbSignatureBlob` 是 null，則執行時間會將簽章儲存在所指定的檔案中 `wszFilePath` 。  
  
 如果不 `ppbSignatureBlob` 是 null，則 common language runtime 會配置要傳回簽章的空間。 呼叫端必須使用 [ICLRStrongName：： StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) 方法釋放此空間。  
  
 `pcbSignatureBlob`  
 擴展所傳回簽章的大小（以位元組為單位）。  
  
 `dwFlags`  
 在下列一個或多個值：  
  
- `SN_SIGN_ALL_FILES` (0x00000001) -重新計算連結模組的所有雜湊。  
  
- `SN_TEST_SIGN` (0x00000002) -測試簽署元件。  
  
## <a name="return-value"></a>傳回值  

 `S_OK` 如果方法成功完成，則為，否則，表示失敗 (的 HRESULT 值會看到清單) 的 [一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values) 。  
  
## <a name="remarks"></a>備註  

 針對計算簽章的 `wszFilePath` 大小而不建立簽章，請指定 null。  
  
 簽章可以直接儲存在檔案中，也可以傳回給呼叫端。  
  
 如果 `SN_SIGN_ALL_FILES` 指定了，但未包含公開金鑰 (則 `pbKeyBlob` 和都是 `wszFilePath` null) ，則會重新計算連結模組的雜湊，但不會重新簽署元件。  
  
 如果 `SN_TEST_SIGN` 指定了，就不會修改 common language runtime 標頭，以表示元件是以強式名稱簽署。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameSignatureGeneration 方法](iclrstrongname-strongnamesignaturegeneration-method.md)
- [ICLRStrongName 介面](iclrstrongname-interface.md)
