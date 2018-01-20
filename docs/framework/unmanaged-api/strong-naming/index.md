---
title: "強式命名 (Unmanaged API 參考)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- strong naming [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], strong naming
- unmanaged API reference [.NET Framework], strong naming
ms.assetid: 428c68b6-a7b4-44be-b280-75905f46612c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ce89e27089ea2f0c918d0fe37c4eea141698f9be
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="strong-naming-unmanaged-api-reference"></a>強式命名 (Unmanaged API 參考)
強式命名 API 可讓用戶端管理強式名稱簽署組件。  
  
 使用強式名稱簽署組件，就會將公開金鑰加密加入含有組件資訊清單的檔案中。 強式名稱簽署可協助驗證唯一名稱，可防止冒用名稱，並解析參考時呼叫端提供的唯一識別。 不過，任何層級不是信任的強式名稱與相關聯。  
  
## <a name="in-this-section"></a>本節內容  
 [強式命名全域靜態函式](http://msdn.microsoft.com/library/efa715df-e8cc-48f2-9ec4-26586f0dc8d0)  
 描述的 unmanaged 全域靜態函式強式命名 API 所使用。  
  
> [!NOTE]
>  所有這些函式被取代開頭為[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。 建議的替代項目，請參閱[ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)介面。  
  
 [GetHashFromAssemblyFile 函式](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromassemblyfile-function.md)  
 取得指定的組件檔案，使用指定的雜湊演算法的雜湊。 起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。  
  
 [GetHashFromAssemblyFileW 函式](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromassemblyfilew-function.md)  
 取得指定的 Unicode 字串，使用指定的雜湊演算法的組件檔案的雜湊。 起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。  
  
 [GetHashFromBlob 函式](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromblob-function.md)  
 取得該組件的雜湊指定的記憶體位址，使用指定的雜湊演算法。 起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。  
  
 [GetHashFromFile 函式](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md)  
 透過指定檔案的內容中產生之雜湊。  起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。  
  
 [GetHashFromFileW 函式](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md)  
 產生之雜湊的 Unicode 字串所指定的檔案內容。 起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。  
  
 [GetHashFromHandle 函式](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromhandle-function.md)  
 產生之雜湊與指定的檔案控制代碼，使用指定的雜湊演算法檔案的內容。  起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。  
  
 [StrongNameCompareAssemblies 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamecompareassemblies-function.md)  
 判斷兩個組件是否只有其強式名稱簽章不同。 起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。  
  
 [StrongNameErrorInfo 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)  
 取得其中一個強式名稱的函式所引發的最後一個錯誤碼。  
  
 [StrongNameFreeBuffer 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)  
 釋放記憶體配置與先前的強式名稱的函式呼叫這類[StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)， [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md)，或[StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).   起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。  
  
 [StrongNameGetBlob 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetblob-function.md)  
 在指定位址之可執行檔的二進位表示法中填入指定的緩衝區。 起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。  
  
 [StrongNameGetBlobFromImage 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetblobfromimage-function.md)  
 取得組件映像的二進位表示法，在指定的記憶體位址。 起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。  
  
 [StrongNameGetPublicKey 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)  
 從私密/公開金鑰組取得的公開金鑰。 起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。  
  
 [StrongNameHashSize 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamehashsize-function.md)  
 取得所需的雜湊，並使用指定的雜湊演算法的緩衝區大小。  起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。  
  
 [StrongNameKeyDelete 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md)  
 刪除指定的金鑰容器。 起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。  
  
 [StrongNameKeyGen 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeygen-function.md)  
 建立新公用/私密金鑰組的強式名稱使用。  起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。  
  
 [StrongNameKeyGenEx 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeygenex-function.md)  
 會產生新的公用/私用金鑰組的強式名稱使用指定的金鑰大小。 起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。  
  
 [StrongNameKeyInstall 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md)  
 匯入容器的公開/私密金鑰組。  起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。  
  
 [StrongNameSignatureGeneration 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)  
 產生強式名稱簽章的指定組件。   起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。  
  
 [StrongNameSignatureGenerationEx 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegenerationex-function.md)  
 指定的組件，並根據指定的旗標產生的強式名稱簽章。    起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。  
  
 [StrongNameSignatureSize 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md)  
 傳回強式名稱簽章的大小。 起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。  
  
 [StrongNameSignatureVerification 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md)  
 取得值，指出是否在提供的路徑上組件資訊清單包含強式名稱簽章，根據指定的旗標加以確認。 起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。  
  
 [StrongNameSignatureVerificationEx 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverificationex-function.md)  
 取得值，指出是否在提供的路徑上組件資訊清單包含強式名稱簽章。  起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。  
  
 [StrongNameSignatureVerificationFromImage 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverificationfromimage-function.md)  
 請確認已對應到記憶體的組件適用於相關聯的公開金鑰。 起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。  
  
 [StrongNameTokenFromAssembly 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md)  
 從指定的組件檔案中建立強式名稱語彙基元。  起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。  
  
 [StrongNameTokenFromAssemblyEx 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassemblyex-function.md)  
 從指定的組件檔案中，建立強式名稱語彙基元，並傳回公開金鑰。 起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。  
  
 [StrongNameTokenFromPublicKey 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md)  
 取得代表公開金鑰的語彙基元。 起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。  
  
 [強式命名結構](http://msdn.microsoft.com/library/4b041a2f-fd12-4b91-aacd-bc3b34a5124d)  
 描述強式命名 API 來管理強式名稱簽署組件所使用的 unmanaged 的結構...  
  
 [PublicKeyBlob 結構](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 表示以二進位格式公開/私密金鑰組的公開金鑰。  
  
## <a name="see-also"></a>請參閱  
 [ICLRStrongName 介面](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 [Unmanaged API 參考](../../../../docs/framework/unmanaged-api/index.md)
