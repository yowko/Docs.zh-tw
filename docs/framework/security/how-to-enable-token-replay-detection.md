---
title: 操作說明︰啟用權杖重新執行偵測
ms.date: 03/30/2017
ms.assetid: 5a9f5771-f5f6-4100-8501-406aa20d731a
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: b9c187998b4af41e1a56ed9a64625da7e4f95d5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408056"
---
# <a name="how-to-enable-token-replay-detection"></a><span data-ttu-id="b5ea4-102">操作說明︰啟用權杖重新執行偵測</span><span class="sxs-lookup"><span data-stu-id="b5ea4-102">How To: Enable Token Replay Detection</span></span>
## <a name="applies-to"></a><span data-ttu-id="b5ea4-103">適用於</span><span class="sxs-lookup"><span data-stu-id="b5ea4-103">Applies To</span></span>  
  
-   <span data-ttu-id="b5ea4-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="b5ea4-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="b5ea4-105">ASP.NET® Web Forms</span><span class="sxs-lookup"><span data-stu-id="b5ea4-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="b5ea4-106">總結</span><span class="sxs-lookup"><span data-stu-id="b5ea4-106">Summary</span></span>  
 <span data-ttu-id="b5ea4-107">此操作說明提供了在使用 WIF 的 ASP.NET 應用程式中啟用權杖重新執行偵測的詳細逐步程序。</span><span class="sxs-lookup"><span data-stu-id="b5ea4-107">This How-To provides detailed step-by-step procedures for enabling token replay detection in an ASP.NET application that uses WIF.</span></span> <span data-ttu-id="b5ea4-108">還提供了一些指示，說明如何測試應用程式來確認已啟用權杖重新執行偵測。</span><span class="sxs-lookup"><span data-stu-id="b5ea4-108">It also provides instructions for how to test the application to verify that token replay detection is enabled.</span></span> <span data-ttu-id="b5ea4-109">這篇使用方法文章並沒有提供建立 Security Token Service (STS) 的詳細指示，而是使用識別和存取工具隨附的「開發 STS」。</span><span class="sxs-lookup"><span data-stu-id="b5ea4-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and instead uses the Development STS that comes with the Identity and Access tool.</span></span> <span data-ttu-id="b5ea4-110">「開發 STS」並不會執行實際的驗證，而只是用於測試用途。</span><span class="sxs-lookup"><span data-stu-id="b5ea4-110">The Development STS does not perform real authentication and is intended for testing purposes only.</span></span> <span data-ttu-id="b5ea4-111">您必須安裝識別和存取工具才能完成這篇使用方法文章。</span><span class="sxs-lookup"><span data-stu-id="b5ea4-111">You will need to install the Identity and Access tool to complete this How-To.</span></span> <span data-ttu-id="b5ea4-112">您可以從下列位置下載：[Identity and Access Tool](http://go.microsoft.com/fwlink/?LinkID=245849) (身分識別與存取工具)</span><span class="sxs-lookup"><span data-stu-id="b5ea4-112">It can be downloaded from the following location: [Identity and Access Tool](http://go.microsoft.com/fwlink/?LinkID=245849)</span></span>  
  
## <a name="contents"></a><span data-ttu-id="b5ea4-113">內容</span><span class="sxs-lookup"><span data-stu-id="b5ea4-113">Contents</span></span>  
  
-   <span data-ttu-id="b5ea4-114">目標</span><span class="sxs-lookup"><span data-stu-id="b5ea4-114">Objectives</span></span>  
  
-   <span data-ttu-id="b5ea4-115">總覽</span><span class="sxs-lookup"><span data-stu-id="b5ea4-115">Overview</span></span>  
  
-   <span data-ttu-id="b5ea4-116">步驟摘要</span><span class="sxs-lookup"><span data-stu-id="b5ea4-116">Summary of Steps</span></span>  
  
-   <span data-ttu-id="b5ea4-117">步驟 1 – 建立簡單的 ASP.NET Web Forms 應用程式並啟用重新執行偵測</span><span class="sxs-lookup"><span data-stu-id="b5ea4-117">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Replay Detection</span></span>  
  
-   <span data-ttu-id="b5ea4-118">步驟 2 – 測試方案</span><span class="sxs-lookup"><span data-stu-id="b5ea4-118">Step 2 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="b5ea4-119">目標</span><span class="sxs-lookup"><span data-stu-id="b5ea4-119">Objectives</span></span>  
  
