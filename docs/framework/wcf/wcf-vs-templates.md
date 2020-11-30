---
title: WCF Visual Studio 範本
ms.date: 03/30/2017
ms.assetid: 6a608575-3535-4190-89da-911e24c8374f
ms.openlocfilehash: a3aa7e3ee57759ef54ddaa898fe036c4e3caa33e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/29/2020
ms.locfileid: "96279697"
---
# <a name="wcf-visual-studio-templates"></a>WCF Visual Studio 範本

Windows Communication Foundation (WCF) Visual Studio 範本是預先定義的專案和專案範本，可在 Visual Studio 中用來快速建立 WCF 服務和周圍的應用程式。  
  
## <a name="using-the-wcf-templates"></a>使用 WCF 範本  

 WCF Visual Studio 範本提供服務開發的基本類別結構。 具體來說，這些範本會提供服務合約、資料合約、服務實作和組態的基本定義。 您可以使用這些範本，建立具有最基本程式碼互動的簡單服務，以及適用於更進階服務的建置組塊。  
  
### <a name="wcf-service-library-project-template"></a>WCF 服務程式庫專案範本  

 [WCF 服務程式庫] 專案範本位於 [ **Visual c # \wcf]** ] 和 [ **visual Basic\WCF**] 底下的 [新增專案] 對話方塊中。  
  
 當您使用 [ **WCF 服務** ] 範本建立新專案時，新專案會自動包含下列三個檔案：  
  
- 服務合約檔案 (IService1.cs 或 IService1.vb)。 服務合約檔案是已套用 WCF 服務屬性的介面。 這個檔案提供簡單服務的定義以示範如何定義服務，而其中也包含以參數為基礎的作業和簡單的資料合約範例。 這是建立 WCF 服務專案之後，在程式碼編輯器中顯示的預設檔案。  
  
- 服務實作檔案 (Service1.cs 或 Service1.vb)。 服務實作檔案會實作服務合約檔案中定義的合約。  
  
- 應用程式組態檔案 (App.config)。 設定檔會使用安全的 HTTP 系結，提供 WCF 服務模型的基本元素。 它也包含服務的端點，並會啟用中繼資料交換。  
  
> [!NOTE]
> Visual Studio 設定為使用 WCF 服務主機（預設設定），將 App.config 檔辨識為專案的設定檔， [ ( # A1) ](wcf-service-host-wcfsvchost-exe.md)。 如果是在可執行檔中裝載服務程式庫，您必須將組態程式碼移至該可執行檔的組態檔，因為 DLL 的組態檔是無效的。  
  
### <a name="wcf-service-application-template"></a>WCF 服務應用程式範本  

 [WCF 服務應用程式] 範本位於 [ **Visual c # \wcf]** 和 **visual Basic\WCF**] 下的 [新增專案] 對話方塊中。  
  
 當您使用 **WCF Web 應用程式服務** 範本建立新專案時，專案會包含下列四個檔案：  
  
- 服務主機檔案 (service1.svc)。  
  
- 服務合約檔案 (IService1.cs 或 IService1.vb)。  
  
- 服務實作檔案 (Service1.svc.cs 或 Service1.svc.vb)。  
  
- Web 組態檔案 (Web.config)。  
  
 範本會自動建立網站 (這會部署到虛擬目錄中) 並在其中裝載服務。  
  
### <a name="wcf-web-site-template"></a>WCF 網站範本  

 您可以在 [新增專案] 對話方塊中的 [ **Visual c # \Web Site\WCF service** and **Visual Basic\Web Site\WCF service**] 下找到 WCF 網站範本。 這會建立與 WCF 服務應用程式範本相同的檔案，但是其組織方式猶如 ASP.NET 網站。 會建立 App_Code 和 App_Data 資料夾。  
  
### <a name="wcf-service-item-template"></a>WCF 服務項目範本  

 WCF 服務專案範本是自訂範本，可讓您快速地將 WCF 服務新增至現有的 Visual Studio 專案。  
  
 若要使用這個範本，請移至 [ **方案總管** ] 窗格，以滑鼠右鍵按一下您的專案名稱，指向 [ **加入**]，然後按一下 [ **新增專案** ]，以啟動 [ **加入新專案** ] 對話方塊。  
  
 服務介面和實作檔案會放置在根專案資料夾。  
  
 如果新服務的組態區段和現有組態檔屬於相容的類型，則範本會嘗試加以合併。  
  
 如果現有專案是 Web 專案，也會建立服務主機檔案 (service1.svc)。  
  
### <a name="wcf-wf-service-project-and-item-template"></a>WCF WF 服務專案和項目範本。  

 這些範本會建立裝載工作流程服務的 WCF 服務，這是可以像 web 服務一樣存取的工作流程。 XAML 或命令式程式撰寫模型各有不同的範本。 您可以使用這些範本來建立循序或狀態機器工作流程。 如需這些工作流程類型的詳細資訊，請參閱 [如何：建立工作流程](../windows-workflow-foundation/how-to-create-a-workflow.md)。 如需建立工作流程專案的詳細資訊，請參閱 [建立舊版工作流程專案](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)。  
  
 使用 XOML 類型的工作流程，而不是使用以程式碼為基礎的工作流程時，Visual Studio 設計工具會更 XOML 工作流程是預設要建立的工作流程類型。  
  
### <a name="wcf-syndication-service-library-template"></a>WCF 新聞訂閱服務程式庫範本  

 此範本可讓您將 RSS 或 ATOM 格式的摘要公開為 WCF 服務。 如需詳細資訊，請參閱 [WCF 摘要整合](./feature-details/wcf-syndication.md)。  
  
#### <a name="changing-the-address-of-the-feed"></a>變更摘要的位址  

 新聞訂閱範本在執行期間使用 Internet Explorer。 當您以滑鼠右鍵按一下 [ **方案 Explorer** ] Visual Studio 中的專案，選取 [ **屬性**]，然後選取 [ **調試** 程式] 索引標籤，就可以看到範本的預設位址。 Internet Explorer 會嘗試開啟這個位址上的摘要。  
  
 如果您變更摘要的位址，您也必須變更 [ **調試** 程式] 索引標籤中的位址。如果您沒有這麼做，Internet Explorer 會嘗試在預設位址開啟摘要，然後失敗。  
  
### <a name="ajax-enabled-wcf-service-item-template"></a>具備 AJAX 能力的 WCF 服務項目範本  

 此範本會以 WCF 服務的形式公開 AJAX 控制項。 如需 AJAX 控制項的詳細資訊，請參閱 [ajax 控制項檔](/aspnet/ajax/)集。  
  
### <a name="silverlight-enabled-wcf-service-item-template"></a>啟用 Silverlight 的 WCF 服務項目範本  

 這個範本會建立提供資料給 Silverlight 用戶端或前端的 Web 服務。 範本可以加入至網站或 Web 應用程式專案，以建立 WCF 服務，其中包含支援與 Silverlight 用戶端進行通訊的服務程式代碼和設定。 然後，您可以使用 **加入服務參考** 將服務的用戶端 proxy 新增至用戶端，並在 silverlight 用戶端與啟用 SILVERLIGHT 的 WCF 服務之間交換資料。  
  
 若要存取這個範本，請在 **方案總管** 中的網站或 web 應用程式專案上按一下滑鼠右鍵，按一下 [ **加入新專案**]，然後按一下 [ **啟用 Silverlight 的 WCF 服務**]。  
  
> [!NOTE]
> 啟用 Silverlight 的 WCF 服務會在不啟用任何安全性設定的情況下公開 `basicHttpBinding` 端點。 因此，所有連接到這個服務的用戶端，都可以取得此服務的相關資訊。 同樣地，服務和用戶端之間的交換訊息也不會經過簽署或加密。 為了確保端點安全性，您應該使用 ASP.NET 驗證、HTTPS 或其他機制。  
  
## <a name="see-also"></a>另請參閱

- [WCF 服務主機 (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
- [WCF 測試用戶端 (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)
