---
title: 部署 WCF 程式庫專案
ms.date: 03/30/2017
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
ms.openlocfilehash: 08a1d794aeeea1a41cd1eb3abf298f3f4a0f6d15
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="deploying-a-wcf-library-project"></a>部署 WCF 程式庫專案
本主題描述如何部署 Windows Communication Foundation (WCF) 服務程式庫專案。  
  
## <a name="deploying-a-wcf-service-library"></a>部署 WCF 服務程式庫  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務程式庫是一種動態連結程式庫 (DLL)。 因此，它無法自行執行， 而必須部署在裝載環境中。 如需此程序的詳細資訊，請參閱[主控和取用 WCF 服務](http://go.microsoft.com/fwlink/?LinkId=99932)。  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務程式庫可以像任何其他 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務一樣來部署。 不過，請注意 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 不支援設定 DLL。 <xref:System.Configuration> 針對每個應用程式定義域各支援一個組態檔。 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務程式庫專案藉由在開發期間為程式庫提供 App.config 檔案，來減輕此限制。 但是，部署後無法辨識 App.config 檔案。  
  
 您必須將組態程式碼移至裝載環境所辨識的組態檔中。 如果是自我裝載，則應該將 App.config 檔案的內容複製到裝載可執行檔的 App.config 檔案中。 如果您使用 IIS 裝載服務，您應該將 App.config 檔案的內容複製到虛擬目錄的 Web.config 檔案中。
