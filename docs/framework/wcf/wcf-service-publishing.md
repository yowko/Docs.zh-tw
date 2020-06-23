---
title: WCF 服務發行
description: WCF 服務發佈可協助您將應用程式部署到生產環境，以供測試之用。
ms.date: 03/30/2017
ms.assetid: c806b253-cd47-4b96-b831-e73cbf08808f
ms.openlocfilehash: 99798b75e1dc01c8db361f4d8d1f162c7f7617b1
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245670"
---
# <a name="wcf-service-publishing"></a>WCF 服務發行

Windows Communication Foundation （WCF）服務發佈可協助您從 WCF 服務主機和 WCF 測試用戶端所提供的早期開發環境進行，以實際將應用程式部署到生產環境以供測試之用。 在您認可到最終的部署計畫之前，您可以使用 Windows Communication Foundation （WCF）服務發佈，確認您的 WCF 服務是否正確執行並已準備好發行。 您也可以選擇將 WCF 服務程式庫部署至各種目標位置，以便進行測試。

## <a name="supported-services-and-target-locations"></a>支援的服務和目標位置

WCF 服務發行支援發佈從 WCF 服務程式庫樣板集合建立的 WCF 服務，以及其對應的專案範本，包括下列各項：

- 具有專案範本的 WCF 服務程式庫範本。

- 新聞訂閱服務程式庫。

您可以藉由選擇 [檔案] **File**  >  [**新增專案**] > [**Visual Basic**或**Visual c #**] > **WCF**來尋找這些服務範本。 針對此位置中的其他 WCF 範本（包括 WCF 工作流程服務應用程式和 WCF 服務應用程式），您可以[針對 web 應用程式](https://docs.microsoft.com/previous-versions/aspnet/dd465337(v=vs.110))使用單鍵發行來發行。

此服務可以發行至下列目標位置。

- 本機 IIS。

- 檔案系統。

- FTP 站台。

## <a name="using-wcf-service-publishing"></a>使用 WCF 服務發行

執行下列步驟，部署服務實作：

1. 以較高的許可權開啟 Visual Studio （以滑鼠右鍵按一下可執行檔，然後選擇 [以**系統管理員身分執行**] 加以開啟）。  如果您使用的是 IIS 7.0 或更新版本，請確定您已使用 [控制台] 中的 [開啟或關閉 Windows 功能] 來安裝 [IIS 元資料庫和 IIS6 設定相容性] 元件。

2. 開啟服務專案，從主功能表中選取 [**組建**  >  **發行 \<Project Name> ** ]，或以滑鼠右鍵按一下**方案總管**中的專案，然後按一下 [**發佈**]。

3. [**發行**] 視窗隨即出現。 按一下 [ **...**]。 按鈕，指定服務應部署至其中的目標位置。 您可以選擇將應用程式部署到本機 IIS、檔案系統或 FTP 網站。 如果將應用程式部署至本機 IIS，您可以按一下右上角的 [**建立新的 Web 應用程式**] 圖示，以選取您的網站，並在其底下建立 web 應用程式。

4. 當您按一下主視窗中的 [**發佈**] 之後，Visual Studio 會將應用程式部署至指定的目標位置，並將 Web.config、.svc 和元件檔複製到目標目錄。 . .Svc 的名稱將會是 "檔案名. ServiceName. .svc"。 成功發佈服務之後，您可以在 [Visual Studio 輸出] 視窗中找到 hotlink，其看起來類似「連接到」 `http://localhost/WebApplicationFolderName...` 。 您可以按下 CTRL，然後按一下此連結，以便在 Visual Studio 內部開啟瀏覽器頁面來檢視服務目錄結構。

     如果您無法瀏覽至網站，可能是因為 IIS 沒有啟用目錄瀏覽器。 請遵循「您可以嘗試的東西」一節中的秘訣來啟用它。 或者，您可以直接鍵入 `http://localhost/WebApplicationFolderName/ProjectName.ServiceName.svc` 來查看您的服務頁面。

您可以使用 [**發行**] 來指定是否要將專案中定義之所有服務的元件、設定和 .svc 檔案複製到目標位置，並覆寫目的地端的現有檔案。

如果您選擇將應用程式部署至本機 IIS，可能會遇到有關 IIS 安裝程式的錯誤。 請確定 IIS 已正確安裝。 您可以 `http://localhost` 在瀏覽器的網址列中輸入，並檢查是否顯示 IIS 預設頁面。 在某些情況下，這些問題也可能是因為不正確地在 IIS 中註冊 ASP.NET 或 WCF 所造成。 您可以開啟 Visual Studio 的開發人員命令提示字元，然後執行命令 `aspnet_regiis.exe -ir` 來修正 ASP.NET 註冊問題，或執行命令 `ServiceModelReg.exe –ia` 來修正 WCF 註冊問題。

## <a name="files-generated-for-publishing"></a>針對發行產生的檔案
 在 WCF 服務程式庫可供 Web 裝載之前，下列檔案是由工具產生：元件檔、Web.config 檔案和 .svc 檔案。 所有檔案都會複製到目標位置。 接著便會發行服務。

### <a name="assembly-files"></a>組件檔
 當您使用此工具發佈 WCF 服務時，會先自動建立服務，而且元件檔會在建立後於服務專案中產生。

### <a name="svc-file"></a>.SVC 檔案
 發佈作業會針對每個 WCF 服務產生 * .svc 檔案，無論檔案是否存在，以確保版本有效性。 有兩種不同的 svc 檔案：一個用於 WCF 服務程式庫和新聞訂閱服務程式庫，另一個用於順序和狀態機器工作流程服務程式庫。 產生的 \* .svc 檔案會複製到目標位置中的根資料夾。

### <a name="webconfig-file"></a>Web.config 檔
 每次服務專案發行到特定目標位置時，都會建立 Web.config 檔。

 產生的 Web.config 檔案包含適用于 Web 裝載的 Web 區段，以及 WCF 服務程式庫 App.config 的內容，其中包含下列變更：

- 已排除基底位址 (Base Address)。

- 已排除 `<diagnostics>` 項目中的設定，以保留目標平台的追蹤設定。

## <a name="publishing-wcf-services-with-non-http-bindings-to-iis"></a>將包含非 HTTP 繫結的 WCF 服務發行至 IIS
 如果您使用的是 IIS 7.0 或更新版本，您可以將具有非 HTTP 系結的 WCF 服務發行至 IIS。 不過，您必須進行一些預先組態設定。 如需詳細資訊，請參閱在[Windows 進程啟用服務中裝載](./feature-details/hosting-in-windows-process-activation-service.md)的主題。

## <a name="security"></a>安全性
 發行到本機 IIS 時需要具有系統管理員權限，因為 IIS 需要使用 Administrator 帳戶執行。 如果沒有系統管理員許可權的使用者開啟 WCF 服務發行，則 IIS 無法當做目標位置使用。 發行至檔案系統或 FTP 網站的工作不需要系統管理員許可權。

## <a name="see-also"></a>另請參閱

- [WCF Visual Studio 範本](wcf-vs-templates.md)
- [WCF 服務主機 (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
- [WCF 測試用戶端 (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)
