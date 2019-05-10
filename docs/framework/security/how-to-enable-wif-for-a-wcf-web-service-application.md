---
title: 如何：啟用 WCF Web 服務應用程式的 WIF
ms.date: 03/30/2017
ms.assetid: bfc64b3d-64e9-4093-a6a4-72e933917af7
author: BrucePerlerMS
ms.openlocfilehash: 4f67ddc7b61c5c127c7fcbe888454e0a4aa36539
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626080"
---
# <a name="how-to-enable-wif-for-a-wcf-web-service-application"></a><span data-ttu-id="4a92d-102">如何：啟用 WCF Web 服務應用程式的 WIF</span><span class="sxs-lookup"><span data-stu-id="4a92d-102">How To: Enable WIF for a WCF Web Service Application</span></span>
## <a name="applies-to"></a><span data-ttu-id="4a92d-103">適用於</span><span class="sxs-lookup"><span data-stu-id="4a92d-103">Applies To</span></span>  
  
- <span data-ttu-id="4a92d-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="4a92d-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
- <span data-ttu-id="4a92d-105">Microsoft® Windows® Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="4a92d-105">Microsoft® Windows® Communication Foundation (WCF)</span></span>  
  
## <a name="summary"></a><span data-ttu-id="4a92d-106">總結</span><span class="sxs-lookup"><span data-stu-id="4a92d-106">Summary</span></span>  
 <span data-ttu-id="4a92d-107">這篇使用方法文章提供了在 WCF Web 服務中啟用 WIF 的詳細逐步程序。</span><span class="sxs-lookup"><span data-stu-id="4a92d-107">This How-To provides detailed step-by-step procedures for enabling WIF in a WCF web service.</span></span> <span data-ttu-id="4a92d-108">此外，它還提供如何測試應用程式以確認應用程式執行時 Web 服務可正確提出宣告的指示。</span><span class="sxs-lookup"><span data-stu-id="4a92d-108">It also provides instructions for how to test the application to verify that the web service is correctly presenting claims when the application is run.</span></span> <span data-ttu-id="4a92d-109">這篇使用方法文章並沒有提供建立 Security Token Service (STS) 的詳細指示，而是使用識別和存取工具隨附的「開發 STS」。</span><span class="sxs-lookup"><span data-stu-id="4a92d-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and instead uses the Development STS that comes with the Identity and Access tool.</span></span> <span data-ttu-id="4a92d-110">「開發 STS」並不會執行實際的驗證，而只是用於測試用途。</span><span class="sxs-lookup"><span data-stu-id="4a92d-110">The Development STS does not perform real authentication and is intended for testing purposes only.</span></span> <span data-ttu-id="4a92d-111">您必須安裝識別和存取工具才能完成這篇使用方法文章。</span><span class="sxs-lookup"><span data-stu-id="4a92d-111">You will need to install the Identity and Access tool to complete this How-To.</span></span> <span data-ttu-id="4a92d-112">它可以從下列位置下載：[身分識別和存取工具](https://go.microsoft.com/fwlink/?LinkID=245849)</span><span class="sxs-lookup"><span data-stu-id="4a92d-112">It can be downloaded from the following location: [Identity and Access Tool](https://go.microsoft.com/fwlink/?LinkID=245849)</span></span>  
  
## <a name="contents"></a><span data-ttu-id="4a92d-113">內容</span><span class="sxs-lookup"><span data-stu-id="4a92d-113">Contents</span></span>  
  
- <span data-ttu-id="4a92d-114">目標</span><span class="sxs-lookup"><span data-stu-id="4a92d-114">Objectives</span></span>  
  
- <span data-ttu-id="4a92d-115">總覽</span><span class="sxs-lookup"><span data-stu-id="4a92d-115">Overview</span></span>  
  
- <span data-ttu-id="4a92d-116">步驟摘要</span><span class="sxs-lookup"><span data-stu-id="4a92d-116">Summary of Steps</span></span>  
  
- <span data-ttu-id="4a92d-117">步驟 1 – 建立簡單的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="4a92d-117">Step 1 – Create a Simple WCF Service</span></span>  
  
- <span data-ttu-id="4a92d-118">步驟 2 – 建立 WCF 服務的用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="4a92d-118">Step 2 – Create a Client Application for the WCF Service</span></span>  
  
