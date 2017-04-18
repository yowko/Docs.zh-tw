---
title: "序列化概念 | Microsoft Docs"
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
ms.assetid: e1ff4740-20a1-4c76-a8ad-d857db307054
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# 序列化概念
為何會想要使用序列化？最重要的兩大原因是，在儲存媒體中保持物件的狀態以便在稍後階段重建完全相同的複本，以及利用值在應用程式定義域之間傳送物件。例如，使用序列化來儲存 ASP.NET 的工作階段狀態，並且複製物件至 Windows Forms 的剪貼簿。它也供遠端使用，利用值在應用程式定義域之間傳遞物件。  
  
## 在本節中  
 [持續性儲存體](../../../docs/framework/serialization/persistent-storage.md)  
 說明序列化物件的需要。  
  
 [以傳值方式封送處理](../../../docs/framework/serialization/marshal-by-value.md)  
 設明傳值封送處理的程序。  
  
## 相關章節  
 [二進位序列化](../../../docs/framework/serialization/binary-serialization.md)  
 說明 Common Language Runtime 中所含的二進位序列化機制。  
  
 [Remote Objects](http://msdn.microsoft.com/zh-tw/515686e6-0a8d-42f7-8188-73abede57c58)  
 說明 .NET Framework 中可用來進行遠端通訊的各種通訊方法。  
  
 [XML 和 SOAP 序列化](../../../docs/framework/serialization/xml-and-soap-serialization.md)  
 說明 Common Language Runtime 中所含的 XML 和 SOAP 序列化機制。