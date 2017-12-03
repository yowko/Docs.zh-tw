---
title: "用戶端驗證"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0c1f805-1a81-4d0d-a112-bf5e2e87a631
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 340af20c44b8fde3fdff92d07837c3cc04ca517d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="client-validation"></a>用戶端驗證
服務經常會發行中繼資料，以便自動產生和設定用戶端 Proxy 型別。 當服務不受信任時，用戶端應用程式應該根據安全性、交易和服務合約類型等條件，驗證中繼資料是否符合用戶端應用程式的原則。 下列範例會示範如何撰寫用戶端端點行為，此行為會驗證服務端點以確定能夠安全地使用服務端點。  
  
 服務會公開 (Expose) 四個服務端點。 第一個端點使用 WSDualHttpBinding，第二個端點會使用 NTLM 驗證，第三個端點會啟用交易流程，而第四個端點會使用憑證架構的驗證。  
  
 用戶端會使用 <xref:System.ServiceModel.Description.MetadataResolver> 類別來擷取服務的中繼資料。 用戶端會使用驗證行為，強制禁止雙工繫結、NTLM 驗證與交易流程的原則。 對於從服務中繼資料匯入的每個 <xref:System.ServiceModel.Description.ServiceEndpoint> 執行個體，用戶端應用程式會在嘗試使用 `InternetClientValidatorBehavior` 用戶端連接至端點之前，將 <xref:System.ServiceModel.Description.ServiceEndpoint> 端點行為的執行個體新增至 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]。 此行為的 `Validate` 方法會在呼叫服務的任何作業之前執行，並且擲回 `InvalidOperationExceptions` 以強制執行該用戶端的原則。  
  
### <a name="to-build-the-sample"></a>若要建置範例  
  
1.  若要建置此方案，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>若要在同一部電腦上執行範例  
  
1.  使用系統管理員權限來開啟 Visual Studio 命令提示字元，然後執行範例安裝資料夾中的 Setup.bat。 這會安裝執行範例所需的所有憑證。  
  
2.  從 \service\bin\Debug 執行服務應用程式。  
  
3.  從 \client\bin\Debug 執行用戶端應用程式。 用戶端活動會顯示在用戶端主控台應用程式上。  
  
4.  如果用戶端和服務無法通訊，請參閱 [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b)。  
  
5.  當您完成範例時，請執行 Cleanup.bat 以移除憑證。 其他安全性範例使用相同的憑證。  
  
### <a name="to-run-the-sample-across-computers"></a>若要跨電腦執行範例  
  
1.  在伺服器上，以系統管理員的權限執行 Visual Studio 命令提示字元中輸入`setup.bat service`。 執行`setup.bat`與`service`引數具有電腦完整網域名稱建立服務憑證，並將服務憑證匯出為名為 Service.cer 的檔案。  
  
2.  在伺服器上，編輯 App.config 以反映新的憑證名稱。 亦即，變更`findValue`屬性[ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)電腦的完整網域名稱的項目。  
  
3.  從服務目錄中將 Service.cer 檔案複製至用戶端電腦上的用戶端目錄。  
  
4.  在用戶端，請開啟 Visual Studio 命令提示字元使用系統管理員權限和型別`setup.bat client`。 執行`setup.bat`與`client`引數會建立名為 Client.com 的用戶端憑證，並將用戶端憑證匯出為名為 Client.cer 的檔案。  
  
5.  在 client.cs 檔中變更 MEX 端點的位址值和 `findValue`，以便將預設伺服器憑證設定成符合您服務的新位址。 您可以藉由使用伺服器的完整網域名稱取代 localhost，完成這個動作。 接著重新建置。  
  
6.  從用戶端目錄將 Client.cer 檔案複製到伺服器上的服務目錄中。  
  
7.  在用戶端上，於使用系統管理員權限開啟的 Visual Studio 命令提示字元中，執行 ImportServiceCert.bat。 這樣會將服務憑證從 Service.cer 檔案匯入至 CurrentUser - TrustedPeople 存放區中。  
  
8.  在伺服器上，於使用系統管理員權限開啟的 Visual Studio 命令提示字元中，執行 ImportClientCert.bat。 這樣便會從 Client.cer 檔將用戶端憑證匯入至 LocalMachine - TrustedPeople 存放區中。  
  
9. 在服務電腦上，使用 Visual Studio 來建置此服務專案並執行 service.exe。  
  
10. 在用戶端電腦上執行 client.exe。  
  
    1.  如果用戶端和服務無法通訊，請參閱 [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b)。  
  
### <a name="to-clean-up-after-the-sample"></a>若要在使用範例之後進行清除  
  
-   當您完成執行範例後，請執行範例資料夾中的 Cleanup.bat。  
  
    > [!NOTE]
    >  跨電腦執行此範例時，這個指令碼不會移除用戶端上的服務憑證。 如果您已執行跨電腦使用憑證的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 範例，請確定清除安裝在 CurrentUser - TrustedPeople 存放區中的服務憑證。 若要這麼做，請使用下列命令：`certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>. For example: certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`。  
  
## <a name="see-also"></a>另請參閱  
 [使用中繼資料](../../../../docs/framework/wcf/feature-details/using-metadata.md)
