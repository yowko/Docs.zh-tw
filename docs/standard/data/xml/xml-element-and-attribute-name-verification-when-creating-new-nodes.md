---
title: "建立新節點時 XML 項目和屬性名稱的驗證 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
caps.latest.revision: 5
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 5
---
# 建立新節點時 XML 項目和屬性名稱的驗證
XML 文件物件模型 \(DOM\) 在建立新項目節點或屬性節點時會檢查名稱的有效性。  如果名稱包含不合法字元，則會擲回例外狀況。  若要確保名稱是有效的且被正確編碼，您必須使用 **XmlConvert** 類別在應用程式層級來編碼名稱並且將它解碼。  **XmlWriter** 有方法來執行其他工作，以確保會產生格式正確的 XML。  
  
## 請參閱  
 [XML 文件物件模型 \(DOM\)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)