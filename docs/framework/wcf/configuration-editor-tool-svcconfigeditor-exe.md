---
title: 組態編輯器工具 (SvcConfigEditor.exe)
description: 瞭解如何使用 WCF 服務設定編輯器來管理 WCF 系結、行為、服務及診斷的設定。
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files, creating
- configuration files
- Configuration file
- configuration file schema
ms.assetid: 2db21a57-5f64-426f-89df-fb0dc2d2def5
ms.openlocfilehash: 258437ff616b969d40feabbfff364ad2cc6b25bc
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247645"
---
# <a name="configuration-editor-tool-svcconfigeditorexe"></a><span data-ttu-id="fc54b-103">組態編輯器工具 (SvcConfigEditor.exe)</span><span class="sxs-lookup"><span data-stu-id="fc54b-103">Configuration Editor Tool (SvcConfigEditor.exe)</span></span>

<span data-ttu-id="fc54b-104">Windows Communication Foundation (WCF) 服務組態編輯器 (SvcConfigEditor.exe) 可讓系統管理員和開發人員使用圖形化使用者介面建立並修改 WCF 服務的組態設定。</span><span class="sxs-lookup"><span data-stu-id="fc54b-104">The Windows Communication Foundation (WCF) Service Configuration Editor (SvcConfigEditor.exe) allows administrators and developers to create and modify configuration settings for WCF services using a graphical user interface.</span></span> <span data-ttu-id="fc54b-105">有了這項工具，您可以管理 WCF 繫結、行為、服務及診斷的設定，而不用直接編輯 XML 組態檔。</span><span class="sxs-lookup"><span data-stu-id="fc54b-105">With this tool, you can manage settings for WCF bindings, behaviors, services, and diagnostics without having to directly edit XML configuration files.</span></span>

<span data-ttu-id="fc54b-106">服務組態編輯器位於 C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin 資料夾。</span><span class="sxs-lookup"><span data-stu-id="fc54b-106">Service Configuration Editor can be found in the C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin folder.</span></span>

## <a name="the-wcf-configuration-editor"></a><span data-ttu-id="fc54b-107">WCF 組態編輯器</span><span class="sxs-lookup"><span data-stu-id="fc54b-107">The WCF Configuration Editor</span></span>

<span data-ttu-id="fc54b-108">服務組態編輯器所提供的精靈會指引您完成設定 WCF 服務或用戶端的所有步驟。</span><span class="sxs-lookup"><span data-stu-id="fc54b-108">Service Configuration Editor comes with a wizard that guides you through all the steps in configuring a WCF service or client.</span></span> <span data-ttu-id="fc54b-109">強烈建議您使用精靈，而不直接使用編輯器。</span><span class="sxs-lookup"><span data-stu-id="fc54b-109">You are strongly advised to use the wizard instead of the editor directly.</span></span>

<span data-ttu-id="fc54b-110">如果您已經擁有一些符合標準 System.Configuration 結構描述的組態檔，就可以透過使用者介面來管理繫結、行為、服務和診斷的特定設定。</span><span class="sxs-lookup"><span data-stu-id="fc54b-110">If you already have some configuration files that comply with the standard System.Configuration schema, you can manage specific settings for bindings, behavior, services, and diagnostics with the user interface.</span></span> <span data-ttu-id="fc54b-111">服務組態編輯器可讓您管理現有 WCF 組態檔和可執行檔、COM+ 服務，以及 Web 託管服務的設定。</span><span class="sxs-lookup"><span data-stu-id="fc54b-111">The Service Configuration Editor enables you to manage the settings for existing WCF configuration files as well as executable files, COM+ services, and Web-hosted services.</span></span> <span data-ttu-id="fc54b-112">使用服務組態編輯器開啟 Web 託管服務時，服務本身的組態和繼承自高層節點的組態區段都會顯示。</span><span class="sxs-lookup"><span data-stu-id="fc54b-112">When opening a Web-hosted service with Service Configuration Editor, both the service’s own configuration and inherited configurations sections of upper level nodes are shown.</span></span>

<span data-ttu-id="fc54b-113">因為 WCF 組態設定位於組態檔的 `<system.serviceModel>` 區段中，所以編輯器只會在這個項目的內容進行作業，不會存取同一個檔案中的其他項目。</span><span class="sxs-lookup"><span data-stu-id="fc54b-113">Because WCF configuration settings are located in the `<system.serviceModel>` section of the configuration file, the editor operates exclusively on the content of this element and does not access other elements in the same file.</span></span> <span data-ttu-id="fc54b-114">您可以直接巡覽至現有的組態檔，或是選取包含服務、虛擬目錄或 COM+ 服務的組件。</span><span class="sxs-lookup"><span data-stu-id="fc54b-114">You can navigate to existing configuration files directly or you can select an assembly that contains a service, virtual directory, or COM+ service.</span></span> <span data-ttu-id="fc54b-115">編輯器會載入特定服務的組態檔，並允許使用者加入新項目，或編輯以巢狀方式置於組態檔 `<system.serviceModel>` 區段中的現有項目。</span><span class="sxs-lookup"><span data-stu-id="fc54b-115">The editor loads the configuration file for that particular service and allows the user to either add new elements or edit existing elements nested in the `<system.serviceModel>` section of the configuration file.</span></span>

<span data-ttu-id="fc54b-116">編輯器支援 IntelliSense 並增強結構描述相容性。</span><span class="sxs-lookup"><span data-stu-id="fc54b-116">The editor supports IntelliSense and enforces schema compliance.</span></span> <span data-ttu-id="fc54b-117">編輯器保證結果輸出符合組態檔的結構描述，且資料值有正確的語法，</span><span class="sxs-lookup"><span data-stu-id="fc54b-117">The resulting output is guaranteed to comply with the schema of the configuration file and to have syntactically correct data values.</span></span> <span data-ttu-id="fc54b-118">但是不保證組態檔的語意為有效。</span><span class="sxs-lookup"><span data-stu-id="fc54b-118">However, the editor does not guarantee that the configuration file is semantically valid.</span></span> <span data-ttu-id="fc54b-119">換句話說，編輯器不保證組態檔能夠與它所設定的服務搭配使用。</span><span class="sxs-lookup"><span data-stu-id="fc54b-119">In other words, the editor does not guarantee that the configuration file can work with the service it configures.</span></span>

> [!CAUTION]
> <span data-ttu-id="fc54b-120">一旦您修改了項目，編輯器便無法清除組態檔中的組態項目。</span><span class="sxs-lookup"><span data-stu-id="fc54b-120">The editor cannot purge a configuration element from the configuration file once you have modified the element.</span></span> <span data-ttu-id="fc54b-121">例如，如果您使用編輯器將端點名稱設定非空白字串並加以儲存，則組態檔會有以下內容，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="fc54b-121">For example, if you use the editor to set the endpoint name to a non-empty string and save it, the configuration file has the following content, as shown in the following example.</span></span>
>
> `<endpoint binding="basicHttpBinding" name="somename" />`
>
> <span data-ttu-id="fc54b-122">如果您嘗試將名稱設為空白字串並儲存檔案藉以移除名稱，則組態檔仍會包含 `name` 屬性，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="fc54b-122">If you attempt to remove the name by setting it to an empty string and save the file, the configuration file still contains the `name` attribute, as shown in the following example.</span></span>
>
> `<endpoint binding="basicHttpBinding" name="" />`
>
> <span data-ttu-id="fc54b-123">若要清除該屬性，您必須使用其他文字編輯器手動編輯該項目。</span><span class="sxs-lookup"><span data-stu-id="fc54b-123">To purge the attribute, you must manually edit the element using another text editor.</span></span>
>
> <span data-ttu-id="fc54b-124">當您使用 `issueToken` 端點行為的 `clientCredential` 項目時，應特別小心此問題。</span><span class="sxs-lookup"><span data-stu-id="fc54b-124">You should be especially careful with this issue when you use the `issueToken` element of the `clientCredential` Endpoint behavior.</span></span> <span data-ttu-id="fc54b-125">具體來說，其 `address` 子項目的 `localIssuer` 屬性不能是空白字串。</span><span class="sxs-lookup"><span data-stu-id="fc54b-125">Specifically, the `address` attribute of its `localIssuer` sub-element must not be an empty string.</span></span> <span data-ttu-id="fc54b-126">如果您已使用組態編輯器修改過 `address` 屬性，且要將該屬性完全移除，則應使用組態編輯器以外的工具來移除。</span><span class="sxs-lookup"><span data-stu-id="fc54b-126">If you have modified the `address` attribute using the Configuration Editor and want to remove it completely, you should do so using a tool other than the Editor.</span></span> <span data-ttu-id="fc54b-127">否則，屬性會包含空白字串，而且您的應用程式會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="fc54b-127">Otherwise, the attribute contains an empty string and your application throws an exception.</span></span>

## <a name="using-the-configuration-editor"></a><span data-ttu-id="fc54b-128">使用組態編輯器</span><span class="sxs-lookup"><span data-stu-id="fc54b-128">Using the Configuration Editor</span></span>

<span data-ttu-id="fc54b-129">服務組態編輯器位於下列 Windows SDK 安裝位置：</span><span class="sxs-lookup"><span data-stu-id="fc54b-129">The Service Configuration Editor can be found at the following Windows SDK installation location:</span></span>

<span data-ttu-id="fc54b-130">C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin\SvcConfigEditor.exe</span><span class="sxs-lookup"><span data-stu-id="fc54b-130">C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin\SvcConfigEditor.exe</span></span>

