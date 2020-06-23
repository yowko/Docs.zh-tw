---
title: WCF 服務主機 (WcfSvcHost.exe)
description: 使用 WCF 服務主機來裝載並測試您已執行的服務。 您可以使用 WCF 測試用戶端或您自己的用戶端來測試服務。
ms.date: 03/30/2017
ms.assetid: 8643a63d-a357-4c39-bd6c-cdfdf71e370e
ms.openlocfilehash: efc9512766d2a9cc814083ab632226d98917bf4e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245722"
---
# <a name="wcf-service-host-wcfsvchostexe"></a><span data-ttu-id="30654-104">WCF 服務主機 (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="30654-104">WCF Service Host (WcfSvcHost.exe)</span></span>

<span data-ttu-id="30654-105">Windows Communication Foundation （WCF）服務主機（WcfSvcHost.exe）可讓您啟動 Visual Studio 偵錯工具（F5），以自動裝載並測試您已執行的服務。</span><span class="sxs-lookup"><span data-stu-id="30654-105">Windows Communication Foundation (WCF) Service Host (WcfSvcHost.exe) allows you to launch the Visual Studio debugger (F5) to automatically host and test a service you have implemented.</span></span> <span data-ttu-id="30654-106">然後，您可以使用 WCF 測試用戶端（WcfTestClient.exe）或您自己的用戶端來測試服務，以尋找並修正任何可能的錯誤。</span><span class="sxs-lookup"><span data-stu-id="30654-106">You can then test the service using WCF Test Client (WcfTestClient.exe), or your own client, to find and fix any potential errors.</span></span>

## <a name="wcf-service-host"></a><span data-ttu-id="30654-107">WCF 服務主機</span><span class="sxs-lookup"><span data-stu-id="30654-107">WCF Service Host</span></span>

<span data-ttu-id="30654-108">WCF 服務主機會列舉 WCF 服務專案中的服務、載入專案的設定，以及為它找到的每個服務具現化主機。</span><span class="sxs-lookup"><span data-stu-id="30654-108">WCF Service Host enumerates the services in a WCF service project, loads the project’s configuration, and instantiates a host for each service that it finds.</span></span> <span data-ttu-id="30654-109">此工具會透過 WCF 服務範本整合到 Visual Studio，並在您開始進行專案的檢查時叫用。</span><span class="sxs-lookup"><span data-stu-id="30654-109">The tool is integrated into Visual Studio through the WCF Service template and is invoked when you start to debug your project.</span></span>

<span data-ttu-id="30654-110">藉由使用 WCF 服務主機，您可以裝載 WCF 服務（在 WCF 服務程式庫專案中），而不需要在開發期間撰寫額外的程式碼或認可特定主機。</span><span class="sxs-lookup"><span data-stu-id="30654-110">By using WCF Service Host, you can host a WCF service (in a WCF service library project) without writing extra code or committing to a specific host during development.</span></span>

> [!NOTE]
> <span data-ttu-id="30654-111">WCF 服務主機不支援部分信任。</span><span class="sxs-lookup"><span data-stu-id="30654-111">WCF Service Host does not support Partial Trust.</span></span> <span data-ttu-id="30654-112">如果您想要在部分信任中使用 WCF 服務，請不要使用 Visual Studio 中的 [WCF 服務程式庫] 專案範本來建立您的服務。</span><span class="sxs-lookup"><span data-stu-id="30654-112">If you want to use a WCF Service in Partial Trust, do not use the WCF Service Library Project template in Visual Studio to build your service.</span></span> <span data-ttu-id="30654-113">而是在 Visual Studio 中，選擇 [WCF 服務網站] 範本來建立新的網站，這可以在支援 WCF 部分信任的 Web 服務器上裝載服務。</span><span class="sxs-lookup"><span data-stu-id="30654-113">Instead, create a New WebSite in Visual Studio by choosing the WCF Service WebSite template, which can host the service in a WebServer on which WCF Partial Trust is supported.</span></span>

## <a name="project-types-hosted-by-wcf-service-host"></a><span data-ttu-id="30654-114">WCF 服務主機裝載的專案類型</span><span class="sxs-lookup"><span data-stu-id="30654-114">Project Types hosted by WCF Service Host</span></span>

