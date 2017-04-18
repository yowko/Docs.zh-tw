---
title: "等號比較運算子 | Microsoft Docs"
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
  - "類別庫設計方針 [.NET Framework] Equals 方法"
  - "類別庫設計方針 [.NET Framework] 等號比較運算子"
  - "等號比較運算子 （= =） [.NET Framework]"
  - "Equals 方法"
  - "= = 運算子 （相等） [.NET Framework]"
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# 等號比較運算子
本節討論多載等號比較運算子並參照 `operator==` 和 `operator!=` 為等號比較運算子。  
  
 **X 不** 的等號比較運算子，而另一個多載。  
  
 **✓ 執行** 確定 <xref:System.Object.Equals%2A?displayProperty=fullName> 和等號比較運算子有完全相同的語意和類似的效能特性。  
  
 這通常表示 `Object.Equals` 需要覆寫等號比較運算子多載。  
  
 **X 避免** 擲回例外狀況從等號比較運算子。  
  
 例如，傳回 false，如果其中一個引數為 null，而非擲回 `NullReferenceException`。  
  
## 實值型別上的等號比較運算子  
 **✓ 執行** 多載等號比較運算子，實值類型，如果是有意義的等號比較。  
  
 在大部分的程式設計語言，沒有預設實作的 `operator==` 實值型別。  
  
## 參考型別上的等號比較運算子  
 **X 避免** 多載可變動參考類型的等號比較運算子。  
  
 許多語言會有參考類型的內建的等號比較運算子。 內建運算子通常會實作參考相等，以及預設的行為變更為實值相等時，許多開發人員都會很驚訝。  
  
 因為不變性會注意到參考相等與實值相等之間的差異很難的不可變的參考型別以降低這個問題。  
  
 **X 避免** 多載等號比較運算子參考型別上的，如果實作會明顯變慢的參考相等。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)   
 [用法方針](../../../docs/standard/design-guidelines/usage-guidelines.md)