<span data-ttu-id="fc54b-131">啟動 [服務設定編輯器] 之後，您可以使用 [檔案] **/[開啟**] 功能表來流覽您要管理的服務或元件。</span><span class="sxs-lookup"><span data-stu-id="fc54b-131">After you launch the Service Configuration Editor, you can use the **File/Open** menu to browse for the service or assembly you want to manage.</span></span> <span data-ttu-id="fc54b-132">您可以直接開啟組態檔，瀏覽 WCF/COM+ 服務，並開啟 Web 託管服務的組態檔。</span><span class="sxs-lookup"><span data-stu-id="fc54b-132">You can open configuration files directly, browse for WCF /COM+ services, and open configuration files for Web-hosted services.</span></span>

<span data-ttu-id="fc54b-133">服務組態編輯器的使用者介面共分為下列幾個區域：</span><span class="sxs-lookup"><span data-stu-id="fc54b-133">The Service Configuration Editor's user interface is divided into the following areas:</span></span>

- <span data-ttu-id="fc54b-134">樹狀檢閱窗格，在左側以樹狀顯示組態項目。</span><span class="sxs-lookup"><span data-stu-id="fc54b-134">Tree View Pane, which displays configuration elements in a tree structure on the left.</span></span> <span data-ttu-id="fc54b-135">您可以用滑鼠右鍵按一下樹狀目錄中的節點來執行作業。</span><span class="sxs-lookup"><span data-stu-id="fc54b-135">You can perform operations in the tree by right-clicking the nodes.</span></span>

- <span data-ttu-id="fc54b-136">工作窗格，可在視窗左下角顯示目前項目的一般工作。</span><span class="sxs-lookup"><span data-stu-id="fc54b-136">Task Pane, which displays common tasks for current elements on the lower-left of the window</span></span>

- <span data-ttu-id="fc54b-137">詳細資料窗格，可在右側顯示 [樹狀檢視] 中所選取組態節點的詳細設定。</span><span class="sxs-lookup"><span data-stu-id="fc54b-137">Detail Pane, which displays detailed settings of the configuration node selected in the Tree View on the right.</span></span>

### <a name="opening-a-configuration-file"></a><span data-ttu-id="fc54b-138">開啟組態檔</span><span class="sxs-lookup"><span data-stu-id="fc54b-138">Opening a Configuration File</span></span>

1. <span data-ttu-id="fc54b-139">使用 [命令] 視窗流覽至您的 WCF 安裝位置，然後輸入，以啟動 [服務設定編輯器] `SvcConfigEditor.exe` 。</span><span class="sxs-lookup"><span data-stu-id="fc54b-139">Start Service Configuration Editor by using a command window to navigate to your WCF installation location, and then type `SvcConfigEditor.exe`.</span></span>

2. <span data-ttu-id="fc54b-140">從 [**檔案**] 功能表中，選取 [**開啟**]，然後按一下您要管理的檔案類型。</span><span class="sxs-lookup"><span data-stu-id="fc54b-140">From the **File** menu, select **Open** and click the type of file you want to manage.</span></span>

3. <span data-ttu-id="fc54b-141">在 [**開啟**] 對話方塊中，流覽至您想要管理的特定檔案，然後按兩下該檔案。</span><span class="sxs-lookup"><span data-stu-id="fc54b-141">In the **Open** dialog box, navigate to the specific file you want to manage and double-click it.</span></span>

<span data-ttu-id="fc54b-142">檢視器會自動遵循組態合併路徑並建立合併組態的檢視。</span><span class="sxs-lookup"><span data-stu-id="fc54b-142">The viewer automatically follows the configuration merge path and creates a view of the merged configuration.</span></span> <span data-ttu-id="fc54b-143">例如，非託管服務的實際設定是 Machine.config 和 App.config 的組合。任何變更都會套用至 Svcconfigeditor.exe 中的使用中檔案。</span><span class="sxs-lookup"><span data-stu-id="fc54b-143">For example, the actual configuration of a non-hosted service is a combination of Machine.config and App.config. Any changes are applied to the active file in the SvcConfigEditor.</span></span> <span data-ttu-id="fc54b-144">如果您想要編輯組態合併路徑中的特定檔案，應該直接開啟它。</span><span class="sxs-lookup"><span data-stu-id="fc54b-144">If you want to edit a specific file in the configuration merge path, you should open it directly.</span></span>

> [!NOTE]
> <span data-ttu-id="fc54b-145">組態編輯器會在目前已開啟的組態檔已在編輯器之外修改時，重新載入該組態檔。</span><span class="sxs-lookup"><span data-stu-id="fc54b-145">Configuration Editor reloads the currently opened configuration file when the latter has been modified outside the Editor.</span></span> <span data-ttu-id="fc54b-146">發生這種情況時，所有未永久儲存在編輯器內的變更都會遺失。</span><span class="sxs-lookup"><span data-stu-id="fc54b-146">When this happens, all the changes that are not durably saved inside the Editor are lost.</span></span> <span data-ttu-id="fc54b-147">如果持續發生重新載入，最有可能的原因是有服務不斷的存取組態檔，例如在背景中執行的防毒軟體。</span><span class="sxs-lookup"><span data-stu-id="fc54b-147">If reloading happens consistently, the most likely cause is a service that constantly accesses the configuration file, for example, an antivirus software running in the background.</span></span> <span data-ttu-id="fc54b-148">若要解決這個問題，請確定該檔案開啟時，組態編輯器是唯一能夠存取該檔案的處理序。</span><span class="sxs-lookup"><span data-stu-id="fc54b-148">To resolve this, ensure that Configuration Editor is the only process that can access the file when it is opened.</span></span>

### <a name="services"></a><span data-ttu-id="fc54b-149">服務</span><span class="sxs-lookup"><span data-stu-id="fc54b-149">Services</span></span>

<span data-ttu-id="fc54b-150">[**服務**] 節點會顯示目前已在設定檔中指派的所有服務。</span><span class="sxs-lookup"><span data-stu-id="fc54b-150">The **Services** node displays all of the services currently assigned in the configuration file.</span></span> <span data-ttu-id="fc54b-151">樹狀目錄中的每個子節點會對應至 `services` 設定檔中 <> 元素的子項目。</span><span class="sxs-lookup"><span data-stu-id="fc54b-151">Each sub-node in the tree corresponds to a sub-element of the <`services`> element in the configuration file.</span></span>

<span data-ttu-id="fc54b-152">當您按一下 [**服務**] 節點時，您可以在 [**詳細資料**窗格] 的 [服務摘要] 頁面上，查看或執行工作。</span><span class="sxs-lookup"><span data-stu-id="fc54b-152">When you click the **Services** node, you can view or perform tasks on the service Summary Page in the **Detail** Pane.</span></span>

#### <a name="creating-a-new-service-configuration"></a><span data-ttu-id="fc54b-153">建立新的服務組態</span><span class="sxs-lookup"><span data-stu-id="fc54b-153">Creating a new Service Configuration</span></span>

<span data-ttu-id="fc54b-154">您可以透過下列方式建立新的服務組態：</span><span class="sxs-lookup"><span data-stu-id="fc54b-154">You can create a new service configuration in the following ways:</span></span>

- <span data-ttu-id="fc54b-155">使用 Wizard：按一下 [**建立新服務**] 連結。</span><span class="sxs-lookup"><span data-stu-id="fc54b-155">Using a Wizard: Click the link **Create a New Service…**</span></span> <span data-ttu-id="fc54b-156">在 [工作窗格] 或 [摘要] 頁面上啟動精靈。</span><span class="sxs-lookup"><span data-stu-id="fc54b-156">on the Task Pane or Summary Page to launch the wizard.</span></span> <span data-ttu-id="fc54b-157">您也可以**在 [檔案**] 功能表中執行此動作->**加入新專案**]。</span><span class="sxs-lookup"><span data-stu-id="fc54b-157">You can also do so in the **File** menu -> **Add New Item**.</span></span>

- <span data-ttu-id="fc54b-158">手動建立：您可以在 [**服務**] 節點上按一下滑鼠右鍵，然後選擇 [**新增服務**]。</span><span class="sxs-lookup"><span data-stu-id="fc54b-158">Create manually: You can right-click the **Services** node and choose **New Service**.</span></span>

#### <a name="creating-a-new-service-endpoint-configuration"></a><span data-ttu-id="fc54b-159">建立新的服務端點組態</span><span class="sxs-lookup"><span data-stu-id="fc54b-159">Creating a new Service Endpoint Configuration</span></span>

<span data-ttu-id="fc54b-160">您可以透過下列方式建立新的服務端點組態：</span><span class="sxs-lookup"><span data-stu-id="fc54b-160">You can create a new service endpoint configuration in the following ways:</span></span>

- <span data-ttu-id="fc54b-161">使用 Wizard 建立：按一下 [**建立新的服務端點**] 連結。</span><span class="sxs-lookup"><span data-stu-id="fc54b-161">Create using a Wizard: click the link **Create a New Service Endpoint…**</span></span> <span data-ttu-id="fc54b-162">在 [工作窗格] 或 [摘要] 頁面上啟動精靈。</span><span class="sxs-lookup"><span data-stu-id="fc54b-162">on the Task Pane or Summary Page to launch the wizard.</span></span> <span data-ttu-id="fc54b-163">您也可以**在 [檔案**] 功能表中執行此動作->**加入新專案**]。</span><span class="sxs-lookup"><span data-stu-id="fc54b-163">You can also do so in the **File** menu -> **Add New Item**.</span></span>

- <span data-ttu-id="fc54b-164">手動建立：建立服務之後，您可以用滑鼠右鍵按一下 [**端點**] 節點，然後選擇 [**新增服務端點**]。</span><span class="sxs-lookup"><span data-stu-id="fc54b-164">Create manually: Once you created a Service, you can right-click the **Endpoints** node and choose "**New Service Endpoint**".</span></span>

#### <a name="editing-a-service-configuration"></a><span data-ttu-id="fc54b-165">編輯服務組態</span><span class="sxs-lookup"><span data-stu-id="fc54b-165">Editing a Service Configuration</span></span>

