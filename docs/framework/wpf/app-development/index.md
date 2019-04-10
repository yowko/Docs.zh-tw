---
title: 應用程式開發
ms.date: 01/26/2018
helpviewer_keywords:
- WPF [WPF], about application development
- application development [WPF], about
ms.assetid: 2996ce5e-81e9-49ae-881b-952db3dd1b7e
ms.openlocfilehash: 3b7e1d04173741088935104e8d4225691927a27b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211058"
---
# <a name="application-development"></a><span data-ttu-id="cf785-102">應用程式開發</span><span class="sxs-lookup"><span data-stu-id="cf785-102">Application Development</span></span>
<a name="introduction"></a> <span data-ttu-id="cf785-103">Windows Presentation Foundation (WPF) 是一種展示架構，可用來開發下列類型的應用程式：</span><span class="sxs-lookup"><span data-stu-id="cf785-103">Windows Presentation Foundation (WPF) is a presentation framework that can be used to develop the following types of applications:</span></span>  
  
-   <span data-ttu-id="cf785-104">獨立應用程式 (建置為可執行組件的傳統式 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 應用程式，這些應用程式會安裝到用戶端電腦並從中執行)。</span><span class="sxs-lookup"><span data-stu-id="cf785-104">Standalone Applications (traditional style [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] applications built as executable assemblies that are installed to and run from the client computer).</span></span>  
  
-   [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] <span data-ttu-id="cf785-105">(應用程式的建置為可執行檔的組件及這類裝載的網頁瀏覽器的瀏覽頁面組成[!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)]或 Mozilla Firefox)。</span><span class="sxs-lookup"><span data-stu-id="cf785-105">(applications composed of navigation pages that are built as executable assemblies and hosted by Web browsers such as [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] or Mozilla Firefox).</span></span>  
  
-   <span data-ttu-id="cf785-106">自訂控制項程式庫 (非可執行組件，其中包含可重複使用的控制項)。</span><span class="sxs-lookup"><span data-stu-id="cf785-106">Custom Control Libraries (non-executable assemblies containing reusable controls).</span></span>  
  
-   <span data-ttu-id="cf785-107">類別庫 (非可執行組件，其中包含可重複使用的類別)。</span><span class="sxs-lookup"><span data-stu-id="cf785-107">Class Libraries (non-executable assemblies that contain reusable classes).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cf785-108">強烈建議不要在 Windows 服務中使用 WPF 類型。</span><span class="sxs-lookup"><span data-stu-id="cf785-108">Using WPF types in a Windows service is strongly discouraged.</span></span> <span data-ttu-id="cf785-109">如果您嘗試在 Windows 服務中使用這些功能，它們可能無法如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="cf785-109">If you attempt to use these features in a Windows service, they may not work as expected.</span></span>  
  
 <span data-ttu-id="cf785-110">[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 會實作多項服務，以建置這組應用程式。</span><span class="sxs-lookup"><span data-stu-id="cf785-110">To build this set of applications, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] implements a host of services.</span></span> <span data-ttu-id="cf785-111">本主題提供這些服務的概觀，並說明何處可以找到更多資訊。</span><span class="sxs-lookup"><span data-stu-id="cf785-111">This topic provides an overview of these services and where to find more information.</span></span>  

