---
title: 將 WCF 要求-回復服務遷移至 WCF 開發人員的 gRPC-gRPC
description: 瞭解如何將簡單的要求-回復服務從 WCF 遷移至 gRPC。
ms.date: 12/15/2020
ms.openlocfilehash: 38c6e33e7588dd7c1b263d813d06c088ab484948
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938568"
---
# <a name="migrate-a-wcf-request-reply-service-to-a-grpc-unary-rpc"></a><span data-ttu-id="d77dd-103">將 WCF 要求-回復服務遷移至 gRPC 一元 RPC</span><span class="sxs-lookup"><span data-stu-id="d77dd-103">Migrate a WCF request-reply service to a gRPC unary RPC</span></span>

<span data-ttu-id="d77dd-104">本節說明如何在 ASP.NET Core gRPC 中，將 WCF 中的基本要求-回復服務遷移至一元 RPC 服務。</span><span class="sxs-lookup"><span data-stu-id="d77dd-104">This section covers how to migrate a basic request-reply service in WCF to a unary RPC service in ASP.NET Core gRPC.</span></span> <span data-ttu-id="d77dd-105">這些服務是 Windows Communication Foundation (WCF) 和 gRPC 中最簡單的服務類型，因此是很好的起點。</span><span class="sxs-lookup"><span data-stu-id="d77dd-105">These services are the simplest service types in both Windows Communication Foundation (WCF) and gRPC, so it's an excellent place to start.</span></span> <span data-ttu-id="d77dd-106">在遷移服務之後，您將瞭解如何從相同的檔案產生用戶端程式庫， `.proto` 以從 .net 用戶端應用程式取用服務。</span><span class="sxs-lookup"><span data-stu-id="d77dd-106">After migrating the service, you'll learn how to generate a client library from the same `.proto` file to consume the service from a .NET client application.</span></span>

## <a name="the-wcf-solution"></a><span data-ttu-id="d77dd-107">WCF 方案</span><span class="sxs-lookup"><span data-stu-id="d77dd-107">The WCF solution</span></span>

<span data-ttu-id="d77dd-108">[PortfoliosSample 解決方案](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys)包含簡單的要求-回復組合服務，可為指定的 trader 下載單一組合或所有組合。</span><span class="sxs-lookup"><span data-stu-id="d77dd-108">The [PortfoliosSample solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys) includes a simple request-reply Portfolio service to download either a single portfolio or all portfolios for a given trader.</span></span> <span data-ttu-id="d77dd-109">服務定義于具有屬性的介面中 `IPortfolioService` `ServiceContract` ：</span><span class="sxs-lookup"><span data-stu-id="d77dd-109">The service is defined in the interface `IPortfolioService` with a `ServiceContract` attribute:</span></span>

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

<span data-ttu-id="d77dd-110">`Portfolio`模型是以[DataContract](xref:System.Runtime.Serialization.DataContractAttribute)標示的簡單 c # 類別，並包含物件清單 `PortfolioItem` 。</span><span class="sxs-lookup"><span data-stu-id="d77dd-110">The `Portfolio` model is a simple C# class marked with [DataContract](xref:System.Runtime.Serialization.DataContractAttribute) and including a list of `PortfolioItem` objects.</span></span> <span data-ttu-id="d77dd-111">這些模型是在專案中定義的， `TraderSys.PortfolioData` 以及代表資料存取抽象概念的儲存機制類別。</span><span class="sxs-lookup"><span data-stu-id="d77dd-111">These models are defined in the `TraderSys.PortfolioData` project along with a repository class that represents a data access abstraction.</span></span>

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

<span data-ttu-id="d77dd-112">此 `ServiceContract` 執行會使用透過相依性插入所提供的儲存機制類別，以傳回類型的實例 `DataContract` ：</span><span class="sxs-lookup"><span data-stu-id="d77dd-112">The `ServiceContract` implementation uses a repository class provided via dependency injection that returns instances of the `DataContract` types:</span></span>

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

## <a name="the-portfoliosproto-file"></a><span data-ttu-id="d77dd-113">組合的 proto 檔案</span><span class="sxs-lookup"><span data-stu-id="d77dd-113">The portfolios.proto file</span></span>

<span data-ttu-id="d77dd-114">如果您已遵循上一節中的指示，您應該會有一個 gRPC 專案，其中包含如下所示的檔案 `portfolios.proto` ：</span><span class="sxs-lookup"><span data-stu-id="d77dd-114">If you followed the instructions in the previous section, you should have a gRPC project with a `portfolios.proto` file that looks like this:</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

<span data-ttu-id="d77dd-115">第一個步驟是將類別遷移 `DataContract` 至其 Protobuf 對應專案。</span><span class="sxs-lookup"><span data-stu-id="d77dd-115">The first step is to migrate the `DataContract` classes to their Protobuf equivalents.</span></span>

