---
title: .NET Core SDK 概觀
description: 了解 .NET Core SDK 相關資訊，這是用來建立 .NET Core 專案的一組程式庫和工具。
ms.date: 07/31/2019
ms.technology: dotnet-cli
ms.openlocfilehash: 0231c08f780455c4956c044815a2e80cef4d827e
ms.sourcegitcommit: 8c6426a3d2adff5fbcbe1fed0f28eda718c15351
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2019
ms.locfileid: "68733383"
---
# <a name="net-core-sdk-overview"></a><span data-ttu-id="41d09-103">.NET Core SDK 概觀</span><span class="sxs-lookup"><span data-stu-id="41d09-103">.NET Core SDK overview</span></span>

<span data-ttu-id="41d09-104">.NET Core 軟體開發套件 (SDK) 是一組程式庫和工具，可讓開發人員建立 .NET Core 應用程式和程式庫。</span><span class="sxs-lookup"><span data-stu-id="41d09-104">.NET Core Software Development Kit (SDK) is a set of libraries and tools that allow developers to create .NET Core applications and libraries.</span></span> <span data-ttu-id="41d09-105">其中包含用來建置並執行應用程式的下列元件：</span><span class="sxs-lookup"><span data-stu-id="41d09-105">It contains the following components that are used to build and run applications:</span></span>

