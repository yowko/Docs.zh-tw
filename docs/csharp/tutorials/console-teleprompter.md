---
title: "主控台應用程式"
description: "本教學課程會教導您一些 .NET Core 和 C# 語言中的功能。"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 41e8976e7b133380687a65265fd5ebe9a810a4ff
ms.lasthandoff: 03/13/2017

---

# <a name="console-application"></a>主控台應用程式

## <a name="introduction"></a>簡介
本教學課程會教導您一些 .NET Core 和 C# 語言中的功能。 您將了解：
*    「.NET Core 命令列介面」(CLI) 的基本概念
*    「C# 主控台應用程式」的結構
*    主控台 I/O
*    .NET Core 中「檔案 I/O API」的基本概念
*    .NET Core 中「工作非同步程式設計模型」的基本概念

您將建置一個應用程式，此應用程式會讀取文字檔，並將該文字檔的內容回應至主控台。 對主控台之輸出的步調將會符合可大聲朗讀它的步調。 您可以按 ‘<’ 或 ‘>’ 鍵來將該步調調快或調慢。

本教學課程中有許多功能。 讓我們來逐一建置它們。 
## <a name="prerequisites"></a>必要條件
您必須設定電腦以執行 .NET Core。 您可以在 [.NET Core (英文)](https://www.microsoft.com/net/core) 頁面找到安裝指示。 您可以在 Windows、Linux、macOS 或是 Docker 容器中執行此應用程式。 您將必須安裝慣用的程式碼編輯器。 
## <a name="create-the-application"></a>建立應用程式
第一個步驟是建立新的應用程式。 請開啟命令提示字元，然後為您的應用程式建立新目錄。 使該目錄成為目前的目錄。 在命令提示字元處輸入命令 `dotnet new console`。 這會建立基本 “Hello World” 應用程式的起始檔案。

在您開始進行修改之前，讓我們先將執行簡單 Hello World 應用程式的所有步驟執行一遍。 在建立應用程式之後，請在命令提示字元處輸入 `dotnet restore`。 此命令會執行 NuGet 套件還原程序。 NuGet 是一個 .NET 套件管理員。 此命令會為您的專案下載任何遺漏的相依性。 由於這是一個新專案，因此沒有任何現有的相依性，所以第一次執行時將會下載 .NET Core 架構。 在這個初始步驟之後，當您新增新的相依套件或更新任何相依性的版本時，將只需要執行 `dotnet restore`。 此程序也會在您的專案目錄中建立專案鎖定檔 (project.lock.json)。 此檔案可協助管理專案相依性。 它包含所有專案相依性的本機位置。 您不需要將此檔案放在原始檔控制中；當您執行 `dotnet restore` 時，就會建立它。 

還原套件之後，您需執行 `dotnet build`。 這會執行建置引擎並建立您的應用程式可執行檔。 最後，您需執行 `dotnet run` 來執行您的應用程式。  

簡單的 Hello World 應用程式程式碼全部都在 Program.cs 中。 請使用您慣用的文字編輯器來開啟該檔案。 我們即將進行我們的最初始變更。
在該檔案的開頭，您會看到 using 陳述式：

```csharp
using System;
```

此陳述式會告訴編譯器任何來自 `System` 命名空間的型別都在範圍內。 與您可能已使用的其他「物件導向」語言相同，C# 也使用命名空間來組織型別。 這個 Hello World 程式並無不同。 您可以看到此程式是包含在 `ConsoleApplication` 命名空間中。 這不是一個非常具描述性的名稱，因此請將它變更為 `TeleprompterConsole`：

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a>讀取及回應檔案
要新增的第一個功能是讀取文字檔，並對主控台顯示該文字全部。 首先，讓我們新增一個文字檔。 請從 GitHub 儲存機制將此[範例](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-teleprompter)的 [sampleQuotes.txt](https://raw.githubusercontent.com/dotnet/docs/master/samples/csharp/getting-started/console-teleprompter/sampleQuotes.txt) 檔案複製到您的專案目錄中。 這將作為您應用程式的指令碼。

接著，在您的 Program 類別 (就在 `Main` 方法下方) 中新增下列方法：

```csharp
static IEnumerable<string> ReadFrom(string file)
{
    string line;
    using (var reader = File.OpenText(file))
    {
        while ((line = reader.ReadLine()) != null)
        {
            yield return line;
        }
    }
}
```

此方法會使用來自兩個新命名空間的型別。 若要讓此檔案進行編譯，您將必須把下列兩行新增到檔案開頭：

```csharp
using System.Collections.Generic;
using System.IO;
```

`IEnumerable<T>` 介面是在 `System.Collections.Generic` 命名空間中定義。 @System.IO.File 類別是在 `System.IO` 命名空間中定義。

此方法是 C# 方法的特殊型別，稱為「列舉程式方法」**。 列舉程式方法會傳回延遲評估的序列。 這意謂著序列中的每個項目會在取用序列的程式碼要求該項目時產生。 列舉程式方法是包含一或多個 `yield return` 陳述式的方法。 `ReadFrom` 方法所傳回的物件包含用來產生序列中每個項目的程式碼。 在此範例中，這牽涉到從原始程式檔讀取下一行文字，並傳回該字串。 每次呼叫程式碼要求序列中的下一個項目時，程式碼都會從檔案讀取下一行文字，並傳回該文字。 當已完全讀取檔案時，序列會指出已沒有任何其他項目。

有兩個其他 C# 語法元素可能是您不熟悉的。 此方法中的 `using` 陳述式會管理資源清除。 在 `using` 陳述式中初始化的變數 (在此範例中為 `reader`) 必須實作 `IDisposable` 介面。 @System.IDisposable 介面會定義單一方法 `Dispose`，在應該釋出資源時，便應該呼叫此方法。 編譯器會在執行到達 `using` 陳述式的結尾大括號時產生該呼叫。 編譯器產生的程式碼會確保即使 using 陳述式所定義區塊中的程式碼擲回例外狀況，也會釋出資源。

定義 `reader` 變數時，是使用 `var` 關鍵字來定義。 `var` 會定義一個「隱含型別區域變數」**。 這意謂著變數的型別取決於指派給該變數之物件的編譯階段型別。 在這裡，這是來自 @System.IO.File.OpenText 的傳回值，是一個 @System.IO.StreamReader 物件。
 
現在，讓我們在 `Main` 方法中填入可讀取檔案的程式碼： 

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line); 
}
```

請執行程式 (使用 `dotnet run`，然後您便可以看到每一行顯示在主控台中)。  

## <a name="adding-delays-and-formatting-output"></a>新增延遲及設定輸出格式
您的內容顯示速度太快，無法大聲朗讀。 現在您必須在輸出中新增延遲。 開始時，您將建置能夠進行非同步處理的部分核心程式碼。 不過，這些開頭的步驟會依循一些反模式。 在您新增程式碼時，註解中會指出這些反模式，然後在稍後的步驟中將會更新此程式碼。

這個部分有兩個步驟。 首先，您將更新迭代器方法以傳回單一文字而不是整行。 這是藉由下列修改來完成。 請以下列程式碼取代 `yield return line;` 陳述式：

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

接著，您必須修改取用檔案行的方式，然後在寫入每個字之後新增延遲。 請以下列區塊取代 `Main` 方法中的 `Console.WriteLine(line)` 陳述式：

```csharp
Console.Write(line);
if (!string.IsNullOrWhiteSpace(line))
{
    var pause = Task.Delay(200);
    // Synchronously waiting on a task is an
    // anti-pattern. This will get fixed in later
    // steps.
    pause.Wait();
}
```

`Task` 類別是在 `System.Threading.Tasks` 命名空間中，因此您必須在檔案開頭新增該 `using` 陳述式：

```csharp
using System.Threading.Tasks;
```

請執行範例並檢查輸出。 現在會顯示每個單字，後面接著 200 毫秒的延遲。 不過，顯示的輸出出現一些問題，因為來源文字檔有數行超過 80 個字元且沒有分行符號。 這在捲動時會相當難以閱讀。 這個問題很容易修正。 您只需記錄每一行的長度，並在每次一行達到特定臨界值時就進行換行。 請在保存行長度的 `words` 宣告之後宣告區域變數：

```csharp
var lineLength = 0;
```
 
接著，在 `yield return word + " ";` 陳述式之後 (在結尾大括號之前) 新增下列程式碼：

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```
 
