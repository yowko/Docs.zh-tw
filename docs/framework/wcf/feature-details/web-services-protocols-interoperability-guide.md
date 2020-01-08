---
title: Web 服務通訊協定互通性指南
ms.date: 03/30/2017
ms.assetid: f2981678-ebdb-433d-899b-467f7df95fb2
ms.openlocfilehash: 1b949880b3ebbaf121b79a958d17cf5708affcf3
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636142"
---
# <a name="web-services-protocols-interoperability-guide"></a>Web 服務通訊協定互通性指南

Windows Communication Foundation （WCF）會執行數個 Web 服務通訊協定。 許多這些通訊協定包含實作者應自行決定的一些選項和擴充點。 本主題提供 WCF 所實行的 Web 服務通訊協定清單。 本節中的其他主題則會提供每個受支援通訊協定的實作詳細資訊。

## <a name="web-services-protocols-implemented-by-wcf"></a>WCF 所實行的 Web 服務通訊協定

WCF 透過「合約」功能，透過通道和 Web 服務應用程式協定，提供 Web 服務（WS）基礎結構通訊協定的支援。 應用程式通訊協定的互通性是透過 XML 結構描述語言 1.0 (XSD) 和 Web 服務描述語言 (WSDL) 1.1 來達成。

基礎結構通訊協定互通性是由 WS-* 規格所提供。 WCF 通道支援一些 WS\* 的基礎結構通訊協定。 WCF 通道是使用繫結項目來設定。 下表包含由各種 WCF 繫結項目所執行的 WS-\* 基礎結構通訊協定的完整清單。

<xref:System.ServiceModel.Channels.HttpTransportBindingElement> 支援下表中的規格。

