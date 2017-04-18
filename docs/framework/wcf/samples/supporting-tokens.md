---
title: "支援權杖 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 65a8905d-92cc-4ab0-b6ed-1f710e40784e
caps.latest.revision: 29
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 29
---
# 支援權杖
這個支援權杖範例會示範如何將其他權杖加入至使用 WS\-Security 的訊息。  範例除了使用者名稱安全性權杖之外，還會新增 X.509 二進位安全性權杖。  權杖會在 WS\-Security 訊息標頭中從用戶端傳遞至服務，而且使用與 X.509 安全性權杖相關聯的私密金鑰簽署該訊息的一部分，以便向接收者證明持有 X.509 憑證。  在必須有多個宣告與訊息產生關聯才能驗證或授權傳送者的情況下，這將十分有幫助。  服務會實作定義要求\-回覆通訊模式的合約。  
  
## 示範  
 範例會示範下列情況：  
  
-   用戶端如何傳遞其他安全性權杖給服務。  
  
-   伺服器如何存取與其他安全性權杖相關聯的宣告。  
  
-   如何使用伺服器的 X.509 憑證保護用於訊息加密和簽章的對稱金鑰。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
## 用戶端透過使用者名稱權杖和支援的 X.509 安全性權杖進行驗證  
 服務會公開用來通訊的單一端點，此端點是使用 `BindingHelper` 和 `EchoServiceHost` 類別，透過程式設計所建立的。  端點是由位址、繫結及合約所組成。  繫結是透過使用 `SymmetricSecurityBindingElement` 和 `HttpTransportBindingElement` 的自訂繫結所設定。  這個範例會設定 `SymmetricSecurityBindingElement`，使其在傳輸期間使用服務 X.509 憑證來保護對稱金鑰，以及在 WS\-Security 訊息標頭中傳遞 `UserNameToken` 以及支援的 `X509SecurityToken`。  對稱金鑰會用來加密訊息本文和使用者名稱安全性權杖。  支援權杖會包含在 WS\-Security 訊息標頭中，當做其他二進位安全性權杖傳遞。  支援權杖的真實性是使用與支援之 X.509 安全性權杖相關聯的私密金鑰來簽署訊息的一部分，而獲得證明。  
  
```  
public static Binding CreateMultiFactorAuthenticationBinding()  
{  
    HttpTransportBindingElement httpTransport = new HttpTransportBindingElement();  
  
    // the message security binding element will be configured to require 2 tokens:  
    // 1) A username-password encrypted with the service token  
    // 2) A client certificate used to sign the message  
  
    // Instantiate a binding element that will require the username/password token in the message (encrypted with the server cert)  
    SymmetricSecurityBindingElement messageSecurity = SecurityBindingElement.CreateUserNameForCertificateBindingElement();  
  
    // Create supporting token parameters for the client X509 certificate.  
    X509SecurityTokenParameters clientX509SupportingTokenParameters = new X509SecurityTokenParameters();  
    // Specify that the supporting token is passed in message send by the client to the service  
    clientX509SupportingTokenParameters.InclusionMode = SecurityTokenInclusionMode.AlwaysToRecipient;  
    // Turn off derived keys  
    clientX509SupportingTokenParameters.RequireDerivedKeys = false;  
    // Augment the binding element to require the client's X509 certificate as an endorsing token in the message  
    messageSecurity.EndpointSupportingTokenParameters.Endorsing.Add(clientX509SupportingTokenParameters);  
  
    // Create a CustomBinding based on the constructed security binding element.  
    return new CustomBinding(messageSecurity, httpTransport);  
}  
  
```  
  
 此行為會指定要用於用戶端驗證的服務認證，以及服務 X.509 憑證的相關資訊。  此範例會使用 `CN=localhost` 做為服務 X.509 憑證中的主體名稱。  
  
