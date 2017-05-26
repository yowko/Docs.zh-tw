---
title: "try-finally (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- finally
- finally_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
caps.latest.revision: 25
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3f7618aa6d4ae3535b2b6cb562349650b3eba1ed
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="try-finally-c-reference"></a>try-finally (C# 參考)
使用 `finally` 區塊，即可清除 [try](../../../csharp/language-reference/keywords/try-catch.md) 區塊中所配置的任何資源，以及執行程式碼，即使 `try` 區塊中發生例外狀況也是一樣。 一般而言，會在控制權離開 `try` 陳述式時，執行 `finally` 區塊的陳述式。 控制權轉移可能是正常執行、執行 `break`、`continue`、`goto` 或 `return` 陳述式，或是傳播 `try` 陳述式的例外狀況所造成。  
  
 在處理的例外狀況內，一定會執行關聯的 `finally` 區塊。 不過，如果無法處理例外狀況，則執行 `finally` 區塊取決於如何觸發例外狀況回溯作業。 接著，取決於您電腦的設定方式。 如需詳細資訊，請參閱 [CLR 中未處理之例外狀況的處理機制](http://go.microsoft.com/fwlink/?LinkId=128371)。  
  
 通常，未處理的例外狀況結束應用程式時，是否執行 `finally` 區塊並不重要。 不過，如果您的 `finally` 區塊中有即使在這種情況下都必須執行的陳述式，則其中一個解決方案是將 `catch` 區塊新增至 `try`-`finally` 陳述式。 或者，您可以攔截可能會在呼叫堆疊較高之 `try`-`finally` 陳述式的 `try` 區塊中擲回的例外狀況。 亦即，您可以攔截下列方法中的例外狀況：呼叫包含 `try`-`finally` 陳述式的方法、呼叫該方法的方法，或呼叫堆疊的任何方法。 如果未攔截到例外狀況，則執行 `finally` 區塊取決於作業系統是否選擇觸發例外狀況回溯作業。  
  
## <a name="example"></a>範例  
 在下列範例中，無效的轉換陳述式會導致 `System.InvalidCastException` 例外狀況。 例外狀況未進行處理。  
  
 [!code-cs[csrefKeywordsExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_1.cs)]  
  
 在下列範例中，會攔截到來自呼叫堆疊最遠的方法中之 `TryCast` 方法的例外狀況。  
  
 [!code-cs[csrefKeywordsExceptions#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_2.cs)]  
  
 如需 `finally` 的詳細資訊，請參閱 [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)。  
  
 C# 也會包含 [using 陳述式](../../../csharp/language-reference/keywords/using-statement.md)，以透過方便使用的語法提供 <xref:System.IDisposable> 物件的類似功能。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [try、throw 和 catch 陳述式 (C++)](https://docs.microsoft.com/cpp/cpp/try-throw-and-catch-statements-cpp)   
 [例外狀況處理陳述式](../../../csharp/language-reference/keywords/exception-handling-statements.md)   
 [throw](../../../csharp/language-reference/keywords/throw.md)   
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [如何：明確擲回例外狀況](https://msdn.microsoft.com/library/xhcbs8fz)