1. <span data-ttu-id="fc54b-166">按一下 [**服務**] 節點。</span><span class="sxs-lookup"><span data-stu-id="fc54b-166">Click a **Service** node.</span></span>

2. <span data-ttu-id="fc54b-167">編輯屬性方格中的設定。</span><span class="sxs-lookup"><span data-stu-id="fc54b-167">Edit the settings in the property grids.</span></span>

#### <a name="editing-a-service-endpoint-configuration"></a><span data-ttu-id="fc54b-168">編輯服務端點組態</span><span class="sxs-lookup"><span data-stu-id="fc54b-168">Editing a Service Endpoint Configuration</span></span>

1. <span data-ttu-id="fc54b-169">按一下 [**服務端點**] 節點。</span><span class="sxs-lookup"><span data-stu-id="fc54b-169">Click a **Service Endpoint** node.</span></span>

2. <span data-ttu-id="fc54b-170">編輯屬性方格中的設定。</span><span class="sxs-lookup"><span data-stu-id="fc54b-170">Edit the settings in the property grids.</span></span>

#### <a name="adding-a-base-address"></a><span data-ttu-id="fc54b-171">加入基底位址</span><span class="sxs-lookup"><span data-stu-id="fc54b-171">Adding a Base Address</span></span>

1. <span data-ttu-id="fc54b-172">按一下 [**主機**] 節點。</span><span class="sxs-lookup"><span data-stu-id="fc54b-172">Click the **Host** node.</span></span>

2. <span data-ttu-id="fc54b-173">按一下 [新增…] \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="fc54b-173">Click the **New…**</span></span> <span data-ttu-id="fc54b-174">[**基底位址**] 區段中的按鈕。</span><span class="sxs-lookup"><span data-stu-id="fc54b-174">button in the **Base Addresses** section.</span></span>

3. <span data-ttu-id="fc54b-175">在對話方塊中輸入基底位址 URI。</span><span class="sxs-lookup"><span data-stu-id="fc54b-175">Type in the base address URI in the dialog box.</span></span>

4. <span data-ttu-id="fc54b-176">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="fc54b-176">Click **OK**.</span></span>

> [!NOTE]
> <span data-ttu-id="fc54b-177">您無法在 [\<baseAddressPrefixFilters>](../configure-apps/file-schema/wcf/baseaddressprefixfilters.md) 此工具內編輯的值。</span><span class="sxs-lookup"><span data-stu-id="fc54b-177">You cannot edit the value of [\<baseAddressPrefixFilters>](../configure-apps/file-schema/wcf/baseaddressprefixfilters.md) inside this tool.</span></span> <span data-ttu-id="fc54b-178">若要新增或修改這個項目，您應使用文字編輯器或 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="fc54b-178">To add or modify this element, you should use a text editor or Visual Studio.</span></span>

### <a name="client"></a><span data-ttu-id="fc54b-179">Client</span><span class="sxs-lookup"><span data-stu-id="fc54b-179">Client</span></span>

<span data-ttu-id="fc54b-180">[**用戶端**] 節點會顯示設定檔中的所有用戶端端點。</span><span class="sxs-lookup"><span data-stu-id="fc54b-180">The **Client** node displays all of the client endpoints in the configuration file.</span></span> <span data-ttu-id="fc54b-181">樹狀目錄中的每個子節點會對應至 `client` 設定檔中 <> 元素的子項目。</span><span class="sxs-lookup"><span data-stu-id="fc54b-181">Every sub-node in the tree corresponds to a sub-element of the <`client`> element in the configuration file.</span></span>

<span data-ttu-id="fc54b-182">當您按一下 [**用戶端**] 節點時，您可以在 [**詳細資料窗格]** 的用戶端 [**摘要] 頁面**上，查看或執行工作。</span><span class="sxs-lookup"><span data-stu-id="fc54b-182">When you click the **Client** node, you can view or perform tasks on the client **Summary Page** in the **Detail Pane**.</span></span>

#### <a name="creating-a-new-client-endpoint-configuration"></a><span data-ttu-id="fc54b-183">建立新的用戶端端點組態</span><span class="sxs-lookup"><span data-stu-id="fc54b-183">Creating a new Client Endpoint Configuration</span></span>

<span data-ttu-id="fc54b-184">您可以透過下列方式來建立新的用戶端端點組態：</span><span class="sxs-lookup"><span data-stu-id="fc54b-184">You can create a new client endpoint configuration in the following ways:</span></span>

- <span data-ttu-id="fc54b-185">由 Wizard 建立：按一下 [**建立新用戶端**] 連結。</span><span class="sxs-lookup"><span data-stu-id="fc54b-185">Create by Wizard: Click the link **Create a New Client…**</span></span> <span data-ttu-id="fc54b-186">在視窗左下角的 [工作**窗格**] 或 [**摘要] 頁面**上，啟動精靈。</span><span class="sxs-lookup"><span data-stu-id="fc54b-186">on the **Task Pane** on the lower-left of the window, or **Summary Page** to launch the wizard.</span></span> <span data-ttu-id="fc54b-187">您也可以**在 [檔案**] 功能表中執行此動作->**加入新專案**]。</span><span class="sxs-lookup"><span data-stu-id="fc54b-187">You can also do so in the **File** menu -> **Add New Item**.</span></span> <span data-ttu-id="fc54b-188">精靈會提示您指向服務組態的位置，從這裡產生用戶端組態。</span><span class="sxs-lookup"><span data-stu-id="fc54b-188">The wizard prompts you to point to the location of the service configuration, from which the client configuration is generated.</span></span> <span data-ttu-id="fc54b-189">然後您可以選擇要連接的服務端點。</span><span class="sxs-lookup"><span data-stu-id="fc54b-189">You can then choose the service endpoint to connect to.</span></span>

- <span data-ttu-id="fc54b-190">手動建立：以滑鼠右鍵按一下 [**用戶端**] 底下的 [**端點**] 節點，然後選擇 [**新增用戶端端點**]。</span><span class="sxs-lookup"><span data-stu-id="fc54b-190">Create manually: Right-click the **Endpoints** node under **Client**, and choose **New Client Endpoint**.</span></span>

#### <a name="editing-a-client-endpoint-configuration"></a><span data-ttu-id="fc54b-191">編輯用戶端端點組態</span><span class="sxs-lookup"><span data-stu-id="fc54b-191">Editing a Client Endpoint Configuration</span></span>

1. <span data-ttu-id="fc54b-192">按一下 [**用戶端端點**] 節點。</span><span class="sxs-lookup"><span data-stu-id="fc54b-192">Click a **Client Endpoint** node.</span></span>

2. <span data-ttu-id="fc54b-193">編輯屬性方格中的設定。</span><span class="sxs-lookup"><span data-stu-id="fc54b-193">Edit the settings in the property grids.</span></span>

### <a name="standard-endpoint"></a><span data-ttu-id="fc54b-194">標準端點</span><span class="sxs-lookup"><span data-stu-id="fc54b-194">Standard Endpoint</span></span>

<span data-ttu-id="fc54b-195">標準端點是專屬端點，可將位址、連絡人和繫結的一個或多個部分設為預設值。</span><span class="sxs-lookup"><span data-stu-id="fc54b-195">Standard endpoints are specialized endpoints that have one or more aspects of the address, contract and binding set to default values.</span></span>

<span data-ttu-id="fc54b-196">這類設定會儲存在 [**標準端點**] 節點中。</span><span class="sxs-lookup"><span data-stu-id="fc54b-196">Such configuration settings are stored in the **Standard Endpoint** node.</span></span> <span data-ttu-id="fc54b-197">[**標準端點**] 節點會顯示設定檔中的所有標準端點設定。</span><span class="sxs-lookup"><span data-stu-id="fc54b-197">The **Standard Endpoint** node displays all of the standard endpoint settings in the configuration file.</span></span> <span data-ttu-id="fc54b-198">樹狀目錄中的每個子節點會對應至設定檔中專案的子項目 `<standardEndpoints>` 。</span><span class="sxs-lookup"><span data-stu-id="fc54b-198">Every sub-node in the tree corresponds to a sub-element in the `<standardEndpoints>` element in the configuration file.</span></span>

<span data-ttu-id="fc54b-199">當您按一下 [**標準端點**] 節點時，可以在 [**詳細資料窗格]** 的標準端點 [**摘要] 頁面**上，查看或執行工作。</span><span class="sxs-lookup"><span data-stu-id="fc54b-199">When you click the **Standard Endpoint** node, you can view or perform tasks on the standard endpoint **Summary Page** in the **Detail Pane**.</span></span>

#### <a name="creating-a-new-standard-endpoint-configuration"></a><span data-ttu-id="fc54b-200">建立新的標準端點組態</span><span class="sxs-lookup"><span data-stu-id="fc54b-200">Creating a New Standard Endpoint Configuration</span></span>

<span data-ttu-id="fc54b-201">您可以透過下列方式建立新的標準端點組態：</span><span class="sxs-lookup"><span data-stu-id="fc54b-201">You can create a new standard endpoint configuration in the following ways:</span></span>

- <span data-ttu-id="fc54b-202">以滑鼠右鍵按一下 [**標準端點**] 節點，然後選取 [**新增標準端點**設定]。</span><span class="sxs-lookup"><span data-stu-id="fc54b-202">Right-click the **Standard Endpoint** node and select **New Standard Endpoint Configuration…**</span></span> <span data-ttu-id="fc54b-203">在對話方塊中選取系結類型，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="fc54b-203">Select the binding type in the dialog box and click **OK**.</span></span>

- <span data-ttu-id="fc54b-204">選取 [**標準端點**] 節點，然後按一下 [**新增標準端點**設定]。</span><span class="sxs-lookup"><span data-stu-id="fc54b-204">Select the **Standard Endpoint** node and click **New Standard Endpoint Configuration…**</span></span> <span data-ttu-id="fc54b-205">在視窗左下角的 [工作**窗格**] 中。</span><span class="sxs-lookup"><span data-stu-id="fc54b-205">in the **Task Pane** on the lower-left of the window.</span></span>