## <a name="convert-the-datacontract-classes-to-grpc-messages"></a><span data-ttu-id="d77dd-116">將 DataContract 類別轉換成 gRPC 訊息</span><span class="sxs-lookup"><span data-stu-id="d77dd-116">Convert the DataContract classes to gRPC messages</span></span>

<span data-ttu-id="d77dd-117">`PortfolioItem`類別會先轉換成 Protobuf 訊息，因為 `Portfolio` 類別相依于它。</span><span class="sxs-lookup"><span data-stu-id="d77dd-117">The `PortfolioItem` class will be converted to a Protobuf message first, because the `Portfolio` class depends on it.</span></span> <span data-ttu-id="d77dd-118">類別很簡單，而且三個屬性會直接對應至 gRPC 資料類型。</span><span class="sxs-lookup"><span data-stu-id="d77dd-118">The class is simple, and three of the properties map directly to gRPC data types.</span></span> <span data-ttu-id="d77dd-119">此 `Cost` 屬性代表購買之共用的付費價格，是一個 `decimal` 欄位。</span><span class="sxs-lookup"><span data-stu-id="d77dd-119">The `Cost` property, which represents the price paid for the shares at purchase, is a `decimal` field.</span></span> <span data-ttu-id="d77dd-120">gRPC 僅支援 `float` 或 `double` 適用于不適合貨幣的實數。</span><span class="sxs-lookup"><span data-stu-id="d77dd-120">gRPC supports only `float` or `double` for real numbers, which aren't suitable for currency.</span></span> <span data-ttu-id="d77dd-121">由於共用價格的變化最少1美分，因此成本可以 `int32` 美分表示。</span><span class="sxs-lookup"><span data-stu-id="d77dd-121">Because share prices vary by a minimum of one cent, the cost can be expressed as an `int32` of cents.</span></span>

> [!NOTE]
> <span data-ttu-id="d77dd-122">請記得將 `snake_case` 用於檔案中的功能變數名稱 `.proto` 。</span><span class="sxs-lookup"><span data-stu-id="d77dd-122">Remember to use `snake_case` for field names in your `.proto` file.</span></span> <span data-ttu-id="d77dd-123">C # 程式碼產生器會 `PascalCase` 為您轉換它們，而其他語言的使用者則會感謝您遵守其不同的編碼標準。</span><span class="sxs-lookup"><span data-stu-id="d77dd-123">The C# code generator will convert them to `PascalCase` for you, and users of other languages will thank you for respecting their different coding standards.</span></span>

```protobuf
message PortfolioItem {
    int32 id = 1;
    int32 share_id = 2;
    int32 holding = 3;
    int32 cost_cents = 4;
}
```

<span data-ttu-id="d77dd-124">`Portfolio`類別會比較複雜一點。</span><span class="sxs-lookup"><span data-stu-id="d77dd-124">The `Portfolio` class is a little more complicated.</span></span> <span data-ttu-id="d77dd-125">在 WCF 程式碼中，開發人員會使用做 `Guid` 為 `TraderId` 屬性，並包含 `List<PortfolioItem>` 。</span><span class="sxs-lookup"><span data-stu-id="d77dd-125">In the WCF code, the developer used a `Guid` for the `TraderId` property, and contains a `List<PortfolioItem>`.</span></span> <span data-ttu-id="d77dd-126">在不具有第一級型別的 Protobuf 中 `UUID` ，您應該針對欄位使用， `string` `traderId` 並在您自己的程式碼中加以剖析。</span><span class="sxs-lookup"><span data-stu-id="d77dd-126">In Protobuf, which doesn't have a first-class `UUID` type, you should use a `string` for the `traderId` field and parse it in your own code.</span></span> <span data-ttu-id="d77dd-127">針對專案清單，在 `repeated` 欄位上使用關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d77dd-127">For the list of items, use the `repeated` keyword on the field.</span></span>

```protobuf
message Portfolio {
    int32 id = 1;
    string trader_id = 2;
    repeated PortfolioItem items = 3;
}
```

<span data-ttu-id="d77dd-128">現在您已有資料訊息，您可以宣告服務 RPC 端點。</span><span class="sxs-lookup"><span data-stu-id="d77dd-128">Now that you have the data messages, you can declare the service RPC endpoints.</span></span>

## <a name="convert-servicecontract-to-a-grpc-service"></a><span data-ttu-id="d77dd-129">將 ServiceContract 轉換成 gRPC 服務</span><span class="sxs-lookup"><span data-stu-id="d77dd-129">Convert ServiceContract to a gRPC service</span></span>

