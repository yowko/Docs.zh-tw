---
title: "如何：覆寫全域 Proxy 的選取範圍 | Microsoft Docs"
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
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
caps.latest.revision: 8
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# 如何：覆寫全域 Proxy 的選取範圍
覆寫以具名為連接埠 80 的 `alternateproxy` 的 Proxy 伺服器的全域 Proxy 選取範圍的範例 **WebRequest** 傳送至 www.contoso.com。  
  
## 範例  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## 編譯程式碼  
 這個範例需要：  
  
-   為 **System.Net** 命名空間的參考。  
  
## 請參閱  
 [使用應用程式通訊協定](../../../docs/framework/network-programming/using-application-protocols.md)   
 [透過 Proxy 存取網際網路](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)