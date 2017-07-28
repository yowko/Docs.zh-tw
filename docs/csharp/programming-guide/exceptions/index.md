---
title: "例外狀況和例外處理 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- exception handling [C#]
- exceptions [C#]
- C# language, exceptions
ms.assetid: 0001887f-4fa2-47e2-8034-2819477e2344
caps.latest.revision: 33
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e372cfa3239c39af86a29cda06b5817f0aeff0a2
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="exceptions-and-exception-handling-c-programming-guide"></a>例外狀況和例外處理 (C# 程式設計手冊)
C# 語言的例外狀況處理功能可協助您處理在程式執行時發生的任何未預期或例外狀況。 例外狀況處理會使用 `try`、`catch` 和 `finally` 關鍵字來嘗試可能失敗的動作，以便在您決定這樣做很合理時處理失敗，之後再清除資源。 例外狀況可以由 Common Language Runtime (CLR)、.NET Framework 或任何協力廠商程式庫，或者應用程式程式碼來產生。 例外狀況是使用 `throw` 關鍵字所建立。  
  
 在許多情況下，例外狀況可能不是由您的程式碼直接呼叫的方法所擲回，而是由呼叫堆疊中更下方的另一個方法所擲回。 發生這種情況時，CLR 將回溯堆疊，針對特定的例外狀況型別尋找具有 `catch` 區塊的方法，而它將會執行第一個這類 `catch` 區塊 (如果找到)。 如果在呼叫堆疊中的任何地方都找不到適當的 `catch` 區塊，它將會終止處理序，並向使用者顯示一則訊息。  
  
 在此範例中，方法會測試除數為零，並攔截錯誤。 如果沒有例外狀況處理，此程式就會終止並產生 **DivideByZeroException 未處理**的錯誤。  
  
 [!code-cs[csProgGuideExceptions#18](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exceptions-and-exception-handling_1.cs)]  
  
## <a name="exceptions-overview"></a>例外狀況概觀  
 例外狀況具有下列屬性：  
  
-   例外狀況是最終全都衍生自 `System.Exception` 的型別。  
  
-   在可能擲回例外狀況的陳述式前後使用 `try` 區塊。  
  
-   一旦 `try` 區塊中發生例外狀況之後，控制流程就會跳至第一個相關聯的例外狀況處理常式，此處理常式存在於呼叫堆疊中的任何位置。 在 C# 中，`catch` 關鍵字是用來定義例外狀況處理常式。  
  
-   如果沒有指定例外狀況的例外狀況處理常式存在，程式就會停止執行並出現錯誤訊息。  
  
-   除非您可以處理它，否則不要攔截例外狀況，並讓應用程式保持已知的狀態。 如果您攔截 `System.Exception`，請在 `catch` 區塊結尾使用 `throw` 關鍵字重新擲回它。  
  
-   如果 `catch` 區塊定義了例外狀況變數，您可以使用它來取得所發生例外狀況型別的詳細資訊。  
  
-   例外狀況可以透過程式使用 `throw` 關鍵字明確地產生。  
  
-   例外狀況物件包含錯誤的詳細資訊，例如呼叫堆疊的狀態和錯誤狀態的文字描述。  
  
-   即使擲回例外狀況，`finally` 區塊中的程式碼也會執行。 使用 `finally` 區塊來釋放資源，例如，關閉已在 `try` 區塊中開啟的任何資料流或檔案。  
  
-   .NET Framework 中的 Managed 例外狀況是在 Win32 結構化例外狀況處理機制上實作的。 如需詳細資訊，請參閱[結構化例外狀況處理 (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp) 和[深入探究 Win32 結構化例外狀況處理的毀損課程 (英文)](http://go.microsoft.com/fwlink/?LinkId=119654)。  
  
## <a name="related-sections"></a>相關章節  
 請參閱下列主題，以了解例外狀況和例外狀況處理的詳細資訊：  
  
-   [使用例外狀況](../../../csharp/programming-guide/exceptions/using-exceptions.md)  
  
-   [例外狀況處理](../../../csharp/programming-guide/exceptions/exception-handling.md)  
  
-   [建立和擲回例外狀況](../../../csharp/programming-guide/exceptions/creating-and-throwing-exceptions.md)  
  
-   [編譯器所產生的例外狀況](../../../csharp/programming-guide/exceptions/compiler-generated-exceptions.md)  
  
-   [如何：使用 try/catch 處理例外狀況 (C# 程式設計指南)](../../../csharp/programming-guide/exceptions/how-to-handle-an-exception-using-try-catch.md)  
  
-   [如何：使用 finally 執行清除程式碼](../../../csharp/programming-guide/exceptions/how-to-execute-cleanup-code-using-finally.md)  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.SystemException>   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [throw](../../../csharp/language-reference/keywords/throw.md)   
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [try-finally](../../../csharp/language-reference/keywords/try-finally.md)   
 [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)   
 [例外狀況](../../../standard/exceptions/index.md)   
 [例外狀況階層架構](http://msdn.microsoft.com/library/f7d68675-be06-40fb-a555-05f0c5a6f66b)   
 [撰寫可靠的 .NET 程式碼](http://go.microsoft.com/fwlink/?LinkId=112400)   
 [特定例外狀況的小型傾印](http://go.microsoft.com/fwlink/?LinkId=112408)

