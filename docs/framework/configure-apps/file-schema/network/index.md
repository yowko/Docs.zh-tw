---
title: "網路設定結構描述 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "組態設定 [.NET Framework], 網路"
  - "連接 [.NET Framework], 網路組態項目"
  - "項目 [.NET Framework], 網路組態項目"
  - "網際網路, 網路組態項目"
  - "網路組態項目"
  - "網路資源, 網路組態項目"
  - "網路設定"
  - "接收資料, 網路組態項目"
  - "傳送資料, 網路組態項目"
ms.assetid: f1de5a0f-76c5-4833-819f-5222b8146340
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# 網路設定結構描述
網路設定指定 .NET Framework 如何連接至網際網路。  下表說明 [\<system.net\> 項目 \(網路設定\)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) 中每個子組態項目的功能。  
  
|元素|說明|  
|--------|--------|  
|[\<authenticationModules\> 項目 \(網路設定\)](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|指定用於驗證網際網路要求的模組。|  
|[\<connectionManagement\> 項目 \(網路設定\)](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|指定連結至網際網路主機的最大數目。|  
|[\<defaultProxy\> 項目 \(網路設定\)](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|指定用於對網際網路 HTTP 要求的 Proxy 伺服器。|  
|[\<mailSettings\> 項目 \(網路設定\)](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|包含郵件傳回選項的設定。|  
|[\<requestCaching\> 項目 \(網路設定\)](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|指定用於向網際網路主機要求資訊的模組。|  
|[\<requestCaching\> 項目 \(網路設定\)](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|為 <xref:System.Net?displayProperty=fullName> 命名空間設定基本的網路選項。|  
|[\<webRequestModules\> 項目 \(網路設定\)](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|指定用於向網際網路主機要求資訊的模組。|  
  
 URI設定指定 .NET Framework 如何處理使用統一資源識別元 \(URI\) 表示的網址。  下表說明 [\<Uri\> 項目 \(Uri 設定\)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md) 中每個子組態項目的功能。  
  
|元素|說明|  
|--------|--------|  
|[\<idn\> 項目 \(Uri 設定\)](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|指定是否要對網域名稱套用國際化網域名稱 \(Internationalized Domain Name，IDN\) 剖析。|  
|[\<iriParsing\> 項目 \(Uri 設定\)](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|指定是否要將國際資源識別項 \(International Resource Identifier，IRI\) 剖析套用至 <xref:System.Uri>，以及是否應該套用 IRI 剖析規則。|  
|[\<schemeSettings\> 項目 \(Uri 設定\)](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|指定如何針對特定配置剖析 <xref:System.Uri>。|  
  
## 請參閱  
 [設定網際網路應用程式](../../../../../docs/framework/network-programming/configuring-internet-applications.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)