<span data-ttu-id="d77dd-130">WCF `Get` 方法會採用兩個參數： `Guid traderId` 和 `int portfolioId` 。</span><span class="sxs-lookup"><span data-stu-id="d77dd-130">The WCF `Get` method takes two parameters: `Guid traderId` and `int portfolioId`.</span></span> <span data-ttu-id="d77dd-131">gRPC 服務方法只能採用單一參數，因此您必須建立訊息來保存兩個值。</span><span class="sxs-lookup"><span data-stu-id="d77dd-131">gRPC service methods can take only a single parameter, so you need to create a message to hold the two values.</span></span> <span data-ttu-id="d77dd-132">常見的作法是將這些要求物件命名為與方法相同的名稱，後面加上尾碼 `Request` 。</span><span class="sxs-lookup"><span data-stu-id="d77dd-132">It's common practice to name these request objects with the same name as the method followed by the suffix `Request`.</span></span> <span data-ttu-id="d77dd-133">同樣地， `string` 會將用於 `traderId` 欄位而不是 `Guid` 。</span><span class="sxs-lookup"><span data-stu-id="d77dd-133">Again, `string` is being used for the `traderId` field instead of `Guid`.</span></span>

<span data-ttu-id="d77dd-134">服務可以 `Portfolio` 直接傳回訊息，但同樣地，這可能會影響未來的回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="d77dd-134">The service could just return a `Portfolio` message directly, but again, this could affect backward compatibility in the future.</span></span> <span data-ttu-id="d77dd-135">`Request`針對服務中的每個方法定義個別和訊息是很好的作法 `Response` ，即使其中有許多也是相同的。</span><span class="sxs-lookup"><span data-stu-id="d77dd-135">It's a good practice to define separate `Request` and `Response` messages for every method in a service, even if many of them are the same right now.</span></span> <span data-ttu-id="d77dd-136">因此，請 `GetResponse` 使用單一欄位宣告訊息 `Portfolio` 。</span><span class="sxs-lookup"><span data-stu-id="d77dd-136">So declare a `GetResponse` message with a single `Portfolio` field.</span></span>

<span data-ttu-id="d77dd-137">此範例顯示 gRPC 服務方法的宣告，並顯示 `GetRequest` 下列訊息：</span><span class="sxs-lookup"><span data-stu-id="d77dd-137">This example shows the declaration of the gRPC service method with the `GetRequest` message:</span></span>

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

<span data-ttu-id="d77dd-138">WCF `GetAll` 方法只接受單一參數， `traderId` 因此您可能會將它指定 `string` 為參數類型。</span><span class="sxs-lookup"><span data-stu-id="d77dd-138">The WCF `GetAll` method takes only a single parameter, `traderId`, so it might seem that you could specify `string` as the parameter type.</span></span> <span data-ttu-id="d77dd-139">但是 gRPC 需要定義的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="d77dd-139">But gRPC requires a defined message type.</span></span> <span data-ttu-id="d77dd-140">這項需求有助於強制執行針對所有輸入和輸出使用自訂訊息的做法，以供未來回溯相容性之用。</span><span class="sxs-lookup"><span data-stu-id="d77dd-140">This requirement helps to enforce the practice of using custom messages for all inputs and outputs, for future backward compatibility.</span></span>

<span data-ttu-id="d77dd-141">WCF 方法也會傳回 `List<Portfolio>` ，但是基於相同的原因，它不允許簡單的參數類型，gRPC 不允許 `repeated Portfolio` 做為傳回型別。</span><span class="sxs-lookup"><span data-stu-id="d77dd-141">The WCF method also returns a `List<Portfolio>`, but for the same reason it doesn't allow simple parameter types, gRPC won't allow `repeated Portfolio` as a return type.</span></span> <span data-ttu-id="d77dd-142">請改為建立 `GetAllResponse` 包裝清單的型別。</span><span class="sxs-lookup"><span data-stu-id="d77dd-142">Instead, create a `GetAllResponse` type to wrap the list.</span></span>

> [!WARNING]
> <span data-ttu-id="d77dd-143">您可能會想要建立一個 `PortfolioList` 或類似的訊息，並在多個服務方法中使用它，但您應該要抵禦這個誘惑。</span><span class="sxs-lookup"><span data-stu-id="d77dd-143">You might be tempted to create a `PortfolioList` message or something similar and use it across multiple service methods, but you should resist this temptation.</span></span> <span data-ttu-id="d77dd-144">您不可能知道服務上的各種方法如何演進，讓他們的訊息保持明確且明確地分隔。</span><span class="sxs-lookup"><span data-stu-id="d77dd-144">It's impossible to know how the various methods on a service will evolve, so keep their messages specific and cleanly separated.</span></span>

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

<span data-ttu-id="d77dd-145">如果您使用這些變更來儲存專案，gRPC 組建目標將會在背景中執行，並產生所有 Protobuf 訊息類型，以及您可以繼承以執行服務的基類。</span><span class="sxs-lookup"><span data-stu-id="d77dd-145">If you save your project with these changes, the gRPC build target will run in the background and generate all the Protobuf message types and a base class that you can inherit to implement the service.</span></span>

