---
redirect_url: /dotnet/articles/csharp/programming-guide/exceptions/
caps.handback.revision: 33
---
# 例外狀況和例外處理 (C# 程式設計手冊)
C\# 語言的例外狀況 \(Exception\) 處理功能可協助您處理任何在程式執行時所發生的未預期或例外情況。  例外狀況處理 \(Exception Handling\) 會使用 `try`、`catch` 和 `finally` 關鍵字，嘗試執行可能不會成功的動作、適時處理失敗，以及在事後清除資源。  Common Language Runtime \(CLR\)、.NET Framework 或任何協力廠商程式庫，或是應用程式程式碼都可能會產生例外狀況。  例外狀況是透過 `throw` 關鍵字建立的。  
  
 許多情況下，例外狀況可能不是由程式碼直接呼叫的方法擲回，而是由呼叫堆疊中後續的另一個方法擲回。  這種情況發生時，CLR 將回溯堆疊以尋找含有特定例外狀況類型之 `catch` 區塊方法，然後將執行這類 `catch` 區塊的第一個 \(如果找到的話\)。  如果在呼叫堆疊中找不到適當的 `catch` 區塊，CLR 就會結束處理序並向使用者顯示訊息。  
  
 在這個範例中，方法會測試除數為零的情形，並攔截錯誤。  如果沒有經過例外狀況處理，這個程式可能會因 \[為**DivideByZeroException 未處理**\] 的錯誤而終止。  
  
 [!code-cs[csProgGuideExceptions#18](../../../csharp/programming-guide/exceptions/codesnippet/csharp/exceptions-and-exception_1.cs)]  
  
## 例外狀況概觀  
 例外狀況有下列特性：  
  
-   例外狀況是最終全都衍生自 `System.Exception` 的型別。  
  
-   在可能擲回例外狀況的陳述式周圍使用 `try` 區塊。  
  
-   一旦 `try` 區塊內發生例外狀況，控制流程會跳至呼叫堆疊中第一個關聯的例外處理常式 \(Exception Handler\)。  C\# 使用 `catch` 關鍵字定義例外狀況處理常式。  
  
-   如果指定的例外狀況並沒有例外處理常式，程式就會停止執行並出現錯誤訊息。  
  
-   除非您可以處理例外狀況，讓應用程式處於已知狀態，否則不要攔截例外狀況。  如果您攔截 `System.Exception`，請在 `catch` 區塊結尾使用 `throw` 關鍵字重新擲回例外狀況。  
  
-   如果 `catch` 區塊中有定義例外狀況變數，您便可以使用該變數來取得發生之例外狀況類型的詳細資訊。  
  
-   程式可以藉由使用 `throw` 關鍵字，明確地產生例外狀況。  
  
-   例外狀況物件會包含錯誤的詳細資訊，例如呼叫堆疊的狀態和錯誤的文字描述。  
  
-   即使擲回例外狀況，`finally` 區塊中的程式碼仍然會執行。  您可以使用 `finally` 區塊來釋放資源，例如，關閉任何在 `try` 區塊中開啟的資料流或檔案。  
  
-   .NET Framework 中的 Managed 例外狀況 \(Exception\) 會在 Win32 結構化例外處理 \(Structured Exception Handling\) 機制的最上層實作。  如需詳細資訊，請參閱[結構化例外狀況處理](/visual-cpp/cpp/structured-exception-handling-c-cpp) 和 [Win32 結構化例外狀況處理奧秘速成](http://go.microsoft.com/fwlink/?LinkId=119654) \(英文\)。  
  
## 相關章節  
 如需例外狀況和例外處理的詳細資訊，請參閱下列主題：  
  
-   [使用例外狀況](../../../csharp/programming-guide/exceptions/using-exceptions.md)  
  
-   [例外狀況處理](../../../csharp/programming-guide/exceptions/exception-handling.md)  
  
-   [建立和擲回例外狀況](../../../csharp/programming-guide/exceptions/creating-and-throwing-exceptions.md)  
  
-   [編譯器所產生的例外狀況](../../../csharp/programming-guide/exceptions/compiler-generated-exceptions.md)  
  
-   [如何：使用 try\/catch 處理例外狀況](../../../csharp/programming-guide/exceptions/how-to-handle-an-exception-using-try-catch.md)  
  
-   [如何：使用 finally 執行清除程式碼](../../../csharp/programming-guide/exceptions/how-to-execute-cleanup-code-using-finally.md)  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 <xref:System.SystemException>   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [throw](../../../csharp/language-reference/keywords/throw.md)   
 [try\-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [try\-finally](../../../csharp/language-reference/keywords/try-finally.md)   
 [try\-catch\-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)   
 [例外狀況](../Topic/Handling%20and%20Throwing%20Exceptions.md)   
 [例外狀況階層架構](../Topic/Exception%20Hierarchy.md)   
 [撰寫可靠的 .NET 程式碼](http://go.microsoft.com/fwlink/?LinkId=112400)   
 [特定例外狀況的小型傾印](http://go.microsoft.com/fwlink/?LinkId=112408)