請執行範例，然後您將能夠以其預先設定的步調大聲朗讀。

## <a name="async-tasks"></a>非同步工作
在這最後一個步驟中，您將新增程式碼以在一個工作中以非同步方式寫入輸出，同時也執行另一個工作以讀取來自使用者的輸入 (如果他們想要加速或減緩文字顯示)。 這包括幾個步驟，而最後，您將會擁有您所需的一切更新。
第一個步驟是建立傳回方法的非同步 @System.Threading.Tasks.Task，該方法代表您到目前為止已建立來讀取和顯示檔案的程式碼。

請將下列方法新增到您的 `Program` 類別 (這是取自您 `Main` 方法的主體)：

```csharp
private static async Task ShowTeleprompter()
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var line in words)
    {
        Console.Write(line);
        if (!string.IsNullOrWhiteSpace(line))
        {
            await Task.Delay(200);
        }
    }
}
```

您將會注意到兩項變更。 首先，在方法的主體中，此版本使用 `await` 關鍵字，而不是呼叫 @System.Threading.Tasks.Task.Wait 來同步等候工作完成。 為了這麼做，您必須將 `async` 修飾詞新增到方法簽章。 此方法會傳回 `Task`。 請注意，並沒有會傳回 `Task` 物件的傳回陳述式。 取而代之的是，會由編譯器在您使用 `await` 運算子時產生的程式碼建立 `Task` 物件。 您可以想像這個方法會在到達 `await` 時返回。 傳回的 `Task` 指出工作尚未完成。
方法會在所等候的工作完成時繼續執行。 當它執行到完成時，傳回的 `Task` 會指出它已完成。
呼叫程式碼可以監視傳回的 `Task` 以判斷它何時完成。

您可以在 `Main` 方法中呼叫這個新方法：