<span data-ttu-id="d77dd-146">開啟 `Services/GreeterService.cs` 類別並刪除範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="d77dd-146">Open the `Services/GreeterService.cs` class and delete the example code.</span></span> <span data-ttu-id="d77dd-147">現在您可以新增組合服務的執行。</span><span class="sxs-lookup"><span data-stu-id="d77dd-147">Now you can add the Portfolio service implementation.</span></span> <span data-ttu-id="d77dd-148">產生的基類會在 `Protos` 命名空間中，並以嵌套類別的形式產生。</span><span class="sxs-lookup"><span data-stu-id="d77dd-148">The generated base class will be in the `Protos` namespace and is generated as a nested class.</span></span> <span data-ttu-id="d77dd-149">gRPC 會建立一個靜態類別，其名稱與檔案中的服務名稱相同， `.proto` 而基類中的基底類別具有尾碼 `Base` ，因此基底類型的完整識別碼為 `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase` 。</span><span class="sxs-lookup"><span data-stu-id="d77dd-149">gRPC creates a static class with the same name as the service in the `.proto` file and a base class with the suffix `Base` inside that static class, so the full identifier for the base type is `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase`.</span></span>

```csharp
namespace TraderSys.Portfolios.Services
{
    public class PortfolioService : Protos.Portfolios.PortfoliosBase
    {
    }
}
```

<span data-ttu-id="d77dd-150">基類 `virtual` `Get` 會宣告和的方法 `GetAll` ，可以覆寫以執行服務。</span><span class="sxs-lookup"><span data-stu-id="d77dd-150">The base class declares `virtual` methods for `Get` and `GetAll` that can be overridden to implement the service.</span></span> <span data-ttu-id="d77dd-151">這些方法不是 `virtual` `abstract` 如此，如果您未執行這些方法，則服務會傳回明確的 gRPC `Unimplemented` 狀態碼，就像您可能會 `NotImplementedException` 在一般的 c # 程式碼中擲回。</span><span class="sxs-lookup"><span data-stu-id="d77dd-151">The methods are `virtual` rather than `abstract` so that if you don't implement them, the service can return an explicit gRPC `Unimplemented` status code, much like you might throw a `NotImplementedException` in regular C# code.</span></span>

<span data-ttu-id="d77dd-152">ASP.NET Core 中所有 gRPC 一元服務方法的簽章都是一致的。</span><span class="sxs-lookup"><span data-stu-id="d77dd-152">The signature for all gRPC unary service methods in ASP.NET Core is consistent.</span></span> <span data-ttu-id="d77dd-153">有兩個參數：第一個是在檔案中宣告的訊息類型 `.proto` ，而第二個則是 `ServerCallContext` ，其運作方式類似于 `HttpContext` ASP.NET Core 的。</span><span class="sxs-lookup"><span data-stu-id="d77dd-153">There are two parameters: the first is the message type declared in the `.proto` file, and the second is a `ServerCallContext` that works similarly to the `HttpContext` from ASP.NET Core.</span></span> <span data-ttu-id="d77dd-154">事實上， `GetHttpContext` `ServerCallContext` 您可以使用類別上的擴充方法來取得基礎 `HttpContext` ，雖然您不需要經常使用它。</span><span class="sxs-lookup"><span data-stu-id="d77dd-154">In fact, there's an extension method called `GetHttpContext` on the `ServerCallContext` class that you can use to get the underlying `HttpContext`, although you shouldn't need to use it often.</span></span> <span data-ttu-id="d77dd-155">我們將在本章 `ServerCallContext` 稍後討論，並在討論驗證的章節中探討。</span><span class="sxs-lookup"><span data-stu-id="d77dd-155">We'll take a look at `ServerCallContext` later in this chapter, and also in the chapter that discusses authentication.</span></span>

<span data-ttu-id="d77dd-156">方法的傳回型別是 `Task<T>` ，其中 `T` 是回應訊息類型。</span><span class="sxs-lookup"><span data-stu-id="d77dd-156">The method's return type is a `Task<T>`, where `T` is the response message type.</span></span> <span data-ttu-id="d77dd-157">所有 gRPC 服務方法都是非同步。</span><span class="sxs-lookup"><span data-stu-id="d77dd-157">All gRPC service methods are asynchronous.</span></span>

## <a name="migrate-the-portfoliodata-library-to-net"></a><span data-ttu-id="d77dd-158">將 PortfolioData 程式庫遷移至 .NET</span><span class="sxs-lookup"><span data-stu-id="d77dd-158">Migrate the PortfolioData library to .NET</span></span>

