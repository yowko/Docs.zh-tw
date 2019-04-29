---
title: WCF 服務發行
ms.date: 03/30/2017
ms.assetid: c806b253-cd47-4b96-b831-e73cbf08808f
ms.openlocfilehash: 33725c2f393529a7e59ed0b3ae1db01a359fb9a5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791205"
---
# <a name="wcf-service-publishing"></a>WCF 服務發行

Windows Communication Foundation (WCF) 服務的發行可協助您進行從提供的 WCF 服務主機和 WCF 測試用戶端來實際應用程式部署至生產環境進行測試的早期開發環境。 認可最後開發計畫之前，您可以使用 Windows Communication Foundation (WCF) 服務發行確認您的 WCF 服務正確執行，而且已準備好發行。 您也可以選擇將您的 WCF 服務程式庫部署到各種不同的目標位置進行測試。

## <a name="supported-services-and-target-locations"></a>支援的服務和目標位置

WCF 服務發行支援發佈的 WCF 服務建立的一組 WCF 服務庫範本和其對應的項目範本，其中包括下列：

- WCF 服務庫範本，包含項目範本。

- 新聞訂閱服務程式庫。

您可以找到這些範本選擇**檔案** > **新專案**> [**Visual Basic**或是**Visual C#** ] > **WCF**。 其他 WCF 中的範本 （包括 WCF 工作流程服務應用程式和 WCF 服務應用程式） 的這個位置，您可以使用發佈[單鍵發佈的 web 應用程式](https://docs.microsoft.com/previous-versions/aspnet/dd465337(v=vs.110))。

此服務可以發行至下列目標位置。

- 本機 IIS。

- 檔案系統。

- FTP 站台。

## <a name="using-wcf-service-publishing"></a>使用 WCF 服務發行

執行下列步驟，部署服務實作：

1. 使用提高的權限開啟 Visual Studio (以滑鼠右鍵按一下可執行檔，然後選擇 **系統管理員身分執行**以開啟它)。  如果您使用 IIS 7.0 或更新版本中，確定您已安裝 「 IIS Metabase 及 IIS6 設定相容性 」 元件使用控制台中的 [關閉 Windows 功能開啟或關閉]。

2. 開啟服務專案中，選取**建置** > **發行\<專案名稱 >** 從主功能表中，或以滑鼠右鍵按一下專案中的**方案總管] 中**按一下 [**發行**。

3. **發佈** 視窗隨即出現。 按一下  **...**. 按鈕，指定服務應部署至其中的目標位置。 您可以選取應用程式部署至本機 IIS、 檔案系統或 FTP 站台。 如果部署到本機 IIS 應用程式，您可以選取您的網站，並建立您的 web 應用程式，方法是按一下**建立新的 Web 應用程式**在右上角的圖示。

4. 按一下 之後**發佈**在主視窗中，Visual Studio 部署到指定的目標位置的應用程式並將 Web.config、.svc 和組件檔案複製到目標目錄。 。 .Svc 的名稱會是"ProjectName.ServiceName.svc"。 已成功發行服務之後，您可以找到在 Visual Studio 輸出視窗中，看起來類似"連接到`http://localhost/WebApplicationFolderName...`"。 您可以按下 CTRL，然後按一下此連結，以便在 Visual Studio 內部開啟瀏覽器頁面來檢視服務目錄結構。

     如果您無法瀏覽至網站，可能是因為 IIS 沒有啟用目錄瀏覽器。 請依照若要啟用它 「 項目您可以試試看 」 一節中的提示。 或者，您可以直接輸入`http://localhost/WebApplicationFolderName/ProjectName.ServiceName.svc`若要檢視您的服務頁面。

您可以使用**發佈**指定是否您想要複製的組件、 組態和目標位置，專案中定義之所有服務的.svc 檔案，並覆寫現有目的地檔案。

如果您選擇將應用程式部署至本機 IIS，可能會遇到有關 IIS 安裝程式的錯誤。 請確定 IIS 已正確安裝。 您可以輸入`http://localhost`在瀏覽器的網址列，並檢查是否 IIS 預設頁面會顯示。 在某些情況下，問題可能也會註冊不當的 ASP.NET 或 IIS 中的 WCF 所造成。 您可以開啟 Visual Studio 開發人員命令提示字元並執行命令`aspnet_regiis.exe -ir`修正 ASP.NET 註冊問題，或執行命令`ServiceModelReg.exe –ia`來修正 WCF 註冊問題。

## <a name="files-generated-for-publishing"></a>針對發行產生的檔案
 工具的 WCF 服務程式庫可以在 Web 裝載之前，會產生下列檔案： 組件檔、 Web.config 檔和.svc 檔案。 所有檔案都會複製到目標位置。 接著便會發行服務。

### <a name="assembly-files"></a>組件檔
 發佈 WCF 服務時使用此工具中，服務會先自動建置，並在建置之後服務專案中產生的組件檔案。

### <a name="svc-file"></a>.SVC 檔案
 發行作業會產生每個 WCF 服務，*.svc 檔案，檔案是否存在與否，以確保版本有效。 有兩種不同的 svc 檔案： 一個用於 WCF 服務程式庫和新聞訂閱服務程式庫和另一個用於循序和狀態機器工作流程服務程式庫。 產生\*.svc 檔案會複製到目標位置中的根資料夾。

### <a name="webconfig-file"></a>Web.config 檔
 每次服務專案發行到特定目標位置時，都會建立 Web.config 檔。

 產生的 Web.config 檔案包含可用於裝載的 Web 和 WCF 服務程式庫，以下列變更 App.config 內容的 Web 區段：

- 已排除基底位址 (Base Address)。

- 已排除 `<diagnostics>` 項目中的設定，以保留目標平台的追蹤設定。

## <a name="publishing-wcf-services-with-non-http-bindings-to-iis"></a>將包含非 HTTP 繫結的 WCF 服務發行至 IIS
 如果您使用的是 IIS7.0 或更新版本中，您可以發佈 WCF 服務使用非 HTTP 繫結至 IIS。 不過，您必須進行一些預先組態設定。 如需詳細資訊，請參閱主題[在 Windows Process Activation Service 中裝載](../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)。

## <a name="security"></a>安全性
 發行到本機 IIS 時需要具有系統管理員權限，因為 IIS 需要使用 Administrator 帳戶執行。 如果沒有系統管理員權限的使用者開啟 WCF 服務發行時，IIS 就無法使用做為目標位置。 發行至檔案系統或 FTP 站台的運作而不需要系統管理員權限。

## <a name="see-also"></a>另請參閱

- [WCF Visual Studio 範本](../../../docs/framework/wcf/wcf-vs-templates.md)
- [WCF 服務主機 (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
- [WCF 測試用戶端 (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)