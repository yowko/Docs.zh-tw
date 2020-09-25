---
title: 使用 .NET 中的相依性插入
description: 瞭解如何在您的 .NET 應用程式中使用相依性插入。
author: IEvangelist
ms.author: dapine
ms.date: 09/23/2020
ms.topic: tutorial
ms.openlocfilehash: f2298cb0be6d555a7636903dc251f022a6a62a43
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2020
ms.locfileid: "91247885"
---
# <a name="tutorial-use-dependency-injection-in-net"></a><span data-ttu-id="ce1d9-103">教學課程：在 .NET 中使用相依性插入</span><span class="sxs-lookup"><span data-stu-id="ce1d9-103">Tutorial: Use dependency injection in .NET</span></span>

<span data-ttu-id="ce1d9-104">本教學課程說明如何 [在 .net 中使用相依性插入 (DI) ](dependency-injection.md)。</span><span class="sxs-lookup"><span data-stu-id="ce1d9-104">This tutorial shows how to use [dependency injection (DI) in .NET](dependency-injection.md).</span></span> <span data-ttu-id="ce1d9-105">使用 *Microsoft 擴充*功能時，DI 是在中新增和設定服務的第一類公民 <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> 。</span><span class="sxs-lookup"><span data-stu-id="ce1d9-105">With *Microsoft Extensions*, DI is a first-class citizen where services are added and configured in an <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span></span> <span data-ttu-id="ce1d9-106"><xref:Microsoft.Extensions.Hosting.IHost>介面會公開 <xref:System.IServiceProvider> 實例，作為所有已註冊服務的容器。</span><span class="sxs-lookup"><span data-stu-id="ce1d9-106">The <xref:Microsoft.Extensions.Hosting.IHost> interface exposes the <xref:System.IServiceProvider> instance, which acts as a container of all the registered services.</span></span>

<span data-ttu-id="ce1d9-107">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="ce1d9-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="ce1d9-108">建立使用相依性插入的 .NET 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="ce1d9-108">Create a .NET console app that uses dependency injection</span></span>
> - <span data-ttu-id="ce1d9-109">建立並設定 [泛型主機](generic-host.md)</span><span class="sxs-lookup"><span data-stu-id="ce1d9-109">Build and configure a [Generic Host](generic-host.md)</span></span>
> - <span data-ttu-id="ce1d9-110">撰寫數個介面和對應的實作為</span><span class="sxs-lookup"><span data-stu-id="ce1d9-110">Write several interfaces and corresponding implementations</span></span>
> - <span data-ttu-id="ce1d9-111">針對 DI 使用服務存留期和範圍</span><span class="sxs-lookup"><span data-stu-id="ce1d9-111">Use service lifetime and scoping for DI</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ce1d9-112">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="ce1d9-112">Prerequisites</span></span>

