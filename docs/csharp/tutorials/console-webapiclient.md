---
title: "使用 .NET Core 來建立 REST 用戶端"
description: "本教學課程會教導您一些 .NET Core 和 C# 語言中的功能。"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 6b0f3acc3a6dbed4f44497d92d3c518ee5a5d2a7
ms.sourcegitcommit: dd6ea7f0e581ac84e0a90d9b23c463fcf1ec3ce7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2018
---
# <a name="rest-client"></a>REST 用戶端

## <a name="introduction"></a>簡介
本教學課程會教導您一些 .NET Core 和 C# 語言中的功能。 您將了解：
*   「.NET Core 命令列介面」(CLI) 的基本概念。
*   「C# 語言」功能的概觀。
*   使用 NuGet 來管理相依性
*   HTTP 通訊
*   處理 JSON 資訊
*   使用「屬性」來管理組態。 

您將建置一個對 GitHub 上的 REST 服務發出「HTTP 要求」的應用程式。 您將讀取 JSON 格式的資訊，並將該 JSON 封包轉換成 C# 物件。 最後，您將了解如何使用 C# 物件。

本教學課程中有許多功能。 讓我們來逐一建置它們。

如果您偏好追蹤本主題的[最終範例](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-webapiclient)，則可以下載它。 如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。

