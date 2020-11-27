---
title: WCF Visual Studio 範本
ms.date: 03/30/2017
ms.assetid: 6a608575-3535-4190-89da-911e24c8374f
ms.openlocfilehash: a3aa7e3ee57759ef54ddaa898fe036c4e3caa33e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279697"
---
# <a name="wcf-visual-studio-templates"></a><span data-ttu-id="ce0db-102">WCF Visual Studio 範本</span><span class="sxs-lookup"><span data-stu-id="ce0db-102">WCF Visual Studio Templates</span></span>

<span data-ttu-id="ce0db-103">Windows Communication Foundation (WCF) Visual Studio 範本是預先定義的專案和專案範本，可在 Visual Studio 中用來快速建立 WCF 服務和周圍的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ce0db-103">Windows Communication Foundation (WCF) Visual Studio templates are predefined project and item templates you can use in Visual Studio to quickly build WCF services and surrounding applications.</span></span>  
  
## <a name="using-the-wcf-templates"></a><span data-ttu-id="ce0db-104">使用 WCF 範本</span><span class="sxs-lookup"><span data-stu-id="ce0db-104">Using the WCF Templates</span></span>  

 <span data-ttu-id="ce0db-105">WCF Visual Studio 範本提供服務開發的基本類別結構。</span><span class="sxs-lookup"><span data-stu-id="ce0db-105">WCF Visual Studio templates provide a basic class structure for service development.</span></span> <span data-ttu-id="ce0db-106">具體來說，這些範本會提供服務合約、資料合約、服務實作和組態的基本定義。</span><span class="sxs-lookup"><span data-stu-id="ce0db-106">Specifically, these templates provide the basic definitions for service contract, data contract, service implementation, and configuration.</span></span> <span data-ttu-id="ce0db-107">您可以使用這些範本，建立具有最基本程式碼互動的簡單服務，以及適用於更進階服務的建置組塊。</span><span class="sxs-lookup"><span data-stu-id="ce0db-107">You can use these templates to create a simple service with minimal code interaction, as well as a building block for more advanced services.</span></span>  
  