- <span data-ttu-id="ce1d9-113">[.Net Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="ce1d9-113">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="ce1d9-114">整合式開發環境 (IDE) 、 [Visual Studio、Visual Studio Code 或 Visual Studio for Mac](https://visualstudio.microsoft.com) 全都是有效的選擇。</span><span class="sxs-lookup"><span data-stu-id="ce1d9-114">An Integrated Development Environment (IDE), [Visual Studio, Visual Studio Code, or Visual Studio for Mac](https://visualstudio.microsoft.com) are all valid choices.</span></span>
- <span data-ttu-id="ce1d9-115">熟悉如何建立新的 .NET 應用程式及安裝 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="ce1d9-115">Familiarity with creating new .NET applications and installing NuGet packages.</span></span>

## <a name="create-a-new-console-application"></a><span data-ttu-id="ce1d9-116">建立新的主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="ce1d9-116">Create a new console application</span></span>

<span data-ttu-id="ce1d9-117">使用 [dotnet new](../tools/dotnet-new.md) 命令或 IDE [新增專案] 嚮導，建立名為 ConsoleDI 的新 .net 主控台應用程式 **。範例**。</span><span class="sxs-lookup"><span data-stu-id="ce1d9-117">Using either the [dotnet new](../tools/dotnet-new.md) command or an IDE new project wizard, create a new .NET console application named **ConsoleDI.Example**.</span></span> <span data-ttu-id="ce1d9-118">將 [裝載](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) NuGet 套件的專案新增至專案。</span><span class="sxs-lookup"><span data-stu-id="ce1d9-118">Add the [Microsoft.Extensions.Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) NuGet package to the project.</span></span>

## <a name="add-interfaces"></a><span data-ttu-id="ce1d9-119">新增介面</span><span class="sxs-lookup"><span data-stu-id="ce1d9-119">Add interfaces</span></span>

<span data-ttu-id="ce1d9-120">將下列介面新增至專案根目錄：</span><span class="sxs-lookup"><span data-stu-id="ce1d9-120">Add the following interfaces to the project root directory:</span></span>

<span data-ttu-id="ce1d9-121">*IOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="ce1d9-121">*IOperation.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/IOperation.cs":::

<span data-ttu-id="ce1d9-122">`IOperation`介面會定義單一 `OperationId` 屬性。</span><span class="sxs-lookup"><span data-stu-id="ce1d9-122">The `IOperation` interface defines a single `OperationId` property.</span></span>

<span data-ttu-id="ce1d9-123">*ITransientOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="ce1d9-123">*ITransientOperation.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/ITransientOperation.cs":::

<span data-ttu-id="ce1d9-124">*IScopedOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="ce1d9-124">*IScopedOperation.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/IScopedOperation.cs":::

<span data-ttu-id="ce1d9-125">*ISingletonOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="ce1d9-125">*ISingletonOperation.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/ISingletonOperation.cs":::

<span data-ttu-id="ce1d9-126">`IOperation`其預期服務存留期的所有名稱子介面。</span><span class="sxs-lookup"><span data-stu-id="ce1d9-126">All of the subinterfaces of `IOperation` name their intended service lifetime.</span></span> <span data-ttu-id="ce1d9-127">例如，「暫時性」或「Singleton」。</span><span class="sxs-lookup"><span data-stu-id="ce1d9-127">For example, "Transient" or "Singleton".</span></span>

## <a name="add-default-implementation"></a><span data-ttu-id="ce1d9-128">新增預設實作為</span><span class="sxs-lookup"><span data-stu-id="ce1d9-128">Add default implementation</span></span>

<span data-ttu-id="ce1d9-129">針對各種作業新增下列預設實作為：</span><span class="sxs-lookup"><span data-stu-id="ce1d9-129">Add the following default implementation for the various operations:</span></span>

<span data-ttu-id="ce1d9-130">*DefaultOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="ce1d9-130">*DefaultOperation.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/DefaultOperation.cs":::

<span data-ttu-id="ce1d9-131">會實作為 `DefaultOperation` 所有命名/標記介面，並將 `OperationId` 屬性初始化為新全域唯一識別碼 (GUID) 的最後四個字元。</span><span class="sxs-lookup"><span data-stu-id="ce1d9-131">The `DefaultOperation` implements all of the named/marker interfaces and initializes the `OperationId` property to the last four characters of a new globally unique identifier (GUID).</span></span>

## <a name="add-service-that-requires-di"></a><span data-ttu-id="ce1d9-132">新增需要 DI 的服務</span><span class="sxs-lookup"><span data-stu-id="ce1d9-132">Add service that requires DI</span></span>

<span data-ttu-id="ce1d9-133">新增下列操作記錄器物件，做為您的主控台應用程式的服務：</span><span class="sxs-lookup"><span data-stu-id="ce1d9-133">Add the following operation logger object, which acts as a service to your console application:</span></span>

<span data-ttu-id="ce1d9-134">*OperationLogger.cs*</span><span class="sxs-lookup"><span data-stu-id="ce1d9-134">*OperationLogger.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/OperationLogger.cs":::

<span data-ttu-id="ce1d9-135">`OperationLogger`會定義需要上述每一個標記介面的函式，也就是 `ITransientOperation` 、 `IScopedOperation` 和 `ISingletonOperation` 。</span><span class="sxs-lookup"><span data-stu-id="ce1d9-135">The `OperationLogger` defines a constructor that requires each of the aforementioned marker interfaces, that is; `ITransientOperation`, `IScopedOperation`, and `ISingletonOperation`.</span></span> <span data-ttu-id="ce1d9-136">此物件會公開單一方法，讓取用者使用指定的參數來記錄作業 `scope` 。</span><span class="sxs-lookup"><span data-stu-id="ce1d9-136">The object exposes a single method that allows the consumer to log the operations with a given `scope` parameter.</span></span> <span data-ttu-id="ce1d9-137">叫用時， `LogOperations` 方法會使用範圍字串和訊息來記錄每個作業的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="ce1d9-137">When invoked, the `LogOperations` method will log each operation's unique identifier with the scope string and message.</span></span>

## <a name="register-services-for-di"></a><span data-ttu-id="ce1d9-138">註冊適用于 DI 的服務</span><span class="sxs-lookup"><span data-stu-id="ce1d9-138">Register services for DI</span></span>

<span data-ttu-id="ce1d9-139">最後，更新 *Program.cs* 檔案以符合下列各項：</span><span class="sxs-lookup"><span data-stu-id="ce1d9-139">Finally, update the *Program.cs* file to match following:</span></span>

:::code language="csharp" source="snippets/configuration/console-di/Program.cs" range="1-18,35-60" highlight="22-26":::

<span data-ttu-id="ce1d9-140">應用程式：</span><span class="sxs-lookup"><span data-stu-id="ce1d9-140">The application:</span></span>

- <span data-ttu-id="ce1d9-141"><xref:Microsoft.Extensions.Hosting.IHostBuilder>使用預設系結器[設定](generic-host.md#default-builder-settings)建立實例。</span><span class="sxs-lookup"><span data-stu-id="ce1d9-141">Creates an <xref:Microsoft.Extensions.Hosting.IHostBuilder> instance with the [default binder settings](generic-host.md#default-builder-settings).</span></span>
- <span data-ttu-id="ce1d9-142">設定服務，並將其新增至其對應的服務存留期。</span><span class="sxs-lookup"><span data-stu-id="ce1d9-142">Configures services and adds them with their corresponding service lifetime.</span></span>
- <span data-ttu-id="ce1d9-143">呼叫 <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> 並指派的實例 <xref:Microsoft.Extensions.Hosting.IHost> 。</span><span class="sxs-lookup"><span data-stu-id="ce1d9-143">Calls <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> and assigns an instance of <xref:Microsoft.Extensions.Hosting.IHost>.</span></span>
- <span data-ttu-id="ce1d9-144">呼叫 `ExemplifyScoping` ，傳入 <xref:Microsoft.Extensions.Hosting.IHost.Services?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="ce1d9-144">Calls `ExemplifyScoping`, passing in the <xref:Microsoft.Extensions.Hosting.IHost.Services?displayProperty=nameWithType>.</span></span>

## <a name="conclusion"></a><span data-ttu-id="ce1d9-145">結論</span><span class="sxs-lookup"><span data-stu-id="ce1d9-145">Conclusion</span></span>

<span data-ttu-id="ce1d9-146">應用程式會產生類似下列範例的輸出：</span><span class="sxs-lookup"><span data-stu-id="ce1d9-146">The application produces output similar to the following example:</span></span>

```console
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): ITransientOperation [ 80f4...Always different        ]
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): IScopedOperation    [ c878...Changes only with scope ]
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]
...
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): ITransientOperation [ f3c0...Always different        ]
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): IScopedOperation    [ c878...Changes only with scope ]
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]

Scope 2-Call 1 .GetRequiredService<OperationLogger>(): ITransientOperation [ f9af...Always different        ]
Scope 2-Call 1 .GetRequiredService<OperationLogger>(): IScopedOperation    [ 2bd0...Changes only with scope ]
Scope 2-Call 1 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]
...
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): ITransientOperation [ fa65...Always different        ]
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): IScopedOperation    [ 2bd0...Changes only with scope ]
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]
```

<span data-ttu-id="ce1d9-147">從應用程式輸出中，您可以看到：</span><span class="sxs-lookup"><span data-stu-id="ce1d9-147">From the application output, you can see that:</span></span>

- <span data-ttu-id="ce1d9-148">暫時性作業永遠不同，這表示會在每次抓取服務時建立新的實例。</span><span class="sxs-lookup"><span data-stu-id="ce1d9-148">Transient operations are always different, meaning a new instance is created with every retrieval of the service.</span></span>
- <span data-ttu-id="ce1d9-149">範圍作業只會與新的範圍變更，但在範圍內是相同的實例。</span><span class="sxs-lookup"><span data-stu-id="ce1d9-149">Scoped operations change only with a new scope, but are the same instance within a scope.</span></span>
- <span data-ttu-id="ce1d9-150">單一作業一律是相同的，這表示新實例只會建立一次。</span><span class="sxs-lookup"><span data-stu-id="ce1d9-150">Singleton operations are always the same, meaning a new instance is only created once.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ce1d9-151">後續步驟</span><span class="sxs-lookup"><span data-stu-id="ce1d9-151">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ce1d9-152">相依性插入方針</span><span class="sxs-lookup"><span data-stu-id="ce1d9-152">Dependency injection guidelines</span></span>](dependency-injection-guidelines.md)