<span data-ttu-id="fc54b-206">[**建立新的標準端點**] 對話方塊會顯示並列出所有已註冊的標準端點類型。</span><span class="sxs-lookup"><span data-stu-id="fc54b-206">The **Creating a New Standard Endpoint** dialog box displays and lists all registered standard endpoint types.</span></span>

#### <a name="viewing-and-editing-a-standard-endpoint-configuration"></a><span data-ttu-id="fc54b-207">檢視及編輯標準端點組態</span><span class="sxs-lookup"><span data-stu-id="fc54b-207">Viewing and Editing a Standard Endpoint Configuration</span></span>

<span data-ttu-id="fc54b-208">您可以透過下列方式開啟標準端點組態進行檢視和編輯：</span><span class="sxs-lookup"><span data-stu-id="fc54b-208">You can open a standard endpoint configuration for viewing and editing in the following ways:</span></span>

- <span data-ttu-id="fc54b-209">按一下以展開 [**標準端點**] 節點，然後按一下個別的 [端點] 子節點。</span><span class="sxs-lookup"><span data-stu-id="fc54b-209">Click to expand the **Standard Endpoint** node and click the respective endpoint sub-node.</span></span>

- <span data-ttu-id="fc54b-210">按一下 [**標準端點**] 節點，然後按一下 [詳細資料] 窗格上的個別端點。</span><span class="sxs-lookup"><span data-stu-id="fc54b-210">Click the **Standard Endpoint** node and click the respective endpoint on the Detail pane.</span></span>

<span data-ttu-id="fc54b-211">端點的屬性會在右窗格中顯示供您編輯。</span><span class="sxs-lookup"><span data-stu-id="fc54b-211">Attributes for the endpoint are shown in the right pane for editing.</span></span>

#### <a name="deleting-a-standard-endpoint-configuration"></a><span data-ttu-id="fc54b-212">刪除標準端點組態</span><span class="sxs-lookup"><span data-stu-id="fc54b-212">Deleting a Standard Endpoint Configuration</span></span>

<span data-ttu-id="fc54b-213">您可以透過下列方式刪除標準端點組態：</span><span class="sxs-lookup"><span data-stu-id="fc54b-213">You can delete a standard endpoint configuration in the following ways:</span></span>

- <span data-ttu-id="fc54b-214">按一下以展開 [**標準端點**] 節點，然後以滑鼠右鍵按一下個別的 [端點] 子節點。</span><span class="sxs-lookup"><span data-stu-id="fc54b-214">Click to expand the **Standard Endpoint** node and right-click the respective endpoint sub-node.</span></span> <span data-ttu-id="fc54b-215">使用內容命令 [**刪除標準端點**設定] 來刪除端點。</span><span class="sxs-lookup"><span data-stu-id="fc54b-215">Use the context command **Delete Standard Endpoint Configuration** to delete the endpoint.</span></span>

- <span data-ttu-id="fc54b-216">按一下 [**標準端點**] 節點。</span><span class="sxs-lookup"><span data-stu-id="fc54b-216">Click the **Standard Endpoint** node.</span></span> <span data-ttu-id="fc54b-217">**在工作窗格**中，按一下 [**刪除標準端點**設定]。</span><span class="sxs-lookup"><span data-stu-id="fc54b-217">In the **Task** pane, click **Delete Standard Endpoint Configuration**.</span></span>

<span data-ttu-id="fc54b-218">如果標準端點正在使用中，當您嘗試刪除它時，就會顯示警告訊息：**標準端點正在使用中。如果您現在刪除它，請務必在設定的其他部分（例如，在服務端點或用戶端端點）中刪除其所有參考。否則，設定將會無效，且下次無法開啟。您確定要刪除標準端點嗎？** 」</span><span class="sxs-lookup"><span data-stu-id="fc54b-218">If the standard endpoint is in used, a warning message is displayed when you attempt to delete it: **The standard endpoint is in use. If you delete it now, please be sure to delete all of its references in other parts of the configuration (for example, in the service endpoint or client endpoint). Otherwise, the configuration will be invalid and cannot be opened next time. Are you sure you want to delete the standard endpoint?"**</span></span>

### <a name="binding"></a><span data-ttu-id="fc54b-219">繫結</span><span class="sxs-lookup"><span data-stu-id="fc54b-219">Binding</span></span>

<span data-ttu-id="fc54b-220">繫結組態是用來設定端點上的繫結。</span><span class="sxs-lookup"><span data-stu-id="fc54b-220">Binding configurations are used to configure bindings on endpoints.</span></span> <span data-ttu-id="fc54b-221">這類設定會儲存**在 [系**結] 節點中。</span><span class="sxs-lookup"><span data-stu-id="fc54b-221">Such configuration settings are stored in the **Binding** node.</span></span> <span data-ttu-id="fc54b-222">端點會依據名稱參考繫結組態，而多個端點可參考單一繫結組態。</span><span class="sxs-lookup"><span data-stu-id="fc54b-222">Endpoints reference binding configurations by name and multiple endpoints can reference a single binding configuration.</span></span>

<span data-ttu-id="fc54b-223">[系結 **] 節點會**顯示設定檔中的所有系結設定。</span><span class="sxs-lookup"><span data-stu-id="fc54b-223">The **Bindings** node displays all of the binding settings in the configuration file.</span></span> <span data-ttu-id="fc54b-224">樹狀目錄中的每個子節點會對應至設定檔中 <> 元素的子項目 `bindings` 。</span><span class="sxs-lookup"><span data-stu-id="fc54b-224">Every sub-node in the tree corresponds to a sub-element in the <`bindings`> element in the configuration file.</span></span>

<span data-ttu-id="fc54b-225">當您按一下 [系結]**節點時**，可以在 [**詳細資料窗格]** 的 [系結**摘要] 頁面**上，查看或執行工作。</span><span class="sxs-lookup"><span data-stu-id="fc54b-225">When you click the **Bindings** node, you can view or perform tasks on the binding **Summary Page** in the **Detail Pane**.</span></span>

#### <a name="creating-a-new-binding-configuration"></a><span data-ttu-id="fc54b-226">建立新的繫結組態</span><span class="sxs-lookup"><span data-stu-id="fc54b-226">Creating a New Binding Configuration</span></span>

<span data-ttu-id="fc54b-227">您可以透過下列方式建立新的繫結組態。</span><span class="sxs-lookup"><span data-stu-id="fc54b-227">You can create a new binding configuration in the following ways.</span></span>

- <span data-ttu-id="fc54b-228">以滑鼠右鍵按一下 **[系**結] 節點，然後選取 [**新增**系結設定]。</span><span class="sxs-lookup"><span data-stu-id="fc54b-228">Right-click the **Bindings** node and select **New Binding Configuration**…</span></span> <span data-ttu-id="fc54b-229">在對話方塊中選取系結類型，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="fc54b-229">Select the binding type in the dialog box and click **OK**.</span></span>

- <span data-ttu-id="fc54b-230">選取 [系結]**節點，然後**按一下 [**新增**系結設定]。</span><span class="sxs-lookup"><span data-stu-id="fc54b-230">Select the **Bindings** node and click **New Binding Configuration**…</span></span> <span data-ttu-id="fc54b-231">在視窗左下角的 [工作**窗格**] 中。</span><span class="sxs-lookup"><span data-stu-id="fc54b-231">in the **Task Pane** on the lower-left of the window.</span></span>

- <span data-ttu-id="fc54b-232">在服務或用戶端摘要頁面中，按一下 [系結設定 **] 欄位中的 [** **按一下以建立**]，為對應的端點建立系結設定。</span><span class="sxs-lookup"><span data-stu-id="fc54b-232">In the service or client summary page, click **Click to Create** in the **Binding Configuration** field to create a binding configuration for the corresponding endpoint.</span></span>

#### <a name="adding-binding-element-extensions-to-a-custom-binding"></a><span data-ttu-id="fc54b-233">將繫結項目擴充功能加入至自訂繫結中</span><span class="sxs-lookup"><span data-stu-id="fc54b-233">Adding Binding Element Extensions to a Custom Binding</span></span>

1. <span data-ttu-id="fc54b-234">選取您要在其中新增擴充功能項目的繫結。</span><span class="sxs-lookup"><span data-stu-id="fc54b-234">Select the binding you want to add an extension element to.</span></span>

2. <span data-ttu-id="fc54b-235">按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="fc54b-235">Click **Add**.</span></span>

3. <span data-ttu-id="fc54b-236">從可用延伸清單中，選取您要加入的繫結項目延伸。</span><span class="sxs-lookup"><span data-stu-id="fc54b-236">From the list of available extensions, select the binding element extension you want to add.</span></span> <span data-ttu-id="fc54b-237">若要選取多個項目，請同時按下 CTRL 鍵。</span><span class="sxs-lookup"><span data-stu-id="fc54b-237">To select multiple items, press the CTRL key simultaneously.</span></span>

4. <span data-ttu-id="fc54b-238">按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="fc54b-238">Click **Add**.</span></span>

#### <a name="adjusting-the-extension-position-in-a-custom-binding"></a><span data-ttu-id="fc54b-239">調整自訂繫結中的擴充功能位置</span><span class="sxs-lookup"><span data-stu-id="fc54b-239">Adjusting the Extension Position in a Custom Binding</span></span>