- <span data-ttu-id="4a92d-119">步驟 3 – 測試方案</span><span class="sxs-lookup"><span data-stu-id="4a92d-119">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="4a92d-120">目標</span><span class="sxs-lookup"><span data-stu-id="4a92d-120">Objectives</span></span>  
  
- <span data-ttu-id="4a92d-121">建立必須使用已發行權杖的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="4a92d-121">Create a WCF service that requires issued tokens</span></span>  
  
- <span data-ttu-id="4a92d-122">建立會從 STS 要求權杖並將它傳遞至 WCF 服務的 WCF 用戶端</span><span class="sxs-lookup"><span data-stu-id="4a92d-122">Create a WCF client that requests a token from an STS and passes it to the WCF service</span></span>  
  
## <a name="overview"></a><span data-ttu-id="4a92d-123">總覽</span><span class="sxs-lookup"><span data-stu-id="4a92d-123">Overview</span></span>  
 <span data-ttu-id="4a92d-124">這篇使用方法文章的目的是要示範開發人員如何在開發 WCF 服務時使用同盟驗證。</span><span class="sxs-lookup"><span data-stu-id="4a92d-124">This How-To is intended to demonstrate how a developer can use federated authentication when developing WCF services.</span></span> <span data-ttu-id="4a92d-125">在 WCF 服務中使用同盟的其中一些優點包括：</span><span class="sxs-lookup"><span data-stu-id="4a92d-125">Some of the benefits of using federation in WCF services include:</span></span>  
  
1. <span data-ttu-id="4a92d-126">將驗證邏輯排除在 WCF 服務程式碼外</span><span class="sxs-lookup"><span data-stu-id="4a92d-126">Factoring authentication logic out of WCF service code</span></span>  
  
2. <span data-ttu-id="4a92d-127">重複使用現有的身分識別管理方案</span><span class="sxs-lookup"><span data-stu-id="4a92d-127">Re-using existing identity management solutions</span></span>  
  
3. <span data-ttu-id="4a92d-128">與其他識別方案的互通性</span><span class="sxs-lookup"><span data-stu-id="4a92d-128">Interoperability with other identity solutions</span></span>  
  
4. <span data-ttu-id="4a92d-129">未來變更的靈活性和彈性</span><span class="sxs-lookup"><span data-stu-id="4a92d-129">Flexibility and resilience to future changes</span></span>  
  
 <span data-ttu-id="4a92d-130">WIF 與相關聯的識別和存取工具可讓您使用同盟驗證更輕鬆地開發及測試 WCF 服務，如下面步驟所示。</span><span class="sxs-lookup"><span data-stu-id="4a92d-130">WIF and the associated Identity and Access tool make it easier to develop and test a WCF service using federated authentication, as the following steps demonstrate.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="4a92d-131">步驟摘要</span><span class="sxs-lookup"><span data-stu-id="4a92d-131">Summary of Steps</span></span>  
  
- <span data-ttu-id="4a92d-132">步驟 1 – 建立簡單的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="4a92d-132">Step 1 – Create a Simple WCF Service</span></span>  
  
- <span data-ttu-id="4a92d-133">步驟 2 – 建立 WCF 服務的用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="4a92d-133">Step 2 – Create a Client Application for the WCF Service</span></span>  
  
- <span data-ttu-id="4a92d-134">步驟 3 – 測試方案</span><span class="sxs-lookup"><span data-stu-id="4a92d-134">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-wcf-service"></a><span data-ttu-id="4a92d-135">步驟 1 – 建立簡單的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="4a92d-135">Step 1 – Create a Simple WCF Service</span></span>  
 <span data-ttu-id="4a92d-136">在這個步驟中，您要建立一個新的 WCF 服務，該服務使用識別和存取工具所隨附的「開發 STS」。</span><span class="sxs-lookup"><span data-stu-id="4a92d-136">In this step, you will create a new WCF service that uses the Development STS that is included with the Identity and Access tool.</span></span>  
  
#### <a name="to-create-a-simple-wcf-service"></a><span data-ttu-id="4a92d-137">若要建立簡單的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="4a92d-137">To create a simple WCF service</span></span>  
  
