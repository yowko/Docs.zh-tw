---
title: .NET 中的設定
description: 瞭解如何使用設定 API 來設定 .NET 應用程式。
author: IEvangelist
ms.author: dapine
ms.date: 09/16/2020
ms.topic: overview
ms.openlocfilehash: f97bd3fd4881c6b0939635ec2372aee21c670d5d
ms.sourcegitcommit: fe8877e564deb68d77fa4b79f55584ac8d7e8997
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90720747"
---
# <a name="configuration-in-net"></a><span data-ttu-id="76ac8-103">.NET 中的設定</span><span class="sxs-lookup"><span data-stu-id="76ac8-103">Configuration in .NET</span></span>

<span data-ttu-id="76ac8-104">.NET 中的設定是使用一或多個設定 [提供者](#configuration-providers)來執行。</span><span class="sxs-lookup"><span data-stu-id="76ac8-104">Configuration in .NET is performed using one or more [configuration providers](#configuration-providers).</span></span> <span data-ttu-id="76ac8-105">設定提供者會使用各種設定來源從機碼值組讀取設定資料：</span><span class="sxs-lookup"><span data-stu-id="76ac8-105">Configuration providers read configuration data from key-value pairs using a variety of configuration sources:</span></span>

- <span data-ttu-id="76ac8-106">設定檔，例如 *appsettings.js*</span><span class="sxs-lookup"><span data-stu-id="76ac8-106">Settings files, such as *appsettings.json*</span></span>
- <span data-ttu-id="76ac8-107">環境變數</span><span class="sxs-lookup"><span data-stu-id="76ac8-107">Environment variables</span></span>
- [<span data-ttu-id="76ac8-108">Azure 金鑰保存庫</span><span class="sxs-lookup"><span data-stu-id="76ac8-108">Azure Key Vault</span></span>](/azure/key-vault/general/overview)
- [<span data-ttu-id="76ac8-109">Azure 應用程式組態</span><span class="sxs-lookup"><span data-stu-id="76ac8-109">Azure App Configuration</span></span>](/azure/azure-app-configuration/overview)
- <span data-ttu-id="76ac8-110">命令列引數</span><span class="sxs-lookup"><span data-stu-id="76ac8-110">Command-line arguments</span></span>
- <span data-ttu-id="76ac8-111">自訂提供者、已安裝或已建立</span><span class="sxs-lookup"><span data-stu-id="76ac8-111">Custom providers, installed or created</span></span>
- <span data-ttu-id="76ac8-112">目錄檔案</span><span class="sxs-lookup"><span data-stu-id="76ac8-112">Directory files</span></span>
- <span data-ttu-id="76ac8-113">記憶體內部 .NET 物件</span><span class="sxs-lookup"><span data-stu-id="76ac8-113">In-memory .NET objects</span></span>

## <a name="configure-console-apps"></a><span data-ttu-id="76ac8-114">設定主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="76ac8-114">Configure console apps</span></span>

<span data-ttu-id="76ac8-115">根據預設，使用 [dotnet new](../tools/dotnet-new.md) 或 Visual Studio 建立新的 .net 主控台應用程式 *不會* 公開設定功能。</span><span class="sxs-lookup"><span data-stu-id="76ac8-115">New .NET console applications created using [dotnet new](../tools/dotnet-new.md) or Visual Studio by default *do not* expose configuration capabilities.</span></span> <span data-ttu-id="76ac8-116">若要在新的 .NET 主控台應用程式中加入設定，請 [將封裝參考加入](../tools/dotnet-add-package.md) 至 `Microsoft.Extensions.Hosting` 。</span><span class="sxs-lookup"><span data-stu-id="76ac8-116">To add configuration in a new .NET console application, [add a package reference](../tools/dotnet-add-package.md) to `Microsoft.Extensions.Hosting`.</span></span> <span data-ttu-id="76ac8-117">修改 *Program.cs* 檔案，以符合下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="76ac8-117">Modify the *Program.cs* file to match the following code:</span></span>

:::code language="csharp" source="snippets/configuration/console/Program.cs" highlight="12":::

<span data-ttu-id="76ac8-118">方法會依 <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])?displayProperty=nameWithType> 下列順序提供應用程式的預設設定：</span><span class="sxs-lookup"><span data-stu-id="76ac8-118">The <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])?displayProperty=nameWithType> method provides default configuration for the app in the following order:</span></span>

