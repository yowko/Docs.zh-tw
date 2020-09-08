---
title: 資料存取與管理
description: 瞭解如何在 ASP.NET Web Forms 和中存取和處理資料 Blazor 。
author: csharpfritz
ms.author: jefritz
no-loc:
- Blazor
ms.date: 09/08/2020
ms.openlocfilehash: 84e12f9890351fa46cd7ed0ee31db449f3c55e59
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89515848"
---
# <a name="work-with-data"></a><span data-ttu-id="418f3-103">使用資料</span><span class="sxs-lookup"><span data-stu-id="418f3-103">Work with data</span></span>

<span data-ttu-id="418f3-104">資料存取是 ASP.NET Web Forms 應用程式的骨幹。</span><span class="sxs-lookup"><span data-stu-id="418f3-104">Data access is the backbone of an ASP.NET Web Forms app.</span></span> <span data-ttu-id="418f3-105">如果您正在建立 web 的表單，該資料會發生什麼事？</span><span class="sxs-lookup"><span data-stu-id="418f3-105">If you're building forms for the web, what happens to that data?</span></span> <span data-ttu-id="418f3-106">有了 Web Form，您可以使用多個資料存取技術來與資料庫互動：</span><span class="sxs-lookup"><span data-stu-id="418f3-106">With Web Forms, there were multiple data access techniques you could use to interact with a database:</span></span>

- <span data-ttu-id="418f3-107">資料來源</span><span class="sxs-lookup"><span data-stu-id="418f3-107">Data Sources</span></span>
- <span data-ttu-id="418f3-108">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="418f3-108">ADO.NET</span></span>
- <span data-ttu-id="418f3-109">Entity Framework</span><span class="sxs-lookup"><span data-stu-id="418f3-109">Entity Framework</span></span>

<span data-ttu-id="418f3-110">資料來源是您可以放在 Web Form 頁面上的控制項，並設定為與其他控制項一樣。</span><span class="sxs-lookup"><span data-stu-id="418f3-110">Data Sources were controls that you could place on a Web Forms page and configure like other controls.</span></span> <span data-ttu-id="418f3-111">Visual Studio 提供一組易記的對話方塊來設定控制項，並將其系結至您的 Web Form 頁面。</span><span class="sxs-lookup"><span data-stu-id="418f3-111">Visual Studio provided a friendly set of dialogs to configure and bind the controls to your Web Forms pages.</span></span> <span data-ttu-id="418f3-112">在第一次發行 Web Form 時，享受「低程式碼」或「無程式碼」方法的開發人員偏好使用此技巧。</span><span class="sxs-lookup"><span data-stu-id="418f3-112">Developers who enjoy a "low code" or "no code" approach preferred this technique when Web Forms was first released.</span></span>

![資料來源](media/data/datasources.png)

<span data-ttu-id="418f3-114">ADO.NET 是與資料庫互動的低層級方法。</span><span class="sxs-lookup"><span data-stu-id="418f3-114">ADO.NET is the low-level approach to interacting with a database.</span></span> <span data-ttu-id="418f3-115">您的應用程式可以使用命令、記錄集和資料集來建立與資料庫的連接，以進行互動。</span><span class="sxs-lookup"><span data-stu-id="418f3-115">Your apps could create a connection to the database with Commands, Recordsets, and Datasets for interacting.</span></span> <span data-ttu-id="418f3-116">然後可以將結果系結至畫面上的欄位，而不需要太多程式碼。</span><span class="sxs-lookup"><span data-stu-id="418f3-116">The results could then be bound to fields on screen without much code.</span></span> <span data-ttu-id="418f3-117">這種方法的缺點是，每一組 ADO.NET 物件 (`Connection` 、 `Command` 和) 系結 `Recordset` 至資料庫供應商所提供的程式庫。</span><span class="sxs-lookup"><span data-stu-id="418f3-117">The drawback of this approach was that each set of ADO.NET objects (`Connection`, `Command`, and `Recordset`) was bound to libraries provided by a database vendor.</span></span> <span data-ttu-id="418f3-118">使用這些元件使程式碼變得固定，而且難以遷移至不同的資料庫。</span><span class="sxs-lookup"><span data-stu-id="418f3-118">Use of these components made the code rigid and difficult to migrate to a different database.</span></span>

