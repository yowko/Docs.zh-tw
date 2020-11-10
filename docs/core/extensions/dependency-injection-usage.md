---
title: 使用 .NET 中的相依性插入
description: 瞭解如何在您的 .NET 應用程式中使用相依性插入。
author: IEvangelist
ms.author: dapine
ms.date: 09/23/2020
ms.topic: tutorial
no-loc:
- 'Transient'
- 'Scoped'
- 'Singleton'
- 'Example'
ms.openlocfilehash: 589e15736c07b465fda308b04c91384a2502755c
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888582"
---
# <a name="tutorial-use-dependency-injection-in-net"></a><span data-ttu-id="7cae4-103">教學課程：在 .NET 中使用相依性插入</span><span class="sxs-lookup"><span data-stu-id="7cae4-103">Tutorial: Use dependency injection in .NET</span></span>

<span data-ttu-id="7cae4-104">本教學課程說明如何 [在 .net 中使用相依性插入 (DI) ](dependency-injection.md)。</span><span class="sxs-lookup"><span data-stu-id="7cae4-104">This tutorial shows how to use [dependency injection (DI) in .NET](dependency-injection.md).</span></span> <span data-ttu-id="7cae4-105">使用 *Microsoft 擴充* 功能時，DI 是在中新增和設定服務的第一類公民 <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> 。</span><span class="sxs-lookup"><span data-stu-id="7cae4-105">With *Microsoft Extensions* , DI is a first-class citizen where services are added and configured in an <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span></span> <span data-ttu-id="7cae4-106"><xref:Microsoft.Extensions.Hosting.IHost>介面會公開 <xref:System.IServiceProvider> 實例，作為所有已註冊服務的容器。</span><span class="sxs-lookup"><span data-stu-id="7cae4-106">The <xref:Microsoft.Extensions.Hosting.IHost> interface exposes the <xref:System.IServiceProvider> instance, which acts as a container of all the registered services.</span></span>

<span data-ttu-id="7cae4-107">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="7cae4-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="7cae4-108">建立使用相依性插入的 .NET 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="7cae4-108">Create a .NET console app that uses dependency injection</span></span>
> - <span data-ttu-id="7cae4-109">建立並設定 [泛型主機](generic-host.md)</span><span class="sxs-lookup"><span data-stu-id="7cae4-109">Build and configure a [Generic Host](generic-host.md)</span></span>
> - <span data-ttu-id="7cae4-110">撰寫數個介面和對應的實作為</span><span class="sxs-lookup"><span data-stu-id="7cae4-110">Write several interfaces and corresponding implementations</span></span>
> - <span data-ttu-id="7cae4-111">針對 DI 使用服務存留期和範圍</span><span class="sxs-lookup"><span data-stu-id="7cae4-111">Use service lifetime and scoping for DI</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7cae4-112">先決條件</span><span class="sxs-lookup"><span data-stu-id="7cae4-112">Prerequisites</span></span>

- <span data-ttu-id="7cae4-113">[.Net Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="7cae4-113">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) or later.</span></span>
- <span data-ttu-id="7cae4-114">熟悉如何建立新的 .NET 應用程式及安裝 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="7cae4-114">Familiarity with creating new .NET applications and installing NuGet packages.</span></span>

## <a name="create-a-new-console-application"></a><span data-ttu-id="7cae4-115">建立新的主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="7cae4-115">Create a new console application</span></span>

<span data-ttu-id="7cae4-116">使用 [dotnet new](../tools/dotnet-new.md)命令或 IDE [新增專案] 嚮導，建立名為 **Example ConsoleDI** 的新 .net 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="7cae4-116">Using either the [dotnet new](../tools/dotnet-new.md) command or an IDE new project wizard, create a new .NET console application named **ConsoleDI.Example** .</span></span> <span data-ttu-id="7cae4-117">將 [裝載](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) NuGet 套件的專案新增至專案。</span><span class="sxs-lookup"><span data-stu-id="7cae4-117">Add the [Microsoft.Extensions.Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) NuGet package to the project.</span></span>

## <a name="add-interfaces"></a><span data-ttu-id="7cae4-118">新增介面</span><span class="sxs-lookup"><span data-stu-id="7cae4-118">Add interfaces</span></span>

<span data-ttu-id="7cae4-119">將下列介面新增至專案根目錄：</span><span class="sxs-lookup"><span data-stu-id="7cae4-119">Add the following interfaces to the project root directory:</span></span>

<span data-ttu-id="7cae4-120">*IOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="7cae4-120">*IOperation.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/IOperation.cs":::

