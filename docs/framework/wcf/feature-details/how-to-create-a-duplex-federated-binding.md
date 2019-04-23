---
title: HOW TO：建立雙面同盟繫結
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: 510faa0b1d791b1d164c55e9fa32daafa559d56c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59346232"
---
# <a name="how-to-create-a-duplex-federated-binding"></a>HOW TO：建立雙面同盟繫結
<xref:System.ServiceModel.WSFederationHttpBinding> 只支援資料包以及要求/回覆訊息交換合約。 若要使用雙工訊息交換合約，必須建立自訂繫結。 下列程序示範如何在組態檔中完成這項工作、使用訊息模式安全性進行 HTTP 與 TCP 傳輸的方法以及利用混合模式安全性進行 TCP 傳輸。 這三種繫結方式的完整程式碼範例會列於本主題的結尾。  
  
 您也可以撰寫程式碼建立繫結。 若要建立繫結項目堆疊的說明，請參閱[How to:建立自訂繫結使用 SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)。  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-http"></a>若要以 HTTP 建立雙工聯合自訂繫結  
  
1. 在  [\<繫結 >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)節點的組態檔中，建立[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)項目。  
  
2. 內部[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)項目，建立[\<繫結 >](../../../../docs/framework/misc/binding.md)項目`name`屬性設為`FederationDuplexHttpMessageSecurityBinding`。  
  
3. 內部[\<繫結 >](../../../../docs/framework/misc/binding.md)項目，建立[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)項目`authenticationMode`屬性設為`SecureConversation`。  
  
4. 內部[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)項目，建立[ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)項目`authenticationMode`屬性設為`IssuedTokenForCertificate`或`IssuedTokenForSslNegotiated`.  
  
5. 遵循[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)項目，建立空白[ \<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)項目。  
  
6. 遵循[ \<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)項目，建立空白[ \<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)項目。  
  
7. 遵循[ \<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)項目，建立空白[ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)項目。  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a>若要以 TCP 訊息安全性模式建立雙工聯合自訂繫結  
  
1. 在  [\<繫結 >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)節點的組態檔中，建立[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)項目。   
  
2. 內部[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)項目，建立[\<繫結 >](../../../../docs/framework/misc/binding.md)項目`name`屬性設為`FederationDuplexTcpMessageSecurityBinding`。  
  
3. 內部[\<繫結 >](../../../../docs/framework/misc/binding.md)項目，建立[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)項目`authenticationMode`屬性設為`SecureConversation`。  
  
4. 內部[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)項目，建立[ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)項目`authenticationMode`屬性設為`IssuedTokenForCertificate`或`IssuedTokenForSslNegotiated`.  
  
5. 遵循[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)項目，建立空白[ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md)項目。  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a>若要以 TCP 混合安全性模式建立雙工聯合自訂繫結  
  
1. 在  [\<繫結 >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)節點的組態檔中，建立[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)項目。   
  
2. 內部[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)項目，建立[\<繫結 >](../../../../docs/framework/misc/binding.md)項目`name`屬性設為`FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`。  
  
3. 內部[\<繫結 >](../../../../docs/framework/misc/binding.md)項目，建立[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)項目`authenticationMode`屬性設為`SecureConversation`。  
  
4. 內部[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)項目，建立[ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)項目`authenticationMode`屬性設為`IssuedTokenForCertificate`或`IssuedTokenForSslNegotiated`.  
  
5. 遵循[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)項目，建立空白[ \<Custombinding> >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)項目。  
  
6. 遵循[ \<Custombinding> >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)項目，建立空白[ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md)項目。  
  
## <a name="code-sample"></a>範例程式碼  
  
#### <a name="sample-with-3-bindings"></a>3 個繫結的範例  
  
1. 將下列程式碼插入組態檔。  
  
## <a name="example"></a>範例  
  
```xml  
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
