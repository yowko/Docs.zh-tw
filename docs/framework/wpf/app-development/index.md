---
title: 應用程式開發
ms.custom: ''
ms.date: 01/26/2018
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WPF [WPF], about application development
- application development [WPF], about
ms.assetid: 2996ce5e-81e9-49ae-881b-952db3dd1b7e
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 00161608997abc14202775c06ecfb283d8d67013
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="application-development"></a><span data-ttu-id="edc17-102">應用程式開發</span><span class="sxs-lookup"><span data-stu-id="edc17-102">Application Development</span></span>
<a name="introduction"></a>
<span data-ttu-id="edc17-103">[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 是可用來開發下列類型的應用程式的呈現架構：</span><span class="sxs-lookup"><span data-stu-id="edc17-103">[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] is a presentation framework that can be used to develop the following types of applications:</span></span>  
  
-   <span data-ttu-id="edc17-104">獨立應用程式 (建置為可執行組件的傳統式 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 應用程式，這些應用程式會安裝到用戶端電腦並從中執行)。</span><span class="sxs-lookup"><span data-stu-id="edc17-104">Standalone Applications (traditional style [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] applications built as executable assemblies that are installed to and run from the client computer).</span></span>  
  
-   [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]<span data-ttu-id="edc17-105"> (以瀏覽頁面組成的應用程式，這些應用程式會建置為可執行組件，並由 [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] 或 Mozilla Firefox 等網頁瀏覽器裝載)。</span><span class="sxs-lookup"><span data-stu-id="edc17-105"> (applications composed of navigation pages that are built as executable assemblies and hosted by Web browsers such as [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] or Mozilla Firefox).</span></span>  
  
-   <span data-ttu-id="edc17-106">自訂控制項程式庫 (非可執行組件，其中包含可重複使用的控制項)。</span><span class="sxs-lookup"><span data-stu-id="edc17-106">Custom Control Libraries (non-executable assemblies containing reusable controls).</span></span>  
  
-   <span data-ttu-id="edc17-107">類別庫 (非可執行組件，其中包含可重複使用的類別)。</span><span class="sxs-lookup"><span data-stu-id="edc17-107">Class Libraries (non-executable assemblies that contain reusable classes).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="edc17-108">強烈建議不要在 Windows 服務中使用 WPF 類型。</span><span class="sxs-lookup"><span data-stu-id="edc17-108">Using WPF types in a Windows service is strongly discouraged.</span></span> <span data-ttu-id="edc17-109">如果您嘗試在 Windows 服務中使用這些功能，它們可能無法如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="edc17-109">If you attempt to use these features in a Windows service, they may not work as expected.</span></span>  
  
 <span data-ttu-id="edc17-110">[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 會實作多項服務，以建置這組應用程式。</span><span class="sxs-lookup"><span data-stu-id="edc17-110">To build this set of applications, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] implements a host of services.</span></span> <span data-ttu-id="edc17-111">本主題提供這些服務的概觀，並說明何處可以找到更多資訊。</span><span class="sxs-lookup"><span data-stu-id="edc17-111">This topic provides an overview of these services and where to find more information.</span></span>  
  

  
<a name="Application_Management"></a>   
## <a name="application-management"></a><span data-ttu-id="edc17-112">應用程式管理</span><span class="sxs-lookup"><span data-stu-id="edc17-112">Application Management</span></span>  
 <span data-ttu-id="edc17-113">可執行的 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式通常需要一組核心功能，其中包括：</span><span class="sxs-lookup"><span data-stu-id="edc17-113">Executable [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications commonly require a core set of functionality that includes the following:</span></span>  
  
-   <span data-ttu-id="edc17-114">建立及管理通用應用程式基礎結構 (包括建立進入點方法和 Windows 訊息迴圈以接收系統和輸入訊息)。</span><span class="sxs-lookup"><span data-stu-id="edc17-114">Creating and managing common application infrastructure (including creating an entry point method and a Windows message loop to receive system and input messages).</span></span>  
  
-   <span data-ttu-id="edc17-115">追蹤應用程式存留期並與其互動。</span><span class="sxs-lookup"><span data-stu-id="edc17-115">Tracking and interacting with the lifetime of an application.</span></span>  
  
-   <span data-ttu-id="edc17-116">擷取及處理命令列參數。</span><span class="sxs-lookup"><span data-stu-id="edc17-116">Retrieving and processing command-line parameters.</span></span>  
  
-   <span data-ttu-id="edc17-117">共用應用程式範圍的屬性和 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]資源。</span><span class="sxs-lookup"><span data-stu-id="edc17-117">Sharing application-scope properties and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] resources.</span></span>  
  
