---
title: 應用程式開發
ms.date: 01/26/2018
helpviewer_keywords:
- WPF [WPF], about application development
- application development [WPF], about
ms.assetid: 2996ce5e-81e9-49ae-881b-952db3dd1b7e
ms.openlocfilehash: b0bdf49e0bb3d9bfa3fc4e7fd94aa68ee4ea0bb3
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636389"
---
# <a name="application-development"></a><span data-ttu-id="67e08-102">應用程式開發</span><span class="sxs-lookup"><span data-stu-id="67e08-102">Application Development</span></span>
<a name="introduction"></a><span data-ttu-id="67e08-103">Windows Presentation Foundation （WPF）是一種呈現架構，可用來開發下列類型的應用程式：</span><span class="sxs-lookup"><span data-stu-id="67e08-103">Windows Presentation Foundation (WPF) is a presentation framework that can be used to develop the following types of applications:</span></span>  
  
- <span data-ttu-id="67e08-104">獨立應用程式（傳統樣式的 Windows 應用程式，建作為可執行元件，並從用戶端電腦執行）。</span><span class="sxs-lookup"><span data-stu-id="67e08-104">Standalone Applications (traditional style Windows applications built as executable assemblies that are installed to and run from the client computer).</span></span>  
  
- <span data-ttu-id="67e08-105">XAML 瀏覽器應用程式（Xbap）（這些應用程式是由建立為可執行元件並由網頁瀏覽器（例如 Microsoft Internet Explorer 或 Mozilla Firefox）所主控的導覽頁面所組成）。</span><span class="sxs-lookup"><span data-stu-id="67e08-105">XAML browser applications (XBAPs) (applications composed of navigation pages that are built as executable assemblies and hosted by Web browsers such as Microsoft Internet Explorer or Mozilla Firefox).</span></span>  
  
- <span data-ttu-id="67e08-106">自訂控制項程式庫 (非可執行組件，其中包含可重複使用的控制項)。</span><span class="sxs-lookup"><span data-stu-id="67e08-106">Custom Control Libraries (non-executable assemblies containing reusable controls).</span></span>  
  
- <span data-ttu-id="67e08-107">類別庫 (非可執行組件，其中包含可重複使用的類別)。</span><span class="sxs-lookup"><span data-stu-id="67e08-107">Class Libraries (non-executable assemblies that contain reusable classes).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="67e08-108">強烈建議不要在 Windows 服務中使用 WPF 類型。</span><span class="sxs-lookup"><span data-stu-id="67e08-108">Using WPF types in a Windows service is strongly discouraged.</span></span> <span data-ttu-id="67e08-109">如果您嘗試在 Windows 服務中使用這些功能，它們可能無法如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="67e08-109">If you attempt to use these features in a Windows service, they may not work as expected.</span></span>  
  
 <span data-ttu-id="67e08-110">為了建立這組應用程式，WPF 會執行服務的主機。</span><span class="sxs-lookup"><span data-stu-id="67e08-110">To build this set of applications, WPF implements a host of services.</span></span> <span data-ttu-id="67e08-111">本主題提供這些服務的概觀，並說明何處可以找到更多資訊。</span><span class="sxs-lookup"><span data-stu-id="67e08-111">This topic provides an overview of these services and where to find more information.</span></span>  

<a name="Application_Management"></a>   
## <a name="application-management"></a><span data-ttu-id="67e08-112">應用程式管理</span><span class="sxs-lookup"><span data-stu-id="67e08-112">Application Management</span></span>  
 <span data-ttu-id="67e08-113">可執行檔 WPF 應用程式通常需要一組核心功能，包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="67e08-113">Executable WPF applications commonly require a core set of functionality that includes the following:</span></span>  
  
- <span data-ttu-id="67e08-114">建立及管理通用應用程式基礎結構 (包括建立進入點方法和 Windows 訊息迴圈以接收系統和輸入訊息)。</span><span class="sxs-lookup"><span data-stu-id="67e08-114">Creating and managing common application infrastructure (including creating an entry point method and a Windows message loop to receive system and input messages).</span></span>  
  
