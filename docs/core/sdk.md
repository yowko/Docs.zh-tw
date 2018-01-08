---
title: ".NET Core SDK 概觀"
description: "了解 .NET Core SDK 相關資訊，這是用來建立 .NET Core 專案的一組程式庫和工具。"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 26bc9822-e42b-48ec-b0d6-499dc604add7
ms.workload: dotnetcore
ms.openlocfilehash: f32f4c50f5b3fef8f38560ea3516265f7a4ac008
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="net-core-sdk-overview"></a><span data-ttu-id="81ad8-104">.NET Core SDK 概觀</span><span class="sxs-lookup"><span data-stu-id="81ad8-104">.NET Core SDK Overview</span></span> 

## <a name="introduction"></a><span data-ttu-id="81ad8-105">簡介</span><span class="sxs-lookup"><span data-stu-id="81ad8-105">Introduction</span></span>
<span data-ttu-id="81ad8-106">.NET Core 軟體開發套件 (SDK) 是一組程式庫和工具，可讓開發人員建立 .NET Core 應用程式和程式庫。</span><span class="sxs-lookup"><span data-stu-id="81ad8-106">.NET Core Software Development Kit (SDK) is a set of libraries and tools that allow developers to create .NET Core applications and libraries.</span></span> <span data-ttu-id="81ad8-107">這是開發人員最可能取得的套件。</span><span class="sxs-lookup"><span data-stu-id="81ad8-107">This is the package that developers will most likely acquire.</span></span> 

<span data-ttu-id="81ad8-108">它包含以下元件：</span><span class="sxs-lookup"><span data-stu-id="81ad8-108">It contains the following components:</span></span>

1. <span data-ttu-id="81ad8-109">用來建置應用程式的 .NET Core 命令列工具</span><span class="sxs-lookup"><span data-stu-id="81ad8-109">The .NET Core Command Line Tools that are used to build applications</span></span>
2. <span data-ttu-id="81ad8-110">可建置及執行應用程式的 .NET Core (程式庫和執行階段)</span><span class="sxs-lookup"><span data-stu-id="81ad8-110">.NET Core (libraries and runtime) that allow applications to both be built and run</span></span>
3. <span data-ttu-id="81ad8-111">執行 [CLI 命令](tools/index.md) 與應用程式的 `dotnet` 驅動程式</span><span class="sxs-lookup"><span data-stu-id="81ad8-111">The `dotnet` driver for running the [CLI commands](tools/index.md) as well as running applications</span></span>


## <a name="acquiring-the-net-core-sdk"></a><span data-ttu-id="81ad8-112">取得 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="81ad8-112">Acquiring the .NET Core SDK</span></span>
<span data-ttu-id="81ad8-113">擁有任何工具時，第一件事都是要將工具安裝到電腦上。</span><span class="sxs-lookup"><span data-stu-id="81ad8-113">As with any tooling, the first thing is to get the tools to your machine.</span></span> <span data-ttu-id="81ad8-114">您可以根據自己的案例，使用原生安裝程式來安裝 SDK，或使用安裝殼層指令碼。</span><span class="sxs-lookup"><span data-stu-id="81ad8-114">Depending on your scenario, you can either use the native installers to install the SDK or use the installation shell script.</span></span>

<span data-ttu-id="81ad8-115">原生安裝程式主要是為了開發人員電腦而設計。</span><span class="sxs-lookup"><span data-stu-id="81ad8-115">The native installers are primarily meant for developer's machines.</span></span> <span data-ttu-id="81ad8-116">SDK 是使用每個支援平台的原生安裝機制所散發 (例如 Ubuntu 上的 DEB 套件或 Windows 上的 MSI 套件組合)。</span><span class="sxs-lookup"><span data-stu-id="81ad8-116">The SDK is distributed using each supported platform's native install mechanism, for instance DEB packages on Ubuntu or MSI bundles on Windows.</span></span> <span data-ttu-id="81ad8-117">這些安裝程式會視需要安裝並設定環境，以讓使用者在安裝後可立即使用 SDK。</span><span class="sxs-lookup"><span data-stu-id="81ad8-117">These installers will install and set up the environment as needed for the user to use the SDK immediately after the install.</span></span> <span data-ttu-id="81ad8-118">不過，它們也需要電腦的系統管理權限。</span><span class="sxs-lookup"><span data-stu-id="81ad8-118">However, they also require administrative privileges on the machine.</span></span> <span data-ttu-id="81ad8-119">您可以檢視 [.NET Core installation guide](https://aka.ms/dotnetcoregs) (.NET Core 安裝指南) 上的安裝指示。</span><span class="sxs-lookup"><span data-stu-id="81ad8-119">You can view the installation instructions on the [.NET Core installation guide](https://aka.ms/dotnetcoregs).</span></span>

<span data-ttu-id="81ad8-120">另一方面來看，安裝指令碼則不需要系統管理權限。</span><span class="sxs-lookup"><span data-stu-id="81ad8-120">Install scripts, on the other hand, do not require administrative privileges.</span></span> <span data-ttu-id="81ad8-121">不過，它們也不會在電腦上安裝任何必要條件；您必須手動安裝所有必要條件。</span><span class="sxs-lookup"><span data-stu-id="81ad8-121">However, they will also not install any prerequisites on the machine; you need to install all of the prerequisites manually.</span></span> <span data-ttu-id="81ad8-122">指令碼大部分用於設定組建伺服器，或您想要安裝工具但沒有系統管理權限時 (請確實注意上述先決條件警告)。</span><span class="sxs-lookup"><span data-stu-id="81ad8-122">The scripts are meant mostly for setting up build servers or when you wish to install the tools without admin privileges (do note the prerequisites caveat above).</span></span> <span data-ttu-id="81ad8-123">如需詳細資訊，請參閱[安裝指令碼參考主題](tools/dotnet-install-script.md)。</span><span class="sxs-lookup"><span data-stu-id="81ad8-123">You can find more information on the [install script reference topic](tools/dotnet-install-script.md).</span></span> <span data-ttu-id="81ad8-124">如果您對如何在 CI 組建伺服器中設定 SDK 感興趣，可以查看 [CI 伺服器的 SDK](tools/using-ci-with-cli.md) 文件。</span><span class="sxs-lookup"><span data-stu-id="81ad8-124">If you are interested in how to set up SDK on your CI build server you can take a look at the [SDK with CI servers](tools/using-ci-with-cli.md) document.</span></span> 

<span data-ttu-id="81ad8-125">根據預設，SDK 會以並存 (SxS) 方式進行安裝。</span><span class="sxs-lookup"><span data-stu-id="81ad8-125">By default, the SDK will install in a "side-by-side" (SxS) manner.</span></span> <span data-ttu-id="81ad8-126">這表示在任何指定時間，單一電腦上可同時存在多個版本的 CLI 工具。</span><span class="sxs-lookup"><span data-stu-id="81ad8-126">This means that multiple versions of the CLI tools can coexist at any given time on a single machine.</span></span> <span data-ttu-id="81ad8-127">.NET Core 命令列工具主題的[驅動程式區段](tools/index.md#driver)中，有詳細說明如何使用正確的版本。</span><span class="sxs-lookup"><span data-stu-id="81ad8-127">How the correct version gets used is explained in more detail in the [driver section](tools/index.md#driver) of .NET Core Command Line Tools topic.</span></span>
