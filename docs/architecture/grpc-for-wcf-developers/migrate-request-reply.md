---
title: 將 WCF 要求-回復服務遷移至 WCF 開發人員的 gRPC-gRPC
description: 瞭解如何將簡單的要求-回復服務從 WCF 遷移至 gRPC。
ms.date: 09/02/2019
ms.openlocfilehash: 018aa94a15cdcb1e0f559afb7b3a88cd4f915398
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628549"
---
# <a name="migrate-a-wcf-request-reply-service-to-a-grpc-unary-rpc"></a><span data-ttu-id="709f9-103">將 WCF 要求-回復服務遷移至 gRPC 一元 RPC</span><span class="sxs-lookup"><span data-stu-id="709f9-103">Migrate a WCF request-reply service to a gRPC unary RPC</span></span>

<span data-ttu-id="709f9-104">本節說明如何在 ASP.NET Core gRPC 中，將 WCF 中的基本要求-回復服務遷移至一元 RPC 服務。</span><span class="sxs-lookup"><span data-stu-id="709f9-104">This section covers how to migrate a basic request-reply service in WCF to a unary RPC service in ASP.NET Core gRPC.</span></span> <span data-ttu-id="709f9-105">這些服務是 Windows Communication Foundation （WCF）和 gRPC 中最簡單的服務類型，因此是很好的起點。</span><span class="sxs-lookup"><span data-stu-id="709f9-105">These services are the simplest service types in both Windows Communication Foundation (WCF) and gRPC, so it's an excellent place to start.</span></span> <span data-ttu-id="709f9-106">遷移服務之後，您將瞭解如何從相同的 `.proto` 檔案產生用戶端程式庫，以便從 .NET 用戶端應用程式取用服務。</span><span class="sxs-lookup"><span data-stu-id="709f9-106">After migrating the service, you'll learn how to generate a client library from the same `.proto` file to consume the service from a .NET client application.</span></span>

## <a name="the-wcf-solution"></a><span data-ttu-id="709f9-107">WCF 解決方案</span><span class="sxs-lookup"><span data-stu-id="709f9-107">The WCF solution</span></span>

<span data-ttu-id="709f9-108">[PortfoliosSample 解決方案](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys)包含簡單的要求-回復組合服務，可針對指定的 trader 下載單一組合或所有公事包。</span><span class="sxs-lookup"><span data-stu-id="709f9-108">The [PortfoliosSample solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys) includes a simple request-reply Portfolio service to download either a single portfolio or all portfolios for a given trader.</span></span> <span data-ttu-id="709f9-109">服務是在介面 `IPortfolioService` 中以 `ServiceContract` 屬性定義的：</span><span class="sxs-lookup"><span data-stu-id="709f9-109">The service is defined in the interface `IPortfolioService` with a `ServiceContract` attribute:</span></span>

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

<span data-ttu-id="709f9-110">`Portfolio` 模型是以[DataContract](xref:System.Runtime.Serialization.DataContractAttribute)標記C#的簡單類別，其中包含 `PortfolioItem` 物件的清單。</span><span class="sxs-lookup"><span data-stu-id="709f9-110">The `Portfolio` model is a simple C# class marked with [DataContract](xref:System.Runtime.Serialization.DataContractAttribute) and including a list of `PortfolioItem` objects.</span></span> <span data-ttu-id="709f9-111">這些模型會在 `TraderSys.PortfolioData` 專案中定義，以及代表資料存取抽象的儲存機制類別。</span><span class="sxs-lookup"><span data-stu-id="709f9-111">These models are defined in the `TraderSys.PortfolioData` project along with a repository class that represents a data access abstraction.</span></span>

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

<span data-ttu-id="709f9-112">`ServiceContract` 的執行會使用透過相依性插入所提供的存放庫類別，以傳回 `DataContract` 類型的實例：</span><span class="sxs-lookup"><span data-stu-id="709f9-112">The `ServiceContract` implementation uses a repository class provided via dependency injection that returns instances of the `DataContract` types:</span></span>

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

## <a name="the-portfoliosproto-file"></a><span data-ttu-id="709f9-113">組合的 proto 檔案</span><span class="sxs-lookup"><span data-stu-id="709f9-113">The portfolios.proto file</span></span>

<span data-ttu-id="709f9-114">如果您遵循上一節中的指示進行，您應該會有一個具有 `portfolios.proto` 檔案的 gRPC 專案，如下所示：</span><span class="sxs-lookup"><span data-stu-id="709f9-114">If you followed the instructions in the previous section, you should have a gRPC project with a `portfolios.proto` file that looks like this:</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

<span data-ttu-id="709f9-115">第一個步驟是將 `DataContract` 類別遷移至其 Protobuf 對應專案。</span><span class="sxs-lookup"><span data-stu-id="709f9-115">The first step is to migrate the `DataContract` classes to their Protobuf equivalents.</span></span>

