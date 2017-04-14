---
title: "二進位序列化 | Microsoft Docs"
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
  - "二進位序列化, 關於序列化"
  - "還原序列化"
  - "序列化, 關於序列化"
ms.assetid: 2b1ea3be-1152-4032-b2b3-07794054c405
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 二進位序列化
可定義序列化為儲存物件狀態至儲存媒體的程序。在此程序中，物件的公用與私用欄位以及類別名稱 \(包括含類別的組件\)，會轉換為位元組資料流，然後寫入資料流當中。當物件隨後還原序列化時，會建立與原始物件完全相同的複製品。  
  
 在物件導向環境中實作序列化機制時，您必須在使用簡易性與彈性之間進行許多取捨。若您對程序擁有足夠的控制，該程序可大幅自動化。例如，可能有簡單二進位序列化並不足夠的情況，或有特定的理由需決定類別中哪個欄位需序列化。下節會檢視 .NET Framework 所提供的穩固序列化機制，並強調數種能讓您自訂程序以滿足需求的重要功能。  
  
> [!NOTE]
>  如果使用不同的 .NET Framework 版本序列化及還原序列化 UTF\-8 或 UTF\-7 編碼的物件，則不會保留該物件的狀態。  
  
## 在本節中  
 [序列化概念](../../../docs/framework/serialization/serialization-concepts.md)  
 討論兩種使用序列化會很有用的案例：一是將資料持續至儲存區，一是跨應用程式定義域傳遞物件。  
  
 [基本序列化](../../../docs/framework/serialization/basic-serialization.md)  
 說明如何使用二進位與 SOAP 格式子來序列化物件。  
  
 [選擇式序列化](../../../docs/framework/serialization/selective-serialization.md)  
 說明如何避免序列化某些類別的成員。  
  
 [自訂序列化](../../../docs/framework/serialization/custom-serialization.md)  
 說明如何使用 <xref:System.Runtime.Serialization.ISerializable> 介面自訂類別的序列化。  
  
 [序列化程序中的步驟](../../../docs/framework/serialization/steps-in-the-serialization-process.md)  
 說明在格式子上呼叫 <xref:System.Runtime.Serialization.Formatter.Serialize%2A> 方法時，執行序列化工作的過程。  
  
 [版本相容序列化](../../../docs/framework/serialization/version-tolerant-serialization.md)  
 說明如何建立可隨時間變更序列化型別，而不會造成應用程式擲回例外狀況。  
  
 [序列化方針](../../../docs/framework/serialization/serialization-guidelines.md)  
 提供決定何時序列化物件的幾個基本指導原則。  
  
## 參考  
 <xref:System.Runtime.Serialization>  
 包含類別，可以用來序列化和還原序列化物件。  
  
## 相關章節  
 [XML 和 SOAP 序列化](../../../docs/framework/serialization/xml-and-soap-serialization.md)  
 說明 Common Language Runtime 中所含的 XML 序列化機制。  
  
 [Security and Serialization](../../../docs/framework/misc/security-and-serialization.md)  
 說明在撰寫執行序列化的程式碼時要遵循的安全程式碼撰寫方針。  
  
 [Remote Objects](http://msdn.microsoft.com/zh-tw/515686e6-0a8d-42f7-8188-73abede57c58)  
 說明 .NET Framework 中可用來進行遠端通訊的各種通訊方法。  
  
 [XML Web Services Created Using ASP.NET and XML Web Service Clients](http://msdn.microsoft.com/zh-tw/1e64af78-d705-4384-b08d-591a45f4379c)  
 提供一個主題，說明並解釋如何設計使用 ASP.NET 建立的 XML Web 服務。