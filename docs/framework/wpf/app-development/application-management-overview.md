---
title: 應用程式管理概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application management [WPF]
ms.assetid: 32b1c054-5aca-423b-b4b5-ed8dc4dc637d
ms.openlocfilehash: 448c212e4afe547dc6342b000fe06d5340db112c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958732"
---
# <a name="application-management-overview"></a><span data-ttu-id="1450d-102">應用程式管理概觀</span><span class="sxs-lookup"><span data-stu-id="1450d-102">Application Management Overview</span></span>
<span data-ttu-id="1450d-103">所有應用程式通常會共用一組適用於應用程式實作和管理的通用功能。</span><span class="sxs-lookup"><span data-stu-id="1450d-103">All applications tend to share a common set of functionality that applies to application implementation and management.</span></span> <span data-ttu-id="1450d-104">本主題提供建立和管理應用程式之<xref:System.Windows.Application>類別中的功能總覽。</span><span class="sxs-lookup"><span data-stu-id="1450d-104">This topic provides an overview of the functionality in the <xref:System.Windows.Application> class for creating and managing applications.</span></span>  

## <a name="the-application-class"></a><span data-ttu-id="1450d-105">Application 類別</span><span class="sxs-lookup"><span data-stu-id="1450d-105">The Application Class</span></span>  
 <span data-ttu-id="1450d-106">在 WPF 中, 通用應用程式範圍的<xref:System.Windows.Application>功能會封裝在類別中。</span><span class="sxs-lookup"><span data-stu-id="1450d-106">In WPF, common application-scoped functionality is encapsulated in the <xref:System.Windows.Application> class.</span></span> <span data-ttu-id="1450d-107"><xref:System.Windows.Application>類別包含下列功能:</span><span class="sxs-lookup"><span data-stu-id="1450d-107">The <xref:System.Windows.Application> class includes the following functionality:</span></span>  
  
- <span data-ttu-id="1450d-108">追蹤應用程式存留期並與其互動。</span><span class="sxs-lookup"><span data-stu-id="1450d-108">Tracking and interacting with application lifetime.</span></span>  
  
- <span data-ttu-id="1450d-109">擷取及處理命令列參數。</span><span class="sxs-lookup"><span data-stu-id="1450d-109">Retrieving and processing command-line parameters.</span></span>  
  
- <span data-ttu-id="1450d-110">偵測及回應未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1450d-110">Detecting and responding to unhandled exceptions.</span></span>  
  
- <span data-ttu-id="1450d-111">共用應用程式範圍的屬性和資源。</span><span class="sxs-lookup"><span data-stu-id="1450d-111">Sharing application-scope properties and resources.</span></span>  
  
- <span data-ttu-id="1450d-112">管理獨立應用程式中的視窗。</span><span class="sxs-lookup"><span data-stu-id="1450d-112">Managing windows in standalone applications.</span></span>  
  
- <span data-ttu-id="1450d-113">追蹤及管理瀏覽。</span><span class="sxs-lookup"><span data-stu-id="1450d-113">Tracking and managing navigation.</span></span>  
  
<a name="The_Application_Class"></a>   
## <a name="how-to-perform-common-tasks-using-the-application-class"></a><span data-ttu-id="1450d-114">如何使用 Application 類別執行一般工作</span><span class="sxs-lookup"><span data-stu-id="1450d-114">How to Perform Common Tasks Using the Application Class</span></span>  
 <span data-ttu-id="1450d-115">如果您對<xref:System.Windows.Application>類別的所有詳細資料不感興趣, 下表列出一些常見的工作, <xref:System.Windows.Application>以及如何完成這些作業。</span><span class="sxs-lookup"><span data-stu-id="1450d-115">If you are not interested in all of the details of the <xref:System.Windows.Application> class, the following table lists some of the common tasks for <xref:System.Windows.Application> and how to accomplish them.</span></span> <span data-ttu-id="1450d-116">您可以檢視相關的 API 和主題，來尋找詳細資訊和範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="1450d-116">By viewing the related API and topics, you can find more information and sample code.</span></span>  
  
