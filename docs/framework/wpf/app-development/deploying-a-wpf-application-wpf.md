---
title: 部署應用程式
ms.date: 03/30/2017
helpviewer_keywords:
- WPF applications [WPF], deployment
- deployment [WPF], applications
ms.assetid: 12cadca0-b32c-4064-9a56-e6a306dcc76d
ms.openlocfilehash: 54d14503a0f65bb50f2dfb14d40af3b47d51589c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186317"
---
# <a name="deploy-a-wpf-application"></a><span data-ttu-id="306c2-102">部署 WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="306c2-102">Deploy a WPF Application</span></span>

<span data-ttu-id="306c2-103">構建 Windows 演示基礎 （WPF） 應用程式後，需要部署它們。</span><span class="sxs-lookup"><span data-stu-id="306c2-103">After Windows Presentation Foundation (WPF) applications are built, they need to be deployed.</span></span> <span data-ttu-id="306c2-104">Windows 和 .NET 框架包括多種部署技術。</span><span class="sxs-lookup"><span data-stu-id="306c2-104">Windows and the .NET Framework include several deployment technologies.</span></span> <span data-ttu-id="306c2-105">用於部署 WPF 應用程式的部署技術取決於應用程式類型。</span><span class="sxs-lookup"><span data-stu-id="306c2-105">The deployment technology that is used to deploy a WPF application depends on the application type.</span></span> <span data-ttu-id="306c2-106">本主題簡要概述了每種部署技術，以及如何結合每種 WPF 應用程式類型的部署要求使用。</span><span class="sxs-lookup"><span data-stu-id="306c2-106">This topic provides a brief overview of each deployment technology, and how they are used in conjunction with the deployment requirements of each WPF application type.</span></span>

<a name="Deployment_Technologies"></a>
## <a name="deployment-technologies"></a><span data-ttu-id="306c2-107">部署技術</span><span class="sxs-lookup"><span data-stu-id="306c2-107">Deployment Technologies</span></span>  
 <span data-ttu-id="306c2-108">Windows 和 .NET 框架包括多種部署技術，包括：</span><span class="sxs-lookup"><span data-stu-id="306c2-108">Windows and the .NET Framework include several deployment technologies, including:</span></span>  
  
- <span data-ttu-id="306c2-109">XCopy 部署。</span><span class="sxs-lookup"><span data-stu-id="306c2-109">XCopy deployment.</span></span>  
  
- <span data-ttu-id="306c2-110">Windows 安裝程式部署。</span><span class="sxs-lookup"><span data-stu-id="306c2-110">Windows Installer deployment.</span></span>  
  
- <span data-ttu-id="306c2-111">ClickOnce 部署。</span><span class="sxs-lookup"><span data-stu-id="306c2-111">ClickOnce deployment.</span></span>  
  
<a name="XCopy_Deployment"></a>
### <a name="xcopy-deployment"></a><span data-ttu-id="306c2-112">XCopy 部署</span><span class="sxs-lookup"><span data-stu-id="306c2-112">XCopy Deployment</span></span>  
 <span data-ttu-id="306c2-113">XCopy 部署是指使用 XCopy 命令列程式，將檔案從一個位置複製到另一個位置。</span><span class="sxs-lookup"><span data-stu-id="306c2-113">XCopy deployment refers to the use of the XCopy command-line program to copy files from one location to another.</span></span> <span data-ttu-id="306c2-114">XCopy 部署適用於下列情況：</span><span class="sxs-lookup"><span data-stu-id="306c2-114">XCopy deployment is suitable under the following circumstances:</span></span>  
  
- <span data-ttu-id="306c2-115">應用程式是獨立的。</span><span class="sxs-lookup"><span data-stu-id="306c2-115">The application is self-contained.</span></span> <span data-ttu-id="306c2-116">不需要更新用戶端即可執行。</span><span class="sxs-lookup"><span data-stu-id="306c2-116">It does not need to update the client to run.</span></span>  
  
