---
title: 安全性
ms.date: 03/30/2017
helpviewer_keywords:
- XAML files [WPF], sandbox behavior
- browser-hosted application security [WPF]
- application security [WPF]
- navigation security [WPF]
- loose XAML files [WPF], sandbox behavior
- WPF security [WPF]
- WebBrowser control [WPF], security
- feature controls [WPF], security
- XBAP security [WPF]
- Internet Explorer security settings [WPF]
ms.assetid: ee1baea0-3611-4e36-9ad6-fcd5205376fb
ms.openlocfilehash: e0a56dcbf8d151fcb0d4f6271ecba15c0ff955a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174611"
---
# <a name="security-wpf"></a><span data-ttu-id="6ff81-102">安全性 (WPF)</span><span class="sxs-lookup"><span data-stu-id="6ff81-102">Security (WPF)</span></span>
<a name="introduction"></a><span data-ttu-id="6ff81-103">在開發 Windows 演示文稿基礎 （WPF） 獨立和瀏覽器託管的應用程式時，必須考慮安全模型。</span><span class="sxs-lookup"><span data-stu-id="6ff81-103">When developing Windows Presentation Foundation (WPF) standalone and browser-hosted applications, you must consider the security model.</span></span> <span data-ttu-id="6ff81-104">WPF 獨立應用程式以不受限制的許可權（CAS**完全信任**許可權集）執行，無論是使用 Windows 安裝程式 （.msi）、XCopy 還是 ClickOnce 部署。</span><span class="sxs-lookup"><span data-stu-id="6ff81-104">WPF standalone applications execute with unrestricted permissions ( CAS**FullTrust** permission set), whether deployed using Windows Installer (.msi), XCopy, or ClickOnce.</span></span> <span data-ttu-id="6ff81-105">不支援使用 ClickOnce 部署部分信任的獨立 WPF 應用程式。</span><span class="sxs-lookup"><span data-stu-id="6ff81-105">Deploying partial-trust, standalone WPF applications with ClickOnce is unsupported.</span></span> <span data-ttu-id="6ff81-106">但是，完全信任的主機應用程式可以使用 .NET 框架外<xref:System.AppDomain>接程式模型創建部分信任。</span><span class="sxs-lookup"><span data-stu-id="6ff81-106">However, a full-trust host application can create a partial-trust <xref:System.AppDomain> using the .NET Framework Add-in model.</span></span> <span data-ttu-id="6ff81-107">有關詳細資訊，請參閱[WPF 載入項概述](./app-development/wpf-add-ins-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="6ff81-107">For more information, see [WPF Add-Ins Overview](./app-development/wpf-add-ins-overview.md).</span></span>  
  
 <span data-ttu-id="6ff81-108">WPF瀏覽器託管的應用程式由 Windows Internet 資源管理器或 Firefox 託管，可以是 XAML 瀏覽器應用程式 （XBAPs） 或鬆散[!INCLUDE[TLA#tla_xaml](../../../includes/tlasharptla-xaml-md.md)]文檔 有關詳細資訊，請參閱[WPF XAML 瀏覽器應用程式概述](./app-development/wpf-xaml-browser-applications-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="6ff81-108">WPF browser-hosted applications are hosted by Windows Internet Explorer or Firefox, and can be either XAML browser applications (XBAPs) or loose [!INCLUDE[TLA#tla_xaml](../../../includes/tlasharptla-xaml-md.md)] documents For more information, see [WPF XAML Browser Applications Overview](./app-development/wpf-xaml-browser-applications-overview.md).</span></span>  
  
 <span data-ttu-id="6ff81-109">預設情況下，WPF 瀏覽器託管的應用程式在部分信任安全沙箱中執行，該沙箱僅限於預設的 CAS**Internet**區域許可權集。</span><span class="sxs-lookup"><span data-stu-id="6ff81-109">WPF browser-hosted applications execute within a partial trust security sandbox, by default, which is limited to the default CAS**Internet** zone permission set.</span></span> <span data-ttu-id="6ff81-110">這將有效地將 WPF 瀏覽器託管的應用程式與用戶端電腦隔離，就像您希望將典型的 Web 應用程式隔離一樣。</span><span class="sxs-lookup"><span data-stu-id="6ff81-110">This effectively isolates WPF browser-hosted applications from the client computer in the same way that you would expect typical Web applications to be isolated.</span></span> <span data-ttu-id="6ff81-111">XBAP 可以根據部署 URL 的安全性區域以及用戶端的安全性組態來提高權限，而最高為「完全信任」。</span><span class="sxs-lookup"><span data-stu-id="6ff81-111">An XBAP can elevate privileges, up to Full Trust, depending on the security zone of the deployment URL and the client's security configuration.</span></span> <span data-ttu-id="6ff81-112">如需詳細資訊，請參閱 [WPF 部分信任安全性](wpf-partial-trust-security.md)。</span><span class="sxs-lookup"><span data-stu-id="6ff81-112">For more information, see [WPF Partial Trust Security](wpf-partial-trust-security.md).</span></span>  
  
 <span data-ttu-id="6ff81-113">本主題討論 Windows 演示文稿基礎 （WPF） 獨立和瀏覽器託管應用程式的安全模型。</span><span class="sxs-lookup"><span data-stu-id="6ff81-113">This topic discusses the security model for Windows Presentation Foundation (WPF) standalone and browser-hosted applications.</span></span>  
  
 <span data-ttu-id="6ff81-114">本主題包含下列幾節：</span><span class="sxs-lookup"><span data-stu-id="6ff81-114">This topic contains the following sections:</span></span>  
  
- [<span data-ttu-id="6ff81-115">安全巡覽</span><span class="sxs-lookup"><span data-stu-id="6ff81-115">Safe Navigation</span></span>](#SafeTopLevelNavigation)  
  
- [<span data-ttu-id="6ff81-116">Web 瀏覽軟體安全性設定</span><span class="sxs-lookup"><span data-stu-id="6ff81-116">Web Browsing Software Security Settings</span></span>](#InternetExplorerSecuritySettings)  
  
- [<span data-ttu-id="6ff81-117">WebBrowser 控制項和功能控制項</span><span class="sxs-lookup"><span data-stu-id="6ff81-117">WebBrowser Control and Feature Controls</span></span>](#webbrowser_control_and_feature_controls)  
  
- [<span data-ttu-id="6ff81-118">停用部分信任用戶端應用程式的 APTCA 組件</span><span class="sxs-lookup"><span data-stu-id="6ff81-118">Disabling APTCA Assemblies for Partially Trusted Client Applications</span></span>](#APTCA)  
  
- [<span data-ttu-id="6ff81-119">鬆散 XAML 檔案的沙箱行為</span><span class="sxs-lookup"><span data-stu-id="6ff81-119">Sandbox Behavior for Loose XAML Files</span></span>](#LooseContentSandboxing)  
  
- [<span data-ttu-id="6ff81-120">用於開發可提高安全性的 WPF 應用程式的資源</span><span class="sxs-lookup"><span data-stu-id="6ff81-120">Resources for Developing WPF Applications that Promote Security</span></span>](#BestPractices)  
  
<a name="SafeTopLevelNavigation"></a>
## <a name="safe-navigation"></a><span data-ttu-id="6ff81-121">安全巡覽</span><span class="sxs-lookup"><span data-stu-id="6ff81-121">Safe Navigation</span></span>  
 <span data-ttu-id="6ff81-122">對於 XBAP，WPF 區分兩種類型的導航：應用程式和瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="6ff81-122">For XBAPs, WPF distinguishes two types of navigation: application and browser.</span></span>  
  
 <span data-ttu-id="6ff81-123">「應用程式巡覽」\*\* 是瀏覽器所裝載之應用程式的內容項目間的巡覽。</span><span class="sxs-lookup"><span data-stu-id="6ff81-123">*Application navigation* is navigation between items of content within an application that is hosted by a browser.</span></span> <span data-ttu-id="6ff81-124">「瀏覽器巡覽」\*\* 是變更瀏覽器本身的內容和位置 URL 的巡覽。</span><span class="sxs-lookup"><span data-stu-id="6ff81-124">*Browser navigation* is navigation that changes the content and location URL of a browser itself.</span></span> <span data-ttu-id="6ff81-125">應用程式導航（通常為 XAML）和瀏覽器導航（通常 HTML）之間的關係如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="6ff81-125">The relationship between application navigation (typically XAML) and browser navigation (typically HTML) is shown in the following illustration:</span></span>
  
 ![應用程式導航和瀏覽器導航之間的關係。](./media/security-wpf/application-browser-navigation-relationship.png)  
  
 <span data-ttu-id="6ff81-127">XBAP 導航到的內容類型主要取決於是否使用應用程式導航或瀏覽器導航。</span><span class="sxs-lookup"><span data-stu-id="6ff81-127">The type of content that is considered safe for an XBAP to navigate to is primarily determined by whether application navigation or browser navigation is used.</span></span>  
  
<a name="Application_Navigation_Security"></a>
### <a name="application-navigation-security"></a><span data-ttu-id="6ff81-128">應用程式巡覽安全性</span><span class="sxs-lookup"><span data-stu-id="6ff81-128">Application Navigation Security</span></span>  
 <span data-ttu-id="6ff81-129">如果可以使用包 URI 進行標識，則應用程式導航被視為安全，該 URI 支援四種類型的內容：</span><span class="sxs-lookup"><span data-stu-id="6ff81-129">Application navigation is considered safe if it can be identified with a pack URI, which supports four types of content:</span></span>  
  
|<span data-ttu-id="6ff81-130">內容類型</span><span class="sxs-lookup"><span data-stu-id="6ff81-130">Content Type</span></span>|<span data-ttu-id="6ff81-131">描述</span><span class="sxs-lookup"><span data-stu-id="6ff81-131">Description</span></span>|<span data-ttu-id="6ff81-132">URI 範例</span><span class="sxs-lookup"><span data-stu-id="6ff81-132">URI Example</span></span>|  
|------------------|-----------------|-----------------|  
|<span data-ttu-id="6ff81-133">資源</span><span class="sxs-lookup"><span data-stu-id="6ff81-133">Resource</span></span>|<span data-ttu-id="6ff81-134">添加到具有組建類型的**資源**的專案的檔。</span><span class="sxs-lookup"><span data-stu-id="6ff81-134">Files that are added to a project with a build type of **Resource**.</span></span>|`pack://application:,,,/MyResourceFile.xaml`|  
|<span data-ttu-id="6ff81-135">內容</span><span class="sxs-lookup"><span data-stu-id="6ff81-135">Content</span></span>|<span data-ttu-id="6ff81-136">添加到具有生成**類型內容**的專案的檔。</span><span class="sxs-lookup"><span data-stu-id="6ff81-136">Files that are added to a project with a build type of **Content**.</span></span>|`pack://application:,,,/MyContentFile.xaml`|  
|<span data-ttu-id="6ff81-137">Site of origin</span><span class="sxs-lookup"><span data-stu-id="6ff81-137">Site of origin</span></span>|<span data-ttu-id="6ff81-138">添加到組建類型的 **"無"** 的專案的檔。</span><span class="sxs-lookup"><span data-stu-id="6ff81-138">Files that are added to a project with a build type of **None**.</span></span>|`pack://siteoforigin:,,,/MySiteOfOriginFile.xaml`|  
|<span data-ttu-id="6ff81-139">應用程式程式碼</span><span class="sxs-lookup"><span data-stu-id="6ff81-139">Application code</span></span>|<span data-ttu-id="6ff81-140">具有已編譯程式碼後置的 XAML 資源。</span><span class="sxs-lookup"><span data-stu-id="6ff81-140">XAML resources that have a compiled code-behind.</span></span><br /><br /> <span data-ttu-id="6ff81-141">-或-</span><span class="sxs-lookup"><span data-stu-id="6ff81-141">-or-</span></span><br /><br /> <span data-ttu-id="6ff81-142">添加到具有組建類型的**Page**的專案的 XAML 檔。</span><span class="sxs-lookup"><span data-stu-id="6ff81-142">XAML files that are added to a project with a build type of **Page**.</span></span>|<span data-ttu-id="6ff81-143">`pack://application:,,,/MyResourceFile` `.xaml`</span><span class="sxs-lookup"><span data-stu-id="6ff81-143">`pack://application:,,,/MyResourceFile` `.xaml`</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="6ff81-144">有關應用程式資料檔案和打包 URI 的詳細資訊，請參閱[WPF 應用程式資源、內容和資料檔案](./app-development/wpf-application-resource-content-and-data-files.md)。</span><span class="sxs-lookup"><span data-stu-id="6ff81-144">For more information about application data files and pack URIs, see [WPF Application Resource, Content, and Data Files](./app-development/wpf-application-resource-content-and-data-files.md).</span></span>  
  
 <span data-ttu-id="6ff81-145">使用者或透過程式設計方式可以巡覽到這些內容類型的檔案︰</span><span class="sxs-lookup"><span data-stu-id="6ff81-145">Files of these content types can be navigated to by either the user or programmatically:</span></span>  
  
- <span data-ttu-id="6ff81-146">**使用者巡覽**。</span><span class="sxs-lookup"><span data-stu-id="6ff81-146">**User Navigation**.</span></span> <span data-ttu-id="6ff81-147">使用者通過按一下<xref:System.Windows.Documents.Hyperlink>元素進行導航。</span><span class="sxs-lookup"><span data-stu-id="6ff81-147">The user navigates by clicking a <xref:System.Windows.Documents.Hyperlink> element.</span></span>  
  
- <span data-ttu-id="6ff81-148">**程式設計巡覽**。</span><span class="sxs-lookup"><span data-stu-id="6ff81-148">**Programmatic Navigation**.</span></span> <span data-ttu-id="6ff81-149">應用程式導航時不涉及使用者，例如，通過設置<xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="6ff81-149">The application navigates without involving the user, for example, by setting the <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType> property.</span></span>  
  
<a name="Browser_Navigation_Security"></a>
### <a name="browser-navigation-security"></a><span data-ttu-id="6ff81-150">瀏覽器巡覽安全性</span><span class="sxs-lookup"><span data-stu-id="6ff81-150">Browser Navigation Security</span></span>  
 <span data-ttu-id="6ff81-151">只有在下列情況下，才會將瀏覽器巡覽視為安全：</span><span class="sxs-lookup"><span data-stu-id="6ff81-151">Browser navigation is considered safe only under the following conditions:</span></span>  
  
- <span data-ttu-id="6ff81-152">**使用者巡覽**。</span><span class="sxs-lookup"><span data-stu-id="6ff81-152">**User Navigation**.</span></span> <span data-ttu-id="6ff81-153">使用者通過按一下<xref:System.Windows.Documents.Hyperlink>主<xref:System.Windows.Navigation.NavigationWindow>元素中的元素而不是嵌套<xref:System.Windows.Controls.Frame>中進行導航。</span><span class="sxs-lookup"><span data-stu-id="6ff81-153">The user navigates by clicking a <xref:System.Windows.Documents.Hyperlink> element that is within the main <xref:System.Windows.Navigation.NavigationWindow>, not in a nested <xref:System.Windows.Controls.Frame>.</span></span>  
  
- <span data-ttu-id="6ff81-154">**區域**。</span><span class="sxs-lookup"><span data-stu-id="6ff81-154">**Zone**.</span></span> <span data-ttu-id="6ff81-155">所要巡覽的內容位在網際網路或近端內部網路。</span><span class="sxs-lookup"><span data-stu-id="6ff81-155">The content being navigated to is located on the Internet or the local intranet.</span></span>  
  
- <span data-ttu-id="6ff81-156">**通訊協定**。</span><span class="sxs-lookup"><span data-stu-id="6ff81-156">**Protocol**.</span></span> <span data-ttu-id="6ff81-157">**file**正在使用的協定是**http\*\*\*\*HTTP、HTTPs、** 檔或**mailto**。</span><span class="sxs-lookup"><span data-stu-id="6ff81-157">The protocol being used is either **http**, **https**, **file**, or **mailto**.</span></span>  
  
 <span data-ttu-id="6ff81-158">如果 XBAP 嘗試以不符合這些條件的方式導航到內容，則引發 。 <xref:System.Security.SecurityException></span><span class="sxs-lookup"><span data-stu-id="6ff81-158">If an XBAP attempts to navigate to content in a manner that does not comply with these conditions, a <xref:System.Security.SecurityException> is thrown.</span></span>  
  
<a name="InternetExplorerSecuritySettings"></a>
## <a name="web-browsing-software-security-settings"></a><span data-ttu-id="6ff81-159">Web 瀏覽軟體安全性設定</span><span class="sxs-lookup"><span data-stu-id="6ff81-159">Web Browsing Software Security Settings</span></span>  
 <span data-ttu-id="6ff81-160">電腦上的安全性設定決定授與任何 Web 瀏覽軟體的存取權。</span><span class="sxs-lookup"><span data-stu-id="6ff81-160">The security settings on your computer determine the access that any Web browsing software is granted.</span></span> <span data-ttu-id="6ff81-161">Web 流覽套裝軟體括使用[WinINet](/windows/win32/wininet/portal)或[UrlMon](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa767916(v=vs.85)) API 的任何應用程式或元件，包括 Internet 資源管理器和演示Host.exe。</span><span class="sxs-lookup"><span data-stu-id="6ff81-161">Web browsing software includes any application or component that uses the [WinINet](/windows/win32/wininet/portal) or [UrlMon](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa767916(v=vs.85)) APIs, including Internet Explorer and PresentationHost.exe.</span></span>  
  
 <span data-ttu-id="6ff81-162">Internet Explorer 提供了一種機制，通過該機制可以配置允許由 Internet Explorer 執行的功能，包括以下內容：</span><span class="sxs-lookup"><span data-stu-id="6ff81-162">Internet Explorer provides a mechanism by which you can configure the functionality that is allowed to be executed by or from Internet Explorer, including the following:</span></span>  
  
- <span data-ttu-id="6ff81-163">.NET 框架相依元件</span><span class="sxs-lookup"><span data-stu-id="6ff81-163">.NET Framework-reliant components</span></span>  
  
- <span data-ttu-id="6ff81-164">ActiveX 控制項和外掛程式</span><span class="sxs-lookup"><span data-stu-id="6ff81-164">ActiveX controls and plug-ins</span></span>  
  
- <span data-ttu-id="6ff81-165">下載</span><span class="sxs-lookup"><span data-stu-id="6ff81-165">Downloads</span></span>  
  
- <span data-ttu-id="6ff81-166">指令碼</span><span class="sxs-lookup"><span data-stu-id="6ff81-166">Scripting</span></span>  
  
- <span data-ttu-id="6ff81-167">使用者驗證</span><span class="sxs-lookup"><span data-stu-id="6ff81-167">User Authentication</span></span>  
  
 <span data-ttu-id="6ff81-168">以這種方式保護的功能集合按區域配置，用於**Internet、Intranet、\*\*\*\*受信任的網站**和**受限網站**區域。 **Internet**</span><span class="sxs-lookup"><span data-stu-id="6ff81-168">The collection of functionality that can be secured in this way is configured on a per-zone basis for the **Internet**, **Intranet**, **Trusted Sites**, and **Restricted Sites** zones.</span></span> <span data-ttu-id="6ff81-169">下列步驟描述如何設定安全性設定：</span><span class="sxs-lookup"><span data-stu-id="6ff81-169">The following steps describe how to configure your security settings:</span></span>  
  
1. <span data-ttu-id="6ff81-170">開啟 [控制台]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6ff81-170">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="6ff81-171">點擊**網路和互聯網**，然後按一下**互聯網選項**。</span><span class="sxs-lookup"><span data-stu-id="6ff81-171">Click **Network and Internet** and then click **Internet Options**.</span></span>  
  
     <span data-ttu-id="6ff81-172">[網際網路選項] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="6ff81-172">The Internet Options dialog box appears.</span></span>  
  
3. <span data-ttu-id="6ff81-173">在 **"安全"** 選項卡上，選擇要為其配置安全設置的區域。</span><span class="sxs-lookup"><span data-stu-id="6ff81-173">On the **Security** tab, select the zone to configure the security settings for.</span></span>  
  
4. <span data-ttu-id="6ff81-174">按一下 **"自訂級別"** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6ff81-174">Click the **Custom Level** button.</span></span>  
  
     <span data-ttu-id="6ff81-175">將顯示 **"安全設置"** 對話方塊，您可以配置所選區域的安全設置。</span><span class="sxs-lookup"><span data-stu-id="6ff81-175">The **Security Settings** dialog box appears and you can configure the security settings for the selected zone.</span></span>  
  
     ![顯示"安全設置"對話方塊的螢幕截圖。](./media/security-wpf/windows-presentation-foundation-security-settings.png)  
  
> [!NOTE]
> <span data-ttu-id="6ff81-177">您也可以從 Internet Explorer 到達 [網際網路選項] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6ff81-177">You can also get to the Internet Options dialog box from Internet Explorer.</span></span> <span data-ttu-id="6ff81-178">按一下**工具**，然後按一下**互聯網選項**。</span><span class="sxs-lookup"><span data-stu-id="6ff81-178">Click **Tools** and then click **Internet Options**.</span></span>  
  
 <span data-ttu-id="6ff81-179">從 Windows Internet 資源管理器 7 開始，包括針對 .NET 框架的以下安全設置：</span><span class="sxs-lookup"><span data-stu-id="6ff81-179">Starting with Windows Internet Explorer 7, the following security settings specifically for .NET Framework are included:</span></span>  
  
- <span data-ttu-id="6ff81-180">**鬆散 XAML**。</span><span class="sxs-lookup"><span data-stu-id="6ff81-180">**Loose XAML**.</span></span> <span data-ttu-id="6ff81-181">控制 Internet 資源管理器是否可以導航到和[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]鬆散的檔。</span><span class="sxs-lookup"><span data-stu-id="6ff81-181">Controls whether Internet Explorer can navigate to and loose [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] files.</span></span> <span data-ttu-id="6ff81-182">([啟用]、[停用] 和 [提示] 選項)。</span><span class="sxs-lookup"><span data-stu-id="6ff81-182">(Enable, Disable, and Prompt options).</span></span>  
  
- <span data-ttu-id="6ff81-183">**XAML 瀏覽器應用程式**。</span><span class="sxs-lookup"><span data-stu-id="6ff81-183">**XAML browser applications**.</span></span> <span data-ttu-id="6ff81-184">控制 Internet 資源管理器是否可以導航到並運行 XBAP。</span><span class="sxs-lookup"><span data-stu-id="6ff81-184">Controls whether Internet Explorer can navigate to and run XBAPs.</span></span> <span data-ttu-id="6ff81-185">([啟用]、[停用] 和 [提示] 選項)。</span><span class="sxs-lookup"><span data-stu-id="6ff81-185">(Enable, Disable, and Prompt options).</span></span>  
  
 <span data-ttu-id="6ff81-186">預設情況下，這些設置都為**Internet、\*\*\*\*本地 Intranet**和**受信任的網站**區域啟用，並且為**受限網站**區域禁用。</span><span class="sxs-lookup"><span data-stu-id="6ff81-186">By default, these settings are all enabled for the **Internet**, **Local intranet**, and **Trusted sites** zones, and disabled for the **Restricted sites** zone.</span></span>  
  
<a name="Security_Settings_for_IE6_and_Below"></a>
### <a name="security-related-wpf-registry-settings"></a><span data-ttu-id="6ff81-187">安全性相關 WPF 登錄設定</span><span class="sxs-lookup"><span data-stu-id="6ff81-187">Security-related WPF Registry Settings</span></span>  
 <span data-ttu-id="6ff81-188">除了透過 [網際網路選項] 取得的安全性設定之外，還提供下列登錄值可選擇性地封鎖許多有安全性顧慮的 WPF 功能。</span><span class="sxs-lookup"><span data-stu-id="6ff81-188">In addition to the security settings available through the Internet Options, the following registry values are available for selectively blocking a number of security-sensitive WPF features.</span></span> <span data-ttu-id="6ff81-189">值會定義在下列機碼下方︰</span><span class="sxs-lookup"><span data-stu-id="6ff81-189">The values are defined under the following key:</span></span>  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\Windows Presentation Foundation\Features`  
  
 <span data-ttu-id="6ff81-190">下表列出可設定的值。</span><span class="sxs-lookup"><span data-stu-id="6ff81-190">The following table lists the values that can be set.</span></span>  
  
|<span data-ttu-id="6ff81-191">值名稱</span><span class="sxs-lookup"><span data-stu-id="6ff81-191">Value Name</span></span>|<span data-ttu-id="6ff81-192">值類型</span><span class="sxs-lookup"><span data-stu-id="6ff81-192">Value Type</span></span>|<span data-ttu-id="6ff81-193">數值資料</span><span class="sxs-lookup"><span data-stu-id="6ff81-193">Value Data</span></span>|  
|----------------|----------------|----------------|  
|<span data-ttu-id="6ff81-194">XBAPDisallow</span><span class="sxs-lookup"><span data-stu-id="6ff81-194">XBAPDisallow</span></span>|<span data-ttu-id="6ff81-195">REG_DWORD</span><span class="sxs-lookup"><span data-stu-id="6ff81-195">REG_DWORD</span></span>|<span data-ttu-id="6ff81-196">1 表示不允許；0 表示允許。</span><span class="sxs-lookup"><span data-stu-id="6ff81-196">1 to disallow; 0 to allow.</span></span>|  
|<span data-ttu-id="6ff81-197">LooseXamlDisallow</span><span class="sxs-lookup"><span data-stu-id="6ff81-197">LooseXamlDisallow</span></span>|<span data-ttu-id="6ff81-198">REG_DWORD</span><span class="sxs-lookup"><span data-stu-id="6ff81-198">REG_DWORD</span></span>|<span data-ttu-id="6ff81-199">1 表示不允許；0 表示允許。</span><span class="sxs-lookup"><span data-stu-id="6ff81-199">1 to disallow; 0 to allow.</span></span>|  
|<span data-ttu-id="6ff81-200">WebBrowserDisallow</span><span class="sxs-lookup"><span data-stu-id="6ff81-200">WebBrowserDisallow</span></span>|<span data-ttu-id="6ff81-201">REG_DWORD</span><span class="sxs-lookup"><span data-stu-id="6ff81-201">REG_DWORD</span></span>|<span data-ttu-id="6ff81-202">1 表示不允許；0 表示允許。</span><span class="sxs-lookup"><span data-stu-id="6ff81-202">1 to disallow; 0 to allow.</span></span>|  
|<span data-ttu-id="6ff81-203">MediaAudioDisallow</span><span class="sxs-lookup"><span data-stu-id="6ff81-203">MediaAudioDisallow</span></span>|<span data-ttu-id="6ff81-204">REG_DWORD</span><span class="sxs-lookup"><span data-stu-id="6ff81-204">REG_DWORD</span></span>|<span data-ttu-id="6ff81-205">1 表示不允許；0 表示允許。</span><span class="sxs-lookup"><span data-stu-id="6ff81-205">1 to disallow; 0 to allow.</span></span>|  
|<span data-ttu-id="6ff81-206">MediaImageDisallow</span><span class="sxs-lookup"><span data-stu-id="6ff81-206">MediaImageDisallow</span></span>|<span data-ttu-id="6ff81-207">REG_DWORD</span><span class="sxs-lookup"><span data-stu-id="6ff81-207">REG_DWORD</span></span>|<span data-ttu-id="6ff81-208">1 表示不允許；0 表示允許。</span><span class="sxs-lookup"><span data-stu-id="6ff81-208">1 to disallow; 0 to allow.</span></span>|  
|<span data-ttu-id="6ff81-209">MediaVideoDisallow</span><span class="sxs-lookup"><span data-stu-id="6ff81-209">MediaVideoDisallow</span></span>|<span data-ttu-id="6ff81-210">REG_DWORD</span><span class="sxs-lookup"><span data-stu-id="6ff81-210">REG_DWORD</span></span>|<span data-ttu-id="6ff81-211">1 表示不允許；0 表示允許。</span><span class="sxs-lookup"><span data-stu-id="6ff81-211">1 to disallow; 0 to allow.</span></span>|  
|<span data-ttu-id="6ff81-212">ScriptInteropDisallow</span><span class="sxs-lookup"><span data-stu-id="6ff81-212">ScriptInteropDisallow</span></span>|<span data-ttu-id="6ff81-213">REG_DWORD</span><span class="sxs-lookup"><span data-stu-id="6ff81-213">REG_DWORD</span></span>|<span data-ttu-id="6ff81-214">1 表示不允許；0 表示允許。</span><span class="sxs-lookup"><span data-stu-id="6ff81-214">1 to disallow; 0 to allow.</span></span>|  
  
<a name="webbrowser_control_and_feature_controls"></a>
## <a name="webbrowser-control-and-feature-controls"></a><span data-ttu-id="6ff81-215">WebBrowser 控制項和功能控制項</span><span class="sxs-lookup"><span data-stu-id="6ff81-215">WebBrowser Control and Feature Controls</span></span>  
 <span data-ttu-id="6ff81-216">WPF<xref:System.Windows.Controls.WebBrowser>控制項可用於託管 Web 內容。</span><span class="sxs-lookup"><span data-stu-id="6ff81-216">The WPF <xref:System.Windows.Controls.WebBrowser> control can be used to host Web content.</span></span> <span data-ttu-id="6ff81-217">WPF<xref:System.Windows.Controls.WebBrowser>控制項包裝基礎 Web 瀏覽器 ActiveX 控制項。</span><span class="sxs-lookup"><span data-stu-id="6ff81-217">The WPF <xref:System.Windows.Controls.WebBrowser> control wraps the underlying WebBrowser ActiveX control.</span></span> <span data-ttu-id="6ff81-218">當您使用 WPF<xref:System.Windows.Controls.WebBrowser>控制項託管不受信任的 Web 內容時，WPF 為保護應用程式提供了一些支援。</span><span class="sxs-lookup"><span data-stu-id="6ff81-218">WPF provides some support for securing your application when you use the WPF <xref:System.Windows.Controls.WebBrowser> control to host untrusted Web content.</span></span> <span data-ttu-id="6ff81-219">但是，某些安全功能必須由使用控制項<xref:System.Windows.Controls.WebBrowser>的應用程式直接應用。</span><span class="sxs-lookup"><span data-stu-id="6ff81-219">However, some security features must be applied directly by the applications using the <xref:System.Windows.Controls.WebBrowser> control.</span></span> <span data-ttu-id="6ff81-220">有關 Web 瀏覽器 ActiveX 控制項的詳細資訊，請參閱[Web 瀏覽器控制項概述和教程](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752041(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="6ff81-220">For more information about the WebBrowser ActiveX control, see [WebBrowser Control Overviews and Tutorials](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752041(v=vs.85)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6ff81-221">本節也適用于控制項，<xref:System.Windows.Controls.Frame>因為它使用<xref:System.Windows.Controls.WebBrowser>導航到 HTML 內容。</span><span class="sxs-lookup"><span data-stu-id="6ff81-221">This section also applies to the <xref:System.Windows.Controls.Frame> control since it uses the <xref:System.Windows.Controls.WebBrowser> to navigate to HTML content.</span></span>  
  
 <span data-ttu-id="6ff81-222">如果 WPF<xref:System.Windows.Controls.WebBrowser>控制項用於託管不受信任的 Web 內容，則應用程式應使用部分信任<xref:System.AppDomain>來説明將應用程式代碼與潛在的惡意 HTML 腳本代碼隔離。</span><span class="sxs-lookup"><span data-stu-id="6ff81-222">If the WPF <xref:System.Windows.Controls.WebBrowser> control is used to host untrusted Web content, your application should use a partial-trust <xref:System.AppDomain> to help insulate your application code from potentially malicious HTML script code.</span></span> <span data-ttu-id="6ff81-223">如果應用程式使用<xref:System.Windows.Controls.WebBrowser.InvokeScript%2A>方法和<xref:System.Windows.Controls.WebBrowser.ObjectForScripting%2A>屬性與託管腳本交互，則尤其如此。</span><span class="sxs-lookup"><span data-stu-id="6ff81-223">This is especially true if your application is interacting with the hosted script by using the <xref:System.Windows.Controls.WebBrowser.InvokeScript%2A> method and the <xref:System.Windows.Controls.WebBrowser.ObjectForScripting%2A> property.</span></span> <span data-ttu-id="6ff81-224">有關詳細資訊，請參閱[WPF 載入項概述](./app-development/wpf-add-ins-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="6ff81-224">For more information, see [WPF Add-Ins Overview](./app-development/wpf-add-ins-overview.md).</span></span>  
  
 <span data-ttu-id="6ff81-225">如果應用程式使用 WPF<xref:System.Windows.Controls.WebBrowser>控制項，則提高安全性和緩解攻擊的另一種方法是啟用 Internet Explorer 功能控制項。</span><span class="sxs-lookup"><span data-stu-id="6ff81-225">If your application uses the WPF <xref:System.Windows.Controls.WebBrowser> control, another way to increase security and mitigate attacks is to enable Internet Explorer feature controls.</span></span> <span data-ttu-id="6ff81-226">功能控制項是 Internet 資源管理器的補充，允許管理員和開發人員配置 Internet Explorer 的功能以及承載 WebBrowser ActiveX 控制項的應用程式，WPF<xref:System.Windows.Controls.WebBrowser>控制項將該控制項包裝。</span><span class="sxs-lookup"><span data-stu-id="6ff81-226">Feature controls are additions to Internet Explorer that allow administrators and developers to configure features of Internet Explorer and applications that host the WebBrowser ActiveX control, which the WPF <xref:System.Windows.Controls.WebBrowser> control wraps.</span></span> <span data-ttu-id="6ff81-227">可以使用[CoInternetSetFeature 啟用功能](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537168(v=vs.85))或更改註冊表中的值來配置功能控制項。</span><span class="sxs-lookup"><span data-stu-id="6ff81-227">Feature controls can be configured by using the [CoInternetSetFeatureEnabled](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537168(v=vs.85)) function or by changing values in the registry.</span></span> <span data-ttu-id="6ff81-228">有關功能控制項的詳細資訊，請參閱[功能控制和](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537184(v=vs.85)) [Internet 功能控制項](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/general-info/ee330720(v=vs.85))簡介。</span><span class="sxs-lookup"><span data-stu-id="6ff81-228">For more information about feature controls, see [Introduction to Feature Controls](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537184(v=vs.85)) and [Internet Feature Controls](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/general-info/ee330720(v=vs.85)).</span></span>  
  
 <span data-ttu-id="6ff81-229">如果您正在開發使用 WPF 控制項的獨立 WPF<xref:System.Windows.Controls.WebBrowser>應用程式，WPF 會自動為應用程式啟用以下功能控制項。</span><span class="sxs-lookup"><span data-stu-id="6ff81-229">If you are developing a standalone WPF application that uses the WPF <xref:System.Windows.Controls.WebBrowser> control, WPF automatically enables the following feature controls for your application.</span></span>  
  
|<span data-ttu-id="6ff81-230">功能控制項</span><span class="sxs-lookup"><span data-stu-id="6ff81-230">Feature Control</span></span>|  
|---------------------|  
|<span data-ttu-id="6ff81-231">FEATURE_MIME_HANDLING</span><span class="sxs-lookup"><span data-stu-id="6ff81-231">FEATURE_MIME_HANDLING</span></span>|  
|<span data-ttu-id="6ff81-232">FEATURE_MIME_SNIFFING</span><span class="sxs-lookup"><span data-stu-id="6ff81-232">FEATURE_MIME_SNIFFING</span></span>|  
|<span data-ttu-id="6ff81-233">FEATURE_OBJECT_CACHING</span><span class="sxs-lookup"><span data-stu-id="6ff81-233">FEATURE_OBJECT_CACHING</span></span>|  
|<span data-ttu-id="6ff81-234">FEATURE_SAFE_BINDTOOBJECT</span><span class="sxs-lookup"><span data-stu-id="6ff81-234">FEATURE_SAFE_BINDTOOBJECT</span></span>|  
|<span data-ttu-id="6ff81-235">FEATURE_WINDOW_RESTRICTIONS</span><span class="sxs-lookup"><span data-stu-id="6ff81-235">FEATURE_WINDOW_RESTRICTIONS</span></span>|  
|<span data-ttu-id="6ff81-236">FEATURE_ZONE_ELEVATION</span><span class="sxs-lookup"><span data-stu-id="6ff81-236">FEATURE_ZONE_ELEVATION</span></span>|  
|<span data-ttu-id="6ff81-237">FEATURE_RESTRICT_FILEDOWNLOAD</span><span class="sxs-lookup"><span data-stu-id="6ff81-237">FEATURE_RESTRICT_FILEDOWNLOAD</span></span>|  
|<span data-ttu-id="6ff81-238">FEATURE_RESTRICT_ACTIVEXINSTALL</span><span class="sxs-lookup"><span data-stu-id="6ff81-238">FEATURE_RESTRICT_ACTIVEXINSTALL</span></span>|  
|<span data-ttu-id="6ff81-239">FEATURE_ADDON_MANAGEMENT</span><span class="sxs-lookup"><span data-stu-id="6ff81-239">FEATURE_ADDON_MANAGEMENT</span></span>|  
|<span data-ttu-id="6ff81-240">FEATURE_HTTP_USERNAME_PASSWORD_DISABLE</span><span class="sxs-lookup"><span data-stu-id="6ff81-240">FEATURE_HTTP_USERNAME_PASSWORD_DISABLE</span></span>|  
|<span data-ttu-id="6ff81-241">FEATURE_SECURITYBAND</span><span class="sxs-lookup"><span data-stu-id="6ff81-241">FEATURE_SECURITYBAND</span></span>|  
|<span data-ttu-id="6ff81-242">FEATURE_UNC_SAVEDFILECHECK</span><span class="sxs-lookup"><span data-stu-id="6ff81-242">FEATURE_UNC_SAVEDFILECHECK</span></span>|  
|<span data-ttu-id="6ff81-243">FEATURE_VALIDATE_NAVIGATE_URL</span><span class="sxs-lookup"><span data-stu-id="6ff81-243">FEATURE_VALIDATE_NAVIGATE_URL</span></span>|  
|<span data-ttu-id="6ff81-244">FEATURE_DISABLE_TELNET_PROTOCOL</span><span class="sxs-lookup"><span data-stu-id="6ff81-244">FEATURE_DISABLE_TELNET_PROTOCOL</span></span>|  
|<span data-ttu-id="6ff81-245">FEATURE_WEBOC_POPUPMANAGEMENT</span><span class="sxs-lookup"><span data-stu-id="6ff81-245">FEATURE_WEBOC_POPUPMANAGEMENT</span></span>|  
|<span data-ttu-id="6ff81-246">FEATURE_DISABLE_LEGACY_COMPRESSION</span><span class="sxs-lookup"><span data-stu-id="6ff81-246">FEATURE_DISABLE_LEGACY_COMPRESSION</span></span>|  
|<span data-ttu-id="6ff81-247">FEATURE_SSLUX</span><span class="sxs-lookup"><span data-stu-id="6ff81-247">FEATURE_SSLUX</span></span>|  
  
 <span data-ttu-id="6ff81-248">因為會無條件地啟用這些功能控制項，所以它們可能會損害完全信任應用程式。</span><span class="sxs-lookup"><span data-stu-id="6ff81-248">Since these feature controls are enabled unconditionally, a full-trust application might be impaired by them.</span></span> <span data-ttu-id="6ff81-249">在此情況下，如果特定應用程式和其所裝載的內容沒有安全性風險，則可以停用對應的功能控制項。</span><span class="sxs-lookup"><span data-stu-id="6ff81-249">In this case, if there is no security risk for the specific application and the content it is hosting, the corresponding feature control can be disabled.</span></span>  
  
 <span data-ttu-id="6ff81-250">功能控制項由具現化 Web 瀏覽器 ActiveX 物件的過程應用。</span><span class="sxs-lookup"><span data-stu-id="6ff81-250">Feature controls are applied by the process instantiating the WebBrowser ActiveX object.</span></span> <span data-ttu-id="6ff81-251">因此，如果您要建立的獨立應用程式會巡覽到不受信任的內容，則應該認真考慮啟用其他功能控制項。</span><span class="sxs-lookup"><span data-stu-id="6ff81-251">Therefore, if you are creating a stand-alone application that can navigate to untrusted content, you should seriously consider enabling additional feature controls.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6ff81-252">這項建議根據 MSHTML 和 SHDOCVW 主機安全性的一般建議。</span><span class="sxs-lookup"><span data-stu-id="6ff81-252">This recommendation is based on general recommendations for MSHTML and SHDOCVW host security.</span></span> <span data-ttu-id="6ff81-253">有關詳細資訊，請參閱[MSHTML 主機安全常見問題解答：II 部分 I](https://msrc-blog.microsoft.com/2009/04/02/the-mshtml-host-security-faq-part-i-of-ii/)和[MSHTML 主機安全常見問題解答：II 的第二部分](https://msrc-blog.microsoft.com/2009/04/03/the-mshtml-host-security-faq-part-ii-of-ii/)。</span><span class="sxs-lookup"><span data-stu-id="6ff81-253">For more information, see [The MSHTML Host Security FAQ: Part I of II](https://msrc-blog.microsoft.com/2009/04/02/the-mshtml-host-security-faq-part-i-of-ii/) and [The MSHTML Host Security FAQ: Part II of II](https://msrc-blog.microsoft.com/2009/04/03/the-mshtml-host-security-faq-part-ii-of-ii/).</span></span>  
  
 <span data-ttu-id="6ff81-254">針對可執行檔，請考慮將登錄值設定為 1 來啟用下列功能控制項。</span><span class="sxs-lookup"><span data-stu-id="6ff81-254">For your executable, consider enabling the following feature controls by setting the registry value to 1.</span></span>  
  
|<span data-ttu-id="6ff81-255">功能控制項</span><span class="sxs-lookup"><span data-stu-id="6ff81-255">Feature Control</span></span>|  
|---------------------|  
|<span data-ttu-id="6ff81-256">FEATURE_ACTIVEX_REPURPOSEDETECTION</span><span class="sxs-lookup"><span data-stu-id="6ff81-256">FEATURE_ACTIVEX_REPURPOSEDETECTION</span></span>|  
|<span data-ttu-id="6ff81-257">FEATURE_BLOCK_LMZ_IMG</span><span class="sxs-lookup"><span data-stu-id="6ff81-257">FEATURE_BLOCK_LMZ_IMG</span></span>|  
|<span data-ttu-id="6ff81-258">FEATURE_BLOCK_LMZ_OBJECT</span><span class="sxs-lookup"><span data-stu-id="6ff81-258">FEATURE_BLOCK_LMZ_OBJECT</span></span>|  
|<span data-ttu-id="6ff81-259">FEATURE_BLOCK_LMZ_SCRIPT</span><span class="sxs-lookup"><span data-stu-id="6ff81-259">FEATURE_BLOCK_LMZ_SCRIPT</span></span>|  
|<span data-ttu-id="6ff81-260">FEATURE_RESTRICT_RES_TO_LMZ</span><span class="sxs-lookup"><span data-stu-id="6ff81-260">FEATURE_RESTRICT_RES_TO_LMZ</span></span>|  
|<span data-ttu-id="6ff81-261">FEATURE_RESTRICT_ABOUT_PROTOCOL_IE7</span><span class="sxs-lookup"><span data-stu-id="6ff81-261">FEATURE_RESTRICT_ABOUT_PROTOCOL_IE7</span></span>|  
|<span data-ttu-id="6ff81-262">FEATURE_SHOW_APP_PROTOCOL_WARN_DIALOG</span><span class="sxs-lookup"><span data-stu-id="6ff81-262">FEATURE_SHOW_APP_PROTOCOL_WARN_DIALOG</span></span>|  
|<span data-ttu-id="6ff81-263">FEATURE_LOCALMACHINE_LOCKDOWN</span><span class="sxs-lookup"><span data-stu-id="6ff81-263">FEATURE_LOCALMACHINE_LOCKDOWN</span></span>|  
|<span data-ttu-id="6ff81-264">FEATURE_FORCE_ADDR_AND_STATUS</span><span class="sxs-lookup"><span data-stu-id="6ff81-264">FEATURE_FORCE_ADDR_AND_STATUS</span></span>|  
|<span data-ttu-id="6ff81-265">FEATURE_RESTRICTED_ZONE_WHEN_FILE_NOT_FOUND</span><span class="sxs-lookup"><span data-stu-id="6ff81-265">FEATURE_RESTRICTED_ZONE_WHEN_FILE_NOT_FOUND</span></span>|  
  
 <span data-ttu-id="6ff81-266">針對可執行檔，請考慮將登錄值設定為 0 來停用下列功能控制項。</span><span class="sxs-lookup"><span data-stu-id="6ff81-266">For your executable, consider disabling the following feature control by setting the registry value to 0.</span></span>  
  
|<span data-ttu-id="6ff81-267">功能控制項</span><span class="sxs-lookup"><span data-stu-id="6ff81-267">Feature Control</span></span>|  
|---------------------|  
|<span data-ttu-id="6ff81-268">FEATURE_ENABLE_SCRIPT_PASTE_URLACTION_IF_PROMPT</span><span class="sxs-lookup"><span data-stu-id="6ff81-268">FEATURE_ENABLE_SCRIPT_PASTE_URLACTION_IF_PROMPT</span></span>|  
  
 <span data-ttu-id="6ff81-269">如果運行部分信任的 XAML 瀏覽器應用程式 （XBAP），該應用程式在<xref:System.Windows.Controls.WebBrowser>Windows Internet 資源管理器中包含 WPF 控制項，則 WPF 在 Internet 資源管理器進程的位址空間中託管 Web 瀏覽器 ActiveX 控制項。</span><span class="sxs-lookup"><span data-stu-id="6ff81-269">If you run a partial-trust XAML browser application (XBAP) that includes a WPF <xref:System.Windows.Controls.WebBrowser> control in Windows Internet Explorer, WPF hosts the WebBrowser ActiveX control in the address space of the Internet Explorer process.</span></span> <span data-ttu-id="6ff81-270">由於 Web 瀏覽器 ActiveX 控制項託管在 Internet 資源管理器過程中，因此 Internet Explorer 的所有功能控制項也已為 Web 瀏覽器 ActiveX 控制項啟用。</span><span class="sxs-lookup"><span data-stu-id="6ff81-270">Since the WebBrowser ActiveX control is hosted in the Internet Explorer process, all of the feature controls for Internet Explorer are also enabled for the WebBrowser ActiveX control.</span></span>  
  
 <span data-ttu-id="6ff81-271">與一般獨立應用程式相較之下，在 Internet Explorer 中執行的 XBAP 也會取得額外層級的安全性。</span><span class="sxs-lookup"><span data-stu-id="6ff81-271">XBAPs running in Internet Explorer also get an additional level of security compared to normal standalone applications.</span></span> <span data-ttu-id="6ff81-272">這種額外的安全性是因為 Internet 資源管理器（因此是 Web 瀏覽器 ActiveX 控制項）預設在 Windows Vista 和 Windows 7 上以受保護模式運行。</span><span class="sxs-lookup"><span data-stu-id="6ff81-272">This additional security is because Internet Explorer, and therefore the WebBrowser ActiveX control, runs in protected mode by default on Windows Vista and Windows 7.</span></span> <span data-ttu-id="6ff81-273">有關受保護模式的詳細資訊，請參閱[在受保護模式下瞭解和工作 Internet 資源管理器](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/)。</span><span class="sxs-lookup"><span data-stu-id="6ff81-273">For more information about protected mode, see [Understanding and Working in Protected Mode Internet Explorer](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6ff81-274">如果您嘗試運行一個 XBAP，該 XBAP 在 Firefox 中包含<xref:System.Windows.Controls.WebBrowser>WPF<xref:System.Security.SecurityException>控制項，而在 Internet 區域中，將引發 。</span><span class="sxs-lookup"><span data-stu-id="6ff81-274">If you try to run an XBAP that includes a WPF <xref:System.Windows.Controls.WebBrowser> control in Firefox, while in the Internet zone, a <xref:System.Security.SecurityException> will be thrown.</span></span> <span data-ttu-id="6ff81-275">這是因為 WPF 安全性原則。</span><span class="sxs-lookup"><span data-stu-id="6ff81-275">This is due to WPF security policy.</span></span>  
  
<a name="APTCA"></a>
## <a name="disabling-aptca-assemblies-for-partially-trusted-client-applications"></a><span data-ttu-id="6ff81-276">停用部分信任用戶端應用程式的 APTCA 組件</span><span class="sxs-lookup"><span data-stu-id="6ff81-276">Disabling APTCA Assemblies for Partially Trusted Client Applications</span></span>  
 <span data-ttu-id="6ff81-277">當託管程式集安裝到全域組件快取 （GAC） 中時，它們將完全受信任，因為使用者必須提供明確權限才能安裝它們。</span><span class="sxs-lookup"><span data-stu-id="6ff81-277">When managed assemblies are installed into the global assembly cache (GAC), they become fully trusted because the user must provide explicit permission to install them.</span></span> <span data-ttu-id="6ff81-278">因為它們完全受信任，所以只有完全受信任的受管理用戶端應用程式才能使用它們。</span><span class="sxs-lookup"><span data-stu-id="6ff81-278">Because they are fully trusted, only fully trusted managed client applications can use them.</span></span> <span data-ttu-id="6ff81-279">要允許部分受信任的應用程式使用它們，必須用<xref:System.Security.AllowPartiallyTrustedCallersAttribute>（APTCA） 標記它們。</span><span class="sxs-lookup"><span data-stu-id="6ff81-279">To allow partially trusted applications to use them, they must be marked with the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA).</span></span> <span data-ttu-id="6ff81-280">只有經過測試可在部分信任中安全執行的組件才應該標記這個屬性。</span><span class="sxs-lookup"><span data-stu-id="6ff81-280">Only assemblies that have been tested to be safe for execution in partial trust should be marked with this attribute.</span></span>  
  
 <span data-ttu-id="6ff81-281">但是，APTCA 程式集在安裝到 GAC 後可能會表現出安全性漏洞。</span><span class="sxs-lookup"><span data-stu-id="6ff81-281">However, it is possible for an APTCA assembly to exhibit a security flaw after being installed into the  GAC .</span></span> <span data-ttu-id="6ff81-282">發現安全性缺陷之後，組件發行者可以產生安全性更新來修正現有安裝上的問題，以及防止在發現問題之後可能進行的安裝。</span><span class="sxs-lookup"><span data-stu-id="6ff81-282">Once a security flaw is discovered, assembly publishers can produce a security update to fix the problem on existing installations, and to protect against installations that may occur after the problem is discovered.</span></span> <span data-ttu-id="6ff81-283">雖然解除安裝組件可能會中斷其他使用組件的完全信任用戶端應用程式，但是更新的其中一個選項是解除安裝組件。</span><span class="sxs-lookup"><span data-stu-id="6ff81-283">One option for the update is to uninstall the assembly, although that may break other fully trusted client applications that use the assembly.</span></span>  
  
 <span data-ttu-id="6ff81-284">WPF 提供了一種機制，通過該機制，無需卸載 APTCA 程式集，即可禁用 APTCA 程式集，以用於部分受信任的 XBAPs。</span><span class="sxs-lookup"><span data-stu-id="6ff81-284">WPF provides a mechanism by which an APTCA assembly can be disabled for partially trusted XBAPs without uninstalling the APTCA assembly.</span></span>  
  
 <span data-ttu-id="6ff81-285">若要停用 APTCA 組件，您必須建立特殊登錄機碼︰</span><span class="sxs-lookup"><span data-stu-id="6ff81-285">To disable an APTCA assembly, you have to create a special registry key:</span></span>  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\<AssemblyFullName>, FileVersion=<AssemblyFileVersion>`  
  
 <span data-ttu-id="6ff81-286">下列示範範例：</span><span class="sxs-lookup"><span data-stu-id="6ff81-286">The following shows an example:</span></span>  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\aptcagac, Version=1.0.0.0, Culture=neutral, PublicKeyToken=215e3ac809a0fea7, FileVersion=1.0.0.0`  
  
 <span data-ttu-id="6ff81-287">此機碼會為 APTCA 組件建立一個項目。</span><span class="sxs-lookup"><span data-stu-id="6ff81-287">This key establishes an entry for the APTCA assembly.</span></span> <span data-ttu-id="6ff81-288">您也必須在這個機碼中建立啟用或停用組件的數值。</span><span class="sxs-lookup"><span data-stu-id="6ff81-288">You also have to create a value in this key that enables or disables the assembly.</span></span> <span data-ttu-id="6ff81-289">數值的詳細資料如下︰</span><span class="sxs-lookup"><span data-stu-id="6ff81-289">The following are the details of the value:</span></span>  
  
- <span data-ttu-id="6ff81-290">值名稱 **：APTCA_FLAG**。</span><span class="sxs-lookup"><span data-stu-id="6ff81-290">Value Name: **APTCA_FLAG**.</span></span>  
  
- <span data-ttu-id="6ff81-291">數值型別 **：REG_DWORD**。</span><span class="sxs-lookup"><span data-stu-id="6ff81-291">Value Type: **REG_DWORD**.</span></span>  
  
- <span data-ttu-id="6ff81-292">值資料 **：1**個要禁用;**0**啟用。</span><span class="sxs-lookup"><span data-stu-id="6ff81-292">Value Data: **1** to disable; **0** to enable.</span></span>  
  
 <span data-ttu-id="6ff81-293">如果必須停用部分信任用戶端應用程式的組件，您可以撰寫可建立登錄機碼和值的更新。</span><span class="sxs-lookup"><span data-stu-id="6ff81-293">If an assembly has to be disabled for partially trusted client applications, you can write an update that creates the registry key and value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6ff81-294">Core .NET 框架程式集不會以這種方式禁用它們，因為它們是託管應用程式運行所必需的。</span><span class="sxs-lookup"><span data-stu-id="6ff81-294">Core .NET Framework assemblies are not affected by disabling them in this way because they are required for managed applications to run.</span></span> <span data-ttu-id="6ff81-295">停用 APTCA 組件的支援主要是針對協力廠商應用程式。</span><span class="sxs-lookup"><span data-stu-id="6ff81-295">Support for disabling APTCA assemblies is primarily targeted to third-party applications.</span></span>  
  
<a name="LooseContentSandboxing"></a>
## <a name="sandbox-behavior-for-loose-xaml-files"></a><span data-ttu-id="6ff81-296">鬆散 XAML 檔案的沙箱行為</span><span class="sxs-lookup"><span data-stu-id="6ff81-296">Sandbox Behavior for Loose XAML Files</span></span>  
 <span data-ttu-id="6ff81-297">鬆散[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]檔是僅標記的 XAML 檔，不依賴于任何代碼備份、事件處理常式或特定于應用程式的程式集。</span><span class="sxs-lookup"><span data-stu-id="6ff81-297">Loose [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] files are markup-only XAML files that do not depend on any code-behind, event handler, or application-specific assembly.</span></span> <span data-ttu-id="6ff81-298">當鬆散[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]檔直接從瀏覽器導航到時，它們將基於預設 Internet 區域許可權集載入到安全沙箱中。</span><span class="sxs-lookup"><span data-stu-id="6ff81-298">When loose [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] files are navigated to directly from the browser, they are loaded in a security sandbox based on the default Internet zone permission set.</span></span>  
  
 <span data-ttu-id="6ff81-299">但是，當鬆散[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]檔從 或<xref:System.Windows.Navigation.NavigationWindow>在獨立應用程式中導航到時<xref:System.Windows.Controls.Frame>，安全行為會有所不同。</span><span class="sxs-lookup"><span data-stu-id="6ff81-299">However, the security behavior is different when loose [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] files are navigated to from either a <xref:System.Windows.Navigation.NavigationWindow> or <xref:System.Windows.Controls.Frame> in a standalone application.</span></span>  
  
 <span data-ttu-id="6ff81-300">在這兩種情況下，導航以[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]繼承其主機應用程式許可權的鬆散檔。</span><span class="sxs-lookup"><span data-stu-id="6ff81-300">In both cases, the loose [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] file that is navigated to inherits the permissions of its host application.</span></span> <span data-ttu-id="6ff81-301">但是，從安全形度來看，此行為可能是不可取的，尤其是在由不[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]受信任的實體或未知實體生成的鬆散檔的情況下。</span><span class="sxs-lookup"><span data-stu-id="6ff81-301">However, this behavior may be undesirable from a security perspective, particularly if a loose [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] file was produced by an entity that is either not trusted or unknown.</span></span> <span data-ttu-id="6ff81-302">這種類型的內容稱為*外部內容*，<xref:System.Windows.Controls.Frame>並且<xref:System.Windows.Navigation.NavigationWindow>可以配置為在導航到時將其隔離。</span><span class="sxs-lookup"><span data-stu-id="6ff81-302">This type of content is known as *external content*, and both <xref:System.Windows.Controls.Frame> and <xref:System.Windows.Navigation.NavigationWindow> can be configured to isolate it when navigated to.</span></span> <span data-ttu-id="6ff81-303">通過將**沙箱外部內容**屬性設置為 true 來實現隔離，如 以下示例<xref:System.Windows.Controls.Frame>所示， <xref:System.Windows.Navigation.NavigationWindow></span><span class="sxs-lookup"><span data-stu-id="6ff81-303">Isolation is achieved by setting the **SandboxExternalContent** property to true, as shown in the following examples for <xref:System.Windows.Controls.Frame> and <xref:System.Windows.Navigation.NavigationWindow>:</span></span>  
  
 [!code-xaml[SecurityOverviewSnippets#FrameMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window2.xaml#framemarkup)]  
  
 [!code-xaml[SecurityOverviewSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window1.xaml#navigationwindowmarkup)]  
  
 <span data-ttu-id="6ff81-304">使用此設定，會將外部內容載入與裝載應用程式的程序不同的程序。</span><span class="sxs-lookup"><span data-stu-id="6ff81-304">With this setting, external content will be loaded into a process that is separate from the process that is hosting the application.</span></span> <span data-ttu-id="6ff81-305">此程序僅限於預設網際網路區域權限集，可有效地隔離它與裝載應用程式和用戶端電腦。</span><span class="sxs-lookup"><span data-stu-id="6ff81-305">This process is restricted to the default Internet zone permission set, effectively isolating it from the hosting application and the client computer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6ff81-306">即使基於 WPF[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]瀏覽器託管基礎結構<xref:System.Windows.Navigation.NavigationWindow>（<xref:System.Windows.Controls.Frame>涉及演示文稿主機進程）實現從 a 或獨立應用程式中對鬆散檔的導航，安全級別比直接在 Windows Vista 和 Windows 7 上的 Internet 資源管理器中載入的內容（這仍通過演示主機）時略低。</span><span class="sxs-lookup"><span data-stu-id="6ff81-306">Even though navigation to loose [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] files from either a <xref:System.Windows.Navigation.NavigationWindow> or <xref:System.Windows.Controls.Frame> in a standalone application is implemented based on the WPF browser hosting infrastructure, involving the PresentationHost process, the security level is slightly less than when the content is loaded directly in Internet Explorer on Windows Vista and Windows 7 (which would still be through PresentationHost).</span></span> <span data-ttu-id="6ff81-307">這是因為使用 Web 瀏覽器的獨立 WPF 應用程式不會提供 Internet Explorer 的額外受保護模式安全性功能。</span><span class="sxs-lookup"><span data-stu-id="6ff81-307">This is because a standalone WPF application using a Web browser does not provide the additional Protected Mode security feature of Internet Explorer.</span></span>  
  
<a name="BestPractices"></a>
## <a name="resources-for-developing-wpf-applications-that-promote-security"></a><span data-ttu-id="6ff81-308">用於開發可提高安全性的 WPF 應用程式的資源</span><span class="sxs-lookup"><span data-stu-id="6ff81-308">Resources for Developing WPF Applications that Promote Security</span></span>  
 <span data-ttu-id="6ff81-309">以下是一些其他資源，可説明開發 WPF 應用程式，以提高安全性：</span><span class="sxs-lookup"><span data-stu-id="6ff81-309">The following are some additional resources to help develop WPF applications that promote security:</span></span>  
  
|<span data-ttu-id="6ff81-310">區域</span><span class="sxs-lookup"><span data-stu-id="6ff81-310">Area</span></span>|<span data-ttu-id="6ff81-311">資源</span><span class="sxs-lookup"><span data-stu-id="6ff81-311">Resource</span></span>|  
|----------|--------------|  
|<span data-ttu-id="6ff81-312">Managed 程式碼</span><span class="sxs-lookup"><span data-stu-id="6ff81-312">Managed code</span></span>|<span data-ttu-id="6ff81-313">[Patterns and Practices Security Guidance for Applications](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)) (應用程式的模式和實務安全性指南)</span><span class="sxs-lookup"><span data-stu-id="6ff81-313">[Patterns and Practices Security Guidance for Applications](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))</span></span>|  
|<span data-ttu-id="6ff81-314">CAS</span><span class="sxs-lookup"><span data-stu-id="6ff81-314">CAS</span></span>|[<span data-ttu-id="6ff81-315">代碼訪問安全性</span><span class="sxs-lookup"><span data-stu-id="6ff81-315">Code Access Security</span></span>](../misc/code-access-security.md)|  
|<span data-ttu-id="6ff81-316">ClickOnce</span><span class="sxs-lookup"><span data-stu-id="6ff81-316">ClickOnce</span></span>|[<span data-ttu-id="6ff81-317">按一下"一次安全和部署"</span><span class="sxs-lookup"><span data-stu-id="6ff81-317">ClickOnce Security and Deployment</span></span>](/visualstudio/deployment/clickonce-security-and-deployment)|  
|<span data-ttu-id="6ff81-318">WPF</span><span class="sxs-lookup"><span data-stu-id="6ff81-318">WPF</span></span>|[<span data-ttu-id="6ff81-319">WPF 部分信任安全性</span><span class="sxs-lookup"><span data-stu-id="6ff81-319">WPF Partial Trust Security</span></span>](wpf-partial-trust-security.md)|  
  
## <a name="see-also"></a><span data-ttu-id="6ff81-320">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ff81-320">See also</span></span>

- [<span data-ttu-id="6ff81-321">WPF 部分信任安全性</span><span class="sxs-lookup"><span data-stu-id="6ff81-321">WPF Partial Trust Security</span></span>](wpf-partial-trust-security.md)
- [<span data-ttu-id="6ff81-322">WPF 安全性策略 – 平台安全性</span><span class="sxs-lookup"><span data-stu-id="6ff81-322">WPF Security Strategy - Platform Security</span></span>](wpf-security-strategy-platform-security.md)
- [<span data-ttu-id="6ff81-323">WPF 安全性策略 – 安全性工程</span><span class="sxs-lookup"><span data-stu-id="6ff81-323">WPF Security Strategy - Security Engineering</span></span>](wpf-security-strategy-security-engineering.md)
- <span data-ttu-id="6ff81-324">[Patterns and Practices Security Guidance for Applications](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)) (應用程式的模式和實務安全性指南)</span><span class="sxs-lookup"><span data-stu-id="6ff81-324">[Patterns and Practices Security Guidance for Applications](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))</span></span>
- [<span data-ttu-id="6ff81-325">代碼訪問安全性</span><span class="sxs-lookup"><span data-stu-id="6ff81-325">Code Access Security</span></span>](../misc/code-access-security.md)
- [<span data-ttu-id="6ff81-326">按一下"一次安全和部署"</span><span class="sxs-lookup"><span data-stu-id="6ff81-326">ClickOnce Security and Deployment</span></span>](/visualstudio/deployment/clickonce-security-and-deployment)
- [<span data-ttu-id="6ff81-327">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="6ff81-327">XAML Overview (WPF)</span></span>](../../desktop-wpf/fundamentals/xaml.md)
