---
title: 將 WCF 要求-回復服務遷移至 WCF 開發人員的 gRPC-gRPC
description: 瞭解如何將簡單的要求-回復服務從 WCF 遷移至 gRPC。
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: ac9eecf66a7ac37a1df9714e6383f7eaebae4781
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184306"
---
# <a name="migrate-a-wcf-request-reply-service-to-a-grpc-unary-rpc"></a><span data-ttu-id="a3a5d-103">將 WCF 要求-回復服務遷移至 gRPC 一元 RPC</span><span class="sxs-lookup"><span data-stu-id="a3a5d-103">Migrate a WCF request-reply service to a gRPC unary RPC</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="a3a5d-104">本節說明如何在 ASP.NET Core gRPC 中，將 WCF 中的基本要求-回復服務遷移至一元 RPC 服務。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-104">This section covers how to migrate a basic request-reply service in WCF to a unary RPC service in ASP.NET Core gRPC.</span></span> <span data-ttu-id="a3a5d-105">這些服務是 Windows Communication Foundation （WCF）和 gRPC 中最簡單的服務類型，因此是很好的起點。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-105">These services are the simplest service types in both Windows Communication Foundation (WCF) and gRPC, so it's an excellent place to start.</span></span> <span data-ttu-id="a3a5d-106">在遷移服務之後，您將瞭解如何從相同`.proto`的檔案產生用戶端程式庫，以從 .net 用戶端應用程式取用服務。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-106">After migrating the service, you'll learn how to generate a client library from the same `.proto` file to consume the service from a .NET client application.</span></span>

## <a name="the-wcf-solution"></a><span data-ttu-id="a3a5d-107">WCF 解決方案</span><span class="sxs-lookup"><span data-stu-id="a3a5d-107">The WCF solution</span></span>

<span data-ttu-id="a3a5d-108">[PortfoliosSample 解決方案](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys)包含簡單的要求-回復組合服務，可供您下載單一組合或指定 Trader 的所有公事包。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-108">The [PortfoliosSample solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys) includes a simple Request-Reply Portfolio service to download a single portfolio, or all portfolios for a given Trader.</span></span> <span data-ttu-id="a3a5d-109">服務會在介面`IPortfolioService`中`ServiceContract`使用屬性來定義：</span><span class="sxs-lookup"><span data-stu-id="a3a5d-109">The service is defined in the interface `IPortfolioService` with a `ServiceContract` attribute:</span></span>

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

<span data-ttu-id="a3a5d-110">模型是以 [DataContract](xref:System.Runtime.Serialization.DataContractAttribute) 標記C#的簡單類別，包括`PortfolioItem`物件的清單。`Portfolio`</span><span class="sxs-lookup"><span data-stu-id="a3a5d-110">The `Portfolio` model is a simple C# class marked with [DataContract](xref:System.Runtime.Serialization.DataContractAttribute), including a list of `PortfolioItem` objects.</span></span> <span data-ttu-id="a3a5d-111">這些模型會在`TraderSys.PortfolioData`專案中定義，以及代表資料存取抽象的儲存機制類別。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-111">These models are defined in the `TraderSys.PortfolioData` project, along with a repository class representing a data access abstraction.</span></span>

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

<span data-ttu-id="a3a5d-112">此`ServiceContract`執行會使用透過相依性插入所提供的存放庫類別， `DataContract`以傳回類型的實例。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-112">The `ServiceContract` implementation uses a repository class provided via dependency injection that returns instances of the `DataContract` types.</span></span>

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

## <a name="the-portfoliosproto-file"></a><span data-ttu-id="a3a5d-113">組合的 proto 檔案</span><span class="sxs-lookup"><span data-stu-id="a3a5d-113">The portfolios.proto file</span></span>

<span data-ttu-id="a3a5d-114">如果您遵循上一節中的指示進行，您應該會有一個 gRPC 專案`portfolios.proto` ，其中包含如下所示的檔案。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-114">If you followed the instructions in the previous section, you should have a gRPC project with a `portfolios.proto` file that looks like this.</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

