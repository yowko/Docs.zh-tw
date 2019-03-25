---
title: HOW TO：使用使用者名稱和密碼進行驗證
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF], user name and password
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
ms.openlocfilehash: f6939659249ea40e97f340771017d0587ec6a08f
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412262"
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a><span data-ttu-id="601e9-102">HOW TO：使用使用者名稱和密碼進行驗證</span><span class="sxs-lookup"><span data-stu-id="601e9-102">How to: Authenticate with a User Name and Password</span></span>

<span data-ttu-id="601e9-103">本主題示範如何啟用 Windows Communication Foundation (WCF) 服務驗證用戶端的 Windows 網域使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="601e9-103">This topic demonstrates how to enable a Windows Communication Foundation (WCF) service to authenticate a client with a Windows domain username and password.</span></span> <span data-ttu-id="601e9-104">這裡假設您有運作中的自我裝載 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="601e9-104">It assumes you have a working, self-hosted WCF service.</span></span> <span data-ttu-id="601e9-105">如需範例，建立基本自我裝載的 WCF 服務，請參閱[入門教學課程](../../../../docs/framework/wcf/getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="601e9-105">For an example of creating a basic self-hosted WCF service see, [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span> <span data-ttu-id="601e9-106">本主題假設服務是在程式碼中進行設定。</span><span class="sxs-lookup"><span data-stu-id="601e9-106">This topic assumes the service is configured in code.</span></span> <span data-ttu-id="601e9-107">如果您想要看到的設定類似服務，使用組態檔範例請參閱[訊息安全性使用者名稱](../../../../docs/framework/wcf/samples/message-security-user-name.md)</span><span class="sxs-lookup"><span data-stu-id="601e9-107">If you would like to see an example of configuring a similar service using a configuration file see [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md)</span></span>  
  
 <span data-ttu-id="601e9-108">若要設定服務使用 Windows 網域使用者名和密碼驗證其用戶端，請使用 <xref:System.ServiceModel.WSHttpBinding>，並將其 `Security.Mode` 屬性設定為 `Message`。</span><span class="sxs-lookup"><span data-stu-id="601e9-108">To configure a service to authenticate its clients using Windows Domain username and passwords use the <xref:System.ServiceModel.WSHttpBinding> and set its `Security.Mode` property to `Message`.</span></span> <span data-ttu-id="601e9-109">此外，將使用者名稱和密碼從用戶端傳送至服務時，您必須指定要用來加密使用者名稱和密碼的 X 509 憑證。</span><span class="sxs-lookup"><span data-stu-id="601e9-109">In addition you must specify an X509 certificate that will be used to encrypt the username and password as they are sent from the client to the service.</span></span>  
  
 <span data-ttu-id="601e9-110">在用戶端上，您必須提示使用者輸入使用者名稱和密碼，並在 WCF 用戶端 Proxy 上指定使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="601e9-110">On the client, you must prompt the user for the username and password and specify the user’s credentials on the WCF client proxy.</span></span>  
  
## <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a><span data-ttu-id="601e9-111">若要設定使用 Windows 網域使用者名稱和密碼進行驗證的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="601e9-111">To configure a WCF service to authenticate using Windows domain username and password</span></span>
  
1.  <span data-ttu-id="601e9-112">請建立 <xref:System.ServiceModel.WSHttpBinding> 的執行個體，將繫結的安全性模式設定為 <xref:System.ServiceModel.WSHttpSecurity.Message?displayProperty=nameWithType>，將繫結的 `ClientCredentialType` 設定為 <xref:System.ServiceModel.MessageCredentialType.UserName?displayProperty=nameWithType>，然後將使用所設定之繫結的服務端點加入至服務主機，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="601e9-112">Create an instance of the <xref:System.ServiceModel.WSHttpBinding>, set the security mode of the binding to <xref:System.ServiceModel.WSHttpSecurity.Message?displayProperty=nameWithType>, set the `ClientCredentialType` of the binding to <xref:System.ServiceModel.MessageCredentialType.UserName?displayProperty=nameWithType>, and add a service endpoint using the configured binding to the service host as shown in the following code:</span></span>  
  
    ```  
    // ...  
    WSHttpBinding userNameBinding = new WSHttpBinding();  
    userNameBinding.Security.Mode = SecurityMode.Message;  
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;  
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");  
    // ...  
    ```  
  
2.  <span data-ttu-id="601e9-113">指定伺服器憑證，用以加密透過網路傳送之使用者名及密碼的資訊。</span><span class="sxs-lookup"><span data-stu-id="601e9-113">Specify the server certificate used to encrypt the username and password information sent over the wire.</span></span> <span data-ttu-id="601e9-114">這個程式碼應直接加在上面程式碼之後。</span><span class="sxs-lookup"><span data-stu-id="601e9-114">This code should immediately follow the code above.</span></span> <span data-ttu-id="601e9-115">下列範例會使用已建立的憑證中的 setup.bat 檔案所[訊息安全性使用者名稱](../../../../docs/framework/wcf/samples/message-security-user-name.md)範例：</span><span class="sxs-lookup"><span data-stu-id="601e9-115">The following example uses the certificate that is created by the setup.bat file from the [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md) sample:</span></span>  
  
    ```  
    // ...  
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");  
    // ...  
    ```  
  
     <span data-ttu-id="601e9-116">您可以使用自己的憑證，只需將程式碼修改成參考您的憑證。</span><span class="sxs-lookup"><span data-stu-id="601e9-116">You can use your own certificate, just modify the code to refer to your certificate.</span></span> <span data-ttu-id="601e9-117">如需建立及使用憑證的詳細資訊，請參閱[Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="601e9-117">For more information about creating and using certificates see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="601e9-118">確認憑證是在本機電腦的 [受信任的人] 憑證存放區中。</span><span class="sxs-lookup"><span data-stu-id="601e9-118">Make sure the certificate is in the Trusted People certificate store for the Local Machine.</span></span> <span data-ttu-id="601e9-119">您可以執行 mmc.exe，然後選取**檔案**，**新增/移除嵌入式管理單元...** 功能表項目。</span><span class="sxs-lookup"><span data-stu-id="601e9-119">You can do this by running mmc.exe and selecting the **File**, **Add/Remove Snap-in...** menu item.</span></span> <span data-ttu-id="601e9-120">在 **新增或移除嵌入式管理單元**對話方塊中，選取**憑證嵌入式管理單元**然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="601e9-120">In the **Add or Remove Snap-ins** dialog, select the **Certificates snap-in** and click **Add**.</span></span> <span data-ttu-id="601e9-121">在 憑證 嵌入式管理單元 對話方塊中選取**電腦帳戶**。</span><span class="sxs-lookup"><span data-stu-id="601e9-121">In the Certificates Snap-in dialog select **Computer account**.</span></span> <span data-ttu-id="601e9-122">根據預設，從訊息安全性使用者名稱範例所產生的憑證位於 [個別/憑證] 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="601e9-122">By default the certificate generated from the Message Security User name sample will be located in the Personal/Certificates folder.</span></span>  <span data-ttu-id="601e9-123">它會列為核發給在 MMC 視窗中的資料行底下的"localhost"。</span><span class="sxs-lookup"><span data-stu-id="601e9-123">It will be listed as "localhost" under the Issued to column in the MMC window.</span></span> <span data-ttu-id="601e9-124">將拖放到憑證**受信任的人**資料夾。</span><span class="sxs-lookup"><span data-stu-id="601e9-124">Drag and drop the certificate into the **Trusted People** folder.</span></span> <span data-ttu-id="601e9-125">這樣可讓 WCF 在執行驗證時，將憑證視為受信任的憑證。</span><span class="sxs-lookup"><span data-stu-id="601e9-125">This will allow WCF to treat the certificate as a trusted certificate when performing authentication.</span></span>  
  
## <a name="to-call-the-service-passing-username-and-password"></a><span data-ttu-id="601e9-126">若要呼叫服務傳遞使用者名稱和密碼</span><span class="sxs-lookup"><span data-stu-id="601e9-126">To call the service passing username and password</span></span>  
  
1.  <span data-ttu-id="601e9-127">用戶端應用程式必須提示使用者輸入其使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="601e9-127">The client application must prompt the user for their username and password.</span></span> <span data-ttu-id="601e9-128">下列程式碼會要求使用者輸入使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="601e9-128">The following code asks the user for username and password.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="601e9-129">由於密碼會在輸入時顯示，這個程式碼不應在實際環境中使用。</span><span class="sxs-lookup"><span data-stu-id="601e9-129">This code should not be used in production as the password is displayed while being entered.</span></span>  
  
    ```  
    public static void GetPassword(out string username, out string password)  
            {  
                Console.WriteLine("Provide a valid machine or domain account. [domain\\user]");  
                Console.WriteLine("   Enter username:");  
                username = Console.ReadLine();  
                Console.WriteLine("   Enter password:");  
                password = Console.ReadLine();             
                return;  
            }  
    ```  
  
2.  <span data-ttu-id="601e9-130">指定用戶端的認證，以建立用戶端 Proxy 的執行個體，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="601e9-130">Create an instance of the client proxy specifying the client’s credentials as shown in the following code:</span></span>  
  
    ```  
    string username;  
    string password;  
  
    // Instantiate the proxy  
    Service1Client proxy = new Service1Client();  
  
    // Prompt the user for username & password  
    GetPassword(out username, out password);  
  
    // Set the user’s credentials on the proxy  
    proxy.ClientCredentials.UserName.UserName = username;  
    proxy.ClientCredentials.UserName.Password = password;  
  
    // Treat the test certificate as trusted  
    proxy.ClientCredentials.ServiceCertificate.Authentication.CertificateValidationMode = System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust;  
    // Call the service operation using the proxy  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="601e9-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="601e9-131">See also</span></span>
- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.SecurityMode>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>
- <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>
- [<span data-ttu-id="601e9-132">使用基本驗證的傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="601e9-132">Transport Security with Basic Authentication</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)
- [<span data-ttu-id="601e9-133">分散式應用程式安全性</span><span class="sxs-lookup"><span data-stu-id="601e9-133">Distributed Application Security</span></span>](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)
- [<span data-ttu-id="601e9-134">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="601e9-134">\<wsHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
