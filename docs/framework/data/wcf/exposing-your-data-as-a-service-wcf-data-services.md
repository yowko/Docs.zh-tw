---
title: "將資料當做服務公開 (WCF 資料服務)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, configuring
- getting started, WCF Data Services
- WCF Data Services, getting started
ms.assetid: df0bbcee-f66f-4a88-abb4-4e73c8b9c908
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 55e0bc058b92540c9b11965854d38e8d124e205c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="exposing-your-data-as-a-service-wcf-data-services"></a>將資料當做服務公開 (WCF 資料服務)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]使用 Visual Studio 可讓您更輕鬆地定義服務，您將資料公開為整合[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]摘要。 建立資料服務會公開[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]摘要包含下列基本步驟：  
  
1.  **定義****資料模型**。 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]原生方式支援資料模型為基礎的[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)。 如需詳細資訊，請參閱[How to： 建立資料服務，使用 ADO.NET Entity Framework 資料來源](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)。  
  
     [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 也支援以 Common Language Runtime (CLR) 物件為基礎的資料模型，這些物件會傳回 <xref:System.Linq.IQueryable%601> 介面的執行個體。 這樣可以讓您部署 .NET Framework 中以清單、陣列和集合為基礎的資料服務。 若要透過這些資料結構啟用建立、更新及刪除作業，您必須同時實作 <xref:System.Data.Services.IUpdatable> 介面。 如需詳細資訊，請參閱[How to： 建立資料服務，使用反映提供者](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)。  
  
     更進階的情況下，[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]包含一組可讓您定義資料模型，根據晚期繫結資料型別提供者。 如需詳細資訊，請參閱[自訂資料服務提供者](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md)。  
  
2.  **建立資料服務。** 最基本的資料服務會公開繼承自 <xref:System.Data.Services.DataService%601> 類別的類別，其具有實體容器之命名空間限定名稱 `T` 型別。 如需詳細資訊，請參閱 [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)的資訊。  
  
3.  **設定資料服務。** 根據預設， [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 會停用實體容器所公開的資源存取。 <xref:System.Data.Services.DataServiceConfiguration> 介面可讓您設定對資源和服務作業的存取、指定可支援的 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 版本，以及定義其他整個服務的行為 (例如，批次行為或在單一回應中可傳回的最大實體數目)。 如需詳細資訊，請參閱[設定資料服務](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)。  
  
 如需如何建立 Northwind 範例資料庫為基礎的簡易資料服務的範例，請參閱[快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)。  
  
## <a name="see-also"></a>請參閱  
 [快速入門](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 [概觀](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)