1. <span data-ttu-id="76ac8-119">[ChainedConfigurationProvider](xref:Microsoft.Extensions.Configuration.ChainedConfigurationSource) ：加入現有的 `IConfiguration` 作為來源。</span><span class="sxs-lookup"><span data-stu-id="76ac8-119">[ChainedConfigurationProvider](xref:Microsoft.Extensions.Configuration.ChainedConfigurationSource) : Adds an existing `IConfiguration` as a source.</span></span>
1. <span data-ttu-id="76ac8-120">使用[JSON 設定提供者](configuration-providers.md#file-configuration-provider)的*appsettings.js* 。</span><span class="sxs-lookup"><span data-stu-id="76ac8-120">*appsettings.json* using the [JSON configuration provider](configuration-providers.md#file-configuration-provider).</span></span>
1. <span data-ttu-id="76ac8-121">*appsettings。* `Environment`使用[json 設定提供者](configuration-providers.md#file-configuration-provider)的*json。*</span><span class="sxs-lookup"><span data-stu-id="76ac8-121">*appsettings.*`Environment`*.json* using the [JSON configuration provider](configuration-providers.md#file-configuration-provider).</span></span> <span data-ttu-id="76ac8-122">例如， *appsettings*。***生產環境***。*json* 和 *appsettings*。***開發***。*json*。</span><span class="sxs-lookup"><span data-stu-id="76ac8-122">For example, *appsettings*.***Production***.*json* and *appsettings*.***Development***.*json*.</span></span>
1. <span data-ttu-id="76ac8-123">應用程式在環境中執行時的應用程式秘密 `Development` 。</span><span class="sxs-lookup"><span data-stu-id="76ac8-123">App secrets when the app runs in the `Development` environment.</span></span>
1. <span data-ttu-id="76ac8-124">使用 [環境變數設定提供者](configuration-providers.md#environment-variable-configuration-provider)的環境變數。</span><span class="sxs-lookup"><span data-stu-id="76ac8-124">Environment variables using the [Environment Variables configuration provider](configuration-providers.md#environment-variable-configuration-provider).</span></span>
1. <span data-ttu-id="76ac8-125">使用 [命令列設定提供者](configuration-providers.md#command-line-configuration-provider)的命令列引數。</span><span class="sxs-lookup"><span data-stu-id="76ac8-125">Command-line arguments using the [Command-line configuration provider](configuration-providers.md#command-line-configuration-provider).</span></span>

<span data-ttu-id="76ac8-126">稍後新增的設定提供者會覆寫先前的金鑰設定。</span><span class="sxs-lookup"><span data-stu-id="76ac8-126">Configuration providers that are added later override previous key settings.</span></span> <span data-ttu-id="76ac8-127">例如，如果在 `SomeKey` 和環境的 *appsettings.js* 中設定，則會使用環境值。</span><span class="sxs-lookup"><span data-stu-id="76ac8-127">For example, if `SomeKey` is set in both *appsettings.json* and the environment, the environment value is used.</span></span> <span data-ttu-id="76ac8-128">使用預設的設定提供者， [命令列設定提供者](configuration-providers.md#command-line-configuration-provider) 會覆寫所有其他提供者。</span><span class="sxs-lookup"><span data-stu-id="76ac8-128">Using the default configuration providers, the [Command-line configuration provider](configuration-providers.md#command-line-configuration-provider) overrides all other providers.</span></span>

### <a name="binding"></a><span data-ttu-id="76ac8-129">繫結</span><span class="sxs-lookup"><span data-stu-id="76ac8-129">Binding</span></span>

<span data-ttu-id="76ac8-130">在 .NET 中設定的主要優點之一，就是能夠將設定值系結至 .NET 物件的實例。</span><span class="sxs-lookup"><span data-stu-id="76ac8-130">One of the key advantages to configuration in .NET is the ability to bind configuration values to instances of .NET objects.</span></span> <span data-ttu-id="76ac8-131">例如，JSON 設定提供者可以用來將檔案 \* 上的appsettings.js\* 對應至 .net 物件，並與相依性插入一起使用。</span><span class="sxs-lookup"><span data-stu-id="76ac8-131">For example, the JSON configuration provider can be used to map *appsettings.json* files to .NET objects and is used with dependency injection.</span></span> <span data-ttu-id="76ac8-132">這會啟用選項模式，選項模式會使用類別來提供相關設定群組的強型別存取。</span><span class="sxs-lookup"><span data-stu-id="76ac8-132">This enables the options pattern, the options pattern uses classes to provide strongly typed access to groups of related settings.</span></span>

## <a name="configuration-providers"></a><span data-ttu-id="76ac8-133">設定提供者</span><span class="sxs-lookup"><span data-stu-id="76ac8-133">Configuration providers</span></span>

<span data-ttu-id="76ac8-134">下表顯示 .NET Core 應用程式可用的設定提供者。</span><span class="sxs-lookup"><span data-stu-id="76ac8-134">The following table shows the configuration providers available to .NET Core apps.</span></span>

| <span data-ttu-id="76ac8-135">提供者</span><span class="sxs-lookup"><span data-stu-id="76ac8-135">Provider</span></span>                                                                                                               | <span data-ttu-id="76ac8-136">從提供設定</span><span class="sxs-lookup"><span data-stu-id="76ac8-136">Provides configuration from</span></span>        |
|------------------------------------------------------------------------------------------------------------------------|------------------------------------|
| [<span data-ttu-id="76ac8-137">Azure App 設定提供者</span><span class="sxs-lookup"><span data-stu-id="76ac8-137">Azure App configuration provider</span></span>](/azure/azure-app-configuration/quickstart-aspnet-core-app)                          | <span data-ttu-id="76ac8-138">Azure 應用程式組態</span><span class="sxs-lookup"><span data-stu-id="76ac8-138">Azure App Configuration</span></span>            |
| [<span data-ttu-id="76ac8-139">Azure Key Vault 設定提供者</span><span class="sxs-lookup"><span data-stu-id="76ac8-139">Azure Key Vault configuration provider</span></span>](/azure/key-vault/general/tutorial-net-virtual-machine)                        | <span data-ttu-id="76ac8-140">Azure 金鑰保存庫</span><span class="sxs-lookup"><span data-stu-id="76ac8-140">Azure Key Vault</span></span>                    |
| [<span data-ttu-id="76ac8-141">命令列設定提供者</span><span class="sxs-lookup"><span data-stu-id="76ac8-141">Command-line configuration provider</span></span>](configuration-providers.md#command-line-configuration-provider)                  | <span data-ttu-id="76ac8-142">命令列參數</span><span class="sxs-lookup"><span data-stu-id="76ac8-142">Command-line parameters</span></span>            |
| [<span data-ttu-id="76ac8-143">自訂設定提供者</span><span class="sxs-lookup"><span data-stu-id="76ac8-143">Custom configuration provider</span></span>](custom-configuration-provider.md)                                                      | <span data-ttu-id="76ac8-144">自訂來源</span><span class="sxs-lookup"><span data-stu-id="76ac8-144">Custom source</span></span>                      |
| [<span data-ttu-id="76ac8-145">環境變數設定提供者</span><span class="sxs-lookup"><span data-stu-id="76ac8-145">Environment Variables configuration provider</span></span>](configuration-providers.md#environment-variable-configuration-provider) | <span data-ttu-id="76ac8-146">環境變數</span><span class="sxs-lookup"><span data-stu-id="76ac8-146">Environment variables</span></span>              |
| [<span data-ttu-id="76ac8-147">檔案設定提供者</span><span class="sxs-lookup"><span data-stu-id="76ac8-147">File configuration provider</span></span>](configuration-providers.md#file-configuration-provider)                                  | <span data-ttu-id="76ac8-148">JSON、XML 和 INI 檔案</span><span class="sxs-lookup"><span data-stu-id="76ac8-148">JSON, XML, and INI files</span></span>           |
| [<span data-ttu-id="76ac8-149">每個檔案的金鑰配置提供者</span><span class="sxs-lookup"><span data-stu-id="76ac8-149">Key-per-file configuration provider</span></span>](configuration-providers.md#key-per-file-configuration-provider)                  | <span data-ttu-id="76ac8-150">目錄檔案</span><span class="sxs-lookup"><span data-stu-id="76ac8-150">Directory files</span></span>                    |
| [<span data-ttu-id="76ac8-151">記憶體設定提供者</span><span class="sxs-lookup"><span data-stu-id="76ac8-151">Memory configuration provider</span></span>](configuration-providers.md#memory-configuration-provider)                              | <span data-ttu-id="76ac8-152">記憶體內集合</span><span class="sxs-lookup"><span data-stu-id="76ac8-152">In-memory collections</span></span>              |
| [<span data-ttu-id="76ac8-153"> (秘密管理員) 的應用程式秘密 </span><span class="sxs-lookup"><span data-stu-id="76ac8-153">App secrets (Secret Manager)</span></span>](/aspnet/core/security/app-secrets)                                                      | <span data-ttu-id="76ac8-154">使用者設定檔目錄中的檔案</span><span class="sxs-lookup"><span data-stu-id="76ac8-154">File in the user profile directory</span></span> |

<span data-ttu-id="76ac8-155">如需各種設定提供者的詳細資訊，請參閱 [.net 中的設定提供者](configuration-providers.md)。</span><span class="sxs-lookup"><span data-stu-id="76ac8-155">For more information on various configuration providers, see [Configuration providers in .NET](configuration-providers.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="76ac8-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76ac8-156">See also</span></span>

- [<span data-ttu-id="76ac8-157">.NET 中的設定提供者</span><span class="sxs-lookup"><span data-stu-id="76ac8-157">Configuration providers in .NET</span></span>](configuration-providers.md)
- [<span data-ttu-id="76ac8-158">執行自訂設定提供者</span><span class="sxs-lookup"><span data-stu-id="76ac8-158">Implement a custom configuration provider</span></span>](custom-configuration-provider.md)
