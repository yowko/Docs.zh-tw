---
title: 例外狀況處理 - C# 程式設計手冊
description: 瞭解例外狀況處理。 請參閱 try-catch、try-finally 和 try-catch 語句的範例。
ms.date: 12/09/2020
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], handling
ms.assetid: b4e4ecf2-b907-4e58-891f-2563762258e9
ms.openlocfilehash: fabf1413ba498232e67f45460195fe96e25fab0a
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110191"
---
# <a name="exception-handling-c-programming-guide"></a>例外狀況處理 (C# 程式設計手冊)

C# 程式設計人員使用 [try](../../language-reference/keywords/try-catch.md) 區塊分割可能受到例外狀況影響的程式碼。 相關聯的 [catch](../../language-reference/keywords/try-catch.md) 區塊用來處理任何產生的例外狀況。 [Finally](../../language-reference/keywords/try-finally.md)區塊包含的程式碼會在區塊中擲回例外狀況時執行 `try` ，例如釋放在區塊中配置的資源 `try` 。 `try` 區塊需要一或多個相關聯的 `catch` 區塊，或 `finally` 區塊，或兩種都要。

下例示範 `try-catch` 陳述式、`try-finally` 陳述式和 `try-catch-finally` 陳述式。

:::code language="csharp" source="snippets/exceptions/Program.cs" id="TryCatchStructure":::

:::code language="csharp" source="snippets/exceptions/Program.cs" id="TryFinallyStructure":::

:::code language="csharp" source="snippets/exceptions/Program.cs" id="TryCatchFinallyStructure":::

`try` 區塊沒有 `catch` 或 `finally` 區塊會造成編譯器錯誤。

## <a name="catch-blocks"></a>catch 區塊

`catch` 區塊可以指定要攔截的例外狀況類型。 類型規格稱之為「例外狀況篩選條件」。 例外狀況類型應衍生自 <xref:System.Exception>。 一般而言， <xref:System.Exception> 除非您知道如何處理區塊中可能擲回的所有例外狀況 `try` ，或在區塊結尾包含 [throw](../../language-reference/keywords/throw.md) 語句，否則請勿指定為例外狀況篩選準則 `catch` 。

`catch`具有不同例外狀況類別的多個區塊可以連結在一起。 `catch` 區塊在您的程式碼中是由上往下評估，但每個被擲回的例外狀況只會執行一個 `catch` 區塊。 執行指定確切類型或擲回例外狀況基底類別的第一個 `catch` 區塊。 如果沒有 `catch` 區塊指定相符的例外狀況類別， `catch` 則會選取沒有任何類型的區塊（如果語句中有一個）。 請務必以 `catch` 最特定的 (定位區塊，也就是最優先的) 例外狀況類別。

當下列條件成立時，請攔截例外狀況：

- 您已經了解例外狀況會擲回的可能原因，而且可以實作特定的復原，例如在您攔截 <xref:System.IO.FileNotFoundException> 物件時，提示使用者輸入新的檔案名稱。
- 您可以建立並擲回更特定的新例外狀況。
  :::code language="csharp" source="snippets/exceptions/Program.cs" id="ThrowMoreSpecificException":::
- 您想要先稍微處理例外狀況，再傳遞它進行額外處理。 在下列範例中， `catch` 區塊是用來在重新擲回例外狀況之前將專案加入至錯誤記錄檔。
  :::code language="csharp" source="snippets/exceptions/Program.cs" id="RethrowError":::

您也可以指定 *例外狀況篩選準則* ，以將布林運算式加入至 catch 子句。 這些表示特定的 catch 子句只有在條件為 true 時才會符合。 在下列範例中，兩個 catch 子句都會使用相同的例外狀況類別，但會檢查額外的條件來建立不同的錯誤訊息：

:::code language="csharp" source="snippets/exceptions/ExceptionFilter.cs" ID="DemonstrateExceptionFilter":::

一律傳回的例外狀況篩選準則 `false` 可以用來檢查所有例外狀況，但不能處理它們。 一般用途是記錄例外狀況：

:::code language="csharp" source="snippets/exceptions/ExceptionFilter.cs" ID="ShowExceptionFilter":::

`LogException`方法一律會傳回 `false` ，不會有 `catch` 使用這個例外狀況篩選準則的子句相符。 Catch 子句可以是一般，使用 <xref:System.Exception?displayProperty=nameWithType> 和更新的子句可以處理更明確的例外狀況類別。

## <a name="finally-blocks"></a>Finally 區塊

`finally` 區塊可讓您清除 `try` 區塊中執行過的動作。 如果有的話，`finally` 區塊會最後執行，在 `try` 區塊和任何符合的 `catch` 區塊之後。 `finally`區塊一律會執行、是否擲回例外狀況，或 `catch` 找到符合例外狀況類型的區塊。

`finally` 區塊可以用來釋放資源，例如檔案資料流、資料庫連接及圖形控點，不必等待執行階段的記憶體回收行程完成物件。 如需詳細資訊，請參閱 [Using 語句](../../language-reference/keywords/using-statement.md)。

在下例中，`finally` 區塊用來關閉在 `try` 區塊中開啟的檔案。 請注意，檔案關閉前已檢查過檔案控制代碼的狀態。 如果 `try` 區塊無法開啟檔案，檔案控制代碼仍具有值 `null` ，而且 `finally` 區塊不會嘗試關閉它。 相反地，如果檔案已成功在區塊中開啟 `try` ，則 `finally` 區塊會關閉開啟的檔案。

:::code language="csharp" source="snippets/exceptions/Program.cs" id="CleanupIfNotNull":::

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](/dotnet/csharp/language-reference/language-specification/introduction)的[例外狀況](~/_csharplang/spec/exceptions.md)與 [try 陳述式](~/_csharplang/spec/statements.md#the-try-statement)。 語言規格是 C# 語法及用法的限定來源。
  
## <a name="see-also"></a>另請參閱

- [C # 參考](../../language-reference/index.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
- [using 陳述式](../../language-reference/keywords/using-statement.md)