1. <span data-ttu-id="4a92d-138">以系統管理員身分的高階權限模式來啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="4a92d-138">Start Visual Studio in elevated mode as administrator.</span></span>  
  
2. <span data-ttu-id="4a92d-139">在 Visual Studio 中，依序按一下 [檔案]、[新增] 和 [專案]。</span><span class="sxs-lookup"><span data-stu-id="4a92d-139">In Visual Studio, click **File**, click **New**, and then click **Project**.</span></span>  
  
3. <span data-ttu-id="4a92d-140">在 [新增專案] 視窗中，按一下 [WCF 服務應用程式]。</span><span class="sxs-lookup"><span data-stu-id="4a92d-140">In the **New Project** window, click **WCF Service Application**.</span></span>  
  
4. <span data-ttu-id="4a92d-141">在 [名稱] 中，輸入 `TestService`，然後按 [確定]。</span><span class="sxs-lookup"><span data-stu-id="4a92d-141">In **Name**, enter `TestService` and press **OK**.</span></span>  
  
5. <span data-ttu-id="4a92d-142">以滑鼠右鍵按一下方案總管 底下的 [TestService]，然後選取 [身分識別與存取]。</span><span class="sxs-lookup"><span data-stu-id="4a92d-142">Right-click the **TestService** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
6. <span data-ttu-id="4a92d-143">[身分識別與存取] 視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="4a92d-143">The **Identity and Access** window appears.</span></span> <span data-ttu-id="4a92d-144">在 [提供者] 底下，選取 [使用本機開發 STS 測試應用程式]，然後按一下 [套用]。</span><span class="sxs-lookup"><span data-stu-id="4a92d-144">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span> <span data-ttu-id="4a92d-145">身分識別與存取工具會在 *Web.config* 檔案中新增組態項目，藉以設定服務使用 WIF，並將驗證外包給本機開發 STS (**LocalSTS**)。</span><span class="sxs-lookup"><span data-stu-id="4a92d-145">The Identity and Access Tool configures the service to use WIF and to outsource authentication to the local development STS (**LocalSTS**) by adding configuration elements to the *Web.config* file.</span></span>  
  
7. <span data-ttu-id="4a92d-146">在 *Service1.svc.cs* 檔案中，**System.Security.Claims** 命名空間新增一個 `using` 指示詞，並使用下面程式碼來取代現有的程式碼，然後儲存檔案：</span><span class="sxs-lookup"><span data-stu-id="4a92d-146">In the *Service1.svc.cs* file, add a `using` directive for the **System.Security.Claims** namespace and replace the existing code with the following, then save the file:</span></span>  
  
    ```csharp  
    public class Service1 : IService1  
    {  
        public string ComputeResponse(string input)  
        {  
            // Get the caller's identity from ClaimsPrincipal.Current  
            ClaimsPrincipal claimsPrincipal = OperationContext.Current.ClaimsPrincipal;  
  
            // Start generating the output  
            StringBuilder builder = new StringBuilder();  
            builder.AppendLine("Computed by ClaimsAwareWebService");  
            builder.AppendLine("Input received from client:" + input);  
  
            if (claimsPrincipal != null)  
            {  
                // Display the claims from the caller. Do not use this code in a production application.  
                ClaimsIdentity identity = claimsPrincipal.Identity as ClaimsIdentity;  
                builder.AppendLine("Client Name:" + identity.Name);  
                builder.AppendLine("IsAuthenticated:" + identity.IsAuthenticated);  
                builder.AppendLine("The service received the following issued claims of the client:");  
  
                // Iterate over the caller’s claims and append to the output  
                foreach (Claim claim in claimsPrincipal.Claims)  
                {  
                    builder.AppendLine("ClaimType :" + claim.Type + "   ClaimValue:" + claim.Value);  
                }  
            }  
  
            return builder.ToString();  
        }  
    }  
    ```  
  
     <span data-ttu-id="4a92d-147">`ComputeResponse` 方法會顯示由 **LocalSTS** 所簽發的各種宣告的屬性。</span><span class="sxs-lookup"><span data-stu-id="4a92d-147">The `ComputeResponse` method displays the properties of various claims that are issued by **LocalSTS**.</span></span>  
  
