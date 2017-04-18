---
title: "將 .NET 遠端處理應用程式移轉到 WCF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ", NET 遠端 [WCF]"
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# 將 .NET 遠端處理應用程式移轉到 WCF
**本主題專門說明一項為了在現有應用程式中提供回溯相容性而保留的舊有技術，不建議用於新的開發工作。分散式應用程式現在應該可以使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 開發。**  
  
 有兩種方法可以利用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 搭配現有的 .NET 遠端處理應用程式：整合與移轉。整合可以讓您同時執行 .Net Remoting 2.0 和 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，以便能同時公開兩種技術的相同商務物件，而不需要修改現有的 .Net Remoting 2.0 程式碼。整合需要在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 \(含\) 以上版本執行。如果您想要利用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 功能，而且不需要與 Remoting 2.0 系統的網路相容性，可以將整個服務移轉到 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]。從 .NET Remoting 2.0 移轉到 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 需要變更遠端物件的介面及其組態設定。這些主題都包含在[從遠端處理到 Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=74403) \(英文\)。  
  
## 請參閱  
 [概觀說明](../../../../docs/framework/wcf/conceptual-overview.md)