<span data-ttu-id="d77dd-159">此時，專案需要 `TraderSys.PortfolioData` WCF 方案中類別庫中所包含的組合存放庫和模型。</span><span class="sxs-lookup"><span data-stu-id="d77dd-159">At this point, the project needs the Portfolio repository and models contained in the `TraderSys.PortfolioData` class library in the WCF solution.</span></span> <span data-ttu-id="d77dd-160">Visual Studio 使用 [ **新增專案** ] 對話方塊和 [類別庫] ( .NET Standard) 範本，或從命令列使用 .NET Core CLI 從命令列執行下列命令，以將它們帶到最簡單的方式，就是建立新的類別庫 `TraderSys.sln` ：</span><span class="sxs-lookup"><span data-stu-id="d77dd-160">The easiest way to bring them across is to create a new class library by using either the Visual Studio **New project** dialog box with the Class Library (.NET Standard) template, or from the command line by using the .NET Core CLI, running these commands from the directory that contains the `TraderSys.sln` file:</span></span>

```dotnetcli
dotnet new classlib -o src/TraderSys.PortfolioData
dotnet sln add src/TraderSys.PortfolioData
```

<span data-ttu-id="d77dd-161">當您建立程式庫並將它新增至方案之後，請刪除產生的檔案， `Class1.cs` 並將檔案從 WCF 解決方案的程式庫複製到新的類別庫資料夾中，並保留資料夾結構：</span><span class="sxs-lookup"><span data-stu-id="d77dd-161">After you've created the library and added it to the solution, delete the generated `Class1.cs` file and copy the files from the WCF solution's library into the new class library's folder, keeping the folder structure:</span></span>

```
Models
  Portfolio.cs
  PortfolioItem.cs
IPortfolioRepository.cs
PortfolioRepository.cs
```

<span data-ttu-id="d77dd-162">SDK 樣式的 .NET 專案會自動 `.cs` 在自己的目錄中包含任何檔案，因此您不需要明確地將它們新增至專案。</span><span class="sxs-lookup"><span data-stu-id="d77dd-162">SDK-style .NET projects automatically include any `.cs` files in or under their own directory, so you don't need to explicitly add them to the project.</span></span> <span data-ttu-id="d77dd-163">剩下的唯一步驟是 `DataContract` `DataMember` 從和類別中移除和屬性 `Portfolio` ， `PortfolioItem` 讓它們是一般的 c # 類別：</span><span class="sxs-lookup"><span data-stu-id="d77dd-163">The only step remaining is to remove the `DataContract` and `DataMember` attributes from the `Portfolio` and `PortfolioItem` classes so they're plain old C# classes:</span></span>

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

## <a name="use-aspnet-core-dependency-injection"></a><span data-ttu-id="d77dd-164">使用 ASP.NET Core 相依性插入</span><span class="sxs-lookup"><span data-stu-id="d77dd-164">Use ASP.NET Core dependency injection</span></span>

<span data-ttu-id="d77dd-165">現在您可以將此程式庫的參考新增至 gRPC 應用程式專案，並 `PortfolioRepository` 使用 gRPC 服務執行中的相依性插入來取用類別。</span><span class="sxs-lookup"><span data-stu-id="d77dd-165">Now you can add a reference to this library to the gRPC application project and consume the `PortfolioRepository` class by using dependency injection in the gRPC service implementation.</span></span> <span data-ttu-id="d77dd-166">在 WCF 應用程式中，相依性插入是由 Autofac IoC 容器所提供。</span><span class="sxs-lookup"><span data-stu-id="d77dd-166">In the WCF application, dependency injection was provided by the Autofac IoC container.</span></span> <span data-ttu-id="d77dd-167">ASP.NET Core 在中具有相依性插入內建。</span><span class="sxs-lookup"><span data-stu-id="d77dd-167">ASP.NET Core has dependency injection baked in.</span></span> <span data-ttu-id="d77dd-168">您可以在類別的方法中註冊存放庫 `ConfigureServices` `Startup` ：</span><span class="sxs-lookup"><span data-stu-id="d77dd-168">You can register the repository in the `ConfigureServices` method in the `Startup` class:</span></span>

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

<span data-ttu-id="d77dd-169">您 `IPortfolioRepository` 現在可以在類別中將此實作為函式參數來指定，如下所示 `PortfolioService` ：</span><span class="sxs-lookup"><span data-stu-id="d77dd-169">The `IPortfolioRepository` implementation can now be specified as a constructor parameter in the `PortfolioService` class, as follows:</span></span>

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

## <a name="implement-the-grpc-service"></a><span data-ttu-id="d77dd-170">執行 gRPC 服務</span><span class="sxs-lookup"><span data-stu-id="d77dd-170">Implement the gRPC service</span></span>

<span data-ttu-id="d77dd-171">現在您已在檔案中宣告訊息和服務 `portfolios.proto` ，您必須在 `PortfolioService` 繼承自 gRPC 產生之類別的類別中，執行服務方法 `Portfolios.PortfoliosBase` 。</span><span class="sxs-lookup"><span data-stu-id="d77dd-171">Now that you've declared your messages and your service in the `portfolios.proto` file, you have to implement the service methods in the `PortfolioService` class that inherits from the gRPC-generated `Portfolios.PortfoliosBase` class.</span></span> <span data-ttu-id="d77dd-172">方法會 `virtual` 在基類中宣告為。</span><span class="sxs-lookup"><span data-stu-id="d77dd-172">The methods are declared as `virtual` in the base class.</span></span> <span data-ttu-id="d77dd-173">如果您未加以覆寫，則預設會傳回 gRPC 「未執行」狀態碼。</span><span class="sxs-lookup"><span data-stu-id="d77dd-173">If you don't override them, they'll return a gRPC "Not Implemented" status code by default.</span></span>