<span data-ttu-id="a3a5d-115">第一個步驟是將`DataContract`類別遷移至其 Protobuf 對應專案。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-115">The first step is to migrate the `DataContract` classes to their Protobuf equivalents.</span></span>

## <a name="convert-the-datacontracts-to-grpc-messages"></a><span data-ttu-id="a3a5d-116">將 DataContracts 轉換為 gRPC 訊息</span><span class="sxs-lookup"><span data-stu-id="a3a5d-116">Convert the DataContracts to gRPC messages</span></span>

<span data-ttu-id="a3a5d-117">類別會先轉換成 Protobuf 訊息， `Portfolio`因為類別會依賴它。 `PortfolioItem`</span><span class="sxs-lookup"><span data-stu-id="a3a5d-117">The `PortfolioItem` class will be converted to a Protobuf message first, as the `Portfolio` class depends on it.</span></span> <span data-ttu-id="a3a5d-118">類別非常簡單，而三個屬性會直接對應至 gRPC 資料類型。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-118">The class is very simple, and three of the properties map directly to gRPC data types.</span></span> <span data-ttu-id="a3a5d-119">屬性（代表購買的股份所支付的價格） `decimal`是欄位，而 gRPC 只支援`float`或`double`適用于貨幣的實數。 `Cost`</span><span class="sxs-lookup"><span data-stu-id="a3a5d-119">The `Cost` property, representing the price paid for the shares at purchase, is a `decimal` field, and gRPC only supports `float` or `double` for real numbers, which aren't suitable for currency.</span></span> <span data-ttu-id="a3a5d-120">由於共用價格的差異最少一美分，因此成本會以美分`int32`的形式表示。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-120">Since share prices vary by a minimum of one cent, the cost can be expressed as an `int32` of cents.</span></span>

> [!NOTE]
> <span data-ttu-id="a3a5d-121">請記得在`camelCase`檔案中使用做`.proto`為功能變數名稱; 程式C#代碼產生器會將它們`PascalCase`轉換為您，而其他語言的使用者則會感謝您遵守其不同的編碼標準。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-121">Remember to use `camelCase` for field names in your `.proto` file; the C# code generator will convert them to `PascalCase` for you, and users of other languages will thank you for respecting their different coding standards.</span></span>

```protobuf
message PortfolioItem {
    int32 id = 1;
    int32 shareId = 2;
    int32 holding = 3;
    int32 costCents = 4;
}
```

<span data-ttu-id="a3a5d-122">`Portfolio`類別比較複雜一點。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-122">The `Portfolio` class is a little more complicated.</span></span> <span data-ttu-id="a3a5d-123">在 WCF 程式碼中，開發人員使用`Guid` `TraderId` `List<PortfolioItem>`屬性的，而且包含。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-123">In the WCF code, the developer used a `Guid` for the `TraderId` property, and contains a `List<PortfolioItem>`.</span></span> <span data-ttu-id="a3a5d-124">在沒有第一類`UUID`類型的 Protobuf 中，您應該`string`針對`traderId`欄位使用，並在您自己的程式碼中進行剖析。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-124">In Protobuf, which doesn't have a first-class `UUID` type, you should use a `string` for the `traderId` field and parse it in your own code.</span></span> <span data-ttu-id="a3a5d-125">針對專案清單，在欄位上使用`repeated`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-125">For the list of items, use the `repeated` keyword on the field.</span></span>

```protobuf
message Portfolio {
    int32 id = 1;
    string traderId = 2;
    repeated PortfolioItem items = 3;
}
```

<span data-ttu-id="a3a5d-126">現在我們已經有資料訊息，我們可以宣告服務 RPC 端點。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-126">Now we have our data messages, we can declare the service RPC endpoints.</span></span>

## <a name="convert-the-servicecontract-to-a-grpc-service"></a><span data-ttu-id="a3a5d-127">將 ServiceContract 轉換成 gRPC 服務</span><span class="sxs-lookup"><span data-stu-id="a3a5d-127">Convert the ServiceContract to a gRPC service</span></span>

