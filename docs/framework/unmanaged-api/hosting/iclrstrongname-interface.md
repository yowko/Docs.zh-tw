---
title: ICLRStrongName 介面
ms.date: 03/30/2017
api_name:
- ICLRStrongName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName
helpviewer_keywords:
- ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 2fac66fd-6b3b-4dbd-8baf-86038bd85526
topic_type:
- apiref
ms.openlocfilehash: 691cc3cf4ec8d036a4de04247f243d99daa887d4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733629"
---
# <a name="iclrstrongname-interface"></a>ICLRStrongName 介面

提供基本的全域靜態函式來簽署具有強式名稱的元件。 所有 `ICLRStrongName` 方法都會傳回標準 COM hresult。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetHashFromAssemblyFile 方法](iclrstrongname-gethashfromassemblyfile-method.md)|使用指定的雜湊演算法取得所指定組件檔案的雜湊。|  
|[GetHashFromAssemblyFileW 方法](iclrstrongname-gethashfromassemblyfilew-method.md)|使用指定的雜湊演算法取得以 Unicode 字串形式指定的組件檔案雜湊。|  
|[GetHashFromBlob 方法](iclrstrongname-gethashfromblob-method.md)|使用指定的雜湊演算法取得位於指定記憶體位址之組件的雜湊。|  
|[GetHashFromFile 方法](iclrstrongname-gethashfromfile-method.md)|產生指定檔案內容的雜湊。|  
|[GetHashFromFileW 方法](iclrstrongname-gethashfromfilew-method.md)|產生以 Unicode 字串指定之檔案內容的雜湊。|  
|[GetHashFromHandle 方法](iclrstrongname-gethashfromhandle-method.md)|使用指定的雜湊演算法產生以指定檔案控制代碼指定之檔案的雜湊。|  
|[StrongNameCompareAssemblies 方法](iclrstrongname-strongnamecompareassemblies-method.md)|判斷兩個組件是否只有強制名稱簽章不同。|  
|[StrongNameFreeBuffer 方法](iclrstrongname-strongnamefreebuffer-method.md)|釋放先前呼叫強式名稱方法（例如 [StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md)、 [StrongNameTokenFromPublicKey](iclrstrongname-strongnametokenfrompublickey-method.md)或 [StrongNameSignatureGeneration](iclrstrongname-strongnamesignaturegeneration-method.md)）所配置的記憶體。|  
|[StrongNameGetBlob 方法](iclrstrongname-strongnamegetblob-method.md)|使用位於所指定位址之可執行檔的二進位表示法填滿指定的緩衝區。|  
|[StrongNameGetBlobFromImage 方法](iclrstrongname-strongnamegetblobfromimage-method.md)|取得位於所指定記憶體位置之組件影像的二進位表示法。|  
|[StrongNameGetPublicKey 方法](iclrstrongname-strongnamegetpublickey-method.md)|從私密/公開金鑰組取得公開金鑰。|  
|[StrongNameHashSize 方法](iclrstrongname-strongnamehashsize-method.md)|使用指定的雜湊演算法取得雜湊所需的緩衝區大小。|  
|[StrongNameKeyDelete 方法](iclrstrongname-strongnamekeydelete-method.md)|刪除指定的金鑰容器。|  
|[StrongNameKeyGen 方法](iclrstrongname-strongnamekeygen-method.md)|建立將供強式名稱使用的新公開/私密金鑰組。|  
|[StrongNameKeyGenEx 方法](iclrstrongname-strongnamekeygenex-method.md)|使用指定的金鑰大小產生將供強式名稱使用的新公開/私密金鑰組。|  
|[StrongNameKeyInstall 方法](iclrstrongname-strongnamekeyinstall-method.md)|將公開/私密金鑰組匯入到容器中。|  
|[StrongNameSignatureGeneration 方法](iclrstrongname-strongnamesignaturegeneration-method.md)|產生指定組件的強式名稱簽章。|  
|[StrongNameSignatureGenerationEx 方法](iclrstrongname-strongnamesignaturegenerationex-method.md)|以指定的旗標為基礎產生指定組件的強式名稱簽章。|  
|[StrongNameSignatureSize 方法](iclrstrongname-strongnamesignaturesize-method.md)|傳回強式名稱簽章的大小。|  
|[StrongNameSignatureVerification 方法](iclrstrongname-strongnamesignatureverification-method.md)|取得指出位於所指定路徑之組件資訊清單是否包含強式名稱簽章的值 (會根據指定的旗標驗證此值)。|  
|[StrongNameSignatureVerificationEx 方法](iclrstrongname-strongnamesignatureverificationex-method.md)|取得指出位於指定路徑的組件資訊清單是否包含強式名稱簽章的值。|  
|[StrongNameSignatureVerificationFromImage 方法](iclrstrongname-strongnamesignatureverificationfromimage-method.md)|驗證已對應到記憶體的組件對關聯的公開金鑰而言有效。|  
|[StrongNameTokenFromAssembly 方法](iclrstrongname-strongnametokenfromassembly-method.md)|從指定的組件檔案建立強式名稱權杖。|  
|[StrongNameTokenFromAssemblyEx 方法](iclrstrongname-strongnametokenfromassemblyex-method.md)|從指定組件檔案建立強式名稱權杖，並傳回公開金鑰。|  
|[StrongNameTokenFromPublicKey 方法](iclrstrongname-strongnametokenfrompublickey-method.md)|取得代表公開金鑰的權杖。|  
  
## <a name="remarks"></a>備註  

 您可以 `ICLRStrongName` 使用和做為參數來呼叫 [ICLRRuntimeInfo：： GetInterface](iclrruntimeinfo-getinterface-method.md) 方法，以取得的實例 `CLSID_CLRStrongName` `IID_ICLRStrongName` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載介面](hosting-interfaces.md)
- [裝載](index.md)
