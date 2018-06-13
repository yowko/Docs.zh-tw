---
title: 聯合範例
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: a9c2b91f7d8bdf24476c76fcd479b7f2fb44c90f
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806844"
---
# <a name="federation-sample"></a><span data-ttu-id="5654d-102">聯合範例</span><span class="sxs-lookup"><span data-stu-id="5654d-102">Federation Sample</span></span>
<span data-ttu-id="5654d-103">這個範例將示範聯合安全性。</span><span class="sxs-lookup"><span data-stu-id="5654d-103">This sample demonstrates federated security.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="5654d-104">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="5654d-104">Sample Details</span></span>  
 <span data-ttu-id="5654d-105">Windows Communication Foundation (WCF) 提供支援部署聯合的安全性架構透過`wsFederationHttpBinding`。</span><span class="sxs-lookup"><span data-stu-id="5654d-105">Windows Communication Foundation (WCF) provides support for deploying federated security architectures through the `wsFederationHttpBinding`.</span></span> <span data-ttu-id="5654d-106">`wsFederationHttpBinding` 提供安全、可靠以及可互通的繫結，其中包括使用 HTTP 做為要求/回覆通訊的基礎傳輸機制，以及採用文字/XML 做為編碼的 Wire 格式。</span><span class="sxs-lookup"><span data-stu-id="5654d-106">The `wsFederationHttpBinding` provides a secure, reliable, and interoperable binding that involves the use of HTTP as the underlying transport mechanism for request/reply communication, and Text/XML as the wire format for encoding.</span></span> <span data-ttu-id="5654d-107">如需在 WCF 中的同盟的詳細資訊，請參閱[同盟](../../../../docs/framework/wcf/feature-details/federation.md)。</span><span class="sxs-lookup"><span data-stu-id="5654d-107">For more information about Federation in WCF, see [Federation](../../../../docs/framework/wcf/feature-details/federation.md).</span></span>  
  
 <span data-ttu-id="5654d-108">本案例由 4 個部分組成：</span><span class="sxs-lookup"><span data-stu-id="5654d-108">The scenario is made up of 4 pieces:</span></span>  
  
-   <span data-ttu-id="5654d-109">BookStore 服務</span><span class="sxs-lookup"><span data-stu-id="5654d-109">BookStore service</span></span>  
  
-   <span data-ttu-id="5654d-110">BookStore STS</span><span class="sxs-lookup"><span data-stu-id="5654d-110">BookStore STS</span></span>  
  
-   <span data-ttu-id="5654d-111">HomeRealm STS</span><span class="sxs-lookup"><span data-stu-id="5654d-111">HomeRealm STS</span></span>  
  
-   <span data-ttu-id="5654d-112">BookStore 用戶端</span><span class="sxs-lookup"><span data-stu-id="5654d-112">BookStore Client</span></span>  
  
 <span data-ttu-id="5654d-113">BookStore 服務支援兩項作業：`BrowseBooks` 和 `BuyBook`。</span><span class="sxs-lookup"><span data-stu-id="5654d-113">The BookStore service supports two operations, `BrowseBooks` and `BuyBook`.</span></span> <span data-ttu-id="5654d-114">它允許匿名存取 `BrowseBooks` 作業，但是要求必須有通過驗證的存取權才能存取 `BuyBooks` 作業。</span><span class="sxs-lookup"><span data-stu-id="5654d-114">It allows anonymous access to the `BrowseBooks` operation, but requires authenticated access to access the `BuyBooks` operation.</span></span> <span data-ttu-id="5654d-115">驗證的形式採用 BookStore STS 所發行的權杖。</span><span class="sxs-lookup"><span data-stu-id="5654d-115">The authentication takes the form of a token issued by the BookStore STS.</span></span> <span data-ttu-id="5654d-116">BookStore 服務的組態檔會使用 `wsFederationHttpBinding`，將用戶端指向 BookStore STS。</span><span class="sxs-lookup"><span data-stu-id="5654d-116">The configuration file for the BookStore Service points clients to the BookStore STS using the `wsFederationHttpBinding`.</span></span>  
  
