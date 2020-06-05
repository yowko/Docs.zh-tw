---
title: 資料存取和管理
description: 瞭解如何存取和處理 ASP.NET Web Forms 和 Blazor 中的資料。
author: csharpfritz
ms.author: jefritz
ms.date: 04/26/2020
ms.openlocfilehash: b9805da60722de1b5d4f91107e856f647f7564a7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446468"
---
# <a name="work-with-data"></a>使用資料

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

資料存取是 ASP.NET Web Forms 應用程式的骨幹。 如果您要建立 web 表單，該資料會如何？ 使用 Web Forms 時，您可以使用多種資料存取技術來與資料庫互動：

- Data Sources
- ADO.NET
- Entity Framework

資料來源是您可以放置在 Web form 頁面上的控制項，而且設定起來就像其他控制項一樣。 Visual Studio 提供了一組易記的對話方塊，可設定控制項並將其系結至您的 Web form 頁面。 使用「低程式碼」或「無程式碼」方法的開發人員，在第一次發行 Web 表單時偏好這項技巧。

![Data Sources](media/data/datasources.png)

ADO.NET 是與資料庫互動的低層級方法。 您的應用程式可以使用命令、記錄集和資料集來建立與資料庫的連接，以進行互動。 結果可能會系結至螢幕上的欄位，而不需要大量程式碼。 這種方法的缺點是每一組 ADO.NET 物件（ `Connection` 、 `Command` 和）都已系結 `Recordset` 至資料庫廠商所提供的程式庫。 使用這些元件會使程式碼變得更嚴格，而且不容易遷移到不同的資料庫。

## <a name="entity-framework"></a>Entity Framework

Entity Framework （EF）是 .NET Foundation 所維護的開放原始碼物件關聯式對應架構。 EF 一開始是使用 .NET Framework 發行，可讓您產生資料庫連接、儲存架構和互動的程式碼。 使用此抽象概念，您可以專注于應用程式的商務規則，並允許受信任的資料庫管理員管理資料庫。 在 .NET Core 中，您可以使用名為 EF Core 的 EF 更新版本。 EF Core 使用命令列工具提供一系列的命令，協助產生和維護您的程式碼與資料庫之間的互動 `dotnet ef` 。 我們來看一下幾個範例，讓您使用資料庫。

### <a name="ef-code-first"></a>EF Code First

開始建立資料庫互動的快速方法，就是從您想要使用的類別物件著手。 EF 提供工具來協助為您的類別產生適當的資料庫程式碼。 這種方法稱為「Code First」開發。 `Product`針對我們想要在 Microsoft SQL Server 之類的關係資料庫中儲存的範例店面應用程式，請考慮下列類別。

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

產品具有主鍵和三個額外的欄位，會在資料庫中建立：  

- EF 會依照 `Id` 慣例將屬性識別為主鍵。
- `Name`將儲存在針對文字儲存所設定的資料行中。 `[Required]`裝飾這個屬性的屬性將會加入 `not null` 條件約束，以協助強制執行此屬性的宣告行為。
- `Description`會儲存在針對文字儲存所設定的資料行中，且最大長度設定為屬性所規定的4000個字元 `[MaxLength]` 。 系統會使用資料類型，將資料庫架構設定為具有名為的 `MaxLength` 資料行 `varchar(4000)` 。
- `Price`屬性會儲存為貨幣。 `[Range]`屬性會產生適當的條件約束，以防止在宣告的最小和最大值以外的資料儲存。

我們需要將這個 `Product` 類別新增至資料庫內容類別，以定義資料庫的連接和轉譯作業。

```csharp
public class MyDbContext : DbContext
{
    public DbSet<Product> Products { get; set; }
}
```

`MyDbContext`類別提供一個屬性，可定義類別的存取和轉譯 `Product` 。  您的應用程式會使用類別的方法中的下列專案，設定此類別以與資料庫互動 `Startup` `ConfigureServices` ：

```csharp
services.AddDbContext<MyDbContext>(options =>
    options.UseSqlServer("MY DATABASE CONNECTION STRING"));
```

