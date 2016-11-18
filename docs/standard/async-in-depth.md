---
title: "深入了解非同步"
description: "深入解說非同步程式碼在 .NET 中的運作方式"
keywords: .NET, .NET Core, .NET Standard
author: cartermp
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 1e38f9d9-8f84-46ee-a15f-199aec4f2e34
translationtype: Human Translation
ms.sourcegitcommit: de0dab146fc811e895dc32f98f877db5e757f82b
ms.openlocfilehash: c8ff0f81054feddb4ee7042926c817de525034f9

---

# <a name="async-in-depth"></a>深入了解非同步

撰寫 I/O-bound 和 CPU-bound 非同步程式碼的直接做法，就是使用以 .NET 工作為基礎的非同步模型。 此模型是由 `Task` 和 `Task<T>` 類型以及 `async` 和 `await` 語言關鍵字所公開。 本文說明如何使用 .NET 非同步，並深入解析幕後所使用的非同步架構。

## <a name="task-and-tasklttgt"></a>Task 與 Task&lt;T&gt;

Task 是用來實作稱為 [Promise 並行存取模型](https://en.wikipedia.org/wiki/Futures_and_promises)的建構。  簡單地說，它們會對您「承諾」工作將於稍後完成，讓您以無障礙的 API 來協調此承諾。

*   `Task` 代表不會傳回值的單一作業。
*   `Task<T>` 代表會傳回類型為 `T` 之值的單一作業。

您必須了解 Task 是以非同步方式執行工作的抽象層，而「不是」透過執行緒的抽象層。 根據預設，Task 會在目前的執行緒上執行，並視需要將工作委派給作業系統。 您可以選擇性地明確要求透過 `Task.Run` API 在個別執行緒上執行 Task。

Task 會公開 API 通訊協定，以監視、等候及存取 Task 的結果值 (如果是 `Task<T>`)。 與 `await` 關鍵字的語言整合提供更高層級的抽象層來使用 Task。 

使用 `await` 可在某個 Task 正在執行時，藉由將控制權轉讓給其呼叫端直到該 Task 完成為止，來允許您的應用程式或服務執行有用的工作。 您的程式碼不需要依賴回呼或事件，就能在 Task 完成之後繼續執行。 語言和工作 API 整合會為您執行這項作業。 如果您使用 `Task<T>`，`await` 關鍵字會另外將 Task 完成時所傳回的值「解除包裝」。  以下將進一步說明其運作方式的細節。

如需 Task 及與其互動之不同方式的詳細資訊，請參閱[以工作為基礎的非同步模式 (TAP)](https://msdn.microsoft.com/library/hh873175.aspx) 一文。

## <a name="deeper-dive-into-tasks-for-an-iobound-operation"></a>更深入了解 I/O-Bound 作業的 Task

下一節將概要描述使用一般非同步 I/O 呼叫會發生什麼情況。 首先讓我們示範兩個範例。

第一個範例會呼叫非同步方法，並傳回作用中但可能尚未完成的 Task。

```csharp
public Task<string> GetHtmlAsync()
{
    // Execution is synchronous here
    var client = new HttpClient();
    
    return client.GetStringAsync("http://www.dotnetfoundation.org");
}
```

第二個範例會加入 `async` 和 `await` 關鍵字的使用，以在 Task 上運作。

```csharp
public async Task<string> GetFirstCharactersCountAsync(string url, int count)
{
    // Execution is synchronous here
    var client = new HttpClient();
    
    // Execution of GetFirstCharactersCountAsync() is yielded to the caller here
    // GetStringAsync returns a Task<string>, which is *awaited*
    var page = await client.GetStringAsync("http://www.dotnetfoundation.org");
    
    // Execution resumes when the client.GetStringAsync task completes,
    // becoming synchronous again.
    
    if (count > page.Length)
    {
        return page;
    }
    else
    {
        return page.Substring(0, count);
    }
}
```

對 `GetStringAsync()` 的呼叫會在較低層級的 .NET 程式庫中進行 (也可能會呼叫其他非同步方法)，直到抵達原生網路程式庫中的 P/Invoke Interop 呼叫。 接著可能會在系統 API 呼叫中呼叫原生程式庫 (例如對 Linux 上的通訊端呼叫 `write()`)。 系統可能會使用 [TaskCompletionSource](xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult(%600)) 在原生/Managed 界限處建立 Task 物件。 此 Task 物件會向上傳遞給所有層級，可能在其上運作或直接傳回，最後將傳回給初始呼叫端。 

在上述第二個範例中，會從 `GetStringAsync` 傳回 `Task<T>` 物件。 使用 `await` 關鍵字會導致方法傳回新建立的 Task 物件。 控制權會從 `GetFirstCharactersCountAsync` 方法的此位置返回呼叫端。 [Task&lt;T&gt;](xref:System.Threading.Tasks.Task%601) 物件的方法和屬性可讓呼叫端監視 Task 的進度，此 Task 將在 GetFirstCharactersCountAsync 中的其餘程式碼都已執行之後完成。

系統 API 呼叫之後，要求現在會在核心空間，直到抵達 OS 的網路子系統 (例如 Linux 核心中的 `/net`)。  OS 將在此「以非同步方式」處理網路要求。  相關細節可能會因使用的 OS 而有所不同 (裝置驅動程式呼叫可能會排程作為傳回執行階段的信號，或裝置驅動程式呼叫可能會發出「再」傳回信號)，但最後都會通知執行階段此網路要求正在進行中。  此時，裝置驅動程式的工作將會是已排程、進行中或已完成 (要求已「透過網路」送出)，但由於全部都會以非同步方式進行，因此裝置驅動程式能夠立即處理其他工作！

例如，在 Windows 中，OS 執行緒會呼叫網路裝置驅動程式，並要求它透過代表網路作業的插斷要求封包 (IRP) 來執行此作業。  裝置驅動程式會接收 IRP、對網路進行呼叫、將 IRP 標記為「擱置」，然後傳回給 OS。  因為 OS 執行緒現在知道 IRP 處於「擱置」狀態，所以沒有任何要讓此作業執行的工作，並且會「傳回」以便用來執行其他工作。

要求完成並透過裝置驅動程式傳回資料之後，它會通知 CPU 透過插斷收到的新資料。  此插斷的處理方式會因 OS 而有所不同，但最後會將資料傳遞通過 OS，直到抵達系統 Interop 呼叫 (例如在 Linux 中，插斷處理常式會排程 IRQ 的後半部，以非同步方式將資料上傳通過 OS)。  請注意，這「也是」以非同步方式進行！  此結果會排入佇列，等候下一個可用的執行緒能夠執行非同步方法並將已完成 Task 的結果「解除包裝」。

這整個過程的重點是**沒有專門用來執行 Task 的執行緒**。  雖然在某些情況下會執行工作 (例如 OS 必須將資料傳遞給裝置驅動程式並回應插斷)，但沒有專門用來「等候」所要求資料傳回的執行緒。  比起等候一些 I/O 呼叫完成，這樣做可讓系統處理更大量的工作。

雖然上述做法似乎需要完成許多工作，但以時鐘時間測量時，它所花費的時間相較於實際 I/O 工作簡直是小巫見大巫。 雖然不完全精確，但這類呼叫的時間軸可能類似如下：

0-1————————————————————————————————————————————————–2-3

*   從點 `0` 至 `1` 所花費的時間，會用在非同步方法將控制權轉讓給其呼叫端之前的所有工作。
*   從點 `1` 至 `2` 所花費的時間，是 I/O 上所花費的時間 (不含 CPU 成本)。
*   最後，從點 `2` 至 `3` 所花費的時間，會用在將控制權 (可能還有值) 交回給非同步方法，然後再次執行。

### <a name="what-does-this-mean-for-a-server-scenario"></a>這對伺服器案例有何意義？

此模型適用於一般伺服器案例的工作負載。  因為沒有封鎖未完成 Task 的專用執行緒，所以伺服器執行緒集區可以服務更大量的 Web 要求。

以兩部伺服器為例︰一部執行非同步程式碼，另一部不執行。  在此範例中，每部伺服器只有 5 個執行緒可用來服務要求。  請注意，此數目比想像中的小，僅供示範內容使用。

假設這兩部伺服器收到 6 個並行要求。 每個要求會執行一個 I/O 作業。  「未使用」非同步程式碼的伺服器必須等到 5 個執行緒的其中一個已完成 I/O-bound 工作並寫入回應，才能將第 6 個要求排入佇列。 排到第 20 個要求時，由於佇列變得太長，因此伺服器可能會開始變慢。

在其上「執行」非同步程式碼的伺服器仍可將第 6 個要求排入佇列，但因為它使用 `async` 和 `await`，所以當 I/O-bound 工作開始時 (而不是完成時)，將會釋放其所包含的每個執行緒。  排到第 20 個要求時，傳入要求的佇列會很小 (如果有任何內容)，而且伺服器不會變慢。

雖然這是虛擬範例，但其運作方式與真實世界非常類似。  事實上，您可以預期伺服器使用 `async` 和 `await` 時，會比針對所收到的每個要求設定專用執行緒，能夠處理更大量的要求。

### <a name="what-does-this-mean-for-client-scenario"></a>這對用戶端案例有何意義？

針對用戶端應用程式使用 `async` 和 `await` 的最大好處在於加快回應速度。  雖然您可以透過手動繁衍執行緒來加快應用程式的回應速度，但相對於只使用 `async` 和 `await`，繁衍執行緒的做法是高度耗費資源的作業。  特別是針對重視 I/O 的項目 (例如行動遊戲)，請務必盡可能將 UI 執行緒的影響降到最低。

更重要的是，因為 I/O-bound 工作在 CPU 上花費的時間幾乎為零，所以讓整個 CPU 執行緒只用來執行極少的任何有用工作，並無法有效利用資源。

此外，使用 `async` 方法可輕鬆地將工作分派給 UI 執行緒 (例如更新 UI)，而且不需要額外的工作 (例如呼叫安全執行緒委派)。

## <a name="deeper-dive-into-task-and-taskt-for-a-cpubound-operation"></a>更深入了解 CPU-Bound 作業的 Task 和 Task<T>

CPU-bound `async` 程式碼與 I/O-bound `async` 程式碼稍微不同。  由於工作會在 CPU 上執行，因此必須指定專門用於計算的執行緒。  使用 `async` 和 `await` 可讓您無障礙地與背景執行緒互動，並確保非同步方法的呼叫端保持回應。  請注意，這不會對共用資料提供任何保護。  如果您要使用共用資料，您仍然需要套用適當的同步處理策略。

CPU-bound 非同步呼叫的概觀如下：

```csharp
public async Task<int> CalculateResult(InputData data)
{
    // This queues up the work on the threadpool.
    var expensiveResultTask = Task.Run(() => DoExpensiveCalculation(data));
    
    // Note that at this point, you can do some other work concurrently,
    // as CalculateResult() is still executing!
    
    // Execution of CalculateResult is yielded here!
    var result = await expensiveResultTask;
    
    return result;
}
```

`CalculateResult()` 會對所呼叫的執行緒執行。  當它呼叫 `Task.Run` 時，它會將執行緒集區上高度耗費資源的 CPU-bound 作業 `DoExpensiveCalculation()` 排入佇列，並收到 `Task<int>` 控制代碼。  `DoExpensiveCalculation()` 最終會對下一個可用的執行緒 (可能位於另一個 CPU 核心) 同時執行。  您可以在另一個執行緒上的 `DoExpensiveCalculation()` 忙碌時，同時執行工作，因為稱為 `CalculateResult()` 的執行緒仍在執行中。

遇到 `await` 之後，`CalculateResult()` 的執行會轉讓給呼叫端，以允許其他工作可在 `DoExpensiveCalculation()` 大量產生結果同時，使用目前的執行緒來執行。  完成後，結果會排入佇列，等候在主執行緒上執行。  最後，主執行緒會返回正在執行的 `CalculateResult()`，此時它會有 `DoExpensiveCalculation()` 的結果。

### <a name="why-does-async-help-here"></a>為什麼非同步有助於此作業？

當您需要快速回應，`async` 與 `await` 是管理 CPU-bound 工作的最佳做法。 搭配 CPU-bound 工作使用 async 的模式有許多種。 請務必注意使用 async 會耗費少量成本，而且不建議用於緊密迴圈。  您必須自行決定要如何撰寫以這項新功能為主的程式碼。


<!--HONumber=Nov16_HO3-->


