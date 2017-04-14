---
title: "序列化 | Microsoft Docs"
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
  - "二進位序列化"
  - "物件, 序列化"
  - "序列化"
  - "序列化物件"
  - "XML 序列化, 已定義的"
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# 序列化
序列化是將物件的狀態轉換成可保存或傳輸之形式的程序。序列化的互補方法是還原序列化，它將資料流轉換成為物件。將這些程序搭配在一起，可讓資料輕鬆地儲存與傳輸。  
  
 .NET Framework 具有兩項序列化技術：  
  
-   二進位序列化保留型別精確度，這對於在應用程式不同的引動過程之間，保留物件狀態相當實用。例如，藉由將物件序列化至剪貼簿，就可在不同應用程式之間共用該物件。您可以將物件序列化為資料流、序列化至磁碟、記憶體、在網路上序列化等等。在遠端使用序列化從一台電腦或應用程式定義域，以「值」傳遞物件至他處。  
  
-   XML 序列化程序僅對公用屬性與欄位進行序列化，並不保留型別精確度。當您不想限制使用資料的應用程式，而能提供或使用資料時，這種做法就很有用。因為 XML 為開放標準，因此是在 Web 上共用資料的很好選擇。同樣是開放標準的 SOAP，也是一項很好的選擇。  
  
## 在本節中  
 [序列化 HOW TO 主題](../../../docs/framework/serialization/serialization-how-to-topics.md)  
 列出本節中所含的 HOW TO 主題的連結。  
  
 [二進位序列化](../../../docs/framework/serialization/binary-serialization.md)  
 說明 Common Language Runtime 中所含的二進位序列化機制。  
  
 [XML 和 SOAP 序列化](../../../docs/framework/serialization/xml-and-soap-serialization.md)  
 說明 Common Language Runtime 中所含的 XML 和 SOAP 序列化機制。  
  
 [序列化工具](../../../docs/framework/serialization/serialization-tools.md)  
 這些工具可幫助開發序列化程式碼。  
  
 [序列化範例](../../../docs/framework/serialization/serialization-samples.md)  
 以下範例示範如何進行序列化。  
  
## 參考  
 <xref:System.Runtime.Serialization>  
 包含類別，可以用來序列化和還原序列化物件。  
  
 <xref:System.Xml.Serialization>  
 包含可用來將物件序列化為 XML 格式之文件或資料流的類別。  
  
## 相關章節  
 [Remote Objects](http://msdn.microsoft.com/zh-tw/515686e6-0a8d-42f7-8188-73abede57c58)  
 說明 .NET Framework 中可用來進行遠端通訊的各種通訊方法。  
  
 [Advanced Development Technologies](http://msdn.microsoft.com/zh-tw/c4a7e341-f0c6-4df4-a74f-223387ac6e4e)  
 提供與 .NET Framework 中精密的開發工作和技巧有關的詳細資訊之連結。  
  
 [XML Web Services Created Using ASP.NET and XML Web Service Clients](http://msdn.microsoft.com/zh-tw/1e64af78-d705-4384-b08d-591a45f4379c)  
 提供一個主題，說明並解釋如何設計使用 ASP.NET 建立的 XML Web 服務。