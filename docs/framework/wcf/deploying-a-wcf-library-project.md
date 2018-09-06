---
title: 部署 WCF 程式庫專案
ms.date: 03/30/2017
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
ms.openlocfilehash: 1ba26a7e68fe262dc5f4f569647af1ebb94e03a8
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "44042526"
---
# <a name="deploying-a-wcf-library-project"></a>部署 WCF 程式庫專案
本主題描述如何部署 Windows Communication Foundation (WCF) 服務程式庫專案。  
  
## <a name="deploying-a-wcf-service-library"></a>部署 WCF 服務程式庫  
 WCF 服務程式庫是動態連結程式庫 (DLL)。 因此，它無法自行執行， 而必須部署在裝載環境中。 如需有關此程序的詳細資訊，請參閱 <<c0> [ 裝載和使用 WCF 服務](https://go.microsoft.com/fwlink/?LinkId=99932)。  
  
 就像任何其他 WCF 服務，您可以部署的 WCF 服務程式庫。 不過，請注意 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 不支援設定 DLL。 <xref:System.Configuration> 針對每個應用程式定義域各支援一個組態檔。 WCF 服務程式庫專案會減輕這項限制，藉由在開發期間提供的程式庫的 App.config 檔案。 但是，部署後無法辨識 App.config 檔案。  
  
 您必須將組態程式碼移至裝載環境所辨識的組態檔中。 如果是自我裝載，則應該將 App.config 檔案的內容複製到裝載可執行檔的 App.config 檔案中。 如果您使用 IIS 裝載服務，您應該將 App.config 檔案的內容複製到虛擬目錄的 Web.config 檔案中。
