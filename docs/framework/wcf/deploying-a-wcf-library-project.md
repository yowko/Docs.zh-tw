---
title: 部署 WCF 程式庫專案
ms.date: 03/30/2017
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
ms.openlocfilehash: 186ce5ae3087fd9b4c7e5c32e110de4bc7d5e578
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2019
ms.locfileid: "74801990"
---
# <a name="deploying-a-wcf-library-project"></a>部署 WCF 程式庫專案
本主題說明如何部署 Windows Communication Foundation （WCF）服務程式庫專案。  
  
## <a name="deploying-a-wcf-service-library"></a>部署 WCF 服務程式庫  
 WCF 服務程式庫是一種動態連結程式庫（DLL）。 因此，它無法自行執行， 而必須部署在裝載環境中。 如需此流程的詳細資訊，請參閱[裝載和使用 WCF 服務](https://docs.microsoft.com/previous-versions/dotnet/articles/bb332338(v=msdn.10))。  
  
 WCF 服務程式庫可以像任何其他 WCF 服務一樣部署。 不過，請注意，.NET Framework 不支援 Dll 的設定。 <xref:System.Configuration> 針對每個應用程式定義域各支援一個組態檔。 WCF 服務程式庫專案會在開發期間提供程式庫的 App.config 檔案，以減輕這項限制。 但是，部署後無法辨識 App.config 檔案。  
  
 您必須將組態程式碼移至裝載環境所辨識的組態檔中。 如果是自我裝載，則應該將 App.config 檔案的內容複製到裝載可執行檔的 App.config 檔案中。 如果您使用 IIS 裝載服務，您應該將 App.config 檔案的內容複製到虛擬目錄的 Web.config 檔案中。