<span data-ttu-id="30654-115">WCF 服務主機可以裝載下列 WCF 服務程式庫專案類型： WCF 服務程式庫、順序工作流程服務程式庫、狀態機器工作流程服務程式庫和新聞訂閱服務程式庫。</span><span class="sxs-lookup"><span data-stu-id="30654-115">WCF Service Host can host the following WCF service library project types: WCF Service Library, Sequential Workflow Service Library, State Machine Workflow Service Library and Syndication Service Library.</span></span> <span data-ttu-id="30654-116">WCF 服務主機也可以使用 [**新增專案**] 功能，裝載可以加入至服務程式庫專案的服務。</span><span class="sxs-lookup"><span data-stu-id="30654-116">WCF Service Host can also host those services that can be added to a service library project using the **Add Item** functionality.</span></span> <span data-ttu-id="30654-117">這包括 WCF 服務、WF 狀態機器服務、WF 順序服務、XAML WF 狀態機器服務和 XAML WF 順序服務。</span><span class="sxs-lookup"><span data-stu-id="30654-117">This includes WCF Service, WF State Machine Service, WF Sequential Service, XAML WF State Machine Service and XAML WF Sequential Service.</span></span>

<span data-ttu-id="30654-118">但是，您應該注意到，此工具無法協助您設定主機。</span><span class="sxs-lookup"><span data-stu-id="30654-118">You should note, however, that the tool will not help you to configure a host.</span></span> <span data-ttu-id="30654-119">對於這項工作，您必須手動編輯 App.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="30654-119">For this task, you must manually edit the App.config file.</span></span> <span data-ttu-id="30654-120">此工具也不會驗證使用者定義的組態檔。</span><span class="sxs-lookup"><span data-stu-id="30654-120">The tool also does not validate user-defined configuration files.</span></span>

> [!CAUTION]
> <span data-ttu-id="30654-121">您不應該在生產環境中使用 WCF 服務主機來裝載服務，因為它並未針對此用途進行設計。</span><span class="sxs-lookup"><span data-stu-id="30654-121">You should not use WCF Service Host to host services in a production environment, as it was not engineered for this purpose.</span></span>  <span data-ttu-id="30654-122">WCF 服務主機不支援這類環境的可靠性、安全性和管理性需求。</span><span class="sxs-lookup"><span data-stu-id="30654-122">WCF Service Host does not support the reliability, security, and manageability requirements of such an environment.</span></span> <span data-ttu-id="30654-123">請改用 IIS，因為它提供比較好的可靠性和監視功能，而且是一般慣用於裝載服務的解決方案。</span><span class="sxs-lookup"><span data-stu-id="30654-123">Instead, use IIS since it provides superior reliability and monitoring features, and is the preferred solution for hosting services.</span></span> <span data-ttu-id="30654-124">一旦服務的開發完成後，您應該將服務從 WCF 服務主機遷移至 IIS。</span><span class="sxs-lookup"><span data-stu-id="30654-124">Once development of your services is complete, you should migrate the services from WCF Service Host to IIS.</span></span>

## <a name="scenarios-for-using-wcf-service-host-inside-visual-studio"></a><span data-ttu-id="30654-125">在 Visual Studio 內使用 WCF 服務主機的案例</span><span class="sxs-lookup"><span data-stu-id="30654-125">Scenarios for Using WCF Service Host inside Visual Studio</span></span>

<span data-ttu-id="30654-126">下表列出 [**命令列引數**] 對話方塊中的所有參數，您可以在 [**方案瀏覽器**] Visual Studio 中的專案上按一下滑鼠右鍵，選取 [**屬性**]，然後選取 [**調試**程式] 索引標籤，再按一下 [**起始專案**]，即可找到此對話方塊。</span><span class="sxs-lookup"><span data-stu-id="30654-126">The following table lists all the parameters in the **Command line arguments** dialog box, which can be found by right-clicking your project in **Solutions Explorer** in Visual Studio, selecting **Properties**, then selecting the **Debug** tab and clicking **Start Project**.</span></span> <span data-ttu-id="30654-127">這些參數在設定 WCF 服務主機時很有用。</span><span class="sxs-lookup"><span data-stu-id="30654-127">These parameters are useful in configuring WCF Service Host.</span></span>

