---
title: HOW TO：指定通道安全性認證
ms.date: 03/30/2017
ms.assetid: f8e03f47-9c4f-4dd5-8f85-429e6d876119
ms.openlocfilehash: f4c2977fe5bc819ff7e9b7a8030b2c2e20b71429
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2018
ms.locfileid: "50201461"
---
# <a name="how-to-specify-channel-security-credentials"></a>HOW TO：指定通道安全性認證
Windows Communication Foundation (WCF) 服務 Moniker 允許 COM 應用程式呼叫 WCF 服務。 大部分的 WCF 服務要求用戶端指定用於驗證和授權的認證。 當從 WCF 用戶端呼叫 WCF 服務，您可以在 managed 程式碼或應用程式組態檔中指定這些認證。 當從 COM 應用程式呼叫 WCF 服務，您可以使用<xref:System.ServiceModel.ComIntegration.IChannelCredentials>介面來指定認證。 本主題將說明各種使用 <xref:System.ServiceModel.ComIntegration.IChannelCredentials> 介面指定認證的方式。  
  
> [!NOTE]
>  <xref:System.ServiceModel.ComIntegration.IChannelCredentials> 是以 IDispatch 為基礎的介面，因此您無法在 Visual Studio 環境中使用 IntelliSense 功能。  
  
 這篇文章會使用 WCF 服務中定義[訊息安全性範例](../../../../docs/framework/wcf/samples/message-security-sample.md)。  
  
### <a name="to-specify-a-client-certificate"></a>若要指定用戶端憑證  
  
1.  執行 Message Security 目錄中的 Setup.bat 檔案以建立並安裝必要的測試憑證。  
  
2.  開啟「訊息安全性」專案。  
  
3.  新增`[ServiceBehavior(Namespace=``http://Microsoft.ServiceModel.Samples``)]`至`ICalculator`介面定義。  
  
4.  新增`bindingNamespace=``http://Microsoft.ServiceModel.Samples`至服務的 App.config 中的端點標記。  
  
5.  建置「訊息安全性範例」並執行 Service.exe。 使用 Internet Explorer 並瀏覽至服務的 URI (http://localhost:8000/ServiceModelSamples/Service)以確保服務正在運作。  
  
6.  開啟 Visual Basic 6.0，並建立新的標準 .exe 檔案。 將按鈕加入至表單中，然後按兩下這個按鈕，將下列程式碼加入至 Click 處理常式：  
  
    ```  
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
        monString = monString + ", binding=BasicHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
        Set monikerProxy = GetObject(monString)  
  
        'Set the Service Certificate.  
     monikerProxy.ChannelCredentials.SetServiceCertificateAuthentication "CurrentUser", "NoCheck", "PeerOrChainTrust"  
    monikerProxy.ChannelCredentials.SetDefaultServiceCertificateFromStore "CurrentUser", "TrustedPeople", "FindBySubjectName", "localhost"  
  
        'Set the Client Certificate.  
        monikerProxy.ChannelCredentials.SetClientCertificateFromStoreByName "CN=client.com", "CurrentUser", "My"  
        MsgBox monikerProxy.Add(3, 4)  
    ```  
  
7.  執行 Visual Basic 應用程式及驗證結果。  
  
     Visual Basic 應用程式將會顯示含有呼叫 Add(3, 4) 之結果的訊息方塊。 您也可以使用 <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29> 或 <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29> 替代 <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> 來設定用戶端憑證：  
  
    ```  
    monikerProxy.ChannelCredentials.SetClientCertificateFromFile "C:\MyClientCert.pfx", "password", "DefaultKeySet"  
    ```  
  
> [!NOTE]
>  用戶端憑證必須在執行用戶端的電腦上受信任，這個呼叫才會有作用。  
  
> [!NOTE]
>  如果 Moniker 的格式錯誤或服務無法使用，則呼叫 `GetObject` 時將會傳回「無效的語法」錯誤。 如果您收到這個錯誤，請確定您所使用的 Moniker 正確無誤，而且此服務為可用狀態。  
  
### <a name="to-specify-user-name-and-password"></a>若要指定使用者名稱和密碼  
  
1.  將服務的 App.config 檔案修改為使用 `wsHttpBinding`。 這對使用者名稱和密碼驗證而言是必要的動作：  
  
  
  
2.  將 `clientCredentialType` 設定為使用者名稱：  
  
  
  
3.  開啟 Visual Basic 6.0，並建立新的標準 .exe 檔案。 將按鈕加入至表單中，然後按兩下這個按鈕，將下列程式碼加入至 Click 處理常式：  
  
    ```  
    monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
    monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set monikerProxy = GetObject(monString)  
  
    monikerProxy.ChannelCredentials.SetServiceCertificateAuthentication "CurrentUser", "NoCheck", "PeerOrChainTrust"  
    monikerProxy.ChannelCredentials.SetUserNameCredential "username", "password"  
  
    MsgBox monikerProxy.Add(3, 4)  
    ```  
  
4.  執行 Visual Basic 應用程式及驗證結果。 Visual Basic 應用程式將會顯示含有呼叫 Add(3, 4) 之結果的訊息方塊。  
  
    > [!NOTE]
    >  在這個範例的服務 Moniker 中指定的繫結已經變更為 WSHttpBinding_ICalculator。 另請注意，您必須在對 <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29> 的呼叫中提供有效的使用者名稱和密碼。  
  
### <a name="to-specify-windows-credentials"></a>若要指定 Windows 認證  
  
1.  在服務的 App.config 檔案中，將 `clientCredentialType` 設定為 Windows：  
  
  
  
2.  開啟 Visual Basic 6.0，並建立新的標準 .exe 檔案。 將按鈕加入至表單中，然後按兩下這個按鈕，將下列程式碼加入至 Click 處理常式：  
  
    ```  
    monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
    monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", upnidentity=domain\userID"  
  
    Set monikerProxy = GetObject(monString)  
     monikerProxy.ChannelCredentials.SetWindowsCredential "domain", "userID", "password", 1, True  
  
    MsgBox monikerProxy.Add(3, 4)  
    ```  
  
3.  執行 Visual Basic 應用程式及驗證結果。 Visual Basic 應用程式將會顯示含有呼叫 Add(3, 4) 之結果的訊息方塊。  
  
    > [!NOTE]
    >  您必須以有效值取代 "domain"、"userID" 和 "password"。  
  
### <a name="to-specify-an-issue-token"></a>指定發行權杖  
  
1.  發行權杖僅適用於使用聯合安全性的應用程式。 如需聯合安全性的詳細資訊，請參閱[聯合與發行權杖](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)並[聯合範例](../../../../docs/framework/wcf/samples/federation-sample.md)。  
  
     下列 Visual Basic 程式碼範例示範如何呼叫 <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> 方法：  
  
    ```  
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/SomeService/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://SomeService.Samples"  
        monString = monString + ", binding=WSHttpBinding_ISomeContract, bindingNamespace=http://SomeService.Samples"  
  
        Set monikerProxy = GetObject(monString)  
    monikerProxy.SetIssuedToken("http://somemachine/sts", "bindingType", "binding")  
    ```  
  
     如需此方法之參數的詳細資訊，請參閱 <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>。  
  
## <a name="see-also"></a>另請參閱  
 [同盟](../../../../docs/framework/wcf/feature-details/federation.md)  
 [如何：設定同盟服務的認證](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [如何：建立同盟用戶端](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [訊息安全性](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 [繫結和安全性](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
