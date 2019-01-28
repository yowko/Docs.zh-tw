---
title: .NET Core 2.2 的新功能
description: 了解 .NET Core 2.2 所提供的新功能。
dev_langs:
- csharp
- vb
author: rpetrusha
ms.author: ronpet
ms.date: 12/04/2018
ms.openlocfilehash: 058e7ee1dc834ff23a9a4aa191f7eaeb1016375c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54679773"
---
# <a name="whats-new-in-net-core-22"></a>.NET Core 2.2 的新功能

.NET Core 2.2 包括應用程式部署、執行階段服務的事件處理、對 Azure SQL 資料庫的驗證、JIT 編譯器效能及執行 `Main` 方法前的程式碼插入等方面的增強功能。

## <a name="new-deployment-mode"></a>新的部署模式

從 .NET Core 2.2 開始，您可以部署[架構相依可執行檔](../deploying/index.md#framework-dependent-executables-fde)，也就是 **.exe** 檔案，而不是 **.dll** 檔案。 架構相依可執行檔 (FDE) 在功能上與架構相依部署類似，仍然必須要有共用的全系統 .NET Core 版本才能執行。 您的應用程式只包含您的程式碼及任何協力廠商相依性。 與架構相依部署不同，FDE 是平台特定的。

這個新部署模式的獨特優點是會建置可執行檔而非程式庫，這意謂著您可以直接執行您的應用程式，而無須先叫用 `dotnet`。

## <a name="core"></a>核心

**處理執行階段服務中的事件**

您可能常常會想要監視應用程式的執行階段服務使用情況 (例如 GC、JIT 及 ThreadPool)，以了解這些服務對您應用程式的影響。 在 Windows 系統上，通常是藉由監視目前程序的 ETW 事件來達到此目的。 雖然此方法持續行得通，但如果您是在低權限環境或是在 Linux 或 macOS 中執行，則未必總是能夠使用 ETW。  

從 .NET Core 2.2 開始，現在已可使用 <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithtype> 類別來取用 CoreCLR 事件。 這些事件將這類執行階段服務的行為描述為 GC、JIT、ThreadPool 及 Interop。 這些事件與 CoreCLR ETW 提供者所含的事件相同。  這可讓應用程式取用這些事件，或使用傳輸機制將事件傳送給遙測彙總服務。 您可以從下列程式碼範例了解如何訂閱事件：

```csharp
internal sealed class SimpleEventListener : EventListener
{
    // Called whenever an EventSource is created.
    protected override void OnEventSourceCreated(EventSource eventSource)
    {
        // Watch for the .NET runtime EventSource and enable all of its events.
        if (eventSource.Name.Equals("Microsoft-Windows-DotNETRuntime"))
        {
            EnableEvents(eventSource, EventLevel.Verbose, (EventKeywords)(-1));
        }
    }

    // Called whenever an event is written.
    protected override void OnEventWritten(EventWrittenEventArgs eventData)
    {
        // Write the contents of the event to the console.
        Console.WriteLine($"ThreadID = {eventData.OSThreadId} ID = {eventData.EventId} Name = {eventData.EventName}");
        for (int i = 0; i < eventData.Payload.Count; i++)
        {
            string payloadString = eventData.Payload[i]?.ToString() ?? string.Empty;
            Console.WriteLine($"\tName = \"{eventData.PayloadNames[i]}\" Value = \"{payloadString}\"");
        }
        Console.WriteLine("\n");
    }
}
```

此外，.NET Core 2.2 還將下列兩個屬性新增至 <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> 類別，以提供有關 ETW 事件的額外資訊：

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.OSThreadId?displayProperty=nameWithType>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.TimeStamp?displayProperty=nameWithType>

## <a name="data"></a>資料

**使用 SqlConnection.AccessToken 屬性向 Azure SQL 資料庫進行 AAD 驗證**

從 .NET Core 2.2 開始，Azure Active Directory 簽發的存取權杖可用來向 Azure SQL 資料庫進行驗證。 為了支援存取權杖，已將 <xref:System.Data.SqlClient.SqlConnection.AccessToken> 屬性新增至 <xref:System.Data.SqlClient.SqlConnection> 類別。 若要利用 AAD 驗證，請下載 4.6 版 System.Data.SqlClient NuGet 套件。 為了使用此功能，您可以使用 [`Microsoft.IdentityModel.Clients.ActiveDirectory`](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet 套件中所含的[適用於 .NET 的 Active Directory 驗證程式庫](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet)來取得存取權杖值。

## <a name="jit-compiler-improvements"></a>JIT 編譯器的改進項目

**階層式編譯仍然是可選擇加入的功能**

在 .NET Core 2.1 中，JIT 編譯器已實作「階層式編譯」這項新編譯器技術作為可選擇加入的功能。 階層式編譯的目標是要提升效能。 由 JIT 編譯器所執行的其中一項重要工作，是將程式碼的執行最佳化。 不過，針對很少使用的程式碼路徑，編譯器將程式碼最佳化的時間，可能會比執行階段執行未最佳化程式碼的時間還要久。 階層式編譯會在 JIT 編譯中引入兩個階段：

- **第一層**：盡快產生程式碼。

- **第二層**：針對那些經常執行的方法產生最佳化的程式碼。 編譯的第二層會以平行方式執行以增強效能。

如需了解階層式編譯所能產生的效能改進，請參閱[宣布推出 .NET Core 2.2 Preview 2](https://blogs.msdn.microsoft.com/dotnet/2018/09/12/announcing-net-core-2-2-preview-2/) \(英文\)。 

在 .NET Core 2.2 Preview 2 中，階層式編譯是預設啟用的功能。 不過，我們已判定我們尚未做好預設啟用階層式編譯的準備。 因此，在 .NET Core 2.2 中，階層式編譯仍繼續維持為可選擇加入的功能。 如需有關如何選擇加入階層式編譯的資訊，請參閱 [.NET Core 2.1 的新功能](dotnet-core-2-1.md)中的 [Jit 編譯器的改進項目](dotnet-core-2-1.md#jit-compiler-improvements)。

## <a name="runtime"></a>執行階段

**在執行 Main 方法前插入程式碼**

從 .NET Core 2.2 開始，您可以使用啟動勾點，在執行應用程式的 Main 方法前插入程式碼。 啟動勾點可讓主機在部署應用程式之後，自訂應用程式的行為，而無須重新編譯或變更應用程式。

我們預期主機服務提供者會定義自訂設定和原則，包括可能影響主要進入點載入行為的設定，例如 <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> 行為。 勾點可用來設定追蹤功能或遙測的插入、設定用於處理的回呼，或定義其他環境相依行為。 勾點與進入點是分開的，因此無須修改使用者程式碼。

如需詳細資訊，請參閱[主機啟動勾點](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md) \(英文\)。

## <a name="see-also"></a>另請參閱

- [.NET Core 的新功能](index.md)
- [ASP.NET Core 2.2 的新功能](/aspnet/core/release-notes/aspnetcore-2.2)
- [EF Core 2.2 中的新功能](/ef/core/what-is-new/ef-core-2.2)