- <span data-ttu-id="41d09-106">.NET Core CLI 工具。</span><span class="sxs-lookup"><span data-stu-id="41d09-106">The .NET Core CLI tools.</span></span>
- <span data-ttu-id="41d09-107">.NET core 程式庫和執行階段。</span><span class="sxs-lookup"><span data-stu-id="41d09-107">.NET Core libraries and runtime.</span></span>
- <span data-ttu-id="41d09-108">`dotnet` [驅動程式](tools/index.md#driver)。</span><span class="sxs-lookup"><span data-stu-id="41d09-108">The `dotnet` [driver](tools/index.md#driver).</span></span>

## <a name="acquiring-the-net-core-sdk"></a><span data-ttu-id="41d09-109">取得 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="41d09-109">Acquiring the .NET Core SDK</span></span>

<span data-ttu-id="41d09-110">擁有任何工具時，第一件事都是要將工具安裝到電腦上。</span><span class="sxs-lookup"><span data-stu-id="41d09-110">As with any tooling, the first thing is to get the tools to your machine.</span></span> <span data-ttu-id="41d09-111">視您的案例而定，您可以使用下列方法之一安裝 SDK：</span><span class="sxs-lookup"><span data-stu-id="41d09-111">Depending on your scenario, you can install the SDK using one of the following methods:</span></span>

- <span data-ttu-id="41d09-112">使用原生的安裝程式。</span><span class="sxs-lookup"><span data-stu-id="41d09-112">Use the native installers.</span></span>
- <span data-ttu-id="41d09-113">使用安裝 Shell 指令碼。</span><span class="sxs-lookup"><span data-stu-id="41d09-113">Use the installation shell script.</span></span>

<span data-ttu-id="41d09-114">原生安裝程式主要是為了開發人員電腦而設計。</span><span class="sxs-lookup"><span data-stu-id="41d09-114">The native installers are primarily meant for developer's machines.</span></span> <span data-ttu-id="41d09-115">SDK 是使用每個支援平台的原生安裝機制所散發，例如 Ubuntu 的 DEB 套件或 Windows 的 MSI 套件組合。</span><span class="sxs-lookup"><span data-stu-id="41d09-115">The SDK is distributed using each supported platform's native install mechanism, such as DEB packages on Ubuntu or MSI bundles on Windows.</span></span> <span data-ttu-id="41d09-116">這些安裝程式會視需要安裝並設定環境，以讓使用者在安裝後可立即使用 SDK。</span><span class="sxs-lookup"><span data-stu-id="41d09-116">These installers install and set up the environment as needed for the user to use the SDK immediately after the install.</span></span> <span data-ttu-id="41d09-117">不過，它們也需要電腦的系統管理權限。</span><span class="sxs-lookup"><span data-stu-id="41d09-117">However, they also require administrative privileges on the machine.</span></span> <span data-ttu-id="41d09-118">您可以在 [.NET 下載](https://dotnet.microsoft.com/download)頁面上找到要安裝的 SDK。</span><span class="sxs-lookup"><span data-stu-id="41d09-118">You can find the SDK to install on the [.NET downloads](https://dotnet.microsoft.com/download) page.</span></span>

<span data-ttu-id="41d09-119">另一方面，安裝指令碼不需要系統管理權限。</span><span class="sxs-lookup"><span data-stu-id="41d09-119">Install scripts, on the other hand, don't require administrative privileges.</span></span> <span data-ttu-id="41d09-120">不過，它們也不會在電腦上安裝任何必要條件；您需要手動安裝所有必要條件。</span><span class="sxs-lookup"><span data-stu-id="41d09-120">However, they also don't install any prerequisites on the machine; you need to install all of the prerequisites manually.</span></span> <span data-ttu-id="41d09-121">指令碼大部分用於設定組建伺服器，或您想要安裝工具但沒有系統管理權限時 (請確實注意上述先決條件警告)。</span><span class="sxs-lookup"><span data-stu-id="41d09-121">The scripts are meant mostly for setting up build servers or when you wish to install the tools without admin privileges (do note the prerequisites caveat above).</span></span> <span data-ttu-id="41d09-122">您可在[安裝指令碼參考](tools/dotnet-install-script.md)一文中取得需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="41d09-122">You can find more information in the [install script reference](tools/dotnet-install-script.md) article.</span></span> <span data-ttu-id="41d09-123">如對如何在 CI 組建伺服器上設定 SDK 有興趣，請參閱[在持續整合 (CI) 中使用 .NET Core SDK 和工具](tools/using-ci-with-cli.md)一文。</span><span class="sxs-lookup"><span data-stu-id="41d09-123">If you're interested in how to set up the SDK on your CI build server, see the [Using .NET Core SDK and tools in Continuous Integration (CI)](tools/using-ci-with-cli.md) article.</span></span>

<span data-ttu-id="41d09-124">根據預設，SDK 會以「並存」(SxS) 的形式安裝，這表示一部電腦上可以同時存在多個版本的 CLI 工具。</span><span class="sxs-lookup"><span data-stu-id="41d09-124">By default, the SDK installs in a "side-by-side" (SxS) manner, which means multiple versions of the CLI tools can coexist at any given time on a single machine.</span></span> <span data-ttu-id="41d09-125">如需了解執行 CLI 命令時如何挑選版本的詳細說明，請參閱[選取要使用的 .NET Core 版本](versions/selection.md)一文。</span><span class="sxs-lookup"><span data-stu-id="41d09-125">How the version gets picked when you're running CLI commands is explained in more detail in the [Select the .NET Core version to use](versions/selection.md) article.</span></span>

## <a name="see-also"></a><span data-ttu-id="41d09-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41d09-126">See also</span></span>

- [<span data-ttu-id="41d09-127">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="41d09-127">.NET Core CLI</span></span>](tools/index.md)
- [<span data-ttu-id="41d09-128">.NET Core 版本控制概觀</span><span class="sxs-lookup"><span data-stu-id="41d09-128">.NET Core versioning overview</span></span>](versions/index.md)
- [<span data-ttu-id="41d09-129">如何移除 .NET Core 執行階段和 SDK</span><span class="sxs-lookup"><span data-stu-id="41d09-129">How to remove the .NET Core runtime and SDK</span></span>](versions/remove-runtime-sdk-versions.md)
- [<span data-ttu-id="41d09-130">選取要使用的 .NET Core 版本</span><span class="sxs-lookup"><span data-stu-id="41d09-130">Select the .NET Core version to use</span></span>](versions/selection.md)