<a name="Application_Management"></a>   
## <a name="application-management"></a><span data-ttu-id="cf785-112">應用程式管理</span><span class="sxs-lookup"><span data-stu-id="cf785-112">Application Management</span></span>  
 <span data-ttu-id="cf785-113">可執行的 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式通常需要一組核心功能，其中包括：</span><span class="sxs-lookup"><span data-stu-id="cf785-113">Executable [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications commonly require a core set of functionality that includes the following:</span></span>  
  
-   <span data-ttu-id="cf785-114">建立及管理通用應用程式基礎結構 (包括建立進入點方法和 Windows 訊息迴圈以接收系統和輸入訊息)。</span><span class="sxs-lookup"><span data-stu-id="cf785-114">Creating and managing common application infrastructure (including creating an entry point method and a Windows message loop to receive system and input messages).</span></span>  
  
-   <span data-ttu-id="cf785-115">追蹤應用程式存留期並與其互動。</span><span class="sxs-lookup"><span data-stu-id="cf785-115">Tracking and interacting with the lifetime of an application.</span></span>  
  
-   <span data-ttu-id="cf785-116">擷取及處理命令列參數。</span><span class="sxs-lookup"><span data-stu-id="cf785-116">Retrieving and processing command-line parameters.</span></span>  
  
-   <span data-ttu-id="cf785-117">共用應用程式範圍的屬性和 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]資源。</span><span class="sxs-lookup"><span data-stu-id="cf785-117">Sharing application-scope properties and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] resources.</span></span>  
  
-   <span data-ttu-id="cf785-118">偵測及處理未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="cf785-118">Detecting and processing unhandled exceptions.</span></span>  
  
-   <span data-ttu-id="cf785-119">傳回結束代碼。</span><span class="sxs-lookup"><span data-stu-id="cf785-119">Returning exit codes.</span></span>  
  
-   <span data-ttu-id="cf785-120">管理獨立應用程式中的視窗。</span><span class="sxs-lookup"><span data-stu-id="cf785-120">Managing windows in standalone applications.</span></span>  
  