8. <span data-ttu-id="4a92d-148">在 *IService1.cs* 檔案中，以下列程式碼取代現有的程式碼，然後儲存檔案：</span><span class="sxs-lookup"><span data-stu-id="4a92d-148">In the *IService1.cs* file, replace the existing code with the following, then save the file:</span></span>  
  
    ```csharp  
    [ServiceContract]  
    public interface IService1  
    {  
        [OperationContract]  
        string ComputeResponse(string input);  
    }  
    ```  
  
9. <span data-ttu-id="4a92d-149">建置專案。</span><span class="sxs-lookup"><span data-stu-id="4a92d-149">Build the project.</span></span>  
  
10. <span data-ttu-id="4a92d-150">按 **Ctrl-F5** 執行服務，而不啟動偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="4a92d-150">Press **Ctrl-F5** to run the service without starting the debugger.</span></span> <span data-ttu-id="4a92d-151">此時應該會開啟一個服務網頁，您可以查看通知區域 (系統匣) 以確認 **LocalSTS** 正在執行。</span><span class="sxs-lookup"><span data-stu-id="4a92d-151">A Web page should open for the service and you can verify that **LocalSTS** is running by looking in the notification area (system tray).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="4a92d-152">當您在下一個步驟中將服務參考新增至用戶端應用程式時，**TestService** 和 **LocalSTS** 都必須是在執行中。</span><span class="sxs-lookup"><span data-stu-id="4a92d-152">Both **TestService** and **LocalSTS** must be running when you add the service reference to the client application in the next step.</span></span>  
  
## <a name="step-2--create-a-client-application-for-the-wcf-service"></a><span data-ttu-id="4a92d-153">步驟 2 – 建立 WCF 服務的用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="4a92d-153">Step 2 – Create a Client Application for the WCF Service</span></span>  
 <span data-ttu-id="4a92d-154">在這個步驟中，您要建立一個主控台應用程式，該應用程式會使用「開發 STS」與您在先前步驟中建立的 WCF 服務進行驗證。</span><span class="sxs-lookup"><span data-stu-id="4a92d-154">In this step, you will create a console application that uses the Development STS to authenticate with the WCF service you created in the previous step.</span></span>  
  
#### <a name="to-create-a-client-application"></a><span data-ttu-id="4a92d-155">若要建立用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="4a92d-155">To create a client application</span></span>  
  
1. <span data-ttu-id="4a92d-156">在 Visual Studio 中，以滑鼠右鍵按一下方案，然後依序按一下 [新增] 和 [新增專案]。</span><span class="sxs-lookup"><span data-stu-id="4a92d-156">In Visual Studio, right-click on the solution, click **Add**, and then click **New Project**.</span></span>  
  
