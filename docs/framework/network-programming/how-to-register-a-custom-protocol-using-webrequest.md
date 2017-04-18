---
title: "如何：使用 WebRequest 註冊自訂通訊協定 | Microsoft Docs"
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
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# 如何：使用 WebRequest 註冊自訂通訊協定
這個範例顯示如何註冊通訊協定專屬的 classthat在其他地方定義。  在此範例中， `CustomWebRequestCreator` 是使用者實作之物件 `CustomWebRequest` 實作傳回物件的 **建立** 方法。  程式碼範例假設您已撰寫，實作自訂通訊協定的 `CustomWebRequest` 程式碼。  
  
## 範例  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## 編譯程式碼  
 這個範例需要：  
  
 為 <xref:System.Net> 命名空間的參考。  
  
## 請參閱  
 [可插式通訊協定程式設計](../../../docs/framework/network-programming/programming-pluggable-protocols.md)