## <a name="convert-the-datacontract-classes-to-grpc-messages"></a><span data-ttu-id="709f9-116">將 DataContract 類別轉換成 gRPC 訊息</span><span class="sxs-lookup"><span data-stu-id="709f9-116">Convert the DataContract classes to gRPC messages</span></span>

<span data-ttu-id="709f9-117">`PortfolioItem` 類別會先轉換成 Protobuf 訊息，因為 `Portfolio` 類別相依于它。</span><span class="sxs-lookup"><span data-stu-id="709f9-117">The `PortfolioItem` class will be converted to a Protobuf message first, because the `Portfolio` class depends on it.</span></span> <span data-ttu-id="709f9-118">此類別很簡單，而三個屬性會直接對應至 gRPC 資料類型。</span><span class="sxs-lookup"><span data-stu-id="709f9-118">The class is simple, and three of the properties map directly to gRPC data types.</span></span> <span data-ttu-id="709f9-119">[`Cost`] 屬性（代表購買的股份所支付的價格）是 `decimal` 欄位。</span><span class="sxs-lookup"><span data-stu-id="709f9-119">The `Cost` property, which represents the price paid for the shares at purchase, is a `decimal` field.</span></span> <span data-ttu-id="709f9-120">gRPC 僅支援針對貨幣不適用的實數 `float` 或 `double`。</span><span class="sxs-lookup"><span data-stu-id="709f9-120">gRPC supports only `float` or `double` for real numbers, which aren't suitable for currency.</span></span> <span data-ttu-id="709f9-121">由於共用價格的差異最少一美分，因此成本會以一 `int32` 美分來表示。</span><span class="sxs-lookup"><span data-stu-id="709f9-121">Because share prices vary by a minimum of one cent, the cost can be expressed as an `int32` of cents.</span></span>

> [!NOTE]
> <span data-ttu-id="709f9-122">請記得在 `.proto` 檔案中使用 camelCase 做為功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="709f9-122">Remember to use camelCase for field names in your `.proto` file.</span></span> <span data-ttu-id="709f9-123">程式C#代碼產生器會為您將它們轉換成 PascalCase，而其他語言的使用者則會感謝您遵守其不同的編碼標準。</span><span class="sxs-lookup"><span data-stu-id="709f9-123">The C# code generator will convert them to PascalCase for you, and users of other languages will thank you for respecting their different coding standards.</span></span>

```protobuf
message PortfolioItem {
    int32 id = 1;
    int32 share_id = 2;
    int32 holding = 3;
    int32 cost_cents = 4;
}
```

<span data-ttu-id="709f9-124">`Portfolio` 類別稍微複雜一點。</span><span class="sxs-lookup"><span data-stu-id="709f9-124">The `Portfolio` class is a little more complicated.</span></span> <span data-ttu-id="709f9-125">在 WCF 程式碼中，開發人員使用 `TraderId` 屬性的 `Guid`，並包含 `List<PortfolioItem>`。</span><span class="sxs-lookup"><span data-stu-id="709f9-125">In the WCF code, the developer used a `Guid` for the `TraderId` property, and contains a `List<PortfolioItem>`.</span></span> <span data-ttu-id="709f9-126">在沒有第一級 `UUID` 類型的 Protobuf 中，您應該使用 `traderId` 欄位的 `string`，並在您自己的程式碼中進行剖析。</span><span class="sxs-lookup"><span data-stu-id="709f9-126">In Protobuf, which doesn't have a first-class `UUID` type, you should use a `string` for the `traderId` field and parse it in your own code.</span></span> <span data-ttu-id="709f9-127">針對專案清單，請使用欄位上的 `repeated` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="709f9-127">For the list of items, use the `repeated` keyword on the field.</span></span>

```protobuf
message Portfolio {
    int32 id = 1;
    string trader_id = 2;
    repeated PortfolioItem items = 3;
}
```

<span data-ttu-id="709f9-128">現在您已有資料訊息，可以宣告服務 RPC 端點。</span><span class="sxs-lookup"><span data-stu-id="709f9-128">Now that you have the data messages, you can declare the service RPC endpoints.</span></span>

## <a name="convert-servicecontract-to-a-grpc-service"></a><span data-ttu-id="709f9-129">將 ServiceContract 轉換成 gRPC 服務</span><span class="sxs-lookup"><span data-stu-id="709f9-129">Convert ServiceContract to a gRPC service</span></span>