```xml  
<wsFederationHttpBinding>  
<!-- This is the Service binding for the BuyBooks endpoint. It redirects clients to the BookStore STS -->  
    <binding name='BuyBookBinding'>  
        <security mode="Message">  
            <message>  
                <issuerMetadata  
  address='http://localhost/FederationSample/BookStoreSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='BookStoreSTS.com'/>  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 <span data-ttu-id="5654d-117">BookStore STS 接著會要求用戶端使用 HomeRealm STS 所發行的權杖進行驗證。</span><span class="sxs-lookup"><span data-stu-id="5654d-117">The BookStore STS then requires that clients authenticate using a token issued by the HomeRealm STS.</span></span> <span data-ttu-id="5654d-118">同樣地，BookStore STS 的組態檔也會使用 `wsFederationHttpBinding`，將用戶端指向 HomeRealm STS。</span><span class="sxs-lookup"><span data-stu-id="5654d-118">Again, the configuration file for the BookStore STS points clients to the HomeRealm STS using the `wsFederationHttpBinding`.</span></span>  
  
```xml  
<wsFederationHttpBinding>  
 <!-- This is the binding for the clients requesting tokens from this STS. It redirects clients to the HomeRealm STS -->  
    <binding name='BookStoreSTSBinding'>  
        <security mode='Message'>  
            <message>  
                <issuerMetadata  
 address='http://localhost/FederationSample/HomeRealmSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='HomeRealmSTS.com' />  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 <span data-ttu-id="5654d-119">在存取 `BuyBook` 作業時，事件的順序如下：</span><span class="sxs-lookup"><span data-stu-id="5654d-119">The sequence of events when accessing the `BuyBook` operation is as follows:</span></span>  
  
1.  <span data-ttu-id="5654d-120">用戶端使用 Windows 認證，向 HomeRealm STS 驗證。</span><span class="sxs-lookup"><span data-stu-id="5654d-120">The client authenticates to the HomeRealm STS using Windows credentials.</span></span>  
  
2.  <span data-ttu-id="5654d-121">HomeRealm STS 發行可用來向 BookStore STS 進行驗證的權杖。</span><span class="sxs-lookup"><span data-stu-id="5654d-121">The HomeRealm STS issues a token that can be used to authenticate to the BookStore STS.</span></span>  
  
3.  <span data-ttu-id="5654d-122">用戶端使用 HomeRealm STS 所發行的權杖，向 BookStore STS 驗證。</span><span class="sxs-lookup"><span data-stu-id="5654d-122">The client authenticates to the BookStore STS using the token issued by the HomeRealm STS.</span></span>  
  
4.  <span data-ttu-id="5654d-123">BookStore STS 發行可用來向 BookStore 服務進行驗證的權杖。</span><span class="sxs-lookup"><span data-stu-id="5654d-123">The BookStore STS issues a token that can be used to authenticate to the BookStore Service.</span></span>  
  
5.  <span data-ttu-id="5654d-124">用戶端使用 BookStore STS 所發行的權杖，向 BookStore 服務驗證。</span><span class="sxs-lookup"><span data-stu-id="5654d-124">The client authenticates to the BookStore service using the token issued by the BookStore STS.</span></span>  
  
6.  <span data-ttu-id="5654d-125">用戶端會存取 `BuyBook` 作業。</span><span class="sxs-lookup"><span data-stu-id="5654d-125">The client accesses the `BuyBook` operation.</span></span>  
  
 <span data-ttu-id="5654d-126">請參閱下列指示，以了解如何安裝和執行這個範例。</span><span class="sxs-lookup"><span data-stu-id="5654d-126">See the following instructions about how to set up and run this sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5654d-127">您必須擁有寫入權限**wwwroot**才能執行此範例的目錄。</span><span class="sxs-lookup"><span data-stu-id="5654d-127">You must have Write permissions to the **wwwroot** directory to run this sample.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5654d-128">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="5654d-128">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="5654d-129">開啟 SDK 命令視窗。</span><span class="sxs-lookup"><span data-stu-id="5654d-129">Open the SDK command window.</span></span> <span data-ttu-id="5654d-130">在範例的路徑中，執行 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="5654d-130">In the sample path, run Setup.bat.</span></span> <span data-ttu-id="5654d-131">這會建立範例所需的虛擬目錄，並安裝具有適當權限的必要憑證。</span><span class="sxs-lookup"><span data-stu-id="5654d-131">This creates the virtual directories required for the sample and installs the required certificates with appropriate permissions.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5654d-132">Setup.bat 批次檔是設計用來從 Windows SDK 命令提示字元執行。</span><span class="sxs-lookup"><span data-stu-id="5654d-132">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="5654d-133">它要求 MSSDK 環境變數指向安裝 SDK 的目錄。</span><span class="sxs-lookup"><span data-stu-id="5654d-133">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="5654d-134">這個環境變數是自動在 Windows SDK 命令提示字元中設定。</span><span class="sxs-lookup"><span data-stu-id="5654d-134">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span> <span data-ttu-id="5654d-135">在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上，您必須確定已安裝 IIS 6.0 管理相容性，因為安裝會使用 IIS 系統管理員指令碼。</span><span class="sxs-lookup"><span data-stu-id="5654d-135">On [!INCLUDE[wv](../../../../includes/wv-md.md)], you must ensure that IIS 6.0 Management Compatibility is installed because the set up uses IIS administrator scripts.</span></span> <span data-ttu-id="5654d-136">在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上執行安裝指令碼時，需要系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="5654d-136">Running the set-up script on [!INCLUDE[wv](../../../../includes/wv-md.md)] requires administrator privileges.</span></span>  
  