|規格/文件|連結|
|-----------------------------|----------|
|HTTP 1.1|[RFC 2616](https://www.rfc-editor.org/rfc/rfc2616.txt)|
|SOAP 1.1 HTTP 繫結|[簡易物件存取通訊協定（SOAP） 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)，第7節|
|SOAP 1.2 HTTP 繫結|[SOAP 版本1.2 第2部分：附加（第二版）](https://www.w3.org/TR/soap12-part2/)，第7節|

<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> 和 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> 支援下表中的規格。

|規格/文件|連結|
|-----------------------------|----------|
|XML|[可延伸標記語言 (XML) （XML）1.0 （第四版）](https://www.w3.org/TR/REC-xml/)|
|SOAP 1.1|[簡易物件存取通訊協定（SOAP）1。1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)|
|SOAP 1.2 核心|[SOAP 版本1.2 第1部分：訊息架構（第二版）](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)|
|WS-Addressing 2004/08|[Web 服務定址（WS-ADDRESSING）](https://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/)|
|W3C Web 服務定址 1.0 - 核心|[Web 服務定址 1.0-核心](https://www.w3.org/TR/2006/REC-ws-addr-core-20060509/)|
|W3C Web 服務定址 1.0 - SOAP 繫結|[Web 服務定址 1.0-SOAP 系結](https://www.w3.org/TR/2006/REC-ws-addr-soap-20060509/)|
|W3C Web 服務定址 1.0 - WSDL 繫結*|[Web 服務定址 1.0-WSDL 系結](https://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/)|
|W3C Web 服務定址 1.0 中繼資料|[Web 服務定址 1.0-中繼資料](https://www.w3.org/TR/ws-addr-metadata/)|
|WSDL SOAP1.1 繫結|[Web 服務描述語言（WSDL）1。1](https://www.w3.org/TR/wsdl/)|
|WSDL SOAP1.2 繫結|[SOAP 1.2 的 WSDL 1.1 系結延伸模組](https://www.w3.org/Submission/wsdl11soap12/)|

<xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> 支援下表中的規格。

|規格/文件|連結|
|-----------------------------|----------|
|XOP|[XML-二進位優化封裝](https://www.w3.org/TR/xop10/)|
|MTOM + SOAP1.2 繫結|[SOAP 訊息傳輸優化機制](https://www.w3.org/TR/soap12-mtom/)|
|MTOM SOAP 1.1 繫結|[MTOM 1.0 的 SOAP 1.1 系結](https://www.w3.org/Submission/soap11mtom10/)|
|MTOM WS-PolicyAssertions|[MTOM 序列化原則判斷提示（WS-MTOMPolicy）](https://www.w3.org/Submission/WS-MTOMPolicy/)|

<xref:System.ServiceModel.Channels.SecurityBindingElement> 支援下表中的規格。

|規格/文件|連結|
|-----------------------------|----------|
|WSS：SOAP 訊息安全性 1.0|[Web 服務安全性： SOAP 訊息安全性1。0](https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf)|
|WSS：使用者名稱權杖設定檔 1.0|[Web 服務安全性 UsernameToken Profile 1。0](https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf)<br /><br /> 需要 Password/@Type= PasswordText （預設值）|
|WSS：X.509 權杖設定檔 1.0|[Web 服務安全性 x.509 憑證權杖設定檔](https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf)|
|WSS：SAML 1.1 權杖設定檔 1.0|[Web 服務安全性： SAML 權杖設定檔](https://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf)|
|WSS：SOAP 訊息安全性 1.1|[Web 服務安全性： SOAP 訊息安全性1。1](https://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf)|
|WSS：使用者名稱權杖設定檔 1.1|[Web 服務安全性 UsernameToken Profile 1。1](https://www.oasis-open.org/committees/download.php/16782/wss-v1.1-spec-os-UsernameTokenProfile.pdf)<br /><br /> 不會實作密碼架構金鑰衍生；<br /><br /> 需要 Password/@Type= PasswordText （預設值）|
|WSS：X509 權杖設定檔 1.1|[Web 服務安全性 x.509 憑證權杖設定檔1。1](https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf)|
|WSS：Kerberos 權杖設定檔 1.1|[Web 服務安全性 Kerberos 權杖設定檔1。1](https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf)|
|WSS：SAML 1.1 權杖設定檔 1.1|[Web 服務安全性 SAML 權杖設定檔1。1](https://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf)|
|WS-SecureConversation|[Web 服務安全交談語言](https://specs.xmlsoap.org/ws/2005/02/sc/ws-secureconversation.pdf)|
|WS-Trust 1.4|[Web 服務信任語言](https://docs.oasis-open.org/ws-sx/ws-trust/200802)|
|WS-SecurityPolicy 2005/07|[Web 服務安全交談語言](https://specs.xmlsoap.org/ws/2005/02/sc/ws-secureconversation.pdf)<br /><br /> 已由提交至 OASIS WS-SX 技術委員會的勘誤表修訂。<br /><br /> [ws-sx 訊息](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html)|
|WS-ReliableMessaging 1.1|[可靠傳訊通訊協定 1.1 版](reliable-messaging-protocol-version-1-1.md)|

<xref:System.ServiceModel.Channels.TransactionFlowBindingElement> 支援下表中的規格。

|規格/文件|連結|
|-----------------------------|----------|
|WS-Coordination|[Web 服務協調](https://docs.microsoft.com/previous-versions/ms951231(v=msdn.10))|
|WS-AtomicTransaction|[Web 服務不可部分完成交易](https://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf)|

<xref:System.ServiceModel.Description.MetadataExporter>、<xref:System.ServiceModel.Description.MetadataImporter>、<xref:System.ServiceModel.Description.WsdlExporter>、<xref:System.ServiceModel.Description.WsdlImporter> 和 <xref:System.ServiceModel.Description.MetadataResolver> 類別支援下列中繼資料規格：

- [XML 架構第1部分：結構第二版](https://www.w3.org/TR/xmlschema-1/)

- [XML 架構第2部分：資料類型第二版](https://www.w3.org/TR/xmlschema-2/)

- [WSDL 1。1](https://www.w3.org/TR/wsdl/)

- [WS-原則1。2](https://www.w3.org/Submission/2006/SUBM-WS-Policy-20060425/)

- [WS-原則1。5](https://www.w3.org/TR/ws-policy/)

- [WS-Ws-policyattachment 1。2](https://www.w3.org/Submission/2006/SUBM-WS-PolicyAttachment-20060425/)

- [WS-透過 ws-metadataexchange 1。1](https://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)

- [取得中繼資料抓取的 WS-Transfer](https://www.w3.org/Submission/2006/SUBM-WS-Transfer-20060315/)

此外，下列互通性設定檔會跨 WCF 執行：

- [基本設定檔1。1](http://www.ws-i.org/Profiles/BasicProfile-1.1-2004-08-24.html)

- [簡單 SOAP 系結1。0](http://www.ws-i.org/Profiles/SimpleSoapBindingProfile-1.0-2004-08-24.html)

- [基本安全性設定檔1.0 工作草稿](http://www.ws-i.org/Profiles/BasicSecurityProfile-1.0-2006-03-29.html)

## <a name="see-also"></a>請參閱

- [系統提供的互通性繫結所支援的 Web 服務通訊協定](web-services-protocols-supported-by-system-provided-interoperability-bindings.md)
- [訊息通訊協定](messaging-protocols.md)
- [資料合約結構描述參考](data-contract-schema-reference.md)
- [WSDL 與原則](wsdl-and-policy.md)
- [安全性通訊協定](security-protocols.md)
- [可靠傳訊通訊協定 1.0 版](reliable-messaging-protocol-version-1-0.md)
- [可靠傳訊通訊協定 1.1 版](reliable-messaging-protocol-version-1-1.md)
- [傳輸通訊協定](transaction-protocols.md)
- [內容交換通訊協定](context-exchange-protocol.md)