- <span data-ttu-id="67e08-115">追蹤應用程式存留期並與其互動。</span><span class="sxs-lookup"><span data-stu-id="67e08-115">Tracking and interacting with the lifetime of an application.</span></span>  
  
- <span data-ttu-id="67e08-116">擷取及處理命令列參數。</span><span class="sxs-lookup"><span data-stu-id="67e08-116">Retrieving and processing command-line parameters.</span></span>  
  
- <span data-ttu-id="67e08-117">共用應用程式範圍的屬性和 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]資源。</span><span class="sxs-lookup"><span data-stu-id="67e08-117">Sharing application-scope properties and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] resources.</span></span>  
  
- <span data-ttu-id="67e08-118">偵測及處理未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="67e08-118">Detecting and processing unhandled exceptions.</span></span>  
  
- <span data-ttu-id="67e08-119">傳回結束代碼。</span><span class="sxs-lookup"><span data-stu-id="67e08-119">Returning exit codes.</span></span>  
  
- <span data-ttu-id="67e08-120">管理獨立應用程式中的視窗。</span><span class="sxs-lookup"><span data-stu-id="67e08-120">Managing windows in standalone applications.</span></span>  
  
- <span data-ttu-id="67e08-121">追蹤 XAML 瀏覽器應用程式（Xbap）中的導覽，以及具有流覽視窗和框架的獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="67e08-121">Tracking navigation in XAML browser applications (XBAPs), and standalone applications with navigation windows and frames.</span></span>  
  
 <span data-ttu-id="67e08-122">這些功能是由 <xref:System.Windows.Application> 類別實作，您可以使用「應用程式定義」將此類別新增至應用程式。</span><span class="sxs-lookup"><span data-stu-id="67e08-122">These capabilities are implemented by the <xref:System.Windows.Application> class, which you add to your applications using an *application definition*.</span></span>  
  
 <span data-ttu-id="67e08-123">如需詳細資訊，請參閱[應用程式管理概觀](application-management-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="67e08-123">For more information, see [Application Management Overview](application-management-overview.md).</span></span>  
  
<a name="WPF_Application_Resource__Content__and_Data_Files"></a>   
## <a name="wpf-application-resource-content-and-data-files"></a><span data-ttu-id="67e08-124">WPF 應用程式資源、內容和資料檔案</span><span class="sxs-lookup"><span data-stu-id="67e08-124">WPF Application Resource, Content, and Data Files</span></span>  
 <span data-ttu-id="67e08-125">WPF 在 Microsoft .NET Framework 中擴充了內嵌資源的核心支援，支援三種無法執行的資料檔案：資源、內容和資料。</span><span class="sxs-lookup"><span data-stu-id="67e08-125">WPF extends the core support in the Microsoft .NET Framework for embedded resources with support for three kinds of non-executable data files: resource, content, and data.</span></span> <span data-ttu-id="67e08-126">如需詳細資訊，請參閱 [WPF 應用程式資源、內容和資料檔案](wpf-application-resource-content-and-data-files.md)。</span><span class="sxs-lookup"><span data-stu-id="67e08-126">For more information, see [WPF Application Resource, Content, and Data Files](wpf-application-resource-content-and-data-files.md).</span></span>  
  
 <span data-ttu-id="67e08-127">WPF 無法執行的資料檔案支援的主要元件，是使用唯一的 URI 來識別和載入它們的能力。</span><span class="sxs-lookup"><span data-stu-id="67e08-127">A key component of the support for WPF non-executable data files is the ability to identify and load them using a unique URI.</span></span> <span data-ttu-id="67e08-128">如需詳細資訊，請參閱 [WPF 中的 Pack URI](pack-uris-in-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="67e08-128">For more information, see [Pack URIs in WPF](pack-uris-in-wpf.md).</span></span>  
  
<a name="Windows_and_Dialog_Boxes"></a>   
## <a name="windows-and-dialog-boxes"></a><span data-ttu-id="67e08-129">視窗和對話方塊</span><span class="sxs-lookup"><span data-stu-id="67e08-129">Windows and Dialog Boxes</span></span>  
 <span data-ttu-id="67e08-130">使用者透過 windows 與 WPF 獨立應用程式互動。</span><span class="sxs-lookup"><span data-stu-id="67e08-130">Users interact with WPF standalone applications through windows.</span></span> <span data-ttu-id="67e08-131">視窗的用途是裝載應用程式內容，以及公開通常可讓使用者與內容互動的應用程式功能。</span><span class="sxs-lookup"><span data-stu-id="67e08-131">The purpose of a window is to host application content and expose application functionality that usually allows users to interact with the content.</span></span> <span data-ttu-id="67e08-132">在 WPF 中，windows 是由 <xref:System.Windows.Window> 類別封裝，它支援：</span><span class="sxs-lookup"><span data-stu-id="67e08-132">In WPF, windows are encapsulated by the <xref:System.Windows.Window> class, which supports:</span></span>  
  
- <span data-ttu-id="67e08-133">建立及顯示視窗。</span><span class="sxs-lookup"><span data-stu-id="67e08-133">Creating and showing windows.</span></span>  
  
- <span data-ttu-id="67e08-134">建立主控視窗/附屬視窗的關聯性。</span><span class="sxs-lookup"><span data-stu-id="67e08-134">Establishing owner/owned window relationships.</span></span>  
  
- <span data-ttu-id="67e08-135">設定視窗外觀 (例如大小、位置、圖示、標題列文字、框線)。</span><span class="sxs-lookup"><span data-stu-id="67e08-135">Configuring window appearance (for example, size, location, icons, title bar text, border).</span></span>  
  
- <span data-ttu-id="67e08-136">追蹤視窗存留期並與其互動。</span><span class="sxs-lookup"><span data-stu-id="67e08-136">Tracking and interacting with the lifetime of a window.</span></span>  
  
 <span data-ttu-id="67e08-137">如需詳細資訊，請參閱 [WPF 視窗概觀](wpf-windows-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="67e08-137">For more information, see [WPF Windows Overview](wpf-windows-overview.md).</span></span>  
  
 <span data-ttu-id="67e08-138"><xref:System.Windows.Window> 可建立一種特殊的視窗類型，稱為對話方塊。</span><span class="sxs-lookup"><span data-stu-id="67e08-138"><xref:System.Windows.Window> supports the ability to create a special type of window known as a dialog box.</span></span> <span data-ttu-id="67e08-139">您可以建立強制回應和非強制回應類型的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="67e08-139">Both modal and modeless types of dialog boxes can be created.</span></span>  
  
 <span data-ttu-id="67e08-140">為了方便起見，以及跨應用程式的重複使用性和一致使用者體驗的優點，WPF 會公開三個通用的 Windows 對話方塊： <xref:Microsoft.Win32.OpenFileDialog>、<xref:Microsoft.Win32.SaveFileDialog>和 <xref:System.Windows.Controls.PrintDialog>。</span><span class="sxs-lookup"><span data-stu-id="67e08-140">For convenience, and the benefits of reusability and a consistent user experience across applications, WPF exposes three of the common Windows dialog boxes: <xref:Microsoft.Win32.OpenFileDialog>, <xref:Microsoft.Win32.SaveFileDialog>, and <xref:System.Windows.Controls.PrintDialog>.</span></span>  
  
 <span data-ttu-id="67e08-141">訊息方塊是一種特殊的對話方塊類型，可將重要的文字資訊顯示給使用者，以及詢問簡單的「是/否/確定/取消」問題。</span><span class="sxs-lookup"><span data-stu-id="67e08-141">A message box is a special type of dialog box for showing important textual information to users, and for asking simple Yes/No/OK/Cancel questions.</span></span> <span data-ttu-id="67e08-142">您可以使用 <xref:System.Windows.MessageBox> 類別來建立及顯示訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="67e08-142">You use the <xref:System.Windows.MessageBox> class to create and show message boxes.</span></span>  
  
 <span data-ttu-id="67e08-143">如需詳細資訊，請參閱[對話方塊概觀](dialog-boxes-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="67e08-143">For more information, see [Dialog Boxes Overview](dialog-boxes-overview.md).</span></span>  
  
<a name="Navigation"></a>   
## <a name="navigation"></a><span data-ttu-id="67e08-144">瀏覽</span><span class="sxs-lookup"><span data-stu-id="67e08-144">Navigation</span></span>  
 <span data-ttu-id="67e08-145">WPF 支援使用頁面（<xref:System.Windows.Controls.Page>）和超連結（<xref:System.Windows.Documents.Hyperlink>）的 Web 樣式導覽。</span><span class="sxs-lookup"><span data-stu-id="67e08-145">WPF supports Web-style navigation using pages (<xref:System.Windows.Controls.Page>) and hyperlinks (<xref:System.Windows.Documents.Hyperlink>).</span></span> <span data-ttu-id="67e08-146">您可以透過各種方式來實作瀏覽，包括：</span><span class="sxs-lookup"><span data-stu-id="67e08-146">Navigation can be implemented in a variety of ways that include the following:</span></span>  
  
- <span data-ttu-id="67e08-147">裝載於網頁瀏覽器的獨立頁面。</span><span class="sxs-lookup"><span data-stu-id="67e08-147">Standalone pages that are hosted in a Web browser.</span></span>  
  
- <span data-ttu-id="67e08-148">編譯成 XBAP 的頁面，裝載在網頁瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="67e08-148">Pages compiled into an XBAP that is hosted in a Web browser.</span></span>  
  
- <span data-ttu-id="67e08-149">編譯成獨立應用程式並由瀏覽視窗 (<xref:System.Windows.Navigation.NavigationWindow>) 裝載的頁面。</span><span class="sxs-lookup"><span data-stu-id="67e08-149">Pages compiled into a standalone application and hosted by a navigation window (<xref:System.Windows.Navigation.NavigationWindow>).</span></span>  
  
- <span data-ttu-id="67e08-150">由框架（<xref:System.Windows.Controls.Frame>）主控的頁面，可能裝載于獨立頁面，或編譯成 XBAP 或獨立應用程式的頁面。</span><span class="sxs-lookup"><span data-stu-id="67e08-150">Pages that are hosted by a frame (<xref:System.Windows.Controls.Frame>), which may be hosted in a standalone page, or a page compiled into either an XBAP or a standalone application.</span></span>  
  
 <span data-ttu-id="67e08-151">為了方便導覽，WPF 會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="67e08-151">To facilitate navigation, WPF implements the following:</span></span>  
  
- <span data-ttu-id="67e08-152"><xref:System.Windows.Navigation.NavigationService>，這是用來處理導覽要求的共用導覽引擎，可由 <xref:System.Windows.Controls.Frame>、<xref:System.Windows.Navigation.NavigationWindow>和 Xbap 用來支援應用程式內導覽。</span><span class="sxs-lookup"><span data-stu-id="67e08-152"><xref:System.Windows.Navigation.NavigationService>, the shared navigation engine for processing navigation requests that is used by <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>, and XBAPs to support intra-application navigation.</span></span>  
  
- <span data-ttu-id="67e08-153">要啟始瀏覽的瀏覽方法。</span><span class="sxs-lookup"><span data-stu-id="67e08-153">Navigation methods to initiate navigation.</span></span>  
  
- <span data-ttu-id="67e08-154">要追蹤瀏覽存留期並與其互動的瀏覽事件。</span><span class="sxs-lookup"><span data-stu-id="67e08-154">Navigation events to track and interact with navigation lifetime.</span></span>  
  
- <span data-ttu-id="67e08-155">使用日誌記住向後和向前瀏覽，該日誌也可供檢查和操作。</span><span class="sxs-lookup"><span data-stu-id="67e08-155">Remembering back and forward navigation using a journal, which can also be inspected and manipulated.</span></span>  
  
 <span data-ttu-id="67e08-156">如需相關資訊，請參閱[瀏覽概觀](navigation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="67e08-156">For information, see [Navigation Overview](navigation-overview.md).</span></span>  
  
 <span data-ttu-id="67e08-157">WPF 也支援一種特殊類型的導覽，稱為結構化導覽。</span><span class="sxs-lookup"><span data-stu-id="67e08-157">WPF also supports a special type of navigation known as structured navigation.</span></span> <span data-ttu-id="67e08-158">結構化瀏覽可用來呼叫一或多個頁面，這些頁面會以與呼叫函式一致的結構化且可預期方式傳回資料。</span><span class="sxs-lookup"><span data-stu-id="67e08-158">Structured navigation can be used to call one or more pages that return data in a structured and predictable way that is consistent with calling functions.</span></span> <span data-ttu-id="67e08-159">此功能相依於 <xref:System.Windows.Navigation.PageFunction%601> 類別，這在[結構化巡覽概觀](structured-navigation-overview.md)中將進一步說明。</span><span class="sxs-lookup"><span data-stu-id="67e08-159">This capability depends on the <xref:System.Windows.Navigation.PageFunction%601> class, which is described further in [Structured Navigation Overview](structured-navigation-overview.md).</span></span> <span data-ttu-id="67e08-160"><xref:System.Windows.Navigation.PageFunction%601> 也可用來簡化複雜瀏覽拓撲的建立，這在[巡覽拓撲概觀](navigation-topologies-overview.md)中將進行說明。</span><span class="sxs-lookup"><span data-stu-id="67e08-160"><xref:System.Windows.Navigation.PageFunction%601> also serves to simplify the creation of complex navigation topologies, which are described in [Navigation Topologies Overview](navigation-topologies-overview.md).</span></span>  
  
<a name="Hosting"></a>   
## <a name="hosting"></a><span data-ttu-id="67e08-161">主控</span><span class="sxs-lookup"><span data-stu-id="67e08-161">Hosting</span></span>  
 <span data-ttu-id="67e08-162">Xbap 可以裝載于 Microsoft Internet Explorer 或 Firefox 中。</span><span class="sxs-lookup"><span data-stu-id="67e08-162">XBAPs can be hosted in Microsoft Internet Explorer or Firefox.</span></span> <span data-ttu-id="67e08-163">每個裝載模型有各自的一組考量和條件約束，[裝載](hosting-wpf-applications.md)中將進行說明。</span><span class="sxs-lookup"><span data-stu-id="67e08-163">Each hosting model has its own set of considerations and constraints that are covered in [Hosting](hosting-wpf-applications.md).</span></span>  
  
<a name="Build_and_Deploy"></a>   
## <a name="build-and-deploy"></a><span data-ttu-id="67e08-164">建立和部署</span><span class="sxs-lookup"><span data-stu-id="67e08-164">Build and Deploy</span></span>  
 <span data-ttu-id="67e08-165">雖然您可以從命令提示字元使用命令列編譯器來建立簡單的 WPF 應用程式，但是 WPF 會與 Visual Studio 整合，以提供簡化開發和建立程式的額外支援。</span><span class="sxs-lookup"><span data-stu-id="67e08-165">Although simple WPF applications can be built from a command prompt using command-line compilers, WPF integrates with Visual Studio to provide additional support that simplified the development and build process.</span></span> <span data-ttu-id="67e08-166">如需詳細資訊，請參閱[建置 WPF 應用程式](building-a-wpf-application-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="67e08-166">For more information, see [Building a WPF Application](building-a-wpf-application-wpf.md).</span></span>  
  
 <span data-ttu-id="67e08-167">根據您建置的應用程式類型，有一或多個部署選項可供選擇。</span><span class="sxs-lookup"><span data-stu-id="67e08-167">Depending on the type of application you build, there are one or more deployment options to choose from.</span></span> <span data-ttu-id="67e08-168">如需詳細資訊，請參閱[部署 WPF 應用程式](deploying-a-wpf-application-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="67e08-168">For more information, see [Deploying a WPF Application](deploying-a-wpf-application-wpf.md).</span></span>  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a><span data-ttu-id="67e08-169">相關主題</span><span class="sxs-lookup"><span data-stu-id="67e08-169">Related Topics</span></span>  
  
|<span data-ttu-id="67e08-170">標題</span><span class="sxs-lookup"><span data-stu-id="67e08-170">Title</span></span>|<span data-ttu-id="67e08-171">描述</span><span class="sxs-lookup"><span data-stu-id="67e08-171">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="67e08-172">應用程式管理概觀</span><span class="sxs-lookup"><span data-stu-id="67e08-172">Application Management Overview</span></span>](application-management-overview.md)|<span data-ttu-id="67e08-173">提供 <xref:System.Windows.Application> 類別的概觀，包括管理應用程式存留期、視窗、應用程式資源和瀏覽。</span><span class="sxs-lookup"><span data-stu-id="67e08-173">Provides an overview of the <xref:System.Windows.Application> class including managing application lifetime, windows, application resources, and navigation.</span></span>|  
|[<span data-ttu-id="67e08-174">WPF 中的視窗</span><span class="sxs-lookup"><span data-stu-id="67e08-174">Windows in WPF</span></span>](windows-in-wpf-applications.md)|<span data-ttu-id="67e08-175">提供在應用程式中管理視窗的詳細資料，包括如何使用 <xref:System.Windows.Window> 類別和對話方塊。</span><span class="sxs-lookup"><span data-stu-id="67e08-175">Provides details of managing windows in your application including how to use the <xref:System.Windows.Window> class and dialog boxes.</span></span>|  
|[<span data-ttu-id="67e08-176">瀏覽概觀</span><span class="sxs-lookup"><span data-stu-id="67e08-176">Navigation Overview</span></span>](navigation-overview.md)|<span data-ttu-id="67e08-177">提供有關管理在應用程式頁面之間瀏覽的概觀。</span><span class="sxs-lookup"><span data-stu-id="67e08-177">Provides an overview of managing navigation between pages of your application.</span></span>|  
|[<span data-ttu-id="67e08-178">裝載</span><span class="sxs-lookup"><span data-stu-id="67e08-178">Hosting</span></span>](hosting-wpf-applications.md)|<span data-ttu-id="67e08-179">提供 XAML 瀏覽器應用程式（Xbap）的總覽。</span><span class="sxs-lookup"><span data-stu-id="67e08-179">Provides an overview of XAML browser applications (XBAPs).</span></span>|  
|[<span data-ttu-id="67e08-180">建置和部署</span><span class="sxs-lookup"><span data-stu-id="67e08-180">Build and Deploy</span></span>](building-and-deploying-wpf-applications.md)|<span data-ttu-id="67e08-181">描述如何建置及部署 WPF 應用程式。</span><span class="sxs-lookup"><span data-stu-id="67e08-181">Describes how to build and deploy your WPF application.</span></span>|  
|[<span data-ttu-id="67e08-182">Visual Studio 中的 WPF 簡介</span><span class="sxs-lookup"><span data-stu-id="67e08-182">Introduction to WPF in Visual Studio</span></span>](../getting-started/introduction-to-wpf-in-vs.md)|<span data-ttu-id="67e08-183">描述 WPF 的主要功能。</span><span class="sxs-lookup"><span data-stu-id="67e08-183">Describes the main features of WPF.</span></span>|  
|[<span data-ttu-id="67e08-184">逐步解說：我的第一個 WPF 傳統型應用程式</span><span class="sxs-lookup"><span data-stu-id="67e08-184">Walkthrough: My first WPF desktop application</span></span>](../getting-started/walkthrough-my-first-wpf-desktop-application.md)|<span data-ttu-id="67e08-185">示範如何建立使用頁面瀏覽、配置、控制項、影像、樣式和繫結之 WPF 應用程式的逐步解說。</span><span class="sxs-lookup"><span data-stu-id="67e08-185">A walkthrough that shows how to create a WPF application using page navigation, layout, controls, images, styles, and binding.</span></span>|