```  
override protected void InitializeRuntime()  
{  
    // Extract the ServiceCredentials behavior or create one.  
    ServiceCredentials serviceCredentials =   
        this.Description.Behaviors.Find<ServiceCredentials>();  
    if (serviceCredentials == null)  
    {  
        serviceCredentials = new ServiceCredentials();  
        this.Description.Behaviors.Add(serviceCredentials);  
    }  
  
    // Set the service certificate  
    serviceCredentials.ServiceCertificate.SetCertificate(  
                                       "CN=localhost");  
  
/*  
Setting the CertificateValidationMode to PeerOrChainTrust means that if the certificate is in the Trusted People store, then it will be trusted without performing a validation of the certificate's issuer chain. This setting is used here for convenience so that the sample can be run without having to have certificates issued by a certification authority (CA).  
This setting is less secure than the default, ChainTrust. The security implications of this setting should be carefully considered before using PeerOrChainTrust in production code.  
*/  
    serviceCredentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
  
    // Create the custom binding and add an endpoint to the service.  
    Binding multipleTokensBinding =  
         BindingHelper.CreateMultiFactorAuthenticationBinding();  
    this.AddServiceEndpoint(typeof(IEchoService),   
                          multipleTokensBinding, string.Empty);  
    base.InitializeRuntime();  
}  
```  
  
 服務程式碼：  
  
```  
[ServiceBehavior(IncludeExceptionDetailInFaults = true)]  
public class EchoService : IEchoService  
{  
    public string Echo()  
    {  
        string userName;  
        string certificateSubjectName;  
        GetCallerIdentities(  
            OperationContext.Current.ServiceSecurityContext,   
            out userName,   
            out certificateSubjectName);  
            return String.Format("Hello {0}, {1}",   
                    userName, certificateSubjectName);  
    }  
  
    public void Dispose()  
    {  
    }  
  
    bool TryGetClaimValue<TClaimResource>(ClaimSet claimSet,   
            string claimType, out TClaimResource resourceValue)  
            where TClaimResource : class  
    {  
        resourceValue = default(TClaimResource);  
        IEnumerable<Claim> matchingClaims =   
            claimSet.FindClaims(claimType, Rights.PossessProperty);  
        if(matchingClaims == null)  
            return false;  
        IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();  
        if (enumerator.MoveNext())  
        {  
            resourceValue =   
              (enumerator.Current.Resource == null) ? null :   
              (enumerator.Current.Resource as TClaimResource);  
            return true;  
        }  
        else  
        {  
            return false;  
        }  
    }  
  
    // Returns the username and certificate subject name provided by   
    //the client  
    void GetCallerIdentities(ServiceSecurityContext   
        callerSecurityContext,   
        out string userName, out string certificateSubjectName)  
    {  
        userName = null;  
        certificateSubjectName = null;  
  
       // Look in all the claimsets in the authorization context  
       foreach (ClaimSet claimSet in   
               callerSecurityContext.AuthorizationContext.ClaimSets)  
       {  
            if (claimSet is WindowsClaimSet)  
            {  
                // Try to find a Name claim. This will have been   
                // generated from the windows username.  
                string tmpName;  
                if (TryGetClaimValue<string>(claimSet, ClaimTypes.Name,   
                                                      out tmpName))  
                {  
                    userName = tmpName;  
                }  
            }  
            else if (claimSet is X509CertificateClaimSet)  
            {  
                // Try to find an X500DisinguishedName claim. This will   
                // have been generated from the client certificate.  
                X500DistinguishedName tmpDistinguishedName;  
                if (TryGetClaimValue<X500DistinguishedName>(claimSet,   
                               ClaimTypes.X500DistinguishedName,   
                               out tmpDistinguishedName))  
                {  
                    certificateSubjectName = tmpDistinguishedName.Name;  
                }  
            }  
        }  
    }  
}   
```  
  
 用戶端端點與服務端點的設定方式相似。  用戶端會使用相同的 `BindingHelper` 類別來建立繫結。  其餘的設定工作則在 `Client` 類別中進行。  用戶端會將使用者名稱安全性權杖和支援之 X.509 安全性權杖的相關資訊，以及安裝程式碼中的服務 X.509 憑證相關資訊，設定為用戶端端點行為集合。  
  
