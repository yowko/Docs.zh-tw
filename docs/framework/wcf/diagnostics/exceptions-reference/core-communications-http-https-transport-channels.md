---
title: "核心通訊：HTTP/HTTPS 傳輸通道 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6c0a23c9-a663-461c-bdab-58b4d3e23642
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 核心通訊：HTTP/HTTPS 傳輸通道
此主題會列出所有由 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Transport HTTP\/HTTPS 通道所產生的例外狀況。  
  
## 例外狀況清單  
  
|資源程式碼|資源字串|  
|-----------|----------|  
|DigestExplicitCredsImpersonationLevel|已指定此指定的模擬等級。  當 HTTP 摘要式驗證與明確的認證搭配使用時，它只會支援「模擬」等級。|  
|FramingContentTypeMismatch|指定的服務不支援指定的內容類型。  用戶端與服務繫結可能不相符。|  
|Hosting\_SslSettingsMisconfigured|指定之服務的安全通訊端層設定與網際網路資訊服務的安全通訊端層設定不相符。|  
|HttpAuthSchemeAndClientCert|HTTPS 接聽項處理站已設定為需要用戶端憑證與指定的驗證配置。  然而，一次只需要一種用戶端驗證格式。|  
|HttpReceiveFailure|對指定項目接收 HTTP 回應時發生錯誤。  服務端點繫結可能並未使用 HTTP 通訊協定。  另一種可能則是因為服務關閉，所以伺服器終止 HTTP 要求內容。  如需詳細資訊，請參閱伺服器記錄。|  
|HttpRegistrationAccessDenied|HTTP 無法註冊指定的 URL。  您的處理序並未具有這個命名空間的存取權 \(如需詳細資訊，請參閱 http:\/\/msdn.microsoft.com\/library\/default.asp?url\=\/library\/http\/http\/namespace\_reservations\_registrations\_and\_routing.asp\)。|  
|HttpRegistrationAlreadyExists|HTTP 無法註冊指定的 URL。  已有另一個應用程式使用 HTTP.SYS 註冊此 URL。|  
|HttpRegistrationPortInUse|HTTP 無法註冊指定的 URL，因為另一個應用程式正在使用指定的 TCP 連接埠。|  
|HttpSendFailure|向指定項目提出 HTTP 要求時發生錯誤。  請確定原因不是出在安全性繫結不符。  同時也請確定服務尚未針對安全通訊端層進行設定。|  
|MessageXmlProtocolError|從網路接收的 XML 發生問題。  如需詳細資訊，請參閱內部例外狀況。|  
|MissingContentType|接收者傳回錯誤，指出對指定項目的要求缺少內容類型。  如需詳細資訊，請參閱內部例外狀況。|  
|ProxyAuthenticationLevelMismatch|HTTP Proxy 驗證認證指定了相互驗證需求，此需求比目標伺服器驗證的需求更為嚴格。|  
|ProxyImpersonationLevelMismatch|HTTP Proxy 驗證認證指定了模擬等級限制，此限制比目標伺服器驗證的限制更為嚴格。|  
|SecureChannelFailure|您無法利用指定的授權為安全通訊端層\/傳輸層安全性建立安全通道。|  
|TrustFailure|您無法利用指定的授權為安全通訊端層\/傳輸層安全性建立信任關係。|  
|UseDefaultWebProxyCantBeUsedWithExplicitProxyAddress|您無法在 HttpTransportBinding 項目中，指定明確的 Proxy 位址，也無法指定 UseDefaultWebProxy\=true。|