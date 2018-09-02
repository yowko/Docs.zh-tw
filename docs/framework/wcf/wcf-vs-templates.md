---
title: WCF Visual Studio 範本
ms.date: 03/30/2017
ms.assetid: 6a608575-3535-4190-89da-911e24c8374f
ms.openlocfilehash: 73d2645977381602ef028d091675a22fb933d60b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43423027"
---
# <a name="wcf-visual-studio-templates"></a>WCF Visual Studio 範本
Windows Communication Foundation (WCF) Visual Studio 範本是預先定義的專案和項目範本，您可以使用 Visual Studio 中，快速建置 WCF 服務和相關的應用程式。  
  
## <a name="using-the-wcf-templates"></a>使用 WCF 範本  
 WCF Visual Studio 範本會提供服務開發的基本類別結構。 具體來說，這些範本會提供服務合約、資料合約、服務實作和組態的基本定義。 您可以使用這些範本，建立具有最基本程式碼互動的簡單服務，以及適用於更進階服務的建置組塊。  
  
### <a name="wcf-service-library-project-template"></a>WCF 服務程式庫專案範本  
 WCF 服務程式庫專案範本位在新專案對話方塊中，在**Visual C# \WCF**並**視覺化 basic\wcf&lt;3**。  
  
 當您建立新的專案使用**WCF 服務**範本，新的專案會自動包含下列三個檔案：  
  
-   服務合約檔案 (IService1.cs 或 IService1.vb)。 服務合約檔案是已套用的 WCF 服務屬性的介面。 這個檔案提供簡單服務的定義以示範如何定義服務，而其中也包含以參數為基礎的作業和簡單的資料合約範例。 這是建立 WCF 服務專案後的程式碼編輯器中顯示的預設檔案。  
  
-   服務實作檔案 (Service1.cs 或 Service1.vb)。 服務實作檔案會實作服務合約檔案中定義的合約。  
  
-   應用程式組態檔案 (App.config)。 組態檔會提供安全的 HTTP 繫結中的 WCF 服務模型的基本項目。 它也包含服務的端點，並會啟用中繼資料交換。  
  