## <a name="entity-framework"></a><span data-ttu-id="418f3-119">Entity Framework</span><span class="sxs-lookup"><span data-stu-id="418f3-119">Entity Framework</span></span>

<span data-ttu-id="418f3-120">Entity Framework (EF) 是 .NET Foundation 所維護的開放原始碼物件關聯式對應架構。</span><span class="sxs-lookup"><span data-stu-id="418f3-120">Entity Framework (EF) is the open source object-relational mapping framework maintained by the .NET Foundation.</span></span> <span data-ttu-id="418f3-121">EF 一開始會使用 .NET Framework，可讓您針對資料庫連接、儲存架構和互動產生程式碼。</span><span class="sxs-lookup"><span data-stu-id="418f3-121">Initially released with .NET Framework, EF allows for generating code for the database connections, storage schemas, and interactions.</span></span> <span data-ttu-id="418f3-122">您可以使用此抽象概念，將焦點放在應用程式的商務規則，並允許受信任的資料庫管理員管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="418f3-122">With this abstraction, you can focus on your app's business rules and allow the database to be managed by a trusted database administrator.</span></span> <span data-ttu-id="418f3-123">在 .NET Core 中，您可以使用名為 EF Core 的 EF 更新版。</span><span class="sxs-lookup"><span data-stu-id="418f3-123">In .NET Core, you can use an updated version of EF called EF Core.</span></span> <span data-ttu-id="418f3-124">EF Core 有助於使用命令列工具來產生和維護您的程式碼與資料庫之間的互動，以及一系列可供您使用的命令 `dotnet ef` 。</span><span class="sxs-lookup"><span data-stu-id="418f3-124">EF Core helps generate and maintain the interactions between your code and the database with a series of commands that are available for you using the `dotnet ef` command-line tool.</span></span> <span data-ttu-id="418f3-125">讓我們來看看一些範例，讓您使用資料庫。</span><span class="sxs-lookup"><span data-stu-id="418f3-125">Let's take a look at a few samples to get you working with a database.</span></span>

### <a name="ef-code-first"></a><span data-ttu-id="418f3-126">EF Code First</span><span class="sxs-lookup"><span data-stu-id="418f3-126">EF Code First</span></span>

<span data-ttu-id="418f3-127">開始建立資料庫互動的快速方法，就是從您想要使用的類別物件開始著手。</span><span class="sxs-lookup"><span data-stu-id="418f3-127">A quick way to get started building your database interactions is to start with the class objects you want to work with.</span></span> <span data-ttu-id="418f3-128">EF 提供的工具可協助您為類別產生適當的資料庫程式碼。</span><span class="sxs-lookup"><span data-stu-id="418f3-128">EF provides a tool to help generate the appropriate database code for your classes.</span></span> <span data-ttu-id="418f3-129">這種方法稱為「Code First」開發。</span><span class="sxs-lookup"><span data-stu-id="418f3-129">This approach is called "Code First" development.</span></span> <span data-ttu-id="418f3-130">`Product`針對我們想要儲存在關係資料庫（例如 Microsoft SQL Server）的範例店面應用程式，請考慮下列類別。</span><span class="sxs-lookup"><span data-stu-id="418f3-130">Consider the following `Product` class for a sample storefront app that we want to store in a relational database like Microsoft SQL Server.</span></span>

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

<span data-ttu-id="418f3-131">產品有一個主要金鑰和三個額外的欄位，會在資料庫中建立：</span><span class="sxs-lookup"><span data-stu-id="418f3-131">Product has a primary key and three additional fields that would be created in our database:</span></span>  

