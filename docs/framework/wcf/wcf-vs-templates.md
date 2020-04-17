---
title: WCF Visual Studio 範本
ms.date: 03/30/2017
ms.assetid: 6a608575-3535-4190-89da-911e24c8374f
ms.openlocfilehash: 13183ad5f05350c34eebd025eca3faa7d97644f8
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2020
ms.locfileid: "81608019"
---
# <a name="wcf-visual-studio-templates"></a>WCF Visual Studio 範本
Windows 通訊基礎 (WCF) 可視化工作室範本是預定義的專案和專案範本,可用於可視化工作室,以快速構建 WCF 服務及其周圍應用程式。  
  
## <a name="using-the-wcf-templates"></a>使用 WCF 範本  
 WCF 可視化工作室範本為服務開發提供了基本的類結構。 具體來說，這些範本會提供服務合約、資料合約、服務實作和組態的基本定義。 您可以使用這些範本，建立具有最基本程式碼互動的簡單服務，以及適用於更進階服務的建置組塊。  
  
### <a name="wcf-service-library-project-template"></a>WCF 服務程式庫專案範本  
 WCF 服務庫專案範本在**Visual C_WCF**和**可視化基礎_WCF**下的新項目對話方塊中可用。  
  
 使用**WCF 服務**樣本建立新項目時,新項目將自動包含以下三個檔:  
  
- 服務合約檔案 (IService1.cs 或 IService1.vb)。 服務協定檔是應用 WCF 服務屬性的介面。 這個檔案提供簡單服務的定義以示範如何定義服務，而其中也包含以參數為基礎的作業和簡單的資料合約範例。 這是創建 WCF 服務專案後代碼編輯器中顯示的預設檔。  
  
- 服務實作檔案 (Service1.cs 或 Service1.vb)。 服務實作檔案會實作服務合約檔案中定義的合約。  
  
- 應用程式組態檔案 (App.config)。 配置檔提供具有安全 HTTP 綁定的 WCF 服務模型的基本元素。 它也包含服務的端點，並會啟用中繼資料交換。  
  
> [!NOTE]
> Visual Studio 配置為使用[WCF 服務主機 (WcfSvc Host.exe) (](wcf-service-host-wcfsvchost-exe.md)預設配置)執行時,將 App.config 檔識別為專案的配置檔。 如果是在可執行檔中裝載服務程式庫，您必須將組態程式碼移至該可執行檔的組態檔，因為 DLL 的組態檔是無效的。  
  
### <a name="wcf-service-application-template"></a>WCF 服務應用程式範本  
 WCF 服務應用程式範本在**VisualC_WCF**和**視覺化基礎_WCF**下的新專案對話框中可用。  
  
 使用**WCF Web 應用程式服務**樣本建立新專案時,該專案包括以下四個檔:  
  
- 服務主機檔案 (service1.svc)。  
  
- 服務合約檔案 (IService1.cs 或 IService1.vb)。  
  
- 服務實作檔案 (Service1.svc.cs 或 Service1.svc.vb)。  
  
- Web 組態檔案 (Web.config)。  
  
 範本會自動建立網站 (這會部署到虛擬目錄中) 並在其中裝載服務。  
  
### <a name="wcf-web-site-template"></a>WCF 網站範本  
 WCF 網站範本在**VisualC_網站_WCF服務和****可視化基礎_WebSite_WCF服務**下的「新專案」對話框中可用。 這會建立與 WCF 服務應用程式範本相同的檔案，但是其組織方式猶如 ASP.NET 網站。 會建立 App_Code 和 App_Data 資料夾。  
  
### <a name="wcf-service-item-template"></a>WCF 服務項目範本  
 WCF 服務專案範本是一個自定義範本,它提供了將 WCF 服務添加到現有 Visual Studio 專案的快速方法。  
  
 要使用此樣本,請轉到 **「解決方案資源管理員」** 窗格,右鍵單擊專案名稱,指向 **'新增**",然後按下「**新增專案**」 以啟動 **「 新增新項目」** 對話方塊。  
  
 服務介面和實作檔案會放置在根專案資料夾。  
  
 如果新服務的組態區段和現有組態檔屬於相容的類型，則範本會嘗試加以合併。  
  
 如果現有專案是 Web 專案，也會建立服務主機檔案 (service1.svc)。  
  
### <a name="wcf-wf-service-project-and-item-template"></a>WCF WF 服務專案和項目範本。  
 這些範本創建承載工作流服務的 WCF 服務,工作流服務是可以像 Web 服務一樣訪問的工作流。 XAML 或命令式程式撰寫模型各有不同的範本。 您可以使用這些範本來建立循序或狀態機器工作流程。 有關這些類型的工作流的詳細資訊,請參閱[如何:建立工作流](../windows-workflow-foundation/how-to-create-a-workflow.md)。 有關建立工作流項目的詳細資訊,請參閱[建立舊工作流專案](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)。  
  
 使用 XOML 類型工作流而不是基於代碼的工作流時,可視化工作室設計器的回應速度會更大。 XOML 工作流程是預設要建立的工作流程類型。  
  
### <a name="wcf-syndication-service-library-template"></a>WCF 新聞訂閱服務程式庫範本  
 此範本使您能夠將源以 RSS 或 ATOM 格式公開為 WCF 服務。 有關詳細資訊,請參閱[WCF 聯合](./feature-details/wcf-syndication.md)。  
  
#### <a name="changing-the-address-of-the-feed"></a>變更摘要的位址  
 新聞訂閱範本在執行期間使用 Internet Explorer。 在可視化工作室中右鍵按**下 「解決方案資源管理員」** 中的專案時,請選擇 **「屬性**」,然後選擇 **「調試」** 選項卡,即可查看範本的預設位址。 Internet Explorer 會嘗試開啟這個位址上的摘要。  
  
 如果更改來源的位址,還必須在 **「除錯」** 選項卡中更改位址。如果不執行此操作,Internet Explorer 會嘗試在預設位址打開源並失敗。  
  
### <a name="ajax-enabled-wcf-service-item-template"></a>具備 AJAX 能力的 WCF 服務項目範本  
 此範本將 AJAX 控制件公開為 WCF 服務。 有關 AJAX 控制件的詳細資訊,請參閱[AJAX 控制檔](/aspnet/ajax/)。  
  
### <a name="silverlight-enabled-wcf-service-item-template"></a>啟用 Silverlight 的 WCF 服務項目範本  
 這個範本會建立提供資料給 Silverlight 用戶端或前端的 Web 服務。 該範本可以添加到網站或 Web 應用程式專案中以建立 WCF 服務,其中包括支援與 Silverlight 用戶端通訊的服務代碼和配置。 然後,可以使用 **「添加服務引用」** 將服務的用戶端代理添加到用戶端,並在 Silverlight 客戶端和啟用 Silverlight 的 WCF 服務之間交換數據。  
  
 要存取此樣本,請在**解決方案資源管理員**右鍵點或 Web 應用程式項目,按下「**新增新項**」,然後按**下 啟用 Silverlight 的 WCF 服務**。  
  
> [!NOTE]
> 啟用 Silverlight 的 WCF 服務會在不啟用任何安全性設定的情況下公開 `basicHttpBinding` 端點。 因此，所有連接到這個服務的用戶端，都可以取得此服務的相關資訊。 同樣地，服務和用戶端之間的交換訊息也不會經過簽署或加密。 為了確保端點安全性，您應該使用 ASP.NET 驗證、HTTPS 或其他機制。  
  
## <a name="see-also"></a>另請參閱

- [WCF 服務主機 (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
- [WCF 測試用戶端 (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)
