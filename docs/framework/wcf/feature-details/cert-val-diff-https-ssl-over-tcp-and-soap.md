---
title: 透過 TCP 與 SOAP 安全性的 HTTPS 與 SSL 之間的憑證驗證差異
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], validation differences
ms.assetid: 953a219f-4745-4019-9894-c70704f352e6
ms.openlocfilehash: 978ef8f0abe3b65110864773a19c15f0c8363236
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183590"
---
# <a name="certificate-validation-differences-between-https-ssl-over-tcp-and-soap-security"></a>透過 TCP 與 SOAP 安全性的 HTTPS 與 SSL 之間的憑證驗證差異
您可以使用憑證在 Windows Communication Foundation (WCF) 除了傳輸層安全性 (TLS) 的訊息層 (SOAP) 安全性以透過 HTTP (HTTPS) 或 TCP。 此主題說明這類憑證的不同驗證方法。  
  
## <a name="validation-of-https-client-certificates"></a>HTTPS 用戶端憑證的驗證  
 使用 HTTPS 在用戶端與服務之間通訊時，用戶端用來驗證服務的憑證必須支援信賴鏈結的原則。 也就是說，它必須鏈結至受信任的根憑證授權單位。 否則，HTTP 層將發出訊息為「遠端伺服器傳回錯誤：(403) 禁止」的 <xref:System.Net.WebException>。 WCF 會呈現為這個例外狀況<xref:System.ServiceModel.Security.MessageSecurityException>。  
  
## <a name="validation-of-https-service-certificates"></a>HTTPS 服務憑證的驗證  
 使用 HTTPS 在用戶端與服務之間通訊時，伺服器驗證的憑證必須預設支援信賴鏈結的原則。 也就是說，它必須鏈結至受信任的根憑證授權單位。 不進行線上檢查憑證是否已經被撤銷。 您可以登錄 <xref:System.Net.Security.RemoteCertificateValidationCallback> 回呼覆寫此行為，如下列程式碼所示。  
  
 [!code-csharp[c_CertificateValidationDifferences#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#1)] 
 [!code-vb[c_CertificateValidationDifferences#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#1)]  
  
 `ValidateServerCertificate` 簽名如下：  
  
 [!code-csharp[c_CertificateValidationDifferences#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#2)]
 [!code-vb[c_CertificateValidationDifferences#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#2)]  
  
 實作 `ValidateServerCertificate` 可執行任何用戶端應用程式開發者認為驗證服務憑證需要的檢查。  
  
## <a name="validation-of-client-certificates-in-ssl-over-tcp-or-soap-security"></a>架構於 TCP 或 SOAP 安全性的用戶端 SSL 憑證驗證  
 使用架構於 TCP 或訊息 (SOAP) 安全性的 Secure Sockets Layer (SSL) 時，用戶端憑證是根據 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> 類別之 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> 屬性值進行驗證。 屬性設為其中一個 <xref:System.ServiceModel.Security.X509CertificateValidationMode> 值。 撤銷檢查是根據 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> 類別的 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> 屬性值執行。 屬性設為其中一個 <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> 值。  
  
 [!code-csharp[c_CertificateValidationDifferences#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#3)]
 [!code-vb[c_CertificateValidationDifferences#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#3)]  
  
## <a name="validation-of-service-certificate-in-ssl-over-tcp-and-soap-security"></a>架構於 TCP 或 SOAP 安全性之服務 SSL 憑證驗證  
 使用架構於 TCP 或 (SOAP) 訊息安全性的 SSL 時，服務憑證是根據 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> 類別之 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> 屬性值進行驗證。 屬性設為其中一個 <xref:System.ServiceModel.Security.X509CertificateValidationMode> 值。  
  
 撤銷檢查是根據 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> 類別的 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> 屬性值執行。 屬性設為其中一個 <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> 值。  
  
 [!code-csharp[c_CertificateValidationDifferences#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#4)]
 [!code-vb[c_CertificateValidationDifferences#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#4)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Net.Security.RemoteCertificateValidationCallback>  
 [使用憑證](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