<span data-ttu-id="a3a5d-128">WCF `Get`方法會接受兩個參數`Guid traderId` ： `int portfolioId`和。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-128">The WCF `Get` method takes two parameters: `Guid traderId` and `int portfolioId`.</span></span> <span data-ttu-id="a3a5d-129">gRPC 服務方法只能接受單一參數，因此必須建立訊息來保存這兩個值。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-129">gRPC service methods can only take a single parameter, so a message must be created to hold the two values.</span></span> <span data-ttu-id="a3a5d-130">常見的做法是使用與方法相同的名稱和尾碼`Request`來命名這些要求物件。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-130">It's common practice to name these request objects with the same name as the method and the suffix `Request`.</span></span> <span data-ttu-id="a3a5d-131">同樣地`string` ，會用於`traderId`欄位，而不`Guid`是。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-131">Again, `string` is being used for the `traderId` field instead of `Guid`.</span></span>

<span data-ttu-id="a3a5d-132">服務可以`Portfolio`直接傳回訊息，但同樣地，這可能會影響未來的回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-132">The service could just return a `Portfolio` message directly, but again, this could impact backward compatibility in the future.</span></span> <span data-ttu-id="a3a5d-133">針對服務中的每個方法定義`Request`個別`Response`和訊息是個很好的作法，即使其中有許多都是相同的，因此`GetResponse`請宣告具有單一`Portfolio`欄位的訊息。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-133">It's a good practice to define separate `Request` and `Response` messages for every method in a service, even if many of them are the same right now, so declare a `GetResponse` message with a single `Portfolio` field.</span></span>

<span data-ttu-id="a3a5d-134">下列範例示範如何使用`GetRequest`訊息來宣告 gRPC 服務方法：</span><span class="sxs-lookup"><span data-stu-id="a3a5d-134">The following example shows the declaration of the gRPC service method using the `GetRequest` message:</span></span>

```protobuf
message GetRequest {
    string traderId = 1;
    int32 portfolioId = 2;
}

message GetResponse {
    Portfolio portfolio = 1;
}

service Portfolios {
    rpc Get(GetRequest) returns (GetResponse);
}
```

<span data-ttu-id="a3a5d-135">WCF `GetAll`方法只接受單一參數， `traderId`因此它可能會指定`string`為參數類型，但 gRPC 需要定義的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-135">The WCF `GetAll` method only takes a single parameter, `traderId`, so it might seem that one could specify `string` as the parameter type, but gRPC requires a defined message type.</span></span> <span data-ttu-id="a3a5d-136">這項需求有助於強制執行針對所有輸入和輸出使用自訂訊息的作法，以供未來回溯相容性之用。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-136">This requirement helps to enforce the practice of using custom messages for all inputs and outputs, for future backward compatibility.</span></span>

<span data-ttu-id="a3a5d-137">WCF 方法也會傳回`List<Portfolio>`，但基於相同的原因，它不允許簡單的參數類型，gRPC 不允許`repeated Portfolio`做為傳回類型。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-137">The WCF method also returned a `List<Portfolio>`, but for the same reason it doesn't allow simple parameter types, gRPC won't allow `repeated Portfolio` as a return type.</span></span> <span data-ttu-id="a3a5d-138">相反地，請`GetAllResponse`建立類型來包裝清單。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-138">Instead, create a `GetAllResponse` type to wrap the list.</span></span>

> [!WARNING]
> <span data-ttu-id="a3a5d-139">您可能會想要建立一個`PortfolioList`或類似的訊息，並在多個服務方法中使用它，但您應該不會受到這個誘惑的抵觸。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-139">You may be tempted to create a `PortfolioList` message or similar and use it across multiple service methods, but you should resist this temptation.</span></span> <span data-ttu-id="a3a5d-140">不可能知道服務上的各種方法在未來的發展方式，因此請將它們的訊息指定為明確且完全分隔。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-140">It's impossible to know how the various methods on a service may evolve in the future, so keep their messages specific and cleanly separated.</span></span>

```protobuf
message GetAllRequest {
    string traderId = 1;
}

message PortfolioList {
    repeated Portfolio portfolios = 1;
}

service Portfolios {
    rpc Get(GetRequest) returns (Portfolio);
    rpc GetAll(GetAllRequest) returns (GetAllResponse);
}
```

