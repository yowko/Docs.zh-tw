---
title: WCF 服務發行
ms.date: 03/30/2017
ms.assetid: c806b253-cd47-4b96-b831-e73cbf08808f
ms.openlocfilehash: 258c7e65b69648477e58880f35b100a9378dc9c0
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806457"
---
# <a name="wcf-service-publishing"></a>WCF 服務發行
Windows Communication Foundation (WCF) 服務的發行可協助您從實際部署至生產環境進行測試應用程式的 WCF 服務主機和 WCF 測試用戶端提供的早期開發環境的進度。 在認可最後開發計畫之前，您可以使用 Windows Communication Foundation (WCF) 服務發行確認您的 WCF 服務正確執行，而且已準備好可以發佈。 您也可以選擇將您的 WCF 服務程式庫部署到不同的目標位置進行測試。  
  
## <a name="supported-services-and-target-locations"></a>支援的服務和目標位置  
 WCF 服務發行支援發佈的 WCF 服務所建立的一組 WCF 服務程式庫範本和其對應的項目範本，其中包括下列各項：  
  
-   WCF 服務程式庫範本，包含項目範本。  
  
-   新聞訂閱服務程式庫。  
  
 您可以找到這些服務範本選擇**檔案** -> **新專案** -> **Visual Basic**或**Visual C#**  ->  **WCF**。 在此位置 （包括 WCF 工作流程服務應用程式和 WCF 服務應用程式） 的其他 WCF 範本可以使用發行[單鍵發行 web 應用程式的](https://msdn.microsoft.com/library/dd465337\(v=vs.110\).aspx)。  
  
 此服務可以發行至下列目標位置。  
  
-   本機 IIS。  
  
-   檔案系統。  
  
-   FTP 站台。  
  
## <a name="using-wcf-service-publishing"></a>使用 WCF 服務發行  
 執行下列步驟，部署服務實作：  
  
1.  開啟 Visual Studio 的提高權限 （以滑鼠右鍵按一下可執行檔並使用 「 系統管理員身分執行 」 來啟動它）。  如果您使用的 IIS 7.0 或更新版本中，確定是否已安裝"IIS Metabase 及 iis 6 設定相容性 」 元件使用"' 開啟或關閉 Windows 功能 」 在控制台中。  
  
2.  開啟服務專案中，選取**建置**->**發行\<專案名稱 >** 從主功能表中的專案上按一下滑鼠右鍵或**方案總管 中**按一下**發行**。  
  
3.  **發行** 視窗隨即出現。 按一下 **...**. 按鈕，指定服務應部署至其中的目標位置。 您可以選取應用程式部署至本機 IIS、 檔案系統或 FTP 站台。 如果部署至本機 IIS 應用程式，您可以選取您的網站，並建立 web 應用程式在其下方，依序按一下**建立新的 Web 應用程式**在右上角的圖示。  
  
4.  按一下 之後**發行**在主視窗中，Visual Studio 應用程式部署至指定的目標位置和 Web.config、.svc 和組件檔案複製到目標目錄。 。 .Svc 的名稱會是"ProjectName.ServiceName.svc"。 已成功發行服務之後，您可以找到在 Visual Studio 輸出視窗中，看起來類似 「 正在連接到超連結"http://localhost/WebApplicationFolderName" http://localhost/WebApplicationFolderName ...」。 您可以按下 CTRL，然後按一下此連結，以便在 Visual Studio 內部開啟瀏覽器頁面來檢視服務目錄結構。  
  
     如果您無法瀏覽至網站，可能是因為 IIS 沒有啟用目錄瀏覽器。 請依照提示 」 項目可以嘗試 」 區段中要加以啟用。 或者，您可以直接輸入 」 超連結"http://localhost/WebApplicationFolderName" http://localhost/WebApplicationFolderName/ProjectName.ServiceName.svc< 若要檢視您的服務頁面。  
  
 您可以使用**發行**指定是否您想要複製的組件、 組態和目標位置，專案中定義之所有服務的.svc 檔案，並覆寫現有目的地檔案。  
  
 如果您選擇將應用程式部署至本機 IIS，可能會遇到有關 IIS 安裝程式的錯誤。 請確定 IIS 已正確安裝。 您可以輸入"超連結"http://localhost" http://localhost」 在瀏覽器，然後檢查是否 IIS 預設頁面會顯示。  在某些情況下，問題可能也是 ASP.NET 或 WCF IIS 中註冊不當所造成。 您可以開啟 Visual Studio 命令提示字元並執行命令"aspnet_regiis.exe-ir"來修正 ASP.NET 註冊問題，或執行"ServiceModelReg.exe – ia"命令來修正 WCF 註冊問題。  
  
## <a name="files-generated-for-publishing"></a>針對發行產生的檔案  
 WCF 服務程式庫可以在 Web 裝載之前，工具會產生下列檔案： 組件檔、 Web.config 檔和.svc 檔案。 所有檔案都會複製到目標位置。 接著便會發行服務。  
  
### <a name="assembly-files"></a>組件檔  
 當您發佈的 WCF 服務時使用這項工具，服務會先自動建置組件檔會產生和服務專案建置之後。  
  
### <a name="svc-file"></a>.SVC 檔案  
 發行作業會產生 *.svc 檔案的每個 WCF 服務，檔案是否存在，確保版本有效。 有兩種不同的 svc 檔案： 一個用於 WCF 服務程式庫和新聞訂閱服務程式庫和另一種用於循序和狀態機器工作流程服務程式庫。 產生\*.svc 檔案會複製到目標位置中的根資料夾。  
  
### <a name="webconfig-file"></a>Web.config 檔  
 每次服務專案發行到特定目標位置時，都會建立 Web.config 檔。  
  
 產生的 Web.config 檔案包含 Web 區段，適用於 Web 主控及的 App.config 內容，針對 WCF 服務程式庫，以下列變更：  
  
-   已排除基底位址 (Base Address)。  
  
-   已排除 `<diagnostics>` 項目中的設定，以保留目標平台的追蹤設定。  
  
## <a name="publishing-wcf-services-with-non-http-bindings-to-iis"></a>將包含非 HTTP 繫結的 WCF 服務發行至 IIS  
 如果您使用的是 IIS7.0 或更新版本中，您可以發佈 WCF 服務使用非 HTTP 繫結到 IIS。 不過，您必須進行一些預先組態設定。 如需詳細資訊，請參閱主題[Windows Process Activation Service 中裝載](../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)。  
  
## <a name="security"></a>安全性  
 發行到本機 IIS 時需要具有系統管理員權限，因為 IIS 需要使用 Administrator 帳戶執行。 如果使用者沒有系統管理員權限開啟 WCF 服務發行，IIS 就無法使用做為目標位置。 發行至檔案系統或 FTP 站台的運作方式沒有系統管理員權限。  
  
## <a name="see-also"></a>另請參閱  
 [WCF Visual Studio 範本](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [WCF 服務主機 (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [WCF 測試用戶端 (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