-   <span data-ttu-id="edc17-118">偵測及處理未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="edc17-118">Detecting and processing unhandled exceptions.</span></span>  
  
-   <span data-ttu-id="edc17-119">傳回結束代碼。</span><span class="sxs-lookup"><span data-stu-id="edc17-119">Returning exit codes.</span></span>  
  
-   <span data-ttu-id="edc17-120">管理獨立應用程式中的視窗。</span><span class="sxs-lookup"><span data-stu-id="edc17-120">Managing windows in standalone applications.</span></span>  
  
-   <span data-ttu-id="edc17-121">追蹤 [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] 以及具有瀏覽視窗和框架之獨立應用程式中的瀏覽。</span><span class="sxs-lookup"><span data-stu-id="edc17-121">Tracking navigation in [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)], and standalone applications with navigation windows and frames.</span></span>  
  
 <span data-ttu-id="edc17-122">這些功能是由 <xref:System.Windows.Application> 類別實作，您可以使用「應用程式定義」將此類別新增至應用程式。</span><span class="sxs-lookup"><span data-stu-id="edc17-122">These capabilities are implemented by the <xref:System.Windows.Application> class, which you add to your applications using an *application definition*.</span></span>  
  
 <span data-ttu-id="edc17-123">如需詳細資訊，請參閱[應用程式管理概觀](../../../../docs/framework/wpf/app-development/application-management-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="edc17-123">For more information, see [Application Management Overview](../../../../docs/framework/wpf/app-development/application-management-overview.md).</span></span>  
  
<a name="WPF_Application_Resource__Content__and_Data_Files"></a>   
## <a name="wpf-application-resource-content-and-data-files"></a><span data-ttu-id="edc17-124">WPF 應用程式資源、內容和資料檔案</span><span class="sxs-lookup"><span data-stu-id="edc17-124">WPF Application Resource, Content, and Data Files</span></span>  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="edc17-125"> 將延伸內嵌資源的 Microsoft.NET Framework 中的核心支援，可以支援三種類型的非可執行檔的資料檔案： 資源、 內容和資料。</span><span class="sxs-lookup"><span data-stu-id="edc17-125"> extends the core support in the Microsoft .NET Framework for embedded resources with support for three kinds of non-executable data files: resource, content, and data.</span></span> <span data-ttu-id="edc17-126">如需詳細資訊，請參閱 [WPF 應用程式資源、內容和資料檔案](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)。</span><span class="sxs-lookup"><span data-stu-id="edc17-126">For more information, see [WPF Application Resource, Content, and Data Files](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).</span></span>  
  
 <span data-ttu-id="edc17-127">支援 WPF 非可執行資料檔案的關鍵之一，就是能夠使用唯一 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 來識別及載入這些檔案。</span><span class="sxs-lookup"><span data-stu-id="edc17-127">A key component of the support for WPF non-executable data files is the ability to identify and load them using a unique [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span> <span data-ttu-id="edc17-128">如需詳細資訊，請參閱 [WPF 中的 Pack URI](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="edc17-128">For more information, see [Pack URIs in WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md).</span></span>  
  
<a name="Windows_and_Dialog_Boxes"></a>   
## <a name="windows-and-dialog-boxes"></a><span data-ttu-id="edc17-129">視窗和對話方塊</span><span class="sxs-lookup"><span data-stu-id="edc17-129">Windows and Dialog Boxes</span></span>  
 <span data-ttu-id="edc17-130">使用者是透過視窗與 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 獨立應用程式互動。</span><span class="sxs-lookup"><span data-stu-id="edc17-130">Users interact with [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] standalone applications through windows.</span></span> <span data-ttu-id="edc17-131">視窗的用途是裝載應用程式內容，以及公開通常可讓使用者與內容互動的應用程式功能。</span><span class="sxs-lookup"><span data-stu-id="edc17-131">The purpose of a window is to host application content and expose application functionality that usually allows users to interact with the content.</span></span> <span data-ttu-id="edc17-132">在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中，視窗是由 <xref:System.Windows.Window> 類別封裝，該類別支援：</span><span class="sxs-lookup"><span data-stu-id="edc17-132">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], windows are encapsulated by the <xref:System.Windows.Window> class, which supports:</span></span>  
  
-   <span data-ttu-id="edc17-133">建立及顯示視窗。</span><span class="sxs-lookup"><span data-stu-id="edc17-133">Creating and showing windows.</span></span>  
  
-   <span data-ttu-id="edc17-134">建立主控視窗/附屬視窗的關聯性。</span><span class="sxs-lookup"><span data-stu-id="edc17-134">Establishing owner/owned window relationships.</span></span>  
  
-   <span data-ttu-id="edc17-135">設定視窗外觀 (例如大小、位置、圖示、標題列文字、框線)。</span><span class="sxs-lookup"><span data-stu-id="edc17-135">Configuring window appearance (for example, size, location, icons, title bar text, border).</span></span>  
  
-   <span data-ttu-id="edc17-136">追蹤視窗存留期並與其互動。</span><span class="sxs-lookup"><span data-stu-id="edc17-136">Tracking and interacting with the lifetime of a window.</span></span>  
  
 <span data-ttu-id="edc17-137">如需詳細資訊，請參閱 [WPF 視窗概觀](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="edc17-137">For more information, see [WPF Windows Overview](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md).</span></span>  
  
 <span data-ttu-id="edc17-138"><xref:System.Windows.Window> 可建立一種特殊的視窗類型，稱為對話方塊。</span><span class="sxs-lookup"><span data-stu-id="edc17-138"><xref:System.Windows.Window> supports the ability to create a special type of window known as a dialog box.</span></span> <span data-ttu-id="edc17-139">您可以建立強制回應和非強制回應類型的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="edc17-139">Both modal and modeless types of dialog boxes can be created.</span></span>  
  
 <span data-ttu-id="edc17-140">為方便起見，並重複使用性和跨應用程式，以一致的使用者經驗的優點[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]會公開三個一般的 [Windows] 對話方塊： <xref:Microsoft.Win32.OpenFileDialog>， <xref:Microsoft.Win32.SaveFileDialog>，和<xref:System.Windows.Controls.PrintDialog>。</span><span class="sxs-lookup"><span data-stu-id="edc17-140">For convenience, and the benefits of reusability and a consistent user experience across applications, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] exposes three of the common Windows dialog boxes: <xref:Microsoft.Win32.OpenFileDialog>, <xref:Microsoft.Win32.SaveFileDialog>, and <xref:System.Windows.Controls.PrintDialog>.</span></span>  
  
 <span data-ttu-id="edc17-141">訊息方塊是一種特殊的對話方塊類型，可將重要的文字資訊顯示給使用者，以及詢問簡單的「是/否/確定/取消」問題。</span><span class="sxs-lookup"><span data-stu-id="edc17-141">A message box is a special type of dialog box for showing important textual information to users, and for asking simple Yes/No/OK/Cancel questions.</span></span> <span data-ttu-id="edc17-142">您可以使用 <xref:System.Windows.MessageBox> 類別來建立及顯示訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="edc17-142">You use the <xref:System.Windows.MessageBox> class to create and show message boxes.</span></span>  
  
 <span data-ttu-id="edc17-143">如需詳細資訊，請參閱[對話方塊概觀](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="edc17-143">For more information, see [Dialog Boxes Overview](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md).</span></span>  
  
<a name="Navigation"></a>   
## <a name="navigation"></a><span data-ttu-id="edc17-144">巡覽</span><span class="sxs-lookup"><span data-stu-id="edc17-144">Navigation</span></span>  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="edc17-145"> 支援使用頁面 (<xref:System.Windows.Controls.Page>) 和超連結 (<xref:System.Windows.Documents.Hyperlink>) 的 Web 式瀏覽。</span><span class="sxs-lookup"><span data-stu-id="edc17-145"> supports Web-style navigation using pages (<xref:System.Windows.Controls.Page>) and hyperlinks (<xref:System.Windows.Documents.Hyperlink>).</span></span> <span data-ttu-id="edc17-146">您可以透過各種方式來實作瀏覽，包括：</span><span class="sxs-lookup"><span data-stu-id="edc17-146">Navigation can be implemented in a variety of ways that include the following:</span></span>  
  
-   <span data-ttu-id="edc17-147">裝載於網頁瀏覽器的獨立頁面。</span><span class="sxs-lookup"><span data-stu-id="edc17-147">Standalone pages that are hosted in a Web browser.</span></span>  
  
-   <span data-ttu-id="edc17-148">編譯成裝載於網頁瀏覽器之 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 的頁面。</span><span class="sxs-lookup"><span data-stu-id="edc17-148">Pages compiled into an [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] that is hosted in a Web browser.</span></span>  
  
-   <span data-ttu-id="edc17-149">編譯成獨立應用程式並由瀏覽視窗 (<xref:System.Windows.Navigation.NavigationWindow>) 裝載的頁面。</span><span class="sxs-lookup"><span data-stu-id="edc17-149">Pages compiled into a standalone application and hosted by a navigation window (<xref:System.Windows.Navigation.NavigationWindow>).</span></span>  
  
-   <span data-ttu-id="edc17-150">由框架 (<xref:System.Windows.Controls.Frame>) 裝載的頁面，框架本身可以裝載於獨立頁面，或是編譯成 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 或獨立應用程式的頁面。</span><span class="sxs-lookup"><span data-stu-id="edc17-150">Pages that are hosted by a frame (<xref:System.Windows.Controls.Frame>), which may be hosted in a standalone page, or a page compiled into either an [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] or a standalone application.</span></span>  
  
 <span data-ttu-id="edc17-151">為了加速瀏覽，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 會實作下列項目：</span><span class="sxs-lookup"><span data-stu-id="edc17-151">To facilitate navigation, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] implements the following:</span></span>  
  
-   <span data-ttu-id="edc17-152"><xref:System.Windows.Navigation.NavigationService>，這是處理瀏覽要求的共用瀏覽引擎，可供 <xref:System.Windows.Controls.Frame>、<xref:System.Windows.Navigation.NavigationWindow> 和 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 用來支援應用程式內的瀏覽。</span><span class="sxs-lookup"><span data-stu-id="edc17-152"><xref:System.Windows.Navigation.NavigationService>, the shared navigation engine for processing navigation requests that is used by <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>, and [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] to support intra-application navigation.</span></span>  
  
-   <span data-ttu-id="edc17-153">要啟始瀏覽的瀏覽方法。</span><span class="sxs-lookup"><span data-stu-id="edc17-153">Navigation methods to initiate navigation.</span></span>  
  
-   <span data-ttu-id="edc17-154">要追蹤瀏覽存留期並與其互動的瀏覽事件。</span><span class="sxs-lookup"><span data-stu-id="edc17-154">Navigation events to track and interact with navigation lifetime.</span></span>  
  
-   <span data-ttu-id="edc17-155">使用日誌記住向後和向前瀏覽，該日誌也可供檢查和操作。</span><span class="sxs-lookup"><span data-stu-id="edc17-155">Remembering back and forward navigation using a journal, which can also be inspected and manipulated.</span></span>  
  
 <span data-ttu-id="edc17-156">如需相關資訊，請參閱[瀏覽概觀](../../../../docs/framework/wpf/app-development/navigation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="edc17-156">For information, see [Navigation Overview](../../../../docs/framework/wpf/app-development/navigation-overview.md).</span></span>  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="edc17-157"> 也支援一種特殊的瀏覽類型，稱為結構化瀏覽。</span><span class="sxs-lookup"><span data-stu-id="edc17-157"> also supports a special type of navigation known as structured navigation.</span></span> <span data-ttu-id="edc17-158">結構化瀏覽可用來呼叫一或多個頁面，這些頁面會以與呼叫函式一致的結構化且可預期方式傳回資料。</span><span class="sxs-lookup"><span data-stu-id="edc17-158">Structured navigation can be used to call one or more pages that return data in a structured and predictable way that is consistent with calling functions.</span></span> <span data-ttu-id="edc17-159">此功能相依於 <xref:System.Windows.Navigation.PageFunction%601> 類別，這在[結構化巡覽概觀](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md)中將進一步說明。</span><span class="sxs-lookup"><span data-stu-id="edc17-159">This capability depends on the <xref:System.Windows.Navigation.PageFunction%601> class, which is described further in [Structured Navigation Overview](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md).</span></span> <span data-ttu-id="edc17-160"><xref:System.Windows.Navigation.PageFunction%601> 也可用來簡化複雜瀏覽拓撲的建立，這在[巡覽拓撲概觀](../../../../docs/framework/wpf/app-development/navigation-topologies-overview.md)中將進行說明。</span><span class="sxs-lookup"><span data-stu-id="edc17-160"><xref:System.Windows.Navigation.PageFunction%601> also serves to simplify the creation of complex navigation topologies, which are described in [Navigation Topologies Overview](../../../../docs/framework/wpf/app-development/navigation-topologies-overview.md).</span></span>  
  
<a name="Hosting"></a>   
## <a name="hosting"></a><span data-ttu-id="edc17-161">裝載</span><span class="sxs-lookup"><span data-stu-id="edc17-161">Hosting</span></span>  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]<span data-ttu-id="edc17-162"> 可以裝載於 [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] 或 Firefox。</span><span class="sxs-lookup"><span data-stu-id="edc17-162"> can be hosted in [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] or Firefox.</span></span> <span data-ttu-id="edc17-163">每個裝載模型有各自的一組考量和條件約束，[裝載](../../../../docs/framework/wpf/app-development/hosting-wpf-applications.md)中將進行說明。</span><span class="sxs-lookup"><span data-stu-id="edc17-163">Each hosting model has its own set of considerations and constraints that are covered in [Hosting](../../../../docs/framework/wpf/app-development/hosting-wpf-applications.md).</span></span>  
  
<a name="Build_and_Deploy"></a>   
## <a name="build-and-deploy"></a><span data-ttu-id="edc17-164">建置和部署</span><span class="sxs-lookup"><span data-stu-id="edc17-164">Build and Deploy</span></span>  
 <span data-ttu-id="edc17-165">雖然您可以從命令提示字元使用命令列編譯器建置簡單的 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式，但 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 與 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] 整合可提供更多支援來簡化開發和建置程序。</span><span class="sxs-lookup"><span data-stu-id="edc17-165">Although simple [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications can be built from a command prompt using command-line compilers, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] integrates with [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] to provide additional support that simplified the development and build process.</span></span> <span data-ttu-id="edc17-166">如需詳細資訊，請參閱[建置 WPF 應用程式](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="edc17-166">For more information, see [Building a WPF Application](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md).</span></span>  
  
 <span data-ttu-id="edc17-167">根據您建置的應用程式類型，有一或多個部署選項可供選擇。</span><span class="sxs-lookup"><span data-stu-id="edc17-167">Depending on the type of application you build, there are one or more deployment options to choose from.</span></span> <span data-ttu-id="edc17-168">如需詳細資訊，請參閱[部署 WPF 應用程式](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="edc17-168">For more information, see [Deploying a WPF Application](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md).</span></span>  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a><span data-ttu-id="edc17-169">相關主題</span><span class="sxs-lookup"><span data-stu-id="edc17-169">Related Topics</span></span>  
  
|<span data-ttu-id="edc17-170">標題</span><span class="sxs-lookup"><span data-stu-id="edc17-170">Title</span></span>|<span data-ttu-id="edc17-171">描述</span><span class="sxs-lookup"><span data-stu-id="edc17-171">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="edc17-172">應用程式管理概觀</span><span class="sxs-lookup"><span data-stu-id="edc17-172">Application Management Overview</span></span>](../../../../docs/framework/wpf/app-development/application-management-overview.md)|<span data-ttu-id="edc17-173">提供 <xref:System.Windows.Application> 類別的概觀，包括管理應用程式存留期、視窗、應用程式資源和瀏覽。</span><span class="sxs-lookup"><span data-stu-id="edc17-173">Provides an overview of the <xref:System.Windows.Application> class including managing application lifetime, windows, application resources, and navigation.</span></span>|  
|[<span data-ttu-id="edc17-174">WPF 中的視窗</span><span class="sxs-lookup"><span data-stu-id="edc17-174">Windows in WPF</span></span>](../../../../docs/framework/wpf/app-development/windows-in-wpf-applications.md)|<span data-ttu-id="edc17-175">提供在應用程式中管理視窗的詳細資料，包括如何使用 <xref:System.Windows.Window> 類別和對話方塊。</span><span class="sxs-lookup"><span data-stu-id="edc17-175">Provides details of managing windows in your application including how to use the <xref:System.Windows.Window> class and dialog boxes.</span></span>|  
|[<span data-ttu-id="edc17-176">瀏覽概觀</span><span class="sxs-lookup"><span data-stu-id="edc17-176">Navigation Overview</span></span>](../../../../docs/framework/wpf/app-development/navigation-overview.md)|<span data-ttu-id="edc17-177">提供有關管理在應用程式頁面之間瀏覽的概觀。</span><span class="sxs-lookup"><span data-stu-id="edc17-177">Provides an overview of managing navigation between pages of your application.</span></span>|  
|[<span data-ttu-id="edc17-178">裝載</span><span class="sxs-lookup"><span data-stu-id="edc17-178">Hosting</span></span>](../../../../docs/framework/wpf/app-development/hosting-wpf-applications.md)|<span data-ttu-id="edc17-179">提供 [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] 的概觀。</span><span class="sxs-lookup"><span data-stu-id="edc17-179">Provides an overview of [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].</span></span>|  
|[<span data-ttu-id="edc17-180">建置和部署</span><span class="sxs-lookup"><span data-stu-id="edc17-180">Build and Deploy</span></span>](../../../../docs/framework/wpf/app-development/building-and-deploying-wpf-applications.md)|<span data-ttu-id="edc17-181">描述如何建置及部署 WPF 應用程式。</span><span class="sxs-lookup"><span data-stu-id="edc17-181">Describes how to build and deploy your WPF application.</span></span>|  
|[<span data-ttu-id="edc17-182">Visual Studio 中的 WPF 簡介</span><span class="sxs-lookup"><span data-stu-id="edc17-182">Introduction to WPF in Visual Studio</span></span>](../../../../docs/framework/wpf/getting-started/introduction-to-wpf-in-vs.md)|<span data-ttu-id="edc17-183">描述 WPF 的主要功能。</span><span class="sxs-lookup"><span data-stu-id="edc17-183">Describes the main features of WPF.</span></span>|  
|[<span data-ttu-id="edc17-184">逐步解說：我的第一個 WPF 傳統型應用程式</span><span class="sxs-lookup"><span data-stu-id="edc17-184">Walkthrough: My first WPF desktop application</span></span>](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)|<span data-ttu-id="edc17-185">示範如何建立使用頁面瀏覽、配置、控制項、影像、樣式和繫結之 WPF 應用程式的逐步解說。</span><span class="sxs-lookup"><span data-stu-id="edc17-185">A walkthrough that shows how to create a WPF application using page navigation, layout, controls, images, styles, and binding.</span></span>|
