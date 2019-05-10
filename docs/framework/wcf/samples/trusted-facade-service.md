---
title: 信任的外觀服務
ms.date: 03/30/2017
ms.assetid: c34d1a8f-e45e-440b-a201-d143abdbac38
ms.openlocfilehash: 27e541c0c9738e93678d32081e49798944160715
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665979"
---
# <a name="trusted-facade-service"></a>信任的外觀服務
此案例的範例示範如何呼叫者的身分識別資訊從一個服務到另一個使用 Windows Communication Foundation (WCF) 安全性基礎結構。  
  
 這是使用外觀服務將服務提供的功能公開至公用網路的一般設計模式。 外觀服務通常是在周邊網路中 (也就是非警戒區域和遮蔽式子網路)，並會與實作商務邏輯並可存取內部資料的後端服務進行通訊。 外觀服務和後端服務之間的通訊通道會經過防火牆，而且其目的通常僅限一項。  
  
 本範例由以下元件組成：  
  
- 計算機用戶端  
  
- 計算機外觀服務  
  
- 計算機後端服務  
  
 外觀服務主要負責驗證要求及呼叫者。 在成功驗證之後，會使用周邊網路到內部網路之間的控制式通訊通道，將要求轉遞至後端服務。 做為轉遞要求的一部分，外觀服務會包含呼叫者身分識別的相關資訊，讓後端服務可以用此資訊進行處理。 將使用訊息 `Username` 標頭內的 `Security` 安全性權杖來傳輸呼叫者身分識別。 此範例會使用 WCF 安全性基礎結構傳輸及擷取這項資訊從`Security`標頭。  
  
> [!IMPORTANT]
>  後端服務會信任外觀服務以驗證呼叫者。 因此，後端服務不會再次驗證呼叫者，而是會在轉遞要求中使用外觀服務提供的身分識別資訊。 由於此信任關係，後端服務必須驗證外觀服務，確保轉遞的訊息是來自可信任的來源，在此例中也就是指外觀服務。  
  
## <a name="implementation"></a>實作  
 在本範例中有兩個通訊路徑。 第一個是在用戶端和外觀服務之間，第二個則是在外觀服務和後端服務之間。  
  
### <a name="communication-path-between-client-and-faade-service"></a>用戶端和外觀服務之間的通訊路徑  
 用戶端到外觀服務的通訊路徑會搭配使用 `wsHttpBinding` 和 `UserName` 用戶端認證類型。 這表示用戶端透過使用者名稱和密碼來驗證外觀服務，而外觀服務使用 X.509 憑證來驗證用戶端。 繫結組態如下列範例所示。  
  
```xml  
<bindings>  
  <wsHttpBinding>  
    <binding name="Binding1">  
      <security mode="Message">  
        <message clientCredentialType="UserName"/>  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
```  
  
 外觀服務會使用自訂 `UserNamePasswordValidator` 實作驗證呼叫者。 針對示範用途，驗證時只會確定呼叫者的使用者名稱和呈現的密碼相符。 在實際狀況中，可能會使用 Active Directory 或自訂 ASP.NET 成員資格提供者來驗證使用者。 驗證器實作是在 `FacadeService.cs` 檔案中。  
  
```  
public class MyUserNamePasswordValidator : UserNamePasswordValidator  
{  
    public override void Validate(string userName, string password)  
    {  
        // check that username matches password  
        if (null == userName || userName != password)  
        {  
            Console.WriteLine("Invalid username or password");  
            throw new SecurityTokenValidationException(  
                       "Invalid username or password");  
        }  
    }  
}  
```  
  
 已將自訂驗證器設定為在外觀服務組態檔的 `serviceCredentials` 行為內使用。 這個行為也可用來設定服務的 X.509 憑證。  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="FacadeServiceBehavior">  
      <!--The serviceCredentials behavior allows you to define -->  
      <!--a service certificate. -->  
      <!--A service certificate is used by the service to  -->  
      <!--authenticate itself to its clients and to provide  -->  
      <!--message protection. -->  
      <!--This configuration references the "localhost"  -->  
      <!--certificate installed during the setup instructions. -->  
      <serviceCredentials>  
        <serviceCertificate   
               findValue="localhost"   
               storeLocation="LocalMachine"   
               storeName="My"   
               x509FindType="FindBySubjectName" />  
        <userNameAuthentication userNamePasswordValidationMode="Custom"  
            customUserNamePasswordValidatorType=  
           "Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator,  
            FacadeService"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