<span data-ttu-id="709f9-130">WCF `Get` 方法會採用兩個參數： `Guid traderId` 和 `int portfolioId`。</span><span class="sxs-lookup"><span data-stu-id="709f9-130">The WCF `Get` method takes two parameters: `Guid traderId` and `int portfolioId`.</span></span> <span data-ttu-id="709f9-131">gRPC 服務方法只能採用單一參數，因此您必須建立訊息來保存這兩個值。</span><span class="sxs-lookup"><span data-stu-id="709f9-131">gRPC service methods can take only a single parameter, so you need to create a message to hold the two values.</span></span> <span data-ttu-id="709f9-132">常見的做法是使用與方法相同的名稱來命名這些要求物件，並在後面加上尾碼 `Request`。</span><span class="sxs-lookup"><span data-stu-id="709f9-132">It's common practice to name these request objects with the same name as the method followed by the suffix `Request`.</span></span> <span data-ttu-id="709f9-133">同樣地，`string` 用於 `traderId` 欄位，而不是 `Guid`。</span><span class="sxs-lookup"><span data-stu-id="709f9-133">Again, `string` is being used for the `traderId` field instead of `Guid`.</span></span>

<span data-ttu-id="709f9-134">服務可以直接傳回 `Portfolio` 訊息，但同樣地，這可能會影響未來的回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="709f9-134">The service could just return a `Portfolio` message directly, but again, this could affect backward compatibility in the future.</span></span> <span data-ttu-id="709f9-135">針對服務中的每個方法定義個別的 `Request` 和 `Response` 訊息是很好的作法，即使其中有許多都是相同的。</span><span class="sxs-lookup"><span data-stu-id="709f9-135">It's a good practice to define separate `Request` and `Response` messages for every method in a service, even if many of them are the same right now.</span></span> <span data-ttu-id="709f9-136">因此，請使用單一 `Portfolio` 欄位宣告 `GetResponse` 訊息。</span><span class="sxs-lookup"><span data-stu-id="709f9-136">So declare a `GetResponse` message with a single `Portfolio` field.</span></span>

<span data-ttu-id="709f9-137">這個範例會顯示 gRPC 服務方法的宣告與 `GetRequest` 訊息：</span><span class="sxs-lookup"><span data-stu-id="709f9-137">This example shows the declaration of the gRPC service method with the `GetRequest` message:</span></span>

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

<span data-ttu-id="709f9-138">WCF `GetAll` 方法只接受單一參數，`traderId`，因此您似乎可以指定 `string` 做為參數類型。</span><span class="sxs-lookup"><span data-stu-id="709f9-138">The WCF `GetAll` method takes only a single parameter, `traderId`, so it might seem that you could specify `string` as the parameter type.</span></span> <span data-ttu-id="709f9-139">但 gRPC 需要定義的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="709f9-139">But gRPC requires a defined message type.</span></span> <span data-ttu-id="709f9-140">這項需求有助於強制執行針對所有輸入和輸出使用自訂訊息的作法，以供未來回溯相容性之用。</span><span class="sxs-lookup"><span data-stu-id="709f9-140">This requirement helps to enforce the practice of using custom messages for all inputs and outputs, for future backward compatibility.</span></span>

<span data-ttu-id="709f9-141">WCF 方法也會傳回 `List<Portfolio>`，但基於相同的原因，它不允許簡單的參數類型，gRPC 不允許 `repeated Portfolio` 做為傳回類型。</span><span class="sxs-lookup"><span data-stu-id="709f9-141">The WCF method also returns a `List<Portfolio>`, but for the same reason it doesn't allow simple parameter types, gRPC won't allow `repeated Portfolio` as a return type.</span></span> <span data-ttu-id="709f9-142">相反地，請建立 `GetAllResponse` 類型來包裝清單。</span><span class="sxs-lookup"><span data-stu-id="709f9-142">Instead, create a `GetAllResponse` type to wrap the list.</span></span>

> [!WARNING]
> <span data-ttu-id="709f9-143">您可能會想要建立 `PortfolioList` 訊息或類似的內容，並在多個服務方法中使用它，但您應該不會受到這個誘惑的抵觸。</span><span class="sxs-lookup"><span data-stu-id="709f9-143">You might be tempted to create a `PortfolioList` message or something similar and use it across multiple service methods, but you should resist this temptation.</span></span> <span data-ttu-id="709f9-144">不可能知道服務上的各種方法會如何演變，因此請將它們的訊息指定為明確且完全分隔。</span><span class="sxs-lookup"><span data-stu-id="709f9-144">It's impossible to know how the various methods on a service will evolve, so keep their messages specific and cleanly separated.</span></span>

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

<span data-ttu-id="709f9-145">如果您使用這些變更來儲存專案，則 gRPC 組建目標會在背景中執行，並產生所有 Protobuf 訊息類型，以及您可以繼承以執行服務的基類。</span><span class="sxs-lookup"><span data-stu-id="709f9-145">If you save your project with these changes, the gRPC build target will run in the background and generate all the Protobuf message types and a base class that you can inherit to implement the service.</span></span>