<span data-ttu-id="a3a5d-141">如果您使用這些變更來儲存專案，則 gRPC 組建目標會在背景中執行，並產生所有 Protobuf 訊息類型，以及您可以繼承以執行服務的基類。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-141">If you save your project with these changes, the gRPC build target will run in the background and generate all the Protobuf message types and a base class you can inherit to implement the service.</span></span>

<span data-ttu-id="a3a5d-142">`Services/GreeterService.cs`開啟類別，並刪除範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-142">Open up the `Services/GreeterService.cs` class and delete the example code.</span></span> <span data-ttu-id="a3a5d-143">現在您可以加入「公事包服務」執行。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-143">Now you can add the Portfolio service implementation.</span></span> <span data-ttu-id="a3a5d-144">產生的基類將會在`Protos`命名空間中，並以嵌套類別的形式產生。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-144">The generated base class will be in the `Protos` namespace and is generated as a nested class.</span></span> <span data-ttu-id="a3a5d-145">gRPC 會使用與服務`.proto`相同的名稱來建立靜態類別，然後再以該靜態類別內的尾碼`Base`做為基類，因此基底類型的完整識別碼為`TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase`。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-145">gRPC creates a static class with the same name as the service in the `.proto` file, and then a base class with the suffix `Base` inside that static class, so the full identifier for the base type is `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase`.</span></span>

```csharp
namespace TraderSys.Portfolios.Services
{
    public class PortfolioService : Protos.Portfolios.PortfoliosBase
    {
    }
}
```

<span data-ttu-id="a3a5d-146">基類`virtual`宣告了`Get`和`GetAll`的方法，可以覆寫以執行服務。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-146">The base class declares `virtual` methods for `Get` and `GetAll` that can be overridden to implement the service.</span></span> <span data-ttu-id="a3a5d-147">`virtual`方法並`Unimplemented` `NotImplementedException` C#不是如此，因此，如果您未加以執行，服務會傳回明確的gRPC狀態碼，就像您可能會在一般程式碼中擲回一樣。`abstract`</span><span class="sxs-lookup"><span data-stu-id="a3a5d-147">The methods are `virtual` rather than `abstract` so that if you don't implement them, the service can return an explicit gRPC `Unimplemented` status code, much like you might throw a `NotImplementedException` in regular C# code.</span></span>

<span data-ttu-id="a3a5d-148">ASP.NET Core 中所有 gRPC 一元服務方法的簽章都是一致的。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-148">The signature for all gRPC unary service methods in ASP.NET Core is consistent.</span></span> <span data-ttu-id="a3a5d-149">有兩個參數：第一個是在檔案中`.proto`宣告的訊息類型，而第二個`ServerCallContext`是`HttpContext` ，其運作方式類似于 from ASP.NET Core。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-149">There are two parameters: the first is the message type declared in the `.proto` file, and the second is a `ServerCallContext` that works similarly to the `HttpContext` from ASP.NET Core.</span></span> <span data-ttu-id="a3a5d-150">事實上，在`GetHttpContext` `ServerCallContext`類別上有一個稱為的擴充方法，可讓您用來取得基礎`HttpContext`，不過您應該不需要經常使用它。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-150">In fact, there's an extension method called `GetHttpContext` on the `ServerCallContext` class that you can use to get the underlying `HttpContext`, although you shouldn't need to use it often.</span></span> <span data-ttu-id="a3a5d-151">我們將`ServerCallContext`在本章稍後介紹，並在討論驗證的章節仲介紹。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-151">We'll take a look at `ServerCallContext` later in this chapter, and also in the chapter that discusses authentication.</span></span>

<span data-ttu-id="a3a5d-152">方法的傳回型別是`Task<T>` ，其中`T`是回應訊息類型。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-152">The method's return type is a `Task<T>` where `T` is the response message type.</span></span> <span data-ttu-id="a3a5d-153">所有的 gRPC 服務方法都是非同步。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-153">All gRPC service methods are asynchronous.</span></span>

