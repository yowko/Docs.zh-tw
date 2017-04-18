---
title: "實作抽象的基底類別 | Microsoft Docs"
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
  - "抽象 [.NET Framework]"
  - "基底類別的抽象概念"
ms.assetid: 37a2d9a4-9721-482a-a40f-eee2c1d97875
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 實作抽象的基底類別
嚴格來說，當從它衍生其他類別類別成為基底類別。 不過，為了本章節中，基底類別是設計主要是為了提供通用抽象或重複使用一些其他類別的預設實作透過繼承的類別。 基底類別通常的繼承階層架構的階層根目錄的抽象概念和數個在底部的自訂實作之間的中間位置。  
  
 它們會充當實作協助程式實作抽象的。 例如，其中一個項目的已排序集合的架構的抽象概念是 <xref:System.Collections.Generic.IList%601> 介面。 實作 <xref:System.Collections.Generic.IList%601> 並非易事，並因此架構提供數個基底類別，例如 <xref:System.Collections.ObjectModel.Collection%601> 和 <xref:System.Collections.ObjectModel.KeyedCollection%602>, ，其做為實作自訂集合的協助程式。  
  
 基底類別是通常不適合作為抽象概念，因為它們包含太多的實作。 比方說， `Collection<T>` 基底類別包含許多相關的事實，它會實作非泛型實作 `IList` 介面 （以整合更理想與非泛型集合），它是儲存在記憶體中其中一個欄位的項目集合的事實。  
  
 如先前所述，基底類別可提供寶貴的說明的使用者必須實作的抽象概念，但同時也很重要的責任。 在新增介面區和增加繼承階層架構深度和因此概念讓問題更複雜的架構。 因此，它們提供重大價值架構的使用者，才應該使用基底類別。 它們應該避免如果它們的架構，應該強烈考慮大小寫委派內部實作，而不是繼承自基底類別實作，才能提供的值。  
  
 **✓ 考慮** 讓基底類別的抽象，即使它們不包含任何抽象的成員。 明確地溝通的使用者，此類別的設計只是要繼承自。  
  
 **✓ 考慮** 置於不同的命名空間從主線情節類型的基底類別。 根據定義，基底類別適用於進階的擴充性案例，因此不需要大多數的使用者。  
  
 **X 避免** 命名基底類別，以"將 Base"後置字元，如果類別用於公用 Api 中使用。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)   
 [擴充性設計](../../../docs/standard/design-guidelines/designing-for-extensibility.md)