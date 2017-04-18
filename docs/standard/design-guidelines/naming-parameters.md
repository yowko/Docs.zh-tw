---
title: "命名參數 | Microsoft Docs"
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
  - "參數名稱"
  - "名稱 [.NET Framework] 參數"
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 命名參數
超過可讀性的明顯原因，是遵循的指導方針參數名稱，因為參數時，會顯示在文件和設計工具的視覺化設計工具提供 Intellisense 和瀏覽功能的類別。  
  
 **✓ 執行** camelCasing 用於參數名稱。  
  
 **✓ 執行** 使用描述性的參數名稱。  
  
 **✓ 考慮** 使用根據參數的意義，而不是參數的型別名稱。  
  
### 運算子多載的參數命名  
 **✓ 執行** 使用 `left` 和 `right` 的二元運算子多載的參數名稱是否有任何參數的意義。  
  
 **✓ 執行** 使用 `value` 的一元運算子多載的參數名稱是否有任何參數的意義。  
  
 **✓ 考慮** 如果這樣做會增加重要的值的參數多載的運算子有意義的名稱。  
  
 **X 不** 使用縮寫或數值索引運算子多載的參數名稱。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)   
 [命名方針](../../../docs/standard/design-guidelines/naming-guidelines.md)