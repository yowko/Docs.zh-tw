---
title: .NET Framework 開發指南
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework, development guide
ms.assetid: 26e3d285-24c3-435c-a797-9fe5affb8525
ms.openlocfilehash: 0500e11d2897cfa7392cc8280a0b69c5e2fc515f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79181625"
---
# <a name="net-framework-development-guide"></a><span data-ttu-id="4c45d-102">.NET Framework 開發指南</span><span class="sxs-lookup"><span data-stu-id="4c45d-102">.NET Framework Development Guide</span></span>
<span data-ttu-id="4c45d-103">本節說明如何建立、設定、偵錯、保護和部署 .NET Framework 應用程式。</span><span class="sxs-lookup"><span data-stu-id="4c45d-103">This section explains how to create, configure, debug, secure, and deploy your .NET Framework apps.</span></span> <span data-ttu-id="4c45d-104">本節也提供有關技術領域的資訊，例如動態程式設計、互通性、擴充性、記憶體管理和執行緒。</span><span class="sxs-lookup"><span data-stu-id="4c45d-104">The section also provides information about technology areas such as dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4c45d-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="4c45d-105">In This Section</span></span>  
 [<span data-ttu-id="4c45d-106">應用程式基本概念</span><span class="sxs-lookup"><span data-stu-id="4c45d-106">Application Essentials</span></span>](../standard/application-essentials.md)  
 <span data-ttu-id="4c45d-107">提供基本應用程式開發工作的相關資訊，例如應用程式定義域和組件的程式設計、使用屬性、格式設定和分析基底類型、使用集合、處理事件和例外狀況、使用檔案和資料流，以及使用泛型。</span><span class="sxs-lookup"><span data-stu-id="4c45d-107">Provides information about basic app development tasks, such as programming with app domains and assemblies, using attributes, formatting and parsing base types, using collections, handling events and exceptions, using files and data streams, and using generics.</span></span>  
  
 [<span data-ttu-id="4c45d-108">資料和建模</span><span class="sxs-lookup"><span data-stu-id="4c45d-108">Data and Modeling</span></span>](./data/index.md)  
 <span data-ttu-id="4c45d-109">提供如何使用 ADO.NET、Language Integrated Query (LINQ)、WCF 資料服務和 XML 來存取資料的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4c45d-109">Provides information about how to access data using ADO.NET, Language Integrated Query (LINQ), WCF Data Services, and XML.</span></span>  
  
 [<span data-ttu-id="4c45d-110">用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="4c45d-110">Client Applications</span></span>](develop-client-apps.md)  
 <span data-ttu-id="4c45d-111">說明如何使用 Windows Presentation Foundation (WPF) 或 Windows Form 建立 Windows 架構應用程式。</span><span class="sxs-lookup"><span data-stu-id="4c45d-111">Explains how to create Windows-based apps by using Windows Presentation Foundation (WPF) or Windows Forms.</span></span>  
  
 [<span data-ttu-id="4c45d-112">使用 ASP.NET 的 Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="4c45d-112">Web Applications with ASP.NET</span></span>](develop-web-apps-with-aspnet.md)  
 <span data-ttu-id="4c45d-113">提供有關使用 ASP.NET，以最少程式碼建置企業級 Web 應用程式之資訊的連結。</span><span class="sxs-lookup"><span data-stu-id="4c45d-113">Provides links to information about using ASP.NET to build enterprise-class web apps with a minimum of coding.</span></span>  
  
 [<span data-ttu-id="4c45d-114">具有 WCF 的服務導向應用程式</span><span class="sxs-lookup"><span data-stu-id="4c45d-114">Service-Oriented Applications with WCF</span></span>](./wcf/index.md)  
 <span data-ttu-id="4c45d-115">說明如何使用 Windows Communication Foundation (WCF) 建立安全、可靠的服務導向應用程式。</span><span class="sxs-lookup"><span data-stu-id="4c45d-115">Describes how to use Windows Communication Foundation (WCF) to build service-oriented apps that are secure and reliable.</span></span>  
  
 <span data-ttu-id="4c45d-116">[使用 Windows 工作流基礎構建工作流](windows-workflow-foundation/index.md)提供有關使用 Windows 工作流基礎 （WF） 的程式設計模型、示例和工具的資訊。</span><span class="sxs-lookup"><span data-stu-id="4c45d-116">[Building workflows with Windows Workflow Foundation](windows-workflow-foundation/index.md) Provides information about the programming model, samples, and tools for using Windows Workflow Foundation (WF).</span></span>  

 [<span data-ttu-id="4c45d-117">Windows 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="4c45d-117">Windows Service Applications</span></span>](./windows-services/index.md)  
 <span data-ttu-id="4c45d-118">說明如何使用 Visual Studio 及 .NET Framework 建立要安裝為服務的應用程式，以及啟動、停止及控制其行為。</span><span class="sxs-lookup"><span data-stu-id="4c45d-118">Explains how you can use Visual Studio and the .NET Framework to create an app that is installed as a service, and start, stop, and otherwise control its behavior.</span></span>  
  
 [<span data-ttu-id="4c45d-119">.NET 中的平行處理、並行和非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="4c45d-119">Parallel Processing, Concurrency, and Async Programming in .NET</span></span>](../standard/parallel-processing-and-concurrency.md)  
 <span data-ttu-id="4c45d-120">提供有關 Managed 執行緒、平行程式設計和非同步程式設計模式的資訊。</span><span class="sxs-lookup"><span data-stu-id="4c45d-120">Provides information about managed threading, parallel programming, and asynchronous programming design patterns.</span></span>  
  
 [<span data-ttu-id="4c45d-121">.NET 框架中的網路程式設計</span><span class="sxs-lookup"><span data-stu-id="4c45d-121">Network Programming in the .NET Framework</span></span>](./network-programming/index.md)  
 <span data-ttu-id="4c45d-122">說明可以讓您迅速方便地整合到您應用程式之有層次、可擴充及受管理的網際網路服務實作。</span><span class="sxs-lookup"><span data-stu-id="4c45d-122">Describes the layered, extensible, and managed implementation of Internet services that you can quickly and easily integrate into your apps.</span></span>  
  
 <span data-ttu-id="4c45d-123">[配置 .NET 框架應用](configure-apps/index.md)說明如何使用設定檔更改設置，而無需重新編譯 .NET Framework 應用。</span><span class="sxs-lookup"><span data-stu-id="4c45d-123">[Configuring .NET Framework Apps](configure-apps/index.md) Explains how you can use configuration files to change settings without having to recompile your .NET Framework apps.</span></span>  
  
 [<span data-ttu-id="4c45d-124">使用 .NET Native 編譯應用程式</span><span class="sxs-lookup"><span data-stu-id="4c45d-124">Compiling Apps with .NET Native</span></span>](./net-native/index.md)  
 <span data-ttu-id="4c45d-125">說明如何使用 .NET Native 預先編譯技術，建置及部署「Windows 市集」的應用程式。</span><span class="sxs-lookup"><span data-stu-id="4c45d-125">Explains how you can use the .NET Native precompilation technology to build and deploy Windows Store apps.</span></span> <span data-ttu-id="4c45d-126">.NET Native 會編譯以受控程式碼 (C#) 所撰寫，並以 .NET Framework 做為機器碼的應用程式。</span><span class="sxs-lookup"><span data-stu-id="4c45d-126">.NET Native compiles apps that are written in managed code (C#) and that target the .NET Framework to native code.</span></span>  
  
 [<span data-ttu-id="4c45d-127">安全性</span><span class="sxs-lookup"><span data-stu-id="4c45d-127">Security</span></span>](../standard/security/index.md)  
 <span data-ttu-id="4c45d-128">提供 .NET Framework 中，可加強應用程式開發安全性的類別及服務的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4c45d-128">Provides information about the classes and services in the .NET Framework that facilitate secure app development.</span></span>  
  
 [<span data-ttu-id="4c45d-129">偵錯、追蹤和程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="4c45d-129">Debugging, Tracing, and Profiling</span></span>](./debug-trace-profile/index.md)  
 <span data-ttu-id="4c45d-130">說明如何測試、最佳化及分析 .NET Framework 應用程式與應用程式的環境。</span><span class="sxs-lookup"><span data-stu-id="4c45d-130">Explains how to test, optimize, and profile .NET Framework apps and the app environment.</span></span> <span data-ttu-id="4c45d-131">本章節包含可供系統管理員和開發者使用的資訊。</span><span class="sxs-lookup"><span data-stu-id="4c45d-131">This section includes information for administrators as well as developers.</span></span>  
  
 [<span data-ttu-id="4c45d-132">進行多平台開發</span><span class="sxs-lookup"><span data-stu-id="4c45d-132">Developing for Multiple Platforms</span></span>](../standard/cross-platform/index.md)  
 <span data-ttu-id="4c45d-133">提供如何使用 .NET Framework ，建置可以讓多種平台與裝置 (例如電話、桌面與 Web) 共用之組件的資訊。</span><span class="sxs-lookup"><span data-stu-id="4c45d-133">Provides information about how you can use the .NET Framework to build assemblies that can be shared across multiple platforms and multiple devices such as phones, desktop, and web.</span></span>  
  
 [<span data-ttu-id="4c45d-134">部署</span><span class="sxs-lookup"><span data-stu-id="4c45d-134">Deployment</span></span>](./deployment/index.md)  
 <span data-ttu-id="4c45d-135">說明如何封裝及散發 .NET Framework 應用程式，同時也加入開發人員與系統管理員適用的部署指南。</span><span class="sxs-lookup"><span data-stu-id="4c45d-135">Explains how to package and distribute your .NET Framework app, and includes deployment guides for both developers and administrators.</span></span>  
  
 [<span data-ttu-id="4c45d-136">效能</span><span class="sxs-lookup"><span data-stu-id="4c45d-136">Performance</span></span>](./performance/index.md)  
 <span data-ttu-id="4c45d-137">提供有關快取、延遲初始設定、可靠性和 ETW 事件的資訊。</span><span class="sxs-lookup"><span data-stu-id="4c45d-137">Provides information about caching, lazy initialization, reliability, and ETW events.</span></span>  

## <a name="reference"></a><span data-ttu-id="4c45d-138">參考</span><span class="sxs-lookup"><span data-stu-id="4c45d-138">Reference</span></span>  
 [<span data-ttu-id="4c45d-139">.NET Framework 類別庫</span><span class="sxs-lookup"><span data-stu-id="4c45d-139">.NET Framework Class Library</span></span>](/dotnet/api/?view=netframework-4.7)  
 <span data-ttu-id="4c45d-140">為每個包含在 .NET Framework 命名空間中的類別，提供語法、程式碼範例及使用方式資訊。</span><span class="sxs-lookup"><span data-stu-id="4c45d-140">Supplies syntax, code examples, and usage information for each class that is contained in the .NET Framework namespaces.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4c45d-141">相關章節</span><span class="sxs-lookup"><span data-stu-id="4c45d-141">Related Sections</span></span>  
 [<span data-ttu-id="4c45d-142">快速入門</span><span class="sxs-lookup"><span data-stu-id="4c45d-142">Getting Started</span></span>](./get-started/index.md)  
 <span data-ttu-id="4c45d-143">提供 .NET Framework 的完整概觀與其他資源的連結。</span><span class="sxs-lookup"><span data-stu-id="4c45d-143">Provides a comprehensive overview of the .NET Framework and links to additional resources.</span></span>  
  
 [<span data-ttu-id="4c45d-144">新功能</span><span class="sxs-lookup"><span data-stu-id="4c45d-144">What's New</span></span>](./whats-new/index.md)  
 <span data-ttu-id="4c45d-145">描述最新版 .NET Framework 中重要的新功能與變更。</span><span class="sxs-lookup"><span data-stu-id="4c45d-145">Describes key new features and changes in the latest version of the .NET Framework.</span></span> <span data-ttu-id="4c45d-146">包含新類型、汰換類型與成員的清單，並提供如何移轉您在舊版 .NET Framework 上之應用程式的指南。</span><span class="sxs-lookup"><span data-stu-id="4c45d-146">Includes lists of new and obsolete types and members, and provides a guide for migrating your apps from the previous version of the .NET Framework.</span></span>  
  
 [<span data-ttu-id="4c45d-147">工具</span><span class="sxs-lookup"><span data-stu-id="4c45d-147">Tools</span></span>](./tools/index.md)  
 <span data-ttu-id="4c45d-148">說明如何應用 .NET Framework 技術，協助您開發、設定及部署應用程式的工具。</span><span class="sxs-lookup"><span data-stu-id="4c45d-148">Describes the tools that help you develop, configure, and deploy apps by using .NET Framework technologies.</span></span>  
  
 [<span data-ttu-id="4c45d-149">.NET 範例與教學課程</span><span class="sxs-lookup"><span data-stu-id="4c45d-149">.NET samples and tutorials</span></span>](../samples-and-tutorials/index.md)  
 <span data-ttu-id="4c45d-150">提供前往範例與教學課程的連結，協助您了解 .NET。</span><span class="sxs-lookup"><span data-stu-id="4c45d-150">Provides links to samples and tutorials that help you learn about .NET.</span></span>