<span data-ttu-id="7cae4-121">`IOperation`介面會定義單一 `OperationId` 屬性。</span><span class="sxs-lookup"><span data-stu-id="7cae4-121">The `IOperation` interface defines a single `OperationId` property.</span></span>

<span data-ttu-id="7cae4-122">*我 Transient Operation.cs*</span><span class="sxs-lookup"><span data-stu-id="7cae4-122">*ITransientOperation.cs*</span></span>

<span data-ttu-id="7cae4-123">：：： code language = "csharp" source = "程式碼片段/設定/主控台-di/I Transient Operation.cs"：：：</span><span class="sxs-lookup"><span data-stu-id="7cae4-123">:::code language="csharp" source="snippets/configuration/console-di/ITransientOperation.cs":::</span></span>

<span data-ttu-id="7cae4-124">*我 Scoped Operation.cs*</span><span class="sxs-lookup"><span data-stu-id="7cae4-124">*IScopedOperation.cs*</span></span>

<span data-ttu-id="7cae4-125">：：： code language = "csharp" source = "程式碼片段/設定/主控台-di/I Scoped Operation.cs"：：：</span><span class="sxs-lookup"><span data-stu-id="7cae4-125">:::code language="csharp" source="snippets/configuration/console-di/IScopedOperation.cs":::</span></span>

<span data-ttu-id="7cae4-126">*我 Singleton Operation.cs*</span><span class="sxs-lookup"><span data-stu-id="7cae4-126">*ISingletonOperation.cs*</span></span>

<span data-ttu-id="7cae4-127">：：： code language = "csharp" source = "程式碼片段/設定/主控台-di/I Singleton Operation.cs"：：：</span><span class="sxs-lookup"><span data-stu-id="7cae4-127">:::code language="csharp" source="snippets/configuration/console-di/ISingletonOperation.cs":::</span></span>

<span data-ttu-id="7cae4-128">`IOperation`其預期服務存留期的所有名稱子介面。</span><span class="sxs-lookup"><span data-stu-id="7cae4-128">All of the subinterfaces of `IOperation` name their intended service lifetime.</span></span> <span data-ttu-id="7cae4-129">例如，" Transient " 或 " Singleton "。</span><span class="sxs-lookup"><span data-stu-id="7cae4-129">For example, "Transient" or "Singleton".</span></span>

## <a name="add-default-implementation"></a><span data-ttu-id="7cae4-130">新增預設實作為</span><span class="sxs-lookup"><span data-stu-id="7cae4-130">Add default implementation</span></span>

<span data-ttu-id="7cae4-131">針對各種作業新增下列預設實作為：</span><span class="sxs-lookup"><span data-stu-id="7cae4-131">Add the following default implementation for the various operations:</span></span>

<span data-ttu-id="7cae4-132">*DefaultOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="7cae4-132">*DefaultOperation.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/DefaultOperation.cs":::

<span data-ttu-id="7cae4-133">會實作為 `DefaultOperation` 所有命名標記介面，並將 `OperationId` 屬性初始化為新全域唯一識別碼 (GUID) 的最後四個字元。</span><span class="sxs-lookup"><span data-stu-id="7cae4-133">The `DefaultOperation` implements all of the named marker interfaces and initializes the `OperationId` property to the last four characters of a new globally unique identifier (GUID).</span></span>

## <a name="add-service-that-requires-di"></a><span data-ttu-id="7cae4-134">新增需要 DI 的服務</span><span class="sxs-lookup"><span data-stu-id="7cae4-134">Add service that requires DI</span></span>

<span data-ttu-id="7cae4-135">新增下列作業記錄器物件，作為主控台應用程式的服務：</span><span class="sxs-lookup"><span data-stu-id="7cae4-135">Add the following operation logger object, which acts as a service to the console app:</span></span>

<span data-ttu-id="7cae4-136">*OperationLogger.cs*</span><span class="sxs-lookup"><span data-stu-id="7cae4-136">*OperationLogger.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/OperationLogger.cs":::

<span data-ttu-id="7cae4-137">`OperationLogger`會定義需要上述每一個標記介面的函式，也就是 `ITransientOperation` 、 `IScopedOperation` 和 `ISingletonOperation` 。</span><span class="sxs-lookup"><span data-stu-id="7cae4-137">The `OperationLogger` defines a constructor that requires each of the aforementioned marker interfaces, that is; `ITransientOperation`, `IScopedOperation`, and `ISingletonOperation`.</span></span> <span data-ttu-id="7cae4-138">此物件會公開單一方法，讓取用者使用指定的參數來記錄作業 `scope` 。</span><span class="sxs-lookup"><span data-stu-id="7cae4-138">The object exposes a single method that allows the consumer to log the operations with a given `scope` parameter.</span></span> <span data-ttu-id="7cae4-139">叫用時， `LogOperations` 方法會使用範圍字串和訊息來記錄每個作業的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="7cae4-139">When invoked, the `LogOperations` method logs each operation's unique identifier with the scope string and message.</span></span>

