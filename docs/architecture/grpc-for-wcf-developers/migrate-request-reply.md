---
title: 將 WCF 要求-回復服務遷移至 WCF 開發人員的 gRPC-gRPC
description: 瞭解如何將簡單的要求-回復服務從 WCF 遷移至 gRPC。
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 183e3b0ab1ce5c63714ced064f0d0901f59819c7
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72770398"
---
# <a name="migrate-a-wcf-request-reply-service-to-a-grpc-unary-rpc"></a>將 WCF 要求-回復服務遷移至 gRPC 一元 RPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

本節說明如何在 ASP.NET Core gRPC 中，將 WCF 中的基本要求-回復服務遷移至一元 RPC 服務。 這些服務是 Windows Communication Foundation （WCF）和 gRPC 中最簡單的服務類型，因此是很好的起點。 遷移服務之後，您將瞭解如何從相同的 `.proto` 檔案產生用戶端程式庫，以便從 .NET 用戶端應用程式取用服務。

## <a name="the-wcf-solution"></a>WCF 解決方案

[PortfoliosSample 解決方案](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys)包含簡單的要求-回復組合服務，可供您下載單一組合或指定 Trader 的所有公事包。 服務是在介面 `IPortfolioService` 中以 `ServiceContract` 屬性定義的：

```csharp
[ServiceContract]
public interface IPortfolioService
{
    [OperationContract]
    Task<Portfolio> Get(Guid traderId, int portfolioId);

    [OperationContract]
    Task<List<Portfolio>> GetAll(Guid traderId);
}
```

@No__t_0 模型是以[DataContract](xref:System.Runtime.Serialization.DataContractAttribute)標記C#的簡單類別，包括 `PortfolioItem` 物件的清單。 這些模型會定義在 `TraderSys.PortfolioData` 專案中，以及代表資料存取抽象的儲存機制類別。

```csharp
[DataContract]
public class Portfolio
{
    [DataMember]
    public int Id { get; set; }

    [DataMember]
    public Guid TraderId { get; set; }

    [DataMember]
    public List<PortfolioItem> Items { get; set; }
}

[DataContract]
public class PortfolioItem
{
    [DataMember]
    public int Id { get; set; }

    [DataMember]
    public int ShareId { get; set; }

    [DataMember]
    public int Holding { get; set; }

    [DataMember]
    public decimal Cost { get; set; }
}
```

@No__t_0 的執行會使用透過相依性插入所提供的存放庫類別，以傳回 `DataContract` 類型的實例。

```csharp
public class PortfolioService : IPortfolioService
{
    private readonly IPortfolioRepository _repository;

    public PortfolioService(IPortfolioRepository repository)
    {
        _repository = repository;
    }

    public async Task<Portfolio> Get(Guid traderId, int portfolioId)
    {
        return await _repository.GetAsync(traderId, portfolioId);
    }

    public async Task<List<Portfolio>> GetAll(Guid traderId)
    {
        return await _repository.GetAllAsync(traderId);
    }
}
```

## <a name="the-portfoliosproto-file"></a>組合的 proto 檔案

如果您遵循上一節中的指示進行，您應該會有一個 gRPC 專案，其中包含如下所示的 `portfolios.proto` 檔案。

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

第一個步驟是將 `DataContract` 類別遷移至其 Protobuf 對應專案。

## <a name="convert-the-datacontracts-to-grpc-messages"></a>將 DataContracts 轉換為 gRPC 訊息

@No__t_0 類別會先轉換成 Protobuf 訊息，因為 `Portfolio` 類別相依于它。 類別非常簡單，而三個屬性會直接對應至 gRPC 資料類型。 [@No__t_0] 屬性（代表購買的共用的價格）是 [`decimal`] 欄位，而 [gRPC] 僅支援實際數位的 `float` 或 `double`，不適用於貨幣。 由於共用價格的差異最少一美分，因此成本會以一 `int32` 美分來表示。

> [!NOTE]
> 請記得在 `.proto` 檔案中使用 `camelCase` 做為功能變數名稱;程式C#代碼產生器會將它們轉換成 `PascalCase`，而其他語言的使用者則會感謝您遵守其不同的編碼標準。

