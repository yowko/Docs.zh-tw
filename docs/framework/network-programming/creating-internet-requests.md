---
title: "建立網際網路要求 | Microsoft Docs"
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
  - "WebRequest 類別，傳送和接收資料"
  - "網路"
  - "HttpWebResponse 類別，傳送和接收資料"
  - "從網際網路要求資料，建立要求"
  - "網路資源"
  - "網際網路，要求資料"
  - "資料要求，建立要求"
ms.assetid: faab683e-3f1e-4eee-b5e9-59f7245033d5
caps.latest.revision: 8
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# 建立網際網路要求
應用程式會 <xref:System.Net.WebRequest.Create%2A?displayProperty=fullName><xref:System.Net.WebRequest> 方法建立執行個體。  這是建立 **WebRequest** 從衍生的類別會根據 URI 配置傳遞給類別的靜態方法。  
  
## Web、檔案和 FTP 要求  
 .NET Framework 提供 <xref:System.Net.HttpWebRequest> 類別，從 **WebRequest**衍生，處理 HTTP 和 HTTPS 要求。  在許多情況下， **WebRequest** 類別提供需要進行所有必要的屬性;如果需要，在中，您可以將轉換 **WebRequest.Create** 方法所建立的 **WebRequest** 物件 **HttpWebRequest** 型別存取所要求的 HTTP 特定屬性。  同樣地， **HttpWebResponse** 物件控制代碼從 HTTP 和 HTTPS 要求的回應。  若要存取 **HttpWebResponse** 的 HTTP 特定屬性的物件，您需要轉換成 **HttpWebResponse** 型別的 **WebResponse** 物件。  
  
 .NET Framework 也提供 <xref:System.Net.FileWebRequest> 和 <xref:System.Net.FileWebResponse> 類別來處理要求中使用「檔案的資源: 」URI 配置。  同樣地， <xref:System.Net.FtpWebRequest> 和 <xref:System.Net.FtpWebResponse> 類別提供控制代碼所需使用這個「ftp 的資源: 」配置。  如果要求是使用這些配置中的任何一個資源，您可以使用方法取得 **WebRequest.Create** 進行要求的物件。  
  
 若要處理使用其他應用程式層級通訊協定的要求，您必須實作繼承自 **WebRequest** 和 **WebResponse**衍生的通訊協定的特定類別。  如需詳細資訊，請參閱 [程式設計可外掛式通訊協定](../../../docs/framework/network-programming/programming-pluggable-protocols.md)。  
  
## 請參閱  
 [如何：使用 WebRequest 類別要求資料](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)   
 [要求資料](../../../docs/framework/network-programming/requesting-data.md)