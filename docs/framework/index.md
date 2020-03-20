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
ms.openlocfilehash: d94d97cd1b519025ff360dc903558ea3656818d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181525"
---
# <a name="net-framework-guide"></a><span data-ttu-id="1b77a-102">.NET Framework 指南</span><span class="sxs-lookup"><span data-stu-id="1b77a-102">.NET Framework guide</span></span>

> [!NOTE]
> <span data-ttu-id="1b77a-103">此 .NET Framework 內容集包含 .NET Framework 4.5 到 4.8 版的資訊。</span><span class="sxs-lookup"><span data-stu-id="1b77a-103">This .NET Framework content set includes information for .NET Framework versions 4.5 through 4.8.</span></span> <span data-ttu-id="1b77a-104">要下載 .NET 框架，請參閱[安裝 .NET 框架](./install/guide-for-developers.md)。</span><span class="sxs-lookup"><span data-stu-id="1b77a-104">To download .NET Framework, see [Install .NET Framework](./install/guide-for-developers.md).</span></span> <span data-ttu-id="1b77a-105">有關 .NET 框架中的新功能和更改的清單，請參閱[.NET 框架中的新增功能](./whats-new/index.md)和更改。</span><span class="sxs-lookup"><span data-stu-id="1b77a-105">For a list of new features and changes in .NET Framework, see [What's New in .NET Framework](./whats-new/index.md).</span></span> <span data-ttu-id="1b77a-106">如需支援平台的清單，請參閱 [.NET Framework 系統需求](./get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1b77a-106">For a list of supported platforms, see [.NET Framework System Requirements](./get-started/system-requirements.md).</span></span> <span data-ttu-id="1b77a-107">有關 .NET 框架的舊版本的文檔，請參閱[.NET 早期版本文檔](https://docs.microsoft.com/previous-versions/dotnet/)。</span><span class="sxs-lookup"><span data-stu-id="1b77a-107">For documentation about older versions of .NET Framework, see [.NET previous versions documentation](https://docs.microsoft.com/previous-versions/dotnet/).</span></span>

<span data-ttu-id="1b77a-108">.NET 框架是一個開發平臺，用於構建 Web、Windows、Windows 伺服器和 Microsoft Azure 的應用。</span><span class="sxs-lookup"><span data-stu-id="1b77a-108">.NET Framework is a development platform for building apps for web, Windows, Windows Server, and Microsoft Azure.</span></span> <span data-ttu-id="1b77a-109">這是由通用語言執行平台 (CLR) 和 .NET Framework 類別庫 (包括各種功能且支援許多產業標準) 所組成。</span><span class="sxs-lookup"><span data-stu-id="1b77a-109">It consists of the common language runtime (CLR) and the .NET Framework class library, which includes a broad range of functionality and support for many industry standards.</span></span>

<span data-ttu-id="1b77a-110">.NET Framework 提供許多服務，包括記憶體管理、類型和記憶體安全、安全性、網路和應用程式部署。</span><span class="sxs-lookup"><span data-stu-id="1b77a-110">.NET Framework provides many services, including memory management, type and memory safety, security, networking, and application deployment.</span></span> <span data-ttu-id="1b77a-111">它提供了簡單好用的資料結構和 API，以抽取出較低層級的 Windows 作業系統。</span><span class="sxs-lookup"><span data-stu-id="1b77a-111">It provides easy-to-use data structures and APIs that abstract the lower-level Windows operating system.</span></span> <span data-ttu-id="1b77a-112">您可以將不同的程式設計語言與 .NET 框架一起使用，包括 C#、F# 和視覺化基本。</span><span class="sxs-lookup"><span data-stu-id="1b77a-112">You can use different programming languages with .NET Framework, including C#, F#, and Visual Basic.</span></span>

<span data-ttu-id="1b77a-113">有關 .NET 框架的一般介紹，請參閱[入門](./get-started/index.md)。</span><span class="sxs-lookup"><span data-stu-id="1b77a-113">For a general introduction to .NET Framework for both users and developers, see [Getting Started](./get-started/index.md).</span></span> <span data-ttu-id="1b77a-114">有關 .NET Framework 的體系結構和關鍵功能的介紹，請參閱[概述](./get-started/overview.md)。</span><span class="sxs-lookup"><span data-stu-id="1b77a-114">For an introduction to the architecture and key features of .NET Framework, see the [overview](./get-started/overview.md).</span></span>

<span data-ttu-id="1b77a-115">.NET 框架可用於 Docker 和[Windows 容器](/virtualization/windowscontainers/about/)。</span><span class="sxs-lookup"><span data-stu-id="1b77a-115">.NET Framework can be used with Docker and with [Windows Containers](/virtualization/windowscontainers/about/).</span></span>

## <a name="installation"></a><span data-ttu-id="1b77a-116">安裝</span><span class="sxs-lookup"><span data-stu-id="1b77a-116">Installation</span></span>

<span data-ttu-id="1b77a-117">.NET 框架附帶 Windows，它使您能夠運行 .NET 框架應用程式。</span><span class="sxs-lookup"><span data-stu-id="1b77a-117">.NET Framework comes with Windows, which enables you to run .NET Framework applications.</span></span> <span data-ttu-id="1b77a-118">您可能需要比 Windows 版本附帶的更高版本的 .NET 框架版本。</span><span class="sxs-lookup"><span data-stu-id="1b77a-118">You may need a later version of .NET Framework than the one that comes with your Windows version.</span></span> <span data-ttu-id="1b77a-119">有關詳細資訊，請參閱在[Windows 上安裝 .NET 框架](./install/index.md)。</span><span class="sxs-lookup"><span data-stu-id="1b77a-119">For more information, see [Install .NET Framework on Windows](./install/index.md).</span></span>

<span data-ttu-id="1b77a-120">要瞭解如何修復 .NET 框架安裝（如果您在安裝過程中遇到錯誤），請參閱修復[.NET 框架](./install/repair.md)。</span><span class="sxs-lookup"><span data-stu-id="1b77a-120">To learn how to repair your .NET Framework installation if you're experiencing errors during installation, see [Repair .NET Framework](./install/repair.md).</span></span>

<span data-ttu-id="1b77a-121">有關下載 .NET 框架的更多詳細資訊，請參閱[為開發人員安裝 .NET 框架](./install/guide-for-developers.md)。</span><span class="sxs-lookup"><span data-stu-id="1b77a-121">For more detailed information on downloading .NET Framework, see [Install the .NET Framework for developers](./install/guide-for-developers.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="1b77a-122">本節內容</span><span class="sxs-lookup"><span data-stu-id="1b77a-122">In this section</span></span>

* [<span data-ttu-id="1b77a-123">新功能</span><span class="sxs-lookup"><span data-stu-id="1b77a-123">What's New</span></span>](./whats-new/index.md)  
<span data-ttu-id="1b77a-124">描述最新版 .NET Framework 中重要的新功能與變更。</span><span class="sxs-lookup"><span data-stu-id="1b77a-124">Describes key new features and changes in the latest versions of the .NET Framework.</span></span> <span data-ttu-id="1b77a-125">包含過時類型及成員的清單，並提供從舊版 .NET Framework 移轉您的應用程式的指南。</span><span class="sxs-lookup"><span data-stu-id="1b77a-125">Includes lists of obsolete types and members, and provides a guide for migrating your applications from the previous version of the .NET Framework.</span></span>

* [<span data-ttu-id="1b77a-126">入門</span><span class="sxs-lookup"><span data-stu-id="1b77a-126">Get Started</span></span>](./get-started/index.md)  
<span data-ttu-id="1b77a-127">提供 .NET Framework 的完整概觀與其他資源的連結。</span><span class="sxs-lookup"><span data-stu-id="1b77a-127">Provides a comprehensive overview of the .NET Framework and links to additional resources.</span></span>

* [<span data-ttu-id="1b77a-128">安裝指南</span><span class="sxs-lookup"><span data-stu-id="1b77a-128">Installation Guide</span></span>](./install/index.md)  
<span data-ttu-id="1b77a-129">提供有關 .NET Framework 安裝與疑難排解的資源與指導方針。</span><span class="sxs-lookup"><span data-stu-id="1b77a-129">Provides resources and guidance about .NET Framework installation and troubleshooting.</span></span>

* [<span data-ttu-id="1b77a-130">遷移指南</span><span class="sxs-lookup"><span data-stu-id="1b77a-130">Migration Guide</span></span>](./migration-guide/index.md)  
<span data-ttu-id="1b77a-131">提供將應用程式移轉至新版 .NET Framework 時所需考量的資源與變更清單。</span><span class="sxs-lookup"><span data-stu-id="1b77a-131">Provides resources and a list of changes you need to consider if you're migrating your application to a new version of the .NET Framework.</span></span>

* [<span data-ttu-id="1b77a-132">開發指南</span><span class="sxs-lookup"><span data-stu-id="1b77a-132">Development Guide</span></span>](./development-guide.md)  
<span data-ttu-id="1b77a-133">提供應用程式開發所有主要技術領域和工作的指引，包括建立、設定、偵錯、保護及部署您的應用程式，以及有關動態程式設計、互通性、擴充性、記憶體管理和執行緒的資訊。</span><span class="sxs-lookup"><span data-stu-id="1b77a-133">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>

* [<span data-ttu-id="1b77a-134">工具</span><span class="sxs-lookup"><span data-stu-id="1b77a-134">Tools</span></span>](./tools/index.md)  
<span data-ttu-id="1b77a-135">說明透過使用 .NET Framework 技術，可協助您開發、設定及部署應用程式的工具。</span><span class="sxs-lookup"><span data-stu-id="1b77a-135">Describes the tools that help you develop, configure, and deploy applications by using .NET Framework technologies.</span></span>

* [<span data-ttu-id="1b77a-136">其他類庫和 API</span><span class="sxs-lookup"><span data-stu-id="1b77a-136">Additional class libraries and APIs</span></span>](./additional-apis/index.md)  
<span data-ttu-id="1b77a-137">提供 Microsoft 工具使用之私人 .NET Framework API 的文件。</span><span class="sxs-lookup"><span data-stu-id="1b77a-137">Provides documentation for private .NET Framework APIs used by Microsoft tools.</span></span>

## <a name="see-also"></a><span data-ttu-id="1b77a-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b77a-138">See also</span></span>

* [<span data-ttu-id="1b77a-139">.NET Framework 類別庫</span><span class="sxs-lookup"><span data-stu-id="1b77a-139">.NET Framework Class Library</span></span>](/dotnet/api/?view=netframework-4.8)
