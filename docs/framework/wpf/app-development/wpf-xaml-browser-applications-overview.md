---
title: WPF XAML 瀏覽器應用程式概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XBAP [WPF], XAML browser application
- WPF XAML browser applications (XBAP)
- XAML browser applications (XBAP)
- browser-hosted applications [WPF]
ms.assetid: 3a7a86a8-75d5-4898-96b9-73da151e5e16
ms.openlocfilehash: 8121b6e8c5a136f5f89b59636a7cb7f15794164a
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43745472"
---
# <a name="wpf-xaml-browser-applications-overview"></a><span data-ttu-id="70785-102">WPF XAML 瀏覽器應用程式概觀</span><span class="sxs-lookup"><span data-stu-id="70785-102">WPF XAML Browser Applications Overview</span></span>
<a name="introduction"></a>
<span data-ttu-id="70785-103">[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] 結合的 Web 應用程式和豐富型用戶端應用程式的功能。</span><span class="sxs-lookup"><span data-stu-id="70785-103">[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] combines features of both Web applications and rich-client applications.</span></span> <span data-ttu-id="70785-104">如同 Web 應用程式，XBAP 可以部署至 Web 伺服器，並且從 Internet Explorer 或 Firefox 啟動。</span><span class="sxs-lookup"><span data-stu-id="70785-104">Like Web applications, XBAPs can be deployed to a Web server and started from Internet Explorer or Firefox.</span></span> <span data-ttu-id="70785-105">如同豐富型用戶端應用程式，Xbap 可以利用 WPF 的功能。</span><span class="sxs-lookup"><span data-stu-id="70785-105">Like rich-client applications, XBAPs can take advantage of the capabilities of WPF.</span></span> <span data-ttu-id="70785-106">開發 XBAP 也類似於豐富型用戶端開發。</span><span class="sxs-lookup"><span data-stu-id="70785-106">Developing XBAPs is also similar to rich-client development.</span></span> <span data-ttu-id="70785-107">本主題提供 XBAP 開發的簡單、高階介紹，並且描述 XBAP 開發與標準豐富型用戶端開發的不同之處。</span><span class="sxs-lookup"><span data-stu-id="70785-107">This topic provides a simple, high-level introduction to XBAP development and describes where XBAP development differs from standard rich-client development.</span></span>  
  
 <span data-ttu-id="70785-108">此主題包括下列章節：</span><span class="sxs-lookup"><span data-stu-id="70785-108">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="70785-109">建立新的 XAML 瀏覽器應用程式 (XBAP)</span><span class="sxs-lookup"><span data-stu-id="70785-109">Creating a New XAML Browser Application (XBAP)</span></span>](#creating_a_new_xaml_browser_application_xbap)  
  
-   [<span data-ttu-id="70785-110">部署 XBAP</span><span class="sxs-lookup"><span data-stu-id="70785-110">Deploying an XBAP</span></span>](#deploying_a_xbap)  
  
-   [<span data-ttu-id="70785-111">與主機網頁通訊</span><span class="sxs-lookup"><span data-stu-id="70785-111">Communicating with the Host Web Page</span></span>](#communicating_with_the_host_web_page)  
  
-   [<span data-ttu-id="70785-112">XBAP 安全性考量</span><span class="sxs-lookup"><span data-stu-id="70785-112">XBAP Security Considerations</span></span>](#xbap_security_considerations)  
  
-   [<span data-ttu-id="70785-113">XBAP 開始時間效能考量</span><span class="sxs-lookup"><span data-stu-id="70785-113">XBAP Start Time Performance Considerations</span></span>](#xbap_start_time_performance_considerations)  
  
<a name="creating_a_new_xaml_browser_application_xbap"></a>   
## <a name="creating-a-new-xaml-browser-application-xbap"></a><span data-ttu-id="70785-114">建立新的 XAML 瀏覽器應用程式 (XBAP)</span><span class="sxs-lookup"><span data-stu-id="70785-114">Creating a New XAML Browser Application (XBAP)</span></span>  
 <span data-ttu-id="70785-115">若要建立新的 XBAP 專案最簡單的方式是使用 Microsoft Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="70785-115">The simplest way to create a new XBAP project is with Microsoft Visual Studio.</span></span> <span data-ttu-id="70785-116">建立新專案時，從範本清單選取 [WPF 瀏覽器應用程式]。</span><span class="sxs-lookup"><span data-stu-id="70785-116">When creating a new project, select **WPF Browser Application** from the list of templates.</span></span> <span data-ttu-id="70785-117">如需更多詳細資訊，請參閱[如何：建立新的 WPF 瀏覽器應用程式專案](https://msdn.microsoft.com/library/72ef4d90-e163-42a1-8df0-ea7ccfd1901f)。</span><span class="sxs-lookup"><span data-stu-id="70785-117">For more information, see [How to: Create a New WPF Browser Application Project](https://msdn.microsoft.com/library/72ef4d90-e163-42a1-8df0-ea7ccfd1901f).</span></span>  
  
 <span data-ttu-id="70785-118">當您執行 XBAP 專案時，它會在瀏覽器視窗中開啟，而不是在獨立視窗中開啟。</span><span class="sxs-lookup"><span data-stu-id="70785-118">When you run the XBAP project, it opens in a browser window instead of a stand-alone window.</span></span> <span data-ttu-id="70785-119">當您偵錯 XBAP 從 Visual Studio 時，應用程式會使用網際網路區域權限執行，並因此如果會擲回安全性例外狀況會在超過這些權限。</span><span class="sxs-lookup"><span data-stu-id="70785-119">When you debug the XBAP from Visual Studio, the application runs with Internet zone permission and will therefore throw security exceptions if those permissions are exceeded.</span></span> <span data-ttu-id="70785-120">如需詳細資訊，請參閱[安全性](../../../../docs/framework/wpf/security-wpf.md)和 [WPF 部分信任安全性](../../../../docs/framework/wpf/wpf-partial-trust-security.md)。</span><span class="sxs-lookup"><span data-stu-id="70785-120">For more information, see [Security](../../../../docs/framework/wpf/security-wpf.md) and [WPF Partial Trust Security](../../../../docs/framework/wpf/wpf-partial-trust-security.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="70785-121">如果您使用 Visual Studio 或您想来深入了解專案檔不進行開發，請參閱[建置 WPF 應用程式](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="70785-121">If you are not developing with Visual Studio or want to learn more about the project files, see [Building a WPF Application](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md).</span></span>  
  
<a name="deploying_a_xbap"></a>   
## <a name="deploying-an-xbap"></a><span data-ttu-id="70785-122">部署 XBAP</span><span class="sxs-lookup"><span data-stu-id="70785-122">Deploying an XBAP</span></span>  
 <span data-ttu-id="70785-123">當您建置 XBAP 時，輸出會包含下列三個檔案︰</span><span class="sxs-lookup"><span data-stu-id="70785-123">When you build an XBAP, the output includes the following three files:</span></span>  
  
|<span data-ttu-id="70785-124">檔案</span><span class="sxs-lookup"><span data-stu-id="70785-124">File</span></span>|<span data-ttu-id="70785-125">描述</span><span class="sxs-lookup"><span data-stu-id="70785-125">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="70785-126">可執行檔 (.exe)</span><span class="sxs-lookup"><span data-stu-id="70785-126">Executable (.exe)</span></span>|<span data-ttu-id="70785-127">它包含已編譯的程式碼，副檔名為 .exe。</span><span class="sxs-lookup"><span data-stu-id="70785-127">This contains the compiled code and has an .exe extension.</span></span>|  
|<span data-ttu-id="70785-128">應用程式資訊清單 (.manifest)</span><span class="sxs-lookup"><span data-stu-id="70785-128">Application manifest (.manifest)</span></span>|<span data-ttu-id="70785-129">它包含與應用程式相關聯的中繼資料，副檔名為 .manifest。</span><span class="sxs-lookup"><span data-stu-id="70785-129">This contains metadata associated with the application and has a .manifest extension.</span></span>|  
|<span data-ttu-id="70785-130">部署資訊清單 (.xbap)</span><span class="sxs-lookup"><span data-stu-id="70785-130">Deployment manifest (.xbap)</span></span>|<span data-ttu-id="70785-131">此檔案包含 ClickOnce 部署應用程式會使用與副檔名為.xbap 的資訊。</span><span class="sxs-lookup"><span data-stu-id="70785-131">This file contains the information that ClickOnce uses to deploy the application and has the .xbap extension.</span></span>|  
  
 <span data-ttu-id="70785-132">您將 XBAP 部署至 Web 伺服器，例如，[!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="70785-132">You deploy XBAPs to a Web server, for example [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] or later versions.</span></span> <span data-ttu-id="70785-133">您不必安裝.NET Framework 的 Web 伺服器上，但您必須註冊[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)][!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)]類型和副檔名。</span><span class="sxs-lookup"><span data-stu-id="70785-133">You do not have to install the .NET Framework on the Web server, but you do have to register the [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] types and file name extensions.</span></span> <span data-ttu-id="70785-134">如需詳細資訊，請參閱[設定 IIS 5.0 和 IIS 6.0 以部署 WPF 應用程式](../../../../docs/framework/wpf/app-development/how-to-configure-iis-5-0-and-iis-6-0-to-deploy-wpf-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="70785-134">For more information, see [Configure IIS 5.0 and IIS 6.0 to Deploy WPF Applications](../../../../docs/framework/wpf/app-development/how-to-configure-iis-5-0-and-iis-6-0-to-deploy-wpf-applications.md).</span></span>  
  
 <span data-ttu-id="70785-135">若要準備您的 XBAP 以進行部署，將 .exe 和相關聯的資訊清單複製到 Web 伺服器。</span><span class="sxs-lookup"><span data-stu-id="70785-135">To prepare your XBAP for deployment, copy the .exe and the associated manifests to the Web server.</span></span> <span data-ttu-id="70785-136">建立 HTML 網頁，其中包含可開啟部署資訊清單 (它是副檔名為 .xbap 的檔案) 的超連結。</span><span class="sxs-lookup"><span data-stu-id="70785-136">Create an HTML page that contains a hyperlink to open the deployment manifest, which is the file that has the .xbap extension.</span></span> <span data-ttu-id="70785-137">當使用者按一下.xbap 檔案的連結時，ClickOnce 會自動處理下載和啟動應用程式的機制。</span><span class="sxs-lookup"><span data-stu-id="70785-137">When the user clicks the link to the .xbap file, ClickOnce automatically handles the mechanics of downloading and starting the application.</span></span> <span data-ttu-id="70785-138">下列範例程式碼顯示包含指向 XBAP 之超連結的 HTML 網頁。</span><span class="sxs-lookup"><span data-stu-id="70785-138">The following example code shows an HTML page that contains a hyperlink that points to an XBAP.</span></span>  
  
```html
<html>   
    <head></head>  
    <body>   
        <a href="XbapEx.xbap">Click this link to launch the application</a>  
    </body>   
</html>  
```  
  
 <span data-ttu-id="70785-139">您也可以在網頁的框架中裝載 XBAP。</span><span class="sxs-lookup"><span data-stu-id="70785-139">You can also host an XBAP in the frame of a Web page.</span></span> <span data-ttu-id="70785-140">建立具有一或多個框架的網頁。</span><span class="sxs-lookup"><span data-stu-id="70785-140">Create a Web page with one or more frames.</span></span> <span data-ttu-id="70785-141">將框架的來源屬性設為部署資訊清單檔。</span><span class="sxs-lookup"><span data-stu-id="70785-141">Set the source property of a frame to the deployment manifest file.</span></span> <span data-ttu-id="70785-142">如果您想要使用內建的機制，在裝載的網頁和 XBAP 之間進行通訊，您必須在框架中裝載應用程式。</span><span class="sxs-lookup"><span data-stu-id="70785-142">If you want to use the built-in mechanism to communicate between the hosting Web page and the XBAP, you must host the application in a frame.</span></span> <span data-ttu-id="70785-143">下列程式碼範例顯示具有兩個框架的 HTML 網頁，第二個框架的來源設定為 XBAP。</span><span class="sxs-lookup"><span data-stu-id="70785-143">The following example code shows an HTML page with two frames, the source for the second frame is set to an XBAP.</span></span>  
  
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
  
### <a name="clearing-cached-xbaps"></a><span data-ttu-id="70785-144">清除快取 XBAP</span><span class="sxs-lookup"><span data-stu-id="70785-144">Clearing Cached XBAPs</span></span>  
 <span data-ttu-id="70785-145">在某些情況下，重新建置並啟動您的 XBAP 之後，您可能會發現舊版 XBAP 開啟。</span><span class="sxs-lookup"><span data-stu-id="70785-145">In some situations after rebuilding and starting your XBAP, you may find that an earlier version of the XBAP is opened.</span></span> <span data-ttu-id="70785-146">例如，當 XBAP 組件版本號碼是靜態的，且您從命令列啟動 XBAP 時，可能會發生這種行為。</span><span class="sxs-lookup"><span data-stu-id="70785-146">For example, this behavior may occur when your XBAP assembly version number is static and you start the XBAP from the command line.</span></span> <span data-ttu-id="70785-147">在此情況下，因為快取版本 (先前已啟動的版本) 與新版本之間的版本號碼維持不變，所以不會下載新版本的 XBAP。</span><span class="sxs-lookup"><span data-stu-id="70785-147">In this case, because the version number between the cached version (the version that was previously started) and the new version remains the same, the new version of the XBAP is not downloaded.</span></span> <span data-ttu-id="70785-148">相反地，會載入快取版本。</span><span class="sxs-lookup"><span data-stu-id="70785-148">Instead, the cached version is loaded.</span></span>  
  
 <span data-ttu-id="70785-149">在這些情況下，您可以藉由移除快取的版本**Mage**命令 （與 Visual Studio 或 Windows SDK 一起安裝），在命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="70785-149">In these situations, you can remove the cached version by using the **Mage** command (installed with Visual Studio or the Windows SDK) at the command prompt.</span></span> <span data-ttu-id="70785-150">下列命令會清除應用程式快取。</span><span class="sxs-lookup"><span data-stu-id="70785-150">The following command clears the application cache.</span></span>  
  
 ```console
 Mage.exe -cc
 ```
  
 <span data-ttu-id="70785-151">此命令可確保啟動最新版本的 XBAP。</span><span class="sxs-lookup"><span data-stu-id="70785-151">This command guarantees that the latest version of your XBAP is started.</span></span> <span data-ttu-id="70785-152">當您偵錯您的應用程式，在 Visual Studio 中時，應該會啟動最新版本的 XBAP。</span><span class="sxs-lookup"><span data-stu-id="70785-152">When you debug your application in Visual Studio, the latest version of your XBAP should be started.</span></span> <span data-ttu-id="70785-153">一般而言，您應該以每個組建更新您的部署版本號碼。</span><span class="sxs-lookup"><span data-stu-id="70785-153">In general, you should update your deployment version number with each build.</span></span> <span data-ttu-id="70785-154">如需 Mage 的詳細資訊，請參閱 [Mage.exe (資訊清單產生和編輯工具)](../../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="70785-154">For more information about Mage, see [Mage.exe (Manifest Generation and Editing Tool)](../../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md).</span></span>  
  
<a name="communicating_with_the_host_web_page"></a>   
## <a name="communicating-with-the-host-web-page"></a><span data-ttu-id="70785-155">與主機網頁通訊</span><span class="sxs-lookup"><span data-stu-id="70785-155">Communicating with the Host Web Page</span></span>  
 <span data-ttu-id="70785-156">當應用程式裝載在 HTML 框架中時，您可以與包含 XBAP 的網頁進行通訊。</span><span class="sxs-lookup"><span data-stu-id="70785-156">When the application is hosted in an HTML frame, you can communicate with the Web page that contains the XBAP.</span></span> <span data-ttu-id="70785-157">您可以擷取<xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A>屬性<xref:System.Windows.Interop.BrowserInteropHelper>。</span><span class="sxs-lookup"><span data-stu-id="70785-157">You do this by retrieving the <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> property of <xref:System.Windows.Interop.BrowserInteropHelper>.</span></span> <span data-ttu-id="70785-158">這個屬性會傳回代表 HTML 視窗的指令碼物件。</span><span class="sxs-lookup"><span data-stu-id="70785-158">This property returns a script object that represents the HTML window.</span></span> <span data-ttu-id="70785-159">您接著可以使用一般 dot 語法，在[視窗物件](https://go.microsoft.com/fwlink/?LinkId=160274)上存取屬性、方法和事件。</span><span class="sxs-lookup"><span data-stu-id="70785-159">You can then access the properties, methods, and events on the [window object](https://go.microsoft.com/fwlink/?LinkId=160274) by using regular dot syntax.</span></span> <span data-ttu-id="70785-160">您也可以存取指令碼方法和全域變數。</span><span class="sxs-lookup"><span data-stu-id="70785-160">You can also access script methods and global variables.</span></span> <span data-ttu-id="70785-161">下列範例示範如何擷取指令碼物件，並且關閉瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="70785-161">The following example shows how to retrieve the script object and close the browser.</span></span>  
  
 [!code-csharp[XbapBrowserInterop#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/xbapbrowserinterop/cs/page1.xaml.cs#10)]
 [!code-vb[XbapBrowserInterop#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/xbapbrowserinterop/vb/page1.xaml.vb#10)]  
  
### <a name="debugging-xbaps-that-use-hostscript"></a><span data-ttu-id="70785-162">針對使用 HostScript 的 XBAP 進行偵錯</span><span class="sxs-lookup"><span data-stu-id="70785-162">Debugging XBAPs that Use HostScript</span></span>  
 <span data-ttu-id="70785-163">如果您的 XBAP 使用<xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A>通訊 [HTML] 視窗中，有兩個設定，您必須指定執行和偵錯 Visual Studio 中的應用程式的物件。</span><span class="sxs-lookup"><span data-stu-id="70785-163">If your XBAP uses the <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> object to communicate with the HTML window, there are two settings that you must specify to run and debug the application in Visual Studio.</span></span> <span data-ttu-id="70785-164">應用程式必須能夠存取它的來源網站，而且您必須使用包含 XBAP 的 HTML 網頁來啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="70785-164">The application must have access to its site of origin and you must start the application with the HTML page that contains the XBAP.</span></span> <span data-ttu-id="70785-165">下列步驟說明如何檢查這兩項設定︰</span><span class="sxs-lookup"><span data-stu-id="70785-165">The following steps describe how to check these two settings:</span></span>  
  
1.  <span data-ttu-id="70785-166">在 Visual Studio 中，開啟專案屬性。</span><span class="sxs-lookup"><span data-stu-id="70785-166">In Visual Studio, open the project properties.</span></span>  
  
2.  <span data-ttu-id="70785-167">在 [安全性] 索引標籤上，按一下 [進階]。</span><span class="sxs-lookup"><span data-stu-id="70785-167">On the **Security** tab, click **Advanced**.</span></span>  
  
     <span data-ttu-id="70785-168">[進階安全性設定] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="70785-168">The Advanced Security Settings dialog box appears.</span></span>  
  
3.  <span data-ttu-id="70785-169">請確定 [允許應用程式存取它的來源網站] 核取方塊已勾選，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="70785-169">Make sure that the **Grant the application access to its site of origin** check box is checked and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="70785-170">在 [偵錯] 索引標籤上，選取 [瀏覽器起始 URL] 選項，並且指定包含 XBAP 之 HTML 網頁的 URL。</span><span class="sxs-lookup"><span data-stu-id="70785-170">On the **Debug** tab, select the **Start browser with URL** option and specify the URL for the HTML page that contains the XBAP.</span></span>  
  
5.  <span data-ttu-id="70785-171">在 Internet Explorer 中，按一下 [工具] 按鈕，然後選取 [網際網路選項]。</span><span class="sxs-lookup"><span data-stu-id="70785-171">In Internet Explorer, click the **Tools** button and then select **Internet Options**.</span></span>  
  
     <span data-ttu-id="70785-172">[網際網路選項] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="70785-172">The Internet Options dialog box appears.</span></span>  
  
6.  <span data-ttu-id="70785-173">按一下 [進階] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="70785-173">Click the **Advanced** tab.</span></span>  
  
7.  <span data-ttu-id="70785-174">在 [安全性] 底下的 [設定]清單中，勾選 [允許檔案中的主動式內容在我的電腦上執行] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="70785-174">In the **Settings** list under **Security**, check the **Allow active content to run in files on My Computer** check box.</span></span>  
  
8.  <span data-ttu-id="70785-175">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="70785-175">Click **OK**.</span></span>  
  
     <span data-ttu-id="70785-176">變更在重新啟動 Internet Explorer 之後才會生效。</span><span class="sxs-lookup"><span data-stu-id="70785-176">The changes will take effect after you restart Internet Explorer.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="70785-177">在 Internet Explorer 中啟用主動式內容可能會讓電腦面臨風險。</span><span class="sxs-lookup"><span data-stu-id="70785-177">Enabling active content in Internet Explorer may put your computer at risk.</span></span> <span data-ttu-id="70785-178">如果您不要變更 Internet Explorer 安全性設定，您可以啟動從伺服器 HTML 網頁，並將 Visual Studio 偵錯工具附加至處理程序。</span><span class="sxs-lookup"><span data-stu-id="70785-178">If you do not want to change your Internet Explorer security settings, you can launch the HTML page from a server and attach the Visual Studio debugger to the process.</span></span>  
  
<a name="xbap_security_considerations"></a>   
## <a name="xbap-security-considerations"></a><span data-ttu-id="70785-179">XBAP 安全性考量</span><span class="sxs-lookup"><span data-stu-id="70785-179">XBAP Security Considerations</span></span>  
 <span data-ttu-id="70785-180">XBAP 通常會在部分信任安全性沙箱中執行，它限制為網際網路區域權限集合。</span><span class="sxs-lookup"><span data-stu-id="70785-180">XBAPs typically execute in a partial-trust security sandbox that is restricted to the Internet zone permission set.</span></span> <span data-ttu-id="70785-181">因此，您的實作必須支援的支援在網際網路區域中的 WPF 項目子集，或您必須提高您的應用程式的權限。</span><span class="sxs-lookup"><span data-stu-id="70785-181">Consequently, your implementation must support the subset of WPF elements that are supported in the Internet zone or you must elevate the permissions of your application.</span></span> <span data-ttu-id="70785-182">如需詳細資訊，請參閱[安全性](../../../../docs/framework/wpf/security-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="70785-182">For more information, see [Security](../../../../docs/framework/wpf/security-wpf.md).</span></span>  
  
 <span data-ttu-id="70785-183">當您使用<xref:System.Windows.Controls.WebBrowser>應用程式中，WPF 控制項在內部具現化原生 WebBrowser ActiveX 控制項。</span><span class="sxs-lookup"><span data-stu-id="70785-183">When you use a <xref:System.Windows.Controls.WebBrowser> control in your application, WPF internally instantiates the native WebBrowser ActiveX control.</span></span> <span data-ttu-id="70785-184">當您的應用程式是在 Internet Explorer 中執行的部分信任 XBAP 時，ActiveX 控制項會在 Internet Explorer 流程的專用執行緒中執行。</span><span class="sxs-lookup"><span data-stu-id="70785-184">When your application is a partial-trust XBAP running in Internet Explorer, the ActiveX control runs in a dedicated thread of the Internet Explorer process.</span></span> <span data-ttu-id="70785-185">因此，會套用下列限制：</span><span class="sxs-lookup"><span data-stu-id="70785-185">Therefore, the following limitations apply:</span></span>  
  
-   <span data-ttu-id="70785-186"><xref:System.Windows.Controls.WebBrowser>控制項應該提供類似主機瀏覽器，包括安全性限制的行為。</span><span class="sxs-lookup"><span data-stu-id="70785-186">The <xref:System.Windows.Controls.WebBrowser> control should provide behavior similar to the host browser, including security restrictions.</span></span> <span data-ttu-id="70785-187">其中一些安全性限制可以透過 Internet Explorer 安全性設定來控制。</span><span class="sxs-lookup"><span data-stu-id="70785-187">Some of these security restrictions can be controlled through the Internet Explorer security settings.</span></span> <span data-ttu-id="70785-188">如需詳細資訊，請參閱[安全性](../../../../docs/framework/wpf/security-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="70785-188">For more information, see [Security](../../../../docs/framework/wpf/security-wpf.md).</span></span>  
  
-   <span data-ttu-id="70785-189">當 XBAP 在 HTML 網頁跨網域載入時，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="70785-189">An exception is thrown when an XBAP is loaded cross-domain in an HTML page.</span></span>  
  
-   <span data-ttu-id="70785-190">輸入是來自 WPF 的另一個執行緒上<xref:System.Windows.Controls.WebBrowser>，因此無法攔截鍵盤輸入，並不會共用 IME 狀態。</span><span class="sxs-lookup"><span data-stu-id="70785-190">Input is on a separate thread from the WPF <xref:System.Windows.Controls.WebBrowser>, so keyboard input cannot be intercepted and the IME state is not shared.</span></span>  
  
-   <span data-ttu-id="70785-191">因為在另一個執行緒上執行的 ActiveX 控制項，瀏覽的時間或順序可能不同。</span><span class="sxs-lookup"><span data-stu-id="70785-191">The timing or order of navigation may be different due to the ActiveX control running on another thread.</span></span> <span data-ttu-id="70785-192">例如，瀏覽至頁面不一定會因為啟動另一個瀏覽要求而取消。</span><span class="sxs-lookup"><span data-stu-id="70785-192">For example, navigating to a page is not always cancelled by starting another navigation request.</span></span>  
  
-   <span data-ttu-id="70785-193">自訂 ActiveX 控制項可能會遇到通訊問題，因為 WPF 應用程式是在個別執行緒中執行。</span><span class="sxs-lookup"><span data-stu-id="70785-193">A custom ActiveX control may have trouble with communication since the WPF application is running in a separate thread.</span></span>  
  
-   <span data-ttu-id="70785-194"><xref:System.Windows.Interop.HwndHost.MessageHook> 不會引發，因為<xref:System.Windows.Interop.HwndHost>無法在另一個執行緒或處理序中執行的視窗的子類別。</span><span class="sxs-lookup"><span data-stu-id="70785-194"><xref:System.Windows.Interop.HwndHost.MessageHook> does not get raised because <xref:System.Windows.Interop.HwndHost> cannot subclass a window running in another thread or process.</span></span>  
  
### <a name="creating-a-full-trust-xbap"></a><span data-ttu-id="70785-195">建立完全信任 XBAP</span><span class="sxs-lookup"><span data-stu-id="70785-195">Creating a Full-Trust XBAP</span></span>  
 <span data-ttu-id="70785-196">如果您的 XBAP 需要完全信任，您可以變更專案以啟用此權限。</span><span class="sxs-lookup"><span data-stu-id="70785-196">If your XBAP requires full trust, you can change your project to enable this permission.</span></span> <span data-ttu-id="70785-197">下列步驟描述如何啟用完全信任︰</span><span class="sxs-lookup"><span data-stu-id="70785-197">The following steps describe how to enable full trust:</span></span>  
  
1.  <span data-ttu-id="70785-198">在 Visual Studio 中，開啟專案屬性。</span><span class="sxs-lookup"><span data-stu-id="70785-198">In Visual Studio, open the project properties.</span></span>  
  
2.  <span data-ttu-id="70785-199">在 [安全性] 索引標籤上，選取 [這是完全信任的應用程式] 選項。</span><span class="sxs-lookup"><span data-stu-id="70785-199">On the **Security** tab, select the **This is a full trust application** option.</span></span>  
  
 <span data-ttu-id="70785-200">這項設定會進行下列變更︰</span><span class="sxs-lookup"><span data-stu-id="70785-200">This setting makes the following changes:</span></span>  
  
-   <span data-ttu-id="70785-201">在專案檔中，`<TargetZone>` 元素值變更為 `Custom`。</span><span class="sxs-lookup"><span data-stu-id="70785-201">In the project file, the `<TargetZone>` element value is changed to `Custom`.</span></span>  
  
-   <span data-ttu-id="70785-202">在應用程式資訊清單 (app.manifest) 中，`Unrestricted="true"` 屬性新增至 `PermissionSet` 元素。</span><span class="sxs-lookup"><span data-stu-id="70785-202">In the application manifest (app.manifest), an `Unrestricted="true"` attribute is added to the `PermissionSet` element.</span></span>  
  
    ```xml
    <PermissionSet class="System.Security.PermissionSet"   
                   version="1"   
                   ID="Custom"   
                   SameSite="site"   
                   Unrestricted="true" />  
    ```  
  
### <a name="deploying-a-full-trust-xbap"></a><span data-ttu-id="70785-203">部署完全信任 XBAP</span><span class="sxs-lookup"><span data-stu-id="70785-203">Deploying a Full-Trust XBAP</span></span>  
 <span data-ttu-id="70785-204">當您部署未遵循 ClickOnce 受信任部署模型的完全信任 XBAP 時，使用者執行應用程式時的行為將取決於安全性區域。</span><span class="sxs-lookup"><span data-stu-id="70785-204">When you deploy a full-trust XBAP that does not follow the ClickOnce Trusted Deployment model, the behavior when the user runs the application will depend on the security zone.</span></span> <span data-ttu-id="70785-205">在某些情況下，使用者會在嘗試安裝它時收到一則警告。</span><span class="sxs-lookup"><span data-stu-id="70785-205">In some cases, the user will receive a warning when they attempt to install it.</span></span> <span data-ttu-id="70785-206">使用者可以選擇繼續或取消安裝。</span><span class="sxs-lookup"><span data-stu-id="70785-206">The user can choose to continue or cancel the installation.</span></span> <span data-ttu-id="70785-207">下表描述每個安全性區域的應用程式行為，以及您必須針對應用程式執行什麼動作才能得到完全信任。</span><span class="sxs-lookup"><span data-stu-id="70785-207">The following table describes the behavior of the application for each security zone and what you have to do for the application to receive full trust.</span></span>  
  
|<span data-ttu-id="70785-208">安全性區域</span><span class="sxs-lookup"><span data-stu-id="70785-208">Security Zone</span></span>|<span data-ttu-id="70785-209">行為</span><span class="sxs-lookup"><span data-stu-id="70785-209">Behavior</span></span>|<span data-ttu-id="70785-210">取得完全信任</span><span class="sxs-lookup"><span data-stu-id="70785-210">Getting Full Trust</span></span>|  
|-------------------|--------------|------------------------|  
|<span data-ttu-id="70785-211">本機電腦</span><span class="sxs-lookup"><span data-stu-id="70785-211">Local computer</span></span>|<span data-ttu-id="70785-212">自動的完全信任</span><span class="sxs-lookup"><span data-stu-id="70785-212">Automatic full trust</span></span>|<span data-ttu-id="70785-213">不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="70785-213">No action is needed.</span></span>|  
|<span data-ttu-id="70785-214">內部網路和信任的網站</span><span class="sxs-lookup"><span data-stu-id="70785-214">Intranet and trusted sites</span></span>|<span data-ttu-id="70785-215">完全信任的提示</span><span class="sxs-lookup"><span data-stu-id="70785-215">Prompt for full trust</span></span>|<span data-ttu-id="70785-216">使用憑證簽署 XBAP，讓使用者在提示中看到來源。</span><span class="sxs-lookup"><span data-stu-id="70785-216">Sign the XBAP with a certificate so that the user sees the source in the prompt.</span></span>|  
|<span data-ttu-id="70785-217">網際網路</span><span class="sxs-lookup"><span data-stu-id="70785-217">Internet</span></span>|<span data-ttu-id="70785-218">因為「未授與信任」而失敗</span><span class="sxs-lookup"><span data-stu-id="70785-218">Fails with "Trust Not Granted"</span></span>|<span data-ttu-id="70785-219">使用憑證簽署 XBAP。</span><span class="sxs-lookup"><span data-stu-id="70785-219">Sign the XBAP with a certificate.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="70785-220">上表中描述的行為是針對未遵循 ClickOnce 受信任部署模型的完全信任 XBAP。</span><span class="sxs-lookup"><span data-stu-id="70785-220">The behavior described in the previous table is for full-trust XBAPs that do not follow the ClickOnce Trusted Deployment model.</span></span>  
  
 <span data-ttu-id="70785-221">建議您使用 ClickOnce 受信任部署模型來部署完全信任 XBAP。</span><span class="sxs-lookup"><span data-stu-id="70785-221">It is recommended that you use the ClickOnce Trusted Deployment model for deploying a full-trust XBAP.</span></span> <span data-ttu-id="70785-222">此模型可讓您的 XBAP 自動授與完全信任，無論安全性區域為何，因此系統不會提示使用者。</span><span class="sxs-lookup"><span data-stu-id="70785-222">This model allows your XBAP to be granted full trust automatically, regardless of the security zone, so that the user is not prompted.</span></span> <span data-ttu-id="70785-223">做為此模型的一部分，您必須使用受信任發行者的憑證來簽署應用程式。</span><span class="sxs-lookup"><span data-stu-id="70785-223">As part of this model, you must sign your application with a certificate from a trusted publisher.</span></span> <span data-ttu-id="70785-224">如需詳細資訊，請參閱[受信任應用程式部署概觀](/visualstudio/deployment/trusted-application-deployment-overview)和[程式碼簽署簡介](https://go.microsoft.com/fwlink/?LinkId=166327)。</span><span class="sxs-lookup"><span data-stu-id="70785-224">For more information, see [Trusted Application Deployment Overview](/visualstudio/deployment/trusted-application-deployment-overview) and [Introduction to Code Signing](https://go.microsoft.com/fwlink/?LinkId=166327).</span></span>  
  
<a name="xbap_start_time_performance_considerations"></a>   
## <a name="xbap-start-time-performance-considerations"></a><span data-ttu-id="70785-225">XBAP 開始時間效能考量</span><span class="sxs-lookup"><span data-stu-id="70785-225">XBAP Start Time Performance Considerations</span></span>  
 <span data-ttu-id="70785-226">XBAP 效能很重要的層面是其開始時間。</span><span class="sxs-lookup"><span data-stu-id="70785-226">An important aspect of XBAP performance is its start time.</span></span> <span data-ttu-id="70785-227">如果 XBAP 是載入的第一個 WPF 應用程式，「冷啟動」時間可以是 10 秒或以上。</span><span class="sxs-lookup"><span data-stu-id="70785-227">If an XBAP is the first WPF application to load, the *cold start* time can be ten seconds or more.</span></span> <span data-ttu-id="70785-228">這是因為進度頁面是由 WPF 轉譯，且 CLR 和 WPF 必須冷啟動來顯示應用程式。</span><span class="sxs-lookup"><span data-stu-id="70785-228">This is because the progress page is rendered by WPF, and both the CLR and WPF must be cold-started to display the application.</span></span>  
  
 <span data-ttu-id="70785-229">從 [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)] 開始，藉由在部署週期早期顯示 unmanaged 進度頁面，降低 XBAP 冷啟動時間。</span><span class="sxs-lookup"><span data-stu-id="70785-229">Starting in [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)], XBAP cold-start time is mitigated by displaying an unmanaged progress page early in the deployment cycle.</span></span> <span data-ttu-id="70785-230">進度頁面幾乎是在應用程式啟動之後立即出現，因為它是由原生裝載程式碼顯示，並且以 HTML 轉譯。</span><span class="sxs-lookup"><span data-stu-id="70785-230">The progress page appears almost immediately after the application is started, because it is displayed by native hosting code and rendered in HTML.</span></span>  
  
 <span data-ttu-id="70785-231">此外，ClickOnce 下載順序的改善的並行會改善最多 10%的開始時間。</span><span class="sxs-lookup"><span data-stu-id="70785-231">In addition, improved concurrency of the ClickOnce download sequence improves start time by up to ten percent.</span></span> <span data-ttu-id="70785-232">ClickOnce 下載和驗證之後資訊清單、 應用程式的下載會啟動，而進度列開始更新。</span><span class="sxs-lookup"><span data-stu-id="70785-232">After ClickOnce downloads and validates manifests, the application download starts, and the progress bar starts to update.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70785-233">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70785-233">See Also</span></span>  
 [<span data-ttu-id="70785-234">設定 Visual Studio 來偵錯 XAML 瀏覽器應用程式以呼叫 Web 服務</span><span class="sxs-lookup"><span data-stu-id="70785-234">Configure Visual Studio to Debug a XAML Browser Application to Call a Web Service</span></span>](../../../../docs/framework/wpf/app-development/configure-vs-to-debug-a-xaml-browser-to-call-a-web-service.md)  
 [<span data-ttu-id="70785-235">部署 WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="70785-235">Deploying a WPF Application</span></span>](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)
