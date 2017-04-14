---
title: "HOW TO：建立雙工聯合繫結 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# HOW TO：建立雙工聯合繫結
<xref:System.ServiceModel.WSFederationHttpBinding> 只支援資料包以及要求\/回覆訊息交換合約。若要使用雙工訊息交換合約，必須建立自訂繫結。下列程序示範如何在組態檔中完成這項工作、使用訊息模式安全性進行 HTTP 與 TCP 傳輸的方法以及利用混合模式安全性進行 TCP 傳輸。這三種繫結方式的完整程式碼範例會列於本主題的結尾。  
  
 您也可以撰寫程式碼建立繫結。如需要建立之繫結項目堆疊的說明，請參閱 [HOW TO：使用 SecurityBindingElement 建立自訂繫結](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)。  
  
### 若要以 HTTP 建立雙工聯合自訂繫結  
  
1.  在組態檔的 [\<繫結\>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) 節點中，建立一個 [\<customBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)項目。  
  
2.  在 [\<customBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) 項目內部，建立一個 [\<繫結\>](../../../../docs/framework/misc/binding.md) 項目，且其中的 `name` 屬性要設為 `FederationDuplexHttpMessageSecurityBinding`。  
  
3.  在 [\<繫結\>](../../../../docs/framework/misc/binding.md) 項目內部，建立一個 [\<安全性\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) 項目，且其中的 `authenticationMode` 屬性要設為 `SecureConversation`。  
  
4.  在 [\<安全性\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)項目內部，建立一個 [\<secureConversationBootstrap\>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) 項目，且其中的 `authenticationMode` 屬性要設為 `IssuedTokenForCertificate`或 `IssuedTokenForSslNegotiated`。  
  
5.  接著 [\<安全性\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)[\<compositeDuplex\>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) 項目。  
  
6.  接著 [\<compositeDuplex\>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)[\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) 項目。  
  
7.  接著 [\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)[\<httpTransport\>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) 項目。  
  
### 若要以 TCP 訊息安全性模式建立雙工聯合自訂繫結  
  
1.  在組態檔的 [\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)[\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) 項目。  
  
2.  在 [\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) 項目內部，建立一個 [\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) 項目，且其中的 `name` 屬性要設為 `FederationDuplexTcpMessageSecurityBinding`。  
  
3.  在 [\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) 項目內部，建立一個[\<安全性\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) 項目，且其中的 `authenticationMode`屬性要設為 `SecureConversation`。  
  
4.  在 [\<安全性\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)項目內部，建立一個 [\<secureConversationBootstrap\>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) 項目，且其中的 `authenticationMode` 屬性要設為 `IssuedTokenForCertificate`或 `IssuedTokenForSslNegotiated`。  
  
5.  接著 [\<安全性\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)[\<tcpTransport\>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) 項目。  
  
### 若要以 TCP 混合安全性模式建立雙工聯合自訂繫結  
  
1.  在組態檔的 [\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)[\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) 項目。  
  
2.  在 [\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) 項目內部，建立一個 [\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) 項目，且其中的 `name` 屬性要設為 `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`。  
  
3.  在 [\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) 項目內部，建立一個[\<安全性\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) 項目，且其中的 `authenticationMode`屬性要設為 `SecureConversation`。  
  
4.  在 [\<安全性\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)項目內部，建立一個 [\<secureConversationBootstrap\>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) 項目，且其中的 `authenticationMode` 屬性要設為 `IssuedTokenForCertificate`或 `IssuedTokenForSslNegotiated`。  
  
5.  接著 [\<安全性\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)[\<SSL 資料流安全性\>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) 項目。  
  
6.  接著 [\<SSL 資料流安全性\>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)[\<tcpTransport\>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) 項目。  
  
## 範例程式碼  
  
#### 3 個繫結的範例  
  
1.  將下列程式碼插入組態檔。  
  
## 範例  
  
```  
  
<bindings>  
   <customBinding>  
      <binding name="FederationDuplexHttpMessageSecurityBinding">  
<!-- duplex contract requires secure conversation with require cancellation = true -->  
          <security authenticationMode="SecureConversation">  
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />  
          </security>  
          <compositeDuplex />  
          <oneWay />  
          <httpTransport />  
       </binding>  
<!-- duplex over https is not supported -->  
       <binding name="FederationDuplexTcpMessageSecurityBinding">  
<!-- duplex contract requires secure conversation with require cancellation = true -->  
          <security authenticationMode="SecureConversation">  
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />  
          </security>  
          <tcpTransport />  
       </binding>              
       <binding name="FederationDuplexTcpTransportSecurityWithMessageCredentialsBinding">  
<!-- duplex contract requires secure conversation with require cancellation = true -->  
          <security authenticationMode="SecureConversation">  
              <secureConversationBootstrap authenticationMode="IssuedTokenOverTransport" />  
          </security>  
<!-- requireClientCertificate = true or <windowsStreamSecurity /> can be used, but does not make sense for most scenarios -->  
          <sslStreamSecurity />  
          <tcpTransport />  
       </binding>              
    </customBinding>  
</bindings>  
  
```