<span data-ttu-id="709f9-146">開啟 `Services/GreeterService.cs` 類別，並刪除範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="709f9-146">Open the `Services/GreeterService.cs` class and delete the example code.</span></span> <span data-ttu-id="709f9-147">現在您可以加入「公事包服務」執行。</span><span class="sxs-lookup"><span data-stu-id="709f9-147">Now you can add the Portfolio service implementation.</span></span> <span data-ttu-id="709f9-148">產生的基類將會在 `Protos` 命名空間中，並以嵌套類別的形式產生。</span><span class="sxs-lookup"><span data-stu-id="709f9-148">The generated base class will be in the `Protos` namespace and is generated as a nested class.</span></span> <span data-ttu-id="709f9-149">gRPC 會建立與 `.proto` 檔案中的服務同名的靜態類別，以及在該靜態類別內具有尾碼 `Base` 的基類，因此會 `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase`基底類型的完整識別碼。</span><span class="sxs-lookup"><span data-stu-id="709f9-149">gRPC creates a static class with the same name as the service in the `.proto` file and a base class with the suffix `Base` inside that static class, so the full identifier for the base type is `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase`.</span></span>

```csharp
namespace TraderSys.Portfolios.Services
{
    public class PortfolioService : Protos.Portfolios.PortfoliosBase
    {
    }
}
```

<span data-ttu-id="709f9-150">基類會針對可覆寫以執行服務的 `Get` 和 `GetAll`，宣告 `virtual` 方法。</span><span class="sxs-lookup"><span data-stu-id="709f9-150">The base class declares `virtual` methods for `Get` and `GetAll` that can be overridden to implement the service.</span></span> <span data-ttu-id="709f9-151">方法 `virtual`，而不是 `abstract`，因此，如果您未加以執行，服務會傳回明確的 gRPC `Unimplemented` 狀態碼，與您可能會在一般C#程式碼中擲回 `NotImplementedException` 很類似。</span><span class="sxs-lookup"><span data-stu-id="709f9-151">The methods are `virtual` rather than `abstract` so that if you don't implement them, the service can return an explicit gRPC `Unimplemented` status code, much like you might throw a `NotImplementedException` in regular C# code.</span></span>

<span data-ttu-id="709f9-152">ASP.NET Core 中所有 gRPC 一元服務方法的簽章都是一致的。</span><span class="sxs-lookup"><span data-stu-id="709f9-152">The signature for all gRPC unary service methods in ASP.NET Core is consistent.</span></span> <span data-ttu-id="709f9-153">有兩個參數：第一個是在 `.proto` 檔案中宣告的訊息類型，而第二個是 `ServerCallContext`，其運作方式類似于 ASP.NET Core 的 `HttpContext`。</span><span class="sxs-lookup"><span data-stu-id="709f9-153">There are two parameters: the first is the message type declared in the `.proto` file, and the second is a `ServerCallContext` that works similarly to the `HttpContext` from ASP.NET Core.</span></span> <span data-ttu-id="709f9-154">事實上，`ServerCallContext` 類別上有一個稱為 `GetHttpContext` 的擴充方法，您可以用它來取得基礎 `HttpContext`，不過您不應該經常使用它。</span><span class="sxs-lookup"><span data-stu-id="709f9-154">In fact, there's an extension method called `GetHttpContext` on the `ServerCallContext` class that you can use to get the underlying `HttpContext`, although you shouldn't need to use it often.</span></span> <span data-ttu-id="709f9-155">我們將在本章稍後介紹 `ServerCallContext`，同時討論驗證的章節。</span><span class="sxs-lookup"><span data-stu-id="709f9-155">We'll take a look at `ServerCallContext` later in this chapter, and also in the chapter that discusses authentication.</span></span>

<span data-ttu-id="709f9-156">方法的傳回型別是一個 `Task<T>`，其中 `T` 是回應訊息類型。</span><span class="sxs-lookup"><span data-stu-id="709f9-156">The method's return type is a `Task<T>`, where `T` is the response message type.</span></span> <span data-ttu-id="709f9-157">所有的 gRPC 服務方法都是非同步。</span><span class="sxs-lookup"><span data-stu-id="709f9-157">All gRPC service methods are asynchronous.</span></span>

## <a name="migrate-the-portfoliodata-library-to-net-core"></a><span data-ttu-id="709f9-158">將 PortfolioData 程式庫遷移至 .NET Core</span><span class="sxs-lookup"><span data-stu-id="709f9-158">Migrate the PortfolioData library to .NET Core</span></span>

