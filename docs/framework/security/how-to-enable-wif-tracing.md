---
title: 如何：啟用 WIF 追蹤
ms.date: 03/30/2017
ms.assetid: 271b6889-3454-46ff-96ab-9feb15e742ee
author: BrucePerlerMS
ms.openlocfilehash: 72e22fb5e0358c5f216bfe59d16ad030ce02e0eb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626064"
---
# <a name="how-to-enable-wif-tracing"></a><span data-ttu-id="6f312-102">如何：啟用 WIF 追蹤</span><span class="sxs-lookup"><span data-stu-id="6f312-102">How To: Enable WIF Tracing</span></span>
## <a name="applies-to"></a><span data-ttu-id="6f312-103">適用於</span><span class="sxs-lookup"><span data-stu-id="6f312-103">Applies To</span></span>  
  
- <span data-ttu-id="6f312-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="6f312-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
- <span data-ttu-id="6f312-105">ASP.NET® Web Forms</span><span class="sxs-lookup"><span data-stu-id="6f312-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="6f312-106">總結</span><span class="sxs-lookup"><span data-stu-id="6f312-106">Summary</span></span>  
 <span data-ttu-id="6f312-107">這個操作說明提供了在 ASP.NET 應用程式中啟用 WIF 追蹤的詳細逐步程序。</span><span class="sxs-lookup"><span data-stu-id="6f312-107">This How-To provides detailed step-by-step procedures for enabling WIF tracing in an ASP.NET application.</span></span> <span data-ttu-id="6f312-108">還提供了一些指示，說明如何測試應用程式以確認追蹤接聽項和記錄檔正常運作。</span><span class="sxs-lookup"><span data-stu-id="6f312-108">It also provides instructions testing the application to verify that the trace listener and log are working correctly.</span></span> <span data-ttu-id="6f312-109">這篇使用方法文章並沒有提供建立 Security Token Service (STS) 的詳細指示，而是使用識別和存取工具隨附的「開發 STS」。</span><span class="sxs-lookup"><span data-stu-id="6f312-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and instead uses the Development STS that comes with the Identity and Access tool.</span></span> <span data-ttu-id="6f312-110">「開發 STS」並不會執行實際的驗證，而只是用於測試用途。</span><span class="sxs-lookup"><span data-stu-id="6f312-110">The Development STS does not perform real authentication and is intended for testing purposes only.</span></span> <span data-ttu-id="6f312-111">您必須安裝識別和存取工具才能完成這篇使用方法文章。</span><span class="sxs-lookup"><span data-stu-id="6f312-111">You will need to install the Identity and Access tool to complete this How-To.</span></span> <span data-ttu-id="6f312-112">它可以從下列位置下載：[身分識別和存取工具](https://go.microsoft.com/fwlink/?LinkID=245849)</span><span class="sxs-lookup"><span data-stu-id="6f312-112">It can be downloaded from the following location: [Identity and Access Tool](https://go.microsoft.com/fwlink/?LinkID=245849)</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6f312-113">為被動應用程式 (也就是使用 WS-同盟通訊協定的應用程式) 啟用 WIF 追蹤，可能會使應用程式暴露於阻斷服務 (DoS) 攻擊或洩漏資訊給惡意方的風險下。</span><span class="sxs-lookup"><span data-stu-id="6f312-113">Enabling WIF tracing for passive applications, that is, applications that use the WS-Federation protocol, can potentially expose the application to denial of service (DoS) attacks or to information disclosure to a malicious party.</span></span> <span data-ttu-id="6f312-114">這同時包括被動 RP 和被動 STS。</span><span class="sxs-lookup"><span data-stu-id="6f312-114">This includes both passive RPs and passive STSes.</span></span> <span data-ttu-id="6f312-115">基於這個理由，建議您不要在生產環境中為被動 RP 或 STS 啟用 WIF 追蹤。</span><span class="sxs-lookup"><span data-stu-id="6f312-115">For this reason, we recommend that you not enable WIF tracing for passive RPs or STSes in a production environment.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="6f312-116">內容</span><span class="sxs-lookup"><span data-stu-id="6f312-116">Contents</span></span>  
  
- <span data-ttu-id="6f312-117">目標</span><span class="sxs-lookup"><span data-stu-id="6f312-117">Objectives</span></span>  
  
- <span data-ttu-id="6f312-118">總覽</span><span class="sxs-lookup"><span data-stu-id="6f312-118">Overview</span></span>  
  
- <span data-ttu-id="6f312-119">步驟摘要</span><span class="sxs-lookup"><span data-stu-id="6f312-119">Summary of Steps</span></span>  
  
- <span data-ttu-id="6f312-120">步驟 1 – 建立簡單的 ASP.NET Web Form 應用程式並啟用追蹤</span><span class="sxs-lookup"><span data-stu-id="6f312-120">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Tracing</span></span>  
  