### <a name="communication-path-between-faade-service-and-backend-service"></a>外觀服務和後端服務之間的通訊路徑  
 外觀服務到後端服務的通訊路徑會使用由數個繫結項目組成的 `customBinding` 。 此繫結會完成兩個動作。 第一，會驗證外觀服務和後端服務，確保通訊為安全而且是來自可信任的來源。 第二，也會傳輸 `Username` 安全性權杖內部的初始呼叫者身分識別。 在此情況下，只有初始呼叫者的使用者名稱會傳輸至後端服務，而訊息中不含密碼。 這是因為後端服務信任外觀服務，以在轉遞要求至呼叫者之前先驗證呼叫者。 由於外觀服務會對後端服務進行自我驗證，後端服務便會信任轉遞之要求中所含的資訊。  
  
 下列為此通訊路徑的繫結組態。  
  
```xml  
<bindings>  
  <customBinding>  
    <binding name="ClientBinding">  
      <security authenticationMode="UserNameOverTransport"/>  
      <windowsStreamSecurity/>  
      <tcpTransport/>  
    </binding>  
  </customBinding>  
</bindings>  
```  
  
 [\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)繫結項目會處理初始呼叫者的使用者名稱傳輸和擷取。 [ \<Windowsstreamsecurity 正在 >](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md)並[ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md)負責驗證外觀和後端服務和訊息保護。  
  
 若要轉遞要求，外觀服務實作必須提供初始呼叫者的使用者名稱，讓該 WCF 安全性基礎結構可將此轉送的訊息。 會在外觀服務實作中提供初始呼叫者的使用者名稱，方法是在用戶端 Proxy 執行個體 (外觀服務用此執行個體與後端服務通訊) 上的 `ClientCredentials` 屬性設定即可。  
  
 下列程式碼會顯示如何在外觀服務上實作 `GetCallerIdentity` 方法。 其他方法也使用相同的模式。  
  
```  
public string GetCallerIdentity()  
{  
    CalculatorClient client = new CalculatorClient();  
    client.ClientCredentials.UserName.UserName = ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    string result = client.GetCallerIdentity();  
    client.Close();  
    return result;  
}  
```  
  
 如前面程式碼所示，不會在 `ClientCredentials` 屬性中設定密碼，而只會設定使用者名稱。 WCF 安全性基礎結構會建立不含密碼的使用者名稱安全性權杖在此情況下，這就是所需在此案例中。  
  
 在後端服務上，必須驗證使用者名稱安全性權杖中所含的資訊。 根據預設，WCF 安全性會嘗試將使用者對應至 Windows 帳戶使用提供的密碼。 在此情況下，將不會提供密碼，而且驗證使用者名稱也不需要後端服務，這是因為外觀服務已經執行驗證了。 若要實作這項功能在 WCF 中，自訂`UserNamePasswordValidator`提供，它只會強制使用者名稱權杖中所指定，並不會執行任何額外的驗證。  
  
```  
public class MyUserNamePasswordValidator : UserNamePasswordValidator  
{  
    public override void Validate(string userName, string password)  
    {  
        // Ignore the password because it is empty,   
        // we trust the facade service to authenticate the client.  
        // Accept the username information here so that the   
        // application gets access to it.  
        if (null == userName)  
        {  
            Console.WriteLine("Invalid username");  
            throw new   
             SecurityTokenValidationException("Invalid username");  
        }  
    }  
}  
```  
  
 已將自訂驗證器設定為在外觀服務組態檔的 `serviceCredentials` 行為內使用。  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="BackendServiceBehavior">  
      <serviceCredentials>  
        <userNameAuthentication userNamePasswordValidationMode="Custom"  
           customUserNamePasswordValidatorType=  
          "Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator,   
           BackendService"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 若要擷取使用者名稱資訊以及與信任的外觀服務帳戶相關的資訊，後端服務實作會使用 `ServiceSecurityContext` 類別。 下列程式碼會顯示如何實作 `GetCallerIdentity` 方法。  
  