## <a name="migrate-the-portfoliodata-library-to-net-core"></a><span data-ttu-id="a3a5d-154">將 PortfolioData 程式庫遷移至 .NET Core</span><span class="sxs-lookup"><span data-stu-id="a3a5d-154">Migrate the PortfolioData library to .NET Core</span></span>

<span data-ttu-id="a3a5d-155">此時，專案需要 WCF 方案的`TraderSys.PortfolioData`類別庫中包含的組合存放庫和模型。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-155">At this point, the project needs the Portfolio repository and models contained in the `TraderSys.PortfolioData` class library in the WCF solution.</span></span> <span data-ttu-id="a3a5d-156">將它們帶入最簡單的方式，就是使用 [Visual Studio**新增專案**] 對話方塊與 [*類別庫] （.NET Standard）* 範本，或從命令列使用 .NET Core CLI 執行下列命令，以建立新的類別庫。從包含`TraderSys.sln`檔案的目錄。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-156">The easiest way to bring them across is to create a new class library using either the Visual Studio **New project** dialog with the *Class Library (.NET Standard)* template, or from the command line using the .NET Core CLI, running the following commands from the directory containing the `TraderSys.sln` file.</span></span>

```dotnetcli
dotnet new classlib -o src/TraderSys.PortfolioData
dotnet sln add src/TraderSys.PortfolioData
```

<span data-ttu-id="a3a5d-157">建立程式庫並將其新增至解決方案之後，請刪除產生`Class1.cs`的檔案，並將檔案從 WCF 方案的程式庫複製到新的類別庫資料夾，並保留資料夾結構。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-157">Once the library has been created and added to the solution, delete the generated `Class1.cs` file and copy the files from the WCF solution's library into the new class library's folder, keeping the folder structure.</span></span>

```
Models
  Portfolio.cs
  PortfolioItem.cs
IPortfolioRepository.cs
PortfolioRepository.cs
```

<span data-ttu-id="a3a5d-158">現代化的 .net 專案檔會自動`.cs`包含或其本身目錄底下的任何檔案，因此不需要明確地將它們新增至專案。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-158">Modern .NET project files automatically include any `.cs` files in or under their own directory, so there's no need to explicitly add them to the project.</span></span> <span data-ttu-id="a3a5d-159">剩下的唯一步驟是從`DataContract` `Portfolio`和`PortfolioItem`類別中`DataMember`移除和屬性，使其成為簡單的C#類別。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-159">The only step remaining is to remove the `DataContract` and `DataMember` attributes from the `Portfolio` and `PortfolioItem` classes so they're plain old C# classes.</span></span>

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

## <a name="use-aspnet-core-dependency-injection"></a><span data-ttu-id="a3a5d-160">使用 ASP.NET Core 相依性插入</span><span class="sxs-lookup"><span data-stu-id="a3a5d-160">Use ASP.NET Core dependency injection</span></span>

<span data-ttu-id="a3a5d-161">現在您可以將此程式庫的參考新增至 gRPC 應用程式專案，並`PortfolioRepository`使用 gRPC 服務實中的相依性插入來取用類別。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-161">Now you can add a reference to this library to the gRPC application project and consume the `PortfolioRepository` class using dependency injection in the gRPC service implementation.</span></span> <span data-ttu-id="a3a5d-162">在 WCF 應用程式中，相依性插入是由 Autofac IoC 容器所提供。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-162">In the WCF application, dependency injection was provided by the Autofac IoC container.</span></span> <span data-ttu-id="a3a5d-163">ASP.NET Core 在中具有相依性插入內建;存放庫可以在`ConfigureServices` `Startup`類別的方法中註冊。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-163">ASP.NET Core has dependency injection baked in; the repository can be registered in the `ConfigureServices` method in the `Startup` class.</span></span>

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

<span data-ttu-id="a3a5d-164">在類別`PortfolioService`中，現在可以將實作為函數參數來指定，`IPortfolioRepository`如下所示：</span><span class="sxs-lookup"><span data-stu-id="a3a5d-164">The `IPortfolioRepository` implementation can now be specified as a constructor parameter in the `PortfolioService` class, as follows:</span></span>

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