<span data-ttu-id="d77dd-174">首先，請執行 `Get` 方法。</span><span class="sxs-lookup"><span data-stu-id="d77dd-174">Start by implementing the `Get` method.</span></span> <span data-ttu-id="d77dd-175">預設覆寫看起來如以下範例所示：</span><span class="sxs-lookup"><span data-stu-id="d77dd-175">The default override looks like this example:</span></span>

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    return base.Get(request, context);
}
```

<span data-ttu-id="d77dd-176">第一個問題是 `request.TraderId` 字串，而服務需要 `Guid` 。</span><span class="sxs-lookup"><span data-stu-id="d77dd-176">The first problem is that `request.TraderId` is a string, and the service requires a `Guid`.</span></span> <span data-ttu-id="d77dd-177">雖然字串的預期格式為 `UUID` ，但是程式碼必須處理呼叫端傳送無效值並適當回應的可能性。</span><span class="sxs-lookup"><span data-stu-id="d77dd-177">Even though the expected format for the string is `UUID`, the code has to deal with the possibility that a caller has sent an invalid value and respond appropriately.</span></span> <span data-ttu-id="d77dd-178">服務可以擲回 `RpcException` ，並使用標準 `InvalidArgument` 狀態碼來表達問題，以回應錯誤：</span><span class="sxs-lookup"><span data-stu-id="d77dd-178">The service can respond with errors by throwing an `RpcException` and use the standard `InvalidArgument` status code to express the problem:</span></span>

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

<span data-ttu-id="d77dd-179">在有適當的 `Guid` 值之後 `traderId` ，您可以使用存放庫來取出組合，並將其傳回給用戶端：</span><span class="sxs-lookup"><span data-stu-id="d77dd-179">After there's a proper `Guid` value for `traderId`, you can use the repository to retrieve the Portfolio and return it to the client:</span></span>

```csharp
    var response = new GetResponse
    {
        Portfolio = await _repository.GetAsync(request.TraderId, request.PortfolioId)
    };