- <span data-ttu-id="418f3-132">EF 會依照 `Id` 慣例將屬性識別為主鍵。</span><span class="sxs-lookup"><span data-stu-id="418f3-132">EF will identify the `Id` property as a primary key by convention.</span></span>
- <span data-ttu-id="418f3-133">`Name` 將儲存在設定為文字儲存的資料行中。</span><span class="sxs-lookup"><span data-stu-id="418f3-133">`Name` will be stored in a column configured for text storage.</span></span> <span data-ttu-id="418f3-134">`[Required]`裝飾這個屬性的屬性會加入 `not null` 條件約束，以協助強制執行此屬性的宣告行為。</span><span class="sxs-lookup"><span data-stu-id="418f3-134">The `[Required]` attribute decorating this property will add a `not null` constraint to help enforce this declared behavior of the property.</span></span>
- <span data-ttu-id="418f3-135">`Description` 會儲存在設定為文字儲存的資料行中，並具有設定為4000個字元的最大長度（由屬性所規定） `[MaxLength]` 。</span><span class="sxs-lookup"><span data-stu-id="418f3-135">`Description` will be stored in a column configured for text storage, and have a maximum length configured of 4000 characters as dictated by the `[MaxLength]` attribute.</span></span> <span data-ttu-id="418f3-136">資料庫架構會設定為 `MaxLength` 使用資料類型的資料行 `varchar(4000)` 。</span><span class="sxs-lookup"><span data-stu-id="418f3-136">The database schema will be configured with a column named `MaxLength` using data type `varchar(4000)`.</span></span>
- <span data-ttu-id="418f3-137">`Price`屬性將會儲存為貨幣。</span><span class="sxs-lookup"><span data-stu-id="418f3-137">The `Price` property will be stored as currency.</span></span> <span data-ttu-id="418f3-138">`[Range]`屬性會產生適當的條件約束，以防止在宣告的最小值和最大值以外的資料儲存。</span><span class="sxs-lookup"><span data-stu-id="418f3-138">The `[Range]` attribute will generate appropriate constraints to prevent data storage outside of the minimum and maximum values declared.</span></span>

<span data-ttu-id="418f3-139">我們必須將這個 `Product` 類別新增至資料庫內容類別，以定義資料庫的連接和轉譯作業。</span><span class="sxs-lookup"><span data-stu-id="418f3-139">We need to add this `Product` class to a database context class that defines the connection and translation operations with our database.</span></span>

```csharp
public class MyDbContext : DbContext
{
    public DbSet<Product> Products { get; set; }
}
```

<span data-ttu-id="418f3-140">`MyDbContext`類別會提供一個屬性，以定義類別的存取和轉譯 `Product` 。</span><span class="sxs-lookup"><span data-stu-id="418f3-140">The `MyDbContext` class provides the one property that defines the access and translation for the `Product` class.</span></span>  <span data-ttu-id="418f3-141">您的應用程式會使用類別的方法中的下列專案，將此類別設定為與資料庫互動 `Startup` `ConfigureServices` ：</span><span class="sxs-lookup"><span data-stu-id="418f3-141">Your application configures this class for interaction with the database using the following entries in the `Startup` class's `ConfigureServices` method:</span></span>

```csharp
services.AddDbContext<MyDbContext>(options =>
    options.UseSqlServer("MY DATABASE CONNECTION STRING"));
```

<span data-ttu-id="418f3-142">上述程式碼會連接到具有指定連接字串的 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="418f3-142">The preceding code will connect to a SQL Server database with the specified connection string.</span></span> <span data-ttu-id="418f3-143">您可以將連接字串放在檔案、環境變數或其他設定儲存位置的 *appsettings.js* 中，並適當地取代此內嵌字串。</span><span class="sxs-lookup"><span data-stu-id="418f3-143">You can place the connection string in your *appsettings.json* file, environment variables, or other configuration storage locations and replace this embedded string appropriately.</span></span>

<span data-ttu-id="418f3-144">然後，您可以使用下列命令來產生適用于此類別的資料庫資料表：</span><span class="sxs-lookup"><span data-stu-id="418f3-144">You can then generate the database table appropriate for this class using the following commands:</span></span>

```dotnetcli
dotnet ef migrations add 'Create Product table'
dotnet ef database update
```

<span data-ttu-id="418f3-145">第一個命令會將您對資料庫架構所做的變更定義為新的 EF 遷移，稱為 `Create Product table` 。</span><span class="sxs-lookup"><span data-stu-id="418f3-145">The first command defines the changes you're making to the database schema as a new EF Migration called `Create Product table`.</span></span>  <span data-ttu-id="418f3-146">遷移會定義如何套用和移除新的資料庫變更。</span><span class="sxs-lookup"><span data-stu-id="418f3-146">A Migration defines how to apply and remove your new database changes.</span></span>

