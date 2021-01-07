---
title: 建立新的 ASP.NET Core gRPC 專案-gRPC （適用于 WCF 開發人員）
description: 瞭解如何使用 Visual Studio 或命令列來建立 gRPC 專案。
ms.date: 01/06/2021
ms.openlocfilehash: c9d66a773f0633c2ae93c42ce3ce53084032cd17
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970254"
---
# <a name="create-a-new-aspnet-core-grpc-project"></a><span data-ttu-id="5976b-103">建立新的 ASP.NET Core gRPC 專案</span><span class="sxs-lookup"><span data-stu-id="5976b-103">Create a new ASP.NET Core gRPC project</span></span>

<span data-ttu-id="5976b-104">.NET SDK 隨附強大的 CLI 工具，可 `dotnet` 讓您從命令列建立和管理專案和解決方案。</span><span class="sxs-lookup"><span data-stu-id="5976b-104">The .NET SDK comes with a powerful CLI tool, `dotnet`, which enables you to create and manage projects and solutions from the command line.</span></span> <span data-ttu-id="5976b-105">SDK 與 Visual Studio 緊密整合，因此您也可以透過熟悉的圖形化使用者介面來取得所有專案。</span><span class="sxs-lookup"><span data-stu-id="5976b-105">The SDK is closely integrated with Visual Studio, so everything is also available through the familiar graphical user interface.</span></span> <span data-ttu-id="5976b-106">本章將說明建立新的 ASP.NET Core gRPC 專案的兩種方式。</span><span class="sxs-lookup"><span data-stu-id="5976b-106">This chapter shows both ways to create a new ASP.NET Core gRPC project.</span></span>

## <a name="create-the-project-by-using-visual-studio"></a><span data-ttu-id="5976b-107">使用 Visual Studio 建立專案</span><span class="sxs-lookup"><span data-stu-id="5976b-107">Create the project by using Visual Studio</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5976b-108">若要開發任何 ASP.NET Core 5.0 應用程式，您需要已安裝 **ASP.NET 和 網頁程式開發** 工作負載的 Visual Studio 2019 16.8 版或更新版本。</span><span class="sxs-lookup"><span data-stu-id="5976b-108">To develop any ASP.NET Core 5.0 app, you need Visual Studio 2019 version 16.8 or later, with the **ASP.NET and web development** workload installed.</span></span>

<span data-ttu-id="5976b-109">從 *空白解決方案* 範本建立稱為 **TraderSys** 的空白解決方案。</span><span class="sxs-lookup"><span data-stu-id="5976b-109">Create an empty solution called **TraderSys** from the *Blank Solution* template.</span></span> <span data-ttu-id="5976b-110">加入名為的方案資料夾 `src` 。</span><span class="sxs-lookup"><span data-stu-id="5976b-110">Add a solution folder called `src`.</span></span> <span data-ttu-id="5976b-111">然後，在資料夾上按一下滑鼠右鍵，然後選擇 [**加入**  >  **新專案**]。</span><span class="sxs-lookup"><span data-stu-id="5976b-111">Then, right-click on the folder and choose **Add** > **New Project**.</span></span> <span data-ttu-id="5976b-112">`grpc`在範本搜尋方塊中輸入，您應該會看到名為的專案範本 `gRPC Service` 。</span><span class="sxs-lookup"><span data-stu-id="5976b-112">Enter `grpc` in the template search box, and you should see a project template called `gRPC Service`.</span></span>

![[加入新專案] 對話方塊的螢幕擷取畫面](media/create-project/new-grpc-project.png)

<span data-ttu-id="5976b-114">選取 **[下一步** ] 以繼續前往 [ **設定您的新專案** ] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="5976b-114">Select **Next** to continue to the **Configure your new project** dialog box.</span></span> <span data-ttu-id="5976b-115">為專案命名 `TraderSys.Portfolios` ，並將 `src` 子目錄新增至該 **位置**。</span><span class="sxs-lookup"><span data-stu-id="5976b-115">Name the project `TraderSys.Portfolios` and add an `src` subdirectory to the **Location**.</span></span>

