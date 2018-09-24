---
title: .NET Framework 開發指南
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework, development guide
ms.assetid: 26e3d285-24c3-435c-a797-9fe5affb8525
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a21f4cd8657a9d2c26ac481e7f2b00e6a2f502c9
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581099"
---
# <a name="net-framework-development-guide"></a><span data-ttu-id="79168-102">.NET Framework 開發指南</span><span class="sxs-lookup"><span data-stu-id="79168-102">.NET Framework Development Guide</span></span>
<span data-ttu-id="79168-103">本節說明如何建立、設定、偵錯、保護和部署 .NET Framework 應用程式。</span><span class="sxs-lookup"><span data-stu-id="79168-103">This section explains how to create, configure, debug, secure, and deploy your .NET Framework apps.</span></span> <span data-ttu-id="79168-104">本節也提供有關技術領域的資訊，例如動態程式設計、互通性、擴充性、記憶體管理和執行緒。</span><span class="sxs-lookup"><span data-stu-id="79168-104">The section also provides information about technology areas such as dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="79168-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="79168-105">In This Section</span></span>  
 [<span data-ttu-id="79168-106">應用程式基本概念</span><span class="sxs-lookup"><span data-stu-id="79168-106">Application Essentials</span></span>](../../docs/standard/application-essentials.md)  
 <span data-ttu-id="79168-107">提供基本應用程式開發工作的相關資訊，例如應用程式定義域和組件的程式設計、使用屬性、格式設定和分析基底類型、使用集合、處理事件和例外狀況、使用檔案和資料流，以及使用泛型。</span><span class="sxs-lookup"><span data-stu-id="79168-107">Provides information about basic app development tasks, such as programming with app domains and assemblies, using attributes, formatting and parsing base types, using collections, handling events and exceptions, using files and data streams, and using generics.</span></span>  
  
 [<span data-ttu-id="79168-108">資料與模型化</span><span class="sxs-lookup"><span data-stu-id="79168-108">Data and Modeling</span></span>](../../docs/framework/data/index.md)  
 <span data-ttu-id="79168-109">提供如何使用 ADO.NET、Language Integrated Query (LINQ)、WCF 資料服務和 XML 來存取資料的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="79168-109">Provides information about how to access data using ADO.NET, Language Integrated Query (LINQ), WCF Data Services, and XML.</span></span>  
  
 [<span data-ttu-id="79168-110">用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="79168-110">Client Applications</span></span>](../../docs/framework/develop-client-apps.md)  
 <span data-ttu-id="79168-111">說明如何使用 Windows Presentation Foundation (WPF) 或 Windows Form 建立 Windows 架構應用程式。</span><span class="sxs-lookup"><span data-stu-id="79168-111">Explains how to create Windows-based apps by using Windows Presentation Foundation (WPF) or Windows Forms.</span></span>  
  
 [<span data-ttu-id="79168-112">使用 ASP.NET 的 Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="79168-112">Web Applications with ASP.NET</span></span>](../../docs/framework/develop-web-apps-with-aspnet.md)  
 <span data-ttu-id="79168-113">提供有關使用 ASP.NET，以最少程式碼建置企業級 Web 應用程式之資訊的連結。</span><span class="sxs-lookup"><span data-stu-id="79168-113">Provides links to information about using ASP.NET to build enterprise-class web apps with a minimum of coding.</span></span>  
  
 [<span data-ttu-id="79168-114">使用 WCF 以服務為導向的應用程式</span><span class="sxs-lookup"><span data-stu-id="79168-114">Service-Oriented Applications with WCF</span></span>](../../docs/framework/wcf/index.md)  
 <span data-ttu-id="79168-115">說明如何使用 Windows Communication Foundation (WCF) 建立安全、可靠的服務導向應用程式。</span><span class="sxs-lookup"><span data-stu-id="79168-115">Describes how to use Windows Communication Foundation (WCF) to build service-oriented apps that are secure and reliable.</span></span>  
  
 <span data-ttu-id="79168-116">[使用 Windows Workflow Foundation 建立工作流程](windows-workflow-foundation/index.md)   </span><span class="sxs-lookup"><span data-stu-id="79168-116">[Building workflows with Windows Workflow Foundation](windows-workflow-foundation/index.md)   </span></span>  
 <span data-ttu-id="79168-117">提供使用 Windows Workflow Foundation (WF) 程式撰寫模型、範例和工具的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="79168-117">Provides information about the programming model, samples, and tools for using Windows Workflow Foundation (WF).</span></span>  

 [<span data-ttu-id="79168-118">Windows 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="79168-118">Windows Service Applications</span></span>](../../docs/framework/windows-services/index.md)  
 <span data-ttu-id="79168-119">說明如何使用 Visual Studio 及 .NET Framework 建立要安裝為服務的應用程式，以及啟動、停止及控制其行為。</span><span class="sxs-lookup"><span data-stu-id="79168-119">Explains how you can use Visual Studio and the .NET Framework to create an app that is installed as a service, and start, stop, and otherwise control its behavior.</span></span>  
  
 [<span data-ttu-id="79168-120">.NET 中的平行處理、並行和非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="79168-120">Parallel Processing, Concurrency, and Async Programming in .NET</span></span>](../../docs/standard/parallel-processing-and-concurrency.md)  
 <span data-ttu-id="79168-121">提供有關 Managed 執行緒、平行程式設計和非同步程式設計模式的資訊。</span><span class="sxs-lookup"><span data-stu-id="79168-121">Provides information about managed threading, parallel programming, and asynchronous programming design patterns.</span></span>  
  
 [<span data-ttu-id="79168-122">以 .NET Framework 進行網路程式設計</span><span class="sxs-lookup"><span data-stu-id="79168-122">Network Programming in the .NET Framework</span></span>](../../docs/framework/network-programming/index.md)  
 <span data-ttu-id="79168-123">說明可以讓您迅速方便地整合到您應用程式之有層次、可擴充及受管理的網際網路服務實作。</span><span class="sxs-lookup"><span data-stu-id="79168-123">Describes the layered, extensible, and managed implementation of Internet services that you can quickly and easily integrate into your apps.</span></span>  
  
 <span data-ttu-id="79168-124">[設定 .NET Framework 應用程式](configure-apps/index.md)  </span><span class="sxs-lookup"><span data-stu-id="79168-124">[Configuring .NET Framework Apps](configure-apps/index.md)  </span></span>  
 <span data-ttu-id="79168-125">說明如何直接使用組態檔變更設定，而無須重新編譯您的 .NET Framework 應用程式。</span><span class="sxs-lookup"><span data-stu-id="79168-125">Explains how you can use configuration files to change settings without having to recompile your .NET Framework apps.</span></span>  
  
 [<span data-ttu-id="79168-126">使用 .NET Native 編譯應用程式</span><span class="sxs-lookup"><span data-stu-id="79168-126">Compiling Apps with .NET Native</span></span>](../../docs/framework/net-native/index.md)  
 <span data-ttu-id="79168-127">說明如何使用 [!INCLUDE[net_native](../../includes/net-native-md.md)] 預先編譯技術，建置及部署「Windows 市集」的應用程式。</span><span class="sxs-lookup"><span data-stu-id="79168-127">Explains how you can use the [!INCLUDE[net_native](../../includes/net-native-md.md)] precompilation technology to build and deploy Windows Store apps.</span></span> [!INCLUDE[net_native](../../includes/net-native-md.md)]<span data-ttu-id="79168-128"> 會編譯以 Managed 程式碼 (C#) 所撰寫，並以 .NET Framework 做為機器碼的應用程式。</span><span class="sxs-lookup"><span data-stu-id="79168-128"> compiles apps that are written in managed code (C#) and that target the .NET Framework to native code.</span></span>  
  
 [<span data-ttu-id="79168-129">安全性</span><span class="sxs-lookup"><span data-stu-id="79168-129">Security</span></span>](../../docs/standard/security/index.md)  
 <span data-ttu-id="79168-130">提供 .NET Framework 中，可加強應用程式開發安全性的類別及服務的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="79168-130">Provides information about the classes and services in the .NET Framework that facilitate secure app development.</span></span>  
  
 [<span data-ttu-id="79168-131">偵錯、追蹤和程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="79168-131">Debugging, Tracing, and Profiling</span></span>](../../docs/framework/debug-trace-profile/index.md)  
 <span data-ttu-id="79168-132">說明如何測試、最佳化及分析 .NET Framework 應用程式與應用程式的環境。</span><span class="sxs-lookup"><span data-stu-id="79168-132">Explains how to test, optimize, and profile .NET Framework apps and the app environment.</span></span> <span data-ttu-id="79168-133">本章節包含可供系統管理員和開發者使用的資訊。</span><span class="sxs-lookup"><span data-stu-id="79168-133">This section includes information for administrators as well as developers.</span></span>  
  
 [<span data-ttu-id="79168-134">進行多平台開發</span><span class="sxs-lookup"><span data-stu-id="79168-134">Developing for Multiple Platforms</span></span>](../../docs/standard/cross-platform/index.md)  
 <span data-ttu-id="79168-135">提供如何使用 .NET Framework ，建置可以讓多種平台與裝置 (例如電話、桌面與 Web) 共用之組件的資訊。</span><span class="sxs-lookup"><span data-stu-id="79168-135">Provides information about how you can use the .NET Framework to build assemblies that can be shared across multiple platforms and multiple devices such as phones, desktop, and web.</span></span>  
  
 [<span data-ttu-id="79168-136">部署</span><span class="sxs-lookup"><span data-stu-id="79168-136">Deployment</span></span>](../../docs/framework/deployment/index.md)  
 <span data-ttu-id="79168-137">說明如何封裝及散發 .NET Framework 應用程式，同時也加入開發人員與系統管理員適用的部署指南。</span><span class="sxs-lookup"><span data-stu-id="79168-137">Explains how to package and distribute your .NET Framework app, and includes deployment guides for both developers and administrators.</span></span>  
  
 [<span data-ttu-id="79168-138">效能</span><span class="sxs-lookup"><span data-stu-id="79168-138">Performance</span></span>](../../docs/framework/performance/index.md)  
 <span data-ttu-id="79168-139">提供有關快取、延遲初始設定、可靠性和 ETW 事件的資訊。</span><span class="sxs-lookup"><span data-stu-id="79168-139">Provides information about caching, lazy initialization, reliability, and ETW events.</span></span>  
 
## <a name="reference"></a><span data-ttu-id="79168-140">參考資料</span><span class="sxs-lookup"><span data-stu-id="79168-140">Reference</span></span>  
 [<span data-ttu-id="79168-141">.NET Framework 類別庫</span><span class="sxs-lookup"><span data-stu-id="79168-141">.NET Framework Class Library</span></span>](/dotnet/api/?view=netframework-4.7)  
 <span data-ttu-id="79168-142">為每個包含在 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 命名空間的類別提供語法、程式碼範例和用法資訊。</span><span class="sxs-lookup"><span data-stu-id="79168-142">Supplies syntax, code examples, and usage information for each class that is contained in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] namespaces.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="79168-143">相關章節</span><span class="sxs-lookup"><span data-stu-id="79168-143">Related Sections</span></span>  
 [<span data-ttu-id="79168-144">快速入門</span><span class="sxs-lookup"><span data-stu-id="79168-144">Getting Started</span></span>](../../docs/framework/get-started/index.md)  
 <span data-ttu-id="79168-145">提供 .NET Framework 的完整概觀與其他資源的連結。</span><span class="sxs-lookup"><span data-stu-id="79168-145">Provides a comprehensive overview of the .NET Framework and links to additional resources.</span></span>  
  
 [<span data-ttu-id="79168-146">新功能</span><span class="sxs-lookup"><span data-stu-id="79168-146">What's New</span></span>](../../docs/framework/whats-new/index.md)  
 <span data-ttu-id="79168-147">描述最新版 .NET Framework 中重要的新功能與變更。</span><span class="sxs-lookup"><span data-stu-id="79168-147">Describes key new features and changes in the latest version of the .NET Framework.</span></span> <span data-ttu-id="79168-148">包含新類型、汰換類型與成員的清單，並提供如何移轉您在舊版 .NET Framework 上之應用程式的指南。</span><span class="sxs-lookup"><span data-stu-id="79168-148">Includes lists of new and obsolete types and members, and provides a guide for migrating your apps from the previous version of the .NET Framework.</span></span>  
  
 [<span data-ttu-id="79168-149">工具</span><span class="sxs-lookup"><span data-stu-id="79168-149">Tools</span></span>](../../docs/framework/tools/index.md)  
 <span data-ttu-id="79168-150">說明如何應用 .NET Framework 技術，協助您開發、設定及部署應用程式的工具。</span><span class="sxs-lookup"><span data-stu-id="79168-150">Describes the tools that help you develop, configure, and deploy apps by using .NET Framework technologies.</span></span>  
  
 [<span data-ttu-id="79168-151">.NET Framework 範例</span><span class="sxs-lookup"><span data-stu-id="79168-151">.NET Framework Samples</span></span>](https://msdn.microsoft.com/library/177055f8-4a1f-43e7-aee6-995c196079b1)  
 <span data-ttu-id="79168-152">提供 MSDN 程式碼範例庫中之範例應用程式的連結，以示範 .NET Framework 技術。</span><span class="sxs-lookup"><span data-stu-id="79168-152">Provides links to the MSDN Code Samples Gallery for sample apps that demonstrate .NET Framework technologies.</span></span>