<span data-ttu-id="418f3-147">套用之後，您的資料庫中就會有一個簡單的 `Product` 資料表，並在專案中加入一些新的類別，以協助管理資料庫架構。</span><span class="sxs-lookup"><span data-stu-id="418f3-147">Once applied, you have a simple `Product` table in your database and some new classes added to the project that help manage the database schema.</span></span>  <span data-ttu-id="418f3-148">根據預設，您可以在稱為「 *遷移*」的新資料夾中找到這些產生的類別。</span><span class="sxs-lookup"><span data-stu-id="418f3-148">You can find these generated classes, by default, in a new folder called *Migrations*.</span></span>  <span data-ttu-id="418f3-149">當您變更 `Product` 類別，或新增更多相關類別來與資料庫互動時，您需要使用新的遷移名稱再次執行命令列命令。</span><span class="sxs-lookup"><span data-stu-id="418f3-149">When you make changes to the `Product` class or add more related classes you would like interacting with your database, you need to run the command-line commands again with a new name of the migration.</span></span>  <span data-ttu-id="418f3-150">此命令會產生另一組遷移類別，以更新您的資料庫架構。</span><span class="sxs-lookup"><span data-stu-id="418f3-150">This command will generate another set of migration classes to update your database schema.</span></span>

### <a name="ef-database-first"></a><span data-ttu-id="418f3-151">EF Database First</span><span class="sxs-lookup"><span data-stu-id="418f3-151">EF Database First</span></span>

<span data-ttu-id="418f3-152">針對現有的資料庫，您可以使用 .NET 命令列工具來產生 EF Core 的類別。</span><span class="sxs-lookup"><span data-stu-id="418f3-152">For existing databases, you can generate the classes for EF Core by using the .NET command-line tools.</span></span> <span data-ttu-id="418f3-153">若要 scaffold 類別，請使用下列命令的變化：</span><span class="sxs-lookup"><span data-stu-id="418f3-153">To scaffold the classes, use a variation of the following command:</span></span>

```dotnetcli
dotnet ef dbcontext scaffold "CONNECTION STRING" Microsoft.EntityFrameworkCore.SqlServer -c MyDbContext -t Product -t Customer
```