- <span data-ttu-id="6f312-121">步驟 2 – 測試方案</span><span class="sxs-lookup"><span data-stu-id="6f312-121">Step 2 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="6f312-122">目標</span><span class="sxs-lookup"><span data-stu-id="6f312-122">Objectives</span></span>  
  
- <span data-ttu-id="6f312-123">建立從身分識別與存取工具使用 WIF 和開發 STS 的簡單 ASP.NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="6f312-123">Create a simple ASP.NET application that uses WIF and the Development STS from the Identity and Access Tool</span></span>  
  
- <span data-ttu-id="6f312-124">啟用追蹤，並確認它能夠正常運作</span><span class="sxs-lookup"><span data-stu-id="6f312-124">Enable tracing and verify that it is working</span></span>  
  
## <a name="overview"></a><span data-ttu-id="6f312-125">總覽</span><span class="sxs-lookup"><span data-stu-id="6f312-125">Overview</span></span>  
 <span data-ttu-id="6f312-126">追蹤可讓您對 WIF 的許多類型問題進行偵錯和疑難排解，包括權杖、Cookie、宣告、通訊協定訊息等等。</span><span class="sxs-lookup"><span data-stu-id="6f312-126">Tracing enables you to debug and troubleshoot many types of issues with WIF, including tokens, cookies, claims, protocol messages, and more.</span></span> <span data-ttu-id="6f312-127">WIF 追蹤類似於 WCF 追蹤；例如，您可以選擇追蹤的詳細資訊來顯示從重大訊息到所有訊息的一切項目。</span><span class="sxs-lookup"><span data-stu-id="6f312-127">WIF tracing is similar to WCF tracing; for example, you can choose the verbosity of traces to display everything from critical messages to all messages.</span></span> <span data-ttu-id="6f312-128">WIF 追蹤是在 **.xml** 檔案或 **.svclog** 檔案中產生，而您可以使用服務追蹤檢視器工具來檢視這些檔案。</span><span class="sxs-lookup"><span data-stu-id="6f312-128">WIF traces can be generated in **.xml** files or in **.svclog** files that are viewable by using the Service Trace Viewer Tool.</span></span> <span data-ttu-id="6f312-129">此工具位於**bin** Windows SDK 目錄路徑在電腦上安裝，例如：**C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\SvcTraceViewer.exe**.</span><span class="sxs-lookup"><span data-stu-id="6f312-129">This tool is located in the **bin** directory of the Windows SDK install path on your computer, for example: **C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\SvcTraceViewer.exe**.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="6f312-130">步驟摘要</span><span class="sxs-lookup"><span data-stu-id="6f312-130">Summary of Steps</span></span>  
  
- <span data-ttu-id="6f312-131">步驟 1 – 建立簡單的 ASP.NET Web Form 應用程式並啟用追蹤</span><span class="sxs-lookup"><span data-stu-id="6f312-131">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Tracing</span></span>  
  
- <span data-ttu-id="6f312-132">步驟 2 – 測試方案</span><span class="sxs-lookup"><span data-stu-id="6f312-132">Step 2 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-tracing"></a><span data-ttu-id="6f312-133">步驟 1 – 建立簡單的 ASP.NET Web Form 應用程式並啟用追蹤</span><span class="sxs-lookup"><span data-stu-id="6f312-133">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Tracing</span></span>  
 <span data-ttu-id="6f312-134">在此步驟中，您將建立新的 ASP.NET Web Form 應用程式，並修改 *Web.config* 檔案以啟用追蹤。</span><span class="sxs-lookup"><span data-stu-id="6f312-134">In this step, you will create a new ASP.NET Web Forms application and modify the *Web.config* file to enable tracing.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="6f312-135">建立簡單的 ASP.NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="6f312-135">To create a simple ASP.NET application</span></span>  
  
1. <span data-ttu-id="6f312-136">啟動 Visual Studio，並依序按一下 [檔案]、[新增] 和 [專案]。</span><span class="sxs-lookup"><span data-stu-id="6f312-136">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2. <span data-ttu-id="6f312-137">在 [新增專案] 視窗中，按一下 [ASP.NET Web Forms 應用程式]。</span><span class="sxs-lookup"><span data-stu-id="6f312-137">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3. <span data-ttu-id="6f312-138">在 [名稱] 中，輸入 `TestApp`，然後按 [確定]。</span><span class="sxs-lookup"><span data-stu-id="6f312-138">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4. <span data-ttu-id="6f312-139">以滑鼠右鍵按一下方案總管底下的 [TestApp] 專案，然後選取 [身分識別與存取]。</span><span class="sxs-lookup"><span data-stu-id="6f312-139">Right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
5. <span data-ttu-id="6f312-140">[身分識別與存取] 視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="6f312-140">The **Identity and Access** window appears.</span></span> <span data-ttu-id="6f312-141">在 [提供者] 底下，選取 [Test your application with the Local Development STS] (使用本機開發 STS 測試應用程式}，然後按一下 [套用]。</span><span class="sxs-lookup"><span data-stu-id="6f312-141">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
6. <span data-ttu-id="6f312-142">建立新的資料夾中名為**記錄檔**根目錄中的**c:** 磁碟機，例如所示：**C:\logs**</span><span class="sxs-lookup"><span data-stu-id="6f312-142">Create a new folder in named **logs** in the root of the **C:** drive, like shown: **C:\logs**</span></span>  
  