<span data-ttu-id="709f9-159">此時，專案需要 WCF 方案中包含在 `TraderSys.PortfolioData` 類別庫中的組合存放庫和模型。</span><span class="sxs-lookup"><span data-stu-id="709f9-159">At this point, the project needs the Portfolio repository and models contained in the `TraderSys.PortfolioData` class library in the WCF solution.</span></span> <span data-ttu-id="709f9-160">將其帶入最簡單的方式，就是使用 [Visual Studio**新增專案**] 對話方塊與 [類別庫] （.NET Standard）範本，或從命令列使用 .NET Core CLI，從包含 `TraderSys.sln` 檔案的目錄執行下列命令，以建立新的類別庫：</span><span class="sxs-lookup"><span data-stu-id="709f9-160">The easiest way to bring them across is to create a new class library by using either the Visual Studio **New project** dialog box with the Class Library (.NET Standard) template, or from the command line by using the .NET Core CLI, running these commands from the directory that contains the `TraderSys.sln` file:</span></span>

```dotnetcli
dotnet new classlib -o src/TraderSys.PortfolioData
dotnet sln add src/TraderSys.PortfolioData
```

<span data-ttu-id="709f9-161">建立程式庫並將其新增至方案之後，請刪除產生的 `Class1.cs` 檔案，然後將檔案從 WCF 方案的程式庫複製到新的類別庫資料夾，並保留資料夾結構：</span><span class="sxs-lookup"><span data-stu-id="709f9-161">After you've created the library and added it to the solution, delete the generated `Class1.cs` file and copy the files from the WCF solution's library into the new class library's folder, keeping the folder structure:</span></span>

```
Models
  Portfolio.cs
  PortfolioItem.cs
IPortfolioRepository.cs
PortfolioRepository.cs
```

<span data-ttu-id="709f9-162">SDK 樣式的 .NET 專案會自動在或其本身的目錄底下包含任何 `.cs` 檔案，因此您不需要明確地將它們新增至專案。</span><span class="sxs-lookup"><span data-stu-id="709f9-162">SDK-style .NET projects automatically include any `.cs` files in or under their own directory, so you don't need to explicitly add them to the project.</span></span> <span data-ttu-id="709f9-163">剩下的唯一步驟是從 `Portfolio` 和 `PortfolioItem` 類別中移除 `DataContract` 和 `DataMember` 屬性，讓它們是單純的C#類別：</span><span class="sxs-lookup"><span data-stu-id="709f9-163">The only step remaining is to remove the `DataContract` and `DataMember` attributes from the `Portfolio` and `PortfolioItem` classes so they're plain old C# classes:</span></span>

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

## <a name="use-aspnet-core-dependency-injection"></a><span data-ttu-id="709f9-164">使用 ASP.NET Core 相依性插入</span><span class="sxs-lookup"><span data-stu-id="709f9-164">Use ASP.NET Core dependency injection</span></span>

<span data-ttu-id="709f9-165">現在您可以將此程式庫的參考新增至 gRPC 應用程式專案，並使用 gRPC 服務執行中的相依性插入來取用 `PortfolioRepository` 類別。</span><span class="sxs-lookup"><span data-stu-id="709f9-165">Now you can add a reference to this library to the gRPC application project and consume the `PortfolioRepository` class by using dependency injection in the gRPC service implementation.</span></span> <span data-ttu-id="709f9-166">在 WCF 應用程式中，相依性插入是由 Autofac IoC 容器所提供。</span><span class="sxs-lookup"><span data-stu-id="709f9-166">In the WCF application, dependency injection was provided by the Autofac IoC container.</span></span> <span data-ttu-id="709f9-167">ASP.NET Core 在中具有相依性插入內建。</span><span class="sxs-lookup"><span data-stu-id="709f9-167">ASP.NET Core has dependency injection baked in.</span></span> <span data-ttu-id="709f9-168">您可以在 `Startup` 類別的 `ConfigureServices` 方法中註冊存放庫：</span><span class="sxs-lookup"><span data-stu-id="709f9-168">You can register the repository in the `ConfigureServices` method in the `Startup` class:</span></span>

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

<span data-ttu-id="709f9-169">`IPortfolioRepository` 的執行現在可以指定為 `PortfolioService` 類別中的「函數參數」，如下所示：</span><span class="sxs-lookup"><span data-stu-id="709f9-169">The `IPortfolioRepository` implementation can now be specified as a constructor parameter in the `PortfolioService` class, as follows:</span></span>

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

## <a name="implement-the-grpc-service"></a><span data-ttu-id="709f9-170">執行 gRPC 服務</span><span class="sxs-lookup"><span data-stu-id="709f9-170">Implement the gRPC service</span></span>