-   <span data-ttu-id="b5ea4-120">建立從身分識別與存取工具使用 WIF 和開發 STS 的簡單 ASP.NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="b5ea4-120">Create a simple ASP.NET application that uses WIF and the Development STS from the Identity and Access Tool</span></span>  
  
-   <span data-ttu-id="b5ea4-121">啟用權杖重新執行偵測，並確認它能夠正常運作</span><span class="sxs-lookup"><span data-stu-id="b5ea4-121">Enable token replay detection and verify that it is working</span></span>  
  
## <a name="overview"></a><span data-ttu-id="b5ea4-122">總覽</span><span class="sxs-lookup"><span data-stu-id="b5ea4-122">Overview</span></span>  
 <span data-ttu-id="b5ea4-123">當用戶端嘗試以用戶端已使用之 STS 權杖向信賴憑證者進行驗證時，就會發生重新執行攻擊。</span><span class="sxs-lookup"><span data-stu-id="b5ea4-123">A replay attack occurs when a client attempts to authenticate to a relying party with an STS token that the client has already used.</span></span> <span data-ttu-id="b5ea4-124">為了協助避免這種攻擊，WIF 會包含先前所使用之 STS 權杖的重新執行偵測快取。</span><span class="sxs-lookup"><span data-stu-id="b5ea4-124">To help prevent this attack, WIF contains a replay detection cache of previously used STS tokens.</span></span> <span data-ttu-id="b5ea4-125">啟用時，重新執行偵測會檢查傳入要求的權杖，並確認先前是否已使用該權杖。</span><span class="sxs-lookup"><span data-stu-id="b5ea4-125">When enabled, replay detection checks the token of the incoming request and verifies whether or not the token has been previously used.</span></span> <span data-ttu-id="b5ea4-126">如果已使用該權杖，就會拒絕要求並擲回 <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b5ea4-126">If the token has been used already, the request is refused and a <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> exception is thrown.</span></span>  
  
 <span data-ttu-id="b5ea4-127">下列步驟示範啟用重新執行偵測所需的組態變更。</span><span class="sxs-lookup"><span data-stu-id="b5ea4-127">The following steps demonstrate the configuration changes required to enable replay detection.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="b5ea4-128">步驟摘要</span><span class="sxs-lookup"><span data-stu-id="b5ea4-128">Summary of Steps</span></span>  
  
-   <span data-ttu-id="b5ea4-129">步驟 1 – 建立簡單的 ASP.NET Web Forms 應用程式並啟用重新執行偵測</span><span class="sxs-lookup"><span data-stu-id="b5ea4-129">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Replay Detection</span></span>  
  
-   <span data-ttu-id="b5ea4-130">步驟 2 – 測試方案</span><span class="sxs-lookup"><span data-stu-id="b5ea4-130">Step 2 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-replay-detection"></a><span data-ttu-id="b5ea4-131">步驟 1 – 建立簡單的 ASP.NET Web Forms 應用程式並啟用重新執行偵測</span><span class="sxs-lookup"><span data-stu-id="b5ea4-131">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Replay Detection</span></span>  
 <span data-ttu-id="b5ea4-132">在此步驟中，您將建立新的 ASP.NET Web Forms 應用程式，並修改 *Web.config* 檔案以啟用重新執行偵測。</span><span class="sxs-lookup"><span data-stu-id="b5ea4-132">In this step, you will create a new ASP.NET Web Forms application and modify the *Web.config* file to enable replay detection.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="b5ea4-133">建立簡單的 ASP.NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="b5ea4-133">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="b5ea4-134">啟動 Visual Studio，並依序按一下 [檔案]、[新增] 和 [專案]。</span><span class="sxs-lookup"><span data-stu-id="b5ea4-134">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="b5ea4-135">在 [新增專案] 視窗中，按一下 [ASP.NET Web Forms 應用程式]。</span><span class="sxs-lookup"><span data-stu-id="b5ea4-135">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="b5ea4-136">在 [名稱] 中，輸入 `TestApp`，然後按 [確定]。</span><span class="sxs-lookup"><span data-stu-id="b5ea4-136">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4.  <span data-ttu-id="b5ea4-137">以滑鼠右鍵按一下方案總管底下的 [TestApp] 專案，然後選取 [身分識別與存取]。</span><span class="sxs-lookup"><span data-stu-id="b5ea4-137">Right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
