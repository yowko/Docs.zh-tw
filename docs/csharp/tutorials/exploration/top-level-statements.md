---
title: '最上層語句-c # 教學課程'
description: 本教學課程示範如何使用最上層的語句來實驗和證明概念，同時探索您的想法
ms.date: 10/28/2020
ms.openlocfilehash: 210fbd83bf4677061cab303089d0b27f1a4a7d01
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2020
ms.locfileid: "93189388"
---
# <a name="tutorial-explore-ideas-using-top-level-statements-to-build-code-as-you-learn"></a>教學課程：使用最上層的語句探索想法，以在您學習時建立程式碼

在本教學課程中，您將了解如何：

> [!div class="checklist"]
>
> - 瞭解如何使用最上層語句的規則。
> - 使用最上層的語句來探索演算法。
> - 將探勘重構為可重複使用的元件。

## <a name="prerequisites"></a>Prerequisites

您將需要設定您的電腦以執行 .NET 5，其中包括 c # 9 編譯器。 從 [Visual Studio 2019 16.9 版 preview 1](https://visualstudio.microsoft.com/vs/preview/) 或 [.net 5.0 SDK](https://dot.net/get-dotnet5)開始，可以使用 c # 9 編譯器。

本教學課程假設您已熟悉 C# 和 .NET，包括 Visual Studio 或 .NET Core CLI。

## <a name="start-exploring"></a>開始探索

最上層的語句可讓您將程式的進入點放在類別中的靜態方法，以避免需要額外的繁瑣。 新主控台應用程式的一般起點看起來會像下列程式碼：

```csharp
using System;

namespace Application
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

上述程式碼是 `dotnet new console` 執行命令並建立新的主控台應用程式的結果。 這11行只包含一行可執行程式碼。 您可以使用新的最上層語句功能來簡化該程式。 這可讓您移除此程式中的所有程式程式碼，而不是兩行：

```csharp
using System;

Console.WriteLine("Hello World!");
```

此動作可簡化開始探索新構想所需的一切。 您可以使用最上層的語句來撰寫腳本案例，或使用來進行探索。 完成基本工作之後，您就可以開始重構程式碼，並建立方法、類別或其他元件，以使用您所建立的可重複使用元件。 最上層的語句可讓您快速實驗和初學者教學課程。 它們也提供從實驗到完整程式的流暢途徑。

最上層的語句會依它們出現在檔案中的順序來執行。 最上層的語句只可用於應用程式中的一個原始程式檔。 如果您在多個檔案中使用，編譯器會產生錯誤。

## <a name="build-a-magic-net-answer-machine"></a>打造魔術 .NET 回應機器

在本教學課程中，我們將建立一個主控台應用程式，以隨機答案回答「是」或「否」問題。 您將逐步建立功能。 您可以專注于工作，而不是一般程式結構所需的工作。 然後，當您對功能感到滿意之後，就可以依照您的需要重構應用程式。

好的起點是將問題寫回主控台。 您可以從撰寫下列程式碼開始：

```csharp
using System;

Console.WriteLine(args);
```

您不會宣告 `args` 變數。 針對包含最上層語句的單一原始程式檔，編譯器會辨識 `args` 為代表命令列引數。 引數的類型為 `string[]` ，如同在所有 c # 程式中一樣。

您可以藉由執行下列命令來測試您的程式碼 `dotnet run` ：

```dotnetcli
dotnet run -- Should I use top level statements in all my programs?
```

`--`命令列上的引數會傳遞至程式。 您可以看到變數的類型 `args` ，因為這會功能列印到主控台：

```console
System.String[]
```

若要將問題寫入主控台，您必須列舉引數，並以空格分隔。 `WriteLine`以下列程式碼取代呼叫：

:::code language="csharp" source="snippets/top-level-statements/Program.cs" ID="EchoInput":::

現在，當您執行程式時，它會正確地將問題顯示為引數字串。

## <a name="respond-with-a-random-answer"></a>以隨機答案回應

回應問題之後，您可以加入程式碼來產生隨機答案。 從新增可能的答案陣列開始：

:::code language="csharp" source="snippets/top-level-statements/Program.cs" ID="Answers":::

這個陣列有12個肯定的答案，六個是非順序，六個為負數。 接下來，新增下列程式碼，以產生並顯示來自陣列的隨機答案：

:::code language="csharp" source="snippets/top-level-statements/Program.cs" ID="GenerateAnswer":::

您可以再次執行應用程式以查看結果。 您應該會看到類似下列輸出的內容：

```dotnetcli
dotnet run -- Should I use top level statements in all my programs?

