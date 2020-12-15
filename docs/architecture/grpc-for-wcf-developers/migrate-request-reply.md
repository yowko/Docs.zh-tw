---
title: 將 WCF 要求-回復服務遷移至 WCF 開發人員的 gRPC-gRPC
description: 瞭解如何將簡單的要求-回復服務從 WCF 遷移至 gRPC。
ms.date: 09/02/2019
ms.openlocfilehash: 29a7bc77bc3a4becd767fc7a50adff5b746f54bc
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512693"
---
# <a name="migrate-a-wcf-request-reply-service-to-a-grpc-unary-rpc"></a>將 WCF 要求-回復服務遷移至 gRPC 一元 RPC

本節說明如何在 ASP.NET Core gRPC 中，將 WCF 中的基本要求-回復服務遷移至一元 RPC 服務。 這些服務是 Windows Communication Foundation (WCF) 和 gRPC 中最簡單的服務類型，因此是很好的起點。 在遷移服務之後，您將瞭解如何從相同的檔案產生用戶端程式庫， `.proto` 以從 .net 用戶端應用程式取用服務。

## <a name="the-wcf-solution"></a>WCF 方案

[PortfoliosSample 解決方案](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys)包含簡單的要求-回復組合服務，可為指定的 trader 下載單一組合或所有組合。 服務定義于具有屬性的介面中 `IPortfolioService` `ServiceContract` ：

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

`Portfolio`模型是以[DataContract](xref:System.Runtime.Serialization.DataContractAttribute)標示的簡單 c # 類別，並包含物件清單 `PortfolioItem` 。 這些模型是在專案中定義的， `TraderSys.PortfolioData` 以及代表資料存取抽象概念的儲存機制類別。

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

此 `ServiceContract` 執行會使用透過相依性插入所提供的儲存機制類別，以傳回類型的實例 `DataContract` ：

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

如果您已遵循上一節中的指示，您應該會有一個 gRPC 專案，其中包含如下所示的檔案 `portfolios.proto` ：

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

第一個步驟是將類別遷移 `DataContract` 至其 Protobuf 對應專案。

## <a name="convert-the-datacontract-classes-to-grpc-messages"></a>將 DataContract 類別轉換成 gRPC 訊息

`PortfolioItem`類別會先轉換成 Protobuf 訊息，因為 `Portfolio` 類別相依于它。 類別很簡單，而且三個屬性會直接對應至 gRPC 資料類型。 此 `Cost` 屬性代表購買之共用的付費價格，是一個 `decimal` 欄位。 gRPC 僅支援 `float` 或 `double` 適用于不適合貨幣的實數。 由於共用價格的變化最少1美分，因此成本可以 `int32` 美分表示。

> [!NOTE]
> 請記得將 `snake_case` 用於檔案中的功能變數名稱 `.proto` 。 C # 程式碼產生器會 `PascalCase` 為您轉換它們，而其他語言的使用者則會感謝您遵守其不同的編碼標準。

```protobuf
message PortfolioItem {
    int32 id = 1;
    int32 share_id = 2;
    int32 holding = 3;
    int32 cost_cents = 4;
}
```

`Portfolio`類別會比較複雜一點。 在 WCF 程式碼中，開發人員會使用做 `Guid` 為 `TraderId` 屬性，並包含 `List<PortfolioItem>` 。 在不具有第一級型別的 Protobuf 中 `UUID` ，您應該針對欄位使用， `string` `traderId` 並在您自己的程式碼中加以剖析。 針對專案清單，在 `repeated` 欄位上使用關鍵字。

```protobuf
message Portfolio {
    int32 id = 1;
    string trader_id = 2;
    repeated PortfolioItem items = 3;
}
```

現在您已有資料訊息，您可以宣告服務 RPC 端點。

## <a name="convert-servicecontract-to-a-grpc-service"></a>將 ServiceContract 轉換成 gRPC 服務

WCF `Get` 方法會採用兩個參數： `Guid traderId` 和 `int portfolioId` 。 gRPC 服務方法只能採用單一參數，因此您必須建立訊息來保存兩個值。 常見的作法是將這些要求物件命名為與方法相同的名稱，後面加上尾碼 `Request` 。 同樣地， `string` 會將用於 `traderId` 欄位而不是 `Guid` 。

服務可以 `Portfolio` 直接傳回訊息，但同樣地，這可能會影響未來的回溯相容性。 `Request`針對服務中的每個方法定義個別和訊息是很好的作法 `Response` ，即使其中有許多也是相同的。 因此，請 `GetResponse` 使用單一欄位宣告訊息 `Portfolio` 。

此範例顯示 gRPC 服務方法的宣告，並顯示 `GetRequest` 下列訊息：

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

WCF `GetAll` 方法只接受單一參數， `traderId` 因此您可能會將它指定 `string` 為參數類型。 但是 gRPC 需要定義的訊息類型。 這項需求有助於強制執行針對所有輸入和輸出使用自訂訊息的做法，以供未來回溯相容性之用。

WCF 方法也會傳回 `List<Portfolio>` ，但是基於相同的原因，它不允許簡單的參數類型，gRPC 不允許 `repeated Portfolio` 做為傳回型別。 請改為建立 `GetAllResponse` 包裝清單的型別。

