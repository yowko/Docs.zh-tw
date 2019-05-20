---
title: try-catch-finally - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
ms.openlocfilehash: 66f24994c7fcd2037887507bae65f590e4f90019
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633883"
---
# <a name="try-catch-finally-c-reference"></a>try-catch-finally (C# 參考)

常見的搭配使用 `catch` 與 `finally` 是要取得和使用 `try` 區塊中的資源、處理 `catch` 區塊中的例外情況，以及釋放 `finally` 區塊中的資源。

 如需重新擲回例外狀況的詳細資訊和範例，請參閱 [try-catch](try-catch.md) 和[擲回例外狀況](../../../standard/exceptions/index.md)。 如需 `finally` 區塊的詳細資訊，請參閱 [try-finally](try-finally.md)。

## <a name="example"></a>範例

[!code-csharp[csrefKeywordsExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#1)]  

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 關鍵字](index.md)
- [try、throw 和 catch 陳述式 (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [例外狀況處理陳述式](exception-handling-statements.md)
- [throw](throw.md)
- [如何：明確擲回例外狀況](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
- [using 陳述式](using-statement.md)
