---
title: "將可列印報表加入至 Visual Studio 應用程式"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- printing [Visual Studio], reports
- reports [Visual Basic], printing in Visual Studio
ms.assetid: 93928405-ef41-495e-bce2-9d43d5a7080a
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4ce2a8b12d8202a9f201a82b0d4a571249210d48
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="adding-printable-reports-to-visual-studio-applications"></a><span data-ttu-id="7f2fa-102">將可列印報表加入至 Visual Studio 應用程式</span><span class="sxs-lookup"><span data-stu-id="7f2fa-102">Adding Printable Reports to Visual Studio Applications</span></span>
<span data-ttu-id="7f2fa-103">Visual Studio 支援各種不同的報表方案，可將報告給 Visual Basic 應用程式的豐富資料。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-103">Visual Studio supports a variety of reporting solutions to help you add rich data reporting to your Visual Basic applications.</span></span> <span data-ttu-id="7f2fa-104">您可以建立並加入使用 ReportViewer 控制項、 採用的 Crystal Reports 或 SQL Server Reporting Services 報表。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-104">You can create and add reports using ReportViewer controls, Crystal Reports, or SQL Server Reporting Services.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7f2fa-105">SQL Server Reporting Services 是 SQL Server 2005，而不是 Visual Studio 的一部分。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-105">SQL Server Reporting Services is part of SQL Server 2005 rather than Visual Studio.</span></span> <span data-ttu-id="7f2fa-106">未安裝在您的系統上，除非您已安裝 SQL Server 2005 reporting Services。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-106">Reporting Services not installed on your system unless you have installed SQL Server 2005.</span></span>  
  
## <a name="overview-of-microsoft-reporting-technology-in-visual-basic-applications"></a><span data-ttu-id="7f2fa-107">Microsoft 報表技術，在 Visual Basic 應用程式的概觀</span><span class="sxs-lookup"><span data-stu-id="7f2fa-107">Overview of Microsoft Reporting Technology in Visual Basic Applications</span></span>  
 <span data-ttu-id="7f2fa-108">若要使用 Microsoft 報表技術應用程式中的選擇下列方法：</span><span class="sxs-lookup"><span data-stu-id="7f2fa-108">Choose from the following approaches to use a Microsoft reporting technology in your application:</span></span>  
  
-   <span data-ttu-id="7f2fa-109">Visual Basic Windows 應用程式中加入 ReportViewer 控制項的一個或多個執行個體。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-109">Add one or more instances of a ReportViewer control to a Visual Basic Windows application.</span></span>  
  
-   <span data-ttu-id="7f2fa-110">以程式設計方式將 SQL Server Reporting Services 整合藉由呼叫報表伺服器 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-110">Integrate SQL Server Reporting Services programmatically by making calls to the Report Server Web service.</span></span>  
  
-   <span data-ttu-id="7f2fa-111">ReportViewer 控制項和 Microsoft SQL Server 2005 報告的服務一起使用，當做報表檢視器和報表伺服器當做報表處理器使用控制項。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-111">Use the ReportViewer control and Microsoft SQL Server 2005 Reporting Services together, using the control as a report viewer and a report server as a report processor.</span></span> <span data-ttu-id="7f2fa-112">（請注意，是否您想要同時使用報表伺服器和 ReportViewer 控制項，您必須使用 Reporting Services 的 SQL Server 2005 版本）。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-112">(Note that you must use the SQL Server 2005 version of Reporting Services if you want to use a report server and the ReportViewer control together).</span></span>  
  