<span data-ttu-id="fc54b-240">自訂繫結是一種會形成堆疊的繫結項目集合。</span><span class="sxs-lookup"><span data-stu-id="fc54b-240">A custom binding is a collection of binding elements that form a stack.</span></span> <span data-ttu-id="fc54b-241">堆疊上的每個繫結項目都有專屬的組態設定。</span><span class="sxs-lookup"><span data-stu-id="fc54b-241">Each binding element on the stack has its own configuration settings.</span></span> <span data-ttu-id="fc54b-242">自訂繫結中的繫結項目擴充功能順序代表每個擴充功能在堆疊中的位置。</span><span class="sxs-lookup"><span data-stu-id="fc54b-242">The order of the binding element extensions in a custom binding indicates their positions in the stack.</span></span> <span data-ttu-id="fc54b-243">在堆疊頂端的項目會優先套用。</span><span class="sxs-lookup"><span data-stu-id="fc54b-243">Elements at the top of the stack are applied first.</span></span> <span data-ttu-id="fc54b-244">若要變更順序：</span><span class="sxs-lookup"><span data-stu-id="fc54b-244">To change the ordering:</span></span>

1. <span data-ttu-id="fc54b-245">選取自訂繫結節點。</span><span class="sxs-lookup"><span data-stu-id="fc54b-245">Select the custom binding node.</span></span>

2. <span data-ttu-id="fc54b-246">在 [**繫結項目延伸位置**] 區段中選取一個系結延伸模組元素。</span><span class="sxs-lookup"><span data-stu-id="fc54b-246">Select one binding extension element in the **Binding Element Extension Position** section.</span></span>

3. <span data-ttu-id="fc54b-247">使用清單左側的 [**向上**] 或 [**向下**] 按鈕，變更選取專案的位置。</span><span class="sxs-lookup"><span data-stu-id="fc54b-247">Use the **Up** or **Down** button on the left side of the list to change the position of the selected element.</span></span>

#### <a name="editing-the-configuration-of-binding-element-extensions-in-a-custom-binding"></a><span data-ttu-id="fc54b-248">編輯自訂繫結中繫結項目擴充功能的組態</span><span class="sxs-lookup"><span data-stu-id="fc54b-248">Editing the Configuration of Binding Element Extensions in a Custom Binding</span></span>

1. <span data-ttu-id="fc54b-249">選取樹狀目錄中的繫結程序節點。</span><span class="sxs-lookup"><span data-stu-id="fc54b-249">Select the binding node in the tree.</span></span>

2. <span data-ttu-id="fc54b-250">選取包含您要編輯之項目的自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="fc54b-250">Select the custom binding that contains the element you want to edit.</span></span>

3. <span data-ttu-id="fc54b-251">選取您要編輯的繫結項目延伸。</span><span class="sxs-lookup"><span data-stu-id="fc54b-251">Select the binding element extension you want to edit.</span></span> <span data-ttu-id="fc54b-252">項目設定會出現在右窗格中供您進行編輯。</span><span class="sxs-lookup"><span data-stu-id="fc54b-252">The settings of the element appear in the right pane, where they can be edited.</span></span>

### <a name="diagnostics"></a><span data-ttu-id="fc54b-253">診斷</span><span class="sxs-lookup"><span data-stu-id="fc54b-253">Diagnostics</span></span>

<span data-ttu-id="fc54b-254">[**診斷**] 節點會顯示設定檔中的所有診斷設定。</span><span class="sxs-lookup"><span data-stu-id="fc54b-254">The **Diagnostics** node displays all of the diagnostic settings in the configuration file.</span></span> <span data-ttu-id="fc54b-255">它可讓您開啟或關閉效能計數器、啟用或停用 Windows Management Instrumentation （WMI）、設定 WCF 追蹤，以及設定 WCF 訊息記錄。</span><span class="sxs-lookup"><span data-stu-id="fc54b-255">It enables you to turn performance counters on or off, enable or disable Windows Management Instrumentation (WMI), configure WCF tracing, and configure WCF message logging.</span></span> <span data-ttu-id="fc54b-256">[**診斷**] 節點中的設定會對應至設定檔中的 [<`system.diagnostics`>] 區段和 [] `<diagnostics>` 區段 `<system.serviceModel>` 。</span><span class="sxs-lookup"><span data-stu-id="fc54b-256">The settings in the **Diagnostics** node correspond to the <`system.diagnostics`> section, and `<diagnostics>` section in `<system.serviceModel>` in the configuration file.</span></span>

<span data-ttu-id="fc54b-257">當您按一下 [**診斷**] 節點時，可以在 [**詳細資料窗格]** 的診斷 [**摘要] 頁面**上，查看或執行工作。</span><span class="sxs-lookup"><span data-stu-id="fc54b-257">When you click the **Diagnostics** node, you can view or perform tasks on the diagnostics **Summary Page** in the **Detail Pane**.</span></span>

#### <a name="configuring-performance-counters-and-wmi"></a><span data-ttu-id="fc54b-258">設定效能計數器與 WMI</span><span class="sxs-lookup"><span data-stu-id="fc54b-258">Configuring performance counters and WMI</span></span>

1. <span data-ttu-id="fc54b-259">按一下 [**診斷**] 節點。</span><span class="sxs-lookup"><span data-stu-id="fc54b-259">Click the **Diagnostics** node.</span></span>

2. <span data-ttu-id="fc54b-260">按一下 [**切換效能計數器**]。</span><span class="sxs-lookup"><span data-stu-id="fc54b-260">Click **Toggle Performance Counters**.</span></span> <span data-ttu-id="fc54b-261">效能計數器具有三種狀態：Off (default)、ServiceOnly 和 All。</span><span class="sxs-lookup"><span data-stu-id="fc54b-261">The performance counter has three states: Off (default), ServiceOnly, and All.</span></span> <span data-ttu-id="fc54b-262">按一下連結，即可切換設定這三種狀態。</span><span class="sxs-lookup"><span data-stu-id="fc54b-262">Clicking the link toggles the setting among these three states.</span></span>

#### <a name="configuring-wmi-provider"></a><span data-ttu-id="fc54b-263">設定 WMI 提供者</span><span class="sxs-lookup"><span data-stu-id="fc54b-263">Configuring WMI Provider</span></span>

1. <span data-ttu-id="fc54b-264">按一下 [**診斷**] 節點。</span><span class="sxs-lookup"><span data-stu-id="fc54b-264">Click the **Diagnostics** node.</span></span>

2. <span data-ttu-id="fc54b-265">若要啟用 WMI 提供者，請按一下 [**啟用 Wmi 提供者**] 連結。</span><span class="sxs-lookup"><span data-stu-id="fc54b-265">To enable WMI provider, click the **Enable WMI Provider** link.</span></span>

#### <a name="enabling-wcf-tracing"></a><span data-ttu-id="fc54b-266">啟用 WCF 追蹤</span><span class="sxs-lookup"><span data-stu-id="fc54b-266">Enabling WCF Tracing</span></span>

<span data-ttu-id="fc54b-267">您可以使用標準屬性來建立 WCF 追蹤檔，或是設定自訂追蹤檔。</span><span class="sxs-lookup"><span data-stu-id="fc54b-267">You can create a WCF trace file with standard properties or set up a custom trace file.</span></span>

1. <span data-ttu-id="fc54b-268">按一下 [**診斷**] 節點。</span><span class="sxs-lookup"><span data-stu-id="fc54b-268">Click the **Diagnostics** node.</span></span>

2. <span data-ttu-id="fc54b-269">按一下 [**啟用追蹤**]。</span><span class="sxs-lookup"><span data-stu-id="fc54b-269">Click **Enable Tracing**.</span></span>

3. <span data-ttu-id="fc54b-270">按一下 [**追蹤層級**] 連結，以調整追蹤層級。</span><span class="sxs-lookup"><span data-stu-id="fc54b-270">Click the **Trace Level** link to adjust the trace level.</span></span> <span data-ttu-id="fc54b-271">追蹤層級共有六個：關閉、關鍵、錯誤、警告、資訊與詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="fc54b-271">There are six trace levels: Off, Critical, Error, Warning, Information, and Verbose.</span></span> <span data-ttu-id="fc54b-272">[**活動追蹤**] 與 [**傳播活動**] 選項可讓您使用 WCF 活動追蹤功能。</span><span class="sxs-lookup"><span data-stu-id="fc54b-272">The **Activity Tracing** and **Propagate Activity** option enable you to use the WCF activity tracing feature.</span></span>

4. <span data-ttu-id="fc54b-273">您可以按一下追蹤接聽項名稱，指定追蹤檔案與選項。</span><span class="sxs-lookup"><span data-stu-id="fc54b-273">Click the trace listener name to specify the trace file and options.</span></span>

#### <a name="enabling-wcf-logging"></a><span data-ttu-id="fc54b-274">啟用 WCF 記錄</span><span class="sxs-lookup"><span data-stu-id="fc54b-274">Enabling WCF Logging</span></span>

<span data-ttu-id="fc54b-275">您可以使用標準屬性來建立 WCF 追蹤檔，或是設定自訂追蹤檔。</span><span class="sxs-lookup"><span data-stu-id="fc54b-275">You can create a WCF trace file with standard properties or set up a custom trace file.</span></span>

1. <span data-ttu-id="fc54b-276">按一下 [**診斷**] 節點。</span><span class="sxs-lookup"><span data-stu-id="fc54b-276">Click the **Diagnostics** node.</span></span>

2. <span data-ttu-id="fc54b-277">按一下 [**啟用訊息記錄**]。</span><span class="sxs-lookup"><span data-stu-id="fc54b-277">Click **Enable Message Logging**.</span></span>

3. <span data-ttu-id="fc54b-278">按一下 [**記錄層級**] 連結，以調整記錄層級。</span><span class="sxs-lookup"><span data-stu-id="fc54b-278">Click the **Log Level** link to adjust the log level.</span></span> <span data-ttu-id="fc54b-279">記錄層級共有三個：格式錯誤、服務和傳輸。</span><span class="sxs-lookup"><span data-stu-id="fc54b-279">There are three log levels: Malformed, Service, and Transport.</span></span>

