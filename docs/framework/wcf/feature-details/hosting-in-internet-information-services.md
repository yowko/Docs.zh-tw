---
title: 在網際網路資訊服務中裝載
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- hosting services [WCF], IIS
ms.assetid: ddae14e8-143c-442d-b660-2046809b2d43
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b933626c2f3f5ee7121d141d3704376efeb54ba5
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="hosting-in-internet-information-services"></a>在網際網路資訊服務中裝載
您可以選擇將 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務裝載於網際網路資訊服務 (IIS) 應用程式內。 這個裝載模型與 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 和 ASP.NET (ASMX) Web 服務所使用的模型很類似。  
  
## <a name="versions-of-iis"></a>IIS 的版本  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可以裝載到下列作業系統上的 IIS 版本中：  
  
-   [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] 上的 IIS 5.1。 這個環境適合用來設計與開發 IIS 裝載的應用程式，以便稍後部署到 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 之類的伺服器作業系統中。  
  
-   [!INCLUDE[iis601](../../../../includes/iis601-md.md)] 上的 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]。 [!INCLUDE[iis601](../../../../includes/iis601-md.md)] 提供進階處理模型，具有改良的延展性、可靠性和應用程式隔離。 這個環境適合用在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的實際執行部署中，以便單獨使用 HTTP 通訊。  
  
-   [!INCLUDE[wv](../../../../includes/wv-md.md)] 和 [!INCLUDE[lserver](../../../../includes/lserver-md.md)] 上的 IIS 7.0。 雖然 IIS 7.0 提供和 [!INCLUDE[iis601](../../../../includes/iis601-md.md)] 相同的進階處理模型，但是使用 Windows Process Activation Service (WAS) 來允許在 HTTP 以外的通訊協定上進行啟動和網路通訊。 這個環境適合用來開發 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務，以便透過任何由 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 支援的網路通訊協定來進行通訊 (包括 HTTP、net.tcp、net.pipe 和 net.msmq)。 如需 WAS 的詳細資訊，請參閱[Windows Process Activation Service 中裝載](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)。  
  
-   [Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=196496)搭配[!INCLUDE[iisver](../../../../includes/iisver-md.md)]和 Windows Process Activation Service (WAS) 提供豐富的應用程式裝載環境為 NET4 WCF 和 WF 服務。 這些優點包括處理序生命週期管理、處理序回收、共用裝載、快速失敗保護、處理序損壞、隨選啟動和健康監視。 如需詳細資訊，請參閱[AppFabric 主控功能](http://go.microsoft.com/fwlink/?LinkId=196494)和[AppFabric 主控概念](http://go.microsoft.com/fwlink/?LinkId=196495)。  
  
## <a name="benefits-of-iis-hosting"></a>IIS 裝載的優點  
 將 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務裝載到 IIS 具有下列優點：  
  
-   您可以依據部署與管理其他任何類型 IIS 應用程式的方式，來部署與管理 IIS 所裝載的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務，包括 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 應用程式和 ASMX。  
  
-   IIS 可提供處理序啟動、系統健康狀態管理，與回收功能來增加所裝載之應用程式的可靠性。  
  
-   就像 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 一樣，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 所裝載的 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 服務會充分善用 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 共用裝載模型的優勢，讓多個應用程式駐留在一般背景工作處理序中以改善伺服器密度與延展性。  
  
-   IIS 所裝載的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務與 [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] 所使用的動態編譯模型是一樣的，都會針對裝載的服務簡化其開發與部署。  
  
 在決定將 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務裝載到 IIS 時，請務必記得 IIS 5.1 和 [!INCLUDE[iis601](../../../../includes/iis601-md.md)] 僅限於 HTTP 通訊用途。 如需有關選擇裝載環境的詳細資訊，請參閱[裝載服務](../../../../docs/framework/wcf/hosting-services.md)。  
  
## <a name="deploying-an-iis-hosted-wcf-service"></a>部署 IIS 裝載的 WCF 服務  
 開發與部署 IIS 裝載的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務包含下列工作：  
  
-   確定 IIS、ASP.NET、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 和 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] HTTP 啟動元件都已正確安裝及註冊。  
  
-   建立新的 IIS 應用程式，或是重複使用現有的 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 應用程式。  
  
-   建立 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的 .svc 檔案。  
  
-   將服務實作部署到 IIS 應用程式。  
  
-   設定 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務。  
  
 這些工作的討論，請參閱[部署 Internet Information Services-Hosted WCF 服務](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)。  
  
## <a name="wcf-services-and-aspnet"></a>WCF 服務與 ASP.NET  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務可以同時與 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 裝載在一起，或是裝載在 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 相容性模式中，以讓服務充分善用 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web 應用程式平台所提供的種種優勢。 如需這些功能的討論，請參閱[WCF 服務與 ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 ServiceHostFactory 擴充裝載](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
 [部署已裝載 Internet Information Services 的 WCF 服務](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)  
 [WCF 服務與 ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)  
 [Internet Information Services 裝載最佳做法](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [設定 Internet Information Services 7.0 for Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/configuring-iis-for-wcf.md)  
 [Windows Server App Fabric 裝載功能](http://go.microsoft.com/fwlink/?LinkId=201276)