## <a name="using-reportviewer-controls"></a><span data-ttu-id="7f2fa-113">使用 ReportViewer 控制項</span><span class="sxs-lookup"><span data-stu-id="7f2fa-113">Using ReportViewer Controls</span></span>  
 <span data-ttu-id="7f2fa-114">在 Visual Basic Windows 應用程式報表功能嵌入的最簡單方式是將 ReportViewer 控制項加入至您的應用程式中的表單。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-114">The easiest way to embed report functionality into a Visual Basic Windows application is to add the ReportViewer control to a form in your application.</span></span> <span data-ttu-id="7f2fa-115">將報表處理功能，以您的應用程式直接加入的控制項，並提供整合式的報表設計工具，讓您可以建立報表使用任何 ADO.NET 資料物件中的資料。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-115">The control adds report processing capabilities directly to your application and provides an integrated report designer so that you can build reports using data from any ADO.NET data object.</span></span> <span data-ttu-id="7f2fa-116">完整的 API 以程式設計方式存取控制項，並報告，讓您可以設定執行階段功能。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-116">A full-featured API provides programmatic access to the control and reports so that you can configure run-time functionality.</span></span>  
  
 <span data-ttu-id="7f2fa-117">ReportViewer 提供內建的報表處理和檢視單一且任意散發的資料控制項中的功能。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-117">ReportViewer provides built-in report processing and viewing capability in a single, freely distributable data control.</span></span> <span data-ttu-id="7f2fa-118">選擇 ReportViewer 控制項，是否您需要下列的報表功能：</span><span class="sxs-lookup"><span data-stu-id="7f2fa-118">Choose ReportViewer controls if you require the following report functionality:</span></span>  
  
-   <span data-ttu-id="7f2fa-119">報表處理的用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-119">Report processing in the client application.</span></span> <span data-ttu-id="7f2fa-120">已處理的報表會出現在控制項所提供的檢視區域。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-120">A processed report appears in a view area provided by the control.</span></span>  
  
-   <span data-ttu-id="7f2fa-121">資料繫結至 ADO.NET 資料的資料表。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-121">Data binding to ADO.NET data tables.</span></span> <span data-ttu-id="7f2fa-122">您可以建立取用報表<xref:System.Data.DataTable>提供給控制項的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-122">You can create reports that consume <xref:System.Data.DataTable> instances supplied to the control.</span></span> <span data-ttu-id="7f2fa-123">您也可以直接至商務物件繫結。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-123">You can also bind directly to business objects.</span></span>  
  
-   <span data-ttu-id="7f2fa-124">您可以在您的應用程式中包含的可轉散發控制項。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-124">Redistributable controls that you can include in your application.</span></span>  
  
-   <span data-ttu-id="7f2fa-125">執行階段功能，例如頁面導覽、 列印、 搜尋及匯出格式。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-125">Runtime functionality such as page navigation, printing, searching, and export formats.</span></span> <span data-ttu-id="7f2fa-126">ReportViewer 工具列提供這些作業的支援。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-126">A ReportViewer toolbar provides support for these operations.</span></span>  
  
 <span data-ttu-id="7f2fa-127">若要使用 ReportViewer 控制項，您可以將它從拖曳**資料**Visual Studio 工具箱拖曳至表單，以在 Visual Basic Windows 應用程式中的區段。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-127">To use the ReportViewer control, you can drag it from the **Data** section of the Visual Studio Toolbox onto a form in your Visual Basic Windows application.</span></span>  
  
### <a name="creating-reports-in-visual-studio-for-reportviewer-controls"></a><span data-ttu-id="7f2fa-128">在 Visual Studio 中建立報表，ReportViewer 控制項</span><span class="sxs-lookup"><span data-stu-id="7f2fa-128">Creating Reports in Visual Studio for ReportViewer Controls</span></span>  
 <span data-ttu-id="7f2fa-129">若要建置 ReportViewer 在執行的報表，加入**報表**至您的專案範本。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-129">To build a report that runs in ReportViewer, add a **Report** template to your project.</span></span> <span data-ttu-id="7f2fa-130">Visual Studio 會建立用戶端報表定義 (.rdlc) 檔案、 將檔案加入您的專案，並在 Visual Studio 工作區中開啟整合式的報表設計師。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-130">Visual Studio creates a client report definition file (.rdlc), adds the file to your project, and opens an integrated report designer in the Visual Studio workspace.</span></span>  
  
 <span data-ttu-id="7f2fa-131">Visual Studio 報表設計工具整合**資料來源**視窗。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-131">The Visual Studio Report Designer integrates with the **Data Sources** window.</span></span> <span data-ttu-id="7f2fa-132">當您將欄位從**資料來源**加入報表，報表設計師視窗會將資料來源的相關中繼資料複製到報表定義檔案。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-132">When you drag a field from the **Data Sources** window to the report, the Report Designer copies metadata about the data source into the report definition file.</span></span> <span data-ttu-id="7f2fa-133">此中繼資料可由 ReportViewer 控制項來自動產生資料繫結程式碼。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-133">This metadata is used by the ReportViewer control to automatically generate data-binding code.</span></span>  
  
 <span data-ttu-id="7f2fa-134">Visual Studio 報表設計工具不包括報表預覽功能。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-134">The Visual Studio Report Designer does not include report preview functionality.</span></span> <span data-ttu-id="7f2fa-135">若要預覽報表，執行應用程式並預覽報表內嵌在其中。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-135">To preview your report, run the application and preview the report embedded in it.</span></span>  
  