4. <span data-ttu-id="fc54b-280">您可以按一下接聽項名稱，指定記錄檔案與選項。</span><span class="sxs-lookup"><span data-stu-id="fc54b-280">Click the listener name to specify the log file and options.</span></span>

> [!NOTE]
> <span data-ttu-id="fc54b-281">如果您想要在關閉應用程式時自動清除追蹤和訊息記錄，請啟用 [**自動清除**] 選項。</span><span class="sxs-lookup"><span data-stu-id="fc54b-281">If you want the trace and message logs to be flushed automatically when your application is closed, enable the **Auto Flush** option.</span></span>

<span data-ttu-id="fc54b-282">[**診斷\*\*\*\*摘要] 頁面**可讓您完成設定診斷作業的最常見工作。</span><span class="sxs-lookup"><span data-stu-id="fc54b-282">The **Diagnostics** **Summary Page** enables you to accomplish the most common tasks in configuring diagnostics.</span></span> <span data-ttu-id="fc54b-283">不過，如果您想要手動編輯 [接聽程式] 和 [來源] 設定，必須展開 [診斷] 節點，然後編輯 [**訊息記錄** **]、[** 接聽**程式**和**來源**] 節點中的設定。</span><span class="sxs-lookup"><span data-stu-id="fc54b-283">However, if you want to manually edit the Listeners and Sources settings, you must expand the **Diagnostics** node and edit settings in **Message Logging**, **Listeners** and **Sources** node.</span></span>

#### <a name="enabling-wcf-custom-tracing-or-message-logging"></a><span data-ttu-id="fc54b-284">啟用 WCF 自訂追蹤或訊息記錄</span><span class="sxs-lookup"><span data-stu-id="fc54b-284">Enabling WCF Custom Tracing or Message Logging</span></span>

1. <span data-ttu-id="fc54b-285">按一下 [**診斷**] 節點，然後將它展開。</span><span class="sxs-lookup"><span data-stu-id="fc54b-285">Click the **Diagnostics** node, and expand it.</span></span>

2. <span data-ttu-id="fc54b-286">以滑鼠右鍵按一下 **[接聽**程式] 節點，然後選取 [新增接聽程式 **]**。</span><span class="sxs-lookup"><span data-stu-id="fc54b-286">Right-click the **Listeners** node and select **New Listener**.</span></span>

3. <span data-ttu-id="fc54b-287">在 [ **InitData** ] 欄位中輸入追蹤檔名稱。</span><span class="sxs-lookup"><span data-stu-id="fc54b-287">Type in the trace file name in the **InitData** field.</span></span> <span data-ttu-id="fc54b-288">您可以按一下 [...]按鈕以流覽至路徑。</span><span class="sxs-lookup"><span data-stu-id="fc54b-288">You can click the "…" button to browse to a path.</span></span>

4. <span data-ttu-id="fc54b-289">按一下 [ **TypeName** ] 行就會顯示「...」button.</span><span class="sxs-lookup"><span data-stu-id="fc54b-289">Clicking the **TypeName** line displays a "…" button.</span></span> <span data-ttu-id="fc54b-290">按一下此按鈕以開啟 [**追蹤接聽程式類型瀏覽器]**，您可以用來尋找已經安裝的預先設定追蹤接聽項。</span><span class="sxs-lookup"><span data-stu-id="fc54b-290">Click this button to open the **Trace Listener Type Browser**, which you can use to find pre-configured trace listeners that are already installed.</span></span>

5. <span data-ttu-id="fc54b-291">請注意 [**來源**] 區段。</span><span class="sxs-lookup"><span data-stu-id="fc54b-291">Note the **Source** section.</span></span> <span data-ttu-id="fc54b-292">按一下此區段中的 [**新增**] 以開啟含有下拉式功能表的對話方塊，其中會列出可用的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="fc54b-292">Click **Add** in this section to open a dialog box with a drop-down menu, which lists available tracing sources.</span></span> <span data-ttu-id="fc54b-293">選取追蹤來源，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="fc54b-293">Select a tracing source and click **OK**.</span></span>

6. <span data-ttu-id="fc54b-294">若要編輯訊息記錄設定，請按一下 [**訊息記錄**] 節點。</span><span class="sxs-lookup"><span data-stu-id="fc54b-294">To edit Message Logging settings, click the **Message Logging** node.</span></span> <span data-ttu-id="fc54b-295">您可以編輯屬性方格中的設定。</span><span class="sxs-lookup"><span data-stu-id="fc54b-295">You can edit the settings in the property grid.</span></span>

### <a name="advanced"></a><span data-ttu-id="fc54b-296">進階</span><span class="sxs-lookup"><span data-stu-id="fc54b-296">Advanced</span></span>

#### <a name="behaviors"></a><span data-ttu-id="fc54b-297">「行為」</span><span class="sxs-lookup"><span data-stu-id="fc54b-297">Behaviors</span></span>

<span data-ttu-id="fc54b-298">[**行為**] 節點會顯示目前定義于設定檔中的行為。</span><span class="sxs-lookup"><span data-stu-id="fc54b-298">The **Behaviors** node displays the behaviors that are currently defined in the configuration file.</span></span>

<span data-ttu-id="fc54b-299">行為組態是用來設定端點與服務的行為。</span><span class="sxs-lookup"><span data-stu-id="fc54b-299">Behavior configurations are used to configure behaviors of endpoints and services.</span></span> <span data-ttu-id="fc54b-300">這類設定會儲存在 [**服務行為**] 和 [**端點行為**] 底下的 [ **Advanced** ] 節點中。</span><span class="sxs-lookup"><span data-stu-id="fc54b-300">Such configuration settings are stored in the **Advanced** node under **Service Behaviors** and **Endpoint Behaviors**.</span></span> <span data-ttu-id="fc54b-301">服務會使用服務行為，而端點則會使用端點行為。</span><span class="sxs-lookup"><span data-stu-id="fc54b-301">Service behaviors are used by services; whereas endpoint behaviors by endpoints.</span></span>

<span data-ttu-id="fc54b-302">行為是一種會形成堆疊之延伸項目的集合。</span><span class="sxs-lookup"><span data-stu-id="fc54b-302">Behaviors are a collection of extension elements that for a stack.</span></span> <span data-ttu-id="fc54b-303">在堆疊頂端的項目會優先套用。</span><span class="sxs-lookup"><span data-stu-id="fc54b-303">The element at the top of the stack is applied first.</span></span> <span data-ttu-id="fc54b-304">每個延伸項目可以擁有專屬的組態。</span><span class="sxs-lookup"><span data-stu-id="fc54b-304">Each extension element can have its own configuration.</span></span>

##### <a name="creating-a-new-behavior-configuration"></a><span data-ttu-id="fc54b-305">建立新的行為組態</span><span class="sxs-lookup"><span data-stu-id="fc54b-305">Creating a new Behavior Configuration</span></span>

<span data-ttu-id="fc54b-306">您可以透過下列兩種方式建立新的行為組態。</span><span class="sxs-lookup"><span data-stu-id="fc54b-306">You can create a new behavior configuration in two ways.</span></span>

- <span data-ttu-id="fc54b-307">以滑鼠右鍵按一下其中一個行為節點，然後選取 [**新增行為**設定 ...]</span><span class="sxs-lookup"><span data-stu-id="fc54b-307">Right-click one of the behavior nodes and select "**New Behavior Configuration…**</span></span>

- <span data-ttu-id="fc54b-308">選取其中一個行為節點，然後按一下 [**新增行為**設定]。</span><span class="sxs-lookup"><span data-stu-id="fc54b-308">Select one of the behavior nodes and click the **New Behavior Configuration**…</span></span> <span data-ttu-id="fc54b-309">在視窗左下角的 [工作**窗格**] 中。</span><span class="sxs-lookup"><span data-stu-id="fc54b-309">in the **Task Pane** on the lower-left of the window.</span></span>

##### <a name="adding-behavior-element-extensions-to-a-behavior"></a><span data-ttu-id="fc54b-310">將行為項目延伸加入至行為中</span><span class="sxs-lookup"><span data-stu-id="fc54b-310">Adding Behavior Element Extensions to a Behavior</span></span>

1. <span data-ttu-id="fc54b-311">選取其中一個行為節點。</span><span class="sxs-lookup"><span data-stu-id="fc54b-311">Select one of the behavior nodes.</span></span>

2. <span data-ttu-id="fc54b-312">選取您要編輯的行為。</span><span class="sxs-lookup"><span data-stu-id="fc54b-312">Select the behavior you want edit.</span></span>

3. <span data-ttu-id="fc54b-313">按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="fc54b-313">Click **Add**.</span></span>

4. <span data-ttu-id="fc54b-314">從可用擴充功能清單中，選取您要新增的行為項目擴充功能。</span><span class="sxs-lookup"><span data-stu-id="fc54b-314">From the list of available extensions, select the behavior element extension you want to add.</span></span>

5. <span data-ttu-id="fc54b-315">按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="fc54b-315">Click **Add**.</span></span>

##### <a name="adjusting-the-extension-position-in-a-behavior"></a><span data-ttu-id="fc54b-316">調整行為中的延伸位置</span><span class="sxs-lookup"><span data-stu-id="fc54b-316">Adjusting the Extension Position in a Behavior</span></span>

<span data-ttu-id="fc54b-317">行為是一種會形成堆疊之項目的集合。</span><span class="sxs-lookup"><span data-stu-id="fc54b-317">Behaviors are collections of elements that form a stack.</span></span> <span data-ttu-id="fc54b-318">堆疊上的每個項目都有專屬的組態。</span><span class="sxs-lookup"><span data-stu-id="fc54b-318">Each element on the stack has its own configuration.</span></span> <span data-ttu-id="fc54b-319">行為中的行為項目延伸順序代表每個延伸在堆疊中的位置。</span><span class="sxs-lookup"><span data-stu-id="fc54b-319">The order of the behavior element extensions in a behavior indicates their positions in the stack.</span></span> <span data-ttu-id="fc54b-320">在堆疊頂端的項目會優先套用。</span><span class="sxs-lookup"><span data-stu-id="fc54b-320">Elements at the top of the stack are applied first.</span></span> <span data-ttu-id="fc54b-321">若要變更順序：</span><span class="sxs-lookup"><span data-stu-id="fc54b-321">To change the ordering:</span></span>

