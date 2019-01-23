---
title: 網路設定結構描述
ms.date: 03/30/2017
helpviewer_keywords:
  - 'elements [.NET Framework], network configuration elements'
  - 'sending data, network configuration elements'
  - 'receiving data, network configuration elements'
  - 'configuration settings [.NET Framework], networks'
  - 'Internet, network configuration elements'
  - network configuration elements
  - network settings
  - 'connections [.NET Framework], network configuration elements'
  - 'network resources, network configuration elements'
ms.assetid: f1de5a0f-76c5-4833-819f-5222b8146340
---
# <a name="network-settings-schema"></a>網路設定結構描述
網路設定會指定 .NET Framework 如何連接至網際網路。 下表描述 [\<system.Net> 項目 (網路設定)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) 下每個子組態項目的功能。  
  
|元素|描述|  
|-------------|-----------------|  
|[\<authenticationModules> 項目 (網路設定)](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|指定用來驗證網際網路要求的模組。|  
|[\<connectionManagement> 項目 (網路設定)](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|指定連線到網際網路主機的最大連線數目。|  
|[\<defaultProxy> 項目 (網路設定)](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|指定用於網際網路之 HTTP 要求的 Proxy 伺服器。|  
|[\<mailSettings> 項目 (網路設定)](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|包含郵件傳送選項的設定。|  
|[\<requestCaching> 項目 (網路設定)](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|控制網路要求的快取機制。|  
|[\<webRequestModules> 項目 (網路設定)](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|指定用來向網際網路主機要求資訊的模組。|  
  
 URI 設定會指定 .NET Framework 如何處理使用統一資源識別元 (URI) 表示的網站位址。 下表描述 [\<URI> 項目 (URI 設定)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md) 下每個子組態項目的功能。  
  
|元素|描述|  
|-------------|-----------------|  
|[\<idn> 項目 (URI設定)](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|指定是否要對網域名稱套用國際化網域名稱 (IDN) 剖析。|  
|[\<iriParsing> 項目 (URI 設定)](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|指定是否要將國際資源識別項 (IRI) 剖析套用至 <xref:System.Uri>，以及是否應該套用 IRI 剖析規則。|  
|[\<schemeSettings> 項目 (URI 設定)](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|指定如何針對特定配置剖析 <xref:System.Uri>。|  
  
## <a name="see-also"></a>另請參閱
- [設定網際網路應用程式](../../../../../docs/framework/network-programming/configuring-internet-applications.md)
- [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
