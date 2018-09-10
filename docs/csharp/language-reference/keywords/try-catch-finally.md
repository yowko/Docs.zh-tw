---
title: try-catch-finally (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
ms.openlocfilehash: b60a1e17f02d7a04b782c661f2b99a28403997eb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510094"
---
# <a name="try-catch-finally-c-reference"></a>try-catch-finally (C# 參考)
常見的搭配使用 `catch` 與 `finally` 是要取得和使用 `try` 區塊中的資源、處理 `catch` 區塊中的例外情況，以及釋放 `finally` 區塊中的資源。  
  
 如需重新擲回例外狀況的詳細資訊和範例，請參閱 [try-catch](../../../csharp/language-reference/keywords/try-catch.md) 和[擲回例外狀況](../../../standard/exceptions/index.md)。 如需 `finally` 區塊的詳細資訊，請參閱 [try-finally](../../../csharp/language-reference/keywords/try-finally.md)。  
  
## <a name="example"></a>範例  
 [!code-csharp[csrefKeywordsExceptions#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch-finally_1.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱

- [C# 參考](../../../csharp/language-reference/index.md)  
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)  
- [try、throw 和 catch 陳述式 (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)  
- [例外狀況處理陳述式](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
- [throw](../../../csharp/language-reference/keywords/throw.md)  
- [操作說明：明確擲回例外狀況](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)  
- [using 陳述式](../../../csharp/language-reference/keywords/using-statement.md)
