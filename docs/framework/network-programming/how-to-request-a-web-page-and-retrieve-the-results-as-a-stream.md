---
title: "如何：要求網頁並擷取結果當做資料流 | Microsoft Docs"
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
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# 如何：要求網頁並擷取結果當做資料流
這個範例顯示如何要求 Web 網頁和擷取資料流中的結果。  
  
## 範例  
  
```csharp  
WebClient myClient = new WebClient();  
Stream response = myClient.OpenRead("http://www.contoso.com/index.htm");  
// The stream data is used here.  
response.Close();  
```  
  
```vb  
Dim myClient As WebClient = New WebClient()  
Dim response As Stream = myClient.OpenRead("http://www.contoso.com/index.htm")  
' The stream data is used here.  
response.Close()  
```  
  
## 編譯程式碼  
 這個範例需要：  
  
-   <xref:System.IO> 和 <xref:System.Net> 命名空間的參考。  
  
## 請參閱  
 [要求資料](../../../docs/framework/network-programming/requesting-data.md)