```  
 static void Main()  
 {  
     // Create the custom binding and an endpoint address for   
     // the service.  
     Binding multipleTokensBinding =   
         BindingHelper.CreateMultiFactorAuthenticationBinding();  
         EndpointAddress serviceAddress = new EndpointAddress(  
         "http://localhost/servicemodelsamples/service.svc");  
       ChannelFactory<IEchoService> channelFactory = null;  
       IEchoService client = null;  
  
       Console.WriteLine("Username authentication required.");  
       Console.WriteLine(  
         "Provide a valid machine or domain account. [domain\\user]");  
       Console.WriteLine("   Enter username:");  
       string username = Console.ReadLine();  
       Console.WriteLine("   Enter password:");  
       string password = "";  
       ConsoleKeyInfo info = Console.ReadKey(true);  
       while (info.Key != ConsoleKey.Enter)  
       {  
           if (info.Key != ConsoleKey.Backspace)  
           {  
               if (info.KeyChar != '\0')  
               {  
                   password += info.KeyChar;  
                }  
                info = Console.ReadKey(true);  
            }  
            else if (info.Key == ConsoleKey.Backspace)  
            {  
                if (password != "")  
                {  
                    password =   
                       password.Substring(0, password.Length - 1);  
                }  
                info = Console.ReadKey(true);  
            }  
         }  
         for (int i = 0; i < password.Length; i++)  
            Console.Write("*");  
         Console.WriteLine();  
         try  
         {  
           // Create a proxy with the previously create binding and   
           // endpoint address  
              channelFactory =   
                 new ChannelFactory<IEchoService>(  
                     multipleTokensBinding, serviceAddress);  
           // configure the username credentials, the client   
           // certificate and the server certificate on the channel   
           // factory   
           channelFactory.Credentials.UserName.UserName = username;  
           channelFactory.Credentials.UserName.Password = password;  
           channelFactory.Credentials.ClientCertificate.SetCertificate(  
           "CN=client.com", StoreLocation.CurrentUser, StoreName.My);  
              channelFactory.Credentials.ServiceCertificate.SetDefaultCertificate(  
           "CN=localhost", StoreLocation.LocalMachine, StoreName.My);  
           client = channelFactory.CreateChannel();  
           Console.WriteLine("Echo service returned: {0}",   
                                           client.Echo());  
  
           ((IChannel)client).Close();  
           channelFactory.Close();  
        }  
        catch (CommunicationException e)  
        {  
         Abort((IChannel)client, channelFactory);  
         // if there is a fault then print it out  
         FaultException fe = null;  
         Exception tmp = e;  
         while (tmp != null)  
         {  
            fe = tmp as FaultException;  
            if (fe != null)  
            {  
                break;  
            }  
            tmp = tmp.InnerException;  
        }  
        if (fe != null)  
        {  
           Console.WriteLine("The server sent back a fault: {0}",   
         fe.CreateMessageFault().Reason.GetMatchingTranslation().Text);  
        }  
        else  
        {  
         Console.WriteLine("The request failed with exception: {0}",e);  
        }  
    }  
    catch (TimeoutException)  
    {  
        Abort((IChannel)client, channelFactory);  
        Console.WriteLine("The request timed out");  
    }  
    catch (Exception e)  
    {  
         Abort((IChannel)client, channelFactory);  
          Console.WriteLine(  
          "The request failed with unexpected exception: {0}", e);  
    }  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
}  
```  
  