![[設定您的新專案] 對話方塊的螢幕擷取畫面](media/create-project/configure-project.png)

<span data-ttu-id="5976b-117">選取 **[下一步** ] 繼續前往 [ **建立新的 gRPC 服務** ] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="5976b-117">Select **Next** to continue to the **Create a new gRPC service** dialog box.</span></span>

![[建立新的 gRPC 服務] 對話方塊的螢幕擷取畫面](media/create-project/create-new-grpc-service-v2.png)

<span data-ttu-id="5976b-119">目前，您有限制的服務建立選項。</span><span class="sxs-lookup"><span data-stu-id="5976b-119">At present, you have limited options for the service creation.</span></span> <span data-ttu-id="5976b-120">Docker 將于稍後推出，因此現在請將該選項保留為未選取狀態。</span><span class="sxs-lookup"><span data-stu-id="5976b-120">Docker will be introduced later, so for now, leave that option unselected.</span></span> <span data-ttu-id="5976b-121">只需選取 [ **建立**]。</span><span class="sxs-lookup"><span data-stu-id="5976b-121">Just select **Create**.</span></span> <span data-ttu-id="5976b-122">系統會產生您的第一個 ASP.NET Core 5.0 gRPC 專案，並將其新增至方案。</span><span class="sxs-lookup"><span data-stu-id="5976b-122">Your first ASP.NET Core 5.0 gRPC project is generated and added to the solution.</span></span> <span data-ttu-id="5976b-123">如果您不想要知道如何使用 `dotnet CLI` ，請跳至 [清除範例程式碼](#clean-up-the-example-code) 一節。</span><span class="sxs-lookup"><span data-stu-id="5976b-123">If you don't want to know about working with the `dotnet CLI`, skip to the [Clean up the example code](#clean-up-the-example-code) section.</span></span>

## <a name="create-the-project-by-using-the-net-cli"></a><span data-ttu-id="5976b-124">使用 .NET CLI 建立專案</span><span class="sxs-lookup"><span data-stu-id="5976b-124">Create the project by using the .NET CLI</span></span>

<span data-ttu-id="5976b-125">本節將說明如何從命令列建立方案和專案。</span><span class="sxs-lookup"><span data-stu-id="5976b-125">This section covers the creation of solutions and projects from the command line.</span></span>

<span data-ttu-id="5976b-126">建立解決方案，如下列命令所示。</span><span class="sxs-lookup"><span data-stu-id="5976b-126">Create the solution as shown in the following command.</span></span> <span data-ttu-id="5976b-127">`-o` (或 `--output`) 旗標會指定在目前的目錄中建立的輸出目錄（如果尚未存在）。</span><span class="sxs-lookup"><span data-stu-id="5976b-127">The `-o` (or `--output`) flag specifies the output directory, which is created in the current directory if it doesn't already exist.</span></span> <span data-ttu-id="5976b-128">方案與目錄具有相同的名稱： `TraderSys.sln` 。</span><span class="sxs-lookup"><span data-stu-id="5976b-128">The solution has the same name as the directory: `TraderSys.sln`.</span></span> <span data-ttu-id="5976b-129">您可以使用 `-n` (或) 旗標來提供不同的名稱 `--name` 。</span><span class="sxs-lookup"><span data-stu-id="5976b-129">You can provide a different name by using the `-n` (or `--name`) flag.</span></span>

```dotnetcli
dotnet new sln -o TraderSys
cd TraderSys
```

<span data-ttu-id="5976b-130">ASP.NET Core 5.0 隨附 gRPC services 的 CLI 範本。</span><span class="sxs-lookup"><span data-stu-id="5976b-130">ASP.NET Core 5.0 comes with a CLI template for gRPC services.</span></span> <span data-ttu-id="5976b-131">使用此範本建立新的專案，並將其放入 `src` 子目錄中，作為 ASP.NET Core 專案的傳統方式。</span><span class="sxs-lookup"><span data-stu-id="5976b-131">Create the new project by using this template, putting it into an `src` subdirectory as is conventional for ASP.NET Core projects.</span></span> <span data-ttu-id="5976b-132">`TraderSys.Portfolios.csproj`除非您使用旗標指定不同的名稱，否則專案會以目錄 () 來命名 `-n` 。</span><span class="sxs-lookup"><span data-stu-id="5976b-132">The project is named after the directory (`TraderSys.Portfolios.csproj`), unless you specify a different name with the `-n` flag.</span></span>

```dotnetcli
dotnet new grpc -o src/TraderSys.Portfolios
```

<span data-ttu-id="5976b-133">最後，使用下列命令將專案新增至方案 `dotnet sln` ：</span><span class="sxs-lookup"><span data-stu-id="5976b-133">Finally, add the project to the solution by using the `dotnet sln` command:</span></span>

```dotnetcli
dotnet sln add src/TraderSys.Portfolios
```

> [!TIP]
> <span data-ttu-id="5976b-134">因為特定目錄只包含單一檔案 `.csproj` ，所以您可以只指定目錄來儲存鍵入。</span><span class="sxs-lookup"><span data-stu-id="5976b-134">Because the particular directory only contains a single `.csproj` file, you can specify just the directory, to save typing.</span></span>

<span data-ttu-id="5976b-135">您現在可以在 Visual Studio 2019、Visual Studio Code 或任何偏好的編輯器中開啟此方案。</span><span class="sxs-lookup"><span data-stu-id="5976b-135">You can now open this solution in Visual Studio 2019, Visual Studio Code, or whatever editor you prefer.</span></span>

## <a name="clean-up-the-example-code"></a><span data-ttu-id="5976b-136">清除範例程式碼</span><span class="sxs-lookup"><span data-stu-id="5976b-136">Clean up the example code</span></span>

<span data-ttu-id="5976b-137">您現在已使用 gRPC 範本建立了範例服務，此範本已在本書稍早審核。</span><span class="sxs-lookup"><span data-stu-id="5976b-137">You've now created an example service by using the gRPC template, which was reviewed earlier in the book.</span></span> <span data-ttu-id="5976b-138">這段程式碼在股票交易內容中並不實用，因此我們將編輯第一個專案的內容。</span><span class="sxs-lookup"><span data-stu-id="5976b-138">This code isn't useful in our stock trading context, so we'll edit things for our first project.</span></span>

### <a name="rename-and-edit-the-proto-file"></a><span data-ttu-id="5976b-139">重新命名和編輯 proto 檔案</span><span class="sxs-lookup"><span data-stu-id="5976b-139">Rename and edit the proto file</span></span>

<span data-ttu-id="5976b-140">繼續並將檔案重新命名 `Protos/greet.proto` 為 `Protos/portfolios.proto` ，並在編輯器中開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="5976b-140">Go ahead and rename the `Protos/greet.proto` file to `Protos/portfolios.proto`, and open it in your editor.</span></span> <span data-ttu-id="5976b-141">刪除該行之後的所有專案 `package` 。</span><span class="sxs-lookup"><span data-stu-id="5976b-141">Delete everything after the `package` line.</span></span> <span data-ttu-id="5976b-142">然後變更 `option csharp_namespace` 、 `package` 和 `service` 名稱，然後移除預設 `SayHello` 服務。</span><span class="sxs-lookup"><span data-stu-id="5976b-142">Then change the `option csharp_namespace`, `package` and `service` names, and remove the default `SayHello` service.</span></span> <span data-ttu-id="5976b-143">程式碼現在看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="5976b-143">The code now looks like the following:</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

> [!TIP]
> <span data-ttu-id="5976b-144">範本預設不會新增 `Protos` 命名空間元件，但新增它可讓您更輕鬆地將 gRPC 產生的類別和您自己的類別明確地分隔在程式碼中。</span><span class="sxs-lookup"><span data-stu-id="5976b-144">The template doesn't add the `Protos` namespace part by default, but adding it makes it easier to keep gRPC-generated classes and your own classes clearly separated in your code.</span></span>

<span data-ttu-id="5976b-145">如果您 `greet.proto` 在整合式開發環境中重新命名檔案 (IDE) 例如 Visual Studio，則會自動更新檔案中的這個檔案參考 `.csproj` 。</span><span class="sxs-lookup"><span data-stu-id="5976b-145">If you rename the `greet.proto` file in an integrated development environment (IDE) like Visual Studio, a reference to this file is automatically updated in the `.csproj` file.</span></span> <span data-ttu-id="5976b-146">但是在某些其他編輯器中（例如 Visual Studio Code），此參考不會自動更新，因此您需要手動編輯專案檔。</span><span class="sxs-lookup"><span data-stu-id="5976b-146">But in some other editor, such as Visual Studio Code, this reference isn't updated automatically, so you need to edit the project file manually.</span></span>

<span data-ttu-id="5976b-147">在 gRPC 組建目標中，有一個 `Protobuf` 專案專案可讓您指定 `.proto` 應該編譯哪些檔案，以及需要何種形式的程式碼產生 (也就是「伺服器」或「用戶端」 ) 。</span><span class="sxs-lookup"><span data-stu-id="5976b-147">In the gRPC build targets, there's a `Protobuf` item element that lets you specify which `.proto` files should be compiled, and which form of code generation is required (that is, "Server" or "Client").</span></span>

```xml
<ItemGroup>
  <Protobuf Include="Protos\portfolios.proto" GrpcServices="Server" />
</ItemGroup>
```

### <a name="rename-the-greeterservice-class"></a><span data-ttu-id="5976b-148">重新命名 `GreeterService` 類別</span><span class="sxs-lookup"><span data-stu-id="5976b-148">Rename the `GreeterService` class</span></span>

<span data-ttu-id="5976b-149">`GreeterService`類別位於 `Services` 資料夾中，並繼承自 `Greeter.GreeterBase` 。</span><span class="sxs-lookup"><span data-stu-id="5976b-149">The `GreeterService` class is in the `Services` folder and inherits from `Greeter.GreeterBase`.</span></span> <span data-ttu-id="5976b-150">將它重新命名為 `PortfolioService` ，並將基類變更為 `Portfolios.PortfoliosBase` 。</span><span class="sxs-lookup"><span data-stu-id="5976b-150">Rename it to `PortfolioService`, and change the base class to `Portfolios.PortfoliosBase`.</span></span> <span data-ttu-id="5976b-151">刪除 `override` 方法。</span><span class="sxs-lookup"><span data-stu-id="5976b-151">Delete the `override` methods.</span></span>

```csharp
public class PortfolioService : Portfolios.PortfoliosBase
{
}
```

<span data-ttu-id="5976b-152">在類別的方法中，有類別的參考 `GreeterService` `Configure` `Startup` 。</span><span class="sxs-lookup"><span data-stu-id="5976b-152">There was a reference to the `GreeterService` class in the `Configure` method in the `Startup` class.</span></span> <span data-ttu-id="5976b-153">如果您使用重構來重新命名類別，則應該會自動更新此參考。</span><span class="sxs-lookup"><span data-stu-id="5976b-153">If you used refactoring to rename the class, this reference should have been updated automatically.</span></span> <span data-ttu-id="5976b-154">但是，如果您沒有這麼做，您需要手動進行編輯。</span><span class="sxs-lookup"><span data-stu-id="5976b-154">However, if you didn't, you need to edit it manually.</span></span>

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

<span data-ttu-id="5976b-155">在下一節中，我們會將功能新增至這個新的服務。</span><span class="sxs-lookup"><span data-stu-id="5976b-155">In the next section, we'll add functionality to this new service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5976b-156">[上一個](migrate-wcf-to-grpc.md) 
>[下一步](migrate-request-reply.md)</span><span class="sxs-lookup"><span data-stu-id="5976b-156">[Previous](migrate-wcf-to-grpc.md)
[Next](migrate-request-reply.md)</span></span>
