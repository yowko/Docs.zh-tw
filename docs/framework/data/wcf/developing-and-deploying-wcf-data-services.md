---
title: "開發和部署 WCF Data Services"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- deploying [WCF Data Services
- developing applications [WCF Data Services]
ms.assetid: 6557c0e3-5aea-4f6e-bc14-77ad317a168b
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 87a074b96583f44e8655c9efde145e28b490f6e9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
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
  
 本主題主要涵蓋如何使用 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]開發和部署資料服務。 如需 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 針對公開資料做為 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要所提供之彈性的詳細資訊，請參閱 [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)的資訊。  
  
### <a name="choosing-a-development-web-server"></a>選擇開發 Web 伺服器  
 當您使用 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 開發 WCF Data Services 做為 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 應用程式或 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]網站時，可以選擇在開發期間執行資料服務所使用的 Web 伺服器。 以下的 Web 伺服器整合 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] ，讓它更容易針對本機電腦上的資料服務進行測試和偵錯。  
  
1.  **本機 IIS 伺服器**  
  
     當您建立屬於 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 應用程式或在 Internet Information Services (IIS) 上執行之 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 網站的資料服務時，建議您使用本機電腦上的 IIS 對您的資料服務進行開發和測試。 在 IIS 上執行資料服務時，更容易在偵錯期間追蹤 HTTP 要求。 這也讓您預先決定 IIS 用來存取資料服務所需之檔案、資料庫和其他資源時所需的必要權限。 若要在 IIS 上執行資料服務，您必須確認 IIS 和 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 都已正確安裝並設定，並授予 IIS 帳戶在檔案系統和資料庫中的存取權。 如需詳細資訊，請參閱 [How to: Develop a WCF Data Service Running on IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)。  
  
    > [!NOTE]
    >  您必須使用系統管理員權限執行 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] ，才能讓開發環境設定本機 IIS 伺服器。  
  
