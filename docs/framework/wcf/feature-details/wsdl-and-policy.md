---
title: "WSDL 與原則"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cea87440-3519-4640-8494-b8a2b0e88c84
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f502d24f98c9229d064be3de0e0edc081664dd03
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="wsdl-and-policy"></a>WSDL 與原則
這個主題中涵蓋了 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] WSDL 1.1、WS-Policy 和 WS-PolicyAttachment 實作詳細資料，以及 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 所引入的其他 WS-Policy 判斷提示和 WSDL 1.1 延伸項目。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會利用本文件所述的限制和說明，實作提交至 W3C 的 WS-Policy 和 WS-PolicyAttachment 規格。  
  
 本文件會使用下表所示的前置詞和命名空間。  
  
|前置詞|命名空間|  
|------------|---------------|  
|wsp (WS-Policy 1.2)|http://schemas.xmlsoap.org/ws/2004/09/policy|  
|wsp (WS-Policy 1.5)|http://www.w3.org/ns/ws-policy|  
|http|http://schemas.microsoft.com/ws/06/2004/policy/http|  
|msmq|http://schemas.microsoft.com/ws/06/2004/mspolicy/msmq|  
|msf|http://schemas.microsoft.com/ws/2006/05/framing/policy|  
|mssp|http://schemas.microsoft.com/ws/2005/07/securitypolicy|  
|msc|http://schemas.microsoft.com/ws/2005/12/wsdl/contract|  
|cdp|http://schemas.microsoft.com/net/2006/06/duplex|  
  
## <a name="wcf-wsdl11-extensions"></a>WCF WSDL1.1 延伸項目  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會使用下列 WSDL1.1 延伸項目來描述合約工作階段的需求。  
  
 wsdl:portType/wsdl:operation/@msc:isInitiating  
 xs:boolean，指出此作業會初始化 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 工作階段；預設值為 `false`。  
  
 wsdl:portType/wsdl:operation/@msc:isTerminating  
 xs:boolean，指出此作業會終止 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 工作階段；預設值為 `false`。  
  
 wsdl:portType/wsdl:operation/@msc:usingSession  
 xs:boolean，指出此合約需要建立工作階段。  
  
### <a name="soap-1x-http-binding-transport-uris"></a>SOAP 1.x HTTP 繫結傳輸 URI  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會使用下列 URI 指出要用於 WSDL 1.1、SOAP 1.1 和 SOAP 1.2 繫結延伸項目的傳輸。  
  
|Transport|URI|  
|---------------|---------|  
|HTTP|http://schemas.xmlsoap.org/soap/http|  
|TCP|http://schemas.microsoft.com/soap/tcp|  
|MSMQ|http://schemas.microsoft.com/soap/msmq|  
|具名管道|http://schemas.microsoft.com/soap/named-pipe|  
  
## <a name="policy-assertions-implemented-by-wcf"></a>WCF 實作的原則判斷提示  
 除了在 Web 服務規格 (WS-*) 中引入以及在本文件其他章節所提及的原則判斷提示以外，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 也會實作下列原則判斷提示。  
  
|原則判斷提示|原則主體|描述|  
|----------------------|--------------------|-----------------|  
|http:HttpBasicAuthentication|端點|端點會使用 HTTP 基本驗證。|  
|http:HttpDigestAuthentication|端點|端點會使用 HTTP 摘要式驗證。|  
|http:HttpNegotiateAuthentication|端點|端點會使用 HTTP 交涉式驗證。|  
|http:HttpNtlmAuthentication|端點|端點會使用 HTTP NTLM 驗證。|  
|msf:Streamed|端點|端點會使用已進行資料流處理的訊息框架處理。 這個判斷提示會與訊息框架處理通訊協定搭配使用，而這個通訊協定是專為 TCP 這類傳輸和具名管道所提供。|  
|msf:SslTransportSecurity|端點|端點會使用傳輸層安全性 (TLS) 搭配訊息框架處理。|  
|msf:WindowsTransportSecurity|端點|端點會使用安全性提供者交涉 (SPNEGO) 搭配訊息框架處理。|  
|msmq:MsmqBestEffort|端點|具備最佳保證的 MSMQ。|  
|msmq:MsmqSession|端點|具備工作階段保證的 MSMQ。|  
|msmq:MsmqVolatile|端點|MSMQ 變動性。|  
|msmq:Authenticated|端點|驗證會與 MSMQ 傳輸搭配使用。|  
|msmq:WindowsDomain|端點|MSMQ 會使用 Windows 網域驗證。|  
|cdp:CompositeDuplex|端點|端點會針對傳入和傳出訊息，使用兩種分離的相反傳輸連線。|  
|mssp:RsaToken|巢狀|RSA 金鑰權杖判斷提示。 在簽署簽章中直接做為金鑰資訊而序列化的 RSA 金鑰，通常就可以滿足此需求。|  
|mssp:SslContextToken|巢狀|需要使用二進位 TLS 信號交換 (使用已使用的 WS-Trust) 來取得 SecurityContextToken。 巢狀判斷提示包括：sp:RequireDerivedKeys、mssp:MustNotSendCancel、mssp:RequireClientCertificate。|  
|mssp:MustNotSendCancel|巢狀|所指定的需求為：使用取消繫結 [WS-Trust, WS-SC] 的要求安全性權杖 (RST) 要求訊息 [WS-Trust]，不要傳送至提供之 SecurityContextToken 的簽發者。 如果出現這個判斷提示，則這種要求訊息一定不能傳送至簽發者。 如果未出現這個判斷提示，則這種要求訊息可以傳送至簽發者。|  
|mssp:RequireClientCertificate|巢狀|這個選用項目會對用戶端憑證指定要求，也就是是否要做為 TLSNEGO 通訊協定的一部分而提供。 如果出現這個判斷提示，則必須提供用戶端憑證。 如果未出現這個判斷提示，則不可提供用戶端憑證。 這個判斷提示不可在 mssp:SslContextToken 以外使用。|  
  
## <a name="see-also"></a>另請參閱  
 [自訂 WSDL 發行物](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)  
 [如何： 匯出自訂 WSDL](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md)  
 [如何： 匯入自訂 WSDL](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
