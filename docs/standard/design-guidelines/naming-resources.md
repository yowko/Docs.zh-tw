---
title: "命名資源 | Microsoft Docs"
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
helpviewer_keywords: 
  - "名稱 [.NET Framework] 當地語系化資源"
  - "當地語系化命名方針"
  - "資源名稱"
  - "命名方針的全球化應用程式"
  - "國際化應用程式，命名方針"
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 命名資源
也可以透過某些物件參考可當地語系化的資源，如同它們是屬性，因為資源命名方針是類似屬性的指導方針。  
  
 **✓ 執行** PascalCasing 用於資源索引鍵。  
  
 **✓ 執行** 提供描述性的而不是簡短的識別項。  
  
 **X 不** 使用主要 CLR 語言的語言特有的關鍵字。  
  
 **✓ 執行** 使用只有英數字元和底線命名資源。  
  
 **✓ 執行** 例外狀況訊息資源使用下列命名慣例。  
  
 資源識別項應該是例外狀況型別名稱加上例外狀況的簡短識別項︰  
  
 `ArgumentExceptionIllegalCharacters`   
 `ArgumentExceptionInvalidName`   
 `ArgumentExceptionFileNameIsMalformed`  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)   
 [命名方針](../../../docs/standard/design-guidelines/naming-guidelines.md)