---
title: "將資料公開為服務 (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "使用者入門, WCF Data Services"
  - "WCF Data Services, 設定"
  - "WCF Data Services, 使用者入門"
ms.assetid: df0bbcee-f66f-4a88-abb4-4e73c8b9c908
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 將資料公開為服務 (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 會與 Visual Studio 整合，可讓您更輕鬆地定義服務，將您的資料公開為 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] 摘要。  建立資料服務來公開 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要包含下列基本步驟：  
  
1.  **定義** **資料模型**。  [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 原本就支援以 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) 為基礎的資料模型。  如需詳細資訊，請參閱[HOW TO：使用 ADO.NET Entity Framework 資料來源建立資料服務](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)。  
  
     [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 也支援以 Common Language Runtime \(CLR\) 物件為基礎的資料模型，這些物件會傳回 <xref:System.Linq.IQueryable%601> 介面的執行個體。  這可讓您根據 .NET Framework 中的清單、陣列與集合，部署資料服務。若要透過這些資料結構啟用建立、更新和刪除作業，您也必須實作 <xref:System.Data.Services.IUpdatable> 介面。  如需詳細資訊，請參閱[HOW TO：使用反映提供者建立資料服務](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)。  
  
     如果是更進階的案例，[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 包含一組提供者，可讓您根據晚期繫結的資料型別定義資料模型。  如需詳細資訊，請參閱[自訂資料服務提供者](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md)。  
  
2.  **建立資料服務。**最基本的資料服務會公開繼承自 <xref:System.Data.Services.DataService%601> 類別的類別，其具有實體容器之命名空間限定名稱的 `T` 型別。  如需詳細資訊，請參閱[定義 WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)。  
  
3.  **設定資料服務。**根據預設，[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 會停用經由實體容器公開之資源的存取。<xref:System.Data.Services.DataServiceConfiguration> 介面可讓您設定對資源和服務作業的存取、指定支援的 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 版本，以及定義其他的全服務行為 \(例如，批次行為或可在單一回應中傳回的最大實體數目\)。如需詳細資訊，請參閱[設定資料服務](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)。  
  
 如需如何建立以 Northwind 範例資料庫為基礎的簡單資料服務，請參閱[快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)。  
  
## 請參閱  
 [使用者入門](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)   
 [概觀](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)