## 顯示呼叫端的資訊  
 若要顯示呼叫者的資訊，您可以使用 `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets`，如下列程式碼所示。  `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` 包含與目前呼叫者關聯的授權宣告。  [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 會自動為訊息中所收到的每個權杖提供這些宣告。  
  
```  
bool TryGetClaimValue<TClaimResource>(ClaimSet claimSet, string   
                         claimType, out TClaimResource resourceValue)  
    where TClaimResource : class  
{  
    resourceValue = default(TClaimResource);  
    IEnumerable<Claim> matchingClaims =   
    claimSet.FindClaims(claimType, Rights.PossessProperty);  
    if (matchingClaims == null)  
          return false;  
    IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();  
    if (enumerator.MoveNext())  
    {  
        resourceValue = (enumerator.Current.Resource == null) ? null : (enumerator.Current.Resource as TClaimResource);  
        return true;  
    }  
    else  
    {  
         return false;  
    }  
}  
  
// Returns the username and certificate subject name provided by the client  
void GetCallerIdentities(ServiceSecurityContext callerSecurityContext, out string userName, out string certificateSubjectName)  
{  
    userName = null;  
    certificateSubjectName = null;  
  
    // Look in all the claimsets in the authorization context  
    foreach (ClaimSet claimSet in   
      callerSecurityContext.AuthorizationContext.ClaimSets)  
    {  
        if (claimSet is WindowsClaimSet)  
        {  
            // Try to find a Name claim. This will have been generated   
            //from the windows username.  
            string tmpName;  
            if (TryGetClaimValue<string>(claimSet, ClaimTypes.Name,   
                                                     out tmpName))  
            {  
                userName = tmpName;  
            }  
        }  
        else if (claimSet is X509CertificateClaimSet)  
         {  
            //Try to find an X500DisinguishedName claim.   
            //This will have been generated from the client   
            //certificate.  
            X500DistinguishedName tmpDistinguishedName;  
            if (TryGetClaimValue<X500DistinguishedName>(claimSet,   
               ClaimTypes.X500DistinguishedName,   
               out tmpDistinguishedName))  
            {  
                    certificateSubjectName = tmpDistinguishedName.Name;  
            }  
        }  
    }  
}  
```  
  
## 執行範例  
 當您執行範例時，用戶端首先會提示您提供使用者名稱權杖的使用者名稱和密碼。  請務必提供系統帳戶的正確值，因為服務上的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會將使用者名稱權杖中提供的值對應至系統所提供的身分識別。  然後，用戶端便會顯示服務的回應。  在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。  
  
## 設定批次檔  
 這個範例隨附的 Setup.bat 批次檔可讓您使用相關的憑證設定伺服器，以執行需要伺服器憑證安全性的網際網路資訊服務 \(IIS\) 裝載應用程式。  這個批次檔必須經過修改才能跨機器運作，或在非裝載的情況下運作。  
  
 下面提供批次檔的各區段簡要概觀，讓您將批次檔修改為可在適當的組態下執行。  
  
### 建立用戶端憑證  
 下列 Setup.bat 批次檔中的程式行會建立要使用的用戶端憑證。  `%CLIENT_NAME%` 變數會指定用戶端憑證的主體。  這個範例使用 "client.com" 做為主體名稱。  
  
 憑證會儲存在 `CurrentUser` 存放區位置下的 My \(Personal\) 存放區中。  
  
```  
echo ************  
echo making client cert  
echo ************  
makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
```  
  
### 將用戶端憑證安裝至伺服器的受信任存放區中  
 Setup.bat 批次檔中的下列程式行會將用戶端憑證複製到伺服器的受信任人存放區。  這是必要步驟，因為伺服器系統並未隱含信任 Makecert.exe 產生的憑證。  如果您已經有一個以用戶端信任的根憑證 \(例如 Microsoft 所發行的憑證\) 為基礎的憑證，就不需要這個將伺服器憑證填入用戶端憑證存放區的步驟。  
  
```  
echo ************  
echo copying client cert to server's CurrentUserstore  
echo ************  
certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople  
```  
  
### 建立伺服器憑證  
 下列 Setup.bat 批次檔中的程式行會建立要使用的伺服器憑證。  `%SERVER_NAME%`  變數會指定伺服器名稱。  您可以變更這個變數來指定自己的伺服器名稱。  這個批次檔中的預設值為 localhost。  
  
 憑證會儲存在 LocalMachine 存放區位置下的 My \(Personal\) 存放區中。  憑證會儲存在 IIS 裝載服務的 LocalMachine 存放區中。  對於自我裝載的服務，您應該以 CurrentUser 取代字串 LocalMachine，將批次檔改為在 CurrentUser 存放區的位置上儲存伺服器憑證。  
  
```  
echo ************  
echo Server cert setup starting  
echo %SERVER_NAME%  
echo ************  
echo making server cert  
echo ************  
makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
```  
  
### 將伺服器憑證安裝至用戶端的受信任憑證存放區中  
 Setup.bat 批次檔中的下列程式行會將伺服器憑證複製到用戶端受信任人的存放區。  這是必要步驟，因為用戶端系統並未隱含信任 Makecert.exe 產生的憑證。  如果您已經有一個以用戶端信任的根憑證 \(例如 Microsoft 所發行的憑證\) 為基礎的憑證，就不需要這個將伺服器憑證填入用戶端憑證存放區的步驟。  
  
```  
echo ************  
echo copying server cert to client's TrustedPeople store  
echo ************certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
```  
  
### 啟用對憑證私密金鑰的存取  
 若要啟用從 IIS 裝載服務對憑證私密金鑰進行的存取，就必須將私密金鑰的適當權限授與用於執行 IIS 裝載處理序的使用者帳戶。  Setup.bat 指令碼中的最後幾個步驟將會完成這個部分。  
  
```  
echo ************  
echo setting privileges on server certificates  
echo ************  
for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i  
set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE  
(ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET  
echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R  
iisreset  
```  
  
##### 若要安裝、建置及執行範例  
  
1.  確認您已經執行 [Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建立方案，請依照[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示進行。  
  
3.  若要在單一或跨電腦的組態中執行本範例，請使用下列指示。  
  
##### 若要在同一部機器上執行範例  
  
1.  在使用系統管理員權限執行的 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 命令提示字元內部，執行範例安裝資料夾中的 Setup.bat。  這會安裝執行範例所需的所有憑證。  
  
    > [!NOTE]
    >  Setup.bat 批次檔是設計用來從 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 命令提示字元執行。  在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 命令提示字元中設定的 PATH 環境變數會指向包含 Setup.bat 指令碼所需之可執行檔的目錄。  當您完成範例時，請務必執行 Cleanup.bat 以移除憑證。  其他安全性範例使用相同的憑證。  
  
2.  從 \\client\\bin 啟動 Client.exe。  用戶端活動會顯示在用戶端主控台應用程式上。  
  
3.  如果用戶端和服務無法通訊，請參閱[疑難排解提示](http://msdn.microsoft.com/zh-tw/8787c877-5e96-42da-8214-fa737a38f10b)。  
  
##### 若要跨機器執行範例  
  
1.  在服務機器上建立目錄。  使用網際網路資訊服務 \(IIS\) 管理工具，為這個目錄建立名為 servicemodelsamples 的虛擬應用程式。  
  
2.  將 \\inetpub\\wwwroot\\servicemodelsamples 中的服務程式檔複製至服務機器上的虛擬目錄中。  確定複製 \\bin 子目錄中的檔案。  同時將 Setup.bat、Cleanup.bat 和 ImportClientCert.bat 檔案複製到服務機器。  
  
3.  在用戶端機器上為用戶端二進位碼檔案建立一個目錄。  
  
4.  將用戶端程式檔複製到用戶端機器上的用戶端目錄。  同時，將 Setup.bat、Cleanup.bat 和 ImportServiceCert.bat 檔案複製到用戶端。  
  
5.  在伺服器上，於使用系統管理員權限開啟的 Visual Studio 命令提示字元中，執行 `setup.bat service`。  搭配 `service` 引數執行 `setup.bat` `` ，就會建立具有電腦完整網域名稱的服務憑證，並且將服務憑證匯出至名為 Service.cer 的檔案。  
  
6.  編輯 Web.config 以反映新的憑證名稱 \(在 [\<serviceCertificate\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) 元素的 `findValue` 屬性中\)，這個名稱與電腦的完整網域名稱相同。  
  
7.  從服務目錄中將 Service.cer 檔案複製至用戶端機器上的用戶端目錄。  
  
8.  在用戶端上，於使用系統管理員權限開啟的 Visual Studio 命令提示字元中，執行 `setup.bat client`。  搭配 `client` 引數執行 `setup.bat`，就會建立名為 Client.com 的用戶端憑證，並且會將用戶端憑證匯出至名為 Client.cer 的檔案。  
  
9. 在用戶端機器上的 Client.exe.config 檔案中，變更端點的位址值以符合服務的新位址。  若要這麼做，請使用伺服器的完整網域名稱取代 localhost。  
  
10. 從用戶端目錄將 Client.cer 檔案複製到伺服器上的服務目錄中。  
  
11. 在用戶端上執行 ImportServiceCert.bat。  這樣會將服務憑證從 Service.cer 檔案匯入至 CurrentUser \- TrustedPeople 存放區中。  
  
12. 在伺服器上執行 ImportClientCert.bat，這樣會從 Client.cer 檔案中將用戶端憑證匯入至 LocalMachine \- TrustedPeople 存放區中。  
  
13. 在用戶端機器上，從命令提示字元視窗啟動 Client.exe。  如果用戶端和服務無法通訊，請參閱[疑難排解提示](http://msdn.microsoft.com/zh-tw/8787c877-5e96-42da-8214-fa737a38f10b)。  
  
##### 若要在使用範例之後進行清除  
  
-   當您完成執行範例後，請執行範例資料夾中的 Cleanup.bat。  
  
> [!NOTE]
>  跨機器執行此範例時，這個指令碼不會移除用戶端上的服務憑證。  如果您已執行跨機器使用憑證的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 範例，請確定清除安裝在 CurrentUser \- TrustedPeople 存放區中的服務憑證。  若要這麼做，請使用下列命令：`certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`，例如：`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`。  
  
## 請參閱