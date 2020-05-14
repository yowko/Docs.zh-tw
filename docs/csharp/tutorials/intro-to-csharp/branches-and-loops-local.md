---
title: 分支和迴圈 - C# 教學課程簡介
description: 在這個關於分支和迴圈的教學課程中，您將會撰寫 C# 程式碼以探索支援條件式分支和迴圈的語言語法，以重複執行陳述式。
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: d67cfe359634783bb542e9ac34df52a095b45c20
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396885"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a>透過分支和迴圈陳述式了解條件式邏輯

此教學課程將教您如何撰寫程式碼來檢查變數，並根據那些變數來變更執行路徑。 您將會撰寫 C# 程式碼，並查看程式碼編譯和執行的結果。 此教學課程包含一系列探索 C# 中分支和迴圈建構的課程。 這些課程會教導您 C# 語言的基本概念。

此教學課程要求您必須有可用於開發的電腦。 .NET 教學課程[Hello World 在10分鐘內](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)，有在 Windows、Linux 或 macOS 上設定本機開發環境的指示。 您可以在[熟悉開發工具](local-environment.md)中快速檢視將會用到的命令，並取得可提供詳細資料的連結。

## <a name="make-decisions-using-the-if-statement"></a>使用 `if` 陳述式來做決策

建立名為 *branches-tutorial* 的目錄。 將它設為目前的目錄，然後執行下列命令：

```dotnetcli
dotnet new console -n BranchesAndLoops -o .
```

此命令會在目前的目錄中建立新的 .NET Core 主控台應用程式。

在您最愛的編輯器中開啟 *Program.cs*，並以下列程式碼取代 `Console.WriteLine("Hello World!");` 程式碼行：

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

在主控台視窗中鍵入 `dotnet run` 來嘗試此程式碼。 您應該會看見訊息 "The answer is greater than 10" 顯示於主控台中。

修改 `b` 的宣告，讓總和小於 10：

```csharp
int b = 3;
```

再次輸入 `dotnet run`。 因為答案小於 10，所以不會印出任何東西。 您正在測試的**條件**為 False。 您尚未有可執行的程式碼，因為您在 `if` 陳述式中僅撰寫了一個可能的分支：True 分支。

> [!TIP]
> 在您探索 C# (或任何程式設計語言) 時，可能會在撰寫程式碼時犯錯。 編譯器會找出並回報錯誤。 仔細查看錯誤輸出，以及產生該錯誤的程式碼。 編譯器錯誤通常可以協助找出問題。

此第一個範例示範 `if` 和布林值類型的功能。 「*布林*值」是一個變數，可以有兩個值的其中一個： `true` 或 `false` 。 C# 會針對布林值變數定義特殊類型：`bool`。 `if` 陳述式會檢查 `bool` 的值。 當值為 `true` 時，就會執行 `if` 之後的陳述式。 否則會略過。

這項檢查條件和根據這些條件執行語句的程式功能強大。

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
> C# 語言不會將縮排或空白字元視為有意義的內容。
> `if` 或 `else` 關鍵字之後的陳述式將會根據條件來執行。 此教學課程中的所有範例都遵循常見的實務，根據陳述式的控制流程縮排程式碼行。

因為縮排沒有意義，所以您需要使用 `{` 和 `}` 來表示當您想要有一個以上的語句是有條件地執行之區塊的一部分時。 C# 程式設計人員通常會在所有的 `if` 和 `else` 子句上使用這些大括號。 下列範例與您建立的相同。 修改程式碼，使它符合下列程式碼：

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
> 本教學課程的其餘部分，程式碼範例都會遵循常見的做法，在程式碼中包含大括號。

您可以測試更複雜的條件。 將下列程式碼新增至您目前已在 `Main` 方法中撰寫的內容後方：

```csharp
int c = 4;
if ((a + b + c > 10) && (a == b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("And the first number is equal to the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("Or the first number is not equal to the second");
}
```

適用於*相等*的 `==` 符號測試。 使用 `==` 可區分指派中相等的測試，您在 `a = 5` 中看過該指派。

`&&` 代表「且」。 這表示兩個條件都必須為 True，才會執行 True 分支中的陳述式。  這些範例也示範在每個條件式分支中可以有多個陳述式，前提是必須將陳述式放在 `{` 和 `}` 之中。

您也可以使用 `||` 來代表「或」。 在您目前已撰寫的程式碼後方新增下列程式碼：

