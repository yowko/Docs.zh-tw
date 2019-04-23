---
title: 組態編輯器工具 (SvcConfigEditor.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files, creating
- configuration files
- Configuration file
- configuration file schema
ms.assetid: 2db21a57-5f64-426f-89df-fb0dc2d2def5
ms.openlocfilehash: e4b54026c71e18e4011661c5cad2ca95dfcb733e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979936"
---
# <a name="configuration-editor-tool-svcconfigeditorexe"></a><span data-ttu-id="35089-102">組態編輯器工具 (SvcConfigEditor.exe)</span><span class="sxs-lookup"><span data-stu-id="35089-102">Configuration Editor Tool (SvcConfigEditor.exe)</span></span>
<span data-ttu-id="35089-103">Windows Communication Foundation (WCF) 服務組態編輯器 (SvcConfigEditor.exe) 可讓系統管理員和開發人員使用圖形化使用者介面建立並修改 WCF 服務的組態設定。</span><span class="sxs-lookup"><span data-stu-id="35089-103">The Windows Communication Foundation (WCF) Service Configuration Editor (SvcConfigEditor.exe) allows administrators and developers to create and modify configuration settings for WCF services using a graphical user interface.</span></span> <span data-ttu-id="35089-104">有了這項工具，您可以管理 WCF 繫結、行為、服務及診斷的設定，而不用直接編輯 XML 組態檔。</span><span class="sxs-lookup"><span data-stu-id="35089-104">With this tool, you can manage settings for WCF bindings, behaviors, services, and diagnostics without having to directly edit XML configuration files.</span></span>  
  
 <span data-ttu-id="35089-105">服務組態編輯器位於 C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin 資料夾。</span><span class="sxs-lookup"><span data-stu-id="35089-105">Service Configuration Editor can be found in the C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin folder.</span></span>  
  
## <a name="the-wcf-configuration-editor"></a><span data-ttu-id="35089-106">WCF 組態編輯器</span><span class="sxs-lookup"><span data-stu-id="35089-106">The WCF Configuration Editor</span></span>  
 <span data-ttu-id="35089-107">服務組態編輯器所提供的精靈會指引您完成設定 WCF 服務或用戶端的所有步驟。</span><span class="sxs-lookup"><span data-stu-id="35089-107">Service Configuration Editor comes with a wizard that guides you through all the steps in configuring a WCF service or client.</span></span> <span data-ttu-id="35089-108">強烈建議您使用精靈，而不直接使用編輯器。</span><span class="sxs-lookup"><span data-stu-id="35089-108">You are strongly advised to use the wizard instead of the editor directly.</span></span>  
  
 <span data-ttu-id="35089-109">如果您已經擁有一些符合標準 System.Configuration 結構描述的組態檔，就可以透過使用者介面來管理繫結、行為、服務和診斷的特定設定。</span><span class="sxs-lookup"><span data-stu-id="35089-109">If you already have some configuration files that comply with the standard System.Configuration schema, you can manage specific settings for bindings, behavior, services, and diagnostics with the user interface.</span></span> <span data-ttu-id="35089-110">服務組態編輯器可讓您管理現有 WCF 組態檔和可執行檔、COM+ 服務，以及 Web 託管服務的設定。</span><span class="sxs-lookup"><span data-stu-id="35089-110">The Service Configuration Editor enables you to manage the settings for existing WCF configuration files as well as executable files, COM+ services, and Web-hosted services.</span></span> <span data-ttu-id="35089-111">使用服務組態編輯器開啟 Web 託管服務時，服務本身的組態和繼承自高層節點的組態區段都會顯示。</span><span class="sxs-lookup"><span data-stu-id="35089-111">When opening a Web-hosted service with Service Configuration Editor, both the service’s own configuration and inherited configurations sections of upper level nodes are shown.</span></span>  
  
 <span data-ttu-id="35089-112">因為 WCF 組態設定位於組態檔的 `<system.serviceModel>` 區段中，所以編輯器只會在這個項目的內容進行作業，不會存取同一個檔案中的其他項目。</span><span class="sxs-lookup"><span data-stu-id="35089-112">Because WCF configuration settings are located in the `<system.serviceModel>` section of the configuration file, the editor operates exclusively on the content of this element and does not access other elements in the same file.</span></span> <span data-ttu-id="35089-113">您可以直接巡覽至現有的組態檔，或是選取包含服務、虛擬目錄或 COM+ 服務的組件。</span><span class="sxs-lookup"><span data-stu-id="35089-113">You can navigate to existing configuration files directly or you can select an assembly that contains a service, virtual directory, or COM+ service.</span></span> <span data-ttu-id="35089-114">編輯器會載入特定服務的組態檔，並允許使用者加入新項目，或編輯以巢狀方式置於組態檔 `<system.serviceModel>` 區段中的現有項目。</span><span class="sxs-lookup"><span data-stu-id="35089-114">The editor loads the configuration file for that particular service and allows the user to either add new elements or edit existing elements nested in the `<system.serviceModel>` section of the configuration file.</span></span>  
  
 <span data-ttu-id="35089-115">編輯器支援 IntelliSense 並增強結構描述相容性。</span><span class="sxs-lookup"><span data-stu-id="35089-115">The editor supports IntelliSense and enforces schema compliance.</span></span> <span data-ttu-id="35089-116">編輯器保證結果輸出符合組態檔的結構描述，且資料值有正確的語法，</span><span class="sxs-lookup"><span data-stu-id="35089-116">The resulting output is guaranteed to comply with the schema of the configuration file and to have syntactically correct data values.</span></span> <span data-ttu-id="35089-117">但是不保證組態檔的語意為有效。</span><span class="sxs-lookup"><span data-stu-id="35089-117">However, the editor does not guarantee that the configuration file is semantically valid.</span></span> <span data-ttu-id="35089-118">換句話說，編輯器不保證組態檔能夠與它所設定的服務搭配使用。</span><span class="sxs-lookup"><span data-stu-id="35089-118">In other words, the editor does not guarantee that the configuration file can work with the service it configures.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="35089-119">一旦您修改了項目，編輯器便無法清除組態檔中的組態項目。</span><span class="sxs-lookup"><span data-stu-id="35089-119">The editor cannot purge a configuration element from the configuration file once you have modified the element.</span></span> <span data-ttu-id="35089-120">例如，如果您使用編輯器將端點名稱設定非空白字串並加以儲存，則組態檔會有以下內容，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="35089-120">For example, if you use the editor to set the endpoint name to a non-empty string and save it, the configuration file has the following content, as shown in the following example.</span></span>  
>   
>  `<endpoint binding="basicHttpBinding" name="somename" />`  
>   
>  <span data-ttu-id="35089-121">如果您嘗試將名稱設為空白字串並儲存檔案藉以移除名稱，則組態檔仍會包含 `name` 屬性，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="35089-121">If you attempt to remove the name by setting it to an empty string and save the file, the configuration file still contains the `name` attribute, as shown in the following example.</span></span>  
>   
>  `<endpoint binding="basicHttpBinding" name="" />`  
>   
>  <span data-ttu-id="35089-122">若要清除該屬性，您必須使用其他文字編輯器手動編輯該項目。</span><span class="sxs-lookup"><span data-stu-id="35089-122">To purge the attribute, you must manually edit the element using another text editor.</span></span>  
>   
>  <span data-ttu-id="35089-123">當您使用 `issueToken` 端點行為的 `clientCredential` 項目時，應特別小心此問題。</span><span class="sxs-lookup"><span data-stu-id="35089-123">You should be especially careful with this issue when you use the `issueToken` element of the `clientCredential` Endpoint behavior.</span></span> <span data-ttu-id="35089-124">具體來說，其 `address` 子項目的 `localIssuer` 屬性不能是空白字串。</span><span class="sxs-lookup"><span data-stu-id="35089-124">Specifically, the `address` attribute of its `localIssuer` sub-element must not be an empty string.</span></span> <span data-ttu-id="35089-125">如果您已使用組態編輯器修改過 `address` 屬性，且要將該屬性完全移除，則應使用組態編輯器以外的工具來移除。</span><span class="sxs-lookup"><span data-stu-id="35089-125">If you have modified the `address` attribute using the Configuration Editor and want to remove it completely, you should do so using a tool other than the Editor.</span></span> <span data-ttu-id="35089-126">否則，屬性會包含空白字串，而且您的應用程式會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="35089-126">Otherwise, the attribute contains an empty string and your application throws an exception.</span></span>  
  
## <a name="using-the-configuration-editor"></a><span data-ttu-id="35089-127">使用組態編輯器</span><span class="sxs-lookup"><span data-stu-id="35089-127">Using the Configuration Editor</span></span>  
 <span data-ttu-id="35089-128">服務組態編輯器位於下列 Windows SDK 安裝位置：</span><span class="sxs-lookup"><span data-stu-id="35089-128">The Service Configuration Editor can be found at the following Windows SDK installation location:</span></span>  
  
 <span data-ttu-id="35089-129">C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin\SvcConfigEditor.exe</span><span class="sxs-lookup"><span data-stu-id="35089-129">C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin\SvcConfigEditor.exe</span></span>  
  
 <span data-ttu-id="35089-130">啟動 服務組態編輯器之後，您可以使用**檔案/開啟**功能表來瀏覽至服務或您想要管理組件。</span><span class="sxs-lookup"><span data-stu-id="35089-130">After you launch the Service Configuration Editor, you can use the **File/Open** menu to browse for the service or assembly you want to manage.</span></span> <span data-ttu-id="35089-131">您可以直接開啟組態檔，瀏覽 WCF/COM+ 服務，並開啟 Web 託管服務的組態檔。</span><span class="sxs-lookup"><span data-stu-id="35089-131">You can open configuration files directly, browse for WCF /COM+ services, and open configuration files for Web-hosted services.</span></span>  
  
 <span data-ttu-id="35089-132">服務組態編輯器的使用者介面共分為下列幾個區域：</span><span class="sxs-lookup"><span data-stu-id="35089-132">The Service Configuration Editor's user interface is divided into the following areas:</span></span>  
  
-   <span data-ttu-id="35089-133">樹狀檢閱窗格，在左側以樹狀顯示組態項目。</span><span class="sxs-lookup"><span data-stu-id="35089-133">Tree View Pane, which displays configuration elements in a tree structure on the left.</span></span> <span data-ttu-id="35089-134">您可以用滑鼠右鍵按一下樹狀目錄中的節點來執行作業。</span><span class="sxs-lookup"><span data-stu-id="35089-134">You can perform operations in the tree by right-clicking the nodes.</span></span>  
  
-   <span data-ttu-id="35089-135">工作窗格，可在視窗左下角顯示目前項目的一般工作。</span><span class="sxs-lookup"><span data-stu-id="35089-135">Task Pane, which displays common tasks for current elements on the lower-left of the window</span></span>  
  
-   <span data-ttu-id="35089-136">詳細資料窗格，可在右側顯示 [樹狀檢視] 中所選取組態節點的詳細設定。</span><span class="sxs-lookup"><span data-stu-id="35089-136">Detail Pane, which displays detailed settings of the configuration node selected in the Tree View on the right.</span></span>  
  
### <a name="opening-a-configuration-file"></a><span data-ttu-id="35089-137">開啟組態檔</span><span class="sxs-lookup"><span data-stu-id="35089-137">Opening a Configuration File</span></span>  
  
1. <span data-ttu-id="35089-138">若要瀏覽至您的 WCF 安裝位置，然後輸入使用命令視窗來啟動服務組態編輯器`SvcConfigEditor.exe`。</span><span class="sxs-lookup"><span data-stu-id="35089-138">Start Service Configuration Editor by using a command window to navigate to your WCF installation location, and then type `SvcConfigEditor.exe`.</span></span>  
  
2. <span data-ttu-id="35089-139">從**檔案**功能表上，選取**開啟**，按一下您想要管理的檔案類型。</span><span class="sxs-lookup"><span data-stu-id="35089-139">From the **File** menu, select **Open** and click the type of file you want to manage.</span></span>  
  
3. <span data-ttu-id="35089-140">在 **開啟**對話方塊方塊中，瀏覽至您想要管理，然後按兩下該特定檔案。</span><span class="sxs-lookup"><span data-stu-id="35089-140">In the **Open** dialog box, navigate to the specific file you want to manage and double-click it.</span></span>  
  
 <span data-ttu-id="35089-141">檢視器會自動遵循組態合併路徑並建立合併組態的檢視。</span><span class="sxs-lookup"><span data-stu-id="35089-141">The viewer automatically follows the configuration merge path and creates a view of the merged configuration.</span></span> <span data-ttu-id="35089-142">例如，非託管服務的實際組態是由 Machine.config 與 App.config 所共同組成。任何變更都會套用到 SvcConfigEditor 的使用中檔案。</span><span class="sxs-lookup"><span data-stu-id="35089-142">For example, the actual configuration of a non-hosted service is a combination of Machine.config and App.config. Any changes are applied to the active file in the SvcConfigEditor.</span></span> <span data-ttu-id="35089-143">如果您想要編輯組態合併路徑中的特定檔案，應該直接開啟它。</span><span class="sxs-lookup"><span data-stu-id="35089-143">If you want to edit a specific file in the configuration merge path, you should open it directly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="35089-144">組態編輯器會在目前已開啟的組態檔已在編輯器之外修改時，重新載入該組態檔。</span><span class="sxs-lookup"><span data-stu-id="35089-144">Configuration Editor reloads the currently opened configuration file when the latter has been modified outside the Editor.</span></span> <span data-ttu-id="35089-145">發生這種情況時，所有未永久儲存在編輯器內的變更都會遺失。</span><span class="sxs-lookup"><span data-stu-id="35089-145">When this happens, all the changes that are not durably saved inside the Editor are lost.</span></span> <span data-ttu-id="35089-146">如果持續發生重新載入，最有可能的原因是有服務不斷的存取組態檔，例如在背景中執行的防毒軟體。</span><span class="sxs-lookup"><span data-stu-id="35089-146">If reloading happens consistently, the most likely cause is a service that constantly accesses the configuration file, for example, an antivirus software running in the background.</span></span> <span data-ttu-id="35089-147">若要解決這個問題，請確定該檔案開啟時，組態編輯器是唯一能夠存取該檔案的處理序。</span><span class="sxs-lookup"><span data-stu-id="35089-147">To resolve this, ensure that Configuration Editor is the only process that can access the file when it is opened.</span></span>  
  
### <a name="services"></a><span data-ttu-id="35089-148">服務</span><span class="sxs-lookup"><span data-stu-id="35089-148">Services</span></span>  
 <span data-ttu-id="35089-149">**Services**節點會顯示所有目前指派的組態檔中的服務。</span><span class="sxs-lookup"><span data-stu-id="35089-149">The **Services** node displays all of the services currently assigned in the configuration file.</span></span> <span data-ttu-id="35089-150">在樹狀目錄中的每個子節點對應至的子元素 <`services`> 組態檔中的項目。</span><span class="sxs-lookup"><span data-stu-id="35089-150">Each sub-node in the tree corresponds to a sub-element of the <`services`> element in the configuration file.</span></span>  
  
 <span data-ttu-id="35089-151">當您按一下  **Services**節點，您可以檢視或執行中的服務上的工作摘要頁面**詳細資料**窗格。</span><span class="sxs-lookup"><span data-stu-id="35089-151">When you click the **Services** node, you can view or perform tasks on the service Summary Page in the **Detail** Pane.</span></span>  
  
#### <a name="creating-a-new-service-configuration"></a><span data-ttu-id="35089-152">建立新的服務組態</span><span class="sxs-lookup"><span data-stu-id="35089-152">Creating a new Service Configuration</span></span>  
 <span data-ttu-id="35089-153">您可以透過下列方式建立新的服務組態：</span><span class="sxs-lookup"><span data-stu-id="35089-153">You can create a new service configuration in the following ways:</span></span>  
  
-   <span data-ttu-id="35089-154">使用精靈：按一下連結**建立新的服務...**</span><span class="sxs-lookup"><span data-stu-id="35089-154">Using a Wizard: Click the link **Create a New Service…**</span></span> <span data-ttu-id="35089-155">在 [工作窗格] 或 [摘要] 頁面來啟動精靈。</span><span class="sxs-lookup"><span data-stu-id="35089-155">on the Task Pane or Summary Page to launch the wizard.</span></span> <span data-ttu-id="35089-156">您也可以在執行**檔案** 功能表->**加入新項目**。</span><span class="sxs-lookup"><span data-stu-id="35089-156">You can also do so in the **File** menu -> **Add New Item**.</span></span>  
  
-   <span data-ttu-id="35089-157">以手動方式建立：您可以按一下滑鼠右鍵**Services**節點，然後選擇**新的服務**。</span><span class="sxs-lookup"><span data-stu-id="35089-157">Create manually: You can right-click the **Services** node and choose **New Service**.</span></span>  
  
#### <a name="creating-a-new-service-endpoint-configuration"></a><span data-ttu-id="35089-158">建立新的服務端點組態</span><span class="sxs-lookup"><span data-stu-id="35089-158">Creating a new Service Endpoint Configuration</span></span>  
 <span data-ttu-id="35089-159">您可以透過下列方式建立新的服務端點組態：</span><span class="sxs-lookup"><span data-stu-id="35089-159">You can create a new service endpoint configuration in the following ways:</span></span>  
  
-   <span data-ttu-id="35089-160">使用精靈來建立： 按一下連結**建立新的服務端點...**</span><span class="sxs-lookup"><span data-stu-id="35089-160">Create using a Wizard: click the link **Create a New Service Endpoint…**</span></span> <span data-ttu-id="35089-161">在 [工作窗格] 或 [摘要] 頁面來啟動精靈。</span><span class="sxs-lookup"><span data-stu-id="35089-161">on the Task Pane or Summary Page to launch the wizard.</span></span> <span data-ttu-id="35089-162">您也可以在執行**檔案** 功能表->**加入新項目**。</span><span class="sxs-lookup"><span data-stu-id="35089-162">You can also do so in the **File** menu -> **Add New Item**.</span></span>  
  
-   <span data-ttu-id="35089-163">以手動方式建立：當您建立服務之後時，您可以以滑鼠右鍵按一下**端點**節點，然後選擇 「**新的服務端點**"。</span><span class="sxs-lookup"><span data-stu-id="35089-163">Create manually: Once you created a Service, you can right-click the **Endpoints** node and choose "**New Service Endpoint**".</span></span>  
  
#### <a name="editing-a-service-configuration"></a><span data-ttu-id="35089-164">編輯服務組態</span><span class="sxs-lookup"><span data-stu-id="35089-164">Editing a Service Configuration</span></span>  
  
1. <span data-ttu-id="35089-165">按一下 **服務**節點。</span><span class="sxs-lookup"><span data-stu-id="35089-165">Click a **Service** node.</span></span>  
  
2. <span data-ttu-id="35089-166">編輯屬性方格中的設定。</span><span class="sxs-lookup"><span data-stu-id="35089-166">Edit the settings in the property grids.</span></span>  
  
#### <a name="editing-a-service-endpoint-configuration"></a><span data-ttu-id="35089-167">編輯服務端點組態</span><span class="sxs-lookup"><span data-stu-id="35089-167">Editing a Service Endpoint Configuration</span></span>  
  
1. <span data-ttu-id="35089-168">按一下 **服務端點**節點。</span><span class="sxs-lookup"><span data-stu-id="35089-168">Click a **Service Endpoint** node.</span></span>  
  
2. <span data-ttu-id="35089-169">編輯屬性方格中的設定。</span><span class="sxs-lookup"><span data-stu-id="35089-169">Edit the settings in the property grids.</span></span>  
  
#### <a name="adding-a-base-address"></a><span data-ttu-id="35089-170">加入基底位址</span><span class="sxs-lookup"><span data-stu-id="35089-170">Adding a Base Address</span></span>  
  
1. <span data-ttu-id="35089-171">按一下 **主機**節點。</span><span class="sxs-lookup"><span data-stu-id="35089-171">Click the **Host** node.</span></span>  
  
2. <span data-ttu-id="35089-172">按一下 **新...**</span><span class="sxs-lookup"><span data-stu-id="35089-172">Click the **New…**</span></span> <span data-ttu-id="35089-173">按鈕**基底位址**一節。</span><span class="sxs-lookup"><span data-stu-id="35089-173">button in the **Base Addresses** section.</span></span>  
  
3. <span data-ttu-id="35089-174">在對話方塊中輸入基底位址 URI。</span><span class="sxs-lookup"><span data-stu-id="35089-174">Type in the base address URI in the dialog box.</span></span>  
  
4. <span data-ttu-id="35089-175">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="35089-175">Click **OK**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="35089-176">您無法編輯的值[ \<baseAddressPrefixFilters >](../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)內這項工具。</span><span class="sxs-lookup"><span data-stu-id="35089-176">You cannot edit the value of [\<baseAddressPrefixFilters>](../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md) inside this tool.</span></span> <span data-ttu-id="35089-177">若要新增或修改這個項目，您應使用文字編輯器或 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="35089-177">To add or modify this element, you should use a text editor or Visual Studio.</span></span>  
  
### <a name="client"></a><span data-ttu-id="35089-178">用戶端</span><span class="sxs-lookup"><span data-stu-id="35089-178">Client</span></span>  
 <span data-ttu-id="35089-179">**用戶端**節點會顯示所有的用戶端端點組態檔中。</span><span class="sxs-lookup"><span data-stu-id="35089-179">The **Client** node displays all of the client endpoints in the configuration file.</span></span> <span data-ttu-id="35089-180">在樹狀目錄中的每個子節點對應至的子元素 <`client`> 組態檔中的項目。</span><span class="sxs-lookup"><span data-stu-id="35089-180">Every sub-node in the tree corresponds to a sub-element of the <`client`> element in the configuration file.</span></span>  
  
 <span data-ttu-id="35089-181">當您按一下 **用戶端**節點，您可以檢視，或在用戶端上執行工作**摘要頁面**中**詳細資料窗格**。</span><span class="sxs-lookup"><span data-stu-id="35089-181">When you click the **Client** node, you can view or perform tasks on the client **Summary Page** in the **Detail Pane**.</span></span>  
  
#### <a name="creating-a-new-client-endpoint-configuration"></a><span data-ttu-id="35089-182">建立新的用戶端端點組態</span><span class="sxs-lookup"><span data-stu-id="35089-182">Creating a new Client Endpoint Configuration</span></span>  
 <span data-ttu-id="35089-183">您可以透過下列方式來建立新的用戶端端點組態：</span><span class="sxs-lookup"><span data-stu-id="35089-183">You can create a new client endpoint configuration in the following ways:</span></span>  
  
-   <span data-ttu-id="35089-184">建立精靈：按一下連結**建立新的用戶端...**</span><span class="sxs-lookup"><span data-stu-id="35089-184">Create by Wizard: Click the link **Create a New Client…**</span></span> <span data-ttu-id="35089-185">在上**工作窗格**在左下角的視窗，或**摘要 頁面**來啟動精靈。</span><span class="sxs-lookup"><span data-stu-id="35089-185">on the **Task Pane** on the lower-left of the window, or **Summary Page** to launch the wizard.</span></span> <span data-ttu-id="35089-186">您也可以在執行**檔案** 功能表->**加入新項目**。</span><span class="sxs-lookup"><span data-stu-id="35089-186">You can also do so in the **File** menu -> **Add New Item**.</span></span> <span data-ttu-id="35089-187">精靈會提示您指向服務組態的位置，從這裡產生用戶端組態。</span><span class="sxs-lookup"><span data-stu-id="35089-187">The wizard prompts you to point to the location of the service configuration, from which the client configuration is generated.</span></span> <span data-ttu-id="35089-188">然後您可以選擇要連接的服務端點。</span><span class="sxs-lookup"><span data-stu-id="35089-188">You can then choose the service endpoint to connect to.</span></span>  
  
-   <span data-ttu-id="35089-189">以手動方式建立：以滑鼠右鍵按一下**端點**下方的節點**用戶端**，然後選擇 **新增用戶端端點**。</span><span class="sxs-lookup"><span data-stu-id="35089-189">Create manually: Right-click the **Endpoints** node under **Client**, and choose **New Client Endpoint**.</span></span>  
  
#### <a name="editing-a-client-endpoint-configuration"></a><span data-ttu-id="35089-190">編輯用戶端端點組態</span><span class="sxs-lookup"><span data-stu-id="35089-190">Editing a Client Endpoint Configuration</span></span>  
  
1. <span data-ttu-id="35089-191">按一下 **用戶端端點**節點。</span><span class="sxs-lookup"><span data-stu-id="35089-191">Click a **Client Endpoint** node.</span></span>  
  
2. <span data-ttu-id="35089-192">編輯屬性方格中的設定。</span><span class="sxs-lookup"><span data-stu-id="35089-192">Edit the settings in the property grids.</span></span>  
  
### <a name="standard-endpoint"></a><span data-ttu-id="35089-193">標準端點</span><span class="sxs-lookup"><span data-stu-id="35089-193">Standard Endpoint</span></span>  
 <span data-ttu-id="35089-194">標準端點是專屬端點，可將位址、連絡人和繫結的一個或多個部分設為預設值。</span><span class="sxs-lookup"><span data-stu-id="35089-194">Standard endpoints are specialized endpoints that have one or more aspects of the address, contract and binding set to default values.</span></span>  
  
 <span data-ttu-id="35089-195">此類組態設定會儲存在**標準端點**節點。</span><span class="sxs-lookup"><span data-stu-id="35089-195">Such configuration settings are stored in the **Standard Endpoint** node.</span></span> <span data-ttu-id="35089-196">**標準端點**節點會顯示所有的標準端點設定的組態檔中。</span><span class="sxs-lookup"><span data-stu-id="35089-196">The **Standard Endpoint** node displays all of the standard endpoint settings in the configuration file.</span></span> <span data-ttu-id="35089-197">在樹狀目錄中的每個子節點對應至的子元素中`<standardEndpoints>`組態檔中的項目。</span><span class="sxs-lookup"><span data-stu-id="35089-197">Every sub-node in the tree corresponds to a sub-element in the `<standardEndpoints>` element in the configuration file.</span></span>  
  
 <span data-ttu-id="35089-198">當您按一下 **標準端點**節點，您可以檢視或執行工作的標準端點**摘要頁面**中**詳細資料窗格**。</span><span class="sxs-lookup"><span data-stu-id="35089-198">When you click the **Standard Endpoint** node, you can view or perform tasks on the standard endpoint **Summary Page** in the **Detail Pane**.</span></span>  
  
#### <a name="creating-a-new-standard-endpoint-configuration"></a><span data-ttu-id="35089-199">建立新的標準端點組態</span><span class="sxs-lookup"><span data-stu-id="35089-199">Creating a New Standard Endpoint Configuration</span></span>  
 <span data-ttu-id="35089-200">您可以透過下列方式建立新的標準端點組態：</span><span class="sxs-lookup"><span data-stu-id="35089-200">You can create a new standard endpoint configuration in the following ways:</span></span>  
  
-   <span data-ttu-id="35089-201">以滑鼠右鍵按一下**標準端點**節點，然後選取**新增標準端點組態...**</span><span class="sxs-lookup"><span data-stu-id="35089-201">Right-click the **Standard Endpoint** node and select **New Standard Endpoint Configuration…**</span></span> <span data-ttu-id="35089-202">在對話方塊中選取的繫結類型，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="35089-202">Select the binding type in the dialog box and click **OK**.</span></span>  
  
-   <span data-ttu-id="35089-203">選取 **標準端點**節點，然後按一下**新增標準端點組態...**</span><span class="sxs-lookup"><span data-stu-id="35089-203">Select the **Standard Endpoint** node and click **New Standard Endpoint Configuration…**</span></span> <span data-ttu-id="35089-204">在 **工作窗格**上視窗的左下方。</span><span class="sxs-lookup"><span data-stu-id="35089-204">in the **Task Pane** on the lower-left of the window.</span></span>  
  
 <span data-ttu-id="35089-205">**建立新的標準端點** 對話方塊中顯示，並列出所有已註冊的標準端點型別。</span><span class="sxs-lookup"><span data-stu-id="35089-205">The **Creating a New Standard Endpoint** dialog box displays and lists all registered standard endpoint types.</span></span>  
  
#### <a name="viewing-and-editing-a-standard-endpoint-configuration"></a><span data-ttu-id="35089-206">檢視及編輯標準端點組態</span><span class="sxs-lookup"><span data-stu-id="35089-206">Viewing and Editing a Standard Endpoint Configuration</span></span>  
 <span data-ttu-id="35089-207">您可以透過下列方式開啟標準端點組態進行檢視和編輯：</span><span class="sxs-lookup"><span data-stu-id="35089-207">You can open a standard endpoint configuration for viewing and editing in the following ways:</span></span>  
  
-   <span data-ttu-id="35089-208">按一下以展開**標準端點**節點並按一下各個端點子節點。</span><span class="sxs-lookup"><span data-stu-id="35089-208">Click to expand the **Standard Endpoint** node and click the respective endpoint sub-node.</span></span>  
  
-   <span data-ttu-id="35089-209">按一下 **標準端點**節點，按一下 詳細資料 窗格上的各個端點。</span><span class="sxs-lookup"><span data-stu-id="35089-209">Click the **Standard Endpoint** node and click the respective endpoint on the Detail pane.</span></span>  
  
 <span data-ttu-id="35089-210">端點的屬性會在右窗格中顯示供您編輯。</span><span class="sxs-lookup"><span data-stu-id="35089-210">Attributes for the endpoint are shown in the right pane for editing.</span></span>  
  
#### <a name="deleting-a-standard-endpoint-configuration"></a><span data-ttu-id="35089-211">刪除標準端點組態</span><span class="sxs-lookup"><span data-stu-id="35089-211">Deleting a Standard Endpoint Configuration</span></span>  
 <span data-ttu-id="35089-212">您可以透過下列方式刪除標準端點組態：</span><span class="sxs-lookup"><span data-stu-id="35089-212">You can delete a standard endpoint configuration in the following ways:</span></span>  
  
-   <span data-ttu-id="35089-213">按一下以展開**標準端點**節點並以滑鼠右鍵按一下各個端點子節點。</span><span class="sxs-lookup"><span data-stu-id="35089-213">Click to expand the **Standard Endpoint** node and right-click the respective endpoint sub-node.</span></span> <span data-ttu-id="35089-214">使用內容命令**刪除標準端點設定**刪除端點。</span><span class="sxs-lookup"><span data-stu-id="35089-214">Use the context command **Delete Standard Endpoint Configuration** to delete the endpoint.</span></span>  
  
-   <span data-ttu-id="35089-215">按一下 **標準端點**節點。</span><span class="sxs-lookup"><span data-stu-id="35089-215">Click the **Standard Endpoint** node.</span></span> <span data-ttu-id="35089-216">在 **任務**窗格中，按一下**刪除標準端點設定**。</span><span class="sxs-lookup"><span data-stu-id="35089-216">In the **Task** pane, click **Delete Standard Endpoint Configuration**.</span></span>  
  
 <span data-ttu-id="35089-217">如果標準端點正在使用中，當您嘗試刪除它時，會顯示一則警告訊息：**標準端點正在使用中。如果您現在要將它刪除，請確定刪除位於組態其他部分 (例如，服務端點或用戶端端點) 的所有參考。否則組態將無效，且下一次將無法開啟。是否確定要刪除標準端點嗎？ 」**</span><span class="sxs-lookup"><span data-stu-id="35089-217">If the standard endpoint is in used, a warning message is displayed when you attempt to delete it: **The standard endpoint is in use. If you delete it now, please be sure to delete all of its references in other parts of the configuration (for example, in the service endpoint or client endpoint). Otherwise, the configuration will be invalid and cannot be opened next time. Are you sure you want to delete the standard endpoint?"**</span></span>  
  
### <a name="binding"></a><span data-ttu-id="35089-218">繫結</span><span class="sxs-lookup"><span data-stu-id="35089-218">Binding</span></span>  
 <span data-ttu-id="35089-219">繫結組態是用來設定端點上的繫結。</span><span class="sxs-lookup"><span data-stu-id="35089-219">Binding configurations are used to configure bindings on endpoints.</span></span> <span data-ttu-id="35089-220">此類組態設定會儲存在**繫結**節點。</span><span class="sxs-lookup"><span data-stu-id="35089-220">Such configuration settings are stored in the **Binding** node.</span></span> <span data-ttu-id="35089-221">端點會依據名稱參考繫結組態，而多個端點可參考單一繫結組態。</span><span class="sxs-lookup"><span data-stu-id="35089-221">Endpoints reference binding configurations by name and multiple endpoints can reference a single binding configuration.</span></span>  
  
 <span data-ttu-id="35089-222">**繫結**節點會顯示所有繫結設定的組態檔中。</span><span class="sxs-lookup"><span data-stu-id="35089-222">The **Bindings** node displays all of the binding settings in the configuration file.</span></span> <span data-ttu-id="35089-223">在樹狀目錄中的每個子節點對應至的子元素中 <`bindings`> 組態檔中的項目。</span><span class="sxs-lookup"><span data-stu-id="35089-223">Every sub-node in the tree corresponds to a sub-element in the <`bindings`> element in the configuration file.</span></span>  
  
 <span data-ttu-id="35089-224">當您按一下 **繫結**節點，您可以檢視或執行工作之繫結上**摘要頁面**中**詳細資料窗格**。</span><span class="sxs-lookup"><span data-stu-id="35089-224">When you click the **Bindings** node, you can view or perform tasks on the binding **Summary Page** in the **Detail Pane**.</span></span>  
  
#### <a name="creating-a-new-binding-configuration"></a><span data-ttu-id="35089-225">建立新的繫結組態</span><span class="sxs-lookup"><span data-stu-id="35089-225">Creating a New Binding Configuration</span></span>  
 <span data-ttu-id="35089-226">您可以透過下列方式建立新的繫結組態。</span><span class="sxs-lookup"><span data-stu-id="35089-226">You can create a new binding configuration in the following ways.</span></span>  
  
-   <span data-ttu-id="35089-227">以滑鼠右鍵按一下**繫結**節點，然後選取**新增繫結組態**...</span><span class="sxs-lookup"><span data-stu-id="35089-227">Right-click the **Bindings** node and select **New Binding Configuration**…</span></span> <span data-ttu-id="35089-228">在對話方塊中選取的繫結類型，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="35089-228">Select the binding type in the dialog box and click **OK**.</span></span>  
  
-   <span data-ttu-id="35089-229">選取 **繫結**節點，然後按一下**新增繫結組態**...</span><span class="sxs-lookup"><span data-stu-id="35089-229">Select the **Bindings** node and click **New Binding Configuration**…</span></span> <span data-ttu-id="35089-230">在 **工作窗格**上視窗的左下方。</span><span class="sxs-lookup"><span data-stu-id="35089-230">in the **Task Pane** on the lower-left of the window.</span></span>  
  
-   <span data-ttu-id="35089-231">在服務或用戶端摘要頁面中，按一下**按一下即可建立**中**繫結組態**欄位，以建立對應的端點的繫結組態。</span><span class="sxs-lookup"><span data-stu-id="35089-231">In the service or client summary page, click **Click to Create** in the **Binding Configuration** field to create a binding configuration for the corresponding endpoint.</span></span>  
  
#### <a name="adding-binding-element-extensions-to-a-custom-binding"></a><span data-ttu-id="35089-232">將繫結項目擴充功能加入至自訂繫結中</span><span class="sxs-lookup"><span data-stu-id="35089-232">Adding Binding Element Extensions to a Custom Binding</span></span>  
  
1. <span data-ttu-id="35089-233">選取您要在其中新增擴充功能項目的繫結。</span><span class="sxs-lookup"><span data-stu-id="35089-233">Select the binding you want to add an extension element to.</span></span>  
  
2. <span data-ttu-id="35089-234">按一下 [加入] 。</span><span class="sxs-lookup"><span data-stu-id="35089-234">Click **Add**.</span></span>  
  
3. <span data-ttu-id="35089-235">從可用延伸清單中，選取您要加入的繫結項目延伸。</span><span class="sxs-lookup"><span data-stu-id="35089-235">From the list of available extensions, select the binding element extension you want to add.</span></span> <span data-ttu-id="35089-236">若要選取多個項目，請同時按下 CTRL 鍵。</span><span class="sxs-lookup"><span data-stu-id="35089-236">To select multiple items, press the CTRL key simultaneously.</span></span>  
  
4. <span data-ttu-id="35089-237">按一下 [加入] 。</span><span class="sxs-lookup"><span data-stu-id="35089-237">Click **Add**.</span></span>  
  
#### <a name="adjusting-the-extension-position-in-a-custom-binding"></a><span data-ttu-id="35089-238">調整自訂繫結中的擴充功能位置</span><span class="sxs-lookup"><span data-stu-id="35089-238">Adjusting the Extension Position in a Custom Binding</span></span>  
 <span data-ttu-id="35089-239">自訂繫結是一種會形成堆疊的繫結項目集合。</span><span class="sxs-lookup"><span data-stu-id="35089-239">A custom binding is a collection of binding elements that form a stack.</span></span> <span data-ttu-id="35089-240">堆疊上的每個繫結項目都有專屬的組態設定。</span><span class="sxs-lookup"><span data-stu-id="35089-240">Each binding element on the stack has its own configuration settings.</span></span> <span data-ttu-id="35089-241">自訂繫結中的繫結項目擴充功能順序代表每個擴充功能在堆疊中的位置。</span><span class="sxs-lookup"><span data-stu-id="35089-241">The order of the binding element extensions in a custom binding indicates their positions in the stack.</span></span> <span data-ttu-id="35089-242">在堆疊頂端的項目會優先套用。</span><span class="sxs-lookup"><span data-stu-id="35089-242">Elements at the top of the stack are applied first.</span></span> <span data-ttu-id="35089-243">若要變更順序：</span><span class="sxs-lookup"><span data-stu-id="35089-243">To change the ordering:</span></span>  
  
1. <span data-ttu-id="35089-244">選取自訂繫結節點。</span><span class="sxs-lookup"><span data-stu-id="35089-244">Select the custom binding node.</span></span>  
  
2. <span data-ttu-id="35089-245">選取有一個繫結延伸模組項目**繫結項目延伸位置**一節。</span><span class="sxs-lookup"><span data-stu-id="35089-245">Select one binding extension element in the **Binding Element Extension Position** section.</span></span>  
  
3. <span data-ttu-id="35089-246">使用**向上**或是**向下**清單來變更選取項目的位置左邊的按鈕。</span><span class="sxs-lookup"><span data-stu-id="35089-246">Use the **Up** or **Down** button on the left side of the list to change the position of the selected element.</span></span>  
  
#### <a name="editing-the-configuration-of-binding-element-extensions-in-a-custom-binding"></a><span data-ttu-id="35089-247">編輯自訂繫結中繫結項目擴充功能的組態</span><span class="sxs-lookup"><span data-stu-id="35089-247">Editing the Configuration of Binding Element Extensions in a Custom Binding</span></span>  
  
1. <span data-ttu-id="35089-248">選取樹狀目錄中的繫結程序節點。</span><span class="sxs-lookup"><span data-stu-id="35089-248">Select the binding node in the tree.</span></span>  
  
2. <span data-ttu-id="35089-249">選取包含您要編輯之項目的自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="35089-249">Select the custom binding that contains the element you want to edit.</span></span>  
  
3. <span data-ttu-id="35089-250">選取您要編輯的繫結項目延伸。</span><span class="sxs-lookup"><span data-stu-id="35089-250">Select the binding element extension you want to edit.</span></span> <span data-ttu-id="35089-251">項目設定會出現在右窗格中供您進行編輯。</span><span class="sxs-lookup"><span data-stu-id="35089-251">The settings of the element appear in the right pane, where they can be edited.</span></span>  
  
### <a name="diagnostics"></a><span data-ttu-id="35089-252">診斷</span><span class="sxs-lookup"><span data-stu-id="35089-252">Diagnostics</span></span>  
 <span data-ttu-id="35089-253">**診斷**節點會顯示所有的診斷設定組態檔中。</span><span class="sxs-lookup"><span data-stu-id="35089-253">The **Diagnostics** node displays all of the diagnostic settings in the configuration file.</span></span> <span data-ttu-id="35089-254">它可讓您開啟或關閉效能計數器、 啟用或停用 Windows Management Instrumentation (WMI)、 設定 WCF 追蹤，以及設定 WCF 訊息記錄。</span><span class="sxs-lookup"><span data-stu-id="35089-254">It enables you to turn performance counters on or off, enable or disable Windows Management Instrumentation (WMI), configure WCF tracing, and configure WCF message logging.</span></span> <span data-ttu-id="35089-255">中的設定**診斷**節點對應至 <`system.diagnostics`> 區段中，與`<diagnostics>`一節中`<system.serviceModel>`組態檔中。</span><span class="sxs-lookup"><span data-stu-id="35089-255">The settings in the **Diagnostics** node correspond to the <`system.diagnostics`> section, and `<diagnostics>` section in `<system.serviceModel>` in the configuration file.</span></span>  
  
 <span data-ttu-id="35089-256">當您按一下 **診斷**節點，您可以檢視或執行工作的診斷**摘要頁面**中**詳細資料窗格**。</span><span class="sxs-lookup"><span data-stu-id="35089-256">When you click the **Diagnostics** node, you can view or perform tasks on the diagnostics **Summary Page** in the **Detail Pane**.</span></span>  
  
#### <a name="configuring-performance-counters-and-wmi"></a><span data-ttu-id="35089-257">設定效能計數器與 WMI</span><span class="sxs-lookup"><span data-stu-id="35089-257">Configuring performance counters and WMI</span></span>  
  
1. <span data-ttu-id="35089-258">按一下 **診斷**節點。</span><span class="sxs-lookup"><span data-stu-id="35089-258">Click the **Diagnostics** node.</span></span>  
  
2. <span data-ttu-id="35089-259">按一下 **切換效能計數器**。</span><span class="sxs-lookup"><span data-stu-id="35089-259">Click **Toggle Performance Counters**.</span></span> <span data-ttu-id="35089-260">效能計數器有三種狀態：Off （預設）、 ServiceOnly 和 All。</span><span class="sxs-lookup"><span data-stu-id="35089-260">The performance counter has three states: Off (default), ServiceOnly, and All.</span></span> <span data-ttu-id="35089-261">按一下連結，即可切換設定這三種狀態。</span><span class="sxs-lookup"><span data-stu-id="35089-261">Clicking the link toggles the setting among these three states.</span></span>  
  
#### <a name="configuring-wmi-provider"></a><span data-ttu-id="35089-262">設定 WMI 提供者</span><span class="sxs-lookup"><span data-stu-id="35089-262">Configuring WMI Provider</span></span>  
  
1. <span data-ttu-id="35089-263">按一下 **診斷**節點。</span><span class="sxs-lookup"><span data-stu-id="35089-263">Click the **Diagnostics** node.</span></span>  
  
2. <span data-ttu-id="35089-264">若要啟用 WMI 提供者，請按一下**啟用 WMI 提供者**連結。</span><span class="sxs-lookup"><span data-stu-id="35089-264">To enable WMI provider, click the **Enable WMI Provider** link.</span></span>  
  
#### <a name="enabling-wcf-tracing"></a><span data-ttu-id="35089-265">啟用 WCF 追蹤</span><span class="sxs-lookup"><span data-stu-id="35089-265">Enabling WCF Tracing</span></span>  
 <span data-ttu-id="35089-266">您可以使用標準屬性來建立 WCF 追蹤檔，或是設定自訂追蹤檔。</span><span class="sxs-lookup"><span data-stu-id="35089-266">You can create a WCF trace file with standard properties or set up a custom trace file.</span></span>  
  
1. <span data-ttu-id="35089-267">按一下 **診斷**節點。</span><span class="sxs-lookup"><span data-stu-id="35089-267">Click the **Diagnostics** node.</span></span>  
  
2. <span data-ttu-id="35089-268">按一下 **啟用追蹤**。</span><span class="sxs-lookup"><span data-stu-id="35089-268">Click **Enable Tracing**.</span></span>  
  
3. <span data-ttu-id="35089-269">按一下 **追蹤層級**連結調整追蹤層級。</span><span class="sxs-lookup"><span data-stu-id="35089-269">Click the **Trace Level** link to adjust the trace level.</span></span> <span data-ttu-id="35089-270">有六個的追蹤層級：關閉、 嚴重、 錯誤、 警告、 資訊和詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="35089-270">There are six trace levels: Off, Critical, Error, Warning, Information, and Verbose.</span></span> <span data-ttu-id="35089-271">**活動追蹤**並**傳播活動**選項可讓您使用 WCF 活動追蹤功能。</span><span class="sxs-lookup"><span data-stu-id="35089-271">The **Activity Tracing** and **Propagate Activity** option enable you to use the WCF activity tracing feature.</span></span>  
  
4. <span data-ttu-id="35089-272">您可以按一下追蹤接聽項名稱，指定追蹤檔案與選項。</span><span class="sxs-lookup"><span data-stu-id="35089-272">Click the trace listener name to specify the trace file and options.</span></span>  
  
#### <a name="enabling-wcf-logging"></a><span data-ttu-id="35089-273">啟用 WCF 記錄</span><span class="sxs-lookup"><span data-stu-id="35089-273">Enabling WCF Logging</span></span>  
 <span data-ttu-id="35089-274">您可以使用標準屬性來建立 WCF 追蹤檔，或是設定自訂追蹤檔。</span><span class="sxs-lookup"><span data-stu-id="35089-274">You can create a WCF trace file with standard properties or set up a custom trace file.</span></span>  
  
1. <span data-ttu-id="35089-275">按一下 **診斷**節點。</span><span class="sxs-lookup"><span data-stu-id="35089-275">Click the **Diagnostics** node.</span></span>  
  
2. <span data-ttu-id="35089-276">按一下 **啟用訊息記錄**。</span><span class="sxs-lookup"><span data-stu-id="35089-276">Click **Enable Message Logging**.</span></span>  
  
3. <span data-ttu-id="35089-277">按一下 **記錄層級**連結調整記錄層級。</span><span class="sxs-lookup"><span data-stu-id="35089-277">Click the **Log Level** link to adjust the log level.</span></span> <span data-ttu-id="35089-278">有三個記錄層級：格式不正確，服務和傳輸。</span><span class="sxs-lookup"><span data-stu-id="35089-278">There are three log levels: Malformed, Service, and Transport.</span></span>  
  
4. <span data-ttu-id="35089-279">您可以按一下接聽項名稱，指定記錄檔案與選項。</span><span class="sxs-lookup"><span data-stu-id="35089-279">Click the listener name to specify the log file and options.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="35089-280">如果您想關閉您的應用程式時，自動清除，請啟用追蹤與訊息記錄**自動排清**選項。</span><span class="sxs-lookup"><span data-stu-id="35089-280">If you want the trace and message logs to be flushed automatically when your application is closed, enable the **Auto Flush** option.</span></span>  
  
 <span data-ttu-id="35089-281">**診斷\*\*\*\*摘要頁面**可讓您完成設定診斷方面最常見的工作。</span><span class="sxs-lookup"><span data-stu-id="35089-281">The **Diagnostics** **Summary Page** enables you to accomplish the most common tasks in configuring diagnostics.</span></span> <span data-ttu-id="35089-282">不過，如果您想要以手動方式編輯接聽程式] 和 [來源設定，您必須展開**診斷**中的節點，然後編輯設定**訊息記錄**，**接聽程式**和**來源**節點。</span><span class="sxs-lookup"><span data-stu-id="35089-282">However, if you want to manually edit the Listeners and Sources settings, you must expand the **Diagnostics** node and edit settings in **Message Logging**, **Listeners** and **Sources** node.</span></span>  
  
#### <a name="enabling-wcf-custom-tracing-or-message-logging"></a><span data-ttu-id="35089-283">啟用 WCF 自訂追蹤或訊息記錄</span><span class="sxs-lookup"><span data-stu-id="35089-283">Enabling WCF Custom Tracing or Message Logging</span></span>  
  
1. <span data-ttu-id="35089-284">按一下 [**診斷**] 節點，並將其展開。</span><span class="sxs-lookup"><span data-stu-id="35089-284">Click the **Diagnostics** node, and expand it.</span></span>  
  
2. <span data-ttu-id="35089-285">以滑鼠右鍵按一下**接聽程式**節點，然後選取**新的接聽程式**。</span><span class="sxs-lookup"><span data-stu-id="35089-285">Right-click the **Listeners** node and select **New Listener**.</span></span>  
  
3. <span data-ttu-id="35089-286">中的追蹤檔案名稱中的型別**InitData**欄位。</span><span class="sxs-lookup"><span data-stu-id="35089-286">Type in the trace file name in the **InitData** field.</span></span> <span data-ttu-id="35089-287">您可以按一下 [...]若要瀏覽至路徑的按鈕。</span><span class="sxs-lookup"><span data-stu-id="35089-287">You can click the "…" button to browse to a path.</span></span>  
  
4. <span data-ttu-id="35089-288">按一下  **TypeName**行顯示 ...按鈕。</span><span class="sxs-lookup"><span data-stu-id="35089-288">Clicking the **TypeName** line displays a "…" button.</span></span> <span data-ttu-id="35089-289">按一下此按鈕即可開啟**追蹤接聽項型別瀏覽器**，可用來尋找已安裝的預先設定的追蹤接聽項。</span><span class="sxs-lookup"><span data-stu-id="35089-289">Click this button to open the **Trace Listener Type Browser**, which you can use to find pre-configured trace listeners that are already installed.</span></span>  
  
5. <span data-ttu-id="35089-290">附註**來源**一節。</span><span class="sxs-lookup"><span data-stu-id="35089-290">Note the **Source** section.</span></span> <span data-ttu-id="35089-291">按一下 **新增**本節中使用下拉功能表中開啟一個對話方塊，其中會列出可用的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="35089-291">Click **Add** in this section to open a dialog box with a drop-down menu, which lists available tracing sources.</span></span> <span data-ttu-id="35089-292">選取追蹤來源，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="35089-292">Select a tracing source and click **OK**.</span></span>  
  
6. <span data-ttu-id="35089-293">若要編輯訊息記錄設定，請按一下**訊息記錄**節點。</span><span class="sxs-lookup"><span data-stu-id="35089-293">To edit Message Logging settings, click the **Message Logging** node.</span></span> <span data-ttu-id="35089-294">您可以編輯屬性方格中的設定。</span><span class="sxs-lookup"><span data-stu-id="35089-294">You can edit the settings in the property grid.</span></span>  
  
### <a name="advanced"></a><span data-ttu-id="35089-295">進階</span><span class="sxs-lookup"><span data-stu-id="35089-295">Advanced</span></span>  
  
#### <a name="behaviors"></a><span data-ttu-id="35089-296">「行為」</span><span class="sxs-lookup"><span data-stu-id="35089-296">Behaviors</span></span>  
 <span data-ttu-id="35089-297">**行為**節點會顯示目前的組態檔中所定義的行為。</span><span class="sxs-lookup"><span data-stu-id="35089-297">The **Behaviors** node displays the behaviors that are currently defined in the configuration file.</span></span>  
  
 <span data-ttu-id="35089-298">行為組態是用來設定端點與服務的行為。</span><span class="sxs-lookup"><span data-stu-id="35089-298">Behavior configurations are used to configure behaviors of endpoints and services.</span></span> <span data-ttu-id="35089-299">此類組態設定會儲存在**進階**下方的節點**服務行為**並**端點行為**。</span><span class="sxs-lookup"><span data-stu-id="35089-299">Such configuration settings are stored in the **Advanced** node under **Service Behaviors** and **Endpoint Behaviors**.</span></span> <span data-ttu-id="35089-300">服務會使用服務行為，而端點則會使用端點行為。</span><span class="sxs-lookup"><span data-stu-id="35089-300">Service behaviors are used by services; whereas endpoint behaviors by endpoints.</span></span>  
  
 <span data-ttu-id="35089-301">行為是一種會形成堆疊之延伸項目的集合。</span><span class="sxs-lookup"><span data-stu-id="35089-301">Behaviors are a collection of extension elements that for a stack.</span></span> <span data-ttu-id="35089-302">在堆疊頂端的項目會優先套用。</span><span class="sxs-lookup"><span data-stu-id="35089-302">The element at the top of the stack is applied first.</span></span> <span data-ttu-id="35089-303">每個延伸項目可以擁有專屬的組態。</span><span class="sxs-lookup"><span data-stu-id="35089-303">Each extension element can have its own configuration.</span></span>  
  
##### <a name="creating-a-new-behavior-configuration"></a><span data-ttu-id="35089-304">建立新的行為組態</span><span class="sxs-lookup"><span data-stu-id="35089-304">Creating a new Behavior Configuration</span></span>  
 <span data-ttu-id="35089-305">您可以透過下列兩種方式建立新的行為組態。</span><span class="sxs-lookup"><span data-stu-id="35089-305">You can create a new behavior configuration in two ways.</span></span>  
  
-   <span data-ttu-id="35089-306">以滑鼠右鍵按一下其中一個行為節點，然後選取 「**新增行為組態...**</span><span class="sxs-lookup"><span data-stu-id="35089-306">Right-click one of the behavior nodes and select "**New Behavior Configuration…**</span></span>  
  
-   <span data-ttu-id="35089-307">選取其中一個行為節點，然後按一下**新增行為組態**...</span><span class="sxs-lookup"><span data-stu-id="35089-307">Select one of the behavior nodes and click the **New Behavior Configuration**…</span></span> <span data-ttu-id="35089-308">在 **工作窗格**上視窗的左下方。</span><span class="sxs-lookup"><span data-stu-id="35089-308">in the **Task Pane** on the lower-left of the window.</span></span>  
  
##### <a name="adding-behavior-element-extensions-to-a-behavior"></a><span data-ttu-id="35089-309">將行為項目延伸加入至行為中</span><span class="sxs-lookup"><span data-stu-id="35089-309">Adding Behavior Element Extensions to a Behavior</span></span>  
  
1. <span data-ttu-id="35089-310">選取其中一個行為節點。</span><span class="sxs-lookup"><span data-stu-id="35089-310">Select one of the behavior nodes.</span></span>  
  
2. <span data-ttu-id="35089-311">選取您要編輯的行為。</span><span class="sxs-lookup"><span data-stu-id="35089-311">Select the behavior you want edit.</span></span>  
  
3. <span data-ttu-id="35089-312">按一下 [加入] 。</span><span class="sxs-lookup"><span data-stu-id="35089-312">Click **Add**.</span></span>  
  
4. <span data-ttu-id="35089-313">從可用擴充功能清單中，選取您要新增的行為項目擴充功能。</span><span class="sxs-lookup"><span data-stu-id="35089-313">From the list of available extensions, select the behavior element extension you want to add.</span></span>  
  
5. <span data-ttu-id="35089-314">按一下 [加入] 。</span><span class="sxs-lookup"><span data-stu-id="35089-314">Click **Add**.</span></span>  
  
##### <a name="adjusting-the-extension-position-in-a-behavior"></a><span data-ttu-id="35089-315">調整行為中的延伸位置</span><span class="sxs-lookup"><span data-stu-id="35089-315">Adjusting the Extension Position in a Behavior</span></span>  
 <span data-ttu-id="35089-316">行為是一種會形成堆疊之項目的集合。</span><span class="sxs-lookup"><span data-stu-id="35089-316">Behaviors are collections of elements that form a stack.</span></span> <span data-ttu-id="35089-317">堆疊上的每個項目都有專屬的組態。</span><span class="sxs-lookup"><span data-stu-id="35089-317">Each element on the stack has its own configuration.</span></span> <span data-ttu-id="35089-318">行為中的行為項目延伸順序代表每個延伸在堆疊中的位置。</span><span class="sxs-lookup"><span data-stu-id="35089-318">The order of the behavior element extensions in a behavior indicates their positions in the stack.</span></span> <span data-ttu-id="35089-319">在堆疊頂端的項目會優先套用。</span><span class="sxs-lookup"><span data-stu-id="35089-319">Elements at the top of the stack are applied first.</span></span> <span data-ttu-id="35089-320">若要變更順序：</span><span class="sxs-lookup"><span data-stu-id="35089-320">To change the ordering:</span></span>  
  
1. <span data-ttu-id="35089-321">選取其中一個行為節點。</span><span class="sxs-lookup"><span data-stu-id="35089-321">Select one of the behavior nodes.</span></span>  
  
2. <span data-ttu-id="35089-322">選取您要編輯的行為。</span><span class="sxs-lookup"><span data-stu-id="35089-322">Select the behavior you want edit.</span></span>  
  
3. <span data-ttu-id="35089-323">選取行為延伸項目中的**行為項目延伸位置**一節。</span><span class="sxs-lookup"><span data-stu-id="35089-323">Select a behavior extension element in the **Behavior Element Extension Position** section.</span></span>  
  
4. <span data-ttu-id="35089-324">使用**向上**或是**向下**清單來變更選取項目的位置左邊的按鈕。</span><span class="sxs-lookup"><span data-stu-id="35089-324">Use the **Up** or **Down** button on the left side of the list to change the position of the selected element.</span></span>  
  
##### <a name="editing-the-configuration-of-behavior-element-extensions"></a><span data-ttu-id="35089-325">編輯行為項目擴充功能的組態</span><span class="sxs-lookup"><span data-stu-id="35089-325">Editing the Configuration of Behavior Element Extensions</span></span>  
  
1. <span data-ttu-id="35089-326">選取樹狀目錄的其中一個行為節點。</span><span class="sxs-lookup"><span data-stu-id="35089-326">Select one of the behavior nodes in the tree.</span></span>  
  
2. <span data-ttu-id="35089-327">選取包含您要編輯之項目的行為。</span><span class="sxs-lookup"><span data-stu-id="35089-327">Select the behavior that contains the element you want to edit.</span></span>  
  
3. <span data-ttu-id="35089-328">選取您要編輯的行為項目擴充功能。</span><span class="sxs-lookup"><span data-stu-id="35089-328">Select the behavior element extension you want to edit.</span></span> <span data-ttu-id="35089-329">項目設定會出現在右窗格中供您進行編輯。</span><span class="sxs-lookup"><span data-stu-id="35089-329">The settings of the element appear in the right pane where they can be edited.</span></span>  
  
#### <a name="protocolmapping"></a><span data-ttu-id="35089-330">ProtocolMapping</span><span class="sxs-lookup"><span data-stu-id="35089-330">ProtocolMapping</span></span>  
 <span data-ttu-id="35089-331">這個區段可讓您透過通訊協定位址配置與可能的繫結之間已定義的對應，針對不同的通訊協定設定預設的繫結型別，例如 http、tcp、MSMQ 或 net.pipe。</span><span class="sxs-lookup"><span data-stu-id="35089-331">This section allows you to set default binding types for different protocols such as http, tcp, MSMQ or net.pipe through defined mapping between protocol address schemes and the possible bindings.</span></span> <span data-ttu-id="35089-332">您也可以加入其他通訊協定的新對應。</span><span class="sxs-lookup"><span data-stu-id="35089-332">You can also add new mappings to other protocols.</span></span>  
  
#### <a name="extensions"></a><span data-ttu-id="35089-333">延伸模組</span><span class="sxs-lookup"><span data-stu-id="35089-333">Extensions</span></span>  
 <span data-ttu-id="35089-334">可以註冊新的繫結延伸、 繫結項目延伸、 標準端點延伸和行為延伸模組，以便在 WCF 組態中使用。</span><span class="sxs-lookup"><span data-stu-id="35089-334">New binding extensions, binding element extensions, standard endpoint extensions and behavior extensions can be registered for use in WCF configuration.</span></span> <span data-ttu-id="35089-335">擴充功能是名稱/型別的配對。</span><span class="sxs-lookup"><span data-stu-id="35089-335">Extensions are name/type pairs.</span></span> <span data-ttu-id="35089-336">名稱可定義組態中延伸的名稱，而型別則可實作延伸。</span><span class="sxs-lookup"><span data-stu-id="35089-336">The name defines the name of the extension in configuration, whereas the type implements the extension.</span></span> <span data-ttu-id="35089-337">延伸有四種型別：</span><span class="sxs-lookup"><span data-stu-id="35089-337">There are four types of extensions:</span></span>  
  
-   <span data-ttu-id="35089-338">繫結延伸可定義整個繫結型別。</span><span class="sxs-lookup"><span data-stu-id="35089-338">Binding extensions define an entire binding type.</span></span> <span data-ttu-id="35089-339">範例：`basicHttpBinding`。</span><span class="sxs-lookup"><span data-stu-id="35089-339">Example: `basicHttpBinding`.</span></span>  
  
-   <span data-ttu-id="35089-340">繫結項目延伸可定義繫結項目。</span><span class="sxs-lookup"><span data-stu-id="35089-340">Binding element extensions define an element of a binding.</span></span> <span data-ttu-id="35089-341">範例：`textMessageEncoding`。</span><span class="sxs-lookup"><span data-stu-id="35089-341">Example: `textMessageEncoding`.</span></span>  
  
-   <span data-ttu-id="35089-342">標準端點延伸可定義整個標準端點。</span><span class="sxs-lookup"><span data-stu-id="35089-342">Standard endpoint extensions define an entire standard endpoint.</span></span> <span data-ttu-id="35089-343">範例：`discoveryEndpoint`。</span><span class="sxs-lookup"><span data-stu-id="35089-343">Example: `discoveryEndpoint`.</span></span>  
  
-   <span data-ttu-id="35089-344">行為項目延伸可定義行為項目。</span><span class="sxs-lookup"><span data-stu-id="35089-344">Behavior element extensions define an element of a behavior.</span></span> <span data-ttu-id="35089-345">範例：`clientVia`。</span><span class="sxs-lookup"><span data-stu-id="35089-345">Example: `clientVia`.</span></span>  
  
 <span data-ttu-id="35089-346">已經於組態中註冊的擴充功能可比照同類型的任何其他 WCF 元件使用。</span><span class="sxs-lookup"><span data-stu-id="35089-346">Extensions that have been registered in configuration can be used like any other WCF component of the same type.</span></span>  
  
##### <a name="adding-a-new-extension"></a><span data-ttu-id="35089-347">加入新的延伸</span><span class="sxs-lookup"><span data-stu-id="35089-347">Adding a new extension</span></span>  
 <span data-ttu-id="35089-348">在進階節點中選取其中一個延伸節點：</span><span class="sxs-lookup"><span data-stu-id="35089-348">Select one of the extension nodes in the advanced nodes:</span></span>  
  
1. <span data-ttu-id="35089-349">按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="35089-349">Click **New**.</span></span>  
  
2. <span data-ttu-id="35089-350">輸入名稱和型別。</span><span class="sxs-lookup"><span data-stu-id="35089-350">Enter a name and type.</span></span>  
  
3. <span data-ttu-id="35089-351">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="35089-351">Click **OK**.</span></span>  
  
4. <span data-ttu-id="35089-352">擴充功能現在會出現在編輯器的適當位置中。</span><span class="sxs-lookup"><span data-stu-id="35089-352">The extension now appears in the appropriate place in the Editor.</span></span> <span data-ttu-id="35089-353">例如，如果您新增行為項目延伸，則這個功能會出現在可用延伸清單中。</span><span class="sxs-lookup"><span data-stu-id="35089-353">For example, if you add a behavior element extension, it appears in the list of available extensions.</span></span>  
  
#### <a name="hosting-environment"></a><span data-ttu-id="35089-354">裝載環境</span><span class="sxs-lookup"><span data-stu-id="35089-354">Hosting Environment</span></span>  
 <span data-ttu-id="35089-355">這個區段可讓您定義服務裝載環境的執行個體化設定。</span><span class="sxs-lookup"><span data-stu-id="35089-355">This section allows you to define instantiation settings for the service hosting environment.</span></span>  
  
### <a name="creating-a-configuration-file-using-the-wizard"></a><span data-ttu-id="35089-356">使用精靈來建立組態檔</span><span class="sxs-lookup"><span data-stu-id="35089-356">Creating a Configuration File Using the Wizard</span></span>  
 <span data-ttu-id="35089-357">建立新組態檔的一個方法是使用 [新增服務項目精靈]。</span><span class="sxs-lookup"><span data-stu-id="35089-357">One way to create a new configuration file is to use the New Service Element Wizard.</span></span> <span data-ttu-id="35089-358">此精靈會尋找已安裝的服務類型和其他項目與 WCF 相容的電腦上，包括 COM + 與 Web 裝載虛擬目錄，並載入以簡化組態的建立。</span><span class="sxs-lookup"><span data-stu-id="35089-358">The wizard finds the installed service types and other elements compatible with WCF on the computer, including COM+ and Web-hosted virtual directories, and loads them to make creating the configuration much more streamlined.</span></span>  
  
#### <a name="creating-a-configuration-file"></a><span data-ttu-id="35089-359">建立組態檔</span><span class="sxs-lookup"><span data-stu-id="35089-359">Creating a Configuration File</span></span>  
  
1. <span data-ttu-id="35089-360">若要瀏覽至您的 WCF 安裝位置，然後輸入使用命令視窗來啟動服務組態編輯器`SvcConfigEditor.exe`。</span><span class="sxs-lookup"><span data-stu-id="35089-360">Start Service Configuration Editor by using a command window to navigate to your WCF installation location, and then type `SvcConfigEditor.exe`.</span></span>  
  
2. <span data-ttu-id="35089-361">從**檔案**功能表上，選取**開放**然後按一下**可執行檔**， **COM + 服務**，或**WebHosted 服務**，這取決於您想要建立的組態檔的類型。</span><span class="sxs-lookup"><span data-stu-id="35089-361">From the **File** menu, select **Open** and click **Executable**, **COM+ Service**, or **WebHosted Service**, depending on the type of configuration file you want to create.</span></span>  
  
3. <span data-ttu-id="35089-362">在 **開啟**對話方塊方塊中，瀏覽至您想要建立的組態檔，然後按兩下該特定檔案。</span><span class="sxs-lookup"><span data-stu-id="35089-362">In the **Open** dialog box, navigate to the specific file you want to create a configuration file for and double-click it.</span></span>  
  
4. <span data-ttu-id="35089-363">在 **檔案**功能表上，指向**加入新項目**然後按一下**服務**。</span><span class="sxs-lookup"><span data-stu-id="35089-363">In the **File** menu, point to **Add New Item** and click **Service**.</span></span> <span data-ttu-id="35089-364">[新增服務項目精靈] 隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="35089-364">The New Service Element Wizard opens.</span></span>  
  
5. <span data-ttu-id="35089-365">依照精靈中的步驟執行，以建立新服務。</span><span class="sxs-lookup"><span data-stu-id="35089-365">Follow the steps in the wizard to create the new service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="35089-366">如果您要從精靈所產生的組態檔中使用 NetPeerTcpBinding，您必須手動新增繫結組態項目，並將其 `mode` 項目的 `security` 屬性修改為 [無]。</span><span class="sxs-lookup"><span data-stu-id="35089-366">If you want to use the NetPeerTcpBinding from the configuration file generated by the Wizard, you have to manually add a binding configuration element and modify the `mode` attribute of its `security` element to "None".</span></span>  
  
## <a name="configuring-com"></a><span data-ttu-id="35089-367">設定 COM+</span><span class="sxs-lookup"><span data-stu-id="35089-367">Configuring COM+</span></span>  
 <span data-ttu-id="35089-368">服務組態編輯器可讓您針對現有的 COM+ 應用程式建立新的組態檔，或是編輯現有的 COM+ 組態。</span><span class="sxs-lookup"><span data-stu-id="35089-368">The Service Configuration Editor enables you to create a new configuration file for an existing COM+ application, or edit an existing COM+ configuration.</span></span> <span data-ttu-id="35089-369">**COM 合約**節點時，才看 <`comContract`> 組態檔中的區段存在。</span><span class="sxs-lookup"><span data-stu-id="35089-369">The **COM Contract** node is only visible when the <`comContract`> section exists in the configuration file.</span></span>  
  
### <a name="creating-a-new-com-configuration"></a><span data-ttu-id="35089-370">建立新 COM+ 組態</span><span class="sxs-lookup"><span data-stu-id="35089-370">Creating a New COM+ Configuration</span></span>  
 <span data-ttu-id="35089-371">在建立新的 COM+ 組態之前，請先確定您的 COM+ 應用程式已安裝在 [元件服務] 中，並在 [全域組件快取] \(GAC) 中註冊。</span><span class="sxs-lookup"><span data-stu-id="35089-371">Before creating a new COM+ configuration, make sure that your COM+ application is installed in Component Services, and registered in the Global Assembly Cache (GAC).</span></span>  
  
1. <span data-ttu-id="35089-372">選取 [**檔案**] 功能表->**整合** -> **COM + 應用程式。**</span><span class="sxs-lookup"><span data-stu-id="35089-372">Select **File** menu -> **Integrate** -> **COM+ Application.**</span></span> <span data-ttu-id="35089-373">這個作業會關閉目前開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="35089-373">This operation closes the current opened file.</span></span> <span data-ttu-id="35089-374">如果目前檔案中包含未儲存的資料，就會出現 [儲存] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="35089-374">If there is unsaved data in the current file, a Save dialog appears.</span></span> <span data-ttu-id="35089-375">**COM + 整合精靈**隨即啟動。</span><span class="sxs-lookup"><span data-stu-id="35089-375">The **COM+ Integration Wizard** is then launched.</span></span>  
  
2. <span data-ttu-id="35089-376">從第一頁的樹狀目錄中選取 COM+ 應用程式。</span><span class="sxs-lookup"><span data-stu-id="35089-376">In the first page, select the COM+ application from the tree.</span></span> <span data-ttu-id="35089-377">如果您在樹狀目錄中找不到您的 COM+ 應用程式，請確認該應用程式是否已經安裝在 [元件服務] 中，並且在 [全域組件快取] \(GAC) 中註冊。</span><span class="sxs-lookup"><span data-stu-id="35089-377">If you cannot find your COM+ application in the tree, verify that it is installed in the Component Services and registered in the Global Assembly Cache (GAC).</span></span>  
  
3. <span data-ttu-id="35089-378">在下一頁，選取您要公開為 WCF 服務的方法。</span><span class="sxs-lookup"><span data-stu-id="35089-378">In the next page, select which method(s) you want to expose as WCF services.</span></span> <span data-ttu-id="35089-379">預設會顯示並選取 COM+ 應用程式支援的所有方法。</span><span class="sxs-lookup"><span data-stu-id="35089-379">All the supported methods in the COM+ application are displayed and selected by default.</span></span>  
  
4. <span data-ttu-id="35089-380">選擇裝載的方法。</span><span class="sxs-lookup"><span data-stu-id="35089-380">Choose a hosting method.</span></span>  
  
5. <span data-ttu-id="35089-381">依據精靈中的指示進行其他設定。</span><span class="sxs-lookup"><span data-stu-id="35089-381">Configure other settings according to the guides in the wizard.</span></span>  
  
6. <span data-ttu-id="35089-382">服務組態編輯器會在背景中使用 ComSvcConfig.exe 來產生組態檔。</span><span class="sxs-lookup"><span data-stu-id="35089-382">Service Configuration Editor utilizes ComSvcConfig.exe in the background to generate configuration file.</span></span> <span data-ttu-id="35089-383">完成後，您就可以檢視摘要並結束精靈。</span><span class="sxs-lookup"><span data-stu-id="35089-383">After this is completed, you can view a summary and exit the wizard.</span></span> <span data-ttu-id="35089-384">產生的組態檔隨即開啟，方便您直接進行編輯。</span><span class="sxs-lookup"><span data-stu-id="35089-384">The generated configuration file is opened so that you can edit it directly.</span></span>  
  
### <a name="editing-an-existing-com-configuration"></a><span data-ttu-id="35089-385">編輯現有的 COM+ 組態</span><span class="sxs-lookup"><span data-stu-id="35089-385">Editing an Existing COM+ Configuration</span></span>  
  
1. <span data-ttu-id="35089-386">選取 [**檔案**] 功能表->**開放** -> **COM + 服務**...</span><span class="sxs-lookup"><span data-stu-id="35089-386">Select **File** menu -> **Open** -> **COM+ Service**…</span></span>  
  
2. <span data-ttu-id="35089-387">從清單中選取您要編輯的 COM+ 服務。</span><span class="sxs-lookup"><span data-stu-id="35089-387">Select the COM+ Service you want to edit from the list.</span></span>  
  
3. <span data-ttu-id="35089-388">編輯中的組態設定**COM 合約**節點。</span><span class="sxs-lookup"><span data-stu-id="35089-388">Edit configuration settings in the **COM Contracts** node.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="35089-389">您也可以直接開啟並編輯包含 COM 合約的組態檔。</span><span class="sxs-lookup"><span data-stu-id="35089-389">You can also directly open and edit a configuration file that contains COM contracts.</span></span>  
  
## <a name="security"></a><span data-ttu-id="35089-390">安全性</span><span class="sxs-lookup"><span data-stu-id="35089-390">Security</span></span>  
 <span data-ttu-id="35089-391">不保證組態編輯器產生的服務組態檔是安全的。</span><span class="sxs-lookup"><span data-stu-id="35089-391">A service configuration file generated by the Configuration Editor is not guaranteed to be secure.</span></span> <span data-ttu-id="35089-392">請參閱[安全性](../../../docs/framework/wcf/feature-details/security.md)文件，了解如何保護您的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="35089-392">Please refer to the [Security](../../../docs/framework/wcf/feature-details/security.md) documentation to find out how to secure your WCF services.</span></span>  
  
 <span data-ttu-id="35089-393">此外，組態編輯器只能用於讀取和寫入有效的 WCF 組態項目。</span><span class="sxs-lookup"><span data-stu-id="35089-393">In addition, the Configuration Editor can only be used to read and write valid WCF configuration elements.</span></span> <span data-ttu-id="35089-394">該工具會忽略符合結構描述、使用者定義的項目。</span><span class="sxs-lookup"><span data-stu-id="35089-394">The tool ignores schema-compliant, user-defined elements.</span></span> <span data-ttu-id="35089-395">它也不會嘗試將這些項目從組態檔中移除，或判斷其對已知 WCF 項目的影響。</span><span class="sxs-lookup"><span data-stu-id="35089-395">It also does not attempt remove these elements from the configuration file or determine their effects on the known WCF elements.</span></span> <span data-ttu-id="35089-396">使用者應負責判斷這些項目是否會對應用程式或系統造成威脅。</span><span class="sxs-lookup"><span data-stu-id="35089-396">It is the user’s responsibility to determine whether these elements pose a threat to the application or the system.</span></span>
