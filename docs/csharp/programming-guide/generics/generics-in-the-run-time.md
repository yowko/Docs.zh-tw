---
title: "執行階段中的泛型 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "泛型 [C#], 於執行階段"
ms.assetid: 119df7e6-9ceb-49df-af36-24f8f8c0747f
caps.latest.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 18
---
# 執行階段中的泛型 (C# 程式設計手冊)
當泛型型別或方法編譯至 Microsoft Intermediate Language \(MSIL\) 時，會包含中繼資料以將其識別為擁有型別參數。  泛型型別之 MSIL 的使用方式，會根據提供的型別參數是實值型別 \(Value Type\) 或參考型別 \(Reference Type\) 而有所不同。  
  
 當泛型型別先使用實值型別建構為參數時，執行階段就會使用所提供之參數，或是在 MSIL 內適當位置中取代的參數，來建立特殊的泛型型別。  每個用來當做參數的唯一實值型別，都會建立一次特殊的泛型型別。  
  
 舉例來說，假設程式的程式碼宣告以整數建構的堆疊：  
  
 [!code-cs[csProgGuideGenerics#42](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_1.cs)]  
  
 此時，執行階段會產生 <xref:System.Collections.Generic.Stack%601> 類別的特殊版本，並會使用適當的整數取代其參數。  現在，當程式的程式碼使用整數堆疊時，執行階段就會重複利用所產生之特定的 <xref:System.Collections.Generic.Stack%601> 類別。  在下列程式碼範例中會建立兩個整數堆疊的執行個體，並且共用 `Stack<int>` 程式碼的單一執行個體：  
  
 [!code-cs[csProgGuideGenerics#43](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_2.cs)]  
  
 然而，假設在程式碼中的其他地方，還有建立另一個具有不同的實值型別 \(例如 `long`\)，或是以使用者定義的結構當做其參數的  <xref:System.Collections.Generic.Stack%601> 類別。  在此情況下，執行階段便會產生另一個泛型型別的版本，並會替代 MSIL 中適當位置的 `long`。  因為每個特殊的泛型類別原本就包含實值型別，所以不再需要進行轉換。  
  
 參考型別的泛型運作方式有些不同。  當第一次使用任意參考型別建構泛型型別時，執行階段會使用在 MSIL 中取代參數之物件參考建立特殊的泛型型別。  然後，每次以參考型別當做參數產生建構的型別時 \(無論是何種型別\)，執行階段都會重複使用之前所建特殊版本的泛型型別。  因為所有的參考大小都相同，所以才能這樣做。  
  
 例如，假設有兩個參考型別 \(`Customer` 類別和 `Order` 類別\)，並假設您已建立 `Customer` 型別的堆疊：  
  
 [!code-cs[csProgGuideGenerics#47](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_3.cs)]  
  
 [!code-cs[csProgGuideGenerics#44](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_4.cs)]  
  
 此時，執行階段會產生 <xref:System.Collections.Generic.Stack%601> 類別的特殊版本，其中會存放稍後填滿的物件參考，而不是存放資料。  假設下一行程式碼會建立另一個參考型別的堆疊，稱為 `Order`：  
  
 [!code-cs[csProgGuideGenerics#45](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_5.cs)]  
  
 與使用實值型別不同的是，不會建立 `Order` 型別的另一個 <xref:System.Collections.Generic.Stack%601> 類別特定版本，  而是建立 <xref:System.Collections.Generic.Stack%601> 類別之特殊版本的執行個體，並將 `orders` 變數設定為參考這個執行個體。  假設之後又遇到建立 `Customer` 型別之堆疊的程式碼行：  
  
 [!code-cs[csProgGuideGenerics#46](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_6.cs)]  
  
 在搭配先前使用 <xref:System.Collections.Generic.Stack%601> 類別 \(使用 `Order` 型別所建立\) 之後，就會建立特殊 <xref:System.Collections.Generic.Stack%601> 類別的另一個執行個體。  包含於其中的指標會設定為參考 `Customer` 型別之大小的記憶體區域。  因為參考型別的數量會因程式而有很大不同，所以泛型的 C\# 實作 \(Implementation\) 會藉由縮小至編譯器為參考型別之泛型類別所建立的特殊類別數量，以大幅減少程式碼的數量。  
  
 此外，當使用型別參數 \(實值或參考型別\) 產生泛型 C\# 類別時，在執行階段即可使用反映 \(Reflection\) 查詢這個類別，並可同時確定其實際型別和型別參數。  
  
## 請參閱  
 <xref:System.Collections.Generic>   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [泛型簡介](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [泛型](../Topic/Generics%20in%20the%20.NET%20Framework.md)