## <a name="register-services-for-di"></a><span data-ttu-id="7cae4-140">註冊適用于 DI 的服務</span><span class="sxs-lookup"><span data-stu-id="7cae4-140">Register services for DI</span></span>

<span data-ttu-id="7cae4-141">使用下列程式碼更新 *Program.cs* ：</span><span class="sxs-lookup"><span data-stu-id="7cae4-141">Update *Program.cs* with the following code:</span></span>

:::code language="csharp" source="snippets/configuration/console-di/Program.cs" range="1-18,35-60" highlight="22-26":::

<span data-ttu-id="7cae4-142">應用程式：</span><span class="sxs-lookup"><span data-stu-id="7cae4-142">The app:</span></span>

- <span data-ttu-id="7cae4-143"><xref:Microsoft.Extensions.Hosting.IHostBuilder>使用預設系結器[設定](generic-host.md#default-builder-settings)建立實例。</span><span class="sxs-lookup"><span data-stu-id="7cae4-143">Creates an <xref:Microsoft.Extensions.Hosting.IHostBuilder> instance with the [default binder settings](generic-host.md#default-builder-settings).</span></span>
- <span data-ttu-id="7cae4-144">設定服務，並將其新增至其對應的服務存留期。</span><span class="sxs-lookup"><span data-stu-id="7cae4-144">Configures services and adds them with their corresponding service lifetime.</span></span>
- <span data-ttu-id="7cae4-145">呼叫 <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> 並指派的實例 <xref:Microsoft.Extensions.Hosting.IHost> 。</span><span class="sxs-lookup"><span data-stu-id="7cae4-145">Calls <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> and assigns an instance of <xref:Microsoft.Extensions.Hosting.IHost>.</span></span>
- <span data-ttu-id="7cae4-146">呼叫 `ExemplifyScoping` ，傳入 <xref:Microsoft.Extensions.Hosting.IHost.Services?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="7cae4-146">Calls `ExemplifyScoping`, passing in the <xref:Microsoft.Extensions.Hosting.IHost.Services?displayProperty=nameWithType>.</span></span>

## <a name="conclusion"></a><span data-ttu-id="7cae4-147">結論</span><span class="sxs-lookup"><span data-stu-id="7cae4-147">Conclusion</span></span>

<span data-ttu-id="7cae4-148">應用程式會顯示類似下列範例的輸出：</span><span class="sxs-lookup"><span data-stu-id="7cae4-148">The app displays output similar to the following example:</span></span>

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

<span data-ttu-id="7cae4-149">從應用程式輸出中，您可以看到：</span><span class="sxs-lookup"><span data-stu-id="7cae4-149">From the app output, you can see that:</span></span>

- <span data-ttu-id="7cae4-150">Transient 作業永遠不同，會在每次抓取服務時建立新的實例。</span><span class="sxs-lookup"><span data-stu-id="7cae4-150">Transient operations are always different, a new instance is created with every retrieval of the service.</span></span>
- <span data-ttu-id="7cae4-151">Scoped 作業只會與新的範圍變更，但在範圍內是相同的實例。</span><span class="sxs-lookup"><span data-stu-id="7cae4-151">Scoped operations change only with a new scope, but are the same instance within a scope.</span></span>
- <span data-ttu-id="7cae4-152">Singleton 作業一律相同，只會建立一次新的實例。</span><span class="sxs-lookup"><span data-stu-id="7cae4-152">Singleton operations are always the same, a new instance is only created once.</span></span>

## <a name="see-also"></a><span data-ttu-id="7cae4-153">請參閱</span><span class="sxs-lookup"><span data-stu-id="7cae4-153">See also</span></span>

* [<span data-ttu-id="7cae4-154">相依性插入指導方針</span><span class="sxs-lookup"><span data-stu-id="7cae4-154">Dependency injection guidelines</span></span>](dependency-injection-guidelines.md)
* [<span data-ttu-id="7cae4-155">ASP.NET Core 中的相依性插入</span><span class="sxs-lookup"><span data-stu-id="7cae4-155">Dependency injection in ASP.NET Core</span></span>](/aspnet/core/fundamentals/dependency-injection)
