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
ms.openlocfilehash: 0571ec6dbc42f103ec922a6b2b13a52510640a78
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "75700597"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Main() 和命令列引數 (C# 程式設計指南)

`Main` 方法是 C# 應用程式的進入點。 （庫和服務不需要`Main`方法作為進入點。啟動應用程式時，`Main`該方法是調用的第一個方法。

 C# 程式中只能有一個進入點。 如果您具有多個含 `Main` 方法的類別，就必須使用 **/main** 編譯器選項來編譯您的程式，以指定要使用哪一個 `Main` 方法做為進入點。 有關詳細資訊，請參閱[-main （C# 編譯器選項）](../../language-reference/compiler-options/main-compiler-option.md)。

[!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a>概觀

- `Main` 方法是可執行程式的進入點；它是程式控制開始和結束的位置。
- `Main` 會宣告於類別或結構內部。 `Main` 必須是 [static](../../language-reference/keywords/static.md)，但不必是 [public](../../language-reference/keywords/public.md)。 （在前面的示例中，它接收[私有](../../language-reference/keywords/private.md)的預設存取權限 。封閉類或結構不一定是靜態的。
- `Main` 的傳回型別可以是 `void`、`int`，或是 `Task`、`Task<int>` (從 C# 7.1 開始)。
- 如果 且僅當`Main`返回`Task`或`Task<int>`時，聲明`Main`可以包括[`async`](../../language-reference/keywords/async.md)修飾符。 請注意，上列敘述排除了 `async void Main` 方法。
- `Main` 方法不一定要使用包含命令列引數的 `string[]` 參數來宣告。 使用 Visual Studio 創建 Windows 應用程式時，可以手動添加參數，也可以使用<xref:System.Environment.GetCommandLineArgs>方法獲取[命令列參數](command-line-arguments.md)。 參數會讀入來做為以零為基礎的命令列引數。 與 C 和 C++不同，程式的名稱不被視為`args`陣列中的第一個命令列參數，但它是<xref:System.Environment.GetCommandLineArgs>方法的第一個元素。

以下是有效`Main`簽名的清單：

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

當主控台應用程式必須啟動且等待 `Main` 中的 `await` 非同步作業時，新增的 `async` 與 `Task`、`Task<int>` 傳回型別可簡化程式碼。

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [使用 csc.exe 建置命令列](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [C# 程式設計指南](../index.md)
- [方法](../classes-and-structs/methods.md)
- [C# 程式內部](../inside-a-program/index.md)
