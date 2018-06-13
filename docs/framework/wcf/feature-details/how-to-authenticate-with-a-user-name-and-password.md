---
title: HOW TO：使用使用者名稱與密碼來驗證
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF], user name and password
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
ms.openlocfilehash: b37d296312be4c7694a2db55d85dd618e3252f14
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493305"
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a>HOW TO：使用使用者名稱與密碼來驗證

本主題示範如何啟用 Windows Communication Foundation (WCF) 服務驗證用戶端使用 Windows 網域使用者名稱和密碼。 這裡假設您有運作中的自我裝載 WCF 服務。 如需範例，建立基本自我裝載的 WCF 服務，請參閱[入門教學課程](../../../../docs/framework/wcf/getting-started-tutorial.md)。 本主題假設服務是在程式碼中進行設定。 如果您想要看到的設定類似的服務，使用組態檔範例請參閱[訊息安全性使用者名稱](../../../../docs/framework/wcf/samples/message-security-user-name.md)  
  
 若要設定服務使用 Windows 網域使用者名和密碼驗證其用戶端，請使用 <xref:System.ServiceModel.WSHttpBinding>，並將其 `Security.Mode` 屬性設定為 `Message`。 此外，將使用者名稱和密碼從用戶端傳送至服務時，您必須指定要用來加密使用者名稱和密碼的 X 509 憑證。  
  
 在用戶端上，您必須提示使用者輸入使用者名稱和密碼，並在 WCF 用戶端 Proxy 上指定使用者的認證。  
  
## <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a>若要設定使用 Windows 網域使用者名稱和密碼進行驗證的 WCF 服務
  
1.  請建立 <xref:System.ServiceModel.WSHttpBinding> 的執行個體，將繫結的安全性模式設定為 `SecurityMode.Message`，將繫結的 `ClientCredentialType` 設定為 `MessageCredentialType.UserName`，然後將使用所設定之繫結的服務端點加入至服務主機，如下列程式碼所示：  
  
    ```  
    // ...  
    WSHttpBinding userNameBinding = new WSHttpBinding();  
    userNameBinding.Security.Mode = SecurityMode.Message;  
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;  
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");  
    // ...  
    ```  
  
2.  指定伺服器憑證，用以加密透過網路傳送之使用者名及密碼的資訊。 這個程式碼應直接加在上面程式碼之後。 下列範例會使用的憑證，會建立由 setup.bat 檔從[訊息安全性使用者名稱](../../../../docs/framework/wcf/samples/message-security-user-name.md)範例：  
  
    ```  
    // ...  
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");  
    // ...  
    ```  
  
     您可以使用自己的憑證，只需將程式碼修改成參考您的憑證。 如需有關建立及使用憑證，請參閱[使用憑證](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。 確認憑證是在本機電腦的 [受信任的人] 憑證存放區中。 您可以執行 mmc.exe，然後選取**檔案**，**新增/移除嵌入式管理單元...** 功能表項目。 在**新增或移除嵌入式管理單元**對話方塊中，選取**憑證嵌入式管理單元**按一下**新增**。 在 [憑證嵌入式管理單元] 對話方塊中選取**電腦帳戶**。 根據預設，從訊息安全性使用者名稱範例所產生的憑證位於 [個別/憑證] 資料夾中。  將為"localhost"下的 發行至資料行在 MMC 視窗中列出。 將拖放到憑證**受信任的人**資料夾。 這樣可讓 WCF 在執行驗證時，將憑證視為受信任的憑證。  
  
## <a name="to-call-the-service-passing-username-and-password"></a>若要呼叫服務傳遞使用者名稱和密碼  
  
1.  用戶端應用程式必須提示使用者輸入其使用者名稱和密碼。 下列程式碼會要求使用者輸入使用者名稱和密碼。  
  
    > [!WARNING]
    >  由於密碼會在輸入時顯示，這個程式碼不應在實際環境中使用。  
  
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
  
2.  指定用戶端的認證，以建立用戶端 Proxy 的執行個體，如下列程式碼所示：  
  
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
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.WSHttpBinding>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.SecurityMode>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>  
 <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>  
 <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>  
 [使用基本驗證的傳輸安全性](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)  
 [分散式應用程式安全性](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)  
 [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
