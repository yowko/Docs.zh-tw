---
title: .NET Framework 文件
ms.date: 04/02/2019
ms.custom: updateeachrelease
f1_keywords:
- f61f02f2-2f20-483d-8f56-a9c8f3a54986
helpviewer_keywords:
- .NET Framework, documentation
- documentation, .NET Framework
ms.assetid: f61f02f2-2f20-483d-8f56-a9c8f3a54986
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5a86b3abf821a37944a0e478d0bc8f1bea31ccb
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699046"
---
# <a name="net-framework-guide"></a><span data-ttu-id="27c9f-102">.NET Framework 指南</span><span class="sxs-lookup"><span data-stu-id="27c9f-102">.NET Framework Guide</span></span>

> [!NOTE]
> <span data-ttu-id="27c9f-103">此 .NET Framework 內容集包含 .NET Framework 4.5 到 4.8 版的資訊。</span><span class="sxs-lookup"><span data-stu-id="27c9f-103">This .NET Framework content set includes information for .NET Framework versions 4.5 through 4.8.</span></span> <span data-ttu-id="27c9f-104">若要下載 .NET Framework，請參閱[安裝 .NET Framework](./install/guide-for-developers.md)。</span><span class="sxs-lookup"><span data-stu-id="27c9f-104">To download the .NET Framework, see [Installing the .NET Framework](./install/guide-for-developers.md).</span></span> <span data-ttu-id="27c9f-105">如需 .NET Framework 的新功能和變更清單，請參閱 [.NET Framework 中的新功能](./whats-new/index.md)。</span><span class="sxs-lookup"><span data-stu-id="27c9f-105">For a list of new features and changes in the NET Framework, see [What's New in the .NET Framework](./whats-new/index.md).</span></span> <span data-ttu-id="27c9f-106">如需支援平台的清單，請參閱 [.NET Framework 系統需求](./get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="27c9f-106">For a list of supported platforms, see [.NET Framework System Requirements](./get-started/system-requirements.md).</span></span> <span data-ttu-id="27c9f-107">如需舊版 .NET Framework 的文件，請參閱 [.NET 舊版文件](https://docs.microsoft.com/previous-versions/dotnet/)。</span><span class="sxs-lookup"><span data-stu-id="27c9f-107">For documentation about older versions of the .NET Framework, see [.NET previous versions documentation](https://docs.microsoft.com/previous-versions/dotnet/).</span></span>

<span data-ttu-id="27c9f-108">.NET Framework 這套開發平台可用於建置可在網路、Windows、Windows Phone、Windows Server 及 Microsoft Azure 上使用的 App。</span><span class="sxs-lookup"><span data-stu-id="27c9f-108">The .NET Framework is a development platform for building apps for web, Windows, Windows Phone, Windows Server, and Microsoft Azure.</span></span> <span data-ttu-id="27c9f-109">這是由通用語言執行平台 (CLR) 和 .NET Framework 類別庫 (包括各種功能且支援許多產業標準) 所組成。</span><span class="sxs-lookup"><span data-stu-id="27c9f-109">It consists of the common language runtime (CLR) and the .NET Framework class library, which includes a broad range of functionality and support for many industry standards.</span></span>

<span data-ttu-id="27c9f-110">.NET Framework 提供許多服務，包括記憶體管理、類型與記憶體安全、安全性、網路及應用程式部署。</span><span class="sxs-lookup"><span data-stu-id="27c9f-110">The .NET Framework provides many services, including memory management, type and memory safety, security, networking, and application deployment.</span></span> <span data-ttu-id="27c9f-111">它提供了簡單好用的資料結構和 API，以抽取出較低層級的 Windows 作業系統。</span><span class="sxs-lookup"><span data-stu-id="27c9f-111">It provides easy-to-use data structures and APIs that abstract the lower-level Windows operating system.</span></span> <span data-ttu-id="27c9f-112">您可以搭配 .NET Framework 使用不同的程式設計語言，包括 C#、F# 與 Visual Basic。</span><span class="sxs-lookup"><span data-stu-id="27c9f-112">You can use different programming languages with the .NET Framework, including C#, F#, and Visual Basic.</span></span>

<span data-ttu-id="27c9f-113">如需適用於使用者和開發人員的 .NET Framework 一般簡介，請參閱[使用者入門](./get-started/index.md)。</span><span class="sxs-lookup"><span data-stu-id="27c9f-113">For a general introduction to the .NET Framework for both users and developers, see [Getting Started](./get-started/index.md).</span></span> <span data-ttu-id="27c9f-114">如需 .NET Framework 架構與重要功能的簡介，請參閱[概觀](./get-started/overview.md)。</span><span class="sxs-lookup"><span data-stu-id="27c9f-114">For an introduction to the architecture and key features of the .NET Framework, see the [overview](./get-started/overview.md).</span></span>

<span data-ttu-id="27c9f-115">.NET Framework 可以搭配 Docker 與 [Windows 容器 (英文)](/virtualization/windowscontainers/about/) 使用。</span><span class="sxs-lookup"><span data-stu-id="27c9f-115">The .NET Framework can be used with Docker and with [Windows Containers](/virtualization/windowscontainers/about/).</span></span>

## <a name="installation"></a><span data-ttu-id="27c9f-116">安裝</span><span class="sxs-lookup"><span data-stu-id="27c9f-116">Installation</span></span>

<span data-ttu-id="27c9f-117">.NET Framework 隨附於 Windows，讓您能夠執行 .NET Framework 應用程式。</span><span class="sxs-lookup"><span data-stu-id="27c9f-117">The .NET Framework comes with Windows, enabling you to run .NET Framework applications.</span></span> <span data-ttu-id="27c9f-118">但您需要的 .NET Framework 版本可能比 Windows 所隨附的版本更高。</span><span class="sxs-lookup"><span data-stu-id="27c9f-118">You may need a later version of the .NET Framework than the one that comes with your Windows version.</span></span> <span data-ttu-id="27c9f-119">如需詳細資訊，請參閱[在 Windows 上安裝 .NET Framework](./install/index.md)。</span><span class="sxs-lookup"><span data-stu-id="27c9f-119">For more information, see [Install the .NET Framework on Windows](./install/index.md).</span></span>

<span data-ttu-id="27c9f-120">請參閱[修復 .NET Framework](./install/repair.md)，以了解如何在遇到 .NET Framework 安裝錯誤時修復 .NET Framework 安裝。</span><span class="sxs-lookup"><span data-stu-id="27c9f-120">See [Repair the .NET Framework](./install/repair.md) to learn how to repair your .NET Framework installation if you're experiencing errors when installing the .NET Framework.</span></span>

<span data-ttu-id="27c9f-121">如需下載 .NET Framework 的詳細資訊，請參閱[安裝適用於開發人員的 .NET Framework](./install/guide-for-developers.md)。</span><span class="sxs-lookup"><span data-stu-id="27c9f-121">For more detailed information on downloading the .NET Framework, see [Install the .NET Framework for developers](./install/guide-for-developers.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="27c9f-122">本節內容</span><span class="sxs-lookup"><span data-stu-id="27c9f-122">In this section</span></span>

* [<span data-ttu-id="27c9f-123">新功能</span><span class="sxs-lookup"><span data-stu-id="27c9f-123">What's New</span></span>](./whats-new/index.md)  
<span data-ttu-id="27c9f-124">描述最新版 .NET Framework 中重要的新功能與變更。</span><span class="sxs-lookup"><span data-stu-id="27c9f-124">Describes key new features and changes in the latest versions of the .NET Framework.</span></span> <span data-ttu-id="27c9f-125">包含過時類型及成員的清單，並提供從舊版 .NET Framework 移轉您的應用程式的指南。</span><span class="sxs-lookup"><span data-stu-id="27c9f-125">Includes lists of obsolete types and members, and provides a guide for migrating your applications from the previous version of the .NET Framework.</span></span>

* [<span data-ttu-id="27c9f-126">開始使用</span><span class="sxs-lookup"><span data-stu-id="27c9f-126">Get Started</span></span>](./get-started/index.md)  
<span data-ttu-id="27c9f-127">提供 .NET Framework 的完整概觀與其他資源的連結。</span><span class="sxs-lookup"><span data-stu-id="27c9f-127">Provides a comprehensive overview of the .NET Framework and links to additional resources.</span></span>

* [<span data-ttu-id="27c9f-128">安裝指南</span><span class="sxs-lookup"><span data-stu-id="27c9f-128">Installation Guide</span></span>](./install/index.md)  
<span data-ttu-id="27c9f-129">提供有關 .NET Framework 安裝與疑難排解的資源與指導方針。</span><span class="sxs-lookup"><span data-stu-id="27c9f-129">Provides resources and guidance about .NET Framework installation and troubleshooting.</span></span>

* [<span data-ttu-id="27c9f-130">移轉手冊</span><span class="sxs-lookup"><span data-stu-id="27c9f-130">Migration Guide</span></span>](./migration-guide/index.md)  
<span data-ttu-id="27c9f-131">提供將應用程式移轉至新版 .NET Framework 時所需考量的資源與變更清單。</span><span class="sxs-lookup"><span data-stu-id="27c9f-131">Provides resources and a list of changes you need to consider if you're migrating your application to a new version of the .NET Framework.</span></span>

* [<span data-ttu-id="27c9f-132">開發指南</span><span class="sxs-lookup"><span data-stu-id="27c9f-132">Development Guide</span></span>](./development-guide.md)  
<span data-ttu-id="27c9f-133">提供應用程式開發所有主要技術領域和工作的指引，包括建立、設定、偵錯、保護及部署您的應用程式，以及有關動態程式設計、互通性、擴充性、記憶體管理和執行緒的資訊。</span><span class="sxs-lookup"><span data-stu-id="27c9f-133">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>

* [<span data-ttu-id="27c9f-134">工具</span><span class="sxs-lookup"><span data-stu-id="27c9f-134">Tools</span></span>](./tools/index.md)  
<span data-ttu-id="27c9f-135">說明透過使用 .NET Framework 技術，可協助您開發、設定及部署應用程式的工具。</span><span class="sxs-lookup"><span data-stu-id="27c9f-135">Describes the tools that help you develop, configure, and deploy applications by using .NET Framework technologies.</span></span>

* [<span data-ttu-id="27c9f-136">其他類別庫和 API</span><span class="sxs-lookup"><span data-stu-id="27c9f-136">Additional class libraries and APIs</span></span>](./additional-apis/index.md)  
<span data-ttu-id="27c9f-137">提供 Microsoft 工具使用之私人 .NET Framework API 的文件。</span><span class="sxs-lookup"><span data-stu-id="27c9f-137">Provides documentation for private .NET Framework APIs used by Microsoft tools.</span></span>

## <a name="see-also"></a><span data-ttu-id="27c9f-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27c9f-138">See also</span></span>

- [<span data-ttu-id="27c9f-139">.NET Framework 類別庫</span><span class="sxs-lookup"><span data-stu-id="27c9f-139">.NET Framework Class Library</span></span>](/dotnet/api/?view=netframework-4.8)