5.  <span data-ttu-id="b5ea4-138">[身分識別與存取] 視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="b5ea4-138">The **Identity and Access** window appears.</span></span> <span data-ttu-id="b5ea4-139">在 [提供者] 底下，選取 [Test your application with the Local Development STS] (使用本機開發 STS 測試應用程式}，然後按一下 [套用]。</span><span class="sxs-lookup"><span data-stu-id="b5ea4-139">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
6.  <span data-ttu-id="b5ea4-140">將下列 **\<tokenReplayDetection>** 項目加入至 *Web.config* 組態檔中緊接在 **\<system.identityModel>** 和**\<identityConfiguration>** 項目後面的位置，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b5ea4-140">Add the following **\<tokenReplayDetection>** element to the *Web.config* configuration file immediately following the **\<system.identityModel>** and **\<identityConfiguration>** elements, like shown:</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <tokenReplayDetection enabled="true"/>  
    ```  
  
## <a name="step-2--test-your-solution"></a><span data-ttu-id="b5ea4-141">步驟 2 – 測試方案</span><span class="sxs-lookup"><span data-stu-id="b5ea4-141">Step 2 – Test Your Solution</span></span>  
 <span data-ttu-id="b5ea4-142">在此步驟中，您將測試啟用 WIF 的 ASP.NET 應用程式來確認已啟用重新執行偵測。</span><span class="sxs-lookup"><span data-stu-id="b5ea4-142">In this step, you will test your WIF-enabled ASP.NET application to verify that replay detection has been enabled.</span></span>  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-replay-detection"></a><span data-ttu-id="b5ea4-143">測試啟用 WIF 的 ASP.NET 應用程式的重新執行偵測</span><span class="sxs-lookup"><span data-stu-id="b5ea4-143">To test your WIF-enabled ASP.NET application for replay detection</span></span>  
  
1.  <span data-ttu-id="b5ea4-144">按 **F5** 鍵執行方案。</span><span class="sxs-lookup"><span data-stu-id="b5ea4-144">Run the solution by pressing the **F5** key.</span></span> <span data-ttu-id="b5ea4-145">您應該會看到預設的 ASP.NET 首頁，並且會以使用者名稱 *Terry* (這是開發 STS 傳回的預設使用者) 自動進行驗證。</span><span class="sxs-lookup"><span data-stu-id="b5ea4-145">You should be presented with the default ASP.NET Home Page and automatically authenticated with the username *Terry*, which is the default user that is returned by the Development STS.</span></span>  
  
2.  <span data-ttu-id="b5ea4-146">請按瀏覽器的**上一頁**按鈕。</span><span class="sxs-lookup"><span data-stu-id="b5ea4-146">Press the browser’s **Back** button.</span></span> <span data-ttu-id="b5ea4-147">您應該會看到 **Server Error in ‘/’ Application** 頁面以及下列描述：*ID1062: Replay has been detected for: Token: 'System.IdentityModel.Tokens.SamlSecurityToken'*，後面接著 *AssertionId* 和 *Issuer*。</span><span class="sxs-lookup"><span data-stu-id="b5ea4-147">You should be presented with a **Server Error in ‘/’ Application** page with the following description: *ID1062: Replay has been detected for: Token: 'System.IdentityModel.Tokens.SamlSecurityToken'*, followed by an *AssertionId* and an *Issuer*.</span></span>  
  
     <span data-ttu-id="b5ea4-148">因為在偵測到權杖重新執行時，會擲回 <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> 類型的例外狀況，所以您會看到此錯誤頁面。</span><span class="sxs-lookup"><span data-stu-id="b5ea4-148">You are seeing this error page because an exception of type <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> was thrown when the token replay was detected.</span></span> <span data-ttu-id="b5ea4-149">發生此錯誤的原因是您在權杖第一次出現時，嘗試重新傳送初始 POST 要求。</span><span class="sxs-lookup"><span data-stu-id="b5ea4-149">This error occurs because you are attempting to re-send the initial POST request when the token was first presented.</span></span> <span data-ttu-id="b5ea4-150">**上一頁**按鈕不會造成後續的伺服器要求發生這種行為。</span><span class="sxs-lookup"><span data-stu-id="b5ea4-150">The **Back** button will not cause this behavior on subsequent requests to the server.</span></span>