```

### <a name="map-internal-models-to-grpc-messages"></a><span data-ttu-id="d77dd-180">將內部模型對應至 gRPC 訊息</span><span class="sxs-lookup"><span data-stu-id="d77dd-180">Map internal models to gRPC messages</span></span>

<span data-ttu-id="d77dd-181">先前的程式碼並不會實際運作，因為存放庫會傳回自己的 POCO 模型 `Portfolio` ，但 gRPC 需要自己的 Protobuf 訊息 `Portfolio` 。</span><span class="sxs-lookup"><span data-stu-id="d77dd-181">The previous code doesn't actually work because the repository is returning its own POCO model `Portfolio`, but gRPC needs its own Protobuf message `Portfolio`.</span></span> <span data-ttu-id="d77dd-182">當您將 Entity Framework 類型對應到資料傳輸類型時，最好的解決方法是在兩者之間提供轉換。</span><span class="sxs-lookup"><span data-stu-id="d77dd-182">As when you map Entity Framework types to data transfer types, the best solution is to provide a conversion between the two.</span></span> <span data-ttu-id="d77dd-183">將這項轉換的程式碼放在 Protobuf 產生的類別中是一個很好的位置，它會宣告為 `partial` 類別，以便進行擴充：</span><span class="sxs-lookup"><span data-stu-id="d77dd-183">A good place to put the code for this conversion is in the Protobuf-generated class, which is declared as a `partial` class so it can be extended:</span></span>

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
> <span data-ttu-id="d77dd-184">您可以使用程式庫（例如[AutoMapper](https://automapper.org/) ）來處理從內部模型類別到 Protobuf 類型的轉換，只要您設定較低層級的類型轉換（例如 `string` / `Guid` 或 `decimal` / `double` 和清單對應）即可。</span><span class="sxs-lookup"><span data-stu-id="d77dd-184">You could use a library like [AutoMapper](https://automapper.org/) to handle this conversion from internal model classes to Protobuf types, as long as you configure the lower-level type conversions like `string`/`Guid` or `decimal`/`double` and the list mapping.</span></span>

<span data-ttu-id="d77dd-185">現在您已備妥轉換程式碼，您可以完成方法執行 `Get` ：</span><span class="sxs-lookup"><span data-stu-id="d77dd-185">Now that you have the conversion code in place, you can complete the `Get` method implementation:</span></span>

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

<span data-ttu-id="d77dd-186">方法的執行 `GetAll` 方式很類似。</span><span class="sxs-lookup"><span data-stu-id="d77dd-186">The implementation of the `GetAll` method is similar.</span></span> <span data-ttu-id="d77dd-187">請注意， `repeated` Protobuf 訊息上的欄位會產生為 `readonly` 類型的屬性 `RepeatedField<T>` ，因此您必須使用方法將專案加入至這些欄位 `AddRange` ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="d77dd-187">Note that the `repeated` fields on Protobuf messages are generated as `readonly` properties of type `RepeatedField<T>`, so you have to add items to them by using the `AddRange` method, like in this example:</span></span>

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

<span data-ttu-id="d77dd-188">成功將 WCF 要求-回復服務遷移至 gRPC 之後，讓我們看看如何從檔案建立用戶端 `.proto` 。</span><span class="sxs-lookup"><span data-stu-id="d77dd-188">Having successfully migrated the WCF request-reply service to gRPC, let's look at creating a client for it from the `.proto` file.</span></span>

## <a name="generate-client-code"></a><span data-ttu-id="d77dd-189">產生用戶端程式代碼</span><span class="sxs-lookup"><span data-stu-id="d77dd-189">Generate client code</span></span>

<span data-ttu-id="d77dd-190">在相同方案中建立 .NET Standard 類別庫以包含用戶端。</span><span class="sxs-lookup"><span data-stu-id="d77dd-190">Create a .NET Standard class library in the same solution to contain the client.</span></span> <span data-ttu-id="d77dd-191">這主要是建立用戶端程式代碼的範例，但您可以使用 NuGet 封裝這類程式庫，並將其散發至內部儲存機制，以供其他 .NET 小組使用。</span><span class="sxs-lookup"><span data-stu-id="d77dd-191">This is primarily an example of creating client code, but you could package such a library by using NuGet and distribute it on an internal repository for other .NET teams to consume.</span></span> <span data-ttu-id="d77dd-192">繼續進行，並將名為的新 .NET Standard 類別庫加入 `TraderSys.Portfolios.Client` 至方案，然後刪除該檔案 `Class1.cs` 。</span><span class="sxs-lookup"><span data-stu-id="d77dd-192">Go ahead and add a new .NET Standard class library called `TraderSys.Portfolios.Client` to the solution and delete the `Class1.cs` file.</span></span>

> [!CAUTION]
> <span data-ttu-id="d77dd-193">[Grpc .net. 用戶端](https://www.nuget.org/packages/Grpc.Net.Client)NuGet 套件需要 .net Core 3.0 或更新版本 (或其他 .NET Standard 2.1 相容的執行時間) 。</span><span class="sxs-lookup"><span data-stu-id="d77dd-193">The [Grpc.Net.Client](https://www.nuget.org/packages/Grpc.Net.Client) NuGet package requires .NET Core 3.0 or later (or another .NET Standard 2.1-compliant runtime).</span></span> <span data-ttu-id="d77dd-194">Grpc 和 .NET Core 的舊版 .NET Framework 和 .NET Core 是由 [Core](https://www.nuget.org/packages/Grpc.Core) NuGet 套件支援。</span><span class="sxs-lookup"><span data-stu-id="d77dd-194">Earlier versions of .NET Framework and .NET Core are supported by the [Grpc.Core](https://www.nuget.org/packages/Grpc.Core) NuGet package.</span></span>

<span data-ttu-id="d77dd-195">在 Visual Studio 2019 中，您可以將參考新增至 gRPC 服務，其方式類似于將服務參考加入至舊版 Visual Studio 的 WCF 專案。</span><span class="sxs-lookup"><span data-stu-id="d77dd-195">In Visual Studio 2019, you can add references to gRPC services in a way that's similar to how you'd add service references to WCF projects in earlier versions of Visual Studio.</span></span> <span data-ttu-id="d77dd-196">服務參考和已聯機服務現在都是在相同的 UI 下進行管理。</span><span class="sxs-lookup"><span data-stu-id="d77dd-196">Service references and connected services are all managed under the same UI now.</span></span> <span data-ttu-id="d77dd-197">您可以用滑鼠右鍵按一下 [方案總管 **]** 中專案的 [相依性] 節點 `TraderSys.Portfolios.Client` ，然後選取 [ **加入已連接服務**]，來存取 UI。</span><span class="sxs-lookup"><span data-stu-id="d77dd-197">You can access the UI by right-clicking the **Dependencies** node in the `TraderSys.Portfolios.Client` project in Solution Explorer and selecting **Add Connected Service**.</span></span> <span data-ttu-id="d77dd-198">在出現的工具視窗中，選取 [ **服務參考** ] 區段，然後選取 [ **新增 gRPC 服務參考**]：</span><span class="sxs-lookup"><span data-stu-id="d77dd-198">In the tool window that appears, select the **Service References** section and then select **Add new gRPC service reference**:</span></span>

![Visual Studio 2019 中的已連線的服務 UI](media/migrate-request-reply/add-connected-service.png)

<span data-ttu-id="d77dd-200">流覽至 `portfolios.proto` 專案中的檔案 `TraderSys.Portfolios` ，讓 **用戶端** 保持在 [ **選取要產生的類別類型**] 下，然後選取 **[確定]**：</span><span class="sxs-lookup"><span data-stu-id="d77dd-200">Browse to the `portfolios.proto` file in the `TraderSys.Portfolios` project, leave **Client** under **Select the type of class to be generated**, and then select **OK**:</span></span>

![Visual Studio 2019 中的 [新增 gRPC 服務參考] 對話方塊](media/migrate-request-reply/add-new-grpc-service-reference.png)

> [!TIP]
> <span data-ttu-id="d77dd-202">請注意，此對話方塊也會提供 URL 欄位。</span><span class="sxs-lookup"><span data-stu-id="d77dd-202">Notice that this dialog box also provides a URL field.</span></span> <span data-ttu-id="d77dd-203">如果您的組織維護 web 可存取的目錄 `.proto` ，您只要設定此 URL 位址，就可以建立用戶端。</span><span class="sxs-lookup"><span data-stu-id="d77dd-203">If your organization maintains a web-accessible directory of `.proto` files, you can create clients just by setting this URL address.</span></span>

<span data-ttu-id="d77dd-204">當您使用 Visual Studio **加入已連接服務** ] 功能時，會將檔案 `portfolios.proto` 新增至類別庫專案做為 *連結* 的檔案，而不是複製，因此服務專案中檔案的變更會自動套用至用戶端專案。</span><span class="sxs-lookup"><span data-stu-id="d77dd-204">When you use the Visual Studio **Add Connected Service** feature, the `portfolios.proto` file is added to the class library project as a *linked file* rather than copied, so changes to the file in the service project will automatically be applied in the client project.</span></span> <span data-ttu-id="d77dd-205">檔案 `<Protobuf>` 中的元素 `csproj` 看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="d77dd-205">The `<Protobuf>` element in the `csproj` file looks like this:</span></span>

```xml
<Protobuf Include="..\TraderSys.Portfolios\Protos\portfolios.proto" GrpcServices="Client">
  <Link>Protos\portfolios.proto</Link>
