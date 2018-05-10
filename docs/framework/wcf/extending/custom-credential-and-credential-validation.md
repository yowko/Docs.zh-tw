---
title: 自訂認證與認證驗證
ms.date: 03/30/2017
helpviewer_keywords:
- credentials [WCF], custom
- credentials [WCF]
- custom credentials [WCF]
- credential validation [WCF]
- credentials [WCF], validation
ms.assetid: da831bec-e281-4d44-b343-437b5eef688e
ms.openlocfilehash: 9b340c01a9eb4ce4007e93f2b38e292cd6543ba1
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="custom-credential-and-credential-validation"></a>自訂認證與認證驗證
Windows Communication Foundation (WCF) 安全性為基礎的服務和用戶端之間的認證交換。 使用一般認證類型就可滿足大多數安全性案例，例如 Windows (Kerberos)、使用者名稱和密碼以及憑證。 不過，如果需要新的認證類型，可在本節的各主題中找到如何處理及驗證新類型的方法。  
  
## <a name="in-this-section"></a>本節內容  
 [如何：建立使用自訂憑證驗證程式的服務](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 說明如何透過繼承自自訂 WCF 驗證<xref:System.IdentityModel.Selectors.X509CertificateValidator>類別。  
  
 [逐步解說：建立自訂用戶端和服務認證](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 示範如何擴充<xref:System.ServiceModel.Description.ClientCredentials>和<xref:System.ServiceModel.Description.ServiceCredentials>類別，以涵蓋新認證類型。 而這是說明建立自訂認證類型之主題系列中的第一項。  
  
 [如何：建立自訂安全性權杖提供者](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 說明如何建立安全性權杖提供者，以處理新認證類型並傳回認證的新權杖。 這是主題系列中的第二個主題。  
  
 [如何：建立自訂安全性權杖驗證器](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 說明如何建立自訂驗證器，以驗證新認證類型。 這是主題系列中的第三個主題。  
  
## <a name="reference"></a>參考資料  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>  
  
 <xref:System.ServiceModel.Description.ClientCredentials>  
  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
  
## <a name="related-sections"></a>相關章節  
 [驗證](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
 [同盟與發行的權杖](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
  
 [授權](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a>另請參閱  
 [安全性](../../../../docs/framework/wcf/feature-details/security.md)