- <span data-ttu-id="306c2-117">應用程式檔必須從一個位置移動到另一個位置，例如從生成位置（本地磁片、UNC 檔共用等）移動到發佈位置（網站、UNC 檔共用等）。</span><span class="sxs-lookup"><span data-stu-id="306c2-117">Application files must be moved from one location to another, such as from a build location (local disk, UNC file share, and so on) to a publish location (Web site, UNC file share, and so on).</span></span>  
  
- <span data-ttu-id="306c2-118">應用程式不需要介面整合 ([開始] 功能表捷徑、桌面圖示等)。</span><span class="sxs-lookup"><span data-stu-id="306c2-118">The application does not require shell integration (Start menu shortcut, desktop icon, and so on).</span></span>  
  
 <span data-ttu-id="306c2-119">雖然 XCopy 適用於簡單的部署案例，但當需要更複雜的部署功能時卻會受到限制。</span><span class="sxs-lookup"><span data-stu-id="306c2-119">Although XCopy is suitable for simple deployment scenarios, it is limited when more complex deployment capabilities are required.</span></span> <span data-ttu-id="306c2-120">特別是，使用 XCopy 通常需要另外建立、執行和維護指令碼，才能穩固地管理部署。</span><span class="sxs-lookup"><span data-stu-id="306c2-120">In particular, using XCopy often incurs the overhead for creating, executing, and maintaining scripts for managing deployment in a robust way.</span></span> <span data-ttu-id="306c2-121">此外，XCopy 不支援版本設定、解除安裝或復原。</span><span class="sxs-lookup"><span data-stu-id="306c2-121">Furthermore, XCopy does not support versioning, uninstallation, or rollback.</span></span>  
  