```protobuf
message PortfolioItem {
    int32 id = 1;
    int32 share_id = 2;
    int32 holding = 3;
    int32 cost_cents = 4;
}
```

@No__t_0 類別稍微複雜一點。 在 WCF 程式碼中，開發人員使用 `TraderId` 屬性的 `Guid`，並包含 `List<PortfolioItem>`。 在沒有第一級 `UUID` 類型的 Protobuf 中，您應該使用 `traderId` 欄位的 `string`，並在您自己的程式碼中進行剖析。 針對專案清單，請使用欄位上的 `repeated` 關鍵字。

```protobuf
message Portfolio {
    int32 id = 1;
    string trader_id = 2;
    repeated PortfolioItem items = 3;
}
```

現在我們已經有資料訊息，我們可以宣告服務 RPC 端點。

## <a name="convert-the-servicecontract-to-a-grpc-service"></a>將 ServiceContract 轉換成 gRPC 服務

WCF `Get` 方法會採用兩個參數： `Guid traderId` 和 `int portfolioId`。 gRPC 服務方法只能接受單一參數，因此必須建立訊息來保存這兩個值。 常見的做法是使用與方法相同的名稱來命名這些要求物件，並 `Request` 尾碼。 同樣地，`string` 用於 `traderId` 欄位，而不是 `Guid`。

服務可以直接傳回 `Portfolio` 訊息，但同樣地，這可能會影響未來的回溯相容性。 針對服務中的每個方法定義個別的 `Request` 和 `Response` 訊息是個很好的作法，即使其中有許多都是相同的，因此請使用單一 `Portfolio` 欄位宣告 `GetResponse` 訊息。

下列範例會使用 `GetRequest` 訊息，顯示 gRPC 服務方法的宣告：

```protobuf
message GetRequest {
    string trader_id = 1;
    int32 portfolio_id = 2;
}

message GetResponse {
    Portfolio portfolio = 1;
}

service Portfolios {
    rpc Get(GetRequest) returns (GetResponse);
}
```

WCF `GetAll` 方法只接受單一參數，`traderId`，因此它可能會將 `string` 指定為參數類型，但 gRPC 需要定義的訊息類型。 這項需求有助於強制執行針對所有輸入和輸出使用自訂訊息的作法，以供未來回溯相容性之用。

WCF 方法也會傳回 `List<Portfolio>`，但基於相同的原因，它不允許簡單的參數類型，gRPC 不允許 `repeated Portfolio` 做為傳回類型。 相反地，請建立 `GetAllResponse` 類型來包裝清單。

> [!WARNING]
> 您可能會想要建立 `PortfolioList` 訊息或類似檔案，並在多個服務方法中使用它，但您應該不會受到此誘惑的抵觸。 不可能知道服務上的各種方法在未來的發展方式，因此請將它們的訊息指定為明確且完全分隔。

```protobuf
message GetAllRequest {
    string trader_id = 1;
}

message PortfolioList {
    repeated Portfolio portfolios = 1;
}

service Portfolios {
    rpc Get(GetRequest) returns (Portfolio);
    rpc GetAll(GetAllRequest) returns (GetAllResponse);
}
```

如果您使用這些變更來儲存專案，則 gRPC 組建目標會在背景中執行，並產生所有 Protobuf 訊息類型，以及您可以繼承以執行服務的基類。

開啟 `Services/GreeterService.cs` 類別，並刪除範例程式碼。 現在您可以加入「公事包服務」執行。 產生的基類將會在 `Protos` 命名空間中，並以嵌套類別的形式產生。 gRPC 會建立一個靜態類別，其名稱與 `.proto` 檔案中的服務相同，然後在該靜態類別內具有尾碼 `Base` 的基類，因此會 `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase` 基底類型的完整識別碼。

```csharp
namespace TraderSys.Portfolios.Services
{
    public class PortfolioService : Protos.Portfolios.PortfoliosBase
    {
    }
}
```

