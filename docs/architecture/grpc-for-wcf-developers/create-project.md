---
title: 為 WCF 開發人員建立新的 ASP.NET Core gRPC 專案 gRPC
description: 瞭解如何使用 Visual Studio 或從命令列建立 gRPC 專案。
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: a0fcc3f9c4e32e87260a6bc79205c909ea3800e0
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184565"
---
# <a name="create-a-new-aspnet-core-grpc-project"></a><span data-ttu-id="79fc4-103">建立新的 ASP.NET Core gRPC 專案</span><span class="sxs-lookup"><span data-stu-id="79fc4-103">Create a new ASP.NET Core gRPC project</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="79fc4-104">.Net Core 隨附功能強大的 CLI 工具， `dotnet`可讓您從命令列建立和管理專案和解決方案。</span><span class="sxs-lookup"><span data-stu-id="79fc4-104">.NET Core comes with a powerful CLI tool, `dotnet`, which enables you to create and manage projects and solutions from the command line.</span></span> <span data-ttu-id="79fc4-105">此工具與 Visual Studio 緊密整合，因此您也可以透過熟悉的 GUI 介面取得所有專案。</span><span class="sxs-lookup"><span data-stu-id="79fc4-105">The tool is closely integrated with Visual Studio, so everything is also available through the familiar GUI interface.</span></span> <span data-ttu-id="79fc4-106">本章將示範兩種建立新 ASP.NET Core gRPC 專案的方式：先使用 Visual Studio，然後再加上 .NET Core CLI。</span><span class="sxs-lookup"><span data-stu-id="79fc4-106">This chapter will show both ways to create a new ASP.NET Core gRPC project: first with Visual Studio, then with the .NET Core CLI.</span></span>

## <a name="create-the-project-using-visual-studio"></a><span data-ttu-id="79fc4-107">使用 Visual Studio 建立專案</span><span class="sxs-lookup"><span data-stu-id="79fc4-107">Create the project using Visual Studio</span></span>

> [!IMPORTANT]
> <span data-ttu-id="79fc4-108">若要開發任何 ASP.NET Core 3.0 應用程式，您需要已安裝**ASP.NET 和 網頁程式開發**工作負載的 Visual Studio 2019.3 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="79fc4-108">To develop any ASP.NET Core 3.0 app, you need Visual Studio 2019.3 or later with the **ASP.NET and web development** workload installed.</span></span>

<span data-ttu-id="79fc4-109">從*空白解決方案*範本建立名為**TraderSys**的空白解決方案。</span><span class="sxs-lookup"><span data-stu-id="79fc4-109">Create an empty solution called **TraderSys** from the *Blank Solution* template.</span></span> <span data-ttu-id="79fc4-110">新增名`src`為的方案資料夾，然後以滑鼠右鍵按一下該資料夾，然後從內容功能表選擇 [**加入** > **新專案**]。</span><span class="sxs-lookup"><span data-stu-id="79fc4-110">Add a Solution Folder called `src`, then right-click on the folder and choose **Add** > **New Project** from the context menu.</span></span> <span data-ttu-id="79fc4-111">在`grpc` [範本搜尋] 方塊中輸入，您應該會看到名`gRPC Service`為的專案範本。</span><span class="sxs-lookup"><span data-stu-id="79fc4-111">Enter `grpc` in the template search box and you should see a project template called `gRPC Service`.</span></span>

![顯示 gRPC 服務專案範本的 [新增專案] 對話方塊](media/create-project/new-grpc-project.png)

<span data-ttu-id="79fc4-113">按 **[下一步**] 以繼續前往 [**設定專案**] `TraderSys.Portfolios`對話方塊並為專案`src`命名，並將子目錄新增至該**位置**。</span><span class="sxs-lookup"><span data-stu-id="79fc4-113">Click **Next** to continue to the **Configure project** dialog and name the project `TraderSys.Portfolios`, and add an `src` subdirectory to the **Location**.</span></span>