<span data-ttu-id="709f9-171">既然您已在 `portfolios.proto` 檔案中宣告您的訊息和服務，就必須在 `PortfolioService` 類別中，執行繼承自 gRPC 產生之 `Portfolios.PortfoliosBase` 類別的服務方法。</span><span class="sxs-lookup"><span data-stu-id="709f9-171">Now that you've declared your messages and your service in the `portfolios.proto` file, you have to implement the service methods in the `PortfolioService` class that inherits from the gRPC-generated `Portfolios.PortfoliosBase` class.</span></span> <span data-ttu-id="709f9-172">方法會在基類中宣告為 `virtual`。</span><span class="sxs-lookup"><span data-stu-id="709f9-172">The methods are declared as `virtual` in the base class.</span></span> <span data-ttu-id="709f9-173">如果您未覆寫它們，它們預設會傳回「未實 gRPC」狀態碼。</span><span class="sxs-lookup"><span data-stu-id="709f9-173">If you don't override them, they'll return a gRPC "Not Implemented" status code by default.</span></span>

<span data-ttu-id="709f9-174">一開始先執行 `Get` 方法。</span><span class="sxs-lookup"><span data-stu-id="709f9-174">Start by implementing the `Get` method.</span></span> <span data-ttu-id="709f9-175">預設覆寫看起來就像這個範例：</span><span class="sxs-lookup"><span data-stu-id="709f9-175">The default override looks like this example:</span></span>

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    return base.Get(request, context);
}
```

<span data-ttu-id="709f9-176">第一個問題是，`request.TraderId` 是字串，而服務需要 `Guid`。</span><span class="sxs-lookup"><span data-stu-id="709f9-176">The first problem is that `request.TraderId` is a string, and the service requires a `Guid`.</span></span> <span data-ttu-id="709f9-177">雖然字串的預期格式是 `UUID`，但程式碼必須處理呼叫者已傳送無效值並適當回應的可能性。</span><span class="sxs-lookup"><span data-stu-id="709f9-177">Even though the expected format for the string is `UUID`, the code has to deal with the possibility that a caller has sent an invalid value and respond appropriately.</span></span> <span data-ttu-id="709f9-178">服務可以藉由擲回 `RpcException` 來回應錯誤，並使用標準的 `InvalidArgument` 狀態碼來表示問題：</span><span class="sxs-lookup"><span data-stu-id="709f9-178">The service can respond with errors by throwing an `RpcException` and use the standard `InvalidArgument` status code to express the problem:</span></span>

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

<span data-ttu-id="709f9-179">`traderId`有適當的 `Guid` 值之後，您可以使用存放庫來抓取組合，並將其傳回給用戶端：</span><span class="sxs-lookup"><span data-stu-id="709f9-179">After there's a proper `Guid` value for `traderId`, you can use the repository to retrieve the Portfolio and return it to the client:</span></span>

```csharp
    var response = new GetResponse
    {
        Portfolio = await _repository.GetAsync(request.TraderId, request.PortfolioId)
    };
