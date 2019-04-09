---
title: Authenticode (Unmanaged API 參考)
ms.date: 03/30/2017
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 408219307015d5c39cb581b3884ed9810f4c0566
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59216341"
---
# <a name="authenticode-unmanaged-api-reference"></a>Authenticode (Unmanaged API 參考)
支援 Authenticode XrML 授權的建立及驗證模組。  
  
## <a name="in-this-section"></a>本節內容  
 [_AxlGetIssuerPublicKeyHash 函式](../../../../docs/framework/unmanaged-api/authenticode/axlgetissuerpublickeyhash-function.md)  
 擷取公開金鑰的 SHA-1 雜湊，該公開金鑰與用來簽署指定憑證的私密金鑰相關聯。  
  
 [_AxlPublicKeyBlobToPublicKeyToken 函式](../../../../docs/framework/unmanaged-api/authenticode/axlpublickeyblobtopublickeytoken-function.md)  
 從 CSP PUBLICKEYBLOB 格式運算強式名稱公開金鑰語彙基元。  
  
 [_AxlRSAKeyValueToPublicKeyToken 函式](../../../../docs/framework/unmanaged-api/authenticode/axlrsakeyvaluetopublickeytoken-function.md)  
 將模數和指數轉換成強式名稱公開金鑰語彙基元。  
  
 [CertFreeAuthenticodeSignerInfo 函式](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md)  
 釋出配置給 AXL_AUTHENTICODE_SIGNER_INFO 結構的資源。  
  
 [CertFreeAuthenticodeTimestamperInfo 函式](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md)  
 釋出配置給 AXL_AUTHENTICODE_TIMESTAMPER_INFO 結構的資源。  
  
 [CertTimestampAuthenticodeLicense 函式](../../../../docs/framework/unmanaged-api/authenticode/certtimestampauthenticodelicense-function.md)  
 為 CertCreateAuthenticodeLicense 建立的 Authenticode XrML 授權加註時間戳記。  
  
 [CertVerifyAuthenticodeLicense 函式](../../../../docs/framework/unmanaged-api/authenticode/certverifyauthenticodelicense-function.md)  
 驗證 Authenticode XrML 授權的有效性。  
  
 [AXL_AUTHENTICODE_SIGNER_INFO 結構](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md)  
 定義 Authenticode 簽署人資訊。  
  
 [AXL_AUTHENTICODE_TIMESTAMPER_INFO 結構](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md)  
 定義 Authenticode 時間戳記程式資訊。  
  
## <a name="see-also"></a>另請參閱

- [Unmanaged API 參考](../../../../docs/framework/unmanaged-api/index.md)