```csharp
ShowTeleprompter().Wait();
```

在這裡，`Main` 中的程式碼會執行同步等候。 您應該儘可能使用 `await` 運算子而不是同步等候。 但是，在主控台應用程式的 `Main` 方法中，您無法使用 `await` 運算子。 那會導致應用程式在所有工作完成之前即結束。

接著，您必須撰寫第二個非同步方法，以從主控台進行讀取並監視 ‘<’ 和 ‘>’ 鍵。 以下是您針對該工作新增的方法：

```csharp
private static async Task GetInput()
{
    var delay = 200;
    Action work = () =>
    {
        do {
            var key = Console.ReadKey(true);
            if (key.KeyChar == '>')
            {
                delay -= 10;
            }
            else if (key.KeyChar == '<')
            {
                delay += 10;
            }
        } while (true);
    };
    await Task.Run(work);
}
```

這會建立 lambda 運算式來代表 @System.Action 委派，此委派會從主控台讀取機碼，並修改代表使用者按 ‘<’ 或 ‘>’ 鍵時之延遲的區域變數。 此方法會使用 @System.Console.ReadKey 來封鎖並等候使用者按下按鍵。

若要完成此功能，您必須建立一個會傳回方法的新 `async Task`，該方法既會啟動這兩項工作 (`GetInput` 和 `ShowTeleprompter`)，也會管理這兩項工作之間的共用資料。
 
現在即可建立可處理這兩項工作間之共用資料的類別。 此類別包含兩個公用屬性：延遲和一個指出已完全讀取檔案的旗標：

```csharp
namespace TeleprompterConsole
{
    internal class TelePrompterConfig
    {
        private object lockHandle = new object();
        public int DelayInMilliseconds { get; private set; } = 200;

        public void UpdateDelay(int increment) // negative to speed up
        {
            var newDelay = Min(DelayInMilliseconds + increment, 1000);
            newDelay = Max(newDelay, 20);
            lock (lockHandle)
            {
                DelayInMilliseconds = newDelay;
            }
        }
    }
}
```

請將該類別放在新檔案中，然後如以上所示，將該類別包含在 `TeleprompterConsole` 命名空間中。 您還必須新增 `using static` 陳述式，如此您才能在不使用封入類別或命名空間名稱的情況下參考 `Min` 和 `Max` 方法。 `using static` 陳述式會從一個類別匯入方法。 這與到目前為止所使用的 `using` 陳述式形成對比，該陳述式會從命名空間匯入所有類別。

```csharp
using static System.Math;
```

另一個新的語言功能是 `lock` 陳述式。 此陳述式可確保在任何指定的時間點，該程式碼中都只能有單一執行緒。 如果有一個執行緒處於鎖定的區段，其他執行緒就必須等候第一個執行緒結束該區段。 `lock` 陳述式會使用一個保護鎖定區段的物件。 此類別會依循標準慣用語來鎖定類別中的私用物件。

接著，您必須更新 `ShowTeleprompter` 和 `GetInput` 方法以使用新的 `config` 物件。 請撰寫一個最後的 `Task` 來傳回 `async` 方法，以啟動兩項工作並在第一個工作完成時結束：

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

這裡的一個新方法是 @System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[]) 呼叫。 此方法會建立一個 `Task`，它會在其引數清單中的任何工作完成時便結束。

接著，您必須更新 `ShowTeleprompter` 和 `GetInput` 方法以使用 `config` 物件來設定延遲：

```csharp
private static async Task ShowTeleprompter(TelePrompterConfig config)
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var line in words)
    {
        Console.Write(line);
        if (!string.IsNullOrWhiteSpace(line))
        {
            await Task.Delay(config.DelayInMilliseconds);
        }
    }
    config.SetDone();
}

private static async Task GetInput(TelePrompterConfig config)
{

    Action work = () =>
    {
        do {
            var key = Console.ReadKey(true);
            if (key.KeyChar == '>')
                config.UpdateDelay(-10);
            else if (key.KeyChar == '<')
                config.UpdateDelay(10);
        } while (!config.Done);
    };
    await Task.Run(work);
}
```

這個新版本的 `ShowTeleprompter` 會呼叫 `TeleprompterConfig` 類別中的新方法。 現在，您必須更新 `Main` 以呼叫 `RunTeleprompter` 而不是 `ShowTeleprompter`：

```csharp
RunTeleprompter().Wait();
```

若要完成，您將必須將 `SetDone` 方法和 `Done` 屬性新增到 `TelePrompterConfig` 類別：

```csharp
public bool Done => done;

private bool done;

public void SetDone()
{
    done = true;    
}
```

## <a name="conclusion"></a>結論
本教學課程示範一些與在主控台應用程式中工作有關的 C# 語言和 .NET Core 程式庫相關功能。
您可以利用這項知識作為基礎，進一步探索這裡介紹的語言和類別。 您已經了解檔案和主控台 I/O 的基本概念、工作型非同步程式設計模型的封鎖和非封鎖用法、C# 語言和 C# 程式組織方式的教學課程，以及「.NET Core 命令列介面」與工具。
 
<!--aaa-->
