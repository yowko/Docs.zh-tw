---
title: 開發和部署 WCF Data Services
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- deploying [WCF Data Services
- developing applications [WCF Data Services]
ms.assetid: 6557c0e3-5aea-4f6e-bc14-77ad317a168b
ms.openlocfilehash: 484505406701b52a2b80b95b718a23a2156aa22c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/29/2020
ms.locfileid: "90556085"
---
# <a name="develop-and-deploy-wcf-data-services"></a>開發和部署 WCF Data Services

本文提供有關開發和部署 WCF Data Services 的資訊。 如需有關 WCF Data Services 的詳細基本資訊，請參閱 [消費者入門](getting-started-with-wcf-data-services.md) 和 [總覽](wcf-data-services-overview.md)。

## <a name="develop-wcf-data-services"></a>開發 WCF Data Services

當您使用 WCF Data Services 建立支援開放式資料通訊協定 (OData) 的資料服務時，您必須在開發期間執行下列基本工作：

1. **定義資料模型**

     WCF Data Services 支援各種資料服務提供者，可讓您根據各種資料來源中的資料，從關係資料庫到晚期繫結資料類型，來定義資料模型。 如需詳細資訊，請參閱 [資料服務提供者](data-services-providers-wcf-data-services.md)。

2. **建立資料服務**

     最基本的資料服務會公開繼承自 <xref:System.Data.Services.DataService%601> 類別的類別，其具有實體容器之命名空間限定名稱 `T` 型別。 如需詳細資訊，請參閱 [Defining WCF Data Services](defining-wcf-data-services.md)的資訊。

3. **設定資料服務**

     根據預設，WCF Data Services 會停用實體容器所公開之資源的存取權。 <xref:System.Data.Services.DataServiceConfiguration>介面可讓您設定對資源和服務作業的存取、指定支援的 OData 版本，以及定義其他整個服務的行為，例如批次處理行為或可在單一回應摘要中傳回的實體數目上限。 如需詳細資訊，請參閱設定 [資料服務](configuring-the-data-service-wcf-data-services.md)。

本文主要說明如何使用 Visual Studio 來開發和部署資料服務。 如需 WCF Data Services 針對將資料公開為 OData 摘要所提供之彈性的詳細資訊，請參閱 [定義 WCF Data Services](defining-wcf-data-services.md)。

### <a name="choose-a-development-web-server"></a>選擇開發 Web 服務器

當您使用 Visual Studio 2015 開發 WCF 資料服務作為 ASP.NET 應用程式或 ASP.NET 網站時，您可以選擇在開發期間用來執行資料服務的 Web 服務器。 下列 Web 服務器會與 Visual Studio 整合，讓您更輕鬆地在本機電腦上測試及偵測您的資料服務。

1. **本機 IIS 伺服器**

     當您建立的資料服務是 ASP.NET 應用程式，或是在 Internet Information Services (IIS) 上執行的 ASP.NET 網站時，我們建議您在本機電腦上使用 IIS 來開發和測試您的資料服務。 在 IIS 上執行資料服務時，更容易在偵錯期間追蹤 HTTP 要求。 這也可讓您預先確定 IIS 所需的必要許可權，以存取資料服務所需的檔案、資料庫和其他資源。 若要在 IIS 上執行資料服務，請確定已正確安裝和設定 IIS 和 Windows Communication Foundation (WCF) ，並將存取權授與檔案系統和資料庫中的 IIS 帳戶。 如需詳細資訊，請參閱 [How to: Develop a WCF Data Service Running on IIS](how-to-develop-a-wcf-data-service-running-on-iis.md)。

    > [!NOTE]
    > 您必須以系統管理員許可權執行 Visual Studio，才能讓開發環境設定本機 IIS 伺服器。

2. **Visual Studio 程式開發伺服器**

     Visual Studio 包含內建的 Web 服務器，也就是 Visual Studio 程式開發伺服器，也就是 ASP.NET 專案的預設 Web 服務器。 此網頁伺服器的設計目的是在開發期間于本機電腦上執行 ASP.NET 專案。 [WCF Data Services 快速入門](quickstart-wcf-data-services.md)會顯示如何建立在 Visual Studio 程式開發伺服器中執行的資料服務。

     當您使用 Visual Studio 程式開發伺服器開發資料服務時，請注意下列限制：

    - 只能在本機電腦上存取這個伺服器。

    - 此伺服器會接聽 `localhost` 和一個特定的連接埠 (而非連接埠 80)，此連接埠是用於 HTTP 訊息的預設連接埠。 如需詳細資訊，請參閱 [Visual Studio 中 ASP.NET Web 專案的 Web 伺服器](/previous-versions/aspnet/58wxa9w5(v=vs.120))。

    - 此伺服器會在目前使用者帳戶的內容中執行資料服務。 例如，如果您是以系統管理員層級的使用者身分執行，在 Visual Studio 程式開發伺服器中執行的資料服務將擁有系統管理員層級的許可權。 這可能會使資料服務能夠存取在部署到 IIS 伺服器時沒有存取權限的資源。

    - 這個伺服器不包含 IIS 的額外功能，例如驗證。

    - 從資料服務存取大型二進位資料時，此伺服器無法處理 WCF Data Services 用戶端預設傳送的區塊 HTTP 資料流程。 如需詳細資訊，請參閱 [資料流程提供者](streaming-provider-wcf-data-services.md)。

    - 此伺服器在 URL 中處理期間 (`.`) 字元時發生問題，即使金鑰值的 WCF Data Services 支援此字元也是一樣。

    > [!TIP]
    > 雖然您可以在開發期間使用 Visual Studio 程式開發伺服器來測試您的資料服務，但是您應該在部署到執行 IIS 的 Web 服務器之後，再次進行測試。

3. **Azure 開發環境**

     適用于 Visual Studio 的 azure Tools 包含一組整合式工具，可供您在 Visual Studio 中開發 Azure 服務。 使用這些工具，您可以開發可部署至 Azure 的資料服務，而且您可以在部署之前，先在本機電腦上測試資料服務。 使用 Visual Studio 開發在 Azure 平臺上執行的資料服務時，請使用這些工具。 如需安裝工具的相關資訊，請參閱 [Visual Studio 2015 的 Azure 工具](../../../azure/vs2015-install.md)。 如需有關開發在 Azure 上執行之資料服務的詳細資訊，請參閱在 [azure 中部署 OData 服務](/archive/blogs/astoriateam/deploying-an-odata-service-in-windows-azure)的文章。

### <a name="development-tips"></a>開發秘訣

當您開發資料服務時，請考慮下列事項：

- 如果您打算驗證使用者或限制特定使用者的存取權，請判斷資料服務的安全性需求。 如需詳細資訊，請參閱 [Securing WCF Data Services](securing-wcf-data-services.md)。

- 當您透過讓您檢查要求和回應訊息的內容時，HTTP 檢查程式可能會很有説明。 可以顯示原始封包的任何網路封包分析器可用於檢查資料服務的 HTTP 要求及其回應。

- 當您對資料服務進行偵錯工具時，您可能會想要從資料服務取得比一般作業期間更多的錯誤相關資訊。 您可以從資料服務取得其他錯誤資訊，方法是，將 <xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A> 中的 <xref:System.Data.Services.DataServiceConfiguration> 屬性 (Property) 設為 `true` ，然後在資料服務類別上，將 <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A> 屬性 (Attribute) 的 <xref:System.ServiceModel.Description.ServiceDebugBehavior> 屬性 (Property) 設為 `true`。 如需詳細資訊，請參閱 post [偵錯工具 WCF Data Services](/archive/blogs/phaniraj/debugging-wcf-data-services)。 您也可以在 WCF 中啟用追蹤，以查看在 HTTP 訊息層中引發的例外狀況。 如需詳細資訊，請參閱 [Configuring Tracing](../../wcf/diagnostics/tracing/configuring-tracing.md)。

- 資料服務通常會開發為 ASP.NET 應用程式專案，但您也可以在 Visual Studio 中將資料服務建立為 ASP.NET 的網站專案。 如需兩種專案類型之間差異的詳細資訊，請參閱 [Visual Studio 中的 Web 應用程式專案和網站專案](/previous-versions/aspnet/dd547590(v=vs.110))。

- 當您使用 Visual Studio 中的 [ **加入新專案** ] 對話方塊建立資料服務時，資料服務是由 IIS 中的 ASP.NET 所主控。 雖然 ASP.NET 和 IIS 是資料服務的預設主機，但也支援其他裝載選項。 如需詳細資訊，請參閱 [裝載資料服務](hosting-the-data-service-wcf-data-services.md)。

## <a name="deploy-wcf-data-services"></a>部署 WCF Data Services

WCF Data Services 提供選擇裝載資料服務之程序的彈性。 您可以使用 Visual Studio 將資料服務部署到下列平臺：

- **IIS 裝載的 Web 服務**

    當資料服務開發為 ASP.NET 專案時，可以使用標準 ASP.NET 部署程式將它部署到 IIS Web 服務器。 Visual Studio 提供下列 ASP.NET 部署技術，視裝載您要部署之資料服務的 ASP.NET 專案類型而定。

  - **用於 ASP.NET Web 應用程式的部署技術**

    - [HOW TO：在 Visual Studio 中建立 Web 部署套件](/previous-versions/aspnet/dd465323(v=vs.110))

    - [如何：在 Visual Studio 中使用 One-Click 發佈來部署 Web 專案](/previous-versions/aspnet/dd465337(v=vs.110))

  - **用於 ASP.NET 網站的部署技術**

    - [如何：使用複製網站工具複製網站檔案](/previous-versions/aspnet/c95809c0(v=vs.100))

    - [How to：發行網站](/previous-versions/aspnet/20yh9f1b(v=vs.100))

    - [逐步解說：使用 XCOPY 部署 ASP.NET Web 應用程式](/previous-versions/aspnet/f735abw9(v=vs.100))

     如需 ASP.NET 應用程式部署選項的詳細資訊，請參閱 [Visual Studio 和 ASP.NET 的 Web 部署總覽](/previous-versions/aspnet/dd394698(v=vs.110))。

    > [!TIP]
    > 在您嘗試將資料服務部署到 IIS 之前，請確認您已經測試執行 IIS 之 Web 伺服器的部署。 如需詳細資訊，請參閱 [How to: Develop a WCF Data Service Running on IIS](how-to-develop-a-wcf-data-service-running-on-iis.md)。

- **Azure**

     您可以使用 [Azure Tools for Visual Studio](../../../azure/vs2015-install.md)，將資料服務部署至 azure。 如需將資料服務部署至 Azure 的詳細資訊，請參閱 [在 azure 中部署 OData 服務](/archive/blogs/astoriateam/deploying-an-odata-service-in-windows-azure)。

### <a name="deployment-considerations"></a>部署考量

部署資料服務時，請考慮下列事項：

- 當您部署的資料服務使用 Entity Framework 提供者來存取 SQL Server 資料庫時，您可能也需要使用資料服務部署傳播資料結構、資料或兩者。 Visual Studio 可以自動建立腳本 ( .sql 檔案) 在目的地資料庫中進行這項作業，而且這些腳本可包含在 ASP.NET 應用程式的 Web 部署套件中。 如需詳細資訊，請參閱 [如何：使用 Web 應用程式專案部署資料庫](/previous-versions/dd465343(v=vs.100))。 針對 ASP.NET 網站，您可以使用 Visual Studio 中的 [ **資料庫發佈嚮導]** 來進行這項操作。 如需詳細資訊，請參閱 [發佈 SQL Database](/previous-versions/aspnet/bb907585(v=vs.100))。

- 由於 WCF Data Services 包含基本的 WCF 執行，因此您可以使用 Windows Server AppFabric 來監視部署到在 Windows Server 上執行之 IIS 的資料服務。 如需使用 Windows Server AppFabric 監視資料服務的詳細資訊，請參閱 [Windows Server appfabric 的 Post 追蹤 WCF Data Services](/archive/blogs/rjacobs/tracking-wcf-data-services-with-windows-server-appfabric)。

## <a name="see-also"></a>另請參閱

- [裝載資料服務](hosting-the-data-service-wcf-data-services.md)
- [保護 WCF Data Services 的安全](securing-wcf-data-services.md)
- [定義 WCF 資料服務](defining-wcf-data-services.md)
