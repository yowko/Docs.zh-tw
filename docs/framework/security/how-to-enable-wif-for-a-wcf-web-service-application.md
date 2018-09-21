---
title: 如何：啟用 WCF Web 服務應用程式的 WIF
ms.date: 03/30/2017
ms.assetid: bfc64b3d-64e9-4093-a6a4-72e933917af7
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 71897299d68c2f0e43def8e70730ea456d6e9e24
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2018
ms.locfileid: "46508748"
---
# <a name="how-to-enable-wif-for-a-wcf-web-service-application"></a>如何：啟用 WCF Web 服務應用程式的 WIF
## <a name="applies-to"></a>適用於  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   Microsoft® Windows® Communication Foundation (WCF)  
  
## <a name="summary"></a>總結  
 這篇使用方法文章提供了在 WCF Web 服務中啟用 WIF 的詳細逐步程序。 此外，它還提供如何測試應用程式以確認應用程式執行時 Web 服務可正確提出宣告的指示。 這篇使用方法文章並沒有提供建立 Security Token Service (STS) 的詳細指示，而是使用識別和存取工具隨附的「開發 STS」。 「開發 STS」並不會執行實際的驗證，而只是用於測試用途。 您必須安裝識別和存取工具才能完成這篇使用方法文章。 您可以從下列位置下載：[Identity and Access Tool](https://go.microsoft.com/fwlink/?LinkID=245849) (身分識別與存取工具)  
  
## <a name="contents"></a>內容  
  
-   目標  
  
-   總覽  
  
-   步驟摘要  
  
-   步驟 1 – 建立簡單的 WCF 服務  
  
-   步驟 2 – 建立 WCF 服務的用戶端應用程式  
  
-   步驟 3 – 測試方案  
  
## <a name="objectives"></a>目標  
  
-   建立必須使用已發行權杖的 WCF 服務  
  
-   建立會從 STS 要求權杖並將它傳遞至 WCF 服務的 WCF 用戶端  
  
## <a name="overview"></a>總覽  
 這篇使用方法文章的目的是要示範開發人員如何在開發 WCF 服務時使用同盟驗證。 在 WCF 服務中使用同盟的其中一些優點包括：  
  
1.  將驗證邏輯排除在 WCF 服務程式碼外  
  
2.  重複使用現有的身分識別管理方案  
  
3.  與其他識別方案的互通性  
  
4.  未來變更的靈活性和彈性  
  
 WIF 與相關聯的識別和存取工具可讓您使用同盟驗證更輕鬆地開發及測試 WCF 服務，如下面步驟所示。  
  
## <a name="summary-of-steps"></a>步驟摘要  
  
-   步驟 1 – 建立簡單的 WCF 服務  
  
-   步驟 2 – 建立 WCF 服務的用戶端應用程式  
  
-   步驟 3 – 測試方案  
  
## <a name="step-1--create-a-simple-wcf-service"></a>步驟 1 – 建立簡單的 WCF 服務  
 在這個步驟中，您要建立一個新的 WCF 服務，該服務使用識別和存取工具所隨附的「開發 STS」。  
  
#### <a name="to-create-a-simple-wcf-service"></a>若要建立簡單的 WCF 服務  
  
1.  以系統管理員身分的高階權限模式來啟動 Visual Studio。  
  
2.  在 Visual Studio 中，依序按一下 [檔案]、[新增] 和 [專案]。  
  
3.  在 [新增專案] 視窗中，按一下 [WCF 服務應用程式]。  
  
4.  在 [名稱] 中，輸入 `TestService`，然後按 [確定]。  
  
5.  以滑鼠右鍵按一下方案總管 底下的 [TestService]，然後選取 [身分識別與存取]。  
  
6.  [身分識別與存取] 視窗隨即出現。 在 [提供者] 底下，選取 [使用本機開發 STS 測試應用程式]，然後按一下 [套用]。 身分識別與存取工具會在 *Web.config* 檔案中新增組態項目，藉以設定服務使用 WIF，並將驗證外包給本機開發 STS (**LocalSTS**)。  
  
7.  在 *Service1.svc.cs* 檔案中，**System.Security.Claims** 命名空間新增一個 `using` 指示詞，並使用下面程式碼來取代現有的程式碼，然後儲存檔案：  
  
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
  
     `ComputeResponse` 方法會顯示由 **LocalSTS** 所簽發的各種宣告的屬性。  
  
8.  在 *IService1.cs* 檔案中，以下列程式碼取代現有的程式碼，然後儲存檔案：  
  
    ```csharp  
    [ServiceContract]  
    public interface IService1  
    {  
        [OperationContract]  
        string ComputeResponse(string input);  
    }  
    ```  
  
9. 建置專案。  
  
10. 按 **Ctrl-F5** 執行服務，而不啟動偵錯工具。 此時應該會開啟一個服務網頁，您可以查看通知區域 (系統匣) 以確認 **LocalSTS** 正在執行。  
  
    > [!IMPORTANT]
    >  當您在下一個步驟中將服務參考新增至用戶端應用程式時，**TestService** 和 **LocalSTS** 都必須是在執行中。  
  
## <a name="step-2--create-a-client-application-for-the-wcf-service"></a>步驟 2 – 建立 WCF 服務的用戶端應用程式  
 在這個步驟中，您要建立一個主控台應用程式，該應用程式會使用「開發 STS」與您在先前步驟中建立的 WCF 服務進行驗證。  
  
#### <a name="to-create-a-client-application"></a>若要建立用戶端應用程式  
  
1.  在 Visual Studio 中，以滑鼠右鍵按一下方案，然後依序按一下 [新增] 和 [新增專案]。  
  
2.  在 [新增專案] 視窗中，選取 [Visual C#] 範本清單中的 [主控台應用程式]，輸入 `Client`，然後按 [確定]。 您的方案資料夾中就會建立新的專案。  
  
3.  以滑鼠右鍵按一下 [Client] 專案底下的 [參考]，然後按一下 [加入服務參考]。  
  
4.  在 [加入服務參考] 視窗中，按一下 [探索] 按鈕上的下拉箭號，然後按一下 [方案中的服務]。 [位址] 會自動填入您稍早建立的 WCF 服務，而 [命名空間] 則會設定為 **ServiceReference1**。 按一下 [確定 **Deploying Office Solutions**]。  
  
    > [!IMPORTANT]
    >  當您將服務參考新增至用戶端時，**TestService** 和 **LocalSTS** 都必須是在執行中。  
  
5.  Visual Studio 會產生 WCF 服務的 Proxy 類別，並加入所有必要的參考資訊。 它也會將項目新增至 *App.config* 檔案中，來設定用戶端從 STS 取得權杖以便向服務進行驗證。 當這個程序完成之後，**Program.cs** 檔案隨即開啟。 為 **System.ServiceModel** 新增 `using` 指示詞，也為 **Client.ServiceReference1** 新增指示詞，並以下列程式碼取代 **Main** 方法，然後儲存檔案：  
  
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
  
6.  開啟 *App.config* 檔案，並在 `<system.serviceModel>` 項目底下新增下列 XML 作為第一個子項目，然後儲存檔案：  
  
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
  
     這會停用憑證驗證。  
  
7.  以滑鼠右鍵按一下 [TestService] 方案，然後按一下 [設定啟始專案]。 [啟始專案] 屬性頁隨即開啟。 在 [啟始專案] 屬性頁上，選取 [多個啟始專案] ，然後在每個專案的 [動作] 欄位中按一下，並從下拉式功能表中選取 [啟動]。 按一下 [確定] 儲存這些設定。  
  
8.  建置方案。  
  
## <a name="step-3--test-your-solution"></a>步驟 3 – 測試方案  
 在這個步驟中，您要測試啟用了 WIF 的 WCF 應用程式並確認有提出宣告。  
  
#### <a name="to-test-your-wif-enabled-wcf-application-for-claims"></a>若要針對宣告測試啟用了 WIF 的 WCF 應用程式  
  
1.  按 **F5** 鍵建置並執行應用程式。 您應該會看到一個主控台視窗，並看到下面文字：**Press Enter key to invoke service, any other key to quit application:**  
  
2.  按 **Enter**，然後主控台中應該會顯示下列宣告資訊：  
  
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
    >  在您按 **Enter** 之前，**TestService** 和 **LocalSTS** 都必須是在執行中。 此時應該會開啟一個服務網頁，您可以查看通知區域 (系統匣) 以確認 **LocalSTS** 正在執行。  
  
3.  如果這些宣告出現在主控台中，則您已成功與 STS 進行驗證以顯示 WCF 服務的宣告。
