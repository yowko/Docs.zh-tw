---
title: "透過 TCP 與 SOAP 安全性的 HTTPS 與 SSL 之間的憑證驗證差異 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "憑證 [WCF], 驗證差異"
ms.assetid: 953a219f-4745-4019-9894-c70704f352e6
caps.latest.revision: 14
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 14
---
# 透過 TCP 與 SOAP 安全性的 HTTPS 與 SSL 之間的憑證驗證差異
除了 HTTP \(HTTPS\) 或 TCP 之上的傳輸層安全性 \(TLS\) 外，您還可以使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 裡含訊息層 \(SOAP\) 安全性的憑證。此主題說明這類憑證的不同驗證方法。  
  
## HTTPS 用戶端憑證的驗證  
 使用 HTTPS 在用戶端與服務之間通訊時，用戶端用來驗證服務的憑證必須支援信賴鏈結的原則。也就是說，它必須鏈結至受信任的根憑證授權單位。否則，HTTP 層將發出訊息為「遠端伺服器傳回錯誤：\(403\) 禁止」的 <xref:System.Net.WebException>。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會將此例外狀況做為 <xref:System.ServiceModel.Security.MessageSecurityException>。  
  
## HTTPS 服務憑證的驗證  
 使用 HTTPS 在用戶端與服務之間通訊時，伺服器驗證的憑證必須預設支援信賴鏈結的原則。也就是說，它必須鏈結至受信任的根憑證授權單位。不進行線上檢查憑證是否已經被撤銷。您可以登錄 <xref:System.Net.Security.RemoteCertificateValidationCallback> 回呼覆寫此行為，如下列程式碼所示。  
  
 [!code-csharp[c_CertificateValidationDifferences#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#1)]
 [!code-vb[c_CertificateValidationDifferences#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#1)]  
  
 `ValidateServerCertificate` 簽名如下：  
  
 [!code-csharp[c_CertificateValidationDifferences#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#2)]
 [!code-vb[c_CertificateValidationDifferences#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#2)]  
  
 實作 `ValidateServerCertificate` 可執行任何用戶端應用程式開發者認為驗證服務憑證需要的檢查。  
  
## 架構於 TCP 或 SOAP 安全性的用戶端 SSL 憑證驗證  
 使用架構於 TCP 或訊息 \(SOAP\) 安全性的 Secure Sockets Layer \(SSL\) 時，用戶端憑證是根據 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> 類別之 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> 屬性值進行驗證。屬性設為其中一個 <xref:System.ServiceModel.Security.X509CertificateValidationMode> 值。撤銷檢查是根據 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> 類別的 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> 屬性值執行。屬性設為其中一個 <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> 值。  
  
 [!code-csharp[c_CertificateValidationDifferences#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#3)]
 [!code-vb[c_CertificateValidationDifferences#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#3)]  
  
## 架構於 TCP 或 SOAP 安全性之服務 SSL 憑證驗證  
 使用架構於 TCP 或 \(SOAP\) 訊息安全性的 SSL 時，服務憑證是根據 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> 類別之 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> 屬性值進行驗證。屬性設為其中一個 <xref:System.ServiceModel.Security.X509CertificateValidationMode> 值。  
  
 撤銷檢查是根據 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> 類別的 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> 屬性值執行。屬性設為其中一個 <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> 值。  
  
 [!code-csharp[c_CertificateValidationDifferences#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#4)]
 [!code-vb[c_CertificateValidationDifferences#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#4)]  
  
## 請參閱  
 <xref:System.Net.Security.RemoteCertificateValidationCallback>   
 [使用憑證](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)