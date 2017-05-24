---
title: "委派的一般模式"
description: "委派的一般模式"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 0ff8fdfd-6a11-4327-b061-0f2526f35b43
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 549edb4e55adf60feb874b0b8ba9d80c46ec667a
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---

# <a name="common-patterns-for-delegates"></a>委派的一般模式

[上一個](delegates-strongly-typed.md)

委派會提供一種機制，啟用與元件之間最小結合程度有關的軟體設計。

這種設計的一個絕佳範例是 LINQ。 LINQ 查詢運算式模式依賴其所有功能的委派。 請考量這個簡單範例：

```csharp
var smallNumbers = numbers.Where(n => n < 10);
```

這會篩選一系列的數字，只顯示小於值 10 的數字。
`Where` 方法會使用委派，來決定序列的哪些項目通過篩選。 當您建立 LINQ 查詢時，會對此特定用途提供委派的實作。

Where 方法的原型是︰

```csharp
public static IEnumerable<TSource> Where<in TSource> (IEnumerable<TSource> source, Func<TSource, bool> predicate);
```

這個範例會重複使用為 LINQ 一部分的所有方法。 它們全都依賴管理特定查詢之程式碼的委派。 此 API 設計模式是一種要學習和了解之功能強大的模式。

這個簡單範例說明委派如何需要元件之間的極小結合程度。 您不需要建立衍生自特定基底類別的類別。 您不需要實作特定介面。
唯一的需求是提供手邊工作的一個必要方法的實作。

## <a name="building-your-own-components-with-delegates"></a>使用委派建置自己的元件

讓我們使用依賴委派的設計來建立元件，以建置該範例。

讓我們定義可以用於大型系統中記錄檔訊息的元件。 程式庫元件可以用於許多不同環境的多個不同平台上。 在管理記錄檔的元件中有許多一般功能。 它必須接受系統中任何元件的訊息。 這些訊息將會有核心元件可管理的不同優先順序。 訊息的最終保存格式應該會有時間戳記。 如需更進階的案例，您可以依來源元件來篩選訊息。

功能有一個部分會經常變更︰即寫入訊息。 在某些環境中，它們可能會寫入至錯誤主控台。 在其他環境中，則會寫入檔案。 其他可能性包括資料庫儲存空間、OS 事件記錄檔或其他文件儲存空間。

也可以在不同案例中使用輸出的組合。 您可能會想要將訊息寫入至主控台和檔案。

以委派為基礎的設計將提供相當大的彈性，並輕鬆地支援可在未來新增的儲存機制。

透過這種設計，主要記錄元件可以是非虛擬，即使是密封類別也是一樣。 您可以插入任何一組的委派，以將訊息寫入至不同的儲存媒體。 多點傳送委派的內建支援可讓您更輕鬆地支援必須將訊息寫入至多個位置 (檔案和主控台) 的案例。

## <a name="a-first-implementation"></a>第一個實作

讓我們開始︰初始實作將接受新訊息，並使用任何附加的委派來寫入它們。 您可以開始使用一個將訊息寫入至主控台的委派。

```csharp
public static class Logger
{
    public static Action<string> WriteMessage;
    
    public static void LogMessage(string msg)
    {
        WriteMessage(msg);
    }
}
```

上述靜態類別是可運作的最簡單事項。 我們需要撰寫將訊息寫入主控台之方法的單一實作︰ 

```csharp
public static void LogToConsole(string message)
{
    Console.Error.WriteLine(message);
}
```

最後，您必須連結委派，方法是將它附加到記錄器中所宣告的 WriteMessage 委派︰

```csharp
Logger.WriteMessage += LogToConsole;
```

## <a name="practices"></a>做法

我們的範例到目前為止都相當簡單，但它仍會示範與委派有關之設計的一些重要指導方針。

使用核心架構中所定義的委派類型，可讓使用者輕鬆地使用委派。 您不需要定義新類型，而且使用您程式庫的開發人員不需要學習新的特殊委派類型。

使用的介面最小也最具彈性︰若要建立新的輸出記錄器，您必須建立一種方法。 該方法可能是靜態方法或執行個體方法。 它可能會任何存取權。

## <a name="formatting-output"></a>Formatting Output

讓我們使第一版更為強固，然後開始建立其他記錄機制。

接下來，讓我們將幾個引數新增至 `LogMessage()` 方法，讓您的記錄類別建立更結構化的訊息︰

```csharp
// Logger implementation two
public enum Severity
{
    Verbose,
    Trace,
    Information,
    Warning,
    Error,
    Critical
}

public static class Logger
{
    public static Action<string> WriteMessage;
    
    public static void LogMessage(Severity s, string component, string msg)
    {
        var outputMsg = $"{DateTime.Now}\t{s}\t{component}\t{msg}";
        WriteMessage(outputMsg);
    }
}
```

接下來，讓我們使用該 `Severity` 引數，來篩選傳送到記錄檔輸出的訊息。 

```csharp
public static class Logger
{
    public static Action<string> WriteMessage;
    
    public static Severity LogLevel {get;set;} = Severity.Warning;
    
    public static void LogMessage(Severity s, string component, string msg)
    {
        if (s < LogLevel)
            return;
            
        var outputMsg = $"{DateTime.Now}\t{s}\t{component}\t{msg}";
        WriteMessage(outputMsg);
    }
}
```
## <a name="practices"></a>做法