1. <span data-ttu-id="fc54b-322">選取其中一個行為節點。</span><span class="sxs-lookup"><span data-stu-id="fc54b-322">Select one of the behavior nodes.</span></span>

2. <span data-ttu-id="fc54b-323">選取您要編輯的行為。</span><span class="sxs-lookup"><span data-stu-id="fc54b-323">Select the behavior you want edit.</span></span>

3. <span data-ttu-id="fc54b-324">在 [**行為專案延伸位置**] 區段中選取行為延伸模組元素。</span><span class="sxs-lookup"><span data-stu-id="fc54b-324">Select a behavior extension element in the **Behavior Element Extension Position** section.</span></span>

4. <span data-ttu-id="fc54b-325">使用清單左側的 [**向上**] 或 [**向下**] 按鈕，變更選取專案的位置。</span><span class="sxs-lookup"><span data-stu-id="fc54b-325">Use the **Up** or **Down** button on the left side of the list to change the position of the selected element.</span></span>

##### <a name="editing-the-configuration-of-behavior-element-extensions"></a><span data-ttu-id="fc54b-326">編輯行為項目擴充功能的組態</span><span class="sxs-lookup"><span data-stu-id="fc54b-326">Editing the Configuration of Behavior Element Extensions</span></span>

1. <span data-ttu-id="fc54b-327">選取樹狀目錄的其中一個行為節點。</span><span class="sxs-lookup"><span data-stu-id="fc54b-327">Select one of the behavior nodes in the tree.</span></span>

2. <span data-ttu-id="fc54b-328">選取包含您要編輯之項目的行為。</span><span class="sxs-lookup"><span data-stu-id="fc54b-328">Select the behavior that contains the element you want to edit.</span></span>

3. <span data-ttu-id="fc54b-329">選取您要編輯的行為項目擴充功能。</span><span class="sxs-lookup"><span data-stu-id="fc54b-329">Select the behavior element extension you want to edit.</span></span> <span data-ttu-id="fc54b-330">項目設定會出現在右窗格中供您進行編輯。</span><span class="sxs-lookup"><span data-stu-id="fc54b-330">The settings of the element appear in the right pane where they can be edited.</span></span>

#### <a name="protocolmapping"></a><span data-ttu-id="fc54b-331">ProtocolMapping</span><span class="sxs-lookup"><span data-stu-id="fc54b-331">ProtocolMapping</span></span>

<span data-ttu-id="fc54b-332">這個區段可讓您透過通訊協定位址配置與可能的繫結之間已定義的對應，針對不同的通訊協定設定預設的繫結型別，例如 http、tcp、MSMQ 或 net.pipe。</span><span class="sxs-lookup"><span data-stu-id="fc54b-332">This section allows you to set default binding types for different protocols such as http, tcp, MSMQ or net.pipe through defined mapping between protocol address schemes and the possible bindings.</span></span> <span data-ttu-id="fc54b-333">您也可以加入其他通訊協定的新對應。</span><span class="sxs-lookup"><span data-stu-id="fc54b-333">You can also add new mappings to other protocols.</span></span>

#### <a name="extensions"></a><span data-ttu-id="fc54b-334">延伸模組</span><span class="sxs-lookup"><span data-stu-id="fc54b-334">Extensions</span></span>

<span data-ttu-id="fc54b-335">您可以註冊新的系結延伸、繫結項目延伸、標準端點延伸和行為延伸模組，以便在 WCF 設定中使用。</span><span class="sxs-lookup"><span data-stu-id="fc54b-335">New binding extensions, binding element extensions, standard endpoint extensions and behavior extensions can be registered for use in WCF configuration.</span></span> <span data-ttu-id="fc54b-336">擴充功能是名稱/型別的配對。</span><span class="sxs-lookup"><span data-stu-id="fc54b-336">Extensions are name/type pairs.</span></span> <span data-ttu-id="fc54b-337">名稱可定義組態中延伸的名稱，而型別則可實作延伸。</span><span class="sxs-lookup"><span data-stu-id="fc54b-337">The name defines the name of the extension in configuration, whereas the type implements the extension.</span></span> <span data-ttu-id="fc54b-338">延伸有四種型別：</span><span class="sxs-lookup"><span data-stu-id="fc54b-338">There are four types of extensions:</span></span>

- <span data-ttu-id="fc54b-339">繫結延伸可定義整個繫結型別。</span><span class="sxs-lookup"><span data-stu-id="fc54b-339">Binding extensions define an entire binding type.</span></span> <span data-ttu-id="fc54b-340">範例： `basicHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="fc54b-340">Example: `basicHttpBinding`.</span></span>

- <span data-ttu-id="fc54b-341">繫結項目延伸可定義繫結項目。</span><span class="sxs-lookup"><span data-stu-id="fc54b-341">Binding element extensions define an element of a binding.</span></span> <span data-ttu-id="fc54b-342">範例： `textMessageEncoding`.</span><span class="sxs-lookup"><span data-stu-id="fc54b-342">Example: `textMessageEncoding`.</span></span>

- <span data-ttu-id="fc54b-343">標準端點延伸可定義整個標準端點。</span><span class="sxs-lookup"><span data-stu-id="fc54b-343">Standard endpoint extensions define an entire standard endpoint.</span></span> <span data-ttu-id="fc54b-344">範例： `discoveryEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="fc54b-344">Example: `discoveryEndpoint`.</span></span>

- <span data-ttu-id="fc54b-345">行為項目延伸可定義行為項目。</span><span class="sxs-lookup"><span data-stu-id="fc54b-345">Behavior element extensions define an element of a behavior.</span></span> <span data-ttu-id="fc54b-346">範例： `clientVia`.</span><span class="sxs-lookup"><span data-stu-id="fc54b-346">Example: `clientVia`.</span></span>

 <span data-ttu-id="fc54b-347">已經於組態中註冊的擴充功能可比照同類型的任何其他 WCF 元件使用。</span><span class="sxs-lookup"><span data-stu-id="fc54b-347">Extensions that have been registered in configuration can be used like any other WCF component of the same type.</span></span>

##### <a name="adding-a-new-extension"></a><span data-ttu-id="fc54b-348">加入新的延伸</span><span class="sxs-lookup"><span data-stu-id="fc54b-348">Adding a new extension</span></span>

<span data-ttu-id="fc54b-349">在進階節點中選取其中一個延伸節點：</span><span class="sxs-lookup"><span data-stu-id="fc54b-349">Select one of the extension nodes in the advanced nodes:</span></span>

1. <span data-ttu-id="fc54b-350">按一下 **[新增]** 。</span><span class="sxs-lookup"><span data-stu-id="fc54b-350">Click **New**.</span></span>

2. <span data-ttu-id="fc54b-351">輸入名稱和型別。</span><span class="sxs-lookup"><span data-stu-id="fc54b-351">Enter a name and type.</span></span>

3. <span data-ttu-id="fc54b-352">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="fc54b-352">Click **OK**.</span></span>

4. <span data-ttu-id="fc54b-353">擴充功能現在會出現在編輯器的適當位置中。</span><span class="sxs-lookup"><span data-stu-id="fc54b-353">The extension now appears in the appropriate place in the Editor.</span></span> <span data-ttu-id="fc54b-354">例如，如果您新增行為項目延伸，則這個功能會出現在可用延伸清單中。</span><span class="sxs-lookup"><span data-stu-id="fc54b-354">For example, if you add a behavior element extension, it appears in the list of available extensions.</span></span>

#### <a name="hosting-environment"></a><span data-ttu-id="fc54b-355">裝載環境</span><span class="sxs-lookup"><span data-stu-id="fc54b-355">Hosting Environment</span></span>

<span data-ttu-id="fc54b-356">這個區段可讓您定義服務裝載環境的執行個體化設定。</span><span class="sxs-lookup"><span data-stu-id="fc54b-356">This section allows you to define instantiation settings for the service hosting environment.</span></span>

### <a name="creating-a-configuration-file-using-the-wizard"></a><span data-ttu-id="fc54b-357">使用精靈來建立組態檔</span><span class="sxs-lookup"><span data-stu-id="fc54b-357">Creating a Configuration File Using the Wizard</span></span>

<span data-ttu-id="fc54b-358">建立新組態檔的一個方法是使用 [新增服務項目精靈]。</span><span class="sxs-lookup"><span data-stu-id="fc54b-358">One way to create a new configuration file is to use the New Service Element Wizard.</span></span> <span data-ttu-id="fc54b-359">此嚮導會尋找與電腦上的 WCF 相容的已安裝服務類型和其他專案（包括 COM + 和 Web 裝載的虛擬目錄），並載入這些專案，讓建立設定更為簡化。</span><span class="sxs-lookup"><span data-stu-id="fc54b-359">The wizard finds the installed service types and other elements compatible with WCF on the computer, including COM+ and Web-hosted virtual directories, and loads them to make creating the configuration much more streamlined.</span></span>

#### <a name="creating-a-configuration-file"></a><span data-ttu-id="fc54b-360">建立組態檔</span><span class="sxs-lookup"><span data-stu-id="fc54b-360">Creating a Configuration File</span></span>

1. <span data-ttu-id="fc54b-361">使用 [命令] 視窗流覽至您的 WCF 安裝位置，然後輸入，以啟動 [服務設定編輯器] `SvcConfigEditor.exe` 。</span><span class="sxs-lookup"><span data-stu-id="fc54b-361">Start Service Configuration Editor by using a command window to navigate to your WCF installation location, and then type `SvcConfigEditor.exe`.</span></span>

