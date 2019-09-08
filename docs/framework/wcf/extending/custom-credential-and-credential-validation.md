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
ms.openlocfilehash: 1418d4155bc7f2fefc9f3e6caf4d3a264747a667
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795813"
---
# <a name="custom-credential-and-credential-validation"></a>自訂認證與認證驗證
Windows Communication Foundation （WCF）中的安全性是以服務與用戶端之間的認證交換為基礎。 使用一般認證類型就可滿足大多數安全性案例，例如 Windows (Kerberos)、使用者名稱和密碼以及憑證。 不過，如果需要新的認證類型，可在本節的各主題中找到如何處理及驗證新類型的方法。  
  
## <a name="in-this-section"></a>本節內容  
 [如何：建立採用自訂憑證驗證程式的服務](how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 說明如何藉由繼承<xref:System.IdentityModel.Selectors.X509CertificateValidator>自類別來自訂 WCF 驗證。  
  
 [逐步解說：建立自訂用戶端和服務認證](walkthrough-creating-custom-client-and-service-credentials.md)  
 示範如何擴充<xref:System.ServiceModel.Description.ClientCredentials>和<xref:System.ServiceModel.Description.ServiceCredentials>類別，以容納新的認證類型。 而這是說明建立自訂認證類型之主題系列中的第一項。  
  
 [如何：建立自訂安全性權杖提供者](how-to-create-a-custom-security-token-provider.md)  
 說明如何建立安全性權杖提供者，以處理新認證類型並傳回認證的新權杖。 這是主題系列中的第二個主題。  
  
 [如何：建立自訂安全性權杖驗證器](how-to-create-a-custom-security-token-authenticator.md)  
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
 [驗證](../feature-details/authentication-in-wcf.md)  
  
 [同盟與發行的權杖](../feature-details/federation-and-issued-tokens.md)  
  
 [授權](../feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a>另請參閱

- [Security](../feature-details/security.md)