您已將新功能新增至記錄基礎結構。 因為記錄器元件極為鬆散結合到任何輸出機制，所以可以新增這些新功能，而不會影響任何實作記錄器委派的程式碼。

當您持續建置這項作業時，會看到更多範例來說明鬆散結合如何啟用更大的彈性來更新網站的各部分，而不需要對其他位置進行任何變更。 事實上，在較大的應用程式中，記錄器輸出類別可能位於不同的組件中，甚至不需要重新建置。

## <a name="building-a-second-output-engine"></a>建置第二個輸出引擎

也會提供記錄元件。 讓我們新增將訊息記錄到檔案的另一個輸出引擎。 這會更為牽涉到輸出引擎。 它將是封裝檔案作業的類別，並確保一律在每次寫入後關閉檔案。 這確保在產生每個訊息之後，將所有資料都排清至磁碟。

以下是檔案型記錄器︰

```csharp
public class FileLogger
{
    private readonly string logPath;
    public FileLogger(string path)
    {
        logPath = path;
        Logger.WriteMessage += LogMessage;
    }
    
    public void DetachLog() => Logger.WriteMessage -= LogMessage;

    // make sure this can't throw.
    private void LogMessage(string msg)
    {
        try {
            using (var log = File.AppendText(logPath))
            {
                log.WriteLine(msg);
                log.Flush();
            }
        } catch (Exception e)
        {
            // Hmm. Not sure what to do.
            // Logging is failing...
        }
    }
}
```

建立這個類別之後，即可將它具現化，而且它會將其 LogMessage 方法附加至記錄器元件︰

```csharp
var file = new FileLogger("log.txt");
```

這兩者不互斥。 您可以連接這兩種記錄方法，並將訊息產生到主控台和檔案︰

```csharp
var fileOutput = new FileLogger("log.txt");
Logger.WriteMessage += LogToConsole;
```

稍後，即使在相同的應用程式中，您還是可以移除其中一個委派，而且系統不會有任何其他問題︰

```csharp
Logger.WriteMessage -= LogToConsole;
```

## <a name="practices"></a>做法

現在，您已經新增記錄子系統的第二個輸出處理常式。
這個需要更多的基礎結構，才能正確支援檔案系統。 委派是執行個體方法。 它也是私用方法。
因為委派基礎結構都可以連接委派，所以不需要更大的存取範圍。

其次，委派設計會啟用多個輸出方法，而不需要任何額外程式碼。 您不需要建置任何額外基礎結構，即可支援多個輸出方法。 它們只會變成引動過程清單上的另一種方法。

請特別注意記錄輸出方法之檔案中的程式碼。 對它編寫程式碼，確保不會擲回任何例外狀況。 雖然這不一定絕對需要，但通常是不錯的做法。 如果其中一個委派方法擲回例外狀況，則不會叫用引動過程上的其餘委派。

最後請注意，檔案記錄器必須開啟和關閉每個記錄檔訊息上的檔案，以管理其資源。 您可以選擇讓檔案保持開啟，並實作 IDisposable 以在完成時關閉檔案。
任一個方法都會有其優缺點。 兩者都會建立類別之間更多的結合程度。

不需要更新記錄器類別中的程式碼，即可支援任一案例。

## <a name="handling-null-delegates"></a>處理 Null 委派

最後，讓我們更新 LogMessage 方法，以在未選取輸出機制時，在大部分情況下都更為強固。 目前實作將會在 `WriteMessage` 委派未附加引動過程清單時擲回 `NullReferenceException`。
您可能會偏好的設計是在未附加任何方法時，以無訊息模式繼續進行。 搭配使用 Null 條件運算子與 `Delegate.Invoke()` 方法，這個作業即容易達成：

```csharp
public static void LogMessage(string msg)
{
    WriteMessage?.Invoke(msg);
}
```

左運算元 (在此情況下為 `WriteMessage`) 為 Null 時，Null 條件運算子 (`?.`) 會短路，這表示不會嘗試記錄訊息。

您找不到 `System.Delegate` 或 `System.MulticastDelegate` 的文件中所列的 `Invoke()` 方法。 編譯器會針對任何宣告的委派類型產生類型安全 `Invoke` 方法。 在此範例中，這表示 `Invoke` 接受單一 `string` 引數，且具有 void 傳回型別。

## <a name="summary-of-practices"></a>做法摘要

您已了解可以使用其他寫入器和其他功能來擴充記錄元件的開頭。 在設計中使用委派，這些不同元件的結合十分鬆散。 這提供幾項優點。 它很容易建立新的輸出機制，並將它們附加至系統。 這些其他機制只需要一個方法︰寫入記錄訊息的方法。 新增功能時，這是很有彈性的設計。 任何寫入器所需的合約都是實作一個方法。 該方法可以是靜態或執行個體方法。 它可以是公用、私用或任何其他合法存取。

記錄器類別可以進行任意數目的增強或變更，而不需要中斷變更。 與任何類別一樣，修改公用 API 會有中斷變更的風險。 但是，因為記錄器與任何輸出引擎之間的結合程度只能透過委派，所以不會包含其他類型 (例如介面或基底類別)。 結合程度越小越好。

[下一個](events-overview.md)

