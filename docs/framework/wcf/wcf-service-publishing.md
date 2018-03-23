---
title: WCF 服務發行
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c806b253-cd47-4b96-b831-e73cbf08808f
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 823edadf7d387d1a509edbdf839ac6eeece5d41f
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
---
# <a name="wcf-service-publishing"></a>WCF 服務發行
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 服務發行可協助您從 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務主機和 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 測試用戶端提供的早期開發環境，進入實際部署應用程式至實際執行環境進行測試。 在認可最後開發計畫之前，您可以使用 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 服務發行確認 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務正確執行，而且可開始發行。 您也可以選擇將 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務程式庫部署到各種不同的目標位置進行測試。  
  
## <a name="supported-services-and-target-locations"></a>支援的服務和目標位置  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務發行支援發行從 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務程式庫範本集及其對應的項目範本建立的 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務，這些範本包括如下：  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務程式庫範本，包含項目範本。  
  
-   新聞訂閱服務程式庫。  
  
 您可以找到這些服務範本選擇**檔案** -> **新專案** -> **Visual Basic**或**Visual C#**  ->  **WCF**。 在此位置 （包括 WCF 工作流程服務應用程式和 WCF 服務應用程式） 的其他 WCF 範本可以使用發行[單鍵發行 web 應用程式的](https://msdn.microsoft.com/library/dd465337\(v=vs.110\).aspx)。  
  
 此服務可以發行至下列目標位置。  
  
-   本機 IIS。  
  
-   檔案系統。  
  
-   FTP 站台。  
  
## <a name="using-wcf-service-publishing"></a>使用 WCF 服務發行  
 執行下列步驟，部署服務實作：  
  
1.  開啟 Visual Studio 的提高權限 （以滑鼠右鍵按一下可執行檔並使用 「 系統管理員身分執行 」 來啟動它）。  如果您使用的 IIS 7.0 或更新版本中，確定是否已安裝"IIS Metabase 及 iis 6 設定相容性 」 元件使用"' 開啟或關閉 Windows 功能 」 在控制台中。  
  
2.  開啟服務專案中，選取**建置**->**發行\<專案名稱 >**從主功能表中的專案上按一下滑鼠右鍵或**方案總管 中**按一下**發行**。  
  
3.  **發行** 視窗隨即出現。 按一下**...**. 按鈕，指定服務應部署至其中的目標位置。 您可以選取應用程式部署至本機 IIS、 檔案系統或 FTP 站台。 如果部署至本機 IIS 應用程式，您可以選取您的網站，並建立 web 應用程式在其下方，依序按一下**建立新的 Web 應用程式**在右上角的圖示。  
  
4.  按一下 之後**發行**在主視窗中，Visual Studio 應用程式部署至指定的目標位置和 Web.config、.svc 和組件檔案複製到目標目錄。 。 .Svc 的名稱會是"ProjectName.ServiceName.svc"。 已成功發行服務之後，您可以找到類似 「 正在連接至超連結"http://localhost/WebApplicationFolderName"http://localhost/WebApplicationFolderName...」 的 Visual Studio 輸出 視窗中。 您可以按下 CTRL，然後按一下此連結，以便在 Visual Studio 內部開啟瀏覽器頁面來檢視服務目錄結構。  
  
     如果您無法瀏覽至網站，可能是因為 IIS 沒有啟用目錄瀏覽器。 請依照提示 」 項目可以嘗試 」 區段中要加以啟用。 或者，您可以直接輸入 」 超連結"http://localhost/WebApplicationFolderName"http://localhost/WebApplicationFolderName/ProjectName.ServiceName.svc"來檢視您的服務頁面。  
  
 您可以使用**發行**指定是否您想要複製的組件、 組態和目標位置，專案中定義之所有服務的.svc 檔案，並覆寫現有目的地檔案。  
  
 如果您選擇將應用程式部署至本機 IIS，可能會遇到有關 IIS 安裝程式的錯誤。 請確定 IIS 已正確安裝。 您可以在您的瀏覽器中輸入"超連結"http://localhost"http://localhost"，並檢查是否顯示 IIS 預設頁面。  在某些情況下，IIS 中註冊不當的 ASP.NET 或 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 可能也會導致這些問題。 您可以開啟 Visual Studio 命令提示字元並執行命令"aspnet_regiis.exe-ir"來修正 ASP.NET 註冊問題，或執行"ServiceModelReg.exe – ia"命令來修正 WCF 註冊問題。  
  
## <a name="files-generated-for-publishing"></a>針對發行產生的檔案  
 此工具會先產生組件檔、Web.config 檔和 .svc 檔等檔案，才能使 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務程式庫成為 Web 裝載。 所有檔案都會複製到目標位置。 接著便會發行服務。  
  
### <a name="assembly-files"></a>組件檔  
 當您使用這個工具發行 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務時，服務會先自動建置，而組件檔會在建置之後於服務專案中產生。  
  
### <a name="svc-file"></a>.SVC 檔案  
 發行作業會為每個 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務產生 *.svc 檔 (無論檔案是否存在)，確保版本有效。 svc 檔有兩種不同的版本：一種用於 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務程式庫和新聞訂閱服務程式庫，另一種用於循序和狀態機器工作流程服務程式庫。 產生\*.svc 檔案會複製到目標位置中的根資料夾。  
  
### <a name="webconfig-file"></a>Web.config 檔  
 每次服務專案發行到特定目標位置時，都會建立 Web.config 檔。  
  
 產生的 Web.config 檔包括可用於 Web 裝載的 Web 區段，以及 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務程式庫的 App.config 內容，其中包含下列變更：  
  
-   已排除基底位址 (Base Address)。  
  
-   已排除 `<diagnostics>` 項目中的設定，以保留目標平台的追蹤設定。  
  
## <a name="publishing-wcf-services-with-non-http-bindings-to-iis"></a>將包含非 HTTP 繫結的 WCF 服務發行至 IIS  
 如果您使用的是 IIS7.0 或更新版本，就可以將包含非 HTTP 繫結的 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務發行至 IIS。 不過，您必須進行一些預先組態設定。 如需詳細資訊，請參閱主題[Windows Process Activation Service 中裝載](../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)。  
  
## <a name="security"></a>安全性  
 發行到本機 IIS 時需要具有系統管理員權限，因為 IIS 需要使用 Administrator 帳戶執行。 如果由不具系統管理員權限的使用者開啟 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務發行，IIS 就不能做為目標位置使用。 發行至檔案系統或 FTP 站台的運作方式沒有系統管理員權限。  
  
## <a name="see-also"></a>另請參閱  
 [WCF Visual Studio 範本](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [WCF 服務主機 (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [WCF 測試用戶端 (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
