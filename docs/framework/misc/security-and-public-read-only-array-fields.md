---
title: "Security and Public Read-only Array Fields | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
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
  - "security [.NET Framework], public read-only array fields"
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
caps.latest.revision: 7
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 7
---
# Security and Public Read-only Array Fields
請勿使用來自 Managed 程式庫的唯讀公用陣列欄位，來定義應用程式的界限行為或安全性，因為唯讀公用陣列欄位是可以修改的。  
  
## 備註  
 有些 .NET Framework 類別包括唯讀的公用欄位，內含平台特定的界限參數。例如，<xref:System.IO.Path.InvalidPathChars> 欄位是一個陣列，說明了不允許出現在檔案路徑字串中的字元。整個 .NET Framework 有許多類似的欄位。  
  
 如 <xref:System.IO.Path.InvalidPathChars> 這類公用唯讀欄位的值，可以利用您的程式碼或應用程式定義域的共用程式碼加以修改。您不應該像這樣使用唯讀公用陣列欄位，來定義應用程式的界限行為。如果這麼做，會讓惡意程式碼有機會變更界限定義，並以無法預期的方式使用您的程式碼。  
  
 在 2.0 \(含\) 以後版本的 .NET Framework 中，您必須使用傳回新陣列的方法，而非使用公用陣列欄位。例如，您應該使用 <xref:System.IO.Path.GetInvalidPathChars%2A> 方法，而非 <xref:System.IO.Path.InvalidPathChars> 欄位。  
  
 請注意，.NET Framework 型別內部也不使用公用欄位來定義界限型別。.NET Framework 使用的是個別的私用欄位。變更這些公用欄位的值並不會改變 .NET Framework 型別的行為。  
  
## 請參閱  
 [Secure Coding Guidelines](../../../docs/standard/security/secure-coding-guidelines.md)