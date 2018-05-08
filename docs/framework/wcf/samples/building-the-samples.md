---
title: 建置 Windows Communication Foundation 範例
ms.date: 03/30/2017
ms.assetid: 2899e7a5-9cb2-4e8d-b8d2-f31391549198
ms.openlocfilehash: 5493972306092fc3309b0993d595f22c74c8603a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="building-the-windows-communication-foundation-samples"></a>建置 Windows Communication Foundation 範例
您可以建置 Windows Communication Foundation (WCF) 範例，使用 Visual Studio 2010 或**msbuild**從命令列命令。 本主題將同時說明這兩個程序。  
  
> [!NOTE]
>  在建置或執行任何之前[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]範例，請確定您已經執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
### <a name="to-build-the-sample-using-a-command-prompt"></a>若要使用命令提示字元建置範例  
  
1.  使用系統管理員權限來開啟 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 命令提示字元，並巡覽至安裝範例所在目錄位置下任一語言特定子目錄。  
  
2.  型別`msbuild`在命令列。 用戶端程式檔會建置至 client\bin，服務程式檔則建置至 service\bin。 如果服務是由 Internet Information Services (IIS) 裝載，則服務程式檔也會被複製到 servicemodelsamples 目錄及其 \bin 子目錄中。  
  
> [!NOTE]
>  您必須在 %systemdrive%\inetpub\wwwroot 上設定 ACL 以將修改權限授予您用來執行的帳戶。 否則，有些建置後事件將會失敗。 或者，您也可以不去改變這些 ACL，而以系統管理員身分來執行 SDK 命令提示字元。  
  
### <a name="to-build-the-sample-using-visual-studio"></a>若要使用 Visual Studio 建置範例  
  
1.  如果您使用[!INCLUDE[wv](../../../../includes/wv-md.md)]， [!INCLUDE[lserver](../../../../includes/lserver-md.md)]，Windows 7 或 Windows Server 2008 R2，且在執行[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]，您必須使用更高權限執行 Visual Studio。 若要這樣做，請以滑鼠右鍵按一下 開始 功能表上的圖示，然後按一下 **系統管理員身分執行**。  
  
2.  從**檔案**功能表在 Visual Studio 中，按一下**開啟**，然後按一下 **專案/方案**。 瀏覽至安裝範例所在的目錄下的特定語言子目錄，然後按兩下.sln 檔案圖示，以在 Visual Studio 中開啟方案。  
  
3.  在**建置**功能表上，選取**重建方案**。 用戶端程式檔會建置至 client\bin，服務程式檔則建置至 service\bin。 如果服務是由 IIS 裝載，則服務程式檔也會被複製到 servicemodelsamples 目錄及其 \bin 子目錄中。  
  
> [!NOTE]
>  您必須在 %systemdrive%\inetpub\wwwroot 上設定 ACL 以將修改權限授予您用來執行的帳戶。 否則，有些建置後事件將會失敗。 不過，您也可以不去改變這些 ACL，而以系統管理員身分來執行 SDK 命令提示字元或 Visual Studio。 有些 Visual Studio 動作 (例如將偵錯工具附加到 ASP.Net 工作處理序中) 同時要求具備系統管理員權限。  
  
## <a name="setup-batch-files-and-scripts"></a>設定批次檔和指令碼  
 Setup.exe 和 Cleanup.exe 批次檔與指令碼必須透過 Visual Studio 命令提示字元來執行。 數種設定與清除檔案會執行需要系統管理員權限才能執行與啟動的工作。  
  
## <a name="important-security-information-about-metadata-endpoints"></a>關於中繼資料端點的重要安全性資訊  
 若要避免意外洩露潛在的敏感服務中繼資料，Windows Communication Foundation (WCF) 服務的預設組態會停用中繼資料發行。 這個行為依預設為安全行為，但也表示您無法使用中繼資料匯入工具 (例如 Svcutil.exe) 來產生呼叫服務所需的用戶端程式碼，除非組態中已明確啟用服務的中繼發行行為。 為了讓範例的實驗順利進行，幾乎所有範例都會公開不安全的中繼資料發行端點。 未經驗證的匿名使用者可能可以使用這類端點，所以部署前必須小心謹慎，才能確保公開服務中繼資料是否適切。 如需有關發行服務中繼資料的詳細資訊，請參閱[中繼資料發行行為](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)範例。 請參閱[自訂安全中繼資料端點](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)範例如保障安全的中繼資料端點的範例。  
  
## <a name="exception-handling"></a>例外狀況處理  
 一般來說，這些範例不包含例外狀況處理，以便讓程式碼專注在範例主題上。 如需例外狀況處理的詳細資訊，請參閱[預期的例外狀況](../../../../docs/framework/wcf/samples/expected-exceptions.md)範例。  
  
## <a name="regenerating-clients-and-configuration-with-svcutil"></a>使用 Svcutil 重新產生用戶端與組態  
 您可以使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)重新產生用戶端程式碼和組態的範例。 某些範例需要您手動編輯組態。 例如，如果您使用 Svcutil.exe 針對使用用戶端憑證認證的範例重新產生組態，則您必須手動指定先前設定的認證。 某些範例使用特定的 Svcutil.exe 選項來影響產生的程式碼，而這些選項都會在特定的範例主題中加以指定。  
  
#### <a name="to-regenerate-the-client-and-configuration-files"></a>若要重新產生用戶端與組態檔  
  
1.  開啟 [SDK 命令提示字元]，並巡覽至安裝範例所在目錄位置下任一語言特定子目錄。  
  
2.  如果服務是 Web 裝載的型別，請使用下列命令。  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs  
    ```  
  
     如果服務是自我裝載的型別，請使用下列命令。  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /out:generatedClient.cs  
    ```  
  
     取代http://localhost:8000/ServiceModelSamples/service.svc/mex自我裝載的服務的 mex 端點的位址。  
  
     若要以 Visual Basic 型別來產生用戶端，請使用下列命令。  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb  
    ```  
  
     如果服務是自我裝載的型別，請使用下列命令。  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb  
    ```  
  
    > [!NOTE]
    >  略過加入產生的用戶端設定 **/noConfig**選項。  
  
## <a name="see-also"></a>另請參閱  
 [執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)  
 [ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