> [!WARNING]
> 您可能會想要建立一個 `PortfolioList` 或類似的訊息，並在多個服務方法中使用它，但您應該要抵禦這個誘惑。 您不可能知道服務上的各種方法如何演進，讓他們的訊息保持明確且明確地分隔。

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

如果您使用這些變更來儲存專案，gRPC 組建目標將會在背景中執行，並產生所有 Protobuf 訊息類型，以及您可以繼承以執行服務的基類。

開啟 `Services/GreeterService.cs` 類別並刪除範例程式碼。 現在您可以新增組合服務的執行。 產生的基類會在 `Protos` 命名空間中，並以嵌套類別的形式產生。 gRPC 會建立一個靜態類別，其名稱與檔案中的服務名稱相同， `.proto` 而基類中的基底類別具有尾碼 `Base` ，因此基底類型的完整識別碼為 `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase` 。

```csharp
namespace TraderSys.Portfolios.Services
{
    public class PortfolioService : Protos.Portfolios.PortfoliosBase
    {
    }
}
```

基類 `virtual` `Get` 會宣告和的方法 `GetAll` ，可以覆寫以執行服務。 這些方法不是 `virtual` `abstract` 如此，如果您未執行這些方法，則服務會傳回明確的 gRPC `Unimplemented` 狀態碼，就像您可能會 `NotImplementedException` 在一般的 c # 程式碼中擲回。

ASP.NET Core 中所有 gRPC 一元服務方法的簽章都是一致的。 有兩個參數：第一個是在檔案中宣告的訊息類型 `.proto` ，而第二個則是 `ServerCallContext` ，其運作方式類似于 `HttpContext` ASP.NET Core 的。 事實上， `GetHttpContext` `ServerCallContext` 您可以使用類別上的擴充方法來取得基礎 `HttpContext` ，雖然您不需要經常使用它。 我們將在本章 `ServerCallContext` 稍後討論，並在討論驗證的章節中探討。

方法的傳回型別是 `Task<T>` ，其中 `T` 是回應訊息類型。 所有 gRPC 服務方法都是非同步。

## <a name="migrate-the-portfoliodata-library-to-net-core"></a>將 PortfolioData 程式庫遷移至 .NET Core

此時，專案需要 `TraderSys.PortfolioData` WCF 方案中類別庫中所包含的組合存放庫和模型。 Visual Studio 使用 [ **新增專案** ] 對話方塊和 [類別庫] ( .NET Standard) 範本，或從命令列使用 .NET Core CLI 從命令列執行下列命令，以將它們帶到最簡單的方式，就是建立新的類別庫 `TraderSys.sln` ：

```dotnetcli
dotnet new classlib -o src/TraderSys.PortfolioData
dotnet sln add src/TraderSys.PortfolioData
```

當您建立程式庫並將它新增至方案之後，請刪除產生的檔案， `Class1.cs` 並將檔案從 WCF 解決方案的程式庫複製到新的類別庫資料夾中，並保留資料夾結構：

```
Models
  Portfolio.cs
  PortfolioItem.cs
IPortfolioRepository.cs
PortfolioRepository.cs
```

SDK 樣式的 .NET 專案會自動 `.cs` 在自己的目錄中包含任何檔案，因此您不需要明確地將它們新增至專案。 剩下的唯一步驟是 `DataContract` `DataMember` 從和類別中移除和屬性 `Portfolio` ， `PortfolioItem` 讓它們是一般的 c # 類別：

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

現在您可以將此程式庫的參考新增至 gRPC 應用程式專案，並 `PortfolioRepository` 使用 gRPC 服務執行中的相依性插入來取用類別。 在 WCF 應用程式中，相依性插入是由 Autofac IoC 容器所提供。 ASP.NET Core 在中具有相依性插入內建。 您可以在類別的方法中註冊存放庫 `ConfigureServices` `Startup` ：

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

您 `IPortfolioRepository` 現在可以在類別中將此實作為函式參數來指定，如下所示 `PortfolioService` ：

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

現在您已在檔案中宣告訊息和服務 `portfolios.proto` ，您必須在 `PortfolioService` 繼承自 gRPC 產生之類別的類別中，執行服務方法 `Portfolios.PortfoliosBase` 。 方法會 `virtual` 在基類中宣告為。 如果您未加以覆寫，則預設會傳回 gRPC 「未執行」狀態碼。

首先，請執行 `Get` 方法。 預設覆寫看起來如以下範例所示：

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    return base.Get(request, context);
}
```

第一個問題是 `request.TraderId` 字串，而服務需要 `Guid` 。 雖然字串的預期格式為 `UUID` ，但是程式碼必須處理呼叫端傳送無效值並適當回應的可能性。 服務可以擲回 `RpcException` ，並使用標準 `InvalidArgument` 狀態碼來表達問題，以回應錯誤：

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

在有適當的 `Guid` 值之後 `traderId` ，您可以使用存放庫來取出組合，並將其傳回給用戶端：

```csharp
    var response = new GetResponse
    {
        Portfolio = await _repository.GetAsync(request.TraderId, request.PortfolioId)
    };
