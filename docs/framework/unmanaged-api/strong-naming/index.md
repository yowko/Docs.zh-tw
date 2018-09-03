---
title: 強式命名 (Unmanaged API 參考)
ms.date: 03/30/2017
helpviewer_keywords:
- strong naming [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], strong naming
- unmanaged API reference [.NET Framework], strong naming
ms.assetid: 428c68b6-a7b4-44be-b280-75905f46612c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 44ca428c028f9c3ee0a5e9a087f95af627d49f25
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43470099"
---
# <a name="strong-naming-unmanaged-api-reference"></a>強式命名 (Unmanaged API 參考)
強式命名 API 可讓用戶端管理組件的強式命名簽署。  
  
 使用強式名稱簽署組件，就會將公開金鑰加密加入含有組件資訊清單的檔案中。 強式名稱簽署可協助驗證名稱唯一性，防止名稱冒用，並且在解析參考時為呼叫者提供唯一身分識別。 但是，並沒有任何信任等級與強式名稱關聯。  
  
## <a name="in-this-section"></a>本節內容  
 [強式命名全域靜態函式](https://msdn.microsoft.com/library/efa715df-e8cc-48f2-9ec4-26586f0dc8d0)  
 說明強式命名 API 所使用的非受控全域靜態函式。  
  
> [!NOTE]
>  從 [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] 開始，所有這些函式都已過時。 如需建議的替代函式，請參閱 [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) 介面。  
  
 [GetHashFromAssemblyFile 函式](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromassemblyfile-function.md)  
 使用指定的雜湊演算法取得所指定組件檔案的雜湊。 從 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 開始過時。  
  
 [GetHashFromAssemblyFileW 函式](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromassemblyfilew-function.md)  
 使用指定的雜湊演算法取得以 Unicode 字串形式指定的組件檔案雜湊。 從 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 開始過時。  
  
 [GetHashFromBlob 函式](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromblob-function.md)  
 使用指定的雜湊演算法取得位於指定記憶體位址之組件的雜湊。 從 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 開始過時。  
  
 [GetHashFromFile 函式](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md)  
 產生指定檔案內容的雜湊。  從 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 開始過時。  
  
 [GetHashFromFileW 函式](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md)  
 產生以 Unicode 字串指定之檔案內容的雜湊。 從 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 開始過時。  
  
 [GetHashFromHandle 函式](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromhandle-function.md)  
 使用指定的雜湊演算法產生以指定檔案控制代碼指定之檔案的雜湊。  從 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 開始過時。  
  
 [StrongNameCompareAssemblies 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamecompareassemblies-function.md)  
 判斷兩個組件是否只有強制名稱簽章不同。 從 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 開始過時。  
  
 [StrongNameErrorInfo 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)  
 取得由其中一強式名稱函式所引發的最後一個錯誤代碼。  
  
 [StrongNameFreeBuffer 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)  
 釋放使用對強式名稱函式 (例如 [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)、[StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md) 或 [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)) 的上一個呼叫所配置的記憶體。   從 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 開始過時。  
  
 [StrongNameGetBlob 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetblob-function.md)  
 使用位於所指定位址之可執行檔的二進位表示法填滿指定的緩衝區。 從 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 開始過時。  
  
 [StrongNameGetBlobFromImage 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetblobfromimage-function.md)  
 取得位於所指定記憶體位置之組件影像的二進位表示法。 從 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 開始過時。  
  
 [StrongNameGetPublicKey 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)  
 從私密/公開金鑰組取得公開金鑰。 從 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 開始過時。  
  
 [StrongNameHashSize 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamehashsize-function.md)  
 使用指定的雜湊演算法取得雜湊所需的緩衝區大小。  從 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 開始過時。  
  
 [StrongNameKeyDelete 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md)  
 刪除指定的金鑰容器。 從 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 開始過時。  
  
 [StrongNameKeyGen 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeygen-function.md)  
 建立將供強式名稱使用的新公開/私密金鑰組。  從 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 開始過時。  
  
 [StrongNameKeyGenEx 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeygenex-function.md)  
 使用指定的金鑰大小產生將供強式名稱使用的新公開/私密金鑰組。 從 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 開始過時。  
  
 [StrongNameKeyInstall 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md)  
 將公開/私密金鑰組匯入到容器中。  從 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 開始過時。  
  
 [StrongNameSignatureGeneration 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)  
 產生指定組件的強式名稱簽章。   從 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 開始過時。  
  
 [StrongNameSignatureGenerationEx 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegenerationex-function.md)  
 以指定的旗標為基礎產生指定組件的強式名稱簽章。    從 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 開始過時。  
  
 [StrongNameSignatureSize 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md)  
 傳回強式名稱簽章的大小。 從 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 開始過時。  
  
 [StrongNameSignatureVerification 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md)  
 取得指出位於所指定路徑之組件資訊清單是否包含強式名稱簽章的值 (會根據指定的旗標驗證此值)。 從 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 開始過時。  
  
 [StrongNameSignatureVerificationEx 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverificationex-function.md)  
 取得指出位於指定路徑的組件資訊清單是否包含強式名稱簽章的值。  從 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 開始過時。  
  
 [StrongNameSignatureVerificationFromImage 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverificationfromimage-function.md)  
 驗證已對應到記憶體的組件對關聯的公開金鑰而言有效。 從 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 開始過時。  
  
 [StrongNameTokenFromAssembly 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md)  
 從指定的組件檔案建立強式名稱權杖。  從 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 開始過時。  
  
 [StrongNameTokenFromAssemblyEx 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassemblyex-function.md)  
 從指定組件檔案建立強式名稱權杖，並傳回公開金鑰。 從 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 開始過時。  
  
 [StrongNameTokenFromPublicKey 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md)  
 取得代表公開金鑰的權杖。 從 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 開始過時。  
  
 [強式命名結構](https://msdn.microsoft.com/library/4b041a2f-fd12-4b91-aacd-bc3b34a5124d)  
 說明非強式命名 API 用來管理組件之強式名稱簽署的非受控結構。  
  
 [PublicKeyBlob 結構](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 代表公開/私密金鑰組的公開金鑰 (二進位格式)。  
  
## <a name="see-also"></a>另請參閱  
 [ICLRStrongName 介面](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 [Unmanaged API 參考](../../../../docs/framework/unmanaged-api/index.md)