上述程式碼會使用指定的連接字串連接到 SQL Server 資料庫。 您可以將連接字串放在*appsettings*檔案、環境變數或其他設定儲存位置，並適當地取代此內嵌字串。

接著，您可以使用下列命令，產生適用于此類別的資料庫資料表：

```dotnetcli
dotnet ef migrations add 'Create Product table'
dotnet ef database update
```

第一個命令會定義您要對資料庫架構進行的變更，做為名為的新 EF 遷移 `Create Product table` 。  「遷移」會定義如何套用和移除新的資料庫變更。

套用之後，您就可以 `Product` 在資料庫中使用簡單的資料表，並在專案中加入可協助管理資料庫架構的一些新類別。  根據預設，您可以在稱為「*遷移*」的新資料夾中找到這些產生的類別。  當您對類別進行變更 `Product` ，或新增更多相關類別來與資料庫互動時，您需要使用新的遷移名稱再次執行命令列命令。  此命令會產生另一組遷移類別，以更新您的資料庫架構。

### <a name="ef-database-first"></a>EF Database First

針對現有的資料庫，您可以使用 .NET 命令列工具來產生 EF Core 的類別。 若要 scaffold 類別，請使用下列命令的變化：

```dotnetcli
dotnet ef dbcontext scaffold "CONNECTION STRING" Microsoft.EntityFrameworkCore.SqlServer -c MyDbContext -t Product -t Customer
```

上述命令會使用指定的連接字串和提供者連接到資料庫 `Microsoft.EntityFrameworkCore.SqlServer` 。 一旦連接之後，就會建立名為的資料庫內容類別 `MyDbContext` 。 此外，也會針對 `Product` 使用選項所指定的和資料表，建立支援的類別 `Customer` `-t` 。 此命令有許多設定選項可產生適用于您資料庫的類別階層。 如需完整的參考，請參閱[命令的檔](/ef/core/miscellaneous/cli/dotnet#dotnet-ef-dbcontext-scaffold)。

如需[EF Core](/ef/core/)的詳細資訊，請參閱 Microsoft Docs 網站。

## <a name="interact-with-web-services"></a>與 web 服務互動

第一次發行 ASP.NET 時，SOAP 服務是 web 伺服器和用戶端交換資料的慣用方式。 自該時間以來已經變更過許多，而且與服務的慣用互動已轉移至直接的 HTTP 用戶端互動。 使用 ASP.NET Core 和 Blazor，您可以 `HttpClient` 在 `Startup` 類別的方法中註冊的設定 `ConfigureServices` 。 當您需要與 HTTP 端點互動時，請使用該設定。 請考慮下列設定程式碼：

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

每當您需要從 GitHub 存取資料時，請建立名稱為的用戶端 `github` 。 用戶端是以基底位址設定，而且要求標頭會適當地設定。 使用指示詞 `IHttpClientFactory` `@inject` 或屬性上的屬性，將插入至您的 Blazor 元件 `[Inject]` 。 建立您的命名用戶端，並使用下列語法與服務互動：

```razor
@inject IHttpClientFactory factory

...

@code {
    protected override async Task OnInitializedAsync()
    {
        var client = factory.CreateClient("github");
        var response = await client.GetAsync("repos/dotnet/docs/issues");
        response.EnsureStatusCode();
        var content = async response.Content.ReadAsStringAsync();
    }
}
```

這個方法會傳回描述*dotnet/* 檔 GitHub 存放庫中的問題集合的字串。 它會以 JSON 格式傳回內容，並將其還原序列化為適當的 GitHub 問題物件。 有許多方式可讓您設定 `HttpClientFactory` 來傳遞預先設定的 `HttpClient` 物件。 請嘗試 `HttpClient` 針對您使用的各種 web 服務，使用不同的名稱和端點來設定多個實例。 這種方法可讓您與這些服務的互動更容易在每個頁面上使用。 如需詳細資訊，請閱讀[IHttpClientFactory 的檔](/aspnet/core/fundamentals/http-requests)。

>[!div class="step-by-step"]
>[上一個](forms-validation.md) 
>[下一步](middleware.md)
