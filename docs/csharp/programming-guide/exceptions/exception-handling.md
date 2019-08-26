---
title: 例外狀況處理 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], handling
ms.assetid: b4e4ecf2-b907-4e58-891f-2563762258e9
ms.openlocfilehash: 5013738e74aaa260ab6f5bcd4d73904cfbdcc3c8
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590273"
---
# <a name="exception-handling-c-programming-guide"></a>例外狀況處理 (C# 程式設計手冊)
C# 程式設計人員使用 [try](../../language-reference/keywords/try-catch.md) 區塊分割可能受到例外狀況影響的程式碼。 相關聯的 [catch](../../language-reference/keywords/try-catch.md) 區塊用來處理任何產生的例外狀況。 無論 `try` 區塊是否擲回例外狀況，[finally](../../language-reference/keywords/try-finally.md) 區塊都包含執行的程式碼，例如釋放配置在 `try` 區塊中的資源。 `try` 區塊需要一或多個相關聯的 `catch` 區塊，或 `finally` 區塊，或兩種都要。  
  
 下例示範 `try-catch` 陳述式、`try-finally` 陳述式和 `try-catch-finally` 陳述式。  
  
 [!code-csharp[csProgGuideExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#6)]  
  
 [!code-csharp[csProgGuideExceptions#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#7)]  
  
 [!code-csharp[csProgGuideExceptions#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#8)]  
  
 `try` 區塊沒有 `catch` 或 `finally` 區塊會造成編譯器錯誤。  
  
## <a name="catch-blocks"></a>catch 區塊  
 `catch` 區塊可以指定要攔截的例外狀況類型。 類型規格稱之為「例外狀況篩選條件」  。 例外狀況類型應衍生自 <xref:System.Exception>。 一般情況下，不指定 <xref:System.Exception> 為例外狀況篩選條件，除非您知道如何處理 `try` 區塊中可能擲回的所有例外狀況，或您在 `catch` 區塊的結尾已包含 [throw](../../language-reference/keywords/throw.md) 陳述式。  
  
 多個 `catch` 區塊有不同的例外狀況篩選條件可以鏈結在一起。 `catch` 區塊在您的程式碼中是由上往下評估，但每個被擲回的例外狀況只會執行一個 `catch` 區塊。 執行指定確切類型或擲回例外狀況基底類別的第一個 `catch` 區塊。 如果沒有任何 `catch` 區塊指定符合的例外狀況篩選條件，即選取沒有篩選的 `catch` 區塊，如果陳述式中有的話。 請務必先定位 `catch` 區塊和最特定的 (亦即衍生程度最高的) 例外狀況。  
  
 當下列條件成立時，您應該攔截例外狀況︰  
  
- 您已經了解例外狀況會擲回的可能原因，而且可以實作特定的復原，例如在您攔截 <xref:System.IO.FileNotFoundException> 物件時，提示使用者輸入新的檔案名稱。  
  
- 您可以建立並擲回更特定的新例外狀況。  
  
     [!code-csharp[csProgGuideExceptions#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#9)]  
  
- 您想要先稍微處理例外狀況，再傳遞它進行額外處理。 在下例中，`catch` 區塊是用來在重新擲回例外狀況之前，將項目新增至錯誤記錄檔。  
  
     [!code-csharp[csProgGuideExceptions#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#10)]  
  
## <a name="finally-blocks"></a>Finally 區塊  
 `finally` 區塊可讓您清除 `try` 區塊中執行過的動作。 如果有的話，`finally` 區塊會最後執行，在 `try` 區塊和任何符合的 `catch` 區塊之後。 不論是擲回例外狀況還是找到與例外狀況型別相符的 `catch` 區塊，`finally` 區塊會一律執行。  
  
 `finally` 區塊可以用來釋放資源，例如檔案資料流、資料庫連接及圖形控點，不必等待執行階段的記憶體回收行程完成物件。 如需詳細資訊，請參閱 [sing 陳述式](../../language-reference/keywords/using-statement.md)。  
  
 在下例中，`finally` 區塊用來關閉在 `try` 區塊中開啟的檔案。 請注意，檔案關閉前已檢查過檔案控制代碼的狀態。 如果 `try` 區塊無法開啟檔案，檔案控制代碼仍有值 `null`，而 `finally` 區塊不會嘗試關閉它。 或者，如果已成功在 `try` 區塊中開啟檔案，則 `finally` 區塊會關閉開啟的檔案。  
  
 [!code-csharp[csProgGuideExceptions#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#11)]  
  
## <a name="c-language-specification"></a>C# 語言規格  

如需詳細資訊，請參閱 [C# 語言規格](../../language-reference/language-specification/index.md)的[例外狀況](~/_csharplang/spec/exceptions.md)與 [try 陳述式](~/_csharplang/spec/statements.md#the-try-statement)。 語言規格是 C# 語法及用法的限定來源。
  
## <a name="see-also"></a>另請參閱

- [C# 參考](../../language-reference/index.md)
- [C# 程式設計指南](../index.md)
- [例外狀況和例外狀況處理](./index.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
- [using 陳述式](../../language-reference/keywords/using-statement.md)