### <a name="wcf-service-library-project-template"></a><span data-ttu-id="ce0db-108">WCF 服務程式庫專案範本</span><span class="sxs-lookup"><span data-stu-id="ce0db-108">WCF Service Library Project Template</span></span>  

 <span data-ttu-id="ce0db-109">[WCF 服務程式庫] 專案範本位於 [ **Visual c # \wcf]** ] 和 [ **visual Basic\WCF**] 底下的 [新增專案] 對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="ce0db-109">The WCF Service Library project template is available in the new project dialog box under **Visual C#\WCF** and **Visual Basic\WCF**.</span></span>  
  
 <span data-ttu-id="ce0db-110">當您使用 [ **WCF 服務** ] 範本建立新專案時，新專案會自動包含下列三個檔案：</span><span class="sxs-lookup"><span data-stu-id="ce0db-110">When you create a new project using the **WCF Service** template, the new project automatically includes the following three files:</span></span>  
  
- <span data-ttu-id="ce0db-111">服務合約檔案 (IService1.cs 或 IService1.vb)。</span><span class="sxs-lookup"><span data-stu-id="ce0db-111">Service contract file (IService1.cs or IService1.vb).</span></span> <span data-ttu-id="ce0db-112">服務合約檔案是已套用 WCF 服務屬性的介面。</span><span class="sxs-lookup"><span data-stu-id="ce0db-112">The service contract file is an interface that has WCF service attributes applied.</span></span> <span data-ttu-id="ce0db-113">這個檔案提供簡單服務的定義以示範如何定義服務，而其中也包含以參數為基礎的作業和簡單的資料合約範例。</span><span class="sxs-lookup"><span data-stu-id="ce0db-113">This file provides a definition of a simple service to show you how to define your services, and includes parameter-based operations and a simple data contract sample.</span></span> <span data-ttu-id="ce0db-114">這是建立 WCF 服務專案之後，在程式碼編輯器中顯示的預設檔案。</span><span class="sxs-lookup"><span data-stu-id="ce0db-114">This is the default file displayed in the code editor after creating a WCF service project.</span></span>  
  
- <span data-ttu-id="ce0db-115">服務實作檔案 (Service1.cs 或 Service1.vb)。</span><span class="sxs-lookup"><span data-stu-id="ce0db-115">Service implementation file (Service1.cs or Service1.vb).</span></span> <span data-ttu-id="ce0db-116">服務實作檔案會實作服務合約檔案中定義的合約。</span><span class="sxs-lookup"><span data-stu-id="ce0db-116">The service implementation file implements the contract defined in the service contract file.</span></span>  
  
- <span data-ttu-id="ce0db-117">應用程式組態檔案 (App.config)。</span><span class="sxs-lookup"><span data-stu-id="ce0db-117">Application configuration file (App.config).</span></span> <span data-ttu-id="ce0db-118">設定檔會使用安全的 HTTP 系結，提供 WCF 服務模型的基本元素。</span><span class="sxs-lookup"><span data-stu-id="ce0db-118">The configuration file provides the basic elements of a WCF service model with a secure HTTP binding.</span></span> <span data-ttu-id="ce0db-119">它也包含服務的端點，並會啟用中繼資料交換。</span><span class="sxs-lookup"><span data-stu-id="ce0db-119">It also includes an endpoint for the service and enables metadata exchange.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce0db-120">Visual Studio 設定為使用 WCF 服務主機（預設設定），將 App.config 檔辨識為專案的設定檔， [ ( # A1) ](wcf-service-host-wcfsvchost-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="ce0db-120">Visual Studio is configured to recognize the App.config file as the configuration file for the project when it is run using the [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md), which is the default configuration.</span></span> <span data-ttu-id="ce0db-121">如果是在可執行檔中裝載服務程式庫，您必須將組態程式碼移至該可執行檔的組態檔，因為 DLL 的組態檔是無效的。</span><span class="sxs-lookup"><span data-stu-id="ce0db-121">If you host the service library in an executable, you have to move the configuration code to the configuration file of the executable, as configuration files for DLLs are not valid.</span></span>  
  
### <a name="wcf-service-application-template"></a><span data-ttu-id="ce0db-122">WCF 服務應用程式範本</span><span class="sxs-lookup"><span data-stu-id="ce0db-122">WCF Service Application Template</span></span>  

 <span data-ttu-id="ce0db-123">[WCF 服務應用程式] 範本位於 [ **Visual c # \wcf]** 和 **visual Basic\WCF**] 下的 [新增專案] 對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="ce0db-123">The WCF Service Application template is available in the New Project dialog box under **Visual C#\WCF** and **Visual Basic\WCF**.</span></span>  
  
 <span data-ttu-id="ce0db-124">當您使用 **WCF Web 應用程式服務** 範本建立新專案時，專案會包含下列四個檔案：</span><span class="sxs-lookup"><span data-stu-id="ce0db-124">When you create a new project using the **WCF Web Application Service** template, the project includes the following four files:</span></span>  
  
- <span data-ttu-id="ce0db-125">服務主機檔案 (service1.svc)。</span><span class="sxs-lookup"><span data-stu-id="ce0db-125">Service host file (service1.svc).</span></span>  
  
- <span data-ttu-id="ce0db-126">服務合約檔案 (IService1.cs 或 IService1.vb)。</span><span class="sxs-lookup"><span data-stu-id="ce0db-126">Service contract file (IService1.cs or IService1.vb).</span></span>  
  
- <span data-ttu-id="ce0db-127">服務實作檔案 (Service1.svc.cs 或 Service1.svc.vb)。</span><span class="sxs-lookup"><span data-stu-id="ce0db-127">Service implementation file (Service1.svc.cs or Service1.svc.vb).</span></span>  
  
- <span data-ttu-id="ce0db-128">Web 組態檔案 (Web.config)。</span><span class="sxs-lookup"><span data-stu-id="ce0db-128">Web configuration file (Web.config).</span></span>  
  
 <span data-ttu-id="ce0db-129">範本會自動建立網站 (這會部署到虛擬目錄中) 並在其中裝載服務。</span><span class="sxs-lookup"><span data-stu-id="ce0db-129">The template automatically creates a Web site (to be deployed to a virtual directory) and hosts a service in it.</span></span>  
  
### <a name="wcf-web-site-template"></a><span data-ttu-id="ce0db-130">WCF 網站範本</span><span class="sxs-lookup"><span data-stu-id="ce0db-130">WCF Web Site Template</span></span>  

 <span data-ttu-id="ce0db-131">您可以在 [新增專案] 對話方塊中的 [ **Visual c # \Web Site\WCF service** and **Visual Basic\Web Site\WCF service**] 下找到 WCF 網站範本。</span><span class="sxs-lookup"><span data-stu-id="ce0db-131">The WCF Web Site template is available in the New Project dialog box under **Visual C#\Web Site\WCF Service** and **Visual Basic\Web Site\WCF Service**.</span></span> <span data-ttu-id="ce0db-132">這會建立與 WCF 服務應用程式範本相同的檔案，但是其組織方式猶如 ASP.NET 網站。</span><span class="sxs-lookup"><span data-stu-id="ce0db-132">This creates the same files as the WCF Service Application template but organizes it as if it were a ASP.NET web site.</span></span> <span data-ttu-id="ce0db-133">會建立 App_Code 和 App_Data 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ce0db-133">App_Code and App_Data folders are created.</span></span>  
  
### <a name="wcf-service-item-template"></a><span data-ttu-id="ce0db-134">WCF 服務項目範本</span><span class="sxs-lookup"><span data-stu-id="ce0db-134">WCF Service Item Template</span></span>  

 <span data-ttu-id="ce0db-135">WCF 服務專案範本是自訂範本，可讓您快速地將 WCF 服務新增至現有的 Visual Studio 專案。</span><span class="sxs-lookup"><span data-stu-id="ce0db-135">The WCF Service Item template is a custom template that provides a quick way to add WCF services to your existing Visual Studio projects.</span></span>  
  
 <span data-ttu-id="ce0db-136">若要使用這個範本，請移至 [ **方案總管** ] 窗格，以滑鼠右鍵按一下您的專案名稱，指向 [ **加入**]，然後按一下 [ **新增專案** ]，以啟動 [ **加入新專案** ] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ce0db-136">To use this template, go to the **Solution Explorer** pane, right-click your project name, point to **Add**, and then click **New Item** to launch the **Add New Item** dialog box.</span></span>  
  
 <span data-ttu-id="ce0db-137">服務介面和實作檔案會放置在根專案資料夾。</span><span class="sxs-lookup"><span data-stu-id="ce0db-137">The service interface and implementation files are placed in the root project folder.</span></span>  
  
 <span data-ttu-id="ce0db-138">如果新服務的組態區段和現有組態檔屬於相容的類型，則範本會嘗試加以合併。</span><span class="sxs-lookup"><span data-stu-id="ce0db-138">The template attempts to merge the configuration section of the new service to the existing configuration file, if they are compatible types.</span></span>  
  
 <span data-ttu-id="ce0db-139">如果現有專案是 Web 專案，也會建立服務主機檔案 (service1.svc)。</span><span class="sxs-lookup"><span data-stu-id="ce0db-139">A service host file (service1.svc) is also created if the existing project is a Web project.</span></span>  
  
### <a name="wcf-wf-service-project-and-item-template"></a><span data-ttu-id="ce0db-140">WCF WF 服務專案和項目範本。</span><span class="sxs-lookup"><span data-stu-id="ce0db-140">WCF WF Service Project and Item Template.</span></span>  

 <span data-ttu-id="ce0db-141">這些範本會建立裝載工作流程服務的 WCF 服務，這是可以像 web 服務一樣存取的工作流程。</span><span class="sxs-lookup"><span data-stu-id="ce0db-141">These templates create WCF services that host a Workflow Service, which is a workflow that can be accessed like a web service.</span></span> <span data-ttu-id="ce0db-142">XAML 或命令式程式撰寫模型各有不同的範本。</span><span class="sxs-lookup"><span data-stu-id="ce0db-142">Separate templates exist for XAML or imperative programming models.</span></span> <span data-ttu-id="ce0db-143">您可以使用這些範本來建立循序或狀態機器工作流程。</span><span class="sxs-lookup"><span data-stu-id="ce0db-143">Using the templates, you can create sequential or state machine workflow.</span></span> <span data-ttu-id="ce0db-144">如需這些工作流程類型的詳細資訊，請參閱 [如何：建立工作流程](../windows-workflow-foundation/how-to-create-a-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="ce0db-144">For more information on these types of workflow, see [How to: Create a Workflow](../windows-workflow-foundation/how-to-create-a-workflow.md).</span></span> <span data-ttu-id="ce0db-145">如需建立工作流程專案的詳細資訊，請參閱 [建立舊版工作流程專案](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)。</span><span class="sxs-lookup"><span data-stu-id="ce0db-145">For more information about creating workflow projects, see [Creating Legacy Workflow Projects](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer).</span></span>  
  
 <span data-ttu-id="ce0db-146">使用 XOML 類型的工作流程，而不是使用以程式碼為基礎的工作流程時，Visual Studio 設計工具會更</span><span class="sxs-lookup"><span data-stu-id="ce0db-146">Visual Studio designer is more responsive when XOML type workflows are used instead of code based ones.</span></span> <span data-ttu-id="ce0db-147">XOML 工作流程是預設要建立的工作流程類型。</span><span class="sxs-lookup"><span data-stu-id="ce0db-147">XOML workflow is the default workflow type to be created.</span></span>  
  
### <a name="wcf-syndication-service-library-template"></a><span data-ttu-id="ce0db-148">WCF 新聞訂閱服務程式庫範本</span><span class="sxs-lookup"><span data-stu-id="ce0db-148">WCF Syndication Service Library Template</span></span>  

 <span data-ttu-id="ce0db-149">此範本可讓您將 RSS 或 ATOM 格式的摘要公開為 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="ce0db-149">This template enables you to expose your feed in the RSS or ATOM format as a WCF service.</span></span> <span data-ttu-id="ce0db-150">如需詳細資訊，請參閱 [WCF 摘要整合](./feature-details/wcf-syndication.md)。</span><span class="sxs-lookup"><span data-stu-id="ce0db-150">For more information, see [WCF Syndication](./feature-details/wcf-syndication.md).</span></span>  
  
#### <a name="changing-the-address-of-the-feed"></a><span data-ttu-id="ce0db-151">變更摘要的位址</span><span class="sxs-lookup"><span data-stu-id="ce0db-151">Changing the Address of the Feed</span></span>  

 <span data-ttu-id="ce0db-152">新聞訂閱範本在執行期間使用 Internet Explorer。</span><span class="sxs-lookup"><span data-stu-id="ce0db-152">The syndication template uses Internet Explorer during execution.</span></span> <span data-ttu-id="ce0db-153">當您以滑鼠右鍵按一下 [ **方案 Explorer** ] Visual Studio 中的專案，選取 [ **屬性**]，然後選取 [ **調試** 程式] 索引標籤，就可以看到範本的預設位址。</span><span class="sxs-lookup"><span data-stu-id="ce0db-153">When you right-click your project in **Solutions Explorer** in Visual Studio, select **Properties**, then select the **Debug** tab and you can see the default address of the template.</span></span> <span data-ttu-id="ce0db-154">Internet Explorer 會嘗試開啟這個位址上的摘要。</span><span class="sxs-lookup"><span data-stu-id="ce0db-154">Internet Explorer attempts to open the feed at this address.</span></span>  
  
 <span data-ttu-id="ce0db-155">如果您變更摘要的位址，您也必須變更 [ **調試** 程式] 索引標籤中的位址。如果您沒有這麼做，Internet Explorer 會嘗試在預設位址開啟摘要，然後失敗。</span><span class="sxs-lookup"><span data-stu-id="ce0db-155">If you change the address of your feed, you must also change the address in the **Debug** tab. If you do not do this, Internet Explorer attempts to open the feed at the default address and fail.</span></span>  
  
### <a name="ajax-enabled-wcf-service-item-template"></a><span data-ttu-id="ce0db-156">具備 AJAX 能力的 WCF 服務項目範本</span><span class="sxs-lookup"><span data-stu-id="ce0db-156">AJAX enabled WCF Service Item Template</span></span>  

 <span data-ttu-id="ce0db-157">此範本會以 WCF 服務的形式公開 AJAX 控制項。</span><span class="sxs-lookup"><span data-stu-id="ce0db-157">This template exposes an AJAX control as a WCF service.</span></span> <span data-ttu-id="ce0db-158">如需 AJAX 控制項的詳細資訊，請參閱 [ajax 控制項檔](/aspnet/ajax/)集。</span><span class="sxs-lookup"><span data-stu-id="ce0db-158">For more information on AJAX controls, see the [AJAX control documentation](/aspnet/ajax/).</span></span>  
  
### <a name="silverlight-enabled-wcf-service-item-template"></a><span data-ttu-id="ce0db-159">啟用 Silverlight 的 WCF 服務項目範本</span><span class="sxs-lookup"><span data-stu-id="ce0db-159">Silverlight-enabled WCF Service Item Template</span></span>  

 <span data-ttu-id="ce0db-160">這個範本會建立提供資料給 Silverlight 用戶端或前端的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="ce0db-160">This template creates a Web service that provides data to a Silverlight client or front-end.</span></span> <span data-ttu-id="ce0db-161">範本可以加入至網站或 Web 應用程式專案，以建立 WCF 服務，其中包含支援與 Silverlight 用戶端進行通訊的服務程式代碼和設定。</span><span class="sxs-lookup"><span data-stu-id="ce0db-161">The template can be added to a Web site or Web application project to create a WCF service, which includes service code and configuration that support communicating with a Silverlight client.</span></span> <span data-ttu-id="ce0db-162">然後，您可以使用 **加入服務參考** 將服務的用戶端 proxy 新增至用戶端，並在 silverlight 用戶端與啟用 SILVERLIGHT 的 WCF 服務之間交換資料。</span><span class="sxs-lookup"><span data-stu-id="ce0db-162">You can then use **Add Service Reference** to add a client proxy of the service to the client, and exchange data between the Silverlight client and the Silverlight-enabled WCF service.</span></span>  
  
 <span data-ttu-id="ce0db-163">若要存取這個範本，請在 **方案總管** 中的網站或 web 應用程式專案上按一下滑鼠右鍵，按一下 [ **加入新專案**]，然後按一下 [ **啟用 Silverlight 的 WCF 服務**]。</span><span class="sxs-lookup"><span data-stu-id="ce0db-163">To access this template, right-click a Web site or Web application project in **Solution Explorer**, click **Add a new item**, and click **Silverlight-enabled WCF Service**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce0db-164">啟用 Silverlight 的 WCF 服務會在不啟用任何安全性設定的情況下公開 `basicHttpBinding` 端點。</span><span class="sxs-lookup"><span data-stu-id="ce0db-164">The Silverlight-enabled WCF Service exposes a `basicHttpBinding` endpoint without enabling any security settings.</span></span> <span data-ttu-id="ce0db-165">因此，所有連接到這個服務的用戶端，都可以取得此服務的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ce0db-165">Therefore, information about the service can be obtained by all clients that connect to this service.</span></span> <span data-ttu-id="ce0db-166">同樣地，服務和用戶端之間的交換訊息也不會經過簽署或加密。</span><span class="sxs-lookup"><span data-stu-id="ce0db-166">Messages exchanged between the service and the client are also not signed or encrypted.</span></span> <span data-ttu-id="ce0db-167">為了確保端點安全性，您應該使用 ASP.NET 驗證、HTTPS 或其他機制。</span><span class="sxs-lookup"><span data-stu-id="ce0db-167">To secure the endpoint properly, you should use ASP.NET authentication, HTTPS or other mechanisms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce0db-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce0db-168">See also</span></span>

- [<span data-ttu-id="ce0db-169">WCF 服務主機 (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="ce0db-169">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)
- [<span data-ttu-id="ce0db-170">WCF 測試用戶端 (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="ce0db-170">WCF Test Client (WcfTestClient.exe)</span></span>](wcf-test-client-wcftestclient-exe.md)