基類會針對可覆寫以執行服務的 `Get` 和 `GetAll`，宣告 `virtual` 方法。 方法 `virtual`，而不是 `abstract`，因此，如果您未加以執行，服務會傳回明確的 gRPC `Unimplemented` 狀態碼，與您可能會在一般C#程式碼中擲回 `NotImplementedException` 很類似。

ASP.NET Core 中所有 gRPC 一元服務方法的簽章都是一致的。 有兩個參數：第一個是在 `.proto` 檔案中宣告的訊息類型，而第二個是 `ServerCallContext`，其運作方式類似于 ASP.NET Core 的 `HttpContext`。 事實上，`ServerCallContext` 類別上有一個稱為 `GetHttpContext` 的擴充方法，您可以用它來取得基礎 `HttpContext`，不過您不應該經常使用它。 我們將在本章稍後介紹 `ServerCallContext`，同時討論驗證的章節。

方法的傳回型別是 `Task<T>`，其中 `T` 是回應訊息類型。 所有的 gRPC 服務方法都是非同步。

## <a name="migrate-the-portfoliodata-library-to-net-core"></a>將 PortfolioData 程式庫遷移至 .NET Core

此時，專案需要 WCF 方案中包含在 `TraderSys.PortfolioData` 類別庫中的組合存放庫和模型。 將它們帶入最簡單的方式，就是使用 [Visual Studio**新增專案**] 對話方塊與 [*類別庫] （.NET Standard）* 範本，或從命令列使用 .NET Core CLI 執行下列命令，以建立新的類別庫。從包含 `TraderSys.sln` 檔案的目錄。

```dotnetcli
dotnet new classlib -o src/TraderSys.PortfolioData
dotnet sln add src/TraderSys.PortfolioData
```

一旦建立程式庫並將其加入方案中，請刪除產生的 `Class1.cs` 檔案，然後將檔案從 WCF 方案的程式庫複製到新的類別庫資料夾，並保留資料夾結構。

```
Models
  Portfolio.cs
  PortfolioItem.cs
IPortfolioRepository.cs
PortfolioRepository.cs
```

SDK 樣式的 .NET 專案會自動在或其本身的目錄底下包含任何 `.cs` 檔案，因此不需要明確地將它們新增至專案。 剩下的唯一步驟是從 `Portfolio` 和 `PortfolioItem` 類別中移除 `DataContract` 和 `DataMember` 屬性，使其成為簡單的C#類別。

```csharp
public class Portfolio
{
    public int Id { get; set; }
    public Guid TraderId { get; set; }
    public List<PortfolioItem> Items { get; set; }
}

public class PortfolioItem
{
    public int Id { get; set; }
    public int ShareId { get; set; }
    public int Holding { get; set; }
    public decimal Cost { get; set; }
}
```

## <a name="use-aspnet-core-dependency-injection"></a>使用 ASP.NET Core 相依性插入

現在您可以將此程式庫的參考新增至 gRPC 應用程式專案，並使用 gRPC 服務執行中的相依性插入來取用 `PortfolioRepository` 類別。 在 WCF 應用程式中，相依性插入是由 Autofac IoC 容器所提供。 ASP.NET Core 在中具有相依性插入內建;存放庫可以在 `Startup` 類別的 `ConfigureServices` 方法中註冊。

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        // Register the repository class as a scoped service (instance per request)
        services.AddScoped<IPortfolioRepository, PortfolioRepository>();

        services.AddGrpc();
    }

    // ...
}
```

@No__t_0 的執行現在可以指定為 `PortfolioService` 類別中的「函數參數」，如下所示：

```csharp
public class PortfolioService : Protos.Portfolios.PortfoliosBase
{
    private readonly IPortfolioRepository _repository;

    public PortfolioService(IPortfolioRepository repository)
    {
        _repository = repository;
    }
}
```

## <a name="implement-the-grpc-service"></a>執行 gRPC 服務

既然您已在 `portfolios.proto` 檔案中宣告您的訊息和服務，就必須在 `PortfolioService` 類別中，執行繼承自 gRPC 產生之 `Portfolios.PortfoliosBase` 類別的服務方法。 方法會在基類中宣告為 `virtual`。 如果您未覆寫它們，它們預設會傳回「未實 gRPC」狀態碼。

一開始先執行 `Get` 方法。 預設覆寫看起來如下列範例所示：

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    return base.Get(request, context);
}
```