|<span data-ttu-id="1450d-117">工作</span><span class="sxs-lookup"><span data-stu-id="1450d-117">Task</span></span>|<span data-ttu-id="1450d-118">方法</span><span class="sxs-lookup"><span data-stu-id="1450d-118">Approach</span></span>|  
|----------|--------------|  
|<span data-ttu-id="1450d-119">取得代表目前應用程式的物件</span><span class="sxs-lookup"><span data-stu-id="1450d-119">Get an object that represents the current application</span></span>|<span data-ttu-id="1450d-120">請使用 <xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="1450d-120">Use the <xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> property.</span></span>|  
|<span data-ttu-id="1450d-121">將啟動畫面新增至應用程式</span><span class="sxs-lookup"><span data-stu-id="1450d-121">Add a startup screen to an application</span></span>|<span data-ttu-id="1450d-122">請參閱[將啟動顯示畫面新增至 WPF 應用程式](how-to-add-a-splash-screen-to-a-wpf-application.md)。</span><span class="sxs-lookup"><span data-stu-id="1450d-122">See [Add a Splash Screen to a WPF Application](how-to-add-a-splash-screen-to-a-wpf-application.md).</span></span>|  
|<span data-ttu-id="1450d-123">啟動應用程式</span><span class="sxs-lookup"><span data-stu-id="1450d-123">Start an application</span></span>|<span data-ttu-id="1450d-124">請使用 <xref:System.Windows.Application.Run%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="1450d-124">Use the <xref:System.Windows.Application.Run%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="1450d-125">停止應用程式</span><span class="sxs-lookup"><span data-stu-id="1450d-125">Stop an application</span></span>|<span data-ttu-id="1450d-126">使用<xref:System.Windows.Application.Current%2A?displayProperty=nameWithType>物件<xref:System.Windows.Application.Shutdown%2A>的方法。</span><span class="sxs-lookup"><span data-stu-id="1450d-126">Use the <xref:System.Windows.Application.Shutdown%2A> method of the <xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> object.</span></span>|  
|<span data-ttu-id="1450d-127">從命令列取得引數</span><span class="sxs-lookup"><span data-stu-id="1450d-127">Get arguments from the command line</span></span>|<span data-ttu-id="1450d-128">處理事件並使用<xref:System.Windows.StartupEventArgs.Args%2A?displayProperty=nameWithType>屬性。 <xref:System.Windows.Application.Startup?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="1450d-128">Handle the <xref:System.Windows.Application.Startup?displayProperty=nameWithType> event and use the <xref:System.Windows.StartupEventArgs.Args%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="1450d-129">如需範例, 請參閱<xref:System.Windows.Application.Startup?displayProperty=nameWithType>事件。</span><span class="sxs-lookup"><span data-stu-id="1450d-129">For an example, see the <xref:System.Windows.Application.Startup?displayProperty=nameWithType> event.</span></span>|  
|<span data-ttu-id="1450d-130">取得及設定應用程式結束代碼</span><span class="sxs-lookup"><span data-stu-id="1450d-130">Get and set the application exit code</span></span>|<span data-ttu-id="1450d-131">在事件處理常式中設定<xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A?displayProperty=nameWithType>屬性, 或呼叫方法<xref:System.Windows.Application.Shutdown%2A>並傳入整數。 <xref:System.Windows.Application.Exit?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="1450d-131">Set the <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A?displayProperty=nameWithType> property in the <xref:System.Windows.Application.Exit?displayProperty=nameWithType> event handler or call the <xref:System.Windows.Application.Shutdown%2A> method and pass in an integer.</span></span>|  
|<span data-ttu-id="1450d-132">偵測及回應未處理的例外狀況</span><span class="sxs-lookup"><span data-stu-id="1450d-132">Detect and respond to unhandled exceptions</span></span>|<span data-ttu-id="1450d-133"><xref:System.Windows.Application.DispatcherUnhandledException>處理事件。</span><span class="sxs-lookup"><span data-stu-id="1450d-133">Handle the <xref:System.Windows.Application.DispatcherUnhandledException> event.</span></span>|  
|<span data-ttu-id="1450d-134">取得及設定應用程式範圍的資源</span><span class="sxs-lookup"><span data-stu-id="1450d-134">Get and set application-scoped resources</span></span>|<span data-ttu-id="1450d-135">請使用 <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="1450d-135">Use the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property.</span></span>|  
|<span data-ttu-id="1450d-136">使用應用程式範圍的資源字典</span><span class="sxs-lookup"><span data-stu-id="1450d-136">Use an application-scope resource dictionary</span></span>|<span data-ttu-id="1450d-137">請參閱[使用應用程式範圍的資源字典](how-to-use-an-application-scope-resource-dictionary.md)。</span><span class="sxs-lookup"><span data-stu-id="1450d-137">See [Use an Application-Scope Resource Dictionary](how-to-use-an-application-scope-resource-dictionary.md).</span></span>|  
|<span data-ttu-id="1450d-138">取得及設定應用程式範圍的屬性</span><span class="sxs-lookup"><span data-stu-id="1450d-138">Get and set application-scoped properties</span></span>|<span data-ttu-id="1450d-139">請使用 <xref:System.Windows.Application.Properties%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="1450d-139">Use the <xref:System.Windows.Application.Properties%2A?displayProperty=nameWithType> property.</span></span>|  
|<span data-ttu-id="1450d-140">取得及儲存應用程式的狀態</span><span class="sxs-lookup"><span data-stu-id="1450d-140">Get and save an application's state</span></span>|<span data-ttu-id="1450d-141">請參閱[跨應用程式會話保存和還原應用程式範圍的屬性](persist-and-restore-application-scope-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="1450d-141">See [Persist and Restore Application-Scope Properties Across Application Sessions](persist-and-restore-application-scope-properties.md).</span></span>|  
|<span data-ttu-id="1450d-142">管理非程式碼資料檔案，包括資源檔、內容檔案和來源網站檔案。</span><span class="sxs-lookup"><span data-stu-id="1450d-142">Manage non-code data files, including resource files, content files, and site-of-origin files.</span></span>|<span data-ttu-id="1450d-143">請參閱[WPF 應用程式資源、內容和資料檔案](wpf-application-resource-content-and-data-files.md)。</span><span class="sxs-lookup"><span data-stu-id="1450d-143">See [WPF Application Resource, Content, and Data Files](wpf-application-resource-content-and-data-files.md).</span></span>|  
|<span data-ttu-id="1450d-144">管理獨立應用程式中的視窗</span><span class="sxs-lookup"><span data-stu-id="1450d-144">Manage windows in standalone applications</span></span>|<span data-ttu-id="1450d-145">請參閱 [WPF 視窗概觀](wpf-windows-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="1450d-145">See [WPF Windows Overview](wpf-windows-overview.md).</span></span>|  
|<span data-ttu-id="1450d-146">追蹤及管理瀏覽</span><span class="sxs-lookup"><span data-stu-id="1450d-146">Track and manage navigation</span></span>|<span data-ttu-id="1450d-147">請參閱[導覽總覽](navigation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="1450d-147">See [Navigation Overview](navigation-overview.md).</span></span>|  
  
<a name="The_Application_Definition"></a>   
## <a name="the-application-definition"></a><span data-ttu-id="1450d-148">應用程式定義</span><span class="sxs-lookup"><span data-stu-id="1450d-148">The Application Definition</span></span>  
 <span data-ttu-id="1450d-149">若要利用<xref:System.Windows.Application>類別的功能, 您必須執行應用程式定義。</span><span class="sxs-lookup"><span data-stu-id="1450d-149">To utilize the functionality of the <xref:System.Windows.Application> class, you must implement an application definition.</span></span> <span data-ttu-id="1450d-150">WPF 應用程式定義是衍生自<xref:System.Windows.Application>的類別, 並使用特殊的 MSBuild 設定進行設定。</span><span class="sxs-lookup"><span data-stu-id="1450d-150">A WPF application definition is a class that derives from <xref:System.Windows.Application> and is configured with a special MSBuild setting.</span></span>  

### <a name="implementing-an-application-definition"></a><span data-ttu-id="1450d-151">實作應用程式定義</span><span class="sxs-lookup"><span data-stu-id="1450d-151">Implementing an Application Definition</span></span>  
 <span data-ttu-id="1450d-152">一般的 WPF 應用程式定義會同時使用標記和程式碼後置來執行。</span><span class="sxs-lookup"><span data-stu-id="1450d-152">A typical WPF application definition is implemented using both markup and code-behind.</span></span> <span data-ttu-id="1450d-153">這可讓您使用標記，以宣告方式設定應用程式屬性、資源和註冊事件，同時在程式碼後置中，處理事件及實作應用程式特定行為。</span><span class="sxs-lookup"><span data-stu-id="1450d-153">This allows you to use markup to declaratively set application properties, resources, and register events, while handling events and implementing application-specific behavior in code-behind.</span></span>  
  
 <span data-ttu-id="1450d-154">下列範例示範如何使用標記和程式碼後置，來實作應用程式定義：</span><span class="sxs-lookup"><span data-stu-id="1450d-154">The following example shows how to implement an application definition using both markup and code-behind:</span></span>  
  
 [!code-xaml[ApplicationSnippets#ApplicationXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml#applicationxaml)]  
  
 [!code-csharp[ApplicationSnippets#ApplicationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml.cs#applicationcodebehind)]
 [!code-vb[ApplicationSnippets#ApplicationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSnippets/visualbasic/application.xaml.vb#applicationcodebehind)]  
  
 <span data-ttu-id="1450d-155">若要搭配使用標記檔案和程式碼後置檔案，下列情況必須成立：</span><span class="sxs-lookup"><span data-stu-id="1450d-155">To allow a markup file and code-behind file to work together, the following needs to happen:</span></span>  
  
- <span data-ttu-id="1450d-156">在標記中, `Application`元素必須`x:Class`包含屬性。</span><span class="sxs-lookup"><span data-stu-id="1450d-156">In markup, the `Application` element must include the `x:Class` attribute.</span></span> <span data-ttu-id="1450d-157">建立應用程式`x:Class`時, 標記檔案中的存在會使 MSBuild `partial`建立衍生自<xref:System.Windows.Application>的類別, 並`x:Class`具有屬性所指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="1450d-157">When the application is built, the existence of `x:Class` in the markup file causes MSBuild to create a `partial` class that derives from <xref:System.Windows.Application> and has the name that is specified by the `x:Class` attribute.</span></span> <span data-ttu-id="1450d-158">這需要新增 XAML 架構的 XML 命名空間宣告 (`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`)。</span><span class="sxs-lookup"><span data-stu-id="1450d-158">This requires the addition of an XML namespace declaration for the XAML schema (`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`).</span></span>
  
- <span data-ttu-id="1450d-159">在程式碼後置中, 類別必須是`partial`具有與標記中的`x:Class`屬性所指定相同名稱的類別, 而且必須衍生自<xref:System.Windows.Application>。</span><span class="sxs-lookup"><span data-stu-id="1450d-159">In code-behind, the class must be a `partial` class with the same name that is specified by the `x:Class` attribute in markup and must derive from <xref:System.Windows.Application>.</span></span> <span data-ttu-id="1450d-160">這可讓程式碼後置檔案與`partial`建立應用程式時為標記檔案產生的類別相關聯 (請參閱[建立 WPF 應用程式](building-a-wpf-application-wpf.md))。</span><span class="sxs-lookup"><span data-stu-id="1450d-160">This allows the code-behind file to be associated with the `partial` class that is generated for the markup file when the application is built (see [Building a WPF Application](building-a-wpf-application-wpf.md)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1450d-161">當您使用 Visual Studio 建立新的 WPF 應用程式專案或 WPF 瀏覽器應用程式專案時, 預設會包含應用程式定義, 並使用標記和程式碼後置來定義。</span><span class="sxs-lookup"><span data-stu-id="1450d-161">When you create a new WPF Application project or WPF Browser Application project using Visual Studio, an application definition is included by default and is defined using both markup and code-behind.</span></span>  
  
 <span data-ttu-id="1450d-162">此程式碼是實作應用程式定義的最低需求。</span><span class="sxs-lookup"><span data-stu-id="1450d-162">This code is the minimum that is required to implement an application definition.</span></span> <span data-ttu-id="1450d-163">不過, 在建立和執行應用程式之前, 必須先對應用程式定義進行其他的 MSBuild 設定。</span><span class="sxs-lookup"><span data-stu-id="1450d-163">However, an additional MSBuild configuration needs to be made to the application definition before building and running the application.</span></span>  
  
### <a name="configuring-the-application-definition-for-msbuild"></a><span data-ttu-id="1450d-164">設定 MSBuild 的應用程式定義</span><span class="sxs-lookup"><span data-stu-id="1450d-164">Configuring the Application Definition for MSBuild</span></span>  
 <span data-ttu-id="1450d-165">獨立應用程式和 XAML 瀏覽器應用程式 (Xbap) 需要先執行特定層級的基礎結構, 才能執行。</span><span class="sxs-lookup"><span data-stu-id="1450d-165">Standalone applications and XAML browser applications (XBAPs) require the implementation of a certain level of infrastructure before they can run.</span></span> <span data-ttu-id="1450d-166">此基礎結構的最重要部分是進入點。</span><span class="sxs-lookup"><span data-stu-id="1450d-166">The most important part of this infrastructure is the entry point.</span></span> <span data-ttu-id="1450d-167">當使用者啟動應用程式時，作業系統會呼叫進入點，這是用於啟動應用程式的已知函式。</span><span class="sxs-lookup"><span data-stu-id="1450d-167">When an application is launched by a user, the operating system calls the entry point, which is a well-known function for starting applications.</span></span>  
  
 <span data-ttu-id="1450d-168">傳統上，開發人員必須自行撰寫這段程式碼的一部分或全部 (視使用技術而定)。</span><span class="sxs-lookup"><span data-stu-id="1450d-168">Traditionally, developers have needed to write some or all of this code for themselves, depending on the technology.</span></span> <span data-ttu-id="1450d-169">不過, 當應用程式定義的標記檔案設定為 msbuild `ApplicationDefinition`專案時, WPF 會為您產生此程式碼, 如下列 MSBuild 專案檔所示:</span><span class="sxs-lookup"><span data-stu-id="1450d-169">However, WPF generates this code for you when the markup file of your application definition is configured as an MSBuild `ApplicationDefinition` item, as shown in the following MSBuild project file:</span></span>  
  
```xml  
<Project   
  DefaultTargets="Build"  
                        xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  ...  
  <ApplicationDefinition Include="App.xaml" />  
  <Compile Include="App.xaml.cs" />  
  ...  
</Project>  
```  
  
 <span data-ttu-id="1450d-170">由於程式碼後置檔案包含程式碼, 因此會將它標示`Compile`為 MSBuild 專案, 如同平常一般。</span><span class="sxs-lookup"><span data-stu-id="1450d-170">Because the code-behind file contains code, it is marked as an MSBuild `Compile` item, as is normal.</span></span>  
  
 <span data-ttu-id="1450d-171">將這些 MSBuild 設定應用於應用程式定義的標記和程式碼後置檔案, 會導致 MSBuild 產生如下所示的程式碼:</span><span class="sxs-lookup"><span data-stu-id="1450d-171">The application of these MSBuild configurations to the markup and code-behind files of an application definition causes MSBuild to generate code like the following:</span></span>  
  
 [!code-csharp[auto-generated-code](~/samples/snippets/csharp/VS_Snippets_Wpf/AppDefAugSnippets/CSharp/App.cs)]
 [!code-vb[auto-generated-code](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AppDefAugSnippets/VisualBasic/App.vb)]  
  
 <span data-ttu-id="1450d-172">產生的程式碼會以額外的基礎結構程式碼 (包括進入點方法`Main`) 來增強您的應用程式定義。</span><span class="sxs-lookup"><span data-stu-id="1450d-172">The resulting code augments your application definition with additional infrastructure code, which includes the entry-point method `Main`.</span></span> <span data-ttu-id="1450d-173">屬性會套用`Main`至方法, 以指出 wpf 應用程式的主要 UI 執行緒是 wpf 應用程式所需的 STA 執行緒。 <xref:System.STAThreadAttribute></span><span class="sxs-lookup"><span data-stu-id="1450d-173">The <xref:System.STAThreadAttribute> attribute is applied to the `Main` method to indicate that the main UI thread for the WPF application is an STA thread, which is required for WPF applications.</span></span> <span data-ttu-id="1450d-174">呼叫時, `Main`會先建立的`App`新實例, 再`InitializeComponent`呼叫方法來註冊事件, 並設定在標記中執行的屬性。</span><span class="sxs-lookup"><span data-stu-id="1450d-174">When called, `Main` creates a new instance of `App` before calling the `InitializeComponent` method to register the events and set the properties that are implemented in markup.</span></span> <span data-ttu-id="1450d-175">因為`InitializeComponent`會為您產生, 所以您不需要明確地`InitializeComponent`從應用程式定義呼叫, 就像<xref:System.Windows.Controls.Page>您<xref:System.Windows.Window>針對和執行所做的一樣。</span><span class="sxs-lookup"><span data-stu-id="1450d-175">Because `InitializeComponent` is generated for you, you don't need to explicitly call `InitializeComponent` from an application definition like you do for <xref:System.Windows.Controls.Page> and <xref:System.Windows.Window> implementations.</span></span> <span data-ttu-id="1450d-176">最後, <xref:System.Windows.Application.Run%2A>會呼叫方法來啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="1450d-176">Finally, the <xref:System.Windows.Application.Run%2A> method is called to start the application.</span></span>  
  
<a name="Getting_the_Current_Application"></a>   
## <a name="getting-the-current-application"></a><span data-ttu-id="1450d-177">取得目前的應用程式</span><span class="sxs-lookup"><span data-stu-id="1450d-177">Getting the Current Application</span></span>  
 <span data-ttu-id="1450d-178">由於<xref:System.Windows.Application>類別的功能會在應用程式之間共用, 因此每個<xref:System.AppDomain>只能有一個<xref:System.Windows.Application>類別的實例。</span><span class="sxs-lookup"><span data-stu-id="1450d-178">Because the functionality of the <xref:System.Windows.Application> class are shared across an application, there can be only one instance of the <xref:System.Windows.Application> class per <xref:System.AppDomain>.</span></span> <span data-ttu-id="1450d-179">若要強制執行此<xref:System.Windows.Application>功能, 類別會實作為單一類別 (請參閱[在C#中執行 singleton ](https://go.microsoft.com/fwlink/?LinkId=100567)), 這會建立本身的單一實例, 並使用`static` <xref:System.Windows.Application.Current%2A>屬性提供其共用的存取權。</span><span class="sxs-lookup"><span data-stu-id="1450d-179">To enforce this, the <xref:System.Windows.Application> class is implemented as a singleton class (see [Implementing Singleton in C#](https://go.microsoft.com/fwlink/?LinkId=100567)), which creates a single instance of itself and provides shared access to it with the `static`<xref:System.Windows.Application.Current%2A> property.</span></span>  
  
 <span data-ttu-id="1450d-180">下列程式碼顯示如何取得目前<xref:System.Windows.Application> <xref:System.AppDomain>的物件參考。</span><span class="sxs-lookup"><span data-stu-id="1450d-180">The following code shows how to acquire a reference to the <xref:System.Windows.Application> object for the current <xref:System.AppDomain>.</span></span>  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getcurrentappcode)]  
  
 <span data-ttu-id="1450d-181"><xref:System.Windows.Application.Current%2A>傳回<xref:System.Windows.Application>類別實例的參考。</span><span class="sxs-lookup"><span data-stu-id="1450d-181"><xref:System.Windows.Application.Current%2A> returns a reference to an instance of the <xref:System.Windows.Application> class.</span></span> <span data-ttu-id="1450d-182">如果您想要參考<xref:System.Windows.Application>衍生類別, 您必須轉換<xref:System.Windows.Application.Current%2A>屬性的值, 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="1450d-182">If you want a reference to your <xref:System.Windows.Application> derived class you must cast the value of the <xref:System.Windows.Application.Current%2A> property, as shown in the following example.</span></span>  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getstcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getstcurrentappcode)]  
  
 <span data-ttu-id="1450d-183">您可以在<xref:System.Windows.Application>物件存留期<xref:System.Windows.Application.Current%2A>的任何時間點檢查的值。</span><span class="sxs-lookup"><span data-stu-id="1450d-183">You can inspect the value of <xref:System.Windows.Application.Current%2A> at any point in the lifetime of an <xref:System.Windows.Application> object.</span></span> <span data-ttu-id="1450d-184">不過，您應該要小心。</span><span class="sxs-lookup"><span data-stu-id="1450d-184">However, you should be careful.</span></span> <span data-ttu-id="1450d-185">在<xref:System.Windows.Application>類別具現化之後, 會有一個期間, 在此期間, <xref:System.Windows.Application>物件的狀態不一致。</span><span class="sxs-lookup"><span data-stu-id="1450d-185">After the <xref:System.Windows.Application> class is instantiated, there is a period during which the state of the <xref:System.Windows.Application> object is inconsistent.</span></span> <span data-ttu-id="1450d-186">在這段期間<xref:System.Windows.Application> , 會執行您的程式碼所需的各種初始設定工作, 包括建立應用程式基礎結構、設定屬性和註冊事件。</span><span class="sxs-lookup"><span data-stu-id="1450d-186">During this period, <xref:System.Windows.Application> is performing the various initialization tasks that are required by your code to run, including establishing application infrastructure, setting properties, and registering events.</span></span> <span data-ttu-id="1450d-187">如果您在這段期間<xref:System.Windows.Application>嘗試使用物件, 您的程式碼可能會產生非預期的結果, 特別是當<xref:System.Windows.Application>它相依于所設定的各種屬性時。</span><span class="sxs-lookup"><span data-stu-id="1450d-187">If you try to use the <xref:System.Windows.Application> object during this period, your code may have unexpected results, particularly if it depends on the various <xref:System.Windows.Application> properties being set.</span></span>  
  
 <span data-ttu-id="1450d-188">當<xref:System.Windows.Application>完成其初始化工作時, 其存留期就會真正開始。</span><span class="sxs-lookup"><span data-stu-id="1450d-188">When <xref:System.Windows.Application> completes its initialization work, its lifetime truly begins.</span></span>  
  
<a name="Application_Lifetime"></a>   
## <a name="application-lifetime"></a><span data-ttu-id="1450d-189">應用程式存留期</span><span class="sxs-lookup"><span data-stu-id="1450d-189">Application Lifetime</span></span>  
 <span data-ttu-id="1450d-190">WPF 應用程式的存留期會由所引發<xref:System.Windows.Application>的數個事件加以標記, 讓您知道應用程式何時啟動、已啟用並停用, 而且已關閉。</span><span class="sxs-lookup"><span data-stu-id="1450d-190">The lifetime of a WPF application is marked by several events that are raised by <xref:System.Windows.Application> to let you know when your application has started, has been activated and deactivated, and has been shut down.</span></span>  

<a name="Splash_Screen"></a>   
### <a name="splash-screen"></a><span data-ttu-id="1450d-191">啟動顯示畫面</span><span class="sxs-lookup"><span data-stu-id="1450d-191">Splash Screen</span></span>  
 <span data-ttu-id="1450d-192">從 .NET Framework 3.5 SP1 開始, 您可以指定要在啟動視窗或啟動顯示*畫面*中使用的映射。</span><span class="sxs-lookup"><span data-stu-id="1450d-192">Starting in the .NET Framework 3.5 SP1, you can specify an image to be used in a startup window, or *splash screen*.</span></span> <span data-ttu-id="1450d-193"><xref:System.Windows.SplashScreen>類別可讓您在應用程式載入時輕鬆顯示啟動視窗。</span><span class="sxs-lookup"><span data-stu-id="1450d-193">The <xref:System.Windows.SplashScreen> class makes it easy to display a startup window while your application is loading.</span></span> <span data-ttu-id="1450d-194">在<xref:System.Windows.SplashScreen>呼叫之前<xref:System.Windows.Application.Run%2A> , 會建立並顯示此視窗。</span><span class="sxs-lookup"><span data-stu-id="1450d-194">The <xref:System.Windows.SplashScreen> window is created and shown before <xref:System.Windows.Application.Run%2A> is called.</span></span> <span data-ttu-id="1450d-195">如需詳細資訊, 請參閱[應用程式啟動時間](../advanced/application-startup-time.md)和[將啟動顯示畫面新增至 WPF 應用程式](how-to-add-a-splash-screen-to-a-wpf-application.md)。</span><span class="sxs-lookup"><span data-stu-id="1450d-195">For more information, see [Application Startup Time](../advanced/application-startup-time.md) and [Add a Splash Screen to a WPF Application](how-to-add-a-splash-screen-to-a-wpf-application.md).</span></span>  
  
<a name="Starting_an_Application"></a>   
### <a name="starting-an-application"></a><span data-ttu-id="1450d-196">啟動應用程式</span><span class="sxs-lookup"><span data-stu-id="1450d-196">Starting an Application</span></span>  
 <span data-ttu-id="1450d-197">在<xref:System.Windows.Application.Run%2A>呼叫並初始化應用程式之後, 應用程式就已準備好執行。</span><span class="sxs-lookup"><span data-stu-id="1450d-197">After <xref:System.Windows.Application.Run%2A> is called and the application is initialized, the application is ready to run.</span></span> <span data-ttu-id="1450d-198">這段時間是在引發<xref:System.Windows.Application.Startup>事件時表示:</span><span class="sxs-lookup"><span data-stu-id="1450d-198">This moment is signified when the <xref:System.Windows.Application.Startup> event is raised:</span></span>  
  
[!code-csharp[Startup-event](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs?range=3-11,31-33)]
[!code-vb[Startup-event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb?range=5-11,30-32)]
  
 <span data-ttu-id="1450d-199">此時, 在應用程式的存留期內, 最常見的做法是顯示 UI。</span><span class="sxs-lookup"><span data-stu-id="1450d-199">At this point in an application's lifetime, the most common thing to do is to show a UI.</span></span>  
  
<a name="Showing_a_User_Interface"></a>
### <a name="showing-a-user-interface"></a><span data-ttu-id="1450d-200">顯示使用者介面</span><span class="sxs-lookup"><span data-stu-id="1450d-200">Showing a User Interface</span></span>  
 <span data-ttu-id="1450d-201">大多數獨立 Windows 應用程式開始<xref:System.Windows.Window>執行時, 會開啟。</span><span class="sxs-lookup"><span data-stu-id="1450d-201">Most standalone Windows applications open a <xref:System.Windows.Window> when they begin running.</span></span> <span data-ttu-id="1450d-202"><xref:System.Windows.Application.Startup>事件處理常式是您可以從中執行此動作的一個位置, 如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="1450d-202">The <xref:System.Windows.Application.Startup> event handler is one location from which you can do this, as demonstrated by the following code.</span></span>  
  
 [!code-xaml[AppShowWindowHardSnippets#StartupEventMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml#startupeventmarkup)]  
  
 [!code-csharp[AppShowWindowHardSnippets#StartupEventCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml.cs#startupeventcodebehind)]
 [!code-vb[AppShowWindowHardSnippets#StartupEventCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AppShowWindowHardSnippets/VisualBasic/Application.xaml.vb#startupeventcodebehind)]  
  
> [!NOTE]
> <span data-ttu-id="1450d-203">要在<xref:System.Windows.Window>獨立應用程式中具現化的第一個, 預設會成為主應用程式視窗。</span><span class="sxs-lookup"><span data-stu-id="1450d-203">The first <xref:System.Windows.Window> to be instantiated in a standalone application becomes the main application window by default.</span></span> <span data-ttu-id="1450d-204">這個<xref:System.Windows.Window>物件是<xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>由屬性所參考。</span><span class="sxs-lookup"><span data-stu-id="1450d-204">This <xref:System.Windows.Window> object is referenced by the <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="1450d-205">如果與第一個<xref:System.Windows.Application.MainWindow%2A>具現化<xref:System.Windows.Window>的視窗不同, 則可以透過程式設計方式變更屬性的值。</span><span class="sxs-lookup"><span data-stu-id="1450d-205">The value of the <xref:System.Windows.Application.MainWindow%2A> property can be changed programmatically if a different window than the first instantiated <xref:System.Windows.Window> should be the main window.</span></span>  
  
 <span data-ttu-id="1450d-206">當 XBAP 第一次啟動時, 它很可能會流覽<xref:System.Windows.Controls.Page>至。</span><span class="sxs-lookup"><span data-stu-id="1450d-206">When an XBAP first starts, it will most likely navigate to a <xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="1450d-207">如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="1450d-207">This is shown in the following code.</span></span>  
  
 [!code-xaml[XBAPAppStartupSnippets#StartupXBAPMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml#startupxbapmarkup)]  
  
 [!code-csharp[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml.cs#startupxbapcodebehind)]
 [!code-vb[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppStartupSnippets/VisualBasic/Application.xaml.vb#startupxbapcodebehind)]  
  
 <span data-ttu-id="1450d-208">如果您處理<xref:System.Windows.Application.Startup>只<xref:System.Windows.Window>開啟或流覽至<xref:System.Windows.Controls.Page>, 您可以改為在標記中`StartupUri`設定屬性。</span><span class="sxs-lookup"><span data-stu-id="1450d-208">If you handle <xref:System.Windows.Application.Startup> to only open a <xref:System.Windows.Window> or navigate to a <xref:System.Windows.Controls.Page>, you can set the `StartupUri` attribute in markup instead.</span></span>  
  
 <span data-ttu-id="1450d-209">下列範例顯示如何<xref:System.Windows.Application.StartupUri%2A>從獨立應用程式使用來<xref:System.Windows.Window>開啟。</span><span class="sxs-lookup"><span data-stu-id="1450d-209">The following example shows how to use the <xref:System.Windows.Application.StartupUri%2A> from a standalone application to open a <xref:System.Windows.Window>.</span></span>  
  
 [!code-xaml[ApplicationManagementOverviewSnippets#OverviewStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/App.xaml#overviewstartupurimarkup)]  
  
 <span data-ttu-id="1450d-210">下列範例示範如何從 XBAP 使用<xref:System.Windows.Application.StartupUri%2A> , 以流覽<xref:System.Windows.Controls.Page>至。</span><span class="sxs-lookup"><span data-stu-id="1450d-210">The following example shows how to use <xref:System.Windows.Application.StartupUri%2A> from an XBAP to navigate to a <xref:System.Windows.Controls.Page>.</span></span>  
  
 [!code-xaml[PageSnippets#XBAPStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/PageSnippets/CSharp/App.xaml#xbapstartupurimarkup)]  
  
 <span data-ttu-id="1450d-211">此標記與前述用來開啟視窗的程式碼有相同的效果。</span><span class="sxs-lookup"><span data-stu-id="1450d-211">This markup has the same effect as the previous code for opening a window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1450d-212">如需有關導覽的詳細資訊, 請參閱[流覽總覽](navigation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="1450d-212">For more information on navigation, see [Navigation Overview](navigation-overview.md).</span></span>  
  
 <span data-ttu-id="1450d-213">如果您需要使用非<xref:System.Windows.Application.Startup>參數化的函式來具現化事件, 或是需要先設定其屬性或訂閱其事件, 然後才顯示它, 您必須處理該事件以開啟, 或者您需要處理任何命令列引數。 <xref:System.Windows.Window>啟動應用程式時所提供的。</span><span class="sxs-lookup"><span data-stu-id="1450d-213">You need to handle the <xref:System.Windows.Application.Startup> event to open a <xref:System.Windows.Window> if you need to instantiate it using a non-parameterless constructor, or you need to set its properties or subscribe to its events before showing it, or you need to process any command-line arguments that were supplied when the application was launched.</span></span>  
  
<a name="Processing_Command_Line_Arguments"></a>   
### <a name="processing-command-line-arguments"></a><span data-ttu-id="1450d-214">處理命令列引數</span><span class="sxs-lookup"><span data-stu-id="1450d-214">Processing Command-Line Arguments</span></span>  
 <span data-ttu-id="1450d-215">在 Windows 中, 可以從命令提示字元或桌面啟動獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="1450d-215">In Windows, standalone applications can be launched from either a command prompt or the desktop.</span></span> <span data-ttu-id="1450d-216">在這兩種情況下，都會將命令列引數傳遞至應用程式。</span><span class="sxs-lookup"><span data-stu-id="1450d-216">In both cases, command-line arguments can be passed to the application.</span></span> <span data-ttu-id="1450d-217">下列範例顯示以單一命令列引數 "/StartMinimized" 啟動的應用程式：</span><span class="sxs-lookup"><span data-stu-id="1450d-217">The following example shows an application that is launched with a single command-line argument, "/StartMinimized":</span></span>  
  
 `wpfapplication.exe /StartMinimized`  
  
 <span data-ttu-id="1450d-218">在應用程式初始化期間, WPF 會從作業系統抓取命令列引數, 並透過<xref:System.Windows.Application.Startup> <xref:System.Windows.StartupEventArgs>參數的<xref:System.Windows.StartupEventArgs.Args%2A>屬性將它們傳遞至事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="1450d-218">During application initialization, WPF retrieves the command-line arguments from the operating system and passes them to the <xref:System.Windows.Application.Startup> event handler via the <xref:System.Windows.StartupEventArgs.Args%2A> property of the <xref:System.Windows.StartupEventArgs> parameter.</span></span> <span data-ttu-id="1450d-219">您可以使用如下的程式碼擷取及儲存命令列引數。</span><span class="sxs-lookup"><span data-stu-id="1450d-219">You can retrieve and store the command-line arguments using code like the following.</span></span>  
  
 [!code-xaml[ApplicationStartupSnippets#HandleStartupXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml#handlestartupxaml)]  
  
 [!code-csharp[ApplicationStartupSnippets#HandleStartupCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#handlestartupcodebehind)]
 [!code-vb[ApplicationStartupSnippets#HandleStartupCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#handlestartupcodebehind)]  
  
 <span data-ttu-id="1450d-220">程式碼會<xref:System.Windows.Application.Startup>處理以檢查是否已提供 **/StartMinimized**命令列引數; 如果是, 則會開啟具有<xref:System.Windows.WindowState>之的<xref:System.Windows.WindowState.Minimized>主視窗。</span><span class="sxs-lookup"><span data-stu-id="1450d-220">The code handles <xref:System.Windows.Application.Startup> to check whether the **/StartMinimized** command-line argument was provided; if so, it opens the main window with a <xref:System.Windows.WindowState> of <xref:System.Windows.WindowState.Minimized>.</span></span> <span data-ttu-id="1450d-221">請注意, 因為<xref:System.Windows.Window.WindowState%2A>屬性必須以程式設計方式設定, <xref:System.Windows.Window>所以必須在程式碼中明確開啟主要。</span><span class="sxs-lookup"><span data-stu-id="1450d-221">Note that because the <xref:System.Windows.Window.WindowState%2A> property must be set programmatically, the main <xref:System.Windows.Window> must be opened explicitly in code.</span></span>  
  
 <span data-ttu-id="1450d-222">Xbap 無法取出和處理命令列引數, 因為它們是使用 ClickOnce 部署啟動的 (請參閱[部署 WPF 應用程式](deploying-a-wpf-application-wpf.md))。</span><span class="sxs-lookup"><span data-stu-id="1450d-222">XBAPs cannot retrieve and process command-line arguments because they are launched using ClickOnce deployment (see [Deploying a WPF Application](deploying-a-wpf-application-wpf.md)).</span></span> <span data-ttu-id="1450d-223">不過，它們可以透過用來啟動的 URL 擷取及處理查詢字串參數。</span><span class="sxs-lookup"><span data-stu-id="1450d-223">However, they can retrieve and process query string parameters from the URLs that are used to launch them.</span></span>  
  
<a name="Application_Activation_and_Deactivation"></a>   
### <a name="application-activation-and-deactivation"></a><span data-ttu-id="1450d-224">應用程式啟用和停用</span><span class="sxs-lookup"><span data-stu-id="1450d-224">Application Activation and Deactivation</span></span>  
 <span data-ttu-id="1450d-225">Windows 可讓使用者在應用程式之間切換。</span><span class="sxs-lookup"><span data-stu-id="1450d-225">Windows allows users to switch between applications.</span></span> <span data-ttu-id="1450d-226">最常見的做法是使用 ALT+TAB 按鍵組合。</span><span class="sxs-lookup"><span data-stu-id="1450d-226">The most common way is to use the ALT+TAB key combination.</span></span> <span data-ttu-id="1450d-227">只有當應用程式具有可供使用者選取的可見度<xref:System.Windows.Window>時, 才能將它切換成。</span><span class="sxs-lookup"><span data-stu-id="1450d-227">An application can only be switched to if it has a visible <xref:System.Windows.Window> that a user can select.</span></span> <span data-ttu-id="1450d-228">目前選取<xref:System.Windows.Window>的是*使用中視窗*(也稱為*前景視窗*), 而則是接收使用者<xref:System.Windows.Window>輸入的。</span><span class="sxs-lookup"><span data-stu-id="1450d-228">The currently selected <xref:System.Windows.Window> is the *active window* (also known as the *foreground window*) and is the <xref:System.Windows.Window> that receives user input.</span></span> <span data-ttu-id="1450d-229">具有使用中視窗的應用程式是使用中的*應用程式*(或*前景應用*程式)。</span><span class="sxs-lookup"><span data-stu-id="1450d-229">The application with the active window is the *active application* (or *foreground application*).</span></span> <span data-ttu-id="1450d-230">在下列情況中，應用程式會變成使用中應用程式：</span><span class="sxs-lookup"><span data-stu-id="1450d-230">An application becomes the active application in the following circumstances:</span></span>  
  
- <span data-ttu-id="1450d-231">它會啟動並顯示<xref:System.Windows.Window>。</span><span class="sxs-lookup"><span data-stu-id="1450d-231">It is launched and shows a <xref:System.Windows.Window>.</span></span>  
  
- <span data-ttu-id="1450d-232">使用者藉由<xref:System.Windows.Window>在應用程式中選取來切換另一個應用程式。</span><span class="sxs-lookup"><span data-stu-id="1450d-232">A user switches from another application by selecting a <xref:System.Windows.Window> in the application.</span></span>  
  
 <span data-ttu-id="1450d-233">您可以藉由處理<xref:System.Windows.Application.Activated?displayProperty=nameWithType>事件來偵測應用程式何時變成使用中狀態。</span><span class="sxs-lookup"><span data-stu-id="1450d-233">You can detect when an application becomes active by handling the <xref:System.Windows.Application.Activated?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="1450d-234">同樣地，在下列情況中，應用程式會變成非使用中：</span><span class="sxs-lookup"><span data-stu-id="1450d-234">Likewise, an application can become inactive in the following circumstances:</span></span>  
  
- <span data-ttu-id="1450d-235">使用者從目前的應用程式切換至另一個應用程式。</span><span class="sxs-lookup"><span data-stu-id="1450d-235">A user switches to another application from the current one.</span></span>  
  
- <span data-ttu-id="1450d-236">應用程式關閉時。</span><span class="sxs-lookup"><span data-stu-id="1450d-236">When the application shuts down.</span></span>  
  
 <span data-ttu-id="1450d-237">您可以藉由處理<xref:System.Windows.Application.Deactivated?displayProperty=nameWithType>事件來偵測應用程式何時變成非作用中。</span><span class="sxs-lookup"><span data-stu-id="1450d-237">You can detect when an application becomes inactive by handling the <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="1450d-238">下列程式碼會示範如何處理<xref:System.Windows.Application.Activated>和<xref:System.Windows.Application.Deactivated>事件, 以判斷應用程式是否為使用中狀態。</span><span class="sxs-lookup"><span data-stu-id="1450d-238">The following code shows how to handle the <xref:System.Windows.Application.Activated> and <xref:System.Windows.Application.Deactivated> events to determine whether an application is active.</span></span>  
  
 [!code-xaml[ApplicationActivationSnippets#DetectActivationStateXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml#detectactivationstatexaml)]  
  
 [!code-csharp[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml.cs#detectactivationstatecodebehind)]
 [!code-vb[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationActivationSnippets/visualbasic/application.xaml.vb#detectactivationstatecodebehind)]  
  
 <span data-ttu-id="1450d-239">也<xref:System.Windows.Window>可以啟用和停用。</span><span class="sxs-lookup"><span data-stu-id="1450d-239">A <xref:System.Windows.Window> can also be activated and deactivated.</span></span> <span data-ttu-id="1450d-240">如需詳細資訊，請參閱 <xref:System.Windows.Window.Activated?displayProperty=nameWithType> 和 <xref:System.Windows.Window.Deactivated?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="1450d-240">See <xref:System.Windows.Window.Activated?displayProperty=nameWithType> and <xref:System.Windows.Window.Deactivated?displayProperty=nameWithType> for more information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1450d-241"><xref:System.Windows.Application.Activated?displayProperty=nameWithType> 和<xref:System.Windows.Application.Deactivated?displayProperty=nameWithType>都不會針對 xbap 引發。</span><span class="sxs-lookup"><span data-stu-id="1450d-241">Neither <xref:System.Windows.Application.Activated?displayProperty=nameWithType> nor <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> is raised for XBAPs.</span></span>  
  
<a name="Application_Shutdown"></a>   
### <a name="application-shutdown"></a><span data-ttu-id="1450d-242">應用程式關閉</span><span class="sxs-lookup"><span data-stu-id="1450d-242">Application Shutdown</span></span>  
 <span data-ttu-id="1450d-243">應用程式一旦關閉，其存留期間便告結束，而應用程式關閉的可能原因包括：</span><span class="sxs-lookup"><span data-stu-id="1450d-243">The life of an application ends when it is shut down, which can occur for the following reasons:</span></span>  
  
- <span data-ttu-id="1450d-244">使用者關閉每個<xref:System.Windows.Window>。</span><span class="sxs-lookup"><span data-stu-id="1450d-244">A user closes every <xref:System.Windows.Window>.</span></span>  
  
- <span data-ttu-id="1450d-245">使用者關閉主<xref:System.Windows.Window>。</span><span class="sxs-lookup"><span data-stu-id="1450d-245">A user closes the main <xref:System.Windows.Window>.</span></span>  
  
- <span data-ttu-id="1450d-246">使用者藉由登出或關閉來結束 Windows 會話。</span><span class="sxs-lookup"><span data-stu-id="1450d-246">A user ends the Windows session by logging off or shutting down.</span></span>  
  
- <span data-ttu-id="1450d-247">已符合應用程式特定條件。</span><span class="sxs-lookup"><span data-stu-id="1450d-247">An application-specific condition has been met.</span></span>  
  
 <span data-ttu-id="1450d-248">為了協助您管理應用程式關閉<xref:System.Windows.Application> , 會<xref:System.Windows.Application.Shutdown%2A>提供方法、 <xref:System.Windows.Application.ShutdownMode%2A>屬性和<xref:System.Windows.Application.SessionEnding>和<xref:System.Windows.Application.Exit>事件。</span><span class="sxs-lookup"><span data-stu-id="1450d-248">To help you manage application shutdown, <xref:System.Windows.Application> provides the <xref:System.Windows.Application.Shutdown%2A> method, the <xref:System.Windows.Application.ShutdownMode%2A> property, and the <xref:System.Windows.Application.SessionEnding> and <xref:System.Windows.Application.Exit> events.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1450d-249"><xref:System.Windows.Application.Shutdown%2A>只能從具有<xref:System.Security.Permissions.UIPermission>的應用程式呼叫。</span><span class="sxs-lookup"><span data-stu-id="1450d-249"><xref:System.Windows.Application.Shutdown%2A> can only be called from applications that have <xref:System.Security.Permissions.UIPermission>.</span></span> <span data-ttu-id="1450d-250">獨立 WPF 應用程式一律具有此許可權。</span><span class="sxs-lookup"><span data-stu-id="1450d-250">Standalone WPF applications always have this permission.</span></span> <span data-ttu-id="1450d-251">不過, 在網際網路區域部分信任安全性沙箱中執行的 Xbap 則不會。</span><span class="sxs-lookup"><span data-stu-id="1450d-251">However, XBAPs running in the Internet zone partial-trust security sandbox do not.</span></span>  
  
#### <a name="shutdown-mode"></a><span data-ttu-id="1450d-252">程式關閉模式</span><span class="sxs-lookup"><span data-stu-id="1450d-252">Shutdown Mode</span></span>  
 <span data-ttu-id="1450d-253">大多數應用程式會在所有視窗關閉或主視窗關閉時一併關閉。</span><span class="sxs-lookup"><span data-stu-id="1450d-253">Most applications shut down either when all the windows are closed or when the main window is closed.</span></span> <span data-ttu-id="1450d-254">不過有時候，應用程式關閉的時機可能是由其他應用程式特定條件決定。</span><span class="sxs-lookup"><span data-stu-id="1450d-254">Sometimes, however, other application-specific conditions may determine when an application shuts down.</span></span> <span data-ttu-id="1450d-255">您可以設定<xref:System.Windows.Application.ShutdownMode%2A>下列<xref:System.Windows.ShutdownMode>其中一個列舉值, 以指定您的應用程式將會關閉的條件:</span><span class="sxs-lookup"><span data-stu-id="1450d-255">You can specify the conditions under which your application will shut down by setting <xref:System.Windows.Application.ShutdownMode%2A> with one of the following <xref:System.Windows.ShutdownMode> enumeration values:</span></span>  
  
- <xref:System.Windows.ShutdownMode.OnLastWindowClose>  
  
- <xref:System.Windows.ShutdownMode.OnMainWindowClose>  
  
- <xref:System.Windows.ShutdownMode.OnExplicitShutdown>  
  
 <span data-ttu-id="1450d-256">的預設值<xref:System.Windows.Application.ShutdownMode%2A>為<xref:System.Windows.ShutdownMode.OnLastWindowClose>, 表示應用程式會在使用者關閉應用程式中的最後一個視窗時自動關閉。</span><span class="sxs-lookup"><span data-stu-id="1450d-256">The default value of <xref:System.Windows.Application.ShutdownMode%2A> is <xref:System.Windows.ShutdownMode.OnLastWindowClose>, which means that an application automatically shuts down when the last window in the application is closed by the user.</span></span> <span data-ttu-id="1450d-257">不過, 如果您的應用程式應該在主視窗關閉時關閉, WPF 會在您將設定<xref:System.Windows.Application.ShutdownMode%2A>為<xref:System.Windows.ShutdownMode.OnMainWindowClose>時自動執行此工作。</span><span class="sxs-lookup"><span data-stu-id="1450d-257">However, if your application should be shut down when the main window is closed, WPF automatically does that if you set <xref:System.Windows.Application.ShutdownMode%2A> to <xref:System.Windows.ShutdownMode.OnMainWindowClose>.</span></span> <span data-ttu-id="1450d-258">這在下列範例中顯示。</span><span class="sxs-lookup"><span data-stu-id="1450d-258">This is shown in the following example.</span></span>  
  
 [!code-xaml[ApplicationShutdownModeSnippets#OnMainWindowCloseMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationShutdownModeSnippets/CS/Page1.xaml#onmainwindowclosemarkup)]  
  
 <span data-ttu-id="1450d-259">當您有應用程式特定的關機狀況時, <xref:System.Windows.Application.ShutdownMode%2A>請<xref:System.Windows.ShutdownMode.OnExplicitShutdown>將設定為。</span><span class="sxs-lookup"><span data-stu-id="1450d-259">When you have application-specific shutdown conditions, you set <xref:System.Windows.Application.ShutdownMode%2A> to <xref:System.Windows.ShutdownMode.OnExplicitShutdown>.</span></span> <span data-ttu-id="1450d-260">在此情況下, 您必須負責明確呼叫<xref:System.Windows.Application.Shutdown%2A>方法來關閉應用程式; 否則, 即使所有視窗都已關閉, 您的應用程式仍會繼續執行。</span><span class="sxs-lookup"><span data-stu-id="1450d-260">In this case, it is your responsibility to shut an application down by explicitly calling the <xref:System.Windows.Application.Shutdown%2A> method; otherwise, your application will continue running even if all the windows are closed.</span></span> <span data-ttu-id="1450d-261">請注意<xref:System.Windows.Application.Shutdown%2A> , <xref:System.Windows.Application.ShutdownMode%2A>當是<xref:System.Windows.ShutdownMode.OnLastWindowClose>或<xref:System.Windows.ShutdownMode.OnMainWindowClose>時, 會隱含地呼叫。</span><span class="sxs-lookup"><span data-stu-id="1450d-261">Note that <xref:System.Windows.Application.Shutdown%2A> is called implicitly when the <xref:System.Windows.Application.ShutdownMode%2A> is either <xref:System.Windows.ShutdownMode.OnLastWindowClose> or <xref:System.Windows.ShutdownMode.OnMainWindowClose>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1450d-262"><xref:System.Windows.Application.ShutdownMode%2A>可以從 XBAP 設定, 但它會被忽略;當 XBAP 在瀏覽器中離開時, 或裝載 XBAP 的瀏覽器關閉時, 就一律會關閉 XBAP。</span><span class="sxs-lookup"><span data-stu-id="1450d-262"><xref:System.Windows.Application.ShutdownMode%2A> can be set from an XBAP, but it is ignored; an XBAP is always shut down when it is navigated away from in a browser or when the browser that hosts the XBAP is closed.</span></span> <span data-ttu-id="1450d-263">如需詳細資訊，請參閱[覽概觀](navigation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="1450d-263">For more information, see [Navigation Overview](navigation-overview.md).</span></span>  
  
#### <a name="session-ending"></a><span data-ttu-id="1450d-264">工作階段結束</span><span class="sxs-lookup"><span data-stu-id="1450d-264">Session Ending</span></span>  
 <span data-ttu-id="1450d-265"><xref:System.Windows.Application.ShutdownMode%2A>屬性所描述的關機狀況是應用程式特有的。</span><span class="sxs-lookup"><span data-stu-id="1450d-265">The shutdown conditions that are described by the <xref:System.Windows.Application.ShutdownMode%2A> property are specific to an application.</span></span> <span data-ttu-id="1450d-266">不過在某些情況下，應用程式可能會因為外部狀況而關閉。</span><span class="sxs-lookup"><span data-stu-id="1450d-266">In some cases, though, an application may shut down as a result of an external condition.</span></span> <span data-ttu-id="1450d-267">當使用者透過下列動作結束 Windows 會話時, 就會發生最常見的外部狀況:</span><span class="sxs-lookup"><span data-stu-id="1450d-267">The most common external condition occurs when a user ends the Windows session by the following actions:</span></span>  
  
- <span data-ttu-id="1450d-268">登出</span><span class="sxs-lookup"><span data-stu-id="1450d-268">Logging off</span></span>  
  
- <span data-ttu-id="1450d-269">關機</span><span class="sxs-lookup"><span data-stu-id="1450d-269">Shutting down</span></span>  
  
- <span data-ttu-id="1450d-270">重新啟動</span><span class="sxs-lookup"><span data-stu-id="1450d-270">Restarting</span></span>  
  
- <span data-ttu-id="1450d-271">休眠</span><span class="sxs-lookup"><span data-stu-id="1450d-271">Hibernating</span></span>  
  
 <span data-ttu-id="1450d-272">若要偵測 Windows 會話何時結束, 您可以處理<xref:System.Windows.Application.SessionEnding>事件, 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="1450d-272">To detect when a Windows session ends, you can handle the <xref:System.Windows.Application.SessionEnding> event, as illustrated in the following example.</span></span>  
  
 [!code-xaml[ApplicationSessionEndingSnippets#HandlingSessionEndingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml#handlingsessionendingxaml)]  
  
 [!code-csharp[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml.cs#handlingsessionendingcodebehind)]
 [!code-vb[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/visualbasic/application.xaml.vb#handlingsessionendingcodebehind)]  
  
 <span data-ttu-id="1450d-273">在此範例中, 程式碼會<xref:System.Windows.SessionEndingCancelEventArgs.ReasonSessionEnding%2A>檢查屬性, 以判斷 Windows 會話的結束方式。</span><span class="sxs-lookup"><span data-stu-id="1450d-273">In this example, the code inspects the <xref:System.Windows.SessionEndingCancelEventArgs.ReasonSessionEnding%2A> property to determine how the Windows session is ending.</span></span> <span data-ttu-id="1450d-274">接著，它會使用這個值對使用者顯示確認訊息。</span><span class="sxs-lookup"><span data-stu-id="1450d-274">It uses this value to display a confirmation message to the user.</span></span> <span data-ttu-id="1450d-275">如果使用者不想要結束會話, 則程式碼會將設定<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>為`true` , 以防止 Windows 會話結束。</span><span class="sxs-lookup"><span data-stu-id="1450d-275">If the user does not want the session to end, the code sets <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> to `true` to prevent the Windows session from ending.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1450d-276"><xref:System.Windows.Application.SessionEnding>不會針對 Xbap 引發。</span><span class="sxs-lookup"><span data-stu-id="1450d-276"><xref:System.Windows.Application.SessionEnding> is not raised for XBAPs.</span></span>

#### <a name="exit"></a><span data-ttu-id="1450d-277">結束</span><span class="sxs-lookup"><span data-stu-id="1450d-277">Exit</span></span>  
 <span data-ttu-id="1450d-278">當應用程式關閉時，可能需要執行一些最終處理作業，例如保存應用程式狀態。</span><span class="sxs-lookup"><span data-stu-id="1450d-278">When an application shuts down, it may need to perform some final processing, such as persisting application state.</span></span> <span data-ttu-id="1450d-279">在這些情況下, 您可以處理<xref:System.Windows.Application.Exit>事件, `App_Exit`因為事件處理常式會在下列範例中執行。</span><span class="sxs-lookup"><span data-stu-id="1450d-279">For these situations, you can handle the <xref:System.Windows.Application.Exit> event, as the `App_Exit` event handler does in the following example.</span></span> <span data-ttu-id="1450d-280">它會定義為*app.xaml*檔案中的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="1450d-280">It is defined as an event handler in the *App.xaml* file.</span></span> <span data-ttu-id="1450d-281">它的實*App.xaml.cs*和*app.xaml*檔案中會反白顯示。</span><span class="sxs-lookup"><span data-stu-id="1450d-281">Its implementation is highlighted in the *App.xaml.cs* and *Application.xaml.vb* files.</span></span>
  
[!code-xaml[Defining-the-Exit-event-handler](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]  
  
 [!code-csharp[Handling-the-Exit-event](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=42-55)]
 [!code-vb[Handling-the-Exit-event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb?highlight=34-45)]  
  
 <span data-ttu-id="1450d-282">如需完整範例, 請參閱[跨應用程式會話保存和還原應用程式範圍的屬性](persist-and-restore-application-scope-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="1450d-282">For the complete example, see [Persist and Restore Application-Scope Properties Across Application Sessions](persist-and-restore-application-scope-properties.md).</span></span>  
  
 <span data-ttu-id="1450d-283"><xref:System.Windows.Application.Exit>可由獨立應用程式和 Xbap 處理。</span><span class="sxs-lookup"><span data-stu-id="1450d-283"><xref:System.Windows.Application.Exit> can be handled by both standalone applications and XBAPs.</span></span> <span data-ttu-id="1450d-284">若是 xbap, <xref:System.Windows.Application.Exit>則會在下列情況下引發:</span><span class="sxs-lookup"><span data-stu-id="1450d-284">For XBAPs, <xref:System.Windows.Application.Exit> is raised when in the following circumstances:</span></span>  
  
- <span data-ttu-id="1450d-285">XBAP 會離開。</span><span class="sxs-lookup"><span data-stu-id="1450d-285">An XBAP is navigated away from.</span></span>  
  
- <span data-ttu-id="1450d-286">在 Internet Explorer 中, 當裝載 XBAP 的索引標籤已關閉時。</span><span class="sxs-lookup"><span data-stu-id="1450d-286">In Internet Explorer, when the tab that is hosting the XBAP is closed.</span></span>  
  
- <span data-ttu-id="1450d-287">關閉瀏覽器時。</span><span class="sxs-lookup"><span data-stu-id="1450d-287">When the browser is closed.</span></span>  
  
#### <a name="exit-code"></a><span data-ttu-id="1450d-288">結束代碼</span><span class="sxs-lookup"><span data-stu-id="1450d-288">Exit Code</span></span>  
 <span data-ttu-id="1450d-289">應用程式大部分是由作業系統啟動，以回應使用者要求。</span><span class="sxs-lookup"><span data-stu-id="1450d-289">Applications are mostly launched by the operating system in response to a user request.</span></span> <span data-ttu-id="1450d-290">不過，應用程式可由另一個應用程式啟動，以執行某項特定工作。</span><span class="sxs-lookup"><span data-stu-id="1450d-290">However, an application can be launched by another application to perform some specific task.</span></span> <span data-ttu-id="1450d-291">關閉已啟動的應用程式時，正在啟動的應用程式可能需要知道已啟動之應用程式的關閉條件。</span><span class="sxs-lookup"><span data-stu-id="1450d-291">When the launched application shuts down, the launching application may want to know the condition under which the launched application shut down.</span></span> <span data-ttu-id="1450d-292">在這些情況下, Windows 可讓應用程式在關機時傳回應用程式結束代碼。</span><span class="sxs-lookup"><span data-stu-id="1450d-292">In these situations, Windows allows applications to return an application exit code on shutdown.</span></span> <span data-ttu-id="1450d-293">根據預設, WPF 應用程式會傳回結束代碼值0。</span><span class="sxs-lookup"><span data-stu-id="1450d-293">By default, WPF applications return an exit code value of 0.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1450d-294">當您從 Visual Studio 進行調試時, 應用程式關閉時, 應用程式結束代碼會顯示在 [**輸出**] 視窗中, 以如下所示的訊息:</span><span class="sxs-lookup"><span data-stu-id="1450d-294">When you debug from Visual Studio, the application exit code is displayed in the **Output** window when the application shuts down, in a message that looks like the following:</span></span>  
>   
>  `The program '[5340] AWPFApp.vshost.exe: Managed' has exited with code 0 (0x0).`  
>   
>  <span data-ttu-id="1450d-295">按一下 [**視圖**] 功能表上的 [**輸出**], 即可開啟 [**輸出**] 視窗。</span><span class="sxs-lookup"><span data-stu-id="1450d-295">You open the **Output** window by clicking **Output** on the **View** menu.</span></span>  
  
 <span data-ttu-id="1450d-296">若要變更結束代碼, 您可以呼叫<xref:System.Windows.Application.Shutdown%28System.Int32%29>多載, 這會接受整數引數做為結束代碼:</span><span class="sxs-lookup"><span data-stu-id="1450d-296">To change the exit code, you can call the <xref:System.Windows.Application.Shutdown%28System.Int32%29> overload, which accepts an integer argument to be the exit code:</span></span>  
  
 [!code-csharp[ApplicationExitSnippets#AppExitCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationExitSnippets/CSharp/MainWindow.xaml.cs#appexitcode)]
 [!code-vb[ApplicationExitSnippets#AppExitCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationExitSnippets/visualbasic/mainwindow.xaml.vb#appexitcode)]  
  
 <span data-ttu-id="1450d-297">您可以藉由處理<xref:System.Windows.Application.Exit>事件來偵測結束代碼的值, 並加以變更。</span><span class="sxs-lookup"><span data-stu-id="1450d-297">You can detect the value of the exit code, and change it, by handling the <xref:System.Windows.Application.Exit> event.</span></span> <span data-ttu-id="1450d-298">傳遞了<xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A>事件處理常式, 其可讓您存取具有屬性的結束代碼。 <xref:System.Windows.ExitEventArgs> <xref:System.Windows.Application.Exit></span><span class="sxs-lookup"><span data-stu-id="1450d-298">The <xref:System.Windows.Application.Exit> event handler is passed an <xref:System.Windows.ExitEventArgs> which provides access to the exit code with the <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A> property.</span></span> <span data-ttu-id="1450d-299">如需詳細資訊，請參閱 <xref:System.Windows.Application.Exit>。</span><span class="sxs-lookup"><span data-stu-id="1450d-299">For more information, see <xref:System.Windows.Application.Exit>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1450d-300">您可以在獨立應用程式和 Xbap 中設定結束代碼。</span><span class="sxs-lookup"><span data-stu-id="1450d-300">You can set the exit code in both standalone applications and XBAPs.</span></span> <span data-ttu-id="1450d-301">不過, Xbap 會忽略結束代碼值。</span><span class="sxs-lookup"><span data-stu-id="1450d-301">However, the exit code value is ignored for XBAPs.</span></span>  
  
<a name="Unhandled_Exceptions"></a>   
### <a name="unhandled-exceptions"></a><span data-ttu-id="1450d-302">未處理的例外狀況</span><span class="sxs-lookup"><span data-stu-id="1450d-302">Unhandled Exceptions</span></span>  
 <span data-ttu-id="1450d-303">有時候，應用程式可能會在異常情況下關閉，例如擲回非預期的例外狀況時。</span><span class="sxs-lookup"><span data-stu-id="1450d-303">Sometimes an application may shut down under abnormal conditions, such as when an unanticipated exception is thrown.</span></span> <span data-ttu-id="1450d-304">在此情況下，應用程式可能沒有可偵測及處理例外狀況的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1450d-304">In this case, the application may not have the code to detect and process the exception.</span></span> <span data-ttu-id="1450d-305">這種類型的例外狀況是未處理的例外狀況；在應用程式關閉之前，會顯示與下圖所示類似的通知。</span><span class="sxs-lookup"><span data-stu-id="1450d-305">This type of exception is an unhandled exception; a notification similar to that shown in the following figure is displayed before the application is closed.</span></span>  
  
 ![顯示未處理之例外狀況通知的螢幕擷取畫面。](./media/application-management-overview/unhandled-exception-notification.png)  
  
 <span data-ttu-id="1450d-307">從使用者體驗的觀點來看，應用程式最好能夠藉由執行下列部分或所有動作，來避免此預設行為：</span><span class="sxs-lookup"><span data-stu-id="1450d-307">From the user experience perspective, it is better for an application to avoid this default behavior by doing some or all of the following:</span></span>  
  
- <span data-ttu-id="1450d-308">顯示方便使用的資訊。</span><span class="sxs-lookup"><span data-stu-id="1450d-308">Displaying user-friendly information.</span></span>  
  
- <span data-ttu-id="1450d-309">嘗試繼續執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="1450d-309">Attempting to keep an application running.</span></span>  
  
- <span data-ttu-id="1450d-310">在 Windows 事件記錄檔中記錄詳細、開發人員易記的例外狀況資訊。</span><span class="sxs-lookup"><span data-stu-id="1450d-310">Recording detailed, developer-friendly exception information in the Windows event log.</span></span>  
  
 <span data-ttu-id="1450d-311">執行此支援取決於能夠偵測到未處理的例外狀況, 這就<xref:System.Windows.Application.DispatcherUnhandledException>是引發事件的目標。</span><span class="sxs-lookup"><span data-stu-id="1450d-311">Implementing this support depends on being able to detect unhandled exceptions, which is what the <xref:System.Windows.Application.DispatcherUnhandledException> event is raised for.</span></span>  
  
[!code-xaml[detecting-unhandled-exceptions](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml#handledispatcherunhandledexceptionxaml)]  
  
[!code-csharp[code-to-detect-unhandled-exceptions](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml.cs)]
[!code-vb[code-to-detect-unhandled-exceptions](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/visualbasic/application.xaml.vb)]  
  
 <span data-ttu-id="1450d-312">事件處理常式會傳遞一個<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs>參數, 其中包含與未處理的例外狀況相關的內容資訊,<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Exception%2A?displayProperty=nameWithType>包括例外狀況本身 ()。 <xref:System.Windows.Application.DispatcherUnhandledException></span><span class="sxs-lookup"><span data-stu-id="1450d-312">The <xref:System.Windows.Application.DispatcherUnhandledException> event handler is passed a <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs> parameter that contains contextual information regarding the unhandled exception, including the exception itself (<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Exception%2A?displayProperty=nameWithType>).</span></span> <span data-ttu-id="1450d-313">您可以使用這項資訊來判斷如何處理例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1450d-313">You can use this information to determine how to handle the exception.</span></span>  
  
 <span data-ttu-id="1450d-314">當您處理<xref:System.Windows.Application.DispatcherUnhandledException>時, 您應該<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A?displayProperty=nameWithType>將屬性設定`true`為; 否則, WPF 仍會將例外狀況視為未處理, 並還原成先前所述的預設行為。</span><span class="sxs-lookup"><span data-stu-id="1450d-314">When you handle <xref:System.Windows.Application.DispatcherUnhandledException>, you should set the <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A?displayProperty=nameWithType> property to `true`; otherwise, WPF still considers the exception to be unhandled and reverts to the default behavior described earlier.</span></span> <span data-ttu-id="1450d-315">如果引發未處理的例外狀況, 且<xref:System.Windows.Application.DispatcherUnhandledException>未處理事件, 或是事件已處理且<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A>設定為`false`, 則應用程式會立即關閉。</span><span class="sxs-lookup"><span data-stu-id="1450d-315">If an unhandled exception is raised and either the <xref:System.Windows.Application.DispatcherUnhandledException> event is not handled, or the event is handled and <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A> is set to `false`, the application shuts down immediately.</span></span> <span data-ttu-id="1450d-316">此外, 也不<xref:System.Windows.Application>會引發任何其他事件。</span><span class="sxs-lookup"><span data-stu-id="1450d-316">Furthermore, no other <xref:System.Windows.Application> events are raised.</span></span> <span data-ttu-id="1450d-317">因此, 如果您的應用<xref:System.Windows.Application.DispatcherUnhandledException>程式具有必須在應用程式關閉之前執行的程式碼, 則您需要處理。</span><span class="sxs-lookup"><span data-stu-id="1450d-317">Consequently, you need to handle <xref:System.Windows.Application.DispatcherUnhandledException> if your application has code that must run before the application shuts down.</span></span>  
  
 <span data-ttu-id="1450d-318">雖然應用程式可能因為未處理的例外狀況而關閉，但是應用程式通常是為了回應使用者的要求而關閉 (如下節所述)。</span><span class="sxs-lookup"><span data-stu-id="1450d-318">Although an application may shut down as a result of an unhandled exception, an application usually shuts down in response to a user request, as discussed in the next section.</span></span>  
  
<a name="Application_Lifetime_Events"></a>   
### <a name="application-lifetime-events"></a><span data-ttu-id="1450d-319">應用程式存留期事件</span><span class="sxs-lookup"><span data-stu-id="1450d-319">Application Lifetime Events</span></span>  
 <span data-ttu-id="1450d-320">獨立應用程式和 Xbap 沒有完全相同的存留期。</span><span class="sxs-lookup"><span data-stu-id="1450d-320">Standalone applications and XBAPs don't have exactly the same lifetimes.</span></span> <span data-ttu-id="1450d-321">下圖說明獨立應用程式存留期內的主要事件，並顯示這些事件的引發順序。</span><span class="sxs-lookup"><span data-stu-id="1450d-321">The following figure illustrates the key events in the lifetime of a standalone application and shows the sequence in which they are raised.</span></span>  
  
 <span data-ttu-id="1450d-322">![獨立應用程式 &#45; 應用程式物件事件](./media/applicationmodeloverview-applicationobjectevents.png "ApplicationModelOverview_ApplicationObjectEvents")</span><span class="sxs-lookup"><span data-stu-id="1450d-322">![Standalone Application &#45; Application Object Events](./media/applicationmodeloverview-applicationobjectevents.png "ApplicationModelOverview_ApplicationObjectEvents")</span></span>  
  
 <span data-ttu-id="1450d-323">同樣地, 下圖說明 XBAP 存留期的主要事件, 並顯示其引發的順序。</span><span class="sxs-lookup"><span data-stu-id="1450d-323">Likewise, the following figure illustrates the key events in the lifetime of an XBAP, and shows the sequence in which they are raised.</span></span>  
  
 <span data-ttu-id="1450d-324">![XBAP &#45; 應用程式物件事件](./media/applicationmodeloverview-applicationobjectevents-xbap.png "ApplicationModelOverview_ApplicationObjectEvents_xbap")</span><span class="sxs-lookup"><span data-stu-id="1450d-324">![XBAP &#45; Application Object Events](./media/applicationmodeloverview-applicationobjectevents-xbap.png "ApplicationModelOverview_ApplicationObjectEvents_xbap")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1450d-325">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1450d-325">See also</span></span>

- <xref:System.Windows.Application>
- [<span data-ttu-id="1450d-326">WPF 視窗概觀</span><span class="sxs-lookup"><span data-stu-id="1450d-326">WPF Windows Overview</span></span>](wpf-windows-overview.md)
- [<span data-ttu-id="1450d-327">瀏覽概觀</span><span class="sxs-lookup"><span data-stu-id="1450d-327">Navigation Overview</span></span>](navigation-overview.md)
- [<span data-ttu-id="1450d-328">WPF 應用程式資源、內容和資料檔案</span><span class="sxs-lookup"><span data-stu-id="1450d-328">WPF Application Resource, Content, and Data Files</span></span>](wpf-application-resource-content-and-data-files.md)
- [<span data-ttu-id="1450d-329">WPF 中的 Pack URI</span><span class="sxs-lookup"><span data-stu-id="1450d-329">Pack URIs in WPF</span></span>](pack-uris-in-wpf.md)
- <span data-ttu-id="1450d-330">[應用程式模型:How to 主題](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms749013(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1450d-330">[Application Model: How-to Topics](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms749013(v=vs.100))</span></span>
- [<span data-ttu-id="1450d-331">應用程式開發</span><span class="sxs-lookup"><span data-stu-id="1450d-331">Application Development</span></span>](index.md)