|<span data-ttu-id="7f2fa-136">將基本報表功能加入至您的應用程式</span><span class="sxs-lookup"><span data-stu-id="7f2fa-136">To add basic report functionality to your application</span></span>|  
|---|    
|<span data-ttu-id="7f2fa-137">1.拖曳 ReportViewer 控制項從**資料** 索引標籤**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-137">1.  Drag a ReportViewer control from the **Data** tab of the **Toolbox** onto your form.</span></span><br /><span data-ttu-id="7f2fa-138">2.在 [ **專案** ] 功能表中，選擇 [ **加入新項目**]。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-138">2.  On the **Project** menu, choose **Add New Item**.</span></span> <span data-ttu-id="7f2fa-139">在**加入新項目**對話方塊中，選取**報表**圖示，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-139">In the **Add New Item** dialog box, select the **Report** icon and click **Add**.</span></span><br />     <span data-ttu-id="7f2fa-140">在開發環境中，開啟報表設計師和報表 (.rdlc) 檔案加入至專案。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-140">The Report Designer opens in the development environment, and a report (.rdlc) file is added to the project.</span></span><br /><span data-ttu-id="7f2fa-141">3.拖曳報表項目從**工具箱**在報表配置，然後排列它們，您的需要。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-141">3.  Drag report items from the **Toolbox** on the report layout and arrange them as you want.</span></span><br /><span data-ttu-id="7f2fa-142">4.將欄位從**資料來源**視窗，以在報表配置中的報表項目。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-142">4.  Drag fields from the **Data Sources** window to the report items in the report layout.</span></span>|  
  
## <a name="using-reporting-services-in-visual-basic-applications"></a><span data-ttu-id="7f2fa-143">在 Visual Basic 應用程式中使用 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="7f2fa-143">Using Reporting Services in Visual Basic Applications</span></span>  
 <span data-ttu-id="7f2fa-144">Reporting Services 是伺服器架構報表技術，隨附於 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-144">Reporting Services is a server-based reporting technology that is included with SQL Server.</span></span> <span data-ttu-id="7f2fa-145">Reporting Services 包含 ReportViewer 控制項中找不到的其他功能。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-145">Reporting Services includes additional features that are not found in the ReportViewer controls.</span></span> <span data-ttu-id="7f2fa-146">如果您需要下列功能，請選擇 Reporting Services:</span><span class="sxs-lookup"><span data-stu-id="7f2fa-146">Choose Reporting Services if you require any of the following features:</span></span>  
  
-   <span data-ttu-id="7f2fa-147">向外延展部署，而且可提供更佳的效能，針對高容量報表活動的複雜或長時間執行的報表及伺服器端報表處理。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-147">Scale-out deployment and server-side report processing that provides improved performance for complex or long-running reports and for high-volume report activity.</span></span>  
  
-   <span data-ttu-id="7f2fa-148">整合式的資料和報表處理，並且支援自訂報表控制項和豐富的轉譯輸出格式。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-148">Integrated data and report processing, with support for custom report controls and rich rendering output formats.</span></span>  
  
-   <span data-ttu-id="7f2fa-149">排程報表處理，讓您能夠精確地指定報表的執行。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-149">Scheduled report processing so that you can specify exactly when reports are run.</span></span>  
  
