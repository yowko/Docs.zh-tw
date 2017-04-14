---
title: "採用 Windows Communication Foundation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 49ba71e2-9468-4082-84c5-cf8daf95e34a
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# 採用 Windows Communication Foundation
您可以選擇使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 開發新項目，同時繼續維護使用 ASP.NET 開發的現有應用程式。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 預期是最適合在任何情況下使用以 .NET Framework 建置之應用程式簡化通訊的選擇，因此，它可以當做標準工具，以 ASP.NET 無法使用的方式，來解決各種軟體通訊問題。  
  
 新的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式可以在與現有 ASP.NET Web 服務相同的電腦上進行部署。如果現有的 ASP.NET Web 服務使用的 .NET Framework 版本早於 2.0 版，則您可以使用 ASP.NET IIS 註冊工具，將 .NET Framework 2.0 選擇性地部署至要裝載新 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式的 IIS 應用程式。該工具的說明位於 [ASP.NET IIS 註冊工具 \(Aspnet\_regiis.exe\)](http://go.microsoft.com/fwlink/?LinkId=94687) \(英文\)，且其使用者介面內建在 IIS 6.0 管理主控台中。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可用來將新功能加入至現有的 ASP.NET Web 服務中，方法是，將設定在 ASP.NET 相容性模式下執行的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務加入至 IIS 中現有的 ASP.NET Web 服務應用程式。由於 ASP.NET 相容性模式的緣故，新 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的程式碼現在可以使用 <xref:System.Web.HttpContext> 類別，存取與更新與 ASP.NET 現有程式碼相同的應用程式狀態資訊。應用程式也可以共用相同的類別庫。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端可以使用 ASP.NET Web 服務。ASP.NET Web 服務用戶端可以使用以 <xref:System.ServiceModel.BasicHttpBinding> 設定的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務。ASP.NET Web 服務可以與 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式並存，甚至可以使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 將功能加入至現有的 ASP.NET Web 服務。假設這些所有方式都能夠與 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 和 ASP.NET Web 服務一起使用，則只有在您需要 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] \(而非 ASP.NET Web 服務\) 所提供的功能時，才能將 ASP.NET Web 服務移轉至 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]。  
  
 即使是在少數必要的情況下，謹慎考慮將程式碼在兩個技術之間移轉也不見得是正確的方法。採用新技術的原因在於符合使用稍早技術無法滿足的新需求，在該情況下，正確的做法是設計新的解決方案以符合一組新擴展的需求。新設計的優點在於採用現有系統的經驗，以及設計該系統以來所獲取的智慧。新設計也可以使用新技術的完整功能，而不必在新平台上重現舊設計。製作新設計主要元素的原型之後，在新系統中重複使用現有系統的程式碼就會變得更容易。  
  
 在少數情況下，從 ASP.NET Web 服務移轉到 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 是正確的解決方案，下節將提供一些如何進行的指導方針。其中包含如何移轉服務以及如何移轉用戶端的建議。  
  
 如需如何將現有的 ASP.NET Web 服務移轉至 WCF 的完整分析，請參閱 [ASP.NET Web 服務和 Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkID=71761) \(英文\)。本節說明如何從中繼資料為您實作相容的 WCF 服務 \(ASP.NET Web 服務\)，以及如何將 ASP.NET Web 服務和用戶端程式碼移轉至 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]。  
  
## 請參閱  
 [HOW TO：擷取中繼資料並實作相容性服務](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)   
 [HOW TO：將 ASP.NET Web 服務程式碼移轉至 Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-to-wcf.md)   
 [HOW TO：將 ASP.NET Web 服務用戶端程式碼移轉至 Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-client-to-wcf.md)