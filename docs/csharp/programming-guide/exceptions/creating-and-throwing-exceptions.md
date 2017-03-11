---
title: "建立和擲回例外狀況 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "攔截例外狀況 [C#]"
  - "例外狀況 [C#], 建立"
  - "例外狀況 [C#], 擲回"
  - "擲回例外狀況 [C#]"
ms.assetid: 6bbba495-a115-4c6d-90cc-1f4d7b5f39e2
caps.latest.revision: 28
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 28
---
# 建立和擲回例外狀況 (C# 程式設計手冊)
例外狀況可用於指出程式執行時所發生的錯誤。  會建立描述錯誤的例外狀況物件，然後使用 [throw](../../../csharp/language-reference/keywords/throw.md) 關鍵字「*擲回*」\(Thrown\)。  然後執行階段會搜尋最適合的例外狀況處理常式。  
  
 程式設計人員應該設計在下列一個或多個條件為 True 時擲回例外狀況：  
  
-   方法無法完成本身定義的功能。  
  
     例如，方法的參數值無效：  
  
     [!code-cs[csProgGuideExceptions#12](../../../csharp/programming-guide/exceptions/codesnippet/csharp/creating-and-throwing-ex_1.cs)]  
  
-   在物件某種狀態下，對物件進行不當的呼叫。  
  
     例如可能會嘗試寫入唯讀檔案的範例。  在物件狀態不允許作業的狀況下，會擲回 <xref:System.InvalidOperationException> 的執行個體或依據此類別衍生的物件。  這是擲回 <xref:System.InvalidOperationException> 物件的方法範例：  
  
     [!code-cs[csProgGuideExceptions#13](../../../csharp/programming-guide/exceptions/codesnippet/csharp/creating-and-throwing-ex_2.cs)]  
  
-   當方法引數會造成例外狀況時。  
  
     在這種情況下，應攔截原始的例外狀況，並應建立 <xref:System.ArgumentException> 執行個體。  原始的例外狀況應該做為 <xref:System.Exception.InnerException%2A> 參數傳遞至 <xref:System.ArgumentException> 的建構函式 \(Constructor\)：  
  
     [!code-cs[csProgGuideExceptions#14](../../../csharp/programming-guide/exceptions/codesnippet/csharp/creating-and-throwing-ex_3.cs)]  
  
 例外狀況會包含名為 <xref:System.Exception.StackTrace%2A> 的屬性。  這個字串包含目前呼叫堆疊上方法的名稱，以及針對每個方法擲回例外狀況所在的檔案名稱及行號。  Common Language Runtime \(CLR\) 會在出現 `throw` 陳述式 \(Statement\) 的位置自動建立 <xref:System.Exception.StackTrace%2A> 物件，因此例外狀況必須從堆疊追蹤應有的起始點擲回。  
  
 所有的例外狀況都包含名為 <xref:System.Exception.Message%2A> 的屬性。  這個字串應該設定為說明例外狀況的原因。  請注意，訊息文字中不應該放入安全性的敏感資訊。  除了 <xref:System.Exception.Message%2A> 以外，<xref:System.ArgumentException> 也包含名為 <xref:System.ArgumentException.ParamName%2A> 的屬性，該屬性應設為引發例外狀況擲回的引數名稱。  若為屬性 setter，則 <xref:System.ArgumentException.ParamName%2A> 應設為 `value`。  
  
 每當公用和受保護方法成員無法完成預期的功能時，都應該擲回例外狀況。  擲回的例外狀況類別，應該是符合錯誤狀況的最特定可用例外狀況。  這些例外狀況應記載為類別功能的一部分，而且衍生類別 \(Derived Class\) 或更新後的類別也應該維持與原始類別相同的行為，以保有回溯相容性 \(Backward Compatibility\)。  
  
## 擲回例外狀況時應該要避免的做法  
 下列清單會指出擲回例外狀況時應該要避免的做法：  
  
-   例外狀況不應在一般執行時用來變更程式流程。  例外狀況只應該用來報告和處理錯誤狀況。  
  
-   例外狀況不應在擲回以外，做為傳回值或參數傳回。  
  
-   請勿從自己的原始程式碼蓄意擲回 <xref:System.Exception?displayProperty=fullName>、<xref:System.SystemException?displayProperty=fullName>、<xref:System.NullReferenceException?displayProperty=fullName> 或 <xref:System.IndexOutOfRangeException?displayProperty=fullName>。  
  
-   請勿建立可以在偵錯模式中擲回，但是不能在發行模式中擲回的例外狀況。  若要在開發階段期間辨識執行階段錯誤，請改用 Debug Assert。  
  
## 定義例外狀況類別  
 程式可以擲回 <xref:System> 命名空間 \(Namespace\) 中的預先定義例外狀況類別 \(除了之前所註明者\)，或是從 <xref:System.Exception> 衍生以建立其本身的例外狀況類別。  衍生類別應至少定義四個建構函式：一個是預設建構函式、一個設定訊息屬性，一個則同時設定 <xref:System.Exception.Message%2A> 和 <xref:System.Exception.InnerException%2A> 屬性。  第四個建構函式則是用來序列化例外狀況。  新的例外狀況類別應該是可序列化的。  例如：  
  
 [!code-cs[csProgGuideExceptions#15](../../../csharp/programming-guide/exceptions/codesnippet/csharp/creating-and-throwing-ex_4.cs)]  
  
 除非新屬性提供的資料有助於解析例外狀況，否則不應隨意將新屬性加入至例外狀況類別。  如果您將新屬性加入到衍生的例外狀況類別中，則應覆寫 `ToString()` 以傳回新增的資訊。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [例外狀況和例外狀況處理](../../../csharp/programming-guide/exceptions/exceptions-and-exception-handling.md)   
 [例外狀況階層架構](../Topic/Exception%20Hierarchy.md)   
 [例外狀況處理](../../../csharp/programming-guide/exceptions/exception-handling.md)