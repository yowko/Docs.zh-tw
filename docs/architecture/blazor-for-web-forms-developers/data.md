---
title: 資料存取與管理
description: 瞭解如何在 ASP.NET Web Forms 和中存取和處理資料 Blazor 。
author: csharpfritz
ms.author: jefritz
no-loc:
- Blazor
ms.date: 11/20/2020
ms.openlocfilehash: 66e6001cbcac612cb556e90fb86fd694ca7d1459
ms.sourcegitcommit: 2f485e721f7f34b87856a51181b5b56624b31fd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2020
ms.locfileid: "96509750"
---
# <a name="work-with-data"></a>使用資料

資料存取是 ASP.NET Web Forms 應用程式的骨幹。 如果您正在建立 web 的表單，該資料會發生什麼事？ 有了 Web Form，您可以使用多個資料存取技術來與資料庫互動：

- 資料來源
- ADO.NET
- Entity Framework

資料來源是您可以放在 Web Form 頁面上的控制項，並設定為與其他控制項一樣。 Visual Studio 提供一組易記的對話方塊來設定控制項，並將其系結至您的 Web Form 頁面。 在第一次發行 Web Form 時，享受「低程式碼」或「無程式碼」方法的開發人員偏好使用此技巧。

![資料來源](media/data/datasources.png)

ADO.NET 是與資料庫互動的低層級方法。 您的應用程式可以使用命令、記錄集和資料集來建立與資料庫的連接，以進行互動。 然後可以將結果系結至畫面上的欄位，而不需要太多程式碼。 這種方法的缺點是，每一組 ADO.NET 物件 (`Connection` 、 `Command` 和) 系結 `Recordset` 至資料庫供應商所提供的程式庫。 使用這些元件使程式碼變得固定，而且難以遷移至不同的資料庫。

## <a name="entity-framework"></a>Entity Framework

Entity Framework (EF) 是 .NET Foundation 所維護的開放原始碼物件關聯式對應架構。 EF 一開始會使用 .NET Framework，可讓您針對資料庫連接、儲存架構和互動產生程式碼。 您可以使用此抽象概念，將焦點放在應用程式的商務規則，並允許受信任的資料庫管理員管理資料庫。 在 .NET 中，您可以使用名為 EF Core 的 EF 更新版。 EF Core 有助於使用命令列工具來產生和維護您的程式碼與資料庫之間的互動，以及一系列可供您使用的命令 `dotnet ef` 。 讓我們來看看一些範例，讓您使用資料庫。

### <a name="ef-code-first"></a>EF Code First

開始建立資料庫互動的快速方法，就是從您想要使用的類別物件開始著手。 EF 提供的工具可協助您為類別產生適當的資料庫程式碼。 這種方法稱為「Code First」開發。 `Product`針對我們想要儲存在關係資料庫（例如 Microsoft SQL Server）的範例店面應用程式，請考慮下列類別。

```csharp
public class Product
{
    public int Id { get; set; }

    [Required]
    public string Name { get; set; }

    [MaxLength(4000)]
    public string Description { get; set; }

    [Range(0, 99999,99)]
    [DataType(DataType.Currency)]
    public decimal Price { get; set; }
}
```

產品有一個主要金鑰和三個額外的欄位，會在資料庫中建立：  

- EF 會依照 `Id` 慣例將屬性識別為主鍵。
- `Name` 將儲存在設定為文字儲存的資料行中。 `[Required]`裝飾這個屬性的屬性會加入 `not null` 條件約束，以協助強制執行此屬性的宣告行為。
- `Description` 會儲存在設定為文字儲存的資料行中，並具有設定為4000個字元的最大長度（由屬性所規定） `[MaxLength]` 。 資料庫架構會設定為 `MaxLength` 使用資料類型的資料行 `varchar(4000)` 。
- `Price`屬性將會儲存為貨幣。 `[Range]`屬性會產生適當的條件約束，以防止在宣告的最小值和最大值以外的資料儲存。

我們必須將這個 `Product` 類別新增至資料庫內容類別，以定義資料庫的連接和轉譯作業。

```csharp
public class MyDbContext : DbContext
{
    public DbSet<Product> Products { get; set; }
}
```

`MyDbContext`類別會提供一個屬性，以定義類別的存取和轉譯 `Product` 。  您的應用程式會使用類別的方法中的下列專案，將此類別設定為與資料庫互動 `Startup` `ConfigureServices` ：

```csharp
services.AddDbContext<MyDbContext>(options =>
    options.UseSqlServer("MY DATABASE CONNECTION STRING"));
```

