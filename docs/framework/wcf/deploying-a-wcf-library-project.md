---
title: 部署 WCF 程式庫專案
ms.date: 03/30/2017
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
ms.openlocfilehash: 0f4c880bbd5c1bb819a04f42e91f531250c4f32e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554315"
---
# <a name="deploying-a-wcf-library-project"></a>部署 WCF 程式庫專案
本主題說明如何部署 Windows Communication Foundation (WCF) 的服務程式庫專案。  
  
## <a name="deploying-a-wcf-service-library"></a>部署 WCF 服務程式庫  
 WCF 服務程式庫是 (DLL) 的動態連結程式庫。 因此，它無法自行執行， 而必須部署在裝載環境中。 如需此程式的詳細資訊，請參閱 [裝載和使用 WCF 服務](/previous-versions/dotnet/articles/bb332338(v=msdn.10))。  
  
 WCF 服務程式庫可以像任何其他 WCF 服務一樣地部署。 不過請注意，.NET Framework 不支援 Dll 的設定。 <xref:System.Configuration> 針對每個應用程式定義域各支援一個組態檔。 WCF 服務程式庫專案會在開發期間提供程式庫的 App.config 檔案來緩和這項限制。 但是，部署後無法辨識 App.config 檔案。  
  
 您必須將組態程式碼移至裝載環境所辨識的組態檔中。 如果是自我裝載，則應該將 App.config 檔案的內容複製到裝載可執行檔的 App.config 檔案中。 如果您使用 IIS 裝載服務，您應該將 App.config 檔案的內容複製到虛擬目錄的 Web.config 檔案中。
