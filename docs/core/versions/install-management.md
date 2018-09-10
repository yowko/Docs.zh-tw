---
title: 管理 .NET Core 安裝
description: 使用並存安裝策略，在您的電腦上管理多個 .NET Core SDK 和執行階段版本。
author: leecow
ms.author: wiwagn
ms.date: 08/22/2018
ms.openlocfilehash: 06c3f43e7917efb8fd31898044d8f5d920c2cada
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43485444"
---
# <a name="manage-net-core-installations"></a><span data-ttu-id="31ea8-103">管理 .NET Core 安裝</span><span class="sxs-lookup"><span data-stu-id="31ea8-103">Manage .NET Core installations</span></span>

<span data-ttu-id="31ea8-104">.NET Core 允許多個 SDK 和執行階段版本共存，因此提高建置及執行 .NET Core 應用程式時的版本相依性彈性。</span><span class="sxs-lookup"><span data-stu-id="31ea8-104">.NET Core allows multiple versions of the SDK and Runtime to exist side-by-side, enabling version dependency flexibility for both building and running .NET Core applications.</span></span> <span data-ttu-id="31ea8-105">這些安裝和自動版本向前復原行為提供寶貴的優點，但有一個明顯的缺點。</span><span class="sxs-lookup"><span data-stu-id="31ea8-105">These installation and automatic version roll-forward behaviors offer valuable benefits, but one pronounced drawback.</span></span> <span data-ttu-id="31ea8-106">安裝 .NET Core SDK 或 .NET Core 執行階段的更新之後，舊版仍會保留在磁碟上。</span><span class="sxs-lookup"><span data-stu-id="31ea8-106">As updates of the .NET Core SDK or .NET Core Runtime are installed, previous versions remain on-disk.</span></span> <span data-ttu-id="31ea8-107">隨時間下來，安裝多個版本會增加磁碟使用量。</span><span class="sxs-lookup"><span data-stu-id="31ea8-107">Multiple installed versions increase disk usage over time.</span></span> <span data-ttu-id="31ea8-108">目前已發行超過 50 個 .NET Core SDK 更新。</span><span class="sxs-lookup"><span data-stu-id="31ea8-108">More than 50 .NET Core SDK updates have been released.</span></span> <span data-ttu-id="31ea8-109">您的系統上可能安裝了許多 SDK 和執行階段版本，這些可以加以移除。</span><span class="sxs-lookup"><span data-stu-id="31ea8-109">There may be many versions of the SDK and Runtime installed on your system that could be removed.</span></span>

## <a name="safe-to-remove"></a><span data-ttu-id="31ea8-110">移除是否安全？</span><span class="sxs-lookup"><span data-stu-id="31ea8-110">Safe to remove?</span></span>

<span data-ttu-id="31ea8-111">[.NET Core 版本選取](selection.md)行為及不同更新之間的 .NET Core 執行階段相容性，可讓您安全地移除舊版。</span><span class="sxs-lookup"><span data-stu-id="31ea8-111">The [.NET Core version selection](selection.md) behaviors and the runtime compatibility of .NET Core across updates enables safe removal of previous versions.</span></span> <span data-ttu-id="31ea8-112">.NET Core 執行階段更新在主要版本「範圍」內 (例如 1.x 和 2.x) 是相容的。</span><span class="sxs-lookup"><span data-stu-id="31ea8-112">.NET Core runtime updates are compatible within a major version 'band' such as 1.x and 2.x.</span></span> <span data-ttu-id="31ea8-113">此外，較新版本的 .NET Core SDK 通常能夠繼續以相容的方式，來建置以舊版執行階段為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="31ea8-113">Additionally, newer releases of the .NET Core SDK generally maintain the ability to build applications that target previous versions of the runtime in a compatible manner.</span></span>

<span data-ttu-id="31ea8-114">一般而言，您只需要最新的 SDK，以及您應用程式所需之執行階段的最新修補版本。</span><span class="sxs-lookup"><span data-stu-id="31ea8-114">In general, you only need the latest SDK and latest patch version of the runtimes required for your application.</span></span> <span data-ttu-id="31ea8-115">保留舊版 SDK 或執行階段版本的執行個體包括維護以 project.json 為基礎的應用程式。</span><span class="sxs-lookup"><span data-stu-id="31ea8-115">Instances where retaining older SDK or Runtime versions include maintaining project.json-based applications.</span></span>  <span data-ttu-id="31ea8-116">除非您的應用程式有特定理由需要舊版 SDK 或執行階段，否則您可以安全地移除舊版。</span><span class="sxs-lookup"><span data-stu-id="31ea8-116">Unless your application has specific reasons for earlier SDKs or runtimes, you may safely remove older versions.</span></span>

<span data-ttu-id="31ea8-117">移除 .NET Core 的方法會依平台而異，而且在 .NET Core 版本之間已有些變更。</span><span class="sxs-lookup"><span data-stu-id="31ea8-117">The methods for removing .NET Core vary from platform to platform and have changed somewhat across .NET Core versions.</span></span> <span data-ttu-id="31ea8-118">如需移除不再需要之 .NET Core 版本的詳細資訊，請參閱 [.NET Core 文件](../index.md)中的[如何移除 .NET Core 執行階段和 SDK](remove-runtime-sdk-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="31ea8-118">For details on removing versions of .NET Core that are no longer needed, see ['How to remove the .NET Core Runtime and SDK'](remove-runtime-sdk-versions.md) in the [.NET Core documentation](../index.md).</span></span>
