---
title: 開發和部署 WCF Data Services
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- deploying [WCF Data Services
- developing applications [WCF Data Services]
ms.assetid: 6557c0e3-5aea-4f6e-bc14-77ad317a168b
ms.openlocfilehash: cf1782eaf54701f0cf93576325b3d46e8bc4d3f1
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44183808"
---
# <a name="develop-and-deploy-wcf-data-services"></a>開發和部署 WCF 資料服務

本主題提供有關開發及部署 WCF 資料服務的資訊。 更基本 WCF Data Services 的詳細資訊，請參閱[快速入門](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)並[概觀](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)。

## <a name="develop-wcf-data-services"></a>開發 WCF Data Services

當您使用 WCF Data Services 來建立資料服務支援[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]，您必須在開發期間執行下列基本工作：

1.  **定義資料模型**

     WCF Data Services 支援各種不同的資料服務提供者可讓您定義資料模型，根據從各種關聯式資料庫到晚期繫結資料類型的資料來源的資料。 如需詳細資訊，請參閱 <<c0> [ 資料服務提供者](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)。

2.  **建立資料服務**

     最基本的資料服務會公開繼承自 <xref:System.Data.Services.DataService%601> 類別的類別，其具有實體容器之命名空間限定名稱 `T` 型別。 如需詳細資訊，請參閱 [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)的資訊。

3.  **設定資料服務**

     根據預設，WCF Data Services 會停用實體容器所公開的資源的存取權。 <xref:System.Data.Services.DataServiceConfiguration>介面可讓您設定資源的存取權和服務作業，請指定支援的 OData 中，版本，以及定義其他整個服務的行為，例如，批次行為或可傳回的實體數目上限在單一回應摘要中。 如需詳細資訊，請參閱 <<c0> [ 設定資料服務](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)。

本主題涵蓋使用 Visual Studio 的主要開發和部署資料服務。 您將資料公開為 OData 摘要的 WCF 資料服務所提供之彈性的詳細資訊，請參閱[Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)。

### <a name="choose-a-development-web-server"></a>選擇開發 Web 伺服器

當您開發 WCF 資料服務，當做[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]應用程式或[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]網站上使用 Visual Studio 2015，您可以選擇要在開發期間執行資料服務的 Web 伺服器。 以下的 Web 伺服器整合至 Visual Studio，讓您更輕鬆地測試和偵錯您本機電腦上的資料服務。

1.  **本機 IIS 伺服器**

     當您建立屬於 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 應用程式或在 Internet Information Services (IIS) 上執行之 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 網站的資料服務時，建議您使用本機電腦上的 IIS 對您的資料服務進行開發和測試。 在 IIS 上執行資料服務時，更容易在偵錯期間追蹤 HTTP 要求。 這也讓您預先決定 IIS 用來存取資料服務所需之檔案、資料庫和其他資源時所需的必要權限。 若要在 IIS 上執行您的資料服務，您必須可確保 IIS 和 Windows Communication Foundation (WCF) 會安裝並正確設定並將 IIS 帳戶的存取權授與檔案系統和資料庫中。 如需詳細資訊，請參閱 [如何：開發在 IIS 上執行的 WCF 資料服務](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)。

    > [!NOTE]
    > 若要啟用的開發環境來設定本機 IIS 伺服器的系統管理員權限，您必須執行 Visual Studio。

2.  **Visual Studio 程式開發伺服器**

     Visual Studio 包括內建的 Web 伺服器、 Visual Studio 程式開發伺服器中，也就是預設 Web 伺服器，如[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]專案。 這個 Web 伺服器是為了在開發期間於本機電腦上執行 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 專案而設計。 [WCF Data Services 快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)示範如何建立會在 Visual Studio 程式開發伺服器中執行的資料服務。

     當您使用 Visual Studio 程式開發伺服器開發資料服務時，您應該注意下列限制：

    -   只能在本機電腦上存取這個伺服器。

    -   此伺服器會接聽 `localhost` 和一個特定的連接埠 (而非連接埠 80)，此連接埠是用於 HTTP 訊息的預設連接埠。 如需詳細資訊，請參閱 [Visual Studio 中 ASP.NET Web 專案的 Web 伺服器](https://msdn.microsoft.com/library/31d4f588-df59-4b7e-b9ea-e1f2dd204328)。

    -   此伺服器會在目前使用者帳戶的內容中執行資料服務。 比方說，如果您正在以系統管理員層級的使用者身分，在 Visual Studio 程式開發伺服器中執行的資料服務會有系統管理員層級權限。 這可能會使資料服務能夠存取在部署到 IIS 伺服器時沒有存取權限的資源。

    -   這個伺服器不包含 IIS 的額外功能，例如驗證。

    -   此伺服器無法處理區塊的 HTTP 資料流，這會傳送為 WCF Data Services 用戶端的預設值，從資料服務存取大型二進位資料時。 如需詳細資訊，請參閱 <<c0> [ 資料流處理提供者](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md)。

    -   此伺服器已處理期間的問題 (`.`) 字元，在 URL 中，即使此字元由 WCF Data Services 支援索引鍵值。

    > [!TIP]
    > 雖然您可以使用 Visual Studio 程式開發伺服器來測試您的資料服務開發期間，您應該在部署到執行 IIS 的 Web 伺服器之後，再次測試它們。

3.  **Microsoft Azure 開發環境**

     Windows Azure Tools for Visual Studio 包含一組整合式開發 Visual Studio 中的 Windows Azure 服務的工具。 您可以使用這些工具開發可以部署到 Microsoft Azure 的資料服務，並在部署之前，先在本機電腦上測試資料服務。 當您使用 Visual Studio 開發 Windows Azure 平台執行的資料服務時，請使用這些工具。 您可以下載 Windows Azure Tools for Visual Studio [Microsoft 下載中心](https://go.microsoft.com/fwlink/?LinkID=201848)。 如需有關如何開發在 Windows Azure 執行之資料服務的詳細資訊，請參閱文章[部署 Windows Azure 中的 OData 服務](https://go.microsoft.com/fwlink/?LinkId=201847)。

### <a name="development-tips"></a>開發秘訣

當您開發資料服務時，應該考慮下列事項：

-   如果您計劃驗證使用者或限制特定使用者存取，請決定您資料服務的安全性需求。 如需詳細資訊，請參閱 [Securing WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)。

-   透過讓您檢查要求和回應訊息的內容對資料服務進行偵錯時，HTTP 檢查程式可能會很有幫助。 可以顯示原始封包的任何網路封包分析器可用於檢查資料服務的 HTTP 要求及其回應。

-   對資料服務進行偵錯時，可能比正常作業期間更想要從資料服務取得有關錯誤的詳細資訊。 您可以從資料服務取得其他錯誤資訊，方法是，將 <xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A> 中的 <xref:System.Data.Services.DataServiceConfiguration> 屬性 (Property) 設為 `true` ，然後在資料服務類別上，將 <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A> 屬性 (Attribute) 的 <xref:System.ServiceModel.Description.ServiceDebugBehavior> 屬性 (Property) 設為 `true`。 如需詳細資訊，請參閱文章[偵錯 WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=201868)。 您也可以啟用追蹤，在 WCF 中，檢視在 HTTP 訊息層引發的例外狀況。 如需詳細資訊，請參閱 [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)。

-   資料服務通常會開發為[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]應用程式專案，但您也可以建立資料服務當做[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Visual Studio 中的網站專案。 如需兩種專案類型之間的差異資訊，請參閱[NIB︰ Web 應用程式專案與 Visual Studio 中的網站專案](https://msdn.microsoft.com/library/2861815e-f5a2-4378-a2f8-b8a86dc012f5)。

-   當您使用，會在建立資料服務時**加入新項目**對話方塊中，在 Visual Studio 中，資料服務由[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]在 IIS 中。 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 和 IIS 是資料服務的預設主機，因此支援其他裝載選項。 如需詳細資訊，請參閱 <<c0> [ 裝載資料服務](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)。

## <a name="deploy-wcf-data-services"></a>部署 WCF 資料服務

WCF Data Services 提供選擇裝載資料服務之程序的彈性。 若要將資料服務部署到下列平台，您可以使用 Visual Studio:

-   **IIS 裝載的 Web 服務**

     將資料服務開發為 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 專案時，可以使用標準的 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 部署程序部署至 IIS Web 伺服器。  Visual Studio 提供下列部署技術[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]，這取決於類型的[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]裝載您要部署之資料服務的專案。

    -   **用於 ASP.NET Web 應用程式的部署技術**

        -   [Web 部署套件](https://msdn.microsoft.com/library/1f9713c8-9540-494c-b80d-9893b970ad6f)

        -   [單鍵發行](https://msdn.microsoft.com/library/59226246-99ad-4aec-975d-7c61e8a8911c)

    -   **用於 ASP.NET 網站的部署技術**

        -   [複製網站工具](https://msdn.microsoft.com/library/b819aed4-014b-427e-be80-02317b1bb003)

        -   [發行網站工具](https://msdn.microsoft.com/library/d0a1a20f-15be-4940-9485-cb8e4aa8181b)

        -   [XCopy](https://msdn.microsoft.com/library/4312c651-2119-49be-bbeb-ee28bdbfe71e)

     如需有關的部署選項[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]應用程式，請參閱 <<c2> [ 的 Visual Studio 及 ASP.NET Web 部署概觀](https://msdn.microsoft.com/library/99bd1927-b59f-4e02-87b4-55c6ba2adbc3)。

    > [!TIP]
    > 在您嘗試將資料服務部署到 IIS 之前，請確認您已經測試執行 IIS 之 Web 伺服器的部署。 如需詳細資訊，請參閱 [How to: Develop a WCF Data Service Running on IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)。

-   **Microsoft Azure**

     您可以使用 Windows Azure Tools for Visual Studio，到 Windows Azure 部署的資料服務。 您可以下載 Windows Azure Tools for Visual Studio [Microsoft 下載中心](https://go.microsoft.com/fwlink/?LinkID=201848)。 如需將資料服務部署至 Windows Azure 的詳細資訊，請參閱文章[部署 Windows Azure 中的 OData 服務](https://go.microsoft.com/fwlink/?LinkId=201847)。

### <a name="deployment-considerations"></a>部署考量

部署資料服務時，應該考慮下列事項：

-   當您部署使用 [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] 提供者存取 SQL Server 資料庫的資料服務時，可能也需要使用資料服務部署傳播資料結構、資料或兩者。 Visual Studio 可以自動建立指令碼 （.sql 檔案），以在目的地資料庫中，執行這項操作，而且這些指令碼可以包含的 Web 部署套件中[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]應用程式。 如需詳細資訊，請參閱 <<c0> [ 如何： 資料庫使用 Web 應用程式專案部署](https://msdn.microsoft.com/library/683b33f1-8a3d-45cf-af6e-61ab50fc518b)。 針對[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]網站上，您可以藉由使用**Database Publishing Wizard** Visual Studio 中。 如需詳細資訊，請參閱 [部署資料庫使用資料庫發行精靈](https://msdn.microsoft.com/library/1e3682e7-8b57-4da6-a393-af9640ccf8b7)。

-   因為 WCF Data Services 包含基本的 WCF 實作，您可以使用 Windows Server AppFabric 監視資料服務部署至 Windows Server 上執行的 IIS。 如需使用 Windows Server AppFabric 監視資料服務的詳細資訊，請參閱文章[使用 Windows Server AppFabric 追蹤 WCF Data Services](https://go.microsoft.com/fwlink/?LinkID=202005)。

## <a name="see-also"></a>另請參閱

- [裝載資料服務](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)
- [保護 WCF 資料服務的安全](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)
- [定義 WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
