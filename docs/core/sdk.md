---
title: .NET SDK 總覽
description: 瞭解 .NET SDK，這是用來建立 .NET 專案的一組程式庫和工具。
ms.date: 07/31/2019
ms.technology: dotnet-cli
ms.openlocfilehash: 5236d4abec5dcbf950059dd906958158cfb592fe
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216137"
---
# <a name="net-sdk-overview"></a><span data-ttu-id="82dec-103">.NET SDK 總覽</span><span class="sxs-lookup"><span data-stu-id="82dec-103">.NET SDK overview</span></span>

<span data-ttu-id="82dec-104">.NET SDK 是一組程式庫和工具，可讓開發人員建立 .NET 應用程式和程式庫。</span><span class="sxs-lookup"><span data-stu-id="82dec-104">The .NET SDK is a set of libraries and tools that allow developers to create .NET applications and libraries.</span></span> <span data-ttu-id="82dec-105">其中包含用來建置並執行應用程式的下列元件：</span><span class="sxs-lookup"><span data-stu-id="82dec-105">It contains the following components that are used to build and run applications:</span></span>

- <span data-ttu-id="82dec-106">.NET CLI。</span><span class="sxs-lookup"><span data-stu-id="82dec-106">The .NET CLI.</span></span>
- <span data-ttu-id="82dec-107">.NET 程式庫和執行時間。</span><span class="sxs-lookup"><span data-stu-id="82dec-107">.NET libraries and runtime.</span></span>
- <span data-ttu-id="82dec-108">`dotnet`[驅動程式](tools/index.md#driver)。</span><span class="sxs-lookup"><span data-stu-id="82dec-108">The `dotnet` [driver](tools/index.md#driver).</span></span>

## <a name="acquiring-the-net-sdk"></a><span data-ttu-id="82dec-109">取得 .NET SDK</span><span class="sxs-lookup"><span data-stu-id="82dec-109">Acquiring the .NET SDK</span></span>

<span data-ttu-id="82dec-110">使用任何工具時，第一件事都是要取得適合電腦的工具。</span><span class="sxs-lookup"><span data-stu-id="82dec-110">As with any tooling, the first thing is to get the tools to your machine.</span></span> <span data-ttu-id="82dec-111">視您的案例而定，您可以使用下列方法之一安裝 SDK：</span><span class="sxs-lookup"><span data-stu-id="82dec-111">Depending on your scenario, you can install the SDK using one of the following methods:</span></span>

- <span data-ttu-id="82dec-112">使用原生的安裝程式。</span><span class="sxs-lookup"><span data-stu-id="82dec-112">Use the native installers.</span></span>
- <span data-ttu-id="82dec-113">使用安裝 Shell 指令碼。</span><span class="sxs-lookup"><span data-stu-id="82dec-113">Use the installation shell script.</span></span>

<span data-ttu-id="82dec-114">原生安裝程式主要是為了開發人員電腦而設計。</span><span class="sxs-lookup"><span data-stu-id="82dec-114">The native installers are primarily meant for developer's machines.</span></span> <span data-ttu-id="82dec-115">SDK 是使用每個支援平台的原生安裝機制所散發，例如 Ubuntu 的 DEB 套件或 Windows 的 MSI 套件組合。</span><span class="sxs-lookup"><span data-stu-id="82dec-115">The SDK is distributed using each supported platform's native install mechanism, such as DEB packages on Ubuntu or MSI bundles on Windows.</span></span> <span data-ttu-id="82dec-116">這些安裝程式會視需要安裝並設定環境，以讓使用者在安裝後可立即使用 SDK。</span><span class="sxs-lookup"><span data-stu-id="82dec-116">These installers install and set up the environment as needed for the user to use the SDK immediately after the install.</span></span> <span data-ttu-id="82dec-117">不過，它們也需要電腦的系統管理權限。</span><span class="sxs-lookup"><span data-stu-id="82dec-117">However, they also require administrative privileges on the machine.</span></span> <span data-ttu-id="82dec-118">您可以在 [.NET 下載](https://dotnet.microsoft.com/download)頁面上找到要安裝的 SDK。</span><span class="sxs-lookup"><span data-stu-id="82dec-118">You can find the SDK to install on the [.NET downloads](https://dotnet.microsoft.com/download) page.</span></span>

<span data-ttu-id="82dec-119">另一方面，安裝指令碼不需要系統管理權限。</span><span class="sxs-lookup"><span data-stu-id="82dec-119">Install scripts, on the other hand, don't require administrative privileges.</span></span> <span data-ttu-id="82dec-120">不過，它們也不會在電腦上安裝任何必要條件；您需要手動安裝所有必要條件。</span><span class="sxs-lookup"><span data-stu-id="82dec-120">However, they also don't install any prerequisites on the machine; you need to install all of the prerequisites manually.</span></span> <span data-ttu-id="82dec-121">指令碼大部分用於設定組建伺服器，或您想要安裝工具但沒有系統管理權限時 (請確實注意上述先決條件警告)。</span><span class="sxs-lookup"><span data-stu-id="82dec-121">The scripts are meant mostly for setting up build servers or when you wish to install the tools without admin privileges (do note the prerequisites caveat above).</span></span> <span data-ttu-id="82dec-122">您可在[安裝指令碼參考](tools/dotnet-install-script.md)一文中取得需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="82dec-122">You can find more information in the [install script reference](tools/dotnet-install-script.md) article.</span></span> <span data-ttu-id="82dec-123">如果您想瞭解如何在您的 CI 組建伺服器上設定 SDK，請參閱 [使用 .NET SDK 和持續整合 (CI 中的工具) ](tools/using-ci-with-cli.md) 文章。</span><span class="sxs-lookup"><span data-stu-id="82dec-123">If you're interested in how to set up the SDK on your CI build server, see the [Using .NET SDK and tools in Continuous Integration (CI)](tools/using-ci-with-cli.md) article.</span></span>

<span data-ttu-id="82dec-124">根據預設，SDK 會以「並存」 (SxS) 方式安裝，這表示單一電腦上的任何指定時間都可以並存的多個版本。</span><span class="sxs-lookup"><span data-stu-id="82dec-124">By default, the SDK installs in a "side-by-side" (SxS) manner, which means multiple versions can coexist at any given time on a single machine.</span></span> <span data-ttu-id="82dec-125">當您執行 CLI 命令時，會在 [ [選取要使用的 .net 版本](versions/selection.md) ] 文章中更詳細地說明版本的選取方式。</span><span class="sxs-lookup"><span data-stu-id="82dec-125">How the version gets picked when you're running CLI commands is explained in more detail in the [Select the .NET version to use](versions/selection.md) article.</span></span>

## <a name="see-also"></a><span data-ttu-id="82dec-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82dec-126">See also</span></span>

- [<span data-ttu-id="82dec-127">.NET CLI 總覽</span><span class="sxs-lookup"><span data-stu-id="82dec-127">.NET CLI overview</span></span>](tools/index.md)
- [<span data-ttu-id="82dec-128">.NET 版本控制總覽</span><span class="sxs-lookup"><span data-stu-id="82dec-128">.NET versioning overview</span></span>](versions/index.md)
- [<span data-ttu-id="82dec-129">如何移除 .NET 執行時間和 SDK</span><span class="sxs-lookup"><span data-stu-id="82dec-129">How to remove the .NET runtime and SDK</span></span>](install/remove-runtime-sdk-versions.md)
- [<span data-ttu-id="82dec-130">選取要使用的 .NET 版本</span><span class="sxs-lookup"><span data-stu-id="82dec-130">Select the .NET version to use</span></span>](versions/selection.md)
