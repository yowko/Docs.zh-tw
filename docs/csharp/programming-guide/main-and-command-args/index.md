---
title: Main() 和命令列引數 - C# 程式設計指南
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
ms.openlocfilehash: 723884dd448232777ae2cfeac5bfcf5ea24363b0
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007737"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Main() 和命令列引數 (C# 程式設計指南)

`Main` 方法是 C# 應用程式的進入點。 （程式庫和服務不需要 `Main` 方法做為進入點）。當應用程式啟動時， `Main` 方法是第一個叫用的方法。

C# 程式中只能有一個進入點。 如果您有多個具有方法的類別 `Main` ，則必須使用編譯器選項來編譯器， `-main` 以指定 `Main` 要使用哪一個方法做為進入點。 如需詳細資訊，請參閱[-main （c # 編譯器選項）](../../language-reference/compiler-options/main-compiler-option.md)。

[!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a>概觀

- `Main` 方法是可執行程式的進入點；它是程式控制開始和結束的位置。
- `Main` 會宣告於類別或結構內部。 `Main` 必須是 [static](../../language-reference/keywords/static.md)，但不必是 [public](../../language-reference/keywords/public.md)。 （在先前的範例中，它會接收[私](../../language-reference/keywords/private.md)用的預設存取權）。封入類別或結構不需要是靜態的。
- `Main` 的傳回型別可以是 `void`、`int`，或是 `Task`、`Task<int>` (從 C# 7.1 開始)。
- 只有在傳回 `Main` `Task` 或時，的宣告才 `Task<int>` `Main` 會包含 [`async`](../../language-reference/keywords/async.md) 修飾詞。 請注意，上列敘述排除了 `async void Main` 方法。
- `Main` 方法不一定要使用包含命令列引數的 `string[]` 參數來宣告。 使用 Visual Studio 建立 Windows 應用程式時，您可以手動新增參數，或使用 <xref:System.Environment.GetCommandLineArgs> 方法來取得[命令列引數](command-line-arguments.md)。 參數會讀入來做為以零為基礎的命令列引數。 不同于 C 和 c + +，程式的名稱不會被視為陣列中的第一個命令列引數 `args` ，而是方法的第一個元素 <xref:System.Environment.GetCommandLineArgs> 。

以下是有效簽章的清單 `Main` ：

```csharp
public static void Main() { }
public static int Main() { }
public static void Main(string[] args) { }
public static int Main(string[] args) { }
public static async Task Main() { }
public static async Task<int> Main() { }
public static async Task Main(string[] args) { }
public static async Task<int> Main(string[] args) { }
```

上述範例全都使用公用存取子修飾詞。 這是典型的，但並非必要。

當主控台應用程式必須啟動且等待 `Main` 中的 `await` 非同步作業時，新增的 `async` 與 `Task`、`Task<int>` 傳回型別可簡化程式碼。

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [使用 csc.exe 建置命令列](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [C # 程式設計指南](../index.md)
- [方法](../classes-and-structs/methods.md)
- [在 c # 程式中](../inside-a-program/index.md)