Should I use top level statements in all my programs?
Better not tell you now.
```

這段程式碼會回答問題，但讓我們再新增一項功能。 您希望您的問題應用程式模擬對答案的思考。 您可以藉由新增一些 ASCII 動畫，並在工作時暫停。  將下列程式碼新增至回顯問題的行之後：

:::code language="csharp" source="snippets/top-level-statements/UtilitiesPassOne.cs" ID="AnimationFirstPass":::

您也需要將 `using` 語句新增至原始程式檔的頂端：

```csharp
using System.Threading.Tasks;
```

`using`語句必須在檔案中的任何其他語句之前。 否則，就是編譯器錯誤。 您可以再次執行程式，並查看動畫。 這可提供更好的體驗。 請試驗延遲的長度，以符合您的感受。

上述程式碼會建立一組以空格分隔的旋轉線。 新增 `await` 關鍵字會指示編譯器以具有修飾詞的方法產生程式進入點 `async` ，並傳回 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 。 此程式不會傳回值，因此程式進入點會傳回 `Task` 。 如果您的程式傳回整數值，您可以在最上層語句的結尾加入 return 語句。 該 return 語句會指定要傳回的整數值。 如果最上層的語句包含 `await` 運算式，則傳回類型會變成 <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> 。

## <a name="refactoring-for-the-future"></a>未來的重構

您的程式看起來應該像下列程式碼：

```csharp
using System;
using System.Threading.Tasks;

Console.WriteLine();
foreach(var s in args)
{
    Console.Write(s);
    Console.Write(' ');
}
Console.WriteLine();

for (int i = 0; i < 20; i++)
{
    Console.Write("| -");
    await Task.Delay(50);
    Console.Write("\b\b\b");
    Console.Write("/ \\");
    await Task.Delay(50);
    Console.Write("\b\b\b");
    Console.Write("- |");
    await Task.Delay(50);
    Console.Write("\b\b\b");
    Console.Write("\\ /");
    await Task.Delay(50);
    Console.Write("\b\b\b");
}
Console.WriteLine();

string[] answers =
{
    "It is certain.",       "Reply hazy, try again.",     "Don’t count on it.",
    "It is decidedly so.",  "Ask again later.",           "My reply is no.",
    "Without a doubt.",     "Better not tell you now.",   "My sources say no.",
    "Yes – definitely.",    "Cannot predict now.",        "Outlook not so good.",
    "You may rely on it.",  "Concentrate and ask again.", "Very doubtful.",
    "As I see it, yes.",
    "Most likely.",
    "Outlook good.",
    "Yes.",
    "Signs point to yes.",
};

var index = new Random().Next(answers.Length - 1);
Console.WriteLine(answers[index]);
```

上述程式碼是合理的。 這麼做確實有成效。 但它無法重複使用。 現在您已讓應用程式運作，接下來可以提取可重複使用的元件。

其中一個候選項是顯示等候動畫的程式碼。 該程式碼片段可能會變成方法：

您可以從在檔案中建立區域函數開始。 以下列程式碼取代目前的動畫：

```csharp
await ShowConsoleAnimation();

static async Task ShowConsoleAnimation()
{
    for (int i = 0; i < 20; i++)
    {
        Console.Write("| -");
        await Task.Delay(50);
        Console.Write("\b\b\b");
        Console.Write("/ \\");
        await Task.Delay(50);
        Console.Write("\b\b\b");
        Console.Write("- |");
        await Task.Delay(50);
        Console.Write("\b\b\b");
        Console.Write("\\ /");
        await Task.Delay(50);
        Console.Write("\b\b\b");
    }
    Console.WriteLine();
}
```

上述程式碼會在您的 main 方法內建立區域函數。 這仍然無法重複使用。 因此，請將該程式碼解壓縮至類別中。 建立名為 *utilities.cs* 的新檔案，並新增下列程式碼：

:::code language="csharp" source="snippets/top-level-statements/UtilitiesPassOne.cs" ID="SnippetUtilities":::

最上層的語句只能在一個檔案中，而該檔案不能包含命名空間或類型。

最後，您可以清除動畫程式碼以移除一些重複項：

:::code language="csharp" source="snippets/top-level-statements/Utiliities.cs" ID="Animation":::

現在您有一個完整的應用程式，而且您已經重構可重複使用的元件，以供稍後使用。

## <a name="summary"></a>摘要

最上層的語句可讓您更輕鬆地建立簡單的程式，以用來探索新的演算法。 您可以嘗試使用不同的程式碼片段來實驗演算法。 一旦您瞭解運作方式之後，就可以重構程式碼，以更容易維護。

最上層的語句可簡化以主控台應用程式為基礎的程式。 這些功能包括 Azure 函式、GitHub 動作和其他小型公用程式。