第一個問題是，`request.TraderId` 是字串，而服務需要 `Guid`。 雖然字串的預期格式是 `UUID`，但程式碼必須處理呼叫者已傳送無效值並適當回應的可能性。 服務可以藉由擲回 `RpcException` 來回應錯誤，並使用標準的 `InvalidArgument` 狀態碼來表示問題。

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    if (!Guid.TryParse(request.TraderId, out var traderId))
    {
        throw new RpcException(new Status(StatusCode.InvalidArgument, "traderId must be a UUID"));
    }

    return base.Get(request, context);
}
```

一旦 `traderId` 有適當的 `Guid` 值，就可以使用存放庫來抓取組合，並將其傳回給用戶端。

```csharp
    var response = new GetResponse
    {
        Portfolio = await _repository.GetAsync(request.TraderId, request.PortfolioId)
    };
```

### <a name="map-internal-models-to-grpc-messages"></a>將內部模型對應至 gRPC 訊息

先前的程式碼實際上並不可行，因為存放庫會傳回自己的 POCO 模型 `Portfolio`，但 gRPC 需要*它自己的*Protobuf 訊息 `Portfolio`。 就像是將 Entity Framework 類型對應到資料傳輸類型，最好的方法是在兩者之間提供轉換。 將此程式碼放在 Protobuf 產生的類別中，這是一個很好的位置，它會宣告為 `partial` 類別，讓它可以擴充。

```csharp
namespace TraderSys.Portfolios.Protos
{
    public partial class PortfolioItem
    {
        public static PortfolioItem FromRepositoryModel(PortfolioData.Models.PortfolioItem source)
        {
            if (source is null) return null;

            return new PortfolioItem
            {
                Id = source.Id,
                ShareId = source.ShareId,
                Holding = source.Holding,
                CostCents = (int)(source.Cost * 100)
            };
        }
    }

    public partial class Portfolio
    {
        public static Portfolio FromRepositoryModel(PortfolioData.Models.Portfolio source)
        {
            if (source is null) return null;

            var target = new Portfolio
            {
                Id = source.Id,
                TraderId = source.TraderId.ToString(),
            };

            target.Items.AddRange(source.Items.Select(PortfolioItem.FromRepositoryModel));

            return target;
        }
    }
}
```

> [!NOTE]
> 您可以使用程式庫（例如[AutoMapper](https://automapper.org/) ）來處理從內部模型類別到 Protobuf 類型的這種轉換，只要您設定較低層級的類型轉換，例如 `string` / `Guid` 或 `decimal` / `double` 和清單對應。

轉換程式碼準備好之後，就可以完成 `Get` 方法的執行。

```csharp
public override async Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    if (!Guid.TryParse(request.TraderId, out var traderId))
    {
        throw new RpcException(new Status(StatusCode.InvalidArgument, "traderId must be a UUID"));
    }

    var portfolio = await _repository.GetAsync(traderId, request.PortfolioId);

    return new GetResponse
    {
        Portfolio = Portfolio.FromRepositoryModel(portfolio)
    };
}

