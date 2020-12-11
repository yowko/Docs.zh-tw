---
title: 例外狀況與例外狀況處理 - C# 程式設計手冊
description: '瞭解例外狀況和例外狀況處理。 這些 c # 功能有助於處理常式執行時所發生的非預期或例外狀況。'
ms.date: 12/09/2020
helpviewer_keywords:
- exception handling [C#]
- exceptions [C#]
- C# language, exceptions
ms.assetid: 0001887f-4fa2-47e2-8034-2819477e2344
ms.openlocfilehash: 679171e6d397741ef44cb37fb770f6feba039fd9
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110620"
---
# <a name="exceptions-and-exception-handling-c-programming-guide"></a>例外狀況和例外處理 (C# 程式設計手冊)

C# 語言的例外狀況處理功能可協助您處理在程式執行時發生的任何未預期或例外狀況。 例外狀況處理 `try` 會使用、 `catch` 和 `finally` 關鍵字來嘗試可能不會成功的動作，以便在您決定是否合理進行時處理失敗，並在之後清除資源。 例外狀況可由 common language runtime (CLR) 、.NET 或協力廠商程式庫，或應用程式程式碼產生。 例外狀況是使用 `throw` 關鍵字所建立。

在許多情況下，例外狀況可能不是由您的程式碼直接呼叫的方法所擲回，而是由呼叫堆疊中更下方的另一個方法所擲回。 當擲回例外狀況時，CLR 會回溯堆疊，尋找具有 `catch` 特定例外狀況類型之區塊的方法，並執行第一個這類 `catch` 區塊（如果找到的話）。 如果在呼叫堆疊中的任何地方都找不到適當的 `catch` 區塊，它將會終止處理序，並向使用者顯示一則訊息。

在此範例中，方法會測試除數為零，並攔截錯誤。 如果沒有例外狀況處理，此程式就會終止並產生 **DivideByZeroException 未處理** 的錯誤。

:::code language="csharp" source="snippets/exceptions/ExceptionTest.cs" ID="ExceptionTest":::

## <a name="exceptions-overview"></a>例外狀況概觀

例外狀況具有下列屬性：

- 例外狀況是最終全都衍生自 `System.Exception` 的型別。
- 在可能擲回例外狀況的陳述式前後使用 `try` 區塊。
- 一旦 `try` 區塊中發生例外狀況之後，控制流程就會跳至第一個相關聯的例外狀況處理常式，此處理常式存在於呼叫堆疊中的任何位置。 在 C# 中，`catch` 關鍵字是用來定義例外狀況處理常式。
- 如果沒有指定例外狀況的例外狀況處理常式存在，程式就會停止執行並出現錯誤訊息。
- 除非您可以處理例外狀況，並讓應用程式處於已知狀態，否則請勿攔截例外狀況。 如果您攔截 `System.Exception`，請在 `catch` 區塊結尾使用 `throw` 關鍵字重新擲回它。
- 如果 `catch` 區塊定義了例外狀況變數，您可以使用它來取得所發生例外狀況型別的詳細資訊。
- 例外狀況可以透過程式使用 `throw` 關鍵字明確地產生。
- 例外狀況物件包含錯誤的詳細資訊，例如呼叫堆疊的狀態和錯誤狀態的文字描述。
- 即使擲回例外狀況，`finally` 區塊中的程式碼也會執行。 使用 `finally` 區塊來釋放資源，例如，關閉已在 `try` 區塊中開啟的任何資料流或檔案。
- .NET 中的 Managed 例外狀況會在 Win32 結構化例外狀況處理機制之上執行。 如需詳細資訊，請參閱[結構化例外狀況處理 (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp) 和[深入探究 Win32 結構化例外狀況處理的毀損課程 (英文)](http://bytepointer.com/resources/pietrek_crash_course_depths_of_win32_seh.htm)。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](/dotnet/csharp/language-reference/language-specification/introduction)中的[例外狀況](~/_csharplang/spec/exceptions.md)。 語言規格是 C# 語法及用法的限定來源。

## <a name="see-also"></a>另請參閱

- <xref:System.SystemException>
- [C # 關鍵字](../../language-reference/keywords/index.md)
- [扔](../../language-reference/keywords/throw.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
- [例外狀況](../../../standard/exceptions/index.md)
