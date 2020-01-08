---
title: 在網際網路資訊服務中裝載
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], IIS
ms.assetid: ddae14e8-143c-442d-b660-2046809b2d43
ms.openlocfilehash: b8e8bbe35ec3091816a4a943662f93f1b4581663
ms.sourcegitcommit: 8c99457955fc31785b36b3330c4ab6ce7984a7ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/29/2019
ms.locfileid: "75544678"
---
# <a name="host-in-internet-information-services"></a>Internet Information Services 中的主機

裝載 Windows Communication Foundation （WCF）服務的一個選項是在 Internet Information Services （IIS）應用程式中。 此裝載模型類似于 ASP.NET 和 ASP.NET Web 服務（.ASMX） Web 服務所使用的模型。

## <a name="versions-of-iis"></a>IIS 的版本

WCF 可以裝載于下列作業系統上的下列 IIS 版本：

- [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] 上的 IIS 5.1。 此環境適用于稍後部署在伺服器作業系統（例如 Windows Server 2003）上的 IIS 裝載應用程式的設計和開發。

- Windows Server 2003 上的 IIS 6.0。 IIS 6.0 提供先進的進程模型，可提供改良的擴充性、可靠性和應用程式隔離。 此環境適用于以獨佔方式使用 HTTP 通訊的 WCF 服務生產部署。

- Windows Vista 和 Windows Server 2008 上的 IIS 7.0。 IIS 7.0 提供與 IIS 6.0 相同的先進進程模型，但使用 Windows 進程啟用服務（WAS）允許透過 HTTP 以外的通訊協定進行啟用和網路通訊。 此環境適用于透過 WCF 支援的任何網路通訊協定進行通訊的 WCF 服務開發（包括 HTTP、net.tcp、net.pipe 和 net.tcp）。 如需 WAS 的詳細資訊，請參閱[在 Windows 進程啟用服務中裝載](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)。

- [Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkId=196496)適用于 IIS 7.0 和 Windows 進程啟用服務（WAS），以提供豐富的應用程式裝載環境來 NET4 WCF 和 WF 服務。 這些優點包括處理序生命週期管理、處理序回收、共用裝載、快速失敗保護、處理序損壞、隨選啟動和健康監視。 如需詳細資訊，請參閱[Appfabric 裝載功能](https://go.microsoft.com/fwlink/?LinkId=196494)和[appfabric 裝載概念](https://go.microsoft.com/fwlink/?LinkId=196495)。

## <a name="benefits-of-iis-hosting"></a>IIS 裝載的優點

在 IIS 中裝載 WCF 服務有數個優點：

- 裝載于 IIS 中的 WCF 服務會像任何其他類型的 IIS 應用程式一樣進行部署和管理，包括 ASP.NET 應用程式和 .ASMX。

- IIS 提供處理程序啟動、健康情況管理以及回收功能，以提升裝載應用程式的可靠性。

- 如同 ASP.NET，裝載在 ASP.NET 中的 WCF 服務可以利用 ASP.NET 共用裝載模型，其中多個應用程式位於共同的工作者進程中，以改善伺服器密度和擴充性。

- 裝載于 IIS 的 WCF 服務會使用與 ASP.NET 2.0 相同的動態編譯模型，這可簡化託管服務的開發和部署。

在決定要在 IIS 中裝載 WCF 服務時，請務必記住 IIS 5.1 和 IIS 6.0 僅限於 HTTP 通訊。 如需選擇裝載環境的詳細資訊，請參閱[裝載服務](../../../../docs/framework/wcf/hosting-services.md)。

## <a name="deploy-an-iis-hosted-wcf-service"></a>部署裝載于 IIS 的 WCF 服務

開發和部署 IIS 裝載的 WCF 服務包含下列工作：

- 請確定已正確安裝及註冊 IIS、ASP.NET、WCF 和 WCF HTTP 啟用元件。

- 建立新的 IIS 應用程式，或重複使用現有的 ASP.NET 應用程式。

- 建立 WCF 服務的 .svc 檔案。

- 將服務實作部署到 IIS 應用程式。

- 設定 WCF 服務。

如需每項工作的討論，請參閱[部署 Internet Information Services 託管的 WCF 服務](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)。

## <a name="wcf-services-and-aspnet"></a>WCF 服務和 ASP.NET

WCF 服務可以與 ASP.NET 並存裝載，或在 ASP.NET 相容性模式中裝載，服務可以充分利用 ASP.NET Web 應用程式平臺所提供的功能。 如需這些功能的討論，請參閱[WCF 服務和 ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)。

## <a name="see-also"></a>請參閱

- [使用 ServiceHostFactory 擴充裝載](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)
- [部署已裝載 Internet Information Services 的 WCF 服務](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)
- [WCF 服務與 ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
- [Internet Information Services 裝載最佳做法](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)
- [設定 Internet Information Services 7.0 for Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/configuring-iis-for-wcf.md)
- [Windows Server AppFabric 裝載功能](https://go.microsoft.com/fwlink/?LinkId=201276)
