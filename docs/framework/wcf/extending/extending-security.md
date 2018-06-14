---
title: 擴充安全性
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], extending
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 94aefe80674c5b4ec6fcce6a41d9b68e093f4262
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809397"
---
# <a name="extending-security"></a>擴充安全性
為了配合新的宣告類型和自訂權杖，您可以擴充安全性基礎結構的 Windows Communication Foundation (WCF)。 本章節中的主題會示範如何做到這點。  
  
## <a name="in-this-section"></a>本節內容  
 [安全性架構](http://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)  
 逐步解說 WCF 安全性系統的架構。  
  
 [自訂認證與認證驗證](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md)  
 說明如何在驗證自訂認證時使用身分識別模型。  
  
 [自訂權杖](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 通常從安全性權杖服務 (STS) 發行的權杖是 SAML 權杖。 本主題會說明如何建立自訂權杖類型。  
  
 [自訂授權](../../../../docs/framework/wcf/extending/custom-authorization.md)  
 說明如何實作自訂授權。  
  
 [覆寫服務的身分識別以進行驗證](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md)  
 說明如何覆寫服務的身分識別來進行驗證。  
  
 [如何：建立自訂用戶端身分識別驗證器](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)  
 示範如何驗證自訂端點身分識別。  
  
 [如何：使用個別 X.509 憑證簽署與加密](../../../../docs/framework/wcf/extending/how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 訊息通常會以單一憑證來簽署和加密。 本主題會說明如何能在必要時使用兩份憑證。  
  
 [如何：變更 X.509 憑證私密金鑰的密碼編譯提供者](../../../../docs/framework/wcf/extending/change-cryptographic-provider-x509-certificate-private-key.md)  
 說明如何變更用來提供 X.509 憑證之私密金鑰的密碼編譯提供者，以及如何整合到 Windows Communication Foundation (WCF) 架構的提供者。  
  
## <a name="reference"></a>參考資料  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
## <a name="related-sections"></a>相關章節  
 [安全性](../../../../docs/framework/wcf/feature-details/security.md)  
  
 [基本 WCF 程式設計](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
## <a name="see-also"></a>另請參閱  
 [安全性概觀](../../../../docs/framework/wcf/feature-details/security-overview.md)
