---
title: 網路設定結構描述
description: 深入瞭解網路設定的架構，這些設定會指定 .NET Framework 如何連接到網際網路並處理 Uri。
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
ms.openlocfilehash: 8071fcfcdb16b6e71d8d7af05a704d8842b3e963
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158912"
---
# <a name="network-settings-schema"></a>網路設定結構描述

網路設定會指定 .NET Framework 如何連接至網際網路。

這些 \<system.net> 設定會指定 .NET Framework 如何連接到網路。 下表描述專案底下的每個子[ \<system.Net> 設定專案 (網路設定) ](system-net-element-network-settings.md)的功能。  
  
|項目|描述|  
|-------------|-----------------|  
|[\<authenticationModules> (網路設定的元素) ](authenticationmodules-element-network-settings.md)|指定用來驗證網際網路要求的模組。|  
|[\<connectionManagement> (網路設定的元素) ](connectionmanagement-element-network-settings.md)|指定連線到網際網路主機的最大連線數目。|  
|[\<defaultProxy> (網路設定的元素) ](defaultproxy-element-network-settings.md)|指定用於網際網路之 HTTP 要求的 Proxy 伺服器。|  
|[\<mailSettings> (網路設定的元素) ](mailsettings-element-network-settings.md)|包含郵件傳送選項的設定。|  
|[\<requestCaching> (網路設定的元素) ](requestcaching-element-network-settings.md)|控制網路要求的快取機制。|  
|[\<webRequestModules> (網路設定的元素) ](webrequestmodules-element-network-settings.md)|指定用來向網際網路主機要求資訊的模組。|  
  
這些 \<uri> 設定會指定 .NET Framework 如何使用 (uri) 的統一資源識別項來處理 web 位址。 下表描述專案底下的每個子設定元素的函式[ \<uri> (Uri 設定) ](uri-element-uri-settings.md)。  
  
|項目|描述|  
|-------------|-----------------|  
|[\<idn> (Uri 設定的元素) ](idn-element-uri-settings.md)|指定是否要對網域名稱套用國際化網域名稱 (IDN) 剖析。|  
|[\<iriParsing> (Uri 設定的元素) ](iriparsing-element-uri-settings.md)|指定是否要將國際資源識別項 (IRI) 剖析套用至 <xref:System.Uri>，以及是否應該套用 IRI 剖析規則。|  
|[\<schemeSettings> (Uri 設定的元素) ](schemesettings-element-uri-settings.md)|指定如何針對特定配置剖析 <xref:System.Uri>。|  
  
## <a name="see-also"></a>另請參閱

- [設定網際網路應用程式](../../../network-programming/configuring-internet-applications.md)
- [設定檔架構](../index.md)
