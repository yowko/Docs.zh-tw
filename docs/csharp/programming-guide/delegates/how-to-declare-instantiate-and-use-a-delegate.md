---
title: "如何：宣告、產生和使用委派 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "委派 [C#], 宣告和執行個體化"
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
caps.latest.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 21
---
# 如何：宣告、產生和使用委派 (C# 程式設計手冊)
在 C\# 1.0 \(含\) 以後版本中，委派可以依照下列範例所示宣告。  
  
 [!code-cs[csProgGuideDelegates#13](../../../csharp/programming-guide/delegates/codesnippet/csharp/csrefDelegates/Delegates.cs#13)]  
  
 [!code-cs[csProgGuideDelegates#14](../../../csharp/programming-guide/delegates/codesnippet/csharp/csrefDelegates/Delegates.cs#14)]  
  
 C\# 2.0 提供較簡單的方式來撰寫前述宣告，如下列範例所示。  
  
 [!code-cs[csProgGuideDelegates#32](../../../csharp/programming-guide/delegates/codesnippet/csharp/csrefDelegates/Delegates.cs#32)]  
  
 在 C\# 2.0 \(含\) 以後版本中，[委派](../../../csharp/language-reference/keywords/delegate.md)也可以使用匿名方法來宣告及初始化，如下列範例所示：  
  
 [!code-cs[csProgGuideDelegates#15](../../../csharp/programming-guide/delegates/codesnippet/csharp/csrefDelegates/Delegates.cs#15)]  
  
 在 C\# 3.0 \(含\) 以後版本中，委派也可以使用 Lambda 運算式宣告及初始化，如下列範例所示。  
  
 [!code-cs[csProgGuideDelegates#31](../../../csharp/programming-guide/delegates/codesnippet/csharp/csrefDelegates/Delegates.cs#31)]  
  
 如需詳細資訊，請參閱 [Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)。  
  
 下列範例說明宣告、產生和使用委派。  `BookDB` 類別封裝一個維持書籍資料庫的書局資料庫。  它會公開 `ProcessPaperbackBooks` 方法，用以搜尋資料庫中的所有平裝書，並針對每本書呼叫一個委派。  使用的 `delegate` 型別具有 `ProcessBookDelegate` 的名稱。  `Test` 類別會使用這個類別來列印平裝書的標題和平均價格。  
  
 委派的使用使得書局資料庫和用戶端程式碼之間的功能作了良好的分隔。  用戶端程式碼並不知道書籍是如何被儲存或書局程式碼是如何搜尋平裝書。  書局程式碼並不知道在找到平裝書之後，平裝書上會執行哪些作業。  
  
## 範例  
 [!code-cs[csProgGuideDelegates#12](../../../csharp/programming-guide/delegates/codesnippet/csharp/csrefDelegates/Delegates.cs#12)]  
  
## 穩固程式設計  
  
-   宣告委派。  
  
     下列陳述式會宣告新的委派型別。  
  
     [!code-cs[csProgGuideDelegates#16](../../../csharp/programming-guide/delegates/codesnippet/csharp/csrefDelegates/Delegates.cs#16)]  
  
     每一個委派型別說明了引數的數目和引數的型別，和它可以封裝之方法的傳回值型別。  當需要一組新的引數型別或傳回值型別時，必須宣告一個新的傳回型別。  
  
-   執行個體化委派。  
  
     在已宣告委派型別後，就必須建立委派物件，並使其與特定的方法產生關聯。  在上一個範例中，您將 `PrintTitle` 方法傳遞到 `ProcessPaperbackBooks` 方法以做到這點，如下列範例所示：  
  
     [!code-cs[csProgGuideDelegates#17](../../../csharp/programming-guide/delegates/codesnippet/csharp/csrefDelegates/Delegates.cs#17)]  
  
     這會建立與[靜態](../../../csharp/language-reference/keywords/static.md)方法 `Test.PrintTitle` 相關聯的新委派物件。  同樣地，也會傳遞在 `totaller` 物件上的非靜態 `AddBookToTotal` 方法，如下列範例所示：  
  
     [!code-cs[csProgGuideDelegates#18](../../../csharp/programming-guide/delegates/codesnippet/csharp/csrefDelegates/Delegates.cs#18)]  
  
     在這兩種情況下，新的委派物件會傳遞至 `ProcessPaperbackBooks` 方法。  
  
     在建立委派之後，與其關聯的方法永遠不會變更。委派物件是不可變的。  
  
-   呼叫委派。  
  
     在建立委派物件之後，該委派物件通常是傳遞到將會呼叫委派的其他程式碼。  委派物件是使用委派物件的名稱，跟隨著傳遞給委派的括號引數來呼叫。  下列是委派呼叫的範例：  
  
     [!code-cs[csProgGuideDelegates#19](../../../csharp/programming-guide/delegates/codesnippet/csharp/csrefDelegates/Delegates.cs#19)]  
  
     如同這個範例，您可以同步呼叫委派，或是使用 `BeginInvoke` 和 `EndInvoke` 方法進行非同步呼叫。  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [事件](../../../csharp/programming-guide/events/index.md)   
 [委派](../../../csharp/programming-guide/delegates/index.md)