```  
public string GetCallerIdentity()  
{  
    // Facade service is authenticated using Windows authentication.  
    //Its identity is accessible.  
    // On ServiceSecurityContext.Current.WindowsIdentity.  
    string facadeServiceIdentityName =   
          ServiceSecurityContext.Current.WindowsIdentity.Name;  
  
    // The client name is transmitted using Username authentication on   
    //the message level without the password  
    // using a supporting encrypted UserNameToken.  
    // Claims extracted from this supporting token are available in   
    // ServiceSecurityContext.Current.AuthorizationContext.ClaimSets   
    // collection.  
    string clientName = null;  
    foreach (ClaimSet claimSet in   
        ServiceSecurityContext.Current.AuthorizationContext.ClaimSets)  
    {  
        foreach (Claim claim in claimSet)  
        {  
            if (claim.ClaimType == ClaimTypes.Name &&   
                                   claim.Right == Rights.Identity)  
            {  
                clientName = (string)claim.Resource;  
                break;  
            }  
        }  
    }  
    if (clientName == null)  
    {  
        // In case there was no UserNameToken attached to the request.  
        // In the real world implementation the service should reject   
        // this request.  
        return "Anonymous caller via " + facadeServiceIdentityName;  
    }  
  
    return clientName + " via " + facadeServiceIdentityName;  
}  
```  
  
 使用 `ServiceSecurityContext.Current.WindowsIdentity` 屬性擷取外觀服務的帳戶資訊。 若要存取初始呼叫者的相關資訊，後端服務會使用 `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` 屬性。 這個屬性會查詢型別為 `Identity` 的 `Name`宣告。 WCF 安全性基礎結構中所包含的資訊會自動產生此宣告`Username`安全性權杖。  
  
## <a name="running-the-sample"></a>執行範例  
 當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。 在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。 您可以在外觀和後端服務的主控台視窗中按 ENTER 鍵，即可關閉服務。  
  
```  
Username authentication required.  
Provide a valid machine or domain ac  
   Enter username:  
user  
   Enter password:  
****  
user via MyMachine\testaccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 信任的外觀案例範例所包含的 Setup.bat 批次檔可讓您使用相關的憑證設定伺服器，以執行需要憑證安全性的外觀服務並對用戶端自我驗證。 如需詳細資訊，請參閱本主題結尾的安裝程序。  
  
 下面會提供批次檔之不同區段的簡短概觀。  
  
- 建立伺服器憑證。  
  
     下列 Setup.bat 批次檔中的程式行會建立要使用的伺服器憑證。  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     `%SERVER_NAME%` 變數會指定伺服器名稱，預設值為 localhost。 憑證是儲存在 LocalMachine 存放區中。  
  
- 將外觀服務的憑證安裝至用戶端信任的憑證存放區。  
  
     下列程式行會將外觀服務的憑證複製到用戶端受信任人的存放區中。 這是必要步驟，因為用戶端系統並未隱含信任 Makecert.exe 產生的憑證。 如果您已經有一個以用戶端信任的根憑證 (例如 Microsoft 所發行的憑證) 為基礎的憑證，就不需要這個將伺服器憑證填入用戶端憑證的步驟。  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>若要在同一部機器上執行範例  
  
1. 確定路徑中包含 Makecert.exe 所在的資料夾。  
  
2. 從範例安裝資料夾執行 Setup.bat。 這會安裝執行範例所需的所有憑證。  
  
3. 從不同主控台視窗中的 \BackendService\bin 目錄啟動 BackendService.exe  
  
4. 從不同主控台視窗中的 \FacadeService\bin 目錄啟動 FacadeService.exe  
  
5. 從 \client\bin 啟動 Client.exe。 用戶端活動會顯示在用戶端主控台應用程式上。  
  
6. 如果用戶端和服務能夠進行通訊，請參閱[的 WCF 範例的疑難排解秘訣](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。  
  
#### <a name="to-clean-up-after-the-sample"></a>若要在使用範例之後進行清除  
  
1. 當您完成執行範例後，請執行範例資料夾中的 Cleanup.bat。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`  