7. <span data-ttu-id="6f312-143">將下列 **\<system.diagnostics>** 元素加入 *Web.config* 組態檔中緊接在 **\</configSections>** 結尾元素後面的位置，如下所示：</span><span class="sxs-lookup"><span data-stu-id="6f312-143">Add the following **\<system.diagnostics>** element to the *Web.config* configuration file immediately following the closing **\</configSections>** element, like shown:</span></span>  
  
    ```xml  
    <configuration>  
        <configSections>  
            ...
        </configSections>  
        <system.diagnostics>  
            <sources>  
                <source name="System.IdentityModel" switchValue="Verbose">  
                    <listeners>  
                        <add name="xml" type="System.Diagnostics.XmlWriterTraceListener" initializeData="C:\logs\WIF.xml" />  
                    </listeners>  
                </source>  
            </sources>  
            <trace autoflush="true" />  
        </system.diagnostics>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="6f312-144">**initializeData** 屬性中指定的目錄位置必須已存在，才能開始進行記錄。</span><span class="sxs-lookup"><span data-stu-id="6f312-144">The directory location specified in the **initializeData** attribute must exist before logging can begin.</span></span> <span data-ttu-id="6f312-145">如果位置不存在，就不會建立任何記錄檔。</span><span class="sxs-lookup"><span data-stu-id="6f312-145">If the location does not exist, no logs will be created.</span></span>  
  
     <span data-ttu-id="6f312-146">上述組態設定會為 WIF 啟用 **Verbose** 追蹤，並將產生的記錄檔儲存到 **C:logsWIF.xml** 檔案。</span><span class="sxs-lookup"><span data-stu-id="6f312-146">The configuration settings above will enable **Verbose** tracing for WIF and save the resulting log to the **C:logsWIF.xml** file.</span></span>  
  
## <a name="step-2--test-your-solution"></a><span data-ttu-id="6f312-147">步驟 2 – 測試方案</span><span class="sxs-lookup"><span data-stu-id="6f312-147">Step 2 – Test Your Solution</span></span>  
 <span data-ttu-id="6f312-148">在此步驟中，您將測試啟用 WIF 的 ASP.NET 應用程式以確認記錄檔會被記錄。</span><span class="sxs-lookup"><span data-stu-id="6f312-148">In this step, you will test your WIF-enabled ASP.NET application to verify that logs are being recorded.</span></span>  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-successful-tracing"></a><span data-ttu-id="6f312-149">測試啟用 WIF 的 ASP.NET 應用程式以成功追蹤</span><span class="sxs-lookup"><span data-stu-id="6f312-149">To test your WIF-enabled ASP.NET application for successful tracing</span></span>  
  
1. <span data-ttu-id="6f312-150">按 **F5** 鍵執行方案。</span><span class="sxs-lookup"><span data-stu-id="6f312-150">Run the solution by pressing the **F5** key.</span></span> <span data-ttu-id="6f312-151">您應該會看到預設的 ASP.NET 首頁，並且會以使用者名稱 *Terry* (這是開發 STS 傳回的預設使用者) 自動進行驗證。</span><span class="sxs-lookup"><span data-stu-id="6f312-151">You should be presented with the default ASP.NET Home Page and automatically authenticated with the username *Terry*, which is the default user that is returned by the Development STS.</span></span>  
  
2. <span data-ttu-id="6f312-152">關閉瀏覽器視窗，然後巡覽至 **C:\logs** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="6f312-152">Close the browser window and then navigate to the **C:\logs** folder.</span></span> <span data-ttu-id="6f312-153">使用文字編輯器開啟 **C:\logs\WIF.xml** 檔案。</span><span class="sxs-lookup"><span data-stu-id="6f312-153">Open the **C:\logs\WIF.xml** file using a text editor.</span></span>  
  
3. <span data-ttu-id="6f312-154">檢查 **WIF.xml** 檔案，並確認其中包含開頭為 **\<E2ETraceEvent>** 的項目。</span><span class="sxs-lookup"><span data-stu-id="6f312-154">Inspect the **WIF.xml** file and verify that it contains entries starting with **\<E2ETraceEvent>**.</span></span> <span data-ttu-id="6f312-155">這些追蹤將包含 **\<TraceRecord>** 元素以及所追蹤之活動的描述，例如**正在驗證 SecurityToken**。</span><span class="sxs-lookup"><span data-stu-id="6f312-155">These traces will contain **\<TraceRecord>** elements with descriptions for the traced activity, such as **Validating SecurityToken**.</span></span>