```

### <a name="map-internal-models-to-grpc-messages"></a><span data-ttu-id="709f9-180">將內部模型對應至 gRPC 訊息</span><span class="sxs-lookup"><span data-stu-id="709f9-180">Map internal models to gRPC messages</span></span>

<span data-ttu-id="709f9-181">先前的程式碼實際上並不可行，因為存放庫會傳回自己的 POCO 模型 `Portfolio`，但 gRPC 需要它自己的 Protobuf 訊息 `Portfolio`。</span><span class="sxs-lookup"><span data-stu-id="709f9-181">The previous code doesn't actually work because the repository is returning its own POCO model `Portfolio`, but gRPC needs its own Protobuf message `Portfolio`.</span></span> <span data-ttu-id="709f9-182">當您將 Entity Framework 類型對應到資料傳輸類型時，最佳的解決方式是提供兩者之間的轉換。</span><span class="sxs-lookup"><span data-stu-id="709f9-182">As when you map Entity Framework types to data transfer types, the best solution is to provide a conversion between the two.</span></span> <span data-ttu-id="709f9-183">將此轉換的程式碼放在 Protobuf 產生的類別中，它會宣告為 `partial` 類別，讓它可以擴充：</span><span class="sxs-lookup"><span data-stu-id="709f9-183">A good place to put the code for this conversion is in the Protobuf-generated class, which is declared as a `partial` class so it can be extended:</span></span>

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
> <span data-ttu-id="709f9-184">您可以使用程式庫（例如[AutoMapper](https://automapper.org/) ）來處理從內部模型類別到 Protobuf 類型的這種轉換，只要您設定較低層級的類型轉換，例如 `string`/`Guid` 或 `decimal`/`double` 和清單對應。</span><span class="sxs-lookup"><span data-stu-id="709f9-184">You could use a library like [AutoMapper](https://automapper.org/) to handle this conversion from internal model classes to Protobuf types, as long as you configure the lower-level type conversions like `string`/`Guid` or `decimal`/`double` and the list mapping.</span></span>

<span data-ttu-id="709f9-185">現在您已備妥轉換程式碼，您可以完成 `Get` 方法執行：</span><span class="sxs-lookup"><span data-stu-id="709f9-185">Now that you have the conversion code in place, you can complete the `Get` method implementation:</span></span>

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

<span data-ttu-id="709f9-186">`GetAll` 方法的實作為相似之處。</span><span class="sxs-lookup"><span data-stu-id="709f9-186">The implementation of the `GetAll` method is similar.</span></span> <span data-ttu-id="709f9-187">請注意，Protobuf 訊息上的 `repeated` 欄位會產生為 `RepeatedField<T>`類型的 `readonly` 屬性，因此您必須使用 `AddRange` 方法將專案新增至其中，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="709f9-187">Note that the `repeated` fields on Protobuf messages are generated as `readonly` properties of type `RepeatedField<T>`, so you have to add items to them by using the `AddRange` method, like in this example:</span></span>

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

<span data-ttu-id="709f9-188">已成功將 WCF 要求-回復服務遷移至 gRPC，讓我們來看一下如何從 `.proto` 檔案建立用戶端。</span><span class="sxs-lookup"><span data-stu-id="709f9-188">Having successfully migrated the WCF request-reply service to gRPC, let's look at creating a client for it from the `.proto` file.</span></span>

## <a name="generate-client-code"></a><span data-ttu-id="709f9-189">產生用戶端程式代碼</span><span class="sxs-lookup"><span data-stu-id="709f9-189">Generate client code</span></span>

<span data-ttu-id="709f9-190">在相同的方案中建立 .NET Standard 類別庫，以包含用戶端。</span><span class="sxs-lookup"><span data-stu-id="709f9-190">Create a .NET Standard class library in the same solution to contain the client.</span></span> <span data-ttu-id="709f9-191">這主要是建立用戶端程式代碼的範例，但您可以使用 NuGet 封裝這類程式庫，並將它散發到內部存放庫，以供其他 .NET 小組使用。</span><span class="sxs-lookup"><span data-stu-id="709f9-191">This is primarily an example of creating client code, but you could package such a library by using NuGet and distribute it on an internal repository for other .NET teams to consume.</span></span> <span data-ttu-id="709f9-192">請繼續並將稱為 `TraderSys.Portfolios.Client` 的新 .NET Standard 類別庫加入至方案，並刪除 `Class1.cs` 檔案。</span><span class="sxs-lookup"><span data-stu-id="709f9-192">Go ahead and add a new .NET Standard class library called `TraderSys.Portfolios.Client` to the solution and delete the `Class1.cs` file.</span></span>

> [!CAUTION]
> <span data-ttu-id="709f9-193">[Grpc .net. 用戶端](https://www.nuget.org/packages/Grpc.Net.Client)NuGet 套件需要 .net Core 3.0 （或另一個 .NET Standard 2.1 相容的執行時間）。</span><span class="sxs-lookup"><span data-stu-id="709f9-193">The [Grpc.Net.Client](https://www.nuget.org/packages/Grpc.Net.Client) NuGet package requires .NET Core 3.0 (or another .NET Standard 2.1-compliant runtime).</span></span> <span data-ttu-id="709f9-194">[Grpc](https://www.nuget.org/packages/Grpc.Core) NuGet 套件支援舊版的 .NET FRAMEWORK 和 .net Core。</span><span class="sxs-lookup"><span data-stu-id="709f9-194">Earlier versions of .NET Framework and .NET Core are supported by the [Grpc.Core](https://www.nuget.org/packages/Grpc.Core) NuGet package.</span></span>

<span data-ttu-id="709f9-195">在 Visual Studio 2019 中，您可以加入 gRPC 服務的參考，其方式類似于將服務參考加入舊版 Visual Studio 中的 WCF 專案。</span><span class="sxs-lookup"><span data-stu-id="709f9-195">In Visual Studio 2019, you can add references to gRPC services in a way that's similar to how you'd add service references to WCF projects in earlier versions of Visual Studio.</span></span> <span data-ttu-id="709f9-196">服務參考和已連結的服務現在都是在相同的 UI 下管理。</span><span class="sxs-lookup"><span data-stu-id="709f9-196">Service references and connected services are all managed under the same UI now.</span></span> <span data-ttu-id="709f9-197">您可以在方案總管中的 `TraderSys.Portfolios.Client` 專案中，以滑鼠右鍵按一下 [相依性] 節點，然後選取 [**新增已連結的服務** **]** ，即可存取該 UI。</span><span class="sxs-lookup"><span data-stu-id="709f9-197">You can access the UI by right-clicking the **Dependencies** node in the `TraderSys.Portfolios.Client` project in Solution Explorer and selecting **Add Connected Service**.</span></span> <span data-ttu-id="709f9-198">在出現的工具視窗中，選取 [**服務參考**] 區段，然後選取 [**加入新的 gRPC 服務參考**]：</span><span class="sxs-lookup"><span data-stu-id="709f9-198">In the tool window that appears, select the **Service References** section and then select **Add new gRPC service reference**:</span></span>

![Visual Studio 2019 中的已連線的服務 UI](media/migrate-request-reply/add-connected-service.png)

<span data-ttu-id="709f9-200">流覽至 `TraderSys.Portfolios` 專案中的 `portfolios.proto` 檔案，將 [**用戶端**] 保留在 [**選取要產生的類別類型**] 底下，然後選取 **[確定]** ：</span><span class="sxs-lookup"><span data-stu-id="709f9-200">Browse to the `portfolios.proto` file in the `TraderSys.Portfolios` project, leave **Client** under **Select the type of class to be generated**, and then select **OK**:</span></span>

![Visual Studio 2019 中的 [加入新的 gRPC 服務參考] 對話方塊](media/migrate-request-reply/add-new-grpc-service-reference.png)

> [!TIP]
> <span data-ttu-id="709f9-202">請注意，此對話方塊也會提供 [URL] 欄位。</span><span class="sxs-lookup"><span data-stu-id="709f9-202">Notice that this dialog box also provides a URL field.</span></span> <span data-ttu-id="709f9-203">如果您的組織維護 `.proto` 檔案的 web 可存取目錄，您就可以藉由設定此 URL 位址來建立用戶端。</span><span class="sxs-lookup"><span data-stu-id="709f9-203">If your organization maintains a web-accessible directory of `.proto` files, you can create clients just by setting this URL address.</span></span>

<span data-ttu-id="709f9-204">當您使用 Visual Studio**加入已連接服務**功能時，`portfolios.proto` 檔案會加入至類別庫專案做為*連結*的檔案，而不是複製，因此服務專案中檔案的變更會自動套用至用戶端專案。</span><span class="sxs-lookup"><span data-stu-id="709f9-204">When you use the Visual Studio **Add Connected Service** feature, the `portfolios.proto` file is added to the class library project as a *linked file* rather than copied, so changes to the file in the service project will automatically be applied in the client project.</span></span> <span data-ttu-id="709f9-205">`csproj` 檔案中的 `<Protobuf>` 元素看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="709f9-205">The `<Protobuf>` element in the `csproj` file looks like this:</span></span>

```xml
<Protobuf Include="..\TraderSys.Portfolios\Protos\portfolios.proto" GrpcServices="Client">
  <Link>Protos\portfolios.proto</Link>