2.  **Visual Studio 程式開發伺服器**  
  
     [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 包括內建的 Web 伺服器、 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 程式開發伺服器，也就是 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 專案的預設 Web 伺服器。 這個 Web 伺服器是為了在開發期間於本機電腦上執行 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 專案而設計。 [WCF Data Services 快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) 會示範如何建立在 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 程式開發伺服器上執行的資料服務。  
  
     當您使用 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 程式開發伺服器開發資料服務時，您應該要注意下列限制：  
  
    -   只能在本機電腦上存取這個伺服器。  
  
    -   此伺服器會接聽 `localhost` 和一個特定的連接埠 (而非連接埠 80)，此連接埠是用於 HTTP 訊息的預設連接埠。 如需詳細資訊，請參閱 [Visual Studio 中 ASP.NET Web 專案的 Web 伺服器](http://msdn.microsoft.com/en-us/31d4f588-df59-4b7e-b9ea-e1f2dd204328)。  
  
    -   此伺服器會在目前使用者帳戶的內容中執行資料服務。 例如，如果您要以系統管理員層級的使用者身分執行，在 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 程式開發伺服器中執行的資料服務將具備系統管理員層級的權限。 這可能會使資料服務能夠存取在部署到 IIS 伺服器時沒有存取權限的資源。  
  
    -   這個伺服器不包含 IIS 的額外功能，例如驗證。  
  
    -   此伺服器無法處理區塊式 HTTP 資料流，從資料服務存取大型二進位資料時， [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 用戶端預設會傳送這個資料流。 如需詳細資訊，請參閱[資料流處理提供者](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md)。  
  
    -   此伺服器在處理 URL 中的句點 (`.`) 字元時會出現問題 (即使 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 在索引鍵值中支援這個字元)。  
  
    > [!TIP]
    >  雖然您可以在開發期間使用 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 程式開發伺服器測試資料服務，您都應該在部署到執行 IIS 的 Web 伺服器之後，再次進行測試。  
  
3.  **Microsoft Azure 開發環境**  
  
     用於 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 的 Microsoft Azure Tools 包括一組整合的工具，可用來在 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]中開發 Microsoft Azure 服務。 您可以使用這些工具開發可以部署到 Microsoft Azure 的資料服務，並在部署之前，先在本機電腦上測試資料服務。 使用 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 開發在 Microsoft Azure 平台上執行的資料服務時，請使用這些工具。 您可以從 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] Microsoft 下載中心 [下載適用於](http://go.microsoft.com/fwlink/?LinkID=201848)的 Microsoft Azure 工具。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] 開發在 Microsoft Azure 上執行之資料服務的詳細資訊，請參閱文章 [在 Microsoft Azure 中部署 OData 服務](http://go.microsoft.com/fwlink/?LinkId=201847)。  
  
### <a name="development-tips"></a>開發秘訣  
 當您開發資料服務時，應該考慮下列事項：  
  
-   如果您計劃驗證使用者或限制特定使用者存取，請決定您資料服務的安全性需求。 如需詳細資訊，請參閱 [Securing WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)。  
  
-   透過讓您檢查要求和回應訊息的內容對資料服務進行偵錯時，HTTP 檢查程式可能會很有幫助。 可以顯示原始封包的任何網路封包分析器可用於檢查資料服務的 HTTP 要求及其回應。  
  
-   對資料服務進行偵錯時，可能比正常作業期間更想要從資料服務取得有關錯誤的詳細資訊。 您可以從資料服務取得其他錯誤資訊，方法是，將 <xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A> 中的 <xref:System.Data.Services.DataServiceConfiguration> 屬性 (Property) 設為 `true` ，然後在資料服務類別上，將 <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A> 屬性 (Attribute) 的 <xref:System.ServiceModel.Description.ServiceDebugBehavior> 屬性 (Property) 設為 `true`。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] 文章 [偵錯 WCF Data Services](http://go.microsoft.com/fwlink/?LinkId=201868)。 您也可以在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中啟用追蹤來檢視在 HTTP 訊息層引發的例外狀況。 如需詳細資訊，請參閱 [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)。  
  
-   資料服務通常會開發為 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 應用程式專案，但是您也可以建立您的資料服務做為 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 中的 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]網站專案。 如需兩種專案類型之間差異的相關資訊，請參閱 [NIB︰Web 應用程式專案與 Visual Studio 中的網站專案](http://msdn.microsoft.com/en-us/2861815e-f5a2-4378-a2f8-b8a86dc012f5)。  
  
-   當您使用 **中的 [加入新項目**[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]] 對話方塊建立資料服務時，資料服務是由 IIS 中的 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 裝載。 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 和 IIS 是資料服務的預設主機，因此支援其他裝載選項。 如需詳細資訊，請參閱[裝載資料服務](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)。  
  
## <a name="deploying-wcf-data-services"></a>部署 WCF Data Services  
 WCF Data Services 提供選擇裝載資料服務之程序的彈性。 您可以使用 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 將資料服務部署到下列平台：  
  
-   **IIS 裝載的 Web 服務**  
  
     將資料服務開發為 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 專案時，可以使用標準的 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 部署程序部署至 IIS Web 伺服器。  [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 為 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]提供下列部署技術，端視裝載您要部署之資料服務的 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 專案種類而定。  
  
    -   **用於 ASP.NET Web 應用程式的部署技術**  
  
        -   [Web 部署套件](http://msdn.microsoft.com/en-us/1f9713c8-9540-494c-b80d-9893b970ad6f)  
  
        -   [單鍵發行](http://msdn.microsoft.com/en-us/59226246-99ad-4aec-975d-7c61e8a8911c)  
  
    -   **用於 ASP.NET 網站的部署技術**  
  
        -   [複製網站工具](http://msdn.microsoft.com/library/b819aed4-014b-427e-be80-02317b1bb003)  
  
        -   [發行網站工具](http://msdn.microsoft.com/library/d0a1a20f-15be-4940-9485-cb8e4aa8181b)  
  
        -   [XCopy](http://msdn.microsoft.com/library/4312c651-2119-49be-bbeb-ee28bdbfe71e)  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]部署選項[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]應用程式，請參閱[Visual Studio 和 ASP.NET 的 Web 部署概觀](http://msdn.microsoft.com/en-us/99bd1927-b59f-4e02-87b4-55c6ba2adbc3)。  
  
    > [!TIP]
    >  在您嘗試將資料服務部署到 IIS 之前，請確認您已經測試執行 IIS 之 Web 伺服器的部署。 如需詳細資訊，請參閱 [How to: Develop a WCF Data Service Running on IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)。  
  
-   **Microsoft Azure**  
  
     您可以使用 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]的 Microsoft Azure Tools，將資料服務部署到 Microsoft Azure。 您可以從 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] Microsoft 下載中心 [下載適用於](http://go.microsoft.com/fwlink/?LinkID=201848)的 Microsoft Azure 工具。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] 將資料服務部署至 Microsoft Azure 的詳細資訊，請參閱文章 [在 Microsoft Azure 中部署 OData 服務](http://go.microsoft.com/fwlink/?LinkId=201847)。  
  
### <a name="deployment-considerations"></a>部署考量  
 部署資料服務時，應該考慮下列事項：  
  
-   當您部署使用 [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] 提供者存取 SQL Server 資料庫的資料服務時，可能也需要使用資料服務部署傳播資料結構、資料或兩者。 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 可以自動建立指令碼 (.sql 檔)，在目的資料庫中進行這項處理，而且這些指令碼可併入 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 應用程式的 Web 部署套件中。 如需詳細資訊，請參閱 [NIB：作法：使用 Web 應用程式專案部署資料庫](http://msdn.microsoft.com/en-us/683b33f1-8a3d-45cf-af6e-61ab50fc518b)。 如果是 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 網站，則您可以使用 **中的 [資料庫發行精靈]**[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]來進行這項操作。 如需詳細資訊，請參閱 [Deploying a Database by Using the Database Publishing Wizard](http://msdn.microsoft.com/library/1e3682e7-8b57-4da6-a393-af9640ccf8b7)。  
  
-   [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 包含基本的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 實作，因此您可以使用 Windows Server AppFabric 監視部署至在 Windows Server 上執行之 IIS 的資料服務。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] 使用 Windows Server AppFabric 監視資料服務的詳細資訊，請參閱文章 [使用 Windows Server AppFabric 追蹤 WCF Data Services](http://go.microsoft.com/fwlink/?LinkID=202005)。  
  
## <a name="see-also"></a>另請參閱  
 [裝載資料服務](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)  
 [保護 WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)  
 [定義 WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