-   <span data-ttu-id="cf785-121">追蹤 [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] 以及具有瀏覽視窗和框架之獨立應用程式中的瀏覽。</span><span class="sxs-lookup"><span data-stu-id="cf785-121">Tracking navigation in [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)], and standalone applications with navigation windows and frames.</span></span>  
  
 <span data-ttu-id="cf785-122">這些功能是由 <xref:System.Windows.Application> 類別實作，您可以使用「應用程式定義」將此類別新增至應用程式。</span><span class="sxs-lookup"><span data-stu-id="cf785-122">These capabilities are implemented by the <xref:System.Windows.Application> class, which you add to your applications using an *application definition*.</span></span>  
  
 <span data-ttu-id="cf785-123">如需詳細資訊，請參閱[應用程式管理概觀](application-management-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="cf785-123">For more information, see [Application Management Overview](application-management-overview.md).</span></span>  
  
<a name="WPF_Application_Resource__Content__and_Data_Files"></a>   
## <a name="wpf-application-resource-content-and-data-files"></a><span data-ttu-id="cf785-124">WPF 應用程式資源、內容和資料檔案</span><span class="sxs-lookup"><span data-stu-id="cf785-124">WPF Application Resource, Content, and Data Files</span></span>  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <span data-ttu-id="cf785-125">擴充核心支援在 Microsoft.NET Framework 中的內嵌資源具有支援的非可執行資料檔案的三種： 資源、 內容和資料。</span><span class="sxs-lookup"><span data-stu-id="cf785-125">extends the core support in the Microsoft .NET Framework for embedded resources with support for three kinds of non-executable data files: resource, content, and data.</span></span> <span data-ttu-id="cf785-126">如需詳細資訊，請參閱 [WPF 應用程式資源、內容和資料檔案](wpf-application-resource-content-and-data-files.md)。</span><span class="sxs-lookup"><span data-stu-id="cf785-126">For more information, see [WPF Application Resource, Content, and Data Files](wpf-application-resource-content-and-data-files.md).</span></span>  
  
 <span data-ttu-id="cf785-127">支援 WPF 非可執行資料檔案的關鍵之一，就是能夠使用唯一 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 來識別及載入這些檔案。</span><span class="sxs-lookup"><span data-stu-id="cf785-127">A key component of the support for WPF non-executable data files is the ability to identify and load them using a unique [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span> <span data-ttu-id="cf785-128">如需詳細資訊，請參閱 [WPF 中的 Pack URI](pack-uris-in-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="cf785-128">For more information, see [Pack URIs in WPF](pack-uris-in-wpf.md).</span></span>  
  
<a name="Windows_and_Dialog_Boxes"></a>   
## <a name="windows-and-dialog-boxes"></a><span data-ttu-id="cf785-129">視窗和對話方塊</span><span class="sxs-lookup"><span data-stu-id="cf785-129">Windows and Dialog Boxes</span></span>  
 <span data-ttu-id="cf785-130">使用者是透過視窗與 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 獨立應用程式互動。</span><span class="sxs-lookup"><span data-stu-id="cf785-130">Users interact with [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] standalone applications through windows.</span></span> <span data-ttu-id="cf785-131">視窗的用途是裝載應用程式內容，以及公開通常可讓使用者與內容互動的應用程式功能。</span><span class="sxs-lookup"><span data-stu-id="cf785-131">The purpose of a window is to host application content and expose application functionality that usually allows users to interact with the content.</span></span> <span data-ttu-id="cf785-132">在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中，視窗是由 <xref:System.Windows.Window> 類別封裝，該類別支援：</span><span class="sxs-lookup"><span data-stu-id="cf785-132">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], windows are encapsulated by the <xref:System.Windows.Window> class, which supports:</span></span>  
  
-   <span data-ttu-id="cf785-133">建立及顯示視窗。</span><span class="sxs-lookup"><span data-stu-id="cf785-133">Creating and showing windows.</span></span>  
  
-   <span data-ttu-id="cf785-134">建立主控視窗/附屬視窗的關聯性。</span><span class="sxs-lookup"><span data-stu-id="cf785-134">Establishing owner/owned window relationships.</span></span>  
  
-   <span data-ttu-id="cf785-135">設定視窗外觀 (例如大小、位置、圖示、標題列文字、框線)。</span><span class="sxs-lookup"><span data-stu-id="cf785-135">Configuring window appearance (for example, size, location, icons, title bar text, border).</span></span>  
  
-   <span data-ttu-id="cf785-136">追蹤視窗存留期並與其互動。</span><span class="sxs-lookup"><span data-stu-id="cf785-136">Tracking and interacting with the lifetime of a window.</span></span>  
  
 <span data-ttu-id="cf785-137">如需詳細資訊，請參閱 [WPF 視窗概觀](wpf-windows-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="cf785-137">For more information, see [WPF Windows Overview](wpf-windows-overview.md).</span></span>  
  
 <xref:System.Windows.Window> <span data-ttu-id="cf785-138">支援建立稱為 [對話方塊] 視窗的一種特殊類型的能力。</span><span class="sxs-lookup"><span data-stu-id="cf785-138">supports the ability to create a special type of window known as a dialog box.</span></span> <span data-ttu-id="cf785-139">您可以建立強制回應和非強制回應類型的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="cf785-139">Both modal and modeless types of dialog boxes can be created.</span></span>  
  
 <span data-ttu-id="cf785-140">為了方便起見，和可重複使用性和跨應用程式，提供一致的使用者體驗的優點[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]會公開三個常見的 [Windows] 對話方塊： <xref:Microsoft.Win32.OpenFileDialog>， <xref:Microsoft.Win32.SaveFileDialog>，和<xref:System.Windows.Controls.PrintDialog>。</span><span class="sxs-lookup"><span data-stu-id="cf785-140">For convenience, and the benefits of reusability and a consistent user experience across applications, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] exposes three of the common Windows dialog boxes: <xref:Microsoft.Win32.OpenFileDialog>, <xref:Microsoft.Win32.SaveFileDialog>, and <xref:System.Windows.Controls.PrintDialog>.</span></span>  
  
 <span data-ttu-id="cf785-141">訊息方塊是一種特殊的對話方塊類型，可將重要的文字資訊顯示給使用者，以及詢問簡單的「是/否/確定/取消」問題。</span><span class="sxs-lookup"><span data-stu-id="cf785-141">A message box is a special type of dialog box for showing important textual information to users, and for asking simple Yes/No/OK/Cancel questions.</span></span> <span data-ttu-id="cf785-142">您可以使用 <xref:System.Windows.MessageBox> 類別來建立及顯示訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="cf785-142">You use the <xref:System.Windows.MessageBox> class to create and show message boxes.</span></span>  
  
 <span data-ttu-id="cf785-143">如需詳細資訊，請參閱[對話方塊概觀](dialog-boxes-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="cf785-143">For more information, see [Dialog Boxes Overview](dialog-boxes-overview.md).</span></span>  
  
<a name="Navigation"></a>   
## <a name="navigation"></a><span data-ttu-id="cf785-144">巡覽</span><span class="sxs-lookup"><span data-stu-id="cf785-144">Navigation</span></span>  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <span data-ttu-id="cf785-145">支援使用頁面的 Web 式瀏覽 (<xref:System.Windows.Controls.Page>) 和超連結 (<xref:System.Windows.Documents.Hyperlink>)。</span><span class="sxs-lookup"><span data-stu-id="cf785-145">supports Web-style navigation using pages (<xref:System.Windows.Controls.Page>) and hyperlinks (<xref:System.Windows.Documents.Hyperlink>).</span></span> <span data-ttu-id="cf785-146">您可以透過各種方式來實作瀏覽，包括：</span><span class="sxs-lookup"><span data-stu-id="cf785-146">Navigation can be implemented in a variety of ways that include the following:</span></span>  
  
-   <span data-ttu-id="cf785-147">裝載於網頁瀏覽器的獨立頁面。</span><span class="sxs-lookup"><span data-stu-id="cf785-147">Standalone pages that are hosted in a Web browser.</span></span>  
  
-   <span data-ttu-id="cf785-148">編譯成裝載於網頁瀏覽器之 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 的頁面。</span><span class="sxs-lookup"><span data-stu-id="cf785-148">Pages compiled into an [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] that is hosted in a Web browser.</span></span>  
  
-   <span data-ttu-id="cf785-149">編譯成獨立應用程式並由瀏覽視窗 (<xref:System.Windows.Navigation.NavigationWindow>) 裝載的頁面。</span><span class="sxs-lookup"><span data-stu-id="cf785-149">Pages compiled into a standalone application and hosted by a navigation window (<xref:System.Windows.Navigation.NavigationWindow>).</span></span>  
  
-   <span data-ttu-id="cf785-150">由框架 (<xref:System.Windows.Controls.Frame>) 裝載的頁面，框架本身可以裝載於獨立頁面，或是編譯成 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 或獨立應用程式的頁面。</span><span class="sxs-lookup"><span data-stu-id="cf785-150">Pages that are hosted by a frame (<xref:System.Windows.Controls.Frame>), which may be hosted in a standalone page, or a page compiled into either an [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] or a standalone application.</span></span>  
  
 <span data-ttu-id="cf785-151">為了加速瀏覽，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 會實作下列項目：</span><span class="sxs-lookup"><span data-stu-id="cf785-151">To facilitate navigation, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] implements the following:</span></span>  
  
-   <xref:System.Windows.Navigation.NavigationService><span data-ttu-id="cf785-152">處理巡覽要求所使用的共用瀏覽引擎<xref:System.Windows.Controls.Frame>， <xref:System.Windows.Navigation.NavigationWindow>，和[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]來支援應用程式內部瀏覽。</span><span class="sxs-lookup"><span data-stu-id="cf785-152">, the shared navigation engine for processing navigation requests that is used by <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>, and [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] to support intra-application navigation.</span></span>  
  
-   <span data-ttu-id="cf785-153">要啟始瀏覽的瀏覽方法。</span><span class="sxs-lookup"><span data-stu-id="cf785-153">Navigation methods to initiate navigation.</span></span>  
  
-   <span data-ttu-id="cf785-154">要追蹤瀏覽存留期並與其互動的瀏覽事件。</span><span class="sxs-lookup"><span data-stu-id="cf785-154">Navigation events to track and interact with navigation lifetime.</span></span>  
  
-   <span data-ttu-id="cf785-155">使用日誌記住向後和向前瀏覽，該日誌也可供檢查和操作。</span><span class="sxs-lookup"><span data-stu-id="cf785-155">Remembering back and forward navigation using a journal, which can also be inspected and manipulated.</span></span>  
  
 <span data-ttu-id="cf785-156">如需相關資訊，請參閱[瀏覽概觀](navigation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="cf785-156">For information, see [Navigation Overview](navigation-overview.md).</span></span>  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <span data-ttu-id="cf785-157">也支援一種特殊的稱為結構化巡覽的巡覽。</span><span class="sxs-lookup"><span data-stu-id="cf785-157">also supports a special type of navigation known as structured navigation.</span></span> <span data-ttu-id="cf785-158">結構化瀏覽可用來呼叫一或多個頁面，這些頁面會以與呼叫函式一致的結構化且可預期方式傳回資料。</span><span class="sxs-lookup"><span data-stu-id="cf785-158">Structured navigation can be used to call one or more pages that return data in a structured and predictable way that is consistent with calling functions.</span></span> <span data-ttu-id="cf785-159">此功能相依於 <xref:System.Windows.Navigation.PageFunction%601> 類別，這在[結構化巡覽概觀](structured-navigation-overview.md)中將進一步說明。</span><span class="sxs-lookup"><span data-stu-id="cf785-159">This capability depends on the <xref:System.Windows.Navigation.PageFunction%601> class, which is described further in [Structured Navigation Overview](structured-navigation-overview.md).</span></span> <xref:System.Windows.Navigation.PageFunction%601> <span data-ttu-id="cf785-160">也可用來簡化建立中所述的複雜巡覽拓撲[巡覽拓撲概觀](navigation-topologies-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="cf785-160">also serves to simplify the creation of complex navigation topologies, which are described in [Navigation Topologies Overview](navigation-topologies-overview.md).</span></span>  
  
<a name="Hosting"></a>   
## <a name="hosting"></a><span data-ttu-id="cf785-161">裝載</span><span class="sxs-lookup"><span data-stu-id="cf785-161">Hosting</span></span>  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] <span data-ttu-id="cf785-162">可以裝載於[!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)]或 Firefox。</span><span class="sxs-lookup"><span data-stu-id="cf785-162">can be hosted in [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] or Firefox.</span></span> <span data-ttu-id="cf785-163">每個裝載模型有各自的一組考量和條件約束，[裝載](hosting-wpf-applications.md)中將進行說明。</span><span class="sxs-lookup"><span data-stu-id="cf785-163">Each hosting model has its own set of considerations and constraints that are covered in [Hosting](hosting-wpf-applications.md).</span></span>  
  
<a name="Build_and_Deploy"></a>   
## <a name="build-and-deploy"></a><span data-ttu-id="cf785-164">建置和部署</span><span class="sxs-lookup"><span data-stu-id="cf785-164">Build and Deploy</span></span>  
 <span data-ttu-id="cf785-165">雖然您可以從命令提示字元使用命令列編譯器建置簡單的 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式，但 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 與 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] 整合可提供更多支援來簡化開發和建置程序。</span><span class="sxs-lookup"><span data-stu-id="cf785-165">Although simple [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications can be built from a command prompt using command-line compilers, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] integrates with [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] to provide additional support that simplified the development and build process.</span></span> <span data-ttu-id="cf785-166">如需詳細資訊，請參閱[建置 WPF 應用程式](building-a-wpf-application-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="cf785-166">For more information, see [Building a WPF Application](building-a-wpf-application-wpf.md).</span></span>  
  
 <span data-ttu-id="cf785-167">根據您建置的應用程式類型，有一或多個部署選項可供選擇。</span><span class="sxs-lookup"><span data-stu-id="cf785-167">Depending on the type of application you build, there are one or more deployment options to choose from.</span></span> <span data-ttu-id="cf785-168">如需詳細資訊，請參閱[部署 WPF 應用程式](deploying-a-wpf-application-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="cf785-168">For more information, see [Deploying a WPF Application](deploying-a-wpf-application-wpf.md).</span></span>  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a><span data-ttu-id="cf785-169">相關主題</span><span class="sxs-lookup"><span data-stu-id="cf785-169">Related Topics</span></span>  
  
|<span data-ttu-id="cf785-170">標題</span><span class="sxs-lookup"><span data-stu-id="cf785-170">Title</span></span>|<span data-ttu-id="cf785-171">描述</span><span class="sxs-lookup"><span data-stu-id="cf785-171">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="cf785-172">應用程式管理概觀</span><span class="sxs-lookup"><span data-stu-id="cf785-172">Application Management Overview</span></span>](application-management-overview.md)|<span data-ttu-id="cf785-173">提供 <xref:System.Windows.Application> 類別的概觀，包括管理應用程式存留期、視窗、應用程式資源和瀏覽。</span><span class="sxs-lookup"><span data-stu-id="cf785-173">Provides an overview of the <xref:System.Windows.Application> class including managing application lifetime, windows, application resources, and navigation.</span></span>|  
|[<span data-ttu-id="cf785-174">WPF 中的視窗</span><span class="sxs-lookup"><span data-stu-id="cf785-174">Windows in WPF</span></span>](windows-in-wpf-applications.md)|<span data-ttu-id="cf785-175">提供在應用程式中管理視窗的詳細資料，包括如何使用 <xref:System.Windows.Window> 類別和對話方塊。</span><span class="sxs-lookup"><span data-stu-id="cf785-175">Provides details of managing windows in your application including how to use the <xref:System.Windows.Window> class and dialog boxes.</span></span>|  
|[<span data-ttu-id="cf785-176">巡覽概觀</span><span class="sxs-lookup"><span data-stu-id="cf785-176">Navigation Overview</span></span>](navigation-overview.md)|<span data-ttu-id="cf785-177">提供有關管理在應用程式頁面之間瀏覽的概觀。</span><span class="sxs-lookup"><span data-stu-id="cf785-177">Provides an overview of managing navigation between pages of your application.</span></span>|  
|[<span data-ttu-id="cf785-178">裝載</span><span class="sxs-lookup"><span data-stu-id="cf785-178">Hosting</span></span>](hosting-wpf-applications.md)|<span data-ttu-id="cf785-179">提供 [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] 的概觀。</span><span class="sxs-lookup"><span data-stu-id="cf785-179">Provides an overview of [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].</span></span>|  
|[<span data-ttu-id="cf785-180">建置和部署</span><span class="sxs-lookup"><span data-stu-id="cf785-180">Build and Deploy</span></span>](building-and-deploying-wpf-applications.md)|<span data-ttu-id="cf785-181">描述如何建置及部署 WPF 應用程式。</span><span class="sxs-lookup"><span data-stu-id="cf785-181">Describes how to build and deploy your WPF application.</span></span>|  
|[<span data-ttu-id="cf785-182">Visual Studio 中的 WPF 簡介</span><span class="sxs-lookup"><span data-stu-id="cf785-182">Introduction to WPF in Visual Studio</span></span>](../getting-started/introduction-to-wpf-in-vs.md)|<span data-ttu-id="cf785-183">描述 WPF 的主要功能。</span><span class="sxs-lookup"><span data-stu-id="cf785-183">Describes the main features of WPF.</span></span>|  
|[<span data-ttu-id="cf785-184">逐步解說：我的第一個 WPF 傳統型應用程式</span><span class="sxs-lookup"><span data-stu-id="cf785-184">Walkthrough: My first WPF desktop application</span></span>](../getting-started/walkthrough-my-first-wpf-desktop-application.md)|<span data-ttu-id="cf785-185">示範如何建立使用頁面瀏覽、配置、控制項、影像、樣式和繫結之 WPF 應用程式的逐步解說。</span><span class="sxs-lookup"><span data-stu-id="cf785-185">A walkthrough that shows how to create a WPF application using page navigation, layout, controls, images, styles, and binding.</span></span>|