上述程式碼會連接到具有指定連接字串的 SQL Server 資料庫。 您可以將連接字串放在檔案、環境變數或其他設定儲存位置的 *appsettings.js* 中，並適當地取代此內嵌字串。

然後，您可以使用下列命令來產生適用于此類別的資料庫資料表：

```dotnetcli
dotnet ef migrations add 'Create Product table'
dotnet ef database update
```

第一個命令會將您對資料庫架構所做的變更定義為新的 EF 遷移，稱為 `Create Product table` 。  遷移會定義如何套用和移除新的資料庫變更。

套用之後，您的資料庫中就會有一個簡單的 `Product` 資料表，並在專案中加入一些新的類別，以協助管理資料庫架構。  根據預設，您可以在稱為「 *遷移*」的新資料夾中找到這些產生的類別。  當您變更 `Product` 類別，或新增更多相關類別來與資料庫互動時，您需要使用新的遷移名稱再次執行命令列命令。  此命令會產生另一組遷移類別，以更新您的資料庫架構。

### <a name="ef-database-first"></a>EF Database First

針對現有的資料庫，您可以使用 .NET 命令列工具來產生 EF Core 的類別。 若要 scaffold 類別，請使用下列命令的變化：

```dotnetcli
dotnet ef dbcontext scaffold "CONNECTION STRING" Microsoft.EntityFrameworkCore.SqlServer -c MyDbContext -t Product -t Customer
```

上述命令會使用指定的連接字串和提供者連接到資料庫 `Microsoft.EntityFrameworkCore.SqlServer` 。 連接之後，就會建立名為的資料庫內容類別 `MyDbContext` 。 此外，也會為 `Product` 使用選項指定的和資料表建立支援的類別 `Customer` `-t` 。 此命令有許多設定選項，可產生適用于您資料庫的類別階層。 如需完整的參考，請參閱 [命令的檔](/ef/core/miscellaneous/cli/dotnet#dotnet-ef-dbcontext-scaffold)。

如需有關 [EF Core](/ef/core/) 的詳細資訊，請參閱 Microsoft Docs 網站。

## <a name="interact-with-web-services"></a>與 web 服務互動

當 ASP.NET 首次發行時，SOAP 服務是 web 伺服器和用戶端用來交換資料的慣用方式。 自該時間以來，已有許多變更，而與服務的慣用互動已轉移至直接的 HTTP 用戶端互動。 您可以使用 ASP.NET Core 和 Blazor ， `HttpClient` 在 `Startup` 類別的方法中註冊的設定 `ConfigureServices` 。 當您需要與 HTTP 端點互動時，請使用該設定。 請考慮下列設定程式碼：

```csharp
services.AddHttpClient("github", client =>
{
    client.BaseAddress = new Uri("http://api.github.com/");
    // Github API versioning
    client.DefaultRequestHeaders.Add("Accept", "application/vnd.github.v3+json");
    // Github requires a user-agent
    client.DefaultRequestHeaders.Add("User-Agent", "BlazorWebForms-Sample");
});
```

每當您需要從 GitHub 存取資料時，請建立名稱為的用戶端 `github` 。 用戶端是使用基底位址設定的，而且要求標頭會適當地設定。 使用指示詞 `IHttpClientFactory` Blazor `@inject` 或屬性（attribute）將插入您的元件 `[Inject]` 。 建立您的命名用戶端，並使用下列語法與服務互動：

```razor
@inject IHttpClientFactory factory

...

@code {
    protected override async Task OnInitializedAsync()
    {
        var client = factory.CreateClient("github");
        var response = await client.GetAsync("repos/dotnet/docs/issues");
        response.EnsureStatusCode();
        var content = await response.Content.ReadAsStringAsync();
    }
}
```

這個方法會傳回描述 *dotnet/* 檔 GitHub 存放庫中問題集合的字串。 它會以 JSON 格式傳回內容，並將其還原序列化為適當的 GitHub 問題物件。 有許多方式可讓您設定 `HttpClientFactory` 以傳遞預先設定的 `HttpClient` 物件。 請嘗試使用 `HttpClient` 不同的名稱和端點來設定多個實例，以供您使用的各種 web 服務使用。 這種方法可讓您與這些服務的互動更容易在每個頁面上使用。 如需詳細資訊，請參閱 [IHttpClientFactory 的檔](/aspnet/core/fundamentals/http-requests)。

>[!div class="step-by-step"]
>[上一個](forms-validation.md) 
>[下一步](middleware.md)
