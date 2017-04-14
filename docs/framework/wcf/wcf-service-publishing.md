---
title: "WCF 服務發行 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c806b253-cd47-4b96-b831-e73cbf08808f
caps.latest.revision: 22
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 17
---
# WCF 服務發行
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 服務發行可協助您從 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務主機和 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 測試用戶端提供的早期開發環境，進入實際部署應用程式至實際執行環境進行測試。  在認可最後開發計畫之前，您可以使用 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 服務發行確認 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務正確執行，而且可開始發行。  您也可以選擇將 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務程式庫部署到各種不同的目標位置進行測試。  
  
## 支援的服務和目標位置  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務發行支援發行從 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務程式庫範本集及其對應的項目範本建立的 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務，這些範本包括如下：  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務程式庫範本，包含項目範本。  
  
-   循序工作流程服務程式庫範本，包含項目範本。  
  
-   狀態機器工作流程服務程式庫範本，包含項目範本。  
  
-   新聞訂閱服務程式庫。  
  
 選擇 \[檔案\] \-\> \[新增專案\] \-\> \[Visual Basic\] 或 \[Visual C\#\] \-\> \[WCF\]，便可找出這些範本。  
  
 此服務可以發行至下列目標位置。  
  
-   本機 IIS。  
  
-   檔案系統。  
  
-   FTP 站台。  
  
-   遠端站台。  
  
## 使用 WCF 服務發行  
 執行下列步驟，部署服務實作：  
  
1.  使用更高的權限來開啟 Visual Studio \(以滑鼠右鍵按一下可執行檔，然後使用 \[以系統管理員身分執行\] 來啟動它\)。  如果您使用的是 IIS 7.0 或更新版本，請使用 \[控制台\] 中的 \[開啟或關閉 Windows 功能\] 來確定是否已安裝「IIS Metabase 及 IIS 6 設定相容性」元件。  
  
2.  開啟服務專案，從主功能表選取 \[建置\] \-\> \[發行 \<專案名稱\>\]，或以滑鼠右鍵按一下 \[方案總管\] 中的專案，然後按一下 \[發行\]。  
  
3.  \[**發行**\] 視窗隨即出現。  按一下 **…** 按鈕，指定服務應部署至其中的目標位置。  您可以選擇將應用程式部署到本機 IIS、檔案系統、FTP 站台或遠端站台。  如果您要將應用程式部署至本機 IIS，可以選取您的網站，然後按一下位於右上角的 \[**建立新 Web 應用程式**\] 圖示，藉以建立 Web 應用程式。  
  
4.  按一下主視窗中的 \[**發行**\] 後，Visual Studio 會將應用程式部署至指定的目標位置，並且將 Web.config、.svc 和組件檔複製到目標目錄。  .  .svc 的名稱就是 “ProjectName.ServiceName.svc”。  成功發行服務之後，您就可以在 \[Visual Studio 輸出\] 視窗中找到類似「正在連接到 http:\/\/localhost\/WebApplicationFolderName ...」的熱連結。  您可以按下 CTRL，然後按一下此連結，以便在 Visual Studio 內部開啟瀏覽器頁面來檢視服務目錄結構。  
  
     如果您無法瀏覽至網站，可能是因為 IIS 沒有啟用目錄瀏覽器。  請遵循＜您可以嘗試的事項＞一節中的提示進行，以便啟用此功能。  或者，您也可以直接輸入 “http:\/\/localhost\/WebApplicationFolderName\/ProjectName.ServiceName.svc” 來檢視服務頁面。  
  
 您可以使用 \[**發行**\]，指定是否要將專案中所定義之所有服務的組件、組態和 .svc 檔案複製到目標位置，以及是否要覆寫目的地的現有檔案。  
  
 如果您選擇將應用程式部署至本機 IIS，可能會遇到有關 IIS 安裝程式的錯誤。  請確定 IIS 已正確安裝。  您可以在瀏覽器中輸入 “http:\/\/localhost”，然後檢查是否顯示 IIS 預設頁面。  在某些情況下，IIS 中註冊不當的 ASP.NET 或 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 可能也會導致這些問題。  您可以開啟 Visual Studio 命令提示字元，然後執行 “aspnet\_regiis.exe \-ir” 命令來修正 ASP.NET 註冊問題，或執行 “ServiceModelReg.exe –ia” 命令來修正 WCF 註冊問題。  
  
## 針對發行產生的檔案  
 此工具會先產生組件檔、Web.config 檔和 .svc 檔等檔案，才能使 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務程式庫成為 Web 裝載。  所有檔案都會複製到目標位置。  接著便會發行服務。  
  
### 組件檔  
 當您使用這個工具發行 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務時，服務會先自動建置，而組件檔會在建置之後於服務專案中產生。  
  
### .SVC 檔案  
 發行作業會為每個 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務產生 \*.svc 檔 \(無論檔案是否存在\)，確保版本有效。  svc 檔有兩種不同的版本：一種用於 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務程式庫和新聞訂閱服務程式庫，另一種用於循序和狀態機器工作流程服務程式庫。  產生的 \*.svc 檔會複製到目標位置的根資料夾。  
  
### Web.config 檔  
 每次服務專案發行到特定目標位置時，都會建立 Web.config 檔。  
  
 產生的 Web.config 檔包括可用於 Web 裝載的 Web 區段，以及 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務程式庫的 App.config 內容，其中包含下列變更：  
  
-   已排除基底位址 \(Base Address\)。  
  
-   已排除 `<diagnostics>` 項目中的設定，以保留目標平台的追蹤設定。  
  
## 將包含非 HTTP 繫結的 WCF 服務發行至 IIS  
 如果您使用的是 IIS7.0 或更新版本，就可以將包含非 HTTP 繫結的 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務發行至 IIS。  不過，您必須進行一些預先組態設定。  如需詳細資訊，請參閱 [在 Windows Process Activation Service 中裝載](../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md) 中的主題。  
  
## 安全性  
 發行到本機 IIS 時需要具有系統管理員權限，因為 IIS 需要使用 Administrator 帳戶執行。  如果由不具系統管理員權限的使用者開啟 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務發行，IIS 就不能做為目標位置使用。  發行至檔案系統、FTP 站台或遠端站台時，則可以在未具備系統管理員權限的情況下進行。  
  
## 請參閱  
 [WCF Visual Studio 範本](../../../docs/framework/wcf/wcf-vs-templates.md)   
 [WCF 服務主機 \(WcfSvcHost.exe\)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)   
 [WCF 測試用戶端 \(WcfTestClient.exe\)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)