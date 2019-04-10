---
title: HOW TO：指定通道安全性認證
ms.date: 03/30/2017
ms.assetid: f8e03f47-9c4f-4dd5-8f85-429e6d876119
ms.openlocfilehash: 0bfbb71ade3822b9f504c2f89a41145ce0d435f6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59297976"
---
# <a name="how-to-specify-channel-security-credentials"></a><span data-ttu-id="44a81-102">HOW TO：指定通道安全性認證</span><span class="sxs-lookup"><span data-stu-id="44a81-102">How to: Specify Channel Security Credentials</span></span>
<span data-ttu-id="44a81-103">Windows Communication Foundation (WCF) 服務 Moniker 允許 COM 應用程式呼叫 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="44a81-103">The Windows Communication Foundation (WCF) Service Moniker allows COM applications to call WCF services.</span></span> <span data-ttu-id="44a81-104">大部分的 WCF 服務要求用戶端指定用於驗證和授權的認證。</span><span class="sxs-lookup"><span data-stu-id="44a81-104">Most WCF services require the client to specify credentials for authentication and authorization.</span></span> <span data-ttu-id="44a81-105">當從 WCF 用戶端呼叫 WCF 服務，您可以在 managed 程式碼或應用程式組態檔中指定這些認證。</span><span class="sxs-lookup"><span data-stu-id="44a81-105">When calling a WCF service from a WCF client, you can specify these credentials in managed code or in an application configuration file.</span></span> <span data-ttu-id="44a81-106">當從 COM 應用程式呼叫 WCF 服務，您可以使用<xref:System.ServiceModel.ComIntegration.IChannelCredentials>介面來指定認證。</span><span class="sxs-lookup"><span data-stu-id="44a81-106">When calling a WCF service from a COM application, you can use the <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface to specify credentials.</span></span> <span data-ttu-id="44a81-107">本主題將說明各種使用 <xref:System.ServiceModel.ComIntegration.IChannelCredentials> 介面指定認證的方式。</span><span class="sxs-lookup"><span data-stu-id="44a81-107">This topic will illustrate various ways to specify credentials using the <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface.</span></span>  
  
