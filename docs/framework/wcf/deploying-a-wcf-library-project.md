---
title: "部署 WCF 程式庫專案 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# 部署 WCF 程式庫專案
本主題說明如何部署 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 服務程式庫專案。  
  
## 部署 WCF 服務程式庫  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務程式庫是一種動態連結程式庫 \(DLL\)。因此，它無法自行執行，而必須部署在裝載環境中。如需這個程序的詳細資訊，請參閱[裝載和使用 WCF 服務](http://go.microsoft.com/fwlink/?LinkId=99932) \(本頁面可能為英文\)。  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務程式庫可以像任何其他 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務一樣來部署。不過，請注意 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 不支援設定 DLL。<xref:System.Configuration> 支援一個應用程式定義域 \(App\-Domain\) 使用一個組態檔。[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務程式庫專案藉由在開發期間為程式庫提供 App.config 檔案，來減輕此限制。但是，部署後無法辨識 App.config 檔案。  
  
 您必須將組態程式碼移至裝載環境所辨識的組態檔中。如果是自我裝載，則應該將 App.config 檔案的內容複製到裝載可執行檔的 App.config 檔案中。如果您使用 IIS 裝載服務，您應該將 App.config 檔案的內容複製到虛擬目錄的 Web.config 檔案中。