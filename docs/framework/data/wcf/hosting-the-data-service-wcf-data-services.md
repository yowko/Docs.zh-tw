---
title: "裝載資料服務 (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "HTML"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "WCF Data Services, 設定"
  - "WCF Data Services, Windows Communication Foundation"
ms.assetid: b48f42ce-22ce-4f8d-8f0d-f7ddac9125ee
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 裝載資料服務 (WCF Data Services)
您可以藉由使用 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]，建立一個服務將資料公開為 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] 摘要。  這個資料服務會定義為繼承自 <xref:System.Data.Services.DataService%601> 的類別。  此類別會提供處理要求訊息、針對資料來源執行更新，以及產生回應訊息所需的功能，如 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 所要求。不過，資料服務無法繫結至傳入之 HTTP 要求的網路通訊端，也無法在其上接聽。  對於這個必要的功能而言，資料服務會依賴裝載的元件。  
  
 資料服務主機會代表資料服務執行下列工作：  
  
-   接聽要求，並將這些要求路由傳送到資料服務。  
  
-   為每一個要求建立資料服務的執行個體。  
  
-   要求資料服務處理傳入的要求。  
  
-   代表資料服務傳送回應。  
  
 為了簡化資料服務的裝載，[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 已設計來與 Windows Communication Foundation \(WCF\) 整合。  資料服務會提供預設 WCF 實作，此實作會當做 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 應用程式中的資料服務主機。  因此，您可以透過下列其中一個方法來裝載資料服務：  
  
-   在 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 應用程式中。  
  
-   在支援自我裝載之 WCF 服務的 Managed 應用程式中。  
  
-   在某個其他自訂資料服務主機中。  
  
## 在 ASP.NET 應用程式中裝載資料服務  
 當您在 Visual Studio 中使用 \[**加入新項目**\] 對話方塊來定義 ASP.NET 應用程式中的資料服務時，此工具會在專案中產生兩個新檔案。  第一個檔案的副檔名為 `.svc`，而且它會指示 WCF 執行階段如何具現化資料服務。  下列是這個檔案的範例，適用於當您完成[快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)時所建立的 Northwind 範例資料服務：  
  
```  
<%@ ServiceHost Language="C#"   
    Factory="System.Data.Services.DataServiceHostFactory,   
            System.Data.Services, Version=4.0.0.0,   
            Culture=neutral, PublicKeyToken=b77a5c561934e089"   
    Service="NorthwindService.Northwind" %>   
```  
  
 這個指示詞會告訴應用程式針對指名的資料服務類別建立服務主機，其方式是使用 <xref:System.Data.Services.DataServiceHostFactory> 類別。  
  
 `.svc` 檔案的程式碼後置頁面包含資料服務本身之實作的類別，如下列 Northwind 範例資料服務所定義：  
  
 [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
 [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
 資料服務的行為就像是 WCF 服務，因此，資料服務會與 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 整合，並遵循 WCF Web 程式設計模型。如需詳細資訊，請參閱 [WCF 服務與 ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) 以及 [WCF Web HTTP 程式設計模型](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)。  
  
## 自我裝載的 WCF 服務  
 因為它會合併 WCF 實作，所以 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 支援自我裝載的資料服務當做 WCF 服務。  服務可以在任何 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 應用程式中自我裝載，例如在主控台應用程式中。  繼承自 <xref:System.ServiceModel.Web.WebServiceHost> 的 <xref:System.Data.Services.DataServiceHost> 類別是用來具現化特定位址上的資料服務。  
  
 自我裝載可用於開發及測試，因為它可更輕鬆地部署服務以及針對服務進行疑難排解。  不過，這種裝載不會提供 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 或 Internet Information Services \(IIS\) 所提供的進階裝載與管理功能。如需詳細資訊，請參閱[在 Managed 應用程式中裝載](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)。  
  
## 定義自訂資料服務主機  
 如果是 WCF 主機實作太具限制性的情況，您也可以為資料服務定義自訂主機。  實作 <xref:System.Data.Services.IDataServiceHost> 介面的任何類別都可以當做資料服務的網路主機使用。  自訂主機必須實作 <xref:System.Data.Services.IDataServiceHost> 介面，而且必須能夠處理資料服務主機的下列基本責任：  
  
-   為資料服務提供服務根路徑。  
  
-   針對適當的 <xref:System.Data.Services.IDataServiceHost> 成員實作處理要求和回應標頭資訊。  
  
-   處理資料服務所引發的例外狀況。  
  
-   驗證查詢字串中的參數。  
  
## 請參閱  
 [定義 WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)   
 [將資料公開為服務](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)   
 [設定資料服務](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)