---
title: 開發和部署 WCF Data Services
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- deploying [WCF Data Services
- developing applications [WCF Data Services]
ms.assetid: 6557c0e3-5aea-4f6e-bc14-77ad317a168b
ms.openlocfilehash: e02b7317eef8e7124bd5ba9ceef201cddc9bbea1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="developing-and-deploying-wcf-data-services"></a>開發和部署 WCF Data Services
本主題提供有關開發及部署 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]的資訊。 如需更多的基本資訊[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]，請參閱[入門](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)和[概觀](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)。  
  
## <a name="developing-wcf-data-services"></a>開發 WCF Data Services  
 當您使用 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 建立支援 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]的資料服務時，您必須在開發期間執行下列基本工作：  
  
1.  **定義資料模型**  
  
     [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 支援多種資料服務提供者，可讓您根據各種資料來源的資料，定義關聯式資料庫到晚期繫結資料型別的資料模型。 如需詳細資訊，請參閱[資料服務提供者](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)。  
  
2.  **建立資料服務**  
  
     最基本的資料服務會公開繼承自 <xref:System.Data.Services.DataService%601> 類別的類別，其具有實體容器之命名空間限定名稱 `T` 型別。 如需詳細資訊，請參閱 [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)的資訊。  
  
3.  **設定資料服務**  
  
     根據預設， [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 會停用實體容器所公開的資源存取。 <xref:System.Data.Services.DataServiceConfiguration> 介面可讓您設定對資源和服務作業的存取、指定支援的 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]版本，以及定義其他整個服務的行為 (例如，批次行為或在單一回應摘要中可傳回的最大實體數目)。 如需詳細資訊，請參閱[設定資料服務](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)。  
  
 本主題涵蓋使用 Visual Studio 的主要開發和部署資料服務。 如需 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 針對公開資料做為 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要所提供之彈性的詳細資訊，請參閱 [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)的資訊。  
  
### <a name="choosing-a-development-web-server"></a>選擇開發 Web 伺服器  
 當您開發 WCF Data Services 做為[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]應用程式或[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]網站上使用 Visual Studio，您可以選擇要在開發期間執行資料服務的網頁伺服器。 以下的 Web 伺服器整合更輕鬆地測試和偵錯在本機電腦上的資料服務的 Visual Studio。  
  
1.  **本機 IIS 伺服器**  
  
     當您建立屬於 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 應用程式或在 Internet Information Services (IIS) 上執行之 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 網站的資料服務時，建議您使用本機電腦上的 IIS 對您的資料服務進行開發和測試。 在 IIS 上執行資料服務時，更容易在偵錯期間追蹤 HTTP 要求。 這也讓您預先決定 IIS 用來存取資料服務所需之檔案、資料庫和其他資源時所需的必要權限。 若要在 IIS 上執行您的資料服務，您必須確保 IIS 和 Windows Communication Foundation (WCF) 會安裝並正確設定並授予 IIS 帳戶在檔案系統和資料庫中。 如需詳細資訊，請參閱 [如何：開發在 IIS 上執行的 WCF 資料服務](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)。  
  
    > [!NOTE]
    >  您必須以系統管理員權限，才能讓開發環境設定本機 IIS 伺服器來執行 Visual Studio。  
  
2.  **Visual Studio 程式開發伺服器**  
  
     Visual Studio 包含內建的 Web 伺服器、 Visual Studio 程式開發伺服器中，這是預設的 Web 伺服器的[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]專案。 這個 Web 伺服器是為了在開發期間於本機電腦上執行 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 專案而設計。 [WCF Data Services 快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)示範如何建立會在 Visual Studio 程式開發伺服器中執行的資料服務。  
  
     當您使用 Visual Studio 程式開發伺服器開發資料服務時，您應該注意下列限制：  
  
    -   只能在本機電腦上存取這個伺服器。  
  
    -   此伺服器會接聽 `localhost` 和一個特定的連接埠 (而非連接埠 80)，此連接埠是用於 HTTP 訊息的預設連接埠。 如需詳細資訊，請參閱 [Visual Studio 中 ASP.NET Web 專案的 Web 伺服器](http://msdn.microsoft.com/library/31d4f588-df59-4b7e-b9ea-e1f2dd204328)。  
  
    -   此伺服器會在目前使用者帳戶的內容中執行資料服務。 例如，如果您以系統管理員層級的使用者身分執行，執行 Visual Studio 程式開發伺服器中的資料服務必須系統管理員層級權限。 這可能會使資料服務能夠存取在部署到 IIS 伺服器時沒有存取權限的資源。  
  
    -   這個伺服器不包含 IIS 的額外功能，例如驗證。  
  
    -   此伺服器無法處理區塊式 HTTP 資料流，從資料服務存取大型二進位資料時， [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 用戶端預設會傳送這個資料流。 如需詳細資訊，請參閱[資料流處理提供者](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md)。  
  
    -   此伺服器在處理 URL 中的句點 (`.`) 字元時會出現問題 (即使 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 在索引鍵值中支援這個字元)。  
  
    > [!TIP]
    >  即使您可以使用 Visual Studio 程式開發伺服器測試資料服務，在開發期間，您應該部署到執行 IIS 的 Web 伺服器之後，再次測試它們。  
  
3.  **Microsoft Azure 開發環境**  
  
     Windows Azure Tools for Visual Studio 包含一組整合式開發 Visual Studio 中的 Windows Azure 服務的工具。 您可以使用這些工具開發可以部署到 Microsoft Azure 的資料服務，並在部署之前，先在本機電腦上測試資料服務。 使用 Visual Studio 開發 Windows Azure 平台執行的資料服務時，請使用這些工具。 您可以下載 Windows Azure Tools for Visual Studio 從[Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=201848)。 如需開發在 Windows Azure 執行之資料服務的詳細資訊，請參閱下列文章[部署在 Windows Azure 中 OData 服務](http://go.microsoft.com/fwlink/?LinkId=201847)。  
  
### <a name="development-tips"></a>開發秘訣  
 當您開發資料服務時，應該考慮下列事項：  
  
-   如果您計劃驗證使用者或限制特定使用者存取，請決定您資料服務的安全性需求。 如需詳細資訊，請參閱 [Securing WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)。  
  
-   透過讓您檢查要求和回應訊息的內容對資料服務進行偵錯時，HTTP 檢查程式可能會很有幫助。 可以顯示原始封包的任何網路封包分析器可用於檢查資料服務的 HTTP 要求及其回應。  
  
-   對資料服務進行偵錯時，可能比正常作業期間更想要從資料服務取得有關錯誤的詳細資訊。 您可以從資料服務取得其他錯誤資訊，方法是，將 <xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A> 中的 <xref:System.Data.Services.DataServiceConfiguration> 屬性 (Property) 設為 `true` ，然後在資料服務類別上，將 <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A> 屬性 (Attribute) 的 <xref:System.ServiceModel.Description.ServiceDebugBehavior> 屬性 (Property) 設為 `true`。 如需詳細資訊，請參閱下列文章[偵錯 WCF Data Services](http://go.microsoft.com/fwlink/?LinkId=201868)。 您也可以在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中啟用追蹤來檢視在 HTTP 訊息層引發的例外狀況。 如需詳細資訊，請參閱 [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)。  
  
-   資料服務通常會開發為[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]應用程式專案，但是您也可以建立您資料服務當做[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Visual Studio 中的網站專案。 兩種專案類型之間差異的詳細資訊，請參閱[NIB: Web 應用程式專案與 Visual Studio 中的網站專案](http://msdn.microsoft.com/library/2861815e-f5a2-4378-a2f8-b8a86dc012f5)。  
  
-   當您建立資料服務使用**加入新項目**由裝載在 Visual Studio 中，資料服務 對話方塊[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]在 IIS 中。 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 和 IIS 是資料服務的預設主機，因此支援其他裝載選項。 如需詳細資訊，請參閱[裝載資料服務](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)。  
  
## <a name="deploying-wcf-data-services"></a>部署 WCF Data Services  
 WCF Data Services 提供選擇裝載資料服務之程序的彈性。 您可以使用 Visual Studio，將資料服務部署到下列平台：  
  
-   **IIS 裝載的 Web 服務**  
  
     將資料服務開發為 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 專案時，可以使用標準的 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 部署程序部署至 IIS Web 伺服器。  Visual Studio 提供下列部署技術，用於[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]，端視種類的[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]裝載您要部署之資料服務的專案。  
  
    -   **用於 ASP.NET Web 應用程式的部署技術**  
  
        -   [Web 部署套件](http://msdn.microsoft.com/library/1f9713c8-9540-494c-b80d-9893b970ad6f)  
  
        -   [單鍵發行](http://msdn.microsoft.com/library/59226246-99ad-4aec-975d-7c61e8a8911c)  
  
    -   **用於 ASP.NET 網站的部署技術**  
  
        -   [複製網站工具](http://msdn.microsoft.com/library/b819aed4-014b-427e-be80-02317b1bb003)  
  
        -   [發行網站工具](http://msdn.microsoft.com/library/d0a1a20f-15be-4940-9485-cb8e4aa8181b)  
  
        -   [XCopy](http://msdn.microsoft.com/library/4312c651-2119-49be-bbeb-ee28bdbfe71e)  
  
     如需有關的部署選項[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]應用程式，請參閱[Visual Studio 和 ASP.NET 的 Web 部署概觀](http://msdn.microsoft.com/library/99bd1927-b59f-4e02-87b4-55c6ba2adbc3)。  
  
    > [!TIP]
    >  在您嘗試將資料服務部署到 IIS 之前，請確認您已經測試執行 IIS 之 Web 伺服器的部署。 如需詳細資訊，請參閱 [如何：開發在 IIS 上執行的 WCF 資料服務](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)。  
  
-   **Microsoft Azure**  
  
     您可以使用 Windows Azure Tools for Visual Studio，Windows azure 部署資料服務。 您可以下載 Windows Azure Tools for Visual Studio 從[Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=201848)。 如需將資料服務部署至 Windows Azure 的詳細資訊，請參閱下列文章[部署在 Windows Azure 中 OData 服務](http://go.microsoft.com/fwlink/?LinkId=201847)。  
  
### <a name="deployment-considerations"></a>部署考量  
 部署資料服務時，應該考慮下列事項：  
  
-   當您部署使用 [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] 提供者存取 SQL Server 資料庫的資料服務時，可能也需要使用資料服務部署傳播資料結構、資料或兩者。 Visual Studio 可以自動建立指令碼 （.sql 檔），以在目的地資料庫中，執行這項操作，而且這些指令碼可併入 Web 部署套件[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]應用程式。 如需詳細資訊，請參閱[NIB： 如何： 部署資料庫與 Web 應用程式專案](http://msdn.microsoft.com/library/683b33f1-8a3d-45cf-af6e-61ab50fc518b)。 如[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]網站上，您可以使用**資料庫發行精靈**Visual Studio 中。 如需詳細資訊，請參閱 [部署資料庫使用資料庫發行精靈](http://msdn.microsoft.com/library/1e3682e7-8b57-4da6-a393-af9640ccf8b7)。  
  
-   [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 包含基本的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 實作，因此您可以使用 Windows Server AppFabric 監視部署至在 Windows Server 上執行之 IIS 的資料服務。 如需使用 Windows Server AppFabric 監視資料服務的詳細資訊，請參閱下列文章[使用 Windows Server AppFabric 追蹤 WCF Data Services](http://go.microsoft.com/fwlink/?LinkID=202005)。  
  
## <a name="see-also"></a>另請參閱  
 [裝載資料服務](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)  
 [保護 WCF 資料服務的安全](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)  
 [定義 WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