2. <span data-ttu-id="4a92d-157">在 [新增專案] 視窗中，選取 [Visual C#] 範本清單中的 [主控台應用程式]，輸入 `Client`，然後按 [確定]。</span><span class="sxs-lookup"><span data-stu-id="4a92d-157">In the **Add New Project** window, select **Console Application** from the **Visual C#** templates list, enter `Client`, and then press **OK**.</span></span> <span data-ttu-id="4a92d-158">您的方案資料夾中就會建立新的專案。</span><span class="sxs-lookup"><span data-stu-id="4a92d-158">The new project will be created in your solution folder.</span></span>  
  
3. <span data-ttu-id="4a92d-159">以滑鼠右鍵按一下 [Client] 專案底下的 [參考]，然後按一下 [加入服務參考]。</span><span class="sxs-lookup"><span data-stu-id="4a92d-159">Right-click on **References** under the **Client** project, and then click **Add Service Reference**.</span></span>  
  
4. <span data-ttu-id="4a92d-160">在 [加入服務參考] 視窗中，按一下 [探索] 按鈕上的下拉箭號，然後按一下 [方案中的服務]。</span><span class="sxs-lookup"><span data-stu-id="4a92d-160">In the **Add Service Reference** window, click the drop-down arrow on the **Discover** button and click **Services in Solution**.</span></span> <span data-ttu-id="4a92d-161">[位址] 會自動填入您稍早建立的 WCF 服務，而 [命名空間] 則會設定為 **ServiceReference1**。</span><span class="sxs-lookup"><span data-stu-id="4a92d-161">The **Address** will automatically populate with the WCF service you created earlier, and the **Namespace** will be set to **ServiceReference1**.</span></span> <span data-ttu-id="4a92d-162">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="4a92d-162">Click **OK**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="4a92d-163">當您將服務參考新增至用戶端時，**TestService** 和 **LocalSTS** 都必須是在執行中。</span><span class="sxs-lookup"><span data-stu-id="4a92d-163">Both **TestService** and **LocalSTS** must be running when you add the service reference to the client.</span></span>  
  
5. <span data-ttu-id="4a92d-164">Visual Studio 會產生 WCF 服務的 Proxy 類別，並加入所有必要的參考資訊。</span><span class="sxs-lookup"><span data-stu-id="4a92d-164">Visual Studio will generate proxy classes for the WCF service, and add all of the necessary reference information.</span></span> <span data-ttu-id="4a92d-165">它也會將項目新增至 *App.config* 檔案中，來設定用戶端從 STS 取得權杖以便向服務進行驗證。</span><span class="sxs-lookup"><span data-stu-id="4a92d-165">It will also add elements to the *App.config* file to configure the client to get a token from the STS to authenticate with the service.</span></span> <span data-ttu-id="4a92d-166">當這個程序完成之後，**Program.cs** 檔案隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="4a92d-166">When this process is finished, the **Program.cs** file will open.</span></span> <span data-ttu-id="4a92d-167">為 **System.ServiceModel** 新增 `using` 指示詞，也為 **Client.ServiceReference1** 新增指示詞，並以下列程式碼取代 **Main** 方法，然後儲存檔案：</span><span class="sxs-lookup"><span data-stu-id="4a92d-167">Add a `using` directive for **System.ServiceModel** and another for **Client.ServiceReference1**, replace the **Main** method with the following code, then save the file:</span></span>  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        // Create the client for the service  
        Service1Client client = new Service1Client();  
        Console.WriteLine("-------------WCF Client Application--------------\n");  
  
        while (!ShouldQuitApplication())  
        {  
            try  
            {  
                Console.WriteLine(client.ComputeResponse("Hello World"));  
            }  
            catch (CommunicationException e)  
            {  
                Console.WriteLine(e.Message);  
                Console.WriteLine(e.StackTrace);  
                Exception ex = e.InnerException;  
                while (ex != null)  
                {  
                    Console.WriteLine("===========================");  
                    Console.WriteLine(ex.Message);  
                    Console.WriteLine(ex.StackTrace);  
                    ex = ex.InnerException;  
                }  
            }  
            catch (TimeoutException)  
            {  
                Console.WriteLine("Timed out...");  
            }  
            catch (Exception e)  
            {  
                Console.WriteLine("An unexpected exception occurred.");  
                Console.WriteLine(e.StackTrace);  
            }  
        }  
  
        client.Close();  
  
        if (client != null)  
        {  
            client.Abort();  
        }  
    }  
  
    static bool ShouldQuitApplication()  
    {  
        Console.WriteLine("---------------------------------------------------------------------");  
        Console.WriteLine("Press Enter key to invoke service, any other key to quit application:");  
        Console.WriteLine("----------------------------------------------------------------------");  
  
        ConsoleKeyInfo keyInfo = Console.ReadKey();  
        if (keyInfo.Key == ConsoleKey.Enter)  
            return false;  
        return true;  
    }  
    ```  
  
6. <span data-ttu-id="4a92d-168">開啟 *App.config* 檔案，並在 `<system.serviceModel>` 項目底下新增下列 XML 作為第一個子項目，然後儲存檔案：</span><span class="sxs-lookup"><span data-stu-id="4a92d-168">Open the *App.config* file and add the following XML as the first child element under the `<system.serviceModel>` element, then save the file:</span></span>  
  
    ```xml  
    <behaviors>  
       <endpointBehaviors>  
         <behavior>  
           <clientCredentials>  
             <serviceCertificate>  
               <authentication certificateValidationMode="None"/>  
             </serviceCertificate>  
           </clientCredentials>  
         </behavior>  
       </endpointBehaviors>  
     </behaviors>  
    ```  
  
     <span data-ttu-id="4a92d-169">這會停用憑證驗證。</span><span class="sxs-lookup"><span data-stu-id="4a92d-169">This disables certificate validation.</span></span>  
  
7. <span data-ttu-id="4a92d-170">以滑鼠右鍵按一下 [TestService] 方案，然後按一下 [設定啟始專案]。</span><span class="sxs-lookup"><span data-stu-id="4a92d-170">Right-click the **TestService** solution and click on **Set StartUp Projects**.</span></span> <span data-ttu-id="4a92d-171">[啟始專案] 屬性頁隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="4a92d-171">The **Startup Project** property page opens.</span></span> <span data-ttu-id="4a92d-172">在 [啟始專案] 屬性頁上，選取 [多個啟始專案] ，然後在每個專案的 [動作] 欄位中按一下，並從下拉式功能表中選取 [啟動]。</span><span class="sxs-lookup"><span data-stu-id="4a92d-172">In the **Startup Project** property page, select **Multiple startup projects** then click in the **Action** field for each project and select **Start** from the drop-down menu.</span></span> <span data-ttu-id="4a92d-173">按一下 [確定] 儲存這些設定。</span><span class="sxs-lookup"><span data-stu-id="4a92d-173">Click **OK** to save the settings.</span></span>  
  
8. <span data-ttu-id="4a92d-174">建置方案。</span><span class="sxs-lookup"><span data-stu-id="4a92d-174">Build the solution.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="4a92d-175">步驟 3 – 測試方案</span><span class="sxs-lookup"><span data-stu-id="4a92d-175">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="4a92d-176">在這個步驟中，您要測試啟用了 WIF 的 WCF 應用程式並確認有提出宣告。</span><span class="sxs-lookup"><span data-stu-id="4a92d-176">In this step you will test your WIF-enabled WCF application and verify that claims are presented.</span></span>  
  
#### <a name="to-test-your-wif-enabled-wcf-application-for-claims"></a><span data-ttu-id="4a92d-177">若要針對宣告測試啟用了 WIF 的 WCF 應用程式</span><span class="sxs-lookup"><span data-stu-id="4a92d-177">To test your WIF-enabled WCF application for claims</span></span>  
  
1. <span data-ttu-id="4a92d-178">按 **F5** 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="4a92d-178">Press **F5** to build and run the application.</span></span> <span data-ttu-id="4a92d-179">您應該會看到主控台視窗，並將下列文字：**按下 Enter 鍵來叫用服務，若要結束應用程式的任何其他索引鍵：**</span><span class="sxs-lookup"><span data-stu-id="4a92d-179">You should be presented with a console window, and the following text: **Press Enter key to invoke service, any other key to quit application:**</span></span>  
  
2. <span data-ttu-id="4a92d-180">按 **Enter**，然後主控台中應該會顯示下列宣告資訊：</span><span class="sxs-lookup"><span data-stu-id="4a92d-180">Press **Enter**, and the following claims information should appear in the console:</span></span>  
  
    ```  
    Computed by Service1  
    Input received from client: Hello World  
    Client Name: Terry  
    IsAuthenticated: True  
    The service received the following issued claims of the client:  
    ClaimType :http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name    ClaimValue:Terry  
    ClaimType :http://schema.xmlsoap.org/ws/2005/05/identity/claims/surname    ClaimValue:Adams  
    ClaimType :http://schemas.microsoft.com/ws/2008/06/identity/claims/role    ClaimValue:developer  
    ClaimType :http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress    ClaimValue:terry@contoso.com  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="4a92d-181">在您按 **Enter** 之前，**TestService** 和 **LocalSTS** 都必須是在執行中。</span><span class="sxs-lookup"><span data-stu-id="4a92d-181">Both **TestService** and **LocalSTS** must be running before you press **Enter**.</span></span> <span data-ttu-id="4a92d-182">此時應該會開啟一個服務網頁，您可以查看通知區域 (系統匣) 以確認 **LocalSTS** 正在執行。</span><span class="sxs-lookup"><span data-stu-id="4a92d-182">A Web page should open for the service and you can verify that **LocalSTS** is running by looking in the notification area (system tray).</span></span>  
  
3. <span data-ttu-id="4a92d-183">如果這些宣告出現在主控台中，則您已成功與 STS 進行驗證以顯示 WCF 服務的宣告。</span><span class="sxs-lookup"><span data-stu-id="4a92d-183">If these claims appear in the console, you have successfully authenticated with the STS to display claims from the WCF service.</span></span>
