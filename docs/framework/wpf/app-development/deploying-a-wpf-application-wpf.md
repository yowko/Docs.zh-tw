---
title: 部署 WPF 應用程式 (WPF)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF applications [WPF], deployment
- deployment [WPF], applications
ms.assetid: 12cadca0-b32c-4064-9a56-e6a306dcc76d
ms.openlocfilehash: a1441f0cc3a7ac715a173be12e68c055ce36ff00
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460141"
---
# <a name="deploying-a-wpf-application-wpf"></a><span data-ttu-id="02da6-102">部署 WPF 應用程式 (WPF)</span><span class="sxs-lookup"><span data-stu-id="02da6-102">Deploying a WPF Application (WPF)</span></span>
<span data-ttu-id="02da6-103">建立 Windows Presentation Foundation （WPF）應用程式之後，就必須部署它們。</span><span class="sxs-lookup"><span data-stu-id="02da6-103">After Windows Presentation Foundation (WPF) applications are built, they need to be deployed.</span></span> <span data-ttu-id="02da6-104">Windows 和 .NET Framework 包含數種部署技術。</span><span class="sxs-lookup"><span data-stu-id="02da6-104">Windows and the .NET Framework include several deployment technologies.</span></span> <span data-ttu-id="02da6-105">用來部署 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式的部署技術會視應用程式類型而定。</span><span class="sxs-lookup"><span data-stu-id="02da6-105">The deployment technology that is used to deploy a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application depends on the application type.</span></span> <span data-ttu-id="02da6-106">本主題提供每項部署技術的簡短概觀，並說明這些技術如何配合每種 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式類型的部署需求來使用。</span><span class="sxs-lookup"><span data-stu-id="02da6-106">This topic provides a brief overview of each deployment technology, and how they are used in conjunction with the deployment requirements of each [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application type.</span></span>  

<a name="Deployment_Technologies"></a>   
## <a name="deployment-technologies"></a><span data-ttu-id="02da6-107">部署技術</span><span class="sxs-lookup"><span data-stu-id="02da6-107">Deployment Technologies</span></span>  
 <span data-ttu-id="02da6-108">Windows 和 .NET Framework 包含數種部署技術，包括：</span><span class="sxs-lookup"><span data-stu-id="02da6-108">Windows and the .NET Framework include several deployment technologies, including:</span></span>  
  
- <span data-ttu-id="02da6-109">XCopy 部署。</span><span class="sxs-lookup"><span data-stu-id="02da6-109">XCopy deployment.</span></span>  
  
- <span data-ttu-id="02da6-110">Windows Installer 部署。</span><span class="sxs-lookup"><span data-stu-id="02da6-110">Windows Installer deployment.</span></span>  
  
- <span data-ttu-id="02da6-111">ClickOnce 佈署。</span><span class="sxs-lookup"><span data-stu-id="02da6-111">ClickOnce deployment.</span></span>  
  
<a name="XCopy_Deployment"></a>   
### <a name="xcopy-deployment"></a><span data-ttu-id="02da6-112">XCopy 部署</span><span class="sxs-lookup"><span data-stu-id="02da6-112">XCopy Deployment</span></span>  
 <span data-ttu-id="02da6-113">XCopy 部署是指使用 XCopy 命令列程式，將檔案從一個位置複製到另一個位置。</span><span class="sxs-lookup"><span data-stu-id="02da6-113">XCopy deployment refers to the use of the XCopy command-line program to copy files from one location to another.</span></span> <span data-ttu-id="02da6-114">XCopy 部署適用於下列情況：</span><span class="sxs-lookup"><span data-stu-id="02da6-114">XCopy deployment is suitable under the following circumstances:</span></span>  
  
- <span data-ttu-id="02da6-115">應用程式是獨立的。</span><span class="sxs-lookup"><span data-stu-id="02da6-115">The application is self-contained.</span></span> <span data-ttu-id="02da6-116">不需要更新用戶端即可執行。</span><span class="sxs-lookup"><span data-stu-id="02da6-116">It does not need to update the client to run.</span></span>  
  
- <span data-ttu-id="02da6-117">應用程式檔必須從一個位置移到另一個位置，例如從組建位置（本機磁片、UNC 檔案共用等）到發行位置（網站、UNC 檔案共用等等）。</span><span class="sxs-lookup"><span data-stu-id="02da6-117">Application files must be moved from one location to another, such as from a build location (local disk, UNC file share, and so on) to a publish location (Web site, UNC file share, and so on).</span></span>  
  
- <span data-ttu-id="02da6-118">應用程式不需要介面整合 ([開始] 功能表捷徑、桌面圖示等)。</span><span class="sxs-lookup"><span data-stu-id="02da6-118">The application does not require shell integration (Start menu shortcut, desktop icon, and so on).</span></span>  
  
 <span data-ttu-id="02da6-119">雖然 XCopy 適用於簡單的部署案例，但當需要更複雜的部署功能時卻會受到限制。</span><span class="sxs-lookup"><span data-stu-id="02da6-119">Although XCopy is suitable for simple deployment scenarios, it is limited when more complex deployment capabilities are required.</span></span> <span data-ttu-id="02da6-120">特別是，使用 XCopy 通常需要另外建立、執行和維護指令碼，才能穩固地管理部署。</span><span class="sxs-lookup"><span data-stu-id="02da6-120">In particular, using XCopy often incurs the overhead for creating, executing, and maintaining scripts for managing deployment in a robust way.</span></span> <span data-ttu-id="02da6-121">此外，XCopy 不支援版本設定、解除安裝或復原。</span><span class="sxs-lookup"><span data-stu-id="02da6-121">Furthermore, XCopy does not support versioning, uninstallation, or rollback.</span></span>  
  
<a name="Windows_Installer"></a>   
### <a name="windows-installer"></a><span data-ttu-id="02da6-122">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="02da6-122">Windows Installer</span></span>  
 <span data-ttu-id="02da6-123">Windows Installer 可讓應用程式封裝成獨立的可執行檔，輕鬆散發給用戶端並執行。</span><span class="sxs-lookup"><span data-stu-id="02da6-123">Windows Installer allows applications to be packaged as self-contained executables that can be easily distributed to clients and run.</span></span> <span data-ttu-id="02da6-124">此外，Windows Installer 會與 Windows 一起安裝，並啟用與桌面、[開始] 功能表和 [程式] 控制台的整合。</span><span class="sxs-lookup"><span data-stu-id="02da6-124">Furthermore, Windows Installer is installed with Windows and enables integration with the desktop, the Start menu, and the Programs control panel.</span></span>  
  
 <span data-ttu-id="02da6-125">Windows Installer 簡化了應用程式的安裝和卸載，但它並不提供可確保已安裝的應用程式從版本控制的觀點來保持最新狀態的功能。</span><span class="sxs-lookup"><span data-stu-id="02da6-125">Windows Installer simplifies the installation and uninstallation of applications, but it does not provide facilities for ensuring that installed applications are kept up-to-date from a versioning standpoint.</span></span>  
  
 <span data-ttu-id="02da6-126">如需 Windows Installer 的詳細資訊，請參閱[Windows Installer 部署](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop)。</span><span class="sxs-lookup"><span data-stu-id="02da6-126">For more information about Windows Installer, see [Windows Installer Deployment](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span></span>
  
<a name="ClickOnce_Deployment"></a>   
### <a name="clickonce-deployment"></a><span data-ttu-id="02da6-127">ClickOnce 部署</span><span class="sxs-lookup"><span data-stu-id="02da6-127">ClickOnce Deployment</span></span>  
 <span data-ttu-id="02da6-128">ClickOnce 為非 Web 應用程式啟用 Web 樣式應用程式部署。</span><span class="sxs-lookup"><span data-stu-id="02da6-128">ClickOnce enables Web-style application deployment for non-Web applications.</span></span> <span data-ttu-id="02da6-129">應用程式會先發行至網頁伺服器或檔案伺服器，再從中部署。</span><span class="sxs-lookup"><span data-stu-id="02da6-129">Applications are published to and deployed from Web or file servers.</span></span> <span data-ttu-id="02da6-130">雖然 ClickOnce 不支援 Windows Installer 安裝的應用程式所需的完整用戶端功能範圍，但它支援包含下列的子集：</span><span class="sxs-lookup"><span data-stu-id="02da6-130">Although ClickOnce does not support the full range of client features that Windows Installer-installed applications do, it does support a subset that includes the following:</span></span>  
  
- <span data-ttu-id="02da6-131">與 [開始] 功能表和 [程式集] 控制台整合。</span><span class="sxs-lookup"><span data-stu-id="02da6-131">Integration with the Start menu and Programs control panel.</span></span>  
  
- <span data-ttu-id="02da6-132">版本設定、復原和解除安裝。</span><span class="sxs-lookup"><span data-stu-id="02da6-132">Versioning, rollback, and uninstallation.</span></span>  
  
- <span data-ttu-id="02da6-133">一律會從部署位置啟動應用程式的線上安裝模式。</span><span class="sxs-lookup"><span data-stu-id="02da6-133">Online install mode, which always launches an application from the deployment location.</span></span>  
  
- <span data-ttu-id="02da6-134">在發行新版本時自動更新。</span><span class="sxs-lookup"><span data-stu-id="02da6-134">Automatic updating when new versions are released.</span></span>  
  
- <span data-ttu-id="02da6-135">註冊副檔名。</span><span class="sxs-lookup"><span data-stu-id="02da6-135">Registration of file extensions.</span></span>  
  
 <span data-ttu-id="02da6-136">如需 ClickOnce 的詳細資訊，請參閱[Clickonce 安全性和部署](/visualstudio/deployment/clickonce-security-and-deployment)。</span><span class="sxs-lookup"><span data-stu-id="02da6-136">For more information about ClickOnce, see [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).</span></span>  
  
<a name="Deploying_WPF_Applications"></a>   
## <a name="deploying-wpf-applications"></a><span data-ttu-id="02da6-137">部署 WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="02da6-137">Deploying WPF Applications</span></span>  
 <span data-ttu-id="02da6-138">[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式的部署選項會視應用程式類型而定。</span><span class="sxs-lookup"><span data-stu-id="02da6-138">The deployment options for a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application depend on the type of application.</span></span> <span data-ttu-id="02da6-139">從部署觀點來看，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 有三個重要的應用程式類型：</span><span class="sxs-lookup"><span data-stu-id="02da6-139">From a deployment perspective, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] has three significant application types:</span></span>  
  
- <span data-ttu-id="02da6-140">獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="02da6-140">Standalone applications.</span></span>  
  
- <span data-ttu-id="02da6-141">全標記 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 應用程式。</span><span class="sxs-lookup"><span data-stu-id="02da6-141">Markup-only [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] applications.</span></span>  
  
- <span data-ttu-id="02da6-142">XAML 瀏覽器應用程式（Xbap）。</span><span class="sxs-lookup"><span data-stu-id="02da6-142">XAML browser applications (XBAPs).</span></span>  
  
<a name="Deploying_Standalone_Applications"></a>   
### <a name="deploying-standalone-applications"></a><span data-ttu-id="02da6-143">部署獨立應用程式</span><span class="sxs-lookup"><span data-stu-id="02da6-143">Deploying Standalone Applications</span></span>  
 <span data-ttu-id="02da6-144">使用 ClickOnce 或 Windows Installer 部署獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="02da6-144">Standalone applications are deployed using either ClickOnce or Windows Installer.</span></span> <span data-ttu-id="02da6-145">無論使用哪種方式，獨立應用程式都需要完全信任才能執行。</span><span class="sxs-lookup"><span data-stu-id="02da6-145">Either way, standalone applications require full trust to run.</span></span> <span data-ttu-id="02da6-146">系統會自動將完全信任授與使用 Windows Installer 部署的獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="02da6-146">Full trust is automatically granted to standalone applications that are deployed using Windows Installer.</span></span> <span data-ttu-id="02da6-147">使用 ClickOnce 部署的獨立應用程式不會自動授與完全信任。</span><span class="sxs-lookup"><span data-stu-id="02da6-147">Standalone applications that are deployed using ClickOnce are not automatically granted full trust.</span></span> <span data-ttu-id="02da6-148">相反地，ClickOnce 會在安裝獨立應用程式之前，顯示使用者必須接受的安全性警告對話方塊。</span><span class="sxs-lookup"><span data-stu-id="02da6-148">Instead, ClickOnce displays a security warning dialog that users must accept before a standalone application is installed.</span></span> <span data-ttu-id="02da6-149">如果接受，則會安裝獨立應用程式並授與完全信任。</span><span class="sxs-lookup"><span data-stu-id="02da6-149">If accepted, the standalone application is installed and granted full trust.</span></span> <span data-ttu-id="02da6-150">如果不接受，則不會安裝獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="02da6-150">If not, the standalone application is not installed.</span></span>  
  
<a name="Deploying_Markup_Only_XAML_Applications"></a>   
### <a name="deploying-markup-only-xaml-applications"></a><span data-ttu-id="02da6-151">部署全標記 XAML 應用程式</span><span class="sxs-lookup"><span data-stu-id="02da6-151">Deploying Markup-Only XAML Applications</span></span>  
 <span data-ttu-id="02da6-152">僅限標記的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面通常會發行至網頁伺服器（例如 HTML 網頁），並可使用 Internet Explorer 來進行查看。</span><span class="sxs-lookup"><span data-stu-id="02da6-152">Markup-only [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pages are usually published to Web servers, like HTML pages, and can be viewed using Internet Explorer.</span></span> <span data-ttu-id="02da6-153">全標記 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面會在部分信任的安全性沙箱內執行，其限制是由網際網路區域權限集合所定義。</span><span class="sxs-lookup"><span data-stu-id="02da6-153">Markup-only [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pages run within a partial-trust security sandbox with restrictions that are defined by the Internet zone permission set.</span></span> <span data-ttu-id="02da6-154">這會提供對等的安全性沙箱給 HTML Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="02da6-154">This provides an equivalent security sandbox to HTML-based Web applications.</span></span>  
  
 <span data-ttu-id="02da6-155">如需 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式之安全性的詳細資訊，請參閱[安全性](../security-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="02da6-155">For more information about security for [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications, see [Security](../security-wpf.md).</span></span>  
  
 <span data-ttu-id="02da6-156">僅限標記的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面可以使用 XCopy 或 Windows Installer 安裝到本機檔案系統。</span><span class="sxs-lookup"><span data-stu-id="02da6-156">Markup-only [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pages can be installed to the local file system by using either XCopy or Windows Installer.</span></span> <span data-ttu-id="02da6-157">您可以使用 Internet Explorer 或 Windows Explorer 來查看這些頁面。</span><span class="sxs-lookup"><span data-stu-id="02da6-157">These pages can be viewed using Internet Explorer or Windows Explorer.</span></span>  
  
 <span data-ttu-id="02da6-158">如需 XAML 的詳細資訊，請參閱 [XAML 概觀 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="02da6-158">For more information about XAML, see [XAML Overview (WPF)](../../../desktop-wpf/fundamentals/xaml.md).</span></span>  
  
<a name="Deploying_XAML_Browser_Applications"></a>   
### <a name="deploying-xaml-browser-applications"></a><span data-ttu-id="02da6-159">部署 XAML 瀏覽器應用程式</span><span class="sxs-lookup"><span data-stu-id="02da6-159">Deploying XAML Browser Applications</span></span>  
 <span data-ttu-id="02da6-160">Xbap 是編譯的應用程式，需要部署下列三個檔案：</span><span class="sxs-lookup"><span data-stu-id="02da6-160">XBAPs are compiled applications that require the following three files to be deployed:</span></span>  
  
- <span data-ttu-id="02da6-161">*應用程式名稱*.exe：可執行組件應用程式檔案。</span><span class="sxs-lookup"><span data-stu-id="02da6-161">*ApplicationName*.exe: The executable assembly application file.</span></span>  
  
- <span data-ttu-id="02da6-162">*應用程式名稱*.xbap：部署資訊清單。</span><span class="sxs-lookup"><span data-stu-id="02da6-162">*ApplicationName*.xbap: The deployment manifest.</span></span>  
  
- <span data-ttu-id="02da6-163">*應用程式名稱*.exe.manifest：應用程式資訊清單。</span><span class="sxs-lookup"><span data-stu-id="02da6-163">*ApplicationName*.exe.manifest: The application manifest.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="02da6-164">如需部署和應用程式資訊清單的詳細資訊，請參閱[建置 WPF 應用程式](building-a-wpf-application-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="02da6-164">For more information about deployment and application manifests, see [Building a WPF Application](building-a-wpf-application-wpf.md).</span></span>  
  
 <span data-ttu-id="02da6-165">建立 XBAP 時，會產生這些檔案。</span><span class="sxs-lookup"><span data-stu-id="02da6-165">These files are produced when an XBAP is built.</span></span> <span data-ttu-id="02da6-166">如需更多詳細資訊，請參閱[如何：建立新的 WPF 瀏覽器應用程式專案](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="02da6-166">For more information, see [How to: Create a New WPF Browser Application Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100)).</span></span> <span data-ttu-id="02da6-167">如同僅限標記的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面，Xbap 通常會發行至 Web 服務器，並使用 Internet Explorer 來查看。</span><span class="sxs-lookup"><span data-stu-id="02da6-167">Like markup-only [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pages, XBAPs are typically published to a Web server and viewed using Internet Explorer.</span></span>  
  
 <span data-ttu-id="02da6-168">Xbap 可以使用任何部署技術部署到用戶端。</span><span class="sxs-lookup"><span data-stu-id="02da6-168">XBAPs can be deployed to clients using any of the deployment techniques.</span></span> <span data-ttu-id="02da6-169">不過，建議使用 ClickOnce，因為它提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="02da6-169">However, ClickOnce is recommended since it provides the following capabilities:</span></span>  
  
1. <span data-ttu-id="02da6-170">在發行新版本時自動更新。</span><span class="sxs-lookup"><span data-stu-id="02da6-170">Automatic updates when a new version is published.</span></span>  
  
2. <span data-ttu-id="02da6-171">以完全信任執行之 XBAP 的提升許可權。</span><span class="sxs-lookup"><span data-stu-id="02da6-171">Elevation privileges for the XBAP running with full trust.</span></span>  
  
 <span data-ttu-id="02da6-172">根據預設，ClickOnce 會發行副檔名為 .deploy 的應用程式檔案。</span><span class="sxs-lookup"><span data-stu-id="02da6-172">By default, ClickOnce publishes application files with the .deploy extension.</span></span> <span data-ttu-id="02da6-173">這可能會造成問題，但可予以停用。</span><span class="sxs-lookup"><span data-stu-id="02da6-173">This can be problematic, but can be disabled.</span></span> <span data-ttu-id="02da6-174">如需詳細資訊，請參閱 [ClickOnce 部署中的伺服器和用戶端組態問題](/visualstudio/deployment/server-and-client-configuration-issues-in-clickonce-deployments)。</span><span class="sxs-lookup"><span data-stu-id="02da6-174">For more information, see [Server and Client Configuration Issues in ClickOnce Deployments](/visualstudio/deployment/server-and-client-configuration-issues-in-clickonce-deployments).</span></span>  
  
 <span data-ttu-id="02da6-175">如需部署 XAML 瀏覽器應用程式（Xbap）的詳細資訊，請參閱[WPF XAML 瀏覽器應用程式總覽](wpf-xaml-browser-applications-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="02da6-175">For more information about deploying XAML browser applications (XBAPs), see [WPF XAML Browser Applications Overview](wpf-xaml-browser-applications-overview.md).</span></span>  
  
<a name="Installing__NET_Framework_3_0"></a>   
## <a name="installing-the-net-framework"></a><span data-ttu-id="02da6-176">安裝.NET Framework</span><span class="sxs-lookup"><span data-stu-id="02da6-176">Installing the .NET Framework</span></span>  
 <span data-ttu-id="02da6-177">若要執行 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式，必須在用戶端上安裝 Microsoft .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="02da6-177">To run a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application, the Microsoft .NET Framework must be installed on the client.</span></span> <span data-ttu-id="02da6-178">當 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 瀏覽器裝載的應用程式被查看時，Internet Explorer 會自動偵測用戶端是否已安裝 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="02da6-178">Internet Explorer automatically detects whether clients are installed with .NET Framework when [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] browser-hosted applications are viewed.</span></span> <span data-ttu-id="02da6-179">如果未安裝 .NET Framework，Internet Explorer 會提示使用者安裝它。</span><span class="sxs-lookup"><span data-stu-id="02da6-179">If the .NET Framework is not installed, Internet Explorer prompts users to install it.</span></span>  
  
 <span data-ttu-id="02da6-180">為了偵測是否已安裝 .NET Framework，Internet Explorer 包含一個啟動載入器應用程式，它會註冊為具有下列副檔名之內容檔案的回溯多用途網際網路郵件延伸（MIME）處理常式： .xaml、.xps、xbap、和. 應用程式。</span><span class="sxs-lookup"><span data-stu-id="02da6-180">To detect whether the .NET Framework is installed, Internet Explorer includes a bootstrapper application that is registered as the fallback Multipurpose Internet Mail Extensions (MIME) handler for content files with the following extensions: .xaml, .xps, .xbap, and .application.</span></span> <span data-ttu-id="02da6-181">如果您流覽至這些檔案類型，而且用戶端上未安裝 .NET Framework，啟動載入器應用程式會要求安裝它的許可權。</span><span class="sxs-lookup"><span data-stu-id="02da6-181">If you navigate to these file types and the .NET Framework is not installed on the client, the bootstrapper application requests permission to install it.</span></span> <span data-ttu-id="02da6-182">如果未提供許可權，就不會安裝 .NET Framework 或應用程式。</span><span class="sxs-lookup"><span data-stu-id="02da6-182">If permission is not provided, neither the .NET Framework nor the application is installed.</span></span>  
  
 <span data-ttu-id="02da6-183">如果授與許可權，Internet Explorer 會使用 Microsoft 背景智慧型傳送服務（BITS）下載並安裝 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="02da6-183">If permission is granted, Internet Explorer downloads and installs the .NET Framework using the Microsoft Background Intelligent Transfer Service (BITS).</span></span> <span data-ttu-id="02da6-184">成功安裝 .NET Framework 之後，原先要求的檔案會在新的瀏覽器視窗中開啟。</span><span class="sxs-lookup"><span data-stu-id="02da6-184">After successful installation of the .NET Framework, the originally requested file is opened in a new browser window.</span></span>  
  
 <span data-ttu-id="02da6-185">如需詳細資訊，請參閱[部署 .NET Framework 和應用程式](../../deployment/index.md)。</span><span class="sxs-lookup"><span data-stu-id="02da6-185">For more information, see [Deploying the .NET Framework and Applications](../../deployment/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02da6-186">請參閱</span><span class="sxs-lookup"><span data-stu-id="02da6-186">See also</span></span>

- [<span data-ttu-id="02da6-187">建置 WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="02da6-187">Building a WPF Application</span></span>](building-a-wpf-application-wpf.md)
- [<span data-ttu-id="02da6-188">Security</span><span class="sxs-lookup"><span data-stu-id="02da6-188">Security</span></span>](../security-wpf.md)
