---
title: "快速入門 - 分支和迴圈 - C# 指南"
description: "在這個關於分支和迴圈的快速入門中，您將會撰寫 C# 程式碼以探索支援條件式分支及迴圈的語言語法，以重複執行陳述式。"
author: billwagner
ms.author: wiwagn
ms.date: 10/31/2017
ms.topic: get-started-article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 609c8625b19025a20c1da1e767870eafbab4c4a0
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2018
---
# <a name="branches-and-loops"></a>分支和迴圈

本快速入門將讓您了解如何撰寫程式碼來檢視變數，並根據那些變數來變更執行路徑。 您將會撰寫 C# 程式碼，並查看程式碼編譯和執行的結果。 本快速入門包含一系列探索 C# 中分支和迴圈建構的課程。 這些課程會教導您 C# 語言的基本概念。

本快速入門需要您具備可用於開發的電腦。 .NET 主題[只要 10 分鐘立即上手](https://www.microsoft.com/net/core) \(英文\) 中有關於在 Mac、PC 或 Linux 上設定本機開發環境的指示。 您可以在[本機快速入門簡介](local-environment.md)中快速檢視將會用到的命令，並取得可提供詳細資料的連結。

## <a name="make-decisions-using-the-if-statement"></a>使用 `if` 陳述式來做決策

建立名為 **branches-quickstart** 的目錄。 將該目錄設為目前的目錄，並執行 `dotnet new console -n BranchesAndLoops -o .`。 此命令會在目前的目錄中建立新的 .NET Core 主控台應用程式。 

在您最愛的編輯器中開啟 **Program.cs**，並以下列程式碼取代 `Console.Writeline("Hello World!");` 程式碼行：

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

在主控台視窗中輸入 `dotnet run` 來嘗試此程式碼。 您應該會看見訊息 "The answer is greater than 10" 顯示於主控台中。

修改 `b` 的宣告，讓總和小於 10： 

```csharp
int b = 3;
```

再次輸入 `dotnet run`。 因為答案小於 10，所以不會印出任何東西。 您正在測試的**條件**為 False。 您尚未有可執行的程式碼，因為您在 `if` 陳述式中僅撰寫了一個可能的分支：True 分支。

> [!TIP]
> 在您探索 C# (或任何程式設計語言) 時，可能會在撰寫程式碼時犯錯。 編譯器會找出並回報錯誤。 仔細查看錯誤輸出，以及產生該錯誤的程式碼。 編譯器錯誤通常可以協助找出問題。 

此第一個範例示範 `if` 和布林值類型的功能。 *布林值*是一個變數，可能具有下列兩種值的其中之一：`true` 或 `false`。 C# 會針對布林值變數定義特殊類型：`bool`。 `if` 陳述式會檢查 `bool` 的值。 當值為 `true` 時，就會執行 `if` 之後的陳述式。 否則，就會略過。 

這個流程可以檢查條件，並根據條件來執行陳述式，因此非常實用。


## <a name="make-if-and-else-work-together"></a>搭配使用 if 和 else

若要在 True 和 False 分支中執行不同的程式碼，則必須建立可在條件為 False 時執行的 `else` 分支。 試試這個。 將下列程式碼的最後兩行新增至您的 `Main` 方法 (您應該已經具有前面四行)：

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

只有當測試的條件為 `false` 時，才會執行 `else` 關鍵字之後的陳述式。 將 `if` 和 `else` 結合布林值條件，就可提供處理 `true` 和 `false` 條件的所有功能。

> [!IMPORTANT]
> `if` 和 `else` 陳述式之下的縮排是為了方便人類閱讀。
> C# 語言不會將縮排或空格視為有意義的內容。 `if` 或 `else` 關鍵字之後的陳述式將會根據條件來執行。 在本快速入門中的所有範例，都會遵循常見的做法，根據陳述式的控制流程將程式碼行加以縮排。

因為縮排沒有意義，當您要依條件執行的區塊中有超過一個陳述式時，就需要使用 `{` 和 `}` 來表示。 C# 程式設計人員通常會在所有的 `if` 和 `else` 子句上使用這些大括號。 下列範例與您剛剛所建立的內容相同。 修改程式碼，使它符合下列程式碼：

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
{
    Console.WriteLine("The answer is greater than 10");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
}
```

> [!TIP]
> 本快速入門的其餘部分，程式碼範例都會遵循常見的做法，在程式碼中包含大括號。

您可以測試更複雜的條件。 將下列程式碼新增至您目前已在 `Main` 方法中撰寫的內容後方：

```csharp
    int c = 4;
    if ((a + b + c > 10) && (a > b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("And the first number is greater than the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("Or the first number is not greater than the second");
}
```

`&&` 代表「且」。 這表示兩個條件都必須為 True，才會執行 True 分支中的陳述式。  這些範例也示範在每個條件式分支中可以有多個陳述式，前提是必須將陳述式放在 `{` 和 `}` 之中。

您也可以使用 `||` 來代表「或」。 在您目前已撰寫的程式碼後方新增下列程式碼：

```csharp
if ((a + b + c > 10) || (a > b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("Or the first number is greater than the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("And the first number is not greater than the second");
}
```

您已完成第一個步驟。 在開始下一節之前，讓我們將目前的程式碼移到另一個個別的方法。 這可讓您更輕鬆地開始處理新的範例。 將 `Main` 方法重新命名為 `ExploreIf`，然後撰寫會呼叫 `ExploreIf` 的新 `Main` 方法。 當您完成時，您的程式碼看起來應該像這樣：

```csharp
using System;

namespace BranchesAndLoops
{
    class Program
    {
        static void ExploreIf()
        {
            int a = 5;
            int b = 3;
            if (a + b > 10)
            {
                Console.WriteLine("The answer is greater than 10");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
            }

            if ((a + b + c > 10) && (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("And the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("Or the first number is not greater than the second");
            }

            if ((a + b + c > 10) || (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("Or the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("And the first number is not greater than the second");
            }            
        }

        static void Main(string[] args)
        {
            ExploreIf();
        }
    }
}
```

將針對 `ExploreIf()` 的呼叫註解化。 這會在您處理本節的內容時，使輸出變得較為整齊：

```csharp
//ExploreIf();
```

`//` 會在 C# 中起始一段**註解**。 註解是您想保留在原始程式碼中，但不想要作為程式碼執行的任何文字。 編譯器不會從註解產生任何可執行的程式碼。

## <a name="use-loops-to-repeat-operations"></a>使用迴圈重複執行作業

在本節中，您會使用**迴圈**來重複陳述式。 請在您的 `Main` 方法中嘗試此程式碼：

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

`while` 陳述式會檢查條件，並執行 `while` 之後的陳述式或陳述式區塊。 它會重複檢查條件並執行那些陳述式，直到條件為 False 為止。

在此範例中有一個新的運算子。 `counter` 變數之後的 `++` 是**遞增**運算子。 它會將 1 加到 `counter` 上，並將該值儲存在 `counter` 變數中。

> [!IMPORTANT]
> 請確定 `while` 迴圈條件會在您執行程式碼時會切換至 False。 否則，您建立的**無限迴圈**程式永遠不會結束。 我們不會在此範例中示範此狀況，因為您將必須使用 **CTRL-C**或其他方法來將程式強制結束。

`while` 迴圈會先測試條件，然後才執行 `while` 之後的程式碼。 `do` ... `while` 迴圈會先執行程式碼，然後才檢查條件。 do while 迴圈顯示於以下程式碼範例中：

```csharp
counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

此 `do` 迴圈和稍早的 `while` 迴圈都會產生相同的輸出。

## <a name="work-with-the-for-loop"></a>使用 for 迴圈

**for** 迴圈經常用於 C#。 請在您的 Main() 方法中嘗試此程式碼：

```csharp
for(int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
} 
```

這與先前使用的 `while` 迴圈和 `do` 迴圈有相同的功能。 `for` 陳述式有三個部分來控制其運作方式。 

第一個部分是 **for 初始設定式**：`for index = 0;` 宣告 `index` 是迴圈變數，然後將它的初始值設為 `0`。

中間的部分是 **for 條件**：`index < 10` 宣告此 `for` 迴圈只要 counter (計數器) 的值小於 10，就會繼續執行。

最後一個部分是 **for 迭代器**：`index++` 會指定在執行 `for` 陳述式之後的區塊後，如何修改迴圈變數。 在這裡，它指定 `index` 應該在每次執行區塊之後遞增 1。

您可以自行實驗這些部分。 請嘗試下列各項：

- 變更初始設定式，以不同的值開始。
- 變更條件，以不同的值停止。

當您完成後，我們會繼續使用您學到的內容來撰寫一些程式碼。

## <a name="combine-branches-and-loops"></a>結合分支和迴圈

您已經了解 C# 語言中的 `if` 陳述式和迴圈建構，接著看看您是否能夠撰寫 C# 程式碼，以找出從整數 1 至 20 能夠被 3 整除之數字的總和。  下列提供幾個提示：

- `%` 運算子可提供除法運算的餘數。
- `if` 陳述式可提供條件，以判斷數字是否應為總和的一部分。
- `for` 迴圈可協助您將 1 到 20 的所有數字重複一系列的步驟。

請自己試試看。 然後檢查成果。 您獲得的答案應該是 63。 您可以[在 GitHub 上檢視完整的程式碼](https://github.com/dotnet/docs/tree/master/samples/csharp/branches-quickstart/Program.cs#L46-L54) \(英文\) 來查看其中一個可能的答案。

您已經完成＜分支和迴圈＞快速入門。

您可以在自己的開發環境中，繼續完成[插入字串](interpolated-strings-local.md)快速入門。

您可以在下列主題中深入了解這些概念：

[If 和 else 陳述式](../language-reference/keywords/if-else.md)   
[While 陳述式](../language-reference/keywords/while.md)   
[Do 陳述式](../language-reference/keywords/do.md)   
[For 陳述式](../language-reference/keywords/for.md)   