-   <span data-ttu-id="7f2fa-150">透過電子郵件或檔案共用位置的訂閱者 」 為基礎的報表散發。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-150">Subscriber-based report distribution through e-mail or to file share locations.</span></span>  
  
-   <span data-ttu-id="7f2fa-151">隨選報表，以便視商務使用者可以建立報表。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-151">Ad hoc reporting so that business users can create reports as needed.</span></span>  
  
-   <span data-ttu-id="7f2fa-152">將自訂的報表輸出路由傳送至收件者的動態清單的資料驅動訂閱。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-152">Data-driven subscriptions that route customized report output to a dynamic list of recipients.</span></span>  
  
-   <span data-ttu-id="7f2fa-153">自訂資料處理、 報表傳遞、 自訂驗證，以及報表轉譯的延伸。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-153">Custom extensions for data processing, report delivery, custom authentication, and report rendering.</span></span>  
  
 <span data-ttu-id="7f2fa-154">報表伺服器會實作為 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-154">The report server is implemented as Web service.</span></span> <span data-ttu-id="7f2fa-155">應用程式程式碼必須包含 Web 服務呼叫，以存取報表和其他中繼資料。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-155">Your application code must include calls to the Web service to access reports and other metadata.</span></span> <span data-ttu-id="7f2fa-156">Web 服務會提供完成以程式設計方式存取報表伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-156">The Web service provides complete programmatic access to a report server instance.</span></span>  
  
 <span data-ttu-id="7f2fa-157">由於 Reporting Services Web 為基礎的報表技術的預設檢視器會顯示 HTML 格式轉譯的報表。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-157">Because Reporting Services is a Web-based reporting technology, the default viewer shows reports that are rendered in HTML format.</span></span> <span data-ttu-id="7f2fa-158">如果您不想使用預設的報表呈現格式為 HTML，您必須撰寫您的應用程式的自訂報表檢視器。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-158">If you do not want to use HTML as the default report presentation format, you will have to write a custom report viewer for your application.</span></span>  
  
### <a name="creating-reports-in-visual-studio-for-reporting-services"></a><span data-ttu-id="7f2fa-159">在 Visual Studio 中建立報表，Reporting services</span><span class="sxs-lookup"><span data-stu-id="7f2fa-159">Creating Reports in Visual Studio for Reporting Services</span></span>  
 <span data-ttu-id="7f2fa-160">若要建立報表伺服器執行的報表，您建立報表定義 (.rdl) 檔案在 Business Intelligence Development Studio 中，透過 Visual Studio 中隨附 SQL Server 2005。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-160">To build reports that run on a report server, you create report definition (.rdl) files in Visual Studio through the Business Intelligence Development Studio, which is included with SQL Server 2005.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7f2fa-161">您必須擁有 SQL Server 2005 安裝，才能使用 SQL Server Reporting Services 和 Business Intelligence Development Studio。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-161">You must have SQL Server 2005 installed in order to use SQL Server Reporting Services and the Business Intelligence Development Studio.</span></span>  
  
 <span data-ttu-id="7f2fa-162">Business Intelligence Development Studio 加入專屬於 SQL Server 元件的專案範本。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-162">The Business Intelligence Development Studio adds project templates that are specific to SQL Server components.</span></span> <span data-ttu-id="7f2fa-163">若要建立報表，您可以選擇從**報表伺服器專案**或**報表伺服器專案精靈**範本。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-163">To create reports, you can choose from the **Report Server Project** or **Report Server Project Wizard** templates.</span></span> <span data-ttu-id="7f2fa-164">您可以指定資料來源連接和查詢，以各種不同的資料來源類型，包括 SQL Server、 Oracle、 Analysis Services、 XML 和 SQL Server Integration Services。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-164">You can specify data source connections and queries to a variety of data source types, including SQL Server, Oracle, Analysis Services, XML, and SQL Server Integration Services.</span></span> <span data-ttu-id="7f2fa-165">A**資料**索引標籤上，**配置** 索引標籤和**預覽** 索引標籤可讓您定義資料、 建立報表配置，以及預覽報表，所有在相同的工作區中。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-165">A **Data** tab, **Layout** tab, and **Preview** tab allow you to define data, create a report layout, and preview the report all in the same workspace.</span></span>  
  
 <span data-ttu-id="7f2fa-166">在兩項技術可重複使用您建立的控制項或報表伺服器的報表定義。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-166">Report definitions that you build for the control or the report server can be reused in either technology.</span></span>  
  