2. <span data-ttu-id="fc54b-362">從 [**檔案] 功能表中**，選取 [**開啟**]，然後按一下 [**可執行**檔]、[ **Com + 服務**] 或 [ **WebHosted 服務**]，視您要建立的配置檔案類型而定。</span><span class="sxs-lookup"><span data-stu-id="fc54b-362">From the **File** menu, select **Open** and click **Executable**, **COM+ Service**, or **WebHosted Service**, depending on the type of configuration file you want to create.</span></span>

3. <span data-ttu-id="fc54b-363">在 [**開啟**] 對話方塊中，流覽至您想要建立設定檔的特定檔案，然後按兩下該檔案。</span><span class="sxs-lookup"><span data-stu-id="fc54b-363">In the **Open** dialog box, navigate to the specific file you want to create a configuration file for and double-click it.</span></span>

4. <span data-ttu-id="fc54b-364">**在 [檔案**] 功能表中，指向 [**加入新專案**]，然後按一下 [**服務**]。</span><span class="sxs-lookup"><span data-stu-id="fc54b-364">In the **File** menu, point to **Add New Item** and click **Service**.</span></span> <span data-ttu-id="fc54b-365">[新增服務項目精靈] 隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="fc54b-365">The New Service Element Wizard opens.</span></span>

5. <span data-ttu-id="fc54b-366">依照精靈中的步驟執行，以建立新服務。</span><span class="sxs-lookup"><span data-stu-id="fc54b-366">Follow the steps in the wizard to create the new service.</span></span>

> [!NOTE]
> <span data-ttu-id="fc54b-367">如果您要從精靈所產生的組態檔中使用 NetPeerTcpBinding，您必須手動新增繫結組態項目，並將其 `mode` 項目的 `security` 屬性修改為 [無]。</span><span class="sxs-lookup"><span data-stu-id="fc54b-367">If you want to use the NetPeerTcpBinding from the configuration file generated by the Wizard, you have to manually add a binding configuration element and modify the `mode` attribute of its `security` element to "None".</span></span>

## <a name="configuring-com"></a><span data-ttu-id="fc54b-368">設定 COM+</span><span class="sxs-lookup"><span data-stu-id="fc54b-368">Configuring COM+</span></span>

<span data-ttu-id="fc54b-369">服務組態編輯器可讓您針對現有的 COM+ 應用程式建立新的組態檔，或是編輯現有的 COM+ 組態。</span><span class="sxs-lookup"><span data-stu-id="fc54b-369">The Service Configuration Editor enables you to create a new configuration file for an existing COM+ application, or edit an existing COM+ configuration.</span></span> <span data-ttu-id="fc54b-370">只有當 <> 區段存在於設定檔中時，才會顯示 [ **COM 合約**] 節點 `comContract` 。</span><span class="sxs-lookup"><span data-stu-id="fc54b-370">The **COM Contract** node is only visible when the <`comContract`> section exists in the configuration file.</span></span>

### <a name="creating-a-new-com-configuration"></a><span data-ttu-id="fc54b-371">建立新 COM+ 組態</span><span class="sxs-lookup"><span data-stu-id="fc54b-371">Creating a New COM+ Configuration</span></span>

<span data-ttu-id="fc54b-372">在建立新的 COM+ 組態之前，請先確定您的 COM+ 應用程式已安裝在 [元件服務] 中，並在 [全域組件快取] (GAC) 中註冊。</span><span class="sxs-lookup"><span data-stu-id="fc54b-372">Before creating a new COM+ configuration, make sure that your COM+ application is installed in Component Services, and registered in the Global Assembly Cache (GAC).</span></span>

1. <span data-ttu-id="fc54b-373">選取 **[** 檔案] 功能表->**整合**  ->  **com + 應用程式]。**</span><span class="sxs-lookup"><span data-stu-id="fc54b-373">Select **File** menu -> **Integrate** -> **COM+ Application.**</span></span> <span data-ttu-id="fc54b-374">這個作業會關閉目前開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="fc54b-374">This operation closes the current opened file.</span></span> <span data-ttu-id="fc54b-375">如果目前檔案中包含未儲存的資料，就會出現 [儲存] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="fc54b-375">If there is unsaved data in the current file, a Save dialog appears.</span></span> <span data-ttu-id="fc54b-376">接著會啟動**Com + 整合嚮導**。</span><span class="sxs-lookup"><span data-stu-id="fc54b-376">The **COM+ Integration Wizard** is then launched.</span></span>

2. <span data-ttu-id="fc54b-377">從第一頁的樹狀目錄中選取 COM+ 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fc54b-377">In the first page, select the COM+ application from the tree.</span></span> <span data-ttu-id="fc54b-378">如果您在樹狀目錄中找不到您的 COM+ 應用程式，請確認該應用程式是否已經安裝在 [元件服務] 中，並且在 [全域組件快取] (GAC) 中註冊。</span><span class="sxs-lookup"><span data-stu-id="fc54b-378">If you cannot find your COM+ application in the tree, verify that it is installed in the Component Services and registered in the Global Assembly Cache (GAC).</span></span>

3. <span data-ttu-id="fc54b-379">在下一頁，選取您要公開為 WCF 服務的方法。</span><span class="sxs-lookup"><span data-stu-id="fc54b-379">In the next page, select which method(s) you want to expose as WCF services.</span></span> <span data-ttu-id="fc54b-380">預設會顯示並選取 COM+ 應用程式支援的所有方法。</span><span class="sxs-lookup"><span data-stu-id="fc54b-380">All the supported methods in the COM+ application are displayed and selected by default.</span></span>

4. <span data-ttu-id="fc54b-381">選擇裝載的方法。</span><span class="sxs-lookup"><span data-stu-id="fc54b-381">Choose a hosting method.</span></span>

5. <span data-ttu-id="fc54b-382">依據精靈中的指示進行其他設定。</span><span class="sxs-lookup"><span data-stu-id="fc54b-382">Configure other settings according to the guides in the wizard.</span></span>

6. <span data-ttu-id="fc54b-383">服務組態編輯器會在背景中使用 ComSvcConfig.exe 來產生組態檔。</span><span class="sxs-lookup"><span data-stu-id="fc54b-383">Service Configuration Editor utilizes ComSvcConfig.exe in the background to generate configuration file.</span></span> <span data-ttu-id="fc54b-384">完成後，您就可以檢視摘要並結束精靈。</span><span class="sxs-lookup"><span data-stu-id="fc54b-384">After this is completed, you can view a summary and exit the wizard.</span></span> <span data-ttu-id="fc54b-385">產生的組態檔隨即開啟，方便您直接進行編輯。</span><span class="sxs-lookup"><span data-stu-id="fc54b-385">The generated configuration file is opened so that you can edit it directly.</span></span>

### <a name="editing-an-existing-com-configuration"></a><span data-ttu-id="fc54b-386">編輯現有的 COM+ 組態</span><span class="sxs-lookup"><span data-stu-id="fc54b-386">Editing an Existing COM+ Configuration</span></span>

1. <span data-ttu-id="fc54b-387">選取 **[** 檔案] 功能表->**開啟**  ->  **com + 服務**.。。</span><span class="sxs-lookup"><span data-stu-id="fc54b-387">Select **File** menu -> **Open** -> **COM+ Service**…</span></span>

2. <span data-ttu-id="fc54b-388">從清單中選取您要編輯的 COM+ 服務。</span><span class="sxs-lookup"><span data-stu-id="fc54b-388">Select the COM+ Service you want to edit from the list.</span></span>

3. <span data-ttu-id="fc54b-389">編輯 [ **COM 合約**] 節點中的設定。</span><span class="sxs-lookup"><span data-stu-id="fc54b-389">Edit configuration settings in the **COM Contracts** node.</span></span>

    > [!NOTE]
    > <span data-ttu-id="fc54b-390">您也可以直接開啟並編輯包含 COM 合約的組態檔。</span><span class="sxs-lookup"><span data-stu-id="fc54b-390">You can also directly open and edit a configuration file that contains COM contracts.</span></span>

## <a name="security"></a><span data-ttu-id="fc54b-391">安全性</span><span class="sxs-lookup"><span data-stu-id="fc54b-391">Security</span></span>

<span data-ttu-id="fc54b-392">不保證組態編輯器產生的服務組態檔是安全的。</span><span class="sxs-lookup"><span data-stu-id="fc54b-392">A service configuration file generated by the Configuration Editor is not guaranteed to be secure.</span></span> <span data-ttu-id="fc54b-393">請參閱[安全性](./feature-details/security.md)檔，以瞭解如何保護您的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="fc54b-393">Please refer to the [Security](./feature-details/security.md) documentation to find out how to secure your WCF services.</span></span>

<span data-ttu-id="fc54b-394">此外，組態編輯器只能用於讀取和寫入有效的 WCF 組態項目。</span><span class="sxs-lookup"><span data-stu-id="fc54b-394">In addition, the Configuration Editor can only be used to read and write valid WCF configuration elements.</span></span> <span data-ttu-id="fc54b-395">該工具會忽略符合結構描述、使用者定義的項目。</span><span class="sxs-lookup"><span data-stu-id="fc54b-395">The tool ignores schema-compliant, user-defined elements.</span></span> <span data-ttu-id="fc54b-396">它也不會嘗試將這些項目從組態檔中移除，或判斷其對已知 WCF 項目的影響。</span><span class="sxs-lookup"><span data-stu-id="fc54b-396">It also does not attempt remove these elements from the configuration file or determine their effects on the known WCF elements.</span></span> <span data-ttu-id="fc54b-397">使用者應負責判斷這些項目是否會對應用程式或系統造成威脅。</span><span class="sxs-lookup"><span data-stu-id="fc54b-397">It is the user’s responsibility to determine whether these elements pose a threat to the application or the system.</span></span>
