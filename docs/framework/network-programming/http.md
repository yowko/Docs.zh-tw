---
title: "HTTP | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "通訊協定，HTTP"
  - "傳送資料，HTTP"
  - "HttpWebResponse 類別，傳送和接收資料"
  - "HTTP"
  - "接收資料，HTTP"
  - "應用程式通訊協定，HTTP"
  - "網際網路，HTTP"
  - "網路資源，HTTP"
  - "HTTP，關於 HTTP"
  - "HttpWebRequest 類別，傳送和接收資料"
ms.assetid: 985fe5d8-eb71-4024-b361-41fbdc1618d8
caps.latest.revision: 10
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# HTTP
.NET Framework 使用 HTTP 通訊協定提供廣泛的支援，構成大部分人員所有網路傳遞，以<xref:System.Net.HttpWebRequest> 和 <xref:System.Net.HttpWebResponse> 類別。  這些類別是衍生自， <xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse>傳回，根據預設，當靜態方法 <xref:System.Net.WebRequest.Create%2A?displayProperty=fullName> 從「http」或「、」開頭遇到 URI。  在許多情況下， **WebRequest** 和 **WebResponse** 類別提供所有必要提出要求，，不過，如果您需要為屬性所公開的 HTTP 特定功能的存取權，可能會將角色這些類別加入至 **HttpWebRequest** 或 **HttpWebResponse**。  
  
 **HttpWebRequest** 和 **HttpWebResponse** 封裝一種標準 HTTP 要求和回應交易並提供對通用 HTTP 標頭。  這些類別也支援大部分的 HTTP 1.1 功能，包括管線，傳送和接收大量、驗證、預先驗證、加密、支援、Proxy 伺服器憑證驗證和連結管理的資料。  可以儲存自訂透過屬性所提供的標頭和頁首和 **Headers** 透過屬性存取。  
  
 在中，您可以將 URI 加入至 **WebRequest.Create** 方法之前，**HttpWebRequest** 是 **WebRequest** 所使用的預設類別，而不需要註冊。  
  
 您可以讓應用程式遵循 HTTP 藉由設定 <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> 屬性會自動重新導向至 **true** \(預設值\)。  應用程式重新導向要求，然後， **HttpWebResponse**[ResponseURI](frlrfsystemnethttpwebresponseclassresponseuritopic) 屬性將包含回應要求的實際 Web 資源。  如果您要 **false**的集合 **AllowAutoRedirect** ，您的應用程式必須能夠處理重新導向為 HTTP 通訊協定錯誤。  
  
 應用程式會藉由快取 <xref:System.Net.WebException> 接收 HTTP 通訊協定錯誤和 <xref:System.Net.WebException.Status%2A> 設為 [WebExceptionStatus.ProtocolError](frlrfsystemnetwebexceptionstatusclasstopic)。  <xref:System.Net.WebException.Response%2A> 屬性包含由伺服器傳送的 **WebResponse** 並指出遇到的實際 HTTP 錯誤。  
  
## 請參閱  
 [透過 Proxy 存取網際網路](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)   
 [使用應用程式通訊協定](../../../docs/framework/network-programming/using-application-protocols.md)   
 [如何：存取 HTTP 特定屬性](../../../docs/framework/network-programming/how-to-access-http-specific-properties.md)