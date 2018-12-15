---
title: .NET Core 3.0 的新功能
description: 了解 .NET Core 3.0 所提供的新功能。
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 12/04/2018
ms.openlocfilehash: 3ca833031eb8bb0f43a334f833f2e0075842d57d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53156666"
---
# <a name="whats-new-in-net-core-30-preview-1"></a>.NET Core 3.0 (Preview 1) 的新功能

本文描述 .NET Core 3.0 (Preview 1) 的新功能。 其中一個最大的增強功能是對 Windows 傳統型應用程式的支援 (僅限 Windows)。 您可以運用名為「Windows 傳統型」的 .NET Core 3.0 元件來移植 Windows Forms 和 Windows Presentation Foundation (WPF) 應用程式。 具體而言，只有在 Windows 上才支援「Windows 傳統型」元件。 如需詳細資訊，請參閱下面的 [Windows 傳統型](#windows-desktop)一節。

.NET Core 3.0 新增 C# 8.0 支援。

請立即在 Windows、Mac 及 Linux 上[下載並開始使用 .NET Core 3 Preview 1](https://aka.ms/netcore3download)。 您可以在 [.NET Core 3 Preview 1 版本資訊](https://aka.ms/netcore3releasenotes) \(英文\) 中查看完整的版本詳細資料。

如需詳細資訊，請參閱 [.NET Core 3.0 Preview 1 公告](https://blogs.msdn.microsoft.com/dotnet/2018/12/04/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/) \(英文\)。

## <a name="net-standard-21"></a>.NET Standard 2.1

.NET Core 3.0 實作 .NET Standard 2.1。

## <a name="default-executables"></a>預設可執行檔

.NET Core 現在預設將會建置可執行檔。 這對於使用 .NET Core 全域安裝版本的應用程式來說，是一項新功能。 到目前為止，只有[獨立式部署](../deploying/index.md#self-contained-deployments-scd)具有可執行檔。

進行 `dotnet build` 或 `dotnet publish` 期間，如果與您所使用 SDK 的環境和平台相符，就會建立可執行檔。 針對這些可執行檔，您可以預期能夠進行與其他原生可執行檔相同的操作，例如：

* 您可以按兩下可執行檔。
* 您可以直接從命令提示字元啟動應用程式，例如在 Windows 上為 `myapp.exe`，在 Linux 和 macOS 上為 `./myapp`。

> [!NOTE]
> 不支援使用 `dotnet publish -r` 或 `dotnet build -r` 引數為其他執行階段環境指定特定執行階段。

## <a name="build-copies-dependencies"></a>組建複本相依性

`dotnet build` 現在會從 NuGet 快取將您應用程式的 NuGet 相依性複製到組建輸出資料夾。 先前，只有在進行 `dotnet publish` 的過程中，才會複製相依性。 

有些作業 (例如連結和 Razor 頁面發佈) 仍然需要發佈。


## <a name="local-dotnet-tools"></a>本機 dotnet 工具

.NET Core 2.1 支援全域工具，.NET Core 3.0 現在則具有本機工具。 本機工具與全域工具類似，但與磁碟上的某個特定位置相關聯。 這可針對個別專案和個別存放庫提供工具。 所有安裝在本機的工具都不是全域可用的工具。

本機工具會倚賴您目前目錄中名為 `dotnet-tools.json` 的資訊清單檔。 此資訊清單檔會定義將可供使用的工具。 藉由在存放庫的根目錄建立此資訊清單檔，您便可確保任何複製您程式碼的人員都可進行還原，以及使用成功運用您程式碼所需的工具。

當有本機工具資訊清單檔可用時，請使用下列命令在本機自動下載並安裝這些工具：

```console
dotnet tool restore
```

使用下列命令來執行本機工具：

```console
dotnet tool run <tool-command-name>
```

呼叫本機工具時，dotnet 會沿著目錄結構向上搜尋資訊清單。 找到工具資訊清單檔時，會在其中搜尋所要求的工具。 如果找到工具，它會包含在 NuGet 全域套件位置中尋找該工具所需的資訊。 

如果在資訊清單中找到工具，但在快取中找不到，使用者就會收到錯誤。 在 Preview 1 之後，此訊息將改進為要求使用者執行 `dotnet tool restore`。

若要將本機工具新增至目錄，您必須先建立工具資訊清單檔。 在 Preview 1 之後，我們將提供一個建立工具資訊清單檔的機制，例如 dotnet 新範本。 針對 Preview 1，您必須建立一個名為 `dotnet-tools.json` 且含有下列內容的檔案：

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {}
}
```

建立資訊清單之後，您可以使用下列命令在資訊清單中新增本機工具：

```console
dotnet tool install <toolPackageId>
```

此命令會安裝最新的工具版本，除非已指定另一個版本。  即使已自動選擇最新版本，仍然會將工具的版本寫入至工具資訊清單檔，以允許還原或執行正確的工具版本。

工具資訊清單檔的設計目的是要允許手動編輯 – 當您要更新與存放庫搭配運作所需的版本時，可能會這麼做。

以下是一個範例 `dotnet-tools.json` 檔案：

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "dotnetsay": {
      "version": "2.1.4",
      "commands": [
        "dotnetsay"
      ]
    },
    "t-rex": {
      "version": "1.0.103",
      "commands": [
        "t-rex"
      ]
    }
  }
}
```

若要從工具資訊清單檔中移除某個工具，請執行下列命令：

```console
dotnet tool uninstall <toolPackageId>
```

不論是全域工具還是區域工具，都需要一個相容的執行階段版本。 NuGet.org 上目前許多工具都以 .NET Core 執行階段 2.1 為目標。 若要在全域或本機安裝這些工具，您仍然需要安裝 [NET Core 2.1 執行階段](https://dotnet.microsoft.com/download/dotnet-core/2.1)。

如需詳細資訊，請參閱[本機工具早期預覽文件](https://github.com/dotnet/cli/issues/10288) \(工具\)。

## <a name="windows-desktop"></a>Windows 桌面

從 .NET Core 3.0 Preview 1 開始，您可以使用 WPF 和 Windows Forms 來建置 Windows 傳統型應用程式。 這些架構也支援透過 [XAML 島](/windows/uwp/xaml-platform/xaml-host-controls)使用來自 Windows UI XAML 程式庫 (WinUI) 的新式控制項和 Fluent 樣式。

「Windows 傳統型」元件是 Windows .NET Core 3.0 SDK 的一部分。

您可以使用下列 `dotnet` 命令來建立新的 WPF 或 Windows Forms 應用程式：

```console
dotnet new wpf
dotnet new winforms
```

您也可以在 Visual Studio 2019 Preview 1 中開啟、啟動 .NET Core 3.0 WPF 和 Windows Forms 專案，以及對這新專案進行偵錯。 目前您可以在 Visual Studio 2017 15.9 中開啟這些專案，不過，並不支援這樣的案例 (而且您必須[啟用預覽](https://blogs.msdn.microsoft.com/dotnet/2018/11/13/net-core-tooling-update-for-visual-studio-2017-version-15-9/))。

新專案與現有的 .NET Core 專案相同，但有新增一些項目。 以下是基本 .NET Core 主控台專案與基本 Windows Forms 和 WPF 專案的比較。

在 .NET Core 主控台專案中，專案會使用 `Microsoft.NET.Sdk` SDK，並透過 `netcoreapp3.0` 目標架構宣告與 .NET Core 3.0 的相依性。 若要建立 Windows 傳統型應用程式，請使用 `Microsoft.NET.Sdk.WindowsDesktop` SDK，然後選擇要使用的 UI 架構：

```diff
-<Project Sdk="Microsoft.NET.Sdk">
+<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
+   <UseWPF>true</UseWPF>
  </PropertyGroup>
</Project>
```

若要選擇 Windows Forms 而不選擇 WPF，請設定 `UseWindowsForms` 而不要設定 `UseWPF`：

```diff
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
-   <UseWPF>true</UseWPF>
+   <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>
</Project>
```

如果應用程式同時使用這兩種架構 (例如當 Windows Forms 對話方塊裝載 WPF 控制項時)，則可以將 `UseWPF` 和 `UseWindowsForms` 都設定為 `true`。

請在 [dotnet/winforms](https://github.com/dotnet/winforms/issues)、[dotnet/wpf](https://github.com/dotnet/wpf/issues) 及 [dotnet/core](https://github.com/dotnet/core/issues) 存放庫上分享您的意見反應。

## <a name="fast-built-in-json-support"></a>快速的內建 JSON 支援

`System.Text.Json.Utf8JsonReader` 是一個高效能、低配置、只能順向讀取的 UTF-8 編碼 JSON 文字讀取器，會從 `ReadOnlySpan<byte>` 開始讀取。 `Utf8JsonReader` 是一個基礎的低階類型，可用來建置自訂剖析器和還原序列化程式。 使用新的 `Utf8JsonReader` 來讀取 JSON 承載會比使用來自 [Json.NET](https://www.newtonsoft.com/json) 的讀取器快兩倍。 它會等到您需要將 JSON 權杖實現為 (UTF-16) 字串時，才進行配置。

這個新 API 將包含下列元件：

* 在 Preview 1 中：JSON 讀取器 (循序存取)
* 在即將推出的版本中：JSON 寫入器、DOM (隨機存取)、POCO 序列化程式、POCO 還原序列化程式

以下是 `Utf8JsonReader` 的基本讀取器迴圈，您可以使用它作為起點：

```csharp
using System.Text.Json;

public static void Utf8JsonReaderLoop(ReadOnlySpan<byte> dataUtf8)
{
    var json = new Utf8JsonReader(dataUtf8, isFinalBlock: true, state: default);

    while (json.Read())
    {
        JsonTokenType tokenType = json.TokenType;
        ReadOnlySpan<byte> valueSpan = json.ValueSpan;
        switch (tokenType)
        {
            case JsonTokenType.StartObject:
            case JsonTokenType.EndObject:
                break;
            case JsonTokenType.StartArray:
            case JsonTokenType.EndArray:
                break;
            case JsonTokenType.PropertyName:
                break;
            case JsonTokenType.String:
                string valueString = json.GetStringValue();
                break;
            case JsonTokenType.Number:
                if (!json.TryGetInt32Value(out int valueInteger))
                {
                    throw new FormatException();
                }
                break;
            case JsonTokenType.True:
            case JsonTokenType.False:
                bool valueBool = json.GetBooleanValue();
                break;
            case JsonTokenType.Null:
                break;
            default:
                throw new ArgumentException();
        }
    }

    dataUtf8 = dataUtf8.Slice((int)json.BytesConsumed);
    JsonReaderState state = json.CurrentState;
}
```

.NET 生態系統倚賴 [Json.NET](https://www.newtonsoft.com/json) 及其他熱門的 JSON 程式庫 (這些仍持續是絕佳的選擇)。 JSON.NET 使用 .NET 字串作為其基底資料類型，實際上就是 UTF-16。 

在 .NET Core 2.1 和 3.0 中，我們新增了新的 API，可讓您根據使用 `Span<T>` 和 UTF-8 字串，撰寫所需記憶體少很多且更符合高輸送量應用程式 (例如 Kestrel、ASP.NET Core Web 伺服器) 需求的 JSON API (例如 `Utf8JsonReader`)。

## <a name="ranges-and-indices"></a>範圍和索引

新的 `Index` 類型可用於編製索引。 您可以從會從開頭算起的 `int` 或使用會從結尾算起的前置詞 `^` 運算子 (C#)，來建立一個索引：

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

此外，還有 `Range` 類型，此類型由兩個 `Index` 值所組成 (一個代表開頭，一個代表結尾)，並可用 `x..y` 範圍運算式 (C#) 來撰寫。 您可以接著使用 `Range` 來編製索引以產生配量：

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

> [!NOTE]
> 只有 [C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2018/11/12/building-c-8-0/) 才支援 `Range` 和 `Index` 的語法。

## <a name="async-streams"></a>非同步資料流

`IAsyncEnumerable<T>` 類型是 `IEnumerable<T>` 的新非同步版本。 此語言可讓您針對這些執行 `await foreach` 以取用其元素，然後對它們執行 `yield return` 以產生元素。

下列範例同時示範如何產生和取用非同步資料流。 `foreach` 是非同步陳述式，其本身會使用 `yield return` 來為呼叫端產生非同步資料流。 此模式 (使用 `yield return`) 是針對產生非同步資料流建議採用的模型。

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result; 
    }
}
```

> [!WARNING]
> .NET Core 3.0 Preview 1 目前有 `await foreach` 方面的 Bug。 請改用 `GetEnumerator` 和 `MoveNext` 來處理元素。 如需詳細資訊，請參閱 [roslyn/#31268](https://github.com/dotnet/roslyn/issues/31268)。

除了能夠執行 `await foreach` 之外，您也可以建立非同步迭代器，例如建立一個會傳回 `IAsyncEnumerable/IAsyncEnumerator` 以供您在其中執行 `await` 和 `yield` 的迭代器。 針對需要處置的物件，您可以使用各種 BCL 類型 (例如 `Stream` 和 `Timer`) 所實作的 `IAsyncDisposable`。

> [!NOTE]
> 只有 [C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2018/11/12/building-c-8-0/) 才支援 `await foreach` 語法。

## <a name="type-sequencereader"></a>類型：SequenceReader

在 .NET Core 3.0 中已新增 `System.Buffers.SequenceReader`，這可用來作為 `ReadOnlySequence<T>` 的讀取器。 這可讓您以輕鬆、高效能、低配置的方式，剖析可跨多個支援緩衝區的 `System.IO.Pipelines` 資料。 

下列範例將輸入 `Sequence` 分成以 `CR/LF` 分隔的有效行：

```csharp
private static ReadOnlySpan<byte> CRLF => new byte[] { (byte)'\r', (byte)'\n' };

public static void ReadLines(ReadOnlySequence<byte> sequence)
{
    SequenceReader<byte> reader = new SequenceReader<byte>(sequence);

    while (!reader.End)
    {
        if (!reader.TryReadToAny(out ReadOnlySpan<byte> line, CRLF, advancePastDelimiter:false))
        {
            // Couldn't find another delimiter
            // ...
        }

        if (!reader.IsNext(CRLF, advancePast: true))
        {
            // Not a good CR/LF pair
            // ...
        }

        // line is valid, process
        ProcessLine(line);
    }
}
```

## <a name="type-metadataloadcontext"></a>類型：MetadataLoadContext

已新增 `MetadataLoadContext` 類型，可讓您讀取組件中繼資料，而不會影響到呼叫端的應用程式網域。 讀取組件 (包括為與目前執行階段環境不同的架構和平台建置的組件) 時，會將組件當作資料來讀取。 `MetadataLoadContext` 與 <xref:System.Reflection.Assembly.ReflectionOnlyLoad*> (只有在 .NET Framework 中才有提供) 重疊。

`MetdataLoadContext` 是 [System.Reflection.MetadataLoadContext 套件](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext)中所提供的類型。 這是一個 .NET Standard 2.0 套件。

`MetadataLoadContext` 公開 API 的方式與 <xref:System.Runtime.Loader.AssemblyLoadContext> 類型類似，但並非以該類型為基礎。 就像 <xref:System.Runtime.Loader.AssemblyLoadContext> 一樣，`MetadataLoadContext` 也可讓您載入已隔離之組件載入 Universe 內的組件。 `MetdataLoadContext` API 會傳回 <xref:System.Reflection.Assembly> 物件，以讓您使用熟悉的反映 API。 執行導向 API (例如 [MethodBase.Invoke](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/src/System/Reflection/TypeLoading/Methods/RoMethod.cs#L127)) 不是允許使用的 API，將會擲回 InvalidOperationException。

下列範例示範如何在實作指定介面的組件中尋找具體的類型：

```csharp
var paths = new string[] {@"C:\myapp\mscorlib.dll", @"C:\myapp\myapp.dll"};
var resolver = new PathAssemblyResolver(paths);
using (var lc = new MetadataLoadContext(resolver))
{
    Assembly a = lc.LoadFromAssemblyName("myapp");
    Type myInterface = a.GetType("MyApp.IPluginInterface");
    foreach (Type t in a.GetTypes())
    {
        if (t.IsClass && myInterface.IsAssignableFrom(t))
            Console.WriteLine($"Class {t.FullName} implements IPluginInterface");
    }
}
```

`MetadataLoadContext` 的案例包括設計階段功能、組建階段工具及執行階段啟動功能，這些功能需要將一組組件當作資料來檢查，並將所有檔案鎖定及在執行檢查後將記憶體釋出。

`MetadataLoadContext` 具有一個會傳送給其建構函式的解析程式類別。 此解析程式的工作是在已指定 `AssemblyName` 的情況下載入 `Assembly`。 此解析程式類別衍生自抽象的 `MetadataAssemblyResolver` 類別。 提供路徑型案例的解析器實作時，會以 `PathAssemblyResolver` 提供。

[MetadataLoadContext 測試](https://github.com/dotnet/corefx/tree/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests) 示範許多使用案例。 [組件測試](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests/Assembly/AssemblyTests.cs)是一個絕佳的起點。

## <a name="tls-13--openssl-111-on-linux"></a>Linux 上的 TLS 1.3 和 OpenSSL 1.1.1

.NET Core 現在會利用 [OpenSSL 1.1.1 中的 TLS 1.3 支援](https://www.openssl.org/blog/blog/2018/09/11/release111/) (當在指定的環境中有提供時)。 依據 [OpenSSL 小組](https://www.openssl.org/blog/blog/2018/09/11/release111/)，TLS 1.3 有多項優點：

* 因為用戶端與伺服器之間的來回行程次數減少，所以改善了連線時間。

* 因為移除各種已淘汰和不安全的密碼編譯演算法，並加密更大部分的連線信號交換，所以提升了安全性。

.NET Core 3.0 Preview 1 能夠利用 **OpenSSL 1.1.1**、**OpenSSL 1.1.0** 或 **OpenSSL 1.0.2** (不論在 Linux 系統上找到的最佳版本是哪一個)。  當 **OpenSSL 1.1.1** 可供使用時，在使用 `SslProtocols.None` (系統預設通訊協定) 的情況下，如果用戶端和伺服器都支援 **TLS 1.3**，SslStream 和 HttpClient 類型就會使用 **TLS 1.3**。

下列範例示範連線至 <https://www.cloudflare.com> 之 Ubuntu 18.10 上的 .NET Core 3.0 Preview 1：

```csharp
using System;
using System.Net.Security;
using System.Net.Sockets;
using System.Threading.Tasks;

namespace tlstest
{
    class Program
    {
        static async Task Main()
        {
            using (TcpClient tcpClient = new TcpClient())
            {
                string targetHost = "www.cloudflare.com";

                await tcpClient.ConnectAsync(targetHost, 443);

                using (SslStream sslStream = new SslStream(tcpClient.GetStream()))
                {
                    await sslStream.AuthenticateAsClientAsync(targetHost);
                    await Console.Out.WriteLineAsync($"Connected to {targetHost} with {sslStream.SslProtocol}");
                }
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/tlstest$ dotnet run
Connected to www.cloudflare.com with Tls13
user@comp-ubuntu1810:~/tlstest$ openssl version
OpenSSL 1.1.1  11 Sep 2018
```

>[!IMPORTANT]
>Windows 和 macOS 尚未支援 **TLS 1.3**。 .NET Core 3.0 將在有支援可用時，在這些作業系統上支援 **TLS 1.3**。

## <a name="cryptography"></a>密碼編譯

已新增對 **AES-GCM** 和 **AES-CCM** 加密方式的支援 (透過 `System.Security.Cryptography.AesGcm` 和 `System.Security.Cryptography.AesCcm` 來實作)。 這些演算法既是[搭配關聯資料的驗證加密 (AEAD) 演算法](https://en.wikipedia.org/wiki/Authenticated_encryption)，也是最先新增至 .NET Core 的「驗證加密」(AE) 演算法。

下列程式碼示範如何使用 **AesGcm** 加密方式將隨機資料加密和解密。

**AesCcm** 的程式碼看起來幾乎完全相同 (只有類別變數名稱會有所不同)。

```csharp
// key should be: pre-known, derived, or transported via another channel, such as RSA encryption
byte[] key = new byte[16];
RandomNumberGenerator.Fill(key);

byte[] nonce = new byte[12];
RandomNumberGenerator.Fill(nonce);

// normally this would be your data
byte[] dataToEncrypt = new byte[1234];
byte[] associatedData = new byte[333];
RandomNumberGenerator.Fill(dataToEncrypt);
RandomNumberGenerator.Fill(associatedData);

// these will be filled during the encryption
byte[] tag = new byte[16];
byte[] ciphertext = new byte[dataToEncrypt.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Encrypt(nonce, dataToEncrypt, ciphertext, tag, associatedData);
}

// tag, nonce, ciphertext, associatedData should be sent to the other part

byte[] decryptedData = new byte[ciphertext.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Decrypt(nonce, ciphertext, tag, decryptedData, associatedData);
}

// do something with the data
// this should always print that data is the same
Console.WriteLine($"AES-GCM: Decrypted data is{(dataToEncrypt.SequenceEqual(decryptedData) ? "the same as" : "different than")} original data.");
```

## <a name="cryptographic-key-importexport"></a>密碼編譯金鑰匯入/匯出

.NET Core 3.0 Preview 1 支援從標準格式匯入及匯出非對稱式公開金鑰與私密金鑰，而無須使用 X.509 憑證。

所有金鑰類型 (RSA、DSA、ECDsa、ECDiffieHellman) 都支援適用於公開金鑰的 **X.509 SubjectPublicKeyInfo** 格式，以及適用於私密金鑰的 **PKCS#8 PrivateKeyInfo** 和 **PKCS#8 EncryptedPrivateKeyInfo** 格式。 RSA 還額外支援 **PKCS#1 RSAPublicKey** 和 **PKCS#1 RSAPrivateKey**。 所有匯出方法都會產生 DER 編碼的二進位資料，而匯出方法也是如此。 如果金鑰是以適合文字的 PEM 格式儲存的，呼叫端在呼叫匯入方法之前，就必須先對內容進行 Base64 解碼。

```csharp
using System;
using System.IO;
using System.Security.Cryptography;

namespace rsakeyprint
{
    class Program
    {
        static void Main(string[] args)
        {
            using (RSA rsa = RSA.Create())
            {
                byte[] keyBytes = File.ReadAllBytes(args[0]);
                rsa.ImportRSAPrivateKey(keyBytes, out int bytesRead);
 
                Console.WriteLine($"Read {bytesRead} bytes, {keyBytes.Length-bytesRead} extra byte(s) in file.");
                RSAParameters rsaParameters = rsa.ExportParameters(true);
                Console.WriteLine(BitConverter.ToString(rsaParameters.D));
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/rsakeyprint$ echo Making a small key to save on screen space.
Making a small key to save on screen space.
user@comp-ubuntu1810:~/rsakeyprint$ openssl genrsa 768 | openssl rsa -outform der -out rsa.key
Generating RSA private key, 768 bit long modulus (2 primes)
..+++++++
........+++++++
e is 65537 (0x010001)
writing RSA key
user@comp-ubuntu1810:~/rsakeyprint$ dotnet run rsa.key
Read 461 bytes, 0 extra byte(s) in file.
0F-D0-82-34-F8-13-38-4A-7F-C7-52-4A-F6-93-F8-FB-6D-98-7A-6A-04-3B-BC-35-8C-7D-AC-A5-A3-6E-AD-C1-66-30-81-2C-2A-DE-DA-60-03-6A-2C-D9-76-15-7F-61-97-57-
79-E1-6E-45-62-C3-83-04-97-CB-32-EF-C5-17-5F-99-60-92-AE-B6-34-6F-30-06-03-AC-BF-15-24-43-84-EB-83-60-EF-4D-3B-BD-D9-5D-56-26-F0-51-CE-F1
user@comp-ubuntu1810:~/rsakeyprint$ openssl rsa -in rsa.key -inform der -text -noout | grep -A7 private
privateExponent:
    0f:d0:82:34:f8:13:38:4a:7f:c7:52:4a:f6:93:f8:
    fb:6d:98:7a:6a:04:3b:bc:35:8c:7d:ac:a5:a3:6e:
    ad:c1:66:30:81:2c:2a:de:da:60:03:6a:2c:d9:76:
    15:7f:61:97:57:79:e1:6e:45:62:c3:83:04:97:cb:
    32:ef:c5:17:5f:99:60:92:ae:b6:34:6f:30:06:03:
    ac:bf:15:24:43:84:eb:83:60:ef:4d:3b:bd:d9:5d:
    56:26:f0:51:ce:f1
```

若要檢查 PKCS#8 檔案，可以使用 `System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo` 類別。

若要檢查和操作 PFX/PKCS#12 檔案，可以分別使用 `System.Security.Cryptography.Pkcs.Pkcs12Info` 和 `System.Security.Cryptography.Pkcs.Pkcs12Builder`。

## <a name="serialport-for-linux"></a>適用於 Linux 的 SerialPort

.NET Core 3.0 現已在 Linux 上支援 <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>。

先前，.NET Core 僅支援在 Windows 上使用 `SerialPort` 類型。

## <a name="more-bcl-improvements"></a>更多 BCL 改進

在 .NET Core 3.0 中，已將在 .NET Core 2.1 中導入的 `Span<T>`、`Memory<T>` 及相關類型最佳化。 範圍建構、配量、剖析及格式化等常見作業現在執行效能更佳。 

此外，`String` 這類類型也有隱含的改進，使其在搭配 `Dictionary<TKey, TValue>` 及其他集合作為金鑰使用時更有效率。 您無須進行任何程式碼變更，即可享有這些改進的好處。

以下也是 .NET Core 3 Preview 1 中新增的改進：

* HttpClient 內建 Brotli 支援
* ThreadPool.UnsafeQueueWorkItem(IThreadPoolWorkItem)
* Unsafe.Unbox
* CancellationToken.Unregister
* 複雜算術運算子
* 適用於 TCP 持續連線的通訊端 API
* StringBuilder.GetChunks
* IPEndPoint 剖析
* RandomNumberGenerator.GetInt32

## <a name="tiered-compilation"></a>階層式編譯

使用 .NET Core 3.0 時，預設會開啟[階層式編譯](https://blogs.msdn.microsoft.com/dotnet/2018/08/02/tiered-compilation-preview-in-net-core-2-1/)。 這是一項可讓執行階段更彈性使用 Just-In-Time (JIT) 編譯器的功能，可在啟動時及將輸送量最大化時獲得更佳的效能。

此功能在 [.NET Core 2.1](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/) 中是新增為選用功能，然後在 [.NET Core 2.2 Preview 2](https://blogs.msdn.microsoft.com/dotnet/2018/09/12/announcing-net-core-2-2-preview-2/) 中為預設啟用的功能。 之後，在 .NET Core 2.2 版本中則又還原回選用功能。

## <a name="arm64-linux-support"></a>ARM64 Linux 支援

我們正於此版本中新增適用於 Linux 的 ARM64 支援。 針對不同內容，我們藉由 .NET Core 2.1 新增了適用於 Linux 及藉由 .NET Core 2.2 新增了適用於 Windows 的 ARM32 支援。 ARM64 的主要使用案例目前是搭配 IoT 案例。

[針對適用於 ARM64 的 .NET Core 有提供 Docker 映像](https://hub.docker.com/r/microsoft/dotnet/) (Alpine、Debian 及 Ubuntu Docker 映像)。

如需詳細資訊，請參閱 [.NET Core ARM64 狀態](https://github.com/dotnet/announcements/issues/82) \(英文\)。

>[!NOTE]
> 目前尚未提供 **ARM64** Windows 支援。