```csharp
if ((a + b + c > 10) || (a == b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("Or the first number is equal to the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("And the first number is not equal to the second");
}
```

修改 `a`、`b` 和 `c` 的值，並在 `&&` 和 `||` 之間切換以進行探索。 您將更加了解 `&&` 和 `||` 運算子的工作原理。

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

`//` 會在 C# 中起始一段**註解**。 註解是您想保留在原始程式碼中，但不想要作為程式碼執行的任何文字。 編譯器不會從批註產生任何可執行檔程式碼。

## <a name="use-loops-to-repeat-operations"></a>使用迴圈重複執行作業

在本節中，您會使用**迴圈**來重複語句。 請在您的 `Main` 方法中嘗試此程式碼：

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

`while` 迴圈會先測試條件，然後才執行 `while` 之後的程式碼。 `do` ... `while` 迴圈會先執行程式碼，然後才檢查條件。 *Do while*迴圈會顯示在下列程式碼中：

```csharp
int counter = 0;
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
for (int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

先前的程式碼會執行與 `while` 您已使用的迴圈和迴圈相同的工作 `do` 。 `for` 陳述式有三個部分來控制其運作方式。

第一個部分是**for 初始化運算式**：宣告 `int index = 0;` `index` 是迴圈變數，並將它的初始值設為 `0` 。

中間部分是**for 條件**：宣告 `index < 10` 此 `for` 迴圈只要 counter 的值小於10，就會繼續執行。

最後一個部分是**for iterator**： `index++` 指定在語句後面執行區塊之後，如何修改迴圈變數 `for` 。 在這裡，它指定 `index` 應該在每次執行區塊之後遞增 1。

自行實驗。 請嘗試下列每個變化：

- 變更初始設定式，以不同的值開始。
- 變更條件，以不同的值停止。

當您完成後，我們會繼續使用您學到的內容來撰寫一些程式碼。

本教學課程未涵蓋的另一個迴圈語句： `foreach` 語句。 `foreach`語句會針對專案序列中的每個專案重複其語句。 它最常用於*集合*，因此在下一個教學課程中有涵蓋。

## <a name="created-nested-loops"></a>建立的嵌套迴圈

`while`、 `do` 或 `for` 迴圈可以嵌套在另一個迴圈內，以使用外部迴圈中每個專案的組合與內部迴圈中的每個專案來建立矩陣。 讓我們來建立一組英數位元，以代表資料列和資料行。

一個 `for` 迴圈可以產生資料列：

```csharp
for (int row = 1; row < 11; row++)
{
    Console.WriteLine($"The row is {row}");
}
```

另一個迴圈可以產生資料行：

```csharp
for (char column = 'a'; column < 'k'; column++)
{
    Console.WriteLine($"The column is {column}");
}
```

您可以將一個迴圈放在另一個，以形成配對：

```csharp
for (int row = 1; row < 11; row++)
{
    for (char column = 'a'; column < 'k'; column++)
    {
        Console.WriteLine($"The cell is ({row}, {column})");
    }
}
```

您可以看到外部迴圈會針對內部迴圈的每個完整執行遞增一次。 反轉資料列和資料行的嵌套，並查看您自己的變更。

## <a name="combine-branches-and-loops"></a>結合分支和迴圈

您已經了解 C# 語言中的 `if` 陳述式和迴圈建構，接著看看您是否能夠撰寫 C# 程式碼，以找出從整數 1 至 20 能夠被 3 整除之數字的總和。  下列提供幾個提示：

- `%` 運算子可提供除法運算的餘數。
- `if` 陳述式可提供條件，以判斷數字是否應為總和的一部分。
- `for` 迴圈可協助您將 1 到 20 的所有數字重複一系列的步驟。

請自己試試看。 然後檢查成果。 您獲得的答案應該是 63。 您可以[在 GitHub 上檢視完整的程式碼](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54) \(英文\) 來查看其中一個可能的答案。

您已經完成＜分支和迴圈＞教學課程。

您可以在自己的開發環境中，繼續完成[陣列和集合](arrays-and-collections.md)教學課程中的內容。

您可以在下列文章中深入瞭解這些概念：

- [If 和 else 陳述式](../../language-reference/keywords/if-else.md)
- [While 語句](../../language-reference/keywords/while.md)
- [Do 陳述式](../../language-reference/keywords/do.md)
- [For 語句](../../language-reference/keywords/for.md)
