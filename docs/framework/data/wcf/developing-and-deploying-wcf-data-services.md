---
title: 開發和部署 WCF Data Services
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- deploying [WCF Data Services
- developing applications [WCF Data Services]
ms.assetid: 6557c0e3-5aea-4f6e-bc14-77ad317a168b
ms.openlocfilehash: 5c473f818ea874392011065dc3d07101d2ef3bf5
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607954"
---
# <a name="develop-and-deploy-wcf-data-services"></a>開發並部署 WCF 資料服務

本文提供有關開發和部署 WCF 資料服務的資訊。 有關 WCF 資料服務的詳細資訊,請參閱[入門](getting-started-with-wcf-data-services.md)和[概述](wcf-data-services-overview.md)。

## <a name="develop-wcf-data-services"></a>開發 WCF 資料服務

當您使用 WCF 資料服務建立支援開放資料協定 (OData) 的資料服務時,必須在開發期間執行以下基本任務:

1. **定義資料模型**

     WCF 資料服務支援各種資料服務提供者,使您能夠根據來自各種數據源(從關係資料庫到後期綁定數據類型)的數據定義數據模型。 有關詳細資訊,請參閱[資料服務提供者](data-services-providers-wcf-data-services.md)。

2. **建立資料服務**

     最基本的資料服務會公開繼承自 <xref:System.Data.Services.DataService%601> 類別的類別，其具有實體容器之命名空間限定名稱 `T` 型別。 如需詳細資訊，請參閱 [Defining WCF Data Services](defining-wcf-data-services.md)的資訊。

3. **設定資料服務**

     默認情況下,WCF 數據服務會禁止訪問實體容器公開的資源。 該<xref:System.Data.Services.DataServiceConfiguration>介面使您能夠配置對資源和服務操作的訪問,指定支援版本的 OData,並定義其他服務範圍的行為,例如批處理行為或可在單個回應來源中返回的最大實體數。 有關詳細資訊,請參考[設定資料服務](configuring-the-data-service-wcf-data-services.md)。

本文主要介紹使用 Visual Studio 開發和部署數據服務。 有關 WCF 資料服務為將資料公開為 O 資料饋送而提供的靈活性的資訊,請參閱[定義 WCF 資料服務](defining-wcf-data-services.md)。

### <a name="choose-a-development-web-server"></a>選擇開發 Web 伺服器

當您使用 Visual Studio 2015 將 WCF 資料服務開發為 ASP.NET 應用程式或 ASP.NET 網站時,您可以選擇在開發期間運行數據服務的 Web 伺服器。 以下 Web 伺服器與 Visual Studio 整合,以便更輕鬆地在本地電腦上測試和調試數據服務。

1. **本機 IIS 伺服器**

     當您創建在 Internet 資訊服務 (IIS) 上運行 ASP.NET 應用程式或 ASP.NET 網站的數據服務時,我們建議您使用本地電腦上的 IIS 開發和測試數據服務。 在 IIS 上執行資料服務時，更容易在偵錯期間追蹤 HTTP 要求。 這還使您能夠預先確定 IIS 訪問數據服務所需的文件、資料庫和其他資源所需的必要許可權。 要在IIS上執行資料服務,請確保正確安裝和配置IIS和Windows通訊基礎 (WCF),並授予對檔案系統和資料庫中的IIS帳戶的存取許可權。 如需詳細資訊，請參閱 [How to: Develop a WCF Data Service Running on IIS](how-to-develop-a-wcf-data-service-running-on-iis.md)。

    > [!NOTE]
    > 您必須執行具有管理員許可權的 Visual Studio,才能啟用開發環境來配置本地 IIS 伺服器。

2. **Visual Studio 程式開發伺服器**

     Visual Studio 包括一個內建的 Web 伺服器,即可視化工作室開發伺服器,它是 ASP.NET 專案的預設 Web 伺服器。 此 Web 伺服器旨在 ASP.NET 開發期間在本地電腦上運行專案。 [WCF 資料服務快速入門](quickstart-wcf-data-services.md)演示如何創建在可視化工作室開發伺服器中運行的數據服務。

     使用 Visual Studio 開發伺服器開發資料服務時,請注意以下限制:

    - 只能在本機電腦上存取這個伺服器。

    - 此伺服器會接聽 `localhost` 和一個特定的連接埠 (而非連接埠 80)，此連接埠是用於 HTTP 訊息的預設連接埠。 如需詳細資訊，請參閱 [Visual Studio 中 ASP.NET Web 專案的 Web 伺服器](https://docs.microsoft.com/previous-versions/aspnet/58wxa9w5(v=vs.120))。

    - 此伺服器會在目前使用者帳戶的內容中執行資料服務。 例如,如果您以管理員級使用者身份運行,則在可視化工作室開發伺服器中運行的數據服務將具有管理員級許可權。 這可能會使資料服務能夠存取在部署到 IIS 伺服器時沒有存取權限的資源。

    - 這個伺服器不包含 IIS 的額外功能，例如驗證。

    - 此伺服器無法處理分塊 HTTP 流,默認情況下,WCF 數據服務用戶端在從數據服務存取大型二進位數據時發送這些數據。 有關詳細資訊,請參閱[流式處理提供者](streaming-provider-wcf-data-services.md)。

    - 此伺服器在處理 URL 中的`.`句點 ( ) 字元時出現問題,即使 WCF 資料服務在鍵值中支援此字元。

    > [!TIP]
    > 即使可以使用 Visual Studio 開發伺服器在開發期間測試數據服務,但在部署到運行 IIS 的 Web 伺服器後,也應再次測試它們。

3. **Azure 開發環境**

     適用於可視化工作室的 Windows Azure 工具包括一組用於在可視化工作室中開發 Azure 服務的整合工具。 使用這些工具,可以開發可部署到 Azure 的數據服務,也可以在部署之前在本地電腦上測試數據服務。 使用 Visual Studio 開發在 Azure 平臺上運行的數據服務時,請使用這些工具。 有關安裝這些工具的資訊,請參閱[Visual Studio 2015 的 Azure 工具](../../../azure/sdk/vs2015-install.md)。 有關開發在 Azure 上運行的數據服務的詳細資訊,請參閱在 Azure[中部署 OData 服務](https://docs.microsoft.com/archive/blogs/astoriateam/deploying-an-odata-service-in-windows-azure)的帖子。

### <a name="development-tips"></a>開發秘訣

開發資料服務時請考慮以下事項:

- 如果計劃對使用者進行身份驗證或限制特定使用者的訪問,請確定數據服務的安全要求。 如需詳細資訊，請參閱 [Securing WCF Data Services](securing-wcf-data-services.md)。

- 通過允許您檢查請求和回應消息的內容,HTTP 檢查程式在調試數據服務時非常有用。 可以顯示原始封包的任何網路封包分析器可用於檢查資料服務的 HTTP 要求及其回應。

- 除錯資料服務時,您可能希望從資料服務獲得與常規操作期間有關錯誤的詳細資訊。 您可以從資料服務取得其他錯誤資訊，方法是，將 <xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A> 中的 <xref:System.Data.Services.DataServiceConfiguration> 屬性 (Property) 設為 `true` ，然後在資料服務類別上，將 <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A> 屬性 (Attribute) 的 <xref:System.ServiceModel.Description.ServiceDebugBehavior> 屬性 (Property) 設為 `true`。 有關詳細資訊,請參閱[調試 WCF 數據服務](https://docs.microsoft.com/archive/blogs/phaniraj/debugging-wcf-data-services)後。 您還可以在 WCF 中啟用跟蹤,以查看 HTTP 消息層中引發的異常。 如需詳細資訊，請參閱 [Configuring Tracing](../../wcf/diagnostics/tracing/configuring-tracing.md)。

- 數據服務通常作為應用程式專案ASP.NET開發,但您也可以在Visual Studio中創建資料服務作為ASP.NET網站專案。 有關這兩種項目之間的差異的資訊,請參閱[Visual Studio 中的 Web 應用程式專案與網站專案](https://docs.microsoft.com/previous-versions/aspnet/dd547590(v=vs.110))。

- 當您使用 Visual Studio 中的「**新增新專案」** 對話框建立資料服務時,資料服務由 iIS 中的 ASP.NET 託管。 雖然ASP.NET和IIS是數據服務的預設主機,但支援其他託管選項。 有關詳細資訊,請參閱[託管資料服務](hosting-the-data-service-wcf-data-services.md)。

## <a name="deploy-wcf-data-services"></a>部署 WCF 資料服務

WCF Data Services 提供選擇裝載資料服務之程序的彈性。 您可以使用 Visual Studio 將資料服務部署到以下平臺:

- **IIS 裝載的 Web 服務**

    當資料服務作為ASP.NET專案開發時,可以使用標準ASP.NET部署過程將其部署到IIS Web伺服器。 Visual Studio 為ASP.NET提供以下部署技術,具體取決於承載要部署的數據服務的ASP.NET項目類型。

  - **用於 ASP.NET Web 應用程式的部署技術**

    - [HOW TO：在 Visual Studio 中建立 Web 部署套件](https://docs.microsoft.com/previous-versions/aspnet/dd465323(v=vs.110))

    - [如何:在可視化工作室中使用一鍵發佈部署 Web 專案](https://docs.microsoft.com/previous-versions/aspnet/dd465337(v=vs.110))

  - **用於 ASP.NET 網站的部署技術**

    - [如何:使用複製網站工具複製網站檔案](https://docs.microsoft.com/previous-versions/aspnet/c95809c0(v=vs.100))

    - [如何:發佈網站](https://docs.microsoft.com/previous-versions/aspnet/20yh9f1b(v=vs.100))

    - [演練:使用 XCOPY 部署ASP.NET Web 應用程式](https://docs.microsoft.com/previous-versions/aspnet/f735abw9(v=vs.100))

     有關ASP.NET應用程式的部署選項的詳細資訊,請參閱 Visual Studio[和 ASP.NET 的 Web 部署概述](https://docs.microsoft.com/previous-versions/aspnet/dd394698(v=vs.110))。

    > [!TIP]
    > 在您嘗試將資料服務部署到 IIS 之前，請確認您已經測試執行 IIS 之 Web 伺服器的部署。 如需詳細資訊，請參閱 [How to: Develop a WCF Data Service Running on IIS](how-to-develop-a-wcf-data-service-running-on-iis.md)。

- **Azure**

     可以使用 Visual Studio 的 Azure[工具](../../../azure/sdk/vs2015-install.md)將數據服務部署到 Azure。 有關將資料服務部署到 Azure 的詳細資訊,請參閱[在 Azure 中部署 OData 服務](https://docs.microsoft.com/archive/blogs/astoriateam/deploying-an-odata-service-in-windows-azure)。

### <a name="deployment-considerations"></a>部署考量

部署資料服務時請考慮以下事項:

- 部署使用實體框架提供程式訪問 SQL Server 資料庫的數據服務時,可能還必須透過資料服務部署來傳播資料結構、資料或兩者。 Visual Studio 可以自動建立文稿 (.sql 檔案)以在目標資料庫中執行此操作,這些腳本可以包含在ASP.NET應用程式的 Web 部署包中。 有關詳細資訊,請參閱[如何:使用 Web 應用程式專案部署資料庫](https://docs.microsoft.com/previous-versions/dd465343(v=vs.100))。 對於ASP.NET網站,您可以通過在可視化工作室中使用**資料庫發佈嚮導**來執行此操作。 有關詳細資訊,請參閱發佈[SQL 資料庫](https://docs.microsoft.com/previous-versions/aspnet/bb907585(v=vs.100))。

- 由於 WCF 資料服務包含基本的 WCF 實現,因此可以使用 Windows 伺服器 AppFabric 監視部署到在 Windows 伺服器上運行的 IIS 的數據服務。 有關使用 Windows 伺服器 AppFabric 監視數據服務的詳細資訊,請參閱使用[Windows 伺服器 AppFabric 跟蹤 WCF 數據服務](https://docs.microsoft.com/archive/blogs/rjacobs/tracking-wcf-data-services-with-windows-server-appfabric)的帖子。

## <a name="see-also"></a>另請參閱

- [裝載資料服務](hosting-the-data-service-wcf-data-services.md)
- [Securing WCF Data Services](securing-wcf-data-services.md)
- [定義 WCF 資料服務](defining-wcf-data-services.md)