<span data-ttu-id="418f3-154">上述命令會使用指定的連接字串和提供者連接到資料庫 `Microsoft.EntityFrameworkCore.SqlServer` 。</span><span class="sxs-lookup"><span data-stu-id="418f3-154">The preceding command connects to the database using the specified connection string and the `Microsoft.EntityFrameworkCore.SqlServer` provider.</span></span> <span data-ttu-id="418f3-155">連接之後，就會建立名為的資料庫內容類別 `MyDbContext` 。</span><span class="sxs-lookup"><span data-stu-id="418f3-155">Once connected, a database context class named `MyDbContext` is created.</span></span> <span data-ttu-id="418f3-156">此外，也會為 `Product` 使用選項指定的和資料表建立支援的類別 `Customer` `-t` 。</span><span class="sxs-lookup"><span data-stu-id="418f3-156">Additionally, supporting classes are created for the `Product` and `Customer` tables that were specified with the `-t` options.</span></span> <span data-ttu-id="418f3-157">此命令有許多設定選項，可產生適用于您資料庫的類別階層。</span><span class="sxs-lookup"><span data-stu-id="418f3-157">There are many configuration options for this command to generate the class hierarchy appropriate for your database.</span></span> <span data-ttu-id="418f3-158">如需完整的參考，請參閱 [命令的檔](/ef/core/miscellaneous/cli/dotnet#dotnet-ef-dbcontext-scaffold)。</span><span class="sxs-lookup"><span data-stu-id="418f3-158">For a complete reference, see [the command's documentation](/ef/core/miscellaneous/cli/dotnet#dotnet-ef-dbcontext-scaffold).</span></span>

<span data-ttu-id="418f3-159">如需有關 [EF Core](/ef/core/) 的詳細資訊，請參閱 Microsoft Docs 網站。</span><span class="sxs-lookup"><span data-stu-id="418f3-159">More information about [EF Core](/ef/core/) can be found on the Microsoft Docs site.</span></span>

## <a name="interact-with-web-services"></a><span data-ttu-id="418f3-160">與 web 服務互動</span><span class="sxs-lookup"><span data-stu-id="418f3-160">Interact with web services</span></span>

<span data-ttu-id="418f3-161">當 ASP.NET 首次發行時，SOAP 服務是 web 伺服器和用戶端用來交換資料的慣用方式。</span><span class="sxs-lookup"><span data-stu-id="418f3-161">When ASP.NET was first released, SOAP services were the preferred way for web servers and clients to exchange data.</span></span> <span data-ttu-id="418f3-162">自該時間以來，已有許多變更，而與服務的慣用互動已轉移至直接的 HTTP 用戶端互動。</span><span class="sxs-lookup"><span data-stu-id="418f3-162">Much has changed since that time, and the preferred interactions with services have shifted to direct HTTP client interactions.</span></span> <span data-ttu-id="418f3-163">您可以使用 ASP.NET Core 和 Blazor ， `HttpClient` 在 `Startup` 類別的方法中註冊的設定 `ConfigureServices` 。</span><span class="sxs-lookup"><span data-stu-id="418f3-163">With ASP.NET Core and Blazor, you can register the configuration of your `HttpClient` in the `Startup` class's `ConfigureServices` method.</span></span> <span data-ttu-id="418f3-164">當您需要與 HTTP 端點互動時，請使用該設定。</span><span class="sxs-lookup"><span data-stu-id="418f3-164">Use that configuration when you need to interact with the HTTP endpoint.</span></span> <span data-ttu-id="418f3-165">請考慮下列設定程式碼：</span><span class="sxs-lookup"><span data-stu-id="418f3-165">Consider the following configuration code:</span></span>

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

<span data-ttu-id="418f3-166">每當您需要從 GitHub 存取資料時，請建立名稱為的用戶端 `github` 。</span><span class="sxs-lookup"><span data-stu-id="418f3-166">Whenever you need to access data from GitHub, create a client with a name of `github`.</span></span> <span data-ttu-id="418f3-167">用戶端是使用基底位址設定的，而且要求標頭會適當地設定。</span><span class="sxs-lookup"><span data-stu-id="418f3-167">The client is configured with the base address, and the request headers are set appropriately.</span></span> <span data-ttu-id="418f3-168">使用指示詞 `IHttpClientFactory` Blazor `@inject` 或屬性（attribute）將插入您的元件 `[Inject]` 。</span><span class="sxs-lookup"><span data-stu-id="418f3-168">Inject the `IHttpClientFactory` into your Blazor components with the `@inject` directive or an `[Inject]` attribute on a property.</span></span> <span data-ttu-id="418f3-169">建立您的命名用戶端，並使用下列語法與服務互動：</span><span class="sxs-lookup"><span data-stu-id="418f3-169">Create your named client and interact with services using the following syntax:</span></span>

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

<span data-ttu-id="418f3-170">這個方法會傳回描述 *dotnet/* 檔 GitHub 存放庫中問題集合的字串。</span><span class="sxs-lookup"><span data-stu-id="418f3-170">This method returns the string describing the collection of issues in the *dotnet/docs* GitHub repository.</span></span> <span data-ttu-id="418f3-171">它會以 JSON 格式傳回內容，並將其還原序列化為適當的 GitHub 問題物件。</span><span class="sxs-lookup"><span data-stu-id="418f3-171">It returns content in JSON format and is deserialized into appropriate GitHub issue objects.</span></span> <span data-ttu-id="418f3-172">有許多方式可讓您設定 `HttpClientFactory` 以傳遞預先設定的 `HttpClient` 物件。</span><span class="sxs-lookup"><span data-stu-id="418f3-172">There are many ways that you can configure the `HttpClientFactory` to deliver preconfigured `HttpClient` objects.</span></span> <span data-ttu-id="418f3-173">請嘗試使用 `HttpClient` 不同的名稱和端點來設定多個實例，以供您使用的各種 web 服務使用。</span><span class="sxs-lookup"><span data-stu-id="418f3-173">Try configuring multiple `HttpClient` instances with different names and endpoints for the various web services you work with.</span></span> <span data-ttu-id="418f3-174">這種方法可讓您與這些服務的互動更容易在每個頁面上使用。</span><span class="sxs-lookup"><span data-stu-id="418f3-174">This approach will make your interactions with those services easier to work with on each page.</span></span> <span data-ttu-id="418f3-175">如需詳細資訊，請參閱 [IHttpClientFactory 的檔](/aspnet/core/fundamentals/http-requests)。</span><span class="sxs-lookup"><span data-stu-id="418f3-175">For more details, read [the documentation for the IHttpClientFactory](/aspnet/core/fundamentals/http-requests).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="418f3-176">[上一個](forms-validation.md) 
>[下一步](middleware.md)</span><span class="sxs-lookup"><span data-stu-id="418f3-176">[Previous](forms-validation.md)
[Next](middleware.md)</span></span>
