---
title: "管理陣列和清單的泛型委派 | Microsoft Docs"
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
  - "陣列 [.NET Framework], 泛型委派"
  - "變更委派"
  - "委派 [.NET Framework], 泛型委派"
  - "泛型委派 [.NET Framework]"
  - "泛型 [.NET Framework], 委派"
  - "清單 [.NET Framework], 泛型委派"
ms.assetid: 416be383-cc61-4102-9b1b-88b51adb963e
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 9
---
# 管理陣列和清單的泛型委派
本主題概略說明轉換、搜尋述詞以及要在陣列或集合的項目上採取之動作的泛型委派。  
  
## 管理陣列和清單的泛型委派  
 <xref:System.Action%601> 泛型委派表示在指定類型項目上執行某些動作的方法。  您可以建立一個在項目上執行所需動作的方法、建立 <xref:System.Action%601> 委派的執行個體來表示該方法，然後將陣列和委派傳遞至 <xref:System.Array.ForEach%2A?displayProperty=fullName> 靜態泛型方法。  針對陣列的每個項目，都會呼叫該方法。  
  
 <xref:System.Collections.Generic.List%601> 泛型類別也有提供一個使用 <xref:System.Action%601> 委派的 <xref:System.Collections.Generic.List%601.ForEach%2A> 方法。  這不是泛型方法。  
  
> [!NOTE]
>  這對於泛型類型和方法形成有趣的一點。  <xref:System.Array.ForEach%2A?displayProperty=fullName> 方法必須為靜態 \(在 Visual Basic 中為 `Shared`\) 和泛型，因為 <xref:System.Array> 不是泛型類型；您可以為 <xref:System.Array.ForEach%2A?displayProperty=fullName> 指定操作類型的唯一理由，就是該方法有它自己的類型參數清單。  相對地，非泛型 <xref:System.Collections.Generic.List%601.ForEach%2A?displayProperty=fullName> 方法屬於泛型類別 <xref:System.Collections.Generic.List%601>，因此它會直接使用其類別的類型參數。  該類別為強類型，因此這個方法可以是執行個體方法。  
  
 <xref:System.Predicate%601> 泛型委派表示用來判斷特定項目是否符合您定義之準則的方法。  您可以將其與 <xref:System.Array> 的下列靜態泛型方法搭配使用，以搜尋單一項目或一組項目：<xref:System.Array.Exists%2A>、<xref:System.Array.Find%2A>、<xref:System.Array.FindAll%2A>、<xref:System.Array.FindIndex%2A>、<xref:System.Array.FindLast%2A>、<xref:System.Array.FindLastIndex%2A> 和 <xref:System.Array.TrueForAll%2A>。  
  
 <xref:System.Predicate%601> 也可以搭配使用 <xref:System.Collections.Generic.List%601> 泛型類別的對應非泛型執行個體方法。  
  
 <xref:System.Comparison%601> 泛型委派可讓您針對沒有原生排序順序的陣列或清單項目，提供排序順序，或是覆寫原生的排序順序。  建立一個執行比較的方法、建立 <xref:System.Comparison%601> 委派的執行個體來表示您的方法，然後將陣列和委派傳遞至 [Array.Sort\<T\>\(T\<xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29?displayProperty=fullName> 靜態泛型方法。  <xref:System.Collections.Generic.List%601> 泛型類別提供對應的執行個體方法多載 <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29?displayProperty=fullName>。  
  
 <xref:System.Converter%602> 泛型委派可讓您定義兩個類型之間的轉換，並可將一種類型的陣列轉換成另一種類型的陣列，或是將一種類型的清單轉換成另一種類型的清單。  建立一個方法，以將現有清單中的項目轉換成新的類型、建立委派執行個體來表示方法，並使用 <xref:System.Array.ConvertAll%2A?displayProperty=fullName> 泛型靜態方法，從原始的陣列產生新的類型陣列，或是使用 <xref:System.Collections.Generic.List%601.ConvertAll%2A?displayProperty=fullName> 泛型執行個體方法，從原始清單產生新類型的清單。  
  
### 變更委派  
 許多使用這些委派的方法都會傳回陣列或清單，該陣列或清單可以再傳遞至另一個方法。  例如，如果您想要選取陣列的特定項目、將這些項目轉換成新的類型，並將它們儲存在新的陣列中，您可以將 <xref:System.Array.FindAll%2A> 泛型方法傳回的陣列傳遞至 <xref:System.Array.ConvertAll%2A> 泛型方法。  如果新的項目類型沒有自然排序順序，您可以將 <xref:System.Array.ConvertAll%2A> 泛型方法傳回的陣列傳遞至 [Sort\<T\>\(T\<xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29> 泛型方法。  
  
## 請參閱  
 <xref:System.Collections.Generic?displayProperty=fullName>   
 <xref:System.Collections.ObjectModel?displayProperty=fullName>   
 [泛型](../../../docs/standard/generics/index.md)   
 [.NET Framework 中的泛型集合](../../../docs/standard/generics/collections.md)   
 [泛型介面](../../../docs/standard/generics/interfaces.md)   
 [共變數和反變數](../../../docs/standard/generics/covariance-and-contravariance.md)