---
title: "規則運算式範例 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "規則運算式 [.NET Framework]，範例"
  - "規則運算式 [.NET Framework]"
  - "字串 [.NET Framework]，規則運算式"
ms.assetid: e9fd53f2-ed56-4b09-b2ea-e9bc9d65e6d6
caps.latest.revision: 17
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 17
---
# 規則運算式範例
這個章節包含的程式碼範例說明規則運算式在通用應用程式中的使用方式。  
  
> [!NOTE]
>  <xref:System.Web.RegularExpressions> 命名空間包含許多規則運算式物件，這些物件會實作預先定義的規則運算式模式，用來剖析來自 HTML、XML 和 ASP.NET 文件的字串。  例如，<xref:System.Web.RegularExpressions.TagRegex> 類別會識別字串中的開始標記，而 <xref:System.Web.RegularExpressions.CommentRegex> 類別則會識別字串中的 ASP.NET 註解。  
  
## 在本節中  
 [範例：掃描 HREF](../../../docs/standard/base-types/regular-expression-example-scanning-for-hrefs.md)  
 提供搜尋輸入字串並印出所有 href\="…" 值和它們在字串中的位置的範例。  
  
 [範例：變更日期格式](../../../docs/standard/base-types/regular-expression-example-changing-date-formats.md)  
 提供以 dd\-mm\-yy 日期格式取代 mm\/dd\/yy 日期格式的範例。  
  
 [如何：從 URL 擷取通訊協定和通訊埠編號](../../../docs/standard/base-types/how-to-extract-a-protocol-and-port-number-from-a-url.md)  
 提供從包含 URL 的字串中擷取通訊協定與埠號的範例。  例如，"http:\/\/www.contoso.com:8080\/letters\/readme.html" 將會傳回 "http:8080"。  
  
 [如何：從字串中刪除無效的字元](../../../docs/standard/base-types/how-to-strip-invalid-characters-from-a-string.md)  
 提供範例從字串中刪除無效非英數字元的範例。  
  
 [如何：確認字串是否為有效的電子郵件格式](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md)  
 提供可以用來驗證字串是有效電子郵件格式的範例。  
  
## 參考  
 <xref:System.Text.RegularExpressions>  
 提供 .NET Framework **System.Text.RegularExpressions** 命名空間的類別庫參考資訊。  
  
## 相關章節  
 [.NET Framework 規則運算式](../../../docs/standard/base-types/regular-expressions.md)  
 提供規則運算式之程式設計語言方面的概觀。  
  
 [規則運算式物件模型](../../../docs/standard/base-types/the-regular-expression-object-model.md)  
 描述包含在 `System.Text.RegularExpression` 命名空間中的規則運算式類別，並提供其使用範例。  
  
 [規則運算式行為的詳細資訊](../../../docs/standard/base-types/details-of-regular-expression-behavior.md)  
 提供有關 .NET Framework 規則運算式的功能和行為的詳細資訊。  
  
 [規則運算式語言 \- 快速參考](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 提供一組可以用來定義規則運算式的字元、運算子以及建構的資訊。