## <a name="implement-the-grpc-service"></a><span data-ttu-id="a3a5d-165">執行 gRPC 服務</span><span class="sxs-lookup"><span data-stu-id="a3a5d-165">Implement the gRPC service</span></span>

<span data-ttu-id="a3a5d-166">既然您已在檔案中`portfolios.proto`宣告您的訊息和服務，就必須在繼承自 gRPC 產生`Portfolios.PortfoliosBase`之類別的`PortfolioService`類別中，執行服務方法。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-166">Now that you've declared your messages and your service in the `portfolios.proto` file, you have to implement the service methods in the `PortfolioService` class that inherits from the gRPC-generated `Portfolios.PortfoliosBase` class.</span></span> <span data-ttu-id="a3a5d-167">方法會在基類中`virtual`宣告為。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-167">The methods are declared as `virtual` in the base class.</span></span> <span data-ttu-id="a3a5d-168">如果您未覆寫它們，它們預設會傳回「未實 gRPC」狀態碼。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-168">If you don't override them, they'll return a gRPC "Not Implemented" status code by default.</span></span>

<span data-ttu-id="a3a5d-169">一開始先執行`Get`方法。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-169">Start by implementing the `Get` method.</span></span> <span data-ttu-id="a3a5d-170">預設覆寫看起來如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="a3a5d-170">The default override looks like the following example:</span></span>

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    return base.Get(request, context);
}
```

<span data-ttu-id="a3a5d-171">第一個問題是`request.TraderId`字串，而服務`Guid`需要。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-171">The first issue is that `request.TraderId` is a string, and the service requires a `Guid`.</span></span> <span data-ttu-id="a3a5d-172">雖然字串的預期格式是`UUID`，但程式碼必須處理呼叫者已傳送無效值並適當回應的可能性。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-172">Even though the expected format for the string is a `UUID`, the code has to deal with the possibility that a caller has sent an invalid value and respond appropriately.</span></span> <span data-ttu-id="a3a5d-173">服務可以藉由`RpcException`擲回來回應錯誤，並使用標準`InvalidArgument`狀態碼來表示問題。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-173">The service can respond with errors by throwing an `RpcException`, and use the standard `InvalidArgument` status code to express the problem.</span></span>

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

<span data-ttu-id="a3a5d-174">一旦有適當`Guid`的`traderId`值，就可以使用存放庫來抓取組合，並將其傳回給用戶端。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-174">Once there's a proper `Guid` value for `traderId`, the repository can be used to retrieve the Portfolio and return it to the client.</span></span>

```csharp
    var response = new GetResponse
    {
        Portfolio = await _repository.GetAsync(request.TraderId, request.PortfolioId)
    };