|<span data-ttu-id="7f2fa-167">若要建立報表伺服器執行的報表</span><span class="sxs-lookup"><span data-stu-id="7f2fa-167">To create a report that runs on a report server</span></span>|  
|---|    
|<span data-ttu-id="7f2fa-168">1.在**檔案**功能表上，選擇**新增**。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-168">1.  On the **File** menu, choose **New**.</span></span><br />     <span data-ttu-id="7f2fa-169">[ **新增專案** ] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-169">The **New Project** dialog box opens.</span></span><br /><span data-ttu-id="7f2fa-170">2.在**專案類型**] 窗格中，按一下 [**商業智慧專案**。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-170">2.  In the **Project types** pane, click **Business Intelligence Projects**.</span></span><br /><span data-ttu-id="7f2fa-171">3.在 [範本] 窗格中，選取**報表伺服器專案**或**報表伺服器專案精靈**。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-171">3.  In the Templates pane, select **Report Server Project** or **Report Server Project Wizard**.</span></span>|  
  
## <a name="using-reportviewer-controls-and-sql-server-reporting-services-together"></a><span data-ttu-id="7f2fa-172">使用 ReportViewer 控制項和 SQL Server Reporting Services 一起</span><span class="sxs-lookup"><span data-stu-id="7f2fa-172">Using ReportViewer Controls and SQL Server Reporting Services Together</span></span>  
 <span data-ttu-id="7f2fa-173">ReportViewer 控制項和 SQL Server 2005 Reporting Services 可一起在相同的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-173">The ReportViewer controls and SQL Server 2005 Reporting Services can be used together in the same application.</span></span>  
  
-   <span data-ttu-id="7f2fa-174">ReportViewer 控制項提供用來在您的應用程式中顯示報表檢視器。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-174">The ReportViewer control provides a viewer that is used to display reports in your application.</span></span>  
  
-   <span data-ttu-id="7f2fa-175">Reporting Services 提供的報表，並在遠端伺服器上執行所有的處理。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-175">Reporting Services provides the reports and performs all processing on a remote server.</span></span>  
  
 <span data-ttu-id="7f2fa-176">ReportViewer 控制項可以設定為顯示遠端的 Reporting Services 報表伺服器上所儲存和處理報表。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-176">The ReportViewer control can be configured to show reports that are stored and processed on a remote Reporting Services report server.</span></span> <span data-ttu-id="7f2fa-177">這種設定稱為*遠端處理模式*。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-177">This type of configuration is called *remote processing mode*.</span></span> <span data-ttu-id="7f2fa-178">在遠端處理模式中，控制項要求儲存遠端報表伺服器的報表。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-178">In remote processing mode, the control requests a report that is stored on a remote report server.</span></span> <span data-ttu-id="7f2fa-179">報表伺服器會執行所有報表處理、 資料處理和轉譯報表。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-179">The report server performs all report processing, data processing, and report rendering.</span></span> <span data-ttu-id="7f2fa-180">完成之後，轉譯的報表是傳回至控制項，而且顯示在檢視區域。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-180">A finished, rendered report is returned to the control and displayed in the view area.</span></span>  
  
 <span data-ttu-id="7f2fa-181">執行報表伺服器支援其他報表的匯出格式，有不同的報表參數化實作，使用資料來源類型都支援報表伺服器，以及透過以角色為基礎的授權模型上存取報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-181">Reports that run on a report server support additional export formats, have a different report parameterization implementation, use the data source types that are supported by the report server, and are accessed through the role-based authorization model on the report server.</span></span>  
  
 <span data-ttu-id="7f2fa-182">若要使用遠端處理模式中，指定的 URL 和伺服器報表的路徑設定 ReportViewer 控制項時。</span><span class="sxs-lookup"><span data-stu-id="7f2fa-182">To use remote processing mode, specify the URL and path to a server report when configuring the ReportViewer control.</span></span>