|<span data-ttu-id="30654-128">參數</span><span class="sxs-lookup"><span data-stu-id="30654-128">Parameter</span></span>|<span data-ttu-id="30654-129">意義</span><span class="sxs-lookup"><span data-stu-id="30654-129">Meaning</span></span>|
|---------------|-------------|
|`/client`|<span data-ttu-id="30654-130">選擇性參數，會指定要在裝載服務後執行之可執行檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="30654-130">An optional parameter that specifies the path to an executable to run after the services are hosted.</span></span> <span data-ttu-id="30654-131">這會在裝載之後啟動 WCF 測試用戶端。</span><span class="sxs-lookup"><span data-stu-id="30654-131">This launches WCF Test Client following hosting.</span></span>|
|`/clientArg`|<span data-ttu-id="30654-132">會指定字串做為傳遞給自訂用戶端應用程式的引數。</span><span class="sxs-lookup"><span data-stu-id="30654-132">Specify a string as an argument that is passed to the custom client application.</span></span>|
|`/?`|<span data-ttu-id="30654-133">顯示說明文字。</span><span class="sxs-lookup"><span data-stu-id="30654-133">Displays the help text.</span></span>|

#### <a name="using-wcf-test-client"></a><span data-ttu-id="30654-134">使用 WCF 測試用戶端</span><span class="sxs-lookup"><span data-stu-id="30654-134">Using WCF Test Client</span></span>

<span data-ttu-id="30654-135">在您建立新的 WCF 服務專案並按下 F5 啟動偵錯工具後，WCF 服務主機會開始裝載它在您專案中找到的所有服務。</span><span class="sxs-lookup"><span data-stu-id="30654-135">After you create a new WCF service project and press F5 to start the debugger, WCF Service Host starts hosting all the services it finds in your project.</span></span> <span data-ttu-id="30654-136">WCF 測試用戶端會自動開啟，並顯示在設定檔案中定義的服務端點清單。</span><span class="sxs-lookup"><span data-stu-id="30654-136">WCF Test Client automatically opens and displays a list of service endpoints defined in the configuration file.</span></span> <span data-ttu-id="30654-137">您可以從主視窗中測試參數並叫用服務。</span><span class="sxs-lookup"><span data-stu-id="30654-137">From the main window, you can test the parameters and invoke your service.</span></span>

<span data-ttu-id="30654-138">若要確定已使用 WCF 測試用戶端，請在 [**方案 Explorer** ] 中的專案上按一下滑鼠右鍵 Visual Studio，選取 [**屬性**]，然後選取 [**調試**程式] 索引標籤。按一下 [**起始專案**]，並確定下列專案出現在 [**命令列引數**] 對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="30654-138">To make sure that WCF Test Client is used, right-click your project in **Solutions Explorer** in Visual Studio, select **Properties**, then select the **Debug** tab. Click **Start Project** and ensure that the following appears in the **Command line arguments** dialog box.</span></span>

`/client:WcfTestClient.exe`

#### <a name="using-a-custom-client"></a><span data-ttu-id="30654-139">使用自訂用戶端</span><span class="sxs-lookup"><span data-stu-id="30654-139">Using a Custom Client</span></span>

<span data-ttu-id="30654-140">若要使用自訂用戶端，請在 [**方案 Explorer** ] 中的專案上按一下滑鼠右鍵，Visual Studio，選取 [**屬性**]，然後選取 [**調試**程式] 索引標籤。按一下 [**開始專案**]，然後 `/client` 在 [**命令列引數**] 對話方塊中編輯參數，以指向您的自訂用戶端，如下列範例</span><span class="sxs-lookup"><span data-stu-id="30654-140">To use a custom client, right-click your project in **Solutions Explorer** in Visual Studio, select **Properties**, then select the **Debug** tab. Click **Start Project** and edit the `/client` parameter in the **Command line arguments** dialog box to point to your custom client, as indicated in the following example.</span></span>

`/client:"path/CustomClient.exe"`

<span data-ttu-id="30654-141">當您按下 F5 再次啟動服務時，WCF 服務主機會在您啟動偵錯工具時自動啟動您的自訂用戶端。</span><span class="sxs-lookup"><span data-stu-id="30654-141">When you press F5 to start the service again, WCF Service Host automatically starts your custom client when you launch the debugger.</span></span>