```

@No__t_0 方法的實作為相似之處。 請注意，Protobuf 訊息上的 `repeated` 欄位會產生為 `RepeatedField<T>` 類型的 `readonly` 屬性，因此您必須使用 `AddRange` 方法將專案新增至其中，如下列範例所示：

```csharp
public override async Task<GetAllResponse> GetAll(GetAllRequest request, ServerCallContext context)
{
    if (!Guid.TryParse(request.TraderId, out var traderId))
    {
        throw new RpcException(new Status(StatusCode.InvalidArgument, "traderId must be a UUID"));
    }

    var portfolios = await _repository.GetAllAsync(traderId);

    var response = new GetAllResponse();
    response.Portfolios.AddRange(portfolios.Select(Portfolio.FromRepositoryModel));

    return response;
}
```

已成功將 WCF 要求-回復服務遷移至 gRPC，讓我們來看一下如何從 `.proto` 檔案建立用戶端。

## <a name="generate-client-code"></a>產生用戶端程式代碼

在相同的方案中建立 .NET Standard 類別庫，以包含用戶端。 這主要是建立用戶端程式代碼的範例，但您可以使用 NuGet 封裝這類程式庫，並將它散發到內部存放庫，以供其他 .NET 小組使用。 請繼續並將稱為 `TraderSys.Portfolios.Client` 的新 .NET Standard 類別庫加入至方案，並刪除 `Class1.cs` 檔案。

> [!CAUTION]
> [Grpc .net. 用戶端](https://www.nuget.org/packages/Grpc.Net.Client)NuGet 套件需要 .net Core 3.0 （或另一個 .NET Standard 2.1 相容的執行時間）。 [Grpc](https://www.nuget.org/packages/Grpc.Core) NuGet 套件支援舊版的 .NET FRAMEWORK 和 .net Core。

在 Visual Studio 2019 中，您可以加入 gRPC 服務的參考，就像您在舊版 Visual Studio 中將服務參考新增至 WCF 專案的方式一樣。 服務參考和已連線的服務現在都是在相同的 UI 下進行管理，您可以用滑鼠右鍵按一下方案總管中 `TraderSys.Portfolios.Client` 專案的 [相依性] 節點，然後選取 [**新增已連結的服務** **]** 來存取。 在出現的工具視窗中，選取 [**服務參考**] 區段，然後按一下 [**加入新的 gRPC 服務參考**]。

![Visual Studio 2019 中的已連線的服務 UI](media/migrate-request-reply/add-connected-service.png)

流覽至 `TraderSys.Portfolios` 專案中的 `portfolios.proto` 檔案，將**類別類型**保留為 [**用戶端**]，然後按一下 **[確定]** 。

![Visual Studio 2019 中的 [加入新的 gRPC 服務參考] 對話方塊](media/migrate-request-reply/add-new-grpc-service-reference.png)

> [!TIP]
> 請注意，此對話方塊也會提供 [URL] 欄位。 如果您的組織維護 `.proto` 檔案的 web 可存取目錄，您就可以藉由設定此 URL 位址來建立用戶端。

使用 Visual Studio**加入已連接服務**功能時，會將 `portfolios.proto` 檔案新增至類別庫專案做為*連結*的檔案，而不是複製，因此服務專案中檔案的變更會自動套用至用戶端專案. @No__t_1 檔案中的 `<Protobuf>` 元素看起來像這樣：

```xml
<Protobuf Include="..\TraderSys.Portfolios\Protos\portfolios.proto" GrpcServices="Client">
  <Link>Protos\portfolios.proto</Link>
</Protobuf>
```

> [!TIP]
> 如果您不是使用 Visual Studio 或偏好從命令列工作，您可以使用**dotnet-grpc**通用工具來管理 .net grpc 專案中的 Protobuf 參考。 [如需詳細資訊，請參閱**dotnet-grpc**檔](https://docs.microsoft.com/aspnet/core/grpc/dotnet-grpc)。

### <a name="use-the-portfolios-service-from-a-client-application"></a>從用戶端應用程式使用包服務

下列程式碼是在主控台應用程式中使用所產生之用戶端的簡單範例。 如需更詳細的 gRPC 用戶端程式代碼探索，請見本章的結尾。

```csharp
public class Program
{
    public async Task Main(string[] args)
    {
        GetResponse response;

        using (var channel = GrpcChannel.ForAddress("https://localhost:5001"))
        {
            var client = new Protos.Portfolios.PortfoliosClient(channel);

            response = await client.GetAsync(new GetRequest
            {
                TraderId = args[0],
                PortfolioId = int.Parse(args[1])
            });
        }

        foreach (var item in response.Portfolio.Items)
        {
            Console.WriteLine($"Holding {item.Holding} of Share ID {item.ShareId}.");
        }
    }
}
```

現在，您已將基本 WCF 應用程式遷移至 ASP.NET Core gRPC 服務，並建立用戶端以從 .NET 應用程式取用服務。 下一節將涵蓋更多「雙工」服務。

>[!div class="step-by-step"]
>[上一頁](create-project.md)
>[下一頁](migrate-duplex-services.md)