## <a name="prerequisites"></a>必要條件
您將必須設定電腦以執行 .NET Core。 您可以在 [.NET Core (英文)](https://www.microsoft.com/net/core) 頁面找到安裝指示。 您可以在 Windows、Linux、macOS 或是 Docker 容器中執行此應用程式。 您將必須安裝慣用的程式碼編輯器。 以下說明使用 [Visual Studio Code (英文)](https://code.visualstudio.com/)，這是開放原始碼的跨平台編輯器。 不過，您可以使用您熟悉的任何工具。
## <a name="create-the-application"></a>建立應用程式
第一個步驟是建立新的應用程式。 請開啟命令提示字元，然後為您的應用程式建立新目錄。 使該目錄成為目前的目錄。 在命令提示字元處輸入命令 `dotnet new console`。 這會建立基本 "Hello World" 應用程式的起始檔案。

在您開始進行修改之前，讓我們先將執行簡單 Hello World 應用程式的所有步驟執行一遍。 在建立應用程式之後，在命令提示字元鍵入 `dotnet restore` ([參閱附註](#dotnet-restore-note))。 此命令會執行 NuGet 套件還原程序。 NuGet 是一個 .NET 套件管理員。 此命令會為您的專案下載任何遺漏的相依性。 由於這是一個新專案，因此沒有任何現有的相依性，所以第一次執行時將會下載 .NET Core 架構。 在這個初始步驟之後，當您新增新的相依套件或更新任何相依性的版本時，將只需要執行 `dotnet restore` ([參閱附註](#dotnet-restore-note))。  

還原套件之後，您需執行 `dotnet build`。 這會執行建置引擎並建立您的應用程式。 最後，您需執行 `dotnet run` 來執行您的應用程式。

## <a name="adding-new-dependencies"></a>新增新的相依性
.NET Core 的其中一個主要設計目標就是將 .NET Framework 安裝大小縮減到最小。 .NET Core 應用程式架構只包含 .NET 完整架構的最常見元素。 如果應用程式的某些功能需要額外的程式庫，您可以將這些相依性新增到 C# 專案檔 (\*.csproj) 中。 就我們的範例而言，您將必須新增 `System.Runtime.Serialization.Json` 套件，以便讓您的應用程式能夠處理 JSON 回應。

請開啟您的 `csproj` 專案檔。 檔案的第一行程應該顯示如下：

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

在此行之後，緊接著新增下列程式碼： 

```xml
   <ItemGroup>
      <PackageReference Include="System.Runtime.Serialization.Json" Version="4.3.0" />
   </ItemGroup> 
```
大多數程式碼編輯器都有為這些程式庫的不同版本提供完成功能。 您通常會想要使用所新增之任何套件的最新版本。 不過，請務必確保所有套件的版本都相符，此外，也與 .NET Core 應用程式架構的版本相符。

在您進行這些變更之後，應該重新執行 `dotnet restore` ([參閱附註](#dotnet-restore-note))，讓套件安裝在您的系統上。

## <a name="making-web-requests"></a>提出 Web 要求
現在您已經準備好開始從 Web 接收資料。 在此應用程式中，您將從 [GitHub API](https://developer.github.com/v3/) 讀取資訊。 讓我們在 [.NET Foundation](http://www.dotnetfoundation.org/) 的庇護下讀取專案的相關資訊。 您將從對 GitHub API 提出要求以擷取專案相關資訊著手。 您將使用的端點為：[https://api.github.com/orgs/dotnet/repos](https://api.github.com/orgs/dotnet/repos)。 您想要擷取這些專案的所有相關資訊，因此您將使用 HTTP GET 要求。
您的瀏覽器也會使用 HTTP GET 要求，因此您可以將該 URL 貼到瀏覽器中，以查看您將接收和處理的資訊。

您需使用 <xref:System.Net.Http.HttpClient> 類別來提出 Web 要求。 與所有新式 .NET API 相同，<xref:System.Net.Http.HttpClient> 針對它的長時間執行 API 只支援非同步方法。
請從建立非同步方法著手。 您將在建置應用程式的功能時填入實作。 請從開啟您專案目錄中的 `program.cs` 檔案並將下列方法新增到 `Program` 類別著手：

```csharp
private static async Task ProcessRepositories()
{
    
}
```

您將必須在 `Main` 方法上面新增 `using` 陳述式，如此 C# 編譯器才能夠辨識 <xref:System.Threading.Tasks.Task> 型別：

```csharp
using System.Threading.Tasks;
```

如果您在此時建置專案，您將會收到針對此方法產生的警告，因為它不包含任何 `await` 運算子，所以將會以同步方式執行。 目前請先忽略該警告；您將在填入方法時新增 `await` 運算子。

接著，請將 `namespace` 陳述式中定義的命名空間從其預設值 `ConsoleApp` 重新命名為 `WebAPIClient`。 我們稍後將會在此命名空間中定義 `repo` 類別。

接著，請將 `Main` 方法更新成呼叫此方法。 `ProcessRepositories` 方法會傳回一個工作，而在該工作完成之前，您不應該結束程式。 因此，您必須使用 `Wait` 方法來封鎖並等候工作完成：

```csharp
public static void Main(string[] args)
{
    ProcessRepositories().Wait();
}
```

現在，您擁有一個不會執行任何動作但會以非同步方式執行的程式。 來加以改善吧。

首先，您需要一個能夠從網路擷取資料的物件；使用 <xref:System.Net.Http.HttpClient> 即可達成。 此物件會處理要求和回應。 在 Program.cs 檔案內，將 `Program` 類別中該類型的單一執行個體具現化。

```csharp
namespace WebAPIClient
{
    class Program
    {
        private static readonly HttpClient client = new HttpClient();

        static void Main(string[] args)
        {
            //...
        }
    }
}
```

 讓我們回到 `ProcessRepositories` 方法並填入其第一個版本：

```csharp
private static async Task ProcessRepositories()
{
    client.DefaultRequestHeaders.Accept.Clear();
    client.DefaultRequestHeaders.Accept.Add(
        new MediaTypeWithQualityHeaderValue("application/vnd.github.v3+json"));
    client.DefaultRequestHeaders.Add("User-Agent", ".NET Foundation Repository Reporter");

    var stringTask = client.GetStringAsync("https://api.github.com/orgs/dotnet/repos");

    var msg = await stringTask;
    Console.Write(msg);
}
```

您將必須在檔案開頭一併新增兩個新的 using 陳述式以讓此檔案進行編譯：

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

第一個版本會提出 Web 要求來讀取 dotnet foundation 組織底下的所有儲存機制清單。 (.NET Foundation 的 gitHub 識別碼是 'dotnet')。 前幾行會為這個要求設定 <xref:System.Net.Http.HttpClient>。 首先，會將它設定為接受 GitHub JSON 回應。
此格式就是 JSON。 下一行會將「使用者代理程式」標頭新增到來自此物件的所有要求。 這兩個標頭會受到 GitHub 伺服器程式碼檢查，並且是從 GitHub 擷取資訊的必要標頭。

設定 <xref:System.Net.Http.HttpClient> 之後，您需提出 Web 要求並擷取回應。 在這個第一版中，您會使用 <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> 便利方法。 這個便利方法會啟動一個提出 Web 要求的工作，然後當要求返回時，它會讀取回應資料流並從該資料流擷取內容。 回應本文會以 <xref:System.String> 的形式傳回。 當工作完成時，就會提供該字串。 

此方法的最後兩行會等候該工作，然後將回應顯示在主控台中。
請建置應用程式並執行它。 建置警告現在已消失，因為 `ProcessRepositories` 現在確實包含 `await` 運算子。 您將會看到一長串顯示的 JSON 格式文字。   

## <a name="processing-the-json-result"></a>處理 JSON 結果

此時，您已撰寫程式碼來從 Web 伺服器擷取回應，並顯示包含在該回應中的文字。 接著，讓我們將該 JSON 回應轉換成 C# 物件。

「JSON 序列化程式」會將 JSON 資料轉匯成「C# 物件」。 您的第一個工作是定義 C# 類別型別，以包含所使用來自這個回應的資訊。 讓我們慢慢地進行建置，因此，請從包含儲存機制名稱的簡單 C# 型別著手：

```csharp
using System;

namespace WebAPIClient
{
    public class repo
    {
        public string name;
    }
}
``` 

請將上述程式碼放在名為 'repo.cs' 的新檔案中。 這個類別版本代表處理 JSON 資料的最簡單路徑。 類別名稱和成員名稱會符合 JSON 封包中使用的名稱，而不是符合下列 C# 慣例。 您將在稍後藉由提供一些其他組態屬性來修正此問題。 此類別示範了 JSON 序列化和還原序列化的另一個重要功能：並非 JSON 封包中的所有欄位都屬於此類別。
JSON 序列化程式將會忽略未包含在所要使用之類別型別中的資訊。
這個功能可讓您更容易建立只對 JSON 封包中的欄位子集有作用的型別。

現在您已經建立型別，讓我們來將它還原序列化。 您將必須建立 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 物件。 此物件必須知道針對其擷取的 JSON 封包預期的 CLR 型別。 來自 GitHub 的封包會包含一個儲存機制序列，因此 `List<repo>` 是正確的型別。 請將下列這一行新增到您的 `ProcessRepositories` 方法：

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<repo>));
```

您將使用兩個新的命名空間，因此您將必須一併新增下列程式碼：

```csharp
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
```

接著，您將使用序列化程式將 JSON 轉換成 C# 物件。 請使用以下兩行來取代對您 `ProcessRepositories` 方法中 <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> 的呼叫：

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = serializer.ReadObject(await streamTask) as List<repo>;
```

請注意，您現在使用的是 <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> 而不是 <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>。 序列化程式會使用資料流 (而不是字串) 作為其來源。 讓我們來說明上述第二行中所使用的一些 C# 語言功能。 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> 的引數是 `await` 運算式。 Await 運算式可以出現在您程式碼中幾乎任何一個地方，雖然到目前為止，您只在指派陳述式中看到它們。

其次，`as` 運算子會從編譯階段型別 `object` 轉換成 `List<repo>`。 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> 的宣告會宣告其傳回 <xref:System.Object?displayProperty=nameWithType> 類型的物件。 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> 會傳回您在加以建構時指定的類型 (在本教學課程中為 `List<repo>`)。 如果轉換並未成功，`as` 運算子就會評估為 `null`，而不是擲回例外狀況。

您差不多已經完成這個部分。 現在您已將 JSON 轉換成 C# 物件，讓我們來顯示每個儲存機制的名稱。 將下列幾行：

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

取代為：

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

編譯並執行應用程式。 它將會列印出隸屬於 .NET Foundation 的儲存機制名稱。

## <a name="controlling-serialization"></a>控制序列化

在您新增更多功能之前，讓我們先處理 `repo` 型別並讓它符合更標準的 C# 慣例。 您將透過在 `repo` 型別上加註控制「JSON 序列化程式」運作方式的「屬性」，來進行這項操作。 在您的案例中，您將使用這些屬性來定義 JSON 機碼名稱與 C# 類別及成員名稱之間的對應。 所使用的兩個屬性為 `DataContract` 屬性和 `DataMember` 屬性。 透過轉換，所有屬性類別都會以後置詞 `Attribute` 結尾。 不過，當您套用屬性時，並不需要使用該後置詞。 

`DataContract` 和 `DataMember` 屬性位於不同的程式庫中，因此您將必須把該程式庫新增到 C# 專案檔中作為相依性。 請將下列行新增到您專案檔中的 `<ItemGroup>` 區段：

```xml
<PackageReference Include="System.Runtime.Serialization.Primitives" Version="4.3.0" />
```

在您儲存檔案之後，請執行 `dotnet restore` ([參閱附註](#dotnet-restore-note)) 來擷取此套件。

接著，開啟 `repo.cs` 檔案。 讓我們變更名稱以使用「Pascal 命名法的大小寫」，並完整拼出名稱 `Repository`。 我們仍然想要將 JSON 'repo' 節點對應到這個型別，因此您將必須把 `DataContract` 屬性新增到類別宣告。 您將把該屬性的 `Name` 屬性設定為與此型別對應之 JSON 節點的名稱：

```csharp
[DataContract(Name="repo")]
public class Repository
```

<xref:System.Runtime.Serialization.DataContractAttribute> 是 <xref:System.Runtime.Serialization> 命名空間的成員，因此您將必須在檔案的開頭新增適當的 `using` 陳述式：

```csharp
using System.Runtime.Serialization;
```

您已將 `repo` 類別的名稱變更為 `Repository`，因此您將必須在 Program.cs 中進行相同的名稱變更 (有些編輯器可能支援可自動進行這項變更的重新命名重構功能)：

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<Repository>));

// ...

var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
```

接著，讓我們使用 <xref:System.Runtime.Serialization.DataMemberAttribute> 類別來以 `name` 欄位進行相同的變更。 請對 repo.cs 中 `name` 欄位的宣告進行下列變更：

```csharp
[DataMember(Name="name")]
public string Name;
```

這項變更意謂著您必須變更 program.cs 中寫入每個儲存機制名稱的程式碼：

```csharp
Console.WriteLine(repo.Name);
```

請執行 `dotnet build` 再接著執行 `dotnet run` 以確保您的對應正確。 您應該會看到與之前相同的輸出。 在處理更多來自 Web 伺服器的屬性之前，讓我們先對 `Repository` 類別再多進行一項變更。 `Name` 成員是一個可公開存取的欄位。 這並非一個理想的物件導向做法，因此讓我們將它變更成屬性。 就我們的目的而言，當取得或設定該屬性時，我們並不需要執行任何特定的程式碼，但變更成屬性可讓稍後新增這些變更變得更容易，而不會破壞使用 `Repository` 類別的任何程式碼。

請移除欄位定義，然後以[自動實作的屬性](../programming-guide/classes-and-structs/auto-implemented-properties.md)來取代它：

```csharp
public string Name { get; set; }
```

編譯器除了會產生用來儲存名稱的私用欄位之外，也會產生 `get` 和 `set` 存取子的主體。 它會類似於以下您可以手動輸入的程式碼：

```csharp
public string Name 
{ 
    get { return this._name; }
    set { this._name = value; }
}
private string _name;
```

讓我們在新增新功能之前，再多進行一項變更。 `ProcessRepositories` 方法可以執行非同步工作，然後傳回儲存機制的集合。 讓我們從該方法傳回 `List<Repository>`，並將寫入資訊的程式碼移到 `Main` 方法中。

請變更 `ProcessRepositories` 的簽章以傳回其結果為 `Repository` 物件清單的工作：

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

接著，在處理 JSON 回應後，直接傳回儲存機制：

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

編譯器會產生用於傳回的 `Task<T>` 物件，因為您已將此方法標示為 `async`。
接著，讓我們來修改 `Main` 方法，使它擷取那些結果並將每個儲存機制名稱寫入到主控台。 您的 `Main` 方法現在看起來會像這樣：

```csharp
public static void Main(string[] args)
{
    var repositories = ProcessRepositories().Result;

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

系統會封鎖存取工作之 `Result` 屬性的行為，直到工作完成為止。 通常，您會偏好 `await` 工作完成，就像在 `ProcessRepositories` 方法中一樣，但在 `Main` 方法中並不允許這樣做。

## <a name="reading-more-information"></a>讀取更多資訊

讓我們再多處理 GitHub API 所傳送之 JSON 封包中的幾個屬性，來結束這個部分。 您不會想要全盤了解，但新增幾個屬性將可示範更多一些的 C# 語言功能。

讓我們從再多將幾個簡單型別新增到 `Repository` 類別定義著手。 請將下列屬性新增到該類別：

```csharp
[DataMember(Name="description")]
public string Description { get; set; }

[DataMember(Name="html_url")]
public Uri GitHubHomeUrl { get; set; }

[DataMember(Name="homepage")]
public Uri Homepage { get; set; }

[DataMember(Name="watchers")]
public int Watchers { get; set; }
```

這些屬性具有從字串型別 (JSON 封包所包含的型別) 轉換成目標型別的內建轉換。 您可能不熟悉 <xref:System.Uri> 型別。 它代表 URI，或在此案例中是代表 URL。 在 `Uri` 和 `int` 型別的案例中，如果 JSON 封包包含不會轉換成目標型別的資料，序列化動作將會擲回例外狀況。

在您新增這些屬性之後，請更新 `Main` 方法以顯示下列元素：

```csharp
foreach (var repo in repositories)
{
    Console.WriteLine(repo.Name);
    Console.WriteLine(repo.Description);
    Console.WriteLine(repo.GitHubHomeUrl);
    Console.WriteLine(repo.Homepage);
    Console.WriteLine(repo.Watchers);
    Console.WriteLine();
}
```
在最後一個步驟中，讓我們新增最後一個推送作業的資訊。 此資訊會在 JSON 回應中採用下列形式的格式：

```json
2016-02-08T21:27:00Z
```

該格式並不符合任何標準 .NET <xref:System.DateTime> 格式。 因此，您將需要撰寫一個自訂的轉換方法。 您可能也不會想要對 `Repository` 類別的使用者公開原始字串。 屬性也可以幫助控制該行為。 首先，請定義 `private` 屬性，此屬性將保存您 `Repository` 類別中日期時間的字串表示：

```csharp
[DataMember(Name="pushed_at")]
private string JsonDate { get; set; }
```

`DataMember` 屬性會通知序列化程式應該處理此屬性，即使它並非公用成員。 接著，您需要撰寫一個公用的唯讀屬性來將字串轉換成有效的 <xref:System.DateTime> 物件，並傳回該 <xref:System.DateTime>：

```csharp
[IgnoreDataMember]
public DateTime LastPush
{
    get
    {
        return DateTime.ParseExact(JsonDate, "yyyy-MM-ddTHH:mm:ssZ", CultureInfo.InvariantCulture);
    }
}
```

讓我們來檢查上述的新建構。 `IgnoreDataMember` 屬性會指示序列化程式不應該將此型別讀取到任何 JSON 物件，或從任何 JSON 物件寫入此型別。 此屬性只包含 `get` 存取子。 沒有 `set` 存取子。 這就是您以 C# 定義「唯讀」屬性的方式。 (是的，您可以用 C# 來建立「唯寫」屬性，但其值會受到限制)。<xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> 方法會剖析字串並使用提供的日期格式來建立 <xref:System.DateTime> 物件，然後使用 `CultureInfo` 物件為 `DateTime` 新增額外的中繼資料。 如果剖析作業失敗，屬性存取子就會擲回例外狀況。

若要使用 <xref:System.Globalization.CultureInfo.InvariantCulture> ，您將必須把 <xref:System.Globalization> 命名空間新增到 `repo.cs` 中的 `using` 陳述式：

```csharp
using System.Globalization;
```

最後，請在主控台中再多新增一個輸出陳述式，這樣您便已準備好來重新建置及執行此應用程式：

```csharp
Console.WriteLine(repo.LastPush);
```

您的版本現在應該與[完成範例](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-webapiclient)相符。
 
## <a name="conclusion"></a>結論

本教學課程示範了如何提出 Web 要求、剖析結果，以及顯示這些結果的屬性。 您也在專案中新增了新的套件作為相依性。 您已了解一些支援物件導向技術的 C# 語言功能。

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