<span data-ttu-id="30654-142">您也可以使用 `/clientArg:` 參數，指定字串做為傳遞給自訂用戶端應用程式的引數，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="30654-142">You can also use the `/clientArg:` parameter to specify a string as an argument that is passed to the custom client application, as indicated in the following example.</span></span>

`/client:"path/CustomClient.exe" /clientArg:"arguments that are passed to Client"`

<span data-ttu-id="30654-143">例如，如果您使用新聞訂閱服務程式庫範本，就可以使用下列命令列引數：</span><span class="sxs-lookup"><span data-stu-id="30654-143">For example, if you are using the Syndication Service Library template, you can use the following command line arguments,</span></span>

`/client:iexplore.exe /clientArgs:http://localhost:8731/Design_Time_Addresses/Feed1/`

#### <a name="specifying-no-client"></a><span data-ttu-id="30654-144">不指定任何用戶端</span><span class="sxs-lookup"><span data-stu-id="30654-144">Specifying No Client</span></span>

<span data-ttu-id="30654-145">若要指定 WCF 服務裝載後不會使用任何用戶端，請以滑鼠右鍵按一下 [**方案瀏覽器**] 中的專案 Visual Studio，選取 [**屬性**]，然後選取 [**調試**程式] 索引標籤。按一下 [**起始專案**]，並將 [**命令列引數**] 對話方塊保留空白。</span><span class="sxs-lookup"><span data-stu-id="30654-145">To specify that no client will be used after WCF service hosting, right-click your project in **Solutions Explorer** in Visual Studio, select **Properties**, then select the **Debug** tab. Click **Start Project** and leave the **Command line arguments** dialog box blank.</span></span>

#### <a name="using-a-custom-host"></a><span data-ttu-id="30654-146">使用自訂主機</span><span class="sxs-lookup"><span data-stu-id="30654-146">Using a Custom Host</span></span>

<span data-ttu-id="30654-147">若要使用自訂主機，請在 [**方案 Explorer** ] 中的專案上按一下滑鼠右鍵 Visual Studio，選取 [**屬性**]，然後選取 [**調試**程式] 索引標籤。按一下 [**啟動外部程式**]，並輸入自訂主機的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="30654-147">To use a custom host, right-click your project in **Solutions Explorer** in Visual Studio, select **Properties**, then select the **Debug** tab. Click **Start External Program** and enter the full path to the custom host.</span></span> <span data-ttu-id="30654-148">您也可以使用 [**命令列引數**] 對話方塊來指定要傳遞至主機的引數。</span><span class="sxs-lookup"><span data-stu-id="30654-148">You can also use the **Command line arguments** dialog box to specify arguments to be passed to the host.</span></span>

## <a name="wcf-service-host-user-interface"></a><span data-ttu-id="30654-149">WCF 服務主機使用者介面</span><span class="sxs-lookup"><span data-stu-id="30654-149">WCF Service Host User Interface</span></span>

<span data-ttu-id="30654-150">當您一開始叫用 WCF 服務主機（在 Visual Studio 內按 F5）時，[ **WCF 服務主機**] 視窗會自動開啟。</span><span class="sxs-lookup"><span data-stu-id="30654-150">When you initially invoke WCF Service Host (by pressing F5 inside Visual Studio), the **WCF Service Host** window automatically opens.</span></span> <span data-ttu-id="30654-151">當 WCF 服務主機正在執行時，程式的圖示會出現在通知區域中。</span><span class="sxs-lookup"><span data-stu-id="30654-151">When WCF Service Host is running, the program's icon appears in the notification area.</span></span> <span data-ttu-id="30654-152">按兩下圖示以開啟 [ **WCF 服務主機**] 視窗</span><span class="sxs-lookup"><span data-stu-id="30654-152">Double-click the icon to open the **WCF Service Host** window</span></span>

<span data-ttu-id="30654-153">當服務裝載期間發生錯誤時，[WCF 服務主機] 對話方塊會開啟以顯示相關資訊。</span><span class="sxs-lookup"><span data-stu-id="30654-153">When errors occur during service hosting, WCF Service Host dialog box will open to display relevant information.</span></span>

