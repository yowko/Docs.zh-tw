---
title: "HOW TO：使用使用者名稱與密碼來驗證"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: authentication [WCF], user name and password
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 73ef3c3f4f4aeb9295cedbbf56635454869b3f4f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a><span data-ttu-id="a9085-102">HOW TO：使用使用者名稱與密碼來驗證</span><span class="sxs-lookup"><span data-stu-id="a9085-102">How to: Authenticate with a User Name and Password</span></span>
<span data-ttu-id="a9085-103">本主題示範如何讓 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務使用 Windows 網域使用者名稱與密碼來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="a9085-103">This topic demonstrates how to enable a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service to authenticate a client with a Windows domain username and password.</span></span> <span data-ttu-id="a9085-104">這裡假設您有運作中的自我裝載 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="a9085-104">It assumes you have a working, self-hosted WCF service.</span></span> <span data-ttu-id="a9085-105">如需範例，建立基本自我裝載的 WCF 服務，請參閱[入門教學課程](../../../../docs/framework/wcf/getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="a9085-105">For an example of creating a basic self-hosted WCF service see, [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span> <span data-ttu-id="a9085-106">本主題假設服務是在程式碼中進行設定。</span><span class="sxs-lookup"><span data-stu-id="a9085-106">This topic assumes the service is configured in code.</span></span> <span data-ttu-id="a9085-107">如果您想要看到的設定類似的服務，使用組態檔範例請參閱[訊息安全性使用者名稱](../../../../docs/framework/wcf/samples/message-security-user-name.md)</span><span class="sxs-lookup"><span data-stu-id="a9085-107">If you would like to see an example of configuring a similar service using a configuration file see [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md)</span></span>  
  
 <span data-ttu-id="a9085-108">若要設定服務驗證用戶端使用 Windows 網域使用者名稱和密碼使用 <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> 並設定其`Security.Mode`屬性`Message`。</span><span class="sxs-lookup"><span data-stu-id="a9085-108">To configure a service to authenticate its clients using Windows Domain username and passwords use the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> and set its `Security.Mode` property to `Message`.</span></span> <span data-ttu-id="a9085-109">此外，將使用者名稱和密碼從用戶端傳送至服務時，您必須指定要用來加密使用者名稱和密碼的 X 509 憑證。</span><span class="sxs-lookup"><span data-stu-id="a9085-109">In addition you must specify an X509 certificate that will be used to encrypt the username and password as they are sent from the client to the service.</span></span>  
  
 <span data-ttu-id="a9085-110">在用戶端上，您必須提示使用者輸入使用者名稱和密碼，並在 WCF 用戶端 Proxy 上指定使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="a9085-110">On the client, you must prompt the user for the username and password and specify the user’s credentials on the WCF client proxy.</span></span>  
  
### <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a><span data-ttu-id="a9085-111">若要將 WCF 服務設為使用 Windows 網域使用者名稱與密碼進行驗證。</span><span class="sxs-lookup"><span data-stu-id="a9085-111">To configure a WCF service to authenticate using Windows domain username and password.</span></span>  
  
1.  <span data-ttu-id="a9085-112">建立的執行個體 <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>，設定要繫結的安全性模式`SecurityMode.Message`，將`ClientCredentialType`繫結至的`MessageCredentialType.UserName`，並加入服務端點所示，使用設定的繫結至服務主機下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="a9085-112">Create an instance of the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>, set the security mode of the binding to `SecurityMode.Message`, set the `ClientCredentialType` of the binding to `MessageCredentialType.UserName`, and add a service endpoint using the configured binding to the service host as shown in the following code:</span></span>  
  
    ```  
    // ...  
    WSHttpBinding userNameBinding = new WSHttpBinding();  
    userNameBinding.Security.Mode = SecurityMode.Message;  
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;  
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");  
    // ...  
    ```  
  
2.  <span data-ttu-id="a9085-113">指定伺服器憑證，用以加密透過網路傳送之使用者名及密碼的資訊。</span><span class="sxs-lookup"><span data-stu-id="a9085-113">Specify the server certificate used to encrypt the username and password information sent over the wire.</span></span> <span data-ttu-id="a9085-114">這個程式碼應直接加在上面程式碼之後。</span><span class="sxs-lookup"><span data-stu-id="a9085-114">This code should immediately follow the code above.</span></span> <span data-ttu-id="a9085-115">下列範例會使用的憑證，會建立由 setup.bat 檔從[訊息安全性使用者名稱](../../../../docs/framework/wcf/samples/message-security-user-name.md)範例：</span><span class="sxs-lookup"><span data-stu-id="a9085-115">The following example uses the certificate that is created by the setup.bat file from the [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md) sample:</span></span>  
  
    ```  
    // ...  
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");  
    // ...  
    ```  
  
     <span data-ttu-id="a9085-116">您可以使用自己的憑證，只需將程式碼修改成參考您的憑證。</span><span class="sxs-lookup"><span data-stu-id="a9085-116">You can use your own certificate, just modify the code to refer to your certificate.</span></span> <span data-ttu-id="a9085-117">如需有關建立及使用憑證，請參閱[使用憑證](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="a9085-117">For more information about creating and using certificates see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="a9085-118">確認憑證是在本機電腦的 [受信任的人] 憑證存放區中。</span><span class="sxs-lookup"><span data-stu-id="a9085-118">Make sure the certificate is in the Trusted People certificate store for the Local Machine.</span></span> <span data-ttu-id="a9085-119">您可以執行 mmc.exe，然後選取**檔案**，**新增/移除嵌入式管理單元...**功能表項目。</span><span class="sxs-lookup"><span data-stu-id="a9085-119">You can do this by running mmc.exe and selecting the **File**, **Add/Remove Snap-in...** menu item.</span></span> <span data-ttu-id="a9085-120">在**新增或移除嵌入式管理單元**對話方塊中，選取**憑證嵌入式管理單元**按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="a9085-120">In the **Add or Remove Snap-ins** dialog, select the **Certificates snap-in** and click **Add**.</span></span> <span data-ttu-id="a9085-121">在 [憑證嵌入式管理單元] 對話方塊中選取**電腦帳戶**。</span><span class="sxs-lookup"><span data-stu-id="a9085-121">In the Certificates Snap-in dialog select **Computer account**.</span></span> <span data-ttu-id="a9085-122">根據預設，從訊息安全性使用者名稱範例所產生的憑證位於 [個別/憑證] 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="a9085-122">By default the certificate generated from the Message Security User name sample will be located in the Personal/Certificates folder.</span></span>  <span data-ttu-id="a9085-123">將為"localhost"下的 發行至資料行在 MMC 視窗中列出。</span><span class="sxs-lookup"><span data-stu-id="a9085-123">It will be listed as "localhost" under the Issued to column in the MMC window.</span></span> <span data-ttu-id="a9085-124">將拖放到憑證**受信任的人**資料夾。</span><span class="sxs-lookup"><span data-stu-id="a9085-124">Drag and drop the certificate into the **Trusted People** folder.</span></span> <span data-ttu-id="a9085-125">這樣可讓 WCF 在執行驗證時，將憑證視為受信任的憑證。</span><span class="sxs-lookup"><span data-stu-id="a9085-125">This will allow WCF to treat the certificate as a trusted certificate when performing authentication.</span></span>  
  
### <a name="to-call-the-service-passing-username-and-password"></a><span data-ttu-id="a9085-126">若要呼叫服務傳遞使用者名稱和密碼</span><span class="sxs-lookup"><span data-stu-id="a9085-126">To call the service passing username and password</span></span>  
  
1.  <span data-ttu-id="a9085-127">用戶端應用程式必須提示使用者輸入其使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="a9085-127">The client application must prompt the user for their username and password.</span></span> <span data-ttu-id="a9085-128">下列程式碼會要求使用者輸入使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="a9085-128">The following code asks the user for username and password.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="a9085-129">由於密碼會在輸入時顯示，這個程式碼不應在實際環境中使用。</span><span class="sxs-lookup"><span data-stu-id="a9085-129">This code should not be used in production as the password is displayed while being entered.</span></span>  
  
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
  
2.  <span data-ttu-id="a9085-130">指定用戶端的認證，以建立用戶端 Proxy 的執行個體，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="a9085-130">Create an instance of the client proxy specifying the client’s credentials as shown in the following code:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a9085-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9085-131">See Also</span></span>  
 <span data-ttu-id="a9085-132"><<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`></span><span class="sxs-lookup"><span data-stu-id="a9085-132"><<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`></span></span>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.SecurityMode>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>  
 <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>  
 <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>  
 [<span data-ttu-id="a9085-133">使用基本驗證的傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="a9085-133">Transport Security with Basic Authentication</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)  
 [<span data-ttu-id="a9085-134">分散式應用程式安全性</span><span class="sxs-lookup"><span data-stu-id="a9085-134">Distributed Application Security</span></span>](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)  
 [<span data-ttu-id="a9085-135">\<wsHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="a9085-135">\<wsHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