> [!NOTE]
>  Visual Studio 已設定為執行使用時，會將 App.config 檔案識別為專案的組態檔[WCF 服務主機 (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)，這是預設組態。 如果是在可執行檔中裝載服務程式庫，您必須將組態程式碼移至該可執行檔的組態檔，因為 DLL 的組態檔是無效的。  
  
### <a name="wcf-service-application-template"></a>WCF 服務應用程式範本  
 WCF 服務應用程式範本位在 [新增專案] 對話方塊中，在**Visual C# \WCF**並**視覺化 basic\wcf&lt;3**。  
  
 當您建立新的專案使用**WCF Web 應用程式服務**範本，專案會包含下列四個檔案：  
  
-   服務主機檔案 (service1.svc)。  
  
-   服務合約檔案 (IService1.cs 或 IService1.vb)。  
  
-   服務實作檔案 (Service1.svc.cs 或 Service1.svc.vb)。  
  
-   Web 組態檔案 (Web.config)。  
  
 範本會自動建立網站 (這會部署到虛擬目錄中) 並在其中裝載服務。  
  
### <a name="wcf-web-site-template"></a>WCF 網站範本  
 WCF 網站範本位在 [新增專案] 對話方塊中，在**Visual C# \web 服務**並**視覺化 {Site\WCF Service&lt;3}**。 這會建立與 WCF 服務應用程式範本相同的檔案，但是其組織方式猶如 ASP.NET 網站。 會建立 App_Code 和 App_Data 資料夾。  
  
### <a name="wcf-service-item-template"></a>WCF 服務項目範本  
 WCF 服務項目範本會提供快速的方式，將 WCF 服務加入至您現有的 Visual Studio 專案的自訂範本。  
  
 若要使用此範本，請移至**方案總管**窗格中，您的專案名稱上按一下滑鼠右鍵，指向**新增**，然後按一下 [**新項目**啟動**加入新項目**] 對話方塊。  
  
 服務介面和實作檔案會放置在根專案資料夾。  
  
 如果新服務的組態區段和現有組態檔屬於相容的類型，則範本會嘗試加以合併。  
  
 如果現有專案是 Web 專案，也會建立服務主機檔案 (service1.svc)。  
  
### <a name="wcf-wf-service-project-and-item-template"></a>WCF WF 服務專案和項目範本。  
 這些範本會建立 WCF 服務裝載工作流程服務，這是可以存取像是 web 服務工作流程。 XAML 或命令式程式撰寫模型各有不同的範本。 您可以使用這些範本來建立循序或狀態機器工作流程。 如需有關這些類型的工作流程的詳細資訊，請參閱 < [Windows Workflow Foundation 教學課程](https://msdn.microsoft.com/library/e9705654-bd96-4b56-8d98-f1f118112d97)。 如需建立工作流程專案的詳細資訊，請參閱[建立舊版工作流程專案](/visualstudio/workflow-designer/creating-legacy-workflow-projects)。  
  
 使用工作流程的 XOML 類型改為程式碼為主時，回應速度更快 visual Studio 設計工具。 XOML 工作流程是預設要建立的工作流程類型。  
  
### <a name="wcf-syndication-service-library-template"></a>WCF 新聞訂閱服務程式庫範本  
 此範本可讓您公開為 WCF 服務 RSS 或 ATOM 格式摘要。 如需詳細資訊，請參閱 < [WCF 新聞訂閱](../../../docs/framework/wcf/feature-details/wcf-syndication.md)。  
  
#### <a name="changing-the-address-of-the-feed"></a>變更摘要的位址  
 新聞訂閱範本在執行期間使用 Internet Explorer。 當您以滑鼠右鍵按一下您的專案中**方案總管**在 Visual Studio 中，選取**屬性**，然後選取**偵錯** 索引標籤上，而且您可以看到的預設位址範本。 Internet Explorer 會嘗試開啟這個位址上的摘要。  
  
 如果您變更摘要的位址，您也必須變更中的地址**偵錯** 索引標籤。如果您沒有這麼做，Internet Explorer 會嘗試開啟預設位址上的摘要，但將無法開啟。  
  
### <a name="ajax-enabled-wcf-service-item-template"></a>具備 AJAX 能力的 WCF 服務項目範本  
 此範本會將未 AJAX 控制項公開為 WCF 服務。 如需 AJAX 控制項的詳細資訊，請參閱[AJAX 控制項文件](https://go.microsoft.com/fwlink/?LinkId=96717)。  
  
### <a name="silverlight-enabled-wcf-service-item-template"></a>啟用 Silverlight 的 WCF 服務項目範本  
 這個範本會建立提供資料給 Silverlight 用戶端或前端的 Web 服務。 範本可以加入至網站或 Web 的應用程式專案，以建立 WCF 服務，其中包含服務程式碼和組態的支援與 Silverlight 用戶端進行通訊。 然後您可以使用**加入服務參考**將服務的用戶端 proxy 加入至用戶端，並在 Silverlight 用戶端和啟用 Silverlight 的 WCF 服務之間交換資料。  
  
 若要存取此範本，以滑鼠右鍵按一下中的網站或 Web 應用程式專案**方案總管 中**，按一下**加入新項目**，然後按一下**啟用 Silverlight 的 WCF 服務**。  
  
> [!NOTE]
>  啟用 Silverlight 的 WCF 服務會在不啟用任何安全性設定的情況下公開 `basicHttpBinding` 端點。 因此，所有連接到這個服務的用戶端，都可以取得此服務的相關資訊。 同樣地，服務和用戶端之間的交換訊息也不會經過簽署或加密。 為了確保端點安全性，您應該使用 ASP.NET 驗證、HTTPS 或其他機制。  
  
## <a name="see-also"></a>另請參閱  
 [WCF 服務主機 (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [WCF 測試用戶端 (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