</Protobuf>
```

> [!TIP]
> <span data-ttu-id="709f9-206">如果您不是使用 Visual Studio 或偏好從命令列工作，您可以使用 `dotnet-grpc` 全域工具來管理 .NET gRPC 專案中的 Protobuf 參考。</span><span class="sxs-lookup"><span data-stu-id="709f9-206">If you're not using Visual Studio or prefer to work from the command line, you can use the `dotnet-grpc` global tool to manage Protobuf references in a .NET gRPC project.</span></span> <span data-ttu-id="709f9-207">如需詳細資訊，請參閱[`dotnet-grpc` 檔](/aspnet/core/grpc/dotnet-grpc)。</span><span class="sxs-lookup"><span data-stu-id="709f9-207">For more information, see the [`dotnet-grpc` documentation](/aspnet/core/grpc/dotnet-grpc).</span></span>

### <a name="use-the-portfolios-service-from-a-client-application"></a><span data-ttu-id="709f9-208">從用戶端應用程式使用包服務</span><span class="sxs-lookup"><span data-stu-id="709f9-208">Use the Portfolios service from a client application</span></span>

<span data-ttu-id="709f9-209">下列程式碼是如何在主控台應用程式中使用產生的用戶端的簡單範例。</span><span class="sxs-lookup"><span data-stu-id="709f9-209">The following code is a brief example of how to use the generated client in a console application.</span></span> <span data-ttu-id="709f9-210">如需更詳細的 gRPC 用戶端程式代碼探索，請見本章的結尾。</span><span class="sxs-lookup"><span data-stu-id="709f9-210">A more detailed exploration of the gRPC client code is at the end of this chapter.</span></span>

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

<span data-ttu-id="709f9-211">您現在已將基本 WCF 應用程式遷移至 ASP.NET Core gRPC 服務，並建立了用戶端以從 .NET 應用程式取用服務。</span><span class="sxs-lookup"><span data-stu-id="709f9-211">You've now migrated a basic WCF application to an ASP.NET Core gRPC service and created a client to consume the service from a .NET application.</span></span> <span data-ttu-id="709f9-212">下一節將涵蓋更多的雙工服務。</span><span class="sxs-lookup"><span data-stu-id="709f9-212">The next section will cover the more involved duplex services.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="709f9-213">[上一頁](create-project.md)
>[下一頁](migrate-duplex-services.md)</span><span class="sxs-lookup"><span data-stu-id="709f9-213">[Previous](create-project.md)
[Next](migrate-duplex-services.md)</span></span>
