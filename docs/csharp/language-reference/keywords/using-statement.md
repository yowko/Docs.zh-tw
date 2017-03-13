---
title: "using 陳述式 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "using 陳述式 [C#]"
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
caps.latest.revision: 31
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 31
---
# using 陳述式 (C# 參考)
提供方便的語法，可確保正確使用 <xref:System.IDisposable> 物件。  
  
## 範例  
 在下列範例中，會示範如何使用 using 陳述式。  
  
 [!code-cs[csrefKeywordsNamespace#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_1.cs)]  
  
## 備註  
 <xref:System.IO.File> 和 <xref:System.Drawing.Font> 為 Managed 型別的範例，這些型別會存取 Unmanaged 資源 \(在這個例子中，表示檔案控制代碼 \(File Handle\) 和裝置內容 \(Device Context，DC\)\)。  還有許多其他種類的 Unmanaged 資源，以及封裝這些資源的類別庫型別。  這些型別都必須實作 <xref:System.IDisposable> 介面。  
  
 因此，當您使用 `IDisposable` 物件時，就必須在 `using` 陳述式中宣告及執行個體化該物件。  `using` 陳述式會以正確的方法在物件上呼叫 <xref:System.IDisposable.Dispose%2A> 方法，而 \(當您以之前顯示的方法使用該陳述式時\) 一旦呼叫 <xref:System.IDisposable.Dispose%2A>，也會導致物件本身超出範圍。  在 `using` 區塊內，物件為唯讀而且不可修改或重新指派。  
  
 當您在物件上呼叫方法時，`using` 陳述式可確定即使發生例外狀況時，也都會呼叫 <xref:System.IDisposable.Dispose%2A>。  您可以將物件放在 try 區塊內，並在 finally 區塊中呼叫 <xref:System.IDisposable.Dispose%2A>，即可達到相同的結果。事實上，這就是編譯器轉譯 `using` 陳述式的方法。  先前的程式碼範例會在編譯時期擴展為下列程式碼 \(請注意，會使用額外的大括號來建立物件的限制範圍\)：  
  
 [!code-cs[csrefKeywordsNamespace#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_2.cs)]  
  
 一種類型的多個執行個體可以在`using`陳述式中宣告，如下列範例所示。  
  
 [!code-cs[csrefKeywordsNamespace#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_3.cs)]  
  
 您可以執行個體化資源物件，然後將變數傳遞至 `using` 陳述式，但這不是最佳作法。  在此情況下，控制項離開 `using` 區塊之後，即使物件無法再存取其 Unmanaged 資源，仍會在範圍中。  換句話說，將無法再完整初始化該物件。  如果您嘗試在 `using` 區塊外部使用該物件，會有擲回例外狀況的風險。  因此，比較好的作法是在 `using` 陳述式中執行個體化物件，並將其範圍限制為 `using` 區塊。  
  
 [!code-cs[csrefKeywordsNamespace#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_4.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [using 指示詞](../../../csharp/language-reference/keywords/using-directive.md)   
 [Garbage Collection](../Topic/Garbage%20Collection.md)   
 [Implementing a Dispose Method](../Topic/Implementing%20a%20Dispose%20Method.md)