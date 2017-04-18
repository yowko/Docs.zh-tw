---
title: "擴充方法 | Microsoft Docs"
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
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
caps.latest.revision: 4
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 4
---
# 擴充方法
擴充方法是一項語言功能，可讓靜態方法，以使用執行個體方法呼叫語法來呼叫。 這些方法必須採用至少一個參數，表示要對方法的執行個體。  
  
 定義此類擴充方法的類別稱為 「 贊助商 」 類別，且它必須為靜態宣告。 若要使用擴充方法，一個必須匯入定義的贊助者類別的命名空間。  
  
 **X 避免** frivolously 特別是在不屬於您的型別上定義擴充方法。  
  
 如果您擁有原始碼的型別，請考慮改為使用一般的執行個體方法。 如果不屬於您，而且您想要新增的方法，要非常小心。 盡量使用延伸方法有可能會佔用 Api 都不具有這些方法的型別。  
  
 **✓ 考慮** 在任何下列案例中使用擴充方法︰  
  
-   若要提供協助程式功能相關的介面，每個實作說功能可以核心介面來撰寫。 這是因為具象實作否則無法指派給介面。 例如， `LINQ to Objects` 運算子當做擴充方法實作所有 <xref:System.Collections.Generic.IEnumerable%601> 型別。 因此，任何 `IEnumerable<>` 實作是自動啟用 LINQ。  
  
-   當執行個體方法會造成相依於某些型別，但是這類相依性會中斷相依性管理規則。 例如，從相依性 <xref:System.String> 至 <xref:System.Uri?displayProperty=fullName> 可能不是恰當的，因此 `String.ToUri()` 傳回的執行個體方法 `System.Uri` 錯誤的設計相依性管理的觀點而言。 靜態擴充方法 `Uri.ToUri(this string str)` 傳回 `System.Uri` 會是更好的設計。  
  
 **X 避免** 上定義擴充方法 <xref:System.Object?displayProperty=fullName>。  
  
 VB 使用者不能使用延伸方法語法的物件參考上呼叫這類方法。 VB 不支援呼叫這類方法，因為在 VB 中，宣告的參考，因為物件會強制所有的方法引動過程上是晚期繫結 （名為實際的成員判斷在執行階段），而繫結到擴充方法在編譯階段 （早期繫結） 決定。  
  
 請注意指導方針適用於相同的繫結行為，其他語言，或不支援的擴充方法。  
  
 **X 不** 放在擴充的型別相同的命名空間的擴充方法，除非它是將方法加入至介面或相依性管理。  
  
 **X 避免** 定義兩個或多個擴充方法使用相同的簽章，即使它們位於不同的命名空間。  
  
 **✓ 考慮** 擴充的型別相同的命名空間中定義的擴充方法，如果型別是介面，並擴充方法適用於大部分或所有的情況下。  
  
 **X 不** 定義擴充方法實作一項功能通常與其他功能相關聯的命名空間中。 相反地，在其所屬的功能與相關聯的命名空間中定義它們。  
  
 **X 避免** 泛型命名的命名空間專門用來擴充方法 （例如，「 擴充功能 」）。 使用描述性名稱 （例如，「 路由 」） 而。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [成員設計方針](../../../docs/standard/design-guidelines/member.md)   
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)