2.  <span data-ttu-id="5654d-137">在 Visual Studio 中開啟 FederationSample.sln，然後選取**建置方案**從**建置**功能表。</span><span class="sxs-lookup"><span data-stu-id="5654d-137">Open FederationSample.sln in Visual Studio and select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="5654d-138">這會建置通用專案檔、Bookstore 服務、Bookstore STS、HomeRealm STS，然後將它們部署在 IIS 中。</span><span class="sxs-lookup"><span data-stu-id="5654d-138">This builds the common project files, Bookstore service, Bookstore STS, HomeRealm STS, and deploys them in IIS.</span></span> <span data-ttu-id="5654d-139">還會建置 Bookstore 用戶端應用程式，並將可執行檔 BookStoreClient.exe 放置在 FederationSample\BookStoreClient\bin\Debug 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="5654d-139">This also builds the Bookstore client application and places the executable BookStoreClient.exe in the FederationSample\BookStoreClient\bin\Debug folder.</span></span>  
  
3.  <span data-ttu-id="5654d-140">按兩下 BookStoreClient.exe。</span><span class="sxs-lookup"><span data-stu-id="5654d-140">Double-click BookStoreClient.exe.</span></span> <span data-ttu-id="5654d-141">BookStoreClient 視窗隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="5654d-141">The BookStoreClient window is displayed.</span></span>  
  
4.  <span data-ttu-id="5654d-142">您可以按一下瀏覽書店中的書籍**瀏覽書籍**。</span><span class="sxs-lookup"><span data-stu-id="5654d-142">You can browse the books available in the bookstore by clicking **Browse Books**.</span></span>  
  
5.  <span data-ttu-id="5654d-143">若要購買特定書籍，在清單中選取活頁簿，然後按一下**購買書籍**。</span><span class="sxs-lookup"><span data-stu-id="5654d-143">To purchase a particular book, select the book in the list and click **Buy Book**.</span></span> <span data-ttu-id="5654d-144">應用程式隨即啟動，然後會使用 Windows 驗證向 HomeRealm 安全性權杖服務進行驗證。</span><span class="sxs-lookup"><span data-stu-id="5654d-144">The application starts up and authenticates using Windows authentication with the HomeRealm Security Token Service.</span></span>  
  
     <span data-ttu-id="5654d-145">此範例已設定為允許使用者購買價值在 $15 (含) 以下的書籍。</span><span class="sxs-lookup"><span data-stu-id="5654d-145">The sample is configured to allow users to purchase books that cost $15 or less.</span></span> <span data-ttu-id="5654d-146">嘗試購買價值超過 15 美元的書籍，會導致用戶端從「書店服務」(Book Store Service) 收到「拒絕存取」訊息。</span><span class="sxs-lookup"><span data-stu-id="5654d-146">Attempting to buy books that cost more than $15 results in the client getting an Access Denied message from the Book Store Service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5654d-147">此範例不會在使用者購買之後更新其信用額度限制。</span><span class="sxs-lookup"><span data-stu-id="5654d-147">The sample does not update the user’s credit limit after a purchase.</span></span> <span data-ttu-id="5654d-148">您可以在使用者的 (固定) 信用額度限制以內重複購買書籍。</span><span class="sxs-lookup"><span data-stu-id="5654d-148">You can repeatedly purchase books within the user’s (fixed) credit limit.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="5654d-149">若要清除</span><span class="sxs-lookup"><span data-stu-id="5654d-149">To clean up</span></span>  
  
1.  <span data-ttu-id="5654d-150">執行 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="5654d-150">Run Cleanup.bat.</span></span> <span data-ttu-id="5654d-151">這會刪除安裝期間建立的虛擬目錄，也會移除安裝期間所安裝的憑證。</span><span class="sxs-lookup"><span data-stu-id="5654d-151">This deletes the virtual directories that were created during set up and also removes the certificates installed during setup.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5654d-152">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="5654d-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5654d-153">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="5654d-153">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5654d-154">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="5654d-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5654d-155">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="5654d-155">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
  
## <a name="see-also"></a><span data-ttu-id="5654d-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5654d-156">See Also</span></span>
