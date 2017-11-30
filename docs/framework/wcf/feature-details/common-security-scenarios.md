---
title: "常見的安全性案例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: security [WCF], scenarios
ms.assetid: 201923b5-5162-4a8a-8d4c-e7bd242748d5
caps.latest.revision: "18"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 9428c5d7c8c6cf0f571b05a8b9c33b96d073d7a5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="common-security-scenarios"></a>常見的安全性案例
本章節中的主題列出一些可能的用戶端和服務安全性組態。 組態會視一些因素而改變。 例如，服務或用戶端是否在內部網路，或安全性是由 Windows 或傳輸 (例如 HTTPS) 所提供。  
  
## <a name="in-this-section"></a>本章節內容  
 [網際網路不安全的用戶端和服務](../../../../docs/framework/wcf/feature-details/internet-unsecured-client-and-service.md)  
 公開、不安全的用戶端與服務範例。  
  
 [內部網路不安全的用戶端和服務](../../../../docs/framework/wcf/feature-details/intranet-unsecured-client-and-service.md)  
 一個基本的 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務，為了將安全私人網路上的資訊提供給 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式而開發。  
  
 [使用基本驗證的傳輸安全性](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)  
 應用程式允許用戶端使用自訂驗證登入。  
  
 [使用 Windows 驗證的傳輸安全性](../../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md)  
 顯示由 Windows 安全性保護的用戶端和服務。  
  
 [匿名用戶端使用的傳輸安全性](../../../../docs/framework/wcf/feature-details/transport-security-with-an-anonymous-client.md)  
 這個案例會使用傳輸安全性 (例如 HTTPS) 來確保機密性和完整性。  
  
 [憑證驗證的傳輸安全性](../../../../docs/framework/wcf/feature-details/transport-security-with-certificate-authentication.md)  
 顯示由憑證保護的用戶端和服務。  
  
 [匿名用戶端的訊息安全性](../../../../docs/framework/wcf/feature-details/message-security-with-an-anonymous-client.md)  
 顯示由 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 訊息安全性保護的用戶端和服務。  
  
 [使用者名稱用戶端的訊息安全性](../../../../docs/framework/wcf/feature-details/message-security-with-a-user-name-client.md)  
 用戶端是 Windows Forms 應用程式，允許用戶端使用網域使用者名稱和密碼登入。  
  
 [憑證用戶端的訊息安全性](../../../../docs/framework/wcf/feature-details/message-security-with-a-certificate-client.md)  
 伺服器有憑證，每一個用戶端也都有憑證。 安全性內容是透過傳輸層安全性 (TLS) 交涉所建立。  
  
 [訊息安全性的 Windows 用戶端](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md)  
 憑證用戶端的驗證。 伺服器有憑證，每一個用戶端也都有憑證。 安全性內容是透過 TLS 交涉所建立。  
  
 [不具有認證交涉的 Windows 用戶端的訊息安全性](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client-without-credential-negotiation.md)  
 顯示由 Kerberos 網域保護的用戶端和服務。  
  
 [相互憑證的訊息安全性](../../../../docs/framework/wcf/feature-details/message-security-with-mutual-certificates.md)  
 伺服器有憑證，每一個用戶端也都有憑證。 伺服器憑證隨應用程式散發，並可超出範圍提供。  
  
 [發行之權杖的訊息安全性](../../../../docs/framework/wcf/feature-details/message-security-with-issued-tokens.md)  
 聯合安全性，可在獨立網域之間建立信任關係。  
  
 [受信任的子系統](../../../../docs/framework/wcf/feature-details/trusted-subsystem.md)  
 用戶端會存取分散在網路上的一或多個 Web 服務。 Web 服務會存取必須受到保護的其他資源 (例如，資料庫或其他 Web 服務)。  
  
## <a name="reference"></a>參考資料  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a>相關章節  
 [授權](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
 [安全性概觀](../../../../docs/framework/wcf/feature-details/security-overview.md)  
  
 [安全性](../../../../docs/framework/wcf/feature-details/security.md)  
  
 [繫結和安全性](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [保護服務和用戶端](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
 [驗證](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
 [授權](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
 [同盟與發行的權杖](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
  
 [稽核](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
  
## <a name="see-also"></a>另請參閱  
 [安全性指導方針和最佳作法](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
 [Windows Server App Fabric 的安全性模型](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