<span data-ttu-id="30654-154">[ **WCF 服務主機**] 主視窗包含兩個功能表：</span><span class="sxs-lookup"><span data-stu-id="30654-154">The **WCF Service Host** main window contains two menus:</span></span>

- <span data-ttu-id="30654-155">**File**：包含**Close**和**Exit**命令。</span><span class="sxs-lookup"><span data-stu-id="30654-155">**File**: Contains the **Close** and **Exit** commands.</span></span> <span data-ttu-id="30654-156">當您按一下 [**關閉**] 時，[ **WCF 服務主機**] 對話方塊會關閉，但仍會繼續裝載服務。</span><span class="sxs-lookup"><span data-stu-id="30654-156">When you click **Close**, the **WCF Service Host** dialog box closes, but the services continue to be hosted.</span></span> <span data-ttu-id="30654-157">當**您按一下 [** 結束] 時，[WCF 服務主機] 也會關閉。</span><span class="sxs-lookup"><span data-stu-id="30654-157">When you click **Exit**, WCF Service Host is also shut down.</span></span> <span data-ttu-id="30654-158">這還會停止所有裝載的服務。</span><span class="sxs-lookup"><span data-stu-id="30654-158">This also stops all hosted services.</span></span>

- <span data-ttu-id="30654-159">**Help**：包含**About**命令，其中包含版本資訊。</span><span class="sxs-lookup"><span data-stu-id="30654-159">**Help**: Contains the **About** command that contains version information.</span></span> <span data-ttu-id="30654-160">它也包含可開啟說明檔的**help**命令。</span><span class="sxs-lookup"><span data-stu-id="30654-160">It also contains the **Help** command that can open a help file.</span></span>

<span data-ttu-id="30654-161">主要的 [ **WCF 服務主機**] 視窗包含兩個區域：</span><span class="sxs-lookup"><span data-stu-id="30654-161">The main **WCF Service Host** window contains two areas:</span></span>

- <span data-ttu-id="30654-162">第一個區域是 [**服務**]。</span><span class="sxs-lookup"><span data-stu-id="30654-162">The first area is **Service**.</span></span> <span data-ttu-id="30654-163">其中包含一份顯示所有服務基本資訊的清單。</span><span class="sxs-lookup"><span data-stu-id="30654-163">It contains a list that displays basic information of all services.</span></span> <span data-ttu-id="30654-164">這些資訊包括：</span><span class="sxs-lookup"><span data-stu-id="30654-164">The information includes:</span></span>

  - <span data-ttu-id="30654-165">**服務**：列出所有服務。</span><span class="sxs-lookup"><span data-stu-id="30654-165">**Service**: Lists all the services.</span></span>

  - <span data-ttu-id="30654-166">**狀態**：列出服務的狀態。</span><span class="sxs-lookup"><span data-stu-id="30654-166">**Status**: Lists the status of the service.</span></span> <span data-ttu-id="30654-167">有效值為「已啟動」、「已停止」和「錯誤」。</span><span class="sxs-lookup"><span data-stu-id="30654-167">Valid values are "Started", "Stopped," and "Error".</span></span>

  - <span data-ttu-id="30654-168">**中繼資料位址**：顯示服務的中繼資料位址。</span><span class="sxs-lookup"><span data-stu-id="30654-168">**Metadata Address**: Displays the metadata address of the services.</span></span>

- <span data-ttu-id="30654-169">第二個區域是**其他資訊**。</span><span class="sxs-lookup"><span data-stu-id="30654-169">The second area is **Additional Information**.</span></span> <span data-ttu-id="30654-170">當您在 [**服務**] 區域中選取特定的服務行時，它會顯示服務狀態的詳細說明。</span><span class="sxs-lookup"><span data-stu-id="30654-170">It displays a detailed explanation of the service status when the specific service line is selected in the **Service** area.</span></span> <span data-ttu-id="30654-171">如果狀態為「錯誤」，您就可以在螢幕上檢視完整的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="30654-171">If the status is Error, you can view the full error message on the screen.</span></span>

## <a name="stopping-wcf-service-host"></a><span data-ttu-id="30654-172">停止 WCF 服務主機</span><span class="sxs-lookup"><span data-stu-id="30654-172">Stopping WCF Service Host</span></span>

