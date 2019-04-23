---
title: 服務身分識別範例
ms.date: 03/30/2017
ms.assetid: 79fa8c1c-85bb-4b67-bc67-bfaf721303f8
ms.openlocfilehash: 72068002572ff82d2f166ffdd79e455cec7a2961
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "59977856"
---
# <a name="service-identity-sample"></a>服務身分識別範例
這個服務身分識別範例示範如何設定服務的身分識別。 在設計階段，用戶端可以使用服務的中繼資料擷取身分識別，然後在執行階段，用戶端就可以驗證服務的身分識別。 服務身分識別的概念主要是允許用戶端在呼叫任何作業之前驗證服務，從而保護用戶端以免遭到未經驗證的呼叫。 在安全連線上，服務還會在允許用戶端存取之前驗證其認證，但這不是本範例的重點。 請參閱中的範例[用戶端](../../../../docs/framework/wcf/samples/client.md)，示範伺服器驗證。

> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。

 這個範例說明下列功能：

-   如何在服務的不同端點上設定不同類型的身分識別。 每個身分識別類型各有不同的功能。 要使用的身分識別類型取決於端點繫結上使用的安全性認證類型。

-   身分識別可在組態中以宣告方式設定，或是在程式碼中以命令方式指定。 對於用戶端和服務，通常都應該使用組態來設定身分識別。

-   如何在用戶端設定自訂身分識別。 自訂身分識別通常是對身分識別現有類型進行的自訂，這可讓用戶端檢查服務認證中提供的其他宣告資訊，以便在呼叫服務之前做出授權決策。

    > [!NOTE]
    >  這個範例會檢查特定憑證的身分識別 (名為 identity.com) 以及此憑證內含的 RSA 金鑰。 在用戶端的組態中使用憑證和 RSA 身分識別類型時，取得這些值的簡易方式是檢查這些值序列化所在之處的服務 WSDL。

 下列範例程式碼示範如何使用 WSHttpBinding，透過憑證的「網域名稱伺服器」(DNS) 來設定服務端點的身分識別。

```csharp
//Create a service endpoint and set its identity to the certificate's DNS
WSHttpBinding wsAnonbinding = new WSHttpBinding (SecurityMode.Message);
// Client are Anonymous to the service
wsAnonbinding.Security.Message.ClientCredentialType = MessageCredentialType.None;
WServiceEndpoint ep = serviceHost.AddServiceEndpoint(typeof(ICalculator),wsAnonbinding, String.Empty);
EndpointAddress epa = new EndpointAddress(dnsrelativeAddress,EndpointIdentity.CreateDnsIdentity("identity.com"));
ep.Address = epa;
```

 身分識別也可以在 App.config 檔的組態中指定。 下列範例示範如何設定服務端點的 UPN (使用者主體名稱) 身分識別。

```xml
<endpoint address="upnidentity"
        behaviorConfiguration=""
        binding="wsHttpBinding"
        bindingConfiguration="WSHttpBinding_Windows"
        name="WSHttpBinding_ICalculator_Windows"
        contract="Microsoft.ServiceModel.Samples.ICalculator">
  <!-- Set the UPN identity for this endpoint -->
  <identity>
      <userPrincipalName value="host\myservice.com" />
  </identity >
</endpoint>
```

 透過從 <xref:System.ServiceModel.EndpointIdentity> 和 <xref:System.ServiceModel.Security.IdentityVerifier> 類別衍生的方式，可以在用戶端上設定自訂身分識別。 在概念上，可以將 <xref:System.ServiceModel.Security.IdentityVerifier> 類別視為服務之 `AuthorizationManager` 類別的用戶端對等類別。 下列程式碼範例示範 `OrgEndpointIdentity` 的實作，它會在伺服器憑證的主體名稱中儲存要符合的組織名稱。 在 `CheckAccess` 類別上的 `CustomIdentityVerifier` 方法中，會針對組織名稱進行授權檢查。

```csharp
// This custom EndpointIdentity stores an organization name
public class OrgEndpointIdentity : EndpointIdentity
{
    private string orgClaim;
    public OrgEndpointIdentity(string orgName)
    {
        orgClaim = orgName;
    }
    public string OrganizationClaim
    {
        get { return orgClaim; }
        set { orgClaim = value; }
    }
}

//This custom IdentityVerifier uses the supplied OrgEndpointIdentity to
//check that X.509 certificate's distinguished name claim contains
//the organization name e.g. the string value "O=Contoso"
class CustomIdentityVerifier : IdentityVerifier
{
    public override bool CheckAccess(EndpointIdentity identity, AuthorizationContext authContext)
    {
        bool returnvalue = false;
        foreach (ClaimSet claimset in authContext.ClaimSets)
        {
            foreach (Claim claim in claimset)
            {
                if (claim.ClaimType == "http://schemas.microsoft.com/ws/2005/05/identity/claims/x500distinguishedname")
                {
                    X500DistinguishedName name = (X500DistinguishedName)claim.Resource;
                    if (name.Name.Contains(((OrgEndpointIdentity)identity).OrganizationClaim))
                    {
                        Console.WriteLine("Claim Type: {0}",claim.ClaimType);
                        Console.WriteLine("Right: {0}", claim.Right);
                        Console.WriteLine("Resource: {0}",claim.Resource);
                        Console.WriteLine();
                        returnvalue = true;
                    }
                }
            }
        }
        return returnvalue;
    }
}
```

 這個範例會使用名為 identity.com 的憑證，其位於語言特定的身分識別方案資料夾中。

### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例

1. 請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。

2. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。

3. 若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。

### <a name="to-run-the-sample-on-the-same-computer"></a>若要在同一部電腦上執行範例

1. 在 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 或 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上，使用 MMC 嵌入式管理單元工具，將身分識別方案資料夾中的 Identity.pfx 憑證檔匯入至 LocalMachine/My (Personal) 憑證存放區。 這個檔案有密碼保護。 它會在匯入時要求您提供密碼。 型別`xyz`在密碼方塊。 如需詳細資訊，請參閱[如何：使用 MMC 嵌入式管理單元檢視憑證](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)主題。 完成之後，執行 Setup.bat 在開發人員命令提示字元中適用於 Visual Studio 系統管理員權限，可將此憑證複製到 CurrentUser/Trusted People 存放區可用於用戶端上。

2. 在  [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]，從範例安裝資料夾，在 Visual Studio 2012 的命令提示字元，以系統管理員權限執行 Setup.bat。 這會安裝執行範例所需的所有憑證。

    > [!NOTE]
    >  Setup.bat 批次檔被設計來從 Visual Studio 2012 命令提示字元執行。 路徑環境變數設定在 Visual Studio 2012 命令提示字元會指向包含 Setup.bat 指令碼所需的可執行檔的目錄。 當您完成範例時，請務必執行 Cleanup.bat 以移除憑證。 其他安全性範例使用相同的憑證。  
  
3. 從 \service\bin 目錄啟動 Service.exe。 確定服務指出它已準備好，並按下對顯示的提示\<Enter > 終止服務。  
  
4. 從 \client\bin 目錄啟動 Client.exe，或是在 Visual Studio 中按下 F5 鍵來建置並執行。 用戶端活動會顯示在用戶端主控台應用程式上。  
  
5. 如果用戶端和服務能夠進行通訊，請參閱[的 WCF 範例的疑難排解秘訣](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。  
  
### <a name="to-run-the-sample-across-computers"></a>若要跨電腦執行範例  
  
1. 建置範例的用戶端部分之前，請務必在 Client.cs 檔案內的 `CallServiceCustomClientIdentity` 方法中變更服務端點位址的值， 然後才建置範例。  
  
2. 在服務電腦上建立目錄。  
  
3. 將服務程式檔從 service\bin 複製到服務電腦上的目錄。 同時，將 Setup.bat 和 Cleanup.bat 檔案複製到服務電腦中。  
  
4. 在用戶端電腦上為用戶端二進位碼檔案建立一個目錄。  
  
5. 將用戶端程式檔複製到用戶端電腦上的用戶端目錄。 同時，將 Setup.bat、Cleanup.bat 和 ImportServiceCert.bat 檔案複製到用戶端。  
  
6. 在服務上，執行`setup.bat service`在開發人員命令提示字元適用於 Visual Studio 開啟系統管理員權限。 執行`setup.bat`與`service`引數會建立具有電腦完整網域名稱的服務憑證，並將服務憑證匯出為名為 Service.cer 的檔案。  
  
7. 從服務目錄中將 Service.cer 檔案複製至用戶端電腦上的用戶端目錄。  
  
8. 在用戶端電腦上的 Client.exe.config 檔案中，變更端點的位址值以符合服務的新位址。 其中會有多個必須加以變更的執行個體。  
  
9. 在用戶端，以系統管理員權限開啟的 Visual studio 中開發人員命令提示字元執行 ImportServiceCert.bat。 這樣會將服務憑證從 Service.cer 檔案匯入至 CurrentUser - TrustedPeople 存放區中。  
  
10. 在服務電腦上，從命令提示字元啟動 Service.exe。  
  
11. 在用戶端電腦上，從命令提示字元啟動 Client.exe。 如果用戶端和服務能夠進行通訊，請參閱[的 WCF 範例的疑難排解秘訣](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。  
  
### <a name="to-clean-up-after-the-sample"></a>若要在使用範例之後進行清除  
  
-   當您完成執行範例後，請執行範例資料夾中的 Cleanup.bat。  
  
    > [!NOTE]
    >  跨電腦執行此範例時，這個指令碼不會移除用戶端上的服務憑證。 如果您已執行跨電腦使用憑證的 Windows Communication Foundation (WCF) 範例，請務必清除已安裝在 CurrentUser-TrustedPeople 存放區的服務憑證。 若要這樣做，請使用下列命令：`certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` 例如： `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`。