</Protobuf>
```

> [!TIP]
> <span data-ttu-id="d77dd-206">如果您不是使用 Visual Studio 或偏好從命令列工作，您可以使用 `dotnet-grpc` 全域工具來管理 .Net gRPC 專案中的 Protobuf 參考。</span><span class="sxs-lookup"><span data-stu-id="d77dd-206">If you're not using Visual Studio or prefer to work from the command line, you can use the `dotnet-grpc` global tool to manage Protobuf references in a .NET gRPC project.</span></span> <span data-ttu-id="d77dd-207">如需詳細資訊，請參閱[ `dotnet-grpc` 檔](/aspnet/core/grpc/dotnet-grpc)。</span><span class="sxs-lookup"><span data-stu-id="d77dd-207">For more information, see the [`dotnet-grpc` documentation](/aspnet/core/grpc/dotnet-grpc).</span></span>

### <a name="use-the-portfolios-service-from-a-client-application"></a><span data-ttu-id="d77dd-208">從用戶端應用程式使用組合服務</span><span class="sxs-lookup"><span data-stu-id="d77dd-208">Use the Portfolios service from a client application</span></span>

<span data-ttu-id="d77dd-209">下列程式碼是如何在主控台應用程式中使用產生的用戶端的簡單範例。</span><span class="sxs-lookup"><span data-stu-id="d77dd-209">The following code is a brief example of how to use the generated client in a console application.</span></span> <span data-ttu-id="d77dd-210">GRPC 用戶端程式代碼的更詳細探索是在本章結尾。</span><span class="sxs-lookup"><span data-stu-id="d77dd-210">A more detailed exploration of the gRPC client code is at the end of this chapter.</span></span>

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

<span data-ttu-id="d77dd-211">您現在已將基本 WCF 應用程式遷移至 ASP.NET Core 的 gRPC 服務，並建立了從 .NET 應用程式取用服務的用戶端。</span><span class="sxs-lookup"><span data-stu-id="d77dd-211">You've now migrated a basic WCF application to an ASP.NET Core gRPC service and created a client to consume the service from a .NET application.</span></span> <span data-ttu-id="d77dd-212">下一節將涵蓋更多的雙工服務。</span><span class="sxs-lookup"><span data-stu-id="d77dd-212">The next section will cover the more involved duplex services.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d77dd-213">[上一個](create-project.md) 
>[下一步](migrate-duplex-services.md)</span><span class="sxs-lookup"><span data-stu-id="d77dd-213">[Previous](create-project.md)
[Next](migrate-duplex-services.md)</span></span>
