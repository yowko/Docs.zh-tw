---
title: ".NET Framework 4.7、4.6 和 4.5"
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
ms.custom: updateeachrelease
f1_keywords: f61f02f2-2f20-483d-8f56-a9c8f3a54986
helpviewer_keywords:
- .NET Framework, documentation
- documentation, .NET Framework
ms.assetid: f61f02f2-2f20-483d-8f56-a9c8f3a54986
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 34402e74bb0cb560d213760c38ce4b936d712eb4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="net-framework-guide"></a><span data-ttu-id="7c780-102">.NET Framework 指南</span><span class="sxs-lookup"><span data-stu-id="7c780-102">.NET Framework Guide</span></span>

> [!NOTE]
> <span data-ttu-id="7c780-103">此 .NET Framework 內容集包含 .NET Framework 4.5、4.5.1、4.5.2、4.6、4.6.1、4.6.2、4.7 和 4.7.1 版的資訊。</span><span class="sxs-lookup"><span data-stu-id="7c780-103">This .NET Framework content set includes information for .NET Framework versions 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, and 4.7.1.</span></span> <span data-ttu-id="7c780-104">若要下載 .NET Framework，請參閱[安裝 .NET Framework](../../docs/framework/install/guide-for-developers.md)。</span><span class="sxs-lookup"><span data-stu-id="7c780-104">To download the .NET Framework, see [Installing the .NET Framework](../../docs/framework/install/guide-for-developers.md).</span></span> <span data-ttu-id="7c780-105">如需 NET Framework 4.5、[!INCLUDE[net_v46](../../includes/net-v46-md.md)]、其點發行版以及 .NET Framework 4.7 和 4.7.1 版的新功能和變更清單，請參閱 [.NET Framework 的新功能](../../docs/framework/whats-new/index.md)。</span><span class="sxs-lookup"><span data-stu-id="7c780-105">For a list of new features and changes in the NET Framework 4.5, the [!INCLUDE[net_v46](../../includes/net-v46-md.md)], their point releases, and the .NET Framework 4.7 and 4.7.1, see [What's New in the .NET Framework](../../docs/framework/whats-new/index.md).</span></span> <span data-ttu-id="7c780-106">如需支援平台的清單，請參閱 [.NET Framework 系統需求](../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7c780-106">For a list of supported platforms, see [.NET Framework System Requirements](../../docs/framework/get-started/system-requirements.md).</span></span> 

<span data-ttu-id="7c780-107">.NET Framework 這套開發平台可用於建置可在網路、Windows、Windows Phone、Windows Server 及 Microsoft Azure 上使用的 App。</span><span class="sxs-lookup"><span data-stu-id="7c780-107">The .NET Framework is a development platform for building apps for web, Windows, Windows Phone, Windows Server, and Microsoft Azure.</span></span> <span data-ttu-id="7c780-108">這是由通用語言執行平台 (CLR) 和 .NET Framework 類別庫 (包括各種功能且支援許多產業標準) 所組成。</span><span class="sxs-lookup"><span data-stu-id="7c780-108">It consists of the common language runtime (CLR) and the .NET Framework class library, which includes a broad range of functionality and support for many industry standards.</span></span>

<span data-ttu-id="7c780-109">.NET Framework 提供許多服務，包括記憶體管理、類型與記憶體安全、安全性、網路及應用程式部署。</span><span class="sxs-lookup"><span data-stu-id="7c780-109">The .NET Framework provides many services, including memory management, type and memory safety, security, networking, and application deployment.</span></span> <span data-ttu-id="7c780-110">它提供了簡單好用的資料結構和 API，以抽取出較低層級的 Windows 作業系統。</span><span class="sxs-lookup"><span data-stu-id="7c780-110">It provides easy-to-use data structures and APIs that abstract the lower-level Windows operating system.</span></span> <span data-ttu-id="7c780-111">您可以使用各種程式設計語言與 .NET Framework 一起搭配使用，包括 C#、F# 及 Visual Basic。</span><span class="sxs-lookup"><span data-stu-id="7c780-111">You can use a variety of programming languages with the .NET Framework, including C#, F#, and Visual Basic.</span></span>  

<span data-ttu-id="7c780-112">如需適用於使用者和開發人員的 .NET Framework 一般簡介，請參閱[使用者入門](../../docs/framework/get-started/index.md)。</span><span class="sxs-lookup"><span data-stu-id="7c780-112">For a general introduction to the .NET Framework for both users and developers, see [Getting Started](../../docs/framework/get-started/index.md).</span></span> <span data-ttu-id="7c780-113">如需 .NET Framework 架構與重要功能的簡介，請參閱[概觀](../../docs/framework/get-started/overview.md)。</span><span class="sxs-lookup"><span data-stu-id="7c780-113">For an introduction to the architecture and key features of the .NET Framework, see the [overview](../../docs/framework/get-started/overview.md).</span></span>  

<span data-ttu-id="7c780-114">.NET Framework 可以搭配 Docker 與 [Windows 容器 (英文)](https://msdn.microsoft.com/virtualization/windowscontainers/about/about_overview) 使用。</span><span class="sxs-lookup"><span data-stu-id="7c780-114">The .NET Framework can be used with Docker and with [Windows Containers](https://msdn.microsoft.com/virtualization/windowscontainers/about/about_overview).</span></span> <span data-ttu-id="7c780-115">請參閱[使用 Docker 部署 .NET Framework 應用程式](./docker/index.md)，以了解如何在 Docker 容器中執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="7c780-115">See [Deploying .NET Framework applications with Docker](./docker/index.md) to learn how to run your applications in Docker containers.</span></span>

## <a name="installation"></a><span data-ttu-id="7c780-116">安裝</span><span class="sxs-lookup"><span data-stu-id="7c780-116">Installation</span></span>

<span data-ttu-id="7c780-117">.NET Framework 隨附於 Windows，讓您能夠執行 .NET Framework 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7c780-117">The .NET Framework comes with Windows, enabling you to run .NET Framework applications.</span></span> <span data-ttu-id="7c780-118">但您需要的 .NET framework 版本可能比 Windows 所隨附的版本更高。</span><span class="sxs-lookup"><span data-stu-id="7c780-118">You may need a later version of the .NET Framework than comes with your Windows version.</span></span> <span data-ttu-id="7c780-119">如需詳細資訊，請參閱[在 Windows 上安裝 .NET Framework](./install/index.md)。</span><span class="sxs-lookup"><span data-stu-id="7c780-119">For more information, see [Install the .NET Framework on Windows](./install/index.md).</span></span>

<span data-ttu-id="7c780-120">請參閱[修復 .NET Framework](./install/repair.md)，以了解如何在遇到 .NET Framework 安裝錯誤時修復 .NET Framework 安裝。</span><span class="sxs-lookup"><span data-stu-id="7c780-120">See [Repair the .NET Framework](./install/repair.md) to learn how to repair your .NET Framework installation if you are experiencing errors when installing the .NET Framework.</span></span>

<span data-ttu-id="7c780-121">如需下載 .NET Framework 的詳細資訊，請參閱[安裝適用於開發人員的 .NET Framework](../../docs/framework/install/guide-for-developers.md)。</span><span class="sxs-lookup"><span data-stu-id="7c780-121">For more detailed information on downloading the .NET Framework, see [Install the .NET Framework for developers](../../docs/framework/install/guide-for-developers.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7c780-122">本節內容</span><span class="sxs-lookup"><span data-stu-id="7c780-122">In This Section</span></span>

[<span data-ttu-id="7c780-123">新功能</span><span class="sxs-lookup"><span data-stu-id="7c780-123">What's New</span></span>](../../docs/framework/whats-new/index.md)  
<span data-ttu-id="7c780-124">描述最新版 .NET Framework 中重要的新功能與變更。</span><span class="sxs-lookup"><span data-stu-id="7c780-124">Describes key new features and changes in the latest versions of the .NET Framework.</span></span> <span data-ttu-id="7c780-125">包含過時類型及成員的清單，並提供從舊版 .NET Framework 移轉您的應用程式的指南。</span><span class="sxs-lookup"><span data-stu-id="7c780-125">Includes lists of obsolete types and members, and provides a guide for migrating your applications from the previous version of the .NET Framework.</span></span>  
  
[<span data-ttu-id="7c780-126">快速入門</span><span class="sxs-lookup"><span data-stu-id="7c780-126">Getting Started</span></span>](../../docs/framework/get-started/index.md)  
<span data-ttu-id="7c780-127">提供 .NET Framework 的完整概觀與其他資源的連結。</span><span class="sxs-lookup"><span data-stu-id="7c780-127">Provides a comprehensive overview of the .NET Framework and links to additional resources.</span></span>  
  
<span data-ttu-id="7c780-128">[移轉手冊](../../docs/framework/migration-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="7c780-128">[Migration Guide](../../docs/framework/migration-guide/index.md) </span></span>  
<span data-ttu-id="7c780-129">提供將應用程式移轉至新版 .NET Framework 時所需考量的資源和變更清單。</span><span class="sxs-lookup"><span data-stu-id="7c780-129">Provides resources and a list of changes you need to consider  if you're migrating your application to a new version of the .NET Framework.</span></span>  
  
[<span data-ttu-id="7c780-130">開發指南</span><span class="sxs-lookup"><span data-stu-id="7c780-130">Development Guide</span></span>](../../docs/framework/development-guide.md)  
<span data-ttu-id="7c780-131">提供應用程式開發所有主要技術領域和工作的指引，包括建立、設定、偵錯、保護及部署您的應用程式，以及有關動態程式設計、互通性、擴充性、記憶體管理和執行緒的資訊。</span><span class="sxs-lookup"><span data-stu-id="7c780-131">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>  
  
[<span data-ttu-id="7c780-132">工具</span><span class="sxs-lookup"><span data-stu-id="7c780-132">Tools</span></span>](../../docs/framework/tools/index.md)  
<span data-ttu-id="7c780-133">說明透過使用 .NET Framework 技術，可協助您開發、設定及部署應用程式的工具。</span><span class="sxs-lookup"><span data-stu-id="7c780-133">Describes the tools that help you develop, configure, and deploy applications by using .NET Framework technologies.</span></span>  
  
<span data-ttu-id="7c780-134">[.NET Framework 類別庫](/dotnet/api/?view=netframework-4.7.1) </span><span class="sxs-lookup"><span data-stu-id="7c780-134">[.NET Framework Class Library](/dotnet/api/?view=netframework-4.7.1) </span></span>  
<span data-ttu-id="7c780-135">為每個包含在 .NET Framework 命名空間的類別提供語法、程式碼範例和相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7c780-135">Supplies syntax, code examples, and related information for each class contained in the .NET Framework namespaces.</span></span>  
  
[<span data-ttu-id="7c780-136">其他類別庫和 API</span><span class="sxs-lookup"><span data-stu-id="7c780-136">Additional Class Libraries and APIs</span></span>](../../docs/framework/additional-apis/index.md)  
<span data-ttu-id="7c780-137">提供頻外 (OOB) 版本中所包含類別的文件，以及針對特定平台或 .NET Framework 實作之類別的文件。</span><span class="sxs-lookup"><span data-stu-id="7c780-137">Provides documentation for classes contained in out-of-band (OOB) releases, as well as for classes that target specific platforms or implementations of the .NET Framework.</span></span>