<a name="Windows_Installer"></a>
### <a name="windows-installer"></a><span data-ttu-id="306c2-122">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="306c2-122">Windows Installer</span></span>  
 <span data-ttu-id="306c2-123">Windows 安裝程式允許將應用程式打包為可獨立執行檔，以便輕鬆分發到用戶端並運行。</span><span class="sxs-lookup"><span data-stu-id="306c2-123">Windows Installer allows applications to be packaged as self-contained executables that can be easily distributed to clients and run.</span></span> <span data-ttu-id="306c2-124">此外，Windows 安裝程式與 Windows 一起安裝，並啟用與桌面、"開始"功能表和程式控制面板的集成。</span><span class="sxs-lookup"><span data-stu-id="306c2-124">Furthermore, Windows Installer is installed with Windows and enables integration with the desktop, the Start menu, and the Programs control panel.</span></span>  
  
 <span data-ttu-id="306c2-125">Windows 安裝程式簡化了應用程式的安裝和卸載，但它不提供從版本控制的角度來看確保已安裝的應用程式保持最新功能。</span><span class="sxs-lookup"><span data-stu-id="306c2-125">Windows Installer simplifies the installation and uninstallation of applications, but it does not provide facilities for ensuring that installed applications are kept up-to-date from a versioning standpoint.</span></span>  
  
 <span data-ttu-id="306c2-126">有關 Windows 安裝程式的詳細資訊，請參閱[Windows 安裝程式部署](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop)。</span><span class="sxs-lookup"><span data-stu-id="306c2-126">For more information about Windows Installer, see [Windows Installer Deployment](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span></span>
  
<a name="ClickOnce_Deployment"></a>
### <a name="clickonce-deployment"></a><span data-ttu-id="306c2-127">ClickOnce 部署</span><span class="sxs-lookup"><span data-stu-id="306c2-127">ClickOnce Deployment</span></span>  
 <span data-ttu-id="306c2-128">ClickOnce 支援針對非 Web 應用程式部署 Web 樣式的應用程式。</span><span class="sxs-lookup"><span data-stu-id="306c2-128">ClickOnce enables Web-style application deployment for non-Web applications.</span></span> <span data-ttu-id="306c2-129">應用程式會先發行至網頁伺服器或檔案伺服器，再從中部署。</span><span class="sxs-lookup"><span data-stu-id="306c2-129">Applications are published to and deployed from Web or file servers.</span></span> <span data-ttu-id="306c2-130">儘管 ClickOnce 不支援 Windows 安裝程式安裝的應用程式的全部用戶端功能，但它確實支援包含以下內容的子集：</span><span class="sxs-lookup"><span data-stu-id="306c2-130">Although ClickOnce does not support the full range of client features that Windows Installer-installed applications do, it does support a subset that includes the following:</span></span>  
  
- <span data-ttu-id="306c2-131">與 [開始] 功能表和 [程式集] 控制台整合。</span><span class="sxs-lookup"><span data-stu-id="306c2-131">Integration with the Start menu and Programs control panel.</span></span>  
  
- <span data-ttu-id="306c2-132">版本設定、復原和解除安裝。</span><span class="sxs-lookup"><span data-stu-id="306c2-132">Versioning, rollback, and uninstallation.</span></span>  
  
- <span data-ttu-id="306c2-133">一律會從部署位置啟動應用程式的線上安裝模式。</span><span class="sxs-lookup"><span data-stu-id="306c2-133">Online install mode, which always launches an application from the deployment location.</span></span>  
  
- <span data-ttu-id="306c2-134">在發行新版本時自動更新。</span><span class="sxs-lookup"><span data-stu-id="306c2-134">Automatic updating when new versions are released.</span></span>  
  
- <span data-ttu-id="306c2-135">註冊副檔名。</span><span class="sxs-lookup"><span data-stu-id="306c2-135">Registration of file extensions.</span></span>  
  
 <span data-ttu-id="306c2-136">有關按一下"一次"的詳細資訊，請參閱[按一下"一次安全和部署](/visualstudio/deployment/clickonce-security-and-deployment)"。</span><span class="sxs-lookup"><span data-stu-id="306c2-136">For more information about ClickOnce, see [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).</span></span>  
  
<a name="Deploying_WPF_Applications"></a>
## <a name="deploying-wpf-applications"></a><span data-ttu-id="306c2-137">部署 WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="306c2-137">Deploying WPF Applications</span></span>  
 <span data-ttu-id="306c2-138">WPF 應用程式的部署選項取決於應用程式的類型。</span><span class="sxs-lookup"><span data-stu-id="306c2-138">The deployment options for a WPF application depend on the type of application.</span></span> <span data-ttu-id="306c2-139">從部署的角度來看，WPF 有三種重要的應用程式類型：</span><span class="sxs-lookup"><span data-stu-id="306c2-139">From a deployment perspective, WPF has three significant application types:</span></span>  
  
- <span data-ttu-id="306c2-140">獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="306c2-140">Standalone applications.</span></span>  
  
- <span data-ttu-id="306c2-141">全標記 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 應用程式。</span><span class="sxs-lookup"><span data-stu-id="306c2-141">Markup-only [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] applications.</span></span>  
  
- <span data-ttu-id="306c2-142">XAML 瀏覽器應用程式 （XBAP）。</span><span class="sxs-lookup"><span data-stu-id="306c2-142">XAML browser applications (XBAPs).</span></span>  
  
<a name="Deploying_Standalone_Applications"></a>
### <a name="deploying-standalone-applications"></a><span data-ttu-id="306c2-143">部署獨立應用程式</span><span class="sxs-lookup"><span data-stu-id="306c2-143">Deploying Standalone Applications</span></span>  
 <span data-ttu-id="306c2-144">使用 ClickOnce 或 Windows 安裝程式部署獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="306c2-144">Standalone applications are deployed using either ClickOnce or Windows Installer.</span></span> <span data-ttu-id="306c2-145">無論使用哪種方式，獨立應用程式都需要完全信任才能執行。</span><span class="sxs-lookup"><span data-stu-id="306c2-145">Either way, standalone applications require full trust to run.</span></span> <span data-ttu-id="306c2-146">完全信任將自動授予使用 Windows 安裝程式部署的獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="306c2-146">Full trust is automatically granted to standalone applications that are deployed using Windows Installer.</span></span> <span data-ttu-id="306c2-147">使用 ClickOnce 部署的獨立應用程式不會自動授予完全信任。</span><span class="sxs-lookup"><span data-stu-id="306c2-147">Standalone applications that are deployed using ClickOnce are not automatically granted full trust.</span></span> <span data-ttu-id="306c2-148">相反，ClickOnce 會顯示使用者在安裝獨立應用程式之前必須接受的安全警告對話方塊。</span><span class="sxs-lookup"><span data-stu-id="306c2-148">Instead, ClickOnce displays a security warning dialog that users must accept before a standalone application is installed.</span></span> <span data-ttu-id="306c2-149">如果接受，則會安裝獨立應用程式並授與完全信任。</span><span class="sxs-lookup"><span data-stu-id="306c2-149">If accepted, the standalone application is installed and granted full trust.</span></span> <span data-ttu-id="306c2-150">如果不接受，則不會安裝獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="306c2-150">If not, the standalone application is not installed.</span></span>  
  
<a name="Deploying_Markup_Only_XAML_Applications"></a>
### <a name="deploying-markup-only-xaml-applications"></a><span data-ttu-id="306c2-151">部署全標記 XAML 應用程式</span><span class="sxs-lookup"><span data-stu-id="306c2-151">Deploying Markup-Only XAML Applications</span></span>  
 <span data-ttu-id="306c2-152">僅[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記頁面通常發佈到 Web 服務器（如 HTML 頁面），並且可以使用 Internet Explorer 查看。</span><span class="sxs-lookup"><span data-stu-id="306c2-152">Markup-only [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pages are usually published to Web servers, like HTML pages, and can be viewed using Internet Explorer.</span></span> <span data-ttu-id="306c2-153">全標記 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面會在部分信任的安全性沙箱內執行，其限制是由網際網路區域權限集合所定義。</span><span class="sxs-lookup"><span data-stu-id="306c2-153">Markup-only [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pages run within a partial-trust security sandbox with restrictions that are defined by the Internet zone permission set.</span></span> <span data-ttu-id="306c2-154">這為基於 HTML 的 Web 應用程式提供了等效的安全沙箱。</span><span class="sxs-lookup"><span data-stu-id="306c2-154">This provides an equivalent security sandbox to HTML-based Web applications.</span></span>  
  
 <span data-ttu-id="306c2-155">有關 WPF 應用程式安全性的詳細資訊，請參閱[安全](../security-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="306c2-155">For more information about security for WPF applications, see [Security](../security-wpf.md).</span></span>  
  
 <span data-ttu-id="306c2-156">通過使用 XCopy[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]或 Windows 安裝程式，只能將標記頁面安裝到本地檔案系統。</span><span class="sxs-lookup"><span data-stu-id="306c2-156">Markup-only [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pages can be installed to the local file system by using either XCopy or Windows Installer.</span></span> <span data-ttu-id="306c2-157">可以使用 Internet 資源管理器或 Windows 資源管理器查看這些頁面。</span><span class="sxs-lookup"><span data-stu-id="306c2-157">These pages can be viewed using Internet Explorer or Windows Explorer.</span></span>  
  
 <span data-ttu-id="306c2-158">如需 XAML 的詳細資訊，請參閱 [XAML 概觀 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="306c2-158">For more information about XAML, see [XAML Overview (WPF)](../../../desktop-wpf/fundamentals/xaml.md).</span></span>  
  
<a name="Deploying_XAML_Browser_Applications"></a>
### <a name="deploying-xaml-browser-applications"></a><span data-ttu-id="306c2-159">部署 XAML 瀏覽器應用程式</span><span class="sxs-lookup"><span data-stu-id="306c2-159">Deploying XAML Browser Applications</span></span>  
 <span data-ttu-id="306c2-160">XBAP 是需要部署以下三個檔的編譯應用程式：</span><span class="sxs-lookup"><span data-stu-id="306c2-160">XBAPs are compiled applications that require the following three files to be deployed:</span></span>  
  
- <span data-ttu-id="306c2-161">*應用程式名稱*.exe：可執行組件應用程式檔案。</span><span class="sxs-lookup"><span data-stu-id="306c2-161">*ApplicationName*.exe: The executable assembly application file.</span></span>  
  
- <span data-ttu-id="306c2-162">*應用程式名稱*.xbap：部署資訊清單。</span><span class="sxs-lookup"><span data-stu-id="306c2-162">*ApplicationName*.xbap: The deployment manifest.</span></span>  
  
- <span data-ttu-id="306c2-163">*應用程式名稱*.exe.manifest：應用程式資訊清單。</span><span class="sxs-lookup"><span data-stu-id="306c2-163">*ApplicationName*.exe.manifest: The application manifest.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="306c2-164">如需部署和應用程式資訊清單的詳細資訊，請參閱[建置 WPF 應用程式](building-a-wpf-application-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="306c2-164">For more information about deployment and application manifests, see [Building a WPF Application](building-a-wpf-application-wpf.md).</span></span>  
  
 <span data-ttu-id="306c2-165">這些檔是在生成 XBAP 時生成的。</span><span class="sxs-lookup"><span data-stu-id="306c2-165">These files are produced when an XBAP is built.</span></span> <span data-ttu-id="306c2-166">如需詳細資訊，請參閱[如何：建立新的 WPF 瀏覽器應用程式專案](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="306c2-166">For more information, see [How to: Create a New WPF Browser Application Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100)).</span></span> <span data-ttu-id="306c2-167">與僅[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記頁面一樣，XBAP 通常發佈到 Web 服務器並使用 Internet 資源管理器進行查看。</span><span class="sxs-lookup"><span data-stu-id="306c2-167">Like markup-only [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pages, XBAPs are typically published to a Web server and viewed using Internet Explorer.</span></span>  
  
 <span data-ttu-id="306c2-168">可以使用任何部署技術將 XBAP 部署到用戶端。</span><span class="sxs-lookup"><span data-stu-id="306c2-168">XBAPs can be deployed to clients using any of the deployment techniques.</span></span> <span data-ttu-id="306c2-169">但是，建議按一下一次，因為它提供以下功能：</span><span class="sxs-lookup"><span data-stu-id="306c2-169">However, ClickOnce is recommended since it provides the following capabilities:</span></span>  
  
1. <span data-ttu-id="306c2-170">在發行新版本時自動更新。</span><span class="sxs-lookup"><span data-stu-id="306c2-170">Automatic updates when a new version is published.</span></span>  
  
2. <span data-ttu-id="306c2-171">完全信任運行的 XBAP 的提升許可權。</span><span class="sxs-lookup"><span data-stu-id="306c2-171">Elevation privileges for the XBAP running with full trust.</span></span>  
  
 <span data-ttu-id="306c2-172">根據預設，ClickOnce 會發行副檔名為 .deploy 的應用程式檔案。</span><span class="sxs-lookup"><span data-stu-id="306c2-172">By default, ClickOnce publishes application files with the .deploy extension.</span></span> <span data-ttu-id="306c2-173">這可能會造成問題，但可予以停用。</span><span class="sxs-lookup"><span data-stu-id="306c2-173">This can be problematic, but can be disabled.</span></span> <span data-ttu-id="306c2-174">如需詳細資訊，請參閱 [ClickOnce 部署中的伺服器和用戶端組態問題](/visualstudio/deployment/server-and-client-configuration-issues-in-clickonce-deployments)。</span><span class="sxs-lookup"><span data-stu-id="306c2-174">For more information, see [Server and Client Configuration Issues in ClickOnce Deployments](/visualstudio/deployment/server-and-client-configuration-issues-in-clickonce-deployments).</span></span>  
  
 <span data-ttu-id="306c2-175">有關部署 XAML 瀏覽器應用程式 （XBAPs） 的詳細資訊，請參閱[WPF XAML 瀏覽器應用程式概述](wpf-xaml-browser-applications-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="306c2-175">For more information about deploying XAML browser applications (XBAPs), see [WPF XAML Browser Applications Overview](wpf-xaml-browser-applications-overview.md).</span></span>  
  
<a name="Installing__NET_Framework_3_0"></a>
## <a name="installing-the-net-framework"></a><span data-ttu-id="306c2-176">安裝.NET Framework</span><span class="sxs-lookup"><span data-stu-id="306c2-176">Installing the .NET Framework</span></span>  
 <span data-ttu-id="306c2-177">要運行 WPF 應用程式，必須在用戶端上安裝 Microsoft .NET 框架。</span><span class="sxs-lookup"><span data-stu-id="306c2-177">To run a WPF application, the Microsoft .NET Framework must be installed on the client.</span></span> <span data-ttu-id="306c2-178">當查看 WPF 瀏覽器託管的應用程式時，Internet Explorer 會自動檢測用戶端是否安裝了 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="306c2-178">Internet Explorer automatically detects whether clients are installed with .NET Framework when WPF browser-hosted applications are viewed.</span></span> <span data-ttu-id="306c2-179">如果未安裝 .NET 框架，Internet Explorer 會提示使用者安裝它。</span><span class="sxs-lookup"><span data-stu-id="306c2-179">If the .NET Framework is not installed, Internet Explorer prompts users to install it.</span></span>  
  
 <span data-ttu-id="306c2-180">為了檢測是否安裝了 .NET 框架，Internet Explorer 包括一個引導應用程式，該應用程式註冊為具有以下副檔名的內容檔的回退多用途 Internet 郵件擴展 （MIME） 處理常式：.xaml、.xps、.xbap和 .應用程式。</span><span class="sxs-lookup"><span data-stu-id="306c2-180">To detect whether the .NET Framework is installed, Internet Explorer includes a bootstrapper application that is registered as the fallback Multipurpose Internet Mail Extensions (MIME) handler for content files with the following extensions: .xaml, .xps, .xbap, and .application.</span></span> <span data-ttu-id="306c2-181">如果導航到這些檔案類型，並且未在用戶端上安裝 .NET Framework，則引導程式應用程式將請求安裝它的許可權。</span><span class="sxs-lookup"><span data-stu-id="306c2-181">If you navigate to these file types and the .NET Framework is not installed on the client, the bootstrapper application requests permission to install it.</span></span> <span data-ttu-id="306c2-182">如果未提供許可權，則既不安裝 .NET 框架，也不會安裝應用程式。</span><span class="sxs-lookup"><span data-stu-id="306c2-182">If permission is not provided, neither the .NET Framework nor the application is installed.</span></span>  
  
 <span data-ttu-id="306c2-183">如果授予許可權，Internet Explorer 將使用 Microsoft 後臺智慧傳輸服務 （BITS） 下載並安裝 .NET 框架。</span><span class="sxs-lookup"><span data-stu-id="306c2-183">If permission is granted, Internet Explorer downloads and installs the .NET Framework using the Microsoft Background Intelligent Transfer Service (BITS).</span></span> <span data-ttu-id="306c2-184">成功安裝 .NET 框架後，在新的瀏覽器視窗中打開最初請求的檔。</span><span class="sxs-lookup"><span data-stu-id="306c2-184">After successful installation of the .NET Framework, the originally requested file is opened in a new browser window.</span></span>  
  
 <span data-ttu-id="306c2-185">如需詳細資訊，請參閱[部署 .NET Framework 和應用程式](../../deployment/index.md)。</span><span class="sxs-lookup"><span data-stu-id="306c2-185">For more information, see [Deploying the .NET Framework and Applications](../../deployment/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="306c2-186">另請參閱</span><span class="sxs-lookup"><span data-stu-id="306c2-186">See also</span></span>

- [<span data-ttu-id="306c2-187">建置 WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="306c2-187">Building a WPF Application</span></span>](building-a-wpf-application-wpf.md)
- [<span data-ttu-id="306c2-188">安全性</span><span class="sxs-lookup"><span data-stu-id="306c2-188">Security</span></span>](../security-wpf.md)