> [!NOTE]
>  <xref:System.ServiceModel.ComIntegration.IChannelCredentials> <span data-ttu-id="44a81-108">是以 IDispatch 為基礎的介面，並將 Visual Studio 環境中無法取得 IntelliSense 功能。</span><span class="sxs-lookup"><span data-stu-id="44a81-108">is an IDispatch-based interface and you will not get IntelliSense functionality in the Visual Studio environment.</span></span>  
  
 <span data-ttu-id="44a81-109">這篇文章會使用 WCF 服務中定義[訊息安全性範例](../../../../docs/framework/wcf/samples/message-security-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="44a81-109">This article will use the WCF service defined in the [Message Security Sample](../../../../docs/framework/wcf/samples/message-security-sample.md).</span></span>  
  
### <a name="to-specify-a-client-certificate"></a><span data-ttu-id="44a81-110">若要指定用戶端憑證</span><span class="sxs-lookup"><span data-stu-id="44a81-110">To specify a client certificate</span></span>  
  
1. <span data-ttu-id="44a81-111">執行 Message Security 目錄中的 Setup.bat 檔案以建立並安裝必要的測試憑證。</span><span class="sxs-lookup"><span data-stu-id="44a81-111">Run the Setup.bat file in the Message Security directory to create and install the required test certificates.</span></span>  
  
2. <span data-ttu-id="44a81-112">開啟「訊息安全性」專案。</span><span class="sxs-lookup"><span data-stu-id="44a81-112">Open the Message Security project.</span></span>  
  
3. <span data-ttu-id="44a81-113">新增`[ServiceBehavior(Namespace="http://Microsoft.ServiceModel.Samples")]`至`ICalculator`介面定義。</span><span class="sxs-lookup"><span data-stu-id="44a81-113">Add `[ServiceBehavior(Namespace="http://Microsoft.ServiceModel.Samples")]` to the `ICalculator` interface definition.</span></span>  
  
4. <span data-ttu-id="44a81-114">新增`bindingNamespace="http://Microsoft.ServiceModel.Samples"`至服務的 App.config 中的端點標記。</span><span class="sxs-lookup"><span data-stu-id="44a81-114">Add `bindingNamespace="http://Microsoft.ServiceModel.Samples"` to the endpoint tag in the App.config for the service.</span></span>  
  
5. <span data-ttu-id="44a81-115">建置「訊息安全性範例」並執行 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="44a81-115">Build the Message Security Sample and run Service.exe.</span></span> <span data-ttu-id="44a81-116">使用 Internet Explorer 並瀏覽至服務的 URI (http://localhost:8000/ServiceModelSamples/Service)以確保服務正在運作。</span><span class="sxs-lookup"><span data-stu-id="44a81-116">Use Internet Explorer and browse to the service's URI (http://localhost:8000/ServiceModelSamples/Service) to ensure that the service is working.</span></span>  
  
6. <span data-ttu-id="44a81-117">開啟 Visual Basic 6.0，並建立新的標準 .exe 檔案。</span><span class="sxs-lookup"><span data-stu-id="44a81-117">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="44a81-118">將按鈕加入至表單中，然後按兩下這個按鈕，將下列程式碼加入至 Click 處理常式：</span><span class="sxs-lookup"><span data-stu-id="44a81-118">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
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
  
7. <span data-ttu-id="44a81-119">執行 Visual Basic 應用程式及驗證結果。</span><span class="sxs-lookup"><span data-stu-id="44a81-119">Run the Visual Basic application and verify the results.</span></span>  
  
     <span data-ttu-id="44a81-120">Visual Basic 應用程式將會顯示含有呼叫 Add(3, 4) 之結果的訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="44a81-120">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span> <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29> <span data-ttu-id="44a81-121">或是<xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29>也可用的位置<xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29>來設定用戶端憑證：</span><span class="sxs-lookup"><span data-stu-id="44a81-121">or <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29> can also be used in place of <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> to set the Client Certificate:</span></span>  
  
    ```  
    monikerProxy.ChannelCredentials.SetClientCertificateFromFile "C:\MyClientCert.pfx", "password", "DefaultKeySet"  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="44a81-122">用戶端憑證必須在執行用戶端的電腦上受信任，這個呼叫才會有作用。</span><span class="sxs-lookup"><span data-stu-id="44a81-122">For this call to work, the client certificate needs to be trusted on the machine the client is running on.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="44a81-123">如果 Moniker 的格式錯誤或服務無法使用，則呼叫 `GetObject` 時將會傳回「無效的語法」錯誤。</span><span class="sxs-lookup"><span data-stu-id="44a81-123">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span> <span data-ttu-id="44a81-124">如果您收到這個錯誤，請確定您所使用的 Moniker 正確無誤，而且此服務為可用狀態。</span><span class="sxs-lookup"><span data-stu-id="44a81-124">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
### <a name="to-specify-user-name-and-password"></a><span data-ttu-id="44a81-125">若要指定使用者名稱和密碼</span><span class="sxs-lookup"><span data-stu-id="44a81-125">To specify user name and password</span></span>  
  
1. <span data-ttu-id="44a81-126">將服務的 App.config 檔案修改為使用 `wsHttpBinding`。</span><span class="sxs-lookup"><span data-stu-id="44a81-126">Modify the Service App.config file to use the `wsHttpBinding`.</span></span> <span data-ttu-id="44a81-127">這對使用者名稱和密碼驗證而言是必要的動作：</span><span class="sxs-lookup"><span data-stu-id="44a81-127">This is required for user name and password validation:</span></span>  

2. <span data-ttu-id="44a81-128">將 `clientCredentialType` 設定為使用者名稱：</span><span class="sxs-lookup"><span data-stu-id="44a81-128">Set the `clientCredentialType` to UserName:</span></span>  

3. <span data-ttu-id="44a81-129">開啟 Visual Basic 6.0，並建立新的標準 .exe 檔案。</span><span class="sxs-lookup"><span data-stu-id="44a81-129">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="44a81-130">將按鈕加入至表單中，然後按兩下這個按鈕，將下列程式碼加入至 Click 處理常式：</span><span class="sxs-lookup"><span data-stu-id="44a81-130">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
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
  
4. <span data-ttu-id="44a81-131">執行 Visual Basic 應用程式及驗證結果。</span><span class="sxs-lookup"><span data-stu-id="44a81-131">Run the Visual Basic application and verify the results.</span></span> <span data-ttu-id="44a81-132">Visual Basic 應用程式將會顯示含有呼叫 Add(3, 4) 之結果的訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="44a81-132">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="44a81-133">在這個範例的服務 Moniker 中指定的繫結已經變更為 WSHttpBinding_ICalculator。</span><span class="sxs-lookup"><span data-stu-id="44a81-133">The binding specified in the service moniker in this sample has been changed to WSHttpBinding_ICalculator.</span></span> <span data-ttu-id="44a81-134">另請注意，您必須在對 <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29> 的呼叫中提供有效的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="44a81-134">Also note that you must supply a valid user name and password in the call to <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29>.</span></span>  
  
### <a name="to-specify-windows-credentials"></a><span data-ttu-id="44a81-135">若要指定 Windows 認證</span><span class="sxs-lookup"><span data-stu-id="44a81-135">To specify Windows Credentials</span></span>  
  
1. <span data-ttu-id="44a81-136">在服務的 App.config 檔案中，將 `clientCredentialType` 設定為 Windows：</span><span class="sxs-lookup"><span data-stu-id="44a81-136">Set `clientCredentialType` to Windows in the Service App.config file:</span></span>  

2. <span data-ttu-id="44a81-137">開啟 Visual Basic 6.0，並建立新的標準 .exe 檔案。</span><span class="sxs-lookup"><span data-stu-id="44a81-137">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="44a81-138">將按鈕加入至表單中，然後按兩下這個按鈕，將下列程式碼加入至 Click 處理常式：</span><span class="sxs-lookup"><span data-stu-id="44a81-138">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
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
  
3. <span data-ttu-id="44a81-139">執行 Visual Basic 應用程式及驗證結果。</span><span class="sxs-lookup"><span data-stu-id="44a81-139">Run the Visual Basic application and verify the results.</span></span> <span data-ttu-id="44a81-140">Visual Basic 應用程式將會顯示含有呼叫 Add(3, 4) 之結果的訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="44a81-140">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="44a81-141">您必須以有效值取代 "domain"、"userID" 和 "password"。</span><span class="sxs-lookup"><span data-stu-id="44a81-141">You must replace "domain", "userID", and "password" with valid values.</span></span>  
  
### <a name="to-specify-an-issue-token"></a><span data-ttu-id="44a81-142">指定發行權杖</span><span class="sxs-lookup"><span data-stu-id="44a81-142">To specify an issue token</span></span>  
  
1. <span data-ttu-id="44a81-143">發行權杖僅適用於使用聯合安全性的應用程式。</span><span class="sxs-lookup"><span data-stu-id="44a81-143">Issue tokens are used only for applications using federated security.</span></span> <span data-ttu-id="44a81-144">如需聯合安全性的詳細資訊，請參閱[聯合與發行權杖](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)並[聯合範例](../../../../docs/framework/wcf/samples/federation-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="44a81-144">For more information about federated security, see [Federation and Issued Tokens](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md) and [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
     <span data-ttu-id="44a81-145">下列 Visual Basic 程式碼範例示範如何呼叫 <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> 方法：</span><span class="sxs-lookup"><span data-stu-id="44a81-145">The following Visual Basic code example illustrates how to call the <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> method:</span></span>  
  
    ```  
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/SomeService/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://SomeService.Samples"  
        monString = monString + ", binding=WSHttpBinding_ISomeContract, bindingNamespace=http://SomeService.Samples"  
  
        Set monikerProxy = GetObject(monString)  
    monikerProxy.SetIssuedToken("http://somemachine/sts", "bindingType", "binding")  
    ```  
  
     <span data-ttu-id="44a81-146">如需此方法之參數的詳細資訊，請參閱 <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>。</span><span class="sxs-lookup"><span data-stu-id="44a81-146">For more information about the parameters for this method, see <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44a81-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44a81-147">See also</span></span>

- [<span data-ttu-id="44a81-148">同盟</span><span class="sxs-lookup"><span data-stu-id="44a81-148">Federation</span></span>](../../../../docs/framework/wcf/feature-details/federation.md)
- [<span data-ttu-id="44a81-149">HOW TO：設定同盟服務的認證</span><span class="sxs-lookup"><span data-stu-id="44a81-149">How to: Configure Credentials on a Federation Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="44a81-150">HOW TO：建立同盟用戶端</span><span class="sxs-lookup"><span data-stu-id="44a81-150">How to: Create a Federated Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="44a81-151">訊息安全性</span><span class="sxs-lookup"><span data-stu-id="44a81-151">Message Security</span></span>](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
- [<span data-ttu-id="44a81-152">繫結和安全性</span><span class="sxs-lookup"><span data-stu-id="44a81-152">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
