---
title: "泛型的優點 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "泛型 [C#], 好處"
ms.assetid: 80f037cd-9ea7-48be-bfc1-219bfb2d4277
caps.latest.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 23
---
# 泛型的優點 (C# 程式設計手冊)
在舊版 Common Language Runtime 和 C\# 語言中，您必須將型別來回轉換成通用基底型別 <xref:System.Object>，才能達成泛型化的目的，而現在有了泛型，便得以突破這項限制。  藉由建立泛型類別，您可以建立在編譯時期為型別安全的集合。  
  
 使用非泛型集合類別的限制，可透過撰寫將會使用 .NET Framework 類別庫之 <xref:System.Collections.ArrayList> 集合類別的簡短程式來示範。  <xref:System.Collections.ArrayList> 是十分方便的集合類別，可以在不經修改下，用以儲存任何參考或實值型別。  
  
 [!code-cs[csProgGuideGenerics#4](../../../csharp/programming-guide/generics/codesnippet/csharp/benefits-of-generics_1.cs)]  
  
 但這種方便性是要付出代價的。  加入 <xref:System.Collections.ArrayList> 的任何參考或實值型別都會隱含向上轉型成 <xref:System.Object>。  如果項目屬於實值型別，加入清單時必須先經 boxed 處理，而擷取時則需經過 unboxed 處理。  轉型、boxing 和 unboxing 作業都會降低效能，因此，在必須逐一查看大型集合的案例中，boxing 和 unboxing 作業會對效能影響甚鉅。  
  
 另一個限制則是缺少編譯時期的型別檢查。由於 <xref:System.Collections.ArrayList> 會將所有項目都轉型成 <xref:System.Object>，所以在編譯時期並無法防止用戶端執行如下面這段的程式碼：  
  
 [!code-cs[csProgGuideGenerics#5](../../../csharp/programming-guide/generics/codesnippet/csharp/benefits-of-generics_2.cs)]  
  
 雖然在建立異質性集合時是完全合於語法，而且有時是刻意這麼做，但在單一 <xref:System.Collections.ArrayList> 中結合使用字串和 `ints`，更有可能會視為程式設計錯誤，而且直到執行階段才會偵測出此錯誤。  
  
 在 C\# 語言的 1.0 和 1.1 版中，若要避免 .NET Framework 基底類別程式庫集合類別中的泛型化程式碼造成問題，唯一的方法就是自行撰寫型別特定的集合。  當然，由於這種類別不能在多種資料型別中重複使用，而就無法發揮泛型化的優點，且必須替每種需要儲存的型別重新撰寫類別。  
  
 <xref:System.Collections.ArrayList> 及其他相似類別真正需要的是，可以讓用戶端程式碼視每個執行個體而定，指定要使用的特定資料型別。  如此就不再需要向上轉型成 `T:System.Object`，而編譯器也可以進行型別檢查。  換句話說，<xref:System.Collections.ArrayList> 需要型別參數。  這正好是泛型可以提供的。  在泛型 <xref:System.Collections.Generic.List%601> 集合的 `N:System.Collections.Generic` 命名空間中，同樣是將項目加入集合，但看起來會像這樣：  
  
 [!code-cs[csProgGuideGenerics#6](../../../csharp/programming-guide/generics/codesnippet/csharp/benefits-of-generics_3.cs)]  
  
 對用戶端程式碼來說，相較於 <xref:System.Collections.ArrayList>，<xref:System.Collections.Generic.List%601> 唯一增加的語法就是宣告和執行個體化中的型別引數。  雖然程式碼撰寫起來稍微複雜，但您所建立的清單不但比 <xref:System.Collections.ArrayList> 安全，同時也快速許多，特別是清單項目為實值型別時。  
  
## 請參閱  
 <xref:System.Collections.Generic>   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [泛型簡介](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [Boxing 和 Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)   
 [集合最佳做法](http://go.microsoft.com/fwlink/?LinkId=112403)