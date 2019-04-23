---
title: Main() 和命令列引數 - C# 程式設計指南
ms.custom: seodec18
ms.date: 08/02/2017
f1_keywords:
- CS5001
- main_CSharpKeyword
- Main
helpviewer_keywords:
- Main method [C#]
- C# language, command-line arguments
- arguments [C#], command-line
- command line [C#], arguments
- command-line arguments [C#], Main method
ms.assetid: 73a17231-cf96-44ea-aa8a-54807c6fb1f4
ms.openlocfilehash: f1cbbc6081c0e2f3e29d49f413e00c7346ea7e60
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61678819"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Main() 和命令列引數 (C# 程式設計指南)

`Main` 方法是 C# 應用程式的進入點。 (程式庫和服務不需要使用 `Main` 方法做為進入點)。啟動應用程式時，`Main` 方法是第一個叫用的方法。

 C# 程式中只能有一個進入點。 如果您具有多個含 `Main` 方法的類別，就必須使用 **/main** 編譯器選項來編譯您的程式，以指定要使用哪一個 `Main` 方法做為進入點。 如需詳細資訊，請參閱 [/main (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/main-compiler-option.md)。

 [!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a>總覽

- `Main` 方法是可執行程式的進入點；它是程式控制開始和結束的位置。
- `Main` 會宣告於類別或結構內部。 `Main` 必須是 [static](../../../csharp/language-reference/keywords/static.md)，但不必是 [public](../../../csharp/language-reference/keywords/public.md)。 (在先前範例中，它會接收 [private](../../../csharp/language-reference/keywords/private.md) 的預設存取)。封入類別或結構不需要是 static。
- `Main` 的傳回型別可以是 `void`、`int`，或是 `Task`、`Task<int>` (從 C# 7.1 開始)。
- 只有當 `Main` 傳回 `Task` 或 `Task<int>` 時，`Main` 的宣告才可以包含 [`async`](../../language-reference/keywords/async.md) 修飾詞。 請注意，上列敘述排除了 `async void Main` 方法。
- `Main` 方法不一定要使用包含命令列引數的 `string[]` 參數來宣告。 使用 Visual Studio 來建立 Windows 應用程式時，您可以手動新增參數，或使用 <xref:System.Environment> 類別來取得命令列引數。 參數會讀入來做為以零為基礎的命令列引數。 不同於 C 和 C++，程式的名稱不會被視為第一個命令列引數。

當主控台應用程式必須啟動且等待 `Main` 中的 `await` 非同步作業時，新增的 `async` 與 `Task`、`Task<int>` 傳回型別可簡化程式碼。

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [使用 csc.exe 建置命令列](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [方法](../../../csharp/programming-guide/classes-and-structs/methods.md)
- [C# 程式內部](../../../csharp/programming-guide/inside-a-program/index.md)