```

### <a name="map-internal-models-to-grpc-messages"></a><span data-ttu-id="a3a5d-175">將內部模型對應至 gRPC 訊息</span><span class="sxs-lookup"><span data-stu-id="a3a5d-175">Map internal models to gRPC messages</span></span>

<span data-ttu-id="a3a5d-176">先前的程式碼實際上並不可行，因為存放庫會傳回自己`Portfolio`的 POCO 模型，但 gRPC 需要它`Portfolio`自己*的*Protobuf 訊息。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-176">The previous code doesn't actually work because the repository is returning its own POCO model `Portfolio`, but gRPC needs *its* own Protobuf message `Portfolio`.</span></span> <span data-ttu-id="a3a5d-177">就像是將 Entity Framework 類型對應到資料傳輸類型，最好的方法是在兩者之間提供轉換。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-177">Much like mapping Entity Framework types to data transfer types, the best solution is to provide conversion between the two.</span></span> <span data-ttu-id="a3a5d-178">將此程式碼放在 Protobuf 產生的類別中，這是一個很好的位置，它會`partial`宣告為類別，讓它可以擴充。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-178">A good place to put the code for this is in the Protobuf-generated class, which is declared as a `partial` class so it can be extended.</span></span>

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
> <span data-ttu-id="a3a5d-179">您可以使用程式庫（例如[AutoMapper](https://automapper.org/) ）來處理從內部模型類別到 Protobuf 類型的這種轉換，只要您設定較低層級的`string`類型`decimal`轉換/ `Guid` ，例如或/和清單對應。 `double`</span><span class="sxs-lookup"><span data-stu-id="a3a5d-179">You could use a library like [AutoMapper](https://automapper.org/) to handle this conversion from internal model classes to Protobuf types, as long as you configure the lower-level type conversions like `string`/`Guid` or `decimal`/`double` and the list mapping.</span></span>

<span data-ttu-id="a3a5d-180">轉換程式碼準備好之後，就`Get`可以完成方法的執行。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-180">With the conversion code in place, the `Get` method implementation can be completed.</span></span>

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

<span data-ttu-id="a3a5d-181">`GetAll`方法的實作為類似。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-181">The implementation of the `GetAll` method is similar.</span></span> <span data-ttu-id="a3a5d-182">請注意， `repeated` Protobuf 訊息上的欄位會產生`readonly`為類型`RepeatedField<T>`的屬性，因此您`AddRange`必須使用方法將專案新增至其中，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="a3a5d-182">Note that the `repeated` fields on Protobuf messages are generated as `readonly` properties of type `RepeatedField<T>`, so you have to add items to them using the `AddRange` method, like in the following example:</span></span>

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

<span data-ttu-id="a3a5d-183">已成功將 WCF 要求-回復服務遷移至 gRPC，讓我們來看看如何從`.proto`檔案建立用戶端。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-183">Having successfully migrated the WCF request-reply service to gRPC, let's look at creating a client for it from the `.proto` file.</span></span>

## <a name="generate-client-code"></a><span data-ttu-id="a3a5d-184">產生用戶端程式代碼</span><span class="sxs-lookup"><span data-stu-id="a3a5d-184">Generate client code</span></span>

<span data-ttu-id="a3a5d-185">在相同的方案中建立 .NET Standard 類別庫，以包含用戶端。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-185">Create a .NET Standard class library in the same solution to contain the client.</span></span> <span data-ttu-id="a3a5d-186">這主要是建立用戶端程式代碼的範例，但您可以使用 NuGet 封裝這類程式庫，並將它散發到內部存放庫，以供其他 .NET 小組使用。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-186">This is primarily an example of creating client code, but you could package such a library using NuGet and distribute it on an internal repository for other .NET teams to consume.</span></span> <span data-ttu-id="a3a5d-187">請繼續並將名`TraderSys.Portfolios.Client`為的新 .NET Standard 類別庫加入至方案，並刪除該`Class1.cs`檔案。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-187">Go ahead and add a new .NET Standard Class Library called `TraderSys.Portfolios.Client` to the solution and delete the `Class1.cs` file.</span></span>

> [!CAUTION]
> <span data-ttu-id="a3a5d-188">[Grpc .net. 用戶端](https://www.nuget.org/packages/Grpc.Net.Client)NuGet 套件需要 .net Core 3.0 （或另一個 .NET Standard 2.1 相容的執行時間）。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-188">The [Grpc.Net.Client](https://www.nuget.org/packages/Grpc.Net.Client) NuGet package requires .NET Core 3.0 (or another .NET Standard 2.1-compliant runtime).</span></span> <span data-ttu-id="a3a5d-189">[Grpc](https://www.nuget.org/packages/Grpc.Core) NuGet 套件支援舊版的 .NET FRAMEWORK 和 .net Core。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-189">Earlier versions of .NET Framework and .NET Core are supported by the [Grpc.Core](https://www.nuget.org/packages/Grpc.Core) NuGet package.</span></span>

<span data-ttu-id="a3a5d-190">在 Visual Studio 2019 中，您可以加入 gRPC 服務的參考，就像您在舊版 Visual Studio 中將服務參考新增至 WCF 專案的方式一樣。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-190">In Visual Studio 2019, you can add references to gRPC services similar to the way you'd add Service References to WCF projects in earlier versions of Visual Studio.</span></span> <span data-ttu-id="a3a5d-191">服務參考和已連線的服務現在都是在相同的 UI 下進行管理，您可以用滑鼠右鍵按一下`TraderSys.Portfolios.Client`專案方案總管中的 [相依性] 節點，然後選取 [**新增已連結的服務** **]** ，即可存取它們。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-191">Service References and Connected Services are all managed under the same UI now, which you can access by right-clicking the **Dependencies** node in the `TraderSys.Portfolios.Client` project in Solution Explorer and selecting **Add Connected Service**.</span></span> <span data-ttu-id="a3a5d-192">在出現的工具視窗中，選取 [**服務參考**] 區段，然後按一下 [**加入新的 gRPC 服務參考**]。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-192">In the tool window that appears, select the **Service References** section and click **Add new gRPC service reference**.</span></span>

![Visual Studio 2019 中的已連線的服務 UI](media/migrate-request-reply/add-connected-service.png)

<span data-ttu-id="a3a5d-194">流覽至`TraderSys.Portfolios`專案`portfolios.proto`中的檔案，將**類別類型**保留為 [**用戶端**]，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-194">Browse to the `portfolios.proto` file in the `TraderSys.Portfolios` project, leave the **type of class to be generated** as **Client**, and click **OK**.</span></span>

![Visual Studio 2019 中的 [加入新的 gRPC 服務參考] 對話方塊](media/migrate-request-reply/add-new-grpc-service-reference.png)

> [!TIP]
> <span data-ttu-id="a3a5d-196">請注意，此對話方塊也會提供 [URL] 欄位。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-196">Notice that this dialog also provides a URL field.</span></span> <span data-ttu-id="a3a5d-197">如果您的組織維護 web 可存取的`.proto`檔案目錄，您就可以藉由設定此 URL 位址來建立用戶端。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-197">If your organization maintains a web-accessible directory of `.proto` files, you can create clients just by setting this URL address.</span></span>

<span data-ttu-id="a3a5d-198">使用 Visual Studio**加入已連接服務**功能時， `portfolios.proto`會將檔案新增至類別庫專案做為*連結*的檔案，而不是複製，因此服務專案中檔案的變更會自動套用於用戶端專案。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-198">When using the Visual Studio **Add Connected Service** feature, the `portfolios.proto` file is added to the Class Library project as a *linked file*, rather than copied, so changes to the file in the service project will automatically be applied in the client project.</span></span> <span data-ttu-id="a3a5d-199">`<Protobuf>` 檔案`csproj`中的元素看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="a3a5d-199">The `<Protobuf>` element in the `csproj` file looks like this:</span></span>

```xml
<Protobuf Include="..\TraderSys.Portfolios\Protos\portfolios.proto" GrpcServices="Client">
  <Link>Protos\portfolios.proto</Link>