![[設定專案] 對話方塊](media/create-project/configure-project.png)

<span data-ttu-id="79fc4-115">按 **[下一步**] 以繼續前往 [**新增 gRPC 專案**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="79fc4-115">Click **Next** to continue to the **New gRPC project** dialog.</span></span>

![[新增 gRPC 專案] 對話方塊](media/create-project/create-new-grpc-service.png)

<span data-ttu-id="79fc4-117">目前，服務建立有一些有限的選項。</span><span class="sxs-lookup"><span data-stu-id="79fc4-117">At present, there are limited options for the service creation.</span></span> <span data-ttu-id="79fc4-118">Docker 稍後會在本書中引進，因此請不要勾選該核取方塊，只要按一下 [**建立**] 即可。</span><span class="sxs-lookup"><span data-stu-id="79fc4-118">Docker will be introduced later in the book, so leave that checkbox unchecked for now and just click **Create**.</span></span> <span data-ttu-id="79fc4-119">系統會產生您的第一個 ASP.NET Core 3.0 gRPC 專案，並將其新增至方案。</span><span class="sxs-lookup"><span data-stu-id="79fc4-119">Your first ASP.NET Core 3.0 gRPC project is generated and added to the solution.</span></span> <span data-ttu-id="79fc4-120">如果您不想要知道`dotnet CLI`如何使用，請跳至[清除範例程式碼](#clean-up-the-example-code)一節。</span><span class="sxs-lookup"><span data-stu-id="79fc4-120">If you don't want to know about working with the `dotnet CLI`, skip to the [Clean up the example code](#clean-up-the-example-code) section.</span></span>

## <a name="create-the-project-using-the-net-core-cli"></a><span data-ttu-id="79fc4-121">使用 .NET Core CLI 建立專案</span><span class="sxs-lookup"><span data-stu-id="79fc4-121">Create the project using the .NET Core CLI</span></span>

<span data-ttu-id="79fc4-122">本節說明如何從命令列建立解決方案和專案。</span><span class="sxs-lookup"><span data-stu-id="79fc4-122">This section covers the creation of solutions and projects from the command line.</span></span>

<span data-ttu-id="79fc4-123">建立解決方案，如下所示。</span><span class="sxs-lookup"><span data-stu-id="79fc4-123">Create the solution as shown below.</span></span> <span data-ttu-id="79fc4-124">`-o` （或`--output`）旗標會指定輸出目錄，如果它不存在，則會在目前的目錄中建立。</span><span class="sxs-lookup"><span data-stu-id="79fc4-124">The `-o` (or `--output`) flag specifies the output directory, which will be created in the current directory if it does not exist.</span></span> <span data-ttu-id="79fc4-125">方案的名稱會與目錄相同，例如`TraderSys.sln`。您可以使用`-n` （或`--name`）旗標來提供不同的名稱。</span><span class="sxs-lookup"><span data-stu-id="79fc4-125">The solution will be given the same name as the directory, i.e. `TraderSys.sln`. You can provide a different name using the `-n` (or `--name`) flag.</span></span>

```dotnetcli
dotnet new sln -o TraderSys
cd TraderSys
```

<span data-ttu-id="79fc4-126">ASP.NET Core 3.0 隨附 gRPC services 的 CLI 範本。</span><span class="sxs-lookup"><span data-stu-id="79fc4-126">ASP.NET Core 3.0 comes with a CLI template for gRPC services.</span></span> <span data-ttu-id="79fc4-127">使用此範本建立新的專案，並將其放`src`入子目錄中，如同 ASP.NET Core 專案的慣例。</span><span class="sxs-lookup"><span data-stu-id="79fc4-127">Create the new project using this template, putting it into an `src` subdirectory as is the convention for ASP.NET Core projects.</span></span> <span data-ttu-id="79fc4-128">除非您`TraderSys.Portfolios.csproj` `-n`使用旗標指定不同的名稱，否則專案會以目錄（亦即）命名。</span><span class="sxs-lookup"><span data-stu-id="79fc4-128">The project will be named after the directory (i.e. `TraderSys.Portfolios.csproj`) unless you specify a different name with the `-n` flag.</span></span>

```dotnetcli
dotnet new grpc -o src/TraderSys.Portfolios
```

<span data-ttu-id="79fc4-129">最後，使用`dotnet sln`命令將專案新增至方案。</span><span class="sxs-lookup"><span data-stu-id="79fc4-129">Finally, add the project to the solution using the `dotnet sln` command.</span></span>

```dotnetcli
dotnet sln add src/TraderSys.Portfolios
```

> [!TIP]
> <span data-ttu-id="79fc4-130">由於指定的目錄只包含單一`.csproj`檔案，因此您可以只指定目錄來儲存輸入。</span><span class="sxs-lookup"><span data-stu-id="79fc4-130">Since the given directory only contains a single `.csproj` file, you can get away with specifying just the directory to save typing.</span></span>

<span data-ttu-id="79fc4-131">您現在可以在 Visual Studio 2019、Visual Studio Code 或任何您偏好的編輯器中開啟此方案。</span><span class="sxs-lookup"><span data-stu-id="79fc4-131">You can now open this solution in Visual Studio 2019, Visual Studio Code, or whatever editor you prefer.</span></span>

## <a name="clean-up-the-example-code"></a><span data-ttu-id="79fc4-132">清除範例程式碼</span><span class="sxs-lookup"><span data-stu-id="79fc4-132">Clean up the example code</span></span>

<span data-ttu-id="79fc4-133">您現在已使用 gRPC 範本建立了範例服務，先前已在本書中進行檢查。</span><span class="sxs-lookup"><span data-stu-id="79fc4-133">You've now created an example service using the gRPC template, which was reviewed earlier in the book.</span></span> <span data-ttu-id="79fc4-134">這在我們的股票交易內容中並不實用，因此我們將編輯第一個專案的事項。</span><span class="sxs-lookup"><span data-stu-id="79fc4-134">This isn't useful in our stock trading context, so we'll edit things for our first project.</span></span>

### <a name="rename-and-edit-the-proto-file"></a><span data-ttu-id="79fc4-135">重新命名和編輯 proto 檔案</span><span class="sxs-lookup"><span data-stu-id="79fc4-135">Rename and edit the proto file</span></span>

<span data-ttu-id="79fc4-136">繼續進行，並將`Protos/greet.proto`檔案重新`Protos/portfolios.proto`命名為，並在編輯器中開啟它。</span><span class="sxs-lookup"><span data-stu-id="79fc4-136">Go ahead and rename the `Protos/greet.proto` file to `Protos/portfolios.proto` and open it in your editor.</span></span> <span data-ttu-id="79fc4-137">刪除`package`行之後的所有專案，然後`option csharp_namespace`變更、 `package`和`service`名稱，並移除預設`SayHello`服務，讓程式碼看起來像這樣。</span><span class="sxs-lookup"><span data-stu-id="79fc4-137">Delete everything after the `package` line, then change the `option csharp_namespace`, `package` and `service` names, and remove the default `SayHello` service, so the code looks like this.</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

> [!TIP]
> <span data-ttu-id="79fc4-138">範本預設不會新增`Protos`命名空間部分，但新增它可讓您更輕鬆地將 gRPC 產生的類別和您自己的類別明確分隔在程式碼中。</span><span class="sxs-lookup"><span data-stu-id="79fc4-138">The template doesn't add the `Protos` namespace part by default, but adding it makes it easier to keep gRPC-generated classes and your own classes clearly separated in your code.</span></span>

<span data-ttu-id="79fc4-139">如果您在 Visual Studio `greet.proto`之類的整合式開發環境（IDE）中重新命名檔案，檔案中會自動更新`.csproj`此檔案的參考。</span><span class="sxs-lookup"><span data-stu-id="79fc4-139">If you rename the `greet.proto` file in an integrated development environment (IDE) like Visual Studio, a reference to this file is automatically updated in the `.csproj` file.</span></span> <span data-ttu-id="79fc4-140">但是在某些其他編輯器（例如 Visual Studio Code）中，此參考不會自動更新，因此您必須手動編輯專案檔。</span><span class="sxs-lookup"><span data-stu-id="79fc4-140">But in some other editor, such as Visual Studio Code, this reference isn't updated automatically, so you need to edit the project file manually.</span></span>

<span data-ttu-id="79fc4-141">在 gRPC 組建目標中，有一個`Protobuf` item 專案，可讓您指定應該編譯的`.proto`檔案，以及需要產生哪一種程式碼（也就是「伺服器」或「用戶端」）。</span><span class="sxs-lookup"><span data-stu-id="79fc4-141">In the gRPC build targets, there's a `Protobuf` item element that lets you specify which `.proto` files should be compiled and which form of code generation is required (that is, "Server" or "Client").</span></span>

```xml
<ItemGroup>
  <Protobuf Include="Protos\portfolios.proto" GrpcServices="Server" />
</ItemGroup>
```

### <a name="rename-the-greeterservice-class"></a><span data-ttu-id="79fc4-142">重新命名 GreeterService 類別</span><span class="sxs-lookup"><span data-stu-id="79fc4-142">Rename the GreeterService class</span></span>

<span data-ttu-id="79fc4-143">類別位於`Services`資料夾中，並繼承自`Greeter.GreeterBase`。 `GreeterService`</span><span class="sxs-lookup"><span data-stu-id="79fc4-143">The `GreeterService` class is in the `Services` folder and inherits from `Greeter.GreeterBase`.</span></span> <span data-ttu-id="79fc4-144">將它重新`PortfolioService`命名為，並將基類`Portfolios.PortfoliosBase`變更為。</span><span class="sxs-lookup"><span data-stu-id="79fc4-144">Rename it to `PortfolioService` and change the base class to `Portfolios.PortfoliosBase`.</span></span> <span data-ttu-id="79fc4-145">`override`刪除方法。</span><span class="sxs-lookup"><span data-stu-id="79fc4-145">Delete the `override` methods.</span></span>

```csharp
public class PortfolioService : Portfolios.PortfoliosBase
{
}
```

<span data-ttu-id="79fc4-146">在`GreeterService` 類別`Startup`的`Configure`方法中，有類別的參考。</span><span class="sxs-lookup"><span data-stu-id="79fc4-146">There was a reference to the `GreeterService` class in the `Configure` method in the `Startup` class.</span></span> <span data-ttu-id="79fc4-147">如果您使用重構來重新命名類別，此參考應該已自動更新。</span><span class="sxs-lookup"><span data-stu-id="79fc4-147">If you used refactoring to rename the class, this reference should have been updated automatically.</span></span> <span data-ttu-id="79fc4-148">不過，如果您沒有這麼做，則需要手動編輯它。</span><span class="sxs-lookup"><span data-stu-id="79fc4-148">However, if you didn't, you need to edit it manually.</span></span>

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }

    app.UseRouting();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapGrpcService<PortfolioService>();
    });
}
```

<span data-ttu-id="79fc4-149">在下一節中，我們會新增新服務的功能。</span><span class="sxs-lookup"><span data-stu-id="79fc4-149">In the next section, we'll add functionality to this new service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="79fc4-150">[上一頁](migrate-wcf-to-grpc.md)
>[下一頁](migrate-request-reply.md)</span><span class="sxs-lookup"><span data-stu-id="79fc4-150">[Previous](migrate-wcf-to-grpc.md)
[Next](migrate-request-reply.md)</span></span>