```

### <a name="map-internal-models-to-grpc-messages"></a>將內部模型對應至 gRPC 訊息

先前的程式碼並不會實際運作，因為存放庫會傳回自己的 POCO 模型 `Portfolio` ，但 gRPC 需要自己的 Protobuf 訊息 `Portfolio` 。 當您將 Entity Framework 類型對應到資料傳輸類型時，最好的解決方法是在兩者之間提供轉換。 將這項轉換的程式碼放在 Protobuf 產生的類別中是一個很好的位置，它會宣告為 `partial` 類別，以便進行擴充：

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
> 您可以使用程式庫（例如[AutoMapper](https://automapper.org/) ）來處理從內部模型類別到 Protobuf 類型的轉換，只要您設定較低層級的類型轉換（例如 `string` / `Guid` 或 `decimal` / `double` 和清單對應）即可。

現在您已備妥轉換程式碼，您可以完成方法執行 `Get` ：

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

方法的執行 `GetAll` 方式很類似。 請注意， `repeated` Protobuf 訊息上的欄位會產生為 `readonly` 類型的屬性 `RepeatedField<T>` ，因此您必須使用方法將專案加入至這些欄位 `AddRange` ，如下列範例所示：

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

成功將 WCF 要求-回復服務遷移至 gRPC 之後，讓我們看看如何從檔案建立用戶端 `.proto` 。

## <a name="generate-client-code"></a>產生用戶端程式代碼

在相同方案中建立 .NET Standard 類別庫以包含用戶端。 這主要是建立用戶端程式代碼的範例，但您可以使用 NuGet 封裝這類程式庫，並將其散發至內部儲存機制，以供其他 .NET 小組使用。 繼續進行，並將名為的新 .NET Standard 類別庫加入 `TraderSys.Portfolios.Client` 至方案，然後刪除該檔案 `Class1.cs` 。

> [!CAUTION]
> [Grpc .net. 用戶端](https://www.nuget.org/packages/Grpc.Net.Client)NuGet 套件需要 .net Core 3.0 (或其他 .NET Standard 2.1 相容的執行時間) 。 Grpc 和 .NET Core 的舊版 .NET Framework 和 .NET Core 是由 [Core](https://www.nuget.org/packages/Grpc.Core) NuGet 套件支援。

在 Visual Studio 2019 中，您可以將參考新增至 gRPC 服務，其方式類似于將服務參考加入至舊版 Visual Studio 的 WCF 專案。 服務參考和已聯機服務現在都是在相同的 UI 下進行管理。 您可以用滑鼠右鍵按一下 [方案總管 **]** 中專案的 [相依性] 節點 `TraderSys.Portfolios.Client` ，然後選取 [ **加入已連接服務**]，來存取 UI。 在出現的工具視窗中，選取 [ **服務參考** ] 區段，然後選取 [ **新增 gRPC 服務參考**]：

![Visual Studio 2019 中的已連線的服務 UI](media/migrate-request-reply/add-connected-service.png)

流覽至 `portfolios.proto` 專案中的檔案 `TraderSys.Portfolios` ，讓 **用戶端** 保持在 [ **選取要產生的類別類型**] 下，然後選取 **[確定]**：

![Visual Studio 2019 中的 [新增 gRPC 服務參考] 對話方塊](media/migrate-request-reply/add-new-grpc-service-reference.png)

> [!TIP]
> 請注意，此對話方塊也會提供 URL 欄位。 如果您的組織維護 web 可存取的目錄 `.proto` ，您只要設定此 URL 位址，就可以建立用戶端。

當您使用 Visual Studio **加入已連接服務** ] 功能時，會將檔案 `portfolios.proto` 新增至類別庫專案做為 *連結* 的檔案，而不是複製，因此服務專案中檔案的變更會自動套用至用戶端專案。 檔案 `<Protobuf>` 中的元素 `csproj` 看起來像這樣：

```xml
<Protobuf Include="..\TraderSys.Portfolios\Protos\portfolios.proto" GrpcServices="Client">
  <Link>Protos\portfolios.proto</Link>
</Protobuf>
```

> [!TIP]
> 如果您不是使用 Visual Studio 或偏好從命令列工作，您可以使用 `dotnet-grpc` 全域工具來管理 .Net gRPC 專案中的 Protobuf 參考。 如需詳細資訊，請參閱[ `dotnet-grpc` 檔](/aspnet/core/grpc/dotnet-grpc)。

### <a name="use-the-portfolios-service-from-a-client-application"></a>從用戶端應用程式使用組合服務

下列程式碼是如何在主控台應用程式中使用產生的用戶端的簡單範例。 GRPC 用戶端程式代碼的更詳細探索是在本章結尾。

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

您現在已將基本 WCF 應用程式遷移至 ASP.NET Core 的 gRPC 服務，並建立了從 .NET 應用程式取用服務的用戶端。 下一節將涵蓋更多的雙工服務。

>[!div class="step-by-step"]
>[上一個](create-project.md) 
>[下一步](migrate-duplex-services.md)
