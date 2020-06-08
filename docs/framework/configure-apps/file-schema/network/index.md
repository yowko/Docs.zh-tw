---
title: 網路設定結構描述
description: 瞭解網路設定的架構，其指定 .NET Framework 如何連接至網際網路並處理 Uri。
ms.date: 03/30/2017
helpviewer_keywords:
- elements [.NET Framework], network configuration elements
- sending data, network configuration elements
- receiving data, network configuration elements
- configuration settings [.NET Framework], networks
- Internet, network configuration elements
- network configuration elements
- network settings
- connections [.NET Framework], network configuration elements
- network resources, network configuration elements
ms.assetid: f1de5a0f-76c5-4833-819f-5222b8146340
ms.openlocfilehash: 6a22d7f1608db2e8909d0ead11e9110ec8a8a2c5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504572"
---
# <a name="network-settings-schema"></a>網路設定結構描述
網路設定會指定 .NET Framework 如何連接至網際網路。

這些 \<system.net> 設定會指定 .NET Framework 如何連接到網路。 下表描述[ \<system.Net> 元素（網路設定）](system-net-element-network-settings.md)底下每個子 configuration 專案的功能。  
  
|元素|描述|  
|-------------|-----------------|  
|[\<authenticationModules>元素（網路設定）](authenticationmodules-element-network-settings.md)|指定用來驗證網際網路要求的模組。|  
|[\<connectionManagement>元素（網路設定）](connectionmanagement-element-network-settings.md)|指定連線到網際網路主機的最大連線數目。|  
|[\<defaultProxy>元素（網路設定）](defaultproxy-element-network-settings.md)|指定用於網際網路之 HTTP 要求的 Proxy 伺服器。|  
|[\<mailSettings>元素（網路設定）](mailsettings-element-network-settings.md)|包含郵件傳送選項的設定。|  
|[\<requestCaching>元素（網路設定）](requestcaching-element-network-settings.md)|控制網路要求的快取機制。|  
|[\<webRequestModules>元素（網路設定）](webrequestmodules-element-network-settings.md)|指定用來向網際網路主機要求資訊的模組。|  
  
這些 \<uri> 設定會指定 .NET Framework 如何處理使用統一資源識別項（uri）所表示的 web 位址。 下表描述專案[ \<uri> （Uri 設定）](uri-element-uri-settings.md)底下每個子設定元素的功能。  
  
|元素|描述|  
|-------------|-----------------|  
|[\<idn>元素（Uri 設定）](idn-element-uri-settings.md)|指定是否要對網域名稱套用國際化網域名稱 (IDN) 剖析。|  
|[\<iriParsing>元素（Uri 設定）](iriparsing-element-uri-settings.md)|指定是否要將國際資源識別項 (IRI) 剖析套用至 <xref:System.Uri>，以及是否應該套用 IRI 剖析規則。|  
|[\<schemeSettings>元素（Uri 設定）](schemesettings-element-uri-settings.md)|指定如何針對特定配置剖析 <xref:System.Uri>。|  
  
## <a name="see-also"></a>另請參閱

- [設定網際網路應用程式](../../../network-programming/configuring-internet-applications.md)
- [設定檔架構](../index.md)