</Protobuf>
```

### <a name="use-the-portfolios-service-from-a-client-application"></a><span data-ttu-id="a3a5d-200">從用戶端應用程式使用包服務</span><span class="sxs-lookup"><span data-stu-id="a3a5d-200">Use the Portfolios service from a client application</span></span>

<span data-ttu-id="a3a5d-201">下列程式碼是在主控台應用程式中使用所產生之用戶端的簡單範例。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-201">The following code is a brief example of using the generated client in a console application.</span></span> <span data-ttu-id="a3a5d-202">如需更詳細的 gRPC 用戶端程式代碼探索，請見本章的結尾。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-202">A more detailed exploration of the gRPC client code is at the end of this chapter.</span></span>

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

<span data-ttu-id="a3a5d-203">現在，您已將基本 WCF 應用程式遷移至 ASP.NET Core gRPC 服務，並建立用戶端以從 .NET 應用程式取用服務。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-203">Now, you've migrated a basic WCF application to an ASP.NET Core gRPC service and created a client to consume the service from a .NET application.</span></span> <span data-ttu-id="a3a5d-204">下一節將涵蓋更多「雙工」服務。</span><span class="sxs-lookup"><span data-stu-id="a3a5d-204">The next section will cover the more involved "duplex" services.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a3a5d-205">[上一頁](create-project.md)
>[下一頁](migrate-duplex-services.md)</span><span class="sxs-lookup"><span data-stu-id="a3a5d-205">[Previous](create-project.md)
[Next](migrate-duplex-services.md)</span></span>
