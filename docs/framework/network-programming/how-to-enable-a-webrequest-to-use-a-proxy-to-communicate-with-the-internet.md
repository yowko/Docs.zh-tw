---
title: "如何：啟用 WebRequest 以使用 Proxy 與網際網路通訊 | Microsoft Docs"
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
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# 如何：啟用 WebRequest 以使用 Proxy 與網際網路通訊
這個範例會建立讓所有 <xref:System.Net.WebRequest> 使用 Proxy 與網際網路通訊的全域 Proxy 執行個體。  這個範例假設， Proxy 伺服器名為 `webproxy` ，而且在通訊埠 80 通訊，標準 HTTP 通訊埠。  
  
## 範例  
  
```csharp  
WebProxy proxyObject = new WebProxy("http://webproxy:80/");  
GlobalProxySelection.Select = proxyObject;  
```  
  
```vb  
Dim proxyObject As WebProxy = New WebProxy("http://webproxy:80/")  
GlobalProxySelection.Select = proxyObject  
```  
  
## 編譯程式碼  
 這個範例需要：  
  
-   為 **System.Net** 命名空間的參考。  
  
## 請參閱  
 [使用應用程式通訊協定](../../../docs/framework/network-programming/using-application-protocols.md)   
 [透過 Proxy 存取網際網路](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)