<span data-ttu-id="30654-173">您可以透過下列四種方式關閉 WCF 服務主機：</span><span class="sxs-lookup"><span data-stu-id="30654-173">You can shut down WCF Service Host in the following four ways:</span></span>

- <span data-ttu-id="30654-174">停止 Visual Studio 中的「調試」會話。</span><span class="sxs-lookup"><span data-stu-id="30654-174">Stop the debugging session in Visual Studio.</span></span>

- <span data-ttu-id="30654-175">從 [ **WCF 服務主機**] 視窗的 [檔案 **] 功能表\*\*\*\*中選取 [** 結束]。</span><span class="sxs-lookup"><span data-stu-id="30654-175">Select **Exit** from the **File** menu in the **WCF Service Host** window.</span></span>

- <span data-ttu-id="30654-176">在系統通知區域中，從 WCF 服務主機匣圖示的內容**功能表中選取**[結束]。</span><span class="sxs-lookup"><span data-stu-id="30654-176">Select **Exit** from context menu of WCF Service Host tray icon in the system notification area.</span></span>

- <span data-ttu-id="30654-177">結束 WCF 測試用戶端（如果正在使用）。</span><span class="sxs-lookup"><span data-stu-id="30654-177">Exit WCF Test Client if it is being used.</span></span>

## <a name="using-service-host-without-administrator-privilege"></a><span data-ttu-id="30654-178">在沒有系統管理員權限的情況下使用服務主機</span><span class="sxs-lookup"><span data-stu-id="30654-178">Using Service Host without Administrator privilege</span></span>

<span data-ttu-id="30654-179">若要讓沒有系統管理員許可權的使用者開發 WCF 服務，在安裝 Visual Studio 期間，會為命名空間 "" 建立 ACL （存取控制清單） http://+:8731/Design_Time_Addresses 。</span><span class="sxs-lookup"><span data-stu-id="30654-179">To enable users without administrator privilege to develop WCF services, an ACL (Access Control List) is created for the namespace "http://+:8731/Design_Time_Addresses" during the installation of Visual Studio.</span></span> <span data-ttu-id="30654-180">ACL 會設定為 (UI)，其中包含已登入電腦的所有互動使用者。</span><span class="sxs-lookup"><span data-stu-id="30654-180">The ACL is set to (UI), which includes all interactive users logged on to the machine.</span></span> <span data-ttu-id="30654-181">系統管理員可以在此 ACL 中新增或移除使用者，或開啟其他埠。此 ACL 可讓使用者在不授與系統管理員許可權的情況下，使用 WCF 服務自動裝載（wcfSvcHost.exe）。</span><span class="sxs-lookup"><span data-stu-id="30654-181">Administrators can add or remove users from this ACL, or open additional ports.This ACL enables users to use the WCF Service Auto Host (wcfSvcHost.exe) without granting them administrator privileges.</span></span>

<span data-ttu-id="30654-182">您可以使用 Windows Vista 中的 [netsh.exe] 工具，以提高許可權的系統管理員帳戶修改存取權。</span><span class="sxs-lookup"><span data-stu-id="30654-182">You can modify access using the netsh.exe tool in Windows Vista under the elevated administrator account.</span></span> <span data-ttu-id="30654-183">下列是使用 netsh.exe 的範例。</span><span class="sxs-lookup"><span data-stu-id="30654-183">The following is an example of using netsh.exe.</span></span>

```console
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>
```

<span data-ttu-id="30654-184">如需 netsh.exe 的詳細資訊，請參閱「[如何使用 Netsh.exe 工具和命令列參數](https://docs.microsoft.com/previous-versions/tn-archive/bb490939(v=technet.10))」。</span><span class="sxs-lookup"><span data-stu-id="30654-184">For more information on netsh.exe, see "[How to Use the Netsh.exe Tool and Command-Line Switches](https://docs.microsoft.com/previous-versions/tn-archive/bb490939(v=technet.10))".</span></span>

## <a name="see-also"></a><span data-ttu-id="30654-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30654-185">See also</span></span>

- [<span data-ttu-id="30654-186">WCF 測試用戶端 (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="30654-186">WCF Test Client (WcfTestClient.exe)</span></span>](wcf-test-client-wcftestclient-exe.md)
