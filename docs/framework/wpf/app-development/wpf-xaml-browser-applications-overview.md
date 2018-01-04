---
title: "WPF XAML 瀏覽器應用程式概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XBAP [WPF], XAML browser application
- WPF XAML browser applications (XBAP)
- XAML browser applications (XBAP)
- browser-hosted applications [WPF]
ms.assetid: 3a7a86a8-75d5-4898-96b9-73da151e5e16
caps.latest.revision: "47"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c894d431aa31e32b4a8cb7ff02d39d5aa5e95381
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="wpf-xaml-browser-applications-overview"></a><span data-ttu-id="abc61-102">WPF XAML 瀏覽器應用程式概觀</span><span class="sxs-lookup"><span data-stu-id="abc61-102">WPF XAML Browser Applications Overview</span></span>
<a name="introduction"></a>
<span data-ttu-id="abc61-103">[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]結合的 Web 應用程式與豐富型用戶端應用程式的功能。</span><span class="sxs-lookup"><span data-stu-id="abc61-103">[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] combines features of both Web applications and rich-client applications.</span></span> <span data-ttu-id="abc61-104">如同 Web 應用程式，XBAP 可以部署至 Web 伺服器，並且從 Internet Explorer 或 Firefox 啟動。</span><span class="sxs-lookup"><span data-stu-id="abc61-104">Like Web applications, XBAPs can be deployed to a Web server and started from Internet Explorer or Firefox.</span></span> <span data-ttu-id="abc61-105">如同豐富型用戶端應用程式，XBAP 可以利用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的功能。</span><span class="sxs-lookup"><span data-stu-id="abc61-105">Like rich-client applications, XBAPs can take advantage of the capabilities of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="abc61-106">開發 XBAP 也類似於豐富型用戶端開發。</span><span class="sxs-lookup"><span data-stu-id="abc61-106">Developing XBAPs is also similar to rich-client development.</span></span> <span data-ttu-id="abc61-107">本主題提供 XBAP 開發的簡單、高階介紹，並且描述 XBAP 開發與標準豐富型用戶端開發的不同之處。</span><span class="sxs-lookup"><span data-stu-id="abc61-107">This topic provides a simple, high-level introduction to XBAP development and describes where XBAP development differs from standard rich-client development.</span></span>  
  
 <span data-ttu-id="abc61-108">此主題包括下列章節：</span><span class="sxs-lookup"><span data-stu-id="abc61-108">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="abc61-109">建立新的 XAML 瀏覽器應用程式 (XBAP)</span><span class="sxs-lookup"><span data-stu-id="abc61-109">Creating a New XAML Browser Application (XBAP)</span></span>](#creating_a_new_xaml_browser_application_xbap)  
  
-   [<span data-ttu-id="abc61-110">部署 XBAP</span><span class="sxs-lookup"><span data-stu-id="abc61-110">Deploying an XBAP</span></span>](#deploying_a_xbap)  
  
-   [<span data-ttu-id="abc61-111">與主機網頁通訊</span><span class="sxs-lookup"><span data-stu-id="abc61-111">Communicating with the Host Web Page</span></span>](#communicating_with_the_host_web_page)  
  
-   [<span data-ttu-id="abc61-112">XBAP 安全性考量</span><span class="sxs-lookup"><span data-stu-id="abc61-112">XBAP Security Considerations</span></span>](#xbap_security_considerations)  
  
-   [<span data-ttu-id="abc61-113">XBAP 開始時間效能考量</span><span class="sxs-lookup"><span data-stu-id="abc61-113">XBAP Start Time Performance Considerations</span></span>](#xbap_start_time_performance_considerations)  
  
<a name="creating_a_new_xaml_browser_application_xbap"></a>   
## <a name="creating-a-new-xaml-browser-application-xbap"></a><span data-ttu-id="abc61-114">建立新的 XAML 瀏覽器應用程式 (XBAP)</span><span class="sxs-lookup"><span data-stu-id="abc61-114">Creating a New XAML Browser Application (XBAP)</span></span>  
 <span data-ttu-id="abc61-115">建立新的 XBAP 專案最簡單的方法是使用 [!INCLUDE[vs_dev10_ext](../../../../includes/vs-dev10-ext-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="abc61-115">The simplest way to create a new XBAP project is with [!INCLUDE[vs_dev10_ext](../../../../includes/vs-dev10-ext-md.md)].</span></span> <span data-ttu-id="abc61-116">建立新專案時，從範本清單選取 [WPF 瀏覽器應用程式]。</span><span class="sxs-lookup"><span data-stu-id="abc61-116">When creating a new project, select **WPF Browser Application** from the list of templates.</span></span> <span data-ttu-id="abc61-117">如需更多詳細資訊，請參閱[如何：建立新的 WPF 瀏覽器應用程式專案](http://msdn.microsoft.com/en-us/72ef4d90-e163-42a1-8df0-ea7ccfd1901f)。</span><span class="sxs-lookup"><span data-stu-id="abc61-117">For more information, see [How to: Create a New WPF Browser Application Project](http://msdn.microsoft.com/en-us/72ef4d90-e163-42a1-8df0-ea7ccfd1901f).</span></span>  
  
 <span data-ttu-id="abc61-118">當您執行 XBAP 專案時，它會在瀏覽器視窗中開啟，而不是在獨立視窗中開啟。</span><span class="sxs-lookup"><span data-stu-id="abc61-118">When you run the XBAP project, it opens in a browser window instead of a stand-alone window.</span></span> <span data-ttu-id="abc61-119">當您從 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] 針對 XBAP 進行偵錯時，應用程式會使用網際網路區域權限執行，因此如果超過這些權限，則會擲回安全性例外狀況。</span><span class="sxs-lookup"><span data-stu-id="abc61-119">When you debug the XBAP from [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], the application runs with Internet zone permission and will therefore throw security exceptions if those permissions are exceeded.</span></span> <span data-ttu-id="abc61-120">如需詳細資訊，請參閱[安全性](../../../../docs/framework/wpf/security-wpf.md)和 [WPF 部分信任安全性](../../../../docs/framework/wpf/wpf-partial-trust-security.md)。</span><span class="sxs-lookup"><span data-stu-id="abc61-120">For more information, see [Security](../../../../docs/framework/wpf/security-wpf.md) and [WPF Partial Trust Security](../../../../docs/framework/wpf/wpf-partial-trust-security.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="abc61-121">如果您不是使用 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] 開發，或者想要深入了解專案檔，請參閱[建置 WPF 應用程式](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="abc61-121">If you are not developing with [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] or want to learn more about the project files, see [Building a WPF Application](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md).</span></span>  
  
<a name="deploying_a_xbap"></a>   
## <a name="deploying-an-xbap"></a><span data-ttu-id="abc61-122">部署 XBAP</span><span class="sxs-lookup"><span data-stu-id="abc61-122">Deploying an XBAP</span></span>  
 <span data-ttu-id="abc61-123">當您建置 XBAP 時，輸出會包含下列三個檔案︰</span><span class="sxs-lookup"><span data-stu-id="abc61-123">When you build an XBAP, the output includes the following three files:</span></span>  
  
|<span data-ttu-id="abc61-124">檔案</span><span class="sxs-lookup"><span data-stu-id="abc61-124">File</span></span>|<span data-ttu-id="abc61-125">描述</span><span class="sxs-lookup"><span data-stu-id="abc61-125">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="abc61-126">可執行檔 (.exe)</span><span class="sxs-lookup"><span data-stu-id="abc61-126">Executable (.exe)</span></span>|<span data-ttu-id="abc61-127">它包含已編譯的程式碼，副檔名為 .exe。</span><span class="sxs-lookup"><span data-stu-id="abc61-127">This contains the compiled code and has an .exe extension.</span></span>|  
|<span data-ttu-id="abc61-128">應用程式資訊清單 (.manifest)</span><span class="sxs-lookup"><span data-stu-id="abc61-128">Application manifest (.manifest)</span></span>|<span data-ttu-id="abc61-129">它包含與應用程式相關聯的中繼資料，副檔名為 .manifest。</span><span class="sxs-lookup"><span data-stu-id="abc61-129">This contains metadata associated with the application and has a .manifest extension.</span></span>|  
|<span data-ttu-id="abc61-130">部署資訊清單 (.xbap)</span><span class="sxs-lookup"><span data-stu-id="abc61-130">Deployment manifest (.xbap)</span></span>|<span data-ttu-id="abc61-131">這個檔案包含資訊，[!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] 用來部署應用程式，副檔名為 .xbap。</span><span class="sxs-lookup"><span data-stu-id="abc61-131">This file contains the information that [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] uses to deploy the application and has the .xbap extension.</span></span>|  
  
 <span data-ttu-id="abc61-132">您將 XBAP 部署至 Web 伺服器，例如，[!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="abc61-132">You deploy XBAPs to a Web server, for example [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] or later versions.</span></span> <span data-ttu-id="abc61-133">您不需要在 Web 伺服器上安裝 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)]，但是您必須註冊 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] 型別和副檔名。</span><span class="sxs-lookup"><span data-stu-id="abc61-133">You do not have to install the [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] on the Web server, but you do have to register the [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] types and file name extensions.</span></span> <span data-ttu-id="abc61-134">如需詳細資訊，請參閱[設定 IIS 5.0 和 IIS 6.0 以部署 WPF 應用程式](../../../../docs/framework/wpf/app-development/how-to-configure-iis-5-0-and-iis-6-0-to-deploy-wpf-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="abc61-134">For more information, see [Configure IIS 5.0 and IIS 6.0 to Deploy WPF Applications](../../../../docs/framework/wpf/app-development/how-to-configure-iis-5-0-and-iis-6-0-to-deploy-wpf-applications.md).</span></span>  
  
 <span data-ttu-id="abc61-135">若要準備您的 XBAP 以進行部署，將 .exe 和相關聯的資訊清單複製到 Web 伺服器。</span><span class="sxs-lookup"><span data-stu-id="abc61-135">To prepare your XBAP for deployment, copy the .exe and the associated manifests to the Web server.</span></span> <span data-ttu-id="abc61-136">建立 HTML 網頁，其中包含可開啟部署資訊清單 (它是副檔名為 .xbap 的檔案) 的超連結。</span><span class="sxs-lookup"><span data-stu-id="abc61-136">Create an HTML page that contains a hyperlink to open the deployment manifest, which is the file that has the .xbap extension.</span></span> <span data-ttu-id="abc61-137">當使用者按一下 .xbap 檔案的連結，[!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] 會自動處理下載和啟動應用程式的機制。</span><span class="sxs-lookup"><span data-stu-id="abc61-137">When the user clicks the link to the .xbap file, [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] automatically handles the mechanics of downloading and starting the application.</span></span> <span data-ttu-id="abc61-138">下列範例程式碼顯示包含指向 XBAP 之超連結的 HTML 網頁。</span><span class="sxs-lookup"><span data-stu-id="abc61-138">The following example code shows an HTML page that contains a hyperlink that points to an XBAP.</span></span>  
  
```html
<html>   
    <head></head>  
    <body>   
        <a href="XbapEx.xbap">Click this link to launch the application</a>  
    </body>   
</html>  
```  
  
 <span data-ttu-id="abc61-139">您也可以在網頁的框架中裝載 XBAP。</span><span class="sxs-lookup"><span data-stu-id="abc61-139">You can also host an XBAP in the frame of a Web page.</span></span> <span data-ttu-id="abc61-140">建立具有一或多個框架的網頁。</span><span class="sxs-lookup"><span data-stu-id="abc61-140">Create a Web page with one or more frames.</span></span> <span data-ttu-id="abc61-141">將框架的來源屬性設為部署資訊清單檔。</span><span class="sxs-lookup"><span data-stu-id="abc61-141">Set the source property of a frame to the deployment manifest file.</span></span> <span data-ttu-id="abc61-142">如果您想要使用內建的機制，在裝載的網頁和 XBAP 之間進行通訊，您必須在框架中裝載應用程式。</span><span class="sxs-lookup"><span data-stu-id="abc61-142">If you want to use the built-in mechanism to communicate between the hosting Web page and the XBAP, you must host the application in a frame.</span></span> <span data-ttu-id="abc61-143">下列程式碼範例顯示具有兩個框架的 HTML 網頁，第二個框架的來源設定為 XBAP。</span><span class="sxs-lookup"><span data-stu-id="abc61-143">The following example code shows an HTML page with two frames, the source for the second frame is set to an XBAP.</span></span>  
  
```html
<html>   
    <head>
        <title>A page with frames</title>
    </head>  
    <frameset cols="50%,50%">   
        <frame src="introduction.htm">   
        <frame src="XbapEx.xbap">   
    </frameset>   
</html>  
```  
  
### <a name="clearing-cached-xbaps"></a><span data-ttu-id="abc61-144">清除快取 XBAP</span><span class="sxs-lookup"><span data-stu-id="abc61-144">Clearing Cached XBAPs</span></span>  
 <span data-ttu-id="abc61-145">在某些情況下，重新建置並啟動您的 XBAP 之後，您可能會發現舊版 XBAP 開啟。</span><span class="sxs-lookup"><span data-stu-id="abc61-145">In some situations after rebuilding and starting your XBAP, you may find that an earlier version of the XBAP is opened.</span></span> <span data-ttu-id="abc61-146">例如，當 XBAP 組件版本號碼是靜態的，且您從命令列啟動 XBAP 時，可能會發生這種行為。</span><span class="sxs-lookup"><span data-stu-id="abc61-146">For example, this behavior may occur when your XBAP assembly version number is static and you start the XBAP from the command line.</span></span> <span data-ttu-id="abc61-147">在此情況下，因為快取版本 (先前已啟動的版本) 與新版本之間的版本號碼維持不變，所以不會下載新版本的 XBAP。</span><span class="sxs-lookup"><span data-stu-id="abc61-147">In this case, because the version number between the cached version (the version that was previously started) and the new version remains the same, the new version of the XBAP is not downloaded.</span></span> <span data-ttu-id="abc61-148">相反地，會載入快取版本。</span><span class="sxs-lookup"><span data-stu-id="abc61-148">Instead, the cached version is loaded.</span></span>  
  
 <span data-ttu-id="abc61-149">在這些情況下，您可以藉由在命令提示字元使用 **Mage** 命令 (與 Visual Studio 一起安裝或 [!INCLUDE[TLA2#tla_lhsdk](../../../../includes/tla2sharptla-lhsdk-md.md)])，移除快取版本。</span><span class="sxs-lookup"><span data-stu-id="abc61-149">In these situations, you can remove the cached version by using the **Mage** command (installed with Visual Studio or the [!INCLUDE[TLA2#tla_lhsdk](../../../../includes/tla2sharptla-lhsdk-md.md)]) at the command prompt.</span></span> <span data-ttu-id="abc61-150">下列命令會清除應用程式快取。</span><span class="sxs-lookup"><span data-stu-id="abc61-150">The following command clears the application cache.</span></span>  
  
 ```console
 Mage.exe -cc
 ```
  
 <span data-ttu-id="abc61-151">此命令可確保啟動最新版本的 XBAP。</span><span class="sxs-lookup"><span data-stu-id="abc61-151">This command guarantees that the latest version of your XBAP is started.</span></span> <span data-ttu-id="abc61-152">當您在 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] 中針對應用程式進行偵錯時，應該會啟動最新版本的 XBAP。</span><span class="sxs-lookup"><span data-stu-id="abc61-152">When you debug your application in [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], the latest version of your XBAP should be started.</span></span> <span data-ttu-id="abc61-153">一般而言，您應該以每個組建更新您的部署版本號碼。</span><span class="sxs-lookup"><span data-stu-id="abc61-153">In general, you should update your deployment version number with each build.</span></span> <span data-ttu-id="abc61-154">如需 Mage 的詳細資訊，請參閱 [Mage.exe (資訊清單產生和編輯工具)](../../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="abc61-154">For more information about Mage, see [Mage.exe (Manifest Generation and Editing Tool)](../../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md).</span></span>  
  
<a name="communicating_with_the_host_web_page"></a>   
## <a name="communicating-with-the-host-web-page"></a><span data-ttu-id="abc61-155">與主機網頁通訊</span><span class="sxs-lookup"><span data-stu-id="abc61-155">Communicating with the Host Web Page</span></span>  
 <span data-ttu-id="abc61-156">當應用程式裝載在 HTML 框架中時，您可以與包含 XBAP 的網頁進行通訊。</span><span class="sxs-lookup"><span data-stu-id="abc61-156">When the application is hosted in an HTML frame, you can communicate with the Web page that contains the XBAP.</span></span> <span data-ttu-id="abc61-157">您可以擷取<xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A>屬性<xref:System.Windows.Interop.BrowserInteropHelper>。</span><span class="sxs-lookup"><span data-stu-id="abc61-157">You do this by retrieving the <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> property of <xref:System.Windows.Interop.BrowserInteropHelper>.</span></span> <span data-ttu-id="abc61-158">這個屬性會傳回代表 HTML 視窗的指令碼物件。</span><span class="sxs-lookup"><span data-stu-id="abc61-158">This property returns a script object that represents the HTML window.</span></span> <span data-ttu-id="abc61-159">您接著可以使用一般 dot 語法，在[視窗物件](http://go.microsoft.com/fwlink/?LinkId=160274)上存取屬性、方法和事件。</span><span class="sxs-lookup"><span data-stu-id="abc61-159">You can then access the properties, methods, and events on the [window object](http://go.microsoft.com/fwlink/?LinkId=160274) by using regular dot syntax.</span></span> <span data-ttu-id="abc61-160">您也可以存取指令碼方法和全域變數。</span><span class="sxs-lookup"><span data-stu-id="abc61-160">You can also access script methods and global variables.</span></span> <span data-ttu-id="abc61-161">下列範例示範如何擷取指令碼物件，並且關閉瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="abc61-161">The following example shows how to retrieve the script object and close the browser.</span></span>  
  
 [!code-csharp[XbapBrowserInterop#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/xbapbrowserinterop/cs/page1.xaml.cs#10)]
 [!code-vb[XbapBrowserInterop#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/xbapbrowserinterop/vb/page1.xaml.vb#10)]  
  
### <a name="debugging-xbaps-that-use-hostscript"></a><span data-ttu-id="abc61-162">針對使用 HostScript 的 XBAP 進行偵錯</span><span class="sxs-lookup"><span data-stu-id="abc61-162">Debugging XBAPs that Use HostScript</span></span>  
 <span data-ttu-id="abc61-163">如果您 XBAP 使用<xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A>通訊與 [HTML] 視窗中，有兩個設定，您必須指定的物件執行和偵錯中的應用程式[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="abc61-163">If your XBAP uses the <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> object to communicate with the HTML window, there are two settings that you must specify to run and debug the application in [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)].</span></span> <span data-ttu-id="abc61-164">應用程式必須能夠存取它的來源網站，而且您必須使用包含 XBAP 的 HTML 網頁來啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="abc61-164">The application must have access to its site of origin and you must start the application with the HTML page that contains the XBAP.</span></span> <span data-ttu-id="abc61-165">下列步驟說明如何檢查這兩項設定︰</span><span class="sxs-lookup"><span data-stu-id="abc61-165">The following steps describe how to check these two settings:</span></span>  
  
1.  <span data-ttu-id="abc61-166">在 Visual Studio 中，開啟專案屬性。</span><span class="sxs-lookup"><span data-stu-id="abc61-166">In Visual Studio, open the project properties.</span></span>  
  
2.  <span data-ttu-id="abc61-167">在 [安全性] 索引標籤上，按一下 [進階]。</span><span class="sxs-lookup"><span data-stu-id="abc61-167">On the **Security** tab, click **Advanced**.</span></span>  
  
     <span data-ttu-id="abc61-168">[進階安全性設定] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="abc61-168">The Advanced Security Settings dialog box appears.</span></span>  
  
3.  <span data-ttu-id="abc61-169">請確定 [允許應用程式存取它的來源網站] 核取方塊已勾選，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="abc61-169">Make sure that the **Grant the application access to its site of origin** check box is checked and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="abc61-170">在 [偵錯] 索引標籤上，選取 [瀏覽器起始 URL] 選項，並且指定包含 XBAP 之 HTML 網頁的 URL。</span><span class="sxs-lookup"><span data-stu-id="abc61-170">On the **Debug** tab, select the **Start browser with URL** option and specify the URL for the HTML page that contains the XBAP.</span></span>  
  
5.  <span data-ttu-id="abc61-171">在 Internet Explorer 中，按一下 [工具] 按鈕，然後選取 [網際網路選項]。</span><span class="sxs-lookup"><span data-stu-id="abc61-171">In Internet Explorer, click the **Tools** button and then select **Internet Options**.</span></span>  
  
     <span data-ttu-id="abc61-172">[網際網路選項] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="abc61-172">The Internet Options dialog box appears.</span></span>  
  
6.  <span data-ttu-id="abc61-173">按一下 [進階] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="abc61-173">Click the **Advanced** tab.</span></span>  
  
7.  <span data-ttu-id="abc61-174">在 [安全性] 底下的 [設定]清單中，勾選 [允許檔案中的主動式內容在我的電腦上執行] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="abc61-174">In the **Settings** list under **Security**, check the **Allow active content to run in files on My Computer** check box.</span></span>  
  
8.  <span data-ttu-id="abc61-175">按一下 [確定 **Deploying Office Solutions**]。</span><span class="sxs-lookup"><span data-stu-id="abc61-175">Click **OK**.</span></span>  
  
     <span data-ttu-id="abc61-176">變更在重新啟動 Internet Explorer 之後才會生效。</span><span class="sxs-lookup"><span data-stu-id="abc61-176">The changes will take effect after you restart Internet Explorer.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="abc61-177">在 Internet Explorer 中啟用主動式內容可能會讓電腦面臨風險。</span><span class="sxs-lookup"><span data-stu-id="abc61-177">Enabling active content in Internet Explorer may put your computer at risk.</span></span> <span data-ttu-id="abc61-178">如需詳細資訊，請參閱 [Internet Explorer 中的安全性和隱私權功能](http://go.microsoft.com/fwlink/?LinkId=179286)。</span><span class="sxs-lookup"><span data-stu-id="abc61-178">For more information, see [Security and privacy features in Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=179286).</span></span> <span data-ttu-id="abc61-179">如果您不想要變更 Internet Explorer 安全性設定，您可以從伺服器啟動 HTML 網頁，並且將 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] 偵錯工具連接至流程。</span><span class="sxs-lookup"><span data-stu-id="abc61-179">If you do not want to change your Internet Explorer security settings, you can launch the HTML page from a server and attach the [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] debugger to the process.</span></span>  
  
<a name="xbap_security_considerations"></a>   
## <a name="xbap-security-considerations"></a><span data-ttu-id="abc61-180">XBAP 安全性考量</span><span class="sxs-lookup"><span data-stu-id="abc61-180">XBAP Security Considerations</span></span>  
 <span data-ttu-id="abc61-181">XBAP 通常會在部分信任安全性沙箱中執行，它限制為網際網路區域權限集合。</span><span class="sxs-lookup"><span data-stu-id="abc61-181">XBAPs typically execute in a partial-trust security sandbox that is restricted to the Internet zone permission set.</span></span> <span data-ttu-id="abc61-182">因此，您的實作必須支援 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 元素的子集，它在網際網路區域受到支援，或者必須提高應用程式的權限。</span><span class="sxs-lookup"><span data-stu-id="abc61-182">Consequently, your implementation must support the subset of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements that are supported in the Internet zone or you must elevate the permissions of your application.</span></span> <span data-ttu-id="abc61-183">如需詳細資訊，請參閱[安全性](../../../../docs/framework/wpf/security-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="abc61-183">For more information, see [Security](../../../../docs/framework/wpf/security-wpf.md).</span></span>  
  
 <span data-ttu-id="abc61-184">當您使用<xref:System.Windows.Controls.WebBrowser>應用程式中，WPF 控制項在內部具現化的原生 WebBrowser ActiveX 控制項。</span><span class="sxs-lookup"><span data-stu-id="abc61-184">When you use a <xref:System.Windows.Controls.WebBrowser> control in your application, WPF internally instantiates the native WebBrowser ActiveX control.</span></span> <span data-ttu-id="abc61-185">當您的應用程式是在 Internet Explorer 中執行的部分信任 XBAP 時，ActiveX 控制項會在 Internet Explorer 流程的專用執行緒中執行。</span><span class="sxs-lookup"><span data-stu-id="abc61-185">When your application is a partial-trust XBAP running in Internet Explorer, the ActiveX control runs in a dedicated thread of the Internet Explorer process.</span></span> <span data-ttu-id="abc61-186">因此，會套用下列限制：</span><span class="sxs-lookup"><span data-stu-id="abc61-186">Therefore, the following limitations apply:</span></span>  
  
-   <span data-ttu-id="abc61-187"><xref:System.Windows.Controls.WebBrowser>控制項應該提供類似於主機的瀏覽器，包括安全性限制的行為。</span><span class="sxs-lookup"><span data-stu-id="abc61-187">The <xref:System.Windows.Controls.WebBrowser> control should provide behavior similar to the host browser, including security restrictions.</span></span> <span data-ttu-id="abc61-188">其中一些安全性限制可以透過 Internet Explorer 安全性設定來控制。</span><span class="sxs-lookup"><span data-stu-id="abc61-188">Some of these security restrictions can be controlled through the Internet Explorer security settings.</span></span> <span data-ttu-id="abc61-189">如需詳細資訊，請參閱[安全性](../../../../docs/framework/wpf/security-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="abc61-189">For more information, see [Security](../../../../docs/framework/wpf/security-wpf.md).</span></span>  
  
-   <span data-ttu-id="abc61-190">當 XBAP 在 HTML 網頁跨網域載入時，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="abc61-190">An exception is thrown when an XBAP is loaded cross-domain in an HTML page.</span></span>  
  
-   <span data-ttu-id="abc61-191">輸入是另一個執行緒從 WPF <xref:System.Windows.Controls.WebBrowser>，因此無法攔截的鍵盤輸入，而且不共用的輸入法狀態。</span><span class="sxs-lookup"><span data-stu-id="abc61-191">Input is on a separate thread from the WPF <xref:System.Windows.Controls.WebBrowser>, so keyboard input cannot be intercepted and the IME state is not shared.</span></span>  
  
-   <span data-ttu-id="abc61-192">因為在另一個執行緒上執行的 ActiveX 控制項，瀏覽的時間或順序可能不同。</span><span class="sxs-lookup"><span data-stu-id="abc61-192">The timing or order of navigation may be different due to the ActiveX control running on another thread.</span></span> <span data-ttu-id="abc61-193">例如，瀏覽至頁面不一定會因為啟動另一個瀏覽要求而取消。</span><span class="sxs-lookup"><span data-stu-id="abc61-193">For example, navigating to a page is not always cancelled by starting another navigation request.</span></span>  
  
-   <span data-ttu-id="abc61-194">自訂 ActiveX 控制項可能會遇到通訊問題，因為 WPF 應用程式是在個別執行緒中執行。</span><span class="sxs-lookup"><span data-stu-id="abc61-194">A custom ActiveX control may have trouble with communication since the WPF application is running in a separate thread.</span></span>  
  
-   <span data-ttu-id="abc61-195"><xref:System.Windows.Interop.HwndHost.MessageHook>不會不取得引發因為<xref:System.Windows.Interop.HwndHost>無法在另一個執行緒或處理序中執行視窗子類別。</span><span class="sxs-lookup"><span data-stu-id="abc61-195"><xref:System.Windows.Interop.HwndHost.MessageHook> does not get raised because <xref:System.Windows.Interop.HwndHost> cannot subclass a window running in another thread or process.</span></span>  
  
### <a name="creating-a-full-trust-xbap"></a><span data-ttu-id="abc61-196">建立完全信任 XBAP</span><span class="sxs-lookup"><span data-stu-id="abc61-196">Creating a Full-Trust XBAP</span></span>  
 <span data-ttu-id="abc61-197">如果您的 XBAP 需要完全信任，您可以變更專案以啟用此權限。</span><span class="sxs-lookup"><span data-stu-id="abc61-197">If your XBAP requires full trust, you can change your project to enable this permission.</span></span> <span data-ttu-id="abc61-198">下列步驟描述如何啟用完全信任︰</span><span class="sxs-lookup"><span data-stu-id="abc61-198">The following steps describe how to enable full trust:</span></span>  
  
1.  <span data-ttu-id="abc61-199">在 Visual Studio 中，開啟專案屬性。</span><span class="sxs-lookup"><span data-stu-id="abc61-199">In Visual Studio, open the project properties.</span></span>  
  
2.  <span data-ttu-id="abc61-200">在 [安全性] 索引標籤上，選取 [這是完全信任的應用程式] 選項。</span><span class="sxs-lookup"><span data-stu-id="abc61-200">On the **Security** tab, select the **This is a full trust application** option.</span></span>  
  
 <span data-ttu-id="abc61-201">這項設定會進行下列變更︰</span><span class="sxs-lookup"><span data-stu-id="abc61-201">This setting makes the following changes:</span></span>  
  
-   <span data-ttu-id="abc61-202">在專案檔中，`<TargetZone>` 元素值變更為 `Custom`。</span><span class="sxs-lookup"><span data-stu-id="abc61-202">In the project file, the `<TargetZone>` element value is changed to `Custom`.</span></span>  
  
-   <span data-ttu-id="abc61-203">在應用程式資訊清單 (app.manifest) 中，`Unrestricted="true"` 屬性新增至 `PermissionSet` 元素。</span><span class="sxs-lookup"><span data-stu-id="abc61-203">In the application manifest (app.manifest), an `Unrestricted="true"` attribute is added to the `PermissionSet` element.</span></span>  
  
    ```xml
    <PermissionSet class="System.Security.PermissionSet"   
                   version="1"   
                   ID="Custom"   
                   SameSite="site"   
                   Unrestricted="true" />  
    ```  
  
### <a name="deploying-a-full-trust-xbap"></a><span data-ttu-id="abc61-204">部署完全信任 XBAP</span><span class="sxs-lookup"><span data-stu-id="abc61-204">Deploying a Full-Trust XBAP</span></span>  
 <span data-ttu-id="abc61-205">當您部署未遵循 ClickOnce 受信任部署模型的完全信任 XBAP 時，使用者執行應用程式時的行為將取決於安全性區域。</span><span class="sxs-lookup"><span data-stu-id="abc61-205">When you deploy a full-trust XBAP that does not follow the ClickOnce Trusted Deployment model, the behavior when the user runs the application will depend on the security zone.</span></span> <span data-ttu-id="abc61-206">在某些情況下，使用者會在嘗試安裝它時收到一則警告。</span><span class="sxs-lookup"><span data-stu-id="abc61-206">In some cases, the user will receive a warning when they attempt to install it.</span></span> <span data-ttu-id="abc61-207">使用者可以選擇繼續或取消安裝。</span><span class="sxs-lookup"><span data-stu-id="abc61-207">The user can choose to continue or cancel the installation.</span></span> <span data-ttu-id="abc61-208">下表描述每個安全性區域的應用程式行為，以及您必須針對應用程式執行什麼動作才能得到完全信任。</span><span class="sxs-lookup"><span data-stu-id="abc61-208">The following table describes the behavior of the application for each security zone and what you have to do for the application to receive full trust.</span></span>  
  
|<span data-ttu-id="abc61-209">安全性區域</span><span class="sxs-lookup"><span data-stu-id="abc61-209">Security Zone</span></span>|<span data-ttu-id="abc61-210">行為</span><span class="sxs-lookup"><span data-stu-id="abc61-210">Behavior</span></span>|<span data-ttu-id="abc61-211">取得完全信任</span><span class="sxs-lookup"><span data-stu-id="abc61-211">Getting Full Trust</span></span>|  
|-------------------|--------------|------------------------|  
|<span data-ttu-id="abc61-212">本機電腦</span><span class="sxs-lookup"><span data-stu-id="abc61-212">Local computer</span></span>|<span data-ttu-id="abc61-213">自動的完全信任</span><span class="sxs-lookup"><span data-stu-id="abc61-213">Automatic full trust</span></span>|<span data-ttu-id="abc61-214">不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="abc61-214">No action is needed.</span></span>|  
|<span data-ttu-id="abc61-215">內部網路和信任的網站</span><span class="sxs-lookup"><span data-stu-id="abc61-215">Intranet and trusted sites</span></span>|<span data-ttu-id="abc61-216">完全信任的提示</span><span class="sxs-lookup"><span data-stu-id="abc61-216">Prompt for full trust</span></span>|<span data-ttu-id="abc61-217">使用憑證簽署 XBAP，讓使用者在提示中看到來源。</span><span class="sxs-lookup"><span data-stu-id="abc61-217">Sign the XBAP with a certificate so that the user sees the source in the prompt.</span></span>|  
|<span data-ttu-id="abc61-218">網際網路</span><span class="sxs-lookup"><span data-stu-id="abc61-218">Internet</span></span>|<span data-ttu-id="abc61-219">因為「未授與信任」而失敗</span><span class="sxs-lookup"><span data-stu-id="abc61-219">Fails with "Trust Not Granted"</span></span>|<span data-ttu-id="abc61-220">使用憑證簽署 XBAP。</span><span class="sxs-lookup"><span data-stu-id="abc61-220">Sign the XBAP with a certificate.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="abc61-221">上表中描述的行為是針對未遵循 ClickOnce 受信任部署模型的完全信任 XBAP。</span><span class="sxs-lookup"><span data-stu-id="abc61-221">The behavior described in the previous table is for full-trust XBAPs that do not follow the ClickOnce Trusted Deployment model.</span></span>  
  
 <span data-ttu-id="abc61-222">建議您使用 ClickOnce 受信任部署模型來部署完全信任 XBAP。</span><span class="sxs-lookup"><span data-stu-id="abc61-222">It is recommended that you use the ClickOnce Trusted Deployment model for deploying a full-trust XBAP.</span></span> <span data-ttu-id="abc61-223">此模型可讓您的 XBAP 自動授與完全信任，無論安全性區域為何，因此系統不會提示使用者。</span><span class="sxs-lookup"><span data-stu-id="abc61-223">This model allows your XBAP to be granted full trust automatically, regardless of the security zone, so that the user is not prompted.</span></span> <span data-ttu-id="abc61-224">做為此模型的一部分，您必須使用受信任發行者的憑證來簽署應用程式。</span><span class="sxs-lookup"><span data-stu-id="abc61-224">As part of this model, you must sign your application with a certificate from a trusted publisher.</span></span> <span data-ttu-id="abc61-225">如需詳細資訊，請參閱[受信任應用程式部署概觀](/visualstudio/deployment/trusted-application-deployment-overview)和[程式碼簽署簡介](http://go.microsoft.com/fwlink/?LinkId=166327)。</span><span class="sxs-lookup"><span data-stu-id="abc61-225">For more information, see [Trusted Application Deployment Overview](/visualstudio/deployment/trusted-application-deployment-overview) and [Introduction to Code Signing](http://go.microsoft.com/fwlink/?LinkId=166327).</span></span>  
  
<a name="xbap_start_time_performance_considerations"></a>   
## <a name="xbap-start-time-performance-considerations"></a><span data-ttu-id="abc61-226">XBAP 開始時間效能考量</span><span class="sxs-lookup"><span data-stu-id="abc61-226">XBAP Start Time Performance Considerations</span></span>  
 <span data-ttu-id="abc61-227">XBAP 效能很重要的層面是其開始時間。</span><span class="sxs-lookup"><span data-stu-id="abc61-227">An important aspect of XBAP performance is its start time.</span></span> <span data-ttu-id="abc61-228">如果 XBAP 是載入的第一個 WPF 應用程式，「冷啟動」時間可以是 10 秒或以上。</span><span class="sxs-lookup"><span data-stu-id="abc61-228">If an XBAP is the first WPF application to load, the *cold start* time can be ten seconds or more.</span></span> <span data-ttu-id="abc61-229">這是因為進度頁面是由 WPF 轉譯，且 CLR 和 WPF 必須冷啟動來顯示應用程式。</span><span class="sxs-lookup"><span data-stu-id="abc61-229">This is because the progress page is rendered by WPF, and both the CLR and WPF must be cold-started to display the application.</span></span>  
  
 <span data-ttu-id="abc61-230">從 [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)] 開始，藉由在部署週期早期顯示 unmanaged 進度頁面，降低 XBAP 冷啟動時間。</span><span class="sxs-lookup"><span data-stu-id="abc61-230">Starting in [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)], XBAP cold-start time is mitigated by displaying an unmanaged progress page early in the deployment cycle.</span></span> <span data-ttu-id="abc61-231">進度頁面幾乎是在應用程式啟動之後立即出現，因為它是由原生裝載程式碼顯示，並且以 HTML 轉譯。</span><span class="sxs-lookup"><span data-stu-id="abc61-231">The progress page appears almost immediately after the application is started, because it is displayed by native hosting code and rendered in HTML.</span></span>  
  
 <span data-ttu-id="abc61-232">此外，改善的並行 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 下載序列，會改善最多 10% 的開始時間。</span><span class="sxs-lookup"><span data-stu-id="abc61-232">In addition, improved concurrency of the [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] download sequence improves the start time by up to ten percent.</span></span> <span data-ttu-id="abc61-233">在 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 下載和驗證資訊清單之後，應用程式下載會啟動且更新進度列開始更新。</span><span class="sxs-lookup"><span data-stu-id="abc61-233">After [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] downloads and validates manifests, the application download starts, and the progress bar starts to update.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abc61-234">請參閱</span><span class="sxs-lookup"><span data-stu-id="abc61-234">See Also</span></span>  
 [<span data-ttu-id="abc61-235">設定 Visual Studio 來偵錯 XAML 瀏覽器應用程式以呼叫 Web 服務</span><span class="sxs-lookup"><span data-stu-id="abc61-235">Configure Visual Studio to Debug a XAML Browser Application to Call a Web Service</span></span>](../../../../docs/framework/wpf/app-development/configure-vs-to-debug-a-xaml-browser-to-call-a-web-service.md)  
 [<span data-ttu-id="abc61-236">部署 WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="abc61-236">Deploying a WPF Application</span></span>](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)
